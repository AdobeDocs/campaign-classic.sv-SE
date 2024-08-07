---
product: campaign
title: "Användningsexempel: webbformulär"
description: "Användningsexempel: webbformulär"
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Forms
exl-id: 7aa4646d-1325-47c2-b553-6fe375c48973
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 0%

---

# Användningsfall: webbformulär{#use-cases-web-forms}



## Skapa ett prenumerationsformulär med dubbel anmälan {#create-a-subscription--form-with-double-opt-in}

När du erbjuder informationstjänster måste mottagarna prenumerera för att få all länkad kommunikation. För att undvika felaktig kommunikation och för att säkerställa att mottagaren prenumererar avsiktligt rekommenderar vi att du skickar en bekräftelse på prenumerationen för att skapa en dubbel anmälan. Prenumerationen träder endast i kraft när användaren klickar på länken i bekräftelsemeddelandet.

Det här exemplet baseras på följande scenario:

1. Skapa ett prenumerationsformulär för nyhetsbrev på en webbplats som innehåller en kryssruta för att prenumerera på en tillfällig tjänst. Med den här tjänsten kan du leverera bekräftelsemeddelanden för prenumerationer.
1. Skapa bekräftelseleveransen för prenumerationen med en leveransmall som är länkad till webbformuläret. Den innehåller bekräftelselänken som anropar formuläret för prenumeration på nyhetsbrev och visar ett meddelande om prenumerationsgodkännande.

### Steg 1 - Skapa informationstjänster {#step-1---creating-information-services}

1. Skapa den prenumerationstjänst för nyhetsbrev som ska erbjudas dina mottagare. Mer information om hur du skapar ett nyhetsbrev finns i [det här avsnittet](../../delivery/using/about-services-and-subscriptions.md).

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1.png)

1. Skapa en andra informationstjänst, en tillfällig tjänst som är länkad till en leveransmall för att skicka bekräftelsemeddelanden för prenumerationer.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1c.png)

### Steg 2 - Skapa bekräftelsemeddelanden {#step-2---creating-confirmation-messages}

Bekräftelsemeddelanden skickas via en dedikerad leveransmall som refereras till på tillfällig tjänstnivå.

1. I **[!UICONTROL Explorer]** väljer du **[!UICONTROL Resources > Templates > Delivery templates]**.
1. Skapa en leveransmall för att skicka bekräftelsemeddelanden för prenumerationer.
1. Klicka på knappen **[!UICONTROL To]** i **[!UICONTROL Email parameters]** för att associera leveransmallen med målmappningen för prenumerationer i stället för mottagare.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1d.png)

1. Eftersom mottagarna av den här leveransen inte har bekräftat sitt godkännande finns de fortfarande på blockeringslista i databasen. För att de ska kunna ta emot det här meddelandet måste du godkänna leveranser som baseras på den här mallen för att rikta sig till mottagare på blockeringslista.

   Klicka på fliken **[!UICONTROL Exclusions]** om du vill göra det.

1. Klicka på länken **[!UICONTROL Edit...]** och avmarkera alternativet **[!UICONTROL Exclude recipients who no longer want to be contacted]**.

   <!-- ![](assets/s_ncs_admin_survey_double-opt-in_sample_4d.png)-->

   >[!IMPORTANT]
   >
   >Det här alternativet kan endast inaktiveras i den här typen av sammanhang.

1. Anpassa leveransen och infoga bekräftelselänken i meddelandeinnehållet. Med den här länken kan du komma åt webbformuläret och registrera en prenumerationsbekräftelse.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_1b.png)

1. Länka URL:en till webbformuläret med DCE. Eftersom webbformuläret inte har skapats ännu bör du ersätta värdet så snart du har skapat det.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3.png)

1. Länka slutligen den här mallen till den temporära tjänst som skapades tidigare.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_3c.png)

### Steg 3 - Skapa prenumerationsformuläret {#step-3---creating-the-subscription-form}

Webbformuläret innehåller funktioner för både mottagarens prenumeration och prenumerationsbekräftelse.

Arbetsflödet för webbformulär kommer att innehålla följande aktiviteter:

![](assets/s_ncs_admin_survey_double-opt-in_sample_4c.png)

Gör så här:

1. Skapa ett webbformulär och välj mallen **[!UICONTROL Newsletter subscription (subNewsletter)]**.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5a.png)

1. På fliken **[!UICONTROL Edit]** måste vi konfigurera det befintliga arbetsflödet eftersom vi vill lägga till ett bekräftelsemeddelande till mottagarna som vill prenumerera.

   Om du vill göra det dubbelklickar du på rutan **[!UICONTROL Preloading]** och konfigurerar den enligt följande.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5b.png)

   Det innebär att om användaren öppnar formuläret via länken i bekräftelsemeddelandet, läses profilinformationen in. Om de öppnar webbformuläret via en sida på webbplatsen läses ingen information in.

1. Lägg till en **[!UICONTROL Test]**-aktivitet i arbetsflödet.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6e.png)

   Aktiviteten **[!UICONTROL Test]** kan beröra mottagarens e-postadress. I det här fallet ska du konfigurera det på följande sätt:

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6d.png)

1. Lägg till två **[!UICONTROL Script]** aktiviteter i ditt arbetsflöde.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6f.png)

   Den första **[!UICONTROL Script]**-aktiviteten lägger till mottagare på blockeringslista tills de har bekräftat sin prenumeration på nyhetsbrevet. Innehållet ska vara följande:

   ```
   ctx.recipient.@blackList=1
   ```

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6bbis.png)

   Den andra **[!UICONTROL Script]**-aktiviteten tillåter att leveranser skickas till användarna och prenumererar på dem i nyhetsbrevet. De sista två raderna i skriptet gör att du kan överföra dina mottagare från den tillfälliga mappen till en annan mapp och stämma av med befintliga profiler så fort de har bekräftat prenumerationen.

   ```
   ctx.recipient.@blackList=0
   nms.subscription.Subscribe("INTERNAL_NAME_OF_THE_NEWSLETTER", ctx.recipient, false)
   ctx.recipient.folder = <folder name="nmsRootRecipient"/>
   nms.subscription.Unsubscribe("TEMP", ctx.recipient)
   ```

   >[!NOTE]
   >
   >Partitionen **[!UICONTROL Temp]** kan även rensas regelbundet med hjälp av ett arbetsflöde.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_6b.png)

1. Dubbelklicka på aktiviteten **[!UICONTROL Subscription]** för att anpassa prenumerationsformuläret och länka en kryssruta till den tillfälliga tjänst som skapats tidigare.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5c.png)

1. Konfigurera aktiviteten **[!UICONTROL Storage]** för att spara informationen som anges på formulärsidan.

   Med den här aktiviteten kan du skapa mottagarprofiler i en dedikerad tillfällig mapp för att skilja dem från profilerna i databasen som kommunikationen kan skickas till.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5g.png)

   >[!NOTE]
   >
   >Du får inte definiera några avstämningsalternativ.

1. Lägg till två **[!UICONTROL End]** aktiviteter för att visa ett meddelande för användaren.

   I den andra **[!UICONTROL End]**-rutan visas bekräftelsemeddelandet när prenumerationen är klar.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_5h.png)

1. När webbformuläret har skapats och konfigurerats kan du nu referera till det i leveransmallen för att skicka bekräftelsemeddelanden.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_7b.png)

### Steg 4 - Publicera och testa formuläret {#step-4---publishing-and-testing-the-form}

Nu kan du publicera formuläret så att det blir tillgängligt för användarna.

![](assets/s_ncs_admin_survey_double-opt-in_sample_8b.png)

Prenumerationen på nyhetsbrevet omfattar följande steg:

1. Webbplatsens användare loggar in på prenumerationssidan och godkänner formuläret.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8c.png)

   De meddelas via ett meddelande i webbläsaren att deras begäran har beaktats.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8d.png)

   Användaren läggs till i Adobe Campaign-databasen i mappen **[!UICONTROL Temp]** och deras profil är på blockeringslista tills de bekräftar sin prenumeration med e-postmeddelandet.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8f.png)

1. Ett bekräftelsemeddelande med en länk för att godkänna prenumerationen skickas till dem.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8e.png)

1. När de klickar på den här länken visas godkännandesidan i webbläsaren.

   ![](assets/s_ncs_admin_survey_double-opt-in_sample_8.png)

   I Adobe Campaign uppdateras användarprofilen:

   * de inte längre är på blockeringslista,
   * de prenumererar på informationstjänsten.

     ![](assets/s_ncs_admin_survey_double-opt-in_sample_9.png)

## Visa olika alternativ beroende på de valda värdena {#displaying-different-options-depending-on-the-selected-values}

I följande exempel ombeds användaren att välja en fordonstyp. Du kan visa tillgängliga fordonskategorier beroende på vilken typ som valts. Det innebär att de objekt som visas i den högra kolumnen beror på användarens val:

![](assets/s_ncs_admin_survey_condition_sample0.png)

* När användaren väljer &quot;privat fordon&quot; erbjuds valet mellan &quot;Compact&quot; och &quot;Minivan&quot;.

  ![](assets/s_ncs_admin_survey_condition_sample2.png)

* När användaren väljer &quot;nyttofordon&quot; visas ett urval i en nedrullningsbar lista:

  ![](assets/s_ncs_admin_survey_condition_sample1.png)

I det här exemplet lagras inte fordonstypen i databasen. Listrutan är konfigurerad enligt följande:

![](assets/s_ncs_admin_survey_condition_config1.png)

Informationen lagras i en lokal variabel.

Den högra kolumnens villkorliga visning är konfigurerad i behållarna:

![](assets/s_ncs_admin_survey_condition_config1bis.png)

* Villkorlig synlighet för fält för ett privat fordon:

  ![](assets/s_ncs_admin_survey_condition_config2.png)

* Villkorlig synlighet för fälten för ett nyttofordon:

  ![](assets/s_ncs_admin_survey_condition_config3.png)
