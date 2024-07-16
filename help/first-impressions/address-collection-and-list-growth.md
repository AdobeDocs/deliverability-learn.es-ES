---
title: Recopilación de direcciones y aumento de listas
description: Descubra cuáles son las mejores fuentes para las nuevas direcciones de correo electrónico, cómo garantizar una alta calidad de los datos y la alineación con las directrices legales.
topics: Deliverability
jira: KT-7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
exl-id: 350950dc-4703-402a-8e22-3862f4e21d52
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '1594'
ht-degree: 3%

---

# Recopilación de direcciones y aumento de listas

Las mejores fuentes de las nuevas direcciones de correo electrónico son las fuentes directas, como los registros en el sitio web o en las tiendas físicas. En estas situaciones, puede controlar la experiencia para asegurarse de que es positiva y de que el suscriptor está interesado en recibir correo electrónico de su marca.

Algunas notas sobre estos métodos de registro:

La colección de listas **Almacenamiento físico** puede presentar desafíos debido a entradas de direcciones verbales o escritas que causan errores ortográficos en las direcciones. Se recomienda enviar un correo electrónico de confirmación lo antes posible después de los registros en la tienda.

La forma más común de **registro en un sitio web** es la &quot;inclusión única&quot;. Es el estándar mínimo absoluto que debe utilizar para adquirir direcciones de correo electrónico. La inclusión única se produce cuando el titular de una dirección de correo electrónico específica concede a un remitente permiso para enviarle correos electrónicos de marketing, normalmente enviando la dirección a través de un formulario web o suscripciones en la tienda. Aunque es posible ejecutar una campaña de correo electrónico correcta mediante este método, puede ser la causa de algunos problemas.

* Las direcciones de correo electrónico no confirmadas pueden tener errores tipográficos o estar mal formadas, ser incorrectas o utilizarse de forma malintencionada. Los errores de escritura y las direcciones mal formadas causan altas tasas de devolución, lo que puede provocar y provoca bloqueos emitidos por los ISP o pérdida de reputación de IP.

* El envío malicioso de trampas de correo no deseado conocidas (a veces denominadas &quot;envenenamiento de listas&quot;) puede causar enormes problemas con la entrega y la reputación si el propietario de esa trampa toma medidas. Es imposible saber si el destinatario realmente desea que se le añada a una lista de marketing sin una confirmación. Esto hace que sea igualmente imposible establecer las expectativas del destinatario y puede provocar un aumento de las quejas de correo no deseado, y a veces una inclusión en la lista de bloqueados si el correo electrónico recopilado resulta ser una trampa de correo no deseado.

Para obtener instrucciones sobre cómo minimizar los problemas presentados en el almacenamiento físico y en la opción de inclusión única, vaya a la sección [Calidad de los datos e higiene](#data-quality-and-hygiene) de esta guía para ver los detalles y las ventajas de la opción de inclusión doble.

>[!NOTE]
>
>Los suscriptores suelen utilizar direcciones de desecho, direcciones caducadas o direcciones que no son suyas para obtener lo que desean de un sitio web, pero también para evitar que se les añada a las listas de marketing. Cuando esto sucede, las listas de especialistas en marketing generan un número elevado de rechazos graves, tasas de quejas de spam elevadas y suscriptores que no hacen clic, abren ni interactúan de forma positiva con los correos electrónicos. Se puede ver como una marca roja para los proveedores de buzones de correo y los ISP.

## Formularios de registro

Además de añadir los campos para los datos que desea recopilar sobre sus nuevos suscriptores, hay otras cosas que debe hacer con el formulario de registro en el sitio web.

* Establezca expectativas claras con el suscriptor en cuanto a que está de acuerdo en recibir correos electrónicos, lo que recibirá y la frecuencia con la que lo recibirá.
* Agregue opciones que permitan al suscriptor seleccionar la frecuencia o el tipo de comunicaciones que recibe. Estas opciones le permiten conocer las preferencias del suscriptor desde el principio para que pueda proporcionar la mejor experiencia posible a su nuevo cliente.
* Equilibre el riesgo de perder el interés del suscriptor durante el proceso de registro solicitando la mayor cantidad de información posible. Las cosas como su cumpleaños, ubicación o intereses le ayudan a enviar contenido más personalizado. Los suscriptores de cada marca tienen diferentes expectativas y umbrales de tolerancia, por lo que las pruebas son clave para encontrar el equilibrio adecuado para su situación.

>[!NOTE]
>
> No utilice casillas premarcadas durante el proceso de registro. Aunque puede meterle en problemas legalmente, también es una experiencia negativa para el cliente.

## Calidad e higiene de los datos

La recopilación de datos es solo parte del desafío. También debe asegurarse de que los datos sean precisos y se puedan utilizar. Debe disponer de filtros de formato básicos. Una dirección de correo electrónico no es válida si no incluye &quot;@&quot; o &quot;&quot;. por ejemplo. Asegúrese de no permitir direcciones de alias comunes, que también se denominan cuentas de funciones (como &quot;información&quot;, &quot;administrador&quot;, &quot;ventas&quot;, &quot;asistencia&quot;, etc.). Las cuentas de funciones pueden presentar riesgos porque, por su naturaleza, el destinatario contiene un grupo de personas en lugar de un único suscriptor. Las expectativas y la tolerancia pueden variar dentro de un grupo, lo que conlleva el riesgo de quejas, participación variable, cancelaciones de suscripción y confusión general.

Estas son algunas soluciones a problemas comunes que puede encontrar con los datos de su dirección de correo electrónico:

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] está considerada como la mejor práctica de envío por la mayoría de los expertos en correo electrónico. Si tiene problemas con trampas de correo no deseado o quejas en sus correos electrónicos de bienvenida, el DOI es una buena manera de asegurarse de que el suscriptor que recibe sus correos electrónicos se haya registrado en su programa de correo electrónico y desee recibir sus correos electrónicos.

El DOI consiste en enviar un correo electrónico de confirmación a la dirección de correo electrónico del suscriptor que se ha suscrito a su programa de correo electrónico, que contiene un vínculo en el que se debe hacer clic para confirmar el consentimiento. Con este método de adquisición, si el suscriptor no confirma, el remitente no le enviará más correos electrónicos. Informe a los nuevos suscriptores de que está haciendo esto en el sitio web, animándolos a completar la suscripción antes de continuar. Este método sí observa una reducción en el número de inscripciones, pero las personas que sí se inscriben tienden a estar muy comprometidas y a permanecer a largo plazo. Generalmente resulta en un retorno de la inversión mucho mayor para el remitente.

**Campo oculto**
La aplicación de un campo oculto en el formulario de registro es una buena manera de diferenciar los registros de bots automatizados de los suscriptores humanos reales. Dado que el campo de datos no está visible ni oculto en el código del HTML, un bot introducirá datos en los que un humano no lo haría. Con este método, puede generar reglas para suprimir cualquier registro que incluya datos rellenados en ese campo oculto.

**[!DNL re-CAPTCHA] es un método de validación que puede utilizar para reducir las posibilidades de que el suscriptor sea un bot y no una persona real. Existen varias versiones, algunas de las cuales contienen identificación de palabras clave o imágenes. Algunas versiones son más efectivas que otras y lo que se obtiene en seguridad y prevención de problemas de capacidad de entrega es mucho más alto que cualquier impacto negativo en las conversiones.

## Directrices legales

Consulte a sus abogados para interpretar las leyes locales y nacionales relativas al correo electrónico. Recuerde que las leyes de correo electrónico varían ampliamente entre diferentes países y, a veces, diferentes regiones locales dentro de un país.

* Asegúrese de recopilar la información de ubicación de un suscriptor para cumplir con las leyes de país del suscriptor. Sin ese detalle, se puede limitar la forma de comercializar con el suscriptor.
* Cualquier ley relevante está determinada por la ubicación del destinatario, no del remitente. Por lo tanto, debe conocer y seguir las leyes de cualquier país donde pueda tener un suscriptor.
* A menudo es difícil saber con total certeza el país de residencia del suscriptor. Los datos proporcionados por el cliente pueden estar desactualizados y los datos de ubicación de los píxeles pueden ser inexactos debido a la VPN o al almacenamiento de imágenes, como con Gmail y Yahoo. En caso de duda, es más seguro aplicar las leyes y directrices más estrictas posibles.

## Otros métodos de colección de listas no recomendados

Existen muchas otras formas de recopilar direcciones, cada una con sus propias oportunidades, desafíos e inconvenientes. El Adobe no recomienda estos métodos en general, ya que el uso a menudo se restringe a través de políticas de uso aceptables del proveedor. Veamos algunos ejemplos comunes, para que pueda conocer los peligros que le ayudarán a limitar o evitar los riesgos:

**Comprar o alquilar una lista**
Existen muchos tipos de direcciones de correo electrónico. Correo electrónico principal, correos electrónicos de trabajo, correos electrónicos escolares, correos electrónicos secundarios y correos electrónicos inactivos, por nombrar algunos. Los tipos de direcciones recopiladas y compartidas a través de listas compradas o alquiladas rara vez son cuentas de correo electrónico principales, que son donde se produce casi toda la participación y la actividad de compra.

Si tienes suerte, obtienes cuentas secundarias, donde la gente busca ofertas y ofertas cuando están listos para comprar algo. Esto suele dar como resultado niveles de participación bajos, si los hay. Si no tiene suerte, la lista está llena de correos electrónicos inactivos, que ahora podrían ser trampas de correo no deseado. A menudo, recibe una combinación de correos electrónicos secundarios e inactivos. En general, la calidad de estos tipos de listas hace más daño que bien a un programa de correo electrónico. Esta práctica está prohibida por la [Política de uso aceptable de Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Listas anexadas**
Estos son clientes que han elegido interactuar con su marca, lo cual es genial. Pero eligieron emplear un método distinto al correo electrónico (en la tienda, en las redes sociales, etc.). No pudieron mostrarse receptivos a recibir un correo electrónico no solicitado de usted y también pueden estar preocupados por cómo obtuvo su dirección de correo electrónico, ya que no la proporcionaron. Este método tiene el riesgo de convertir a un cliente o cliente potencial que se involucra con su marca en un detractor que ya no confía en su marca y va a su competencia en su lugar. Esta práctica está prohibida por la [Política de uso aceptable de Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Feria comercial u otra colección de eventos**
La recopilación de direcciones en un stand o a través de otro método oficial de marca clara puede ser útil. El riesgo es que muchos eventos como este recopilen todas las direcciones y las distribuyan a través del promotor o anfitrión del evento. Lo que significa que los propietarios de estas direcciones de correo electrónico nunca solicitaron recibir correos electrónicos de su marca. Es probable que estos suscriptores se quejen y marquen su correo como correo no deseado y es posible que no hayan proporcionado información de contacto precisa.

**Sorteos**

Los sorteos proporcionan grandes cantidades de direcciones de correo electrónico rápidamente. Pero estos suscriptores quieren el premio, no sus correos electrónicos. Es posible que ni siquiera hayan prestado atención al nombre de quién les contactaría. Es probable que se quejen y marquen su correo como correo no deseado, y es poco probable que se involucren o realicen una compra.

## Recursos específicos de los productos

**Adobe Campaign Classic**

* [Creación de un formulario de suscripción con doble inclusión](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=es#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Proceso de inclusión doble](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=es#communication-channels)
