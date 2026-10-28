# WeddingManager — Nuestra Película de Amor

Sistema personalizado de gestión de bodas que permite organizar invitados, administrar confirmaciones de asistencia, distribuir mesas, gestionar los detalles del evento y ofrecer una invitación digital interactiva para los invitados.

## Descripción del proyecto

WeddingManager es una aplicación web desarrollada para centralizar la organización de una boda en una plataforma con un diseño romántico, elegante y adaptable a dispositivos móviles.

El sistema cuenta con dos experiencias principales:

- **Portal público:** invitación digital con información del evento y funcionalidades para los invitados.
- **Panel de administración:** espacio privado para gestionar invitados, confirmaciones, mesas y otros aspectos de la boda.

El proyecto utiliza el concepto visual **Nuestra Película de Amor**, con una interfaz en tonos blancos y dorados, animaciones elegantes y una experiencia enfocada en la historia de la pareja.

## Características principales

### Invitación digital
- Página pública con diseño romántico y adaptable.
- Presentación de la información de la boda.
- Ubicación del evento y acceso a un mapa.
- Experiencia optimizada para dispositivos móviles.
- Animaciones de entrada y transiciones visuales.

### Gestión de invitados
- Registro, consulta, edición y eliminación lógica de invitados.
- Administración de confirmaciones de asistencia (RSVP).
- Gestión de acompañantes.
- Organización y asignación de mesas.
- Consulta de información de los invitados.

### Administración de la boda
- Panel privado de administración.
- Gestión centralizada de la información del evento.
- Administración de invitados, mesas, alimentos, acompañantes y servicios.
- Acceso protegido mediante autenticación.

### Galería fotográfica
- Acceso a la galería mediante código QR.
- Posibilidad de tomar fotografías o subir imágenes desde el dispositivo.
- Almacenamiento local de las fotografías.
- Publicación de las fotografías para los invitados al día siguiente del evento.

## Tecnologías

- **Backend:** ASP.NET MVC 5.
- **Framework:** .NET Framework 4.7.2.
- **Servidor de desarrollo:** IIS Express.
- **Frontend:** HTML5, CSS3 y JavaScript.
- **Interactividad:** jQuery.
- **Interfaz:** Bootstrap opcional.
- **Persistencia:** archivos JSON locales.
- **Almacenamiento multimedia:** archivos locales.
- **Autenticación:** Forms Authentication.

## Arquitectura

La aplicación separa el backend y el portal de usuario.

```text
WeddingManager/
├── src/
│   ├── WeddingManager/
│   │   ├── App_Data/
│   │   │   ├── data/
│   │   │   └── Uploads/
│   │   ├── Controllers/
│   │   ├── Models/
│   │   ├── Repositories/
│   │   ├── Services/
│   │   ├── Views/
│   │   ├── Web.config
│   │   └── Global.asax
│   │
│   └── Portal/
│       ├── index.html
│       ├── admin.html
│       ├── css/
│       ├── js/
│       └── assets/
│
├── README.md
└── AGENTS.md
```

La estructura representa la organización prevista del proyecto; los nombres y subdirectorios concretos deben corresponder a los existentes en el repositorio.

## Almacenamiento de datos

Toda la información se almacena localmente dentro del proyecto mediante archivos JSON.

- Datos persistentes: `App_Data/data`.
- Fotografías y archivos: `App_Data/Uploads`.
- Configuración de la ruta de datos: `WeddingManager:DataFolder`.

### Reglas de persistencia

- No utilizar SQL Server.
- No utilizar Entity Framework.
- Implementar acceso a datos mediante `JsonStore` y `WeddingRepository`.
- Realizar escrituras atómicas para proteger la integridad de los archivos.
- Crear copias de seguridad `.bak` antes de reemplazar datos.
- Rechazar archivos JSON inválidos sin sobrescribir la información existente.
- Utilizar borrado lógico mediante la propiedad `IsDeleted`.

## Rutas principales

| Ruta | Función |
|---|---|
| `/` | Invitación digital pública |
| `/Guests` | Gestión o consulta de invitados |
| `/Management` | Panel de administración |
| `/Account/Setup` | Configuración inicial |
| `/Account/Login` | Inicio de sesión administrativo |

El acceso administrativo debe permanecer protegido mediante autenticación. El perfil de administrador no debe exponerse como una opción pública dentro de la invitación.

## Seguridad

- Autenticación mediante Forms Authentication.
- Cookies de autenticación configuradas con `HttpOnly`.
- Protección de las rutas administrativas.
- Validación de entradas y archivos cargados.
- Restricción de acceso directo a los archivos internos de `App_Data`.
- Almacenamiento de contraseñas mediante mecanismos seguros de hash.
- Validación de permisos antes de ejecutar operaciones administrativas.

## Requisitos

- Windows con soporte para .NET Framework 4.7.2.
- Visual Studio compatible con proyectos ASP.NET MVC 5.
- IIS Express.
- Navegador web moderno.

## Instalación y ejecución

1. Clonar o descargar el repositorio.
2. Abrir la solución en Visual Studio.
3. Restaurar las dependencias NuGet necesarias.
4. Verificar la configuración de `WeddingManager:DataFolder`.
5. Comprobar que las carpetas de datos y archivos tengan los permisos de escritura necesarios.
6. Ejecutar el proyecto utilizando IIS Express.
7. Acceder a `/Account/Setup` para realizar la configuración inicial, si todavía no se ha completado.
8. Abrir la ruta `/` para visualizar la invitación digital.

## Diseño y experiencia de usuario

La interfaz debe mantener una identidad visual consistente con el concepto **Nuestra Película de Amor**:

- Paleta de colores blancos y dorados.
- Diseño romántico, moderno y elegante.
- Transiciones y animaciones fluidas.
- Diseño adaptable a teléfonos, tabletas y computadoras.
- Navegación sencilla para los invitados.
- Panel administrativo funcional y organizado.

Las animaciones pueden inspirarse en demostraciones de GSAP, manteniendo un rendimiento adecuado y una experiencia accesible.

## Principios de desarrollo

- Mantener la compatibilidad con ASP.NET MVC 5 y .NET Framework 4.7.2.
- No incorporar bases de datos externas.
- Mantener toda la persistencia dentro del proyecto.
- Separar controladores, modelos, repositorios y servicios.
- Evitar dependencias innecesarias.
- Validar las operaciones de lectura y escritura.
- Mantener el portal público independiente de la interfaz administrativa.
- Priorizar la seguridad, la mantenibilidad y la experiencia móvil.

## Objetivo

Crear una plataforma privada y personalizada que permita organizar todos los aspectos de la boda desde un solo lugar, ofreciendo a los invitados una invitación digital elegante y una experiencia memorable antes, durante y después del evento.

**WeddingManager — Nuestra Película de Amor.**
