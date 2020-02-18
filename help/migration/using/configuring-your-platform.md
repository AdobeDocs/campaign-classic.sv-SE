---
title: Konfigurera din plattform
seo-title: Konfigurera din plattform
description: Konfigurera din plattform
seo-description: null
page-status-flag: never-activated
uuid: e6255e4b-c9c8-4ac9-9ee3-aaa4dc9e5ecf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 4d2e765b-750b-457f-ad55-8bd6faaa86af
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 40391fbea53757decb48fd937f5e74e8ba6fb207

---


# Konfigurera din plattform{#configuring-your-platform}

Vissa större ändringar i Adobe Campaign v7 kräver en konfiguration för att den ska fungera effektivt. Dessa parametrar kan vara nödvändiga före eller efter migrering. De berörda ändringarna och deras konfigurationsläge visas i det här avsnittet.

Under migreringen återskapas **NmsRecipient** -tabellen från schemadefinitionen. Alla ändringar som görs i SQL-strukturen för den här tabellen utanför Adobe Campaign går förlorade.

Exempelelement att kontrollera:

* Om du har lagt till en kolumn (eller ett index) i **NmsRecipient** -tabellen men inte har detaljerat den i schemat, sparas inte den här kolumnen.
* Attributet för **tabellutrymme** återtar sina värden som standard, det vill säga de som definieras i distributionsguiden.
* Om du har lagt till en referensvy i NmsRecipient-tabellen måste du ta bort den innan du migrerar.

Den här varningen gäller även Oracle-användare: Om du har lagt till alternativet **usetimestamptz:1** under en efteruppgradering (se [Tidszoner](../../migration/using/general-configurations.md#time-zones)), återskapas alla tabeller som innehåller minst ett **datum+tid** -fält.

## Före migreringen {#before-the-migration}

När du migrerar till Adobe Campaign v7 måste följande element konfigureras. Dessa element måste åtgärdas innan **efteruppgraderingen** startas.

* Tidszoner

   Under en migrering från en v5.11-plattform måste du ange vilken tidszon som ska användas under efteruppgraderingen.

   Om du vill använda läget &quot;multitidszon&quot;, se avsnittet [Tidszoner](../../migration/using/general-configurations.md#time-zones) .

   Om du använder Oracle som en databas kontrollerar du att Oracles tidszonsfiler har synkroniserats korrekt mellan programservern och databasservern. Mer information finns i avsnittet [Oracle](../../migration/using/general-configurations.md#oracle) .

* Säkerhetszoner

   Av säkerhetsskäl är Adobe Campaign-plattformen inte längre tillgänglig som standard: du måste konfigurera säkerhetszonerna, vilket kräver att du samlar in användarens IP-adresser innan migreringen.

   Mer information finns i avsnittet [Säkerhet](../../migration/using/general-configurations.md#security) .

* Syntax

   Vissa syntaxer i JavaScript kan accepteras i version 5.11 och 6.02 och inte längre accepteras i version 7 på grund av att en ny tolk används. Mer information finns i [JavaScript](../../migration/using/general-configurations.md#javascript) -avsnittet.

   På samma sätt introduceras en ny syntax i Adobe Campaign v7 som ersätter den SQLData-baserade syntaxen. Om du använder kodelement med den här syntaxen måste du anpassa dem. Mer information finns i avsnittet [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Lösenord

   Du måste konfigurera **administratörslösenordet** och det **interna** lösenordet. Mer information finns i avsnittet [Användarlösenord](../../migration/using/before-starting-migration.md#user-passwords) .

* Trädstruktur

   Om du migrerar från en v5.11-plattform måste du ordna om trädstrukturmapparna enligt Adobe Campaign v6-standarderna. Mer information finns i [trädstrukturavsnittet](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure) Adobe Campaign v7.

* Interaktion

   Om du använder **Interaktion** måste du ta bort alla 6.02 schemareferenser som inte längre finns i v7. Mer information finns i avsnittet [Interaktion](../../migration/using/general-configurations.md#interaction) .

## Efter migreringen {#after-the-migration}

När du har kört **efteruppgraderingen** måste följande element beaktas och motsvarande konfigurationer utföras.

* Spegla sidor

   Spegelsidans anpassningsblock har ändrats med v6.x. Den här nya versionen förbättrar säkerheten vid åtkomst av dessa sidor.

   Om du använde v5-anpassningsblocket i dina meddelanden kommer speglingssidan inte att visas. Adobe rekommenderar att du använder det nya personaliseringsblocket när du infogar en spegelsida i dina meddelanden.

   Som en tillfällig lösning (och eftersom spegelsidorna fortfarande är aktiva) kan du återgå till det gamla personaliseringsblocket för att undvika det här problemet genom att ändra alternativet **[!UICONTROL XtkAcceptOldPasswords]** och ange det som **[!UICONTROL 1]**. Detta påverkar inte användningen av det nya v6.x-anpassningsblocket.

* Syntax

   Om du får problem med syntaxen under efteruppgraderingen måste du tillfälligt aktivera alternativet **allowSQLInjection** i **serverConf.xml** -filen eftersom det ger dig tid att skriva om koden. När koden har anpassats måste du se till att återaktivera säkerheten. Mer information finns i avsnittet [SQLData](../../migration/using/general-configurations.md#sqldata) .

* Konflikter

   Migreringen utförs efter uppgraderingen och konflikter kan uppstå i rapporter, formulär eller webbprogram. Konflikterna kan lösas från konsolen.

   Se avsnittet [Konflikter](../../migration/using/general-configurations.md#conflicts) .

* Tomcat

   Om du har anpassat installationsmappen kontrollerar du att den har uppdaterats korrekt efter migreringen. Mer information finns i avsnittet [Tomcat](../../migration/using/general-configurations.md#tomcat) .

* Rapporter

   Alla färdiga rapporter använder för närvarande v6.x-renderingsmotorn. Om du har lagt till JavaScript-kod i rapporterna kan vissa element ändras.

   Se avsnittet [Rapporter](../../migration/using/general-configurations.md#reports) .

* Webbprogram

   Om du har problem med att ansluta till dina identifierade webbprogram efter uppgraderingen måste du aktivera alternativen **allowUserPassword** och **sessionTokenOnly** i **filen serverConf.xml** . Kom ihåg att sedan inaktivera dessa två alternativ. Mer information finns i avsnittet [Identifierade webbprogram](../../migration/using/general-configurations.md#identified-web-applications) .

   Beroende på vilken typ av webbprogram det är och hur de är konfigurerade måste du utföra ytterligare ändringar för att vara säker på att de fungerar som de ska.

   Se avsnittet [Webbprogram](../../migration/using/general-configurations.md#web-applications) .

   Om du migrerar från en v5.11-plattform måste ytterligare konfigurationer utföras: Mer information finns i avsnittet [Webbprogram](../../migration/using/specific-configurations-in-v5-11.md#web-applications) .

* Säkerhetszoner.

   Innan du startar servern måste du konfigurera säkerhetszonerna. Mer information finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#defining-security-zones) och i avsnittet [Säkerhet](../../migration/using/general-configurations.md#security) .

* Scheman

   I Red Hat kan du stöta på fel när du redigerar vissa scheman. Mer information finns i avsnittet [Röd-Hatt](../../migration/using/general-configurations.md#red-hat) .

* Arbetsflöden

   Om du migrerar från en v5.11-plattform måste du styra körningskatalogen för arbetsflöden. Mer information finns i avsnittet [Arbetsflöden](../../migration/using/specific-configurations-in-v5-11.md#workflows) .

* Spårning

   Om du migrerar från en v5.11-plattform måste du konfigurera spårningsläget. Mer information finns i avsnittet [Spärra/knip](../../migration/using/specific-configurations-in-v5-11.md#tracking) .

* Startsida

   Om du migrerar från en v6.02-plattform kan du definiera ytterligare parametrar för att hålla din gamla hemsida från v6.02. Mer information finns i [Användarvänlighet: Hemsida och navigeringsavsnitt](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation) .

* Interaktion

   Om du använder **Interaktion** måste du justera alla parametrar efter migreringen. Mer information finns i avsnittet [Interaktion](../../migration/using/general-configurations.md#interaction) .

