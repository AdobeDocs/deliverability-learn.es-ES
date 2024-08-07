---
title: Verizon Media Group (Yahoo, AOL, Verizon, etc.)
description: '"[!DNL Verizon Media Group] suele ser uno de los tres dominios principales de la mayoría de las listas B2C. Se comportan de manera única, ya que generalmente limitan o agrandan el correo si surgen problemas de reputación".'
topics: Deliverability
jira: KT-5320
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 3%

---

# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon, etc.)

[!DNL Verizon Media Group] suele ser uno de los tres dominios principales de la mayoría de las listas B2C. Se comportan de forma única, ya que generalmente limitan o envían correos masivos si surgen problemas de reputación.

A continuación se muestran algunos aspectos destacados:

## Datos importantes

[!DNL Verizon Media Group] (VMG) ha creado y mantiene sus propios filtros de correo no deseado, usando una mezcla de contenido, filtrado de URL y quejas de correo no deseado. Junto con Gmail, son uno de los primeros ISP que adoptaron y que filtran el correo electrónico por dominio y dirección IP.

## ¿Qué datos ponen a disposición?

VMG tiene un FBL utilizado para enviar información de quejas a los remitentes. También están explorando la posibilidad de añadir más datos en el futuro.

## Conocimiento del remitente

La reputación de un remitente está formada por una combinación de dirección IP, dominio y dirección remitente. La reputación se calcula mediante los componentes tradicionales, que incluyen quejas, trampas de correo no deseado, direcciones inactivas o mal formadas y participación. VMG utiliza la limitación de velocidad (también conocida como limitación) junto con la carpeta masiva para defenderse del spam. Complementan sus sistemas de filtrado internos con algunas listas negras de [!DNL Spamhaus], incluidas la PBL, SBL y XBL para proteger a sus usuarios.

## Insights

VMG tiene períodos de mantenimiento regulares para direcciones de correo electrónico antiguas, inactivas últimamente. Esto significa que es común observar un aumento significativo de devoluciones de direcciones no válidas, lo que puede afectar a la tasa de entrega durante un corto período de tiempo. También son sensibles a las altas tasas de devoluciones de direcciones no válidas de un remitente, lo que indica una necesidad de endurecer las políticas de adquisición o participación. Los remitentes a menudo pueden experimentar un impacto negativo en alrededor del 1 por ciento de direcciones no válidas.
