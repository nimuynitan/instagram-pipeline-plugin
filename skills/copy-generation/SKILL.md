---
name: copy-generation
description: This skill should be used when the user needs to write complete Instagram carousel copy — slide text (headline, subtitle, supporting text), caption, hashtags, and CTA — following Universidad Uk's voice and visual hierarchy. Trigger when writing social media copy for Instagram, or when part of the instagram-pipeline. Always reads from the brief produced by brief-analysis.
---

# Skill: copy-generation

## Objetivo
Escribir el copy completo del carrusel: texto de cada slide con jerarquía visual definida, caption para Instagram, hashtags y CTA.

## Voz y tono (Universidad Uk — Instagram)
- **Directo y concreto**: cada slide dice una cosa, bien dicha. Sin relleno.
- **Cercano**: hablamos de tú, no de usted. Adultos que trabajan, no adolescentes.
- **Motivador sin exagerar**: inspiramos sin prometer lo que no podemos cumplir.
- **LATAM-first**: ejemplos y referencias de la región, no genéricos globales.
- **Sin voseo**: tuteo universal (puedes, tienes, decides — nunca podés, tenés, elegís).

## Reglas editoriales fijas
- Universidad siempre escrita **Universidad Uk** (k minúscula)
- Preguntas siempre con ¿ de apertura
- Sin frases vacías: "En el mundo actual...", "Hoy más que nunca..."
- Sin exclamaciones vacías: "¡Inscríbete ya!" → preferir: "El cupo es limitado. Reserva tu lugar."

## Principios de calidad del copy (CRÍTICO — esto define si el carrusel funciona)

Estos cinco principios son lo que separa un carrusel memorable de uno olvidable. Aplicarlos en TODOS los slides.

### 1. Los titulares son FRASES, nunca etiquetas
Cada titular debe cargar tensión, beneficio o sorpresa. Nunca ser una etiqueta de categoría.

| ❌ Etiqueta (débil) | ✅ Frase (fuerte) |
|---|---|
| "El Derecho de ayer" | "Las leyes de ayer te protegen hoy" |
| "El Derecho de hoy" | "Derecho hoy: más salidas que nunca" |
| "El origen de todo" | "Fray Bartolomé lo hizo posible" |
| "Nuestras carreras" | "La carrera que el mercado te está pidiendo" |

Test rápido: si el titular podría ser el encabezado de una diapositiva de PowerPoint, está mal. Reescribilo hasta que diga algo.

### 2. El slide 5 hace callback al slide 1
El cierre debe atar con el hook inicial para dar sensación de historia completa.
- Ejemplo bueno: slide 1 "En 1553, México fue primero" → slide 5 "El Derecho empezó aquí. Tu carrera también puede."
- El lector debe sentir que el carrusel cerró un círculo, no que terminó de golpe.

### 3. Hablale al lector, no del tema
Usar "tú/te/tu" para que el mensaje sea sobre la vida y el futuro del lector, no un recuento abstracto del tema.
- ❌ "El sistema jurídico tiene raíces mexicanas" (habla del tema)
- ✅ "Las leyes de ayer te protegen hoy" (habla al lector)
- En el slide de cierre especialmente: el protagonista es el lector, no la universidad ni la efeméride.

### 4. Mantené los anclajes concretos
Cuando hay un personaje, lugar, fecha o número que hace la historia memorable, conservalo. No lo abstraigas.
- ❌ "El origen de todo" (abstracto)
- ✅ "Fray Bartolomé lo hizo posible" (personaje concreto)
- Los nombres propios, fechas exactas y cifras específicas son lo que se recuerda. Úsalos.

### 5. Cero clichés
Prohibidos terminantemente: "nunca estuvo más vigente", "no para de evolucionar", "más que nunca" (salvo en construcción concreta como "más salidas que nunca"), "en la era digital", "el futuro es ahora", "transforma tu vida", "da el primer paso".
Si una frase podría aparecer en el copy de cualquier universidad, no sirve. Tiene que ser específica de ESTE tema y ESTE lector.

### Conexión con el buyer persona
El brief trae la motivación principal del perfil de la carrera. El ángulo emocional del copy — especialmente slides 1 y 5 — debe activar esa motivación. Ejemplo: si la motivación es "ser ejemplo para un familiar", un cierre como "Tu turno de hacer historia" resuena más que uno de empleabilidad pura.

## Estructura de copy por slide

### Texto en la gráfica (lo que ve el diseñador para poner sobre la imagen)
Cada slide tiene máximo 3 niveles de texto:

| Nivel | Rol | Caracteres máx. | Color en diseño |
|---|---|---|---|
| **Titular** | La idea principal del slide | 30-40 | Amarillo/naranja bold |
| **Subtítulo** | Complemento o gancho | 40-60 | Blanco bold |
| **Texto de apoyo** | Dato, pregunta o contexto | 60-80 | Blanco regular |

No todos los slides necesitan los 3 niveles. El slide 1 (hook) generalmente tiene solo titular + subtítulo.

### Caption de Instagram
- Primeras 2 líneas: el hook más fuerte (aparece antes del "ver más")
- Desarrollo: 3-5 líneas con el mensaje central
- CTA final: una acción clara y específica
- Longitud total: 150-300 caracteres antes del "ver más", 800-1200 en total
- Emojis: 2-4 máximo, usados con propósito (no decoración)

### Hashtags
- 8-12 hashtags por posteo
- Mix: 3-4 generales (#educaciononline #universidadonline), 3-4 de nicho (#carrerasenlinea #estudiaytrabaja), 2-3 de marca (#universidaduk #ukuiversidad)
- Adaptados al país si se especificó

## Proceso
1. Leer el brief completo de `posts/{slug}/brief.md`
2. Escribir el copy de cada slide siguiendo el arco narrativo definido
3. Verificar que el titular de cada slide funcione solo (sin necesitar contexto del anterior)
4. Escribir el caption completo
5. Generar los hashtags
6. Revisar que no haya voseo ni frases prohibidas

## Output esperado

Guardar en `posts/{slug}/copy.md`:

```markdown
# Copy: {tema} — {país}

---

## Slide 1 — Hook
**Titular:** [máx 40 chars — en gráfica, color amarillo/naranja]
**Subtítulo:** [máx 60 chars — en gráfica, color blanco bold]
**Texto de apoyo:** [opcional — máx 80 chars — blanco regular]
**Badge país:** [texto del badge naranja, ej: "Guatemala 2026"]

---

## Slide 2 — Contexto
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 

---

## Slide 3 — Valor 1
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 

---

## Slide 4 — Valor 2
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 

---

## Slide 5 — Cierre + CTA
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 
**CTA gráfica:** [texto del botón/acción en la imagen, si aplica]

---

## Caption

[Línea 1 del hook]
[Línea 2 del hook]

[Desarrollo]

[CTA]

---

## Hashtags

#hashtag1 #hashtag2 ...
```
