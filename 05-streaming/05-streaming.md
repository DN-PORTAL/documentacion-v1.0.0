# Arquitectura de Streaming Multimedia HLS

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe la arquitectura y el flujo técnico implementado para el procesamiento y distribución de contenido multimedia mediante streaming HLS (HTTP Live Streaming).

La solución permite transformar videos cargados en formato MP4 hacia contenido optimizado para reproducción web adaptativa, permitiendo una mejor experiencia de usuario y una distribución multimedia más eficiente.

---

# 2. Objetivo de la Solución de Streaming

La implementación de streaming HLS tiene como finalidad:

- Centralizar distribución multimedia.
- Optimizar reproducción web.
- Mejorar experiencia usuario.
- Reducir buffering.
- Permitir streaming adaptativo.
- Facilitar escalabilidad futura.
- Compatibilidad multiplataforma.

---

# 3. Arquitectura General de Streaming

La solución multimedia está compuesta por:

| Componente | Responsabilidad |
|---|---|
| BackOffice | Carga de videos |
| Servicio Multimedia | Procesamiento de archivos |
| FFmpeg | Conversión multimedia |
| Storage | Almacenamiento HLS |
| Servicio Streaming | Distribución multimedia |
| Portal Web | Reproducción contenido |
| HLS.js | Reproducción HLS navegador |

---

# 4. Flujo General de Streaming

## Flujo funcional

```text
Administrador
      ↓
BackOffice
      ↓
Upload Video MP4
      ↓
Servicio Multimedia
      ↓
FFmpeg
      ↓
Generación HLS
      ↓
Storage Multimedia
      ↓
Portal Web
      ↓
Playback Streaming