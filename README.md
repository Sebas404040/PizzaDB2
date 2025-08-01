# PizzaDB2

## Contextualización

### ¿Qué es una base de datos NoSQL?

Una base de datos NoSQL es una forma moderna de guardar información sin seguir las reglas estrictas de las bases de datos tradicionales. A diferencia de las bases clásicas (que guardan todo en tablas, como una hoja de Excel), las bases NoSQL son más flexibles y se adaptan mejor a diferentes tipos de datos, como textos, imágenes o conexiones entre personas.
Son muy útiles cuando se necesita guardar muchos datos rápidamente o cuando la información cambia con frecuencia. Por eso, son muy usadas en aplicaciones como redes sociales, tiendas en línea o plataformas de video.
En resumen, NoSQL es una manera más libre y ágil de organizar los datos para que los sistemas puedan encontrarlos y usarlos fácilmente.

### ¿Qué es MongoDB?
MongoDB es un tipo de base de datos moderna que se usa para guardar información de manera flexible y rápida. A diferencia de las bases de datos tradicionales que usan tablas (como una hoja de cálculo), MongoDB guarda la información en documentos parecidos a archivos (como fichas), que se organizan en grupos llamados colecciones.
Por ejemplo, si tuvieras que guardar los datos de muchas personas, cada persona sería un documento con su nombre, correo, dirección, etc., y todos esos documentos estarían en una colección llamada "usuarios".
MongoDB es muy popular porque se adapta fácilmente a distintos tipos de datos, es fácil de usar y es ideal para aplicaciones como páginas web, redes sociales o tiendas en línea.

#### ¿Qué diferencia hay entre una base de datos relacional (como MySQL) y una base de datos documental como MongoDB?

Las bases de datos relacionales, como MySQL, guardan la información en tablas organizadas por filas y columnas, parecidas a una hoja de Excel. Por ejemplo, si tienes una lista de clientes, cada fila es un cliente y cada columna es un dato como su nombre, dirección o teléfono. Estas bases requieren que todos los datos sigan un orden y una estructura fija.

En cambio, las bases de datos documentales, como MongoDB, guardan la información en documentos que se parecen a fichas o tarjetas. Cada documento puede tener estructura propia, es decir, no es necesario que todos tengan exactamente los mismos datos. Esto las hace más flexibles y fáciles de adaptar cuando la información cambia o crece.
Resumen sencillo:
MySQL es como una tabla con celdas bien ordenadas.


MongoDB es como una caja con tarjetas, cada una con su propia forma.
Ambas se usan para guardar información, pero cada una funciona mejor dependiendo del tipo de proyecto.

#### ¿Qué son documentos y colecciones en MongoDB?
En MongoDB, la información se guarda en algo llamado documentos y colecciones, que funcionan como una especie de archivo digital.
Un documento es como una ficha o tarjeta que contiene todos los datos sobre algo o alguien. Por ejemplo, un documento de un cliente puede tener su nombre, correo, teléfono y dirección. Los documentos usan un formato llamado JSON, que es como escribir los datos con etiquetas para saber qué es cada cosa.


Una colección es como una caja que guarda muchas fichas. Es decir, una colección contiene muchos documentos relacionados. Por ejemplo, puedes tener una colección llamada “Clientes” que guarda todas las fichas (documentos) de los diferentes clientes.

##### Resumen sencillo:
- Documento = Una ficha con información.


- Colección = Una caja que guarda muchas fichas parecidas.
MongoDB usa esta forma porque es rápida, flexible y se adapta fácilmente a distintos tipos de datos.
PUNTO #4.



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

**Supuestos:**

tipo001 es el tipo "Pizza".

ing001: Queso mozzarella

ing002: Jamón

ing003: Piña

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

**Supuestos:**

prod001: Pizza Hawaiana

prod010: Gaseosa 400ml

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
**Supuestos:**

cli123: Carlos Pérez

adi001: Extra queso

adi002: Tocineta

prod001: Pizza Hawaiana

prod010: Gaseosa 400ml

## Reflexión

### ¿Qué fue lo más difícil de imaginar sin tablas?
Lo más difícil fue cambiar el chip de pensar todo como "tablas relacionadas" y pasar a imaginar la información como documentos independientes o anidados. En bases de datos relacionales, estamos acostumbrados a separar cada entidad en su tabla con claves foráneas. Aquí tuvimos que decidir si anidar información (como los productos dentro de un pedido) o referenciarla con un ID, y eso generó varias dudas sobre cuál era la mejor práctica. También fue un reto evitar redundancia sin perder claridad, sobre todo en pedidos personalizados.

### ¿Qué les gustó del enfoque con documentos?
Nos gustó mucho la flexibilidad de los documentos. Es muy práctico poder guardar toda la información relacionada en un solo documento, como un pedido que incluya los datos del cliente y todos los productos seleccionados, incluyendo las personalizaciones. Esto hace que los datos estén más organizados para casos específicos de uso, como consultar un pedido completo sin hacer múltiples "joins". También sentimos que es más natural y parecido a cómo uno pensaría en objetos reales (una pizza con sus ingredientes, un combo con sus productos, etc.).

### ¿Qué dudas les surgieron al pensar en este nuevo tipo de base de datos?
Nos surgieron varias dudas, por ejemplo:
- ¿Hasta qué punto es buena idea anidar documentos? ¿Cuándo es mejor referenciar?

- ¿Cómo se manejarían los cambios en los datos referenciados? Por ejemplo, si cambia el precio de un producto, ¿se actualizan automáticamente en los pedidos pasados?
- ¿Cómo se consultan o filtran los datos cuando están anidados a varios niveles?

- ¿Qué tan bien escala este modelo cuando hay muchos pedidos o clientes?

Estas preguntas nos dejaron con ganas de seguir aprendiendo más sobre las mejores prácticas en el modelado NoSQL y cómo se aplican en situaciones reales.