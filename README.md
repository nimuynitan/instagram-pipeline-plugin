# instagram-pipeline (plugin de Claude Code)

Pipeline de generación de contenido para Instagram de Universidad Uk. Toma un brief editorial y produce copy completo de 5 slides, imágenes de fondo generadas por DALL-E 3 en formato feed y story, brief Photoshop para el diseñador y preview HTML para aprobar.

---

## Instalación en una máquina nueva

### Requisitos
- Claude Code instalado y logueado
- Plan Claude Pro o Team
- API key de OpenAI (con acceso a DALL-E 3)

### Instalar el plugin

```
claude --dangerously-skip-permissions
/plugin marketplace add https://github.com/nimuynitan/instagram-pipeline-plugin
/plugin install instagram-pipeline@instagram-pipeline-marketplace
/instagram:setup
```

### Completar la configuración

Después del setup, completar:
- `~/.claude/instagram-pipeline/style-guide.md` — colores HEX reales, tipografías, carreras
- `~/.claude/instagram-pipeline/logo.png` — logo PNG con fondo transparente

---

## Uso

```
/instagram:post tema="Día Mundial del Medio Ambiente" formato=carrusel carrera="Ingeniería Ambiental" país=Guatemala contexto="ángulo empleabilidad verde 2026"
```

El pipeline crea automáticamente una carpeta `posts/{slug}/` en tu cwd con todos los archivos generados.

---

## Output por posteo

```
posts/medio-ambiente-guatemala/
├── brief.md              ← análisis narrativo del tema
├── copy.md               ← copy de los 5 slides + caption + hashtags
├── visual-brief.md       ← brief Photoshop + prompts DALL-E usados
├── slide-1-feed.png      ← fondo generado por DALL-E 3 (1024x1024)
├── slide-1-story.png     ← fondo generado por DALL-E 3 (1024x1792)
├── slide-2-feed.png
├── slide-2-story.png
├── slide-3-feed.png
├── slide-3-story.png
├── slide-4-feed.png
├── slide-4-story.png
├── slide-5-feed.png
├── slide-5-story.png
└── preview.html          ← abrir con doble clic para revisar todo junto
```

---

## Costo por posteo

Cada carrusel genera 10 imágenes DALL-E 3 HD:
- 5 feed (1024x1024): ~$0.08 c/u = ~$0.40
- 5 story (1024x1792): ~$0.12 c/u = ~$0.60
- **Total estimado: ~$1.00 USD por posteo**

---

## Configuración persistente

```
~/.claude/instagram-pipeline/
├── .env                  ← OPENAI_API_KEY
├── style-guide.md        ← identidad visual editable
└── logo.png              ← logo PNG transparente
```

No se sobrescribe al actualizar el plugin.

---

## Versión

1.0.0 — Mayo 2026
