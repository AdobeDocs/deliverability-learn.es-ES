---
title: Actualizar calificación de devoluciones después de la interrupción de Italia Online
description: Aprenda a actualizar la calificación de devoluciones después de la interrupción de Italia Online
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
role: Admin
level: Beginner
TQID: https://experienceleague.adobe.com/hPHB9s3PH7E9L3omZMTWZA2ZB0d1JS5vEfawQOjnBLw
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b3b8a63f-51fc-40f6-a7d2-a31c5d49fb45id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 459
ht-degree: 16%

---

# Actualizar devoluciones graves incorrectas después de la interrupción en línea de Italia {#update-bounce-italia}

## Contexto{#outage-context}

A partir del 22 de enero (hora local), Italia Online ha pasado por una interrupción que ha resultado en varios retrasos y correos electrónicos rechazados. El servicio empezó a reanudarse con capacidad limitada el 26 de enero.

Los dominios afectados son: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** y **blu.it**.

Este problema se produjo del 22/1/2023 al 26/1/2023, pero la mayoría de las cuarentenas incorrectas se produjeron el 26 de enero.

Obtenga más información en la comunicación oficial [aquí](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

Como en la mayoría de los casos, cuando se produce una interrupción de un proveedor de servicio de Internet (ISP), algunos correos electrónicos enviados a través de Campaign o Journey Optimizer se marcaron erróneamente como rechazos. Esto no solo impactó a Adobe, sino a todos los que intentaron que Italia Online recibiera correo electrónico durante la interrupción del servicio.

Los síntomas fueron:

* **Devoluciones leves** con el mensaje `452 requested action aborted: try again later`: se volvieron a intentar automáticamente y no se necesitan acciones.

* El ISP ha devuelto **devoluciones graves** con el mensaje `550 <email address> recipient rejected` el 26 de enero, entre las 8:00 y las 14:00, hora local, para evitar que los remitentes sigan sobrecargando sus servidores. Como ha confirmado el administrador de correo de Italia Online, no se trata de devoluciones reales, por lo que recomendamos dejar de poner en cuarentena todas las direcciones de correo electrónico que se excluyeron el 26 de enero de 2023 debido a ese mensaje.

## Proceso de actualización{#outage-update}

### Adobe Campaign{#ac-update}

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones a continuación:

* Para Campaign Classic v7 y Campaign v8, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Para Campaign Standard, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

Por lógica de gestión de devoluciones estándar, Adobe Journey Optimizer agregó automáticamente estas direcciones de correo electrónico a la lista de supresión con una configuración **[!UICONTROL Reason]** de **[!UICONTROL Invalid Recipient]**. Para corregir esto, debe actualizar la lista de supresión buscando y eliminando estas direcciones de correo electrónico.

Una vez identificadas, estas direcciones se pueden eliminar manualmente de la lista de supresión con el botón **[!UICONTROL Delete]**. Estas direcciones se pueden incluir en futuras campañas de correo electrónico.

Obtenga más información en [esta sección](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

