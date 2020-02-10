---
title: Innehållshantering
seo-title: Innehållshantering
description: Innehållshantering
seo-description: null
page-status-flag: never-activated
uuid: 8d1bf84b-96e5-4d3d-9d77-42d2027a74db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 13b72aa1-de40-4548-835b-97e765e04e95
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Innehållshantering{#content-management}

Med en **innehållshanteringsaktivitet** kan du skapa och ändra ett innehåll och generera filer baserat på det här innehållet. Innehållet kan sedan levereras via en &#39;Delivery&#39;-aktivitet.

>[!CAUTION]
>
>Innehållshantering är en valfri Adobe Campaign-modul. Kontrollera licensavtalet.

Aktivitetens egenskaper är uppdelade i tre steg:

* **Val** av innehåll: innehållet kan ha skapats tidigare eller kan skapas via aktiviteten.
* **Innehållsuppdatering**: uppgiften kan ändra innehållet eller importera allt XML-innehåll.
* **Åtgärd**: det slutliga innehållet kan sparas eller genereras.

   ![](assets/content_mgmt_edit.png)

   Mer information om hur du konfigurerar och använder innehållshantering i Adobe Campaign finns i det här [avsnittet](../../delivery/using/about-content-management.md).

1. **Innehåll**

   * **[!UICONTROL Specified in the transition]**

      Med det här alternativet kan du använda innehållet som anges i övergången, d.v.s. händelsen som aktiverar innehållshantering måste innehålla en **[!UICONTROL contentId]** variabel. Den här variabeln kan ha angetts av en tidigare innehållshantering eller av ett skript.

   * **[!UICONTROL Explicit]**

      Med det här alternativet kan du välja innehåll som redan har skapats via **[!UICONTROL Content]** fältet. Det här fältet är bara synligt när du har valt **[!UICONTROL Explicit]** alternativet.

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      Innehållsidentifieraren beräknas av ett skript. I **[!UICONTROL Script]** fältet kan du definiera en JavaScript-mall som utvärderar innehållets identifierare (primärnyckel). Det här fältet är bara synligt när du har valt **[!UICONTROL Calculated by a script]** alternativet.

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      Skapar ett nytt innehåll från en publiceringsmall. Det nya innehållet sparas i filen som anges i **[!UICONTROL String]** fältet. I **[!UICONTROL Template]** fältet anges den publiceringsmall som ska användas för att skapa innehållet.

      ![](assets/content_mgmt_new.png)

1. **Uppdatera innehåll**

   * **[!UICONTROL Subject]**

      I det här fältet kan du ändra innehållets ämne.

   * **[!UICONTROL Access to data from an XML feed]**

      Med det här alternativet kan du skapa innehåll från ett XML-dokument som hämtats via en XSL-formatmall. När det här alternativet är markerat anger **[!UICONTROL URL]** fältet URL:en för hämtning av XML-innehåll. Här **[!UICONTROL XSL stylesheet]** kan du ange vilken formatmall som ska användas för att omforma det hämtade XML-dokumentet. Den här egenskapen är valfri.

      ![](assets/content_mgmt_xmlcontent.png)

1. **Åtgärd som ska köras**

   * **[!UICONTROL Save]**

      Med det här alternativet sparas det skapade eller ändrade innehållet.

      Den utgående övergången aktiveras bara en gång, med innehållet sparat i **[!UICONTROL contentId]** variabeln som en parameter.

   * **[!UICONTROL Generate]**

      Det här alternativet sparar innehållet och genererar sedan utdatafilerna för varje omformningsmall med en publikation av typen File.

      ![](assets/content_mgmt_generate.png)

      Den utgående övergången aktiveras för varje fil som skapas med identifieraren för det innehåll som sparas i variabeln som dess parameter och filnamnet i **[!UICONTROL contentId]** **[!UICONTROL filename]** variabeln.

## Indataparametrar {#input-parameters}

* contentId

Identifierare för det innehåll som ska användas om **[!UICONTROL Specified in the transition]** alternativet är aktiverat.

## Utdataparametrar {#output-parameters}

* contentId

   Innehållsidentifierare.

* filnamn

   Det fullständiga namnet på den genererade filen om den valda åtgärden är **[!UICONTROL Generate]**.

## Exempel {#examples}

Exempel finns i det här [avsnittet](../../delivery/using/automating-via-workflows.md#examples).
