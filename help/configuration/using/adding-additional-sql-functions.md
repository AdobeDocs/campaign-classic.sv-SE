---
product: campaign
title: Lägga till ytterligare SQL-funktioner
description: Lär dig definiera ytterligare SQL-funktioner
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Definiera ytterligare SQL-funktioner{#adding-additional-sql-functions}

![](../../assets/v7-only.svg)

Adobe Campaign låter användaren definiera **sina egna funktioner** som har åtkomst till SQL-funktioner, både de som finns i databasen och de som inte redan finns i konsolen. Detta är användbart för sammanställningsfunktioner (medel, maximum, sum) som till exempel bara kan beräknas på servern eller när databasen är ett enklare sätt att implementera vissa funktioner, i stället för att skriva uttrycket i konsolen manuellt (t.ex. datumhantering).

Den här funktionen kan även användas om du vill använda en nyligen använd eller ovanlig SQL-funktion för databasmotorn som ännu inte finns i Adobe Campaign-konsolen.

När dessa funktioner har lagts till visas de i uttrycksredigeraren precis som andra fördefinierade funktioner.

>[!IMPORTANT]
>
>SQL-funktionsanrop i konsolen skickas inte längre naturligt till servern. Den mekanism som beskrivs här blir därför **det enda sättet att ringa** på den oplanerade SQL-funktionsservern.

## Installation {#installation}

De funktioner som ska läggas till finns i en **&quot;package&quot;-fil i XML-format**, vars struktur beskrivs i följande stycke.

Om du vill installera den från konsolen väljer du **Verktyg/Avancerat/Importera paket** på menyn och sedan **[!UICONTROL Install from file]** och följ instruktionerna i importguiden.

>[!IMPORTANT]
>
>Varning: Även om listan med importerade funktioner visas direkt i funktionsredigeraren kommer de inte att kunna användas förrän Adobe Campaign har startats om.

## Allmän struktur för paket som ska importeras {#general-structure-of-package-to-import}

Funktioner som ska läggas till finns i **filen &quot;package&quot;** i XML-format. Här är ett exempel:

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

* The **name**, **namespace** och **label** endast i informationssyfte. De gör att du kan visa en sammanfattning av paketet i den installerade paketlistan (Utforskaren/Administration/Pakethantering/Installerade paket).
* The **buildVersion** och **buildNumber** fält är obligatoriska. De måste motsvara servernumret som konsolen är ansluten till. Den här informationen finns i rutan &quot;Hjälp/Om&quot;.
* Följande block, **enheter** och **funktionslista** är obligatoriska. I funcList är fälten &quot;name&quot; och &quot;namespace&quot; obligatoriska, men användaren bestämmer själv vilket namn de ska ha och anger en unik funktionslista.

   Det innebär att om en annan lista med funktioner med samma namnutrymmes-/namnpar (här &quot;cus::myList&quot;) importeras, tas de funktioner som tidigare importerats bort. Om du ändrar namnutrymmes-/namnparet läggs den nya serien med importerade funktioner till i det föregående.

* The **grupp** kan du ange i vilken funktionsgrupp de importerade funktionerna ska visas i funktionsredigeraren. Attributet @name kan antingen vara ett namn som redan finns (i så fall läggs funktionerna till i den aktuella gruppen) eller ett nytt namn (i så fall visas de i en ny grupp).
* Påminnelse: möjliga värden för attributet @name i `<group>` -elementet är:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>Se till att du slutför attributet @label: det här namnet visas i listan över tillgängliga funktioner. Om du inte anger något får gruppen inget namn. Om du anger ett annat namn än det befintliga, ändras dock namnet på hela gruppen.

Om du vill lägga till funktioner i flera olika grupper kan du skapa flera `<group>`  elementen spåras i samma lista.

Äntligen en `<group>` -elementet kan innehålla definitionen för en eller flera funktioner, det vill säga syftet med paketfilen. The  `<function>`   -elementet beskrivs i följande stycke.

## Funktionsbeskrivning &lt;function>&lt;/function> {#function-descriptor--function-}

Det fall som presenteras här är ett allmänt fall där vi vill lämna in **funktionsimplementering**.

Nedan visas ett exempel på en funktion för&quot;relativ mognad&quot; som, med hjälp av en ålder, anger i hur många år personen har betraktats som mogen.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

The **@name** fältet refererar till funktionens namn och &quot;args&quot; är den lista med parametrar som ska visas i beskrivningen. I det här fallet visas funktionen som &quot;relativeMaturity&quot; ( `<age>` )&quot; i funktionsvalsfönstret.

* **help** är det fält som visas längst ned i uttrycksredigeringsfönstret.
* **@display** är ett informativt meddelande.

   >[!NOTE]
   >
   >I attributen @help och @display representerar strängen &quot;$1&quot; namnet som angavs i den första funktionsparametern (här, &quot;Ålder&quot;). $2, $3.. skulle motsvara följande parametrar. I attributet @body som anges nedan anger $1 argumentvärdet som skickas till funktionen under anropet.

   >[!NOTE]
   >
   >Beskrivningen måste vara en sträng med giltiga XML-tecken: observera att du använder &#39;&lt;&#39; och &#39;>&#39; i stället för &lt; och >.

* **@type** är funktionens returtyp och är ett standardvärde (long, string, byte, datetime..). Om den utelämnas avgör servern den bästa typen bland de tillgängliga typerna i uttrycket som implementerar funktionen.
* **@minArgs** och **maxArgs** anger antalet parametrar (minimum och maximum) för en parameter. För en funktion med 2 parametrar blir till exempel minArgs och maxArgs 2 och 2. För 3 parametrar, plus 1 valfritt, är de 3 respektive 4.
* Slutligen **providerPart** -element innehåller funktionsimplementeringen.

   * The **provider** är obligatoriskt, anger det databassystem som implementeringen är avsedd för. När uttryckssyntaxen eller underliggande funktioner skiljer sig åt kan alternativa implementeringar tillhandahållas enligt databasen, vilket visas i exemplet.
   * The **@body** -attributet innehåller funktionsimplementeringen. Observera: implementeringen måste vara ett uttryck i databasspråket (inte ett kodblock). Beroende på databaser kan uttryck vara underfrågor (&quot;(markera kolumn från tabell där...)&quot;) som bara returnerar ett värde. Detta är till exempel fallet i Oraclet (frågan måste skrivas inom hakparenteser).

   >[!NOTE]
   >
   >Om det är troligt att bara en eller två databaser efterfrågas av den definierade funktionen, kan vi alltid bara tillhandahålla de definitioner som motsvarar dessa databaser.

## Funktionsbeskrivningen &quot;Pass-through&quot; {#pass-through--function-descriptor}

En särskild funktionsbeskrivning är **&quot;pass-through&quot;** -block, med ett ospecificerat &quot;provider&quot;-databassystem. I det här fallet kan &quot;body&quot;-implementeringen bara innehålla ett enda funktionsanrop med en syntax som inte är beroende av den databas som används. Under tiden är &quot;ProviderPart&quot;-blocket unikt.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

Om du i det här fallet lägger till en funktion skapas bara en databasfunktion som inte skulle ha varit tillgänglig som standard, som nu är synlig för klienten.

## Exempel {#examples}

Fler funktionsexempel finns i det fördefinierade paketet &quot;xtkdatakitfuncList.xml&quot;.
