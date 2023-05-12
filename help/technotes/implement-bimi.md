---
title: Implementar los indicadores de marca de Gmail para la identificación de mensajes (BIMI)
description: Aprenda a implementar BIMI
topics: Deliverability
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: 05f6cd331f4e610e2442d43405333823644d349e
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 0%

---

# Implementación [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) es un estándar del sector que permite que aparezca un logotipo aprobado junto al correo electrónico de un remitente en las plataformas participantes.

Con este estándar, una marca puede determinar un logotipo que debe mostrarse en las bandejas de entrada de los proveedores de buzones de correo. Una vez publicado en un registro denominado BIMI DNS (Sistema de nombres de dominio), un proveedor de buzones de correo puede seleccionar este logotipo y mostrarlo en la bandeja de entrada si se cumplen determinados criterios.

Los diferentes proveedores realizan implementaciones diferentes, pero las ventajas son claras: destacando en la bandeja de entrada, creando confianza y controlando lo que se está mostrando.

BIMI no mejora directamente la capacidad de envío o su reputación. Aunque puede ayudar a crear más confianza con los destinatarios y, por lo tanto, impulsar más participación.

## ¿Cómo se ve?

Puede encontrar algunos ejemplos de implementaciones de diferentes proveedores y más detalles sobre los proveedores que sí muestran el logotipo en el [Página del Grupo BIMI](https://bimigroup.org/where-is-my-bimi-logo-displayed/).

## ¿Quién es el grupo BIMI?

El grupo BIMI es un grupo de trabajo que desarrolla BIMI, ya que no sólo cubre el logotipo sino también los requisitos técnicos, legales y de cumplimiento.

El Grupo BIMI está integrado por varias partes interesadas de diferentes sectores del sector: Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail y Validez.

## ¿Quién apoya a BIMI?

La lista de proveedores de buzones de correo que admiten BIMI está creciendo de manera constante. Se puede encontrar una lista actualizada [here](https://bimigroup.org/bimi-infographic/) tanto para los proveedores de soporte como para los proveedores que consideran BIMI.

Desde abril de 2023, la lista incluye Gmail, Yahoo, La Poste, Fastmail, Onet.pl y Zone, Proofpoint como dispositivo antispam y Apple Mail (a partir de iOS 16).

Los nombres más destacados en esa lista son obviamente Yahoo, Gmail y uno de los usuarios recientes: Apple con iOS 16. Apple desempeña un papel especial en la combinación ya que no es un proveedor de buzones de correo, pero sí que agregó compatibilidad con BIMI a su aplicación de correo nativa. El correo que cumpla con BIMI se mostrará como &quot;correo electrónico certificado digitalmente&quot;, lo que aumenta la confianza en la marca.

## Implementación

La implementación de BIMI viene en varios pasos:

1. Implementación de DMARC (Autenticación de mensajes, informes y conformidad basados en dominio) en el nivel de aplicación tanto para el dominio de envío como para su dominio organizativo: [Más información](#dmarc)

1. Creación del logotipo de su marca en el formato SVG TinyPS - [Más información](#create-brand-logo)

1. Registro para un certificado de marca verificada (solo necesario para algunos proveedores) - [Más información](#vmc)

1. Publicar un registro DNS de BIMI con el logotipo y el certificado - [Más información](#publish-bimi-record)

1. Tener una buena reputación - [Más información](#good-reputation)

>[!NOTE]
>
>Tenga en cuenta que es necesario desactivar todos los pasos.


### DMARC {#dmarc}

DMARC es un estándar que permite a la marca decidir qué debe hacer un proveedor de buzones de correo con un correo electrónico que falla [autenticación](../additional-resources/authentication.md). Las llamadas políticas van desde &quot;ninguno&quot; a &quot;cuarentena&quot; (ubicación de la carpeta de correo no deseado) a &quot;rechazar&quot; (bloqueo directo del correo). Sólo las dos últimas políticas se denominan &quot;cumplimiento&quot; y cumplen los requisitos para el BIMI. El correo enviado por el Adobe pasa la autenticación, ya que SPF (Entorno de políticas del remitente) y DKIM (Correo identificado de claves de dominio) están configurados de forma predeterminada. Adobe está configurando DMARC en su dominio de envío si se solicita.

Además de DMARC en el dominio de envío, DMARC también debe emplearse a nivel de aplicación para el dominio organizativo (si el dominio de envío es news.example.com, example.com es el dominio organizativo).

### Creación del logotipo de su marca {#create-brand-logo}

La creación del logotipo debe seguir los requisitos al 100%. Consulte siempre la [Directrices del Grupo BIMI](https://bimigroup.org/creating-bimi-svg-logo-files/).

Además de los requisitos técnicos, hay algunas recomendaciones prácticas como tener un logotipo cuadrado, con un color sólido como fondo y otras. Estas recomendaciones son para una mejor visualización.
Tenga en cuenta que el incumplimiento puede llevar a que el logotipo no se muestre.

### Certificado de marca verificada (VMC) {#vmc}

Un certificado de marca verificada (VMC) solo es necesario para algunos proveedores de buzones de correo como Gmail y Apple, y por lo tanto es opcional. Aunque recomendamos obtener un VMC para aprovechar realmente BIMI.

Un certificado de marca verificada es una validación legal de que la marca puede utilizar el logotipo. Una entidad certificadora comprobará esto a través de la oficina de marcas donde esté registrado el logotipo de la marca. Este proceso implica varias validaciones y comprobaciones legales, y puede tardar algún tiempo. Actualmente dos entidades emisoras de certificados (autoridades de certificación) emiten MVC: Digicert y Entrust. El primer conjunto de oficinas de marca son Estados Unidos, Canadá, UE, Reino Unido, Alemania, Japón, Australia y España.

Como regla general, necesitará un VMC por logotipo. Tener un VMC para su dominio organizativo cubrirá subdominios, y con una característica añadida, incluso dominios diferentes. Si tiene diferentes logotipos, se necesita más de un VMC. La entidad emisora de certificados o el socio con el que elija trabajar le ayudará a configurarla.

>[!NOTE]
>
>Tenga en cuenta que las MVC tienen una tarifa anual.

### Publicación del registro BIMI {#publish-bimi-record}

Una vez que se hayan realizado los otros pasos, se puede publicar el registro DNS de BIMI. El registro tiene este aspecto:

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;URL de PEM&quot; es la ubicación de archivo del certificado de marca verificada.

Para el dominio de envío, esto debe hacerse por Adobe.

### Buena reputación {#good-reputation}

La confianza es clave para BIMI. El usuario confía en que su proveedor de buzones de correo solo mostrará el logotipo de los remitentes legítimos, por lo que el proveedor de buzones de correo debe confiar en la marca y esto lo está haciendo la reputación del remitente. Si tienes una buena reputación, todo es bueno, pero si no lo eres, el logotipo no se mostrará. Desafortunadamente, no hay información o métrica que podamos ver para averiguar si la reputación es lo suficientemente alta.

Ni siquiera pasar por el esfuerzo y los gastos para una MVC se quita esta parte. Si el proveedor de buzones de correo no confía en la marca, no se mostrará el logotipo.

## Pestaña Sugerencias y trucos

* El grupo BIMI ofrece una útil herramienta de validación para BIMI. Si desea comprobar si todo está configurado y listo, o si solo desea ver si el logotipo es compatible, vaya a [este vínculo](https://bimigroup.org/bimi-generator/). Para esto último, haga clic en **[!UICONTROL Generate BIMI]** e introduzca un dominio de marcador de posición, pero la dirección URL del logotipo correcta. El inspector le indicará si el logotipo es compatible.

* Puede empezar sin un MVC con seguridad, no hay daño en su reputación si su registro BIMI no incluye una URL de MVC, pero el logotipo ya se puede mostrar en Yahoo.

* La implementación de la DMARC a nivel organizativo es una gran empresa. Algunas empresas están especializadas para ayudar a las marcas a lograr la adopción completa de DMARC.

* Se publica una extensa lista de preguntas más frecuentes [here](https://bimigroup.org/faqs-for-senders-esps/).
