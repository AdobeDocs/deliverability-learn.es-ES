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
source-wordcount: '2043'
ht-degree: 2%

---

# Configuración del nombre de dominio

Este documento describe los requisitos comerciales y técnicos para la configuración y delegación de nombres de dominio. Debe seleccionar un subdominio de envío de correo electrónico y, opcionalmente, un subdominio externo para alojar componentes web (páginas de aterrizaje, página de exclusión) para la plataforma de Adobe que esté utilizando.

>[!NOTE]
>
>También puede configurar nuevos subdominios mediante el Panel de control de Campaign (disponible como beta). Obtenga más información en [esta sección](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=es#must-read).

## Subdominios

Con el Adobe, el marketing digital puede convertirse en el motor contextual que potencia el programa de marketing de participación del cliente de su marca.  El correo electrónico sigue siendo la base de los programas de marketing digital. Sin embargo, llegar a la bandeja de entrada se ha vuelto más difícil que nunca.

La creación de un subdominio para campañas de correo electrónico permite a las marcas aislar distintos tipos de tráfico (de marketing o corporativo, por ejemplo) en grupos de IP específicos y con dominios específicos, lo que acelera el [proceso de calentamiento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md) y mejora la capacidad de envío en general. Si comparte un dominio y se bloquea o se agrega a la lista de bloqueados, podría afectar a su envío de correo corporativo. Sin embargo, los problemas de reputación o los bloqueos en un dominio específico de las comunicaciones de marketing por correo electrónico afectarán solo a ese flujo de correo electrónico.  El uso del dominio principal como remitente o de la dirección &quot;De&quot; para varios flujos de correo electrónico también podría interrumpir la autenticación del correo electrónico, lo que provocaría que los mensajes se bloquearan o se colocaran en la carpeta de correo no deseado.

### Delegación

La delegación de nombres de dominio es un método que permite al propietario de un nombre de dominio (técnicamente: una zona DNS) delegar una subdivisión del mismo (técnicamente: una zona DNS debajo de ella, que se puede llamar subzona) a otra entidad. Básicamente, si un cliente gestiona la zona &quot;example.com&quot;, puede delegar la subzona &quot;marketing.example.com&quot; a Adobe Campaign.

Esto significa que los servidores DNS de Adobe Campaign tendrán autoridad total solo en esa zona y no en el dominio de nivel superior. Los servidores DNS de Adobe Campaign proporcionarán respuestas autorizadas a consultas sobre nombres de dominio en esa zona, como &quot;t.marketing.example.com&quot;, pero no &quot;www.example.com&quot;.

Al delegar un subdominio para utilizarlo con Adobe Campaign, los clientes pueden confiar en el Adobe para mantener la infraestructura de DNS necesaria para satisfacer los requisitos de capacidad de entrega estándar del sector para sus dominios de envío de marketing por correo electrónico, a la vez que continúan manteniendo y controlando DNS para sus dominios de correo electrónico internos.  La delegación de subdominios permite:

Clientes que deseen conservar su imagen de marca utilizando un alias DNS con sus nombres de dominio
Adobe de implementar de forma autónoma todas las prácticas recomendadas técnicas para optimizar completamente la capacidad de envío durante el correo electrónico

## Opciones de configuración de DNS

Para proporcionar un servicio administrado basado en la nube, Adobe recomienda encarecidamente a los clientes que utilicen la delegación de subdominios al implementar Adobe Campaign.  Sin embargo, Adobe ofrece a los clientes una opción alternativa (configuración CNAME) para configurar DNS.

| Opción | Descripción | Responsabilidades del Adobe | Responsabilidades del cliente |
|--- |------- |--- |--- |
| Delegación de subdominios a Adobe Campaign | El cliente delega un subdominio (email.example.com) en el Adobe. En esta situación, Adobe puede ofrecer Campaign como servicio administrado controlando y manteniendo todos los aspectos de DNS necesarios para la entrega, el procesamiento y el seguimiento de campañas de correo electrónico. | Administración completa del subdominio y todos los registros DNS necesarios para Adobe Campaign. | Delegación adecuada del subdominio al Adobe |
| Uso de CNAME | El cliente crea un subdominio y utiliza CNAME para señalar registros específicos del Adobe.  Con esta configuración, tanto Adobe como el cliente comparten la responsabilidad de mantener DNS. | Administración de los registros DNS necesarios para Adobe Campaign. | Creación y control del subdominio y creación/administración de los registros CNAME necesarios para Adobe Campaign. |

## Registros DNS necesarios

| Tipo de registro | Objetivo | Ejemplos de registro/contenido |
|--- |--- |--- |
| MX | Especificar servidores de correo para mensajes entrantes | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Marco de política de remitentes | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | DomainKeys Identified Mail | <i>cliente._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY HERE&quot; |
| Hosts Registros (A) | Páginas espejo, alojamiento de imágenes y vínculos de seguimiento, todos los dominios de envío | m.email.example.com EN A 123.111.100.99</br>t.email.example.com EN A 123.111.100.98</br>email.example.com EN A 123.111.100.97 |
| DNS inverso (PTR) | Asigna las direcciones IP del cliente a un nombre de host de marca del cliente | Puntero de nombre de dominio 18.101.100.192.in-addr.arpa r18.email.example.com |
| CNAME | Proporciona un alias a otro nombre de dominio | t1.email.example.com es un alias para t1.email.example.campaign.adobe.com |


Se recomienda Autenticación de mensajes, creación de informes y conformidad basados en dominio (DMARC) para autenticar a los remitentes de correo y garantizar que los sistemas de correo electrónico de destino confíen en los mensajes enviados desde su dominio.

Ejemplo de registro TXT DMARC:

```
_dmarc.email.example.com

“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” 
```

Puede implementar DMARC manualmente o ponerse en contacto con el Adobe para que le ayude a configurar DMARC para su marca.

## Requisitos de configuración

### Delegación de subdominios

Esto requiere que el cliente cree un subdominio en sus servidores DNS y defina los servidores de nombres para este subdominio como los que mantiene el Adobe.  Por ejemplo, un cliente cuyo nombre de dominio principal sea &quot;example.com&quot; y que desee delegar la administración de &quot;marketing.example.com&quot; al Adobe para sus envíos de correo electrónico tendrá que materializar esta delegación para agregar los siguientes registros de tipo a su DNS:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

La delegación de un nombre de dominio implica que este dominio estará dedicado a enviar correo electrónico a través de la plataforma Adobe Campaign y, por lo tanto, no se puede utilizar para otros medios (por ejemplo, enviar correo electrónico desde otra infraestructura de correo electrónico).

Durante el proceso de configuración, el Adobe se asegurará de que el dominio esté adjunto a la infraestructura de correo electrónico entrante de Adobe para administrar y procesar los correos electrónicos de rebote que regresan a estos dominios (configuración de registro DNS de tipo MX).

### Uso de CNAME

Si el cliente decide utilizar CNAME en lugar de delegar un subdominio al Adobe, durante la fase de configuración, el Adobe proporcionará los registros que se colocarán en los servidores DNS del cliente y configurará los valores correspondientes en los servidores DNS de Adobe Campaign.

## Requisitos generales para la implementación

Al implementar una nueva solución de marketing empresarial, existen requisitos para los componentes externos.  Estos incluyen el alojamiento de páginas de destino y formularios web, la configuración de vínculos y páginas web para rastrear, la visualización de páginas espejo y la configuración de una página de exclusión.

Aunque estos requisitos se administran mediante componentes alojados por el Adobe y el cliente, incluyen direcciones URL que pueden ver los destinatarios de los correos electrónicos.  Para evitar tener direcciones URL que indiquen la solución técnica subyacente o el proveedor de alojamiento, se pueden configurar subdominios para que esto sea transparente para los destinatarios de los correos electrónicos.  Por ejemplo, cuando se mira una dirección URL como, http://www.customer.com/, el dominio sería &quot;www.customer.com&quot;.  El subdominio de esto sería &quot;www&quot;.

### Requisitos de subdominio

Determine los subdominios que se utilizarán para las direcciones URL con marca (páginas espejo y URL de seguimiento) desde la aplicación de Adobe Campaign.  Decida también cuál será la &quot;Dirección del remitente&quot;, &quot;Nombre del remitente&quot; y &quot;Dirección de respuesta&quot; para cada subdominio en los envíos de correo electrónico.

Complete la tabla siguiente, la primera línea es solo un ejemplo.

| Subdomain | Dirección de origen | De nombre | Dirección de respuesta |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Cliente | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* El propósito del campo &quot;Dirección de respuesta&quot; es cuando desea que el destinatario responda a una dirección diferente a la &quot;Dirección de origen&quot;.  Aunque no es un campo obligatorio, el Adobe recomienda encarecidamente que la &quot;Dirección de respuesta&quot; sea válida y esté vinculada a un buzón supervisado.  El cliente debe alojar este buzón.  Podría ser un buzón de asistencia, por ejemplo, customercare@customer.com, donde se leen y responden los correos electrónicos.
>* Si el cliente no elige ninguna &quot;Dirección de respuesta&quot;, la dirección predeterminada siempre es `<tenant>-<type>-<env>@<subdomain>`.
>* Cuando la &quot;Dirección de respuesta&quot; está configurada de esta manera, las respuestas se envían a un buzón no supervisado.
>* Al enviar correos electrónicos desde Adobe Campaign, el buzón &quot;Dirección de origen&quot; no se supervisa y los usuarios de marketing no pueden acceder a este buzón. Adobe Campaign tampoco ofrece la capacidad de responder automáticamente o reenviar automáticamente los correos electrónicos recibidos en este buzón.
>* La dirección de origen/remitente de la campaña y la dirección de error no pueden ser &quot;abuse&quot; ni &quot;postmaster&quot;.

## Delegación de subdominios

Los subdominios seleccionados para su uso en la plataforma Adobe Campaign deben delegarse creando cuatro registros de servidor de nombres (NS).  Esto permite delegar correctamente el subdominio al Adobe.  A continuación se muestra un ejemplo de una delegación de subdominios y las instrucciones DNS correspondientes.  Sustituya &quot;emails.customer.com&quot; por el subdominio que desee delegar.  Tenga en cuenta que el subdominio debe ser único y no puede estar siendo utilizado por otra parte (por ejemplo, un ESP o MSP existente).

| Subdominio delegado | Instrucciones DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com. </br> `<subdomain>` NS b.ns.campaign.adobe.com. </br> `<subdomain>` NS c.ns.campaign.adobe.com. </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Seguimiento, Páginas espejo, Recursos

Una vez que los subdominios de envío de correo electrónico se hayan delegado correctamente en Adobe Campaign, el equipo de TechOps de Adobe creará dos o más dominios de nivel inferior para administrar el seguimiento y las páginas espejo de forma independiente.

| Tipo | Dominio |
|--- |--- |
| Páginas espejo | m.`<subdomain>` |
| Seguimiento | t.`<subdomain>` |
| Recursos | res.`<subdomain>` |

## Implementación en la nube (opcional)

Esto solo se aplica si Adobe Campaign Classic está completamente alojado en la nube por Adobe.  Es una configuración opcional.

Cualquier encuesta, formulario web y página de aterrizaje que se vaya a desarrollar se administra mediante Adobe Campaign totalmente alojado en la nube.  Si es necesario, se puede delegar un subdominio adicional al Adobe (por ejemplo, web.customer.com) para utilizarlo con cualquier componente web dentro de la herramienta.  Tenga en cuenta que el subdominio debe ser único y no puede ser utilizado por otra parte (por ejemplo, un ESP o MSP existente).

| Subdominio delegado | Instrucciones DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>De forma predeterminada, cualquier componente web de la herramienta utilizará el subdominio inicial delegado para utilizarse en el correo electrónico.

## Implementación de mensajería en la nube (opcional)

En caso de que la instancia de marketing de Adobe Campaign Classic esté alojada en las instalaciones del cliente, este deberá realizar configuraciones técnicas adicionales.

Cualquier encuesta, formulario web y página de destino que se vaya a desarrollar se administra mediante la instancia de marketing de Adobe Campaign, donde existen los registros de destinatario.

Se requiere una configuración DNS CNAME adicional para implementar componentes web externos alojados en la instancia de marketing de Adobe Campaign.  Esto permitirá que los componentes web (por ejemplo, web.customer.com) sean accesibles públicamente a Internet y estén marcados con el dominio del cliente.

Los cortafuegos también deberán configurarse para permitir el acceso a la instancia de marketing de Adobe Campaign que aloja estos componentes web (en el puerto 80 o 443).

**Práctica recomendada en Recommendations:**

El subdominio para alojar componentes web será visible para los clientes, por lo que asegúrese de que tiene la marca correcta y es fácil de recordar, ya que es posible que deba escribirse manualmente, por ejemplo: https://web.customer.com.
Si es necesario alojar algún formulario en páginas seguras (HTTPS), se requerirá una configuración técnica adicional, como se describe a continuación.

| Subdominio delegado | Instrucciones DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Servicios representados

Después de estas delegaciones, la infraestructura puesta en marcha por el Adobe garantiza que se realicen los siguientes servicios para cada dominio de envío delegado o con alias CNAME:

* Creación de las bandejas de entrada postmaster@ y abuse@
* Configuración de bucles de comentarios para el dominio delegado
* Si se solicita, el Adobe también configurará un registro DMARC como se especifica. Su consultor de capacidad de entrega puede ayudarle a diseñar una política DMARC a largo plazo y a planificar sus dominios de envío.
Los parámetros definidos por el Adobe solo son válidos desde el momento en que se completó la delegación y luego se verificaron mediante el Adobe, y siguen funcionando.  Todas las ofertas de Adobe Campaign Cloud incluyen la delegación de nombres de dominio como estándar.

## Condiciones de facturación e implementación

* Según el contrato inicial y el tipo de paquete seleccionado, podrán incluirse otras delegaciones además de las incluidas como estándar más allá de esta delegación inicial.
* Más allá de estas delegaciones incluidas, se facturarán delegaciones adicionales.
* El método de facturación para estas delegaciones adicionales tiene un costo mensual adicional, como se especifica en el contrato inicial.

Estas delegaciones serán aceptadas siempre que el CLIENTE elija los nombres de dominio asociados dedicados a las entregas a través de la herramienta Adobe Campaign y que los requisitos previos de delegación detallados en el documento correspondiente se implementen correctamente.

## Interrupción de los servicios

En cualquier momento, el CLIENTE podrá realizar una petición por escrito para no seguir beneficiándose de los servicios de delegación y asumir por sí mismo las configuraciones de DNS necesarias.

Si esto sucede, Adobe proporcionará al CLIENTE una estimación que detalla el número de días de servicio necesarios para volver al modo de delegación de dominios no permitidos.

El Adobe quedará exento de cualquier responsabilidad por la contratación de la citada Tasa de Entrega si el Cliente no cumple con los compromisos establecidos anteriormente.

La terminación del servicio de Marketing Cloud llevará automáticamente al final de las delegaciones de dominio y al mantenimiento de DNS para esos dominios por Adobe.

## Supervisión de subdominios mediante el Panel de control de Campaign

Una vez configurados los subdominios para la instancia, puede monitorizarlos con el Panel de control de Campaign.

Esto le permite ver todos los subdominios que delegó en Adobe Campaign, así como solicitar la renovación de sus certificados SSL.

Para obtener más información, consulte la [documentación dedicada](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html?lang=es#subdomains-and-certificates).

>[!NOTE]
>
>El [Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es) está disponible para los clientes que solamente utilizan Adobe Managed Services.
