---
product: campaign
title: Migrera till Adobe Analytics Connector
description: Campaign - Analytics Connector - frågor och svar
source-git-commit: e61f9facac61f942d26b4ffcb5a84a43ede6872d
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 5%

---

# Så här migrerar du till Adobe Analytics Connector {#acc-aa-faq}

Från och med version 21.1.3 av Campaign Classic är Adobe Analytics Data Connector föråldrat. [Läs mer](https://experienceleague.adobe.com/docs/analytics/import/dataconnectors/data-connectors-eol.html)

Den 1 augusti 2021 kommer Adobe Campaign Classic att tas bort från det äldre användargränssnittet för Data Connectors, men befintliga Campaign-integreringar kommer att fortsätta samla in och skicka data till Adobe Analytics fram till den 1 mars 2022. Den 1 mars 2022 upphör integreringen att samla in och skicka uppgifter till Adobe Analytics.

Du måste migrera till den nya integreringen av Adobe Analytics Connector på Adobe Exchange som ersätter den tidigare integreringen av Data Connectors, enligt beskrivningen i [den här sidan](../platform/using/adobe-analytics-connector.md).


>[!NOTE]
>
>Läs [Frågor och svar](#faq-aa) om du har frågor om dessa ändringar. Mer information får du om du kontaktar [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).


## Vad har ändrats?

Nu finns det en ny integrering mellan Campaign Classic v7 och Adobe Analytics. Större förändringar visas nedan.

* Integrationen mellan Adobe Campaign Classic- och Adobe Analytics-autentisering har flyttats från användare/lösenord till Adobe Identity Management-tjänst (IMS). Därför måste du implementera Adobe IMS och ansluta till Campaign [via en Adobe ID](../integrations/using/about-adobe-id.md) innan du startar implementeringen av Analytics Connector.

* Klassificeringen **Kontaktdatum**, som använder datumtypen, har tagits bort av Adobe Analytics. För migrerade integreringar förblir den fortfarande av samma typ. För alla **kontaktdatum** som skapats av Campaign är typen **String**.

* **Bearbetningsregler** skapas av Adobe Campaign som en del av nya integreringar. Antingen **Bearbetningsregler** ska skapas manuellt från Adobe Analytics eller så ska JavaScript-implementering på klientsidan användas direkt. **Bearbetningsreglerna** förblir intakta för befintliga integreringar.

* De inbyggda tekniska arbetsflödena och deras beteende är desamma. Endast de backend-API:er som används av arbetsflödena för att skicka/hämta data till/från Adobe Analytics har ändrats.

* Observera att `nlserver`-processen bör konfigureras med IMS Technical Account User för att den nya anslutningen ska fungera. Denna ändring måste göras av Adobe. Om du vill implementera detta kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* Om du var Adobe Genesis API:er i anpassade arbetsflöden för att hämta in och flytta data från Adobe Analytics måste du nu använda de nya Adobe Analytics 1.4/2.0 API:erna. [Läs mer](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360047148832-Replacements-for-Data-Connector-API-calls)

## Påverkas du?

Om du använder den befintliga Adobe Analytics Data Connector (som tidigare kallades Genesis-integrering) och integreringen implementerades på en lägre version än Campaign 21.1.3 påverkas du.

Lär dig hur du kontrollerar din version [i det här avsnittet](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Hur uppdaterar jag?

Du måste uppgradera till Campaign 21.1.3 (eller mer) **före 1 mars 2022**.

Som värdkund kommer Adobe att arbeta med dig för att uppgradera dina instanser till den nyare versionen.

Som lokalt/hybridkund måste ni uppgradera till en av de nyare versionerna för att dra nytta av den nya integreringen.

När alla instanser har uppgraderats kan du [implementera den nya integrationen](../platform/using/adobe-analytics-connector.md) till Adobe Analytics Connector och säkerställa en smidig övergång.


## Vanliga frågor och svar {#faq-aa}

**Hur får jag tag i loggar?**

Konfigurationen och arbetsflödena för användargränssnittet är utrustade med **utförlig**-loggning.

I detaljerat läge skrivs begärande- och svarshuvuden också ut för varje API-begäran till Adobe Analytics.

Som lokal användare kan du implementera det utförliga läget enligt följande:

* Så här aktiverar du utförligt läge för användargränssnittet: kör om `web`-processen i utförligt läge.
* Så här aktiverar du ett detaljerat läge för arbetsflödena **webAnalytics**: välj alternativet **Kör i motorn** i arbetsflödesegenskaperna och kör om `wfserver` i detaljerat läge.

**Vad betyder felet &#39;Integrationsägare inte administratör&#39;?**

Läs mer om felet i `Integration Owner Not Admin` i [den här sidan](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360035167932-Adobe-Analytics-Data-Connectors-Integration-Owner-Not-Admin-Error).

**Vad händer med gamla data och rapportsviter när migreringen till den nya kopplingen är klar?**

Efter migreringen kommer en ny koppling (migrerad från den gamla kopplingen) att börja skicka data till samma rapportserie och befintliga data påverkas inte: kommer att läggas till befintliga data.

**Vissa befintliga evars/händelser/rapportsviter i Analytics är inte synliga i Campaign. Vad ska jag göra?**

Integrationen bygger på data i Token för det tekniska kontot för den dagliga driften. Om det saknas behörighet för en dimension-/mätnings-/rapportsvit från produktprofilen som är kopplad till Technical Account User, kommer API:er som vi använder att helt enkelt misslyckas för dessa förfrågningar.

Om vi läser information om en Analytics-komponent (som mått/dimensioner/segment/rapportsviter) returnerar API inte dessa komponenter i resultatet (vilket kan se ut som om något har tagits bort på Analytics-sidan eller inte finns). Analys-API:t kommer att ignorera dessa begäranden och felmeddelanden.

Lösningen är att uppdatera **produktprofilen** i användarkontexten för Analytics för teknisk användartoken med de nyskapade/saknade komponenterna genom att lägga till dessa komponenter i [Adobe Admin Console](https://adminconsole.adobe.com/). Kontakta [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du vill ha mer vägledning.

## Användbara länkar

* [Uppgradera din miljö](../production/using/build-upgrade.md)
* [Vanliga frågor och svar om Builduppgradering](../platform/using/faq-build-upgrade.md)
* [Ladda ned Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Gör den nya klientkonsolen tillgänglig för användare](../installation/using/client-console-availability-for-windows.md)
* [Installera Campaign Client Console](../installation/using/installing-the-client-console.md)
