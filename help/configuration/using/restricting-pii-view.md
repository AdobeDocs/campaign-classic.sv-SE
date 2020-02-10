---
title: Begränsa PII-vyn
seo-title: Begränsa PII-vyn
description: Begränsa PII-vyn
seo-description: null
page-status-flag: never-activated
uuid: 4dddc7f5-dac3-47b3-b3cb-92b47eb595fa
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 550439c1-978c-414e-be5b-a9e1a202c4cd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Begränsa PII-vyn{#restricting-pii-view}

## Översikt {#overview}

Vissa kunder behöver marknadsföringsanvändare för att få tillgång till dataposter, men vill inte att de ska kunna se PII (Personally Identiitable Information), till exempel förnamn, efternamn eller e-postadress. Adobe Campaign föreslår ett sätt att skydda integriteten och förhindra att data missbrukas av vanliga kampanjoperatörer.

## Implementering {#implementation}

Ett nytt attribut som kan tillämpas på ett element eller attribut har lagts till i scheman, det kompletterar det befintliga attributet **[!UICONTROL visibleIf]** . Attributet är: **[!UICONTROL accessibleIf]** . När det innehåller ett XTK-uttryck som är relaterat till den aktuella användarkontexten kan det återanvändas **[!UICONTROL HasNamedRight]** eller till **[!UICONTROL $(login)]** exempel .

Du kan hitta ett exempel på ett mottagarschematillägg som visar den här användningen nedan:

```
<srcSchema desc="Recipient table (profiles" entitySchema="xtk:srcSchema" extendedSchema="nms:recipient"
           img="nms:recipient.png" label="Recipients" labelSingular="Recipient"
           name="recipient" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Recipient table (profiles" img="nms:recipient.png" label="Recipients"
           labelSingular="Recipient" name="recipient">
    <attribute name="firstName" accessibleIf="$(login)=='admin'"/>
    <attribute name="lastName" visibleIf="$(login)=='admin'"/>
    <attribute name="email" accessibleIf="$(login)=='admin'"/>
  </element>
</srcSchema>
```

Huvudegenskaperna är:

* **[!UICONTROL visibleIf]** : Döljer fälten från metadata, vilket innebär att de inte kan nås i en schemavy, kolumnmarkering eller ett uttrycksbyggare. Men detta döljer inga data. Om fältnamnet anges manuellt i ett uttryck visas värdet.
* **[!UICONTROL accessibleIf]** : Döljer data (ersätter dem med tomma värden) från den resulterande frågan. Om visibleIf är tomt får det samma uttryck som **[!UICONTROL accessibleIf]** .

Här följer konsekvenserna av att använda det här attributet i Campaign:

* Data visas inte med den generiska frågeredigeraren i konsolen,
* Data visas inte i översiktslistorna eller i postlistan (konsolen).
* Data blir skrivskyddade i detaljerad vy.
* Data kan bara användas i filter (vilket innebär att du fortfarande kan gissa värden om du använder vissa dikotomstrategier).
* Alla uttryck som byggs med ett begränsat fält blir begränsade till: lower(@email) blir lika tillgängligt som @email.
* I ett arbetsflöde kan du lägga till den begränsade kolumnen i målpopulationen som en extra kolumn i övergången, men den är fortfarande inte tillgänglig för Adobe Campaign-användare.
* När målpopulationen lagras i en grupp (lista) är de lagrade fälten desamma som datakällan.
* Data är inte tillgängliga för JS-kod som standard.

## Rekommendationer {#recommendations}

I varje leverans kopieras e-postadresser till **[!UICONTROL broadLog]** och till **[!UICONTROL forecastLog]** tabellerna: Därför måste även dessa fält skyddas.

Nedan visas ett exempel på ett loggtabellstillägg som implementerar detta:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:broadLogRcp" img="nms:broadLog.png"
           label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log"
           name="broadLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema desc="Delivery messages being prepared." entitySchema="xtk:srcSchema"
           extendedSchema="nms:tmpBroadcast" img="" label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast" namespace="sec" xtkschema="xtk:srcSchema">
  <element desc="Delivery messages being prepared." label="Messages being prepared"
           labelSingular="Message" name="tmpBroadcast">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:excludeLogRcp" img="nms:excludeLog.png"
           label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp" namespace="sec" xtkschema="xtk:srcSchema">
  <element img="nms:excludeLog.png" label="Recipient exclusion logs" labelSingular="Recipient exclusion log"
           name="excludeLogRcp">
    <attribute accessibleIf="$(login)=='admin'" name="address"/>
  </element>
</srcSchema>
```

>[!NOTE]
>
>Denna begränsning gäller icke-tekniska användare: en teknisk användare med tillhörande behörigheter kan hämta data. Denna metod är därför inte helt säker.

