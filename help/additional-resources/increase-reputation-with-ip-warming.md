---
title: Aumente su reputación de correo electrónico con el calentamiento de IP
description: Aprenda por qué es importante mejorar su reputación de correo electrónico con el calentamiento de la IP y cómo proceder para lograr una entrega óptima.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: b553a13e-2055-4abc-b784-fd52792380d0
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '1600'
ht-degree: 3%

---

# Aumente su reputación de correo electrónico con el calentamiento de IP

<!--Increase your email reputation with IP warming

## IP Warming overview

In the Adobe Deliverability Consulting and Deliverability Operations teams, we have a vested interest in helping new Campaign customers be as successful as possible as they embark on the route of an IP warming process. If you’ve never been a part of such a project, you may have a lot of questions about it. Let’s get down to the details!-->

## Primeros pasos

El Adobe requiere que los clientes compartan su configuración para ayudar al equipo de entrega de Adobe a comprender su programa único. Las preguntas que formulamos están diseñadas para ayudar al equipo de entrega de Adobe a tener una idea de su reputación de envío y su volumen de correo electrónico. Sin una comprensión concreta de su modelo de negocio, objetivos de marketing por correo electrónico y métricas de reputación, no podremos personalizar la estrategia y habrá riesgo de problemas de envío.

Al principio, se le asignarán sus propias direcciones IP dedicadas (Protocolo de Internet). En el contexto del envío de correos electrónicos, una dirección IP es la ruta que se utiliza para enviar mensajes de correo electrónico a sus clientes. Las direcciones IP y los dominios se utilizan para identificar a los remitentes de una red a los ISP receptores. Adobe asigna el número adecuado de direcciones IP dedicadas para enviar correos electrónicos, en función de su volumen de envío, programas de correo electrónico, prácticas de segmentación de datos y su contrato.

**Temas relacionados:**
* [Cómo realizar la transición sin problemas al cambiar de plataforma de correo electrónico](../../help/transition-process/switching-email-platforms.md)
* [Estrategia de IP](../../help/transition-process/infrastructure.md#ip-strategy)
* [Consideraciones específicas del ISP durante el calentamiento de la IP](../../help/transition-process/isp-specific-considerations-during-ip-warming.md)

## Calentamiento de IP: ¿Por qué se hace? {#why-ip-warming}

Los proveedores de servicios de Internet (ISP) o los proveedores de buzones de correo (MBP) toman precauciones cuando detectan una IP y un dominio de envío desconocidos. Es un procedimiento estándar asociado a cualquier nueva dirección IP de envío, independientemente del tipo de remitente. Los ISP/MBP someten la IP y el dominio de envío a un alto escrutinio para determinar si los correos electrónicos que se envían desde esta IP y el dominio son spam o no.  Es un procedimiento estándar asociado a cualquier nueva dirección IP de envío, independientemente del tipo de remitente.

Los ISP examinan cuidadosamente el volumen de envío, la frecuencia de envío, las quejas y las tasas de devolución generadas a partir de estos envíos de correo. Todos estos se comprueban de cerca porque son indicadores de reputación del remitente, ya sea bueno o malo.

Naturalmente, este proceso de examinar estos puntos de datos lleva tiempo y no se puede lograr en uno o dos días. La reputación se construye con el tiempo. Este proceso es como dejar entrar a un extraño en tu casa. ¿Tendrías reservas acerca de que alguien que nunca has conocido entre en tu casa?

Es muy probable que la respuesta sea sí. Desea analizar a esta persona y sus motivos. ¿Quieren hacer daño? ¿Son una amenaza? Los ISP hacen lo mismo para proteger su red del tráfico malintencionado o no deseado. Las métricas de reputación positivas le ayudan a avanzar mucho en un proceso de calentamiento de IP exitoso. Por eso destacamos la importancia de empezar por enviar volúmenes de correo electrónico pequeños y empezar a enviarlos primero a sus clientes altamente comprometidos. Para obtener más información, consulte [Criterios de segmentación al enviar tráfico nuevo](/help/transition-process/targeting-criteria.md).

Enviar grandes cantidades de correo electrónico desde una IP o IP completamente nuevas fuera de la puerta es una mala práctica y probablemente le causará algunas dificultades de envío. Es importante tener en cuenta que, aunque empiece a enviar volúmenes pequeños y los aumente gradualmente según se recomienda, sigue siendo necesario seguir las prácticas recomendadas de correo electrónico.

![](../../help/assets/ip-warming-volume-trend.png)

## Permiso para enviar por correo (inclusión explícita)

Este es el componente más importante para administrar y aumentar una lista de correo electrónico de suscriptores. A medida que las leyes contra el correo no deseado crecen y se vuelven más completas a nivel internacional, el objetivo principal de un experto en marketing debería ser garantizar que haya recibido un consentimiento explícito (o expreso) de cada suscriptor en su lista. Es decir, cada suscriptor ha aceptado activamente recibir correos electrónicos de su marca. Esto difiere del consentimiento implícito en el que una persona se añade a una lista de correo electrónico después de realizar una acción que no incluía la suscripción explícita a un programa de correo electrónico.

Más información sobre [Política de uso aceptable del Adobe](https://www.adobe.com/legal/terms/aup.html).

## Métricas de reputación: ¿qué buscan los ISP?

Los ISP utilizan tecnología sofisticada para tomar decisiones informadas sobre si enviar o no correos electrónicos que reciben de redes externas. A veces tienen algoritmos complicados y propietarios en su conjunto de herramientas para ayudarles en este proceso.

Algunos de los puntos de datos examinados son los siguientes:

* Visitas de trampa de spam
* Visitas de lista de bloqueados
* Rechazos de correo electrónico
* Participación del suscriptor

Los ISP requieren configuraciones técnicas específicas que se alineen con sus políticas y prácticas recomendadas. El Adobe de configura las direcciones IP y los subdominios delegados para identificarle como un remitente responsable y de confianza. Esto se llama [autenticación por correo electrónico](/help/transition-process/infrastructure.md#authentication). La autenticación ayuda a los receptores a validar si un remitente tiene los derechos para enviar desde esa IP o dominio.

La autenticación permite a los ISP validar que la empresa que envía desde un dominio o IP tiene derecho a hacerlo. Básicamente, se hace para probar tu identidad y para asegurarte de que no pretendas ser otra persona, y de que otra persona no pretenda ser tú.

En el momento del Adobe, configuraremos SPF y DKIM de forma predeterminada y DMARC si se solicita. Los ISP hacen referencia a SPF y DKIM como las formas principales de autenticación. Muchos ISP también incorporan DMARC (Autenticación de mensajes, creación de informes y conformidad basados en dominio) en sus decisiones de filtrado. Los correos electrónicos no autenticados no están necesariamente bloqueados, pero se filtran de forma adicional.

## Calentamiento de IP: Qué esperar

### Correo restringido o bloqueado

Los remitentes de spam envían desde direcciones IP nuevas todo el tiempo: pasarán por un grupo de direcciones IP hasta que se cierren y repitan el proceso en otro grupo de direcciones IP. Como resultado, los ISP tratan cuidadosamente el tráfico que se envía desde nuevas IP. Bloquean el envío de una gran cantidad de correos electrónicos por parte de direcciones IP porque sospechan que se trata de una actividad maliciosa ejecutada por remitentes de correo no deseado.

Por lo tanto, no es inusual recibir mensajes de aplazamiento o limitación cuando comienza a enviar correos desde sus nuevas IP. Tras algunos reintentos, el mensaje suele aceptarse y entregarse.

Lograr un flujo normal de tráfico a través de los ISP que aplazan los nuevos remitentes puede tardar unos días. Aún así, no deje de enviar correos electrónicos: siga centrándose en enviar únicamente a los suscriptores de correo electrónico más comprometidos.

En casos excepcionales, el ISP bloquea el nuevo remitente. El Adobe es monitorizar su cuenta y, si se sospecha un bloqueo de este tipo, se pondrá en contacto con el ISP para intentar solucionar la situación de la mejor manera posible.

Recuerde que la coherencia es clave aquí. Los patrones de volumen de envío irregulares y los patrones de correo poco frecuentes causarán algunos desafíos de entrega a lo largo del camino.

### Quejas

[Reclamaciones](/help/metrics/complaints.md) se producen cuando un suscriptor etiqueta un correo electrónico como correo no deseado a través de su programa de correo electrónico. Esto envía un aviso al ISP sobre la actividad de la queja. Si hay suficientes quejas que llegan al ISP, ese ISP actuará para proteger a sus clientes; posiblemente bloquee muchos correos electrónicos para evitar que lleguen a los suscriptores o dirija una parte de los correos electrónicos a la carpeta masiva, en lugar de a las bandejas de entrada de los suscriptores. Si el problema de envío está causado por quejas, es importante determinar por qué los destinatarios se quejan.

Los suscriptores se quejan por varios motivos. A veces, un suscriptor no quiere recibir más correos electrónicos tuyos, quizá porque cree que está recibiendo demasiados mensajes sobre el mismo tema, porque no esperaba el mensaje o porque no recuerda haberse registrado para recibir sus correos electrónicos.

### Validez de los datos

Las devoluciones duras se producen cuando se envía a una dirección que no se puede enviar  en un ISP. No se puede realizar un envío a una dirección por muchas razones, como un error al escribir la dirección o un correo a una dirección que estaba activa anteriormente, pero que se cerró o terminó después de un período de inactividad.

Si se encuentra con un número sustancial de mensajes devueltos no válidos, es importante comprender por qué. Revise cómo se recopilaron las direcciones y confirme que se concedió el permiso. A veces, las personas cierran su cuenta de correo electrónico y no notifican a quienes tienen esa dirección en su lista de marketing.

### Participación

Los ISP buscan un volumen coherente y una buena calidad de los datos. Aumentará el tráfico de forma lenta y constante en las próximas cuatro a ocho semanas. A veces, las ampliaciones requieren más o menos tiempo en función del volumen y los objetivos, pero por lo general, es un proceso de al menos 8 semanas.

El tráfico de correo electrónico debe implementarse en una progresión lenta y constante, aumentando cada semana hasta que se haya enviado toda la lista. Además, cada segmento seguirá la programación hasta su finalización. Comience primero con los suscriptores más recientes y termine con los menos comprometidos al final. Tenga en cuenta también que algunos ISP pueden requerir un enfoque más personalizado debido a la forma en que administran el nuevo tráfico.

Más información sobre [participación](/help/engagement.md).

## Mantén el curso

Es posible que se sienta tentado a acelerar el proceso de calentamiento de la IP enviando más volumen del recomendado, descuidando pasar tiempo identificando a los suscriptores más comprometidos y no enviándoles correos a estos suscriptores primero en un esfuerzo por crear una reputación positiva. ¡Por favor resiste este impulso! No le ayudará en el largo plazo.

Es muy importante comenzar a enviar por correo a los usuarios altamente comprometidos (¡con correo electrónico!) suscriptores solo para las fases iniciales del calentamiento de la IP. Estos clientes son los más valiosos y su tendencia a abrir los correos electrónicos ayudará a empezar a mostrar a los ISP que es un experto en marketing que envía correos electrónicos interesantes y solicitados. También muestra los ISP que está siguiendo las reglas y las prácticas recomendadas.

## Conclusión

Recuerde: el calentamiento de la IP es una maratón, no un sprint.  Aunque el proceso puede parecer engorroso y requerir mucho tiempo, sería más trabajo intentar reparar una reputación dañada por no seguir las prácticas recomendadas probadas y verdaderas de correo electrónico.

Cuanto mejores sean las prácticas de envío y mayores sean las puntuaciones de reputación con los ISP, más probabilidades habrá de que se envíen los correos electrónicos. El calentamiento y el aumento de la IP, junto con las siguientes prácticas recomendadas para el diseño del correo, ayudarán a optimizar la entrega de la bandeja de entrada.

Nuestro equipo de entrega global es su socio en este proceso y le ayudará durante esta fase de calentamiento de IP a posicionarlo para el éxito.
