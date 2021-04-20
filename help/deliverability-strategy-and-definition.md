---
title: ¿Cuál es la estrategia de entrega y cómo definir la capacidad de entrega?
description: Comprenda cómo se define la capacidad de entrega, por qué importa y las métricas clave de capacidad de entrega.
feature: Deliverability
topics: Deliverability
kt: 5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 5285eda9-5099-48d5-b150-ce2c376ee549
translation-type: ht
source-git-commit: e433002423bd1ab2f4a89425198c16160dae0719
workflow-type: ht
source-wordcount: '844'
ht-degree: 100%

---

# Estrategia y definición de entrega

El diseño de campañas de marketing por correo electrónico exitosas depende de tener una comprensión clara de los objetivos de marketing, ya sean para iniciativas de clientes potenciales o de administración de la relación con los clientes (CRM, por sus siglas en inglés). Esto ayuda a determinar a quién dirigirse, qué promover y cuándo enviar.

Estos son algunos ejemplos de objetivos de estrategia de marketing de correo electrónico:

* Adquisición de nuevos clientes
* Conversión de clientes potenciales a compradores nuevos
* Aumento de las relaciones con los clientes actuales con las ofertas adicionales
* Retención de clientes fieles
* Mejora de la satisfacción del cliente y la lealtad de marca
* Reactivación de clientes perdidos o caducados

## Capacidad de entrega definida

Existen dos métricas clave que desempeñan un papel en la definición de la capacidad de entrega. La *tasa entregada* es el porcentaje de correos electrónicos que no rebotan y que acepta el ISP. A continuación, la *ubicación de la bandeja de entrada* se aplica a los mensajes que acepta el ISP y determina si el correo electrónico aterriza en la bandeja de entrada o en la carpeta de correo no deseado.

Es importante comprender tanto la tasa de entrega como la tasa de ubicación de la bandeja de entrada en conjunto al medir el rendimiento del correo electrónico. Una tasa de entrega alta no es la única faceta de la capacidad de entrega. El hecho de que se reciba un mensaje a través del punto de comprobación inicial de un ISP no significa necesariamente que el suscriptor haya visto e interactuado con la comunicación.

## Por qué importa la capacidad de entrega

Si no sabe si sus correos electrónicos se entregan o si están llegando a la bandeja de entrada en lugar de en la carpeta de correo no deseado, debería saberlo. He aquí la razón.

Se invierten muchas horas en la planificación y producción de sus campañas de correo electrónico. Si los correos electrónicos rebotan o finalmente llegan a la carpeta de correo no deseado de los suscriptores, probablemente los clientes no los lean, no se reconocerá la llamada a la acción y no se cumplirán los objetivos de ingresos debido a la pérdida de conversiones. En pocas palabras, no puede permitirse ignorar la capacidad de entrega. Es crucial para el éxito de sus esfuerzos de marketing por correo electrónico y sus resultados finales.

Las siguientes prácticas recomendadas sobre la capacidad de entrega garantizan que el correo electrónico tenga las mejores posibilidades de aperturas, clics y el objetivo final: la conversión. Puede escribir una línea de asunto brillante, tener imágenes hermosas y contenido atractivo. Pero si ese correo electrónico no se entrega, el cliente no tiene ninguna oportunidad de convertir. En general, en la capacidad de entrega de correo electrónico, cada paso del proceso de aceptación de correo, depende del primero para el éxito del programa.

### Paso 1: Entrega del correo electrónico

Factores importantes para la entrega:

* **Infraestructura sólida**: configuración de IP y dominio, configuración de bucle de comentarios (FBL) (incluida la monitorización y el procesamiento de quejas) y procesamiento regular de devoluciones. Para los clientes de Adobe, Adobe es responsable de esta configuración en nombre de nuestros clientes.
* **Autenticación sólida**: [!DNL Sender Policy Framework] (SPF), [!DNL DomainKeys Identified Mail] (DKIM), [!DNL Domain-based Message Authentication], sistema de informes y conformidad (DMARC).
* **Calidad de lista alta**: inclusión explícita, métodos de adquisición de correo electrónico válidos y políticas de participación.
* **Cadencia de entrega coherente y minimización de las fluctuaciones de volumen**.
* **Alta reputación de dominio e IP**.

### Paso 2: Ubicación de la bandeja de entrada de correo electrónico

Los ISP tienen algoritmos únicos, complejos y que cambian constantemente para determinar si el correo electrónico llega a la bandeja de entrada, la carpeta de la basura o la carpeta de correo no deseado.

Estos son algunos factores importantes para la ubicación en la bandeja de entrada:

* Correo electrónico entregado
* Alta participación
* Baja cantidad de quejas (menos del 0,1 % en total)
* Volumen coherente
* Pocas trampas de correo no deseado
* Tasa de salida hacia otro sitio de mensajes devueltos no válidos baja
* Falta de problemas con la listas de bloqueados

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
   * Esta es la acción principal que quiere conseguir de su audiencia. Suele ser un clic en una dirección URL. Asegúrese de que sea claro y fácil de encontrar para el usuario.
* Relevancia o valor del contenido

### Paso 5: Conversión

Estos son algunos factores importantes para la conversión:

* Todo lo anterior
* Transición del correo electrónico a través de una dirección URL de trabajo a una página de aterrizaje o página de ventas
* Experiencia de la página de aterrizaje
* Reconocimiento, percepción y lealtad de la marca

### Impacto potencial en los ingresos

La conversión es clave, pero ¿cuál es la alternativa? Su estrategia de entrega puede fortalecer o causar estragos en el programa de marketing por correo electrónico. El siguiente gráfico ilustra la pérdida potencial de ingresos que una política de entrega débil puede tener en su programa de marketing. Como se ha demostrado, para una empresa con una tasa de conversión del 2 % y una compra promedio de 100 dólares, cada reducción del 10 % en la llegada a la bandeja de entrada equivale a una pérdida de ingresos de casi 20 000 dólares. Tenga en cuenta que estos números son exclusivos para cada remitente.

| Enviados | Porcentaje | Entregados | Porcentaje | Bandeja de entrada | Número no presente en la bandeja de entrada | Tasa de conversión | Número de pérdidas | Promedio | Pérdidas |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|  | entregados |  | bandeja de entrada |  |  |  | Conversiones | compra | ingresos |
| 100K | 99 % | 99K | 100 % | 99K | - | 2 % | 0 | 100 $ | $ - |
| 100K | 99 % | 99K | 90 % | 89,1K | 9900 | 2 % | 198 | 100 $ | 19 800 $ |
| 100K | 99 % | 99K | 80 % | 79,2K | 19 800 | 2 % | 396 | 100 $ | 39 600 $ |
| 100K | 99 % | 99K | 70 % | 69,3K | 29 700 | 2 % | 594 | 100 $ | 59 400 $ |
| 100K | 99 % | 99K | 60 % | 59,4K | 39 600 | 2 % | 792 | 100 $ | 79 200 $ |
| 100K | 99 % | 99K | 50 % | 49,5K | 49 500 | 2 % | 990 | 100 $ | $99,000 |
| 100K | 99 % | 99K | 40 % | 39,6K | 59 400 | 2 % | 1188 | 100 $ | 118 800 $ |
| 100K | 99 % | 99K | 30 % | 29,7K | 69 300 | 2 % | 1386 | 100 $ | 138 600 $ |
| 100K | 99 % | 99K | 20 % | 19,8K | 79 200 | 2 % | 1584 | 100 $ | 158 400 $ |
