# Clínica Veterinaria 🐾

[![Java](https://img.shields.io/badge/Java_21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React_19-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Couchbase](https://img.shields.io/badge/Couchbase-EA2328?style=for-the-badge&logo=couchbase&logoColor=white)](https://www.couchbase.com/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

---

## 👋 Para recruiters

Aplicación fullstack para la gestión de una clínica veterinaria (usuarios, mascotas y tratamientos), construida con **Java + Spring Boot** en el backend y **React + TypeScript** en el frontend, con **Couchbase** como base de datos NoSQL documental. Desplegada de forma autónoma en infraestructura cloud gratuita.

**¿Qué demuestra este proyecto?**

- ✅ Diseñar e implementar una API REST en **Java + Spring Boot** sobre una base de datos NoSQL documental (**Couchbase**), con modelado de datos anidado y documentación interactiva vía **Swagger/OpenAPI**
- ✅ Construir un SPA en **React + TypeScript** que consume esa API, con enrutado del lado del cliente y dashboard con datos en tiempo real
- ✅ Dockerizar el backend con un build multi-stage y desplegarlo en un servicio cloud (**Render**)
- ✅ Migrar la base de datos a un clúster gestionado (**Couchbase Capella**) y desplegar el frontend como sitio estático (**Netlify**)

| | |
|---|---|
| 🌐 **App** | [veterinario-web.netlify.app](https://veterinario-web.netlify.app/) |
| 🔧 **API (Swagger)** | [veterinariobackend.onrender.com/swagger-ui](https://veterinariobackend.onrender.com/swagger-ui/index.html) |
| 🗄️ **Backend** | [VeterinarioBackend](https://github.com/Fernandodg97/VeterinarioBackend) |
| 💻 **Frontend** | [Veterinario-Aplicacion-Web](https://github.com/Fernandodg97/Veterinario-Aplicacion-Web) |

> ⏱️ Los servicios están en plan gratuito y pueden tardar ~30-50s en arrancar tras un periodo de inactividad.

---

## 🛠️ Stack tecnológico

**Backend** — Java 21 · Spring Boot 3.4 · Spring Data Couchbase · Spring Web · Maven · Docker · Swagger/OpenAPI

**Frontend** — React 19 · TypeScript · Vite · React Router DOM · Axios

**Base de datos** — Couchbase Capella (NoSQL documental, gestionado en la nube)

**Infraestructura** — Render (backend, Docker) · Netlify (frontend, static site) · Couchbase Capella (base de datos)

---

## Arquitectura

```
[Usuario]
    │
    ▼
[React SPA]  ──── HTTP/REST ────▶  [Spring Boot API]
  (Netlify)                           (Render, Docker)
                                             │
                                             ▼
                                    [Couchbase Capella]
                                     (base de datos)
```

---

## Funcionalidades

| Módulo | Descripción |
|---|---|
| **Usuarios** | CRUD completo de propietarios de mascotas |
| **Mascotas** | Gestión de mascotas vinculadas a cada usuario (modelo anidado usuario → mascotas) |
| **Tratamientos** | Registro de tratamientos por mascota (medicamento, dosis, duración) |
| **Dashboard** | Contadores en tiempo real y listados de actividad reciente |

---

## Retos técnicos resueltos

**Modelado NoSQL** — Documentos Couchbase con mascotas embebidas dentro del documento de usuario, y tratamientos como documentos independientes relacionados por `mascotaId`, combinando datos anidados y referenciados según el caso de uso.

**Consultas N1QL** — Índices secundarios (`findByEmail`, `findByMascotaId`) necesarios para que los repositorios de Spring Data Couchbase resuelvan sus queries derivadas.

**Migración a producción** — Paso de un clúster Couchbase local a Couchbase Capella: certificados TLS, credenciales vía variables de entorno y ajuste del *Allowed IP* del clúster para aceptar conexiones desde la IP dinámica de Render.

**Monorepo → despliegue independiente** — Frontend y backend viven en repos separados; Netlify se configura con `base = "frontend"` para el build en la subcarpeta, y la URL de la API se inyecta vía `VITE_API_URL` en tiempo de build.

---

## Autor

| | |
|---|---|
| **Fernando Diaz** | [github.com/Fernandodg97](https://github.com/Fernandodg97) |

---

## Licencia

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.es)
