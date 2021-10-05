---
product: campaign
title: Filtreringsscheman
description: Filtreringsscheman
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 009bed25-cd35-437c-b789-5b58a6d2d7c6
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Filterscheman{#filtering-schemas}

![](../../assets/v7-only.svg)

## Systemfilter {#system-filters}

Du kan filtrera schemaåtkomst till specifika användare, beroende på deras behörigheter. Med systemfilter kan du hantera läs- och skrivbehörigheter för enheter som anges i scheman med hjälp av parametrarna **readAccess** och **writeAccess**.

>[!NOTE]
>
>Denna begränsning gäller endast icke-tekniska användare: en teknisk användare, med relaterade behörigheter eller med ett arbetsflöde, kan hämta och uppdatera data.

* **readAccess**: ger skrivskyddad åtkomst till schemadata.

   **Varning**  - Alla länkade tabeller måste anges med samma begränsning. Den här konfigurationen kan påverka prestanda.

* **writeAccess**: ger skrivåtkomst till schemadata.

Dessa filter anges på huvudnivån **element** för scheman och kan, som visas i följande exempel, utformas för att begränsa åtkomsten.

* Begränsa skrivbehörighet

   Här används filtret för att inte tillåta skrivbehörighet för schemat för operatorer utan administratörsbehörighet. Det innebär att bara administratörer har skrivbehörighet för entiteter som beskrivs i det här schemat.

   ```
   <sysFilter name="writeAccess">      
    <condition enabledIf="hasNamedRight('admin')=false" expr="FALSE"/>    
   </sysFilter>
   ```

* Begränsa läs- och skrivbehörigheter:

   Här används filtret för att inte tillåta både LÄS- och SKRIVbehörigheter för schemat för alla operatorer. Endast det interna **kontot**, som representeras av uttrycket &quot;$(loginId)!=0&quot;, har dessa behörigheter.

   ```
   <sysFilter name="readAccess"> 
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   
   <sysFilter name="writeAccess">  
    <condition enabledIf="$(loginId)!=0" expr="FALSE"/>
   </sysFilter>
   ```

   Möjliga **expr**-attributvärden som används för att definiera villkoret är TRUE eller FALSE.

>[!NOTE]
>
>Om inget filter anges har alla operatorer läs- och skrivbehörighet till schemat.

## Protect inbyggda scheman {#protecting-built-in-schemas}

Inbyggda scheman är som standard bara tillgängliga med SKRIV-behörighet för operatorer med ADMINISTRATIONbehörighet:

* ncm:publicera
* nl:övervakning
* nms:kalender
* xtk:builder
* xtk:anslutningar
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:formulär
* xtk:funcList
* xtk:fusion
* xtk:bild
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rättigheter
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strängar
* xtk:xslt

>[!IMPORTANT]
>
>LÄS- och SKRIVbehörigheter för schemat **xtk:sessionInfo** är bara tillgängliga för det interna kontot för en Adobe Campaign-instans.

## Ändra systemfilter för inbyggda scheman {#modifying-system-filters-of-built-in-schemas}

Du kan fortfarande ändra systemfiltren för de färdiga scheman som som standard är skyddade på grund av kompatibilitetsproblem med äldre versioner.

>[!NOTE]
>
>Adobe rekommenderar dock att du inte ändrar standardparametrarna för att garantera optimal säkerhet.

1. Skapa ett tillägg för det aktuella schemat eller öppna ett befintligt tillägg.
1. Lägg till ett underordnat element **`<sysfilter name="<filter name>" _operation="delete"/>`** i huvudelementet för att ta bort programmet för filtret under samma element i det ursprungliga schemat.
1. Om du vill kan du lägga till ett nytt filter, enligt beskrivningen i [Systemfilter](#system-filters).
