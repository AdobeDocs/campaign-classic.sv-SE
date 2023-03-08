---
product: campaign
title: "Användningsfall: skapa översikter"
description: "Användningsfall: skapa översikter"
feature: Web Apps
exl-id: a1ac3aab-dc81-4533-9207-26d5dc5e1c88
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Användningsexempel: skapa översiktssidor{#use-cases-creating-overviews}

![](../../assets/common.svg)

I följande exempel skapar vi webbprogram av översiktstyp som visar alla webbprogram i din databas. Konfigurera följande element:

* ett filter för mappen (se [Lägga till ett filter i en mapp](#adding-a-filter-on-a-folder)),
* en knapp för att skapa ett nytt webbprogram (se [Lägga till en knapp för att konfigurera ett nytt webbprogram](#adding-a-button-to-configure-a-new-web-application)),
* detaljvisning för varje post i listan (se [Lägga till detaljer i en lista](#adding-detail-to-a-list)),
* ett filter per länkredigeringsverktyg (se [Skapa ett filter med en ländredigerare](#creating-a-filter-using-a-link-editor)),
* en uppdateringslänk (se [Skapa en uppdateringslänk](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Skapa ett webbprogram med en sida {#creating-a-single-page-web-application}

1. Skapa en **[!UICONTROL Page]** Webbprogram och inaktivera utgående övergångar och övergångar till nästa sida.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. Ändrar sidans rubrik.

   Den här titeln visas i översiktshuvudet och i webbprogramöversikten.

1. I webbprogrammets egenskaper ändrar du återgivningen av programmet genom att välja **[!UICONTROL Single-page Web application]** mall.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Öppna **[!UICONTROL Page]** webbprogrammets aktivitet och öppna en lista (**[!UICONTROL Static element > List]**).
1. I **[!UICONTROL Data]** väljer du typ av **[!UICONTROL Web applications]** -dokument och **[!UICONTROL Label]** , **[!UICONTROL Creation date]** och **[!UICONTROL Type of application]** utdatakolumner.
1. I **[!UICONTROL Filter]** skapar du följande filter så som visas nedan för att endast visa webbprogram och utesluta mallar från vyn.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Stäng konfigurationsfönstret på sidan och klicka på **[!UICONTROL Preview]**.

   Listan över webbprogram som finns i din databas visas.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Lägga till ett filter i en mapp {#adding-a-filter-on-a-folder}

I en översikt kan du välja att få åtkomst till data beroende på var de finns i Adobe Campaign-trädet. Det här är ett filter på en mapp. Använd följande process för att lägga till den i översikten.

1. Placera markören på **[!UICONTROL Page]** nod i webbprogrammet och lägg till en **[!UICONTROL Select folder]** element (**[!UICONTROL Advanced controls > Select folder]**).
1. I **[!UICONTROL Storage]** klickar du på **[!UICONTROL Edit variables]** länk.
1. Ändra variabeletiketten så att den passar dina behov.
1. Ändra variabelnamnet med **mapp** värde.

   >[!NOTE]
   >
   >Variabelns namn måste matcha namnet på elementet som är länkat till mappen (definierat i schemat), dvs. **mapp** i detta fall. Du måste återanvända det här namnet när du refererar till tabellen.

1. Använd **[!UICONTROL XML]** till variabeln.

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Välj **[!UICONTROL Refresh page]** interaktion.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Placera markören i listan och i **[!UICONTROL Advanced]** -fliken, referera till variabeln som tidigare skapats i **[!UICONTROL Folder filter XPath]** -fliken i listan. Du måste använda namnet på elementet som berörs av mapplänken, dvs. **mapp**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >I det här skedet finns webbprogrammet inte i programkontexten och filtret kan därför inte testas i mappen.

## Lägga till en knapp för att konfigurera ett nytt webbprogram {#adding-a-button-to-configure-a-new-web-application}

1. Placera markören på **[!UICONTROL Page]** element och lägga till en länk (**[!UICONTROL Static elements > Link]**).
1. Ändra länketiketten eftersom den visas på knappen i översikten.

   I vårt exempel är etiketten **Nytt**.

1. Infoga följande URL i URL-fältet: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** sammanfaller med webbprogrammets schema.
   >
   >**nms:newWebApp** sammanfaller med den nya guiden för att skapa webbprogram.

1. Välj att visa URL:en i samma fönster.
1. Lägg till webbprogramsikonen i bildfältet: **/nms/img/webApp.png**.

   Den här ikonen visas på **[!UICONTROL New]** -knappen.

1. Retur **knapp** i **[!UICONTROL Style]** fält.

   Det här formatet hänvisas till i **[!UICONTROL Single-page Web application]** tidigare vald mall.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Lägga till detaljer i en lista {#adding-detail-to-a-list}

När du konfigurerar en lista i översikten kan du välja att visa ytterligare information för varje post i listan.

1. Placera markören på listelementet som du skapade tidigare.
1. I **[!UICONTROL General]** väljer du **[!UICONTROL Columns and additional detail]** visningsläget i listrutan.

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. I **[!UICONTROL Data]** -flik, lägga till **[!UICONTROL Primary key]** , **[!UICONTROL Internal name]** och **[!UICONTROL Description]** kolumn och markera **[!UICONTROL Hidden field]** för var och en av dem.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   På så sätt visas informationen bara i detalj för varje post.

1. I **[!UICONTROL Additional detail]** lägger du till följande kod:

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

I det här avsnittet skapar du ett filter för att visa översikten över webbprogram som har skapats av en viss operator. Det här filtret skapas med en ländredigerare. När du har valt en operator kan du uppdatera listan för att använda filtret; detta kräver att en uppdateringslänk skapas.

Dessa två element grupperas i samma behållare för att grafiskt grupperas i översikten.

1. Placera markören på **[!UICONTROL Page]** element och markera **[!UICONTROL Container > Standard]**.
1. Ange antalet kolumner som ska **2** så att länkredigeraren och länken ligger bredvid varandra.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Mer information om elementlayout finns i [det här avsnittet](about-web-forms.md).

1. Använd **prickedFilter**.

   Det här formatet hänvisas till i **[!UICONTROL Single-page Web application]** tidigare vald mall.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Skapa ett filter med en ländredigerare {#creating-a-filter-using-a-link-editor}

1. Placera markören på den behållare som skapades under föregående steg och infoga en ländredigerare via **[!UICONTROL Advanced controls]** -menyn.
1. I lagringsfönstret som öppnas automatiskt väljer du **[!UICONTROL Variables]** och sedan klicka på **[!UICONTROL Edit variables]** länka och skapa en XML-variabel för att filtrera data.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Ändra etiketten.

   Den visas bredvid **[!UICONTROL Filter]** i översikten.

1. Välj tabellen Operator som ett programschema.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Placera markören på listelementet och skapa ett filter via **[!UICONTROL Data > Filter]** tab:

   * **Uttryck:** Sekundärnyckel för länken&quot;Skapad av&quot;
   * **Operatör:** är lika med
   * **Värde:** Variabler (variabler)
   * **Ta hänsyn till om** &#39;$(var2/@id)&#39;!=&#39;&#39;

   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Webbprogramanvändaren måste vara en identifierad operator med rätt Adobe Campaign-behörighet för att få tillgång till informationen. Den här typen av konfiguration fungerar inte för anonyma webbprogram.

### Skapa en uppdateringslänk {#creating-a-refresh-link}

1. Placera markören på behållaren och infoga en **[!UICONTROL Link]** via **[!UICONTROL Static elements]** -menyn.
1. Ändra etiketten.
1. Välj **[!UICONTROL Refresh data in a list]**.
1. Lägg till listan som skapades tidigare.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Lägg till uppdateringsikonen på **[!UICONTROL Image]** fält: **/xtk/img/refresh.png**.
1. Med hjälp av sorteringspilarna kan du ordna om de olika elementen i webbprogrammet enligt nedan.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

Webbprogrammet är nu konfigurerat. Du kan klicka på **[!UICONTROL Preview]** för att förhandsgranska den.

![](assets/s_ncs_configuration_webapp_result.png)
