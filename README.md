# Stocky-Sistema-de-Stock
Trabajo práctico cuatrimestral que formó parte de la evaluación final de la materia <strong>Orientación a Objetos II</strong>

Para levantar el proyecto en principio se debe crear una BD vacía en MySQL. Luego en Spring Tool Suite setear las variables de entorno DB_URL, USERNAME y PASSWORD. Una vez hecho esto, solo queda correr el proyecto, se creará la BD sobre lo asignado y se podrá acceder con el usuario “admin” y su contraseña “admin”.

### Login - Register - Logout
El usuario se puede registrar como Usuario normal o Administrador. Al registrarse se guarda en la BD el User junto con su User Role completos. Su contraseña se introduce en la BD encriptada respetando un principio básico de Bases de Datos.
Si el usuario es un usuario normal, carga el home para que solo permita registrar una compra y no tiene acceso al resto de vistas Admin. En cambio, si es Admin, tiene acceso a todas las vistas de la app. Todo esto implementado desde los filtros de seguridad.

### Alta, baja y modificación de productos
Los administradores pueden dar de alta nuevos productos, creando en la BD tanto al producto como a su stock relacionado. La única restricción es que el código de producto no se repita. En caso de repetirse, muestra un error y no impacta en la BD.
Desde la vista de lista de productos, se puede ver su estado, en relación también a su stock. Tanto la cantidad almacenada en ese momento como su cantidad mínima requerida.
Al momento de eliminar el producto, chequea sus relaciones y sólo permite eliminar si el producto tiene un stock asociado, pidiendo confirmar la eliminación para no permitir bajas involuntarias. Si tiene relaciones con alguna otra tabla, no permite hacerlo directamente.

### Entrada de productos
Los administradores pueden crear nuevos lotes, es decir, un ingreso de una cantidad determinada de un mismo producto. Esto actualiza el stock almacenado del mismo. Queda registrado en la BD con su fecha vinculada. También, se permite crear varios lotes de un mismo producto.
Posee una vista donde se puede ver reflejado el historial de lotes ingresados.

### Salida de productos en stock
Tanto administradores como usuarios pueden crear ventas, o compras si lo vemos del lado de un usuario normal. Cuando se vende un producto se registra la salida en el sistema. En la BD actualiza el stock del producto vendido y no permite realizar la venta del producto si no posee el stock necesario.
El administrador tiene una vista donde puede chequear todas las ventas que se realizaron, detallando el usuario que la creó. Esto último lo hace automáticamente.
Si es un usuario normal, puede ver la lista de compras que realizó pero no la de otros usuarios. Pueden realizar la cantidad de compras que deseen siempre y cuando haya stock.

### Control de niveles de stock
El sistema monitorea constantemente los niveles de stock de cada producto. Por defecto lo tenemos seteado en 30 segundos pero se podría cambiar al tiempo deseado.
Si las existencias de un artículo pasan a estar por debajo del mínimo requerido, lanza una alerta en la lista de pedidos y la de productos. Ayudando así a prevenir la falta de productos populares y optimizando la gestión del inventario. 

### Reabastecimiento
Este proceso inicia cuando se activa la alerta de bajo stock. Se crea un nuevo pedido en la BD y podemos verlo en la vista a su correspondiente listado. Dentro de esa misma vista se genera un botón para cargar Lote. Por defecto, crea el lote con la cantidad faltante multiplicada por 2, para asegurarse así de reabastecer sobrepasando el mínimo requerido. Una vez que el producto fue reabastecido, el pedido se borra de la BD y lo dejamos de ver en el listado.

### Este sistema fue construido con:
- *Java*
- *Spring*
- *Hibernate*
- *Maven*
- *MySQL*
- *Html5*
- *Css3*
- *Javascript*

[Documentación presentada](https://drive.google.com/file/d/1yeO9yIvcBDLz7llNLAf3XDWFv2Y6qwrO/view)