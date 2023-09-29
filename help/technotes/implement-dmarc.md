---
title: Implementar los indicadores de marca de Gmail para la identificación de mensajes (BIMI)
description: Aprenda a implementar BIMI
topics: Deliverability
role: Admin
level: Beginner
source-git-commit: 5ac5bc90b5a9bf3ce9b390821476c7222983b818
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---

# Implementación [!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)

El propósito de este documento es proporcionar al lector más información sobre el método de autenticación por correo electrónico, DMARC. Al explicar cómo funciona DMARC y sus diversas opciones de política, los lectores entenderán mejor el impacto de DMARC en la capacidad de envío de correo electrónico.

## ¿Qué es DMARC? {#about}

Autenticación de mensajes, creación de informes y conformidad basados en dominio es un método de autenticación por correo electrónico que permite a los propietarios de dominio proteger su dominio contra el uso no autorizado. DMARC también proporciona comentarios sobre el estado de autenticación de correo electrónico y permite a los remitentes controlar qué sucede con los correos electrónicos que no se autentican correctamente. Esto incluye opciones para monitorizar, poner en cuarentena o rechazar correo según la política DMARC que se haya implementado.

DMARC tiene tres opciones de directiva:

* **Monitor (p=ninguno):** Indica al proveedor del buzón/ISP que haga lo que normalmente haría al mensaje.
* **Cuarentena (p=cuarentena):** Indica al proveedor/ISP del buzón que envíe el correo que no pasa DMARC a la carpeta de correo no deseado o correo no deseado del destinatario.
* **Rechazar (p=rechazar):** Indica al proveedor/ISP del buzón que bloquee el correo que no pasa DMARC, lo que provoca un rechazo.

## ¿Cómo funciona DMARC? {#how}

SPF y DKIM se utilizan para asociar un correo electrónico con un dominio y trabajar juntos para autenticar el correo electrónico. DMARC lleva esto un paso más allá y ayuda a evitar la suplantación haciendo coincidir el Dominio comprobado por DKIM y SPF. Para pasar DMARC, un mensaje debe pasar SPF o DKIM. Si ambas fallan en la autenticación, DMARC fallará y el correo electrónico se enviará según la política DMARC seleccionada.

>[!NOTE]
>
>DMARC requiere la alineación entre las direcciones &quot;De&quot; y &quot;Return-Path&quot;.

## ¿Por qué debería implementarse DMARC? {#why}

DMARC es opcional y, aunque no es obligatoria, es gratuita y permite a los receptores de correo electrónico identificar fácilmente la autenticación de correos electrónicos, lo que podría mejorar potencialmente la entrega. Una de las ventajas clave de DMARC es que ofrece informes sobre los mensajes que no superan SPF o DKIM. También proporciona a los remitentes un grado de control sobre lo que sucede con el correo que no pasa ninguno de estos métodos de autenticación. A través de los informes DMARC, los remitentes obtienen visibilidad sobre qué mensajes fallan en DMARC, lo que permite tomar medidas para mitigar más errores.

>[!NOTE]
>
>Si desea implementar BIMI, se requiere una política p=quarantine o p=reject DMARC.

## Prácticas recomendadas para implementar DMARC {#best-practice}

Como DMARC es opcional, no se configurará de forma predeterminada en ninguna plataforma de ESP. Debe crearse un registro DMARC en DNS para que su dominio funcione. Además, se requiere una dirección de correo electrónico de su elección para indicar a dónde deben ir los informes DMARC dentro de su organización. Como práctica recomendada, se recomienda implementar lentamente la implementación de DMARC escalando la política de DMARC de p=none, p=quarantine, p=reject a medida que se obtiene la comprensión de DMARC del impacto potencial de DMARC.

1. Analice los comentarios que recibe y utiliza (p=ninguno), lo que indica al destinatario que no realice ninguna acción contra los mensajes que no se autentican correctamente, pero que envíe informes de correo electrónico al remitente. Además, revise y corrija los problemas con SPF/DKIM si los mensajes legítimos fallan en la autenticación.
1. Determine si SPF y DKIM están alineados y pasa la autenticación para todo el correo electrónico legítimo y, a continuación, mueva la directiva a (p=quarantine), que indica al servidor de correo electrónico receptor que ponga en cuarentena el correo electrónico que falla en la autenticación (esto generalmente significa colocar esos mensajes en la carpeta de correo no deseado).
1. Ajustar directiva a (p=reject). La directiva p= reject indica al destinatario que deniegue (devuelva) completamente cualquier correo electrónico del dominio que falle en la autenticación. Con esta directiva habilitada, solo los correos electrónicos verificados como 100 % autenticados por el dominio tendrán la oportunidad de colocar la bandeja de entrada.

   >[!NOTE]
   >
   >Utilice esta directiva con precaución y determine si es apropiada para su organización.

## Informes DMARC {#reporting}

DMARC ofrece la capacidad de recibir informes sobre correos electrónicos que fallan en SPF/DKIM. Existen dos informes diferentes generados por los proveedores de servicios de Internet como parte del proceso de autenticación que los remitentes pueden recibir a través de las etiquetas RUA/RUF en su política DMARC:

* **Informes agregados (RUA):** No contiene ninguna PII (información de identificación personal) que sea sensible al RGPD.
* **Informes forenses (RUF):** Contiene direcciones de correo electrónico que son confidenciales para el RGPD. Antes de utilizar, es mejor comprobar internamente cómo tratar la información que necesita cumplir con el RGPD.

El uso principal de estos informes es recibir una descripción general de los correos electrónicos que se intentan suplantar. Se trata de informes muy técnicos que se digieren mejor con una herramienta de terceros. Algunas empresas especializadas en la monitorización de DMARC son:

* [ValueMail](https://www.valimail.com/products/#automated-delivery)
* [Agari](https://www.agari.com/)
* [Dmarciano](https://dmarcian.com/)
* [Proofpoint](https://www.proofpoint.com/us)

### Ejemplo de registro DMARC {#example}

```
v=DMARC1; p=reject; fo=1; rua=mailto:dmarc_rua@emaildefense.proofpoint.com;ruf=mailto:dmarc_ruf@emaildefense.proofpoint.co
```

## Etiquetas DMARC y lo que hacen {#tags}

Los registros DMARC tienen varios componentes llamados etiquetas DMARC. Cada etiqueta tiene un valor que especifica un determinado aspecto de DMARC.

| Nombre de etiqueta | Obligatorio/Opcional | Función | Ejemplo | Valor predeterminado |
|  ---  |  ---  |  ---  |  ---  |  ---  |
| Versión  | Requerido | Esta etiqueta DMARC especifica la versión. De momento, solo hay una versión, por lo que tendrá un valor fijo de v=DMARC1 | V=DMARC1 DMARC1 | DMARC1 |
| p | Requerido | Muestra la directiva DMARC seleccionada y dirige al receptor a informar, poner en cuarentena o rechazar correo que no supere las comprobaciones de autenticación. | p=ninguno, cuarentena o rechazo | - |
| fo | Opcional | Permite al propietario del dominio especificar las opciones de creación de informes. | 0: Generar informe si falla todo<br/>1: Generar un informe si algo falla<br/>d: Generar informe si falla DKIM<br/>s: Generar informe si falla el SPF | 1 (recomendado para informes DMARC) |
| pct | Opcional | Indica el porcentaje de mensajes sujetos al filtrado. | pct=20 | 100 |
| rua | Opcional (recomendado) | Identifica dónde se enviarán los informes agregados. | `rua=mailto:aggrep@example.com` | - |
| tugurio | Opcional (recomendado) | Identifica dónde se enviarán los informes forenses. | `ruf=mailto:authfail@example.com` | - |
| sp | Opcional | Especifica la directiva DMARC para los subdominios del dominio principal. | sp=reject | - |
| adkim | Opcional | Puede ser Estricto (s) o Relajado (r). La alineación relajada significa que el dominio utilizado en la firma DKIM puede ser un subdominio de la dirección &quot;Desde&quot;. Alineación estricta significa que el dominio utilizado en la firma DKIM debe coincidir exactamente con el dominio utilizado en la dirección de origen. | adkim=r | r |
| aspf | Opcional | Puede ser Estricto (s) o Relajado (r). La alineación relajada significa que el dominio ReturnPath puede ser un subdominio de la dirección remitente. La alineación estricta significa que el dominio Return-Path debe coincidir exactamente con la dirección From. | aspf=r | r |

## DMARC y ADOBE CAMPAIGN {#campaign}

Un motivo común de los errores de DMARC es la falta de alineación entre las direcciones &quot;De&quot; y &quot;Errores de destino&quot; o &quot;Ruta de retorno&quot;. Para evitarlo, al configurar DMARC, se recomienda comprobar dos veces la configuración de las direcciones &quot;De&quot; y &quot;Errores a&quot; en las plantillas de envío.

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
