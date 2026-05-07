# Arquitectura General de la Plataforma Multimedia

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe la arquitectura de software implementada para la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

La solución fue diseñada bajo un enfoque moderno basado en microservicios, permitiendo desacoplamiento, escalabilidad, mantenibilidad y automatización de despliegues.

La arquitectura busca soportar:

- Gestión centralizada de contenido multimedia.
- Streaming eficiente de videos.
- Administración mediante BackOffice.
- Consumo desde portal web.
- Escalabilidad futura.
- Automatización CI/CD.
- Contenedorización y despliegue cloud-ready.

---

# 2. Estilo Arquitectónico

La solución adopta una arquitectura basada en microservicios, donde cada componente posee responsabilidades específicas e independientes.

## Principales características arquitectónicas

| Característica | Descripción |
|---|---|
| Arquitectura | Microservicios |
| Comunicación | APIs REST |
| Contenedorización | Docker |
| Streaming | HLS |
| Automatización | CI/CD |
| Gestión código | Git |
| Escalabilidad | Horizontal |
| Despliegue | Cloud Ready |

---

# 3. Arquitectura de Alto Nivel

La plataforma está compuesta por los siguientes dominios principales:

- Portal Web
- BackOffice Administrativo
- Microservicios Backend
- Servicio de Procesamiento Multimedia
- Streaming HLS
- Persistencia de datos
- Infraestructura DevOps

---

# 4. Componentes Principales

| Componente | Responsabilidad |
|---|---|
| Portal Web | Consumo de contenido multimedia |
| BackOffice | Administración de contenido |
| API Backend | Exposición de APIs REST |
| Servicio Multimedia | Procesamiento de videos |
| Servicio Streaming | Distribución multimedia |
| Base de Datos | Persistencia de información |
| Storage Multimedia | Almacenamiento de videos |
| CI/CD | Automatización de despliegues |
| Repositorios Git | Gestión de código fuente |

---

# 5. Arquitectura Lógica

## 5.1 Portal Web

Aplicación encargada del consumo de contenido multimedia por parte de los usuarios finales.

### Responsabilidades

- Navegación de contenido.
- Reproducción multimedia.
- Visualización de formaciones.
- Consulta de contenido.
- Consumo de APIs backend.

---

## 5.2 BackOffice Administrativo

Aplicación administrativa encargada de la gestión operativa del contenido multimedia.

### Responsabilidades

- Registro de contenido.
- Administración de videos.
- Gestión de categorías.
- Organización de publicaciones.
- Administración del portal.

---

## 5.3 Microservicios Backend

Conjunto de servicios independientes encargados de la lógica de negocio.

### Características

- APIs REST.
- Desacoplamiento funcional.
- Escalabilidad independiente.
- Contenedorización.
- Integración CI/CD.

### Posibles microservicios

| Microservicio | Responsabilidad |
|---|---|
| mcsv-auth | Autenticación y autorización |
| mcsv-content | Gestión de contenido |
| mcsv-media | Gestión multimedia |
| mcsv-stream | Streaming HLS |
| mcsv-admin | Funcionalidades administrativas |

---

## 5.4 Servicio de Procesamiento Multimedia

Componente encargado de procesar los archivos de video cargados en la plataforma.

### Funcionalidades

- Conversión MP4 a HLS.
- Segmentación multimedia.
- Generación de playlists.
- Optimización de reproducción.

### Herramientas utilizadas

- FFmpeg

---

## 5.5 Servicio de Streaming

Responsable de la distribución de contenido multimedia mediante HLS.

### Funcionalidades

- Entrega de playlists `.m3u8`
- Distribución de segmentos `.ts`
- Streaming adaptativo
- Reproducción optimizada

---

# 6. Flujo General de la Solución

## Flujo funcional principal

```text
Administrador
    ↓
BackOffice
    ↓
Carga de Video
    ↓
Procesamiento FFmpeg
    ↓
Generación HLS
    ↓
Storage Multimedia
    ↓
Portal Web
    ↓
Usuario Final