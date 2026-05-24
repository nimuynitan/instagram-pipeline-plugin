---
description: Genera un posteo completo para Instagram — copy de 5 slides, imágenes de fondo DALL-E 3 en formato feed y story, brief Photoshop y preview HTML para aprobar.
argument-hint: tema="..." formato=carrusel carrera="..." país="..." contexto="..."
---

Usá el skill `instagram-pipeline` para ejecutar el pipeline completo con los siguientes argumentos:

$ARGUMENTS

**Antes de empezar:** verificar que existan:
- `~/.claude/instagram-pipeline/.env` con `OPENAI_API_KEY`
- `~/.claude/instagram-pipeline/style-guide.md` completado (sin placeholders `[...]`)
- `~/.claude/instagram-pipeline/logo.png`

Si falta alguno, detener y pedir al usuario que corra `/instagram:setup` primero.

**Parámetros disponibles:**
- `tema` (obligatorio): el tema del posteo — efeméride, carrera, tip, etc.
- `formato` (obligatorio): `carrusel` — por ahora el único formato soportado
- `carrera` (opcional): carrera específica de Universidad Uk a mencionar
- `país` (opcional): país de la audiencia objetivo — determina el badge y el contexto local
- `contexto` (opcional): dirección editorial adicional — ángulo, tono, datos específicos a incluir
