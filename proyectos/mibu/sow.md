Autores: Miguel Ruiz

Última revisión: 4 de abril del 2022

# Proyecto MIBU CEDIS

# Tabla de contenidos

[TOC]

# 1.0 Contexto

Empanadas MiBu pondrá un **Centro de Distribución (CEDIS)** en donde van a comprar los ingredientes necesarios para el negocio y también crear los ingredientes derivados de una **receta** necesarios para las empanadas. Los ingredientes que se mandan a las otras sucursales tienen una “porción”, e.g., 2500 gr de guisado de atún o 1200 gramos de picadillo, y cada ingrediente puede tener una porción distinta, por lo que esto es información registrada por el gerente general. Cantidades enteras de porciones de dichos ingredientes se van a mandar a las distintas sucursales mediante una solicitud de cada sucursal. De manera que las sucursales ya no tienen contacto con la lógica de los gastos en ingredientes. A continuación se describen los nuevos casos de uso. **NOTA:** hay algunos casos de uso de la aplicación actual con mejoras.

## 1.1 Sucursales

Ahora se podrá tener **administración de sucursales**. Una sucursal puede ser de una *Sucursal de Venta* o *Centro de Distribución (CEDIS)*. En cada sucursal hay un *Gerente de ventas* (ver sección *1.2 Usuarios*), pero dependiendo de la sucursal (de ventas o CEDIS) son los módulos que tendrá dicho usuario en la aplicación. Además, en las sucursales de venta hay usuarios de ventas y de producción de sucursal (ver sección *1.2 Usuarios*).

## 1.2 Usuarios

Se busca integrar a la aplicación 4 roles de usuario explicados a continuación.

1. **Gerente general**: Antes administradores. Tiene acceso a todos los módulos de todas las sucursales (incluyendo al CEDIS, que también se considerará como sucursal).
2. **Gerente de sucursal**: Tiene acceso a todos los módulos de su sucursal (de venta o CEDIS). En el caso de las sucursales de venta, el gerente de sucursal tendrá acceso a las estadísticas de venta de su sucursal.
3. **Usuario de Ventas:** Ver sección *4.0 Módulos para el usuario de ventas*.
4. **Usuario de Producción de sucursal:** Ver sección *5.0 Módulos para el usuario de producción de sucursal*.

# 2.0 Módulos para el Gerente General

Se busca tener el control de todas las sucursales desde una sola aplicación. Dependiendo del usuario que inicie sesión en la aplicación de Empanadas MiBu, será lo que observe el usuario en la interfaz principal después del login. El módulo de estadísticas podrá dar la información de todas las sucursales registradas.

## 2.1 **Módulo de Catálogos**

En este módulo se administran todas las entidades de la aplicación (se crean, editan o eliminan), y sólo es disponible para los usuarios de tipo *Gerente General*, como actualmente se hace. En este módulo se tendrán los submódulos de “Productos”, “Tipo de Productos”, “Subtipo de Productos”, “Ingredientes”, “Usuarios”, “Promociones”, “Sucursales” y “Proveedores”. A continuación se muestran los submódulos que serán modificados.

### 2.1.1 **Productos**

Los productos se venden a través del punto de venta. Un producto no necesariamente tiene ingredientes, como las bebidas embotelladas. Modificar este submódulo para tomar en cuenta productos que no tengan asociados ingredientes, asignarle un proveedor y que el usuario de ventas registre gastos en estos productos (ver *4.3 Módulo de gastos*). 

### 2.1.2 **Ingredientes**

Los ingredientes tienen una unidad asociada (PZ, G, KG, etc.), y son la materia prima del negocio (harina, jamón, mermelada, etc.). Algunos de estos ingredientes se compran a un proveedor (ver *Catálogos/Proveedores*) y otros son producidos con una *receta* a través de otros ingredientes (pueden que estos ingredientes producidos o ingredientes básicos). Una receta toma cierta cantidad de un conjunto de ingredientes y produce una cantidad del ingrediente a producir. Algunos de estos ingredientes tienen una *porción* que se define en este submódulo (puede ser 600 G, 1 KG o 1 PZ) y se mandan porciones enteras a las sucursales de venta (ver *Módulos del usuario del CEDIS / Módulo de recepción de solicitudes de ingredientes* y también *Módulos del usuario de producción de sucursal / Módulo de solicitud de ingredientes).* 

### 2.1.3 **Proveedores**

Administrar la lista de proveedores a los cuales se les compran ingredientes o productos (como las bebidas embotelladas de Coca-Cola). 

### 2.1.4 **Sucursales**

Ahora se podrá tener **administración de sucursales**. Una sucursal puede ser de una *Sucursal de Venta* o *Centro de Distribución (CEDIS)*. En cada sucursal hay un *Gerente de sucursal* (ver *Catálogos/Usuarios*), pero dependiendo de la sucursal (de ventas o CEDIS) son los módulos que tendrá dicho usuario en la aplicación. Además, en las sucursales de venta hay usuarios de ventas y de producción de sucursal (ver *Catálogos/Usuarios*).

### 2.1.5 **Usuarios**

Se podrá asignar a cada usuario una sucursal para que al entrar a la aplicación se pueda saber de qué sucursal está ingresando. Además, se generará automáticamente un IDE (ID de Empleado) con el que se va a iniciar sesión y una contraseña con formato @####, donde #### es un número secuencial de 4 dígitos y @ una letra de A-Z. El IDE tendrá información del rol del usuario. Los roles posibles son Gerente general, Gerente de sucursal (de venta o de CEDIS), Usuario de Ventas, Usuario de Producción de sucursal (ver sección *Usuarios*)*.*

## 2.2 **Módulo de estadísticas**

1. Ver las estadísticas de cada una de las sucursales registradas, así como estadísticas de todas las sucursales en conjunto.
2. Gráfica de las unidades vendidas de productos escogidos por el usuario a través de un Multiselect. Poner las gráficas en el siguiente orden: Subtipos, Productos, Ventas, Gastos.
3. Recuadro de información al pasar el cursor sobre los días del calendario para poder ver el número de empanadas vendidas.

## 2.3 **Módulo de órdenes**

1. Ver el historial de todas las órdenes de cada sucursal, incluso aquellas que fueron canceladas-eliminadas
2. Poder cancelar/eliminar órdenes sólo **del día actual.** Al eliminar una órden, no contar el dinero de esa venta en la caja o fondo, y tampoco considerarlo en las estadísticas. El stock de las empanadas se dejaría como si no se hubiera hecho la venta.

## 2.4 **Módulo de asistencia de empleados**

Ver el historial de asistencia de todos los usuarios por cada sucursal.

## 2.5 **Módulo de inventario**

Ver y editar el inventario de ingredientes del CEDIS y de cada sucursal, así como el inventario de productos de cada sucursal.

## 2.6 **Módulo de Check in-out**

Ver el historial de check in-out’s creados por los usuarios de ventas por cada sucursal. Además, poner en el check out el número de empanadas por subtipo, número de bebidas, bolsas y vasos que registró el usuario.

# 3.0 Módulos para el Gerente de sucursal

En el caso de una sucursal de Venta (ver sección *Sucursales*), el gerente de sucursal podrá tener acceso a los módulos de los usuarios de venta y los usuarios de producción de sucursal, junto con las estadísticas de venta de la sucursal (ver secciones *Módulos para el usuario de ventas, Módulos para el usuario de producción de sucursal*). 

En el caso de una sucursal CEDIS, a continuación se detallan los módulos a los que tendrá acceso el gerente de sucursal.

## 3.1 **Módulo de recepción de solicitudes de ingredientes de las sucursales.** 

Los usuarios de producción de las sucursales tendrán un módulo para mandarle al CEDIS los ingredientes para hacer las empanadas que les hacen falta (ver *Módulos para el usuario de producción de sucursal /* *Módulo de solicitud de ingredientes*). En este módulo los usuarios del CEDIS pueden ver las solicitudes recibidas en una tabla con los siguientes datos: Fecha, Sucursal, Estatus (*Nueva*, *En proceso*, *En tránsito*, *Entregada,* *Ingrediente rechazado* o *Rechazada*), y Detalles. 

En la columna Detalles habrá un link “Ver” por cada solicitud que desplegará una ventana emergente con los detalles de la solicitud en una tabla: Ingrediente, Cantidad pedida (número de porciones), Cantidad a enviar (por defecto son los valores de "Cantidad pedida" pero con la opción de modificar); y al final de la ventana habrá un botón "Lista para enviar" y  otro botón "Rechazar".  En esta ventana emergente el usuario tiene la opción de salir de la ventana con un ícono ❌ antes de dar clic en “Lista para enviar” o “Rechazar” en la solicitud en cuestión.

Recién creada la solicitud se encuentra en estado *Nueva,* y al dar clic en “Ver” la solicitud pasará al estado *En proceso*. Si se da clic en el botón “Rechazar” en la ventana que se desplega al dar clic en “Ver”*,* la solicitud pasa al estado *Rechazada.* Si se da clic en el botón “Lista para enviar”, la solicitud pasará al estado *En tránsito*. Los ingredientes que se envían tienen la posibilidad de ser rechazados por el usuario de producción por recibir menos porciones de las que se enviaron (ver sección *Módulos para el usuario de producción de sucursal / Módulo de recepción de ingredientes*). Al ver los detalles de una solicitud con un ingrediente que fue rechazado por el usuario de producción, se podrá ver explícitamente el ingrediente rechazado mediante un ícono (e.g., ❗ó ⚠️).

Se debe diferenciar las solicitudes en estado *Nueva* de los demás estados. Los otros estados se obtienen con la interacción entre las solicitudes y los usuarios de producción de sucursal (ver *Módulos para el usuario de producción de surcursal / Módulo de solicitud de ingredientes*). 

## 3.2 **Módulo de gastos en ingredientes.**

Este módulo es para llevar un registro de los gastos que se hacen en los ingredientes que son la materia prima del negocio. Funciona igual que el módulo actual de gastos en insumos (con la mejora de agrupación de los gastos fecha descrita en la sección *Casos de uso faltantes (sin costo)*)  en la aplicación pero con dos mejoras. 

1. Se debe asociar a cada ingrediente un *proveedor* y agrupar los ingredientes por proveedor al hacer un nuevo gasto en insumos. Esto es para facilitar el registro de un gasto, pues cada gasto tendrá muy probablemente ingredientes de un mismo proveedor.
2. Al hacer un nuevo gasto, se debe tener la opción de utilizar dinero digital en fondo, o dinero en efectivo en fondo (esta última opción por defecto).

**Nota:** Las bebidas embotelladas **NO** se compran en el CEDIS. El proveedor Coca-Cola pasa a cada una de las sucursales a dejar el producto, por lo que este gasto se registraría por el usuario de ventas (ver sección *Módulos para el usuario de ventas,* subsección *Módulo de gastos*).

## 3.3 **Módulo de inventario**

Se debe tener un inventario de los ingredientes que hay en el CEDIS, incluyendo las masas (tortillas, con las que se hacen las empanadas) que también se considerarán como ingredientes. Para los ingredientes que no son materia prima (los creados por recetas), se debe mostrar el número de *porciones* enteras que se pueden hacer con el stock actual de dicho ingrediente, el *sobrante* que será igual al stock actual menos el stock que hay en las prociones (en las unidades del ingrediente, i.e., KG, o G), y el stock actual dicho ingrediente. Para los otros ingredientes sólo mostrar el stock actual. Para todos los ingredientes mostrar la fecha de última modificación (como actualmente se hace con los insumos). El usuario del CEDIS sólo tiene acceso de lectura al inventario, pero el administrador sí podría editar el inventario.

## 3.4 **Módulo de producción del CEDIS**

No es la misma producción de empanadas que hay en las sucursales. Aquí se pueden producir ingredientes a través de otros ingredientes. Cada ingrediente tiene una unidad asociada (como en la lógica actual, i.e., G o KG), y se produce una cantidad que puede ser decimal de dichas unidades. En este mismo módulo se podrá visualizar el historial de producciones.

# 4.0 Módulos para el usuario de ventas

Incluye lo que actualmente hace el usuario de empleado con algunos cambios.

## 4.1 **Módulo POS**

1. Al vender un frappucino o malteada, descontar los insumos que le corresponden. En el punto de venta, el stock de las bebidas frappucino y malteada representará el número de bebidas que se pueden hacer con el stock actual (vasos, helados, café, etc.). Al dar clic a uno de esos productos, el stock se tiene que reducir en una unidad en todos los productos del subtipo que se agregó a la comanda. Si no hay stock, SÍ se dejará vender y el stock de los ingredientes se volvería negativo. El vaso para la malteada y el frappé es el mismo.
2. Imprimir ticket después de hacer una venta.
3. Vender bolsas de papel con un botón análogo a los botones de chimichurri y cátsup.
4. Mostrar el número total de empanadas en la comanda. 

## 4.2 **Módulo de retiros**

Nuevo apartado para hacer retiros y mostrar historial de retiros de caja a fondo (para empleados y administradores). Actualmente sólo se puede hacer en el check-out. La posibilidad de retiro en el check-out se quitará por simplicidad. Cada retiro debe tener asociado los siguientes datos: Fecha y hora, usuario, turno, cantidad y fajilla (estos dos últimos son los únicos datos que debe ingresar el usuario). En el historial del check-out mostrar el total de dinero retirado de caja a fondo en la sesión. 

## 4.3 **Módulo de gastos**

Registrar gastos generales, quitar gastos en insumos y registrar gastos en bebidas embotelladas. Al hacer un nuevo gasto, se debe tener la opción de utilizar dinero de caja, dinero digital en fondo, o dinero en efectivo en fondo, donde el dinero de caja será la opción por defecto. Al registrar un gasto en bebidas embotelladas, se debe actualizar el inventario de los productos comprados.

## 4.4 **Módulo de producción**

1. Al registrar una nueva producción y tener el cursor en el campo para ingresar la cantidad a producir de una empanada específica: resaltar dicha empanada para una mejor UI y al dar enter cambiar a la siguiente empanada.
2. Mostrar el número total de charolas (con 1 decimal) que se van acumulando al ingresar las empandas para la producción (tanto al registrar una nueva producción como en el historial de todas las producciones). Una charola es igual a 16 empanadas, y este dato les sirve porque al producir empanadas sólo se pueden ingresar charolas completas, por lo que si el software muestra un número decimal en el número de charolas significa que deben quitar o agregar más empanadas para tener un número entero de charolas por subtipo.
3. Después de registrar la producción, todas las empanadas de la producción tendrán el estado “*Pendiente”*, y el usuario de producción de la sucursal podrá ver la solicitud hecha por el usuario de ventas. El usuario de producción de la sucursal en cuestión manipulará los otros estados de las empanadas de la producción registrada: “*Horneando*”, “*Lista*” o “*Rechazada”* (ver sección *Módulos para el usuario de producción*, subsección *Módulo de producción*). 

## 4.4 **Módulo de check in-out**

1. Al hacer check-out se debe ingresar el dinero en caja, y el inventario de empanadas (esto es lo que actualmente se hace), de bebidas embotelladas, de vasos, y de bolsas de papel.
2. El check-in que sea sólo confirmación del check-out anterior, i.e., mostrar los datos ingresados en el check-out anterior y permitir modificar si hay algún cambio. En la lista de check-in/out, mostrar en el check-in si hubo confirmación o en caso contrario mostrar las correcciones.

# 5.0 Módulos para el usuario de producción de sucursal

Este usuario se encarga de la lógica de negocios asociada a la producción de las empanadas. En una sucursal hay varios empleados que usarían un mismo usuario de producción, por lo que el usuario tendría contraseña conocida por el equipo de producción. 

## 5.1 **Módulo de registro de asistencia**

Registrar la asistencia de los integrantes del equipo de producción ingresando su contraseña de empleado (de la forma @####$$ donde $$ son 2 digitos aleatorios que se generarán a la creación del usuario).

## 5.2 **Módulo de solicitud de ingredientes.**

Mandar a CEDIS la lista con las porciones de los ingredientes que requiere la sucursal. Mostrar historial de las solicitudes hechas. Al hacer una nueva solicitud, se muestra una UI como al registrar una merma, y al dar clic en el botón “+” se puede ir agregando de porción en porción. Sólo se mandan porciones enteras. 

Al crear la solicitud está en estado *Nueva* (ver *Módulos para el usuario del CEDIS / Módulo de recepción de solicitudes de ingredientes de las sucursales* para ver cómo la solicitud pasa a otros estados*).* Cuando el usuario de producción reciba los ingredientes que solicite, tiene que confirmar que recibió las porciones correctas de cada uno de los ingredientes. Para esto, habrá dos botones por cada ingrediente: uno para confirmar y otro para rechazar.

Al rechazar un ingrediente, no se entregará a la sucursal y se regresará al CEDIS. El ingrediente podrá ser visualizado como rechazado mediante un ícono (e.g., ❗ó ⚠️) en los detalles de la solicitud de ingredientes, tanto para el usuario de producción de sucursal como para el gerente de surcursal CEDIS que envió la solicitud, y la solicitud pasará al estado *Ingrediente rechazado.* También se actualizará el inventario de ingredientes del CEDIS como si el ingrediente rechazado no se hubiera mandado. Un usuario administrador tendría que editar el inventario de ser necesario en los rechazos. Si se confirman todos los ingredientes recibidos, la solicitud pasará al estado *Entregada.*

## 5.3 **Módulo de producción**

Ver historial de las producciones registradas por el usuario de ventas y ver los detalles de cada producción. Cada producción tiene 4 posibles estados: *Nueva, Pendiente, Finalizada, Rechazada*. Se debe distinguir las producciones nuevas para mejor UI del usuario de producción. Las producción recién registradas están en el estado *Nueva*, y al ver los detalles de dicha producción pasa al estado *Pendiente.* Al ver los detalles de una producción se muestra una ventana emergente con una tabla con los siguientes encabezados: Empanada, Cantidad pedida, Cantidad a producir, Pin de empleado, Horneando, Lista.

1. En la columna “Empanada” se muestra la empanada que se quiere producir.
2. En la columna “Cantidad pedida” se muestra la cantidad de las empanadas en cuestión que el usuario de ventas quería.
3. En la columna “Cantidad a producir” se puede ingresar un número distinto que la cantidad pedida y mayor que 0. El número por defecto es la cantidad pedida. La cantidad pedida por el usuario de ventas no siempre podrá realizarse, y aquí el usuario de producción pondrá una cantidad menor o mayor que previamente acordó con el usuario de ventas. Si se ingresa un 0, se bloquean los checkbox de las columnas “Horneando” y “Lista”, y denotaría que el usuario rechazó la empanada solicitada.
4. En la columna “Pin de empleado” se ingresa el pin del empleado (de la forma @####$$; mostrarlo como contraseña) que se encargó de la producción de dicha empanada.
5. En la columna “Horneando” se muestra un checkbox para denotar que dicha empanada ya se está horneando. Al seleccionar el checkbox se desbloquea el checkbox de la columna “Lista”, se bloquea la modificación del input en las columnas “Cantidad a producir” y “Pin de empleado”, el estado de la empanada de la producción pasa al estado “*Horneando*”, y el inventario de ingredientes se actualiza disminuyendo el stock de los ingredientes de la empanada en cuestión. Si se quita la selección del checkbox de nuevo, se bloquea el checkbox de la columna “Lista”, se elimina el Pin de empleado para que se tenga que volver a ingresar, y se modifica el inventario de ingredientes aumentando el stock de los ingredientes correspondientes.
6. En la columna “Lista” se muestra un checkbox que se desbloquea cuando el checkbox de la columna “Horneando” está seleccionado. Al seleccionar el checkbox la empanada de la producción pasa al estado “*Lista”,* ya no se permite modificación de su información, y se actualiza el stock de dicha empanada para mostrarse en el POS.

Al final de la ventana emergente hay un botón de Rechazar para rechazar toda la producción, que sólo se muestra mientras una producción está en estado *Nueva* o *Pendiente*. Si se da clic a ese botón, la producción pasa al estado *Rechazada*. La producción pasa del estado *Pendiente* al estado *Finalizada* cuando todas las empanadas de la producción están en el estado *Lista* o hayan sido rechazadas con un 0 en la columna “Cantidad a producir”*.*

## 5.4 Módulo de panel de notificaciones

Hay situaciones en los que los usuarios deben ser notificados de algún evento. Mostrar un ícono siempre en la aplicación con el número de notificaciones sin leer. Una notificación mostrará un texto adecuado para cada evento. Dando clic en la notificación se marcará como leída, y en caso de ser necesario redirigirá al usuario al URL del módulo adecuado. Al recibir una notificación, emitir un sonido para avisar al usuario.

Las notificaciones existentes serán las siguientes:

1. Para el usuario de producción de sucursal, notificar cuando sus solicitudes de ingredientes pasaron al estado *En tránsito*.
2. Para el usuario de producción de sucursal, notificar cuando tiene una nueva solicitud de producción por parte del usuario de ventas.
3. Para el usuario del CEDIS, notificar cuando reciba una nueva solicitud de ingredientes.

# A.0 Apéndice

## A.1 Cambios varios

1. Botón de nuevo más grande en todos los módulos (e.g., mermas, producción, catálogos, etc.)
2. Ventanas emergentes full screen (o al menos más grande) a partir de cierta resolución (en los dispositivos como tabletas o más pequeños)
3. Habrá un fondo unificado en el que se acumulará todo el dinero que se paga con tarjeta en las sucursales (dinero digital en fondo) así como el dinero en efectivo retirado de cada sucursal (ver *Módulos para el usuario de ventas / Módulo de retiros).* 
4. Cuando se registra una merma, al escoger una empanada y darle clic en el botón “+” varias veces se debe ir recalculando el número de la empanada agregada a la merma. Actualmente se muestra una lista con la misma empanada múltiples veces.
5. Al iniciar sesión, se guarda el turno actual dependiendo de si la hora de inicio es antes o después de las 1:50 pm. Considerar este turno en las estadísticas para tener en cuenta los casos cuando el usuario de ventas del turno matutino registra órdenes en el POS después de las 2 pm (e.g., cuando llega tarde el empleado del turno vespertino).
6. En la Comanda del POS, debajo del botón de total, mostrar el número total de empanadas en la comanda.

## A.2 Casos de uso sin modificación

1. **Módulo del punto de venta**

Permite al usuario de ventas (y al administrador) vender productos, manipular la visibilidad de los productos en el menú, aplicar promociones, y registrar pedidos.

2. **Módulo de pedidos**

Permite al usuario de ventas visualizar los pedidos *Pendientes* y *Entregados.* Permite editar los datos del pedido y su estado, así como eliminar un pedido en caso de cancelación.

3. **Módulo de mermas**

Permite al usuario de ventas registrar mermas de las empanadas y ver el historial de mermas. 

## A.3 Correción de errores

1. No se pueden borrar los vasos de bebidas calientes en el catálogo de insumos en ambas sucursales.
2. Considerar el turno vespertino después de la 1:50 pm en la lógica de la sesión.
3. El día 14-03-22 no coincidía el total vendido que aparece en la página principal de estadísticas con lo que reportaba el resumen diario.

## A.4 Nueva lógica para el manejo de ingredientes/insumos

En la lógica actual de la aplicación, hay insumos que representan toda la materia prima de Empanadas MiBu, hay ingredientes que se componen de ciertos insumos, y productos que tienen ingredientes. Ahora se pretende cambiar la lógica para que sólo haya **productos e ingredientes**. Los ingredientes pueden ser materia prima, pero también mediante **recetas** que combinen otros ingredientes se podrá formar un nuevo ingrediente. **OJO:** Las recetas pueden incluir ingredientes que no son materias primas. Esto es para considerar el proceso de la creación de las masas. Este proceso convierte harina en paños, y después se convierte en tortillas listas para usarse en las empanadas. Este proceso se llevará a cabo mediante el *Módulo de producción del CEDIS* (ver sección *Módulos para el usuario del CEDIS)*.
Un ingrediente se podrá comprar o no. En el **Módulo de gastos en ingredientes** se podrán registrar gastos de aquellos ingredientes que se pueden comprar (ver detalles en *Nuevos Casos de Uso / Módulos para el usuario del CEDIS*).

## A.5 Definiciones

Al usuario administrador en la lógica actual ahora le llamaremos Gerente general. Por lo que en este documento el administrador y el gerente general son intercambiables.

## A.6 Casos de uso faltantes (sin costo)

1. Poder asignar promociones a la comanda en el punto de venta. Una promoción será únicamente un descuento en efectivo o en porcentaje del costo total, y tendrá asociado un número *applyIf* que permitirá que una promoción sea sólo aplicada cuando el valor de la comanda es igual a *applyIf.* Esto tiene la desventaja de que sólo podrá aplicarse una promoción a la vez y de que hay varias maneras de lograr que la comanda tenga un costo total de *applyIf*, pero la ventaja es que disminuyen el riesgo de que el empleado aplique promociones sin ninguna restricción. Habrá promociones disponibles sólo para la viste de administrador (como el descuento de empleado) y otras vistas también para el usuario de ventas.
2. Ver los gastos en ingredientes agrupados por fecha. Actualmente, se hace un gasto asignando la cantidad de los ingredientes comprados y el costo total de todos ellos, y en el apartado de gastos en ingredientes se visualizan todos los ingredientes comprados, pero con un costo asociado igual al costo total dividido entre el número de ingredientes del gasto.

# B.0 Módulos

1. Catálogos
   1. Sucursales
   2. Usuarios
   3. Proveedores
   4. Ingredientes
   5. Productos
   6. Descuentos/promociones
2. Estadísticas
3. Órdenes
4. Asistencia
5. Check in-out
6. Solicitudes de ingredientes
7. Gastos en ingredientes
8. Inventario de ingredientes
9. Producción de ingredientes
10. POS
11. Retiros
12. Gastos generales
13. Gastos en productos
14. Producción de productos
15. Notificaciones
16. Wallet (dinero)
17. Mermas
18. UI/UX