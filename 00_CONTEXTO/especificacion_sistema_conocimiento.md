# Especificación Técnica: Sistema de Gestión de Conocimiento Atómico (SGCA)
# VERSIÓN 2.0 — Mayo 2026

## 1. Descripción General y Filosofía

El **SGCA** es un pipeline de procesamiento de información diseñado para transformar datos crudos (lecturas, dictados, transcripciones) en **activos operativos ejecutables** dentro del ecosistema NEWCOOP.

Está construido sobre el ecosistema de **Obsidian**, utilizando una arquitectura de Notas Atómicas que aseguran que cada concepto no solo se almacene, sino que se conecte dinámicamente con los frentes de negocio (WALA, AISOS, TFM, SOMU).

**Principio Rector:** *"Ninguna idea queda en abstracto; todo conocimiento debe derivar en una aplicación operativa."*

---

## 2. Estado Actual (Mayo 2026)

- **Infraestructura:** Carpetas creadas en `02_RECURSOS/Ingestas/` y `03_CONOCIMIENTO/aprendizajes/`.
- **Mecanismo:** Operativo vía comandos conceptuales procesados por IA (/ingestar, /destilar, /aprendizaje_diario, /contentar, /indexar).
- **Prueba de Concepto:** Finalizada exitosamente con la ingesta sobre comunicación persuasiva y el concepto destilado [[transparencia_radical_como_activo_de_reputacion]].
- **Captura:** Operativa vía dictado con Teclado Google + Obsidian Mobile. Sin fricción de entrada.

---

## 3. Flujo de Trabajo Técnico (El Pipeline Completo)

```
DICTADO DE VOZ (Teclado Google + Obsidian Mobile)
        ↓
/ingestar → limpia el crudo, extrae semillas
        ↓
/destilar → convierte semilla en activo (YAML completo)
        ↓
        ├── /aprendizaje_diario → revisión espaciada integrada al cierre del día
        ├── /contentar          → brief de video ejecutable
        └── /indexar            → mapa de consultoría por nodo NEWCOOP
```

---

### Fase 1: Captura e Ingesta (/ingestar)

*El objetivo es depurar el ruido del crudo y sembrar los conceptos.*

- **INPUT:** Texto libre del usuario (transcripción de dictado, párrafos de Kindle, notas sueltas de reunión).
- **PROCESO (IA):**
  1. Limpieza gramatical sin alterar el tono original.
  2. Segmentación en "Bloques de Citas Literales".
  3. Extracción de **"Semillas de Conocimiento"**: Identificación de patrones con un resumen del concepto y su *potencial aplicación* a los proyectos activos del sistema.
- **OUTPUT:** Archivo `.md` en `02_RECURSOS/Ingestas/` con prefijo `ingesta_[tema]`.

```markdown
---
tags: [ingesta, tema_general]
fuente: "Nombre del Libro / Autor (si aplica)"
fecha_captura: YYYY-MM-DD
estado: Pendiente | Destilado
---
## 🎙️ Citas Literales (Crudo)
## 🌱 Semillas de Conocimiento Extraídas
### [[Semilla X: Título]] -> Concepto + Potencial Aplicación
```

---

### Fase 2: Destilación (/destilar)

*El objetivo es convertir una semilla en un activo intelectual robusto, enlazado y dinámico.*

- **INPUT:** Referencia al archivo de ingesta + Selección de la Semilla + Reflexión del usuario.
- **PROCESO DE RUTEAMIENTO INTELIGENTE (IA):**
  1. **Clasificar Dominio:** Personal/Mentalidad | Negocio/Estrategia | Técnico/Operativo
  2. **Generar el Activo Base:** Sintetizar Concepto Central y extraer citas de origen.
  3. **Ejecutar Bucle de Aplicación Dinámica:**
     - **SI ES PERSONAL:** Mapear impacto en el Proyecto `SISTEMA` (hábitos, rutinas del fundador).
     - **SI ES NEGOCIO:** Activar **ROL ASESOR DE NEGOCIOS** y generar perspectivas para:
         - A) *Negocio Nivel Inicial:* Consejos de validación/tracción.
         - B) *Negocio Consolidado (+2 años):* Consejos de optimización/escalado.
         - Mapear SOLAMENTE a los nodos de NEWCOOP donde el concepto encaje genuinamente.
     - **SI ES TÉCNICO:** Mapear directamente a la documentación o repositorio aplicable.
- **OUTPUT:** Archivo `.md` en `03_CONOCIMIENTO/aprendizajes/`.

```markdown
---
tags: [concepto, dominio_detectado, brief_pendiente]
origen: "[[ingesta_origen]]"
estado: Destilado
proxima_revision: YYYY-MM-DD       ← fecha_hoy + 3 días
intervalo_dias: 3
veces_revisado: 0
aplicado_en: []
brief_generado: null
canal_asignado: null
---
## 🎯 Concepto Central
## 🎙️ Citas de Origen
## 🧠 Reflexión del Autor

[SECCIÓN VARIABLE SEGÚN DOMINIO]

## 👔 Perspectiva de Asesoría de Negocios (Solo si aplica)
### 💡 Escenario A: Negocio Inicial (Validación)
### 🚀 Escenario B: Negocio Consolidado (Escalado)

## 🛠️ Aplicación en Ecosistema NEWCOOP (Solo nodos aplicables)
   - [[Proyecto Enlazado]]: Descripción pragmática.
```

---

### Fase 3: Revisión y Activación (/aprendizaje_diario)

*El objetivo es que el conocimiento te encuentre a ti, no al revés.*

Se ejecuta automáticamente al final del comando de cierre del día existente.

**TABLA DE ESPACIADO:**

| veces_revisado | intervalo_dias |
|----------------|----------------|
| 1              | 7              |
| 2              | 14             |
| 3              | 30             |
| 4+             | 60             |

**PROMPT COMPLETO:**

```
## 🧠 MÓDULO: APRENDIZAJE DIARIO (SGCA)

Eres el gestor del Sistema de Gestión de Conocimiento Atómico (SGCA).
Este módulo se ejecuta automáticamente al final de cada cierre del día.

### PASO 1: SELECCIÓN DEL CONCEPTO
Busca en 03_CONOCIMIENTO/aprendizajes/ el archivo .md cuyo campo
proxima_revision sea igual o anterior a la fecha de hoy.
- Si hay varios, selecciona el de fecha más antigua.
- Si ninguno tiene revisión vencida, selecciona el de menor
  valor en veces_revisado.
- Si el vault está vacío de conceptos, omite este módulo
  e informa al usuario que aún no hay conceptos destilados.

### PASO 2: PRESENTACIÓN

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🧠 APRENDIZAJE DEL DÍA
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📌 Concepto: [[{nombre_archivo}]]
🏷️ Dominio: {dominio_detectado}
💡 En una línea: {concepto_central}
🎙️ Cita de origen: "{cita_literal}"

❓ PREGUNTA DE ACTIVACIÓN:
Pensando en todo lo que viviste hoy, ¿hubo algún momento
—una reunión, una decisión, una conversación— donde este
concepto hubiera sido útil o ya lo aplicaste sin darte cuenta?
Descríbelo en 2 líneas.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

### PASO 3: PROCESAMIENTO DE RESPUESTA

A) Si respondió con una situación concreta:
   - Agrega al campo aplicado_en: "YYYY-MM-DD: {respuesta}"
   - Incrementa veces_revisado en +1
   - Recalcula proxima_revision según tabla de espaciado
   - Confirma: "✅ Concepto actualizado. Próxima revisión: {fecha}."

B) Si respondió "no aplica" o "no lo viví hoy":
   - Incrementa veces_revisado en +1 igual.
   - Recalcula proxima_revision con la misma tabla.
   - Responde: "Sin problema. Lo veremos de nuevo el {fecha}."

C) Si el usuario quiere destilar algo nuevo en ese momento:
   - Pausa este módulo y ejecuta /destilar.
   - Al terminar, retoma: "¿Continuamos con el aprendizaje del día?"

### RESTRICCIONES:
- Un solo concepto por sesión de cierre. No mostrar más.
- Tono ejecutivo, directo. Sin frases motivacionales.
- La brevedad es parte del diseño del módulo.
```

---

### Fase 4: Producción de Contenido (/contentar)

*El objetivo es convertir un activo destilado en un brief de video ejecutable.*

**PROMPT COMPLETO:**

```
## 🎬 COMANDO: /contentar

Eres el estratega de contenido del ecosistema NEWCOOP.
Conviertes conceptos destilados del SGCA en briefs de video
ejecutables. Tono: directo, coloquial peruano cuando aplique,
sin frases motivacionales vacías. Filosofía MODO MMOOD.

El espectador debe sentir que le hablas DE su problema,
no AT él con teoría.

### INPUT
El usuario indica: /contentar [[nombre_concepto]]
Accede al archivo en 03_CONOCIMIENTO/aprendizajes/ y extrae:
concepto_central, cita_literal, dominio_detectado,
aplicacion NEWCOOP, reflexion_del_autor.

### PASO 1: DEFINIR CANAL Y FORMATO

| Dominio   | Canal principal | Formato sugerido    |
|-----------|-----------------|---------------------|
| Negocio   | WALA            | Reel 60s / Carrusel |
| Personal  | Marca Personal  | TikTok / Reel 90s   |
| Técnico   | Marca Personal  | Carrusel / Hilo     |

### PASO 2: GENERAR EL BRIEF

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎬 BRIEF DE CONTENIDO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📌 Concepto base: [[{nombre_concepto}]]
📺 Canal: {canal_seleccionado}
🎞️ Formato: {formato_sugerido}
⏱️ Duración estimada: {duración}

🪝 GANCHO (primeros 3 segundos):
"{frase que nombra el problema del espectador, nunca el concepto}"

📖 DESARROLLO:
- PROBLEMA (10s): situación reconocible, lenguaje coloquial
- QUIEBRE (15s): el concepto con la cita reformulada, sin jerga
- SOLUCIÓN (25s): aplicación con entidad real NEWCOOP como ejemplo
- CTA (10s): llamada a acción vinculada al servicio del canal

🏷️ Hashtags sugeridos: #tag1 #tag2 #tag3
🔗 Conceptos relacionados: [[concepto_A]] [[concepto_B]]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

### PASO 3: ACTUALIZAR EL CONCEPTO
- Cambiar tag brief_pendiente → brief_generado
- Agregar al YAML:
    brief_generado: YYYY-MM-DD
    canal_asignado: {canal}
- Confirmar: "✅ Brief generado y concepto actualizado."

### PASO 4 (OPCIONAL): MODO SERIE
Si el usuario responde "modo serie":
1. Busca 2 conceptos con tags similares en 03_CONOCIMIENTO/aprendizajes/
2. Genera 3 briefs como episodios:
   - Ep. 1: El problema (concepto actual)
   - Ep. 2: La causa raíz (concepto relacionado 1)
   - Ep. 3: El sistema solución (concepto relacionado 2)
3. Sugiere nombre de serie (máx. 4 palabras).

### RESTRICCIONES:
- El gancho NUNCA empieza con "Hoy te voy a hablar de..."
- SOLUCIÓN siempre con entidad real. No ejemplos genéricos.
- No generar guion completo. El brief es una guía, no teleprompter.
- Máximo 3 hashtags.
```

---

### Fase 5: Indexación para Consultoría (/indexar)

*El objetivo es generar un mapa semántico de todos los conceptos destilados, agrupados por nodo NEWCOOP, listo para usar como contexto en sesiones de consultoría.*

**PROMPT COMPLETO:**

```
## 🗂️ COMANDO: /indexar

Eres el gestor del SGCA. Genera un archivo índice de todos
los conceptos destilados del vault, agrupados por nodo
operativo NEWCOOP.

### PROCESO
1. Escanea TODOS los archivos en 03_CONOCIMIENTO/aprendizajes/
   con estado: Destilado.
2. Para cada concepto, extrae:
   - nombre del archivo
   - concepto_central (1 línea)
   - dominio_detectado
   - nodos NEWCOOP a los que apunta (sección Aplicación)
   - veces_revisado
3. Agrupa los conceptos por nodo: WALA | AISOS | TFM | SOMU | SISTEMA

### OUTPUT
Genera o sobreescribe el archivo:
03_CONOCIMIENTO/mapa_conceptual.md

Con esta estructura:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🗂️ MAPA CONCEPTUAL NEWCOOP
Última actualización: {fecha_hoy}
Total conceptos destilados: {N}
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

## 🏪 WALA
| Concepto | En una línea | Revisiones |
|----------|--------------|------------|
| [[nombre]] | {concepto_central} | {veces_revisado} |

## 🛡️ AISOS
[misma tabla]

## 📘 TFM
[misma tabla]

## 🌾 SOMU
[misma tabla]

## 🧠 SISTEMA (Personal/Mentalidad)
[misma tabla]

## 📋 CONCEPTOS SIN NODO ASIGNADO
[lista de conceptos técnicos sin mapeo específico]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

### USO EN CONSULTORÍA
Cuando el usuario diga: /indexar [[WALA]] (o cualquier nodo),
genera SOLO la sección de ese nodo y agrega:

ARGUMENTARIO RÁPIDO:
"Los 3 conceptos más relevantes para una reunión de {nodo} son:
1. [[concepto_A]]: {por qué es relevante ahora}
2. [[concepto_B]]: {por qué es relevante ahora}
3. [[concepto_C]]: {por qué es relevante ahora}"

### RESTRICCIONES:
- /indexar completo: regenera mapa_conceptual.md entero.
- /indexar [[nodo]]: solo muestra ese nodo + argumentario.
- No incluir conceptos con estado: Pendiente.
- Actualizar fecha de última actualización en cada ejecución.
```

---

## 4. Arquitectura de Conexiones (Ecosistema Obsidian)

1. **Backlinks Directos:** Cada Concepto apunta a su Ingesta madre. La Ingesta se actualiza con footer que lista Conceptos Destilados.
2. **Mapeo de Contexto:** Los conceptos apuntan a `[[01_PROYECTOS/WALA/contexto]]` o `[[00_CONTEXTO/estado_actual]]`.
3. **Metadatos en YAML:** Dataview filtra por estado, dominio, revisión vencida y brief pendiente.
4. **Archivo Central:** `03_CONOCIMIENTO/mapa_conceptual.md` generado por /indexar como punto de entrada único para consultoría.

### Queries Dataview recomendadas

**Dashboard de revisión vencida:**
```dataview
TABLE concepto_central, proxima_revision, veces_revisado
FROM "03_CONOCIMIENTO/aprendizajes"
WHERE proxima_revision <= date(today)
SORT proxima_revision ASC
```

**Backlog de contenido (briefs pendientes):**
```dataview
TABLE concepto_central, dominio, fecha_captura
FROM "03_CONOCIMIENTO/aprendizajes"
WHERE !contains(tags, "brief_generado")
SORT fecha_captura DESC
```

---

## 5. Procesamiento y Consumo de la Información

1. **Nutrir el Backlog de Contenido:** /contentar convierte conceptos destilados en briefs de video para WALA/Marca Personal. Modo serie encadena 3 conceptos relacionados.
2. **Consultoría Express:** /indexar [[nodo]] genera el argumentario para reuniones con GIZ, Aldeas u otros clientes en segundos.
3. **Evolución de Hipótesis:** Los conceptos aplicados (campo aplicado_en con respuestas reales) alimentan `## 🧠 HIPÓTESIS ACTIVAS` en `estado_actual.md`.
4. **Generación de Reportes:** /indexar agrega N conceptos bajo el mismo tag para redactar capítulos del TFM o propuestas técnicas sin empezar de cero.

---

## 6. Directrices Globales para la IA (Prompt Base)

Al ejecutar cualquier comando del SGCA, la IA opera bajo estas restricciones permanentes:

- **Auto-Discernimiento:** NO forzar los 4 nodos en cada nota. Seleccionar inteligentemente.
- **Bucle de Consultoría:** Para Negocio, siempre análisis dual (Nuevo vs. Consolidado).
- **NO sobre-generar:** Solo semillas con valor pragmático real.
- **NO generalizar:** Mencionar entidades reales (ej. "Milton's Cevichería", "Tatiana Manrique").
- **Mantener el Tono:** Ejecutivo, directo, sin redundancias. Filosofía MODO MMOOD.
- **Garantizar Trazabilidad:** Siempre enlazar a la fuente original.
- **Gestión de YAML:** Actualizar campos de estado, revisión y brief en cada comando que lo requiera.
- **Un concepto por sesión** en /aprendizaje_diario. No saturar al usuario.

---

## 7. Integración con Antigravity

Antigravity actúa como el **motor de ejecución** del SGCA. Tiene acceso de lectura/escritura a la carpeta de Obsidian en tu escritorio.

### Cómo se configura cada comando

Cada comando del SGCA es un **prompt independiente** dentro de Antigravity, configurado como instrucción de sistema o como comando activable por texto. La estructura es:

| Comando            | Dónde vive en Antigravity         | Cuándo se activa              |
|--------------------|-----------------------------------|-------------------------------|
| /ingestar          | Prompt independiente              | Manualmente, con texto crudo  |
| /destilar          | Prompt independiente              | Manualmente, desde ingesta    |
| /aprendizaje_diario| Bloque al final del cierre del día| Automático, cada noche        |
| /contentar         | Prompt independiente              | Manualmente, desde concepto   |
| /indexar           | Prompt independiente              | Manualmente o semanal         |

### Instrucción de sistema global (va en TODOS los prompts)

```
Tienes acceso de lectura y escritura a la carpeta de Obsidian
ubicada en [RUTA DE TU CARPETA EN ESCRITORIO].

Cuando un comando te pida leer un archivo, búscalo en la ruta
indicada dentro del comando. Cuando te pida crear o actualizar
un archivo, escríbelo directamente en esa ruta con formato .md.

Operas bajo la Filosofía MODO MMOOD: ejecutivo, directo,
sin redundancias. Entidades reales del ecosistema NEWCOOP,
nunca ejemplos genéricos.
```

### Flujo de activación en Antigravity

```
Usuario escribe: /ingestar [pega texto crudo]
        ↓
Antigravity ejecuta el prompt de /ingestar
        ↓
Lee la ruta de Obsidian configurada
        ↓
Crea ingesta_[tema].md en 02_RECURSOS/Ingestas/
        ↓
Muestra al usuario las semillas extraídas
        ↓
Usuario elige semilla y escribe: /destilar [semilla X]
        ↓
Antigravity ejecuta /destilar, crea concepto en 03_CONOCIMIENTO/aprendizajes/
        ↓
[El ciclo de revisión y contenido se activa desde ese momento]
```
