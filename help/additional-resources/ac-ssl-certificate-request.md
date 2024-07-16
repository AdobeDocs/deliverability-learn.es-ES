---
title: Proceso de solicitud de certificado SSL
description: Obtenga información sobre cómo instalar certificados SSL en los subdominios delegados en Adobe.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 8a78abd3-afba-49a7-a2ae-8b2c75326749
source-git-commit: 57016f89df54d5c74755a6a108a92db45153ec18
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 1%

---

# Proceso de solicitud de certificado SSL

Una vez que haya delegado un dominio al Adobe para enviar correo electrónico (consulte [Configuración de nombres de dominio](/help/additional-resources/ac-domain-name-setup.md)), el Adobe creará y utilizará ciertos subdominios para funciones específicas.

Por ejemplo, si ha delegado *email.example.com* al Adobe para enviar correos electrónicos, el Adobe creará subdominios como los siguientes:
* *t.email.example.com* - para vínculos de seguimiento
* *m.email.example.com* - para páginas espejo
* *res.email.example.com* - para recursos hospedados (como imágenes)

Se recomienda **proteger estos dominios mediante SSL (HTTPS)**. De hecho, los vínculos no seguros (HTTP) son vulnerables a la interceptación y marcarán advertencias en los exploradores modernos.

Para instalar certificados SSL en estos subdominios, el proceso implica solicitar un archivo CSR y, posteriormente, comprar certificados SSL para su Adobe para instalarlos o renovarlos.

>[!CAUTION]
>
>Antes de instalar un certificado SSL, asegúrese de conocer los requisitos previos enumerados en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=es#installing-ssl-certificate).
>
>El Adobe solo admite certificados de hasta 2048 bits. Los certificados de 4096 bits aún no son compatibles.

## Glosario

| Término | Descripción |
|--- |--- |
| CA (autoridad de certificación) | Proveedor de certificados SSL que emite certificados digitales a organizaciones o personas después de comprobar su identidad, como DigiCert, Symantec, etc.<ul><li>Una CA de confianza suele considerarse como una CA de terceros que emite un certificado raíz.</li><li>Si el certificado lo firma la misma organización o empresa que lo utiliza, se clasifica como CA no confiable aunque sean certificados SSL, como los certificados autofirmados.</li></ul> |
| Certificado de cadena | Un certificado que incluye un certificado raíz y uno o más certificados intermedios se denomina certificado de cadena. |
| CSR (Solicitud de firma de certificado) | Bloque de texto codificado que se proporciona a una autoridad de certificación al solicitar un certificado SSL. Generalmente se genera en el servidor en el que está instalado el certificado. |
| DER (reglas de codificación distintivas) | Un tipo de extensión de certificado. La extensión .der se utiliza para certificados binarios codificados en DER. Estos archivos también pueden admitir la extensión .cer o .crt. |
| Certificado EV (validación extendida) | Un certificado EV es un nuevo tipo de certificado diseñado para evitar ataques de phishing. Requiere una validación extendida de su negocio y de la persona que solicita el certificado. |
| Certificado de alta garantía | La CA emite certificados de alta seguridad después de comprobar la propiedad del nombre de dominio y el registro empresarial válido. |
| CA intermedia | Una entidad emisora de certificados de certificados intermedios incluidos en un certificado de cadena. |
| Certificado intermedio | Una entidad emisora de certificados emite certificados en forma de estructura de árbol. El certificado raíz es el certificado superior del árbol. Cualquier certificado entre el certificado y el certificado raíz se denomina cadena o certificado intermedio. |
| Certificado de baja garantía | Un certificado de baja seguridad, también denominado certificado validado de dominio, incluye solo el nombre de dominio en el certificado (y no el nombre de empresa/organización). |
| PEM (correo mejorado de privacidad) | Certificado con una extensión .pem que contiene datos ASCII (Base64). Estos certificados comienzan con una línea &quot; - - - - - BEGIN CERTIFICATE - - - - -&quot;. |
| Certificado raíz | Una entidad emisora de certificados emite certificados en forma de estructura de árbol. El certificado raíz es el certificado superior del árbol. |
| SAN (nombre alternativo del sujeto) | Los nombres alternativos del asunto son nombres de host adicionales (sitios, direcciones IP, nombres comunes, etc.) que deben firmarse como parte de un único certificado SSL. |
| Certificado firmado automáticamente | Certificado firmado por la persona que lo crea en lugar de por una autoridad de certificación de confianza. Los certificados autofirmados pueden habilitar el mismo nivel de cifrado que un certificado firmado por una CA, pero existen dos inconvenientes principales:<ul><li>La conexión de un visitante podría ser secuestrada permitiendo que un atacante vea todos los datos enviados (con lo que se frustra el propósito de cifrar la conexión)</li><li> El certificado no se puede revocar como un certificado de confianza.</li></ul> |
| SSL (capa de sockets seguros) | La tecnología de seguridad estándar para establecer un vínculo cifrado entre un servidor web y un explorador. |
| Certificado comodín | Un certificado comodín puede proteger un número ilimitado de subdominios de primer nivel en un solo nombre de dominio, como *.adobe.com. |

## Pasos principales

1. Solicite un archivo de solicitud de firma de certificado (CSR) y proporcione la información necesaria (país, estado, ciudad, nombre de organización, nombre de unidad organizativa, etc.) al Adobe.
1. Valide el archivo CSR generado por el Adobe y compruebe que toda la información proporcionada es correcta.
1. Use los detalles de CSR para generar un certificado firmado por una entidad de certificación de confianza<!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. Valide el certificado SSL y compruebe que coincide con la CSR.
1. Proporcione el certificado SSL al Adobe, que lo instalará.
1. Compruebe que el certificado SSL esté instalado correctamente para cada subdominio protegido.
1. Supervise el período de validez del certificado SSL.
1. Actualice cualquier configuración específica en Adobe Campaign.

## Proceso detallado

### Requisitos previos

Debe identificar los nombres de dominio y las funciones (seguimiento, páginas espejo, aplicaciones web, etc.) para asegurar.
>[!NOTE]
>
>El Adobe puede ayudar a definir los nombres de dominio y las funciones que deben implicarse. Para obtener más información, póngase en contacto con el equipo de cuenta de Adobe.

### Paso 1: Obtención de un archivo CSR

Para obtener un archivo CSR (Solicitud de firma de certificado), siga los pasos a continuación.

* Si tiene acceso al [Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), siga las instrucciones de [esta página](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=es#subdomains-and-certificates) para generar y descargar un archivo CSR desde el Panel de control de Campaign.

* De lo contrario, cree un ticket de asistencia a través de https://adminconsole.adobe.com/ para obtener un archivo CSR del Servicio de atención al cliente de Adobe para los subdominios necesarios.

Estas son algunas prácticas recomendadas a seguir:

* Provocar una solicitud por subdominio delegado.
* Es posible combinar varios subdominios en una sola solicitud de CSR, pero solo dentro del mismo entorno. Por ejemplo, en Campaign Classic, el servidor de marketing, [servidor intermediario](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/mid-sourcing-server.html) y [instancia de ejecución](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/configuring-instances.html#execution-instance) son tres entornos independientes.
* Debe obtener un CSR nuevo antes de cualquier renovación de certificado SSL. No utilice un archivo CSR antiguo de hace un año o más.

Deberá proporcionar la siguiente información.

>[!CAUTION]
>
>Se deben rellenar todos los campos indicados en las tablas siguientes. De lo contrario, no se puede procesar la solicitud de CSR.

**Información que se proporcionará con la ayuda del equipo de Adobe:**

| Información que se debe proporcionar | Valor de ejemplo | Nota |
|--- |--- |--- |
| Nombre de cliente | My Company Inc. | Nombre de la organización. Este campo lo utiliza el Adobe para realizar el seguimiento de la solicitud (no formará parte del certificado CSR/SSL). |
| URL de entorno de Adobe Campaign | https://client-mid-prod1.campaign.adobe.com | URL de instancia de Adobe Campaign. |
| Nombre común [CN] | t.subdomain.customer.com | Puede ser cualquiera de los dominios relevantes, pero generalmente el dominio de seguimiento. |
| Nombre alternativo del sujeto [SAN] | t.subdomain.customer.com | Asegúrese de incluir el subdominio de seguimiento como una SAN. |
| Nombre alternativo del sujeto [SAN] | m.subdomain.customer.com |
| Nombre alternativo del sujeto [SAN] | res.subdomain.customer.com |

**Información que debe proporcionar su equipo interno de TI/SSL:**

| Información que se debe proporcionar | Valor de ejemplo | Nota |
|--- |--- |--- |
| País [C] | US | Debe ser un código de dos letras. Acceda a la lista completa de países [aquí](https://www.ssl.com/csrs/country_codes/).</br>*Nota: para el Reino Unido, use GB (no el Reino Unido).* |
| Estado (o nombre de provincia) [ST] | Illinois | Si procede. El valor debe ser un nombre completo, no abreviado. |
| Nombre de ciudad/localidad [L] | Chicago |
| Nombre De Organización [O] | ACME |
| Nombre de la unidad organizativa [OU] | IT |

>[!NOTE]
>
>Sustituya &quot;subdomain.customer.com&quot; por su subdominio delegado y los demás valores de ejemplo por los valores adecuados.

### Paso 2: Validación del archivo CSR

Después de enviar la solicitud con la información relevante, Adobe genera y le proporciona un archivo de solicitud de firma de certificado (CSR).

El texto del archivo CSR resultante debe comenzar con **&quot;-----BEGIN CERTIFICATE REQUEST-----&quot;**.

Una vez que reciba el archivo CSR desde el Adobe, siga los pasos a continuación:

1. Copie y pegue el texto del archivo CSR en un descodificador en línea como https://www.sslshopper.com/csr-decoder.html, <!--https://www.certlogik.com/decoder/,--> o https://www.entrust.net/ssl-technical/csr-viewer.cfm.
También puede usar el comando *OpenSSL* localmente en un equipo Linux.
1. Compruebe que todas las comprobaciones son correctas.
1. Compruebe que se incluyen los parámetros y nombres de dominio correctos.
1. Compruebe que todos los demás datos coinciden con los detalles que proporcionó al enviar la solicitud.

### Paso 3: Generación del certificado SSL

Una vez proporcionado el archivo CSR, debe adquirir y generar un certificado SSL para los dominios adecuados mediante el archivo CSR.

* El certificado SSL:
   * debe estar en formato Apache PEM;
   * no debe superar los 2048 bits;
   * debe estar firmado por una CA (entidad de certificación) válida;
   * debe incluir todas las SAN (nombres alternativos del sujeto) como se menciona en el archivo CSR.
* Si hay uno o más certificados intermedios, debe proporcionar el certificado raíz y todos los certificados intermedios al Adobe.
* Puede establecer cualquier período de validez del certificado, pero Adobe recomienda elegirlo el tiempo suficiente (por ejemplo, dos años).

>[!NOTE]
>
>Si utiliza sus propias herramientas internas o un portal proporcionado por una CA para solicitar el certificado, asegúrese de utilizar los mismos detalles que se proporcionan en la solicitud de CSR para evitar retrasos o discrepancias en el proceso de generación de certificados.

### Paso 4: Validación del certificado SSL

Una vez generado el certificado SSL, debe validarlo antes de enviarlo al Adobe. Para ello, siga los pasos a continuación:

1. Asegúrese de que el certificado tenga la extensión .pem. Si no es así, conviértala al formato PEM. Puede realizar la conversión con *OpenSSL*.
1. Confirme que el certificado comienza con **&quot;-----BEGIN CERTIFICATE-----&quot;**.
1. Copie el texto del certificado en un descodificador en línea, como https://www.sslshopper.com/certificate-decoder.html o https://www.entrust.net/ssl-technical/csr-viewer.cfm.
También puede usar el comando *OpenSSL* localmente en un equipo Linux. Para obtener más información, consulte [esta página externa](https://www.shellhacks.com/decode-ssl-certificate/).
1. Asegúrese de que el certificado se resuelve correctamente, incluidos el nombre común, la SAN, el emisor y el periodo de validez.
1. Si la verificación del certificado SSL se realiza correctamente, compruebe que el certificado coincida con la CSR usando [este sitio web](https://www.sslshopper.com/certificate-key-matcher.html): seleccione **Comprobar si una CSR y un certificado coinciden**, e introduzca el certificado y su CSR en los campos correspondientes. Deberían coincidir.

### Paso 5: Solicitud de la instalación del certificado SSL

* Si tiene acceso al [Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es), siga las instrucciones de [esta página](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=es#installing-ssl-certificate) para cargar el certificado en el Panel de control de Campaign.

* De lo contrario, cree otro ticket de asistencia a través de https://adminconsole.adobe.com/ para solicitar el Adobe para instalar el certificado en los servidores de Adobe.

Deberá proporcionar lo siguiente:

* El archivo de certificado, el certificado raíz y cualquier certificado intermedio (adjunto al ticket), preferiblemente en formato PEM de Apache.
* El número del ticket de soporte previo elevado para la CSR.
* Los mismos datos proporcionados para el vale CSR (incluidos el nombre común, la URL de instancia, el estado, la ciudad/localidad, el nombre de la organización, el nombre de la unidad organizativa, etc.).

### Paso 6: Prueba de la instalación del certificado SSL

Una vez que el certificado SSL esté instalado y confirmado por el Servicio de atención al cliente de Adobe, asegúrese de que se ha instalado correctamente para todas las direcciones URL.

Realice las siguientes pruebas antes de cerrar el ticket de instalación SSL. Asegúrese también de actualizar cualquier configuración específica como se indica en [esta sección](#update-configuration).

Vaya a las siguientes direcciones URL en el explorador (sustituya &quot;subdomain.customer.com&quot; por su subdominio):

* https://subdomain.customer.com/r/test (solo para [aplicaciones web](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/about-web-applications.html?lang=es) subdominios - no se aplica a los subdominios de correo electrónico)
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

Un resultado correcto proporciona información del entorno y la barra de direcciones de la dirección URL indica que la conexión es segura. Por ejemplo, puede ver el siguiente mensaje en Google Chrome:

![](../../help/assets/ssl-google-successful-result.png)

Si el certificado SSL no está instalado correctamente, se muestra la siguiente advertencia:

![](../../help/assets/ssl-google-unsuccessful-result.png)

### Paso 7: Comprobar el período de validez del certificado

Puede comprobar el periodo de validez del certificado en su explorador. Por ejemplo, en Google Chrome, haga clic en **Proteger** > **Certificado**.

Es su responsabilidad comprobar el periodo de validez. El Adobe recomienda implementar un proceso para monitorizar la caducidad del certificado. Obtenga más información sobre lo que sucede cuando su certificado SSL caduca en [este artículo](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

* Cree un ticket de asistencia para solicitar un certificado actualizado al menos dos semanas antes de la fecha de caducidad del certificado. No es necesario que solicite un CSR adicional, a menos que los detalles del CSR hayan cambiado.

* Si tiene acceso al [Panel de control de Campaign](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=es) y su entorno está hospedado por el Adobe en un entorno de AWS, puede usar el Panel de control de Campaign para renovar el certificado antes de que caduque. Obtenga más información en [esta sección](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates).

### Paso 8: Actualización de cualquier configuración específica {#update-configuration}

Una vez que esté seguro de que los certificados SSL solicitados están instalados correctamente, puede actualizar todas las referencias en Adobe Campaign de HTTP a HTTPS.

>[!NOTE]
>
>Para Campaign Classic, las direcciones URL que se van a actualizar se encuentran principalmente en [Asistente para la implementación](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) y en [Cuentas externas](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/accessing-external-database/external-accounts.html) (seguimiento, página espejo y dominios de recursos públicos). Para Campaign Standard, consulte [Configuración de marca](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

Una vez que se actualicen las configuraciones, los nuevos correos electrónicos se enviarán con direcciones URL HTTPS en lugar de HTTP. Para comprobar que las direcciones URL ahora son seguras, puede realizar rápidamente las siguientes pruebas:

* Cargue una imagen desde Adobe Campaign. Una vez cargada la imagen, la URL devuelta debe ser HTTPS.
* Cree un envío de correo electrónico de prueba que incluya un vínculo de página espejo, algunas imágenes, texto y un vínculo para darse de baja. Envíe el correo electrónico a un ID de correo electrónico externo (como su dirección de Gmail). Una vez recibido, abra el correo electrónico y asegúrese de que todos los vínculos dentro del correo electrónico se abran correctamente en su formulario HTTPS (no HTTP), sin advertencias ni errores de certificados SSL.

## Recursos específicos de los productos

**Campaign Classic**

* [Panel de control de Campaign: Agregar certificados SSL (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html). Obtenga información sobre cómo agregar certificados SSL para proteger los subdominios.

**Campaign Standard**

* [Panel de control de Campaign: Agregar certificados SSL (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html). Obtenga información sobre cómo agregar certificados SSL para proteger los subdominios.
