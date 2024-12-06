# glowicom-backend-test

La prueba técnica consiste en desarrollar un sistema backend para una tienda en línea que permita a los usuarios comprar productos. Este sistema debe manejar dos funcionalidades principales.

Objetivos de la prueba:

1. Almacenamiento de compras:
   
Cuando un usuario compra un producto, el sistema debe guardar información sobre la compra, cada compra, incluyendo:

·	userId: ID del usuario que realiza la compra.

·	name: Nombre del producto.

·	price: Precio del producto.

·	priceCategory: Categoría del precio basada en rangos predefinidos: 

- "Cheap" para precios entre 1 y 500.
- "Moderate" para precios de más de 500 y menos de 1000.
- "Expensive" para precios de 1000 y superior.

Se deberá de agregar al menos 2 compras con el mismo usuario y 1 compra con otro usuario distinto. Cada una de las compras debe de caer una categoría de precio distinta.

2. Listado de productos comprados:
   
El sistema debe ser capaz de listar todos los productos comprados, estos son los requisitos:

·	Listar Productos: El sistema debe permitir listar todos los productos comprados hasta el momento.

·	Filtrar por Rango de Precio: 

- Si se envían dos valores (precio mínimo y máximo) el sistema debe consultar la base de datos y devolver solo aquellos productos cuyo precio esté dentro del rango especificado.
- Si se envía el mínimo solamente, debe devolver todos los productos con ese mínimo de precio hacia adelante, 
- Si envía en máximo solamente, debe devolver los productos que tengan dicho máximo como tope.
- Si no se envía ningún valor, se deben listar todos los productos.
  
·	Calcular y mostrar el total gastado por cada usuario: Este cálculo debe incluir todos los productos comprados por cada usuario, sumando los precios de cada producto. Se adjuntará una propiedad adicional en la respuesta que indicará el total gastado por cada usuario en la consulta.
