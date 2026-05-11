# 🏛️ Proyecto: Alejandría Voice (Módulo SGCA)
# Versión: 1.0 — Mayo 2026

## 1. Resumen del Sistema
Aplicación local de alto rendimiento diseñada para capturar la voz del Fundador de NEWCOOP como un activo intelectual. 
- **Entrada:** Micrófono vía Navegador.
- **Proceso:** Compresión y transcripción vía OpenAI Whisper.
- **Salida:** Escritura directa en el sistema de archivos local del Obsidian Vault.

## 2. Arquitectura Técnica (Modern Stack)
- **Frontend:** React 18 + Vite + TailwindCSS (o Vanilla CSS premium).
- **Backend:** Node.js (Express) + `openai` SDK.
- **Persistencia:** Sistema de archivos local (`fs-extra`).
- **Variables de Entorno:** `.env` (Controla rutas absolutas y Keys).

---

## 3. Estructura del Proyecto Sugerida
```text
/alejandria-voice
├── /backend
│   ├── server.js
│   ├── package.json
│   └── .env  <-- RUTA_VAULT, OPENAI_API_KEY
├── /frontend
│   ├── src/
│   ├── package.json
│   └── vite.config.js
└── README.md
```

---

## 🚀 PROMPT MAESTRO PARA INICIALIZAR EL SISTEMA
*(Copia este bloque y pégalo al asistente de IA cuando quieras construirlo)*

> "Actúa como un Ingeniero Senior Full Stack. Vamos a construir 'Alejandría Voice', una micro-app local para capturar audio y transcribirlo directamente a un Obsidian Vault.
> 
> **REQUISITOS TÉCNICOS:**
> 1. **Estructura:** Crear una carpeta `/backend` con Express y una carpeta `/frontend` con React+Vite.
> 2. **Lógica Backend:** 
>    - Debe tener un endpoint `POST /api/transcribe` que reciba un Blob de audio.
>    - Debe usar la API de Whisper de OpenAI para transcribir el audio.
>    - Tras obtener la transcripción, debe realizar DOS escrituras directas usando la ruta configurada en el `.env` (VARIABLE: `VAULT_PATH`):
>       a) Guardar `.mp3` en `${VAULT_PATH}/02_RECURSOS/Audios/grabacion_[timestamp].mp3`.
>       b) Crear `.md` en `${VAULT_PATH}/02_RECURSOS/Ingestas/ingesta_audio_[timestamp].md` con el frontmatter YAML necesario para el sistema de conocimiento y el enlace embebido al audio: `![[grabacion_[timestamp].mp3]]`.
> 3. **Lógica Frontend:**
>    - Interfaz Premium (Modo Oscuro / Minimalista).
>    - Botón circular grande de RECORD/STOP con visualización de ondas (Waveform simple).
>    - Uso de `MediaRecorder API` para capturar audio del micrófono.
>    - Estado visual claro: "Grabando" -> "Procesando (Whisper)" -> "✅ Guardado en Obsidian".
> 
> **ENTREGABLES INMEDIATOS:**
> - Genera el archivo `package.json` de ambas carpetas con las dependencias necesarias (`express`, `cors`, `multer`, `openai`, `dotenv`, `axios`).
> - Genera el código completo de `backend/server.js` y un `frontend/src/App.jsx` funcional."

---

## ⚙️ Configuraciones Clave para Obsidian
Para que el audio se reproduzca directamente en Obsidian sin configurar nada más, el archivo `.md` generado por Alejandría Voice debe tener esta estructura exacta:

```markdown
---
tags: [ingesta, audio, alejandria_voice]
fuente: "Grabación de Voz Directa"
fecha_captura: YYYY-MM-DD HH:mm
estado: Pendiente
---

## 🎙️ Audio Original
![[grabacion_20260510_2045.mp3]]

## 📄 Transcripción Whisper (Crudo)
[Aquí se pega el texto devuelto por la API de OpenAI]

---
*Generado automáticamente por Alejandría Voice*
```

*(Nota técnica para el futuro: Asegúrate de que la carpeta `02_RECURSOS/Audios/` exista en tu Obsidian o que el script la cree automáticamente).*
