---
title: Implementar los indicadores de marca de Gmail para la identificación de mensajes (BIMI)
description: Aprenda a implementar BIMI
topics: Deliverability
role: Admin
level: Beginner
jira: KT-14079
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: ad0646da88f2b1474e74b6c741d0dd5701e88978
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 0%

---

# Implementación [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) es un estándar del sector que permite que aparezca un logotipo aprobado junto al correo electrónico de un remitente en las plataformas participantes.

Con este estándar, una marca puede determinar un logotipo que debe mostrarse en las bandejas de entrada de los proveedores de buzones de correo. Una vez publicado en un registro llamado BIMI DNS (Sistema de Nombres de Dominio), un proveedor de buzones de correo podría recoger este logotipo y mostrarlo en la bandeja de entrada si se cumplen ciertos criterios.

Los distintos proveedores hacen implementaciones diferentes, pero las ventajas son claras: destacar en la bandeja de entrada, generar confianza y tener el control de lo que se muestra.

BIMI no mejora directamente la capacidad de envío ni su reputación. Puede ayudar a generar más confianza en sus destinatarios y, por lo tanto, impulsar una mayor participación.

## ¿Cómo se ve?

Puede encontrar algunos ejemplos de implementaciones de diferentes proveedores y más detalles sobre qué proveedores muestran el logotipo en la [Página del Grupo BIMI](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## ¿Quién es el Grupo BIMI?

El grupo BIMI es un grupo de trabajo que desarrolla BIMI, ya que no solo cubre el logotipo, sino también los requisitos técnicos, legales y de cumplimiento.

El Grupo BIMI está formado por varios grupos de interés de diferentes áreas de la industria: Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail y Validity.

## ¿Quién apoya a BIMI?

La lista de proveedores de buzones de correo que admiten BIMI está creciendo de manera constante. Se puede encontrar una lista actualizada [aquí](https://bimigroup.org/bimi-infographic/){target="_blank"} tanto para los proveedores de apoyo como para los proveedores que consideran BIMI.

A partir de abril de 2023, la lista incluye Gmail, Yahoo, La Poste, Fastmail, Onet.pl y Zone, Proofpoint como dispositivo antispam y Apple Mail (a partir de iOS 16).

Los nombres más destacados en esa lista son, obviamente, Yahoo, Gmail y uno de los que la adoptaron recientemente: Apple con iOS 16. Apple tiene un papel especial en la mezcla, ya que no son un proveedor de buzones de correo, pero sí agregaron compatibilidad con BIMI a su aplicación de correo nativa. El correo que cumpla con BIMI se mostrará como &quot;correo electrónico certificado digitalmente&quot;, lo que aumenta la confianza en la marca.

## Implementación

La implementación de BIMI viene en varios pasos:

1. Implementación de DMARC (Autenticación de mensajes, creación de informes y conformidad basados en dominio) en el nivel de aplicación tanto para el dominio de envío como para su dominio organizativo: [Más información](#dmarc)

1. Creación del logotipo de su marca en el formato SVG TinyPS - [Más información](#create-brand-logo)

1. Suscribirse a un certificado de marca verificada (solo es necesario para algunos proveedores) - [Más información](#vmc)

1. Publicación de un registro DNS BIMI con el logotipo y el certificado - [Más información](#publish-bimi-record)

1. Tener una buena reputación - [Más información](#good-reputation)

>[!NOTE]
>
>Tenga en cuenta que todos los pasos deben marcarse.


### DMARC {#dmarc}

DMARC es un estándar que permite a la marca decidir qué debe hacer un proveedor de buzones de correo con un correo electrónico que falla [authentication](../additional-resources/authentication.md). Las llamadas políticas van desde &quot;ninguno&quot; sobre &quot;cuarentena&quot; (ubicación de carpetas de spam) a &quot;rechazado&quot; (bloqueo directo del correo). Solo estas dos últimas políticas se denominan &quot;cumplimiento&quot; y cumplen los requisitos para BIMI. El correo enviado por Adobe pasa la autenticación, ya que SPF (Marco de políticas del remitente) y DKIM (Correo identificado por claves de dominio) están configurados de forma predeterminada. El Adobe está configurando DMARC en su dominio de envío si se solicita.

Además de DMARC en el dominio de envío, DMARC también debe emplearse en el nivel de aplicación para el dominio organizativo (si el dominio de envío es news.example.com, example.com es el dominio organizativo).

### Creación del logotipo de su marca {#create-brand-logo}

La creación del logotipo debe seguir los requisitos al 100%. Consulte siempre la [Directrices del Grupo BIMI](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

El logotipo debe almacenarse en una ubicación segura (HTTPS), en caso de que se utilice una red de distribución de contenido (CDN), debe desactivarse cualquier protección que impida que los proveedores de buzones de correo obtengan el logotipo (por ejemplo, protección de bots).

Además de los requisitos técnicos, hay algunas recomendaciones prácticas como tener un logotipo cuadrado, tener un color sólido como fondo y otros. Estas recomendaciones sirven para una mejor visualización. Algunos proveedores tienen sus propios requisitos, que son adicionales a los del grupo de trabajo BIMI. [Gmail](https://support.google.com/a/answer/10911027?sjid=903725605955621707-EU){target="_blank"}. por ejemplo, requiere que el logotipo tenga al menos 96 x 96 píxeles.
Tenga en cuenta que el incumplimiento puede hacer que no se muestre el logotipo.

### Certificado de marca verificada (VMC) {#vmc}

Solo se necesita un certificado de marca verificada (VMC) para algunos proveedores de buzones de correo como Gmail y Apple, y por lo tanto es opcional. Sin embargo, recomendamos conseguir una VMC para aprovechar realmente BIMI.

Un certificado de marca verificada es una validación legal de que la marca puede utilizar el logotipo. Una entidad emisora de certificados comprobará esto a través de la oficina de marcas comerciales donde está registrado el logotipo de la marca. Este proceso incluye varias validaciones y comprobaciones legales y puede tardar algún tiempo. Actualmente, dos CA (autoridades de certificación) están emitiendo CMV: Digicert y Entrust. El primer conjunto de oficinas de marcas comerciales son EE. UU., Canadá, UE, Reino Unido, Alemania, Japón, Australia y España.

Como regla general, necesitará un VMC por logotipo. Tener una VMC para su dominio organizativo cubrirá subdominios y, con una función añadida, incluso dominios diferentes. En caso de que tenga distintos logotipos, se necesita más de un VMC. La entidad de certificación o el socio con el que elija trabajar le ayudará a configurarlo.

>[!NOTE]
>
>Tenga en cuenta que los VMC tienen una tarifa anual.

### Publicación del registro BIMI {#publish-bimi-record}

Una vez completados los demás pasos, se puede publicar el registro DNS BIMI. El registro tiene este aspecto:

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;PEM URL&quot; es la ubicación de archivo del certificado de marca verificada.

Para el dominio de envío, esto debe hacerse por Adobe.

### Buena reputación {#good-reputation}

La confianza es clave para BIMI. El usuario confía en que su proveedor de buzones solo mostrará el logotipo de los remitentes legítimos, por lo que el proveedor de buzones debe confiar en la marca, y esto lo hace su reputación de remitente. Si tiene una alta reputación, todo es bueno, pero si no lo es, el logotipo no se mostrará. Desafortunadamente, no hay información o métrica que podamos mirar para averiguar si la reputación es lo suficientemente alta.

Incluso pasar por el esfuerzo y los gastos de un VMC no quita esta parte. Si el proveedor del buzón no confía en la marca, no se mostrará el logotipo.

## Pestaña Sugerencias y trucos

* El Grupo BIMI ofrece una práctica herramienta de validación para BIMI. Si desea comprobar si todo está configurado y listo, o solo desea ver si el logotipo es compatible, vaya a [este vínculo](https://bimigroup.org/bimi-generator/){target="_blank"}. Para esto último, haga clic en **[!UICONTROL Generate BIMI]** e introduzca un dominio de marcador de posición, pero la dirección URL del logotipo correcta. El inspector le dirá si el logotipo es compatible.

* Puede comenzar con seguridad sin un VMC, no hay daño en su reputación si su registro BIMI no incluye una URL de VMC, pero el logotipo ya se puede mostrar en Yahoo.

* La implementación de DMARC a nivel organizativo es una empresa grande. Algunas empresas están especializadas en ayudar a las marcas a lograr una adopción completa de DMARC.

* Se publica una extensa lista de preguntas más frecuentes [aquí](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
