---
product: campaign
title: Avanmälan för försäljning av personuppgifter
description: Läs mer om avanmälan för försäljning av personuppgifter
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 8e308a9f-14a4-4a25-9fd0-8d4bdbcf74ce
source-git-commit: 42b420d7dae7d38e9f4df442146d3b484c25e831
workflow-type: ht
source-wordcount: '554'
ht-degree: 100%

---

# Avanmäl dig till försäljning av personuppgifter (CCPA) {#sale-of-personal-information-ccpa}

![](../../assets/common.svg)

**CCPA (California Consumer Privacy Act)** ger personer bosatta i Kalifornien nya rättigheter när det gäller deras personuppgifter och ålägger vissa företag som bedriver verksamhet i Kalifornien skyldigheter när det gäller uppgiftsskydd.

Konfigurationen och användningen av förfrågningar gällande åtkomst och borttagning är gemensamma för både GDPR och CCPA. Det här avsnittet presenterar avanmälan för försäljning av personuppgifter vilken är specifik för CCPA.

Förutom verktygen för [medgivandehantering](privacy-management.md#consent-management) som finns i Adobe Campaign har du möjligheten att spåra om en konsument har avanmält sig till försäljning av personuppgifter.

Kontakter kan via ditt system bestämma att de inte tillåter att deras personuppgifter säljs till tredje part. I Adobe Campaign kan du lagra och spåra den här informationen.

För att det här ska fungera måste du utöka profiltabellen och lägga till ett **[!UICONTROL Opt-Out for CCPA]**-fält.

>[!IMPORTANT]
>
>Det är ditt ansvar som personuppgiftsansvarig att ta emot den registrerades förfrågan och att hålla reda på förfrågningsdatum för CCPA. Som teknikleverantör erbjuder vi bara ett sätt att avanmäla sig. Mer information om din roll som personuppgiftsansvarig finns i [Personuppgifter och personer](privacy-and-recommendations.md#personal-data).

## Förutsättning {#ccpa-prerequisite}

För att kunna dra nytta av den här informationen måste du skapa det här fältet i Adobe Campaign Classic. För det här ska du lägga till ett booleskt fält i tabellen **[!UICONTROL Recipient]**. När ett nytt fält skapas stöds det automatiskt av API:et i Campaign.

Du måste också utföra den här åtgärden, om du använder en anpassad mottagartabell 

Mer detaljerad information om hur du skapar ett nytt fält finns i [schemadokumentationen](../../configuration/using/about-schema-edition.md).

>[!IMPORTANT]
>
>Att ändra schema är en känslig åtgärd som endast får utföras av expertanvändare.

1. Gå till **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Add new fields]**, välj **[!UICONTROL Recipients]** som **[!UICONTROL Document type]** och klicka på **[!UICONTROL Next]**. Mer information om hur du lägger till fält i en tabell finns i [det här avsnittet](../../configuration/using/new-field-wizard.md).

   ![](assets/privacy-ccpa-1.png)

1. Välj **[!UICONTROL SQL field]** för **[!UICONTROL Field type]**. Använd **[!UICONTROL Opt-Out for CCPA]** som etikett. Välj typen **[!UICONTROL 8-bit integer (boolean)]** och definiera följande unika **[!UICONTROL Relative path]**: @OPTOUTCCPA. Klicka på **[!UICONTROL Finish]**.

   ![](assets/privacy-ccpa-2.png)

   Det här utökar eller skapar schemat **[!UICONTROL Recipient (cus)]**. Kontrollera att fältet har lagts till korrekt genom att klicka på det.

   ![](assets/privacy-ccpa-3.png)

1. Klicka på noden **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** i Utforskaren. Lägg till ett `<input>`-element i **[!UICONTROL Recipient (nms)]** under General Package och använd den relativa sökvägen som definieras i steg 2 för xpath-värdet. Mer information om att identifiera ett formulär finns i [det här avsnittet](../../configuration/using/identifying-a-form.md).

   ```
   <input  colspan="2" type="checkbox" xpath="@OPTOUTCCPA"/>
   ```

   ![](assets/privacy-ccpa-4.png)

1. Koppla från och återanslut. Följ stegen som beskrivs i nästa avsnitt för att verifiera att fältet är tillgängligt i mottagarinformationen.

## Användning {#usage}

Det är den personuppgiftsansvariges ansvar att fylla i fältets värde och följa CCPA:s riktlinjer och regler för försäljning av personuppgifter.

Du kan använda flera olika metoder för att fylla i värdena:

* Använda gränssnittet i Campaign genom att redigera mottagarinformationen
* Använda API:et
* Via ett arbetsflöde för dataimport

Du ska sedan se till att du aldrig säljer personuppgifter, från profiler som har avanmält sig, till någon tredje part.

1. Om du vill ändra avanmälningsstatus går du till **[!UICONTROL Profiles and Target]** > **[!UICONTROL Recipients]** och väljer en mottagare. På fliken **[!UICONTROL General]** ser du fältet som konfigurerades i föregående avsnitt.

   ![](assets/privacy-ccpa-5.png)

1. Konfigurera mottagarlistan så att avanmälningskolumnen visas. Mer information om hur du konfigurerar listor finns i den [detaljerade dokumentationen](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

   ![](assets/privacy-ccpa-6.png)

1. Du kan klicka på kolumnen för att sortera mottagare enligt avanmälningsinformationen. Du kan också skapa ett filter så att endast mottagare som har avanmält sig visas. Mer information om att skapa filter finns i [det här avsnittet](../../platform/using/creating-filters.md).

   ![](assets/privacy-ccpa-7.png)
