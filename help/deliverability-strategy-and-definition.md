---
title: ¿Cuál es la estrategia de envío y cómo definir la capacidad de envío?
description: Comprenda cómo se define la capacidad de envío, por qué importa y las métricas clave de capacidad de envío.
feature: Capacidad de entrega
topics: Deliverability
kt: 5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 11%

---


# Estrategia y definición de la capacidad de entrega

El diseño de campañas de marketing por correo electrónico exitosas depende de tener una comprensión clara de los objetivos de marketing, ya sean para iniciativas de prospección o de administración de la relación con los clientes (CRM). Esto ayuda a determinar a quién dirigirse, qué promover y cuándo es ideal el alcance.

Estos son algunos ejemplos de objetivos de estrategia de marketing por correo electrónico:

* Adquisición de nuevos clientes
* Conversión de clientes potenciales a compradores nuevos
* Aumento de las relaciones actuales con los clientes con ofertas adicionales
* Retención de clientes fieles
* Mejora de la satisfacción del cliente y la lealtad de marca
* Reactivación de clientes perdidos o caducados

## Capacidad de entrega definida

Existen dos métricas clave que desempeñan un papel en la definición de la capacidad de envío. La *tasa entregada* es el porcentaje de correos electrónicos que no rebotan y que el ISP acepta. A continuación, *ubicación de la bandeja de entrada*: esto se aplica a los mensajes que acepta el ISP y determina si el correo electrónico aterriza en la bandeja de entrada o en la carpeta de correo no deseado.

Es importante comprender tanto la tasa de entrega como la tasa de colocación de la bandeja de entrada en conjunto al medir el rendimiento del correo electrónico. Una tasa de entrega alta no es la única faceta de la capacidad de envío. El hecho de que se reciba un mensaje a través del punto de comprobación inicial de un ISP no significa necesariamente que el suscriptor haya visto e interactuado con la comunicación.

## Por qué importa la capacidad de entrega

Si no sabe si sus correos electrónicos se entregan o si están aterrizando en la bandeja de entrada en lugar de en la carpeta de correo no deseado, debe hacerlo. Por eso.

Innumerables horas se dedican a la planificación y producción de sus campañas de correo electrónico. Si los correos electrónicos rebotan o finalmente llegan a la carpeta de correo no deseado de los suscriptores, probablemente los clientes no los lean, no se reconocerá la llamada a la acción y no cumplirá los objetivos de ingresos debido a la pérdida de conversiones. En pocas palabras, no puede permitirse ignorar la capacidad de envío. Es crucial para el éxito de sus esfuerzos de marketing por correo electrónico y sus resultados finales.

Las siguientes prácticas recomendadas sobre la capacidad de envío garantizan que el correo electrónico tenga las mejores posibilidades de aperturas, clics y el objetivo final: la conversión. Puede escribir una línea de asunto brillante y tener imágenes hermosas y contenido atractivo. Pero si ese correo electrónico no se envía, el cliente no tiene ninguna oportunidad de convertir. En general, en la capacidad de envío de correo electrónico, cada paso del proceso de aceptación de correo depende del primero para el éxito del programa.

### Paso 1: Correo electrónico enviado

Factores importantes para la entrega:

* **Infraestructura** sólida: Configuración de IP y dominio, configuración de bucle de comentarios (FBL) (incluida la supervisión y el procesamiento de quejas) y procesamiento regular de devoluciones. Para los clientes de Adobe, Adobe es responsable de esta configuración en nombre de nuestros clientes.
* **Autenticación** sólida:  [!DNL Sender Policy Framework] (SPF),  [!DNL DomainKeys Identified Mail] (DKIM),  [!DNL Domain-based Message Authentication], informes y conformidad (DMARC).
* **Calidad** de lista alta: Inclusión explícita, métodos de adquisición de correo electrónico válidos y políticas de participación.
* **cadencia de envío coherente y minimización de las fluctuaciones** de volumen.
* **Alta reputación** de dominio e IP.

### Paso 2: Ubicación de la bandeja de entrada de correo electrónico

Los ISP tienen algoritmos únicos, complejos y que cambian constantemente para determinar si el correo electrónico se coloca en la bandeja de entrada, la carpeta basura o la carpeta de correo no deseado.

Estos son algunos factores importantes para la colocación en la bandeja de entrada:

* Correo electrónico enviado
* Alta participación
* Baja cantidad de quejas (menos del 0,1 % en total)
* Volumen coherente
* Trampas de correo no deseado bajas
* Tasa de salida hacia otro sitio baja
* Falta de problemas de listas de bloqueados

### Paso 3: Participación por correo electrónico: aperturas

Estos son algunos factores importantes para la tasa de apertura:

* Correo electrónico enviado y aterrizado en la bandeja de entrada
* Reconocimiento de marca
* Línea de asunto y encabezados convincentes
* Personalización
* Frecuencia
* Relevancia o valor del contenido

### Paso 4: Participación por correo electrónico: clics

Estos son algunos factores importantes para la tasa de clics:

* Correo electrónico enviado, aterrizado en la bandeja de entrada y abierto
* CTA fuerte
   * Esta es la acción principal que desea realizar en la audiencia. Normalmente es un clic en una dirección URL. Asegúrese de que es claro y fácil de encontrar para el usuario.
* Relevancia o valor del contenido

### Paso 5: Conversión

Estos son algunos factores importantes para la conversión:

* Todo lo anterior
* Transición del correo electrónico a través de una dirección URL de trabajo a una página de aterrizaje o página de ventas
* Experiencia de la página de aterrizaje
* Reconocimiento, percepción y lealtad de la marca

### Impacto potencial en los ingresos

La conversión es clave, pero ¿cuál es la alternativa? Su estrategia de envío puede fortalecer o causar estragos en el programa de marketing por correo electrónico nirvana. El siguiente gráfico ilustra la pérdida potencial de ingresos que una política de envío débil puede tener en su programa de marketing. Como se ha demostrado, para una empresa con una tasa de conversión del 2 por ciento y una compra promedio de 100 dólares, cada reducción del 10 por ciento en la colocación en la bandeja de entrada equivale a una pérdida de ingresos de casi 20.000 dólares. Tenga en cuenta que estos números son únicos para cada remitente.

| Enviados | Porcentaje | Entregas | Porcentaje | Bandeja de entrada | Número no presente en la bandeja de entrada | Tasa de conversión | Número de pérdidas | Promedio | Perdido |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|  | entrega |  | bandeja de entrada |  |  |  | Conversiones | purchase | ingresos |
| 100 K | 99% | 99 K | 100% | 99 K | - | 2% | 0 | $100 | $ - |
| 100 K | 99 % | 99 K | 90 % | 89,1 K | 9.900 | 2% | 198 | 100 $ | 19 800 $ |
| 100 K | 99 % | 99 K | 80% | 79,2 K | 19.800 | 2% | 396 | 100 $ | 39 600 $ |
| 100 K | 99 % | 99 K | 70% | 69,3 K | 29.700 | 2% | 594 | 100 $ | 59 400 $ |
| 100 K | 99 % | 99 K | 60% | 59,4 K | 39.600 | 2% | 792 | 100 $ | 79 200 $ |
| 100 K | 99 % | 99 K | 50% | 49,5 K | 49.500 | 2% | 990 | 100 $ | 99.000 $ |
| 100 K | 99 % | 99 K | 40% | 39,6 K | 59.400 | 2% | 1188 | 100 $ | 118 800 $ |
| 100 K | 99 % | 99 K | 30% | 29,7 K | 69.300 | 2% | 1386 | 100 $ | 138.600 $ |
| 100 K | 99 % | 99 K | 20% | 19,8 K | 79.200 | 2% | 1584 | 100 $ | 158.400 $ |
