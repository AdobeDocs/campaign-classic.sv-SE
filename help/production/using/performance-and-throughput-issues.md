---
product: campaign
title: Prestanda- och dataflödesproblem
description: Prestanda- och dataflödesproblem
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-on-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: fe69efda-a052-4f67-9c13-665f011d0a2b
source-git-commit: 0429c3608fbcec98a397cc17fd45cd173cf64b6e
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 4%

---

# Prestanda- och dataflödesproblem{#performance-and-throughput-issues}



Först och främst bör du kontrollera att du har den senaste versionen installerad. Detta garanterar att du har de senaste funktionerna och felkorrigeringarna.

Se [Versionsinformation](../../rn/using/latest-release.md) för mer information om innehållet i varje release.

## Maskinvara och infrastruktur {#hardware-and-infrastructure}

Allmänna riktlinjer för maskinvarukrav för Campaign Classic på plats finns i detta avsnitt [page](https://helpx.adobe.com/se/campaign/kb/hardware-sizing-guide.html).

Konsultteamet kan ge värdkunder ett verktyg som gör att du enkelt kan se hur mycket utrymme som används av olika typer av tabeller i databasen samt hur mycket utrymme som används på SFTP-webbplatsen. Dessutom innehåller det verktyg som du kan använda för att rensa bort onödiga data. Kontakt [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du behöver det här verktyget implementerat. Här är några viktiga saker du bör kontrollera med det här verktyget:

* Om indexstorleken är större än tabellstorleken krävs ett vakuum.
* Kontrollera de tabeller som har den maximala blotten. Om dessa tabeller används ofta måste de semitueras.
* Databasblockering kan göra att e-postmeddelanden inte skickas.

Adobe Campaign har också en [verktyg](../../production/using/monitoring-processes.md#manual-monitoring) för att kontrollera processor- och RAM-användning. Använd det här verktyget och se specifika indikatorer som: **Minne**, **Växla minne**, **Skiva**, **Aktiva processer**. Om värdena är för höga kan du försöka minska antalet arbetsflöden eller schemalägga arbetsflöden att starta vid olika tidpunkter.

## Databaskontroll {#database-performances}

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

* MTA och MTAChild-processer och minne: den **mta** för att distribuera meddelanden till **mtachild** underordnade moduler. Varje **mtachild** förbereder meddelanden innan en auktorisering begärs från statistikservern och skickar dem. Se detta [page](../../installation/using/email-deliverability.md) för mer information.
* TLS-konfiguration: Du bör inte aktivera TLS globalt eftersom det kan minska genomströmningen. I stället bör TLS-inställningar per domän, som hanteras av leveransteamet, justeras efter behov. Se detta [page](../../installation/using/email-deliverability.md#mx-configuration) för mer information.
* DKIM: 1024b är det bästa sättet att rekommendera krypteringsstorlek för att försäkra sig om att DKIM:s säkerhetsnivå är. Lägre DKIM-nycklar anses inte giltiga av de flesta åtkomstleverantörer. Se [den här sidan](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

## Leveransproblem {#deliverability-issues}

Här är en lista över bästa praxis och artiklar som rör slutbarhet:

* IP-anseende: Om IP-anseendet inte är tillräckligt bra kommer resultatet att påverkas. The **Leveransövervakning** I modulen finns olika verktyg för att spåra plattformens leveransförmåga. Se detta [page](../../delivery/using/monitoring-deliverability.md).
* IP-uppvärmning: IP-uppvärmningen utförs av leveransteamet. Detta innebär att antalet e-postmeddelanden som skickas via nya IP-adresser gradvis ökar under några veckor.
* Inställningar för IP-tillhörighet: en felaktig inställning av IP-tillhörighet kan stoppa e-postmeddelanden helt (felaktigt operatörs-/tillhörighetsnamn i konfigurationen) eller minska flödet (ett litet antal IP-adresser i tillhörigheten). Se detta [page](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use).
* E-poststorlek: e-poststorleken spelar en viktig roll när det gäller genomströmning. Den rekommenderade maximala e-poststorleken är 60 kB. Se detta [page](https://helpx.adobe.com/legal/product-descriptions/campaign.html). I [Leveransflöde](../../reporting/using/global-reports.md#delivery-throughput) kontrollera antalet byte som har överförts per timme.
* Stort antal ogiltiga mottagare: om det finns ett stort antal ogiltiga mottagare kan det påverka dataflödet. MTA fortsätter att försöka skicka e-post till ogiltiga mottagare. Se till att din databas underhålls väl.
* Mängd personalisering: Om en leverans fortsätter att vara&quot;personalisering pågår&quot;, kontrollerar du det JavaScript som används i personaliseringsblock.

>[!NOTE]
>
>Se även [Leverans](../../delivery/using/about-deliverability.md) -avsnitt. En djupdykning i leveransförmågan finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=sv).
