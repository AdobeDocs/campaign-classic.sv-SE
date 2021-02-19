---
solution: Campaign Classic
product: campaign
title: Exempel på Facebook-appar
description: Exempel på Facebook-appar
audience: social
content-type: reference
topic-tags: annexes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1981'
ht-degree: 1%

---


# Exempel på Facebook-appar{#examples-of-facebook-apps}

När en användare klickar på fliken för ett Facebook-program visas den i ett utrymme som är 810 pixlar brett. Adobe Campaign använder ett webbprogram av Facebook-typ för att du ska kunna definiera och anpassa det innehåll som visas i Facebook-programmet, vilket gör det enklare att hämta profiler.

>[!NOTE]
>
>Det går också att integrera Adobe Campaign med en Facebook-applikation som utvecklats av en partner. I det här fallet finns det inget behov av att använda Adobe Campaign webbprogram för att hämta Facebook-profiler. Mer information finns i [Konfigurera externa konton](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

>[!IMPORTANT]
>
>Följ konfigurationsstegen som beskrivs i [Skapa ett Facebook-program](../../social/using/creating-a-facebook-application.md).

>[!NOTE]
>
>I det här avsnittet beskrivs de element som är länkade till webbprogram av Facebook-typ. Alla element som delas med standardwebbprogram beskrivs i [det här avsnittet](../../web/using/about-web-applications.md).

De exempel på webbapplikationer av Facebook-typ som beskrivs här är:

* Så här skapar du ett Facebook-program i 7 steg. Se [Snabbstart: skapa ett Facebook-program i 7 steg](#quick-start--creating-a-facebook-application-in-7-steps).
* Så här vidarebefordrar du inställningar till ett Facebook-program. Se [Hur du vidarebefordrar inställningar till ett Facebook-program?](#how-to-forward-settings-to-a-facebook-application-).
* Så här hämtar du fläktdata. Se [Hur du hämtar fläktdata?](#how-to-acquire-fan-data-).

>[!IMPORTANT]
>
>Dessa enkla användningsexempel finns som exempel som illustrerar funktionerna i webbapplikationer av Facebook-typ.

## Rekommendationer {#recommendations}

Följande begränsningar är direkt kopplade till Facebook:

* Du måste skapa alla webbprogram i HTTPS.
* Ett Facebook-program som visas via en flik har en bredd på 810 pixlar.

## Snabbstart: skapa ett Facebook-program i 7 steg {#quick-start--creating-a-facebook-application-in-7-steps}

I det här exemplet beskrivs hur du visar ett Adobe Campaign-byggt program på Facebook steg för steg. I det här fallet vill vi skapa ett program där du kan visa **välkomstmeddelandet** när användaren klickar på programfliken (**App01**).

Så här skapar du programmet:

1. Skapa ett program på Facebook ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)). Mer information finns i: [Skapa ett Facebook-program](../../social/using/publishing-on-facebook-walls.md#creating-a-facebook-application).

   ![](assets/social_create_facebook_app_002.png)

1. Skapa ett **[!UICONTROL Facebook Connect]**-typspecifikt externt konto och ange parametrarna för Facebook-programmet. Mer information finns i: [Konfigurera externa konton](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

   ![](assets/social_quick_start_2.png)

1. Ange de **[!UICONTROL Terms of service]**- och **[!UICONTROL Privacy policy]**-länkar som ska visas på skärmen för behörighetsbegäran på Facebook. Mer information finns i: [Ange länkar till användarvillkoren och sekretesspolicyn](../../social/using/creating-a-facebook-application.md#entering-the-terms-of-service-and-privacy-policy-links).

   ![](assets/social_quick_start_1.png)

1. Skapa ett webbprogram av Facebook-typ i Adobe Campaign. Mer information finns i: [Skapa ett webbprogram av Facebook-typ](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_005.png)

1. Redigera webbprogrammet. I det här exemplet har vi lagt till en **[!UICONTROL Page]**-aktivitet och definierat en rubrik för den.

   ![](assets/social_quick_start_4.png)

1. Distribuera programmet.

   ![](assets/social_webapp_004.png)

1. Konfigurera ditt Facebook-program så att det visas som en flik på din Facebook-sida. Mer information finns i: [Konfigurera Facebook-flikar](../../social/using/creating-a-facebook-application.md#configuring-facebook-tabs).

   ![](assets/social_quick_start_5.png)

![](assets/social_quick_start_6.png)

Kontrollera att fliken för **App01**-programmet visas på din Facebook-sida. Om du klickar på det anropas ett **välkomstmeddelande**.

![](assets/social_webapp_042.png)

## Hur man vidarebefordrar inställningar till ett Facebook-program? {#how-to-forward-settings-to-a-facebook-application-}

>[!IMPORTANT]
>
>Följ konfigurationsstegen i [Skapa ett Facebook-program](../../social/using/creating-a-facebook-application.md).

I exempel 1 anpassade vi visningen av Facebook-sidan enligt värdet i fältet **[!UICONTROL Fan of the page]**. Det går också att bearbeta fältet **[!UICONTROL Application settings]**. I det här fältet kan du återställa data som finns i en länk som skapats av Adobe Campaign via Facebook.

Låt oss ta ett exempel på ett företag som bestämmer sig för att skicka en e-postkampanj. I leveransen pekar en länk mot Facebook-programmet. Den här länken är personlig tack vare parametern **[!UICONTROL app_data]** som läggs till i slutet av URL:en. Värdet på den här parametern kan vara en indikator som speglar kundens betydelse. I vårt exempel är värdena för parametern **[!UICONTROL app_data]** **[!UICONTROL big]** (signifikant kund) och **[!UICONTROL small]** (mindre viktig kund).

När URL:en har anpassats ser den ut så här:

* `http://<path of the Facebook application>&app_data=big` (för en betydande kund)
* `http://<path of the Facebook application>&app_data=small` (för en mindre viktig kund)

Bland de anonyma data som vidarebefordrats till Adobe Campaign av Facebook samlas värdet för **[!UICONTROL Application parameters]**-fältet in, vilket gör att Adobe Campaign kan anpassa programvisningen baserat på den här parametern.

Om användaren är en viktig kund (värdet för parametern **[!UICONTROL app_data]** är **[!UICONTROL big]**) visas följande bild:

![](assets/social_webapp_017.png)

Om användaren är en mindre viktig kund (värdet för parametern **[!UICONTROL app_data]** är **[!UICONTROL small]**) visas följande bild:

![](assets/social_webapp_016.png)

Vi har skapat ett webbprogram som består av följande element för att återskapa det här användningsexemplet:

* En **[!UICONTROL Test]**-aktivitet baserad på fältet **[!UICONTROL Application parameter]**.
* två sidor som innehåller bilderna som ska visas enligt värdet i fältet **[!UICONTROL Application parameter]**.

![](assets/social_webapp_018.png)

## Hur får jag tag i fläktdata? {#how-to-acquire-fan-data-}

>[!IMPORTANT]
>
>Följ konfigurationsstegen i [Skapa ett Facebook-program](../../social/using/creating-a-facebook-application.md).

I det här exemplet visas hur du får kontakt med Facebook-användare och erbjuder dem möjlighet att dela sin profilinformation. Låt oss ta ett exempel på ett företag som vill förvärva potentiella kunder och organisera en tävling på sin Facebook-sida för att locka dem.

När en användare klickar på fliken **[!UICONTROL App03]** frågar vi om de vill delta i tävlingen.

![](assets/social_webapp_fb_000.png)

Om de väljer att delta i tävlingen erbjuder vi dem att dela med sig av sin profilinformation.

![](assets/social_webapp_021.png)

Om de godkänner att dela sin information visas följande skärm.

![](assets/social_webapp_022.png)

Vi har skapat ett webbprogram som innehåller följande element för att skapa det här användningsexemplet:

* en **[!UICONTROL Test]**-aktivitet
* tre sidor
* en **[!UICONTROL Access control]**-aktivitet
* en **[!UICONTROL Pre-loading]**-aktivitet
* en **[!UICONTROL Save]**-aktivitet
* en **[!UICONTROL End]**-aktivitet

![](assets/social_webapp_019.png)

### Testaktivitet {#test-activity}

Aktiviteten **[!UICONTROL Test]** baseras på fälten **[!UICONTROL ID]** och **[!UICONTROL Application parameters]**.

![](assets/social_webapp_023.png)

Den består av tre grenar:

* **[!UICONTROL identifier (UID) is empty]** : identifieraren vidarebefordras endast av Facebook om användaren redan har gått med på att dela sin information. Med den första grenen i **[!UICONTROL Test]**-aktiviteten kan du göra tävlingen tillgänglig endast för användare som aldrig har anmält sig, dvs. användare med ett tomt ID.
* **[!UICONTROL application parameter equals 'thanks']** : om du vill lägga ett visningsfel som är länkat till Facebook pekar webbprogrammets slutsida mot webbadressen för det Facebook-program som  **[!UICONTROL app_data]** parametern läggs till i med  **[!UICONTROL thanks]** värdet (mer information finns i:  [Avsluta aktivitet](#end-activity)). I den andra grenen kan du ta reda på om användaren kommer från aktiviteten **[!UICONTROL End]** i den första grenen (och just har anmält sig till tävlingen) för att visa ett tackmeddelande. Mer information om hur du använder ytterligare URL-parametrar finns i: [Hur vidarebefordrar jag inställningar till ett Facebook-program?](#how-to-forward-settings-to-a-facebook-application-).
* **[!UICONTROL Default branch]** : Om användaren redan har anmält sig till tävlingen (ID har redan angetts) vid ett tidigare datum (en annan programparameter än  **[!UICONTROL thanks]**) visas en sida som anger att användaren redan har anmält sig.

### Konkurrenssidan {#competition-page}

Om du vill gå åt sidan av det visningsfel som är länkat till Facebook måste du även välja **[!UICONTROL Parent window]** eller **[!UICONTROL In the top window]** i fältet **[!UICONTROL Window]** på tävlingssidan.

![](assets/social_webapp_028.png)

### Åtkomstkontrollaktivitet {#access-control-activity}

Med aktiviteten **[!UICONTROL Access control]** kan du visa sidan för begäran om behörighet på Facebook när användaren går in i tävlingen. Om de samtycker till att dela sina uppgifter återställs de under förinläsningen. Mer information finns i: [Förinläsningsaktivitet](#pre-loading-activity).

Om du tidigare angav det externa kontot när du skapade webbprogrammet (se [Skapa ett webbprogram av Facebook-typ](../../social/using/creating-a-facebook-application.md#creating-a-facebook-type-web-application)) behöver du inte redigera aktiviteten. Om inte går du till fältet **[!UICONTROL Application]** och väljer det externa konto som är länkat till Facebook-programmet.

![](assets/social_webapp_024.png)

### Förinläsningsaktivitet {#pre-loading-activity}

Välj den datakälla som ska användas för förinläsning:

* **[!UICONTROL Marketing database]** : Med det här alternativet kan du förhandsladda data via Adobe Campaign-databasen.
* **[!UICONTROL Facebook]** : Med det här alternativet kan du läsa in data i förväg med Facebook.

![](assets/social_webapp_029.png)

**Marknadsföringsdatabas**

Med det här alternativet kan du återställa data för en profil som finns i besökstabellen. Verifieringen utförs baserat på det externa Facebook-ID som återställts när användaren klickar på fliken för Facebook-programmet. Om du lägger till ett formulär efter **[!UICONTROL Pre-loading]**-aktiviteten läses fälten som innehåller information i databasen in i förväg.

![](assets/social_webapp_030.png)

>[!NOTE]
>
>Mer information om hur du läser in data i förväg via Adobe Campaign-databasen finns i [det här avsnittet](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

**Facebook**

Med det här alternativet kan du definiera den Facebook-profilinformation som ska samlas in, bland annat den som användaren har gått med på att dela, för att spara den.

![](assets/social_webapp_025.png)

Med alternativet **[!UICONTROL Database information]** kan du samla in följande data:

* **[!UICONTROL External ID]**: användar-ID
* **[!UICONTROL Gender]**: användarens kön
* **[!UICONTROL Verified]** : I det här fältet anges om användaren har ett verifierat Facebook-konto eller inte.
* **[!UICONTROL Full name]**: användarens fullständiga namn
* **[!UICONTROL First name]**: användarens förnamn
* **[!UICONTROL Last name]**: användarens efternamn
* **[!UICONTROL Language]**: användarens språk

Du kan också välja att samla in profilfotot, listan över vänner, e-postadress, födelsedatum, intressen och plats genom att markera lämpliga rutor.

Markera rutan **[!UICONTROL I agree to comply with Facebook conditions of use]** innan du klickar på **[!UICONTROL Ok]**.

>[!NOTE]
>
>Om du markerar en eller flera rutor i avsnittet **[!UICONTROL Private information]** visas åtkomstbegäran för dessa data automatiskt på skärmen för Facebook-behörighetsbegäran.
>
>För att du ska kunna samla in den valda informationen måste användaren samtycka till att dela den.
>
>Om du vill ha båda typerna av förinläsning (via Adobe Campaign och via Facebook) lägger du till två förinläsningsrutor, den ena efter den andra.

### Spara aktivitet {#save-activity}

Med aktiviteten **[!UICONTROL Save]** kan du lagra den information som samlats in under de föregående stegen i besökartabellen.

Om profilen redan finns i besökartabellen uppdateras deras data med de nya data som samlas in.

Om profilen inte finns i databasen och Facebook-användarens e-postadress har samlats in, skapas en besökare i besökartabellen.

![](assets/social_webapp_026.png)

1. I fältet **[!UICONTROL Visitor creation folder]** väljer du mappen som profilen ska skapas i. Om det är ett webbprogram av Facebook-typ är standardmappen **[!UICONTROL Visitors]**.
1. Välj det avstämningsläge som du vill använda i fältet **[!UICONTROL Reconciliation mode]**:

   * **[!UICONTROL Automatic]** : Avstämningen görs utifrån e-post, efternamn, förnamn och födelsedatum.
   * **[!UICONTROL Manual]** : Välj en eller flera avstämningsnycklar.
   * **[!UICONTROL None]** : Ingen avstämning kommer att ske.

1. I fältet **[!UICONTROL Mapping]** väljer du det schema som du vill utföra avstämningen på.

   >[!IMPORTANT]
   >
   >Kontrollera att fälten på fliken **[!UICONTROL Social networks]** är korrekt angivna i leveransmappningen. Leveransmappningar nås via noden **[!UICONTROL Administration > Campaign management > Target mappings]**.

1. Du kan välja en sökmapp för avstämning och en skapandemapp för nya profiler. Om fälten är tomma söks profiler igenom och skapas i standardmappen för mappningsschemat.

### Avsluta aktivitet {#end-activity}

Om du vill stega förbi det visningsfel som är länkat till Facebook måste du markera rutan **[!UICONTROL Use an external URL]** och ange URL:en för Facebook-programmet, följt av parametern **[!UICONTROL app_data]** och ett värde. Det här värdet används i **[!UICONTROL Test]**-aktiviteten för att identifiera om användaren just har anmält sig till tävlingen och för att visa ett tackmeddelande om det är tillämpligt. Mer information finns i: [Testaktivitet](#test-activity).

I vårt exempel är det värde som används **tack**.

![](assets/social_webapp_027.png)

### Skärmen Detaljer för en besökare {#details-screen-of-a-visitor}

Precis som för Twitter-följare (se: [Funktionsprincip](../../social/using/publishing-on-twitter.md#operating-principle)), återställda Facebook-profiler lagras i besökartabellen. Om du vill visa listan över besökare går du till noden **[!UICONTROL Profiles and Targets > Visitors]**.

Alla potentiella Facebook-användare som går med på att dela sin profilinformation läggs till i listan över besökare. Om rutan **[!UICONTROL Friends]** är markerad i aktiviteten **[!UICONTROL Pre-load]** (se: [Förinläsningsaktivitet](#pre-loading-activity)), vänner läggs också till.

![](assets/social_webapp_037.png)

I avsnittet **[!UICONTROL Summary]** i fönstret med besöksinformation finns det två möjliga lägen för indikatorn **[!UICONTROL New Contact]**:

![](assets/social_webapp_038.png)

Om en grön bockmarkering visas betyder det att besökaren inte stämdes av mot någon mottagare. I det här fallet skapas en ny profil i listan över mottagare.

![](assets/social_webapp_039.png)

Ett rött kryss innebär att besökaren stämdes av mot en mottagare. Du kan klicka på förstoringsglaset till höger om fältet **[!UICONTROL Recipient]** för att visa den matchande mottagaren.

![](assets/social_webapp_040.png)

Gå till detaljfönstret för en mottagare för att visa den matchande besökaren, om tillämpligt. Välj fliken **[!UICONTROL Others]** och dubbelklicka sedan på besökarens namn i avsnittet **[!UICONTROL Web identities]**.

![](assets/social_webapp_041.png)

Skärmen **[!UICONTROL Activities]** på en besökares informationssida innehåller följande information:

* Fläktaktiviteter av typen &quot;Open Graph&quot;: uppspelad musik, bevakade videoklipp, artiklar som läses och avbrott i installerade program (Deezer, Spotify, Dailymotion, Yahoo News osv.)

   ![](assets/social_facebook_activities.png)

* &quot;Likes&quot; och kommentarer som lagts till av fläkten efter leveranser från Adobe Campaign
* sidor som fläkten gillar
* incheckningar av fläkten

   ![](assets/social_facebook_checkins.png)

   >[!NOTE]
   >
   >För att Adobe Campaign ska kunna samla in en fan-ins måste du klicka på knappen **[!UICONTROL Subscribe]** på skärmen för tjänstkonfiguration. Mer information finns i [Konfigurera externa konton](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

## Läs in fälten i ett formulär i förväg med Facebook-profildata {#how-to-pre-load-the-fields-of-a-form-using-facebook-profile-data}

Med **[!UICONTROL Social Marketing]**-programmet kan du även lägga till en knapp i ett formulär för att läsa in fält i förväg med hjälp av information om Facebook-profiler. Det här alternativet, som är tillgängligt i alla webbprogrammallar (**[!UICONTROL Page]** typaktiviteter), beskrivs i [det här avsnittet](../../web/using/static-elements-in-a-web-form.md#inserting-html-content).

![](assets/social_webapp_035.png)

>[!NOTE]
>
>Innan du börjar använda den här funktionen måste du skapa ett Facebook-program och ett externt konto av typen **[!UICONTROL Facebook Connect]**. Mer information finns i [Konfigurera externa konton](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

