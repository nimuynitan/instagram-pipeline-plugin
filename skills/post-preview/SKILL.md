---
name: post-preview
description: This skill should be used when the user needs to generate an HTML preview of a complete Instagram carousel — showing all 5 slides with their background images, overlay copy layout, and the Photoshop brief collapsed at the bottom for review before passing to the designer. Trigger when generating previews for Instagram posts, or when part of the instagram-pipeline.
---

# Skill: post-preview

## Objetivo
Generar un archivo HTML que muestre el carrusel completo para que el equipo pueda revisar y aprobar el concepto antes de pasarlo al diseñador.

## Proceso

1. Leer `posts/{slug}/copy.md`
2. Leer `posts/{slug}/visual-brief.md`
3. Verificar qué imágenes existen en `posts/{slug}/` (algunas pueden haber fallado)
4. Generar el HTML con la estructura definida abajo
5. Guardar como `posts/{slug}/preview.html`

## Estructura del HTML

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{tema} — Preview Instagram</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      background: #0a0a0a;
      color: #f0f0f0;
      padding: 40px 20px;
    }
    
    .header {
      max-width: 1100px;
      margin: 0 auto 40px;
      padding-bottom: 24px;
      border-bottom: 1px solid #333;
    }
    
    .header h1 { font-size: 1.4em; font-weight: 600; margin-bottom: 4px; }
    .header p { color: #888; font-size: 0.85em; }
    
    .carousel {
      display: flex;
      gap: 20px;
      max-width: 1100px;
      margin: 0 auto 48px;
      overflow-x: auto;
      padding-bottom: 16px;
    }
    
    .slide {
      flex: 0 0 200px;
    }
    
    .slide-image {
      width: 200px;
      height: 200px;
      background: #1a1a1a;
      border-radius: 8px;
      overflow: hidden;
      margin-bottom: 12px;
      position: relative;
    }
    
    .slide-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    
    .slide-image .no-image {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #444;
      font-size: 0.8em;
      text-align: center;
      padding: 16px;
    }
    
    .slide-number {
      font-size: 0.7em;
      color: #666;
      margin-bottom: 6px;
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }
    
    .slide-copy { padding: 4px 0; }
    
    .copy-titular {
      font-size: 0.85em;
      font-weight: 700;
      color: #FFB800;
      margin-bottom: 4px;
      line-height: 1.3;
    }
    
    .copy-subtitulo {
      font-size: 0.78em;
      font-weight: 600;
      color: #ffffff;
      margin-bottom: 4px;
      line-height: 1.3;
    }
    
    .copy-apoyo {
      font-size: 0.72em;
      color: #aaaaaa;
      line-height: 1.4;
    }
    
    .section {
      max-width: 1100px;
      margin: 0 auto 40px;
    }
    
    .section h2 {
      font-size: 0.9em;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: #666;
      margin-bottom: 16px;
      padding-bottom: 8px;
      border-bottom: 1px solid #222;
    }
    
    .caption-box {
      background: #111;
      border: 1px solid #222;
      border-radius: 8px;
      padding: 20px;
      font-size: 0.9em;
      line-height: 1.7;
      white-space: pre-wrap;
    }
    
    .hashtags {
      color: #3b82f6;
      font-size: 0.85em;
      margin-top: 12px;
      line-height: 1.8;
    }
    
    details {
      background: #111;
      border: 1px solid #222;
      border-radius: 8px;
      padding: 20px;
    }
    
    summary {
      cursor: pointer;
      font-size: 0.9em;
      font-weight: 600;
      color: #888;
      user-select: none;
    }
    
    summary:hover { color: #ccc; }
    
    .brief-content {
      margin-top: 16px;
      font-size: 0.82em;
      line-height: 1.7;
      color: #aaa;
      white-space: pre-wrap;
    }
    
    .badge {
      display: inline-block;
      background: #E85D04;
      color: white;
      font-size: 0.7em;
      font-weight: 600;
      padding: 2px 8px;
      border-radius: 3px;
      margin-bottom: 8px;
    }
    
    .meta-bar {
      background: #111;
      border-radius: 6px;
      padding: 12px 16px;
      font-size: 0.78em;
      color: #666;
      margin-bottom: 32px;
      max-width: 1100px;
      margin-left: auto;
      margin-right: auto;
    }
  </style>
</head>
<body>

  <div class="header">
    <h1>📱 {tema}</h1>
    <p>Preview editorial — Universidad Uk | {país} | {fecha}</p>
  </div>
  
  <div class="meta-bar">
    📋 Preview para aprobación interna — No publicar directamente &nbsp;·&nbsp; 
    Pasar a diseñador con <strong>visual-brief.md</strong>
  </div>

  <!-- CARRUSEL -->
  <div class="carousel">
    <!-- Para cada slide: -->
    <div class="slide">
      <div class="slide-number">Slide 1 — Hook</div>
      <div class="slide-image">
        <img src="slide-1-feed.png" alt="Slide 1" onerror="this.parentElement.innerHTML='<div class=no-image>Imagen no<br>generada</div>'">
      </div>
      <div class="slide-copy">
        [si hay badge: <span class="badge">{país} {año}</span>]
        <div class="copy-titular">{titular slide 1}</div>
        <div class="copy-subtitulo">{subtítulo slide 1}</div>
        <div class="copy-apoyo">{texto apoyo slide 1}</div>
      </div>
    </div>
    <!-- Repetir para slides 2-5 -->
  </div>

  <!-- CAPTION -->
  <div class="section">
    <h2>Caption Instagram</h2>
    <div class="caption-box">{caption completo}</div>
    <div class="hashtags">{hashtags}</div>
  </div>

  <!-- BRIEF PHOTOSHOP (colapsado) -->
  <div class="section">
    <details>
      <summary>🎨 Brief Photoshop para el diseñador (expandir)</summary>
      <div class="brief-content">{contenido completo de visual-brief.md}</div>
    </details>
  </div>

</body>
</html>
```

## Reglas
- Las imágenes se referencian con rutas relativas (`slide-1-feed.png`) para que funcionen con doble clic sin servidor
- Si una imagen no existe, el `onerror` muestra un placeholder en lugar de un ícono roto
- Los colores del preview (`#FFB800`, `#E85D04`) deben coincidir con los del style-guide si están definidos
- El brief Photoshop va colapsado para no sobrecargar la vista inicial

## Output
Guardar como `posts/{slug}/preview.html`
