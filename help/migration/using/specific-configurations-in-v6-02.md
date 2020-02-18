---
title: Specifika konfigurationer i v6.02
seo-title: Specifika konfigurationer i v6.02
description: Specifika konfigurationer i v6.02
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Specifika konfigurationer i v6.02{#specific-configurations-in-v6-02}

I följande avsnitt beskrivs den ytterligare konfiguration som krävs vid migrering från v6.02. Du bör även konfigurera inställningarna som anges i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

## Webbprogram {#web-applications}

Om du migrerar från v6.02 kan felloggar för webbprogram av översiktstyp visas. Exempel på felmeddelanden:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

Dessa webbprogram använde SQLData och är inte kompatibla med v7 på grund av högre säkerhet. Dessa fel leder till ett migreringsfel.

Om du inte använde dessa webbprogram kör du följande rensningsskript och kör efteruppgraderingen igen:

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

Om du har ändrat dessa webbprogram och vill fortsätta använda dem i v7 måste du aktivera alternativet **allowSQLInjection** i dina olika säkerhetszoner och starta om efteruppgraderingen. Mer information finns i avsnittet [SQLData](../../migration/using/general-configurations.md#sqldata) .

## Användarvänlighet: Hemsida och navigering {#user-friendliness--home-page-and-navigation}

>[!IMPORTANT]
>
>Om du vill fortsätta använda webbprogram av översiktstyp v6.02 måste du aktivera alternativet **allowSQLInjection** i dina olika säkerhetszoner innan du utför efteruppgraderingen. Se [webbprogrammen](#web-applications).

Efter en migrering från version 6.02 visas inte längre hemsidan för Adobe Campaign v6.02, men den är fortfarande tillgänglig och kompatibel med Adobe Campaign v7.

Om du vill fortsätta använda v6.02-startsidan måste du installera ett kompatibilitetspaket efter migreringen.

Om du vill göra det importerar du kompatibilitetspaketet:

Klicka på **[!UICONTROL Tools > Advanced > Import package]** och välj paketet **campaignMigration.xml** i **`\nl\datakit\nms\[Your language]\package\optional`**.

Om du vill tillåta åtkomst till gränssnittet av typen v6.02 Web Application måste **konfigurationsalternativet sessionTokenOnly** -server aktiveras i **filen serverConf.xml** :

```
sessionTokenOnly="true"
```

Det här alternativet ändrar säkerhetsnivåerna för att säkerställa gränssnittskompatibiliteten.

När paketet har installerats ersätts hemsidan för Adobe Campaign v7 av din gamla v6.02-hemsida, som är komplett med de allmänna konfigurationerna från v7 (banner för blå hemsida).

![](assets/dashboards.png)

Alla länkar på den här hemsidan länkar till v7-skärmar förutom listorna (**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]** osv.) som länkar till v6.02-översikten (webbprogram).

![](assets/dashboards2.png)

Om du vill lägga till ytterligare en översikt som konfigurerats i v6.02 måste du lägga till den på startsidan från instrumentpanelen. (**[!UICONTROL Administration > Access management > Dashboard]**).

>[!NOTE]
>
>Kom ihåg att koppla från och koppla sedan konsolen igen för att registrera ändringarna.

## Meddelandecenter {#message-center}

Efter migrering av en kontrollinstans i Message Center måste du publicera om transaktionsmeddelandemallarna för att de ska fungera.

I v7 har namnen på transaktionsmeddelandemallar för körningsinstanser ändrats. De prefixeras för närvarande av det operatörsnamn som motsvarar kontrollinstansen som de skapas i, till exempel **control1_template1_rt** (där **control1** är operatorns namn). Om du har ett stort antal mallar rekommenderar vi att du tar bort gamla mallar på kontrollinstanser.
