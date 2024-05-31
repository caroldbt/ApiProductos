# ApiProductos
Creacion de Api Productos con el lenguaje C#, desplegada en Azure.
# API de Productos

## Descripción

Esta API de Productos está diseñada para gestionar productos y categorías. Está construida con C# y utiliza una arquitectura de microservicios desplegada en Azure. La API se comunica a través de un bus de mensajes y usa AutoMapper para facilitar el mapeo de datos entre entidades. La base de datos utilizada es SQL Server en Azure, y el proyecto incluye funcionalidades adicionales para autenticación, autorización y logging.

## Características

- **Microservicios**: Arquitectura basada en microservicios para escalabilidad y mantenimiento.
- **Bus de Mensajes**: Comunicación eficiente entre microservicios utilizando Azure Service Bus.
- **AutoMapper**: Mapeo automático de entidades para simplificar la lógica de negocio.
- **Base de Datos**: SQL Server en Azure para el almacenamiento de datos de productos y categorías.
- **Autenticación y Autorización**: Seguridad implementada con Azure AD.
- **Logging**: Sistema de logging para monitoreo y depuración.
- **Despliegue en Azure**: Implementación y gestión a través de Azure Kubernetes Service (AKS).

## Requisitos

- .NET 6.0 SDK o superior
- Visual Studio 2022 o VS Code
- Cuenta de Azure
- SQL Server en Azure

## Configuración

1. **Clonar el repositorio**

    ```bash
    git clone https://github.com/tu_usuario/api-productos.git
    cd api-productos
    ```

2. **Configuración del proyecto**

    Configura las cadenas de conexión en el archivo `appsettings.json`:

    ```json
    {
      "ConnectionStrings": {
        "DefaultConnection": "Server=tcp:tu_servidor.database.windows.net,1433;Initial Catalog=tu_base_de_datos;Persist Security Info=False;User ID=tu_usuario;Password=tu_contraseña;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"
      },
      "AzureServiceBus": {
        "ConnectionString": "Endpoint=sb://tu_namespace.servicebus.windows.net/;SharedAccessKeyName=tu_clave;SharedAccessKey=tu_valor_de_clave"
      }
    }
    ```

3. **Migraciones de base de datos**

    Ejecuta las migraciones para crear la estructura de la base de datos:

    ```bash
    dotnet ef database update
    ```

4. **Despliegue en Azure**

    Configura y despliega el proyecto en Azure AKS siguiendo la [documentación oficial](https://docs.microsoft.com/en-us/azure/aks/).

## Endpoints

### Productos

- **GET /api/productos**: Obtiene todos los productos.
- **GET /api/productos/{id}**: Obtiene un producto por ID.
- **POST /api/productos**: Crea un nuevo producto.
- **PUT /api/productos/{id}**: Actualiza un producto existente.
- **DELETE /api/productos/{id}**: Elimina un producto por ID.

### Categorías

- **GET /api/categorias**: Obtiene todas las categorías.
- **GET /api/categorias/{id}**: Obtiene una categoría por ID.
- **POST /api/categorias**: Crea una nueva categoría.
- **PUT /api/categorias/{id}**: Actualiza una categoría existente.
- **DELETE /api/categorias/{id}**: Elimina una categoría por ID.

## Ejemplos de Uso

### Crear un Producto

```bash
curl -X POST "https://tu_dominio/api/productos" -H "Content-Type: application/json" -d '{
  "nombre": "Producto Ejemplo",
  "descripcion": "Descripción del producto",
  "precio": 99.99,
  "categoriaId": 1
}'
