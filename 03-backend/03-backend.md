# Documentación Técnica Backend

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe la arquitectura técnica y los componentes backend implementados para la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

La solución backend fue diseñada utilizando una arquitectura basada en microservicios, permitiendo desacoplamiento funcional, escalabilidad, mantenibilidad y despliegues independientes.

---

# 2. Arquitectura Backend

La plataforma backend está compuesta por múltiples microservicios especializados, cada uno con responsabilidades específicas.

## Características principales

| Característica | Descripción |
|---|---|
| Arquitectura | Microservicios |
| Comunicación | APIs REST |
| Lenguaje | Java |
| Framework | Spring Boot |
| Contenedorización | Docker |
| Seguridad | JWT |
| Integración | CI/CD |
| Procesamiento Multimedia | FFmpeg |

---

# 3. Objetivos Técnicos

La arquitectura backend fue diseñada para cumplir los siguientes objetivos:

- Separación de responsabilidades.
- Escalabilidad independiente.
- Despliegues desacoplados.
- Mantenibilidad.
- Integración sencilla.
- Facilidad de automatización.
- Procesamiento eficiente de contenido multimedia.

---

# 4. Microservicios Backend

## 4.1 Microservicios principales

| Microservicio | Responsabilidad |
|---|---|
| mcsv-auth | Autenticación y autorización |
| mcsv-content | Gestión de contenido |
| mcsv-media | Gestión multimedia |
| mcsv-stream | Distribución streaming HLS |
| mcsv-admin | Funcionalidades administrativas |

---

## 4.2 Responsabilidades funcionales

### mcsv-auth
Encargado de:

- Login de usuarios.
- Generación de JWT.
- Validación de autenticación.
- Gestión de permisos y roles.

---

### mcsv-content
Encargado de:

- Registro de contenido.
- Gestión de categorías.
- Gestión de metadata.
- Organización de publicaciones.

---

### mcsv-media
Encargado de:

- Carga de archivos multimedia.
- Validación de formatos.
- Gestión de archivos MP4.
- Procesamiento multimedia.

---

### mcsv-stream
Encargado de:

- Distribución HLS.
- Entrega de playlists `.m3u8`
- Distribución de segmentos `.ts`
- Streaming multimedia.

---

### mcsv-admin
Encargado de:

- Funcionalidades administrativas.
- Gestión operativa.
- Administración de contenido.

---

# 5. Tecnologías Utilizadas

| Categoría | Tecnología |
|---|---|
| Lenguaje | Java |
| Framework | Spring Boot |
| APIs | REST |
| Seguridad | JWT |
| Build Tool | Maven / Gradle |
| Contenedores | Docker |
| Versionamiento | Git |
| Streaming | HLS |
| Multimedia | FFmpeg |

---

# 6. Estructura Base de los Microservicios

Cada microservicio sigue una estructura desacoplada y organizada.

## Estructura sugerida

```text
src/
├── controller/
├── service/
├── repository/
├── entity/
├── dto/
├── mapper/
├── config/
├── security/
├── exception/
├── util/
└── integration/