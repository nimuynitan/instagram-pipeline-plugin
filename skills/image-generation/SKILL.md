---
name: image-generation
description: This skill should be used when the user needs to generate background images for Instagram carousel slides using GPT Image 2 (OpenAI's current image model) via the OpenAI API. Generates 5 feed images (1024x1024) and 5 story images (1024x1536) without text, ready for the designer to overlay copy. Trigger when generating images for Instagram content, or when part of the instagram-pipeline. Requires OPENAI_API_KEY configured. Note: DALL-E 3 was removed from the API in May 2026 — always use gpt-image-2.
---

# Skill: image-generation

## Objetivo
Llamar a la API de GPT Image 2 de OpenAI para generar las 10 imágenes de fondo del carrusel (5 feed + 5 story), descargarlas y guardarlas en la carpeta del posteo.

**Importante:** DALL-E 3 fue removido de la API el 12 de mayo de 2026. Usar siempre `gpt-image-2`.

## Carga de la API key

Obtener `OPENAI_API_KEY` en este orden:
1. Variable de entorno `OPENAI_API_KEY`
2. Archivo `~/.claude/instagram-pipeline/.env` (formato: `OPENAI_API_KEY=valor`)

Si no se encuentra: detener y mostrar:
> No encontré la API key de OpenAI. Corré `/instagram:setup` para configurarla.

Helper Python:
```python
import os
from pathlib import Path

def get_openai_key():
    key = os.environ.get("OPENAI_API_KEY")
    if key:
        return key.strip()
    env_path = Path.home() / ".claude" / "instagram-pipeline" / ".env"
    if env_path.exists():
        for line in env_path.read_text().splitlines():
            line = line.strip()
            if line.startswith("OPENAI_API_KEY="):
                return line.split("=", 1)[1].strip().strip('"').strip("'")
    raise RuntimeError("OPENAI_API_KEY no configurada. Correr /instagram:setup")
```

## Proceso de generación

### Llamada a la API de GPT Image 2

```python
import urllib.request, urllib.error, json, os, base64
from pathlib import Path

def generate_image(prompt, size, api_key, quality="medium"):
    data = json.dumps({
        "model": "gpt-image-2",
        "prompt": prompt,
        "n": 1,
        "size": size,
        "quality": quality,
        "output_format": "png"
    }).encode()
    
    req = urllib.request.Request(
        "https://api.openai.com/v1/images/generations",
        data=data,
        headers={
            "Authorization": f"Bearer {api_key}",
            "Content-Type": "application/json"
        }
    )
    
    try:
        with urllib.request.urlopen(req, timeout=90) as r:
            result = json.loads(r.read().decode())
        # GPT Image 2 devuelve b64_json por defecto
        b64_data = result["data"][0].get("b64_json")
        if b64_data:
            return ("b64", b64_data)
        # Fallback a URL si está disponible
        url = result["data"][0].get("url")
        return ("url", url)
    except urllib.error.HTTPError as e:
        error_body = e.read().decode()
        raise RuntimeError(f"OpenAI API error {e.code}: {error_body}")

def save_image(image_data, output_path):
    kind, data = image_data
    if kind == "b64":
        Path(output_path).write_bytes(base64.b64decode(data))
    else:
        urllib.request.urlretrieve(data, output_path)
```

### Tamaños a generar por slide

| Formato | Tamaño GPT Image 2 | Nombre de archivo |
|---|---|---|
| Feed | `1024x1024` | `slide-{N}-feed.png` |
| Story | `1024x1536` | `slide-{N}-story.png` |

**Nota:** GPT Image 2 no soporta `1024x1792`. El tamaño portrait más cercano es `1024x1536`.

### Secuencia de generación

Para cada slide (1 al 5), en orden:
1. Leer el prompt feed del `visual-brief.md`
2. Llamar a la API con `size="1024x1024"`, `quality="medium"` → guardar como `slide-{N}-feed.png`
3. Leer el prompt story del `visual-brief.md`
4. Llamar a la API con `size="1024x1536"`, `quality="medium"` → guardar como `slide-{N}-story.png`
5. Reportar progreso: "✅ Slide N generado (feed + story)"

**Calidad recomendada:** `medium` para pruebas y producción estándar. Usar `high` solo si la calidad de `medium` no es suficiente para el posteo.

### Manejo de errores

- Si una imagen falla: anotar el error, continuar con las demás
- Si el rate limit es excedido (error 429): esperar 10 segundos y reintentar una vez
- Si content policy rechaza el prompt (error 400): anotar que ese slide necesita un prompt alternativo, continuar
- Al final: listar cuáles slides se generaron y cuáles fallaron

### Costo estimado

GPT Image 2 por imagen en calidad `medium`:
- 1024x1024: ~$0.042 USD
- 1024x1536: ~$0.063 USD
- 10 imágenes por carrusel: ~$0.53 USD por posteo completo

En calidad `low` (para pruebas rápidas):
- 10 imágenes: ~$0.05 USD por posteo — prácticamente gratis para iterar

Reportar el costo estimado al finalizar.

## Output

Archivos guardados en `posts/{slug}/`:
```
slide-1-feed.png
slide-1-story.png
slide-2-feed.png
slide-2-story.png
slide-3-feed.png
slide-3-story.png
slide-4-feed.png
slide-4-story.png
slide-5-feed.png
slide-5-story.png
```

Resumen al finalizar:
```
🖼️ Imágenes generadas: X/10
❌ Fallidas: [lista si hay]
💰 Costo estimado: ~$X.XX USD
```
