# GEMINI.md — Instrucciones para el Agente

## Contexto obligatorio al iniciar cualquier sesión

Antes de responder cualquier cosa, lee estos archivos en este orden:

1. 00_CONTEXTO/MODO_MMOOD.md
2. 00_CONTEXTO/arquitectura_sistema.md
3. 00_CONTEXTO/estado_actual.md

## Comandos de Flujo Diario/Semanal (Core)

/buendia — Inicia el día creando la nota con prioridades precargadas (cashflow, WALA, SOMU)
/cierre — Procesa diario de hoy, distribuye to-dos, actualiza estado y al final EJECUTA AUTOMÁTICAMENTE /aprendizaje_diario
/revision — Ejecuta revisión semanal (completado vs prometido, cashflow, hipótesis)
/actualizar-estado — Actualiza estado_actual.md analizando los diarios recientes
/sync — Sincroniza en caliente el diario de hoy, distribuye to-dos y actualiza estado sin cerrar el día
/contexto — Actualiza el contexto de un proyecto específico tras una decisión o cambio

## Comandos de Foco y Análisis

/anti-dispersion — (o /foco) Analiza frentes abiertos y fuerza a pausar para priorizar cashflow
/drift — Compara intenciones vs ejecución de los últimos 30 días
/ideas — (o /patrones) Escanea diarios de los últimos 14 días y detecta patrones o ideas no ejecutadas

## Comandos de Registro e Integración (SGCA)
> **IMPORTANTE:** Para ejecutar `/ingestar`, `/destilar`, `/contentar`, `/aprendizaje_diario` o `/indexar`, la IA DEBE consultar obligatoriamente `00_CONTEXTO/especificacion_sistema_conocimiento.md` y `00_CONTEXTO/prompts_sgca.md`. 
> **Para `/buendia`, `/cierre` y `/sync`, la IA DEBE consultar `00_CONTEXTO/prompts_flujo_core.md`.**

/ingestar [texto] — La IA extrae semillas y citas literales a '02_RECURSOS/Ingestas/'.
/destilar [archivo_ingesta] + [semilla] + [reflexión] — Crea Nota Atómica en '03_CONOCIMIENTO/aprendizajes/' aplicando ruteamiento inteligente (Personal/Negocio/Técnico).
/contentar [concepto] — Genera un brief de video ejecutable para WALA o Marca Personal a partir de un concepto destilado.
/aprendizaje_diario — Módulo automático de revisión espaciada que se ejecuta al final del comando `/cierre`.
/indexar — Agrupa todos los conceptos en `03_CONOCIMIENTO/mapa_conceptual.md` para uso rápido en consultoría.
/integrar — Procesa output de IA externa (NotebookLM/Perplexity) y lo distribuye en el vault
/generar-pdf [proyecto] — Crea reporte markdown estructurado, listo para exportar a PDF
/reunion — Estructura notas en bruto y extrae to-dos/compromisos
/ficha — Registra cualquier recurso, contacto o herramienta en el sistema
/archivo — Registra un archivo de referencia (Excel, PDF, imagen) en Drive/recursos_drive.md
/citas [fuente/libro] — Busca y consolida todas las semillas y conceptos destilados de un libro o autor específico.

## Comandos de Proyecto (Briefing)

/wala — Briefing WALA completo: contexto + entregas + bloqueos
/aldeas — Briefing Aldeas Infantiles
/tesis — Briefing Tesis de Maestría
/somu — Briefing SOMU
/contenido — Gestor de contenido: inventario, guiones y publicaciones pendientes
