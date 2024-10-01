# WineAppBackEnd

WineAppBackEnd es una aplicación de gestión de inventario de vinos que permite registrar nuevos usuarios y vinos, así como consultar el inventario de vinos. La aplicación sigue una arquitectura de servicios con controladores independientes para la gestión de usuarios y vinos.

## Estructura del Proyecto

El proyecto está dividido en varios componentes clave:

- **Common**: Contiene modelos compartidos utilizados en la aplicación.
- **Data**: Incluye las entidades principales como `User` y `Wine` y los repositorios para la lógica de acceso a datos.
- **Services**: Implementa la lógica de negocio a través de servicios separados para `User` y `Wine`.
- **WineAppBackEnd**: Contiene los controladores y la configuración principal de la API.

### Componentes principales

- **Common.Models**: Modelos comunes, como DTOs (`Data Transfer Objects`) que son utilizados para la comunicación entre el cliente y la API.
- **Data.Entities**: Entidades que representan los modelos de dominio de la base de datos, como `User` y `Wine`.
- **Services.UserServices**: Lógica de negocio relacionada con la gestión de usuarios.
- **Services.WineServices**: Lógica de negocio relacionada con la gestión del inventario de vinos.
- **Controllers**: Controladores API que manejan las solicitudes HTTP y delegan la lógica a los servicios.

## Instalación

1. Clona este repositorio:
   ```bash
   git clone https://github.com/usuario/WineAppBackEnd.git
   ```

2. Navega al directorio del proyecto:
   ```bash
   cd WineAppBackEnd
   ```

3. Restaura los paquetes NuGet:
   ```bash
   dotnet restore
   ```

4. Compila el proyecto:
   ```bash
   dotnet build
   ```

## Ejecución

1. Para ejecutar la aplicación en modo local:
   ```bash
   dotnet run
   ```

2. La API estará disponible en `https://localhost:5001` por defecto.

## Endpoints

### UserController

Maneja las operaciones relacionadas con los usuarios.

- **POST `/api/user`**: Agrega un nuevo usuario.

  **Request Body:**
  ```json
  {
    "username": "exampleUser",
    "password": "examplePassword",
    "email": "example@example.com"
  }
  ```

  **Responses:**
  - `201 Created`: Si el usuario es creado exitosamente.
  - `400 Bad Request`: Si el cuerpo de la solicitud es nulo o si el usuario ya existe.

### WineController

Maneja las operaciones relacionadas con los vinos.

- **POST `/api/wine`**: Agrega un nuevo vino al inventario.

  **Request Body:**
  ```json
  {
    "name": "Cabernet Sauvignon",
    "year": 2018,
    "quantity": 100
  }
  ```

  **Responses:**
  - `201 Created`: Si el vino es agregado exitosamente.
  - `400 Bad Request`: Si el cuerpo de la solicitud es nulo o si el vino ya existe.

- **GET `/api/wine`**: Obtiene todo el stock de vinos.

  **Responses:**
  - `200 OK`: Devuelve una lista de todos los vinos en stock.

## Configuración

La configuración de la aplicación se gestiona a través del archivo `appsettings.json`, donde puedes ajustar los detalles de la conexión a la base de datos y otros parámetros.

## Dependencias

- [.NET 8.0](https://dotnet.microsoft.com/download/dotnet/8.0)
- ASP.NET Core para la construcción de APIs.
