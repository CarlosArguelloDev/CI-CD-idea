# Plataforma CI/CD + IaC + Staging en Raspberry Pi + Producción en Heroku

Este proyecto implementa una arquitectura moderna y profesional para un sistema de negocio ligero (API de registro, pedidos, clientes, etc.) utilizando una Raspberry Pi como servidor de **CI/CD**, **IaC**, **Staging** y **Monitoreo**, mientras que **Heroku** aloja el entorno de **Producción**.

La infraestructura se administra con **Terraform**, los despliegues se orquestan con **Jenkins**, y los servicios de red y seguridad se manejan con **Cloudflare**.

---

## 📌 Objetivo del Proyecto

Construir una plataforma completa que permita:

- Desarrollar y desplegar una **API en Go** para el negocio.
- Servir un **frontend en Node**.
- Mantener una **base de datos Postgres** confiable.
- Tener un entorno **Staging** local para pruebas rápidas.
- Tener un entorno **Producción** estable en Heroku.
- Automatizar despliegues con **CI/CD profesional**.
- Declarar infraestructura con **Terraform (IaC)**.
- Monitorear todo el sistema con **Prometheus + Grafana**.
- Administrar DNS, seguridad y servicios externos con **Cloudflare**.

---

## 🧱 Arquitectura General

### 🖥️ Raspberry Pi (8 GB RAM + SSD recomendado)
Funciona como:

- Servidor **CI/CD** con Jenkins.
- Máquina de desarrollo **IaC** con Terraform.
- Orquestador de contenedores con **Docker**.
- Entorno **Staging** para API, frontend y base de datos.
- Servidor de **monitoreo** con Prometheus + Grafana.
- Reverse proxy con **Nginx**.

**Servicios en la Raspberry Pi:**

- API Go (staging)
- Frontend Node (staging)
- Postgres (staging)
- Jenkins
- Terraform
- Docker
- Prometheus
- Grafana
- Nginx

---

### ☁️ Heroku (Producción)

Heroku aloja:

- API Go (producción)
- Frontend Node (producción)
- Postgres administrado
- Certificados SSL automáticos
- Logs centralizados
- Deploy sin downtime

Los despliegues se realizan automáticamente desde Jenkins.

---

### 🌐 Cloudflare

Administrado con Terraform:

- DNS del dominio del negocio
- Workers (opcional)
- Pages (opcional)
- Firewall rules
- Zero Trust (acceso seguro a la Raspberry Pi)

---

### 🐙 GitHub

- Repositorios del código
- Webhooks hacia Jenkins
- Branch protection
- Secrets
- Administración opcional vía Terraform

---

## 🔄 Flujo CI/CD

1. El desarrollador hace **push** a GitHub.
2. GitHub envía un **webhook** a Jenkins (Raspberry Pi).
3. Jenkins ejecuta el pipeline:
   - Lint (Go, Node)
   - Tests
   - Build
   - Security scan
   - Terraform plan/apply (si es IaC)
   - Deploy a Staging (contenedores en la Raspberry)
4. Si todo pasa, Jenkins realiza **deploy automático a Heroku**.
5. Prometheus + Grafana monitorean todo el sistema.

---

## 📦 Infraestructura como Código (IaC)

Terraform administra:

### Cloudflare
- DNS  
- Workers  
- Pages  
- Firewall rules  
- Zero Trust  

### GitHub
- Repos  
- Teams  
- Secrets  
- Branch protection  

### Docker (local)
- Contenedores  
- Redes  
- Volúmenes  
- Imágenes  

### Staging en Raspberry Pi
- API Go  
- Frontend Node  
- Postgres  
- Monitoreo  

---

## 🗄️ Base de Datos

### Staging (Raspberry Pi)
- Postgres en contenedor Docker
- Volumen persistente en SSD
- Retención de logs controlada

### Producción (Heroku)
- Heroku Postgres
- Backups automáticos
- Alta disponibilidad

---

## 📊 Monitoreo

### Prometheus
- Métricas de contenedores
- Métricas de API Go
- Métricas de Node
- Métricas de Postgres
- Métricas del sistema (Raspberry Pi)

### Grafana
- Dashboards de rendimiento
- Dashboards del negocio (opcional)

---

## 💾 Requerimientos de Disco

### Consumo estimado:
- Sistema operativo: 4–6 GB  
- Jenkins: 3–10 GB  
- Docker: 5–15 GB  
- Postgres: 1–5 GB  
- Prometheus + Grafana: 2–5 GB  
- Terraform + proyectos: 1–3 GB  

### Total recomendado:
**15–40 GB** para uso normal  
**40–60 GB** para crecimiento y logs

### Recomendación:
Usar **SSD de 240 GB** para estabilidad y rendimiento.

---

## 🧩 Idea General del Proyecto

El sistema busca ofrecer una plataforma moderna, modular y escalable para un negocio local, con:

- API ligera para registro y administración.
- Frontend simple para interacción.
- Base de datos confiable.
- CI/CD profesional.
- Infraestructura declarada con IaC.
- Staging local para pruebas rápidas.
- Producción en la nube para estabilidad.
- Monitoreo completo.
- DNS y seguridad administrados con Cloudflare.

Todo esto usando una Raspberry Pi como un **mini‑servidor empresarial**.

