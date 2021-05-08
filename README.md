# Changelog

### Nuevo tipo de Bolsa con limite diario y/o extra
> *Diego Alvitres - 08/05/2021*, [Trello](https://trello.com/c/IYm38U26/238-kobsa-modificaciones-para-la-plataforma-sige-secci%C3%B3n-gesti%C3%B3n-usuarios)
+ [BD-Soporte] Se agregaron 2 campos en la tabla Corporates day_limit y extra_limit para asignacion de bolsa diaria y bolsa extra, se agregó un nuevo valor (3) para el campo has_limit, el cual habilita esta bolsa. Tambien se agregaron estos campos en la tabla corporates_audit.
+ [BD-Soporte] Se modificó la funcion de obtención del consumo y se creó una nueva para obtener consumo de esta bolsa diaria: sp_get_daily_limit(), se creó la función sp_update_corporates_user_info3() que se llama en el SIGE para actualizar los datos, y la función sp_audit_corporates() que se ejecuta como Trigger de la tabla corporates al realizar alguna modificación.
+ [Desarrollo] Se agregó en la sección de Usuarios del SIGE, el tipo de bolsa: **Limitada extra** y 2 cajas de texto para que agreguen los limites diario y extra.
+ [Soporte] Los usuarios que tengan habilitada esta bolsa al cargar su campaña se verifica 2 veces su consumo, uno el limite "real" (Mensual) y el limite diario + el extra, se muestra una alerta por si ha superado alguna de las bolsas.

### Envío de mensajes por número corto con más de 160 caracteres
> *Diego Alvitres - 18/03/2021*, [Trello](https://trello.com/c/jgvhqOEr/118-soporte-mowa-sms)
+ [Soporte] Se agregó un nuevo campo para activar la opción de envío de más de 160 caracteres a los usuarios.
+ [Sistemas] Se agregó en la creación de campañas por excel una validación para detectar si tiene mensajes con más de 160 caracteres, de ser así se muestra una opción de Salida: **Corto con más de 160 caracteres** y posteriormente la cantidad total de mensajes a enviar.
+ [Comercial] Los mensajes que superen los 160 caracteres se "dividen" en mensajes de 153 caracteres (Es lo que factura el proveedor), posteriormente se muestra el **Total de mensajes** a enviar en la ventana de confirmación.

### Características actuales de Mowa...
 - ...

### Descripción
> *Cambios Productos - 18/03/2021*, Se crea la primera versión (beta) del documento: Changelog, donde se mostrará los cambios realizados en los productos de Mowa Consultora de una manera rápida y no formal, con el fin de que el equipo completo pueda enterarse de los últimos cambios importantes que se realicen y los conozcan y si alguno es de su interés puede abundar aun mas en él. El documento de Changelog por ahora es una versión beta que se quiere implementar (quizás no funcione), si alguien del equipo quiere mostrar algún cambio que realice en los productos (ya sean Comerciales , Sistemas , Soporte .. en general) puede utilizar el documento de cambios sin ningún inconveniente.

