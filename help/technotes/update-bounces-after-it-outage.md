---
title: Actualizar calificación de devoluciones después de la interrupción de Italia Online
description: Aprenda a actualizar la calificación de devoluciones después de la interrupción de Italia Online
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
hidefromtoc: true
role: Admin
level: Beginner
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 22%

---

# Actualizar devoluciones graves incorrectas después de la interrupción en línea de Italia {#update-bounce-italia}

## Contexto{#outage-context}

A partir del 22 de enero (hora local), Italia Online ha pasado por una interrupción que ha resultado en varios retrasos y correos electrónicos rechazados. El servicio empezó a reanudarse con capacidad limitada el 26 de enero.

Los dominios afectados son: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**, y **blu.it**.

Este problema se produjo del 22/1/2023 al 26/1/2023, pero la mayoría de las cuarentenas incorrectas se produjeron el 26 de enero.

Obtenga más información en la comunicación oficial [aquí](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

Como en la mayoría de los casos, cuando se produce una interrupción de un proveedor de servicio de Internet (ISP), algunos correos electrónicos enviados a través de Campaign o Journey Optimizer se marcaron erróneamente como rechazos. Esto no solo impactó en el Adobe, sino en todos los que intentaron que Italia Online recibiera correo electrónico durante la interrupción.

Los síntomas fueron:

* **Rechazos leves** con el mensaje `452 requested action aborted: try again later` : se volvieron a intentar automáticamente y no se necesitan acciones.

* **Rechazos graves** con el mensaje `550 <email address> recipient rejected` han sido devueltos por el ISP el 26 de enero, entre las 8:00 y las 14:00, hora local, para evitar que los remitentes sigan sobrecargando sus servidores. Como ha confirmado el administrador de correo de Italia Online, no se trata de devoluciones reales, por lo que recomendamos dejar de poner en cuarentena todas las direcciones de correo electrónico que se excluyeron el 26 de enero de 2023 debido a ese mensaje.

## Proceso de actualización{#outage-update}

### Adobe Campaign{#ac-update}

Por lógica de gestión de devoluciones estándar, Adobe Campaign añadió automáticamente estos destinatarios a la lista de cuarentena con una configuración **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corregir esto, debe actualizar la tabla de cuarentena en Campaign buscando y quitando estos destinatarios o cambiando su **[!UICONTROL Status]** a **[!UICONTROL Valid]** para que el flujo de trabajo de limpieza nocturno los elimine.

Para encontrar los destinatarios afectados por este problema, o en caso de que esto vuelva a suceder con cualquier otro ISP, consulte las instrucciones a continuación:

* Para Campaign Classic v7 y Campaign v8, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Para Campaign Standard, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

Por lógica de gestión de devoluciones estándar, Adobe Journey Optimizer añadió automáticamente estas direcciones de correo electrónico a la lista de supresión con una **[!UICONTROL Reason]** configuración de **[!UICONTROL Invalid Recipient]**. Para corregir esto, debe actualizar la lista de supresión buscando y eliminando estas direcciones de correo electrónico.

Una vez identificadas, estas direcciones se pueden eliminar manualmente de la lista de supresión mediante la variable **[!UICONTROL Delete]** botón. Estas direcciones se pueden incluir en futuras campañas de correo electrónico.

Obtenga más información en [esta sección](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

