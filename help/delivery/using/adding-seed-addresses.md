---
solution: Campaign Classic
product: campaign
title: Lägga till fröadresser
description: Lägga till fröadresser
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 5%

---


# Lägga till fröadresser{#adding-seed-addresses}

## dirigerade adresser i en leverans {#seed-addresses-in-a-delivery}

Om du vill lägga till specifika dirigerade adresser för en leverans klickar du på länken **[!UICONTROL To]** och väljer sedan fliken **[!UICONTROL Seed addresses]**.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Det finns tre möjliga insättningslägen:

1. Ange enskilda dirigeringsadresser.

   Det gör du genom att klicka på knappen **[!UICONTROL Add]** och definiera innehållet i adressfälten. Upprepa för varje adress. Mer information om detta finns i [det här avsnittet](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importera adressmallar och anpassa dem efter dina behov.

   Det gör du genom att klicka på länken **[!UICONTROL Import seed templates...]** och välja den mapp som innehåller adressmallarna. Mer information finns i [Skapa dirigerade adressmallar](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

   När de har lagts till kan du dubbelklicka på dem eller klicka på knappen **[!UICONTROL Detail...]** för att anpassa innehållet i respektive adress.

1. Skapa ett villkor som dynamiskt markerar de kontrolladresser som ska infogas.

   Det gör du genom att klicka på länken **[!UICONTROL Edit the dynamic condition...]** och sedan ange startadressparametrarna. Du kan t.ex. inkludera alla dirigerade adresser i en viss mapp eller dirigerade adresser som tillhör en viss avdelning i organisationen.

   Ett exempel visas i det här avsnittet: [Användningsfall: välja startadresser på villkor](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Det här alternativet används när den mottagartabell som används inte är standardtabellen **nms:mottagare** och du använder den inkorgsåtergivning som finns i Adobe Campaign **[!UICONTROL Deliverability]**-modulen.
>
>Mer information finns i [Använda en extern mottagartabell](../../delivery/using/using-an-external-recipient-table.md) och i dokumentationen om [inkorgsåtergivning](../../delivery/using/inbox-rendering.md).

För leveranser kan du också anpassa hur adresser infogas i extraheringsfilen. Som standard infogas de i utdatafilens sorteringsordning, men du kan välja att infoga dem i slutet eller början av filen, eller slumpmässigt bland mottagarna av huvudmålet.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## dirigerade adresser i en kampanj {#seed-addresses-in-a-campaign}

Om du vill lägga till dirigerade adresser till ett mål för en kampanj väljer du åtgärden och klickar på fliken **[!UICONTROL Edit]**.

Klicka på länken **[!UICONTROL Advanced campaign settings...]** och sedan på fliken **[!UICONTROL Seed addresses]** enligt nedan:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Startadresserna som infogats från kampanjen läggs till i målet för varje leverans i kampanjen.
