---
product: campaign
title: Skapa en landningssida
description: Skapa en landningssida
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Landing Pages
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 2%

---

# Skapa en landningssida{#creating-a-landing-page}



## Skapa landningssidor {#about-landing-pages-creation}

I det här exemplet visas hur du använder Digital Editor för att skapa en landningssida från Adobe Campaign-konsolen.

Innan du börjar konfigurera landningssidan i Adobe Campaign måste du kontrollera att du har **en eller flera mallar** som representerar HTML-sidorna.

Huvudsyftet med det här användningsexemplet är att göra så att formulärfälten för landningssidan motsvarar de interna fälten i Adobe Campaign med funktionerna i DCE.

## Skapa landningssidan {#creating-the-landing-page}

Så här skapar du ett nytt webbprogram av typen Landing Page:

1. Gå till fliken **[!UICONTROL Campaigns]**, klicka på länken **[!UICONTROL Web application]** och klicka sedan på knappen **[!UICONTROL Create]**.
1. Välj mallen **[!UICONTROL New landing page]**, ange en etikett och klicka sedan på **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. Klicka på fliken **[!UICONTROL Edit]**.
1. Ta bort aktiviteten **End**.
1. Lägg till en **[!UICONTROL Page]**-aktivitet efter aktiviteten **[!UICONTROL Storage]**.
1. Redigera aktiviteten **Sida 2** och avmarkera sedan alternativet **[!UICONTROL Activate outbound transitions]** på fliken **[!UICONTROL Properties]**.

   ![](assets/dce_uc1_transition.png)

1. Spara ändringar.

Du får sedan följande sekvensering:

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>Mer information om hur du skapar ett webbprogram finns i [det här avsnittet](creating-a-new-web-application.md).

## Steg 1 - Välja och läsa in mallar {#step-1---selecting-and-loading-templates}

I det här avsnittet ska vi titta på hur du **importerar HTML-innehåll** för varje sida i webbprogrammet.

En mall måste innehålla:

* en **HTML**-fil (obligatorisk)
* en eller flera **CSS**-filer (valfritt)
* en eller flera **bilder** (valfritt)

Så här läser du in mallen på den första sidan:

1. Öppna den första **[!UICONTROL Page]** aktiviteten i webbprogrammet.
1. Välj **[!UICONTROL From a file]** om du vill hämta innehållsmallen.

   ![](assets/dce_uc1_selectmodel.png)

1. Markera den HTML-fil som ska användas.
1. Klicka på **Öppna** för att starta importen.

   Under inläsningen visas listan med delade filer. Importsystemet kontrollerar att alla filer som är länkade till det markerade HTML finns där (CSS, bilder osv.).

   Klicka på knappen **[!UICONTROL Close]** när importen är klar.

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >Du måste vänta tills du får följande meddelande innan du stänger: **[!UICONTROL The external resources have been successfully published]**.

1. Klicka på fliken **[!UICONTROL Properties]**.
1. Ange en **etikett** för varje sida (till exempel: Sida 1= Samla in, Sida 2=Tack).

   ![](assets/dce_uc1_pagelabel.png)

Använd dessa steg för varje sida som infogas i webbprogrammet.

>[!CAUTION]
>
>**DCE kör JavaScript-koden för den inlästa HTML-sidan.** JavaScript-fel i HTML-mallen som kan visas i Adobe Campaign-gränssnittet. Felen är inte relaterade till redigeraren. Om du vill kontrollera att det inte finns några fel i de importerade filerna rekommenderar vi att du testar dem i en webbläsare innan du importerar filerna till DCE.

## Steg 2 - Konfigurera innehållet {#step-2---configuring-the-content}

I det här avsnittet ska vi justera importerat innehåll och länka databasens fält till webbsidans format. Det webbprogram som skapats tidigare är:

![](assets/dce_uc1_lp_enchainement.png)

### Ändra innehåll {#modifying-content}

Vi börjar med att ändra sidans färger. Så här gör du:

1. Öppna sidan **[!UICONTROL Collection]**.
1. Klicka på bakgrunden.
1. Klicka på **Bakgrundsfärg** till höger.
1. Välj en ny bakgrundsfärg.
1. Bekräfta ändringen genom att klicka på **OK**.

   ![](assets/dce_uc1_changecolor.png)

1. Använd samma processer för att ändra färg på knappen

   ![](assets/dce_uc1_finalcolor.png)

### Länka formulärfält {#linking-form-fields}

Vi kommer att länka fälten på sidan till fälten i databasen för att spara den angivna informationen.

1. Välj ett formulärfält.
1. Redigera avsnittet **[!UICONTROL Field]** till höger om redigeraren.
1. Markera det databasfält som du vill länka till det markerade fältet.

   ![](assets/dce_uc1_mapping.png)

1. Upprepa den här processen för varje fält på sidan.

Du kan göra ett fält obligatoriskt: klicka till exempel på fältet **[!UICONTROL Email]** och aktivera alternativet **Obligatoriskt**.

![](assets/dce_uc1_fieldmandatory.png)

### Skapa en länk till nästa sida {#creating-a-link-to-the-next-page}

Det här steget är obligatoriskt eftersom det gör att webbprogrammet kan bestämma sekvensen för nästa steg: Spara insamlade data i databasen och sedan visa nästa sida (**Tack** -sidan).

1. Välj knappen **[!UICONTROL Send it!]** på sidan **[!UICONTROL Collection]**.
1. Klicka på listrutan **[!UICONTROL Action]**.
1. Välj åtgärden **[!UICONTROL Next page]**.

   ![](assets/dce_uc1_actionbouton.png)

### Infoga ett anpassningsfält {#inserting-a-personalization-field}

I det här steget kan du anpassa sidan Tack. Så här gör du:

1. Öppna sidan **[!UICONTROL Thank you]**.
1. Placera markören i ett textområde där du vill infoga mottagarens förnamn.
1. Välj **[!UICONTROL Personalization field]** på menyn **[!UICONTROL Insert]** i verktygsfältet.
1. Markera förnamnet.

   ![](assets/dce_uc1_persochamp.png)

Anpassningsfältet har en gul bakgrund i redigeraren.

![](assets/dce_uc1_edit_champperso.png)

## Steg 3 - Publicera innehåll {#step-3---publishing-content}

Innehållet publiceras från webbprogrammets kontrollpanel. Klicka på knappen **[!UICONTROL Publish]** för att köra den.

![](assets/dce_uc1_pub_dashboard.png)

Under publiceringen visas en logg. Publiceringssystemet analyserar allt innehåll som finns i webbprogrammet

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>I publiceringsloggen sorteras varningar och fel efter aktivitet.

Formuläret är nu tillgängligt: URL:en är tillgänglig på kontrollpanelen för programmet och kan skickas till mottagarna.
