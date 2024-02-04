---
source-git-commit: 5de602d6b75e524dac8688e40db0e96bdbafceba
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 8%

---
### Creación de reglas de tipología para admitir la cancelación de suscripción a una lista de un clic:

**1. Cree la nueva regla de tipología:**

* En el árbol de navegación, haga clic en &quot;nuevo&quot; para crear una nueva tipología


![Imagen](/help/assets/CreatingTypologyRules1.png)



**2. Continúe con la configuración de la regla de tipología:**

* Tipo de regla: Control
* Fase: al principio del objetivo
* Canal: correo electrónico
* Nivel: su elección
* Activo


![Imagen](/help/assets/CreatingTypologyRules2.png)


**Codifique el javascript de la regla de tipología:**


>[!NOTE]
>
>Se debe hacer referencia al código que se describe a continuación solo como ejemplo.
>Este ejemplo detalla cómo:
>* Configure una URL con List-Unsubscribe y añadirá los encabezados o anexará los parámetros mailto: existentes y lo sustituirá por: &lt;mailto..>>, https://...
>* Añadir en el encabezado List-Unsubscribe-Post
>El ejemplo de la URL de publicación utiliza var headerUnsubUrl = &quot;https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;÷
>* Puede agregar otros parámetros (como &amp;service = ...)
>


```
// Function to add or replace a header in the provided headers 
function addHeader(headers, header, value)  { 
    
  // Create the new header line 
  var headerLine = header + ": " + value; 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop through each line 
  for (var i=0; i < headerLines.length; i++) { 
      
    // Check if the specified header exists 
    var match = headerLines[i].match(regExp) 
      
    // If it exists 
    if ( match != null ) { 
        
      // Replace the existing header line 
      headerLines[i] = headerLine; 
        
      // Return the modified headers 
      return headerLines.join("\n"); 
    } 
  } 
    
  // If the header does not exist, add the new header line 
  headerLines.push(headerLine); 
    
  // Return the modified headers 
  return headerLines.join("\n"); 
} 
  
// Function to get the value of a specified header from the provided headers 
function getHeader(headers, header) { 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop each line 
  for each (line in headerLines) { 
      
    // Check if the specified header exists 
    var match = line.match(regExp); 
      
    // If it exists 
    if ( match != null ) { 
        
      // Return the header value, removing leading whitespace 
      return match[1].replace(/^\s*/, ""); 
    } 
  } 
    
  // If the header does not exist, return an empty string 
  return ""; 
} 
  
  
// Define the unsubscribe URL 
var headerUnsubUrl = "https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
// Get the value of the List-Unsubscribe header 
var headerUnsub = getHeader(delivery.mailParameters.headers, "List-Unsubscribe"); 
  
// If the List-Unsubscribe header does not exist 
if ( headerUnsub === "" ) { 
  // Add the List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
// If the List-Unsubscribe header exists and contains 'mailto' 
else if(headerUnsub.search('mailto')){ 
  // Replace the existing List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
  
// Get the value of the List-Unsubscribe-Post header 
var headerUnsubPost = getHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post"); 
  
// If the List-Unsubscribe-Post header does not exist 
if ( headerUnsubPost === "" ) { 
  // Add the List-Unsubscribe-Post header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post", "List-Unsubscribe=One-Click"); 
} 
  
// Return true to indicate success 
return true; 
```


![Imagen](/help/assets/CreatingTypologyRules3.png)



**3. Añada la nueva regla a una tipología a un correo electrónico (la tipología predeterminada es correcta):**

![Imagen](/help/assets/CreatingTypologyRules4.png)



**4. Preparar un nuevo envío (compruebe que los encabezados SMTP adicionales de la propiedad de envío estén vacíos)**

![Imagen](/help/assets/CreatingTypologyRules5.png)



**5. Compruebe durante la preparación de la entrega que se ha aplicado la nueva regla de tipología.**

![Imagen](/help/assets/CreatingTypologyRules6.png)



**6. Compruebe que la cancelación de la suscripción a una lista esté presente.**

![Imagen](/help/assets/CreatingTypologyRules7.png)
