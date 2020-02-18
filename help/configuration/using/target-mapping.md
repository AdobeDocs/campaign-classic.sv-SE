---
title: Målmappning
seo-title: Målmappning
description: Målmappning
seo-description: null
page-status-flag: never-activated
uuid: a7dad8eb-c191-4f10-b7d8-63e0699603b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ff7e6f72-7605-41ee-b25a-1e4618e674d7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Målmappning{#target-mapping}

Målmappning måste skapas i två fall:

* om du använder en annan mottagartabell än den som finns i Adobe Campaign,
* om du konfigurerar en filtreringsdimension som skiljer sig från standardmåldimensionen på målmappningsskärmen.

Guiden för att skapa målmappning hjälper dig att skapa alla scheman som behövs för att du ska kunna använda din anpassade tabell.

## Skapa och konfigurera scheman som är länkade till den anpassade tabellen {#creating-and-configuring-schemas-linked-to-the-custom-table}

Innan du skapar en målmappning krävs flera konfigurationer för att Adobe Campaign ska fungera med ett nytt mottagardataschema.

Gör så här:

1. Skapa ett nytt dataschema som integrerar fälten i den anpassade tabell som du vill använda.

   Mer information finns i [Schemareferens (xtk:srcSchema)](../../configuration/using/about-schema-reference.md).

   I vårt exempel kommer vi att skapa ett kundschema, en mycket enkel tabell som innehåller följande fält: ID, förnamn, efternamn, e-postadress, mobiltelefonnummer. Syftet är att kunna skicka e-post- eller SMS-aviseringar till de personer som lagras i tabellen.

   Exempelschema (cus:individual)

   ```
   <srcSchema name="individual" namespace="cus" label="Individuals">
     <element name="individual">
       <key name="id" internal="true">
         <keyfield xpath="@id"/>
       </key>
       <attribute name="id" type="long" length="32"/>
       <attribute name="lastName" type="string" length="100"/>
       <attribute name="firstName" type="string" length="100"/>
       <attribute name="email" type="string" length="100"/>
       <attribute name="mobile" type="string" length="100"/>
     </element>
   </srcSchema>
   ```

1. Deklarera schemat som en extern vy med attributet =&quot;true&quot;. Se [visningsattributet](../../configuration/using/schema-characteristics.md#the-view-attribute).

   ```
    <srcSchema desc="External recipient table" namespace="cus" view="true"....>
      ...
    </srcSchema>
   ```

1. Om du behöver lägga till en adress för direktreklam använder du följande typ av struktur:

   ```
   <element advanced="true" name="postalAddress" template="nms:common:postalAddress">
        <attribute expr="SubString(JuxtWords(Smart([../infos/@firstname]), Upper([../infos/@name])), 1, 80)"
                   name="line1"/>
        <attribute expr="Upper([../address/@line2])" name="line2"/>
        <attribute expr="Upper([../address/@line])" name="line3"/>
        <attribute expr="Upper([../address/@line])" name="line4"/>
        <attribute expr="Upper([../address/@line])" name="line5"/>
        <attribute expr="Upper([../address/@line])" name="line6"/>
        <attribute _operation="delete" name="line7"/>
        <attribute _operation="delete" name="addrErrorCount"/>
        <attribute _operation="delete" name="addrQuality"/>
        <attribute _operation="delete" name="addrLastCheck"/>
        <element expr="@line1+'n'+@line2+'n'+@line3+'n'+@line4+'n'+@line5+'n'+@line6"
                 name="serialized"/>
        <attribute expr="AllNonNull2([../address/@line], [../infos/@name])" name="addrDefined"/>
      </element>
   ```

1. Klicka på **[!UICONTROL Administration > Campaign management > Target mappings]** noden.
1. Klicka på knappen **Nytt** för att öppna guiden för att skapa målmappning.
1. Ange fältet **Etikett** och välj det schema som du just har skapat i fältet **Måldimension** .

   ![](assets/mapping_diffusion_wizard_1.png)

1. I fönstret **Redigera adressformulär** väljer du de fält i schemat som matchar de olika leveransadresserna. Här kan vi mappa fälten **@email** och **@mobile** .

   ![](assets/mapping_diffusion_wizard_2.png)

1. I följande **lagringsfönster** anger du **suffixet i fältet för tilläggsscheman** för att skilja de nya scheman från de färdiga scheman som tillhandahålls av Adobe Campaign.

   Klicka **[!UICONTROL Define new additional fields]** för att välja den dimension som du vill använda i leveransen.

   Som standard lagras undantagshantering i samma tabeller som meddelanden. Markera rutan **Generera ett lagringsschema för spårning** om du vill konfigurera lagring för spårning som är länkad till målmappningen.

   ![](assets/mapping_diffusion_wizard_3.png)

   >[!IMPORTANT]
   >
   >Adobe Campaign har inte stöd för flera mottagarscheman, som kallas målinriktningsscheman, som är länkade till samma sändnings- och/eller spårningsloggscheman. Detta kan i annat fall leda till avvikelser i dataavstämningen efteråt. Mer information finns på sidan [Rekommendationer och begränsningar](../../configuration/using/about-custom-recipient-table.md) .

1. I fönstret **Tillägg** väljer du de valfria scheman som du vill generera (listan med tillgängliga scheman beror på vilka moduler som är installerade på Adobe Campaign-plattformen).

   ![](assets/mapping_diffusion_wizard_4.png)

1. Klicka på knappen **Spara** för att stänga guiden.

   Guiden använder startschemat för att skapa alla andra scheman som behövs för att den nya målmappningen ska fungera.

   ![](assets/mapping_schema_list.png)

## Använda målmappning {#using-target-mapping}

Det finns två sätt att använda det nya schemat som mål för en leverans:

* Skapa en eller flera leveransmallar baserade på mappning
* Välj mappning direkt när du väljer mål när du skapar en leverans, vilket visas nedan:

![](assets/mapping_selection_ciblage.png)

**Relaterat ämne**

* [Svara snabbt på kundförfrågningar för att få tillgång till deras data](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Quicklyrespondtocustomerrequeststoaccesstheirdata)