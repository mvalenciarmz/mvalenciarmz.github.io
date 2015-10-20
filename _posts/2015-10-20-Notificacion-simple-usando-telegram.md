---
layout: post
title: Notificación automatica simple, usando un bot de Telegram
published: true
---

En algunas ocasiones queremos que nuestros sistemas nos informen de determinados eventos.   Aunque es común el envío de información a través de un correo electrónico, ésto no asegura la recepción de la alerta, ya que depende de una acción del usuario.

Nuestros teléfonos celulares están con nosotros casi 24x7x365, y en general tenemos cierta tendencia a revisar los mensajes en períodos de tiempo muy cortos.

Aprovechando ésto, y la tecnología de **bots** de **Telegram**, podemos hacer un sistema de notificación automático, con la ventaja además de que Telegram está disponible para Android, iOS y Windows Phone, así que independientemente del teléfono que tenga el destinatario de los mensajes, podemos asegurarnos de que lo recibirá sin que tengamos que programar ninguna aplicación del lado del celular, ya que **Telegram** está disponible para todas ésas plataformas.

Existen multitud de tutoriales en internet para crear nuestos bots y programarlos.   Personalmente me parece muy sencillo y concreto el tutorial de [Xataca - cómo crear un bot de telegram](http://www.xatakamovil.com/aplicaciones/llegan-los-bots-a-telegram-como-crear-el-tuyo-propio).

Lo primero que tenemos que hacer es crear nuestro bot.   Esto nos regresara nuestro **token**.   Ya con el token vamos a un navegador y escribimos:

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





