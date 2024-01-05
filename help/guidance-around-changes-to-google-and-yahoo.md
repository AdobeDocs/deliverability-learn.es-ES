---
title: Orientación sobre los cambios anunciados en [!DNL Google] y [!DNL Yahoo]
description: Orientación sobre los cambios anunciados en [!DNL Google] y [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
exl-id: 879e9124-3cfe-4d85-a7d1-64ceb914a460
source-git-commit: 1f2a6c7b53a5f5110250c8aecac349c5b72feb6b
workflow-type: tm+mt
source-wordcount: '1759'
ht-degree: 0%

---

# Orientación sobre los cambios anunciados en [!DNL Google] y [!DNL Yahoo]

El 3 de octubre ambos [!DNL Google] y [!DNL Yahoo] anunciaron conjuntamente los cambios planeados a través de sus blogs. Estos cambios están diseñados para mantener a sus usuarios más seguros y proporcionar una mejor experiencia de correo electrónico mediante la aplicación de algunas prácticas recomendadas comunes del sector como nuevos requisitos a partir del 1 de febrero de 2024.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Anuncio_](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Anuncio](/help/assets/Yahoo.png)

Los expertos en envío de correos electrónicos del Adobe han leído estas publicaciones de blog y toda la documentación vinculada para que no tenga que hacerlo. Estas son las principales conclusiones.

## Entonces, ¿qué son exactamente [!DNL Google] y [!DNL Yahoo] ¿haciendo?

En el mundo del correo electrónico existen requisitos legales, requisitos prácticos y prácticas recomendadas generales. Los requisitos legales varían ampliamente de una ubicación a otra y no forman parte de este tema. En su lugar, [!DNL Google] y [!DNL Yahoo] está tomando las prácticas recomendadas y convirtiéndolas en requisitos prácticos.

Ninguno de los elementos [!DNL Google] y [!DNL Yahoo] Las que empezarán a requerir en febrero son nuevas y a menudo han sido recomendaciones de mejores prácticas durante años, pero la adopción ha sido lenta y desigual en la industria. Esto es [!DNL Google] y [!DNL Yahoo]Es la forma de ayudar a impulsar ese proceso de adopción diciendo &quot;Si desea implementar el correo electrónico para nuestros usuarios (esto puede representar una parte significativa de su lista de correos electrónicos, en algunos casos hasta el 70 %, según la región y el sector), debe hacer estas cosas&quot;.

## ¿Cuáles son los detalles?

Si es un cliente de Adobe, la mayor parte de lo que necesita ya forma parte de su configuración, pero hay algunos elementos clave que son técnicamente opcionales y debe estar seguro de que su organización ha adoptado y configurado estos elementos correctamente antes de febrero de 2024.

## DMARC:

[!DNL Google] y [!DNL Yahoo] Ambos requerirán que tenga un registro DMARC para cualquier dominio que utilice para enviarles correo electrónico. Actualmente NO requieren una configuración p=reject o p=quarantine, por lo que una configuración de p=none, comúnmente denominada &quot;monitorización&quot;, es perfectamente aceptable por ahora. Esto no cambiará la forma en que se procesan los correos electrónicos, sino que hará lo que haría normalmente sin DMARC. Configurar esto es el primer paso para protegerse con DMARC, y además de la nueva ventaja de ayudarle a enviar correos electrónicos a [!DNL Google] y [!DNL Yahoo] también puede ayudarle a ver si hay problemas de autenticación en cualquier lugar dentro de su ecosistema de correo electrónico.

Las reglas para DMARC no cambian, lo que significa que a menos que se configure para evitarlo, se heredará un registro DMARC en el dominio principal (adobe.com, por ejemplo) y abarcará cualquier subdominio (como email.adobe.com). No necesita registros DMARC diferentes para los subdominios, a menos que desee o necesite agregarlos por varios motivos comerciales.

DMARC es totalmente compatible con el Adobe actualmente, pero no es obligatorio. Utilice cualquier verificador DMARC gratuito para ver si ha configurado DMARC para sus subdominios y, si no lo hace, hable con su equipo de soporte de Adobe para ver cuál es la mejor manera de hacerlo.

También puede encontrar más información sobre DMARC y cómo implementarla [aquí](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=es){target="_blank"} for Adobe Campaign or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html){target="_blank"} para el Marketo Engage.

## 1-Click (Lista) Cancelar Suscripción:

No te asustes. [!DNL Google] y [!DNL Yahoo] no se refiere a los vínculos de cancelación de suscripción del cuerpo del correo electrónico o al pie de página en los que un bot de seguridad podría hacer clic simplemente haciendo su trabajo o por accidente. Lo que significan es la funcionalidad de encabezado List-Unsubscribe para las versiones &quot;mailto&quot; o &quot;http/URL&quot;. Esta es la función dentro de [!DNL Yahoo] y las IU de Gmail donde los usuarios pueden hacer clic en cancelar suscripción. Gmail incluso pregunta a los usuarios que hacen clic en &quot;Informar sobre correo no deseado&quot; si querían cancelar la suscripción, lo que puede reducir el número de quejas que recibe (las quejas dañan su reputación) al convertirlas en cancelaciones de suscripción (no perjudica su reputación).

Es importante tener en cuenta que [!DNL Google] y [!DNL Yahoo] se refieren a la opción &quot;http/URL&quot; con el nombre &quot;1-Click&quot;, y esto es intencional. Técnicamente, la opción &quot;http/URL&quot; original le permitía redirigir a los destinatarios a un sitio web. Ese no es el enfoque de [!DNL Yahoo] y [!DNL Google], que hacen referencia al actualizado [RFC8058](https://datatracker.ietf.org/doc/html/rfc8058){target="_blank"} que se centra en procesar la cancelación de la suscripción mediante una solicitud de POST HTTPS en lugar de un sitio web, lo que lo convierte en &quot;1 clic&quot;.

Hoy, Gmail acepta la opción de cancelación de suscripción a la lista &quot;mailto&quot;. Gmail ha dicho que &quot;mailto&quot; no cumple con sus expectativas a partir de ahora, y los remitentes necesitarán tener activada la opción &quot;post&quot; list-unsubscribe. Aquellos remitentes que ya tengan la cancelación de la suscripción a una lista de algún tipo tendrán hasta el 1 de junio de 2024 para tener la cancelación de la suscripción a una lista de 1 clic.

[!DNL Yahoo] ha dicho que seguirán honrando la opción de &quot;mailto&quot;, por ahora, pero que ellos también requerirán &quot;post&quot; en el futuro.

El Adobe recomienda utilizar las opciones &quot;mailto&quot; y &quot;post/1-Click&quot; list-unsubscribe. El Adobe de está trabajando en la habilitación del soporte &quot;post&quot; en todas nuestras plataformas de envío de correo electrónico para apoyar a nuestros usuarios con el cumplimiento de estos requisitos, y futuras actualizaciones en torno a esto.

La necesidad de encabezados de cancelación de suscripción a una lista no se aplica a los correos electrónicos transaccionales. Tenga en cuenta que los mensajes activados, como el carro de compras abandonado y las comunicaciones similares no generadas por el suscriptor, se consideran marketing por proveedores de buzones de correo como [!DNL Google] y [!DNL Yahoo] y esos necesitarían cancelar la suscripción a la lista.

[!DNL Google] y [!DNL Yahoo] ambos saben que, en algunos casos, un destinatario cancela la suscripción y, a continuación, vuelve a suscribirse en un momento posterior. Aunque no están dispuestos a compartir la salsa secreta de cómo identifican estas situaciones, están trabajando en métodos para evitar penalizar incorrectamente a los remitentes en estos casos.

>[!INFO]
> Adobe está trabajando en la habilitación del soporte &quot;post&quot; en todas nuestras plataformas de envío de correo electrónico para apoyar a nuestros usuarios en el cumplimiento de estos requisitos:
> * [!DNL Adobe Campaign Classic V7/V8]: Totalmente compatible con el POST 1-Click hoy. Se publicarán las actualizaciones de la configuración paso a paso [aquí](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=en#list-unsubscribe){target="_blank"} a mediados de enero
>* [!DNL Adobe Campaign Standard]: se está actualizando para admitir el POST 1-Click. Vuelva pronto para ver las actualizaciones. Se proporcionarán las instrucciones de configuración [aquí](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-14778.html?lang=en){target="_blank"}
>* [!DNL Adobe Journey Optimizer]: Totalmente compatible con el POST 1-Click hoy. Se publicarán las actualizaciones de la configuración paso a paso [aquí](https://experienceleague.adobe.com/docs/journey-optimizer/using/email/email-opt-out.html?lang=en){target="_blank"} a mediados de enero
>
> Marketo: se está actualizando para admitir el POST 1 clic. Una vez listo, se aplicará automáticamente donde sea necesario.


## Proceso cancela la suscripción en un plazo de 2 días:

Esta ha sido una práctica recomendada durante un tiempo, ya que cada correo electrónico que implementa a alguien que canceló la suscripción generalmente resulta en una queja de correo no deseado, por lo que cuanto antes deje de enviarle correo electrónico, mejor. Nuevamente, los requisitos legales pueden ser mucho más largos en algunos casos, pero [!DNL Google] y [!DNL Yahoo] sabrá que su usuario canceló la suscripción a través de List-Unsubscribe y que aún le está enviando correos electrónicos el día 3, y ha declarado que no permitirá que los remitentes que lo hagan sigan enviando correos electrónicos a CUALQUIERA de sus usuarios.

Este requisito de 2 días es para cualquier cancelación de suscripción a través de los distintos métodos de cancelación de suscripción a listas. En algunos casos (como &quot;mailto&quot;) eso significa que el Adobe los procesará. El Adobe procesa todas las solicitudes de cancelación de suscripción inmediatamente después de recibir la solicitud, dentro del límite de 2 días. En otros casos, es posible que los esté procesando. Si está procesando estas solicitudes, es posible que tenga que realizar cambios en su extremo para cumplir con este cronograma de 2 días.

## Tasas de quejas:

Mantener tasas de quejas bajas por debajo del 0,2% ha sido una práctica recomendada durante mucho tiempo. [!DNL Google] está fijando el nivel más alto en el 0,3 % durante un periodo prolongado de tiempo, pero ha indicado claramente que hay beneficios en mantenerlo por debajo del 0,1 %. Aquí están los detalles que compartieron:

* Intente mantener la tasa de spam por debajo del 0,10 %.
* Evite una tasa de spam del 0,30 % o superior, especialmente durante cualquier periodo de tiempo prolongado.
* El mantenimiento de una tasa baja de spam hace que los remitentes sean más resistentes a los picos ocasionales en los comentarios de los usuarios.
* Del mismo modo, mantener una alta tasa de spam conducirá a una mayor clasificación de spam. Las mejoras en la tasa de spam pueden tardar un tiempo en reflejarse positivamente en la clasificación de spam.

[!DNL Yahoo] ha declarado que su umbral de quejas también será del 0,30 %.

[!DNL Google] y [!DNL Yahoo]El objetivo de no es castigar a los remitentes por un solo mal día o un error que cause un pico temporal en las quejas. En su lugar, se centran en remitentes que tienen altas tasas de quejas durante un periodo prolongado de tiempo o un patrón de mal comportamiento de envío.

Si necesita ayuda para monitorizar las tasas de quejas o desea ayuda con estrategias para reducir las quejas, hable con su consultor de capacidad de entrega de Adobe o hable con el equipo de la cuenta sobre la adición de un consultor de capacidad de entrega si aún no tiene uno.

## ¿Qué plazos estamos viendo?

Se han recibido actualizaciones de los plazos desde el anuncio original en octubre. Las escalas de tiempo más recientes tienen este aspecto:

[!DNL Gmail]

Febrero de 2024: Empezarán las devoluciones temporales diseñadas para advertir del incumplimiento. Los correos electrónicos se enviarán con normalidad después de un breve retraso si aún no cumple los requisitos. Si cumple totalmente los requisitos, no habrá devoluciones temporales y no notará nada.

Abril de 2024: los bloques comenzarán para los remitentes que no cumplan con todo, excepto List-Unsubscribe 1-Click. Al principio, solo se bloqueará una parte del correo electrónico no conforme y el % bloqueado aumentará con el tiempo.

1 de junio de 2024: Cualquier remitente que no cumpla totalmente los requisitos, incluida la cancelación de la suscripción a una lista con un clic, experimentará un bloqueo.

[!DNL Yahoo]

No ha proporcionado fechas exactas, pero ha dicho que &quot;el despliegue de la aplicación comenzará en febrero de 2024. La aplicación se implantará gradualmente&quot;.

## ¿Cómo me afectará esto como experto en marketing?

No cumplir con estos nuevos requisitos de Gmail y [!DNL Yahoo] se espera que el resultado sea que los correos electrónicos lleguen a la carpeta de correo no deseado o se bloqueen (es decir, que se obtenga una devolución del MBP que indique que el correo electrónico no se entregó).

Como tal, Adobe recomienda encarecidamente que revise los cambios descritos anteriormente y se asegure de que comience a cumplirlos lo antes posible. Ahora también es un buen momento para empezar a comparar su rendimiento en [!DNL Yahoo] y [!DNL Google] para permitirle ver si hay algún cambio sustancial en sus métricas a partir de febrero.

Estamos aquí para ayudarle, así que si tiene alguna pregunta o necesita asistencia, hable con su consultor de capacidad de envío de Adobes o hable con el equipo de su cuenta sobre la adición de un consultor de capacidad de envío si aún no lo tiene.

## ¿Hay maneras de evitar esto?

Si bien siempre surge esta pregunta, la realidad es que estos cambios tienen sentido para los usuarios finales de [!DNL Google] y [!DNL Yahoo]Las plataformas de. Están motivados por las expectativas de estos usuarios de hacer cumplir estas reglas. No recomendamos intentar evitar cualquiera de estos cambios, sino dar un paso atrás y pensar en cómo acomodar estos cambios.

## Nota final:

Tenga en cuenta que esto no se aplica actualmente a los correos electrónicos enviados a [!DNL Yahoo].JP o [!DNL Gmail] Las cuentas de Workspace, sin embargo, sí se aplican a los correos electrónicos procedentes de esas ubicaciones.

## Recursos adicionales (no específicos de estos cambios):

[Directrices de remitente de Google](https://support.google.com/mail/answer/81126){target="_blank"}

[Preguntas frecuentes sobre Google](https://support.google.com/a/answer/14229414?sjid=2864589551334481470-NC){target="_blank"}

[Directrices de remitente de Yahoo](https://senders.yahooinc.com/best-practices/){target="_blank"}

[Preguntas frecuentes sobre Yahoo](https://senders.yahooinc.com/faqs/){target="_blank"}
