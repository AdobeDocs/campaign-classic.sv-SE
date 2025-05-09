---
product: campaign
title: Migrera till Adobe Analytics Connector
description: Campaign - Analytics Connector - frågor och svar
feature: Technote, Analytics Integration
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast för v7-driftsättningar på plats och hybriddriftsättningar"
exl-id: 5bf61654-3d68-4560-a93f-7a768a2c5be4
hide: true
hidefromtoc: true
source-git-commit: a1dbef3e1feca1e3347de013db8bd7809d315016
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 1%

---

# Så här migrerar du befintliga Genesis-integreringar till Adobe Analytics Connector {#acc-aa-faq}

Från och med Campaign Classic v7 version 21.1.3 är Adobe Analytics Data Connector föråldrat. [Läs mer](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html?lang=sv-SE)

Den 1 augusti 2021 har Adobe Campaign Classic tagits bort från det tidigare Data Connectors-gränssnittet, men befintliga Campaign-integreringar kommer att fortsätta att samla in och skicka data till Adobe Analytics fram till den 17 augusti 2022. Efter detta datum upphör integreringen att samla in och skicka data till Adobe Analytics.

Du **måste implementera** den nya Adobe Analytics Connector-integreringen på Adobe Exchange som ersätter den gamla Data Connectors-integreringen. Mer information om Adobe Analytics Connector finns på [den här sidan](../../integrations/using/gs-aa.md).

Läs [Vanliga frågor](#faq-aa) om du har frågor om de här ändringarna. Kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du vill ha mer information.

>[!NOTE]
>
>Om du migrerar från en befintlig Adobe Analytics Data Connector (som tidigare kallades Genesis-integration) och använder den nya klassificeringsarkitekturen i Adobe Analytics behöver du byggversioner från 7.3.1 eller 8.4.1 för att kunna migrera till den nya Adobe Analytics Connector.

## Vad har ändrats?

Nu finns det en ny integrering mellan Campaign Classic v7 och Adobe Analytics. Större förändringar visas nedan.

* Klassificeringen **Kontaktdatum**, som använder typen datum, har tagits bort av Adobe Analytics. För migrerade integreringar kommer den fortfarande att vara av samma typ. För alla **kontaktdatum** som skapats av Campaign blir typen **String**.

* **Bearbetningsregler** skapas av Adobe Campaign som en del av nya integreringar. Antingen **Bearbetningsregler** ska skapas manuellt från Adobe Analytics eller så ska JavaScript-implementering på klientsidan användas direkt. **Bearbetningsreglerna** förblir intakta för befintliga integreringar.

* De inbyggda tekniska arbetsflödena och deras beteende är desamma. Endast de backend-API:er som används av arbetsflödena för att skicka/hämta data till/från Adobe Analytics har ändrats.

* Observera att processen `nlserver` bör konfigureras med IMS Technical Account User för att den nya anslutningen ska fungera. Denna ändring måste göras av Adobe. Kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du vill implementera detta.

* Om du var Adobe Genesis API:er i anpassade arbetsflöden för att hämta in och flytta data från Adobe Analytics måste du nu använda de nya Adobe Analytics 1.4/2.0 API:erna. [Läs mer](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Påverkas du?

Om du använder den befintliga Adobe Analytics Data Connector (som tidigare kallades Genesis-integrering) och integreringen implementerades på en lägre version än Campaign 21.1.3 påverkas du.

Lär dig hur du kontrollerar version [ i det här avsnittet](../../integrations/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Hur uppdaterar jag?

Du måste uppgradera till Campaign 21.1.3 (eller mer) **före 17 augusti 2022**.

Som värdkund kommer Adobe att arbeta med dig för att uppgradera dina instanser till den nyare versionen. Du kan sedan använda [Adobe Analytics-anslutningen](../../platform/using/gs-aa.md).

Som lokalt/hybridkund måste ni uppgradera till en av de nyare versionerna för att dra nytta av den nya integreringen.
När alla instanser har uppgraderats kan du [implementera den nya integrationen](../../integrations/using/adobe-analytics-provisioning.md) till Adobe Analytics Connector och säkerställa en sömlös övergång.

## Vanliga frågor och svar {#faq-aa}

**Hur skaffar jag loggar?**

Konfigurationen och arbetsflödena för användargränssnittet är utrustade med **utförlig** loggning.

I detaljerat läge skrivs begärande- och svarshuvuden också ut för varje API-begäran till Adobe Analytics.

Som lokal användare kan du implementera det utförliga läget enligt följande:

* Så här aktiverar du utförligt läge för användargränssnittet: kör om processen `web` i utförligt läge.
* Om du vill aktivera utförligt läge för arbetsflödena **webAnalytics** väljer du alternativet **Kör i motorn** i arbetsflödesegenskaperna och kör `wfserver` på nytt i utförligt läge.

**Vad betyder felet &#39;Inte administratör för integrationsägare&#39;?**

Läs mer om Data Connectors `Integration Owner Not Admin`-felet i [den här sidan](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Vad händer med gamla data och rapportsviter när migreringen till den nya anslutningen är klar?**

Efter migreringen kommer en ny koppling (migrerad från den gamla kopplingen) att börja skicka data till samma rapportsvit och befintliga data kommer inte att påverkas: de läggs till i befintliga data.

**Vissa befintliga e-postadresser, händelser och rapportsviter i Analytics visas inte i Campaign. Vad ska jag göra?**

Integrationen bygger på data i Token för det tekniska kontot för den dagliga driften. Om det saknas behörighet för en dimension-/mätnings-/rapportsvit från produktprofilen som är kopplad till Technical Account User, kommer API:er som vi använder att helt enkelt misslyckas för dessa förfrågningar.

Om vi läser information om en Analytics-komponent (som mått/dimensioner/segment/rapportsviter) returnerar API inte dessa komponenter i resultatet (vilket kan se ut som om något har tagits bort på Analytics-sidan eller inte finns). Analys-API:t kommer att ignorera dessa begäranden och felmeddelanden.

Lösningen är att uppdatera **produktprofilen** i användarkontexten för Analytics för teknisk användartoken med de nya/saknade komponenterna genom att lägga till dessa komponenter i [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}. Kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du vill ha mer information.

## Användbara länkar

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Ladda ned Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../../installation/using/client-console-availability-for-windows.md)
* [Installera Campaign Client Console](../../installation/using/installing-the-client-console.md)
