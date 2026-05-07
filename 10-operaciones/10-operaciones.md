# Manual Operativo de la Plataforma

---

# 1. Introducción

## 1.1 Objetivo

El presente documento describe las actividades operativas básicas necesarias para administrar, monitorear y mantener la Plataforma Centralizada de Gestión y Distribución de Contenido Multimedia Formativo.

El objetivo es proporcionar lineamientos técnicos para:

- Operación de servicios.
- Monitoreo básico.
- Diagnóstico de incidencias.
- Gestión de contenedores.
- Validación de despliegues.
- Administración operativa.

---

# 2. Alcance

Este documento aplica para:

- Frontend Portal.
- Frontend BackOffice.
- Microservicios backend.
- Servicios multimedia.
- Componentes de streaming.
- Infraestructura Docker.

---

# 3. Arquitectura Operativa

## Componentes principales

| Componente | Función |
|---|---|
| Portal Web | Consumo multimedia |
| BackOffice | Administración |
| Microservicios | Backend |
| Streaming HLS | Distribución multimedia |
| Docker | Contenedores |
| Storage | Archivos multimedia |

---

# 4. Ambientes

La solución contempla múltiples ambientes operativos.

| Ambiente | Objetivo |
|---|---|
| Development | Desarrollo |
| QA | Validación |
| Production | Producción |

---

# 5. Inicio de Servicios

Los componentes pueden ser ejecutados mediante Docker.

## Ejecución general

```bash id="0o1kxz"
docker compose up -d