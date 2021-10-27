---
title: Quejas
description: 'Obtenga información sobre las quejas que se registran cuando un usuario indica que un correo electrónico es no deseado o inesperado. '
topics: Deliverability
kt: 7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: ht
source-wordcount: '290'
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
