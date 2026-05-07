# Documentación Técnica Frontend

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe la arquitectura y los componentes frontend implementados para la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

La solución frontend fue desarrollada utilizando Angular como framework principal, permitiendo construir aplicaciones modernas, escalables y mantenibles para:

- Portal Web de consumo multimedia.
- BackOffice administrativo.
- Integración con APIs backend.
- Reproducción de contenido streaming HLS.

---

# 2. Arquitectura Frontend

La solución frontend está dividida en dos aplicaciones principales:

| Aplicación | Objetivo |
|---|---|
| Portal Web | Consumo de contenido multimedia |
| BackOffice | Administración del contenido |

---

# 3. Tecnologías Utilizadas

| Categoría | Tecnología |
|---|---|
| Framework | Angular |
| Lenguaje | TypeScript |
| Estilos | CSS / SCSS |
| HTTP Client | Angular HttpClient |
| Routing | Angular Router |
| Streaming | HLS.js |
| Gestión Estado | Services / RxJS |
| Build | Angular CLI |
| Contenedores | Docker |

---

# 4. Objetivos Técnicos

La arquitectura frontend fue diseñada considerando:

- Escalabilidad.
- Modularidad.
- Reutilización de componentes.
- Integración desacoplada con APIs.
- Mantenibilidad.
- Experiencia de usuario moderna.
- Adaptabilidad futura.

---

# 5. Arquitectura de Aplicaciones

## 5.1 Portal Web

Aplicación orientada al usuario final para el consumo de contenido multimedia.

### Funcionalidades

- Navegación de contenido.
- Reproducción multimedia.
- Visualización de charlas y formaciones.
- Consulta de categorías.
- Acceso centralizado.

---

## 5.2 BackOffice Administrativo

Aplicación orientada a la administración operativa del contenido.

### Funcionalidades

- Gestión de videos.
- Administración de categorías.
- Gestión de publicaciones.
- Organización del contenido.
- Administración del portal.

---

# 6. Estructura del Proyecto Angular

La solución frontend sigue una estructura modular organizada.

## Estructura base

```text
src/
├── app/
│   ├── core/
│   ├── shared/
│   ├── features/
│   ├── layouts/
│   ├── services/
│   ├── guards/
│   ├── interceptors/
│   ├── models/
│   └── pages/
├── assets/
├── environments/
└── styles/