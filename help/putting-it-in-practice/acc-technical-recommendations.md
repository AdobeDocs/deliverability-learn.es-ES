---
title: Campaign Classic - Recomendaciones técnicas
description: Descubra las técnicas, configuraciones y herramientas que puede utilizar para mejorar la tasa de entrega con Adobe Campaign Classic.
feature: Ponerlo en práctica
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '1579'
ht-degree: 72%

---


# Campaign Classic: Recomendaciones técnicas {#technical-recommendations}

A continuación se enumeran varias técnicas, configuraciones y herramientas que puede utilizar para mejorar la tasa de entrega al utilizar Adobe Campaign Classic.

## Configuración {#configuration}

### DNS inverso {#reverse-dns}

Adobe Campaign comprueba si se ha proporcionado un DNS inverso para una dirección IP y que este señala correctamente a la dirección IP.

Un punto importante de la configuración de red es garantizar que se haya definido un DNS inverso correcto para cada una de las direcciones IP de los mensajes salientes. Esto significa que para una dirección IP determinada, existe un registro DNS inverso (registro PTR) con un bucle DNS (registro A) que corresponde con la dirección IP inicial.

La elección de dominio del DNS inverso influye al tratar con determinados ISP. AOL, en particular, solo acepta bucles de comentarios con una dirección del mismo dominio que el DNS inverso (consulte [Bucle de comentarios](#feedback-loop)).

>[!NOTE]
>
>Puede utilizar [esta herramienta externa](https://mxtoolbox.com/SuperTool.aspx) para verificar la configuración de un dominio.

### Reglas MX {#mx-rules}

Las reglas MX (Mail eXchanger) son las reglas que administran la comunicación entre un servidor emisor y un servidor receptor.

Más precisamente, se utilizan para controlar la velocidad a la que el MTA de Adobe Campaign (Agente de transferencia de mensajes) envía correos electrónicos a cada dominio de correo electrónico o ISP individual (por ejemplo, hotmail.com, comcast.net). Estas reglas generalmente se basan en los límites publicados por los ISP (por ejemplo, no incluyen más de 20 mensajes por cada conexión SMTP).

>[!NOTE]
>
>Para obtener más información sobre la administración MX en Adobe Campaign Classic, consulte [esta sección](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}

TLS (Transport Layer Security) es un protocolo de codificación que se puede utilizar para asegurar la conexión entre dos servidores de correo electrónico y proteger el contenido de un correo electrónico evitar que lo lean destinatarios no previstos.

### Dominio del remitente {#sender-domain}

Para definir el dominio utilizado para el comando HELO, edite el archivo de configuración de la instancia (conf/config-instance.xml) y defina un atributo &quot;localDomain&quot; como se indica a continuación:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

El dominio MAIL FROM es el dominio utilizado en los mensajes de rechazo técnico. Esta dirección se define en el asistente de implementación o a través de la opción NmsEmail_DefaultErrorAddr .

### Registro SPF {#dns-configuration}

Actualmente, un registro SPF se puede definir en un servidor DNS como un registro de tipo TXT (código 16) o un registro de tipo SPF (código 99). Un registro SPF toma la forma de una cadena de caracteres. Por ejemplo:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

define las dos direcciones IP, 12.34.56.78 y 12.34.56.79, como autorizadas para enviar correos electrónicos para el dominio. **~** todo significa que cualquier otra dirección debe interpretarse como un Fallo leve.

Recommendations para definir un registro SPF:

* Agregue **~all** (Fallo leve) o **-all** (Fallo) al final para rechazar todos los servidores que no sean los definidos. Sin esto, los servidores podrán falsificar este dominio (con una evaluación neutra).
* No agregue **ptr** (openspf.org recomienda no agregar esto, ya que es costoso y poco fiable).

>[!NOTE]
>
>Obtenga más información sobre SPF en [esta sección](/help/additional-resources/authentication.md#spf).

## Autenticación

>[!NOTE]
>
>Obtenga más información sobre las diferentes formas de autenticación por correo electrónico en [esta sección](/help/additional-resources/authentication.md).

### DKIM {#dkim-acc}

>[!NOTE]
>
>Para instalaciones hospedadas o híbridas, si ha actualizado al [servidor de correo mejorado](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages), este crea la firma de autenticación de correo electrónico DKIM para todos los mensajes con todos los dominios.

El uso de [DKIM](/help/additional-resources/authentication.md#dkim) con Adobe Campaign Classic requiere el siguiente requisito previo:

**Declaración** de opciones de Adobe Campaign: en Adobe Campaign, la clave privada DKIM se basa en un dominio y un selector DKIM. Actualmente no es posible crear múltiples claves privadas para el mismo dominio/subdominio con distintos selectores. No se puede definir qué dominio/subdominio de selector se debe utilizar para la autenticación en ninguna plataforma o en el correo electrónico. La plataforma selecciona una de las claves privadas, lo que significa que la autenticación tiene una mayor probabilidad de fallo.

* Si ha configurado DomainKeys para la instancia de Adobe Campaign, solo debe seleccionar **dkim** en las [Reglas de administración de dominios](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules). Si no es así, siga los mismos pasos de configuración (clave privada/pública) que para DomainKeys (que reemplazó a DKIM).
* No es necesario activar DomainKeys y DKIM para el mismo dominio, ya que DKIM es una versión mejorada de DomainKeys.
* Los siguientes dominios actualmente validan DKIM: AOL, Gmail.

## Bucle de comentarios {#feedback-loop-acc}

Un bucle de comentarios funciona declarando al nivel del ISP una dirección de correo electrónico determinada para un rango de direcciones IP utilizadas para enviar mensajes. El ISP se envía a este buzón de correo, de manera similar a lo que se hace para los mensajes rechazados, aquellos mensajes cuyos destinatarios notifiquen como correo no deseado. La plataforma debe configurarse para bloquear futuros entregas a los usuarios que envíen quejas. Es importante no volver a ponerse en contacto con ellos aunque no hayan utilizado el vínculo de exclusión adecuado. Estas quejas se basan en que un ISP agregará una dirección IP a su  de lista de bloqueados. En función del ISP, una tasa de quejas de alrededor del 1 % resulta en el bloqueo de una dirección IP.

Actualmente se está elaborando un estándar para definir el formato de los mensajes de bucle de comentarios: el [Abuse Feedback Reporting Format (ARF)](https://tools.ietf.org/html/rfc6650).

La implementación de un bucle de comentarios para una instancia requiere:

* Un buzón dedicado a la instancia, que puede ser el buzón de rechazos
* Direcciones IP de entrega dedicadas a la instancia

La implementación de un bucle de comentarios sencillo en Adobe Campaign utiliza la función de mensaje rechazado. El buzón de comentarios se utiliza como buzón de rechazos y se define una regla para detectar estos mensajes. Las direcciones de correo electrónico de los destinatarios que notificaron el mensaje como correo no deseado se añaden a la lista de cuarentena.

* Cree o modifique una regla de correo rechazado, **Feedback_loop**, en **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** con el motivo **Refused** y el tipo **Hard**.
* Si se ha definido un buzón especialmente para el bucle de comentarios, defina los parámetros para acceder a él mediante la creación de una nueva cuenta de correos rechazados externa en **[!UICONTROL Administration > Platform > External accounts]**.

El mecanismo está operativo inmediatamente para procesar las notificaciones de quejas. Para asegurarse de que esta regla funciona correctamente, puede desactivar temporalmente las cuentas para que no recopilen estos mensajes y, a continuación, comprobar manualmente el contenido del buzón del bucle de comentarios. En el servidor, ejecute los siguientes comandos:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Si está obligado a utilizar una dirección de bucle de comentarios única para varias instancias, debe:

* Reproducir los mensajes recibidos en tantos buzones como instancias haya,
* Hacer que cada instancia recopile un buzón de correo,
* Configure las instancias para que solo procesen los mensajes que les corresponda: la información de la instancia se incluye en el encabezado Message-ID de los mensajes que envía Adobe Campaign y, por lo tanto, también se ubica en los mensajes del bucle de comentarios. Sencillamente especifique el parámetro **checkInstanceName** en el archivo de configuración de instancia (de forma predeterminada, la instancia no se verifica y esto puede provocar que la dirección se ponga en cuarentena indebidamente):

   ```
   <serverConf>
     <inMail checkInstanceName="true"/>
   </serverConf>
   ```

El servicio de capacidad de entregas de Adobe Campaign administra la suscripción a los servicios de bucle de comentarios para los siguientes ISP: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## Cancelación de suscripción a una lista {#list-unsubscribe}

### Acerca de la cancelación de la suscripción a una lista {#about-list-unsubscribe}

La adición de un encabezado SMTP denominado **List-Unsubscribe** es obligatoria para garantizar una gestión óptima de la entrega.

Este encabezado puede utilizarse como alternativa al icono “Notificar como correo no deseado”. Se muestra como un vínculo para darse de baja en la interfaz de correo electrónico.

El uso de esta función ayuda a proteger la reputación, y los comentarios se ejecutan como una baja.

Para utilizar la cancelación de la suscripción a una lista, debe introducir una línea de comandos similar a la siguiente:

```
List-Unsubscribe: mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe
```

>[!CAUTION]
>
>El ejemplo anterior se basa en la tabla de destinatarios. Si la implementación de la base de datos se realiza desde otra tabla, asegúrese de volver a redactar la línea de comandos con la información correcta.

La siguiente línea de comandos se puede utilizar para crear una **List-Unsubscribe** dinámica:

```
List-Unsubscribe: mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%
```

Gmail, Outlook.com y Microsoft Outlook admiten este método y hay un botón de cancelación de suscripción disponible directamente en su interfaz. Esta técnica reduce las tasas de quejas.

Puede implementar **List-Unsubscribe** mediante:

* Añadiendo directamente [la línea de comandos en la plantilla de envío](#adding-a-command-line-in-a-delivery-template)
* [Crear una regla de tipología](#creating-a-typology-rule)

### Adición de una línea de comandos en una plantilla de entrega {#adding-a-command-line-in-a-delivery-template}

La línea de comandos debe añadirse en la sección adicional del encabezado SMTP del correo electrónico.

Esta adición se puede realizar en cada correo electrónico o en plantillas de entrega existentes. También puede crear una nueva plantilla de distribución que incluya esta función.

### Crear una regla de tipología {#creating-a-typology-rule}

La regla debe contener la secuencia que genera la línea de comandos y debe incluirse en el encabezado del correo electrónico.

>[!NOTE]
>
>Se recomienda crear una regla de tipología: la funcionalidad List-Unsubscribe se añade automáticamente en cada correo electrónico.

1. Cancelación de suscripción a una lista: &lt;mailto:unsubscribe@domain.com>

   Al hacer clic en el vínculo **unsubscribe** se abre el cliente de correo electrónico predeterminado del usuario. Esta regla de tipología debe añadirse en una tipología utilizada para crear correo electrónico.

1. Cancelación de suscripción a una lista: `<https://domain.com/unsubscribe.jsp>`

   Al hacer clic en el vínculo **unsubscribe**, se redirige al usuario a su formulario de cancelación de suscripción.

   Ejemplo:

   ![](../assets/s_tn_del_unsubscribe_param.png)

>[!NOTE]
>
>Aprenda a crear reglas de tipología en Adobe Campaign Classic en [esta sección](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

## Optimización del correo electrónico {#email-optimization}

### SMTP {#smtp}

SMTP (Protocolo simple de transferencia de correo) es un estándar de Internet para la transmisión de correos electrónicos.

Los errores de SMTP que no están marcados por una regla se enumeran en la carpeta **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]**. Estos mensajes de error se interpretan de forma predeterminada como errores leves no accesibles.

Los errores más comunes deben identificarse y se debe añadir una regla correspondiente en **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** si desea calificar correctamente los comentarios de los servidores SMTP. Sin esto, la plataforma realiza reintentos innecesarios (en caso de usuarios desconocidos) o pone incorrectamente en cuarentena a los destinatarios tras un número determinado de pruebas.

### IP dedicadas {#dedicated-ips}

Adobe proporciona una estrategia IP dedicada para cada cliente con una IP de aumento para crear una reputación y optimizar el rendimiento de la entrega.
