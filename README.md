# Prueba Técnica Backend GLOWICOM

La prueba técnica consiste en desarrollar un sistema backend para una tienda en línea que permita a los usuarios comprar productos. Este sistema debe manejar dos funcionalidades principales.

## Objetivos de la prueba

### 1. Almacenamiento de Compras

Cuando un usuario compra un producto, el sistema debe guardar información sobre la compra, incluyendo:

- `userName`: Nombre del usuario que realiza la compra.
- `name`: Nombre del producto.
- `price`: Precio del producto.
- `priceCategory`: Categoría del precio basada en rangos predefinidos:
    - `"Cheap"` para precios entre 1 y 500.
    - `"Moderate"` para precios de más de 500 y menos de 1000.
    - `"Expensive"` para precios de 1000 y superior.
      
Para precios menor a 1 deberás devolver un error indicando que es un precio inválido.

Se deberá agregar:

- **2 compras con el mismo usuario, es decir, realizar 2 compras con un usuario con el mismo nombre**.
- **1 compra con otro usuario distinto, es decir, realizar una comprar con un usuario con otro nombre**.

Las 3 compras deben caer en una categoría de precio distinta, o lo que es decir: una compra en `"Cheap"`, otra en `"Moderate"` y la tercera en `"Expensive"`.

### 2. Listado de Productos Comprados

El sistema debe ser capaz de listar todos los productos comprados. Estos son los requisitos:

- **Listar Productos**: El sistema debe permitir listar todos los productos comprados hasta el momento.

- **Filtrar por Rango de Precio**:  
    Si se envían dos valores (precio mínimo y máximo), el sistema debe consultar la base de datos y devolver solo aquellos productos cuyo precio esté dentro del rango especificado.
    - Si se envía el mínimo solamente, debe devolver todos los productos con ese mínimo de precio hacia adelante.
    - Si se envía el máximo solamente, debe devolver los productos que tengan dicho máximo como tope.
    - Si no se envía ningún valor, se deben listar todos los productos.

- **Calcular y Mostrar el Total Gastado por Cada Usuario**:  
    Este cálculo debe incluir todos los productos comprados por cada usuario, sumando los precios de cada producto. Se adjuntará una propiedad adicional en la respuesta que indicará el total gastado por cada usuario en la consulta. El cálculo debe basarse en los productos filtrados.

- **Ejemplo de la respuesta**:  
    Este es un ejemplo ilustrativo de cómo debe ser la respuesta del programa para este apartado:
    
```json
   {
  "results": [
    {
      "id": 1,
      "userName": "Juan",
      "name": "Mesa",
      "price": 400,
      "priceCategory": "Cheap"
    },
    {
      "id": 2,
      "userName": "Juan",
      "name": "Silla",
      "price": 500,
      "priceCategory": "Moderate"
    },
    {
      "id": 3,
      "userName": "Luis",
      "name": "Mueble",
      "price": 1200,
      "priceCategory": "Expensive"
    }
  ],
  "totalPayment": {
    "Juan": 900,
    "Luis": 1200
  }
}
```
