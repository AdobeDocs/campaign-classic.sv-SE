---
product: campaign
title: Skapa radleveranser
description: Lär dig hur du skapar LINE-meddelanden
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Line App
role: User
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 2%

---

# Skapa radleveranser{#line-channel}



[!DNL LINE] är ett program för kostnadsfria snabbmeddelanden, röst- och videosamtal som finns i alla operativsystem för mobila enheter och på datorn.

[!DNL LINE] kan även kombineras med transaktionsmeddelandemodulen för att skicka realtidsmeddelanden på [!DNL LINE] app installerad på konsumentmobilenheter. Se denna [sida](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line) för mer information om detta.

![](assets/line_message.png)

Stegen för att använda [!DNL LINE] kanalen:

1. [Konfigurera LINE-kanal](#setting-up-line-channel)
1. [Skapa en leverans](#creating-the-delivery)
1. [Konfigurera innehållstypen](#defining-the-content)
1. [Övervaka leveransen (spårning, karantän, rapporter osv.)](#accessing-reports)

## Konfigurera LINE-kanal {#setting-up-line-channel}

Innan du skapar [!DNL LINE] konto och externt konto måste du först installera LINE-paketet på din instans. Mer information finns i [det här avsnittet](../../installation/using/installing-campaign-standard-packages.md#line-package).

Du måste först skapa en [!DNL LINE] så att du kan länka det till Adobe Campaign. Sedan kan du skicka [!DNL LINE] meddelanden till de användare som har lagt till [!DNL LINE] i mobilapplikationen. Externa konton och [!DNL LINE] kontot kan bara hanteras av plattformens funktionsadministratör.

Skapa och konfigurera en [!DNL LINE] konto, se [Dokumentation för LINE-utvecklare](https://developers.line.me/).

### Skapa och konfigurera LINE-tjänsten {#configure-line-service}

Skapa [!DNL LINE] tjänst:

1. På Adobe Campaign Classic hemsida väljer du **[!UICONTROL Profiles and Targets]** -fliken.

1. Välj **[!UICONTROL Services and Subscriptions]** och klicka **[!UICONTROL Create]**.

   ![](assets/line_service_1.png)

1. Lägg till en **[!UICONTROL Label]** och **[!UICONTROL Internal name]** till din nya tjänst.

1. Välj **[!UICONTROL LINE]** från **[!UICONTROL Type]** nedrullningsbar meny.

   ![](assets/line_service_2.png)

1. Klicka på **[!UICONTROL Save]**.

Mer information om prenumerationer och tjänster finns i [Hantera prenumerationer](managing-subscriptions.md).

### Konfigurera externt LINE-konto {#configure-line-external}

När du har skapat [!DNL LINE] måste du konfigurera [!DNL LINE] externt konto på Adobe Campaign:

1. I **[!UICONTROL Administration]** > **[!UICONTROL Platform]** trädstruktur, klicka på **[!UICONTROL External Accounts]** -fliken.

1. Välj det inbyggda **[!UICONTROL LINE V2 routing]** externt konto.

   ![](assets/line_config.png)

1. Klicka på **[!UICONTROL LINE]** från ditt externa konto för att börja konfigurera ditt externa konto. Fyll i följande fält:

   ![](assets/line_config_2.png)

   * **[!UICONTROL Channel Alias]**: tillhandahålls via [!DNL LINE] kontot i **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** -fliken.
   * **[!UICONTROL Channel ID]**: tillhandahålls via [!DNL LINE] kontot i **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]** -fliken.
   * **[!UICONTROL Channel secret key]**: tillhandahålls via [!DNL LINE] kontot i **[!UICONTROL Channels]** > **[!UICONTROL Basic Information panel]** -fliken.
   * **[!UICONTROL Access token]**: tillhandahålls via [!DNL LINE] på utvecklarportalen eller genom att klicka på **[!UICONTROL Get access token]** -knappen.
   * **[!UICONTROL Access token expiration date]**: låter dig ange förfallodatum för åtkomsttoken.
   * **[!UICONTROL LINE subscription service]**: gör att du kan ange vilka tjänster som användarna ska prenumerera på.

1. När konfigurationen är klar klickar du på **[!UICONTROL Save]**.

1. Från **[!UICONTROL Explorer]**, markera **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL LINE workflows]** för att kontrollera om **[!UICONTROL LINE V2 access token update (updateLineAccessToken)]** och **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** arbetsflöden har startats.

The [!DNL LINE] är nu konfigurerat i Adobe Campaign och du kan börja skapa och skicka LINE-leveranser till prenumeranter.

## Skapa radleverans {#creating-the-delivery}

>[!NOTE]
>
>När en [!DNL LINE] för leverans till en ny mottagare för första gången måste du lägga till det officiella LINE-meddelandet om användningsvillkoren och samtycke i leveransen. Det officiella meddelandet finns på [följande länk](https://terms.line.me/OA_privacy/).

Skapa en [!DNL LINE] leverans du måste följa dessa steg:

1. Från **[!UICONTROL Campaigns]** flik, välja **[!UICONTROL Deliveries]** klickar du på **[!UICONTROL Create]** -knappen.

   ![](assets/line_message_07.png)

1. Välj **[!UICONTROL LINE V2 delivery]** leveransmall.

   ![](assets/line_message_01.png)

1. Identifiera leveransen med en **[!UICONTROL Label]**, **[!UICONTROL Delivery code]** och  **[!UICONTROL Description]**. Mer information om detta finns i [det här avsnittet](steps-create-and-identify-the-delivery.md#identifying-the-delivery).

1. Klicka **[!UICONTROL Continue]** för att leverera.

1. Välj **[!UICONTROL To]** för att rikta in dig på mottagarna av [!DNL LINE] leverans. Målinriktning genomförs på **[!UICONTROL Visitor subscriptions (nms:visitorSub)]**.

   Mer information finns i [Identifiera målpopulationer](steps-defining-the-target-population.md).

   ![](assets/line_message_08.png)

1. Klicka **[!UICONTROL Add]** för att välja **[!UICONTROL Delivery target population]**.

   ![](assets/line_message_09.png)

1. Välj om du vill ange mål [!DNL LINE] prenumeranter direkt eller om du vill rikta in användare beroende på deras [!DNL LINE] prenumerera och klicka på **[!UICONTROL Next]**. I det här exemplet har vi valt **[!UICONTROL By LINE V2 subscription]**.

1. Välj **[!UICONTROL Line-V2]** i **[!UICONTROL Folder]** rullgardinsmeny och [!DNL LINE] service. Klicka **[!UICONTROL Finish]** sedan **[!UICONTROL Ok]** för att personalisera leveransen.

   ![](assets/line_message_10.png)

1. I leveransprogrammet klickar du på **[!UICONTROL Add]** för att lägga till ett eller flera meddelanden och markera **[!UICONTROL Content type]**.

   Mer information om de olika **[!UICONTROL Content type]** tillgänglig, se [Definiera innehållstypen](#defining-the-content).

   ![](assets/line_message_11.png)

1. När leveransen har skapats och konfigurerats på rätt sätt kan du skicka den till det mål som definierades tidigare.

   Mer information om hur du skickar en leverans finns i [Skicka meddelanden](sending-messages.md).

1. När du har skickat meddelandet kan du visa rapporten och mäta hur effektiv leveransen är.

   Mer information om [!DNL LINE] rapporter, se [Åtkomstrapporter](#accessing-reports).

## Definiera innehållstypen {#defining-the-content}

Definiera innehållet i en [!DNL LINE] måste du först lägga till meddelandetyp till leveransen. Varje [!DNL LINE] leverans kan innehålla upp till 5 meddelanden.

Du kan välja mellan tre meddelandetyper:

* [Textmeddelande](#configuring-a-text-message-delivery)
* [Bild och länk](#configuring-an-image-and-link-delivery)
* [Videomeddelande](#configuring-a-video-message-delivery)

### Konfigurera leverans av textmeddelande {#configuring-a-text-message-delivery}

>[!NOTE]
>
>The `<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>` kan du inkludera en länk till ett webbprogram i ett LINE-meddelande.

A **[!UICONTROL Text message]** [!DNL LINE] leverans är ett meddelande som skickas till mottagarna i textform.

![](assets/line_message_02.png)

Konfigurationen för den här typen av meddelande liknar konfigurationen för **[!UICONTROL Text]** i ett mejl. Mer information finns i [page](defining-the-email-content.md#message-content).

### Konfigurera en bild- och länkleverans {#configuring-an-image-and-link-delivery}

An **[!UICONTROL Image and link]** [!DNL LINE] leverans är ett meddelande som skickas till mottagarna i form av en bild som kan innehålla en eller flera URL:er.

Du kan använda

* a **[!UICONTROL Personalized image]**,

  >[!NOTE]
  >
  >Du kan använda **%SIZE%** variabel för att optimera bildvisningen enligt skärmstorleken för mottagarens mobila enhet.

  ![](assets/line_message_04.png)

* en **[!UICONTROL Image URL]** skärmstorlek per enhet,

  ![](assets/line_message_03.png)

  The **[!UICONTROL Define images per device screen size]** kan du använda olika bildupplösningar för att optimera synligheten för leverans på mobila enheter. Endast bilder med samma höjd och bredd stöds.

  Bilder kan definieras enligt skärmstorleken:

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px

  >[!CAUTION]
  >
  >Storleken 1 040 × 1 040 px är obligatorisk för varje LINE-bild med länk.

  Sedan måste du lägga till alternativ text som visas på mottagarens mobila enhet.

* och **[!UICONTROL Links]**.

  The **[!UICONTROL Links]** kan du välja mellan olika layouter som delar upp bilden i flera klickbara områden. Du kan sedan tilldela var och en av dem en dedikerad **[!UICONTROL Link URL]**.

  ![](assets/line_message_05.png)

### Konfigurera leverans av videomeddelanden {#configuring-a-video-message-delivery}

A **[!UICONTROL Video message]** [!DNL LINE] leverans är ett meddelande som skickas till mottagarna i form av en video som kan innehålla en URL.

The **[!UICONTROL Preview Image URL]** I kan du lägga till URL:en för en förhandsvisningsbild med en teckengräns på 1 000. JPEG och PNG stöds med en filstorleksgräns på 1 MB.

The **[!UICONTROL Video Image URL]** I kan du lägga till webbadressen till videofilen med en teckengräns på 1 000. Endast mp4-format stöds med en filstorleksgräns på 200 MB.

Observera att breda eller höga videor kan beskäras när de spelas upp på vissa enheter.

![](assets/line_message_06.png)

## Åtkomst till rapporter {#accessing-reports}

När leveransen är klar kan du se [!DNL LINE] rapporter via menyn **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** från **[!UICONTROL Explorer]**.

>[!NOTE]
>
>Spårningsrapporterna visar klickfrekvensen. [!DNL LINE] tar inte hänsyn till den öppna räntan.

![](assets/line_reports_01.png)

För [!DNL LINE] tjänstrapporter, gå till menyn **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Services and Subscriptions]** > **[!UICONTROL LINE-V2]** från **[!UICONTROL Explorer]** -fliken. Klicka sedan på **[!UICONTROL Reports]** ikonen i [!DNL LINE] service.

![](assets/line_reports.png)

## Exempel: skapa och skicka ett personligt LINE-meddelande {#example--create-and-send-a-personalized-line-message}

I det här exemplet ska vi skapa och konfigurera ett textmeddelande och en bild som innehåller data som ska anpassas efter mottagaren.

1. Skapa [!DNL LINE] genom att klicka på **[!UICONTROL Create]** från **[!UICONTROL Campaign]** -fliken.

   ![](assets/line_usecase.png)

1. Välj **[!UICONTROL LINE V2 delivery]** leveransmall och ge leveransen ett namn.

   ![](assets/line_usecase_01.png)

1. Välj målpopulation i konfigurationsfönstret för leveransen.

   Mer information finns i [Identifiera målpopulationer](steps-defining-the-target-population.md).

   ![](assets/line_usecase_02.png)

1. Klicka **[!UICONTROL Add]** för att skapa ditt meddelande och välja **[!UICONTROL Content type]**.

   Här vill vi först skapa en **[!UICONTROL Text message]**.

   ![](assets/line_usecase_03.png)

1. Placera markören där du vill infoga den anpassade texten och klicka på listruteikonen och välj **[!UICONTROL Visitor]** > **[!UICONTROL First name]**.

   ![](assets/line_usecase_05.png)

1. Följ samma procedur för att lägga till en bild, välja **[!UICONTROL Image and links]** i **[!UICONTROL Message type]** nedrullningsbar meny.

   Lägg till **[!UICONTROL Image URL]**.

   ![](assets/line_usecase_07.png)

1. I **[!UICONTROL Links]** väljer du den layout som ska dela upp bilden i flera klickbara områden.

1. Tilldela en URL till varje område i bilden.

   ![](assets/line_usecase_08.png)

1. Spara leveransen och klicka sedan på **[!UICONTROL Send]** för att analysera och skicka den till målet.

   Leveransen skickas till målet.

   ![](assets/line_usecase_06.png)

