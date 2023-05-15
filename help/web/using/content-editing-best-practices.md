---
product: campaign
title: Bästa praxis för innehållsredigering
description: Bästa praxis för innehållsredigering
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Apps, Web Forms, Landing Pages
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---

# Bästa praxis för innehållsredigering{#content-editing-best-practices}



För att säkerställa att redigeraren fungerar optimalt rekommenderar vi att du följer följande riktlinjer:

* Före **importera en sidmall för HTML** i Adobe Campaign kontrollerar du att mallen öppnas och visas korrekt i de olika webbläsarna.
* Om HTML-sidan innehåller **JavaScript-skript** måste de köra **utan fel** utanför redigeraren.
* När du skapar en mall rekommenderar vi att du lägger till ett **&quot;type&quot;**-attribut till taggar. `<input>` Den här informationen bearbetas av redigeraren och hjälper användaren att länka ett databasfält till formulärfältet när webbprogrammet konfigureras.

   Exempel på HTML-kod i mallen:

   ```
   <input id="email" type="email" name="email"/>
   ```

   The **type** -attributet är synligt i gränssnittet i följande format:

   ![](assets/dce_sidebar_inputtypechanges.png)

   Den officiella listan med type-attribut är tillgänglig [på denna webbplats](https://www.w3schools.com/tags/att_input_type.asp).

* Steg för att simulera en slutsida med DCE:

   ![](assets/dce_enchainement.png)

* Se till att det bara finns en `<body> </body>` på sidan.
* När en CSS- eller JS-fil överförs, överförs inte bilderna i zip-filen. Referenserna till dessa bilder i CSS uppdateras därför inte.

## Format som stöds av Content Editor {#content-editor-supported-formats}

Digital Content Editor stöder HTML-formatet: du kan växla till **källa** -läget när som helst.

Importfunktionen i Digital Content Editor fungerar enligt följande med följande format som stöds:

* CSS: bilderna i ZIP-filen importeras inte. Referenserna till de här bilderna i CSS uppdateras inte.
* JS: bilderna i ZIP-filen importeras inte. Referenserna till de här bilderna i JS uppdateras inte.
* Iframe: de länkade sidorna importeras inte.
* Landningssidor och webbprogram: om **formulär** -taggen saknas, en varning visas. A `<form> </form>` måste alltid finnas i meddelandetexten.

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
>Kodsidan för HTML måste definieras i en metatagg (HTML 4 eller HTML 5) eller i byteordningsmärken. Om ingen teckentabell är tillgänglig öppnar du filen på latin1.

## HTML innehållsstatus {#html-content-statuses}

I den övre delen av redigeraren visas meddelanden om innehållets status. Färgkoderna för meddelandena är följande:

* **Grått meddelande**: informationsmeddelande, inga åtgärder behöver utföras i redigeraren.
* **Blått meddelande**: informationsmeddelande som rör det innehåll som redigeras.
* **Gult meddelande**: varning eller felmeddelande som kräver åtgärd för användarens räkning.

### Lista över meddelanden när du redigerar ett webbprogram {#list-of-messages-when-editing-a-web-application}

* Innehållet i HTML fungerar.
* Webbprogrammet har inte publicerats och går inte att komma åt online.
* Webbprogrammet är online. Publicera igen för att tillämpa ändringarna.
* Sidinnehållet fungerar inte. Den måste innehålla ett HTML-formulär (`<form>`)
* Det finns inga indatazoner eller knappar att konfigurera.
* Om du vill aktivera övergången till nästa sida måste du länka åtgärden Nästa sida till en knapp eller en länk på den aktuella sidan.

### Lista över meddelanden när en leverans redigeras {#list-of-messages-when-editing-a-delivery}

* Leveransinnehållet fungerar
* Det finns inga fält eller anpassningsblock att konfigurera.
* Leveransinnehållet är klart. Kör analysen igen för att tillämpa ändringarna.
* Leveransen är klar att skickas.
