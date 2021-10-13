---
title: Microsoft (Hotmail, Outlook, Windows Live, etc.)
description: Microsoft es generalmente el segundo o tercer proveedor más grande en función de la configuración de la lista y gestiona el tráfico ligeramente diferente a otros ISP.
topics: Deliverability
kt: 5319
doc-type: article
activity: understand
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.)

[!DNL Microsoft] generalmente es el segundo o tercer proveedor más grande en función de la configuración de la lista, y gestiona el tráfico ligeramente diferente de otros ISP.

A continuación se muestran algunos aspectos destacados:

## Qué datos son importantes

[!DNL Microsoft] se centra en la reputación del remitente, las quejas, la participación del usuario y su propio grupo de usuarios de confianza (también conocidos como datos de reputación del remitente o SRD) a los que sondean para obtener comentarios.

## Qué datos ponen a disposición

[!DNL Microsoft]La herramienta de informes de remitentes propietaria de ,  [!DNL Smart Network Data Services] (SNDS), le permite ver las métricas sobre la cantidad de correo que envía y la cantidad de correo aceptado, así como las quejas y trampas de correo no deseado. Tenga en cuenta que los datos compartidos son una muestra y no reflejan números exactos, pero representa mejor cómo [!DNL Microsoft] lo ve como remitente. [!DNL Microsoft] no proporciona información sobre su grupo de usuarios de confianza públicamente, pero esos datos están disponibles a través del  [!DNL Return Path Certification] programa por un cargo adicional.

## Conocimiento del remitente

[!DNL Microsoft] tradicionalmente se ha centrado en enviar IP en sus evaluaciones de reputación y decisiones de filtrado. También están trabajando activamente en la expansión de sus capacidades de envío de dominio. Ambos están impulsados en gran medida por los influyentes tradicionales en la reputación, como quejas y trampas de spam. La capacidad de entrega también puede verse fuertemente influida por el programa Return Path Certification, que tiene requisitos específicos cuantitativos y cualitativos del programa.

## Perspectivas

[!DNL Microsoft] combina todos los dominios de recepción para establecer y rastrear la reputación de envío. Esto incluye [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], etc., así como cualquier correo electrónico alojado en Office 365. [!DNL Microsoft] puede ser especialmente sensible a las fluctuaciones en el volumen, por lo que considere la posibilidad de aplicar estrategias específicas para aumentar y reducir desde los envíos grandes en lugar de permitir cambios repentinos basados en el volumen.

[!DNL Microsoft] también es especialmente estricto durante los días iniciales de calentamiento de IP, lo que generalmente significa que la mayoría del correo se filtra inicialmente. La mayoría de los ISP consideran inocentes a los remitentes hasta que se demuestre su culpabilidad. [!DNL Microsoft] es lo contrario y te considera culpable hasta que te pruebes inocente.
