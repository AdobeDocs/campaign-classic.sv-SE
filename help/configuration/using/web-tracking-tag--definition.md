---
title: '"Webbspårningstagg: definition"'
seo-title: '"Webbspårningstagg: definition"'
description: '"Webbspårningstagg: definition"'
seo-description: null
page-status-flag: never-activated
uuid: 915ddfd8-ad1b-41ac-96ed-f7fae687c09f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: b8996508-7173-4225-95e7-b51209aae1f1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3ad288bc983002da82b564e8ab3f4244c6324573

---


# Webbspårningstagg: definition{#web-tracking-tag-definition}

En webbspårningstagg är bara en URL som konstruerats med lämpliga parametrar och som skickats till omdirigeringsservern via en HTTP-fråga.

## Format för de data som ska skickas {#format-of-the-data-to-be-sent}

Formatet för en URL för webbspårning är följande: **https://`<name_of_redirection_server>`:`<port>`/r/`<random_number>`?`<parameters>`**

>[!NOTE]
>
>Det slumpmässiga nummer som läggs till i URL:en undviker problem som uppstår när webbläsare cachelagrar webbsidor.

I följande tabell visas en lista med särskilda parametrar som stöds av omdirigeringsservern.

<table>
                     <thead>
                        <tr>
                           <th>Namn</th>
                           <th>Typ</th>
                           <th>Beskrivning</th> 
                        </tr> 
                     </thead>
                     <tbody>
                        <tr>
                           <td>
                              <p>ID</p> 
                           </td>
                           <td>
                              <p>Sessionscookie</p> 
                           </td>
                           <td>
                              <p>Leverans-ID och mottagaridentifierare.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>uuid230</p> 
                           </td>
                           <td>
                              <p>Permanent cookie</p> 
                           </td>
                           <td>
                              <p>Mottagar-ID (användbart om sessions-cookie saknas).</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>tagid</p> 
                           </td>
                           <td>
                              <p>URL-parameter</p> 
                           </td>
                           <td>
                              <p>Identifierare för spårad webbsida: detta är den enda obligatoriska parametern.</p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>jobid</p> 
                           </td>
                           <td>
                              <p>URL-parameter</p> 
                           </td>
                           <td>
                              <p>Leveransidentifierare som ska användas om det inte finns någon sessionscookie. Detta värde ska uttryckas hexadecimalt.
                              </p> 
                           </td> 
                        </tr>
                        <tr>
                           <td>
                              <p>rcpid</p> 
                           </td>
                           <td>
                              <p>URL-parameter</p> 
                           </td>
                           <td>
                              <p>Parametern som används för att identifiera Internetanvändaren. Den här parameterns format är "name=value", där namnet är ett fält i mottagarschemat. Den här parametern har högre prioritet än identifieraren i sessionens cookie.
                              </p> 
                           </td> 
                        </tr> 
                     </tbody>  
                  </table>

**Några webbspårnings-URL:er**

* Besök en startsida för identifierare

   **https://myserver.adobe.com/r/9862?tagid=home**

* Samla in data om affärsvolym

   **https://myserver.adobe.com/r/4567?tagid=command&amp;amount=100&amp;article=2l**

* Ange ett fält för att hitta mottagaren

   **https://myserver.adobe.com/r/2353?tagid=home&amp;rcpid=saccount%3D10**

   En mottagare vars kontonummer är 10 skickas till startsidan.

* Använda en standardleverans

   **https://myserver.adobe.com/r/2456?tagid=home&amp;jobid=e6**

   En mottagare skickas till startsidan. Den här informationen lagras i leveransen med ID 230 (e6 i databas 16) såvida inte en sessions-cookie som innehåller en leveransidentifierare skickas med den här frågan.

>[!NOTE]
>
>Alla värden som skickas till omdirigeringsservern via URL-parametrar måste vara URL-kodade. Observera att tecknen &#39;=&#39; och &#39;|&#39; är kodade som &#39;%3D&#39; respektive &#39;%7C&#39; i exemplen som anges.

## Dataöverföringsmetoder {#data-transmission-methods}

Följande metoder är möjliga:

* Infoga URL:en i attributet **&quot;src&quot;** för en HTML- **`<img>`** tagg som ingår i webbsidan som du vill spåra.
* Direktanrop till omdirigeringsservern när webbsidan som du vill spåra genereras.

