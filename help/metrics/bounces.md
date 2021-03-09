---
title: Devoluciones
description: Obtenga información sobre los distintos tipos de devoluciones
feature: Métricas
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 3%

---


# Devoluciones

Las devoluciones son el resultado de un intento de envío y un error en el que el ISP proporciona avisos de error de devolución. El procesamiento de la manipulación de devoluciones es una parte fundamental de la higiene de la lista. Una vez que un correo electrónico determinado ha rebotado varias veces seguidas, este proceso lo marca para su supresión. El número y el tipo de devoluciones necesarios para activar la supresión varían de un sistema a otro. Este proceso evita que los sistemas continúen enviando direcciones de correo electrónico no válidas. Las devoluciones son uno de los datos clave que los ISP utilizan para determinar la reputación de la IP. Es muy importante vigilar esta métrica. &quot;Entregado&quot; frente a &quot;rechazado&quot; es probablemente la forma más común de medir el envío de mensajes de marketing: cuanto mayor sea el porcentaje entregado, mejor.

Excavaremos en dos tipos diferentes de devoluciones.

## Rechazos graves

Las devoluciones duras son errores permanentes generados después de que un ISP determine que un intento de envío a una dirección de suscriptor no se puede entregar. Dentro de Adobe Campaign, los rechazos graves clasificados como no entregables se añaden a la cuarentena, lo que significa que no se volverían a probar. Hay algunos casos en los que se ignoraría un rechazo grave si se desconoce la causa del error.
Estos son algunos ejemplos comunes de rechazos graves:

* La dirección no existe
* Cuenta deshabilitada
* Sintaxis incorrecta
* Dominio incorrecto

## Rechazos leves

Las devoluciones leves son errores temporales que los ISP generan cuando tienen dificultades para enviar correos. Los errores de software se reintentarán varias veces (con variación según el uso de la configuración de envío personalizada o predeterminada) para intentar una entrega correcta. Las direcciones que reboten de forma continua y suave no se añadirán a la cuarentena hasta que se haya intentado el número máximo de reintentos (que de nuevo varía en función de la configuración). Algunas causas comunes de devoluciones leves son las siguientes:

* Buzón de correo lleno
* Recibir servidor de correo electrónico inactivo
* Problemas de reputación del remitente

![tipos de devolución](../assets/bounce-types.png)

>[!NOTE]
>
>Las devoluciones son un indicador clave de un problema de reputación porque pueden resaltar una fuente de datos incorrecta (rechazo grave) o un problema de reputación con un ISP (rechazo suave).
>
>Los rechazos leves suelen producirse como parte del envío de correo electrónico y se debe permitir que se resuelvan durante el procesamiento de reintentos antes de caracterizarse como un problema de entrega real. Si la tasa de devoluciones leves es superior al 30 por ciento para un solo ISP y no se resuelve en un plazo de 24 horas, es aconsejable plantear una preocupación al consultor de entregas de Adobe Campaign.

## Recursos específicos de productos

**Adobe Campaign Standard**

* [Lista de informes: Resumen de devoluciones (documentación del producto)](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
* [Comprensión de los errores de entrega (documentación del producto)](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=en#about-delivery-failures)

**Adobe Campaign Classic**

* [Comprensión de los errores de entrega (documentación del producto)](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=en#sending-messages)