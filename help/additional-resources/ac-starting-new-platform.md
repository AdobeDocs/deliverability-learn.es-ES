---
title: Inicio de una nueva plataforma
description: Obtenga más información sobre la administración de la capacidad de envío al iniciar una nueva plataforma con Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 65%

---

# Inicio de una nueva plataforma {#starting-new-platform}

Mantener la reputación de su dominio y dirección IP es esencial al configurar una nueva plataforma para usar con Adobe Campaign.

## Un paso delicado

Debe tener mucho cuidado al empezar a enviar correos electrónicos en una nueva plataforma, ya que la plataforma no tiene historial de uso y no tiene reputación cuando las direcciones IP de envío nunca se han utilizado para este fin.

Los ISP sospechan naturalmente de las direcciones IP que nunca se han utilizado para enviar correos electrónicos y que de repente comienzan a enviar grandes volúmenes de tráfico de correo electrónico. De hecho, los remitentes de correo no deseado generalmente utilizan direcciones IP &quot;desconocidas&quot; (direcciones que nunca quedaron en la lista de bloqueados) para enviar la mayor cantidad posible de mensajes antes de la detección.

No se puede esperar alcanzar la velocidad operativa en términos de salida al inicio de la fase de producción. Además, no debería intentar enviar mensajes a este ritmo, ya que podría llevar a los ISP a bloquear las direcciones de envío y comprometer seriamente el resto de la fase de inicio.

## Principios principales

A continuación se enumeran los principios principales que deben seguirse al iniciar una nueva plataforma.

* Configure un subdominio dedicado específico que sea específico de las campañas de correo electrónico enviadas desde el Adobe.

* Si tiene esta información, **importe direcciones no válidas en la tabla de cuarentenas**.
El inicio de una plataforma suele ocurrir cuando se utiliza una lista de direcciones por primera vez y puede que no esté completamente cualificada. Si envía a direcciones no válidas o a direcciones de honeypot, esto contribuye a disminuir la reputación de la plataforma.

   * Si tiene una lista de direcciones no válidas, lo mejor es importarla a la tabla de cuarentena antes de enviarla por primera vez. La tabla de cuarentena está disponible a través de la variable **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) y **[!UICONTROL Administration > Channels > Quarantines > Addresses]** (Campaign Standard).

   * Si, al mismo tiempo, desea recalificar las direcciones no válidas, es preferible hacerlo una vez que se establezca la reputación de la plataforma y poco a poco para &quot;diluir&quot; el uso de direcciones incorrectas con el tiempo.

* **Limite la velocidad de rendimiento** limitando el número de equipos. Para obtener más información sobre cómo ajustar esta configuración técnica, póngase en contacto con el administrador de Adobe Campaign.

* **Aumente progresivamente los volúmenes enviados** para evitar ser marcados como correo no deseado. Evite asignar toda la base de datos desde el mismo inicio; sino, añada una fracción adicional de la lista cada vez que envíe. Esto debería permitirle aumentar el volumen en cada paso y reducir al mismo tiempo la tasa global de direcciones no válidas. Para garantizar un desarrollo fluido de la fase de inicio, puede utilizar olas.

* **Envíe regularmente**. En cierta medida, es mejor enviar pequeñas tomas con regularidad que grandes campañas esporádicamente.
* **Preste mucha atención a los informes de envío**. Los indicadores de error altos pueden significar que una configuración técnica está mal configurada.

## Recursos adicionales

Para obtener más información sobre los principios enumerados anteriormente y su implementación con Adobe Campaign, consulte las secciones siguientes:

* [Aumente su reputación de correo electrónico con el calentamiento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [Todo acerca de las trampas de correo no deseado](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Optimización de la entrega mediante cuarentenas](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identificar direcciones en cuarentena para toda la plataforma](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [Envío mediante múltiples olas](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [Supervisión de entregas](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=es)

**Adobe Campaign Standard**

* [Optimización de la entrega mediante cuarentenas](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identificar direcciones en cuarentena para toda la plataforma](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [Seguimiento de una entrega](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html)
