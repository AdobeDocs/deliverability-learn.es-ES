---
title: Listas de agujeros negros en tiempo real
description: Obtenga información sobre las organizaciones que mantienen listas de direcciones IP y dominios que probablemente utilizarán remitentes de correo no deseado.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 90%

---


# Listas de agujeros negros en tiempo real

Varias organizaciones mantienen las bases de datos de direcciones IP y dominios que suelen utilizar remitentes que envían correo no deseado. Estos sitios pueden ser útiles para comprender por qué algunos mensajes se rechazan como correo no deseado. Por lo general, es posible solicitar la eliminación de una dirección añadida incorrectamente a estas listas.

Estas bases de datos se denominan RBL (Listas de agujeros negros en tiempo real) y se consultan a través de un mecanismo DNS. Existen tres tipos de RBL:

* Por dirección IP: enumera las direcciones IP que envían correo no deseado o que probablemente retransmitan correo no deseado.
* Dominio de remitente: enumera los dominios de remitente (dominio completo de la dirección de correo electrónico de rechazo) que envía el correo electrónico o se configura incorrectamente.
* Por dominio Web: enumera los dominios (dominios de alto nivel registrados con los registradores) encontrados en las direcciones URL de los vínculos e imágenes incluidos en el contenido del correo no deseado. En las soluciones de Adobe, el dominio que se debe considerar es generalmente la dirección que se utiliza para el seguimiento.

A continuación se muestra una lista de los RBL más utilizados. Para obtener una lista más completa, consulte [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

   Consulte [https://www.spamhaus.org/](https://www.spamhaus.org/)

   La base de datos es más importante. En general, encontrarse clasificado en esta lista es una situación muy grave. Si esto ocurre, debe actuar inmediatamente y advertir a los servicios comerciales, a las entregas y al [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/es/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

   Consulte [https://www.spamcop.net/](https://www.spamcop.net/)

   Es una de las bases de datos más interesantes. Si una de las direcciones IP se incluye en esta lista, generalmente significa que los usuarios de SpamCop han declarado sus mensajes como correo no deseado o que usted ha enviado mensajes a una trampa honeypot de SpamCop.

* **URIBL**

   Consulte [https://www.uribl.com/](https://www.uribl.com/)

   Esta lista identifica los dominios que aparecen con regularidad en los mensajes declarados como correo no deseado. Si su dominio aparece en la lista, puede afectar en gran medida a sus envíos. Debe informar a los servicios de entrega y al [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) inmediatamente.

* **SURBL**

   Consulte [http://www.surbl.org/ ](http://www.surbl.org/)

   SURBL identifica los sitios web que aparecen con regularidad en el correo no deseado. Si su dominio aparece en la lista, puede afectar en gran medida a sus envíos. Debe informar a los servicios de entrega y al [Servicio de atención al cliente de Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) inmediatamente.

* **iX Manitu**

   Se trata de una lista de IP y se utiliza ampliamente en Alemania. Consulte [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
