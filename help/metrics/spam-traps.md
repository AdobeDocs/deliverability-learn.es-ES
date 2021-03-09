---
title: Trampas de correo no deseado
description: Obtenga información sobre los distintos tipos de trampas de correo no deseado.
feature: Métricas
topics: Deliverability
kt: 7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 3%

---


# Trampas de correo no deseado

Existen trampas de correo no deseado para ayudar a identificar el correo de remitentes fraudulentos o aquellos que no siguen las prácticas recomendadas de correo electrónico. La dirección de correo electrónico de la trampa de correo no deseado generalmente no se publica públicamente y es casi imposible de identificar. El envío de correos electrónicos a trampas de correo no deseado puede afectar a su reputación con distintos grados de gravedad según el tipo de trampa y el ISP. Obtenga más información sobre los distintos tipos de trampas de correo no deseado en las siguientes secciones.

## Reciclado

Las trampas de correo no deseado recicladas son direcciones que una vez fueron válidas pero que ya no se utilizan. Una forma clave de mantener las listas lo más limpias posible es enviar con regularidad correos electrónicos a toda la lista y suprimir correctamente los correos electrónicos devueltos. Esto ayuda a que las direcciones de correo electrónico abandonadas se pongan en cuarentena y se abstengan de seguir usándolas.

En algunos casos, una dirección puede reciclarse en un plazo de 30 días. El envío regular es un aspecto vital de la buena higiene de las listas, junto con la supresión regular de los usuarios inactivos. **[Las ](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/re-engagement-best-practices.html?lang=en#sending-messages)** campañas de reparticipación suelen formar parte de sofisticados programas de marketing por correo electrónico. Este estilo de campaña permite al remitente intentar recuperar usuarios que de otra manera ya no serían enviados por correo electrónico.

## Typo

Una trampa de correo no deseado tipográfica es una dirección que contiene errores ortográficos o malformaciones. Esto suele ocurrir con errores ortográficos conocidos de dominios importantes como Gmail (por ejemplo: gmial es un error tipográfico común). Los ISP y otros operadores de listas de bloqueo registrarán dominios conocidos que no sean válidos para utilizarse como trampa de correo no deseado con el fin de identificar a los remitentes de correo no deseado y medir el estado del remitente. La mejor manera de evitar trampas de correo no deseado es utilizar un **proceso de inclusión doble** para la recopilación de listas.

## Pristina

Una trampa de correo no deseado prístina es una dirección que no tiene usuario final y que nunca ha tenido un usuario final. Es una dirección que se creó únicamente para identificar el correo electrónico no deseado. Este es el tipo de trampa de correo no deseado más impactante, ya que es virtualmente imposible de identificar y requeriría un esfuerzo sustancial para limpiar de la lista. La mayoría de las listas de bloqueo utilizan trampas de correo no deseado prístinas para enumerar remitentes que no tienen reputación. La única manera de evitar que las trampas de correo no deseado prístinas infecten su lista de correo electrónico de marketing más amplia es utilizar un **proceso de inclusión doble** para la recopilación de listas.

## Recursos específicos de productos

**Adobe Campaign Classic**

* [SpamAssassin](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin.html?lang=en#using-spamassassin)

**Adobe Campaign Standard**

* [Previsualización de su análisis de correo electrónico y antispam](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email.html#designing-content)
* [Proceso de inclusión doble](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=en#communication-channels)

