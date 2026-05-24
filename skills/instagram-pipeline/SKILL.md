---
name: instagram-pipeline
description: This skill should be used when the user wants to generate a complete Instagram carousel post for Universidad Uk — including slide copy, DALL-E 3 background images in feed and story formats, a Photoshop brief, and an HTML preview. Trigger when the user says "generar posteo Instagram", "crear carrusel", "pipeline de Instagram", "post para redes", or provides a topic and asks for social media content. Orchestrates brief-analysis → copy-generation → visual-brief → image-generation → post-preview in sequence.
---

# Skill: instagram-pipeline

## Descripción
Skill maestro que orquesta el pipeline completo de generación de contenido para Instagram. Toma un brief editorial y produce un carrusel de 5 slides listo para aprobar y pasar al diseñador.

## Parámetros de entrada
- `tema` (obligatorio): el tema del posteo
- `formato` (obligatorio): `carrusel`
- `carrera` (opcional): carrera específica de Universidad Uk
- `país` (opcional): país de la audiencia — define el badge y el contexto local
- `contexto` (opcional): dirección editorial adicional

Si no se provee `tema`, pedirlo antes de empezar.

## Paso 0 — Carga de configuración (OBLIGATORIO)

Antes de ejecutar cualquier sub-skill:

1. **Cargar la API key de OpenAI** desde:
   - Variable de entorno `OPENAI_API_KEY`
   - Archivo `~/.claude/instagram-pipeline/.env` (formato: `OPENAI_API_KEY=valor`)

   Si no se encuentra: detener y pedir al usuario que corra `/instagram:setup`.

2. **Cargar la guía de estilo** desde `~/.claude/instagram-pipeline/style-guide.md`.
   Verificar que no tenga placeholders sin completar (`[...]`). Si los tiene, avisar y detener.

3. **Verificar el logo** en `~/.claude/instagram-pipeline/logo.png`.
   Si no existe: continuar igual pero anotar en el brief Photoshop que el logo debe agregarse manualmente.

4. **Definir el slug del posteo**: kebab-case del tema + país si aplica.
   Ejemplo: "Día Mundial del Medio Ambiente" + Guatemala → `medio-ambiente-guatemala`

5. **Crear la carpeta de output** en cwd:
   ```
   posts/{slug}/
   ```

## Pipeline de ejecución

### Paso 1 — brief-analysis
- Invocar el skill `brief-analysis`
- Input: todos los parámetros del usuario + style-guide
- Output: `posts/{slug}/brief.md`

### Paso 2 — copy-generation
- Invocar el skill `copy-generation`
- Input: brief del paso 1
- Output: `posts/{slug}/copy.md`

### Paso 3 — visual-brief
- Invocar el skill `visual-brief`
- Input: brief + copy
- Output: `posts/{slug}/visual-brief.md`

### Paso 4 — image-generation
- Invocar el skill `image-generation`
- Input: visual-brief
- Output: `posts/{slug}/slide-{N}-feed.png` y `posts/{slug}/slide-{N}-story.png` (5 pares)

### Paso 5 — post-preview
- Invocar el skill `post-preview`
- Input: copy + imágenes generadas + visual-brief
- Output: `posts/{slug}/preview.html`

## Reglas generales
- Si un paso falla, guardar el error en `posts/{slug}/error-paso{N}.md` y continuar si es posible
- Si la generación de una imagen falla, continuar con las demás y anotar cuál falló
- Al finalizar, mostrar resumen completo de archivos generados

## Output final

```
✅ Posteo generado: {tema} — {país}

Archivos en posts/{slug}/:
📝 brief.md
✍️  copy.md
🎨 visual-brief.md
🖼️  slide-1-feed.png + slide-1-story.png
    slide-2-feed.png + slide-2-story.png
    slide-3-feed.png + slide-3-story.png
    slide-4-feed.png + slide-4-story.png
    slide-5-feed.png + slide-5-story.png
👁️  preview.html  ← abrir con doble clic para revisar

Próximo paso: abrir preview.html, aprobar el concepto y pasar al diseñador con visual-brief.md
```
