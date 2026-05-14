---
title: Solución de problemas de envío
description: Obtenga información sobre cómo identificar y abordar los problemas de envío.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4cc85124-e7e4-4cd5-99a9-23d2d8cf08fe
TQID: https://experienceleague.adobe.com/EDzTRrQeFbp-5GFRMxRDqwoMx37ykI2auNz6ZH9EmF8
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5f60233-d5ea-4453-a799-0ad258b4d399id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 688
ht-degree: 87%

---

# Solución de problemas de envío {#troubleshooting}

A continuación se describen algunas prácticas recomendadas que pueden ayudar a identificar y abordar los problemas de envío.

## Identificación de un problema de envío {#identify-deliverability-issue}

Para identificar un posible problema, los elementos enumerados en [esa página](/help/ongoing-monitoring.md) pueden llamar su atención.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## Suponer las causas potenciales {#potential-causes}

Hágase las siguientes preguntas para identificar las posibles causas del problema de envío:

* ¿Hubo un cambio reciente en la segmentación de listas?
* ¿He adquirido fuentes de datos nuevas?
* ¿He enviado accidentalmente un archivo de cuarentena?
* ¿Podría deberse el problema al contenido de mi mensaje?
* ¿Envío correos con la frecuencia suficiente para mantener IP calientes?
* ¿Estoy segmentando mis correos por actividad/participación o enviando archivos completos?
* ¿Cuál es el segmento “seguro” de mi archivo en términos de actualización?
* ¿Tengo estrategias de reactivación y reconfirmación para segmentos que no están definidos como seguros?

## Abordar el problema {#address-issue}

### Quejas

Las [quejas](/help/metrics/complaints.md) las definen los suscriptores que informan el correo electrónico como correo no deseado pulsando el botón correspondiente de su bandeja de entrada.

Si su problema de envío fue causado por quejas:
* Debe intentar determinar por qué los destinatarios se quejan.
* También puede considerar mover el enlace de cancelación de suscripción a la parte superior de su correo electrónico. Esto anima a los suscriptores a cancelar la suscripción en lugar de quejarse con el botón de correo no deseado.

Los remitentes pueden obtener una gran cantidad de información de sus quejas del [bucle de retroalimentación](/help/transition-process/infrastructure.md#feedback-loops).
* Es importante agrupar los datos y buscar patrones en elementos como la fuente de inclusión, cuánto tiempo se ha suscrito la dirección o incluso ciertas características demográficas del comportamiento.
* Las quejas pueden identificar a menudo una fuente de datos o un segmento riesgosos dentro del archivo. Se define el riesgo como el más propenso a quejarse, lo que puede dañar la reputación y, a su vez, las tasas de bandeja de entrada.

Las quejas también provienen de suscriptores que ya no quieren recibir correos electrónicos:
* Esto a menudo puede deberse a mensajes excesivos, a la percepción de los suscriptores sobre el mensaje, que no esperaban el mensaje o que no recordaban la inclusión.
* También es importante realizar una auditoría para asegurarse de que todos los puntos de recopilación sean claros y de que no hay casillas premarcadas en los puntos de adquisición.
* También debe enviar un correo electrónico de bienvenida cuando los suscriptores se incluyan para establecer el tono y explicar la frecuencia con la que pueden esperar recibir mensajes de correo electrónico de su parte.

### Validez de datos

**Las devoluciones duras** se producen cuando se envía a una **dirección que no se puede enviar** en un ISP. No se puede realizar un envío a una dirección por muchas razones, como:
* Dirección incorrecta. Esto se puede solucionar con un servicio de validación de datos en tiempo real o requiriendo una opción de inclusión confirmada antes de enviar correos electrónicos de marketing a esa dirección.
* Lista o fuente de datos incorrecta. Si procede de una nueva fuente, revise cómo se recopilaron las direcciones y asegúrese de que haya permisos.
* Enviar un mensaje a una dirección que en un momento estaba activa, pero que se cerró o terminó después de un período de inactividad.

### Participación

Además de las quejas y la validez de los datos, los proveedores de servicios de Internet se concentran más que nunca en la **participación positiva** para tomar decisiones de envío. Están buscando ver si sus suscriptores están abriendo sus correos electrónicos o eliminándolos sin leerlos. Dado que no comparten estos datos con los remitentes, debemos utilizar la información que tenemos disponible y traducir aperturas/clics/transacciones como participación.

Como parte del mantenimiento continuo de la reputación, es importante comprender cómo los suscriptores comprometidos están en su lista y desarrollar una **jerarquía de riesgo de actualización** para los suscriptores de cada archivo. La actualización se define como la última fecha de apertura/clic/transacción o de registro. Este intervalo de tiempo puede variar en función de la vertical. Para ello, haga lo siguiente:

1. Determine segmentos activos (“seguros”) para cada vertical. Generalmente son suscriptores que han estado activos entre los últimos 3 a 6 meses.
1. Reduzca la frecuencia a inactivos.
1. Cree una serie de [reparticipación](/help/additional-resources/re-engagement.md) para los inactivos de riesgo moderado. Generalmente, esto demora de 6 a 9 meses sin participación.
1. Desarrolle una campaña de reconfirmación para los inactivos de mayor riesgo. Generalmente son suscriptores que no han participado con un correo electrónico en un periodo de 9 a 12 meses.
1. Finalmente, establezca una regla desplegable y elimine los suscriptores que no hayan abierto sus correos electrónicos en “x” meses. Normalmente recomendamos más de 12 meses, pero esto puede variar en función del ciclo de compra y venta.
