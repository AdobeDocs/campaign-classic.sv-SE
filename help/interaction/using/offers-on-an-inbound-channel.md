---
product: campaign
title: Erbjudanden på en inkommande kanal
description: Erbjudanden på en inkommande kanal
audience: interaction
content-type: reference
topic-tags: case-study
exl-id: 90afced3-465d-4370-8a33-51a7e4356135
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 0%

---

# Erbjudanden på en inkommande kanal{#offers-on-an-inbound-channel}

## Presentera ett erbjudande för en anonym besökare {#presenting-an-offer-to-an-anonymous-visitor}

Neobank-sajten vill visa ett erbjudande på sin webbplats som riktar sig till oidentifierade besökare som bläddrar på sidan.

För att lägga upp den här interaktionen kommer vi att:

1. [Skapa en anonym miljö](#creating-an-anonymous-environment)
1. [Skapa anonyma erbjudanden](#creating-anonymous-offer-spaces)
1. [Skapa en erbjudandekategori och ett tema](#creating-an-offer-category-and-a-theme)
1. [Skapa anonyma erbjudanden.](#creating-anonymous-offers)
1. [Konfigurera webbplatsens erbjudanden](#configure-the-web-offer-space-on-the-website)

### Skapar en anonym miljö {#creating-an-anonymous-environment}

Följ anvisningarna i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment) för att skapa en anonym miljö baserat på dimensionerna **Besökare**.

Du får en trädstruktur som innehåller din nya miljö:

![](assets/offer_env_anonymous_003.png)

### Skapar anonyma erbjudandeblanksteg {#creating-anonymous-offer-spaces}

1. I din anonyma miljö (**Besökare**) går du till noden **[!UICONTROL Administration]** > **[!UICONTROL Spaces]**.
1. Klicka på **[!UICONTROL New]** för att skapa anropskanaler.

   ![](assets/offer_inbound_anonymous_example_010.png)

   >[!NOTE]
   >
   >Utrymmet länkas automatiskt till den anonyma miljön.

1. Ändra etiketten och välj kanalen **[!UICONTROL Inbound Web]**. Du måste även markera rutan **[!UICONTROL Enable unitary mode]**.

   ![](assets/offer_inbound_anonymous_example_006.png)

1. Markera de innehållsfält för erbjudandet som används för utrymmet och ange dem enligt vad som krävs genom att markera den relevanta rutan.

   På så sätt är erbjudanden som saknar något av följande element inte berättigade till detta utrymme:

   * Titel
   * HTML-innehåll
   * Bild-URL
   * Mål-URL

   ![](assets/offer_inbound_anonymous_example_030.png)

1. Redigera HTML-återgivningsfunktionen enligt följande:

   ```
   function (imageUrl, targetUrl, shortContent, htmlSource){
         var html = "<p><b>" + shortContent + "</b></p>";
         html += "<p>" + htmlSource + "</p>";
         html += "<a _urlType='11' href='" + targetUrl + "'><img src='" + encodeURI(imageUrl) + "'/></a>";
         return html;
       }   
   ```

   >[!IMPORTANT]
   >
   >Återgivningsfunktionen måste namnge fälten som används för utrymmet i den ordning som de markerades tidigare, så att erbjudandena visas korrekt.

   ![](assets/offer_inbound_anonymous_example_031.png)

1. Spara utrymme.

### Skapa en erbjudandekategori och ett tema {#creating-an-offer-category-and-a-theme}

1. Gå till noden **[!UICONTROL Offer catalog]** i miljön som du just har skapat.
1. Högerklicka på noden **[!UICONTROL Offer catalog]** och välj **[!UICONTROL Create a new 'Offer category' folder]**.

   Ge den nya kategorin namnet **Finansiella produkter** till exempel.

1. Gå till fliken **[!UICONTROL Eligibility]** för kategorin och ange **finansiering** som ett tema. Spara sedan ändringarna.

   ![](assets/offer_inbound_anonymous_example_023.png)

### Skapar anonyma erbjudanden {#creating-anonymous-offers}

1. Gå till kategorin som du nyss skapade.
1. Klicka på **[!UICONTROL New]**.

   ![](assets/offer_inbound_anonymous_example_013.png)

1. Välj den färdiga anonyma erbjudandemallen eller en mall som skapats tidigare.

   ![](assets/offer_inbound_anonymous_example_014.png)

1. Ändra etiketten och spara ditt erbjudande.

   ![](assets/offer_inbound_anonymous_example_015.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och ange erbjudandenas vikt enligt dess programkontexter.

   I det här exemplet är erbjudandet konfigurerat att visas som en prioritet på webbplatsens hemsida till slutet av året.

   ![](assets/offer_inbound_anonymous_example_016.png)

1. Gå till fliken **[!UICONTROL Content]** och definiera innehållet i erbjudandet.

   >[!NOTE]
   >
   >Du kan välja **[!UICONTROL Content definitions]** om du vill visa listan med element som krävs för webbsidan.

   ![](assets/offer_inbound_anonymous_example_017.png)

1. Skapa ett andra erbjudande.

   ![](assets/offer_inbound_anonymous_example_018.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och tillämpa samma vikt som för det första erbjudandet.
1. Kör godkännandecykeln för varje erbjudande för att göra dem, samt deras godkända erbjudandeplatser, tillgängliga i onlinemiljön.

### Konfigurera utrymmet för webberbjudandet på webbplatsen {#configure-the-web-offer-space-on-the-website}

Om du vill göra de erbjudanden du just har konfigurerat synliga på webbplatsen infogar du en JavaScript-kod på webbplatsens HTML-sida för att anropa interaktionsmotorn (mer information finns i [Om inkommande kanaler](../../interaction/using/about-inbound-channels.md)).

1. Gå till HTML-sidan och infoga ett @id-attribut med ett värde som matchar det interna namnet på det anonyma erbjudandeutrymme som skapats tidigare (se [Skapa anonyma erbjudandeblanksteg](#creating-anonymous-offer-spaces)), föregånget av **i_**.

   ![](assets/offer_inbound_anonymous_example_019.png)

1. Ange anrops-URL.

   ![](assets/offer_inbound_anonymous_example_020.png)

   De blå URL-rutorna ovan motsvarar instansnamnet, det interna namnet på miljön (se [Skapa en anonym miljö](#creating-an-anonymous-environment)) och det tema som är länkat till kategorin ([Skapa en erbjudandekategori och ett tema](#creating-an-offer-category-and-a-theme)). Den senare är valfri.

När en besökare kommer åt webbplatsens hemsida visas erbjudandena med temat **finansiering** så som de har konfigurerats på HTML-sidan.

![](assets/offer_inbound_anonymous_example_022.png)

En användare som besöker sidan flera gånger kommer att se antingen det ena eller det andra erbjudandet i kategorin eftersom båda har tilldelats samma vikt.

## Växla till en anonym miljö om oidentifierade kontakter är {#switching-to-an-anonymous-environment-in-case-of-unidentified-contacts}

Företaget Neobank vill skapa marknadsföringserbjudanden för två olika mål. Den vill visa generiska erbjudanden för sina anonyma webbläsare. Om någon av dessa användare visar sig vara kund med identifierare från Neobank vill företaget att de ska få personaliserade erbjudanden så fort de loggar in.

Denna fallstudie bygger på följande scenario:

1. En besökare surfar på Neobank-webbplatsen utan att logga in.

   ![](assets/offer_inbound_fallback_example_050.png)

   Tre anonyma erbjudanden visas på sidan: två **Bästa erbjudanden** för Neobank-produkter och ett erbjudande från en Neobank-partner.

   ![](assets/offer_inbound_fallback_example_051.png)

1. Användaren, en Neobank-kund, loggar in med sina inloggningsuppgifter.

   ![](assets/offer_inbound_fallback_example_052.png)

   Tre personaliserade erbjudanden visas.

   ![](assets/offer_inbound_fallback_example_053.png)

För att implementera denna fallstudie måste ni ha två miljöer: en för anonym interaktion och en med erbjudanden som är särskilt konfigurerade för identifierade kontakter. Den identifierade erbjudandemiljön kommer att konfigureras för att automatiskt växla till den anonyma erbjudandemiljön om kontakten inte är inloggad och därför inte identifieras.

Använd följande steg:

* Skapa en katalog med erbjudanden som är specifika för anonyma inkommande interaktioner med följande steg:

   1. [Skapa en miljö för anonyma kontakter](#creating-an-environment-for-anonymous-contacts)
   1. [Konfigurera erbjudandeplatser för den anonyma miljön](#configuring-offer-spaces-for-the-anonymous-environment)
   1. [Skapa erbjudandekategorier i en anonym miljö](#creating-offer-categories-in-an-anonymous-environment)
   1. [Skapa erbjudanden för anonyma besökare](#creating-offers-for-anonymous-visitors)

* Skapa en katalog med erbjudanden som är specifika för identifierade inkommande interaktioner med följande steg:

   1. [Konfigurera erbjudandeutrymmena i den identifierade miljön](#configure-the-offer-spaces-in-the-identified-environment)
   1. [Skapa erbjudandekategorier i en identifierad miljö](#creating-offer-categories-in-an-identified-environment)
   1. [Skapa personaliserade erbjudanden](#creating-personalized-offers)

* Konfigurera anropet till erbjudandemotorn:

   1. [Konfigurera erbjudandeutrymmen på webbsidan](#configuring-offer-spaces-on-the-web-page)
   1. [Ange avancerade inställningar för de identifierade erbjudandeutrymmena](#specifying-the-advanced-settings-of-the-identified-offer-spaces)

### Skapar en miljö för anonyma kontakter {#creating-an-environment-for-anonymous-contacts}

1. Skapa en erbjudandemiljö för anonym inkommande interaktion via guiden för leveranskarta (**Visitor**-mappning). Mer information finns i [Skapa en erbjudandemiljö](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

   ![](assets/offer_env_anonymous_003.png)

### Konfigurera erbjudandeutrymmen för den anonyma miljön {#configuring-offer-spaces-for-the-anonymous-environment}

Erbjudandena som måste presenteras på webbplatsen tillhör två olika kategorier: **Bästa erbjudande** och **Partner**. I det här exemplet ska vi skapa ett specifikt erbjudandeutrymme för varje kategori.

Gör så här för att skapa ett utrymme som matchar kategorin **Bästa erbjudande**:

1. Gå till den anonyma miljön som du just har skapat i Adobe Campaign-trädet och lägg till ett utrymme för erbjudanden.

   ![](assets/offer_inbound_fallback_example_023.png)

1. Skapa ett nytt **[!UICONTROL Inbound web]**-teckenutrymme.

   ![](assets/offer_inbound_fallback_example_024.png)

1. Ange en etikett för den: **Bästa anonyma erbjudande** för webben, till exempel.
1. Lägg till de innehållsfält för erbjudandet som används för erbjudandeutrymmet och konfigurera återgivningsfunktionerna.

   ![](assets/offer_inbound_fallback_example_025.png)

   >[!IMPORTANT]
   >
   >Återgivningsfunktionen måste namnge fälten som används för utrymmet i den ordning som de markerades tidigare, så att erbjudandena visas korrekt.

1. Använd samma process för att skapa ett erbjudande för inkommande webbkanal som matchar kategorin **Partner**.

   ![](assets/offer_inbound_fallback_example_026.png)

### Skapa erbjudandekategorier i en anonym miljö {#creating-offer-categories-in-an-anonymous-environment}

Börja med att skapa två kategorier: kategorin **Bästa erbjudande** och kategorin **Partner**. Varje kategori innehåller två erbjudanden för anonyma kontakter.

1. Gå till **[!UICONTROL Offer catalog]** i den anonyma miljö som du just har skapat.
1. Lägg till en **[!UICONTROL Offer category]**-mapp med **Bästa erbjudande** som etikett.

   ![](assets/offer_inbound_fallback_example_027.png)

1. Skapa en andra kategori med **Partner** som etikett.

   ![](assets/offer_inbound_fallback_example_028.png)

### Skapa erbjudanden för anonyma besökare {#creating-offers-for-anonymous-visitors}

Vi kommer nu att skapa två erbjudanden i varje kategori som skapas ovan.

1. Gå till kategorin **Bästa erbjudande** och skapa ett anonymt erbjudande.

   ![](assets/offer_inbound_fallback_example_029.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och ange erbjudandenas vikt enligt dess programkontexter.

   ![](assets/offer_inbound_fallback_example_030.png)

1. Gå till fliken **[!UICONTROL Content]** och definiera innehållet i erbjudandet.

   ![](assets/offer_inbound_fallback_example_032.png)

1. Skapa ett andra erbjudande i kategorin **Bästa erbjudande**.

   ![](assets/offer_inbound_fallback_example_031.png)

1. Gå till kategorin **Partner** och skapa ett anonymt erbjudande.
1. Gå till fliken **[!UICONTROL Content]** och definiera innehållet i erbjudandet.

   ![](assets/offer_inbound_fallback_example_033.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och ange erbjudandenas vikt enligt dess programkontexter.

   ![](assets/offer_inbound_fallback_example_034.png)

1. Skapa ett andra erbjudande för kategorin **Partner**.

   ![](assets/offer_inbound_fallback_example_035.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och tillämpa samma vikt som du lade på det första erbjudandet i den här kategorin så att erbjudandena visas i följd på webbplatsen.

   ![](assets/offer_inbound_fallback_example_036.png)

1. Kör godkännandecykeln för varje erbjudande för att börja göra det live. När du godkänner innehåll ska du aktivera erbjudandeutrymmet **Partner** eller **Best Offer** enligt erbjudandet.

### Konfigurera erbjudandeutrymmena i den identifierade miljön {#configure-the-offer-spaces-in-the-identified-environment}

Erbjudandena som du kommer att presentera på webbplatsen är uppdelade i två olika kategorier: **Bästa erbjudande** och **Partner**. I det här exemplet vill vi skapa ett specifikt utrymme för varje kategori.

Om du vill skapa de två erbjudandeutrymmena använder du samma procedur som för anonyma erbjudandeutrymmen. Se [Konfigurera erbjudandeutrymmen för den anonyma miljön](#configuring-offer-spaces-for-the-anonymous-environment).

1. I Adobe Campaign-trädet går du till den miljö du just har skapat och lägger till **Bästa erbjudande** och **Partner** erbjuder blanksteg.
1. Använd den process som beskrivs i [Konfigurera erbjudandeutrymmen för den anonyma miljön](#configuring-offer-spaces-for-the-anonymous-environment).

   ![](assets/offer_inbound_fallback_example_005.png)

1. Välj alternativet **[!UICONTROL Fall back on an anonymous environment if no individuals were identified]**.

   ![](assets/offer_inbound_fallback_example_006.png)

1. Använd listrutan för att markera det anonyma webberbjudandeutrymme som skapats tidigare (se [Konfigurera erbjudandeutrymmen för den anonyma miljön](#configuring-offer-spaces-for-the-anonymous-environment)).

   ![](assets/offer_inbound_fallback_example_007.png)

### Ange de avancerade inställningarna för de identifierade erbjudandeutrymmena {#specifying-the-advanced-settings-of-the-identified-offer-spaces}

I det här exemplet sker en kontaktidentifiering tack vare e-postadressen i Adobe Campaign-databasen. Gör så här om du vill lägga till mottagarens e-postadress i utrymmet:

1. I den identifierade miljön går du till mappen för erbjudandeutrymme.
1. Välj **erbjudandeutrymme** och klicka på **[!UICONTROL Advanced parameters]**.

   ![](assets/offer_inbound_fallback_example_044.png)

1. På fliken **[!UICONTROL Target identification]** klickar du på **[!UICONTROL Add]**.

   ![](assets/offer_inbound_fallback_example_046.png)

1. Klicka på **[!UICONTROL Edit expression]**, gå till mottagartabellen och välj fältet **[!UICONTROL Email]**.

   ![](assets/offer_inbound_fallback_example_047.png)

1. Klicka på **[!UICONTROL OK]** för att stänga fönstret **[!UICONTROL Advanced parameters]** och slutföra konfigurationen av erbjudandeutrymmet **Best Offer**.
1. Använd samma process för erbjudandeutrymmet **Partner**.

   ![](assets/offer_inbound_fallback_example_048.png)

### Skapa erbjudandekategorier i en identifierad miljö {#creating-offer-categories-in-an-identified-environment}

Vi ska skapa två olika kategorier: kategorin **Bästa erbjudande** och kategorin **Partner**, där vart och ett har två personaliserade erbjudanden.

1. Gå till noden **[!UICONTROL Offer catalogs]** i den identifierade miljön.
1. Som i den anonyma miljön lägger du till två **[!UICONTROL Offer category]**-mappar med **Bästa erbjudande** och **Partner** som etiketter.

   ![](assets/offer_inbound_fallback_example_009.png)

### Skapa anpassade erbjudanden {#creating-personalized-offers}

Vi vill skapa två personaliserade erbjudanden för varje kategori, nämligen fyra.

1. Gå till kategorin **Bästa erbjudande** och skapa ett första personaliserat erbjudande.

   ![](assets/offer_inbound_fallback_example_011.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och ange erbjudandenas vikt enligt dess programkontexter.

   ![](assets/offer_inbound_fallback_example_012.png)

1. Gå till fliken **[!UICONTROL Content]** och definiera innehållet i erbjudandet.

   ![](assets/offer_inbound_fallback_example_013.png)

1. Skapa ett andra erbjudande i kategorin **Bästa erbjudande**.

   ![](assets/offer_inbound_fallback_example_014.png)

1. Gå till kategorin **Partner** och skapa ett personaliserat erbjudande.

   ![](assets/offer_inbound_fallback_example_015.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och ange erbjudandenas vikt enligt dess programkontexter.

   ![](assets/offer_inbound_fallback_example_016.png)

1. Skapa ett andra erbjudande för kategorin **Partner**.

   ![](assets/offer_inbound_fallback_example_017.png)

1. Gå till fliken **[!UICONTROL Eligibility]** och tillämpa samma vikt som du lade på det första erbjudandet i den här kategorin så att erbjudandena visas i följd på webbplatsen.
1. Kör godkännandecykeln för varje erbjudande för att börja uppdatera dem. Aktivera **partnern** eller **det bästa erbjudandet** under godkännande av innehåll.

### Konfigurera erbjudandeutrymmen på webbsidan {#configuring-offer-spaces-on-the-web-page}

På Neobanks webbplats finns tre olika erbjudanden: två för bankrelaterade erbjudanden från kategorin **Bästa erbjudande** och en för erbjudanden från kategorin **Partner**.

![](assets/offer_inbound_fallback_example_038.png)

Gör så här om du vill konfigurera erbjudandena på webbplatsens HTML-sida:

1. Infoga tre i HTML-sidans innehåll

   element med ett @id-attribut vars värde gör att vi kan ringa upp erbjudandena på webbplatsens olika erbjudandeplatser.

   ![](assets/offer_inbound_fallback_example_039.png)

1. Infoga sedan skriptet för att definiera attributvärden.

   ![](assets/offer_inbound_fallback_example_040.png)

   I det här exemplet får **ContBO1** och **ContBO2** värdet **OsWebBestOfferIdentified**, dvs. det interna namnet på **det bästa erbjudandet** utrymme som skapats tidigare i den identifierade miljön. Värdena **CatBestOffer** och **CatBestOfferAnonym** matchar det interna namnet för kategorierna **Best Offer** för anonyma och identifierade miljöer.

   ![](assets/offer_inbound_fallback_example_041.png)

   På samma sätt tar **ContPtn** emot **OSWebPartnerIdentified**-värdet, som matchar det interna namnet för **Partner**-erbjudandeutrymmet som skapades i den identifierade miljön. **** CatPartnership och  **** CatPartnerAnonymmatch det interna namnet på  **** Partnerkategorierna för anonyma och identifierade miljöer.

   ![](assets/offer_inbound_fallback_example_042.png)

1. Tilldela den information som gör att du kan identifiera den person som loggar in på Neobank-webbplatsen för variabeln **interactionTarget**.

   ![](assets/offer_inbound_fallback_example_043.png)

   Personens identifiering kan baseras på en webbläsarcookie, en läsparameter i URL:en, e-postadressen eller identifieraren för personen. Om ett annat fält i mottagartabellen än primärnyckeln används, måste det definieras i de avancerade parametrarna för utrymmet (se [Ange avancerade inställningar för de identifierade erbjudandeutrymmena](#specifying-the-advanced-settings-of-the-identified-offer-spaces)).

1. Ange anrops-URL.

   ![](assets/offer_inbound_fallback_example_049.png)

   URL:en innehåller **EnvNeobankRecip**, den identifierade miljöns interna namn.

När du öppnar webbsidan; skriptet gör att du kan anropa interaktionsmotorn för att visa innehållet i erbjudanden i relevanta delar av webbsidan. I ett enda anrop till Adobe Campaign-servern avgör motorn miljön, erbjudandeutrymmet och de kategorier som ska väljas.

I det här exemplet känner motorn igen den identifierade miljön (**EnvNeobankIdRecip**). Det identifierar erbjudandeutrymmet (**OSWebBestOfferIdentified**) och kategorin **Bästa erbjudande** (**CatBestOffer**) för den första och andra erbjudandekategorin på webbsidan samt (**OSWebPartnerIdentified**) erbjuder utrymme och kategorin **Partner** (**CatPartner**) för det tredje erbjudandeutrymmet på webbplatsen.

Om motorn inte kan identifiera mottagaren växlar den till de anonyma erbjudandeutrymmena som refereras i de identifierade erbjudandeutrymmena och till de anonyma kategorierna (**CatPartner** och **CatPartnerAnonym**) som anges i skriptet.
