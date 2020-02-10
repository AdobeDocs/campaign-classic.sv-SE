---
title: '"Användningsfall: välja startadresser på villkor"'
seo-title: '"Användningsfall: välja startadresser på villkor"'
description: '"Användningsfall: välja startadresser på villkor"'
seo-description: null
page-status-flag: never-activated
uuid: 6af39893-6ef3-4204-8b53-0c16e35bac8f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: using-seed-addresses
discoiquuid: fa8aab62-e182-4388-aa23-c255b0dbd42e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Användningsfall: välja startadresser enligt villkor{#use-case-selecting-seed-addresses-on-criteria}

I samband med en leverans eller en kampanj kan du med hjälp av länken välja dirigerade adresser baserat på specifika urvalskriterier. **[!UICONTROL Edit the dynamic condition...]**

I det här fallet vill webbplatsen **Mitt onlinebibliotek** anpassa sina nyhetsbrev efter kundernas litterära smak.

Tillsammans med inköpsavdelningen har användaren som ansvarar för leveranser skapat ett nyhetsbrev för prenumeranter som har köpt polisnoveler.

Leveranschefen bestämmer sig för att lägga till sina kollegor från inköpsavdelningen till leveransen som dirigeringsadresser för att dela slutresultatet av samarbetet med dem. Om du använder ett dynamiskt villkor kan du spara tid när du konfigurerar och uppdaterar adresser.

Om du vill använda det dynamiska villkoret måste du ha:

* en leverans som är klar att skickas,
* dirigerade adresser som har ett gemensamt värde. Värdet kan vara ett fält som redan finns i Adobe Campaign. I det här exemplet delar dirigeringsadresserna värdet&quot;Inköp&quot; i fältet&quot;Avdelning&quot;, som inte finns i programmet som standard.

## Steg 1 - Skapa en leverans {#step-1---creating-a-delivery}

Hur du skapar en leverans beskrivs i avsnittet [Skapa en e-postleverans](../../delivery/using/creating-an-email-delivery.md) .

I det här exemplet har leveranshanteraren skapat nyhetsbrevet och valt mottagare.

![](assets/dlv_seeds_usecase_01.png)

## Steg 2 - Skapa ett gemensamt värde {#step-2---creating-a-common-value}

Om du vill skapa ett gemensamt värde som det i vårt exempel (Inköpsavdelning) måste du först utöka **dataschemat** för dina dirigerade adresser och redigera det tillhörande indataformuläret.

### Utöka dataschemat {#extending-the-data-schema}

Mer information om schematillägg finns i [konfigurationsguiden](../../configuration/using/data-schemas.md).

1. Klicka på **[!UICONTROL Administration > Configuration > Data schemas]** ikonen i **[!UICONTROL New]** noden.
1. I **[!UICONTROL Creation of a data schema]** fönstret markerar du **[!UICONTROL Extension of a schema]** alternativet och klickar på **[!UICONTROL Next]**.

   ![](assets/dlv_seeds_usecase_09.png)

1. Välj **[!UICONTROL Seed addresses]** källschemat, ange **doc** som **[!UICONTROL Namespace]** och klicka på **[!UICONTROL Ok]**.

   ![](assets/dlv_seeds_usecase_10.png)

1. Klicka **[!UICONTROL Save]**.
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

   Kopiera sedan följande rader och klistra in dem under **[!UICONTROL Seed to insert in the export files]** elementet.

   ```
       <element aggregate="doc:seedMember:common">
     </element>
   ```

   ![](assets/dlv_seeds_usecase_29.png)

   I det här fallet anger du att en ny uppräkning med namnet **[!UICONTROL Department]** har skapats i dirigerad adresstabellen, och den är baserad på **[!UICONTROL @company]** standarduppräkningsmallen (med namnet **Company** i dirigerad adressform).

1. Klicka **[!UICONTROL Save]**.
1. Välj **[!UICONTROL Tools > Advanced]** alternativet på **[!UICONTROL Update database structure]** menyn.

   ![](assets/dlv_seeds_usecase_12.png)

1. När uppdateringsguiden visas klickar du på **[!UICONTROL Next]** knappen för att öppna fönstret Redigera tabeller: Ändringar som utförs i schemat för startadressdata kräver en strukturuppdatering.

   ![](assets/dlv_seeds_usecase_13.png)

1. Följ guiden tills du kommer till sidan för att köra uppdateringen. Klicka på **[!UICONTROL Start]** knappen.

   ![](assets/dlv_seeds_usecase_14.png)

   När uppdateringen är klar kan du stänga guiden.

1. Koppla från och återanslut sedan till Adobe Campaign. Ändringarna i schemat för startadressdata gäller nu. För att de ska kunna visas från startadressens skärm måste du uppdatera den associerade adressen **[!UICONTROL Input form]**. Mer information finns i avsnittet [Uppdatera indataformulär](#updating-the-input-form) .

#### Utöka dataschemat från en länkad tabell {#extending-the-data-schema-from-a-linked-table}

Startadressernas dataschema kan använda värden från en tabell som är länkad till mottagardataschemat - mottagare (nms).

Användaren vill till exempel integrera den **[!UICONTROL Internet Extension]** som finns i den **[!UICONTROL Country]** tabell som är länkad till mottagarschemat.

![](assets/dlv_seeds_usecase_06.png)

De måste därför utöka dataschemat för dirigerade adresser så som beskrivs i avsnittet. De kodrader som ska integreras i **steg 4** är dock följande:

```
<element name="country">
      <attribute label="Internet Extension" length="2" name="iana" type="string"/>
      <attribute label="Country ISO" length="2" name="countryIsoA2" type="string"/>
    </element>
```

![](assets/dlv_seeds_usecase_11.png)

De anger

* som användaren vill skapa ett nytt element med namnet **[!UICONTROL Internet Extension]**,
* att det här elementet kommer från **[!UICONTROL Country]** tabellen.

>[!CAUTION]
>
>I den länkade tabellens namn måste du ange den länkade tabellens **xpath-dst** .
>
>Detta finns i elementet **[!UICONTROL Country]** i mottagartabellen.

![](assets/dlv_seeds_usecase_07.png)

Användaren kan sedan följa **steg 5** i avsnittet och uppdatera **[!UICONTROL Input form]** startadresserna.

Mer information finns i avsnittet [Uppdatera indataformulär](#updating-the-input-form) .

#### Uppdaterar indataformuläret {#updating-the-input-form}

1. Leta reda på indataformuläret för dirigerade adresser i **[!UICONTROL Administration > Configuration > Input forms]** noden.

   ![](assets/dlv_seeds_usecase_19.png)

1. Redigera formuläret och infoga följande rad i **[!UICONTROL Recipient]** behållaren.

   ```
   <input xpath="@workField"/>
   ```

   ![](assets/dlv_seeds_usecase_21.png)

1. Spara ändringarna.
1. Öppna en startadress. Fältet **[!UICONTROL Department]** visas i **[!UICONTROL Recipient]** tabellen.

   ![](assets/dlv_seeds_usecase_22.png)

1. Redigera de dirigerade adresser som du vill använda för leveransen och ange **Inköp** som värde i **[!UICONTROL Department]** fältet.

## Steg 3 - Definiera villkoret {#step-3---defining-the-condition}

Nu kan du ange det dynamiska villkoret för startadresserna för leveransen. Så här gör du:

1. Öppna en leverans.

   ![](assets/dlv_seeds_usecase_01.png)

1. Klicka på **[!UICONTROL To]** länken och sedan på **[!UICONTROL Seed addresses]** fliken för att öppna **[!UICONTROL Edit the dynamic condition...]** länken.

   ![](assets/dlv_seeds_usecase_02.png)

1. Välj det uttryck som gör att du kan välja vilka dirigerade adresser du vill använda. Här väljer användaren **[!UICONTROL Department (@workField)]** uttrycket.

   ![](assets/dlv_seeds_usecase_03.png)

1. Välj det värde du vill ha. I det här exemplet väljer användaren **Inköpsavdelning** i den nedrullningsbara listan med värden.

   ![](assets/dlv_seeds_usecase_17.png)

   >[!NOTE]
   >
   >Schematillägget som skapades tidigare kommer från **mottagarschemat** . Värdena som visas på skärmen ovan kommer från en uppräkning av **mottagarschemat** .

1. Klicka **[!UICONTROL Ok]**.

   Frågan visas i **[!UICONTROL Select target]** fönstret.

   ![](assets/dlv_seeds_usecase_04.png)

1. Klicka **[!UICONTROL Ok]** för att godkänna frågan.
1. Analysera leveransen och klicka sedan på **[!UICONTROL Delivery]** fliken för att komma åt leveransloggarna.

   Startadresserna för inköpsavdelningen visas som väntande leveranser, precis som för mottagarna eller andra startadresser.

   ![](assets/dlv_seeds_usecase_05.png)

1. Klicka på **[!UICONTROL Send]** knappen för att starta leveransen.

   Medlemmarna på inköpsavdelningen utgör en del av de dirigerade adresser som kommer att ta emot leveransen i inkorgen.

   ![](assets/dlv_seeds_usecase_18.png)
