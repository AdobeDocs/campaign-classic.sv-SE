---
product: campaign
title: Konfigurera din plattform
description: Konfigurera din plattform
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 1%

---

# Konfigurera din plattform{#configuring-your-platform}

Vissa större förändringar i Adobe Campaign v7 kräver en konfiguration för att den ska fungera effektivt. Dessa parametrar kan vara nödvändiga före eller efter migrering. De berörda ändringarna och deras konfigurationsläge visas i det här avsnittet.

Under migreringen återskapas tabellen **NmsRecipient** från schemadefinitionen. Alla ändringar som görs i SQL-strukturen för den här tabellen utanför Adobe Campaign går förlorade.

Exempelelement att kontrollera:

* Om du har lagt till en kolumn (eller ett index) i tabellen **NmsRecipient**, men inte har detaljerat den i schemat, sparas inte den här kolumnen.
* Attributet **tabellutrymme** tar tillbaka sina värden som standard, det vill säga de som definieras i distributionsguiden.
* Om du har lagt till en referensvy i NmsRecipient-tabellen måste du ta bort den innan du migrerar.

Denna varning gäller även användare av Oraclet: Om du har lagt till alternativet **usetimestamptz:1** under en efteruppgradering (se [Tidszoner](../../migration/using/general-configurations.md#time-zones)), återskapas alla tabeller som innehåller minst ett **datum+tid**-fält.

## Före migreringen {#before-the-migration}

När du migrerar till Adobe Campaign v7 måste följande element konfigureras. Dessa element måste åtgärdas innan du startar **postupgrade**.

* Tidszoner

   Under en migrering från en v5.11-plattform måste du ange vilken tidszon som ska användas under efteruppgraderingen.

   Om du vill använda läget &quot;multi-timezone&quot; läser du avsnittet [Tidszoner](../../migration/using/general-configurations.md#time-zones).

   Om du använder Oracle som databas kontrollerar du att Oraclets tidszonsfiler har synkroniserats korrekt mellan programservern och databasservern. Mer information finns i avsnittet [Oracle](../../migration/using/general-configurations.md#oracle).

* Säkerhetszoner

   Av säkerhetsskäl är Adobe Campaign-plattformen inte längre tillgänglig som standard: du måste konfigurera säkerhetszonerna, vilket kräver att du samlar in användarens IP-adresser innan migreringen.

   Mer information finns i avsnittet [Säkerhet](../../migration/using/general-configurations.md#security).

* Syntax

   Vissa syntaxer i JavaScript kan accepteras i version 5.11 och 6.02 och inte längre accepteras i version 7 på grund av att en ny tolk används. Mer information finns i avsnittet [JavaScript](../../migration/using/general-configurations.md#javascript).

   På samma sätt introduceras en ny syntax i Adobe Campaign v7 som ersätter den SQLData-baserade syntaxen. Om du använder kodelement med den här syntaxen måste du anpassa dem. Mer information finns i avsnittet [SQLData](../../migration/using/general-configurations.md#sqldata).

* Lösenord

   Du måste konfigurera **Admin** och **interna** lösenord. Mer information finns i avsnittet [Användarlösenord](../../migration/using/before-starting-migration.md#user-passwords).

* Trädstruktur

   Om du migrerar från en v5.11-plattform måste du ordna om trädstrukturmapparna enligt Adobe Campaign v6-standarderna. Mer information finns i avsnittet [Adobe Campaign v7-trädstruktur](../../migration/using/specific-configurations-in-v5-11.md#campaign-vseven-tree-structure).

* Interaktion

   Om du använder **Interaktion** måste du ta bort alla 6.02 schemareferenser som inte längre finns i v7. Mer information finns i avsnittet [Interaktion](../../migration/using/general-configurations.md#interaction).

## Efter migreringen {#after-the-migration}

När du har kört **postupgrade** måste följande element beaktas och motsvarande konfigurationer utföras.

* Spegla sidor

   Spegelsidans anpassningsblock har ändrats med v6.x. Den här nya versionen förbättrar säkerheten vid åtkomst av dessa sidor.

   Om du använde v5-anpassningsblocket i dina meddelanden kommer speglingssidan inte att visas. Adobe rekommenderar starkt att du använder det nya anpassningsblocket när du infogar en spegelsida i dina meddelanden.

   Som en tillfällig lösning (och eftersom spegelsidorna fortfarande är aktiva) kan du återgå till det gamla personaliseringsblocket för att undvika det här problemet genom att ändra alternativet **[!UICONTROL XtkAcceptOldPasswords]** och ställa in det på **[!UICONTROL 1]**. Detta påverkar inte användningen av det nya v6.x-anpassningsblocket.

* Syntax

   Om du får problem med syntaxen under efteruppgraderingen måste du tillfälligt aktivera alternativet **allowSQLInjection** i **serverConf.xml**-filen, eftersom det ger dig tid att skriva om koden. När koden har anpassats måste du se till att återaktivera säkerheten. Mer information finns i avsnittet [SQLData](../../migration/using/general-configurations.md#sqldata).

* Konflikter

   Migreringen utförs efter uppgraderingen och konflikter kan uppstå i rapporter, formulär eller webbprogram. Konflikterna kan lösas från konsolen.

   Se avsnittet [Konflikter](../../migration/using/general-configurations.md#conflicts).

* Tomcat

   Om du har anpassat installationsmappen kontrollerar du att den har uppdaterats korrekt efter migreringen. Mer information finns i avsnittet [Tomcat](../../migration/using/general-configurations.md#tomcat).

* Rapporter

   Alla färdiga rapporter använder för närvarande v6.x-renderingsmotorn. Om du har lagt till JavaScript-kod i rapporterna kan vissa element ändras.

   Läs avsnittet [Rapporter](../../migration/using/general-configurations.md#reports).

* Webbprogram

   Om du har problem med att ansluta till identifierade webbprogram efter uppgraderingen måste du aktivera alternativen **allowUserPassword** och **sessionTokenOnly** i **serverConf.xml**-filen. Kom ihåg att sedan inaktivera dessa två alternativ. Mer information finns i avsnittet [Identifierade webbprogram](../../migration/using/general-configurations.md#identified-web-applications).

   Beroende på vilken typ av webbprogram det är och hur de är konfigurerade måste du utföra ytterligare ändringar för att vara säker på att de fungerar som de ska.

   Se avsnittet [Webbprogram](../../migration/using/general-configurations.md#web-applications).

   Om du migrerar från en v5.11-plattform måste ytterligare konfigurationer utföras: Mer information finns i avsnittet [Webbprogram](../../migration/using/specific-configurations-in-v5-11.md#web-applications).

* Säkerhetszoner.

   Innan du startar servern måste du konfigurera säkerhetszonerna. Mer information finns i [det här avsnittet](../../installation/using/security-zones.md) och [Security](../../migration/using/general-configurations.md#security).

* Scheman

   I Red Hat kan du stöta på fel när du redigerar vissa scheman. Mer information finns i avsnittet [Red-Hat](../../migration/using/general-configurations.md#red-hat).

* Arbetsflöden

   Om du migrerar från en v5.11-plattform måste du styra körningskatalogen för arbetsflöden. Mer information finns i avsnittet [Arbetsflöden](../../migration/using/specific-configurations-in-v5-11.md#workflows).

* Spåra

   Om du migrerar från en v5.11-plattform måste du konfigurera spårningsläget. Mer information finns i avsnittet [Spårning](../../migration/using/specific-configurations-in-v5-11.md#tracking).

* Startsida

   Om du migrerar från en v6.02-plattform kan du definiera ytterligare parametrar för att hålla din gamla hemsida från v6.02. Mer information finns i [Användarvänlighet: Startsida och navigeringsavsnitt](../../migration/using/specific-configurations-in-v6-02.md#user-friendliness--home-page-and-navigation).

* Interaktion

   Om du använder **Interaktion** måste du justera alla parametrar efter migreringen. Mer information finns i avsnittet [Interaktion](../../migration/using/general-configurations.md#interaction).
