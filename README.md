# Backend Parqueadero

Sistema de backend para gestión de parqueadero desarrollado con Laravel.

## Descripción

Este proyecto es una API REST desarrollada con Laravel para la gestión de un sistema de parqueadero.

## Tecnologías utilizadas

-   **Laravel** - Framework PHP
-   **PostgreSQL** - Base de datos
-   **PHP** - Lenguaje de programación

## Instalación

1. Clonar el repositorio:

```bash
git clone https://github.com/johany03/backend-parqueadero.git
cd backend-parqueadero
```

2. Instalar dependencias:

```bash
composer install
npm install
```

3. Configurar el archivo de entorno:

```bash
cp .env.example .env
```

4. Generar la clave de aplicación:

```bash
php artisan key:generate
```

5. Configurar la base de datos en el archivo `.env`

6. Ejecutar migraciones:

```bash
php artisan migrate
```

7. Iniciar el servidor:

```bash
php artisan serve
```

## Licencia

Este proyecto está bajo la licencia MIT.
