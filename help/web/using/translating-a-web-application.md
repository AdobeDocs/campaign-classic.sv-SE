---
product: campaign
title: Översätt en webbapplikation
description: Översätt en webbapplikation
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Web Apps
exl-id: 82c5c610-8161-4686-aa79-1b690e763765
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 5%

---

# Översätt en webbapplikation{#translating-a-web-application}



Du kan översätta webbprogramsidor som skapats med Adobe Campaign Digital Content Editor (DCE).

Om du väljer minst ett ytterligare språk via **[!UICONTROL Localization]** i **[!UICONTROL Properties]** för ett webbprogram blir ett nytt alternativ tillgängligt när du lägger till ett HTML-innehållsblock på en sida som redigeras med DCE.

Med det här alternativet kan du ange om blockinnehållet måste översättas eller inte.

Strängar som ska översättas samlas in på samma sätt som andra strängar i webbprogrammet via **[!UICONTROL Translations]** -fliken i programmet. Mer information finns på [den här sidan](translating-a-web-form.md).

Så här flaggar du strängar som ska översättas:

1. Öppna en innehållssida som har redigerats med DCE i ett webbprogram.

   ![](assets/dce_translation_3.png)

1. Markera ett HTML-block.
1. I parameterblocket till höger visas **[!UICONTROL Localization]** kan du flagga innehållet i det markerade blocket. Som standard ska bara sidans namn översättas.

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

1. När du är klar med att flagga strängarna går du tillbaka till webbprogrammet och väljer **[!UICONTROL Translations]** -fliken.
1. Välj **[!UICONTROL Collect the strings to translate]**.  Strängarna som är flaggade i DCE läggs till i webbprogrammets strängar.

   >[!NOTE]
   >
   >När strängarna har samlats in tas de inte bort från listan om du tar bort översättningsflaggan i DCE. På så sätt kan du behålla dem i översättningsminnet.

1. Översätt och godkänn strängarna.

   Du kan sedan förhandsgranska översättningarna genom att välja önskat språk i dialogrutan **[!UICONTROL Preview]** -fliken i webbprogrammet.
