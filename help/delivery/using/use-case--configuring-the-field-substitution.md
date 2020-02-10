---
title: '"Användningsfall: konfigurera fältersättning"'
seo-title: '"Användningsfall: konfigurera fältersättning"'
description: '"Användningsfall: konfigurera fältersättning"'
seo-description: null
page-status-flag: never-activated
uuid: 7f083dc6-e6d7-4eea-ac66-87674716515c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: a104fcab-75e6-4d73-bc3d-88570de6df7f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 003bac4c5d89290b9d3653d6ddfab7284b68642d

---


# Användningsfall: konfigurera fältersättning{#use-case-configuring-the-field-substitution}

Med Slumpmässig fältersättning kan du tilldela ett värde från mottagarlistan till de dirigerade adresser som är tomma när användaren använder det här värdet i en leverans (exempel: namn, ort osv.).

Med den här ersättningen sparar du tid när du skapar leveransen: I stället för att manuellt lägga till det önskade värdet till startadresserna, återställer ersättningen det här värdet i listan över mottagare som anges av leveransen och använder det på startadresserna.

## Kontext {#context}

I det här fallet vill webbplatsen **Mitt onlinebibliotek** skicka en rabatt till sina kunder baserat på deras favoritlitterära genre.

Leveranshanteraren har integrerat ett anpassningsfält som är länkat till en favoritgenre i sitt e-postmeddelande. Han skulle vilja använda några frön-adresser. Dessa dirigerade adresser har anpassningsfältet i sin tabell, men inget värde sparas där.

Om du vill använda slumpmässig fältersättning måste du ha:

* en leverans med ett eller flera personaliseringsfält,
* dirigerade adresser vars **dataschema** ändras enligt de anpassningsfält som används i leveransen.

## Skapa en leverans {#step-1---creating-a-delivery}

Hur du skapar en leverans beskrivs i avsnittet [Skapa en e-postleverans](../../delivery/using/creating-an-email-delivery.md) .

I det här exemplet har leveranshanteraren skapat nyhetsbrevet.

![](assets/dlv_seeds_usecase_24.png)

## Redigera dataschemat för dirigerade adresser {#editing-the-seed-addresses-data-schema}

Instruktionerna för hur du ändrar ett dataschema finns i avsnittet.

I det här exemplet får dataschemat för dirigerade adresser ett värde som skapas från mottagarnas dataschema:

```
 <attribute label="Favorite literary genre" length="80" name="favoriteLiteraryGenre"
               type="string" userEnum="favoriteLiteraryGenre"/>
```

Med den här uppräkningen kan användaren ange klienternas favoritlitterära genre.

För att den här ändringen av dataschemat ska kunna visas i **indataformuläret** för dirigerade adresser måste du uppdatera den. Mer information finns i avsnittet [Uppdatera indataformulär](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md#updating-the-input-form) .

## Konfigurera personalisering {#configuring-personalization}

1. Öppna en leverans.

   I det här exemplet har leveransen två anpassningsfält: mottagarens **förnamn** och mottagarens **favoritlitterära genre**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Konfigurera leveranslistan och dina dirigerade adresser. Se [Identifiera målpopulationer](../../delivery/using/steps-defining-the-target-population.md).

   I det här exemplet väljer användaren användare vars **favoritlitterära genre** är Sci-Fi som huvudmålpopulation.

   ![](assets/dlv_seeds_usecase_26.png)

   Användaren lägger till dirigerade adresser till leveransen.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Mer information om **[!UICONTROL Edit the dynamic condition...]** länken finns i [Använda skiftläge: välja startadresser efter villkor](../../delivery/using/use-case--selecting-seed-addresses-on-criteria.md).

1. Klicka på **[!UICONTROL Preview]** fliken och välj sedan en startadress för att testa personaliseringen.

   ![](assets/dlv_seeds_usecase_28.png)

   Du ser att ett av anpassningsfälten är tomt. Eftersom startadressen inte har data för det här fältet kan inte förhandsvisningen av HTML-innehåll visa ett värde.

   Slumpmässig ersättning av fält utförs **vid leveranstillfället**.

1. Klicka på **[!UICONTROL Send]** knappen.
1. Analysera leveransen och **bekräfta leveransen**.

   dirigerade adresser får leveransen i sin inkorg.

   Fältpersonalisering är effektivt.

   ![](assets/dlv_seeds_usecase_08.png)
