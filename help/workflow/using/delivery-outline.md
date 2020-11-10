---
title: Leveransbeskrivning
description: Läs mer om arbetsflödesaktiviteten i leveransutkast
page-status-flag: never-activated
uuid: 2b924cc6-6b71-481e-acab-2d035bbc2852
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: a2a65f97-425b-44b2-8cf4-beea850423bc
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# Leveransbeskrivning{#delivery-outline}

Med **leveransdispositionen** kan du använda en disposition i ett kampanjarbetsflöde. Dispositionen måste ha skapats i kampanjen i förväg.

Mer information om leveransdispositioner i Adobe Campaign finns i det här [avsnittet](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Om du vill konfigurera aktiviteten behöver du bara markera den disposition du vill ha samt det planerade kontaktdatumet. Du kan lägga till filtreringsregler genom att lägga till typologier eller typologiregler.

## Exempel: Infoga ett erbjudande via en leveransdisposition {#example--inserting-an-offer-via-a-delivery-outline}

Med aktiviteten **leveransdisposition** , som är tillgänglig i kampanjarbetsflödena, kan du presentera erbjudanden som refereras i en leveransdisposition från den pågående kampanjen.

>[!NOTE]
>
>Paketet **Interaction** måste installeras.

1. Lägg till en dispositionsaktivitet för leverans i ett arbetsflöde innan du lägger till en leveransaktivitet.
1. I dispositionsaktiviteten för leverans anger du den disposition du vill använda.

   Mer information om hur du anger leveransdispositioner finns i det här [avsnittet](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Fyll i de tillgängliga fälten efter leverans.
1. Det finns två möjliga fall:

   * Markera **[!UICONTROL Restrict the number of propositions selected]** rutan om du vill ringa erbjudandemotorn. Ange erbjudandeutrymme och antalet offerter som ska presenteras i leveransen.

      Anbudsvikterna och reglerna för rätt till uppgradering kommer att beaktas av erbjudandemotorn.

   * Om du inte markerar kryssrutan visas alla erbjudanden i leveransdispositionen utan att du behöver ringa till erbjudandemotorn.

   Förhandsgranskningen tar hänsyn till antalet erbjudanden som anges i leveransen. När du kör ett arbetsflöde är det numret som anges i leveransdispositionen som beaktas.

   ![](assets/int_compo_offre_wf1.png)

