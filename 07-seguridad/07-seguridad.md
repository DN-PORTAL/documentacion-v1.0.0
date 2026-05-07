# Arquitectura y Controles de Seguridad

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe los mecanismos y controles de seguridad implementados para la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

La estrategia de seguridad fue diseñada para proteger:

- Acceso a la plataforma.
- APIs backend.
- Contenido multimedia.
- Información administrativa.
- Comunicación entre componentes.
- Gestión de usuarios y permisos.

---

# 2. Objetivos de Seguridad

La arquitectura de seguridad busca garantizar:

- Autenticación de usuarios.
- Protección de APIs.
- Control de acceso.
- Seguridad del contenido multimedia.
- Protección de credenciales.
- Separación de permisos.
- Reducción de accesos no autorizados.

---

# 3. Arquitectura de Seguridad

La solución implementa una arquitectura de seguridad basada en:

| Componente | Función |
|---|---|
| JWT | Autenticación |
| Roles y permisos | Autorización |
| APIs protegidas | Control acceso |
| Interceptores | Validación requests |
| Variables seguras | Protección credenciales |
| HTTPS | Comunicación segura |

---

# 4. Autenticación

La plataforma utiliza autenticación basada en JWT (JSON Web Token).

## Objetivos

- Validar identidad usuarios.
- Proteger endpoints.
- Mantener sesiones desacopladas.
- Integración frontend/backend.

---

## Flujo de autenticación

```text id="j1pwv5"
Usuario
   ↓
Login
   ↓
Validación credenciales
   ↓
Generación JWT
   ↓
Frontend almacena token
   ↓
Request autenticado