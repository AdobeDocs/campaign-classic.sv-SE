---
title: '"Användningsexempel: skapa översikter"'
seo-title: '"Användningsexempel: skapa översikter"'
description: '"Användningsexempel: skapa översikter"'
seo-description: null
page-status-flag: never-activated
uuid: 404ae82b-2766-4802-8673-aaaa26868f46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: a3834828-4d39-4699-b648-d399797b8ea7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Användningsexempel: skapa översikter{#use-cases-creating-overviews}

I följande exempel skapar vi webbprogram av översiktstyp som visar alla webbprogram i din databas. Konfigurera följande element:

* ett filter i mappen (se [Lägga till ett filter i en mapp](#adding-a-filter-on-a-folder)),
* en knapp för att skapa ett nytt webbprogram (se [Lägga till en knapp för att konfigurera ett nytt webbprogram](#adding-a-button-to-configure-a-new-web-application)),
* Detaljvisning för varje post i listan (se [Lägga till detaljer i en lista](#adding-detail-to-a-list)).
* ett filter per länkredigeringsverktyg (se [Skapa ett filter med en ländredigerare](#creating-a-filter-using-a-link-editor)),
* en uppdateringslänk (se [Skapa en uppdateringslänk](#creating-a-refresh-link)).

![](assets/s_ncs_configuration_webapp_overview.png)

## Skapa ett webbprogram med en sida {#creating-a-single-page-web-application}

1. Skapa ett enda **[!UICONTROL Page]** webbprogram och inaktivera utgående övergångar och övergångar till nästa sida.

   ![](assets/s_ncs_configuration_webapp_create.png)

1. Ändrar sidans rubrik.

   Den här titeln visas i översiktshuvudet och i webbprogramöversikten.

1. I webbprogrammets egenskaper ändrar du återgivningen av programmet genom att välja **[!UICONTROL Single-page Web application]** mallen.

   ![](assets/s_ncs_configuration_webapp_rendering.png)

1. Öppna webbprogrammets **[!UICONTROL Page]** aktivitet och öppna en lista (**[!UICONTROL Static element > List]**).
1. På fliken **[!UICONTROL Data]** i listan väljer du typ av **[!UICONTROL Web applications]** dokument och kolumnerna **[!UICONTROL Label]** , **[!UICONTROL Creation date]** och **[!UICONTROL Type of application]** output.
1. Skapa följande filter på **[!UICONTROL Filter]** underfliken så som visas nedan för att endast visa webbprogram och exkludera mallar från vyn.

   ![](assets/s_ncs_configuration_webapp_filter.png)

1. Stäng konfigurationsfönstret på sidan och klicka på **[!UICONTROL Preview]**.

   Listan över webbprogram som finns i din databas visas.

   ![](assets/s_ncs_configuration_webapp_preview.png)

## Lägga till ett filter i en mapp {#adding-a-filter-on-a-folder}

I en översikt kan du välja att få åtkomst till data beroende på var de finns i Adobe Campaign-trädet. Det här är ett filter på en mapp. Använd följande process för att lägga till den i översikten.

1. Placera markören på **[!UICONTROL Page]** noden i webbprogrammet och lägg till ett **[!UICONTROL Select folder]** element (**[!UICONTROL Advanced controls > Select folder]**).
1. Klicka på **[!UICONTROL Storage]** **[!UICONTROL Edit variables]** länken i det fönster som visas.
1. Ändra variabeletiketten så att den passar dina behov.
1. Ändra variabelnamnet med **mappvärdet** .

   >[!NOTE]
   >
   >Variabelns namn måste matcha namnet på elementet som är länkat till mappen (definierat i schemat), dvs. **mappen** i det här fallet. Du måste återanvända det här namnet när du refererar till tabellen.

1. Använd variabeltypen **[!UICONTROL XML]** .

   ![](assets/s_ncs_configuration_webapp_variable_xml.png)

1. Markera **[!UICONTROL Refresh page]** interaktionen.

   ![](assets/s_ncs_configuration_webapp_variable.png)

1. Placera markören i listan och gå till **[!UICONTROL Advanced]** fliken och referera till den variabel som tidigare skapats på **[!UICONTROL Folder filter XPath]** fliken i listan. Du måste använda namnet på elementet som berörs av mapplänken, dvs. **mappen**.

   ![](assets/s_ncs_configuration_webapp_variable002.png)

   >[!NOTE]
   >
   >I det här skedet finns webbprogrammet inte i programkontexten och filtret kan därför inte testas i mappen.

## Lägga till en knapp för att konfigurera ett nytt webbprogram {#adding-a-button-to-configure-a-new-web-application}

1. Placera markören på **[!UICONTROL Page]** elementet och lägg till en länk (**[!UICONTROL Static elements > Link]**).
1. Ändra länketiketten eftersom den visas på knappen i översikten.

   I vårt exempel är etiketten **Ny**.

1. Infoga följande URL i URL-fältet: **xtk://open/?schema=nms:webApp&amp;form=nms:newWebApp**.

   >[!NOTE]
   >
   >**nms:webApp** sammanfaller med webbprogrammets schema.
   >
   >**nms:newWebApp** sammanfaller med den nya guiden för att skapa webbprogram.

1. Välj att visa URL:en i samma fönster.
1. Lägg till webbprogramsikonen i bildfältet: **/nms/img/webApp.png**.

   Den här ikonen visas på **[!UICONTROL New]** knappen.

1. Ange **knappen** i **[!UICONTROL Style]** fältet.

   Det här formatet refereras till i den tidigare valda **[!UICONTROL Single-page Web application]** mallen.

   ![](assets/s_ncs_configuration_webapp_link.png)

## Lägga till detaljer i en lista {#adding-detail-to-a-list}

När du konfigurerar en lista i översikten kan du välja att visa ytterligare information för varje post i listan.

1. Placera markören på listelementet som du skapade tidigare.
1. Välj visningsläget i listrutan på **[!UICONTROL General]** fliken **[!UICONTROL Columns and additional detail]** .

   ![](assets/s_ncs_configuration_webapp_detail.png)

1. Lägg till **[!UICONTROL Data]** , **[!UICONTROL Primary key]** och **[!UICONTROL Internal name]** kolumn på **[!UICONTROL Description]** fliken och markera **[!UICONTROL Hidden field]** alternativet för var och en av dem.

   ![](assets/s_ncs_configuration_webapp_detail002.png)

   På så sätt visas informationen bara i detalj för varje post.

1. Lägg till följande kod på **[!UICONTROL Additional detail]** fliken:

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

1. Placera markören på **[!UICONTROL Page]** elementet och markera **[!UICONTROL Container > Standard]**.
1. Ange antalet kolumner till **2**, så att länkredigeraren och länken ligger bredvid varandra.

   ![](assets/s_ncs_configuration_webapp_container.png)

   Mer information om elementlayout finns i [det här avsnittet](../../web/using/about-web-forms.md).

1. Använd **prickedFilter**.

   Det här formatet refereras till i mallen **[!UICONTROL Single-page Web applicatio]** n som du valde tidigare.

   ![](assets/s_ncs_configuration_webapp_container002.png)

### Skapa ett filter med en ländredigerare {#creating-a-filter-using-a-link-editor}

1. Placera markören på den behållare som skapades under föregående steg och infoga en ländredigerare via **[!UICONTROL Advanced controls]** menyn.
1. I lagringsfönstret som öppnas automatiskt markerar du **[!UICONTROL Variables]** alternativet, klickar på **[!UICONTROL Edit variables]** länken och skapar en XML-variabel för datafiltrering.

   ![](assets/s_ncs_configuration_webapp_variable003.png)

1. Ändra etiketten.

   Den visas bredvid **[!UICONTROL Filter]** fältet i översikten.

1. Välj tabellen Operator som ett programschema.

   ![](assets/s_ncs_configuration_webapp_linkeditor.png)

1. Placera markören på listelementet och skapa ett filter via **[!UICONTROL Data > Filter]** fliken:

   * **** Uttryck: Sekundärnyckel för länken&quot;Skapad av&quot;
   * **** Operatör: är lika med
   * **** Värde: Variabler (variabler)
   * **** Ta hänsyn till om &#39;$(var2/@id)&#39;!=&#39;&#39;
   ![](assets/s_ncs_configuration_webapp_filter002.png)

>[!CAUTION]
>
>Webbprogramanvändaren måste vara en identifierad operator med rätt Adobe Campaign-behörighet för att få tillgång till informationen. Den här typen av konfiguration fungerar inte för anonyma webbprogram.

### Skapa en uppdateringslänk {#creating-a-refresh-link}

1. Placera markören på behållaren och infoga en **[!UICONTROL Link]** via **[!UICONTROL Static elements]** menyn.
1. Ändra etiketten.
1. Välj **[!UICONTROL Refresh data in a list]**.
1. Lägg till listan som skapades tidigare.

   ![](assets/s_ncs_configuration_webapp_refreshlink.png)

1. Lägg till uppdateringsikonen i **[!UICONTROL Image]** fältet: **/xtk/img/refresh.png **.
1. Med hjälp av sorteringspilarna kan du ordna om de olika elementen i webbprogrammet enligt nedan.

   ![](assets/s_ncs_configuration_webapp_orderelements.png)

Webbprogrammet är nu konfigurerat. Du kan förhandsgranska fliken genom att klicka på den **[!UICONTROL Preview]** .

![](assets/s_ncs_configuration_webapp_result.png)

