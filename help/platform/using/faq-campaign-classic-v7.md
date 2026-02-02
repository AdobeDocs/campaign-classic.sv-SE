---
product: campaign
title: Vanliga frågor och svar om Campaign Classic
description: Frågor som är specifika för Adobe Campaign Classic v7-arkitektur, driftsättning och funktioner
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 8d9bb9d2ff4450646bbf218804b8c8b4459b5a91
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 2%

---

# Vanliga frågor om Campaign Classic v7 {#campaign-classic-v7-faq}

>[!NOTE]
>
>Vanliga frågor och svar om Adobe Campaign Classic v7-arkitektur, distributionsmodeller och v7-specifika funktioner.
>
>**För utförliga svar på vanliga Campaign-frågor** (arbetsflöden, leveranser, målgrupper, rapportering, personalisering osv.), se [**Vanliga frågor och svar om Campaign v8**](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-faq-comprehensive){target="_blank"} som ger detaljerade svar ordnade efter ämne.

## Campaign Classic v7-arkitektur och driftsättning {#v7-architecture}

Hitta svar på om värdmodeller, skillnader i driftsättning och migreringsvägar för Campaign Classic v7. Dessa frågor fokuserar på infrastrukturval och relaterade ansvarsområden.

+++ Vilka värdmodeller finns i Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 har tre driftsättningsmodeller:

* **Värdbaserad (Managed Services)** - Hanteras fullt av Adobe i Adobe-infrastruktur
* **Lokal** - installeras och hanteras på din egen infrastruktur
* **Hybrid** - Arkitektur med flera källor och en blandning av komponenter i molnet och på plats

Varje distributionsmodell har olika funktioner och hanteringsansvar. Vilka moduler, alternativ och konfigurationer som är tillgängliga beror på vilken distributionstyp du har.

[Klicka här om du vill veta mer](../../installation/using/hosting-models.md) om värdmodeller och skillnaderna mellan dem.

**Obs!** Campaign v8 är exklusivt tillgänglig som hanterade molntjänster. [Läs mer om Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

+++

+++ Vilka är skillnaderna när man arbetar lokalt jämfört med i en värdhanterad miljö? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 innehåller en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och vilka konfigurationer de har beror på typen [av distribution](../../installation/using/hosting-models.md) av din installation: värd (Managed Services), hybrid eller lokal.

Viktiga skillnader:

* **Lokal** - Full kontroll över installation, infrastruktur och konfiguration. Kräver interna IT-resurser för underhåll, uppgraderingar och säkerhet.
* **Hosted/Managed Services** - Infrastruktur och underhåll hanteras av Adobe. Automatiska uppgraderingar och förbättrad säkerhet. Begränsad direkt serveråtkomst.
* **Hybrid** - Kombinerar fördelarna med båda modellerna. Marknadsföringsinstans som ligger hos Adobe hanteras exekvering/mellanlagring separat.

[Klicka här för den fullständiga funktionsmatrisen](../../installation/using/capability-matrix.md).

+++

+++ Hur migrerar jag från lokalt/hybridsystem till Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Att migrera till Adobe Managed Services ger förbättrad skalbarhet, säkerhet och minskade IT-kostnader. Det är ofta en stegsten innan man går över till Campaign v8.

**Nyckelpunkter:**

* Inget automatiserat migreringsverktyg tillgängligt - manuell planering och utförande krävs
* Vi rekommenderar starkt stöd för Adobe Professional Services
* Fördelarna är bland annat molninfrastruktur, automatiska säkerhetspatchar, expertsupport och enklare väg till v8
* Migreringen innefattar noggrann genomgång, miljörevision, datarensning, migrering av faser och produktionsreducering

**Komma igång:** Kontakta din Adobe-representant för att utvärdera din miljö och utveckla en detaljerad migreringsplan med Adobe Professional Services.

Läs mer om [migrering till Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

+++

+++ Ska jag migrera från Campaign Classic v7 till Campaign v8? {#should-i-migrate-to-v8}

Campaign v8 är en strategisk Adobe-plattform, idealisk för organisationer som behöver kampanjer i stora volymer, moderna webbgränssnitt, molnbaserade fördelar och långsiktig support. Campaign Classic v7 kommer att nå slutet på supporten under de närmaste åren.

**Överväg att migrera till Campaign v8 om du:**

* Hantera stora datavolymer eller upplev prestandaproblem
* Vill minska IT-kostnaderna och infrastrukturhanteringen (v8 är endast hanterade molntjänster)
* Modernt gränssnitt och integrering med Adobe Experience Platform krävs
* Vill ha framtidssäker teknik med automatiska uppdateringar
* Finns för närvarande på värdbaserade/hanterade tjänster (enklare migreringsväg)

**Viktiga överväganden:**

* Campaign v8 är exklusivt tillgänglig som hanterade molntjänster (inga alternativ på plats/hybridlösningar)
* Kräver planering för migrering av anpassningar och integreringar
* FFDA-arkitekturen ger prestanda men kräver vissa arbetsflödes-/API-anpassningar

**Nästa steg:** Kontakta din Adobe-representant för att utvärdera migreringsberedskapen och åtkomstmigreringsverktygen.

Läs mer:

* [Kampanj v8 - översikt](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}
* [Övergång från Campaign Classic v7 till v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/v7-to-v8.html){target="_blank"}
* [Kampanj v8 - Omfattande frågor och svar](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}

**Detaljerade svar på vanliga Campaign-frågor om arbetsflöden, leveranser, målgrupper, rapportering, personalisering och mycket mer** finns på [Vanliga frågor och svar om Campaign v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"}.

+++

## Bygg uppgraderingar (Campaign Classic v7) {#build-upgrades-v7}

Om du vill ha hjälp med uppgraderingar och relaterade frågor och svar kan du läsa [Vanliga frågor om uppgradering av bygge](faq-build-upgrade.md) och [dokumentationen för uppgradering av byggen](../../production/using/build-upgrade.md).

## Konfiguration av Campaign Classic v7 {#v7-configuration}

Dessa frågor handlar om vanliga konfigurationsuppgifter och principer i Campaign Classic v7, från språkinställningar till säkerhetsförbättringar. Använd dem för att validera installationsalternativ och driftspraxis.

+++ Kan jag ändra språk i Campaign Classic v7-gränssnittet? {#can-i-change-language-v7}

Campaign Classic v7-språk väljs när instansen skapas. **Det går inte att ändra den efteråt.**

Adobe Campaign v7-användargränssnittet finns på fyra språk: engelska, franska, tyska och japanska. Klientkonsolen och servern måste anges med samma språk. Varje instans av Campaign Classic v7 kan bara köras på ett språk.

När du installerar Campaign v7 på engelska kan du välja antingen amerikansk engelska eller brittisk engelska: de skiljer sig åt när det gäller datum- och tidsformat.

[Läs mer i det här avsnittet](../../installation/using/creating-an-instance-and-logging-on.md).

**Obs!** Med webbgränssnittet Campaign v8 kan användare ändra gränssnittsspråk oberoende av varandra. [Läs mer](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

+++

+++ Hur konfigurerar jag säkerhetszoner i Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

Självbetjäningsgränssnittet för säkerhetszoner kan användas för att hantera poster i VPN-säkerhetszonskonfigurationen för en Adobe Campaign Classic v7-distribution. Detta gäller i första hand för driftsättningar på plats och hybriddriftsättningar.

Läs [det här avsnittet](../../installation/using/security-zones.md) om du vill veta mer om säkerhetszoner i Campaign v7.

[Klicka här om du vill veta mer](https://helpx.adobe.com/se/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} om självbetjäningsgränssnittet för säkerhetszonen.

**Obs!** Hosted/Managed Services-kunder bör kontakta Adobe för att konfigurera säkerhetszoner.

+++

+++ Kan Adobe Campaign Classic v7 integreras med LDAP? {#can-campaign-classic-integrate-with-ldap}

Ja. Som **lokal/hybridkund** kan du integrera Campaign Classic v7 med din LDAP-katalog för centraliserad autentisering och användarhantering.

Den här integreringen tillåter:

* Användare som ska autentiseras mot företagets LDAP-katalog
* Centraliserad hantering av användare och rättigheter
* Automatisk synkronisering av användargrupper och behörigheter
* Funktioner för enkel inloggning

[Klicka här för att lära dig hur](../../installation/using/connecting-through-ldap.md) du konfigurerar LDAP-integrering i Campaign Classic v7.

**Obs!** LDAP-integrering är tillgänglig för lokala distributioner och hybriddistributioner. Värdkunder använder Adobe IMS för autentisering.

+++

+++ Vilka är de bästa säkerhetsrutinerna för driftsättningar på plats? {#security-best-practices-on-premise}

Lokala distributioner och hybriddistributioner kräver ytterligare säkerhetskonfiguration och härdning jämfört med värdmiljöer.

**Viktiga säkerhetsområden:**

* Nätverkssäkerhet och brandväggskonfiguration
* Databasåtkomst och -säkerhet
* Härdning av operativsystem
* Filbehörigheter och åtkomstkontroller
* Konfiguration av säkerhetszoner
* Kryptering (vilande och transiterade data)
* Hantering av användaråtkomst
* Vanlig säkerhetspatchning
* Granskningsloggning och övervakning

Läs checklistan för [säkerhetskonfiguration](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy.html?lang=sv){target="_blank"} om du vill identifiera nyckelelement för att kontrollera säkerhetskonfiguration och härdning för lokala distributioner.

+++

+++ Hur rensar jag klientkonsolcachen? {#how-do-i-clear-console-cache}

Om du rensar cachen för Campaign-klientkonsolen löses många vanliga problem med visning och funktioner. Cacheminnet lagrar lokala konfigurationsfiler som ibland kan bli skadade eller inaktuella.

**När cache ska rensas:**

* Nya varumärkningselement visas inte korrekt
* Export-/importfunktioner misslyckas oväntat
* Gränssnittselement uppdateras inte efter konfigurationsändringar
* Prestandaproblem eller långsam konsolrespons
* Efter uppgradering till en ny klientkonsolversion

**Så här rensar du cache:**

1. **Mjuk cache rensad (försök först):**
   * Öppna Campaign-klientkonsolen
   * Gå till menyn **[!UICONTROL File]**
   * Välj **[!UICONTROL Clear the local cache...]**
   * Bekräfta åtgärden när du uppmanas till det
   * Starta om klientkonsolen

2. **Rensa hårddiskcache (om mjuk rensning inte löser problemet):**
   * Utför rensning av mjuk cache först
   * Logga ut och stäng klientkonsolen helt
   * Navigera till:
      * Windows 7/10: `C:\Users\<Username>\AppData\Roaming\Neolane\NL_5\`
      * Windows XP: `C:\Documents and Settings\<Username>\Application Data\Neolane\NL_5\`
   * Ta bort alla XML-filer med namnet `nlclient-config-<alphanumerical value>.xml` och associerade mappar
   * **Viktigt!** Ta INTE bort `nlclient_cnx.xml` fil
   * Starta om klientkonsolen

Läs mer i [dokumentationen för klientkonsolen för Campaign](../../platform/using/launching-adobe-campaign.md).

+++

+++ Var kan värdbaserade kunder hantera instansinställningar? {#where-to-manage-instance-settings}

Kontrollpanelen [](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv){target="_blank"} hjälper produktadministratörer för Adobe Campaign att hantera inställningar och spåra användningen för varje instans. Med det intuitiva gränssnittet kan du övervaka viktiga resurser och utföra administrativa uppgifter som uppdateringar av IP tillåtelselista, SFTP-lagringsövervakning, nyckelhantering med mera.

**Viktiga fördelar:**

* Gör snabbt ändringar i inställningarna utan att kontakta Kundtjänst.
* Konfigurera inställningar baserat på olika affärsbehov vid olika tidpunkter.
* kontrollera åtkomstinställningarna efter behov för att förbättra säkerheten.

+++

## Få hjälp {#getting-help}

Hitta viktig dokumentation, vanliga frågor och supportkanaler för Campaign Classic v7, inklusive länkar till communityforum och Adobe support.

+++ Var hittar jag Campaign Classic v7-dokumentation? {#where-to-find-more-info-v7}

**Dokumentation och resurser:**

* [Campaign Classic v7-dokumentation](https://experienceleague.adobe.com/docs/campaign-classic/using/campaign-classic-home.html?lang=sv){target="_blank"} - fullständig dokumentation
* [Versionsinformation för Campaign Classic v7](../../rn/using/latest-release.md) - Senaste versionsinformation
* [Kompatibilitetsmatris för Campaign Classic](../../rn/using/compatibility-matrix.md) - system och versioner som stöds
* [Campaign Classic-självstudiekurser](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv){target="_blank"} - videokurser

**För vanliga kampanjfrågor:**

Se [**Vanliga frågor och svar om Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"} som ger detaljerade svar om:

* Komma igång med Campaign
* Profiler och målgrupper
* Design och leverans av meddelanden
* Arbetsflöden och automatisering
* Rapportering och analys
* Kampanjinställningar och konfiguration
* Resurser för utvecklare
* Integritet och efterlevnad

+++

+++ Hur får jag tillgång till support för Campaign Classic v7 i communityn eller Adobe? {#where-to-get-support-v7}

**Community och support:**

* [Campaign Community Forums](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe Support](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}

+++
