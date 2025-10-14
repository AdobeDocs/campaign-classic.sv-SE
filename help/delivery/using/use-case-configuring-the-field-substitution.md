---
product: campaign
title: 'Användningsfall: konfigurera fältersättningen'
description: 'Användningsfall: konfigurera fältersättningen'
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Seed Address
exl-id: 3f567b2d-6f98-4831-af84-7db17fd12c6e
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 4%

---

# Användningsfall: konfigurera fältersättningen{#use-case-configuring-the-field-substitution}



Med Slumpmässig fältersättning kan du tilldela ett värde från mottagarlistan till de dirigerade adresser som är tomma när användaren använder det här värdet i en leverans (till exempel namn, stad).

Med denna ersättning kan du spara tid när du skapar leveransen: i stället för att manuellt lägga till det önskade värdet till startadresserna, återställer ersättningen det här värdet i listan över mottagare som levereras och använder det på startadresserna.

## Kontext {#context}

I det här fallet vill webbplatsen **Mitt onlinebibliotek** skicka en rabatt till sina kunder utifrån deras favoritlitterära genre.

Leveranshanteraren har integrerat ett anpassningsfält som är länkat till en favoritgenre i e-postmeddelandet. Målet är att använda vissa dirigerade adresser: dessa dirigerade adresser har personaliseringsfältet i tabellen, men inget värde sparas där.

Om du vill använda slumpmässig fältersättning måste du ha:

* en leverans med ett eller flera personaliseringsfält,
* dirigerade adresser vars **datarema** ändras enligt de personaliseringsfält som används i leveransen.

## Skapa en leverans {#step-1---creating-a-delivery}

Stegen för att skapa en leverans beskrivs i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html){target="_blank"}.

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

Du måste uppdatera den här datarchemaändringen för att den ska kunna visas i dirigerade adresser **Indataformulär**. Se avsnittet [Uppdatera indataformuläret](use-case-selecting-seed-addresses-on-criteria.md#updating-the-input-form).

## Konfigurera personalisering {#configuring-personalization}

1. Öppna en leverans.

   I det här exemplet har leveransen två anpassningsfält: mottagarens **förnamn** och mottagarens **favoritlitterära genre**.

   ![](assets/dlv_seeds_usecase_25.png)

1. Konfigurera leveranslistan och dina dirigerade adresser. Se [Identifiera målpopulationer](steps-defining-the-target-population.md).

   I det här exemplet väljer användaren användare vars **favoritlitterära genre** är Sci-Fi som huvudmålpopulation.

   ![](assets/dlv_seeds_usecase_26.png)

   Användaren lägger till dirigerade adresser till leveransen.

   ![](assets/dlv_seeds_usecase_27.png)

   >[!NOTE]
   >
   >Mer information om länken **[!UICONTROL Edit the dynamic condition...]** finns i [Använd skiftläge: välj startadresser på villkor ](use-case-selecting-seed-addresses-on-criteria.md).

1. Klicka på fliken **[!UICONTROL Preview]** och välj sedan en startadress för att testa personaliseringen.

   ![](assets/dlv_seeds_usecase_28.png)

   Du ser att ett av anpassningsfälten är tomt. Eftersom startadressen inte har data för det här fältet kan HTML innehållsförhandsvisning inte visa ett värde.

   Slumpmässig ersättning av fält utförs **vid leveranstillfället**.

1. Klicka på knappen **[!UICONTROL Send]**.
1. Analysera leveransen och **bekräfta leveransen**.

   dirigerade adresser får leveransen i sin inkorg.

   Fältpersonalisering är effektivt.

   ![](assets/dlv_seeds_usecase_08.png)
