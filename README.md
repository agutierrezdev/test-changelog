# Changelog

### Cargar imagenes en Pop-up del MES sin tener que subir un nuevo war.
> *Diego Alvitres - 08/05/2021*, [Trello](https://trello.com/c/T6xUkjpL/235-insertar-flyer-promoci%C3%B3n-del-mes-en-plataforma-mes)
+ [BD-Soporte] Se agregaron 2 campos a la tabla modal: has_link y link, el cual guardará información de links a redireccionar en el botón Más Información. 
+ [Desarrollo] Se modificó la lectura de imágenes que se muestran en el pop-up y ahora se cargan las imagenes desde la ruta del servidor /home/ubuntu/mes/images/ que estén activas (status = true en tabla modal), si existen mas de un registro activo obtendrá una imagen aleatoriamente, el identificador es el nombre, y se muestra el botón de Más Información si el campo has_alert está en true y si el campo link tiene algun valor (!=null). 
Si no encuentra la imagen en la ruta específica cargará la imagen default.jpg que es uma imagen de Bienvenida (dice: Welcome).

### Alertas para usuarios que excedan un porcentaje registrado.
> *Diego Alvitres - 08/05/2021*, [Trello](https://trello.com/c/IYm38U26/238-kobsa-modificaciones-para-la-plataforma-sige-secci%C3%B3n-gesti%C3%B3n-usuarios)
+ [BD-Soporte] Se agregaron 2 tablas: alert_detail y corporates_alert, la primera para agregar los clientes o usuarios que van a recibir la alerta, con los datos correspondientes: porcentaje, mensaje a enviar y otros. En la tabla corporates se agregó el campo has_alert para habilitar a usuarios que tengan alertas. 
+ [Desarrollo] Se creó un jar que verifica el consumo y las tablas mencionadas anteriormente para ver si hay alertas por enviar, si encuentra llama a la funcion fn_register_alert_for_corporates() la cual inserta un registro en el outoing para enviar el SMS al asesor, el cual obtendrá el número del asesor del campo virtual_line de la tabla corporates, luego insertará un registro en la tabla corporates_alert con el detalle de envio y se actualiza una campaña donde se registraran todas las alertas.
+ [Desarrollo] En el mes se mostrará una alerta en la pestaña de inicio si es que ha excedido su porcentaje configurado. (y tiene que tener activo el has_alert en la tabla corporates)

### Nuevo tipo de Bolsa con limite diario y extra
> *Diego Alvitres - 08/05/2021*, [Trello](https://trello.com/c/IYm38U26/238-kobsa-modificaciones-para-la-plataforma-sige-secci%C3%B3n-gesti%C3%B3n-usuarios)
+ [BD-Soporte] Se agregaron 2 campos en la tabla Corporates day_limit y extra_limit para asignacion de bolsa diaria y bolsa extra, se agregó un nuevo valor (3) para el campo has_limit, el cual habilita esta bolsa. Tambien se agregaron estos campos en la tabla corporates_audit.
+ [BD-Soporte] Se modificó la funcion de obtención del consumo y se creó una nueva para obtener consumo de esta bolsa diaria: sp_get_daily_limit(), se creó la función sp_update_corporates_user_info3() que se llama en el SIGE para actualizar los datos, y la función sp_audit_corporates() que se ejecuta como Trigger de la tabla corporates al realizar alguna modificación.
+ [Desarrollo] Se agregó en la sección de Usuarios del SIGE, el tipo de bolsa: **Limitada extra** y 2 cajas de texto para que agreguen los limites diario y extra.
+ [Soporte] Los usuarios que tengan habilitada esta bolsa al cargar su campaña se verifica 2 veces su consumo, uno el limite "real" (Mensual) y el limite diario + el extra, se muestra una alerta por si ha superado alguna de las bolsas.

### Nuevo proveedor para número corto (Aldeamo)
> *Diego Alvitres - 08/05/2021*, [Trello](https://trello.com/c/zdAO5VWa/212-cambio-de-proveedor-aldeamo)
+ [Desarrollo] Se creó un nuevo jar para enviar por Aldeamo la mayoria de campañas de los clientes. Y se modificó el jar de Broadcaster para que solo salgan las campañas de los clientes Santander, Konecta, 3eriza y Mapfre.
+ [Desarrollo] Se habilitó un servicio WEB (Webhook) para que nos envien las respuestas (MO), las ùltimas pruebas mostraron que solo estaban enviando algunas respuestas no todas que se muestran en su plataforma.

### Filtro Caracteres Raros en el MES
> *Diego Alvitres - 08/05/2021*, [Trello](https://trello.com/c/EQSNwqZC/172-requerimientos-de-plataformas-e-incidencias)
+ [Desarrollo] Se agregaron filtros para caracteres raros en la carga de campañas tanto por archivo y para campañas por personalizado, también para los mensajes del ChatCRM.

 
### Envío de mensajes por número corto con más de 160 caracteres
> *Diego Alvitres - 18/03/2021*, [Trello](https://trello.com/c/jgvhqOEr/118-soporte-mowa-sms)
+ [Soporte] Se agregó un nuevo campo para activar la opción de envío de más de 160 caracteres a los usuarios.
+ [Sistemas] Se agregó en la creación de campañas por excel una validación para detectar si tiene mensajes con más de 160 caracteres, de ser así se muestra una opción de Salida: **Corto con más de 160 caracteres** y posteriormente la cantidad total de mensajes a enviar.
+ [Comercial] Los mensajes que superen los 160 caracteres se "dividen" en mensajes de 153 caracteres (Es lo que factura el proveedor), posteriormente se muestra el **Total de mensajes** a enviar en la ventana de confirmación.

### Características actuales de Mowa...
 - ...

### Descripción
> *Cambios Productos - 18/03/2021*, Se crea la primera versión (beta) del documento: Changelog, donde se mostrará los cambios realizados en los productos de Mowa Consultora de una manera rápida y no formal, con el fin de que el equipo completo pueda enterarse de los últimos cambios importantes que se realicen y los conozcan y si alguno es de su interés puede abundar aun mas en él. El documento de Changelog por ahora es una versión beta que se quiere implementar (quizás no funcione), si alguien del equipo quiere mostrar algún cambio que realice en los productos (ya sean Comerciales , Sistemas , Soporte .. en general) puede utilizar el documento de cambios sin ningún inconveniente.

