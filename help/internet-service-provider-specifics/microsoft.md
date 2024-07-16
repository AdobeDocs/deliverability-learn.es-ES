---
title: Microsoft (Hotmail, Outlook, Windows Live, etc.)
description: Microsoft suele ser el segundo o tercer proveedor más grande según la composición de la lista y gestiona el tráfico de forma ligeramente diferente al de otros ISP.
topics: Deliverability
jira: KT-5319
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.)

[!DNL Microsoft] es generalmente el segundo o tercer proveedor más grande según la composición de la lista y gestiona el tráfico de forma ligeramente diferente a otros ISP.

A continuación se muestran algunos aspectos destacados:

## Datos importantes

[!DNL Microsoft] se centra en la reputación del remitente, las quejas, la participación del usuario y su propio grupo de usuarios de confianza (también conocidos como datos de reputación del remitente o SRD) a los que sondean para obtener comentarios.

## ¿Qué datos ponen a disposición?

La herramienta de informe de remitente registrada de [!DNL Microsoft], [!DNL Smart Network Data Services] (SNDS), le permite ver métricas sobre la cantidad de correo que está enviando y la cantidad de correo que se acepta, así como quejas y trampas de correo no deseado. Tenga en cuenta que los datos compartidos son un ejemplo y no reflejan números exactos, pero representan mejor la forma en que [!DNL Microsoft] lo ve a usted como remitente. [!DNL Microsoft] no proporciona información pública sobre su grupo de usuarios de confianza, pero esos datos están disponibles a través del programa [!DNL Return Path Certification] por un cargo adicional.

## Conocimiento del remitente

[!DNL Microsoft] se ha centrado tradicionalmente en enviar direcciones IP en sus evaluaciones de reputación y decisiones de filtrado. También están trabajando activamente en ampliar sus capacidades de dominio de envío. Ambos están impulsados en gran medida por los influenciadores de reputación tradicionales, como quejas y trampas de correo no deseado. La capacidad de entrega también puede verse fuertemente influida por el programa Return Path Certification, que tiene requisitos cuantitativos y cualitativos específicos del programa.

## Insights

[!DNL Microsoft] combina todos sus dominios de recepción para establecer y rastrear la reputación de envío. Esto incluye [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], etc., así como cualquier correo electrónico alojado en Office 365 corporativo. [!DNL Microsoft] puede ser especialmente sensible a las fluctuaciones en el volumen, así que considere la posibilidad de aplicar estrategias específicas para aumentar y reducir desde envíos grandes en lugar de permitir cambios repentinos basados en el volumen.

[!DNL Microsoft] también es especialmente estricto durante los primeros días del calentamiento de la IP, lo que generalmente significa que la mayoría de los correos se filtran inicialmente. La mayoría de los ISP consideran inocentes a los remitentes hasta que se demuestre su culpabilidad. [!DNL Microsoft] es lo contrario y lo considera culpable hasta que pruebe que es inocente.
