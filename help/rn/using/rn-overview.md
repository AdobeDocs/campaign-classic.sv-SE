---
product: campaign
title: Kom igång med uppgraderingar
description: Läs mer om uppgraderingar till Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Release Notes
role: User
level: Beginner
exl-id: 7a05fdff-8f9d-4e8d-812e-0f1509db5499
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: ht
source-wordcount: '939'
ht-degree: 100%

---

# Versionsuppdateringar{#rn-overview}



Adobe Campaign Classic släpper regelbundet produktuppdateringar som innehåller nya funktioner, felkorrigeringar och förbättrar prestanda, säkerhet och användbarhet. Dessa uppdateringar släpps som **produktversioner**. Detaljerad information om varje ny version finns i [Versionsinformationen](latest-release.md).

## Versionsstatusar{#rn-statuses}

Varje ny version har en status som identifieras av en färg i [Versionsinformationen](latest-release.md).


| Status | Beskrivning |
|---|---|
| [!BADGE Allmän tillgänglighet]{type=Positive} | Den senaste stabila build, validerad i produktion och rekommenderad av Adobe. |
| [!BADGE Begränsad tillgänglighet]{type=Neutral} | Endast distribution på begäran. |
| [!BADGE Frisläppningskandidat]{type=Informative} | Senaste build med nya funktioner. |
| [!BADGE Inte längre tillgänglig]{type=Caution} | Ingen distribution. Ingen felkorrigering. Vi rekommenderar att du uppdaterar till en nyare version. |
| [!BADGE Inaktuell]{type=negative} | Ingen distribution. Ingen felkorrigering. Befintliga implementeringar måste uppgraderas. |

<!--
![](assets/do-not-localize/green3.png) **General Availability** (GA) - Latest stable build, validated in production, and recommended by Adobe. 

![](assets/do-not-localize/limited3.png) **Limited Availability** (LA) - On-demand deployment only.

![](assets/do-not-localize/blue3.png) **Release Candidate** (RC) - Latest build with new capabilities.

![](assets/do-not-localize/orange3.png) **No longer available** - No deployment. No bug fix. Update to a newer build is recommended.

![](assets/do-not-localize/red3.png) **Deprecated** - No deployment. No bug fix. Existing implementations must be upgraded.
-->

## Versionscykel{#rn-cycle}

Adobe Campaign uppdateras regelbundet. Denna regelbundna uppdateringsfrekvens syftar till att ge dig den senaste och bästa produkten, hålla din miljö säker och förbättra din upplevelse med produkten.

Därför anser vi att det är viktigt att du **kör den senaste stabila versionen** av Adobe Campaign. Det säkerställer också att du får en bättre supportupplevelse eftersom det oftast går mycket snabbare att identifiera, återskapa och åtgärda ett problem i en ny build. Dessutom har många problem du kan stöta på redan åtgärdats i de senaste builderna.

Som en värdbaserad kund har du automatiskt tillgång till uppgraderingen med den senaste stabila versionen utan någon åtgärd. Läs mer i [avsnittet Årlig uppgradering](#yearly-upgrade). Om du migrerar från en gammal version rekommenderar Adobe att du uppgraderar till den här versionen först.

## Rekommendationer{#recommendations}

För att säkerställa en stabil konfiguration rekommenderar Adobe att du installerar **samma build** på alla servrar som körs på samma klientkonfiguration.

Om inget annat anges i [Versionsinformation](latest-release.md) måste dessutom klientkonsolen använda **samma version** som serverinstansen.

Om du vill att implementeringen ska vara aktuell bör du läsa sidorna om de [inaktuella och borttagna funktionerna](../../rn/using/deprecated-features.md) samt [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md) för varje ny version.

## Uppgraderingprocess{#process-upgrade}

Kontakta Adobes kundtjänst för att få din miljö uppgraderad om du är värdbaserad-, Managed Services- eller hybridkund.

Som lokal kund kan du utföra uppgraderingen. Du gör detta genom att [hämta den senaste stabila versionen (GA)](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) och uppgradera alla dina miljöer.

Du hittar mer information om [uppgraderingsprocessen](../../production/using/build-upgrade.md) i [vanliga frågor och svar om versionsuppgradering](../../platform/using/faq-build-upgrade.md).

## Årlig uppgradering {#yearly-upgrade}

Adobe strävar efter att ge dig bästa möjliga upplevelse och värde genom våra programvarulösningar. Organisationen vill säkerställa att du har tillgång till de senaste versionerna av relaterad teknik som våra lösningar utnyttjar för att utföra sina uppgifter.

Adobe Campaign Classic använder en rad olika teknologier för att leverera värde. Den här kombinationen av tekniker kräver att du regelbundet uppgraderar dina instanser av Campaign Classic för att säkerställa att de senaste versionerna används, så att de kan leverera överlägsen säkerhet, stabilitet och prestanda.

Som värdbaserad användare drar du automatiskt nytta av uppgraderingen med den senaste GA-versionen, utan någon åtgärd. Läs mer i Vanliga frågor och svar nedan.

### Varför behöver min organisation den här uppgraderingen?

Adobe meddelar dig direkt om du är en värdbaserad kund och vi har identifierat att du behöver uppgradera en eller flera av teknikerna för Campaign Classic, samt om en uppgradering av din infrastruktur till den nuvarande versionen (från till exempel v7.2.1 till v7.3.3) och/eller version (från till exempel v7 till v8) behövs.

Som en lokal- eller hybridkund som kör en äldre version uppmuntrar Adobe dig att gå över till den senaste stabila versionen (GA).

Det här säkerställer att ditt konto är säkert mot sårbarheter samt använder uppdaterad prestandateknik. Den här uppgraderingen konfigurerar också ditt konto för enklare och regelbundna uppgraderingar i framtiden, som kräver mindre manuellt arbete och färre åtgärder.

### Hur ser uppgraderingen ut och när släpps den?

Adobe-teamet leder och vägleder din organisation genom den här resan.

Vi har organiserat ett team med dedikerade kundtjänstrepresentanter, produktchefer, ingenjörer och TechOps-specialister samt produktkonsulter för att hjälpa till och säkerställa att upplevelsen är smidig.

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
    <li>Förbättringar av hela teknikstacken i Campaign Classic märks på både marknadsförings- och IT-avdelningen i organisationen.</li>
    </ul>
  </td>

<td>
      <img alt="Builduppgradering" src="assets/do-not-localize/upgrades.png" />
    <div>
    <strong>Enklare uppgraderingar</strong>
    </a>
    </div>
    <ul>
    <li>Arbetet och komplexiteten med att uppgradera din Campaign Classic-instans ökar med avståndet mellan två versioner.</li>
    <li>Ju längre organisationen väntar, desto mer komplicerad blir uppgraderingen (och desto fler sårbarheter utsätts du för).</li>
    <li>Regelbundna uppdateringar minskar längden på driftstoppen för att uppgradera och minskar risken för regression.</li>
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
