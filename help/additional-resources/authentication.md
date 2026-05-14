---
title: Autenticación
description: Obtenga más información sobre los métodos de autenticación SPF, DKIM y DMARC.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
TQID: https://experienceleague.adobe.com/zuhBmNWmF8CoCSNofsg3FKCcQFLOFfZmRutB2P1L4-U
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 769
ht-degree: 42%

---

# Autenticación

## SPF {#spf}

SPF (Entorno de políticas de remitentes) es un estándar de autenticación de correo electrónico que permite al propietario de un dominio especificar qué servidores de correo electrónico pueden enviar correos electrónicos en nombre de ese dominio. Este estándar utiliza el dominio en el encabezado “Return-Path” del correo electrónico (también denominado la dirección “Envelope From”).

>[!NOTE]
>
>Puede usar [esta herramienta externa](https://www.kitterman.com/spf/validate.html) para comprobar un registro SPF.

El SPF es una técnica que, a su vez, permite asegurarse de que el nombre de dominio utilizado en un mensaje de correo electrónico no sea falso. Cuando se recibe un mensaje de un dominio, se consulta el servidor DNS del dominio. La respuesta es un breve registro (el registro SPF) que muestra los servidores autorizados para enviar correos electrónicos desde este dominio. Si asumimos que solo el propietario del dominio tiene la posibilidad de cambiar este registro, podemos considerar que esta técnica no permite que la dirección del remitente sea falsa, al menos no la parte a la derecha de la “@”.

En la especificación final [RFC 4408](https://www.rfc-editor.org/info/rfc4408), se utilizan dos elementos del mensaje para determinar el dominio considerado como remitente: el dominio especificado por el comando SMTP &quot;HELO&quot; (o &quot;EHLO&quot;) y el dominio especificado por la dirección del encabezado &quot;Return-Path&quot; (o &quot;MAIL FROM&quot;), que también es la dirección de rechazo. Las diferentes consideraciones permiten tener en cuenta solo uno de estos valores; se recomienda que ambos orígenes especifiquen el mismo dominio.

La comprobación del SPF ofrece una evaluación de la validez del dominio del remitente:

* **Ninguno**: no se pudo realizar ninguna evaluación.
* **Neutral**: el dominio consultado no habilita la evaluación.
* **Paso**: el dominio se considera auténtico.
* **Error**: el dominio es falso y el mensaje se debe rechazar.
* **SoftFail**: Es probable que el dominio sea falso, pero el mensaje no se debe rechazar únicamente en función de este resultado.
* **TempError**: Un error temporal detuvo la evaluación. El mensaje se puede rechazar.
* **PermError**: Los registros del SPF del dominio no son válidos.

Cabe señalar que el proceso para tener en cuenta los registros realizados al nivel de los servidores DNS puede tardar hasta 48 horas. Este retardo depende de la frecuencia con que se actualicen las cachés DNS de los servidores receptores.

## DKIM {#dkim}

La autenticación DKIM (DomainKeys Identified Mail) es un sucesor de SPF. Utiliza criptografía de clave pública que permite al servidor de recepción de correos electrónicos verificar que un mensaje fue enviado por la persona o entidad por la que afirma que fue enviado, y si el contenido del mensaje se alteró entre el momento en que se envió originalmente (y &quot;firmado&quot; por DKIM) y la hora en que se recibió. Este estándar suele utilizar el dominio en el encabezado &quot;De&quot; o &quot;Remitente&quot;.

DKIM proviene de una combinación de DomainKeys, Yahoo! y Cisco identificaron los principios de autenticación de correo de Internet y se utilizan para comprobar la autenticidad del dominio del remitente y garantizar la integridad del mensaje.

DKIM sustituye la autenticación por **DomainKeys**.

El uso de DKIM requiere algunos requisitos previos:

* **Seguridad**: el cifrado es un elemento clave de DKIM. Para garantizar el nivel de seguridad de DKIM, 1024b es el tamaño de cifrado recomendado por las prácticas recomendadas. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM inferiores.
* **Reputación**: la reputación se basa en la dirección IP o en el dominio, pero el selector menos transparente de DKIM también es un elemento clave a tener en cuenta. La elección del selector es importante: evite mantener el &quot;predeterminado&quot; que podría utilizar cualquier persona y, por lo tanto, tiene una reputación débil. Debe implementar un selector diferente para las **retention vs. acquisition communications** y para la autenticación.

Obtenga más información sobre los requisitos previos de DKIM al usar Campaign Classic en [esta sección](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Autenticación de mensajes, creación de informes y conformidad basados en dominio) es la forma más reciente de autenticación por correo electrónico y se basa en la autenticación SPF y DKIM para determinar si un correo electrónico pasa o falla. DMARC es único y eficaz de dos maneras importantes:

* Conformidad: permite al remitente indicar a los ISP qué hacer con cualquier mensaje que no se autentique (por ejemplo: no aceptarlo).
* Creación de informes: proporciona al remitente un informe detallado que muestra todos los mensajes en los que se ha producido un error en la autenticación DMARC, junto con el dominio “De” y la dirección IP utilizadas para cada uno. Esto permite a una empresa identificar el correo electrónico legítimo que falla en la autenticación y necesita algún tipo de &quot;corrección&quot; (por ejemplo, añadir direcciones IP a su registro SPF), así como las fuentes y la prevalencia de intentos de phishing en sus dominios de correo electrónico.

>[!NOTE]
>
>DMARC puede aprovechar los informes generados por [250ok](https://250ok.com/).
