---
layout: post
title: Notificación automatica simple, usando un bot de Telegram
published: true
---

En algunas ocasiones queremos que nuestros sistemas nos informen de determinados eventos.   Aunque es común el envío de información a través de un correo electrónico, ésto no asegura la recepción de la alerta, ya que depende de una acción del usuario.

Nuestros teléfonos celulares están con nosotros casi 24x7x365, y en general tenemos cierta tendencia a revisar los mensajes en períodos de tiempo muy cortos.

> Obviamente, el celular debe tener acceso a internet para que el sistema de alertas funcione.

Aprovechando ésto, y la tecnología de **bots** de **Telegram**, podemos hacer un sistema de notificación automático, con la ventaja además de que Telegram está disponible para Android, iOS y Windows Phone, así que independientemente del teléfono que tenga el destinatario de los mensajes, podemos asegurarnos de que lo recibirá sin que tengamos que programar ninguna aplicación del lado del celular.

Existen multitud de tutoriales en internet para crear nuestos bots y programarlos.   Personalmente me parece muy sencillo y concreto el tutorial de [Xataca - cómo crear un bot de telegram](http://www.xatakamovil.com/aplicaciones/llegan-los-bots-a-telegram-como-crear-el-tuyo-propio).

Lo primero que tenemos que hacer es crear nuestro bot siguiendo el tutorial.   Esto nos regresará nuestro **token**.   Ya con el **token** vamos al navegador y escribimos:

```
https://api.telegram.org/bot***AQUI_VA_EL_TOKEN_OBTENIDO***/getUpdates
```

Si todo el proceso se ha realizado correctamente, nos debe regresar una pantalla como ésta:

```
{
ok: true,
result: [ ]
}
```

Ahora lo que tenemos que hacer es enviar un mensaje cualquiera desde telegram hacia nuestro bot.   Por default presenta el botón **Iniciar** cuando iniciamos la conversación con nuestro **@bot**, y luego presenta la opción **/start**.   Basta que pulsemos ésa para nuestro propósito.

> Es **obligatorio** mandar el mensaje desde el celular que recibirá las notificaciones, ya que **Telegram** le asigna un **id** único.

Ahora debemos volver a escribir la dirección en nuestro navegador que usamos anteriormente, y ahora nos devolverá algo parecido a ésto:

```
{  
   ok:true,
   result:[  
      {  
         update_id:########,
         message:{  
            message_id:###,
            from:{  
               id:12345678,
               first_name:"XXXXXX",
               last_name:"XXXXXXXX"
            },
            chat:{  
               id:12345678,
               first_name:"XXXXXX",
               last_name:"XXXXXXXX",
               type:"private"
            },
            date:1445369181,
            text:"/start"
         }
      },
  ]
}
```

Lo importante aquí es el **id** que nos regresa, ya que el **id** del **chat** es lo que necesitamos (junto con el **token**) para comenzar a mandar mensajes a nuestro celular.

Ahora, el ejemplo del lado del servidor lo haré en PHP, pero -como se mencionó anteriormente- abundan en internet buenos ejemplos para casi cualquier lenguaje.

En la parte del código PHP donde querramos que se envíe el mensaje, simplemente escribimos:

```
// Enviamos un mensaje a través de un bot de Telegram
file_get_contents('https://api.telegram.org/bot***AQUI_VA_EL_TOKEN_OBTENIDO***/sendMessage?text=Mensaje que quiera enviarse&chat_id=12345678');
```

Y eso es todo.   Aquí lo importante es que el **token** esté correctamente escrito y el **chat_id** sea el que obtuvimos en la dirección de internet.

> Naturalmente, éste método es muy primitivo e inseguro (sobre todo si compartimos el código) ya que el **token** y el **chat_id** nos permitirán enviar mensajes a un teléfono personal.   Pero la idea es tener un sistema de notificaciones simple y rápido, multiplataforma en los dispositivos receptores. 

Este uso es muy básico, la potencia de los **bots** de **Telegram** es muy robusta, la seguridad es alta, y próximamente intentaremos hacer un completo sistema de mensajes, con administración de usuarios.

Si algo no funciona bien, recuerden, usen la fuerza... un golpe al CPU tal vez arregle el problema.   Y luego van a google a buscar la respuesta.
