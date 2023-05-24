---
title: Infraestructura
description: Descubra qué se necesita para construir correctamente una infraestructura de correo electrónico.
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# Infraestructura

La capacidad de envío exitosa depende de una base sólida. La infraestructura de correo electrónico es un elemento central. Una infraestructura de correo electrónico construida correctamente incluye varios componentes, a saber, dominios y direcciones IP. Estos componentes son como la maquinaria detrás de los correos electrónicos que envía y a menudo son el ancla del envío de reputación. Los consultores en capacidad de envío garantizan que estos elementos se configuren correctamente durante la implementación, pero debido al elemento de reputación, es importante que tenga esta comprensión básica.

## Configuración y estrategia del dominio {#domain-setup-and-strategy}

Los tiempos han cambiado, y algunos ISP (como Gmail y Yahoo) ahora incorporan la reputación de dominio como un punto adicional a la hora de adjuntar la reputación de correo electrónico a un remitente. Su reputación de dominio se basa en el dominio de envío, en lugar de en la dirección IP. Esto significa que su marca tiene prioridad cuando se trata de decisiones de filtrado de ISP.

Parte del proceso de incorporación de nuevos remitentes en las plataformas de Adobe incluye la configuración de los dominios de envío y garantizar que la infraestructura se establezca correctamente. Debe trabajar con un experto en los dominios que planea utilizar a largo plazo. A continuación se ofrecen algunas sugerencias para definir una buena estrategia de dominio:

* Sea lo más claro y reflexivo posible de la marca con el dominio que elija, de modo que los usuarios no identifiquen incorrectamente el correo como correo no deseado. Algunos ejemplos son newsletter.foo.com, receipts.foo.com, etc.
* No debe utilizar su dominio principal o corporativo, ya que podría afectar al envío de correo de su organización a los ISP.
* Considere la posibilidad de utilizar un subdominio del dominio principal para legitimar el dominio de envío.
* Separe los subdominios para las categorías de mensajes transaccionales y de marketing. Esto ayudará a que el tráfico del correo electrónico fluya de forma más fiable, ya que los ISP buscan este método de envío, que es una práctica recomendada conocida y muy recomendable.

## Estrategia de IP {#ip-strategy}

Es importante formar una estrategia de PI bien estructurada que ayude a establecer una reputación positiva. El número de direcciones IP y la configuración varían según el modelo empresarial y los objetivos de marketing. Trabaje con un experto para desarrollar una estrategia clara para comenzar bien. Tenga en cuenta lo siguiente:

* **Demasiadas direcciones IP** puede déclencheur problemas de reputación, ya que es una táctica común de los remitentes de spam **raqueta de nieve**, que es una táctica utilizada por los remitentes de correo no deseado en la que el tráfico se propaga a través de muchas direcciones IP para maximizar el envío de correo no deseado. Aunque no envíe correo no deseado, podría parecer que lo es si utiliza demasiadas direcciones IP, especialmente si esas direcciones IP no han tenido tráfico anterior.
* **Demasiadas pocas direcciones IP** puede causar problemas de rendimiento y potencialmente problemas de reputación de déclencheur. El rendimiento varía según el ISP. La cantidad y la rapidez con que un ISP está dispuesto a aceptar suelen basarse en su infraestructura y en el envío de umbrales de reputación.
* La separación del tráfico para los tipos de mensajería es clave. Es importante, como mínimo, separar el marketing y el correo transaccional en grupos de IP independientes.
* En función de su estrategia de correo electrónico, también puede ser aconsejable separar diferentes productos o flujos de marketing en diferentes grupos de IP si su reputación es drásticamente diferente. Algunos especialistas en marketing también segmentan por región. La separación de la IP para el tráfico con una reputación más baja no corregirá el problema de reputación, pero evitará problemas con las entregas de correo electrónico de &quot;buena&quot; reputación. Después de todo, no quiere sacrificar su buena audiencia por una más riesgosa.

## Bucles de comentarios {#feedback-loops}

Entre bastidores, las plataformas de Adobe procesan datos sobre devoluciones, quejas, cancelaciones de suscripción y mucho más. La configuración de estos bucles de comentarios es un aspecto importante para la capacidad de envío. Las quejas pueden dañar una reputación, por lo que debe enviar direcciones de correo electrónico que registren quejas de la audiencia de destino. Es importante tener en cuenta que Gmail no devuelve estos datos. Los encabezados de cancelación de suscripción a listas y el filtrado de participación son especialmente importantes para los suscriptores de Gmail, que ahora comprenden la mayoría de las bases de datos de suscriptores.

## Autenticación {#authentication}

La autenticación es el proceso que utilizan los ISP para validar la identidad de un remitente. Los dos protocolos de autenticación más comunes son [!DNL Sender Policy Framework] (SPF) y [!DNL DomainKeys Identified Mail] (DKIM). No son visibles para el usuario final, pero ayudan a los ISP a filtrar el correo electrónico de los remitentes verificados. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) está ganando popularidad, aunque sus políticas aún no han sido incorporadas por todos los ISP en sus sistemas de reputación.

### SPF

[!DNL Sender Policy Framework] (SPF) es un método de autenticación que permite al propietario de un dominio especificar qué servidores de correo utilizan para enviar correo desde ese dominio.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) es un método de autenticación que se utiliza para detectar direcciones de remitente falsificadas (comúnmente denominadas suplantación de identidad). Si DKIM está habilitado, permite al destinatario confirmar si el remitente está autorizado para enviar correo desde ese dominio.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) es un método de autenticación que permite a los propietarios de dominio proteger su dominio de un uso no autorizado. DMARC utiliza SPF, DKIM o ambos para permitir que un propietario de dominio controle qué sucede con el correo que falla en la autenticación: enviado, en cuarentena o rechazado.

## Recursos específicos de los productos

**Campaign**

* Obtenga información sobre cómo delegar completamente un subdominio a Adobe Campaign Classic o Standard en [esta sección](/help/additional-resources/ac-domain-name-setup.md).
* [Panel de control de Campaign: delegación de subdominios completa (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Obtenga información sobre cómo delegar completamente un subdominio a Adobe Campaign Classic.*
* [Panel de control de Campaign: delegación de subdominios completa (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Obtenga información sobre cómo delegar completamente un subdominio a Adobe Campaign Standard.*
* Obtenga más información sobre la implementación de un bucle de comentarios para una instancia de Campaign Classic en [esta sección](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Recursos adicionales

* Obtenga más información sobre los métodos de autenticación SPF, DKIM y DMARC en [esta sección](/help/additional-resources/authentication.md).
* Obtenga más información sobre cómo aumentar su reputación de correo electrónico con el calentamiento de IP en [esta sección](/help/additional-resources/increase-reputation-with-ip-warming.md).
