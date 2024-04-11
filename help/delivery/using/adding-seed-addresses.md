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

Om du vill lägga till specifika dirigerade adresser för en leverans klickar du på **[!UICONTROL To]** klicka på **[!UICONTROL Seed addresses]** -fliken.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Det finns tre möjliga insättningslägen:

1. Ange enskilda dirigeringsadresser.

   Klicka på **[!UICONTROL Add]** och definiera innehållet i adressfälten. Upprepa för varje adress.

1. Importera adressmallar och anpassa dem efter dina behov.

   Klicka på **[!UICONTROL Import seed templates...]** och välj den mapp som innehåller adressmallarna. Mer information om detta finns i [det här avsnittet](creating-seed-addresses.md#creating-seed-address-templates).

   Om det behövs kan du dubbelklicka på dem eller klicka på **[!UICONTROL Detail...]** för att anpassa innehållet i varje adress.

1. Skapa ett villkor som dynamiskt markerar de kontrolladresser som ska infogas.

   Klicka på **[!UICONTROL Edit the dynamic condition...]** och ange parametrar för val av dirigeringsadress. Du kan t.ex. inkludera alla dirigerade adresser i en viss mapp eller dirigerade adresser som tillhör en viss avdelning i organisationen.

   Ett exempel visas i det här avsnittet: [Använd skiftläge: välj startadresser på villkor](use-case-selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Det här alternativet används när mottagartabellen som används inte är standard **nms:mottagare** och du använder funktionerna för inkorgsåtergivning i Adobe Campaign **[!UICONTROL Deliverability]** -modul.
>
>Mer information finns i [Använd en extern mottagartabell](using-an-external-recipient-table.md) och dokumentationen om [Inkorgsåtergivning](inbox-rendering.md).

För leveranser kan du också anpassa hur adresser infogas i extraheringsfilen. Som standard infogas de i utdatafilens sorteringsordning, men du kan välja att infoga dem i slutet eller början av filen, eller slumpmässigt bland mottagarna av huvudmålet.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Utsändningsadresser i en kampanj {#seed-addresses-in-a-campaign}

Om du vill lägga till dirigerade adresser till ett mål för en kampanj väljer du åtgärden och klickar på knappen **[!UICONTROL Edit]** -fliken.

Klicka på **[!UICONTROL Advanced campaign settings...]** och sedan **[!UICONTROL Seed addresses]** enligt nedan:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Startadresserna som infogats från kampanjen läggs till i målet för varje leverans i kampanjen.
