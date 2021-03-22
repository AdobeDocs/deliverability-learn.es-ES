---
title: Reclamaciones
description: 'Obtenga información sobre las quejas que se registran cuando un usuario indica que un correo electrónico es no deseado o inesperado. '
feature: Métricas
topics: Deliverability
kt: 7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 550821608eb7049f739a156536dd31b6b2faa2fa
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---


# Reclamaciones

Las quejas se registran cuando un usuario indica que un correo electrónico es no deseado o inesperado. Esta acción del suscriptor se registra generalmente a través del cliente de correo electrónico del suscriptor cuando pulsa el botón de correo no deseado o a través de un sistema de informes de correo no deseado de terceros.

## queja del ISP

La mayoría de los ISP de nivel 1 y algunos de nivel 2 ofrecen un método de informes de correo no deseado a sus usuarios, ya que los procesos de exclusión y cancelación de suscripción se han utilizado de forma maliciosa en el pasado para validar una dirección de correo electrónico. Adobe Campaign recibe estas quejas a través de los ISP FBL. Esto se establece durante el proceso de configuración para cualquier ISP que proporcione FBL y permite a Adobe Campaign añadir automáticamente direcciones de correo electrónico que se quejen a la tabla de cuarentena para su supresión. Los picos en las quejas de los ISP pueden ser un indicador de una calidad de lista deficiente, métodos de recopilación de listas menos que óptimos o políticas de participación débiles. También se suelen observar cuando el contenido no es relevante.

## Reclamaciones de terceros

Existen varios grupos de correo no deseado que permiten la creación de informes de correo no deseado a un nivel más amplio. Las métricas de quejas utilizadas por estos terceros se utilizan para etiquetar contenido de correo electrónico con el fin de identificar el correo electrónico no deseado. Este proceso también se conoce como huella digital. Los usuarios de estos métodos de queja de terceros generalmente son más conocedores del correo electrónico, por lo que pueden tener un impacto bueno que otras quejas si no se les responde.

>[!NOTE]
>
>Los ISP recopilan quejas y las utilizan para determinar la reputación general de un remitente. Todas las denuncias deben suprimirse y ya no deben ponerse en contacto lo antes posible y de conformidad con las leyes y reglamentos locales.

## Recursos específicos de productos

**Adobe Campaign Classic**

* [Indicadores de seguimiento](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#tracking-indicators)

**Adobe Campaign Standard**

* [Informe de quejas](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html#reporting)