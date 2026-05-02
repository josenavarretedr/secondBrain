---
name: integrador_ia
description: Integrador de IA Externa
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Después de cualquier sesión en Perplexity, NotebookLM, ChatGPT, Claude o AI Studio.

## Prompt

@workspace
Voy a pegarte el output de una sesión externa de IA.
Herramienta usada: [Perplexity / NotebookLM / ChatGPT / Claude / AI Studio]

[PEGA EL CONTENIDO AQUÍ]

PASO 1 — Identifica:

- Proyecto al que pertenece: [PROYECTO]
- Tipo de contenido:
  [ ] Decisión estratégica
  [ ] Estrategia / plan
  [ ] Investigación / datos
  [ ] Ideas sueltas
  [ ] To-dos concretos
  [ ] Recurso (imagen, doc, código)

PASO 2 — Genera el .md formateado para el vault:

- Si es estrategia → 01_PROYECTOS/[PROYECTO]/estrategias/[nombre_fecha].md
- Si es investigación → 01_PROYECTOS/[PROYECTO]/investigacion/[nombre].md
- Si es to-dos → directamente a to-dos_activos.md del proyecto
- Si son ideas sueltas → 02_DIARIO/[FECHA].md sección ideas

PASO 3 — Si genera to-dos concretos:
Agrégalos directamente a to-dos_activos.md con fecha límite sugerida

PASO 4 — Si hay hipótesis nuevas:
Propón agregarlas a contexto.md del proyecto con nivel de confianza

PASO 5 — Confirma:

- Archivos creados
- Archivos modificados
- Nada se pierde

