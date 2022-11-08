---
title: Implementar los indicadores de marca de Gmail para la identificación de mensajes (BIMI)
description: Aprenda a implementar BIMI
topics: Deliverability
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: 683ffd3c87a4849aa9fa48fbf50db9ade97991af
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Implementación de [!DNL Brand Indicators for Message Identification] (BIMI)

Gmail anunció recientemente que sería [desarrollo del apoyo general de BIMI](https://cloud.google.com/blog/products/identity-security/bringing-bimi-to-gmail-in-google-workspace){target=&quot;_blank&quot;}. Para poder aprovechar esta situación, tendrá que lidiar con varios artículos, entre ellos: Certificados de marca verificados, Logotipos con marca comercial, Logotipos con formato correcto, configuración de DMARC, y finalmente publicar un registro BIMI en su DNS. Revisaremos todos estos pasos en este artículo.

[!DNL Brand Indicators for Message Identification] (BIMI) es un estándar del sector que permite que un logotipo aprobado aparezca junto al correo electrónico de un remitente en las plataformas participantes. Este atractivo no solo puede aumentar la participación, sino que también ayuda a confirmar la autenticidad del remitente, reduciendo el riesgo de phishing y otras tácticas de spam.

## Certificado de marca verificada

Uno de los componentes clave del programa BIMI de Gmail es el requisito de que los remitentes tengan un certificado de marca verificada (VMC) emitido por una autoridad de certificación válida. Actualmente, estos MVC están disponibles solamente desde Entrust y DigiCert, pero es probable que esa lista de proveedores crezca luego del anuncio de Gmail.

Los VMC serán similares a los certificados SSL de algunas maneras. Necesitará un VMC por cada logotipo que desee mostrar, así que si tiene muchas marcas, debe planificar la necesidad de múltiples VMCs. Cada VMC puede ser válido en múltiples dominios, aunque si se obtiene un VMC Multi-SAN. Por lo tanto, si desea que un logotipo aparezca en varios dominios de envío, solo necesita un VMC.

## Marca comercial del logotipo

Antes de obtener el VMC, hay que completar otro paso clave. Para obtener un MVC, el logotipo que desea mostrar debe estar registrado en una de las 8 oficinas de patentes y marcas comerciales globales aprobadas.

* Oficina de Patentes y Marcas Comerciales de los Estados Unidos (USPTO)
* Oficina Canadiense de Propiedad Intelectual
* Oficina de Propiedad Intelectual de la Unión Europea
* Oficina de Propiedad Intelectual del Reino Unido
* Deutsches Patent-und Markenamt
* Oficina de marcas comerciales de Japón
* Oficina de Patentes y Marcas de España O.A.
* IP Australia

Si el logotipo que desea mostrar no está registrado, o no está registrado en una de estas 8 organizaciones, entonces necesitará colaborar con su equipo legal para solucionarlo antes de solicitar el VMC.

## Formato de imagen del logotipo

Este también sería un buen momento para asegurarse de que su logotipo cumplirá los requisitos del logotipo BIMI para el formato.

Debe estar en formato de SVG y cumplir con el perfil portátil/seguro del SVG (SVG-P/S). Puede encontrar sugerencias sobre cómo hacerlo en la [Grupo de trabajo BIMI](https://bimigroup.org/svg-conversion-tools-released){target=&quot;_blank&quot;}.

## DMARC

Una vez que tenga el logotipo de la marca comercial formateado correctamente y el certificado de marca verificada, también deberá asegurarse de que DMARC esté completamente configurado en cualquier dominio de envío para el que desee que funcione BIMI.

Esto incluye asegurarse de que el P= está configurado como Cuarentena o Rechazar. Si su DMARC utiliza P=None, no será apto para BIMI. Se recomienda encarecidamente la configuración P=None para asegurarse de saber qué correo sale de un dominio y de que nada se bloquearía accidentalmente si se cambia a &quot;Cuarentena&quot; o &quot;Rechazar&quot;, piense en ello como la fase de prueba y recopilación de información. Tendrás que pasar de eso a la aplicación antes de que BIMI esté disponible para ti.

## Entrada DNS

Con todo lo demás finalmente alineado y listo para irse, es hora de actualizar la entrada DNS con su BIMI.

Esta es una entrada simple que debería tener un aspecto similar al siguiente:

```
default._bimi.[domain] IN TXT “v=BIMI1; l=[SVG URL] 
```

Puede obtener los detalles sobre esa entrada e incluso utilizar un verificador BIMI gratuito en la [Sitio del grupo de trabajo BIMI](https://bimigroup.org/implementation-guide){target=&quot;_blank&quot;}.


## Principales seguimientos

Si es [!DNL Adobe Campaign], Adobe puede ayudarle a crear la actualización de DNS de BIMI: póngase en contacto con el servicio de atención al cliente de Adobe para solicitar una. El Adobe también puede ayudarle a solucionar el problema si BIMI no funciona correctamente para usted.

Si es cliente de Marketo, consulte [esta publicación de blog](https://nation.marketo.com/t5/support-blogs/how-to-bimi/ba-p/296966){target=&quot;_blank&quot;} para obtener instrucciones sobre cómo crear su registro BIMI.

Para obtener ayuda con marcas comerciales o certificados de marca verificada, trabaje con su equipo legal y con un proveedor de MVC autorizado.

La configuración de BIMI para Gmail puede no ser un proceso rápido, pero puede tener importantes beneficios tanto desde el punto de vista del marketing como de la seguridad.
