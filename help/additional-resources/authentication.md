---
title: Autenticación
description: Obtenga más información sobre los métodos de autenticación SPF, DKIM y DMARC.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 57%

---

# Autenticación

## SPF {#spf}

SPF (Entorno de políticas de remitentes) es un estándar de autenticación de correo electrónico que permite al propietario de un dominio especificar qué servidores de correo electrónico pueden enviar correos electrónicos en nombre de ese dominio. Este estándar utiliza el dominio en el encabezado “Return-Path” del correo electrónico (también denominado la dirección “Envelope From”).

>[!NOTE]
>
>Puede utilizar [esta herramienta externa](https://www.kitterman.com/spf/validate.html) para verificar un registro SPF.

El SPF es una técnica que, a su vez, permite asegurarse de que el nombre de dominio utilizado en un mensaje de correo electrónico no sea falso. Cuando se recibe un mensaje de un dominio, se consulta el servidor DNS del dominio. La respuesta es un breve registro (el registro SPF) que muestra los servidores autorizados para enviar correos electrónicos desde este dominio. Si asumimos que solo el propietario del dominio tiene la posibilidad de cambiar este registro, podemos considerar que esta técnica no permite que la dirección del remitente sea falsa, al menos no la parte a la derecha de la “@”.

En la especificación final [RFC 4408](https://www.rfc-editor.org/info/rfc4408), se utilizan dos elementos del mensaje para determinar el dominio considerado como remitente: el dominio especificado por el comando SMTP &quot;HELO&quot; (o &quot;EHLO&quot;) y el dominio especificado por la dirección del encabezado &quot;Return-Path&quot; (o &quot;MAIL FROM&quot;), que también es la dirección de rechazo. Las diferentes consideraciones permiten tener en cuenta solo uno de estos valores; se recomienda que ambos orígenes especifiquen el mismo dominio.

La comprobación del SPF ofrece una evaluación de la validez del dominio del remitente:

* **None**: No se pudo realizar ninguna evaluación.
* **Neutral**: El dominio que se consulta no activa la evaluación.
* **Pass**: El dominio se considera auténtico.
* **Fail**: El dominio es falso y el mensaje se debe rechazar.
* **Fallo** leve: Es probable que el dominio sea falso, pero el mensaje no se debe rechazar únicamente en función de este resultado.
* **TempError**: Un error temporal detuvo la evaluación. El mensaje se puede rechazar.
* **PermError**: Los registros del SPF del dominio no son válidos.

Cabe señalar que el proceso para tener en cuenta los registros realizados al nivel de los servidores DNS puede tardar hasta 48 horas. Este retardo depende de la frecuencia con que se actualicen las cachés DNS de los servidores receptores.

## DKIM {#dkim}

La autenticación DKIM (DomainKeys Identified Mail) es un sucesor de SPF. Utiliza criptografía de clave pública que permite al servidor de correo electrónico receptor verificar que un mensaje fue enviado por la persona o entidad por la que afirma que fue enviado y si el contenido del mensaje se alteró entre el momento en que se envió originalmente (y &quot;firmado&quot; por DKIM) y la hora en que se recibió. Este estándar suele utilizar el dominio en el encabezado “De” o “Remitente”. 

DKIM surge a partir de una combinación de los principios de autenticación de DomainKeys, Yahoo! y Cisco Mail, y se utiliza para comprobar la autenticidad del dominio del remitente y garantizar la integridad del mensaje.

DKIM sustituye la autenticación por **DomainKeys**.

El uso de DKIM requiere algunos requisitos previos:

* **Seguridad**: El cifrado es un elemento clave del DKIM. Para garantizar el nivel de seguridad del DKIM, el tamaño de cifrado recomendado es de 1024b. La mayoría de los proveedores de acceso no consideran válidas las claves DKIM inferiores.
* **Reputación**: La reputación se basa en la dirección IP o en el dominio, pero el selector menos transparente de DKIM también es un elemento clave a tener en cuenta. La elección del selector es importante: evite mantener el &quot;predeterminado&quot; que podría utilizar cualquier persona y, por lo tanto, tiene una reputación débil. Debe implementar un selector diferente para las **retention vs. acquisition communications** y para la autenticación.

Obtenga más información sobre el requisito previo de DKIM al utilizar Campaign Classic en [esta sección](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Autenticación de mensajes, creación de informes y conformidad basados en dominio) es la forma más reciente de autenticación por correo electrónico y se basa en la autenticación SPF y DKIM para determinar si un correo electrónico pasa o falla. DMARC es única y potente de dos maneras importantes:

* Conformidad: permite al remitente indicar a los ISP qué hacer con cualquier mensaje que no se autentique (por ejemplo: no lo aceptes).
* Creación de informes: proporciona al remitente un informe detallado que muestra todos los mensajes en los que se ha producido un error en la autenticación DMARC, junto con el dominio “De” y la dirección IP utilizadas para cada uno. Esto permite a una empresa identificar el correo electrónico legítimo que falla en la autenticación y necesita algún tipo de &quot;corrección&quot; (por ejemplo, añadir direcciones IP a su registro SPF), así como las fuentes y la prevalencia de intentos de phishing en sus dominios de correo electrónico.

>[!NOTE]
>
>DMARC puede aprovechar los informes generados por [250ok](https://250ok.com/).
