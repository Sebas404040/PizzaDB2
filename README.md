# PizzaDB2

## Que colecciones tendrian nuestro modelo

### 📦 Colección: Producto


La colección Producto contiene todos los documentos relacionados con los productos disponibles en el sistema, tales como pizzas, panzerottis, bebidas, postres y adiciones.

Cada documento en esta colección representa un producto específico e incluye la siguiente información estructurada:

- id_producto: Identificador único del producto.

- nombre: Nombre comercial del producto.

- id_tipoProducto: Referencia al tipo de producto (relación con la colección TipoProducto).

- ingredientes: Lista de referencias a los ingredientes que componen el producto (relación con la colección Ingredientes).

- tamaño: Tamaño del producto, aplicable especialmente a ítems como pizzas y bebidas.


### 👤 Colección: Cliente

La colección Cliente contiene todos los datos necesarios de cada usuario que desea adquirir productos a través del sistema. Esta información es fundamental para el proceso de registro, atención, entrega y seguimiento de pedidos.

Cada documento en esta colección incluye los siguientes campos:

- cedula: Número de identificación del cliente (único por usuario).

- nombre: Nombre completo del cliente.

- telefono: Número de contacto del cliente.

- direccion: Dirección de residencia o entrega asociada al cliente.


