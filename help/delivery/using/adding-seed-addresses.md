---
title: Lägga till fröadresser
seo-title: Lägga till fröadresser
description: Lägga till fröadresser
seo-description: null
page-status-flag: never-activated
uuid: e94ddd46-bed6-4505-91b7-7e17abb0e9c8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: 0b9b53bf-4dd2-416c-894e-393aded489f8
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 5%

---


# Lägga till fröadresser{#adding-seed-addresses}

## Utsändningsadresser i en leverans {#seed-addresses-in-a-delivery}

Om du vill lägga till specifika dirigerade adresser för en leverans klickar du på **[!UICONTROL To]** länken och väljer sedan **[!UICONTROL Seed addresses]** fliken.

![](assets/s_ncs_user_edit_del_addresses_tab.png)

Det finns tre möjliga insättningslägen:

1. Ange enskilda dirigeringsadresser.

   Det gör du genom att klicka på **[!UICONTROL Add]** knappen och definiera innehållet i adressfälten. Upprepa för varje adress. Mer information om detta finns i [det här avsnittet](../../message-center/using/managing-seed-addresses-in-transactional-messages.md#creating-a-seed-address).

1. Importera adressmallar och anpassa dem efter dina behov.

   Om du vill göra det klickar du på **[!UICONTROL Import seed templates...]** länken och väljer den mapp som innehåller adressmallarna. Mer information finns i [Skapa dirigerade adressmallar](../../delivery/using/creating-seed-addresses.md#creating-seed-address-templates).

   När de har lagts till kan du dubbelklicka på dem eller klicka på **[!UICONTROL Detail...]** knappen för att anpassa innehållet i respektive adress.

1. Skapa ett villkor som dynamiskt markerar de kontrolladresser som ska infogas.

   Det gör du genom att klicka på **[!UICONTROL Edit the dynamic condition...]** länken och sedan ange markeringsparametrarna för startadressen. Du kan t.ex. inkludera alla dirigerade adresser i en viss mapp eller dirigerade adresser som tillhör en viss avdelning i organisationen.

   Ett exempel visas i det här avsnittet: [Användningsfall: välja startadresser efter villkor](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

>[!NOTE]
>
>Det här alternativet används när den mottagartabell som används inte är standardtabellen **nms:mottagare** och du använder den återgivningsfunktion för inkorgen som finns i Adobe Campaign **[!UICONTROL Deliverability]** modul.
>
>Mer information finns i [Använda en extern mottagartabell](../../delivery/using/using-an-external-recipient-table.md) och i dokumentationen om [inkorgsåtergivning](../../delivery/using/inbox-rendering.md).

För leveranser kan du också anpassa hur adresser infogas i extraheringsfilen. Som standard infogas de i utdatafilens sorteringsordning, men du kan välja att infoga dem i slutet eller början av filen, eller slumpmässigt bland mottagarna av huvudmålet.

![](assets/s_ncs_user_edit_del_addresses_sort.png)

## Utsändningsadresser i en kampanj {#seed-addresses-in-a-campaign}

Om du vill lägga till dirigerade adresser till ett mål för en kampanj väljer du åtgärden och klickar på **[!UICONTROL Edit]** -fliken.

Klicka på **[!UICONTROL Advanced campaign settings...]** länken och sedan på **[!UICONTROL Seed addresses]** fliken, som visas nedan:

![](assets/s_ncs_user_edit_op_addresses_tab.png)

Startadresserna som infogats från kampanjen läggs till i målet för varje leverans i kampanjen.
