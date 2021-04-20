---
title: Aumente su reputación de correo electrónico con el calentamiento de IP
description: Descubra por qué es importante mejorar su reputación de correo electrónico con el calentamiento de IP y cómo proceder para una capacidad de envío óptima.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 2%

---


# Aumente su reputación de correo electrónico con el calentamiento de IP

<!--Increase your email reputation with IP warming

## IP Warming overview

In the Adobe Deliverability Consulting and Deliverability Operations teams, we have a vested interest in helping new Campaign customers be as successful as possible as they embark on the route of an IP warming process. If you’ve never been a part of such a project, you may have a lot of questions about it. Let’s get down to the details!-->

## Primeros pasos

Adobe requiere que los clientes compartan su configuración para ayudar al equipo de entrega de Adobe a comprender su programa único. Las preguntas que formulamos están diseñadas para ayudar al equipo de entrega de Adobe a comprender su reputación de envío y su volumen de correo electrónico. Sin una comprensión concreta del modelo empresarial, los objetivos de marketing por correo electrónico y las métricas de reputación, no podremos personalizar la estrategia y existe el riesgo de problemas de envío.

Al principio, se le asignarán sus propias direcciones IP dedicadas (Protocolo de Internet). En el contexto del envío de correo electrónico, una dirección IP es la ruta que se utiliza para enviar mensajes de correo electrónico a sus clientes. Las direcciones IP y los dominios se utilizan para identificar los remitentes de una red a los ISP receptores. Adobe asigna la cantidad adecuada de direcciones IP dedicadas para enviar correos electrónicos, según el volumen de envío, los programas de correo electrónico, las prácticas de segmentación de datos y el contrato.

**Temas relacionados:**
* [Cómo realizar la transición sin problemas al cambiar de plataforma de correo electrónico](../../help/transition-process/switching-email-platforms.md)
* [Estrategia IP](../../help/transition-process/infrastructure.md#ip-strategy)
* [Consideraciones específicas del ISP durante el calentamiento de la IP](../../help/transition-process/isp-specific-considerations-during-ip-warming.md)

## Calentamiento de IP: ¿Por qué se hace? {#why-ip-warming}

Los proveedores de servicios de Internet (ISP) o los proveedores de buzones de correo (MBP) toman precauciones cuando detectan una IP y un dominio de envío desconocidos. Es un procedimiento estándar asociado con cualquier IP de envío nueva, independientemente del tipo de remitente. Los ISP/MBP ponen la IP y el dominio de envío bajo un alto escrutinio para determinar si los correos electrónicos que se envían desde esta IP y este dominio son o no correo no deseado.  Es un procedimiento estándar asociado con cualquier IP de envío nueva, independientemente del tipo de remitente.

Los ISP examinan cuidadosamente el volumen de envío, la frecuencia de envío, las quejas y las tasas de devoluciones generadas a partir de estos correos. Todas estas se comprueban de cerca porque son indicadores de reputación del remitente, ya sea bueno o malo.

Naturalmente, este proceso de examen de estos puntos de datos lleva tiempo y no se puede lograr en uno o dos días. La reputación se construye con el tiempo. Este proceso es como dejar a un extraño en tu casa. ¿Tendrías reservas acerca de tener a alguien que nunca has conocido entrar a tu casa?

Es muy probable que la respuesta sea sí. Desea analizar a esta persona y sus motivos. ¿Significan daño? ¿Son una amenaza? Los ISP hacen lo mismo para proteger su red del tráfico malintencionado o no deseado. Las métricas de reputación positiva le ayudan a avanzar mucho en un proceso exitoso de calentamiento de IP. Es por eso que recalcamos la importancia de empezar por enviar volúmenes de correo electrónico pequeños y empezar a enviar primero a sus clientes altamente comprometidos. Para obtener más información sobre esto, consulte [Criterios de objetivo al enviar nuevo tráfico](/help/transition-process/targeting-criteria.md).

El envío de grandes cantidades de correo electrónico desde una nueva dirección IP o direcciones IP directamente desde la puerta de enlace es una práctica deficiente y probablemente le cause algunas dificultades en la entrega. Es importante tener en cuenta que incluso si comienza a enviar volúmenes pequeños y los aumenta gradualmente según lo recomendado, sigue siendo necesario seguir las prácticas recomendadas relacionadas con el correo electrónico.

![](../../help/assets/ip-warming-volume-trend.png)

## Permiso para enviar correos (Inclusión explícita)

Este es el componente más importante de la gestión y el crecimiento de una lista de correo electrónico de suscriptor. A medida que las leyes contra el correo no deseado crecen y se vuelven más completas a nivel internacional, debería ser un enfoque principal de los especialistas en marketing garantizar que hayan recibido el consentimiento explícito (o explícito) de cada suscriptor en su lista. Es decir, cada suscriptor ha aceptado recibir correos electrónicos de su marca. Esto difiere del consentimiento implícito en el que se añade una persona a una lista de correo electrónico después de realizar una acción que no se estaba registrando explícitamente para un programa de correo electrónico.

Obtenga más información sobre la [Política de uso aceptable del Adobe](https://www.adobe.com/legal/terms/aup.html).

## Métricas de reputación: ¿Qué buscan los ISP?

Los ISP utilizan tecnología sofisticada para tomar decisiones educadas acerca de si ofrecen o no correos electrónicos que reciben de redes externas. A veces tienen algoritmos complicados y patentados en su conjunto de herramientas para ayudarles en este proceso.

Algunos de los puntos de datos examinados son:

* Visitas de trampa de correo no deseado
* visitas de lista de bloqueados
* Rechazos de correo electrónico
* Participación del suscriptor

Los ISP requieren configuraciones técnicas específicas que se ajusten a sus políticas y prácticas recomendadas. Adobe configura sus IP y subdominios delegados para identificarle como remitente responsable y de confianza. Esto se denomina [autenticación de correo electrónico](/help/transition-process/infrastructure.md#authentication). La autenticación ayuda a los receptores a validar si un remitente tiene los derechos para enviar desde esa IP o dominio.

La autenticación permite a los ISP validar que la empresa que envía desde un dominio o IP tiene el derecho de hacerlo. Básicamente se hace para probar tu identidad y para asegurarse de que no estás fingiendo ser alguien más, y que alguien más no pretende ser tú.

En el Adobe, configuraremos SPF y DKIM de forma predeterminada y configuraremos DMARC por solicitud. Los ISP hacen referencia a SPF y DKIM como las formas principales de autenticación. Muchos ISP también incorporan DMARC (Autenticación de mensajes, informes y conformidad basados en dominio) en sus decisiones de filtrado. Los correos electrónicos no autenticados no están necesariamente bloqueados, pero pasan por filtros adicionales.

## Calentamiento de IP: Expectativas

### Correo restringido o bloqueado

Los remitentes de spam envían desde nuevas direcciones IP todo el tiempo: se queman a través de un grupo de direcciones IP hasta que se cierran y repiten el proceso en otro grupo de direcciones IP. Como resultado, los ISP tratan el tráfico que se envía desde nuevas IP con cuidado. Bloquean las IP para que envíen una gran cantidad de correo electrónico porque sospechan que se trata de una actividad maliciosa que están ejecutando los remitentes de correo no deseado.

Por lo tanto, no es inusual recibir mensajes de demora o restringidos cuando comienza a enviar por correo desde sus nuevas IP. Después de varios reintentos, el mensaje se suele aceptar y enviar.

Lograr un flujo normal de tráfico a través de los ISP que retrasan los nuevos remitentes puede tardar unos días. Aun así, no deje de enviar correo: céntrese en enviar solo a los suscriptores de correo electrónico más comprometidos.

En casos excepcionales, el ISP bloquea el nuevo remitente. El Adobe está monitorizando su cuenta, y si se sospecha un bloqueo de este tipo, contactará al ISP para tratar de ayudar a remediar la situación de la mejor manera posible.

Recuerde que la coherencia es clave aquí. Los patrones de volumen de envío irregulares y los patrones de envío poco frecuentes causarán algunos desafíos de envío a lo largo del camino.

### Reclamaciones

[](/help/metrics/complaints.md) Se queja cuando un suscriptor etiqueta un correo electrónico como correo no deseado a través de su programa de correo electrónico. Esto envía un aviso al ISP sobre la actividad de queja. Si hay suficientes de estas quejas que llegan al ISP, ese ISP actuará para proteger a sus clientes, posiblemente impida que muchos correos electrónicos lleguen a los suscriptores o dirija una parte de los correos electrónicos a la carpeta masiva en lugar de a las bandejas de entrada de los suscriptores. Si el problema de entrega se debe a quejas, es importante determinar por qué los destinatarios se quejan.

Los suscriptores se quejan por varias razones. A veces un suscriptor no quiere recibir más correo electrónico de usted, tal vez porque cree que está recibiendo demasiados mensajes sobre el mismo tema, no esperaba el mensaje o no recuerda registrarse para recibir sus correos electrónicos.

### Validez de los datos

Las devoluciones duras se producen cuando se envía a una dirección que no se puede enviar  en un ISP. Una dirección puede no entregarse por muchas razones, como un error al escribir la dirección o al enviar a una dirección que antes estaba activa pero que se cerró o terminó después de un período de inactividad.

Si se produce un número considerable de rechazos graves, es importante comprender por qué. Revise cómo se recopilaron las direcciones y confirme que se ha concedido el permiso. A veces, las personas cierran su cuenta de correo electrónico y no notifican a quienes tienen esa dirección en su lista de marketing.

### Participación

Los ISP buscan un volumen coherente y una buena calidad de datos. El tráfico aumentará lenta y constantemente durante las siguientes cuatro a ocho semanas. A veces, las ampliaciones requieren más o menos tiempo en función del volumen y los objetivos, pero normalmente se trata de un proceso de al menos 8 semanas.

El tráfico de correo electrónico debe implementarse en una progresión lenta y constante, aumentando cada semana hasta que se envíe la lista completa. Además, cada segmento seguirá la programación hasta su finalización. Comience con los suscriptores más recientes primero y termine con los suscriptores menos comprometidos en último lugar. Tenga en cuenta también que algunos ISP pueden requerir un enfoque más personalizado debido a cómo manejan el nuevo tráfico.

Obtenga más información sobre [participación](/help/engagement.md).

## Mantenga el curso

Es posible que esté tentado de acelerar el proceso de calentamiento de la IP enviando más volumen del recomendado, sin perder tiempo identificando a sus suscriptores más comprometidos y sin enviar un correo a estos suscriptores primero en un esfuerzo por crear una reputación positiva. ¡Por favor, resistan esta urgencia! A largo plazo no le ayudará.

Es muy importante que empiece a enviar por correo a los usuarios más comprometidos (con correo electrónico). suscriptores solo para las etapas iniciales del calentamiento de IP. Estos clientes son sus más valiosos y su propensión a abrir sus correos electrónicos ayudará a empezar a mostrar a los ISP que es un comerciante que envía correos que son interesantes y buscados. También muestra los ISP que siguen las reglas y las prácticas recomendadas.

## Conclusión. 

Recuerde: El calentamiento de IP es una maratón - ¡no una carrera!  Aunque el proceso puede parecer engorroso y lleva mucho tiempo, sería más trabajo intentar reparar una reputación dañada por no seguir las prácticas recomendadas probadas y verdaderas de correo electrónico.

Cuanto mejores sean las prácticas de envío y mayores sean las puntuaciones de reputación de los ISP, más probabilidades habrá de que se envíen sus correos electrónicos. El calentamiento y la ampliación de la IP, junto con las prácticas recomendadas para el diseño del correo, ayudarán a optimizar la entrega de la bandeja de entrada.

Nuestro equipo de entrega global es su socio en este proceso y le ayudará durante esta fase de calentamiento de IP a posicionarlo para el éxito.
