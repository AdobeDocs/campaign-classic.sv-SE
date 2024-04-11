---
product: campaign
title: Viral och social marknadsföring
description: Viral och social marknadsföring
feature: Social Marketing
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 2%

---

# Viral och social marknadsföring{#viral-and-social-marketing}

Med Adobe Campaign kan ni skapa verktyg för att uppmuntra viral marknadsföring.

Detta gör att mottagare eller besökare på webbplatser kan dela information med sitt nätverk: från att lägga till en länk till sin Facebook- eller X-profil (tidigare kallad Twitter) till att skicka ett meddelande till en vän.

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>För att de nya länkarna ska fungera på rätt sätt måste den matchande spegelsidan vara tillgänglig. Det gör du genom att inkludera länken till spegelsidan i leveransen.

## Sociala nätverk: dela en länk {#social-networks--sharing-a-link}

Om du vill att leveransmottagarna ska kunna dela innehållet i meddelandena med medlemmarna i deras nätverk måste du inkludera det matchande personaliseringsblocket.

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>Som standard visas inte den här länken i listan med block. Du kommer åt den genom att klicka **[!UICONTROL Other...]** och väljer **[!UICONTROL Social network sharing links]** -block.

![](assets/s_ncs_user_viral_add_link_via_others.png)

Återgivningen blir följande:

![](assets/s_ncs_user_viral_add_link_rendering.png)

När mottagaren klickar på ikonen för ett av de sociala nätverk som visas omdirigeras de automatiskt till sitt konto och kan dela meddelandeinnehållet via en länk. Detta gör att medlemmarna i deras nätverk får tillgång till kommunikationen.

>[!NOTE]
>
>Det här anpassningsblocket innehåller alla länkar (för att skicka och dela meddelanden med alla sociala nätverk). Den kan anpassas efter dina behov. Konfigurationen är dock reserverad för avancerade användare. Om du vill redigera matchande personaliseringsblock går du till **[!UICONTROL Resources > Campaign management > Personalization blocks]** noden i Adobe Campaign-trädet.

## Virusmarknadsföring: vidarebefordra till en vän {#viral-marketing--forward-to-a-friend}

Med en virustjänst kan hänskjutningsåtgärder utföras: dessa åtgärder gör att du kan vidarebefordra ett meddelande till en vän. Referenspersonens profil lagras tillfälligt i databasen (i en särskild tabell). Vidarebefordrade meddelanden innehåller en länk som referenten kan prenumerera på: om de gör det läggs de till i Adobe Campaign-databasen.

Vidarebefordran av meddelanden baseras på samma principer som länkar till sociala nätverk.

Använd följande steg:

1. Lägg till **[!UICONTROL Social network sharing links]** personaliseringsblock i det ursprungliga meddelandets brödtext.
1. Mottagaren kan klicka på **[!UICONTROL Email]** om du vill skicka det här meddelandet till en eller flera vänner.

   ![](assets/s_ncs_user_viral_email_link.png)

   I ett hänvisningsformulär kan du ange e-postadresserna till de refererade.

   ![](assets/s_ncs_user_viral_email_msg.png)

   Meddelandet skickas till dem när huvudmottagaren klickar på **[!UICONTROL Next]** -knappen.

   >[!NOTE]
   >
   >Innehållet i det här meddelandet kan anpassas efter dina behov. Det skapas baserat på **[!UICONTROL Transfer of original message]** -mall som lagras i **[!UICONTROL Administration > Campaign management > Technical delivery templates]** nod.
   >
   >Det går också att ändra meddelandets vidarebefordringsformulär som har gjorts tillgängligt för referenten För att göra detta måste du ändra **Virusform** Webbprogram som lagras i **[!UICONTROL Resources > Online > Web applications]** nod.

1. I det vidarebefordrade meddelandet finns en länk som gör att referenten kan spara sin profil i databasen. En tävlingsblankett tillhandahålls för detta ändamål.

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >Denna konfiguration kan anpassas. Om du vill göra det måste du ändra **Mottagarprenumeration** Webbprogram som lagras i **[!UICONTROL Resources > Online > Web applications]** nod.
   >
   >Mer information om webbprogram finns i [det här avsnittet](../../web/using/about-web-applications.md).

   När de har validerat skickas ett bekräftelsemeddelande till dem: de registreras bara för gott när de har aktiverat länken i bekräftelsemeddelandet. Det här meddelandet har skapats baserat på **[!UICONTROL Registration confirmation]** -mall som lagras i **[!UICONTROL Administration > Campaign management > Technical delivery templates]** nod.

   Referensen läggs till i **Mottagare** databasmappen och prenumererar (som standard) på **Nyhetsbrev** informationstjänst.

## Spåra delning via sociala nätverk {#tracking-social-network-sharing}

Delning och åtkomst till delad information spåras. Denna information som Adobe Campaign samlar in finns tillgänglig på två ställen:

* i **[!UICONTROL Tracking]** Leveransflik (eller individuellt för varje mottagare):

  ![](assets/s_ncs_user_network_del_tracking_tab.png)

* i en dedikerad **[!UICONTROL Sharing to social networks]** rapport:

  ![](assets/s_ncs_user_viral_report.png)
