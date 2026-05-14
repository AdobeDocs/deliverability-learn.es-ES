---
title: Implementar los indicadores de marca de Gmail para la identificación de mensajes (BIMI)
description: Aprenda a implementar BIMI
topics: Deliverability
role: Admin
level: Beginner
exl-id: f1c14b10-6191-4202-9825-23f948714f1e
TQID: https://experienceleague.adobe.com/gvO7rHqY-Dm6nUq9ssccY7Kt1xobV-pqLc26iITgmRA
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: e2290edd-b061-4880-9d79-dee306cf5aa9id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdbid: f82558ea-6af5-44eb-a424-5b3389abb0a3
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 1326
ht-degree: 9%

---

# Implementar [!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)

El propósito de este documento es proporcionar al lector más información sobre el método de autenticación de correo electrónico, DMARC. Al explicar cómo funciona DMARC y sus distintas opciones de directiva, los lectores entenderán mejor el impacto de DMARC en la capacidad de envío de correo electrónico.

## ¿Qué es DMARC? {#about}

Domain-based Message Authentication, Reporting and Conformance es un método de autenticación por correo electrónico que permite a los propietarios de dominio proteger su dominio contra el uso no autorizado. DMARC también proporciona comentarios sobre el estado de autenticación de correo electrónico y permite a los remitentes controlar qué sucede con los correos electrónicos que no se autentican correctamente. Esto incluye opciones para monitorizar, poner en cuarentena o rechazar correo según la política de DMARC que se haya implementado.

DMARC tiene tres opciones de directiva:

* **Supervisar (p=ninguno):** Indica al proveedor o ISP del buzón que haga lo que normalmente haría con el mensaje.
* **Cuarentena (p=cuarentena):** Indica al proveedor/ISP del buzón que debe enviar el correo que no pasa DMARC a la carpeta de correo no deseado del destinatario.
* **Rechazar (p=reject):** Indica al proveedor/ISP del buzón que bloquee el correo que no pasa DMARC, lo que provoca un rechazo.

## ¿Cómo funciona DMARC? {#how}

SPF y DKIM se utilizan para asociar un correo electrónico con un dominio y trabajar juntos para autenticar el correo electrónico. DMARC va más allá y ayuda a evitar la suplantación haciendo coincidir el dominio comprobado por DKIM y SPF. Para pasar DMARC, un mensaje debe pasar SPF o DKIM. Si ambas no se autentican correctamente, DMARC fallará y el correo electrónico se enviará según la directiva de DMARC seleccionada.

>[!NOTE]
>
>DMARC requiere la alineación entre las direcciones &quot;De&quot; y &quot;Return-Path&quot;.

## ¿Por qué debería implementarse DMARC? {#why}

DMARC es opcional y, aunque no es obligatoria, es gratuita y permite a los receptores de correo electrónico identificar fácilmente la autenticación de correos electrónicos, lo que podría mejorar la entrega. Una de las ventajas clave de DMARC es que ofrece informes sobre los mensajes que fallan en SPF o DKIM. También proporciona a los remitentes un grado de control sobre lo que sucede con el correo que no pasa ninguno de estos métodos de autenticación. A través de los informes de DMARC, los remitentes obtienen visibilidad sobre los mensajes que fallan en DMARC, lo que permite realizar pasos para mitigar más errores.

>[!NOTE]
>
>Si desea implementar BIMI, se requiere una directiva p=quarantine o p=reject de DMARC.

## Prácticas recomendadas para implementar DMARC {#best-practice}

Como DMARC es opcional, no se configura de forma predeterminada en ninguna plataforma de ESP. Debe crearse un registro DMARC en DNS para que su dominio funcione. Además, se requiere una dirección de correo electrónico de su elección para indicar a dónde deben ir los informes de DMARC dentro de su organización. Como práctica recomendada, lo es
se recomienda desplegar lentamente la implementación de DMARC escalando la política de DMARC de p=none, p=quarantine, a p=reject a medida que obtiene la comprensión de DMARC del impacto potencial de DMARC.

1. Analice los comentarios que recibe y utiliza (p=ninguno), lo que indica al destinatario que no realice ninguna acción contra los mensajes que no se autentican correctamente, pero que envíe informes de correo electrónico al remitente. Además, revise y corrija los problemas con SPF/DKIM si los mensajes legítimos fallan en la autenticación.
1. Determine si SPF y DKIM están alineados y pasa la autenticación para todo el correo electrónico legítimo y, a continuación, mueva la directiva a (p=quarantine), que indica al servidor de correo electrónico receptor que ponga en cuarentena el correo electrónico que falla en la autenticación (esto generalmente significa colocar esos mensajes en la carpeta de correo no deseado).
1. Ajustar directiva a (p=reject). La directiva p= rechazar indica al destinatario que deniegue (rechace) completamente cualquier correo electrónico del dominio que falle en la autenticación. Con esta directiva habilitada, solo el correo electrónico verificado como 100 % autenticado por el dominio tendrá la oportunidad de ser ubicado en la bandeja de entrada.

   >[!NOTE]
   >
   >Utilice esta directiva con precaución y determine si es apropiada para su organización.

## Informes de DMARC {#reporting}

DMARC ofrece la capacidad de recibir informes sobre los correos electrónicos que fallan en SPF/DKIM. Los proveedores de servicios de ISP generan dos informes diferentes como parte del proceso de autenticación que los remitentes pueden recibir a través de las etiquetas RUA/RUF en su directiva de DMARC:

* **Informes agregados (RUA):** No contiene ninguna PII (información de identificación personal) que pueda ser confidencial con respecto al RGPD.
* **Informes forenses (RUF):** Contiene direcciones de correo electrónico que distinguen entre RGPD. Antes de utilizar, es mejor comprobar internamente cómo tratar la información que necesita cumplir con el RGPD.

El uso principal de estos informes es recibir una descripción general de los correos electrónicos que se intentan suplantar. Se trata de informes muy técnicos que se digieren mejor con una herramienta de terceros. Algunas empresas especializadas en la monitorización de DMARC son:

* [ValueMail](https://www.valimail.com/products/#automated-delivery)
* [Agari](https://www.agari.com/)
* [Dmarciano](https://dmarcian.com/)
* [Proofpoint](https://www.proofpoint.com/us)

>[!CAUTION]
>
>Si las direcciones de correo electrónico que está añadiendo para recibir informes se encuentran fuera del dominio para el que se ha creado el registro DMARC, debe autorizar al dominio externo para especificar al DNS que es propietario de este dominio. Para ello, siga los pasos que se detallan en la sección [Documentación de dmarc.org](https://dmarc.org/2015/08/receiving-dmarc-reports-outside-your-domain)

### Ejemplo de registro de DMARC {#example}

```
v=DMARC1; p=reject; fo=1; rua=mailto:dmarc_rua@emaildefense.proofpoint.com;ruf=mailto:dmarc_ruf@emaildefense.proofpoint.co
```

## Etiquetas de DMARC y lo que hacen {#tags}

Los registros de DMARC tienen varios componentes denominados etiquetas de DMARC. Cada etiqueta tiene un valor que especifica un aspecto determinado de DMARC.

| Nombre de etiqueta | Obligatorio/Opcional | Función | Ejemplo | Valor predeterminado |
|  ---  |  ---  |  ---  |  ---  |  ---  |
| v | Requerido | Esta etiqueta de DMARC especifica la versión. De momento solo hay una versión, por lo que tendrá un valor fijo de v=DMARC1 | V=DMARC1 DMARC1 | DMARC1 |
| p | Requerido | Muestra la directiva de DMARC seleccionada y dirige al receptor a informar, poner en cuarentena o rechazar el correo que no supera las comprobaciones de autenticación. | p=ninguno, cuarentena o rechazo | - |
| fo | Opcional | Permite al propietario del dominio especificar las opciones de creación de informes. | 0: Generar informe si todo falla<br/>1: Generar informe si algo falla<br/>d: Generar informe si DKIM falla<br/>s: Generar informe si SPF falla | 1 (recomendado para informes de DMARC) |
| pct | Opcional | Indica el porcentaje de mensajes sujetos al filtrado. | pct=20 | 100 |
| rua | Opcional (recomendado) | Identifica dónde se enviarán los informes agregados. | `rua=mailto:aggrep@example.com` | - |
| tugurio | Opcional (recomendado) | Identifica dónde se enviarán los informes forenses. | `ruf=mailto:authfail@example.com` | - |
| sp | Opcional | Especifica la directiva de DMARC para los subdominios del dominio principal. | sp=reject | - |
| adkim | Opcional | Puede ser Estricto (s) o Relajado (r). La alineación relajada significa que el dominio utilizado en la firma de DKIM puede ser un subdominio de la dirección &quot;De&quot;. Alineación estricta significa que el dominio utilizado en la firma de DKIM debe coincidir exactamente con el dominio utilizado en la dirección de origen. | adkim=r | r |
| aspf | Opcional | Puede ser Estricto (s) o Relajado (r). La alineación relajada significa que el dominio ReturnPath puede ser un subdominio de la dirección remitente. La alineación estricta significa que el dominio Return-Path debe coincidir exactamente con la dirección From. | aspf=r | r |

## DMARC y ADOBE CAMPAIGN {#campaign}

>[!NOTE]
>
>Si la instancia de Campaign está alojada en AWS, puede implementar DMARC para los subdominios con el Panel de control de Campaign. [Obtenga información sobre cómo implementar registros de DMARC mediante el Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/txt-records/dmarc.html).

Un motivo común de los errores de DMARC es la falta de alineación entre las direcciones &quot;De&quot; y &quot;Errores a&quot; o &quot;Ruta de retorno&quot;. Para evitarlo, al configurar DMARC, se recomienda comprobar la configuración de las direcciones &quot;De&quot; y &quot;Errores a&quot; en las plantillas de envío.

1. En la plantilla de envío, revise qué dirección está configurada actualmente como dirección de origen.

   ![](../assets/dmarc1.png)

1. Desde aquí, seleccione &quot;Propiedades&quot; para poder editar más la plantilla de envíos. En esta ventana, seleccione SMTP y desmarque &quot;Usar la dirección de error predeterminada definida para la plataforma&quot; si está seleccionado. Plantillas de envío en Adobe Campaign: seleccione esta casilla de verificación de forma predeterminada. La dirección de error predeterminada puede no ser la dirección asociada con la dirección de origen en esta plantilla de envío.

   ![](../assets/dmarc2.png)

1. Cuando esta casilla está desactivada, aparece un campo de texto que permite introducir una dirección de error única que utiliza el mismo dominio que se ha definido en la dirección de origen.

   ![](../assets/dmarc3.png)

Una vez guardados estos cambios, podrá avanzar con la implementación de DMARC con la alineación de dominio correcta.

## Vínculos útiles {#links}

* [DMARC.org](https://dmarc.org/){target="_blank"}
* [Autenticación de correo electrónico M3AAWG](https://www.m3aawg.org/sites/default/files/document/M3AAWG_Email_Authentication_Update-2015.pdf){target="_blank"}
