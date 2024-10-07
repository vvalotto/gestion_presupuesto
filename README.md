Gestión de Presupuestos
Este proyecto es una aplicación web diseñada para la Gestión de Presupuestos,
desarrollada utilizando Python y Flask en el backend, con React en el frontend.
El sistema gestiona presupuestos, usuarios, roles, y tipos de cambio, i
ntegrándose con un servicio externo para obtener datos de tipos de cambio en tiempo real.
El proyecto sigue una arquitectura modular basada en Domain-Driven Design (DDD), 
organizando los componentes clave en distintos Bounded Contexts.

Estructura del Proyecto
El proyecto está organizado de la siguiente manera:
gestion_presupuesto/
├── config/                 # Configuración de la aplicación Flask
├── app/                    # Aplicación principal Flask
│   ├── __init__.py         # Inicialización de Flask
│   ├── routes.py           # Definición de rutas de la API
│   └── models/             # Modelos SQLAlchemy para las entidades
├── bounded_contexts/        # Contextos del dominio organizados por DDD
│   ├── gestion_presupuestos/  # Lógica de negocio para la gestión de presupuestos
│   ├── usuarios_roles/        # Gestión de autenticación y autorización
│   └── finanzas_externas/     # Integración con servicios externos de tipo de cambio
├── tests/                  # Pruebas unitarias y funcionales
├── migrations/             # Migraciones de base de datos gestionadas con Flask-Migrate
├── requirements.txt        # Dependencias del proyecto
├── Dockerfile              # Archivo Docker para contenedorización
├── manage.py               # Script de gestión de la aplicación Flask
└── README.md               # Documentación del proyecto

Componentes del Sistema
1. Frontend (Aplicación Web - React)
El frontend está desarrollado con React y es responsable de proporcionar la interfaz de
usuario interactiva. Gestiona la visualización de presupuestos, cuentas y líneas 
presupuestarias. El frontend se comunica con la API del backend mediante peticiones 
HTTP utilizando Axios o Fetch.

2. Backend (API de Servicios - Flask)
El backend está desarrollado con Python-Flask y contiene la lógica de negocio. 
Está dividido en varios Bounded Contexts para gestionar diferentes aspectos del sistema:
Gestión de Presupuestos: Servicios y repositorios relacionados con 
la creación y gestión de presupuestos, cuentas y líneas presupuestarias.
Usuarios y Roles: Manejo de la autenticación, autorización y control de acceso basado 
en roles.
Finanzas Externas: Integración con el sistema externo para obtener los tipos de
cambio de monedas.

3. Base de Datos (MySQL)
La base de datos MySQL almacena la información de presupuestos, cuentas, 
usuarios y tipos de cambio. Las migraciones de base de datos se gestionan utilizando 
Flask-Migrate.

5. Sistema Externo de Tipo de Cambio
El sistema consume datos de un servicio externo para obtener 
tipos de cambio en tiempo real (ej., Fixer.io, Open Exchange Rates). 
Este componente se gestiona mediante servicios y clientes HTTP en el backend.

Requisitos del Proyecto
Las dependencias necesarias para el proyecto están listadas en el archivo requirements.txt. 
ara instalarlas, usa el siguiente comando:
pip install -r requirements.txt

Dependencias clave:

Flask
Flask-SQLAlchemy
Flask-JWT-Extended
Flask-Migrate
Requests
PyMySQL


Configuración del Entorno
Base de Datos: Crea una base de datos MySQL con el siguiente comando:
CREATE DATABASE gestion_presupuestos;

Luego, asegúrate de que la cadena de conexión esté 
definida correctamente en config/settings.py:

Migraciones de Base de Datos: Las migraciones de base de datos se gestionan con Flask-Migrate. 
Para inicializar y aplicar migraciones, usa los siguientes comandos:

flask db init
flask db migrate -m "Creación inicial de tablas"
flask db upgrade

