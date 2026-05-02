---
name: registrar_archivo
description: Registrar Archivo de Referencia
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Cuando generas o recibes un recurso externo (Excel, PDF, imagen, estrategia).

## Prompt

@workspace
Acabo de generar/recibir este recurso:

- Nombre: [nombre descriptivo]
- Tipo: [Excel / PDF / imagen / estrategia / investigación / otro]
- Proyecto: [PROYECTO]
- Ubicación Drive: [link o "pendiente subir"]
- Resumen: [2 líneas de qué contiene]
- Generado con: [Perplexity / NotebookLM / ChatGPT / Claude / manual]

PASO 1 — Agrégalo a 01_PROYECTOS/[PROYECTO]/recursos_drive.md
en la tabla con columnas: Nombre | Tipo | Link | Resumen | Fecha | Herramienta

PASO 2 — Si es estrategia → crea archivo en 01_PROYECTOS/[PROYECTO]/estrategias/[nombre].md
con estructura: Objetivo / Acciones / Métricas / Fecha de revisión

PASO 3 — Si es investigación → registra también en 03_NOTEBOOK_LM/links_activos.md

PASO 4 — Si es imagen → registra en 04_RECURSOS/imagenes/ con nombre descriptivo

PASO 5 — Confirma qué archivos fueron modificados o creados.

