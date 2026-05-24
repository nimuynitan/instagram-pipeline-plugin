# Guía de Estilo — Universidad Uk Instagram

> Este archivo vive en `~/.claude/instagram-pipeline/style-guide.md`.
> Ya está preconfigurado con los valores reales de marca. Completá solo la sección de carreras y CTAs antes de tu primer pipeline.

## Colores de marca

| Elemento | HEX | Uso |
|---|---|---|
| Naranja Uk (principal) | #FF671B | Titular bold, logo, badge |
| Blanco | #FFFFFF | Subtítulo bold, texto de apoyo, "Universidad" en logo |
| Negro | #000000 | Fondo base, overlay |
| Overlay sobre foto | rgba(0, 0, 0, 0.55) | Capa oscurecedora sobre imagen de fondo |

## Tipografía

| Uso | Fuente | Peso |
|---|---|---|
| Titular principal | Montserrat | Bold / ExtraBold |
| Subtítulo | Montserrat | SemiBold |
| Texto de apoyo | Poppins | Light |
| Badge de país | Montserrat | SemiBold |
| "Universidad" en logo | Poppins | Light |

> Montserrat y Poppins están disponibles en Google Fonts de forma gratuita si el diseñador no las tiene instaladas.

## Logo

- Logo para fondos oscuros (uso principal en Instagram): `logo.png`
- Logo alternativo (texto gris, para fondos claros si aplica): `logo-negro.png`
- Ambos archivos están en `${CLAUDE_PLUGIN_ROOT}/assets/` y se copian a `~/.claude/instagram-pipeline/` durante el setup
- **Importante:** si los logos tienen fondo negro en lugar de transparente, pedirle al equipo de diseño la versión con fondo transparente (PNG alpha) para que se integren correctamente sobre las fotos
- Posición en gráfica: esquina superior derecha
- Margen desde bordes: 32px (feed) / 48px (story)
- Ancho recomendado en diseño final: 110–130px

## Dimensiones

| Formato | Dimensiones finales | Tamaño GPT Image 2 |
|---|---|---|
| Feed | 1080 × 1080 px | 1024 × 1024 |
| Story | 1080 × 1920 px | 1024 × 1536 |

## Zona segura de texto

| Formato | Margen mínimo |
|---|---|
| Feed | 60px todos los bordes |
| Story | 80px laterales, 160px arriba y abajo |

## Posición y jerarquía del texto en la gráfica

- Alineación: izquierda
- Bloque de texto: tercio inferior o centro-izquierda de la imagen
- Orden visual de arriba hacia abajo: Titular → Subtítulo → Texto de apoyo
- El titular siempre es el elemento más grande y en #FF671B bold

## Especificaciones Photoshop por elemento

```
Titular:
  Fuente: Montserrat ExtraBold
  Tamaño: 60–72px (feed) / 80–96px (story)
  Color: #FF671B
  
Subtítulo:
  Fuente: Montserrat SemiBold
  Tamaño: 36–44px (feed)
  Color: #FFFFFF

Texto de apoyo:
  Fuente: Poppins Light
  Tamaño: 24–28px (feed)
  Color: #FFFFFF

Badge de país:
  Fondo: #FF671B
  Texto: #FFFFFF, Montserrat SemiBold 18px
  Padding: 6px 16px
  Posición: esquina superior derecha (bajo el logo) o inferior derecha

Overlay:
  Color: #000000
  Opacidad: 55%
  Modo: Normal
```

## Estilo fotográfico para GPT Image 2

- Fotografía profesional, alta resolución, 4K
- Iluminación dramática y cinematográfica — puntos de luz sobre fondos oscuros
- Personas latinoamericanas o escenarios relevantes al tema/carrera
- Espacio libre en la zona del texto (sin sujetos bloqueando el tercio inferior o izquierdo)
- Paleta oscura con acentos cálidos (complementa el naranja #FF671B)
- Nunca texto, palabras, letras ni números en la imagen generada

## Países activos y badge

| País | Badge |
|---|---|
| Guatemala | Guatemala 2026 |
| México | México 2026 |
| Colombia | Colombia 2026 |
| Perú | Perú 2026 |
| Chile | Chile 2026 |
| Ecuador | Ecuador 2026 |
| España | España 2026 |
| Estados Unidos | USA 2026 |

## Carreras que se pueden mencionar

> ⚠️ Completar con el catálogo real antes del primer pipeline

- [Carrera 1]
- [Carrera 2]
- [Carrera 3]

## CTAs estándar

> ⚠️ Completar antes del primer pipeline

- CTA principal: [ej: "Conoce nuestras carreras — link en bio"]
- CTA secundario: [ej: "Escríbenos por WhatsApp"]
- URL de conversión: [URL]

## Temas prohibidos

- No prometer salarios específicos sin fuente verificable
- No comparar directamente con otras universidades por nombre
- No usar imágenes de personas reconocibles sin autorización
