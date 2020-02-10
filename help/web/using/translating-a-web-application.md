---
title: Översätta ett webbprogram
seo-title: Översätta ett webbprogram
description: Översätta ett webbprogram
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# Översätta ett webbprogram{#translating-a-web-application}

Du kan översätta webbprogramsidor som skapats med Adobe Campaign Digital Content Editor (DCE).

Om du väljer ytterligare ett språk via fliken **[!UICONTROL Localization]** i **[!UICONTROL Properties]** ett webbprogram blir ett nytt alternativ tillgängligt när du lägger till ett HTML-innehållsblock på en sida som redigeras med DCE.

Med det här alternativet kan du ange om blockinnehållet måste översättas eller inte.

Strängar som ska översättas samlas in på samma sätt som andra strängar i webbprogrammet via fliken **[!UICONTROL Translations]** i programmet. Mer information finns på [den här sidan](../../web/using/translating-a-web-form.md).

Så här flaggar du strängar som ska översättas:

1. Öppna en innehållssida som har redigerats med DCE i ett webbprogram.

   ![](assets/dce_translation_3.png)

1. Markera ett HTML-block.
1. I parameterblocket till höger kan du med alternativet flagga innehållet i det markerade blocket **[!UICONTROL Localization]** . Som standard ska bara sidans namn översättas.

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >Strängar får inte innehålla fler än 1023 tecken.

   Det finns tre specifika fall:

   * När det markerade blocket innehåller flera strängar/block flaggas det som en sträng som ska översättas. Strängen innehåller sedan HTML-koden för elementen i det här blocket.
   * När du vill flagga ett block som innehåller flera strängar och om minst en av strängarna redan är flaggad visas en varning. Du kan sedan ta bort flaggan från den isolerade strängen och lägga till hela blocket.

      ![](assets/dce_translation_4.png)

   * När du vill ta bort flaggan från en sträng i ett block som redan är flaggat kan du inte ändra strängöversättningsalternativet direkt. Du kan emellertid komma åt blocket som innehåller strängen för att ändra den.

      ![](assets/dce_translation_2.png)

1. När du har flaggat strängarna går du tillbaka till webbprogrammet och väljer **[!UICONTROL Translations]** fliken.
1. Välj **[!UICONTROL Collect the strings to translate]**. Strängarna som är flaggade i DCE läggs till i webbprogrammets strängar.

   >[!NOTE]
   >
   >När strängarna har samlats in tas de inte bort från listan om du tar bort översättningsflaggan i DCE. På så sätt kan du behålla dem i översättningsminnet.

1. Översätt och godkänn strängarna.

   Du kan sedan förhandsgranska översättningarna genom att välja önskat språk på fliken **[!UICONTROL Preview]** i webbprogrammet.

