---
title: Lägga till ytterligare SQL-funktioner
seo-title: Lägga till ytterligare SQL-funktioner
description: Lägga till ytterligare SQL-funktioner
seo-description: null
page-status-flag: never-activated
uuid: d66b5ca2-ac7d-4654-9f0e-9bfe56490c19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 728a95f8-46fe-49a8-a645-a0dd6eeb6615
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# Lägga till ytterligare SQL-funktioner{#adding-additional-sql-functions}

## Introduktion {#introduction}

Med Adobe Campaign kan användaren definiera **egna funktioner** som har åtkomst till SQL-funktioner, både de som finns i databasen och de som inte redan finns i konsolen. Detta är användbart för sammanställningsfunktioner (medel, maximum, sum) som till exempel bara kan beräknas på servern eller när databasen är ett enklare sätt att implementera vissa funktioner, i stället för att skriva uttrycket i konsolen manuellt (t.ex. datumhantering).

Den här mekanismen kan också användas om du vill använda en nyligen använd eller ovanlig SQL-funktion för databasmotorn, som ännu inte finns i Adobe Campaign-konsolen.

När dessa funktioner har lagts till visas de i uttrycksredigeraren precis som andra fördefinierade funktioner.

>[!CAUTION]
>
>SQL-funktionsanrop i konsolen skickas inte längre naturligt till servern. Den mekanism som beskrivs här blir därför **det enda sättet att anropa** den oplanerade SQL-funktionsservern.

## Installation {#installation}

De funktioner som ska läggas till finns i en **&quot;paketfil&quot; i XML-format**, vars struktur beskrivs i följande stycke.

Om du vill installera det från konsolen väljer du alternativen för **Verktyg/Avancerat/Importera paket** på menyn, sedan **[!UICONTROL Install from file]** , och följer sedan instruktionerna i importguiden.

>[!CAUTION]
>
>Varning: Även om listan med importerade funktioner visas direkt i funktionsredigeraren kommer de inte att kunna användas förrän Adobe Campaign har startats om.

## Allmän struktur för paket som ska importeras {#general-structure-of-package-to-import}

De funktioner som ska läggas till finns i **&quot;paketfilen** &quot; i XML-format. Här är ett exempel:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* Namnet **,** namnutrymmet **och** etiketten **** är bara till för information. De gör att du kan visa en sammanfattning av paketet i den installerade paketlistan (Utforskaren/Administration/Pakethantering/Installerade paket).
* Fälten **buildVersion** och **buildNumber** är obligatoriska. De måste motsvara servernumret som konsolen är ansluten till. Den här informationen finns i rutan &quot;Hjälp/Om&quot;.
* Följande block, **entiteter** och **funktionslista** är obligatoriska. I funcList är fälten &quot;name&quot; och &quot;namespace&quot; obligatoriska, men användaren bestämmer själv vilket namn de ska ha och anger en unik funktionslista.

   Det innebär att om en annan lista med funktioner med samma namnutrymmes-/namnpar (här &quot;cus::myList&quot;) importeras, tas de funktioner som tidigare importerats bort. Om du ändrar namnutrymmes-/namnparet läggs den nya serien med importerade funktioner till i det föregående.

* Med **gruppelementet** kan du ange i vilken funktionsgrupp de importerade funktionerna ska visas i funktionsredigeraren. Attributet @name kan antingen vara ett namn som redan finns (i så fall läggs funktionerna till i den aktuella gruppen) eller ett nytt namn (i så fall visas de i en ny grupp).
* Påminnelse: Möjliga värden för attributet @name i `<group>` elementet är:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!CAUTION]
>
>Se till att du slutför attributet @label: det här namnet visas i listan över tillgängliga funktioner. Om du inte anger något får gruppen inget namn. Om du anger ett annat namn än det befintliga, ändras dock namnet på hela gruppen.

Om du vill lägga till funktioner i flera olika grupper kan du göra så att flera `<group>` element spåras i samma lista.

Slutligen kan ett `<group>` -element innehålla definitionen av en eller flera funktioner, det vill säga syftet med paketfilen. Elementet `<function>` beskrivs i följande stycke.

## Funktionsbeskrivning &lt;function>&lt;/function> {#function-descriptor--function-}

Det fall som presenteras här är ett allmänt fall där vi vill tillhandahålla **funktionsimplementeringen**.

Nedan visas ett exempel på en funktion för&quot;relativ mognad&quot; som, med hjälp av en ålder, anger i hur många år personen har betraktats som mogen.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Fältet **@name** refererar till funktionens namn och &quot;args&quot; är den lista med parametrar som ska visas i beskrivningen. I det här fallet visas funktionen som &quot;relativeMaturity ( `<age>` )&quot; i funktionsvalsfönstret.

* **help** är det fält som visas längst ned i uttrycksredigerarfönstret.
* **@display** är ett informativt meddelande.

   >[!NOTE]
   >
   >I attributen @help och @display representerar strängen &quot;$1&quot; namnet som angavs i den första funktionsparametern (här, &quot;Ålder&quot;). $2, $3.. skulle motsvara följande parametrar. I attributet @body som anges nedan anger $1 argumentvärdet som skickas till funktionen under anropet.

   >[!NOTE]
   >
   >Beskrivningen måste vara en sträng med giltiga XML-tecken: observera att du använder &#39;&lt;&#39; och &#39;>&#39; i stället för &lt; och >.

* **@type** är funktionens returtyp och är ett standardvärde (long, string, byte, datetime...). Om den utelämnas avgör servern den bästa typen bland de tillgängliga typerna i uttrycket som implementerar funktionen.
* **@minArgs** och **maxArgs** anger antalet parametrar (minimum och maximum) för en parameter. För en funktion med 2 parametrar blir till exempel minArgs och maxArgs 2 och 2. För 3 parametrar, plus 1 valfritt, är de 3 respektive 4.
* Slutligen innehåller elementet **providerPart** funktionsimplementeringen.

   * Attributet **provider** är obligatoriskt, det specificerar de databassystem som implementeringen tillhandahålls för. När uttryckssyntaxen eller underliggande funktioner skiljer sig åt kan alternativa implementeringar tillhandahållas enligt databasen, vilket visas i exemplet.
   * Attributet **@body** innehåller funktionsimplementeringen. Observera: implementeringen måste vara ett uttryck i databasspråket (inte ett kodblock). Beroende på databaser kan uttryck vara underfrågor (&quot;(markera kolumn från tabell där...)&quot;) som bara returnerar ett värde. Detta är till exempel fallet i Oracle (frågan måste skrivas inom hakparenteser).
   >[!NOTE]
   >
   >Om det är troligt att bara en eller två databaser efterfrågas av den definierade funktionen, kan vi alltid bara tillhandahålla de definitioner som motsvarar dessa databaser.

## Funktionsbeskrivningen &quot;Pass-through&quot; {#pass-through--function-descriptor}

En särskild funktionsbeskrivning är **&quot;pass-through&quot;** -blocket, med ett ospecificerat&quot;provider&quot;-databassystem. I det här fallet kan &quot;body&quot;-implementeringen bara innehålla ett enda funktionsanrop med en syntax som inte är beroende av den databas som används. Under tiden är &quot;ProviderPart&quot;-blocket unikt.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

Om du i det här fallet lägger till en funktion skapas bara en databasfunktion som inte skulle ha varit tillgänglig som standard, som nu är synlig för klienten.

## Exempel {#examples}

Fler funktionsexempel finns i det fördefinierade paketet &quot;xtkdatakitfuncList.xml&quot;.
