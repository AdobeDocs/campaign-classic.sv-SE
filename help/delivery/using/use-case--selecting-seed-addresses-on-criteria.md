---
product: campaign
title: '"Användningsfall: välja fröadresser enligt villkor"'
description: '"Användningsfall: välja fröadresser enligt villkor"'
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
exl-id: 091648b8-bf2d-4595-8be3-287f1ac48edd
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 3%

---

# Användningsfall: välja fröadresser enligt villkor{#use-case-selecting-seed-addresses-on-criteria}

![](../../assets/common.svg)

Inom ramen för en leverans eller en kampanj **[!UICONTROL Edit the dynamic condition...]** kan du välja dirigerade adresser baserat på särskilda urvalskriterier.

I det här fallet används webbplatsen **Mitt onlinebibliotek** vill personalisera sina nyhetsbrev enligt kundernas litterära smak.

Tillsammans med inköpsavdelningen har användaren som ansvarar för leveranser skapat ett nyhetsbrev för prenumeranter som har köpt polisnoveler.

För att kunna dela slutresultatet av samarbetet med dem bestämmer leveranschefen att lägga till kollegor från inköpsavdelningen till leveransen som dirigeringsadresser. Om du använder ett dynamiskt villkor kan du spara tid när du konfigurerar och uppdaterar adresser.

Om du vill använda det dynamiska villkoret måste du ha:

* en leverans som är klar att skickas,
* dirigerade adresser som har ett gemensamt värde. Värdet kan vara ett fält som redan finns i Adobe Campaign. I det här exemplet delar dirigeringsadresserna värdet&quot;Inköp&quot; i fältet&quot;Avdelning&quot;, som inte finns i programmet som standard.

## Steg 1 - Skapa en leverans {#step-1---creating-a-delivery}

Stegen för att skapa en leverans finns i [Skapa en e-postleverans](creating-an-email-delivery.md) -avsnitt.

I det här exemplet har leveranshanteraren skapat nyhetsbrevet och valt mottagare.

![](assets/dlv_seeds_usecase_01.png)

## Steg 2 - Skapa ett gemensamt värde {#step-2---creating-a-common-value}

Om du vill skapa ett gemensamt värde som det i vårt exempel (inköpsavdelningen) måste du först utöka **dataschema** av dina dirigerade adresser och redigera det tillhörande indataformuläret.

### Utöka dataschemat {#extending-the-data-schema}

Mer information om schematillägg finns i [Konfigurationsguide](../../configuration/using/data-schemas.md).

1. I **[!UICONTROL Administration > Configuration > Data schemas]** noden, klicka på **[!UICONTROL New]** ikon.
1. I **[!UICONTROL Creation of a data schema]** väljer du **[!UICONTROL Extension of a schema]** och klicka **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Välj **[!UICONTROL Seed addresses]** källschema, ange **doc** som **[!UICONTROL Namespace]** och klicka **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Klicka på **[!UICONTROL Save]**.
1. I schemaredigeringsfönstret kopierar du raderna nedan och klistrar in dem i det område som visas på skärmbilden.

   ```
     <element name="common">
       <element label="Recipient" name="custom_nms_recipient">
         <attribute label="Department" length="80" name="workField" template="nms:recipient:recipient/@company"
                    type="string" userEnum="workField"/>
       </element>
     </element>
   ```

   ![](assets/dlv_seeds_usecase_20.png)

   Kopiera sedan följande rader och klistra in dem under **[!UICONTROL Seed to insert in the export files]** -element.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   I det här fallet anger du att en ny uppräkning med namnet **[!UICONTROL Department]** har skapats i dirigeringsadresstabellen och baseras på standarden **[!UICONTROL @company]** uppräkningsmall (märkt under namnet **Företag** i utsädesadressformuläret).

1. Klicka på **[!UICONTROL Save]**.
1. I **[!UICONTROL Tools > Advanced]** väljer du **[!UICONTROL Update database structure]** alternativ.

   ![](assets/dlv_seeds_usecase_12.png)

1. När uppdateringsguiden visas klickar du på **[!UICONTROL Next]** för att öppna fönstret Redigera tabeller: Ändringar som utförs i schemat för startadressdata kräver en strukturuppdatering.

   ![](assets/dlv_seeds_usecase_13.png)

1. Följ guiden tills du kommer till sidan för att köra uppdateringen. Klicka på knappen **[!UICONTROL Start]**.

   ![](assets/dlv_seeds_usecase_14.png)

   När uppdateringen är klar kan du stänga guiden.

1. Koppla från och återanslut sedan till Adobe Campaign. Ändringarna i schemat för startadressdata gäller nu. För att de ska kunna visas på startadressens skärm måste du uppdatera den associerade **[!UICONTROL Input form]**. Se [Uppdaterar indataformuläret](#updating-the-input-form) -avsnitt.

#### Utöka dataschemat från en länkad tabell {#extending-the-data-schema-from-a-linked-table}

Startadressernas dataschema kan använda värden från en tabell som är länkad till mottagardataschemat - mottagare (nms).

Användaren vill till exempel integrera **[!UICONTROL Internet Extension]** finns i **[!UICONTROL Country]** tabell som är länkad till mottagarschemat.

![](assets/dlv_seeds_usecase_06.png)

De måste därför utöka dataschemat för dirigerade adresser så som beskrivs i avsnittet. Men de kodrader som ska integreras på **steg 4** är följande:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

De anger

* som användaren vill skapa ett nytt element med namnet **[!UICONTROL Internet Extension]**,
* det här elementet kommer från **[!UICONTROL Country]** tabell.

>[!CAUTION]
>
>I namnet på den länkade tabellen måste du ange **xpath-dst** av den länkade tabellen.
>
>Detta finns i **[!UICONTROL Country]** -element i mottagartabellen.

![](assets/dlv_seeds_usecase_07.png)

Användaren kan sedan följa **steg 5** och uppdatera **[!UICONTROL Input form]** av utsädesadresserna.

Se [Uppdaterar indataformuläret](#updating-the-input-form) -avsnitt.

#### Uppdaterar indataformuläret {#updating-the-input-form}

1. I **[!UICONTROL Administration > Configuration > Input forms]** nod, hitta indataformuläret för dirigerade adresser.

   ![](assets/dlv_seeds_usecase_19.png)

1. Redigera formuläret och infoga följande rad i dialogrutan **[!UICONTROL Recipient]** behållare.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Spara ändringarna.
1. Öppna en startadress. The **[!UICONTROL Department]** fältet visas i **[!UICONTROL Recipient]** tabell.

   ![](assets/dlv_seeds_usecase_22.png)

1. Redigera de dirigerade adresser som du vill använda för leveransen och ange **Inköp** som värdet i **[!UICONTROL Department]** fält.

## Steg 3 - Definiera villkoret {#step-3---defining-the-condition}

Nu kan du ange det dynamiska villkoret för startadresserna för leveransen. Så här gör du:

1. Öppna en leverans.

   ![](assets/dlv_seeds_usecase_01.png)

1. Klicka på **[!UICONTROL To]** sedan länken **[!UICONTROL Seed addresses]** -fliken för att komma åt **[!UICONTROL Edit the dynamic condition...]** länk.

   ![](assets/dlv_seeds_usecase_02.png)

1. Välj det uttryck som gör att du kan välja vilka dirigerade adresser du vill använda. Här väljer användaren **[!UICONTROL Department (@workField)]** -uttryck.

   ![](assets/dlv_seeds_usecase_03.png)

1. Välj det värde du vill ha. I det här exemplet väljer användaren **Inköp** -avdelning i listrutan med värden.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >Schematillägget som skapades tidigare kommer från **mottagare** schema. Värdena som visas på skärmen ovan kommer från en uppräkning av **mottagare** schema.

1. Klicka på **[!UICONTROL Ok]**.

   Frågan visas i **[!UICONTROL Select target]** -fönstret.

   ![](assets/dlv_seeds_usecase_04.png)

1. Klicka **[!UICONTROL Ok]** för att godkänna frågan.
1. Analysera leveransen och klicka sedan på **[!UICONTROL Delivery]** för att komma åt leveransloggarna.

   Startadresserna för inköpsavdelningen visas som väntande leveranser, precis som för mottagarna eller andra startadresser.

   ![](assets/dlv_seeds_usecase_05.png)

1. Klicka på **[!UICONTROL Send]** för att starta leveransen.

   Medlemmarna på inköpsavdelningen utgör en del av de dirigerade adresser som kommer att ta emot leveransen i inkorgen.

   ![](assets/dlv_seeds_usecase_18.png)
