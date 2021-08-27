---
product: campaign
title: Viral och social marknadsföring
description: Viral och social marknadsföring
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 2%

---

# Viral och social marknadsföring{#viral-and-social-marketing}

![](../../assets/common.svg)

## Om viral marknadsföring {#about-viral-marketing}

Med Adobe Campaign kan ni skapa verktyg för att uppmuntra viral marknadsföring.

På så sätt kan mottagare eller besökare dela information med sitt nätverk: från att lägga till en länk till sin Facebook- eller Twitter-profil till att skicka ett meddelande till en vän.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>För att nya länkar ska fungera på rätt sätt måste den matchande spegelsidan vara tillgänglig. Det gör du genom att inkludera länken till spegelsidan i leveransen.

## Sociala nätverk: dela en länk {#social-networks--sharing-a-link}

Om du vill att leveransmottagarna ska kunna dela innehållet i meddelandena med medlemmarna i deras nätverk måste du inkludera det matchande personaliseringsblocket.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>Som standard visas inte den här länken i listan med block. Du kommer åt den genom att klicka på **[!UICONTROL Other...]** och välja **[!UICONTROL Social network sharing links]**-blocket.

![](assets/s_ncs_user_viral_add_link_via_others.png)

Återgivningen blir följande:

![](assets/s_ncs_user_viral_add_link_rendering.png)

När mottagaren klickar på ikonen för ett av de sociala nätverk som visas omdirigeras de automatiskt till sitt konto och kan dela meddelandeinnehållet via en länk. Detta gör att medlemmarna i deras nätverk får tillgång till kommunikationen.

>[!NOTE]
>
>Det här anpassningsblocket innehåller alla länkar (för att skicka och dela meddelanden med alla sociala nätverk). Den kan anpassas efter dina behov. Konfigurationen är dock reserverad för avancerade användare. Om du vill redigera det matchande personaliseringsblocket går du till noden **[!UICONTROL Resources > Campaign management > Personalization blocks]** i Adobe Campaign-trädet.

## Viral marketing: vidarebefordra till en vän {#viral-marketing--forward-to-a-friend}

Med en virustjänst kan hänskjutningsåtgärder utföras: Med dessa åtgärder kan du vidarebefordra ett meddelande till en vän. Referenspersonens profil lagras tillfälligt i databasen (i en dedikerad tabell). Vidarebefordrade meddelanden innehåller en länk där mottagaren kan prenumerera: om de gör det läggs de till i Adobe Campaign-databasen.

Vidarebefordran av meddelanden baseras på samma principer som länkar till sociala nätverk.

Använd följande steg:

1. Lägg till **[!UICONTROL Social network sharing links]**-anpassningsblocket i det ursprungliga meddelandets brödtext.
1. Meddelandemottagaren kan klicka på ikonen **[!UICONTROL Email]** för att skicka meddelandet till en eller flera vänner.

   ![](assets/s_ncs_user_viral_email_link.png)

   I ett hänvisningsformulär kan du ange e-postadresserna till de refererade.

   ![](assets/s_ncs_user_viral_email_msg.png)

   Meddelandet skickas till dem när huvudmottagaren klickar på knappen **[!UICONTROL Next]**.

   >[!NOTE]
   >
   >Innehållet i det här meddelandet kan anpassas efter dina behov. Den skapas baserat på mallen **[!UICONTROL Transfer of original message]**, som lagras i noden **[!UICONTROL Administration > Campaign management > Technical delivery templates]**.
   >
   >Det går också att ändra meddelandets vidarebefordringsformulär som har gjorts tillgängligt för referenten För att göra detta måste du ändra webbprogrammet **Viral form** som finns i noden **[!UICONTROL Resources > Online > Web applications]**.

1. I det vidarebefordrade meddelandet finns en länk som gör att referenten kan spara sin profil i databasen. En tävlingsblankett tillhandahålls för detta ändamål.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Denna konfiguration kan anpassas. För att göra detta måste du ändra **mottagarprenumerationen** webbprogrammet som lagras i noden **[!UICONTROL Resources > Online > Web applications]**.
   >
   >Mer information om webbprogram finns i [det här avsnittet](../../web/using/about-web-applications.md).

   När de har validerat skickas ett bekräftelsemeddelande till dem: de registreras endast för gott när de aktiverar länken i bekräftelsemeddelandet. Det här meddelandet skapas baserat på mallen **[!UICONTROL Registration confirmation]**, som lagras i noden **[!UICONTROL Administration > Campaign management > Technical delivery templates]**.

   Referensen läggs till i mappen **Mottagare** i databasen och prenumereras (som standard) på informationstjänsten **Newsletter**.

## Spåra delning via sociala nätverk {#tracking-social-network-sharing}

Delning och åtkomst till delad information spåras. Denna information som Adobe Campaign samlar in finns tillgänglig på två ställen:

* på fliken **[!UICONTROL Tracking]** för leveransen (eller individuellt för varje mottagare):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* i en dedikerad **[!UICONTROL Sharing to social networks]**-rapport:

   ![](assets/s_ncs_user_viral_report.png)
