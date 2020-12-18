---
solution: Campaign Classic
product: campaign
title: Prestanda- och genomströmningsproblem
description: Prestanda- och genomströmningsproblem
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 3%

---


# Prestanda- och genomströmningsproblem{#performance-and-throughput-issues}

>[!NOTE]
>
>Först och främst bör du kontrollera att du har den senaste versionen installerad. Detta garanterar att du har de senaste funktionerna och felkorrigeringarna. Mer information om innehållet i respektive release finns i [versionsinformationen](../../rn/using/latest-release.md).

## Maskinvara och infrastruktur {#hardware-and-infrastructure}

Allmänna riktlinjer för maskinvarukrav för lokal Campaign Classic finns i den här [artikeln](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html).

Konsultteamet kan ge värdkunder ett verktyg som gör att du enkelt kan se hur mycket utrymme som används av olika typer av tabeller i databasen samt hur mycket utrymme som används på SFTP-webbplatsen. Dessutom innehåller det verktyg som du kan använda för att rensa bort onödiga data. Kontakta konsult- eller supportteamen om du behöver det här verktyget. Här är några viktiga saker du bör kontrollera med det här verktyget:

* Om indexstorleken är större än tabellstorleken krävs ett vakuum.
* Kontrollera de tabeller som har den maximala blotten. Om dessa tabeller används ofta måste de semitueras.
* Databasblockering kan göra att e-postmeddelanden inte skickas.

Adobe Campaign har också ett [verktyg](../../production/using/monitoring-processes.md#manual-monitoring) för att kontrollera processor- och RAM-användning. Använd det här verktyget och se specifika indikatorer som: **Minne**, **Växla minne**, **disk**, **Aktiva processer**. Om värdena är för höga kan du försöka minska antalet arbetsflöden eller schemalägga arbetsflöden att starta vid olika tidpunkter.

## Databasprestanda {#database-performances}

För det mesta är prestandaproblem kopplade till databasunderhåll. Här är de viktigaste objekten att kontrollera:

* Konfiguration: vi rekommenderar att du kontrollerar den ursprungliga Adobe Campaign-plattformskonfigurationen och kör en fullständig maskinvarukontroll.
* Installation och konfigurering av Adobe Campaign-plattformen: kontrollera nätverkskonfigurationen och alternativen för plattformsleverans.
* Databasunderhåll: Se till att databasrensningsaktiviteten är i drift och att databasunderhållet är korrekt schemalagt och körs. Kontrollera antal och storlek på arbetsregister.
* Realtidsdiagnos: kontrollera process- och plattformsloggfilerna och övervaka sedan databasaktiviteten medan problemet återskapas.

>[!NOTE]
>
>Mer information finns i följande avsnitt: [Databasprestanda](../../production/using/database-performances.md).

## Programkonfiguration {#application-configuration}

Här är en lista över artiklar som rör bästa praxis för programkonfiguration:

* MTA och MTAChild-processer och minne: modulen **mta** distribuerar meddelanden till sina underordnade **mtachild**-moduler. Varje **dator** förbereder meddelanden innan en auktorisering begärs från statistikservern och skickar dem. Mer information finns på den här [sidan](../../installation/using/email-deliverability.md).
* TLS-konfiguration: Du bör inte aktivera TLS globalt eftersom det kan minska genomströmningen. I stället bör TLS-inställningar per domän, som hanteras av leveransteamet, justeras efter behov. Mer information finns på den här [sidan](../../installation/using/email-deliverability.md#mx-configuration).
* DKIM: 1024b är den rekommenderade krypteringsstorleken enligt Best Practices för att säkerställa att DKIM:s säkerhetsnivå är. Lägre DKIM-nycklar anses inte giltiga av de flesta åtkomstleverantörer. Se denna [sida](../../delivery/using/technical-recommendations.md#dkim) och denna [Tech](https://helpx.adobe.com/se/campaign/kb/domain-name-delegation.html).

## Leveransproblem {#deliverability-issues}

Här är en lista över bästa praxis och artiklar som rör slutbarhet:

* IP-anseende: Om IP-anseendet inte är tillräckligt bra kommer resultatet att påverkas. Modulen **Leveransövervakning** erbjuder olika verktyg för att spåra plattformens leveransprestanda. Se den här [sidan](../../delivery/using/monitoring-deliverability.md).
* IP-uppvärmning: IP-uppvärmningen utförs av leveransteamet. Detta innebär att antalet e-postmeddelanden som skickas via nya IP-adresser gradvis ökar under några veckor.
* Inställningar för IP-tillhörighet: en felaktig inställning av IP-tillhörighet kan stoppa e-postmeddelanden helt (felaktigt operatörs-/tillhörighetsnamn i konfigurationen) eller minska flödet (ett litet antal IP-adresser i tillhörigheten). Se den här [sidan](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-poststorlek: e-poststorleken spelar en viktig roll när det gäller genomströmning. Den rekommenderade maximala e-poststorleken är 60 kB. Se den här [sidan](https://helpx.adobe.com/legal/product-descriptions/campaign.html). I rapporten [Leveransdataflöde](../../reporting/using/global-reports.md#delivery-throughput) kontrollerar du antalet byte som har överförts per timme.
* Stort antal ogiltiga mottagare: om det finns ett stort antal ogiltiga mottagare kan det påverka dataflödet. MTA fortsätter att försöka skicka e-post till ogiltiga mottagare. Se till att din databas underhålls väl.
* Mängd personalisering: Om en leverans fortsätter att vara&quot;personalisering pågår&quot;, kontrollerar du det JavaScript som används i personaliseringsblock.

>[!NOTE]
>
>Se även avsnittet [Leveransnyckelpunkter](../../delivery/using/deliverability-key-points.md).

