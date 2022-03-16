---
product: campaign
title: Kom igång med uppgraderingar
description: Läs mer om uppgraderingar till Campaign Classic
feature: Overview
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 329cf80ff021322e57a63cf86f4b4e206f6385d1
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 97%

---

# Kom igång med uppgraderingar{#rn-overview}

![](../../assets/v7-only.svg)

## Versionsstatusar{#rn-statuses}

Varje ny version kommer med en status som visas med en färg.

![](assets/do-not-localize/green3.png) **Allmän tillgänglighet** (GA) – senaste stabila build, validerad i produktion och rekommenderad av Adobe.

![](assets/do-not-localize/limited3.png) **Begränsad tillgänglighet** (LA) – endast driftsättning på begäran.

![](assets/do-not-localize/blue3.png) **Releasekandidat** (RC) – senaste versionen med nya funktioner.

![](assets/do-not-localize/orange3.png) **Inte längre tillgängligt** – ingen distribution. Ingen felkorrigering. Vi rekommenderar att du uppdaterar till en nyare version.

![](assets/do-not-localize/red3.png) **Inaktuell** – ingen distribution. Ingen felkorrigering. Befintliga implementeringar måste uppgraderas.

## Versionscykel

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att ge dig den senaste och bästa produkten, hålla din miljö säker och förbättra din upplevelse med produkten.

Därför anser vi att det är viktigt att du **kör den senaste versionen** av Adobe Campaign. Det ser också till att du får en bättre support eftersom det oftast går mycket snabbare att identifiera, återskapa och åtgärda ett problem i en ny build. Många problem som du kan råka ut för har redan åtgärdats i de senaste versionerna.

Som en värdbaserad användare har du automatiskt tillgång till uppgraderingen med den senaste stabila versionen utan någon åtgärd. Läs mer i [avsnittet Årlig uppgradering](#yearly-upgrade). Om du migrerar från en gammal build rekommenderar Adobe att du uppgraderar till den här versionen först.

## Rekommendationer{#recommendations}

För att säkerställa en stabil konfiguration rekommenderar vi att du installerar **samma build** på alla servrar som körs på samma klientkonfiguration.

Om inget annat anges i versionsinformationen måste dessutom klientkonsolen vara aktiverad **samma bygge** som serverinstansen.

Om du vill att implementeringen ska vara aktuell bör du läsa sidorna om de [inaktuella och borttagna funktionerna](../../rn/using/deprecated-features.md) samt [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för varje ny version.

## Uppgraderingprocess{#process-upgrade}

Som värdbaserad kund (Managed Service eller hybrid) måste du kontakta kundtjänst för att få din miljö uppgraderad.

Som lokal användare kan du utföra uppgraderingen. För att göra detta måste du [hämta den senaste stabila builden (GA)](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) och uppgradera alla dina miljöer. Läs mer om [uppgraderingsprocessen](../../production/using/build-upgrade.md) och se [Vanliga frågor och svar om uppgradering av builds](../../platform/using/faq-build-upgrade.md).

## Årlig uppgradering {#yearly-upgrade}

Adobe och Adobe Campaign strävar efter att ge dig bästa möjliga upplevelse och värde genom våra programvarulösningar. Organisationen vill säkerställa att ni har tillgång till de senaste versionerna av relaterad teknik som våra lösningar utnyttjar för att utföra sina uppgifter.

Adobe Campaign Classic använder en rad olika teknologier för att leverera värde. Den här kombinationen av tekniker kräver att du regelbundet uppgraderar dina instanser i Campaign Classic för att säkerställa att de senaste versionerna används så att de kan leverera överlägsen säkerhet, stabilitet och prestanda.

Som en värdbaserad användare har du automatiskt tillgång till uppgraderingen med den senaste GA-builden utan någon åtgärd. Läs mer i Vanliga frågor och svar nedan.

### Varför behöver min organisation den här uppgraderingen?

Adobe meddelar dig direkt om du är en värdbaserad kund och vi har identifierat att du behöver uppgradera en eller flera av teknikerna för Campaign Classic, samt uppdatera den aktuella builden och/eller versionen.

Som en lokal- eller hybridkund som kör en äldre version uppmuntrar Adobe dig att gå över till den senaste stabila builden (GA).

Det här garanterar att ditt konto är säkert mot sårbarheter och utnyttjar den uppdaterade prestandatekniken. Den här uppgraderingen konfigurerar också ditt konto för enklare och regelbundna uppgraderingar i framtiden som kräver mindre manuellt arbete och färre åtgärder.

### Hur ser uppgraderingen ut och när släpps den?

Adobe-teamet leder och vägleder din organisation genom den här resan.

Vi har organiserat ett team med dedikerade kundtjänstassistenter, produktchefer, ingenjörer och TechOps-specialister samt produktkonsulter för att hjälpa till och säkerställa att upplevelsen är smidig.

Vi strävar efter att se till att du har relevant projekt- och kontaktinformation.

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
    <li>Arbetsvolymen för kundtjänst minskar, vilket ger snabbare lösningar och mer uppmärksamhet åt de problem som inte är relaterade till uppgraderingar.</li>
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
    <li>Förbättringar av hela teknikstacken i Campaign Classic kommer att kännas av i både marknadsförings- och IT-avdelningen i organisationen.</li>
    </ul>
  </td>

<td>
      <img alt="Builduppgradering" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Enklare uppgraderingar</strong>
    </a>
    </div>
    <ul>
    <li>Arbetet och komplexiteten med att uppgradera din Campaign Classic-instans ökar med avståndet mellan två versioner (v5 --&gt; v7).</li>
    <li>Ju längre organisationen väntar, desto mer komplicerad blir uppgraderingen (och desto fler sårbarheter utsätts du för).</li>
    <li>Regelbundna uppdateringar minskar driftstoppen för att uppgradera och minskar risken för regression.</li>
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
