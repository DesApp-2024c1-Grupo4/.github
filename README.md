# Guía de Despliegue de Beevents

## Índice
1. [Descripción del Proyecto](#descripción-del-proyecto)
2. [Requisitos de Infraestructura](#requisitos-de-infraestructura)
3. [Entorno de Desarrollo y Dependencias](#entorno-de-desarrollo-y-dependencias)
4. [Configuración de Entornos](#configuración-de-entornos)
5. [Pasos para el Despliegue](#pasos-para-el-despliegue)
6. [Servicios Externos y Configuración](#servicios-externos-y-configuración)
7. [Verificación Post-Despliegue](#verificación-post-despliegue)
8. [Reversión y Contingencias](#reversión-y-contingencias)

---

### Descripción del Proyecto

Beevents es una plataforma de reserva de tickets para eventos como conciertos, conferencias, y actividades deportivas. El sistema permite la creación y gestión de eventos, y la reserva de entradas por parte de los usuarios registrados. No se incluyen funcionalidades de compra o integración con sistemas de pago. 

- **Versión actual**: en desarrollo.
- **Módulos principales**:
  - Gestión de Usuarios: Registro, modificación y autenticación.
  - Gestión de Eventos: Creación, modificación, eliminación y consulta de eventos.
  - Gestión de Tickets: Reserva, consulta y asignación de tickets.
  - Gestión de Predios: Creación y configuración de sectores para eventos.

---

### Requisitos de Infraestructura

1. **Entorno de despliegue**: Actual en [Render](https://beevents.onrender.com/) (puede ser adaptable a otros servicios en la nube o servidores propios on-premise).
2. **Especificaciones mínimas**:
   - Memoria RAM: 512 MB
   - Procesador: 1000 MHz
   - Acceso a red local o Internet
   - Base de datos: MongoDB (local o en MongoDB Atlas)

---

### Entorno de Desarrollo y Dependencias

1. **Stack Tecnológico**:
   - **Frontend**: ReactJS (con Vite y Material UI)
   - **Backend**: NestJS (TypeScript y Mongoose para MongoDB Atlas)

2. **Dependencias**:
   - **Frontend**: 
     - Principales: `@mui/material`, `axios`, `react-router-dom`, `react-redux`, `react-hook-form`, `dayjs`, etc.
     - Desarrollo: `eslint`, `vite`, `@typescript-eslint/eslint-plugin`, `prettier`, etc.
   - **Backend**: 
     - Principales: `@nestjs/common`, `@nestjs/config`, `axios`, `bcrypt`, `cloudinary`, `mongoose`, `passport`, `multer`, etc.
     - Desarrollo: `@nestjs/testing`, `jest`, `typescript`, `eslint`, `prettier`, etc.

3. **Variables de Entorno**:
   - **Frontend**: `.env` file
     - `VITE_API_URL`
   - **Backend**: `.env` file
     - `MONGO_DB_NAME`, `MONGO_DB_URL`, `PORT`

---

### Configuración de Entornos

1. **Entornos disponibles**:
   - **Backend**: Dev
   - **Frontend**: Test

2. **Configuración de variables de entorno**:
   - Cada entorno necesita sus propias variables de configuración en archivos `.env`, detalladas en la sección anterior.

---

### Pasos para el Despliegue

1. **Frontend**:
   - Clonar el repositorio:
     ```bash
     git clone https://github.com/DesApp-2024c1-Grupo4/beevents-front.git
     cd frontend
     ```
   - Instalar dependencias:
     ```bash
     npm install
     ```
   - Crear el archivo `.env` con las variables de entorno correspondientes.
   - Crear el build de producción:
     ```bash
     npm run build
     ```

2. **Backend**:
   - Clonar el repositorio:
     ```bash
     git clone https://github.com/DesApp-2024c1-Grupo4/beevents-back.git
     cd backend
     ```
   - Instalar dependencias:
     ```bash
     yarn install --frozen-lockfile
     ```
   - Crear el archivo `.env` con las variables de entorno correspondientes.
   - Crear el build de producción:
     ```bash
     yarn build
     ```
   - Iniciar la aplicación:
     ```bash
     yarn start
     ```

---

### Servicios Externos y Configuración

1. **Servicios de API**:
   - No se requiere integración con servicios de pago ni notificaciones, solo APIs de acceso gratuito.
   
---

### Verificación Post-Despliegue

1. **Pruebas de Funcionalidad**:
   - Verificar el registro y autenticación de usuarios.
   - Asegurar la creación, modificación, y eliminación de eventos por parte del administrador.
   - Confirmar la reserva y consulta de tickets.

2. **Pruebas de Integración**:
   - Verificar la conexión con MongoDB Atlas (o base de datos local).
   - Asegurar el funcionamiento de las APIs en los endpoints esperados.

---

### Reversión y Contingencias

1. **Backup y Rollback**:
   - Antes de cada despliegue, realizar un snapshot del estado de la base de datos o un backup completo.
   - Mantener la última versión estable del código en el repositorio de Git para revertir cambios en caso de errores graves.

---

**Nota**: Este documento es una guía para el despliegue de la aplicación "Beevents" y debe actualizarse conforme se agreguen nuevas funcionalidades o se realicen cambios en la infraestructura.
