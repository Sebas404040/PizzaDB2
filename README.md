# PizzaDB2

## Que colecciones tendrian nuestro modelo

### 📦 Colección: Producto


La colección Producto contiene todos los documentos relacionados con los productos disponibles en el sistema, tales como pizzas, panzerottis, bebidas, postres y adiciones.

Cada documento en esta colección representa un producto específico e incluye la siguiente información estructurada:

- id_producto: Identificador único del producto.

- nombre: Nombre comercial del producto.

- id_tipoProducto: Referencia al tipo de producto (relación con la colección TipoProducto).

- precio: el costo del producto.

- ingredientes: Lista de referencias a los ingredientes que componen el producto (relación con la colección Ingredientes).

- tamaño: Tamaño del producto, aplicable especialmente a ítems como pizzas y bebidas.


### 👤 Colección: Cliente

La colección Cliente contiene todos los datos necesarios de cada usuario que desea adquirir productos a través del sistema. Esta información es fundamental para el proceso de registro, atención, entrega y seguimiento de pedidos.

Cada documento en esta colección incluye los siguientes campos:

- cedula: Número de identificación del cliente (único por usuario).

- nombre: Nombre completo del cliente.

- telefono: Número de contacto del cliente.

- direccion: Dirección de residencia o entrega asociada al cliente.


### ➕ Colección: Adiciones
La colección Adiciones almacena todos los elementos adicionales que un cliente puede incluir en su pedido, como ingredientes extra, salsas o complementos especiales.

Cada documento en esta colección contiene:

- id_adiciones: Identificador único de la adición.

- nombre: Nombre descriptivo de la adición (ej. "Queso extra", "Tocineta").

- precio: Valor adicional que se suma al total del pedido al seleccionar esta adición.

- id_tipoProducto: Referencia al tipo de producto al que puede asociarse esta adición (relación con la colección TipoProducto).


### 🗂️ Colección: TipoProducto
La colección TipoProducto define las categorías o tipos generales a los que puede pertenecer un producto. Esta clasificación permite organizar y filtrar los productos disponibles en el sistema de forma eficiente.

Cada documento en esta colección incluye:

- id_tipoProducto: Identificador único del tipo de producto.

- nombre: Nombre descriptivo de la categoría (por ejemplo: Pizza, Bebida, Postre, Adición).

### 🧂 Colección: Ingredientes
La colección Ingredientes contiene todos los componentes que conforman los productos del sistema, especialmente útil para productos personalizables como las pizzas o panzerottis.

Cada documento en esta colección incluye:

- id_ingredientes: Identificador único del ingrediente.

- nombre: Nombre del ingrediente (por ejemplo: Jamón, Champiñones, Mozzarella).


### 🧃🍕 Colección: Combos
La colección Combos permite agrupar varios productos en una sola oferta, brindando al cliente la posibilidad de adquirirlos juntos con un precio especial o con descuento. Esta colección facilita la promoción de paquetes y mejora la experiencia de compra al ofrecer opciones más completas y atractivas.

Cada documento en esta colección contiene:

- id_combos: Identificador único del combo.

- nombre: Nombre comercial del combo (por ejemplo: Combo Familiar, Combo 2x1).

- productos: Lista de referencias a productos individuales incluidos en el combo (relación con la colección Producto).

- precio_combo: Precio total del combo, generalmente con descuento respecto al precio por separado.

- observacion: Campo opcional para incluir detalles adicionales, restricciones o notas especiales del combo.

### 🧾 Colección: Pedidos
La colección Pedidos registra toda la información relacionada con las solicitudes realizadas por los clientes, ya sea un producto individual, un postre o un combo. Esta colección es fundamental para el control de ventas y la gestión operativa del establecimiento.

Cada documento en esta colección contiene:

- id_pedidos: Identificador único del pedido.

- cedula: Referencia al cliente que realiza el pedido (relación con la colección Cliente).

- fecha_pedido: Fecha y hora en que se realiza el pedido.

- locacion: Define si el pedido es para llevar o para consumir en el establecimiento.

- productos: El documento "productos" contiene todos los productos que haya pedido el cliente. Mas abajo encontrara como se estructura este documento

- total: suma de todos los subtotales.


## 🧪 Ejemplos de Colecciones (Formato JSON)
A continuación, se presentan ejemplos representativos de cada colección en formato JSON, con el fin de ilustrar su estructura y facilitar su comprensión e implementación. Estos modelos pueden servir como referencia para pruebas, desarrollo o integración con bases de datos NoSQL como MongoDB.

### Coleccion de producto
```json
{
  "_id": "prod001",
  "nombre": "Pizza Hawaiana",
  "id_tipoProducto": "tipo001",  
  "precio": 30000,
  "ingredientes": ["ing001", "ing002", "ing003"],
  "tamaño": ["personal", "mediana", "familiar"]
}
```

### Coleeccion de pedido

```json
{
  "_id": "ped001",
  "cliente_id": "cli123",
  "fecha": "2025-08-01T18:00:00Z",
  "locacion": "para llevar",
  "productos": [
    {
      "producto_id": "prod001",
      "tamaño": "mediana",
      "adiciones": ["adi001"]
    },
    {
      "producto_id": "prod010",
      "adiciones": []
    }
  ],
  "total": 37000,
}
```
### Coleccion de combos

```json
Combo {
  "_id": "combo001",
  "nombre": "Combo Familiar",
  "productos": ["prod001", "prod010"],
  "precio_combo": 45000,
  "observacion": "Incluye 1 pizza grande y 2 bebidas"
}
```

### Coleccion de clientes

```json
Clientes {
  "_id": "cli123",
  "nombre": "Carlos Pérez",
  "telefono": "3123456789",
  "direccion": "Calle 123 #45-67",
  "correo": "carlos@example.com"
}
```
