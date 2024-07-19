---
product: campaign
title: "Användningsexempel: skapa översikter"
description: "Användningsexempel: skapa översikter"
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# Användningsexempel: skapa översiktssidor{#use-cases-creating-overviews}



I följande exempel skapar vi webbprogram av översiktstyp som visar alla webbprogram i din databas. Konfigurera följande element:

* ett filter i mappen (se [Lägga till ett filter i en mapp](#adding-a-filter-on-a-folder)),
* en knapp för att skapa ett nytt webbprogram (se [Lägga till en knapp för att konfigurera ett nytt webbprogram](#adding-a-button-to-configure-a-new-web-application)),
* Detaljvisning för varje post i listan (se [Lägga till detaljer i en lista](#adding-detail-to-a-list)),
* ett filter per länkredigeringsverktyg (se [Skapa ett filter med en länkredigerare](#creating-a-filter-using-a-link-editor)),
* en länk för uppdatering (se [Skapa en länk för uppdatering](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Skapa ett webbprogram med en sida {#creating-a-single-page-web-application}

1. Skapa ett enstaka **[!UICONTROL Page]**-webbprogram och inaktivera utgående övergångar och övergångar till nästa sida.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. Ändrar sidans rubrik.

   Den här titeln visas i översiktshuvudet och i webbprogramöversikten.

1. I webbprogrammets egenskaper ändrar du återgivningen av programmet genom att välja mallen **[!UICONTROL Single-page Web application]**.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Öppna aktiviteten **[!UICONTROL Page]** i webbprogrammet och öppna en lista (**[!UICONTROL Static element > List]**).
1. På fliken **[!UICONTROL Data]** i listan väljer du typ av **[!UICONTROL Web applications]**-dokument och utdatakolumnerna **[!UICONTROL Label]** , **[!UICONTROL Creation date]** och **[!UICONTROL Type of application]**.
1. På underfliken **[!UICONTROL Filter]** skapar du följande filter så som visas nedan för att endast visa webbprogram och exkludera mallar från vyn.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Stäng konfigurationsfönstret på sidan och klicka på **[!UICONTROL Preview]**.

   Listan över webbprogram som finns i din databas visas.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Lägga till ett filter i en mapp {#adding-a-filter-on-a-folder}

I en översikt kan du välja att få åtkomst till data beroende på var de finns i Adobe Campaign-trädet. Det här är ett filter på en mapp. Använd följande process för att lägga till den i översikten.

1. Placera markören på noden **[!UICONTROL Page]** i webbprogrammet och lägg till ett **[!UICONTROL Select folder]**-element (**[!UICONTROL Advanced controls > Select folder]**).
1. Klicka på länken **[!UICONTROL Edit variables]** i fönstret **[!UICONTROL Storage]** som visas.
1. Ändra variabeletiketten efter dina behov.
1. Ändra variabelnamnet med värdet **folder**.

   >[!NOTE]
   >
   >Variabelns namn måste matcha namnet på elementet som är länkat till mappen (definierat i schemat), dvs. **mapp** i det här fallet. Du måste återanvända det här namnet när du refererar till tabellen.

1. Använd typen **[!UICONTROL XML]** för variabeln.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Välj **[!UICONTROL Refresh page]**-interaktionen.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Placera markören i listan och referera till den variabel som tidigare skapats på fliken **[!UICONTROL Folder filter XPath]** i listan på fliken **[!UICONTROL Advanced]**. Du måste använda namnet på elementet som berörs av mapplänken, dvs. **mapp**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >I det här skedet finns webbprogrammet inte i programkontexten och filtret kan därför inte testas i mappen.

## Lägga till en knapp för att konfigurera ett nytt webbprogram {#adding-a-button-to-configure-a-new-web-application}

1. Placera markören på elementet **[!UICONTROL Page]** och lägg till en länk (**[!UICONTROL Static elements > Link]**).
1. Ändra länketiketten eftersom den visas på knappen i översikten.

   I vårt exempel är etiketten **Ny**.

1. Infoga följande URL i URL-fältet: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** sammanfaller med webbprogramschemat.
   >
   >**nms:newWebApp** sammanfaller med den nya guiden för att skapa webbprogram.

1. Välj att visa URL:en i samma fönster.
1. Lägg till webbprogramsikonen i bildfältet: **/nms/img/webApp.png**.

   Den här ikonen visas på knappen **[!UICONTROL New]**.

1. Ange **button** i fältet **[!UICONTROL Style]**.

   Det här formatet refereras till i mallen **[!UICONTROL Single-page Web application]** som du valde tidigare.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Lägga till detaljer i en lista {#adding-detail-to-a-list}

När du konfigurerar en lista i översikten kan du välja att visa ytterligare information för varje post i listan.

1. Placera markören på listelementet som du skapade tidigare.
1. På fliken **[!UICONTROL General]** väljer du visningsläget **[!UICONTROL Columns and additional detail]** i listrutan.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. Lägg till kolumnen **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** och **[!UICONTROL Description]** på fliken **[!UICONTROL Data]** och välj alternativet **[!UICONTROL Hidden field]** för var och en av dem.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   På så sätt visas informationen bara i detalj för varje post.

1. Lägg till följande kod på fliken **[!UICONTROL Additional detail]**:

   ```
   <div class="detailBox">
     <div class="actionBox">
       <span class="action"><img src="/xtk/img/fileEdit.png"/><a title="Open" class="linkAction" href="xtk://open/?schema=nms:webApp&form=nms:webApp&pk=
       <%=webApp.id%>">Open...</a></span>
       <% 
       if( webApp.@appType == 1 ) { //survey
       %>
       <span class="action"><img src="/xtk/img/report.png"/><a target="_blank" title="Reports" class="linkAction" href="/xtk/report.jssp?_context=selection&
         _schema=nms:webApp&_selection=<%=webApp.@id%>
         &__sessiontoken=<%=document.controller.getSessionToken()%>">Reports</a></span>
       <% 
       } 
       %>
     </div>
     <div>
       Internal name: <%= webApp.@internalName %>
     </div>
     <%
     if( webApp.desc != "" )
     {
     %>
     <div>
       Description: <%= webApp.desc %>
     </div>
     <% 
     } 
     %>
   </div>
   ```

>[!NOTE]
>
>Det tar fem minuter att uppdatera JavaScript-bibliotek på servern. Du kan starta om servern för att undvika att vänta på den här fördröjningen.

## Filtrera och uppdatera listan {#filtering-and-updating-the-list}

I det här avsnittet skapar du ett filter för att visa översikten över webbprogram som har skapats av en viss operator. Det här filtret skapas med en ländredigerare. När du har valt en operator kan du uppdatera listan för att använda filtret. Detta kräver att du skapar en uppdateringslänk.

Dessa två element grupperas i samma behållare för att grafiskt grupperas i översikten.

1. Placera markören på elementet **[!UICONTROL Page]** och välj **[!UICONTROL Container > Standard]**.
1. Ange antalet kolumner till **2**, så att länkredigeraren och länken ligger bredvid varandra.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Mer information om elementlayout finns i [det här avsnittet](about-web-forms.md).

1. Använd **prickedFilter**.

   Det här formatet refereras till i mallen **[!UICONTROL Single-page Web application]** som du valde tidigare.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Skapa ett filter med en ländredigerare {#creating-a-filter-using-a-link-editor}

1. Placera markören på den behållare som skapades under föregående steg och infoga en ländredigerare via menyn **[!UICONTROL Advanced controls]**.
1. I lagringsfönstret som öppnas automatiskt väljer du alternativet **[!UICONTROL Variables]**, klickar på länken **[!UICONTROL Edit variables]** och skapar en XML-variabel för att filtrera data.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Ändra etiketten.

   Den visas bredvid fältet **[!UICONTROL Filter]** i översikten.

1. Välj tabellen Operator som ett programschema.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Placera markören på listelementet och skapa ett filter via fliken **[!UICONTROL Data > Filter]**:

   * **Uttryck:** Sekundärnyckel för länken Skapad av
   * **Operator:** är lika med
   * **Värde:** Variabler (variabler)
   * **Ta hänsyn till om:** &#39;$(var2/@id)&#39;!=&#39;&#39;&#39;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Webbprogramanvändaren måste vara en identifierad operator med rätt Adobe Campaign-behörighet för att få tillgång till informationen. Den här typen av konfiguration fungerar inte för anonyma webbprogram.

### Skapa en uppdateringslänk {#creating-a-refresh-link}

1. Placera markören på behållaren och infoga en **[!UICONTROL Link]** via menyn **[!UICONTROL Static elements]**.
1. Ändra etiketten.
1. Välj **[!UICONTROL Refresh data in a list]**.
1. Lägg till listan som skapades tidigare.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Lägg till uppdateringsikonen i fältet **[!UICONTROL Image]**: **/xtk/img/refresh.png**.
1. Med hjälp av sorteringspilarna kan du ordna om de olika elementen i webbprogrammet enligt nedan.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

Webbprogrammet är nu konfigurerat. Du kan förhandsgranska fliken **[!UICONTROL Preview]** genom att klicka på den.

![](assets/s_ncs_configuration_webapp_result.png)
