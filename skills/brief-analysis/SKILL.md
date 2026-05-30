---
name: brief-analysis
description: This skill should be used when the user needs to analyze an Instagram post brief — interpreting the topic, defining the narrative angle, the 5-slide story arc, the target audience mindset, and the key message for each slide. Trigger when analyzing briefs for social media content creation, or when part of the instagram-pipeline. Reads the style guide and, when a career is specified, the matching buyer persona to ground the message in real audience data.
---

# Skill: brief-analysis

## Objetivo
Interpretar el brief editorial y definir la estrategia narrativa del carrusel antes de escribir cualquier copy. Un buen brief-analysis es lo que diferencia un carrusel genérico de uno que genera engagement real.

## Carga de contexto (OBLIGATORIO antes de analizar)

1. **Leer la guía de estilo** desde `~/.claude/instagram-pipeline/style-guide.md`

2. **Si el brief incluye un parámetro `carrera`**, leer el buyer persona correspondiente desde `~/.claude/instagram-pipeline/buyer-personas.md`. Buscar la sección de esa carrera (los nombres están en MAYÚSCULAS como encabezados ##). Extraer y usar:
   - **Edad promedio** del segmento Ingresantes → define la edad del sujeto en las fotos y el tono del mensaje
   - **Género predominante** → influye en quién aparece en las imágenes
   - **Países principales** → si el brief no especifica país, usar el país #1 del persona
   - **Motivación principal para estudiar** → es el ángulo emocional más poderoso para el copy
   - **Situación laboral** → contexto de vida del lector (trabaja, busca crecer, emprende)
   - **Nivel educativo de los padres** → si es mayoría primera generación universitaria, eso es un ángulo de orgullo potente
   - **Datos de satisfacción de graduados** → pruebas sociales reales para usar en el copy

   Si la carrera no aparece exactamente en el archivo, buscar la más cercana (ej: "Marketing Digital" → "Mercadotecnia") o continuar sin persona si no hay match.

## Proceso

### 1. Interpretar el tema y el contexto
- ¿Qué quiere sentir o aprender el lector después de ver este carrusel?
- ¿Es una efeméride (la fecha importa), una carrera (el beneficio importa) o un tip (la utilidad importa)?
- ¿Qué emoción predomina: curiosidad, orgullo, urgencia, inspiración?
- Si hay buyer persona: ¿qué motivación real de ese perfil podemos activar?

### 2. Definir el ángulo narrativo
No todos los temas se cuentan igual. Elegir uno:
- **Dato sorprendente** → hook con cifra o hecho que rompe expectativas
- **Pregunta provocadora** → hook con pregunta que el lector no sabe responder
- **Escenario identificable** → hook con situación que el lector vivió o teme
- **Antes/después** → contraste entre el estado actual y el posible
- **Lista de valor** → "X cosas que no sabías sobre Y"

Si hay buyer persona, anclar el ángulo en su motivación principal. Ejemplo: si la motivación #1 de la carrera es "ser ejemplo para un familiar", un ángulo de orgullo familiar va a resonar más que uno de empleabilidad pura.

### 3. Diseñar el arco de 5 slides

| Slide | Rol | Objetivo |
|---|---|---|
| 1 | Hook / portada | Parar el scroll. Generar curiosidad para que deslicen |
| 2 | Contexto / problema | Establecer por qué esto importa |
| 3 | Desarrollo / valor 1 | Primer punto de valor concreto |
| 4 | Desarrollo / valor 2 | Segundo punto de valor o profundización |
| 5 | Cierre / CTA | Síntesis + acción clara |

Para efemérides: slide 1 menciona la fecha, slides 2-4 desarrollan con datos, slide 5 conecta con la propuesta de la universidad.
Para carreras: slide 1 plantea el diferencial, slides 2-4 exploran salidas laborales o especialidades, slide 5 es el CTA de inscripción.
Para tips: slide 1 es el hook con la promesa, slides 2-4 son los tips, slide 5 es síntesis + CTA.

### 4. Definir el mensaje clave de cada slide
Una oración por slide que resume qué tiene que quedarse grabado en el lector.

### 5. Perfil del sujeto para las imágenes
Basándote en el buyer persona (si está disponible), definir:
- Edad aproximada de la persona que aparece en las fotos
- Género predominante
- Contexto de vida (trabaja en oficina, estudia desde casa, emprende, etc.)

Esto se pasa al visual-brief para que las imágenes muestren personas alineadas al perfil real de la carrera.

## Output esperado

Guardar en `posts/{slug}/brief.md`:

```markdown
# Brief: {tema} — {país}

## Parámetros
- Tema:
- Formato: carrusel 5 slides
- Carrera: [si aplica]
- País:
- Contexto adicional:

## Buyer persona aplicado
[Si hay carrera: resumen del perfil — edad, género, motivación principal, contexto laboral, país principal. Si no hay carrera: "No aplica"]

## Ángulo narrativo
[Tipo elegido + justificación en 2 oraciones, anclado en la motivación del persona si aplica]

## Emoción predominante
[curiosidad / orgullo / urgencia / inspiración / otro]

## Perfil del sujeto para imágenes
- Edad aproximada: [del buyer persona]
- Género: [predominante del persona]
- Contexto: [oficina / casa / exterior / café, según el perfil]

## Arco narrativo

### Slide 1 — Hook
Rol: parar el scroll
Mensaje clave: [1 oración]

### Slide 2 — Contexto
Rol: establecer relevancia
Mensaje clave: [1 oración]

### Slide 3 — Valor 1
Rol: primer punto concreto
Mensaje clave: [1 oración]

### Slide 4 — Valor 2
Rol: segundo punto concreto
Mensaje clave: [1 oración]

### Slide 5 — Cierre
Rol: síntesis + CTA
Mensaje clave: [1 oración]
```
