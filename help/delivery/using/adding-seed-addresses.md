---
product: campaign
title: Lägg till dirigerade adresser
description: Lägg till dirigerade adresser
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Seed Address
role: User
exl-id: ae6eb4b0-b419-4661-9d63-e758f0242a0f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 5%

---

# Lägg till dirigerade adresser{#adding-seed-addresses}

## Utsändningsadresser i en leverans {#seed-addresses-in-a-delivery}

Om du vill lägga till specifika dirigerade adresser för en leverans klickar du på länken **[!UICONTROL To]** och väljer fliken **[!UICONTROL Seed addresses]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Det finns tre möjliga insättningslägen:

1. Ange enskilda dirigeringsadresser.

   Det gör du genom att klicka på knappen **[!UICONTROL Add]** och definiera innehållet i adressfälten. Upprepa för varje adress.

1. Importera adressmallar och anpassa dem efter dina behov.

   Om du vill göra det klickar du på länken **[!UICONTROL Import seed templates...]** och väljer den mapp som innehåller adressmallarna. Mer information om detta finns i [det här avsnittet](creating-seed-addresses.md#creating-seed-address-templates).

   När de har lagts till kan du dubbelklicka på dem eller klicka på knappen **[!UICONTROL Detail...]** för att anpassa innehållet i varje adress.

1. Skapa ett villkor som dynamiskt markerar de kontrolladresser som ska infogas.

   Det gör du genom att klicka på länken **[!UICONTROL Edit the dynamic condition...]** och sedan ange parametrar för val av dirigeringsadress. Du kan t.ex. inkludera alla dirigerade adresser i en viss mapp eller dirigerade adresser som tillhör en viss avdelning i organisationen.

   Ett exempel på detta visas i det här avsnittet: [Använd skiftläge: välj startadresser på villkor](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Det här alternativet används när den mottagartabell som används inte är standardtabellen **nms:mottagare** och du använder inkorgsåtergivning som ingår i Adobe Campaign **[!UICONTROL Deliverability]** -modulen.
>
>Mer information finns i [Använd en extern mottagartabell](using-an-external-recipient-table.md) och i dokumentationen om [Inkorgsåtergivning](inbox-rendering.md).

För leveranser kan du också anpassa hur adresser infogas i extraheringsfilen. Som standard infogas de i utdatafilens sorteringsordning, men du kan välja att infoga dem i slutet eller början av filen, eller slumpmässigt bland mottagarna av huvudmålet.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Utsändningsadresser i en kampanj {#seed-addresses-in-a-campaign}

Om du vill lägga till dirigerade adresser till ett mål för en kampanj väljer du åtgärden och klickar på fliken **[!UICONTROL Edit]**.

Klicka på länken **[!UICONTROL Advanced campaign settings...]** och sedan på fliken **[!UICONTROL Seed addresses]** enligt nedan:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Startadresserna som infogats från kampanjen läggs till i målet för varje leverans i kampanjen.
