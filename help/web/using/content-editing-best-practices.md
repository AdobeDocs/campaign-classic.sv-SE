---
solution: Campaign Classic
product: campaign
title: Bästa praxis för innehållsredigering
description: Bästa praxis för innehållsredigering
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---


# Bästa praxis för innehållsredigering{#content-editing-best-practices}

För att säkerställa att redigeraren fungerar optimalt rekommenderar vi att du följer följande riktlinjer:

* Before **importing an HTML page template** in Adobe Campaign, please make sure the template opens and displays correctly in the various browsers.
* If the HTML page contains **JavaScript scripts**, they need to execute **without errors** outside of the editor.
* När du skapar en mall rekommenderar vi att du lägger till ett **&quot;type&quot;**-attribut till taggar. `<input>` Den här informationen bearbetas av redigeraren och hjälper användaren att länka ett databasfält till formulärfältet när webbprogrammet konfigureras.

   Exempel på HTML-kod i mallen:

   ```
   <input id="email" type="email" name="email"/>
   ```

   Attributet **&#39;type&#39;** är synligt i gränssnittet i följande format:

   ![](assets/dce_sidebar_inputtypechanges.png)

   Den officiella listan med typattribut finns [på den här webbplatsen](https://www.w3schools.com/tags/att_input_type.asp).

* Steg för att simulera en slutsida med DCE:

   ![](assets/dce_enchainement.png)

* Kontrollera att det bara finns en `<body> </body>` på sidan.
* När en CSS- eller JS-fil överförs, överförs inte bilderna i zip-filen. Referenserna till dessa bilder i CSS uppdateras därför inte.

## Format som stöds av Content Editor {#content-editor-supported-formats}

Digital Content Editor stöder HTML-formatet: Du kan när som helst växla till **källäget** .

Importfunktionen i Digital Content Editor fungerar enligt följande med följande format som stöds:

* CSS: bilderna i ZIP-filen importeras inte. Referenserna till de här bilderna i CSS uppdateras inte.
* JS: bilderna i ZIP-filen importeras inte. Referenserna till de här bilderna i JS uppdateras inte.
* Iframe: de länkade sidorna importeras inte.
* Landningssidor och webbprogram: Om en **formulärtagg** saknas visas en varning. En `<form> </form>` måste alltid finnas i meddelandetexten.

Digital Content Editor fungerar även med följande kodsidor som stöds:

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8 (rekommenderas vid användning av en strukturlista)
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>HTML-teckentabellen måste definieras i en metatagg (HTML 4 eller HTML 5) eller i byteordningen. Om ingen teckentabell är tillgänglig öppnar du filen på latin1.

## HTML-innehållsstatus {#html-content-statuses}

I den övre delen av redigeraren visas meddelanden om innehållets status. Färgkoderna för meddelandena är följande:

* **Grått meddelande**: informationsmeddelande, inga åtgärder behöver utföras i redigeraren.
* **Blått meddelande**: informationsmeddelande som rör det innehåll som redigeras.
* **Gult meddelande**: varning eller felmeddelande som kräver åtgärd för användarens räkning.

### Lista över meddelanden när du redigerar ett webbprogram {#list-of-messages-when-editing-a-web-application}

* HTML-innehållet fungerar.
* Webbprogrammet har inte publicerats och går inte att komma åt online.
* Webbprogrammet är online. Publicera igen för att tillämpa ändringarna.
* Sidinnehållet fungerar inte. Det måste innehålla ett HTML-formulär (`<form>`)
* Det finns inga indatazoner eller knappar att konfigurera.
* Om du vill aktivera övergången till nästa sida måste du länka åtgärden Nästa sida till en knapp eller en länk på den aktuella sidan.

### Lista över meddelanden när en leverans redigeras {#list-of-messages-when-editing-a-delivery}

* Leveransinnehållet fungerar
* Det finns inga fält eller anpassningsblock att konfigurera.
* Leveransinnehållet är klart. Kör analysen igen för att tillämpa ändringarna.
* Leveransen är klar att skickas.

