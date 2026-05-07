# Documentación de APIs

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe las APIs REST implementadas para la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

Las APIs permiten la comunicación entre:

- Portal Web
- BackOffice Administrativo
- Microservicios Backend
- Servicios multimedia
- Componentes de streaming

---

# 2. Arquitectura de APIs

La solución implementa APIs REST desacopladas bajo arquitectura de microservicios.

## Características principales

| Característica | Descripción |
|---|---|
| Arquitectura | REST |
| Formato intercambio | JSON |
| Seguridad | JWT |
| Comunicación | HTTP/HTTPS |
| Arquitectura backend | Microservicios |

---

# 3. Base URL

## Ejemplo entorno desarrollo

```http id="z4j2wr"
http://localhost:8080/api/v1