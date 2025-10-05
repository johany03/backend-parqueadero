# Backend Parqueadero - Análisis Arquitectónico

## Tecnologías Utilizadas

### Backend (PHP)

-   PHP 8.2+
-   Framework Laravel 12.0
-   Autenticación JWT (jwt-auth)
-   Laravel Sanctum para autenticación API
-   Laravel Tinker para REPL
-   PHPUnit para pruebas
-   Faker para generar datos de prueba

### Herramientas de Construcción Frontend

-   Vite 7.0 como herramienta de construcción
-   TailwindCSS 4.0 para estilos
-   Plugin Laravel Vite para integración
-   Axios para peticiones HTTP

## Arquitectura del Proyecto

Este proyecto sigue el patrón de arquitectura MVC (Modelo-Vista-Controlador) de Laravel con capas adicionales para el desarrollo de API. Aquí está un desglose detallado de la arquitectura:

### Estructura de Directorios

```
backend-parqueadero/
├── app/                    # Código principal de la aplicación
│   ├── Http/              # Capa HTTP (Controladores, Middleware)
│   ├── Models/            # Modelos Eloquent
│   └── Providers/         # Proveedores de servicios
├── config/                # Archivos de configuración
├── database/              # Archivos relacionados con la base de datos
│   ├── factories/         # Factories de modelos para pruebas
│   ├── migrations/        # Migraciones de base de datos
│   └── seeders/          # Sembradores de datos
├── public/               # Activos públicos y punto de entrada
├── resources/            # Recursos del frontend
│   ├── css/             # Archivos CSS
│   ├── js/              # Archivos JavaScript
│   └── views/           # Plantillas Blade
├── routes/               # Rutas de la aplicación
│   ├── api.php          # Rutas API
│   ├── web.php          # Rutas web
│   └── console.php      # Comandos de consola
├── storage/             # Almacenamiento de la aplicación
├── tests/               # Archivos de prueba
│   ├── Feature/         # Pruebas de características
│   └── Unit/           # Pruebas unitarias
└── vendor/             # Dependencias de Composer
```

## Diagrama de Arquitectura

```mermaid
graph TD
    Client[Cliente] --> API[Capa API]
    API --> Routes[Rutas /routes/api.php]
    Routes --> Controllers[Controladores /app/Http/Controllers]
    Controllers --> Models[Modelos /app/Models]
    Models --> Database[(Base de Datos)]

    subgraph Autenticación
        API --> JWT[JWT Auth]
        API --> Sanctum[Laravel Sanctum]
    end

    subgraph "Capa de Aplicación"
        Controllers --> Services[Servicios]
        Services --> Repositories[Repositorios]
        Repositories --> Models
    end

    subgraph "Capa de Pruebas"
        PHPUnit[Pruebas PHPUnit] --> Feature[Pruebas de Características]
        PHPUnit --> Unit[Pruebas Unitarias]
        Feature --> Controllers
        Unit --> Services
    end## Componentes Principales

1. **Capa API**
   - Endpoints REST API
   - Autenticación JWT
   - Laravel Sanctum para tokens API

2. **Capa de Aplicación**
   - Controladores para manejar peticiones
   - Modelos para interacción con base de datos
   - Proveedores de servicios para inicialización

3. **Capa de Base de Datos**
   - Migraciones para estructura de base de datos
   - Sembradores para datos iniciales
   - Factories para datos de prueba

4. **Capa de Pruebas**
   - Pruebas de características para endpoints API
   - Pruebas unitarias para lógica de negocio
   - PHPUnit como marco de pruebas

## Características de Seguridad

- Autenticación JWT para seguridad API
- Laravel Sanctum para autenticación basada en tokens
- Middleware CORS para peticiones de origen cruzado
- Validación de entrada mediante validación de formularios de Laravel
```
