---
product: campaign
title: Vanliga frågor och svar om Campaign Classic
description: Frågor som är specifika för Adobe Campaign Classic v7-arkitektur, driftsättning och funktioner
feature: Overview, Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: 295e3596d9291cbcc55e2d264309141526c3806b
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 1%

---

# Vanliga frågor om Campaign Classic v7 {#campaign-classic-v7-faq}

Vanliga frågor och svar om Adobe Campaign Classic v7-arkitektur, distributionsmodeller och v7-specifika funktioner.

**För utförliga svar på vanliga Campaign-frågor** (arbetsflöden, leveranser, målgrupper, rapportering, personalisering osv.), se [**Vanliga frågor och svar om Campaign v8**](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/campaign-faq-comprehensive.html){target="_blank"} som ger detaljerade svar ordnade efter ämne.

## Campaign Classic v7-arkitektur och driftsättning {#v7-architecture}

### Vilka värdmodeller finns i Campaign Classic v7? {#what-are-the-hosting-models-available-in-campaign-classic-v7}

Adobe Campaign Classic v7 har tre driftsättningsmodeller:

* **Värdbaserad (Managed Services)** - Hanteras fullt av Adobe i Adobe-infrastruktur
* **Lokal** - installeras och hanteras på din egen infrastruktur
* **Hybrid** - Arkitektur med flera källor och en blandning av komponenter i molnet och på plats

Varje distributionsmodell har olika funktioner och hanteringsansvar. Vilka moduler, alternativ och konfigurationer som är tillgängliga beror på vilken distributionstyp du har.

[Klicka här om du vill veta mer](../../installation/using/hosting-models.md) om värdmodeller och skillnaderna mellan dem.

**Obs!** Campaign v8 är exklusivt tillgänglig som hanterade molntjänster. [Läs mer om Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/new/whats-new.html){target="_blank"}.

### Vilka är skillnaderna när du arbetar lokalt jämfört med i en hostingmiljö? {#what-are-the-differences-when-working-on-premise-vs-in-a-hosted-environment}

Adobe Campaign Classic v7 innehåller en uppsättning moduler och alternativ. Vilka moduler som är tillgängliga och vilka konfigurationer de har beror på typen [av distribution](../../installation/using/hosting-models.md) av din installation: värd (Managed Services), hybrid eller lokal.

Viktiga skillnader:

* **Lokal** - Full kontroll över installation, infrastruktur och konfiguration. Kräver interna IT-resurser för underhåll, uppgraderingar och säkerhet.
* **Hosted/Managed Services** - Infrastruktur och underhåll hanteras av Adobe. Automatiska uppgraderingar och förbättrad säkerhet. Begränsad direkt serveråtkomst.
* **Hybrid** - Kombinerar fördelarna med båda modellerna. Marknadsföringsinstans som ligger hos Adobe hanteras exekvering/mellanlagring separat.

[Klicka här för den fullständiga funktionsmatrisen](../../installation/using/capability-matrix.md).

### Hur migrerar jag från lokalt/hybridsystem till Adobe Managed Services? {#how-do-i-migrate-from-on-premise-hybrid-to-adobe-managed-services}

Att migrera till Adobe Managed Services ger förbättrad skalbarhet, säkerhet och minskade IT-kostnader. Det är ofta en stegsten innan man går över till Campaign v8.

**Nyckelpunkter:**

* Inget automatiserat migreringsverktyg tillgängligt - manuell planering och utförande krävs
* Vi rekommenderar starkt stöd för Adobe Professional Services
* Fördelarna är bland annat molninfrastruktur, automatiska säkerhetspatchar, expertsupport och enklare väg till v8
* Migreringen innefattar noggrann genomgång, miljörevision, datarensning, migrering av faser och produktionsreducering

**Komma igång:** Kontakta din Adobe-representant för att utvärdera din miljö och utveckla en detaljerad migreringsplan med Adobe Professional Services.

Läs mer om [migrering till Managed Services](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic-blogs/migrate-your-adobe-campaign-v7-onprem-hybrid-environment-to/ba-p/681605){target="_blank"}.

## Bygg uppgraderingar (Campaign Classic v7) {#build-upgrades-v7}

### Vad är en bygguppgradering i Campaign Classic v7? {#what-is-a-build-upgrade-v7}

En bygguppgradering är när Adobe Campaign Classic v7 uppdateras till det senaste säkra versionsnumret, men ändå ligger kvar på samma huvud-/delnivå. Exempel: Campaign Classic v7 build 9026 to Campaign v7 build 9032.

Adobe Campaign uppdateras regelbundet. Mindre versioner släpps med nya funktioner, förbättringar och korrigeringar. Dessutom släpps byggen med enbart kumulativa korrigeringar regelbundet.

Läs mer [i det här avsnittet](../../rn/using/rn-overview.md).

### Hur uppgraderar jag Campaign Classic v7 till den senaste versionen? {#how-can-i-upgrade-campaign-classic-v7}

Adobe Campaign Classic använder en rad olika teknologier för att ge mervärde. Den här kombinationen av tekniker kräver att du regelbundet uppgraderar dina Campaign Classic v7-instanser för att säkerställa att de senaste versionerna används för att leverera överlägsen säkerhet, stabilitet och prestanda.

**För värdkunder:** Du får automatiskt en årlig uppgradering från Campaign med den senaste stabila versionen. Adobe hanterar uppgraderingsprocessen och koordinerar timingen med dig.

**För lokalt/hybridkunder:** Du ansvarar för att utföra uppgraderingar. Adobe rekommenderar starkt att du uppgraderar minst en gång per år.

[Läs det här avsnittet](../../production/using/build-upgrade.md) om du vill veta mer om hur du uppdaterar din miljö och läsa [Vanliga frågor om uppgradering](../../platform/using/faq-build-upgrade.md) för mer information om det här specifika ämnet.

### Vilken är den senaste versionen av Adobe Campaign Classic v7? {#what-is-the-latest-version-v7}

Den senaste versionen av Campaign Classic v7, med nya funktioner och dokumentation, finns i den senaste [versionsinformationen](../../rn/using/latest-release.md).

### Hur vet jag vilken version av Campaign Classic v7 jag har? {#how-do-i-know-which-version-v7}

Kontrollera version och build-nummer på menyn **[!UICONTROL Help > About...]** i Adobe Campaign Client Console. Rutan **[!UICONTROL About]** innehåller detaljerad information om versionen och bygget som du kör för både konsolen och servern.

Läs mer [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

### Är en versionsuppgradering detsamma som en versionsuppgradering? {#is-build-upgrade-same-as-version-upgrade}

Nej. En versionsuppgradering är en stegvis uppdatering i en viss större version, medan en versionsuppgradering är en förändring från en större version till en annan. Uppgraderingarna är enkla och innebär vanligtvis inga större förändringar i arkitektur, teknik eller datamodell.

Versionsuppgraderingar (t.ex. v7 till v8) innehåller vanligtvis betydande tekniska ändringar och kan kräva konfigurationsändringar eller partiell omimplementering beroende på dina anpassningar.

## Konfiguration av Campaign Classic v7 {#v7-configuration}

### Kan jag ändra språk i Campaign Classic v7-gränssnittet? {#can-i-change-language-v7}

Campaign Classic v7-språk väljs när instansen skapas. **Det går inte att ändra den efteråt.**

Adobe Campaign v7-användargränssnittet finns på fyra språk: engelska, franska, tyska och japanska. Klientkonsolen och servern måste anges med samma språk. Varje instans av Campaign Classic v7 kan bara köras på ett språk.

När du installerar Campaign v7 på engelska kan du välja antingen amerikansk engelska eller brittisk engelska: de skiljer sig åt när det gäller datum- och tidsformat.

[Läs mer i det här avsnittet](../../installation/using/creating-an-instance-and-logging-on.md).

**Obs!** Med webbgränssnittet Campaign v8 kan användare ändra gränssnittsspråk oberoende av varandra. [Läs mer](https://experienceleague.adobe.com/docs/campaign/campaign-v8/start/connect.html#language-pref){target="_blank"}.

### Hur konfigurerar jag säkerhetszoner i Campaign Classic v7? {#how-can-i-configure-security-zones-v7}

Självbetjäningsgränssnittet för säkerhetszoner kan användas för att hantera poster i VPN-säkerhetszonskonfigurationen för en Adobe Campaign Classic v7-distribution. Detta gäller i första hand för driftsättningar på plats och hybriddriftsättningar.

Läs [det här avsnittet](../../installation/using/security-zones.md) om du vill veta mer om säkerhetszoner i Campaign v7.

[Klicka här om du vill veta mer](https://helpx.adobe.com/se/campaign/kb/configuring-security-zones-self-service.html){target="_blank"} om självbetjäningsgränssnittet för säkerhetszonen.

**Obs!** Hosted/Managed Services-kunder bör kontakta Adobe för att konfigurera säkerhetszoner.

### Kan Adobe Campaign Classic v7 integreras med LDAP? {#can-campaign-classic-integrate-with-ldap}

Ja. Som **lokal/hybridkund** kan du integrera Campaign Classic v7 med din LDAP-katalog för centraliserad autentisering och användarhantering.

Den här integreringen tillåter:

* Användare som ska autentiseras mot företagets LDAP-katalog
* Centraliserad hantering av användare och rättigheter
* Automatisk synkronisering av användargrupper och behörigheter
* Funktioner för enkel inloggning

[Klicka här för att lära dig hur](../../installation/using/connecting-through-ldap.md) du konfigurerar LDAP-integrering i Campaign Classic v7.

**Obs!** LDAP-integrering är tillgänglig för lokala distributioner och hybriddistributioner. Värdkunder använder Adobe IMS för autentisering.

### Vilka är de bästa säkerhetsrutinerna för driftsättningar på plats? {#security-best-practices-on-premise}

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

### Hur rensar jag klientkonsolcachen? {#how-do-i-clear-console-cache}

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

## Få hjälp {#getting-help}

### Var finns mer information om Campaign Classic v7? {#where-to-find-more-info-v7}

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

**Community och support:**

* [Campaign Community Forums](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community){target="_blank"}
* [Adobe Support](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}
* [Kontrollpanelen (värdbaserade kunder)](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv){target="_blank"}

### Ska jag migrera från Campaign Classic v7 till Campaign v8? {#should-i-migrate-to-v8}

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
