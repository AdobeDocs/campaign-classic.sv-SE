---
product: campaign
title: Skapa ett Facebook-program
description: Skapa ett Facebook-program
audience: social
content-type: reference
topic-tags: configuration
exl-id: 5c11bd0f-2df7-4c7f-b682-955fedf8e664
source-git-commit: d891a235002d465f3b00fafa375d87d42ebafaa6
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 5%

---

# Skapa en Facebook-applikation{#creating-a-facebook-application}

![](../../assets/v7-only.svg)

Med Campaign Social Marketing-modulen kan ni visa personaliserat innehåll i era Facebook-program, vilket gör det enklare att hitta potentiella kunder via dessa sociala medier. Fler exempel på webbprogram av Facebook-typ finns i [den här sidan](../../social/using/examples-of-facebook-apps.md).

>[!NOTE]
>
>Du kan även integrera Adobe Campaign med en Facebook-applikation som utvecklats av en partner. I det här fallet behöver du inte använda Adobe Campaign webbprogram för att hämta Facebook-profiler. [Läs mer](#configuring-external-accounts).

![](assets/social_webapp_fb_000.png)

Konfigurationsstegen är:

1. Skapa ett eller flera Facebook-program.
1. Ange **[!UICONTROL terms of service]** och **[!UICONTROL Privacy policy]** länkar som ska visas på skärmen för Facebook behörighetsbegäran. [Läs mer](#entering-the-terms-of-service-and-privacy-policy-links)
1. Skapa en **[!UICONTROL Facebook Connect]** skriv ett externt konto. [Läs mer](#configuring-external-accounts)
1. För varje Facebook-program skapar du ett webbprogram av Facebook-typ i Adobe Campaign. [Läs mer](#creating-a-facebook-type-web-application)
1. Konfigurera dina Facebook-program så att de visas som flikar på din Facebook-sida. [Läs mer](#configuring-facebook-tabs)

## Konfigurera externa konton {#configuring-external-accounts}

För varje Facebook-program måste du skapa en **[!UICONTROL Facebook Connect]** skriv ett externt konto.

Det här steget kräver åtkomst till din Adobe Campaign-konsol och ditt Facebook-administratörskonto:

* På **Facebook**: välj det tidigare skapade programmet ( [https://developers.facebook.com/apps](https://developers.facebook.com/apps)) och väljer **[!UICONTROL Settings]** > **[!UICONTROL Basic]** -fliken.

   ![](assets/social_webapp_fb_008.png)

   >[!NOTE]
   >
   >Om **[!UICONTROL Facebook Web Games]** visas inte klickar du på **[!UICONTROL Add Platform]** längst ned på sidan och välj **[!UICONTROL Facebook Web Games]**.

* På **Adobe Campaign**: bläddra till **[!UICONTROL Administration > Platform > External accounts]** och klicka **[!UICONTROL New]**.

   ![](assets/social_webapp_fb_005.png)

1. Ange en etikett och ett internt namn och välj **[!UICONTROL Facebook Connect]** typ.

   ![](assets/social_webapp_fb_006.png)

1. Välj programvärdläge: **[!UICONTROL hosted by a partner]** eller **[!UICONTROL hosted by this instance]**.

   ![](assets/social_webapp_fb_012.png)

   **Program som hanteras av en partner**

   Det går att integrera Adobe Campaign med en Facebook-applikation som utvecklats av en partner. I det här fallet finns det inget behov av att använda Adobe Campaign webbprogram för att hämta Facebook-profiler. När Facebook-användaren installerar programmet skapas en nyckel (åtkomsttoken). Partnern vidarebefordrar denna åtkomsttoken till Adobe Campaign genom att ringa upp en webbtjänst. Adobe Campaign använder sedan denna token för att logga in i Facebook-databasen och samla in data som delas av användaren via programmet.

   >[!NOTE]
   >
   >Parametrarna för webbtjänsten finns i WSDL-filen som finns här: **`https://<Instance name>/nl/jsp/schemawsdl.jsp?schema=nms:visitor`**

   Om du vill integrera tredjepartsprogrammet i Adobe Campaign måste du kopiera innehållet i **[!UICONTROL App ID]** och **[!UICONTROL App Secret]** Facebook-fält och klistra in dem i **[!UICONTROL Application ID]** och **[!UICONTROL Application secret]** fält i konsolen.

   ![](assets/social_facebook_external_account_013.png)

   **Program som är värd för den här instansen**

   Om du vill ha programmet på den här instansen (om du inte har något tredjepartsprogram) måste du använda Adobe Campaign webbprogram för att hämta Facebook-profiler. Mer information finns på [den här sidan](../../social/using/examples-of-facebook-apps.md).

   I Adobe Campaign Console kopierar du adressen som finns i **[!UICONTROL Secure Canvas URL]** och klistra in den i **[!UICONTROL Facebook Web games (https)]** på Facebook (i **[!UICONTROL Facebook Web Games]** ).

   ![](assets/social_facebook_external_account_009.png)

   >[!CAUTION]
   >
   >Använd inte osäkra URL:er.

   På Facebook kopierar du innehållet i **[!UICONTROL App ID]** och **[!UICONTROL App Secret]** fält och klistra in dem i **[!UICONTROL Application ID]** och **[!UICONTROL Application secret]** fält i konsolen.

   ![](assets/social_facebook_external_account_008.png)

1. På Facebook klickar du på **[!UICONTROL Save Changes]** längst ned på sidan.
1. I Adobe Campaign-konsolen klickar du på **[!UICONTROL Subscribe]** så att Adobe Campaign kan återskapa data i realtid varje gång en fläkt checkar in via programmet.  [Läs mer](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_fb_013.png)

## Ange länkar till användarvillkor och sekretesspolicy {#entering-the-terms-of-service-and-privacy-policy-links}

Vi rekommenderar att du lägger till **[!UICONTROL Terms of service]** och **[!UICONTROL Privacy policy]** -länkar, som visas på Facebook behörighetsbegärandeskärm.

![](assets/social_fb_terms_of_services_001.png)

Konfigurationsstegen är följande:

1. Ange följande adress: [https://developers.facebook.com/apps](https://developers.facebook.com/apps)väljer du sedan Facebook.
1. Välj **[!UICONTROL Settings > Basic]** och ange **[!UICONTROL Privacy Policy URL]** och **[!UICONTROL Terms of Service URL]** fält.

   ![](assets/social_fb_terms_of_services.png)

## Skapa ett webbprogram av Facebook-typ {#creating-a-facebook-type-web-application}

Med Adobe Campaign Facebook-programmet kan du visa anpassat innehåll i dina Facebook-program. För varje Facebook-program måste du skapa ett webbprogram i Adobe Campaign. Så här skapar du ett Facebook-webbprogram:

1. Gå till **[!UICONTROL Social networks]** klickar du på **[!UICONTROL Applications]** länk, sedan **[!UICONTROL Create]** -knappen.

   ![](assets/social_webapp_001.png)

1. Välj en Facebook-webbprogrammall i listan och ange etiketten.

   ![](assets/social_webapp_002.png)

   >[!NOTE]
   >
   >Som standard finns det fyra Facebook webbprogrammallar:
   >
   >* **[!UICONTROL New Facebook application]**: välj den här mallen om du vill starta från ett tomt program.
   >* **[!UICONTROL Pre-entered form]**: Facebook-program med ett formulär och en&quot;Facebook-inloggningsknapp&quot; som gör att användare kan fylla i formulärfälten automatiskt med data från sin profil. På så sätt kan användarna fylla i formuläret snabbare och varumärkena kan få bättre kvalitetsinformation.
   >* **[!UICONTROL "Canvas page" competition]**: Facebook-program som visas på hela skärmen för en bättre visuell upplevelse för användarna.
   >* **[!UICONTROL "Page Tab" competition]**: Facebook-program är helt integrerat i varumärkessidorna.


1. I **[!UICONTROL Application]** anger du det externa konto som är länkat till Facebook-programmet. [Läs mer](#configuring-external-accounts)

   ![](assets/social_webapp_005.png)

1. Välj **[!UICONTROL Edit]** och sedan redigera webbprogrammet. [Läs mer](../../social/using/examples-of-facebook-apps.md)

   ![](assets/social_webapp_003.png)

1. När webbprogrammet är klart väljer du **[!UICONTROL Dashboard]** tabbtangenten och sedan klicka **[!UICONTROL Publish]** för att publicera online.

   ![](assets/social_webapp_004.png)

## Konfigurera Facebook-flikar {#configuring-facebook-tabs}

Du kan konfigurera dina Facebook-program så att de visas som flikar på din Facebook-sida. Gör så här:

1. Markera Facebook-programmet ([https://developers.facebook.com/apps](https://developers.facebook.com/apps)) och väljer **[!UICONTROL Settings > Basic]** -fliken.

   ![](assets/social_webapp_fb_008.png)

1. Klicka på knappen längst ned på sidan **[!UICONTROL Add Platform]** och markera **[!UICONTROL Page Tab]**.

   ![](assets/social_webapp_fb_008bis.png)

1. I **[!UICONTROL Page Tab Name]** fält för **[!UICONTROL Page Tab]** anger du etiketten som du vill att den ska visas på Facebook-sidan.

   ![](assets/social_webapp_fb_001.png)

1. I **[!UICONTROL Secure Page Tab URL]** anger du webbprogrammets offentliga URL, som du kommer åt via **[!UICONTROL Dashboard]** -fliken i webbprogrammet. Mer information om hur du skapar webbprogram av Facebook-typ finns i [det här avsnittet](#creating-a-facebook-type-web-application).

   ![](assets/social_webapp_fb_002.png)

1. På **[!UICONTROL Dashboard]** i webbprogrammet klickar du på **[!UICONTROL Add a page tab]** länk.

   ![](assets/social_webapp_fb_0010.png)

1. Markera den Facebook-sida som du vill lägga till fliken i och klicka på **[!UICONTROL Add Page Tab]**.

   ![](assets/social_webapp_fb_0011.png)
