---
title: Infraestructura
description: 'Descubra qué se necesita para construir correctamente una infraestructura de correo electrónico. '
feature: Proceso de transición
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
translation-type: tm+mt
source-git-commit: 65eb1fd03e6a6617ef24661c371f850d1f8e6054
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 2%

---

# Infraestructura

La capacidad de entrega correcta depende de una base sólida. La infraestructura de correo electrónico es un elemento central. Una infraestructura de correo electrónico construida correctamente incluye varios componentes, a saber, dominios y direcciones IP. Estos componentes son como la maquinaria detrás de los correos electrónicos que envía y suelen ser el ancla de la reputación de envío. Los consultores de capacidad de envío se aseguran de que estos elementos estén correctamente configurados durante la implementación, pero debido al elemento de reputación, es importante que tenga esta comprensión básica.

## Configuración y estrategia del dominio {#domain-setup-and-strategy}

Los tiempos han cambiado y algunos ISP (como Gmail y Yahoo) ahora incorporan la reputación de dominio como punto adicional a la hora de adjuntar la reputación de correo electrónico a un remitente. Su reputación de dominio se basa en su dominio de envío en lugar de en su dirección IP. Esto significa que la marca tiene prioridad cuando se trata de decisiones de filtrado de ISP.

Parte del proceso de incorporación de nuevos remitentes en plataformas de Adobe incluye la configuración de sus dominios de envío y la garantía de que su infraestructura se ha establecido correctamente. Debe trabajar con un experto en los dominios que planea utilizar a largo plazo. A continuación se ofrecen algunas sugerencias que moldean una buena estrategia de dominio:

* Sea lo más claro y reflexivo posible de la marca con el dominio que elija para que los usuarios no identifiquen incorrectamente el correo como correo no deseado. Algunos ejemplos son newsletter.foo.com, recibos.foo.com, etc.
* No debe utilizar su dominio principal o corporativo, ya que podría afectar a la entrega de correo de su organización a los ISP.
* Considere la posibilidad de utilizar un subdominio del dominio principal para legitimar el dominio de envío.
* Separe los subdominios para las categorías de mensajes transaccionales y de marketing. Esto ayudará a que el flujo de tráfico de correo electrónico sea más fiable, ya que los ISP buscarán este método de envío, que es una práctica recomendada conocida y es muy recomendable.

## Estrategia IP {#ip-strategy}

Es importante formar una estrategia de IP bien estructurada para ayudar a establecer una reputación positiva. El número de IP y la configuración varía según el modelo de negocio y los objetivos de marketing. Trabaje con un experto para desarrollar una estrategia clara para empezar bien. Tenga en cuenta lo siguiente:

* **Demasiados problemas de reputación de déclencheur de** IPscan, ya que es una táctica común de remitentes de spam para  **raquetas de nieve**, una táctica utilizada por los remitentes de correo no deseado, donde el tráfico se distribuye en muchas direcciones IP para maximizar el envío de correo no deseado. Aunque no sea un remitente del correo no deseado, puede parecer que lo sea si utiliza demasiadas IP, especialmente si estas no han tenido tráfico anterior.
* **Muy pocos** IPscan causan problemas de rendimiento y problemas de reputación de déclencheur. El rendimiento varía según el ISP. La cantidad y la rapidez con que un ISP está dispuesto a aceptar se basan generalmente en su infraestructura y en el envío de umbrales de reputación.
* La separación del tráfico para los tipos de mensajería es clave. Es importante, como mínimo, separar el correo de marketing y el transaccional en grupos de IP independientes.
* En función de su estrategia de correo, también puede ser aconsejable separar diferentes productos o flujos de marketing en diferentes grupos de IP si su reputación es drásticamente diferente. Algunos especialistas en marketing también segmentan por región. La separación de la IP para el tráfico con una reputación menor no solucionará el problema de reputación, pero evitará problemas con los envíos de correo electrónico de &quot;buena&quot; reputación. Después de todo, no quiere sacrificar a su buena audiencia por una más riesgosa.

## Bucles de comentarios {#feedback-loops}

Entre bastidores, las plataformas de Adobe están procesando datos sobre devoluciones, quejas, cancelaciones de suscripción, etc. La configuración de estos bucles de comentarios es un aspecto importante de la capacidad de envío. Las quejas pueden dañar una reputación, por lo que debe enviar por correo electrónico a las direcciones que registran las quejas de la audiencia de destino. Es importante tener en cuenta que Gmail no devuelve estos datos. Los encabezados de cancelación de suscripción de lista y el filtrado de la participación son especialmente importantes para los suscriptores de Gmail, que ahora comprenden la mayoría de las bases de datos de suscriptores.

## Autenticación {#authentication}

La autenticación es el proceso que los ISP utilizan para validar la identidad de un remitente. Los dos protocolos de autenticación más comunes son [!DNL Sender Policy Framework] (SPF) y [!DNL DomainKeys Identified Mail] (DKIM). El usuario final no puede ver estos datos, pero ayuda a los ISP a filtrar el correo electrónico de los remitentes verificados. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) está ganando popularidad, aunque sus políticas aún no están incorporadas por todos los ISP en sus sistemas de reputación.

### SPF

[!DNL Sender Policy Framework] (SPF) es un método de autenticación que permite al propietario de un dominio especificar qué servidores de correo utilizan para enviar correo desde ese dominio.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) es un método de autenticación que se utiliza para detectar direcciones de remitente falsificadas (comúnmente denominadas suplantación de identidad). Si DKIM está habilitado, permite al receptor confirmar si el remitente está autorizado a enviar correo desde ese dominio.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) es un método de autenticación que permite a los propietarios de dominios proteger su dominio de usos no autorizados. DMARC utiliza SPF, DKIM o ambos para permitir que el propietario de un dominio controle qué sucede con el correo que falla en la autenticación: entregado, puesto en cuarentena o rechazado.

## Recursos específicos de los productos

**Campaign**

* Obtenga información sobre cómo delegar completamente un subdominio a Adobe Campaign Classic o Standard en [esta sección](/help/additional-resources/ac-domain-name-setup.md).
* [Panel de control de Campaign: Delegación de subdominios completa (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) :  *Obtenga información sobre cómo delegar completamente un subdominio a Adobe Campaign Classic.*
* [Panel de control de Campaign: Delegación de subdominios completa (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) :  *Obtenga información sobre cómo delegar completamente un subdominio a Adobe Campaign Standard.*
* Obtenga más información sobre la implementación de un bucle de comentarios para una instancia de Campaign Classic en [esta sección](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Recursos adicionales

* Obtenga más información sobre los métodos de autenticación SPF, DKIM y DMARC en [esta sección](/help/additional-resources/authentication.md).
* Obtenga más información sobre cómo aumentar la reputación de su correo electrónico con el calentamiento de IP en [esta sección](/help/additional-resources/increase-reputation-with-ip-warming.md).
