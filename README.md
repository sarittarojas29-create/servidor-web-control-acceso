# Servidor Web con Control de Acceso

Proyecto de portafolio: configuración de un servidor web en Linux con administración de usuarios y grupos para implementar control de acceso diferenciado.

##  Objetivo

Montar un servidor web funcional en Ubuntu, y configurar permisos de acceso distintos según el rol del usuario (editor vs administrador), aplicando buenas prácticas de administración de sistemas Linux.

##  Tecnologías utilizadas

- Ubuntu Server (en VirtualBox, adaptador puente)
- Nginx (servidor web)
- UFW (firewall)
- Administración de usuarios y grupos (Linux)

##  Proceso

### 1. Preparación del entorno
- Configuración de Ubuntu en VirtualBox con adaptador de red en modo puente, para obtener una IP accesible dentro de la red local.

### 2. Instalación del servidor web
- Actualización del sistema: `sudo apt update && sudo apt upgrade -y`
- Instalación de Nginx: `sudo apt install nginx -y`
- Verificación del servicio activo: `sudo systemctl status nginx`
- Confirmación de acceso vía navegador usando la IP local del servidor.

### 3. Control de acceso: usuarios y grupos
- Creación del grupo `editores`, con permisos de escritura sobre el directorio del sitio (`/var/www/html`).
- Creación del grupo `admins`, con privilegios de superusuario (`sudo`).
- Asignación de permisos con `chown` y `chmod` para que solo el grupo `editores` pueda modificar los archivos del sitio.

### 4. Pruebas de verificación
- Usuario del grupo `editores`: pudo escribir archivos en el sitio ✅
- Usuario sin permisos: recibió "Permission denied" al intentar escribir ❌ (comportamiento esperado)

##  Evidencia

<img width="1885" height="524" alt="Screenshot 2026-09-30 140059" src="https://github.com/user-attachments/assets/992f0bdf-85d6-470a-9ab9-d1e9de2b02b2" />

<img width="948" height="908" alt="Screenshot 2026-09-30 140138" src="https://github.com/user-attachments/assets/9a6002f7-11ed-4fd1-99ce-f060d5b9fab0" />

##  Aprendizajes

Este proyecto reforzó conceptos clave de administración de sistemas Linux: gestión de usuarios y grupos, permisos de archivos (chmod/chown), configuración de servicios y firewall — base para la gestión segura de infraestructura web.
