# Modelo de Datos y Persistencia

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe el modelo de datos y la estrategia de persistencia implementada para la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

La solución contempla almacenamiento estructurado para administrar:

- Usuarios.
- Contenido multimedia.
- Categorías.
- Metadata de videos.
- Información administrativa.
- Configuración funcional.

---

# 2. Objetivos del Modelo de Datos

La arquitectura de persistencia fue diseñada para:

- Centralizar información.
- Organizar contenido multimedia.
- Facilitar consultas.
- Mantener integridad de datos.
- Permitir escalabilidad futura.
- Soportar crecimiento funcional.

---

# 3. Arquitectura de Persistencia

La solución contempla una capa desacoplada de persistencia integrada con los microservicios backend.

## Componentes

| Componente | Responsabilidad |
|---|---|
| Base de Datos | Persistencia estructurada |
| Microservicios | Acceso y gestión datos |
| Repositories | Operaciones CRUD |
| Entidades | Modelo persistente |

---

# 4. Tecnologías Utilizadas

| Categoría | Tecnología |
|---|---|
| Base de datos | PostgreSQL |
| ORM | JPA / Hibernate |
| Lenguaje | Java |
| Framework | Spring Boot |
| Persistencia | Spring Data |

---

# 5. Modelo Conceptual

La plataforma administra diferentes dominios funcionales.

## Dominios principales

- Usuarios.
- Contenido multimedia.
- Videos.
- Categorías.
- Publicaciones.
- Seguridad.

---

# 6. Entidades Principales

| Entidad | Descripción |
|---|---|
| users | Usuarios del sistema |
| roles | Roles y permisos |
| content | Contenido multimedia |
| categories | Categorías |
| media | Archivos multimedia |
| publications | Publicaciones portal |

---

# 7. Entidad Usuarios

## Objetivo

Administrar usuarios autenticados de la plataforma.

---

## Campos principales

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID / Long | Identificador |
| username | String | Usuario |
| email | String | Correo |
| password | String | Contraseña cifrada |
| role_id | FK | Rol asociado |
| status | Boolean | Estado usuario |

---

# 8. Entidad Roles

## Objetivo

Gestionar permisos y perfiles de acceso.

---

## Campos principales

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID / Long | Identificador |
| name | String | Nombre rol |
| description | String | Descripción |

---

# 9. Entidad Content

## Objetivo

Administrar metadata del contenido multimedia.

---

## Campos principales

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID / Long | Identificador |
| title | String | Título |
| description | Text | Descripción |
| category_id | FK | Categoría |
| media_id | FK | Multimedia asociada |
| created_at | Timestamp | Fecha creación |

---

# 10. Entidad Categories

## Objetivo

Organizar contenido multimedia por categorías.

---

## Campos principales

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID / Long | Identificador |
| name | String | Nombre categoría |
| description | String | Descripción |

---

# 11. Entidad Media

## Objetivo

Administrar archivos multimedia y streaming.

---

## Campos principales

| Campo | Tipo | Descripción |
|---|---|---|
| id | UUID / Long | Identificador |
| original_file | String | Archivo original |
| hls_path | String | Ruta HLS |
| duration | Integer | Duración |
| status | String | Estado procesamiento |

---

# 12. Relaciones Principales

## Relaciones funcionales

```text id="j2p5zo"
User
  ↓
Role

Content
  ↓
Category

Content
  ↓
Media