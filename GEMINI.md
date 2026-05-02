# GEMINI.md — Instrucciones para el Agente

## Contexto obligatorio al iniciar cualquier sesión

Antes de responder cualquier cosa, lee estos archivos en este orden:

1. 00_CONTEXTO/MODO_MMOOD.md
2. 00_CONTEXTO/arquitectura_sistema.md
3. 00_CONTEXTO/estado_actual.md

## Comandos base

/contexto — carga 00_CONTEXTO/ completo
/hoy — genera diario con to-dos de TODOS los proyectos
/cierre — procesa diario y distribuye

## Comandos por proyecto

/wala — briefing WALA: contexto + to-dos + estrategias pendientes
/aldeas — briefing Aldeas Infantiles
/tesis — briefing tesis + NotebookLM pendientes
/somu — briefing SOMU
/contenido — videos pendientes + plan de publicaciones

## Comandos especiales

/integrar — "toma este resumen de NotebookLM/Perplexity y distribúyelo"
/generar-pdf [proyecto] — crea PDF desde estrategia + imágenes Drive
/ideas — escanea vault, detecta patrones no ejecutados
/drift — compara intenciones vs acciones (30 días)
