---
title: Todo acerca de las trampas de correo no deseado
description: Aprenda a comprender, identificar y evitar trampas no deseadas al administrar la capacidad de envío.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 45cdcda0-70e4-47f4-8713-a834500e7881
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 2%

---

# Todo acerca de las trampas de correo no deseado

Una [trampa de correo no deseado](/help/metrics/spam-traps.md) es una dirección válida, sin mensaje de error cuando se envían correos electrónicos a. Una trampa de correo no deseado tiene una misión principal: identificar remitentes o remitentes de spam sin proceso de higiene de datos.

## ¿Quién administra estas direcciones de trampa de correo no deseado?

El primer tipo de direcciones de trampa de correo no deseado es la empresa de lista de bloqueados de IP y dominios como SpamHaus, Sorbs, SpamCop. Estas empresas tienen una enorme red de direcciones que se envían en varias páginas de Internet como sitios web, blogs, foros para que sus direcciones sean recopiladas por remitentes de spam.

El segundo tipo de trampa de correo no deseado se basa en las antiguas direcciones ISP activas. Estos ISP tienen su propia red de trampa de correo no deseado creada sobre direcciones inactivas reconvertidas en trampa y cada visita que afectan a la reputación del dominio y la IP del remitente.

## ¿Cómo funciona?

**Una dirección de correo electrónico sin usuario** final: Estas direcciones no tienen y nunca tendrán un usuario final que pueda registrarse en boletines informativos o en cualquier otro tipo de comunicaciones.

**Una dirección de correo electrónico abandonada por un usuario**: Tras un periodo de inactividad, los ISP desactivan las direcciones. Los mensajes de devoluciones se envían a los remitentes para informarles sobre este nuevo estado. Los remitentes deben poner en cuarentena estas direcciones o eliminarlas de futuras comunicaciones. Los ISP utilizan estas direcciones transformadas en &quot;trampa de correo no deseado&quot; para supervisar a los remitentes con prácticas incorrectas.

## ¿Cómo reconocer o identificar una trampa de correo no deseado?

Es difícil identificar las trampas de correo no deseado, ya que estas direcciones deben permanecer anónimas ya que se utilizan para identificar a los remitentes incorrectos. La mayoría de los ISP no tienen un sistema abierto y hacen clic en él para supervisar las visitas de remitentes incorrectos. Según definiciones anteriores, es posible determinar un pod de direcciones sospechosas y comprobar la eficacia de la selección del pod.

## ¿Por qué la base de datos está infectada por trampas de correo no deseado?

La base de datos de direcciones de correo electrónico contiene trampa de correo no deseado, ¿cómo podría ser posible? Las dos razones principales son una falta en el proceso de higiene de la base de datos o disfunción de la colección.

Estos pocos puntos le ayudan a comprobar sus procesos:

* Recopilar disfunción:
   * ¿De dónde provienen sus direcciones de correo electrónico? ¿Cuántas fuentes se utilizan para recopilar estas direcciones? ¿Puede identificarlos? ¿Interno/de registro?
   * ¿Su sistema de inclusión funciona correctamente?
   * ¿Ha comprobado los dominios y el alias de sus direcciones? ¡Hazlo con la mesa de abajo!
* Proceso de higiene de la base de datos:
   * ¿Cuál es su proceso con respecto a la dirección inactiva en los últimos 12 meses?
   * ¿Está procesando una cuarentena en rechazos leves como &quot;usuario inactivo&quot;?
   * ¿Cuándo fue la última vez que cuidaste tu base de datos y trataste de limpiarla? Hazlo regularmente.

## Alias y dominios para evitar

**Alias**

![](../../help/assets/aliases.png)

**Dominios**

![](../../help/assets/domains.png)
