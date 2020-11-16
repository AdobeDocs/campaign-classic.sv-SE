---
title: Leveransnyckelpoäng
description: viktiga punkter att kontrollera för att förbättra leveransen
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
translation-type: tm+mt
source-git-commit: cb2fb5a338220c54aba96b510a7371e520c2189e
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 2%

---


# Leveransnyckelpoäng{#deliverability-key-points}

För att optimera leveransen av dina e-postmeddelanden från Adobe Campaign rekommenderar vi att du använder de bästa metoderna nedan. Leveransproblem är i allmänhet kopplade till skyddsåtgärder mot skräppost som implementeras av Internet-leverantörer och e-postserveradministratörer.

**E-postleveransen** avser den uppsättning egenskaper som avgör om ett meddelande kan nå sin destination, via en personlig e-postadress, inom en kort tid och med den förväntade kvaliteten i fråga om innehåll och format.

Dessa egenskaper kan delas in i fyra huvudkategorier:
* Datakvalitet
* Meddelande och innehåll
* Skicka infrastruktur
* Anseende

Tillsammans utgör de grunden för ett framgångsrikt program för e-postleverans.

Leveransfrekvensen **** är antalet skickade e-postmeddelanden som levererats till mottagarna.

Leveransgraden beror på flera faktorer, särskilt:
* Korrekt konfiguration av dina instanser
* Din IP-adress är känd
* Kvaliteten på adresserna
* Låga klagomål och hög studsfrekvens
* Ditt meddelandeinnehåll
* Meddelandeautentisering (SPF, DKIM, DMARC)
* Avsändarens rykte

Nedan finns en lista över de viktigaste punkterna som ska kontrolleras för att säkerställa god leveransförmåga.

## Kontrollera nätverkskonfiguration {#network-configuration}

Spam försöker dölja sin riktiga identitet och gör därför sina servrar svåra att identifiera. En giltig nätverkskonfiguration som inte försöker dölja serverns identitet är nödvändig för att skicka e-post i stora volymer.

## Skicka till giltiga adresser {#valid-addresses}

Spammare använder ofta adressgeneratorer som bygger på listor över frekventa namn och förnamn. Dessutom bearbetar de sällan tekniska meddelanden som skickas tillbaka från e-postservrar. En hög frekvens med ogiltiga adresser tolkas ofta som ett tecken på skräppost. Dubbla anmälningsmekanismer och effektiv hantering av tekniska studentmeddelanden gör det möjligt att undvika detta.

## Minska antalet klagomål och avhoppsfrekvens {#reduce-complaint-rates}

Internetleverantörer har vanligtvis ett framträdande sätt att rapportera ett mottaget meddelande som skräppost. Detta gör det möjligt att identifiera otillförlitliga källor. Genom att snabbt följa avanmälningsbegäranden, använda en viss lista regelbundet, verifiera samtycke via ett system med dubbel avanmälan och implementera feedbackslingor kan ni minska antalet klagomål.

## Skicka till anteckningsadresser {#honeypot-addresses}

Internetleverantörer och andra organisationer (se webbplatsen [Project Honung Pot](https://www.projecthoneypot.org/) ) använder postlådor som inte motsvarar fysiska personer, men som bara skapas för att lura skräppost. Dessa så kallade &quot;honungsportadresser&quot; publiceras på webben för att samlas in av skräppost och därmed fånga oäkta avsändare. Användningen av en dubbel anmälningsmekanism förhindrar att den här typen av adress läggs till i en lista. När du använder en tredjepartslista måste du vara säker på vilka metoder som används av den som ansvarar för den.

## Anpassa meddelandeinnehållet {#message-content}

I mindre utsträckning kan innehållet i vissa meddelanden leda till att vissa filter identifierar det som skräppost. Användningen av vissa ord, användningen av utropstecken i ämnesraden och i meddelandena, läses som kontrollerbara tecken på skräppost. Det är också känt att skräppost ersätter text med bilder för att förhindra att felaktig text analyseras automatiskt av skräppostfilter. Som svar på detta kan ett meddelande (i HTML-format) med en hög andel bilder, eller bilder som bilagor, blockeras.

## Arbeta med ditt rykte {#reputation}

Spammar gör planerade leveranser för att bevara sitt rykte över tiden. Ibland måste de anpassa sin marknadsföringsplan så att den uppfyller de bästa metoderna som internetleverantörerna har infört, så att de konfigurerar regelbundna leveranser efter ett rykte som når ända upp.

## God praxis {#best-practices}

Lär dig de bästa sätten att leverera med Adobe Campaign. Använd länkarna nedan för att navigera bland ämnen och hitta vägledning.

<table>
<tr>
  <td>
    <a href="starting-new-platform.md">
      <img alt="Starta" src="assets/do-not-localize/start.svg" width="60px"/>
    </a>
    <div>
      <a href="starting-new-platform.md">
    <strong>Starta</strong>
    </a>
    </div>
    <p>
    <em>Starta en ny plattform</em>
    <p>
  </td>
   <td>
    <a href="control-message-content.md">
      <img alt="Design" src="assets/do-not-localize/design.svg" width="60px"/>
    </a>
    <div>
      <a href="control-message-content.md">
    <strong>Design</strong>
    </a>
    </div>
    <p>
    <em>Kontrollera meddelandeinnehåll</em>
    <p>
  </td>
  <td>
    <a href="improve-reputation.md">
      <img alt="Design" src="assets/do-not-localize/check.svg" width="60px"/>
    </a>
    <div>
      <a href="improve-reputation.md">
    <strong>Skicka</strong>
    </a>
    </div>
    <p>
    <em>Förbättra ryktet</em>
    <p>
  </td>
</tr>
<tr>
  <td>
    <a href="technical-recommendations.md">
      <img alt="Optimera" src="assets/do-not-localize/optimize.svg" width="60px"/>
    </a>
    <div>
      <a href="technical-recommendations.md">
    <strong>Optimera</strong>
    </a>
    </div>
    <p>
    <em>Tekniska rekommendationer</em>
    <p>
  </td>
   <td>
    <a href="monitoring-deliverability.md">
      <img alt="Markera" src="assets/do-not-localize/monitor.svg" width="60px"/>
    </a>
    <div>
      <a href="monitoring-deliverability.md">
    <strong>Bildskärm</strong>
    </a>
    </div>
    <p>
    <em>Övervakningsverktyg</em>
    <p>
  </td>
  <td>
    <a href="deliverability-faq.md">
      <img alt="Optimera" src="assets/do-not-localize/troubleshoot.svg" width="60px"/>
    </a>
    <div>
      <a href="deliverability-faq.md">
    <strong>Felsökning</strong>
    </a>
    </div>
    <p>
    <em>Lös problem</em>
    <p>
  </td>
</tr>
</table>
