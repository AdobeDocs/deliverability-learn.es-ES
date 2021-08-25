---
title: Duplicados
description: Obtenga información sobre cómo identificar y limitar duplicados para mejorar la capacidad de envío.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 62%

---

# Duplicados {#duplicates}

Contar con direcciones de correo electrónico duplicadas puede tener varias consecuencias:

* El mismo mensaje se envía más de una vez. Incluso si Adobe realiza un procedimiento de deduplicación de forma predeterminada antes de enviar, no hay nada que detenga el mismo mensaje enviado por acciones diferentes que tengan el mismo contenido cuando se divide un destinatario.
* Solicitudes de cancelación de suscripción no aceptadas. Si un destinatario cancela la suscripción después de recibir un mensaje, su perfil duplicado sigue siendo apto para mensajes posteriores.

Además de este paso secundario de los procedimientos de inclusión, esta situación probablemente lleve a los usuarios a considerar los mensajes como no deseados y a activar un procedimiento de inclusión en la lista de bloqueados en el ISP.

Debe ser particularmente prudente al realizar operaciones en la base de datos:

* Las importaciones deben configurarse meticulosamente, en particular al elegir la clave de reconciliación.
* Las direcciones de correo electrónico cambiadas también pueden ser una fuente de duplicados. En concreto, dos direcciones con dominios diferentes pueden enrutarse al mismo buzón, por ejemplo, si una empresa ha cambiado el nombre y ha mantenido el dominio anterior durante un tiempo determinado: joe.doe@amce-co.com y joe.doe@acme-rebranded.com.
* Las importaciones automáticas, ya sean de listas o de otras bases de datos, son elementos que se deben tener en cuenta al administrar perfiles. ¿Qué sucede cuando elimina o mueve un perfil en otra partición? Se puede volver a crear en la partición inicial mediante una importación automática, por ejemplo, cuando se realiza una orden de compra.
* El almacenamiento de perfiles en diferentes carpetas se puede implementar mediante vistas en lugar de particiones. De este modo, puede estar seguro de que los perfiles están en la misma partición física y, al mismo tiempo, permite que se muestren y gestionen los derechos adecuados.

De todas maneras, hay casos en los que los duplicados entre las diferentes particiones son normales. Por ejemplo, cuando se envían para terceros o entidades de empresa diferentes, es lógico que la misma persona sea receptora por diferentes motivos. Sin embargo, rara vez se pueden encontrar duplicados dentro de la misma partición.

## Recursos específicos de los productos

Las direcciones duplicadas protegen su reputación de envío y garantizan una buena gestión de cuarentena. Obtenga más información en las siguientes secciones de documentación del producto:

**Adobe Campaign Classic**

* [Actividad de anulación de duplicación](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Uso de la funcionalidad Combinar de la actividad de Anulación de duplicación](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html?lang=es)

**Adobe Campaign Standard**

* [Deduplicación de datos de un archivo importado](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)
