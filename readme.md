# Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia

---

# 1. Introducción

Este repositorio contiene la documentación técnica y funcional de la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

La solución fue desarrollada como una Prueba de Concepto (PoC) con el objetivo de centralizar, administrar y distribuir contenido multimedia corporativo relacionado con:

- Charlas técnicas.
- Formaciones internas.
- Capacitaciones.
- Videos educativos.
- Contenido corporativo multimedia.

Anteriormente, este contenido era compartido mediante carpetas distribuidas, dificultando su organización, administración y acceso centralizado.

La plataforma implementa un ecosistema moderno basado en:

- Arquitectura de microservicios.
- Frontend Angular.
- APIs REST.
- Streaming HLS.
- Docker.
- CI/CD.
- DevOps.
- Inteligencia Artificial Generativa.

---

# 2. Objetivos de la Plataforma

La solución busca:

- Centralizar contenido multimedia.
- Facilitar acceso a formaciones.
- Administrar videos mediante BackOffice.
- Optimizar distribución multimedia.
- Implementar streaming moderno HLS.
- Automatizar despliegues.
- Proveer una arquitectura escalable.

---

# 3. Arquitectura General

## Componentes principales

| Componente | Función |
|---|---|
| Portal Web Angular | Consumo multimedia |
| BackOffice Angular | Administración |
| Microservicios Backend | Lógica negocio |
| APIs REST | Integración |
| Streaming HLS | Distribución multimedia |
| FFmpeg | Conversión videos |
| Docker | Contenedores |
| CI/CD | Automatización |

---

# 4. Tecnologías Utilizadas

| Categoría | Tecnología |
|---|---|
| Frontend | Angular |
| Backend | Java + Spring Boot |
| Streaming | HLS |
| Multimedia | FFmpeg |
| Contenedores | Docker |
| Versionamiento | Git |
| DevOps | CI/CD |
| Seguridad | JWT |
| Base de Datos | PostgreSQL |

---

# 5. Estructura de la Documentación

```text id="y9z6tk"
docs/
├── 01-overview/
├── 02-arquitectura/
├── 03-backend/
├── 04-frontend/
├── 05-streaming/
├── 06-devops/
├── 07-seguridad/
├── 08-apis/
├── 09-database/
├── 10-operaciones/
├── 11-ia-prompts/
└── README.md
```

- [01 - Overview](./01-overview/01-overview.md)
- [02 - Arquitectura](./02-arquitectura/02-arquitectura.md)
- [03 - Backend](./03-backend/03-backend.md)
- [04 - Frontend](./04-frontend/04-frontend.md)
- [05 - Streaming](./05-streaming/05-streaming.md)
- [06 - DevOps](./06-devops/06-devops.md)
- [07 - Seguridad](./07-seguridad/07-seguridad.md)
- [08 - APIs](./08-apis/08-apis.md)
- [09 - Database](./09-database/09-database.md)
- [10 - Operaciones](./10-operaciones/10-operaciones.md)
- [11 - IA y Prompts](./11-ia-prompts/11-ia-prompts.md)