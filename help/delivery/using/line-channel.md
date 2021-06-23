---
product: campaign
title: LINE-kanal
description: LINE-kanal
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
exl-id: 1baaabbd-9fd7-4d9b-b78e-d2a559d7dddb
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 2%

---

# Skapa radleveranser{#line-channel}

>[!NOTE]
>
>[!DNL LINE] är endast tillgängligt för installationer av anläggningstjänster eller hanterade tjänster.

[!DNL LINE] är ett program för kostnadsfria snabbmeddelanden, röst- och videosamtal som finns i alla operativsystem för mobila enheter och på datorn.

[!DNL LINE] kan även kombineras med transaktionsmeddelandemodulen för att skicka realtidsmeddelanden till  [!DNL LINE] appen som är installerad på konsumentmobilenheter. Se denna [sida](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line) för mer information om detta.

![](assets/line_message.png)

Stegen för att använda kanalen [!DNL LINE] är:

1. [Konfigurera LINE-kanal](#setting-up-line-channel)
1. [Skapa en leverans](#creating-the-delivery)
1. [Konfigurera innehållstypen](#defining-the-content)
1. [Övervaka leveransen (spårning, karantän, rapporter osv.)](#accessing-reports)

## Konfigurera LINE-kanal {#setting-up-line-channel}

Innan du skapar ett [!DNL LINE]-konto och ett externt konto måste du först installera LINE-paketet på din instans. Mer information finns i avsnittet [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) i installationshandboken.

Du måste först skapa ett [!DNL LINE]-konto så att du kan länka det till Adobe Campaign. Sedan kan du skicka [!DNL LINE]-meddelanden till de användare som har lagt till ditt [!DNL LINE]-konto i deras mobilprogram. Externa konton och [!DNL LINE]-konto kan bara hanteras av plattformens funktionsadministratör.

Information om hur du skapar och konfigurerar ett [!DNL LINE]-konto finns i [LINE-utvecklardokumentation](https://developers.line.me/).

### Skapa och konfigurera LINE-tjänsten {#configure-line-service}

Så här skapar du din [!DNL LINE]-tjänst:

1. På Adobe Campaign Classic hemsida väljer du fliken **[!UICONTROL Profiles and Targets]**.

1. Välj **[!UICONTROL Services and Subscriptions]** på den vänstra menyn och klicka på **[!UICONTROL Create]**.

   ![](assets/line_service_1.png)

1. Lägg till en **[!UICONTROL Label]** och **[!UICONTROL Internal name]** till den nya tjänsten.

1. Välj **[!UICONTROL LINE]** i listrutan **[!UICONTROL Type]**.

   ![](assets/line_service_2.png)

1. Klicka på **[!UICONTROL Save]**.

Mer information om prenumerationer och tjänster finns i [Hantera prenumerationer](managing-subscriptions.md).

### Konfigurera externt LINE-konto {#configure-line-external}

När du har skapat din [!DNL LINE]-tjänst måste du konfigurera det externa [!DNL LINE]-kontot på Adobe Campaign:

1. Klicka på fliken **[!UICONTROL External Accounts]** i trädstrukturen **[!UICONTROL Platform]**.**[!UICONTROL Administration]**

1. Välj det inbyggda externa **[!UICONTROL LINE V2 routing]**-kontot.

   ![](assets/line_config.png)

1. Klicka på fliken **[!UICONTROL LINE]** från ditt externa konto för att börja konfigurera ditt externa konto. Fyll i följande fält:

   ![](assets/line_config_2.png)

   * **[!UICONTROL Channel Alias]**: tillhandahålls via ditt  [!DNL LINE] konto på  **[!UICONTROL Channels]** >- **[!UICONTROL Technical configuration]** fliken.
   * **[!UICONTROL Channel ID]**: tillhandahålls via ditt  [!DNL LINE] konto på  **[!UICONTROL Channels]** >- **[!UICONTROL Basic Information panel]** fliken.
   * **[!UICONTROL Channel secret key]**: tillhandahålls via ditt  [!DNL LINE] konto på  **[!UICONTROL Channels]** >- **[!UICONTROL Basic Information panel]** fliken.
   * **[!UICONTROL Access token]**: visas via ditt  [!DNL LINE] konto på utvecklarportalen eller genom att klicka på  **[!UICONTROL Get access token]** knappen.
   * **[!UICONTROL Access token expiration date]**: gör att du kan ange förfallodatum för åtkomsttoken.
   * **[!UICONTROL LINE subscription service]**: gör att du kan ange vilka tjänster som användarna ska prenumerera på.

1. När konfigurationen är klar klickar du på **[!UICONTROL Save]**.

1. I **[!UICONTROL Explorer]** väljer du **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL LINE workflows]** för att kontrollera om arbetsflödena **[!UICONTROL LINE V2 access token update (updateLineAccessToken)]** och **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** har startats.

[!DNL LINE] är nu konfigurerat i Adobe Campaign och du kan börja skapa och skicka LINE-leveranser till prenumeranter.

## Skapa radleverans {#creating-the-delivery}

>[!NOTE]
>
>När du skickar en [!DNL LINE]-leverans till en ny mottagare för första gången måste du lägga till det officiella LINE-meddelandet om användningsvillkoren och samtycke i leveransen. Det officiella meddelandet finns på länken [som följer](https://terms.line.me/OA_privacy/).

Om du vill skapa en [!DNL LINE]-leverans måste du följa dessa steg:

1. På fliken **[!UICONTROL Campaigns]** väljer du **[!UICONTROL Deliveries]** och klickar sedan på knappen **[!UICONTROL Create]**.

   ![](assets/line_message_07.png)

1. Välj **[!UICONTROL LINE V2 delivery]** leveransmall.

   ![](assets/line_message_01.png)

1. Identifiera leveransen med en **[!UICONTROL Label]**, **[!UICONTROL Delivery code]** och **[!UICONTROL Description]**. Mer information om detta finns i [det här avsnittet](steps-create-and-identify-the-delivery.md#identifying-the-delivery).

1. Klicka på **[!UICONTROL Continue]** för att skapa leveransen.

1. Välj **[!UICONTROL To]** i leveransredigeraren för att ange [!DNL LINE]-leveransens mottagare som mål. Målinriktning utförs på **[!UICONTROL Visitor subscriptions (nms:visitorSub)]**.

   Mer information finns i [Identifiera målpopulationer](steps-defining-the-target-population.md).

   ![](assets/line_message_08.png)

1. Klicka på **[!UICONTROL Add]** för att välja din **[!UICONTROL Delivery target population]**.

   ![](assets/line_message_09.png)

1. Välj om du vill ange [!DNL LINE] som abonnent direkt eller om du vill ange användare som mål beroende på deras [!DNL LINE]-prenumeration och klicka på **[!UICONTROL Next]**. I det här exemplet har vi valt **[!UICONTROL By LINE V2 subscription]**.

1. Välj **[!UICONTROL Line-V2]** i listrutan **[!UICONTROL Folder]** och sedan din [!DNL LINE]-tjänst. Klicka på **[!UICONTROL Finish]** och **[!UICONTROL Ok]** för att börja personalisera leveransen.

   ![](assets/line_message_10.png)

1. Klicka på **[!UICONTROL Add]** i leveransredigeraren för att lägga till ett eller flera meddelanden och välj **[!UICONTROL Content type]**.

   Mer information om de olika **[!UICONTROL Content type]** som är tillgängliga finns i [Definiera innehållstypen](#defining-the-content).

   ![](assets/line_message_11.png)

1. När leveransen har skapats och konfigurerats på rätt sätt kan du skicka den till det mål som definierades tidigare.

   Mer information om hur du skickar en leverans finns i [Skicka meddelanden](sending-messages.md).

1. När du har skickat meddelandet kan du visa rapporten och mäta hur effektiv leveransen är.

   Mer information om [!DNL LINE]-rapporter finns i [Åtkomstrapporter](#accessing-reports).

## Definiera innehållstypen {#defining-the-content}

Om du vill definiera innehållet i en [!DNL LINE]-leverans måste du först lägga till meddelandetypen i leveransen. Varje [!DNL LINE]-leverans kan innehålla upp till 5 meddelanden.

Du kan välja mellan tre meddelandetyper:

* [Textmeddelande](#configuring-a-text-message-delivery)
* [Bild och länk](#configuring-an-image-and-link-delivery)
* [Videomeddelande](#configuring-a-video-message-delivery)

### Konfigurera leverans av textmeddelande {#configuring-a-text-message-delivery}

>[!NOTE]
>
>Med syntaxen `<%@ include option='NmsServer_URL' %>/webApp/APP3?id=<%=escapeUrl(cryptString(visitor.id))%>` kan du inkludera en länk till ett webbprogram i ett LINE-meddelande.

En **[!UICONTROL Text message]** [!DNL LINE]-leverans är ett meddelande som skickas till mottagare i textform.

![](assets/line_message_02.png)

Konfigurationen för den här meddelandetypen liknar konfigurationen för **[!UICONTROL Text]** i ett e-postmeddelande. Mer information finns på den här [sidan](defining-the-email-content.md#message-content).

### Konfigurera en bild- och länkleverans {#configuring-an-image-and-link-delivery}

En **[!UICONTROL Image and link]** [!DNL LINE]-leverans är ett meddelande som skickas till mottagarna i form av en bild som kan innehålla en eller flera URL:er.

Du kan använda:

* a **[!UICONTROL Personalized image]**,

   >[!NOTE]
   >
   >Du kan använda variabeln **%SIZE%** för att optimera bildvisningen enligt skärmstorleken för mottagarens mobila enhet.

   ![](assets/line_message_04.png)

* en **[!UICONTROL Image URL]**-skärmstorlek per enhet,

   ![](assets/line_message_03.png)

   Med alternativet **[!UICONTROL Define images per device screen size]** kan du använda olika bildupplösningar för att optimera synligheten för leverans på mobila enheter. Endast bilder med samma höjd och bredd stöds.

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

   I **[!UICONTROL Links]**-avsnittet kan du välja mellan olika layouter som delar upp bilden i flera klickbara områden. Du kan sedan tilldela var och en av dem en dedikerad **[!UICONTROL Link URL]**.

   ![](assets/line_message_05.png)

### Konfigurera leverans av videomeddelanden {#configuring-a-video-message-delivery}

En **[!UICONTROL Video message]** [!DNL LINE]-leverans är ett meddelande som skickas till mottagare i form av en video som kan innehålla en URL.

I fältet **[!UICONTROL Preview Image URL]** kan du lägga till URL:en för en förhandsvisningsbild med en teckengräns på 1 000. JPEG och PNG stöds med en filstorleksgräns på 1 MB.

I fältet **[!UICONTROL Video Image URL]** kan du lägga till URL-adressen för videofilen med en teckengräns på 1 000. Endast mp4-format stöds med en filstorleksgräns på 200 MB.

Observera att breda eller höga videor kan beskäras när de spelas upp på vissa enheter.

![](assets/line_message_06.png)

## Åtkomst till rapporter {#accessing-reports}

När du har skickat leveransen kan du visa dina [!DNL LINE]-rapporter via menyn **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** från **[!UICONTROL Explorer]**.

>[!NOTE]
>
>Spårningsrapporterna visar klickfrekvensen. [!DNL LINE] tar inte hänsyn till den öppna räntan.

![](assets/line_reports_01.png)

För [!DNL LINE]-tjänstrapporter öppnar du menyn **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Services and Subscriptions]** > **[!UICONTROL LINE-V2]** från fliken **[!UICONTROL Explorer]**. Klicka sedan på ikonen **[!UICONTROL Reports]** i tjänsten [!DNL LINE].

![](assets/line_reports.png)

## Exempel: skapa och skicka ett personligt LINE-meddelande {#example--create-and-send-a-personalized-line-message}

I det här exemplet ska vi skapa och konfigurera ett textmeddelande och en bild som innehåller data som ska anpassas efter mottagaren.

1. Skapa din [!DNL LINE]-leverans genom att klicka på knappen **[!UICONTROL Create]** på fliken **[!UICONTROL Campaign]**.

   ![](assets/line_usecase.png)

1. Välj leveransmallen **[!UICONTROL LINE V2 delivery]** och ge leveransen ett namn.

   ![](assets/line_usecase_01.png)

1. Välj målpopulation i konfigurationsfönstret för leveransen.

   Mer information finns i [Identifiera målpopulationer](steps-defining-the-target-population.md).

   ![](assets/line_usecase_02.png)

1. Klicka på **[!UICONTROL Add]** för att skapa meddelandet och välj **[!UICONTROL Content type]**.

   Här vill vi först skapa en **[!UICONTROL Text message]**.

   ![](assets/line_usecase_03.png)

1. Placera markören där du vill infoga den anpassade texten och klicka på listruteikonen och välj **[!UICONTROL Visitor]** > **[!UICONTROL First name]**.

   ![](assets/line_usecase_05.png)

1. Gör så här för att lägga till en bild och välja **[!UICONTROL Image and links]** i listrutan **[!UICONTROL Message type]**.

   Lägg till din **[!UICONTROL Image URL]**.

   ![](assets/line_usecase_07.png)

1. I avsnittet **[!UICONTROL Links]** väljer du den layout som ska dela upp bilden i flera klickbara områden.

1. Tilldela en URL till varje område i bilden.

   ![](assets/line_usecase_08.png)

1. Spara leveransen och klicka sedan på **[!UICONTROL Send]** för att analysera och skicka den till målet.

   Leveransen skickas till målet.

   ![](assets/line_usecase_06.png)

