# OpenMarket
Plataforma tecnológica para hacer mercadeo

# Documento del Proyecto

## Descripción del Problema
La empresa Colombo-Argentina Digital Asociados SA, está interesada en lanzar al mercado una plataforma tecnológica para hacer mercadeo por internet y ser competidores de plataformas conocidas como Mercado Libre. Esta empresa requiere desarrollar una aplicación back-end que permita a sus usuarios comprar, vender y distribuir productos en línea por medio de una aplicación web de forma segura, rápida y fácil de usar.  A continuación se detallan los requisitos funcionales y no funcionales de esta aplicación: 
1. Datos de los usuarios
  a. Loguear un usuario con uno de los roles del sistema.
  b. La creación de usuarios se puede hacer por script de BD. 
  c. Hay parámetros de configuración del sistema que se cargan en la BD. 
2. Rol vendedor: Alta Baja y Modificación de productos (CRUD) 
  a. Agregar productos ofrecidos. 
    i. Debe tener al menos nombre, descripción, precio, categoría y ubicación (eligiendo alguna del vendedor).
  b. Modificar stock de productos ofrecidos (Atención el proceso de checkout)
  c. Publicar producto
  d. Suspender publicación.
3. Rol usuario: Búsqueda
  a. Listar productos.
  b. Búsqueda de productos. Las búsquedas son por palabras (ya sean en el nombre como así también en la descripción). 
  c. (Bonus) Se pueden aplicar filtros: por rango de precios, por categoría y por ubicación. 
4. Rol usuario registrado: Carrito de Compra
  a. Ver carrito de compra
  b. Agregar producto al Carrito de Compra.
  c. Quitar producto del carrito.
  d. Limpiar Carrito.
5. Rol usuario registrado: Check out (realizar compra)
  a. Las compras se administran con carrito de compras. 
     i. El carrito no vence. 
  b. Al realizar el checkout, se genera un deliveryOrder por cada ítem del carrito.  Luego del check out, el carrito queda vacío y se da de baja el stock en Producto
6. Rol Entregador / Delivery / Repartidor
  a. Ver productos para entregar: son aquellos que hayan sido comprado()s por los usuarios registrados, es decir, los que estén en un comprobante de compra
  b. Tomar producto para entregar
  c. Entregar producto al comprador
## Propuesta de División:
### Modelo Preliminar Minimalista de Clases de Negocio por Subdominios (Cada color representa un subdominio)


## Consideraciones de la arquitectura de software
La aplicación a desarrollar está compuesta por un microservicio por cada color expresado en Modelo General y que serán los siguientes:

Usuario/Persona (color marrón), Producto (color verde), Compra (color cyan) y  Delivery (color lila)

La aplicación permitirá a los vendedores publicar productos, a los compradores buscarlos y comprarlos y finalmente a los repartidores llevar los productos desde el vendedor hasta el comprador. Esto implica que se debe plantear una arquitectura de software que soporte la escalabilidad (a medida que se sumen usuarios compradores y vendedores) y la seguridad de los datos (el sistema, a pesar que es uno sólo, debe aislar la información de usuario, importante definir mecanismo de autenticación y autorización seguros).

No se solicita desarrollar interfaz gráfica para la aplicación. Es suficiente con desarrollar los servicios REST.
Cada microservicio debe ser independiente de los demás, se sugiere utilizar un enfoque de puertos y adaptadores (hexagonal, limpia, dirigida por dominio), además cada microservicio debe tener su propia base de datos (esta puede estar en memoria). La información que no se encuentre en su base de datos deberá ser consultada a través de las API Restful de otros microservicios.

## Entregables
* Documentación de la arquitectura y sus decisiones de diseño más relevantes.
* Proyecto java completo en Gitlab: código fuente e imágen Docker
* Colección postman para ejecutar los escenarios
* Documentación de los servicios con Swagger.
