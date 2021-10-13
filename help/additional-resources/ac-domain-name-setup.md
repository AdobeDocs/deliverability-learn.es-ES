---
title: Configuración del nombre de dominio
description: Obtenga información sobre cómo delegar un subdominio a Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4d52d197-d20e-450c-bfcf-e4541c474be4
source-git-commit: 82f7254a9027f79d2af59aece81f032105c192d5
workflow-type: tm+mt
source-wordcount: '2061'
ht-degree: 2%

---

# Configuración del nombre de dominio

Este documento describe los requisitos técnicos y comerciales para la configuración y delegación de nombres de dominio. Deberá seleccionar un subdominio de envío de correo electrónico y, opcionalmente, un subdominio orientado externamente a los componentes web de host (páginas de aterrizaje, página de exclusión) para la plataforma de Adobe que utiliza.

>[!NOTE]
>
>También puede configurar nuevos subdominios mediante el Panel de control de Campaign (disponible como beta). Obtenga más información en [esta sección](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read).

## Subdominios

Con el Adobe, el marketing digital puede convertirse realmente en el motor contextual que impulsa el programa de marketing de participación del cliente de su marca.  El correo electrónico sigue siendo la base de los programas de marketing digital. Sin embargo, llegar a la bandeja de entrada se ha vuelto más difícil que nunca.

La creación de un subdominio para campañas de correo electrónico permite a las marcas aislar tipos de tráfico variables (marketing vs. empresa, por ejemplo) en grupos de IP específicos y con dominios específicos, lo que acelera el [proceso de calentamiento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md) y mejora la capacidad de envío en general. Si comparte un dominio y este se bloquea o añade a la lista de bloqueados, podría afectar a la entrega de correo empresarial. Sin embargo, los problemas de reputación o los bloques de un dominio específico de las comunicaciones de marketing por correo electrónico solo afectarán a ese flujo de correo electrónico.  El uso del dominio principal como remitente o dirección &quot;De&quot; para varios flujos de correo también podría dañar la autenticación por correo electrónico, lo que bloquearía los mensajes o colocarlos en la carpeta de correo no deseado.

### Delegación

La delegación de nombres de dominio es un método que permite al propietario de un nombre de dominio (técnicamente: una zona DNS) para delegar una subdivisión de ella (técnicamente: una zona DNS bajo ella, que puede llamarse subzona) a otra entidad. Básicamente, si un cliente está manejando la zona &quot;example.com&quot;, puede delegar la subzona &quot;marketing.example.com&quot; a Adobe Campaign.

Esto significa que los servidores DNS de Adobe Campaign tendrán plena autoridad solo en esa zona y no en el dominio de nivel superior. Los servidores DNS de Adobe Campaign proporcionarán respuestas autoritativas a consultas sobre nombres de dominio en esa zona, como &quot;t.marketing.example.com&quot; pero no &quot;www.example.com&quot;.

Al delegar un subdominio para utilizarlo con Adobe Campaign, los clientes pueden confiar en el Adobe para mantener la infraestructura DNS necesaria para cumplir los requisitos de envío estándar del sector para sus dominios de envío de marketing por correo electrónico, a la vez que mantienen y controlan el DNS para sus dominios de correo electrónico internos.  La delegación de subdominios permite:

Clientes para mantener su imagen de marca utilizando un alias DNS con sus nombres de dominio
Adobe de implementar de forma autónoma todas las prácticas recomendadas técnicas para optimizar completamente la capacidad de envío durante el envío de correo electrónico

## Opciones de configuración de DNS

Para proporcionar un servicio administrado basado en la nube, Adobe recomienda encarecidamente a los clientes que utilicen la delegación de subdominios al implementar Adobe Campaign.  Sin embargo, el Adobe ofrece a los clientes una opción alternativa (configuración de CNAME) para configurar DNS.

| Opción | Descripción | Responsabilidades de Adobe | Responsabilidades del cliente |
|--- |------- |--- |--- |
| Delegación de subdominios en Adobe Campaign | El cliente delega un subdominio (email.example.com) al Adobe. En esta situación, Adobe puede ofrecer Campaign como servicio administrado controlando y manteniendo todos los aspectos de DNS necesarios para la entrega, el procesamiento y el seguimiento de campañas de correo electrónico. | Administración completa del subdominio y de todos los registros DNS necesarios para Adobe Campaign. | Delegación adecuada del subdominio en el Adobe |
| Uso de CNAME | El cliente crea un subdominio y utiliza CNAME para señalar registros específicos de Adobe.  Con esta configuración, tanto Adobe como el cliente comparten la responsabilidad de mantener DNS. | Administración de los registros DNS necesarios para Adobe Campaign. | Creación y control del subdominio y creación/administración de los registros CNAME necesarios para Adobe Campaign. |

## Registros DNS necesarios

| Tipo de registro | Finalidad | Ejemplos de registro/contenido |
|--- |--- |--- |
| MX | Especificar servidores de correo para los mensajes entrantes | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Marco de políticas del remitente | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | Correo identificado de DomainKeys | <i>cliente._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY HERE&quot; |
| Registros de hosts (A) | Páginas espejo, alojamiento de imágenes y vínculos de seguimiento, todos los dominios de envío | m.email.example.com EN A 123.111.100.99</br>t.email.example.com EN A 123.111.100.98</br>email.example.com EN A 123.111.100.97 |
| DNS inverso (PTR) | Asigna las direcciones IP del cliente a un nombre de host con marca de cliente | 18.101.100.192.in-addr.arpa puntero de nombre de dominio r18.email.example.com |
| CNAME | Proporciona un alias a otro nombre de dominio | t1.email.example.com es un alias para t1.email.example.campaign.adobe.com |


Se recomienda la autenticación, los informes y la conformidad de mensajes basados en dominio (DMARC) para autenticar remitentes de correo y garantizar que los sistemas de correo electrónico de destino confíen en los mensajes enviados desde su dominio.

Ejemplo de registro TXT de DMARC:

```
_dmarc.email.example.com

“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” 
```

Puede implementar DMARC manualmente o ponerse en contacto con Adobe para ayudarle a configurar DMARC para su marca.

## Requisitos de configuración

### Delegación de subdominios

Esto requiere que el cliente cree un subdominio en sus servidores DNS y defina los servidores de nombres para este subdominio para que sean los que mantiene Adobe.  Por ejemplo, un cliente cuyo nombre de dominio principal sea &quot;example.com&quot; y que desee delegar la administración de &quot;marketing.example.com&quot; en el Adobe para sus envíos de correo electrónico tendrá que materializar esta delegación para agregar los siguientes registros de tipo a su DNS:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

La delegación de un nombre de dominio implica que este dominio se dedicará a enviar correos electrónicos a través de la plataforma Adobe Campaign y, por lo tanto, no se puede utilizar para otros medios (por ejemplo, enviar correos electrónicos desde otra infraestructura de correo electrónico).

Durante el proceso de configuración, el Adobe se asegurará de que el dominio esté adjunto a la infraestructura de correo electrónico entrante del Adobe para administrar y procesar los correos electrónicos de rebote que regresan a estos dominios (configuración de registro DNS de tipo MX).

### Uso de CNAME

Si el cliente decide utilizar CNAME en lugar de delegar un subdominio al Adobe, durante la fase de configuración, el Adobe proporcionará los registros que se van a colocar en los servidores DNS del cliente y configurará los valores correspondientes en los servidores DNS de Adobe Campaign.

## Requisitos generales de implementación

Al implementar una nueva solución de marketing empresarial, existen requisitos para componentes externos.  Entre ellas se incluyen el alojamiento de páginas de aterrizaje y formularios web, la configuración de vínculos y páginas web de las que se realizará un seguimiento, la visualización de páginas espejo y la configuración de una página de exclusión.

Aunque estos requisitos se administran a través de componentes alojados tanto por Adobe como por el cliente, incluyen direcciones URL que pueden ver los destinatarios de los correos electrónicos.  Para evitar tener direcciones URL que indiquen la solución técnica subyacente o el proveedor de alojamiento, se pueden configurar subdominios para que esto sea transparente para los destinatarios de los correos electrónicos.  Por ejemplo, al consultar una dirección URL como http://www.customer.com/, el dominio sería &quot;www.customer.com&quot;.  El subdominio de esto sería &quot;www&quot;.

### Requisitos de subdominio

Determine los subdominios que se utilizarán para las direcciones URL con marca (páginas espejo y URL de seguimiento) de la aplicación Adobe Campaign.  Decida también qué serán &quot;De dirección&quot;, &quot;De nombre&quot; y &quot;De dirección de respuesta&quot; para cada subdominio en los envíos de correo electrónico.

Complete la tabla siguiente; la primera línea es solo un ejemplo.

| Subdomain | De la dirección | De nombre | Dirección de respuesta |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Customer | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* El propósito del campo &quot;Dirección de respuesta&quot; es cuando desea que el destinatario responda a una dirección diferente a la de &quot;Dirección de origen&quot;.  Aunque no es un campo obligatorio, Adobe recomienda encarecidamente que la &quot;Dirección de respuesta&quot; sea válida y esté vinculada a un buzón supervisado.  El cliente debe alojar este buzón.  Podría ser un buzón de soporte, por ejemplo, customercare@customer.com, donde los correos electrónicos se leen y responden.
>* Si el cliente no elige ninguna &quot;Dirección de respuesta&quot;, entonces la dirección predeterminada siempre es `<tenant>-<type>-<env>@<subdomain>`.
>* Cuando la &quot;Dirección de respuesta&quot; está configurada de esta manera, las respuestas se envían a un buzón sin supervisión.
>* Al enviar correos electrónicos desde Adobe Campaign, el buzón &quot;De dirección&quot; no se supervisa y los usuarios de marketing no pueden acceder a este buzón. Adobe Campaign tampoco ofrece la capacidad de responder automáticamente o reenviar automáticamente correos electrónicos recibidos en este buzón.
>* La dirección de origen/remitente de la campaña y la dirección de error no pueden ser &quot;abuso&quot; o &quot;administrador de correo&quot;.


## Delegación de subdominios

Los subdominios elegidos para utilizarse en la plataforma de Adobe Campaign deben delegarse creando cuatro registros de servidor de nombres (NS).  Esto permite delegar correctamente el subdominio en el Adobe.  A continuación se muestra un ejemplo de una delegación de subdominios y las instrucciones DNS correspondientes.  Sustituya &quot;emails.customer.com&quot; por el subdominio que desee delegar.  Tenga en cuenta que el subdominio debe ser único y que otra parte no puede utilizarlo ya (por ejemplo, un ESP o MSP existente).

| Subdominio delegado | Instrucciones DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.  </br> `<subdomain>` NS b.ns.campaign.adobe.com.  </br> `<subdomain>` NS c.ns.campaign.adobe.com.  </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Seguimiento, páginas espejo, recursos

Una vez que los subdominios de envío de correo electrónico se delegan correctamente a Adobe Campaign, el equipo de TechOps de Adobe creará dos o más dominios de nivel inferior para administrar el seguimiento y las páginas espejo de forma independiente.

| Tipo | Domain |
|--- |--- |
| Páginas espejo | m.`<subdomain>` |
| Seguimiento | t.`<subdomain>` |
| Recursos | res.`<subdomain>` |

## Implementación en la nube (opcional)

Esto solo se aplica si Adobe Campaign Classic está totalmente alojado en la nube por Adobe.  Esta es una configuración opcional.

Los estudios, formularios web y páginas de aterrizaje que se vayan a desarrollar se gestionan mediante Adobe Campaign totalmente alojado en la nube.  Si es necesario, se puede delegar un subdominio adicional a Adobe (por ejemplo, web.customer.com) para utilizarlo en cualquier componente web de la herramienta.  Tenga en cuenta que el subdominio debe ser único y no puede ser utilizado por otra parte (por ejemplo, un ESP o MSP existente).

| Subdominio delegado | Instrucciones DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>De forma predeterminada, los componentes web de la herramienta utilizarán el subdominio inicial delegado para utilizarlo en el correo electrónico.

## Implementación de mensajería en la nube (opcional)

En el caso de que la instancia de marketing de Adobe Campaign Classic esté alojada On-Premise en el cliente, el cliente deberá realizar configuraciones técnicas adicionales.

Todos los estudios, formularios web y páginas de aterrizaje que se vayan a desarrollar se administran a través de la instancia de marketing de Adobe Campaign, donde existen los registros de destinatario.

Se requiere una configuración DNS CNAME adicional para implementar componentes web externos alojados en la instancia de marketing de Adobe Campaign.  Esto permitirá que los componentes web (por ejemplo, web.customer.com) sean de acceso público a Internet y estén marcados con el dominio del cliente.

Los cortafuegos también deberán configurarse para permitir el acceso a la instancia de marketing de Adobe Campaign que aloja estos componentes web (en el puerto 80 o 443).

**Práctica recomendada en Recommendations:**

El subdominio para alojar componentes web será visible para los clientes, por lo que asegúrese de que sea adecuado y sencillo de recordar, ya que es posible que tenga que escribirse manualmente, por ejemplo: https://web.customer.com.
Si algún formulario debe alojarse en páginas seguras (HTTPS), se necesitará configuración técnica adicional, tal como se describe a continuación.

| Subdominio delegado | Instrucciones DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME  `<internal customer server>` |

## Servicios procesados

A continuación de estas delegaciones, la infraestructura establecida por Adobe garantiza que se realicen los siguientes servicios para cada dominio de envío delegado o autorizado por CNAME:

* Creación de las bandejas de entrada de postmaster@ y abuse@
* Configuración de los bucles de comentarios para el dominio delegado
* Si se solicita, el Adobe también configurará un registro DMARC según se especifique. Su consultor de capacidad de envío puede ayudarle a diseñar una política DMARC a largo plazo y a planificar los dominios de envío.
Los parámetros establecidos por Adobe sólo son válidos desde el momento en que la delegación se completó y luego se verificó por Adobe, y siguen funcionando.  Todas las ofertas de Adobe Campaign Cloud incluyen delegación de nombres de dominio como estándar.

## Condiciones de facturación e implementación

* Según el contrato inicial y el tipo de paquete seleccionado, podrán incluirse otras delegaciones además de las incluidas como norma aparte de esta delegación inicial.
* Además de estas delegaciones incluidas, se facturarán delegaciones adicionales,
* El método de facturación para estas delegaciones adicionales se aplica a un costo mensual adicional, como se especifica en el contrato inicial.

Estas delegaciones serán aceptadas siempre que el CLIENTE elija los nombres de dominio asociados que se dedican a las entregas a través de la herramienta Adobe Campaign y que los requisitos previos de delegación detallados en el documento correspondiente se apliquen correctamente.

## Interrupción de los servicios

En cualquier momento, el CLIENTE podrá hacer una petición por escrito para no beneficiarse de los servicios de delegación y asumir las configuraciones DNS necesarias.

Si esto sucede, el Adobe proporcionará al CLIENTE una estimación que detalle el número de días de servicio necesarios para volver al modo de delegación que no es de dominio.

El Adobe se liberará de cualquier responsabilidad por la participación de la tasa de entrega mencionada si el cliente no cumple los compromisos establecidos anteriormente.

La terminación del servicio de Marketing Cloud llevará automáticamente al final de las delegaciones de dominio y el mantenimiento de DNS para esos dominios por Adobe.

## Supervisión de subdominios mediante el Panel de control de Campaign

Una vez configurados los subdominios para su instancia, puede monitorizarlos con el Panel de control de Campaign .

Esto le permite ver todos los subdominios delegados en Adobe Campaign, así como solicitar la renovación de sus certificados SSL.

Para obtener más información, consulte la [documentación dedicada](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>[Los ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es) paneles de control están disponibles para los clientes que solo utilizan Adobe Managed Services.
