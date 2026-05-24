---
description: Configura el instagram-pipeline en esta máquina (API key de OpenAI + guía de estilo + logos). Correr una vez por máquina.
argument-hint: (sin argumentos)
---

Tu tarea: configurar el instagram-pipeline en esta máquina por primera vez.

**Paso 1.** Crear el directorio de configuración persistente:

```bash
mkdir -p ~/.claude/instagram-pipeline
```

**Paso 2.** Verificar si ya existe `~/.claude/instagram-pipeline/.env`. Si **no existe**:
- Pedirle al usuario su API key de OpenAI
- Crear el archivo con el contenido:
  ```
  OPENAI_API_KEY=<la_clave_que_proporcionó>
  ```
- Confirmar que quedó guardada sin imprimirla

Si ya existe: preguntar si quiere reemplazarla.

**Paso 3.** Copiar el style guide preconfigurado si no existe:

```bash
cp "${CLAUDE_PLUGIN_ROOT}/assets/style-guide-template.md" ~/.claude/instagram-pipeline/style-guide.md
```

Si ya existe: no sobrescribir.

Avisar al usuario que el style guide ya viene con los colores (#FF671B, blanco, negro), tipografías (Montserrat + Poppins) y logos de Universidad Uk preconfigurados. Solo necesita completar la sección de **Carreras** y **CTAs** antes del primer pipeline.

**Paso 4.** Copiar los logos si no existen:

```bash
cp "${CLAUDE_PLUGIN_ROOT}/assets/logo.png" ~/.claude/instagram-pipeline/logo.png
cp "${CLAUDE_PLUGIN_ROOT}/assets/logo-negro.png" ~/.claude/instagram-pipeline/logo-negro.png
```

Si ya existen: no sobrescribir.

**Paso 5.** Resumir al usuario el estado de la configuración:

✅ Lo que ya está listo:
- API key de OpenAI
- Colores de marca (#FF671B, blanco, negro)
- Tipografías (Montserrat ExtraBold + Poppins Light)
- Logos copiados

⚠️ Lo que falta completar en `~/.claude/instagram-pipeline/style-guide.md`:
- Listado de carreras reales
- CTAs estándar y URL de conversión

Mostrar la ruta exacta del archivo para que el usuario sepa dónde editarlo.

Próximo paso: completar carreras y CTAs, luego correr `/instagram:post` con un brief.

**Reglas:**
- No imprimir la API key después de guardarla
- En Windows usar rutas con `$env:USERPROFILE` si los comandos bash no funcionan
