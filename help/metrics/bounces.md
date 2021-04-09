---
title: Devoluciones
description: Obtenga información acerca de los distintos tipos de devoluciones.
feature: Métricas
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 6338eb67-3efd-476e-8b26-97bbb6a1d35f
translation-type: ht
source-git-commit: e433002423bd1ab2f4a89425198c16160dae0719
workflow-type: ht
source-wordcount: '478'
ht-degree: 100%

---

# Devoluciones

Las devoluciones son el resultado de un intento de entrega y un error en el que el ISP proporciona avisos de error de devolución. El procesamiento de la manipulación de devoluciones es una parte esencial del estado de la lista. Una vez que un correo electrónico determinado ha rebotado varias veces, este proceso indica su supresión. La cantidad y el tipo de devoluciones necesarios para activar la supresión varían de un sistema a otro. Este proceso evita que los sistemas continúen enviando a direcciones de correo electrónico no válidas. Las devoluciones son uno de los datos clave que los ISP utilizan para determinar la reputación de la IP. Es muy importante vigilar esta métrica. &quot;Entregado&quot; frente a &quot;devuelto&quot; es probablemente la forma más común de medir el envío de mensajes de marketing: cuanto mayor sea el porcentaje de entrega, mejor.

Analizaremos dos tipos de devoluciones.

## Devoluciones graves

Las devoluciones graves de mensajes son errores permanentes que se generan después de que un ISP determine que el intento de enviar una campaña de correo a una dirección de un suscriptor no se puede entregar. En Adobe Campaign, las devoluciones graves de mensajes clasificados como no aptos para entrega se añaden a la cuarentena, lo que significa que no se volverán a enviar. Hay algunos casos en los que se ignoran los mensajes devueltos no válidos si se desconoce la causa del error.
Estos son algunos ejemplos comunes de devoluciones graves:

* La dirección no existe
* La cuenta está deshabilitada
* La sintaxis es incorrecta
* El dominio es incorrecto

## Devoluciones leves

Las devoluciones leves de mensajes son errores temporales que los ISP generan cuando tienen dificultades para el envío de correos. Los errores de devoluciones leves se reintentarán varias veces (con variación según el uso de la configuración de envío personalizada o predeterminada) para lograr una entrega correcta. Las direcciones de mensajes devueltos no entregados que reboten de forma continua no se añadirán a la cuarentena hasta que se haya intentado el número máximo de reintentos (que varía en función de la configuración). Algunas causas comunes de las devoluciones leves son las siguientes:

* El buzón está lleno
* El servidor de recepción de correo electrónico está inactivo
* Hay problemas con la reputación del remitente

![Tipos de devolución](../assets/bounce-types.png)

>[!NOTE]
>
>Las devoluciones son un indicador clave de un problema de reputación, ya que pueden resaltar una fuente de datos incorrecta (mensajes devueltos no válidos) o un problema de reputación con un ISP (mensajes devueltos no entregados).
>
>Las devoluciones leves suelen producirse como parte del envío de correo electrónico y se debe permitir que se resuelvan durante el procesamiento de reintentos antes de caracterizarse como un problema de entrega real. Si la tasa de salida hacia otro sitio de los mensajes devueltos no entregados es superior al 30 % en el caso de un solo ISP y no se resuelve en un plazo de 24 horas, es aconsejable hablar con el consultor del equipo de entrega de Adobe Campaign.

## Recursos específicos de los productos

**Adobe Campaign Classic**

* [Tipos y motivos de errores de entrega](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=es#delivery-failure-types-and-reasons)
* [Gestión de correos rechazados](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=es#bounce-mail-management)
* [Informe de rechazos y correos no entregables](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/global-reports.html?lang=es#non-deliverables-and-bounces)

**Adobe Campaign Standard**

* [Tipos y motivos de errores de entrega](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=es#delivery-failure-types-and-reasons)
* [Clasificación del correo rechazado](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=es#bounce-mail-qualification)
* [Informe de resumen de rechazos](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=es#reporting)
