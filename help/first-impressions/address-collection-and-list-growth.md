---
title: Recopilación de direcciones y aumento de listas
description: 'Descubra cuáles son las mejores fuentes para las nuevas direcciones de correo electrónico, cómo garantizar una alta calidad de los datos y la alineación con las directrices legales. '
topics: Deliverability
kt: 7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
exl-id: 350950dc-4703-402a-8e22-3862f4e21d52
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 4%

---

# Recopilación de direcciones y aumento de listas

Las mejores fuentes de nuevas direcciones de correo electrónico son fuentes directas como los registros en el sitio web o en tiendas físicas. En estas situaciones, puede controlar la experiencia para asegurarse de que sea positiva y de que el suscriptor esté interesado en recibir correos electrónicos de su marca.

Algunas notas sobre estos métodos de registro:

**La colección de** tiendas físicas puede presentar desafíos debido a las entradas de direcciones verbales o escritas que causan errores ortográficos en las direcciones. Se recomienda enviar un correo electrónico de confirmación lo más rápido posible después de registrarse en la tienda.

La forma más común de **registro en el sitio web** es la &quot;inclusión única&quot;. Es el estándar mínimo absoluto que debe utilizarse para adquirir direcciones de correo electrónico. La opción de inclusión única se produce cuando el titular de una dirección de correo electrónico específica concede a un remitente permiso para enviarle correos electrónicos de marketing, normalmente enviando la dirección a través de un formulario web o registros en la tienda. Aunque es posible ejecutar una campaña de correo electrónico con éxito mediante este método, puede ser la causa de algunos problemas.

* Las direcciones de correo electrónico no confirmadas pueden tener errores tipográficos o tener un formato incorrecto, ser incorrectas o utilizarse de forma maliciosa. Los errores tipográficos y las direcciones mal formadas provocan altas tasas de devoluciones, lo que puede provocar y no bloques emitidos por ISP o pérdida de reputación de IP.

* El envío malicioso de trampas de correo no deseado conocidas (a veces llamadas &quot;envenenamiento de listas&quot;) puede causar enormes problemas con la entrega y la reputación si el propietario de esa trampa toma medidas. Es imposible saber si el destinatario realmente desea que se añada a una lista de marketing sin una confirmación. Esto hace igualmente imposible establecer las expectativas del destinatario y puede provocar un aumento de las quejas por correo no deseado, y a veces una inclusión en la lista de bloqueados si el correo electrónico recopilado resulta ser una trampa de correo no deseado.

Para obtener instrucciones sobre cómo minimizar los problemas presentados tanto en el almacén físico como en la opción de inclusión única, vaya a la sección [Calidad de los datos e higiene](#data-quality-and-hygiene) en esta guía para conocer los detalles y beneficios de la doble inclusión.

>[!NOTE]
>
>Los suscriptores suelen utilizar direcciones de envío, direcciones caducadas o direcciones que no son suyas para obtener lo que desean de un sitio web, pero también evitan que se agreguen a listas de marketing. Cuando esto sucede, las listas de los especialistas en marketing resultan en un número elevado de rechazos graves, tasas elevadas de quejas por correo no deseado y suscriptores que no hacen clic, abren ni interactúan de forma positiva con los correos electrónicos. Se puede ver como un indicador rojo para proveedores de buzones de correo y ISP.

## Formularios de registro

Además de añadir los campos de los datos, desea recopilar información sobre los nuevos suscriptores, hay algunas otras cosas que debe hacer con el formulario de registro en el sitio web.

* Establezca expectativas claras con el suscriptor de que está aceptando recibir correos electrónicos, qué recibirá y con qué frecuencia lo recibirá.
* Añada opciones que permitan al suscriptor seleccionar la frecuencia o el tipo de comunicaciones que recibe. Estas opciones le permiten conocer las preferencias del suscriptor desde el principio para que pueda ofrecerle la mejor experiencia posible a su nuevo cliente.
* Equilibre el riesgo de perder el interés del suscriptor durante el proceso de registro solicitando la mayor cantidad de información posible. Cosas como su cumpleaños, ubicación o intereses le ayudan a enviar contenido más personalizado. Los suscriptores de cada marca tienen diferentes expectativas y umbrales de tolerancia, por lo que las pruebas son clave para encontrar el equilibrio adecuado para su situación.

>[!NOTE]
>
> No utilice casillas premarcadas durante el proceso de registro. Aunque puede meterle en problemas legalmente, también es una experiencia negativa del cliente.

## Calidad de los datos e higiene

La recopilación de datos es solo parte del desafío. También debe asegurarse de que los datos sean precisos y útiles. Debe tener filtros de formato básicos establecidos. Una dirección de correo electrónico no es válida si no incluye &quot;@&quot; o &quot;.&quot; por ejemplo. Asegúrese de no permitir direcciones de alias comunes, que también se denominan cuentas de rol (como &quot;información&quot;, &quot;administrador&quot;, &quot;ventas&quot;, &quot;asistencia&quot;). Las cuentas de función pueden presentar riesgos porque, por su naturaleza, el destinatario contiene un grupo de personas en lugar de un solo suscriptor. Las expectativas y la tolerancia pueden variar dentro de un grupo, lo que pone en peligro las quejas, la participación variable, las bajas de suscripción y la confusión general.

Estas son algunas soluciones a problemas comunes con los que puede encontrar sus datos de dirección de correo electrónico:

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] la mayoría de los expertos en correo electrónico consideran la mejor práctica de envío. Si tiene problemas con trampas de correo no deseado o quejas sobre sus correos electrónicos de bienvenida, el DOI es una buena manera de asegurarse de que el suscriptor que recibe sus correos electrónicos se haya registrado en su programa de correo electrónico y desee recibir sus correos electrónicos.

El DOI consiste en enviar un correo electrónico de confirmación a la dirección de correo electrónico del suscriptor que se ha suscrito a su programa de correo electrónico que contiene un vínculo en el que se debe hacer clic para confirmar el consentimiento. Con este método de adquisición, si el suscriptor no confirma, el remitente no les enviaría más correos electrónicos. Haga saber a los nuevos suscriptores que está haciendo esto en el sitio web, animándolos a completar la suscripción antes de continuar. Este método sí observa una reducción en el número de suscripciones, pero las personas que sí se registran tienden a estar muy comprometidas y a quedarse a largo plazo. Normalmente resulta en un ROI mucho más alto para el remitente.

**Campo ocultoLa aplicación de un campo oculto en el formulario de registro es una buena forma de diferenciar los registros de bots automatizados de los suscriptores humanos reales.**
Como el campo de datos no está visible, oculto en el código HTML, un bot ingresará datos en los que un ser humano no lo haría. Con este método, puede crear reglas para suprimir cualquier registro que incluya datos rellenados en ese campo oculto.

**[!DNL re-CAPTCHA] es un método de validación que puede utilizar para reducir las probabilidades de que el suscriptor sea un bot y no una persona real. Existen varias versiones, algunas de las cuales contienen identificación de palabras clave o imágenes. Algunas versiones son más efectivas que otras, y lo que se obtiene en la prevención de problemas de seguridad y capacidad de envío es mucho mayor que cualquier impacto negativo en las conversiones.

## Directrices legales

Consulte a sus abogados para interpretar las leyes locales y nacionales relativas al correo electrónico. Recuerde que las leyes de correo electrónico varían ampliamente de entre diferentes países y a veces diferentes regiones locales dentro de un país.

* Asegúrese de recopilar la información de ubicación de un suscriptor para que cumpla con las leyes de país del suscriptor. Sin ese detalle, puede limitarse la forma en que puede comercializar con el suscriptor.
* Cualquier legislación relevante viene determinada por la ubicación del destinatario, no por el remitente. Así que debes conocer y seguir las leyes de cualquier país donde puedas tener un suscriptor.
* A menudo es difícil saber con total certeza el país de residencia del suscriptor. Los datos proporcionados por el cliente pueden estar desactualizados y los datos de ubicación de píxeles pueden ser inexactos debido a la VPN o el almacenamiento de imágenes, como con Gmail y Yahoo. Cuando hay dudas, es más seguro aplicar las leyes y directrices más estrictas posibles.

## Otros métodos de recopilación de listas no recomendados

Hay muchas otras formas de recopilar direcciones, cada una con sus propias oportunidades, desafíos y desventajas. El Adobe no los recomienda en general, ya que el uso se restringe a través de políticas de uso aceptables para el proveedor. Observaremos algunos ejemplos comunes, para que pueda conocer los peligros que le ayudarán a limitar o evitar los riesgos:

**Comprar o alquilar una**
listaExisten muchos tipos de direcciones de correo electrónico. Correo electrónico primario, correos electrónicos de trabajo, correos electrónicos escolares, correos electrónicos secundarios y correos electrónicos inactivos, por nombrar algunos. Los tipos de direcciones recopiladas y compartidas a través de listas compradas o alquiladas rara vez son cuentas de correo electrónico principales, que son donde se produce casi toda la actividad de participación y compra.

Si tiene suerte, obtendrá cuentas secundarias, en las que las personas buscarán ofertas y ofertas cuando estén listas para comprar algo. Esto generalmente da como resultado niveles de participación bajos, si los hay. Si no tiene suerte, la lista está llena de correos electrónicos inactivos, que ahora podrían ser trampas de correo no deseado. A menudo, se obtiene una combinación de correos electrónicos secundarios e inactivos. En general, la calidad de estos tipos de listas hace más daño que bien a un programa de correo electrónico. Esta práctica está prohibida por la [Política de uso aceptable de Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Listas**
appendSon clientes que han elegido interactuar con su marca, lo que es bueno. Pero optaron por utilizar un método distinto del correo electrónico (en tienda, medios sociales, etc.). No pueden ser receptivos a recibir un correo electrónico no solicitado y también pueden estar preocupados por cómo obtuvo su dirección de correo electrónico, ya que no la proporcionaron. Este método conlleva el riesgo de convertir a un cliente o cliente potencial que se comprometa con su marca en un detractor que ya no confía en su marca y, en su lugar, va a la competencia. Esta práctica está prohibida por la [Política de uso aceptable de Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Programa comercial u otra**
colección de eventosLa recopilación de direcciones en una cabina o a través de otro método oficial de marca clara puede ser útil. El riesgo es que muchos eventos como este recopilen todas las direcciones y los distribuyan a través del promotor o host de eventos. Lo que significa que los propietarios de estas direcciones de correo electrónico nunca han solicitado recibir correos electrónicos de su marca. Es probable que estos suscriptores se quejen y marquen su correo como correo no deseado, y es posible que no hayan proporcionado información de contacto precisa.

**Apuestas**

Las apuestas proporcionan un gran número de direcciones de correo electrónico rápidamente. Pero estos suscriptores quieren el premio, no sus correos electrónicos. Puede que ni siquiera hayan prestado atención al nombre de quién se pondría en contacto con ellos. Es probable que se quejen y marquen su correo como correo no deseado, y es poco probable que se involucren o realicen una compra.

## Recursos específicos de los productos

**Adobe Campaign Classic**

* [Creación de un formulario de suscripción con doble inclusión](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=es#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Proceso de inclusión doble](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=es#communication-channels)
