---
title: Quejas
description: Obtenga información sobre las quejas que se registran cuando un usuario indica que un correo electrónico es no deseado o inesperado.
topics: Deliverability
jira: KT-7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
TQID: https://experienceleague.adobe.com/W9G0ZPGeIm5KmVHu5-VuMd-Kb-4x4f7qhBPnpskxqqA
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 100%

---

# Quejas

Las quejas se registran cuando un usuario indica que un correo electrónico es no deseado o inesperado. Esta acción del suscriptor se suele registrar a través del cliente de correo electrónico del suscriptor cuando pulsa el botón de correo no deseado o a través de un sistema de informes de correo no deseado de terceros.

## Queja de ISP

La mayoría de los ISP de nivel 1, así como algunos de nivel 2, ofrecen un método de creación de informes de correo no deseado a sus usuarios, ya que los procesos de exclusión y cancelación de suscripción se han utilizado de forma maliciosa en el pasado para validar una dirección de correo electrónico. Adobe Campaign recibe estas quejas a través de los FBL de los ISP. Esto se establece durante el proceso de configuración para cualquier ISP que proporcione FBL y permite a Adobe Campaign añadir automáticamente las direcciones de correo electrónico que se quejaron a la tabla de cuarentena para su supresión. Los picos en las quejas de los ISP pueden ser un indicador de la mala calidad de la lista, de métodos de colección de listas no óptimos o de débiles políticas de participación. También se suelen observar cuando el contenido no es relevante.

## Quejas de terceros

Existen varios grupos de correo no deseado que permiten la creación de informes de correo no deseado a un nivel más amplio. Las métricas de quejas utilizadas por estos terceros se utilizan para etiquetar el contenido del correo electrónico con el fin de identificar el correo electrónico no deseado. Este proceso también se conoce como huella digital. Los usuarios de estos métodos de presentación de quejas de terceros generalmente tienen más experiencia con correos electrónicos, por lo que pueden tener un mayor impacto que otras quejas si no se les responde.

>[!NOTE]
>
>Los ISP recopilan quejas y las utilizan para determinar la reputación general de un remitente. Todas las quejas deben resolverse y dejar de contactar con los remitentes lo antes posible, de conformidad con las leyes y los reglamentos locales.

## Recursos específicos de los productos

**Adobe Campaign Classic**

* [Indicadores de seguimiento](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=es#tracking-indicators)

**Adobe Campaign Standard**

* [Informe de quejas](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html?lang=es#reporting)
