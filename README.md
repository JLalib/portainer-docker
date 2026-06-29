# Docker Portainer 🐳

Portainer es una interfaz gráfica (UI) ligera y potente para gestionar Docker hosts, Docker Swarm y clusters Kubernetes desde un panel visual intuitivo. Permite realizar todas las operaciones de Docker sin necesidad de memorizar comandos de la CLI, siendo la herramienta ideal para homelabs, startups y administradores de sistemas.

## 🚀 Características Principales

- **Gestión Visual Completa:** Control total sobre contenedores, imágenes, volúmenes y redes.
- **Stacks & Docker Compose:** Despliegue, edición y eliminación de stacks directamente desde la interfaz.
- **Soporte Kubernetes:** Gestión completa de manifests, Helm charts y GitOps.
- **Multi-usuario & RBAC:** Roles y permisos granulares para equipos, con soporte para múltiples usuarios.
- **GitOps:** Sincronización automática y despliegue directo desde fuentes de Git.
- **Edge Agents:** Gestión de hosts remotos desde un panel centralizado.
- **Soporte de Temas:** Selector rápido entre modo claro, oscuro y alto contraste.
- **Ligero y Eficiente:** Se despliega como un único contenedor con un overhead mínimo.

## 🛠️ Requisitos del Sistema

- **Hardware:** Compatible con cualquier servidor x86 o ARM (incluyendo Raspberry Pi).
- **RAM:** 512 MB - 1 GB.
- **Almacenamiento:** 1 GB - 5 GB.
- **Puertos:** 8000 (HTTP) y 9443 (HTTPS).
- **Acceso:** Requiere acceso al socket de Docker (`/var/run/docker.sock`).

## 📦 Instalación con Docker Compose

### 1. Preparar el entorno
Crea la carpeta del proyecto y entra en ella:
```bash
mkdir portainer-docker && cd portainer-docker
```

### 2. Crear el archivo `docker-compose.yml`
Copia el contenido del archivo `docker-compose.yml` incluido en este repositorio.

### 3. Desplegar el servicio
```bash
docker compose up -d
```

### 4. Acceder al Dashboard
Abre tu navegador y entra en: `https://localhost:9443` (HTTPS automático).

## ⚙️ Primeros Pasos

1. **Configuración Inicial:** Crea tu usuario administrador (username y password) al acceder por primera vez.
2. **Selección de Ambiente:** Elige el entorno que deseas gestionar (Docker local o remoto).
3. **Gestión de Contenedores:** Utiliza la sección **Containers** para ver logs en vivo, inspeccionar o reiniciar servicios.
4. **Despliegue de Stacks:** En la sección **Stacks**, puedes pegar el contenido de un archivo `docker-compose.yml` para desplegar aplicaciones complejas automáticamente.

## 🛡️ Seguridad y Mantenimiento

- **HTTPS en Producción:** Para acceso remoto seguro, utiliza un proxy inverso como **Caddy** o **Nginx**.
- **Actualización de Portainer:**
  ```bash
  docker pull portainer/portainer-ce:latest
  docker compose down
  docker compose up -d
  ```
- **Backup de Datos:**
  ```bash
  docker run --rm -v portainer_data:/data -v $(pwd):/backup alpine tar czf /backup/portainer-backup-$(date +%Y%m%d).tar.gz -C /data .
  ```
- **Reiniciar Servicio:** `docker compose restart portainer`

---
*Basado en el tutorial de [Genbyte](https://genbyte.blogspot.com/)*
