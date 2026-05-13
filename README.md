# Auth Fullstack

Descripcion: Auth Fullstack es un sistema web, que permite al usuario registrarse, verificar cu cuenta y recuperar su contraseña

## Funcionalidades

- Registro de Usuario: El usuario crea su cuenta desde el frontend en React.

- Generación de Token: El backend (Express) genera un token único para ese usuario.

- Verificación por Email: Se envía un correo electrónico al usuario con un enlace o token.

-Cuenta Verificada: Una vez que el usuario confirma el token, la cuenta se marca como activa en MongoDB.
  
## Arquitectura del sistema
El proyecto sigue una arquitectura de **Aplicación de Página Única (SPA)** con un backend desacoplado, facilitando el mantenimiento y la escalabilidad.

### Diagrama de Flujo
A continuación se detalla cómo interactúan los componentes según el objetivo del proyecto:

1. **Frontend (React + Vite):** Captura los datos del usuario y gestiona el estado de la autenticación.
2. **API Gateway (Express):** Procesa las peticiones, valida los esquemas y gestiona la lógica de los tokens.
3. **Capa de Datos (MongoDB):** Almacenamiento persistente de perfiles y estados de verificación.
4. **Servicio de Mensajería (Email/Nodemailer):** Envío de tokens únicos para validación de cuenta y recuperación.

### Esquema Visual

`Usuario` ↔ `React (UI)` ↔ `Express (API)` ↔ `JWT ` ↔ `MongoDB`
                                     ↓
                             `Servicio de Email` (Token de verificación)

## Flujo de funcionamiento

El sistema sigue una arquitectura de API desacoplada:

React → Express API → MongoDB → JWT → Email/Token → Cuenta verificada.

## Estructura


```text
auth-fullstack/
├── backend/                # Servidor (Node.js + Express)
│   ├── controllers/        # Lógica de Registro, Login y Recuperación
│   ├── models/             # Esquemas de usuario para MongoDB
│   ├── routes/             # Endpoints de la API
│   ├── .env                # Variables de entorno (Oculto)
│   └── server.js           # Inicio del servidor
├── frontend/               # Cliente (React + Vite + Tailwind)
│   ├── public/             # Recursos estáticos
│   ├── src/                # Código fuente de React
│   │   ├── components/     # Piezas reutilizables de la UI
│   │   ├── pages/          # Vistas (Login, Registro, Confirmar Cuenta)
│   │   └── main.jsx        # Punto de entrada
│   └── vite.config.js      # Configuración del frontend
└── .gitignore              # Reglas globales para ignorar archivos pesados/secretos

```
### Tecnologías y Roles en la Autenticación

| Componente | Tecnología | Rol en la Autenticación |
| :--- | :--- | :--- |
| **Seguridad de Sesión** | **JWT (JSON Web Tokens)** | Maneja la identidad del usuario de forma segura entre el cliente y el servidor. |
| **Base de Datos** | **MongoDB** | Almacena las credenciales y el estado de verificación de cada usuario. |
| **Backend** | **Express API** | Contiene los controladores (`register`, `verifyAccount`, `forgotPassword`) que gestionan la lógica. |
| **Comunicación** | **Email/Token** | El método físico para validar que el usuario es quien dice ser. |


## Variables de entorno

- Este proyecto utiliza variables de entorno para la configuración.
- El archivo `.env` no está incluido en el repositorio por seguridad.
  Ejemplo de variables necesarias:
  ```env
  // backend/.env
PORT=3000
MONGO_URI=mongodb+srv://USUARIO:CLAVE@cluster.mongodb.net/authdb
JWT_SECRET=clave_super_secreta_para_clase
FRONTEND_URL=http://localhost:5173
EMAIL_USER=tu_correo@gmail.com
EMAIL_PASS=tu_app_password

## Pasos para la ejecucion del proyecto:
1. Clona el repositorio en Visual Studio Code
2. En el proyecto abre una nueva terminal para cada carpeta:
   - Frontend
     1. Entra a la carpeta: `cd frontend`
     2. Instala todo lo necesario para el proyecto: `npm install`
     3. Ejecucion del frontend: `npm run dev`
     4. Resultado: `http://localhost:5173/ ` (puede variar según el entorno)
  - Backend
    1. Entra a la carpeta: `cd backend`
    2. Instala todo lo necesario para el proyecto: `npm install`
    3. Ejecucion del backend: `npm run dev`
    4. Resultado: Servidor corriendo en `http://localhost:8000/`


## Capturas del sistema

1. Registro de cuenta

<img width="1019" height="693" alt="image" src="https://github.com/user-attachments/assets/8d88e52a-3695-4581-9945-ebfe34415acb" />


3. Verificacion del token
<img width="961" height="646" alt="image" src="https://github.com/user-attachments/assets/dfd1dd97-2124-4d1b-8e0b-6b2c0fddb765" />

4. Recuperacion de contraseña
<img width="958" height="680" alt="image" src="https://github.com/user-attachments/assets/207f7d63-5474-4452-90a4-31d5f702730f" />

## Autor
- Nombres: Concepcion Arequipa
- Institución: Escuela Politécnica Nacional
