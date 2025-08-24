# 🚀 OpenProject Docker

Implementación de OpenProject usando Docker Compose para gestión de proyectos.

## ¿Qué es OpenProject?

OpenProject es una herramienta de gestión de proyectos de código abierto que incluye:

- Gestión de tareas y proyectos
- Diagramas de Gantt
- Tableros Kanban
- Control de tiempo
- Wiki y documentación

## 🛠️ Requisitos

### Para Windows (WSL recomendado)

- WSL2 (Windows Subsystem for Linux)
- Docker Desktop con integración WSL2
- Docker Compose

### Para Linux

- Docker
- Docker Compose

## 🚀 Uso

### En Windows con WSL

```bash
# Abrir WSL2
wsl

# Navegar al directorio del proyecto
cd /mnt/path/openproject

# Iniciar servicios
docker-compose up -d
```

### En Linux

```bash
# Navegar al directorio del proyecto
cd ~/path/to/openproject

# Iniciar servicios
docker-compose up -d
```

### Acceder a la aplicación

Abre tu navegador y ve a: **http://localhost:8080**

### Credenciales iniciales

- **Usuario:** `admin`
- **Contraseña:** `admin`

> ⚠️ **Importante:** Cambia estas credenciales después del primer login.

### Detener servicios

```bash
docker-compose down
```

## 🏗️ Servicios

### PostgreSQL Database (db)

- **Imagen:** `postgres:13`
- **Puerto interno:** 5432
- **Base de datos:** `openproject_db`
- **Usuario:** `postgres`
- **Función:** Base de datos principal para almacenar todos los datos de OpenProject

### OpenProject (openproject)

- **Imagen:** `openproject/openproject:16`
- **Puerto:** `8080:80`
- **Función:** Aplicación web principal de gestión de proyectos
- **Idioma:** Español (configurado por defecto)
- **Dependencias:** Requiere el servicio `db` para funcionar

## 📁 Estructura del Proyecto

```
openproject/
├── docker-compose.yml     # Configuración de servicios
└── README.md             # Este archivo
```

## ⚙️ Configuración

El proyecto está configurado con:

- Puerto de acceso: `8080`
- Idioma por defecto: Español
- Datos persistentes en volúmenes Docker
- Reinicio automático de servicios
- Base de datos PostgreSQL integrada

## 🔧 Personalización

Para modificar la configuración, edita las variables de entorno en `docker-compose.yml`:

- `OPENPROJECT_HOST__NAME`: Cambia el host/puerto
- `OPENPROJECT_DEFAULT__LANGUAGE`: Cambia el idioma
- `OPENPROJECT_SECRET_KEY_BASE`: Cambia la clave secreta
- `POSTGRES_PASSWORD`: Cambia la contraseña de la base de datos
