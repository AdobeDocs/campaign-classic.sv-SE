---
title: Migrera kampanjoperatorer till Adobe Identity Management System (IMS)
description: Lär dig hur du migrerar kampanjoperatorer till Adobe Identity Management System (IMS)
source-git-commit: 18166dd389847d6b844ed478e19c42e457abeb80
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 0%

---

# Migrera kampanjoperatorer till Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Som en del i arbetet med att stärka säkerhets- och autentiseringsprocessen rekommenderar Adobe Campaign att man migrerar slutanvändarens autentiseringsläge från den inbyggda autentiseringen av inloggnings-/lösenordsinformationen till Adobe Identity Management System (IMS). Alla operatorer ska implementera [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} för att ansluta till Campaign.

Observera att i Campaign v8 tillåts inte längre anslutning med användare/lösenord (dvs. inbyggd autentisering). **Adobe rekommenderar att du utför den här migreringen i Campaign v7.3.5 för att smidigt kunna migrera till Campaign v8.**

I den här artikeln beskrivs stegen som krävs för att migrera en teknisk operatör till ett tekniskt konto på Adobe Developer-konsolen.

## Vad har ändrats?{#move-to-ims-changes}

Med Campaign Classic kan alla vanliga användare redan ansluta till Adobe Campaign klientkonsol via Adobe ID via Adobe Identity Management System (IMS). Det finns dock fortfarande användar-/lösenordsanslutningar. Detta är inte längre tillåtet med Campaign v8.

Som en del av arbetet med att förstärka säkerhets- och autentiseringsprocessen anropar nu Adobe Campaign klientprogram Campaign-API:er direkt med IMS-token för tekniskt konto. Migrering för tekniska operatörer beskrivs i en särskild artikel på [den här sidan](ims-migration.md).

Den här ändringen gäller redan i Campaign Classic v7 och kommer att **obligatoriskt** för att gå över till Campaign v8.

## Påverkas du?{#migrate-ims-impacts}

Den här proceduren gäller alla Campaign-användare som inte redan ansluter till Campaign med sin Adobe ID.

Om operatörer i organisationen ansluter till Campaign-klientkonsolen med hjälp av sina inloggnings-/lösenord (dvs. inbyggd autentisering) påverkas du och bör migrera dessa operatorer till Adobe IMS enligt nedan.

Migrering till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} är en säkerhetsnödvändighet för att göra dina miljöer säkra och standardiserade, eftersom de flesta andra Adobe Experience Cloud-lösningar och program redan finns på IMS.

## Hur migrerar värdmiljöer och Managed Services-miljöer? {#ims-migration-procedure}

### Förhandskrav {#ims-migration-prerequisites}

Innan du startar migreringsprocessen måste du kontakta din Adobe Transition Manager (för Managed Services-kunder) eller Adobe kundtjänst (för andra värdkunder) så att Adobe tekniska team kan migrera dina befintliga Operator-grupper och namngivna rättigheter till Adobe Identity Management System (IMS).

### Viktiga steg {#ims-migration-steps}

Viktiga steg för migreringen visas nedan:

1. Adobe uppgraderar dina miljöer till Campaign v7.3.5.
1. Efter uppgraderingen kan du fortfarande skapa nya användare med båda metoderna, som systemspecifik användare eller med IMS.
1. Din interna Campaign-administratör måste lägga till unika e-postmeddelanden till alla inbyggda användare på Campaign-klientkonsolen och bekräfta för din Adobe-representant/kundtjänst när detta är klart.  Det här steget beskrivs i [det här avsnittet](#ims-migration-id).
1. Samarbeta med er Adobe-representant/kundtjänst för att säkra ett datum då Adobe kan genomföra automatiserad migrering för icke-tekniska användare (operatörer) och produktprofiler. Det här steget kräver ett timmars fönster utan driftstopp för någon av dina tjänster.
1. Din interna Campaign-administratör validerar dessa ändringar och godkänner dem. Efter den här migreringen får du inte längre skapa någon ytterligare operator som autentiseras med användarens inloggning och lösenord.

Du kan också migrera tekniska operatorer till Adobe Developer Console enligt informationen i [den här teknologin](ims-migration.md).

När migreringen är klar bekräftar du till din Adobe Transition Manager (för Managed Services-användare) eller till kundtjänst på Adobe (för värdkunder). Adobe markerar sedan migreringen som slutförd. Miljön är sedan säker och standardiserad.


## Hur migrerar hybridmiljöer och lokala miljöer? {#ims-migration-procedure-on-prem}

Viktiga steg för migreringen visas nedan:

1. Uppgradera era miljöer till Campaign v7.3.5.
1. Efter uppgraderingen kan du fortfarande skapa nya användare med båda metoderna, som systemspecifik användare eller med IMS.
1. Din interna Campaign-administratör måste konfigurera Adobe IMS enligt anvisningarna i [det här avsnittet](../../integrations/using/configuring-ims.md).
1. Lägg sedan till unika e-postmeddelanden till alla inbyggda användare på Campaign-klientkonsolen. Det här steget beskrivs i [det här avsnittet](#ims-migration-id).
1. Skapa användare och produktprofiler i Adobe Admin Console enligt [Kampanjdokumentation v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Aktivera **Anslut till Adobe ID** för alla operatorer.
1. Implementera Adobe IMS för din anslutning enligt informationen i [den här sidan](../../integrations/using/implementing-ims.md).

Du kan också migrera tekniska operatorer till Adobe Developer Console enligt informationen i [den här teknologin](ims-migration.md).


## Vanliga frågor och svar {#ims-migration-faq}

### När kan jag starta migreringen? {#ims-migration-start}

En rekommendation för migrering till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} är att uppgradera till Campaign Classic v7.3.5.

Du kan starta IMS-migrering på din scenmiljö när den har uppgraderats till Campaign Classic v7.3.5 och därefter planera för produktionsmiljön.

### Vad händer efter en uppgradering till Campaign Classic v7.3.5? {#ims-migration-after-upgrade}

När du har uppgraderat till Campaign Classic v7.3.5 kan du starta övergången till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

### När är migreringen klar? {#ims-migration-end}

När migreringen av slutanvändare och den tekniska migreringen till Adobe Identity Management System (IMS) är klar måste du kontakta din Adobe-representant/kundsupport så att Adobe kan ange att migreringen är slutförd.

### Hur skapar man användare efter migreringen? {#ims-migration-native}

Adobe rekommenderar att du bara skapar IMS-användare efter att du uppgraderat till Campaign Classic v7.3.5.

Som Campaign-administratör kan du bevilja behörigheter till användare i din organisation via Adobe Admin Console och Campaign Client Console. Användare loggar in på Adobe Campaign med sin Adobe ID. Lär dig hur du ställer in behörigheter med IMS i [Kampanjdokumentation v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.

### Hur lägger jag till e-post för befintliga användare? {#ims-migration-id}

Som kampanjadministratör måste du lägga till e-post-ID:n till alla inbyggda användare från klientkonsolen. Gör så här:

1. Anslut till klientkonsolen och bläddra till **Administration > Åtkomsthantering > Operatorer**.
1. Välj den operator som ska uppdateras i operatorlistan.
1. Ange e-postadressen till operatorn i dialogrutan **Kontaktpunkter** -delen i operatorformuläret.
1. Spara ändringarna.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Hur loggar jag in på Campaign via IMS? {#ims-migration-log}

Lär dig hur du ansluter till Campaign med din Adobe ID i [det här avsnittet](../../integrations/using/implementing-ims.md).

### Kommer det att bli några driftavbrott under den här migreringen? {#ims-migration-downtime}

För kunder som använder Hosted och Managed Services behöver Adobe ett timmars fönster utan driftstopp för någon av dina instanser (arbetsflöden osv.) för att slutföra migreringen (migrera användare och produktprofiler).

Under den här tidsramen måste alla Campaign-användare logga ut och logga in igen med sin Adobe ID när migreringen till IMS är klar.

Adobe rekommenderar starkt att alla användare loggas ut under migreringsfönstret.

### Användare i min organisation använder redan IMS, behöver jag ändå utföra IMS-migrering?{#ims-migration-needed}

Det finns två aspekter av migreringen: migrering av slutanvändare (plus produktprofiler) och migrering av tekniska användare (används i API:er i din anpassade kod).

Om alla användare (kampanjansvariga) använder IMS måste du ändå kontakta din Adobe-representant/kundsupport för att planera migreringen av produktprofiler. Du måste också migrera tekniska användare som du kan ha använt i anpassad kod. Läs mer i [den här sidan](ims-migration.md).

## Användbara länkar {#ims-useful-links}

* [Migrering av tekniska användare till Adobe Developer Console](ims-migration.md)
* [Versionsinformation för Adobe Campaign v8](../../rn/using/latest-release.md)
* [Vad är Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
