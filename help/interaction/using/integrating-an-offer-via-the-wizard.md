---
product: campaign
title: Integrera ett erbjudande via guiden
description: Integrera ett erbjudande via guiden
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 64aea8b9-7f06-4db0-a3e6-6a0e17c3ddcb
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%

---

# Integrera ett erbjudande via guiden{#integrating-an-offer-via-the-wizard}



När du skapar en leverans finns det två möjliga metoder för att integrera erbjudanden:

* Anropa erbjudandemotorn i en leverans.
* Referera till erbjudanden via kampanjens leveranskonturer. Den här metoden används vanligtvis för papperskampanjer.

## Leverera med ett samtal till erbjudandemotorn {#delivering-with-a-call-to-the-offer-engine}

Om du vill presentera ett erbjudande under en marknadsföringskampanj skapar du bara en klassisk leveransåtgärd utifrån den valda kanalen. Erbjudandemotorn anropas när leveransinnehållet har definierats genom att klicka på ikonen **[!UICONTROL Offers]** som finns i verktygsfältet.

![](assets/offer_delivery_009.png)

Läs mer om leveranser av direkt e-post [i det här avsnittet](../../delivery/using/about-direct-mail-channel.md). Läs mer om marknadsföringskampanjer [i det här avsnittet](../../campaign/using/setting-up-marketing-campaigns.md).

### De viktigaste stegen för att infoga ett erbjudande i en leverans {#main-steps-for-inserting-an-offer-into-a-delivery}

Så här infogar du offertförslag i en leverans:

1. Klicka på ikonen Erbjudanden i leveransfönstret.

   ![](assets/offer_delivery_001.png)

1. Välj det utrymme som passar er erbjudandemiljö.

   ![](assets/offer_delivery_002.png)

1. Om du vill förfina motorns urval av erbjudanden väljer du antingen den kategori från vilken erbjudandena som ska presenteras är en del av, eller ett eller flera teman. Vi rekommenderar att du bara använder ett av dessa fält i taget för att undvika att överbelasta begränsningarna.

   ![](assets/offer_delivery_003.png)

   ![](assets/offer_delivery_004.png)

1. Ange antalet erbjudanden som du vill infoga i leveransbrödtexten.

   ![](assets/offer_delivery_005.png)

1. Välj alternativet **[!UICONTROL Exclude non-eligible recipients]** om det behövs. Mer information finns i [Parametrar för anrop av erbjudandemotor](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_006.png)

1. Välj alternativet **[!UICONTROL Do not display anything if no offers are selected]** om det behövs. Mer information finns i [Parametrar för anrop av erbjudandemotor](#parameters-for-calling-offer-engine).

   ![](assets/offer_delivery_007.png)

1. Infoga egenskaperna i leveransinnehållet med hjälp av kopplingsfälten. Antalet tillgängliga offerter beror på hur motoranropet är konfigurerat och deras ordning beror på erbjudandenas prioritet.

   ![](assets/offer_delivery_008.png)

1. Slutför innehållet och skicka leveransen som vanligt.

   ![](assets/offer_delivery_010.png)

### Parametrar för anrop av erbjudandemotor {#parameters-for-calling-offer-engine}

* **[!UICONTROL Space]** : utrymme i erbjudandemiljön som måste väljas för att erbjudandemotorn ska aktiveras.
* **[!UICONTROL Category]** : den mapp där erbjudandena sorteras. Om ingen kategori anges kommer alla erbjudanden i miljön att beaktas av erbjudandemotorn, såvida inte ett tema väljs.
* **[!UICONTROL Themes]** : nyckelord har definierats uppströms i kategorierna. Dessa fungerar som ett filter och låter dig förfina antalet erbjudanden som ska presenteras genom att välja dem i en uppsättning kategorier.
* **[!UICONTROL Number of propositions]** : antal erbjudanden som returneras av motorn och som kan infogas i leveransenheten. Om de inte infogas i meddelandet kommer erbjudandena fortfarande att genereras, men de visas inte.
* **[!UICONTROL Exclude non-eligible recipients]** : Med det här alternativet kan du aktivera eller inaktivera undantaget för mottagare som det inte finns tillräckligt med giltiga erbjudanden för. Antalet giltiga förslag kan vara lägre än det begärda antalet. Om den här rutan är markerad kommer mottagare som inte har tillräckligt med erbjudanden att uteslutas från leveransen. Om du inte markerar det här alternativet kommer dessa mottagare inte att uteslutas, men de kommer inte att ha det begärda antalet förslag.
* **[!UICONTROL Do not display anything if no offer is selected]** : Med det här alternativet kan du välja hur meddelandet ska behandlas om något av förslagen inte finns. När den här rutan är markerad visas inte representationen av det saknade förslaget och inget innehåll visas i meddelandet för det här förslaget. Om rutan inte är markerad avbryts själva meddelandet när det skickas och mottagarna får inte längre några meddelanden.

### Infoga ett offertförslag i en leverans {#inserting-an-offer-proposition-into-a-delivery}

Representationen av de erbjudanden som ska presenteras infogas i leveransinnehållet via kopplingsfälten. Antalet offerter definieras i parametrarna för anropet till erbjudandemotorn.

Leveransen kan anpassas med hjälp av erbjudandets fält eller, om det är ett e-postmeddelande, med återgivningsfunktionerna.

![](assets/offer_delivery_011.png)

## Leverera med leveranskonturer {#delivering-with-delivery-outlines}

Du kan också presentera erbjudanden i en leverans med hjälp av leveranskonturer.

Mer information om leveransdispositioner finns i guiden [Kampanj - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Skapa en ny kampanj eller få tillgång till en befintlig kampanj.
1. Få åtkomst till leveranskonturer via kampanjens **[!UICONTROL Edit]** > **[!UICONTROL Documents]**-flik.
1. Lägg till en disposition och infoga så många erbjudanden du vill i den genom att högerklicka på dispositionen och välja **[!UICONTROL New]** > **[!UICONTROL Offer]**. Spara sedan kampanjen.

   ![](assets/int_compo_offre1.png)

1. Skapa en leverans vars leveranskonturer du har tillgång till (t.ex. en direktleverans).
1. När du redigerar leveransen klickar du på **[!UICONTROL Select a delivery outline]**.

   >[!NOTE]
   >
   >Beroende på typ av leverans finns det här alternativet på menyn **[!UICONTROL Properties]** > **[!UICONTROL Advanced]** (för e-postleveranser till exempel).

   ![](assets/int_compo_offre2.png)

1. Med knappen **[!UICONTROL Offers]** kan du sedan konfigurera erbjudandeutrymmet och antalet erbjudanden som ska finnas i leveransen.

   ![](assets/int_compo_offre3.png)

1. Lägg till offerterna i leveransbrödtexten med hjälp av anpassningsfälten (mer information finns i avsnittet [Infoga ett offertförslag i ett leveransavsnitt](#inserting-an-offer-proposition-into-a-delivery)) eller, om det är en direktmeddelandeleverans, genom att redigera extraheringsfilformatet.

   Propositioner väljs ut bland de erbjudanden som refereras i leveransdispositionen.

   >[!NOTE]
   >
   >Information om rangordningarna och vikterna sparas endast i förslagstabellen om erbjudandena genereras direkt i leveransen.
