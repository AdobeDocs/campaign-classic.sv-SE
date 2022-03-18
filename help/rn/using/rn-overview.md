---
product: campaign
title: Kom igång med uppgraderingar
description: Läs mer om uppgraderingar till Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 29e56d6bf2817eeb863cbe33f99233a8241f2bf5
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 53%

---

# Kom igång med uppgraderingar{#rn-overview}

![](../../assets/v7-only.svg)

## Versionsstatusar{#rn-statuses}

Varje ny version kommer med en status som visas med en färg.

![](assets/do-not-localize/green3.png) **Allmän tillgänglighet** (GA) - Den senaste stabila versionen, validerad i produktion och rekommenderas av Adobe.

![](assets/do-not-localize/limited3.png) **Begränsad tillgänglighet** (LA) – endast driftsättning på begäran.

![](assets/do-not-localize/blue3.png) **Releasekandidat** (RC) – senaste versionen med nya funktioner.

![](assets/do-not-localize/orange3.png) **Inte längre tillgängligt** – ingen distribution. Ingen felkorrigering. Vi rekommenderar att du uppdaterar till en nyare version.

![](assets/do-not-localize/red3.png) **Inaktuell** – ingen distribution. Ingen felkorrigering. Befintliga implementeringar måste uppgraderas.

## Versionscykel{#rn-cycle}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att ge dig den senaste och bästa produkten, hålla din miljö säker och förbättra din upplevelse med produkten.

Detta är anledningen till att det är viktigt att du **kör den senaste stabila versionen** Adobe Campaign. Det ser också till att du får en bättre supportupplevelse eftersom det oftast går mycket snabbare att identifiera, återskapa och åtgärda ett problem i en nyligen gjord version. Många problem som du kan råka ut för har redan åtgärdats i de senaste versionerna.

Som en värdbaserad användare har du automatiskt tillgång till uppgraderingen med den senaste stabila versionen utan någon åtgärd. Läs mer i [avsnittet Årlig uppgradering](#yearly-upgrade). Om du migrerar från en gammal build rekommenderar Adobe att du uppgraderar till den här versionen först.

## Rekommendationer{#recommendations}

För att konfigurationen ska bli stabil rekommenderar Adobe att du installerar **samma bygge** på alla servrar som körs på samma klientkonfiguration.

Om inget annat anges i versionsinformationen måste dessutom klientkonsolen vara aktiverad **samma bygge** som serverinstansen.

Om du vill att implementeringen ska vara aktuell bör du läsa sidorna om de [inaktuella och borttagna funktionerna](../../rn/using/deprecated-features.md) samt [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för varje ny version.

## Uppgraderingprocess{#process-upgrade}

Som värdkund (Managed Service eller Hybrid) kontaktar du kundtjänstteamet för att få din miljö uppgraderad.

Som lokal användare kan du utföra uppgraderingen. För att göra detta [ladda ned den senaste stabila versionen (GA)](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) och uppgradera alla dina miljöer. Läs mer om [uppgraderingsprocessen](../../production/using/build-upgrade.md) och se [Vanliga frågor och svar om uppgradering av builds](../../platform/using/faq-build-upgrade.md).

## Årlig uppgradering {#yearly-upgrade}

Adobe strävar efter att ge dig bästa möjliga upplevelse och värde genom våra programvarulösningar. Organisationen strävar efter att se till att du har tillgång till de senaste versionerna av relaterad teknik som våra lösningar använder för att utföra sina uppgifter.

Adobe Campaign Classic använder en rad olika teknologier för att leverera värde. Den här kombinationen av tekniker kräver att du uppgraderar dina instanser i Campaign Classic regelbundet för att säkerställa att de senaste versionerna används för att leverera överlägsen säkerhet, stabilitet och prestanda.

Som värdanvändare får du automatiskt uppgradering med den senaste GA-versionen utan någon åtgärd. Läs mer i Vanliga frågor och svar nedan.

### Varför behöver min organisation den här uppgraderingen?

Om ditt konto har identifierats som en värdkund och behöver uppgradera en eller flera av teknikerna som är kopplade till Campaign Classic, samt uppdatera den aktuella versionen och/eller versionen, meddelar Adobe dig direkt.

Som en lokal- eller hybridkund som kör en äldre version uppmuntrar Adobe dig att gå över till den senaste stabila builden (GA).

Detta garanterar att ditt konto är säkert mot sårbarheter och att du använder uppdaterad prestandateknik. Den här uppgraderingen placerar även ditt konto för enklare, regelbundna uppgraderingar som kräver mindre manuellt arbete och åtgärder.

### Hur ser uppgraderingen ut och när släpps den?

Adobe-teamet är här för att leda och vägleda organisationen genom den här resan.

Ett team med dedikerade kundtjänstrepresentanter, produktchefer, ingenjörer och TechOps-specialister och produktkonsulter är här för att hjälpa till och säkerställa att upplevelsen blir smidig.

### Fördelar

<tr>
  <td>
      <img alt="Säkerhet" src="assets/do-not-localize/security.png"/>
    <div>
    <strong>Förbättrad säkerhet</strong>
    </div>
    <ul>
    <li>En kombination av tekniker som används för att driva Adobe Campaign Classic arbetar tillsammans för att skapa värde.</li>
    <li>Alla dina instanser måste uppdateras för att vara säkra.</li>
    <li>Säkerhet kräver konstant fokus och förebyggande underhåll.</li>
    <li>Säkerhetsrisker är alltid närvarande och kan inte ignoreras: varje uppgradering av Campaign Classic förbättrar säkerheten.</li>
    </ul>
  </td>

<td>
      <img alt="Support" src="assets/do-not-localize/support.png" />
    <div>
    <strong>Förbättrad support</strong>
    </div>
    <ul>
    <li>De flesta kritiska problemen går att lösa med uppgraderingar och kan undvikas.</li>
    <li>Regelbundna uppgraderingar hjälper till att minska utmaningar och öka effektiviteten genom att eliminera dessa utmaningar.</li>
    <li>Volymen på kundtjänst minskar, vilket ger snabbare lösningar och mer uppmärksamhet åt problem som inte är relaterade till uppgraderingar.</li>
    </ul>
  </td>
</tr>

<tr>
  <td>
      <img alt="Underhåll" src="assets/do-not-localize/maintenance.png"/>
    <div>
    <strong>Förbättrat underhåll och stabilitet</strong>
    </div>
    <ul>
    <li>Med tiden kan Adobe Campaign-teamet hitta sätt att förbättra produktens stabilitet och prestanda samt korrigera kända fel.</li>
    <li>Uppgraderingen håller instansen uppdaterad med dessa förbättringar och eliminerar vanliga problem som kan uppstå i organisationer som har snabb tillväxt och/eller komplexitet i sina Campaign Classic-instanser.</li>
    <li>Förbättringar i hela teknikhögen som driver Campaign Classic är märkbara både för marknadsförings- och IT-team i din organisation.</li>
    </ul>
  </td>

<td>
      <img alt="Builduppgradering" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Enklare uppgraderingar</strong>
    </a>
    </div>
    <ul>
    <li>Arbetet med att uppgradera din instans i Campaign Classic ökar med avståndet mellan två versioner (v5 —&gt; v7).</li>
    <li>Ju längre organisationen väntar, desto mer komplicerad blir uppgraderingen (och desto fler sårbarheter utsätts du för).</li>
    <li>Regelbundna uppdateringar minskar tiden för uppgradering och risken för regression.</li>
    </ul>
  </td>
</tr>
</table>

## Ytterligare resurser{#support}

* [Hitta din version av Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
* [Hjälp och support](../../support.md)
* [Versioner av Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/release-notes.html?lang=sv)
* [Senaste dokumentationsuppdateringarna](../../rn/using/documentation-updates.md)
* [Inaktuella och borttagna funktioner](../../rn/using/deprecated-features.md)
* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)

Prenumerera på [Adobes prioriterade produktuppdatering](https://www.adobe.com/se/subscription/priority-product-update.html) för att få information om nya versioner av lösningen Experience Cloud.
