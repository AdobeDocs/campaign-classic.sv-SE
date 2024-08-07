---
product: campaign
title: Skapa personaliserade PDF-dokument
description: Lär dig generera skräddarsydda PDF-dokument
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Personalization
role: User
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 1%

---

# Skapa personaliserade PDF-dokument{#generating-personalized-pdf-documents}

## Om PDF-dokument med variabel kod {#about-variable-pdf-documents}

Med Adobe Campaign kan du generera variabla PDF-dokument för e-postbilagor från dokument i LibreOffice eller Microsoft Word.

Följande tillägg stöds: .docx, .doc och .odt.

För att personalisera dina dokument finns samma JavaScript-funktioner som för e-postpersonalisering.

Du måste aktivera alternativet **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]**. Det här alternativet är tillgängligt när du bifogar filen till e-postmeddelandet. Mer information om hur du bifogar en beräknad fil finns i avsnittet [Bifoga filer](attaching-files.md).

Exempel på en anpassning av en fakturarubrik:

![](assets/s_ncs_pdf_simple.png)

Om du vill generera dynamiska tabeller eller inkludera bilder via en URL-adress måste du följa en viss process.

## Generera dynamiska tabeller {#generating-dynamic-tables}

Så här genererar du dynamiska tabeller:

* Skapa en tabell med tre rader och så många kolumner som behövs, och konfigurera sedan tabellens layout (kanter osv.).
* Placera markören på tabellen och klicka på menyn **[!UICONTROL Table > Table properties]**. Gå till fliken **[!UICONTROL Table]** och ange ett namn som börjar med **NlJsTable**.
* I den första cellen på den första raden definierar du en slinga (&quot;for&quot;, till exempel) som aktiverar iteration på de värden som du vill visa i tabellen.
* I varje cell på den andra raden i tabellen infogar du skript som returnerar de värden som ska visas.
* Stäng slingan på tabellens tredje och sista rad.

  Exempel på en dynamisk tabelldefinition:

  ![](assets/s_ncs_pdf_table.png)

## Infoga externa bilder {#inserting-external-images}

Det är praktiskt att infoga externa bilder om du t.ex. vill anpassa ett dokument med en bild vars URL anges i ett fält hos mottagaren.

För att göra detta måste du konfigurera ett personaliseringsblock och sedan ta med ett anrop till personaliseringsblocket i den bifogade filen.

**Exempel: infoga en personlig logotyp beroende på mottagarens land**

**Steg 1: skapa den bifogade filen:**

* Infoga anropet till anpassningsblocket: **&lt;%@ include view=&quot;blockname&quot; %>**.
* Infoga innehållet (anpassat eller inte) i filens brödtext.

![](assets/s_ncs_open_office_blocdeperso.png)

**Steg 2: skapa anpassningsblocket:**

* Gå till menyn **[!UICONTROL Resources > Campaign management > Personalization blocks]** i Adobe Campaign-konsolen.
* Skapa ett nytt anpassningsblock för Min logotyp med&quot;Min_logotyp&quot; som internt namn.
* Klicka på länken **[!UICONTROL Advanced parameters...]** och markera sedan alternativet **[!UICONTROL "The content of the block is included in an attachment"]**. Detta gör att du kan kopiera definitionen av anpassningsblocket direkt till innehållet i OpenOffice-filen.

  ![](assets/s_ncs_pdf_bloc_option.png)

  Ni måste skilja på två typer av deklarationer inom personaliseringsblocket:

   * Adobe Campaign-koden för de anpassningsfält för vilka&quot;öppna&quot; och&quot;stängda&quot;-texterna måste ersättas med escape-tecken (`&lt;` respektive `&gt;`).
   * Hela OpenOffice XML-koden kopieras till OpenOffice-dokumentet.

I exemplet ser personaliseringsblocket ut så här:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

Beroende på vilket land mottagaren bor visas personalisering i det dokument som är länkat till leveransen:

![](assets/s_ncs_pdf_result.png)
