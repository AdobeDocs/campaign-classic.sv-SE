---
title: Duplicera miljöer
seo-title: Duplicera miljöer
description: Duplicera miljöer
seo-description: null
page-status-flag: never-activated
uuid: b8fb8083-e3ec-4b1c-9449-73ac03508d89
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 9f7118f4-aef0-469c-bbe1-b62bed674faa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cb44d439c6866d94f8e1201575ab3d3094d6ad79
workflow-type: tm+mt
source-wordcount: '1291'
ht-degree: 0%

---


# Duplicera miljöer{#duplicating-environments}

## Introduktion {#introduction}

### Översikt {#overview}

>[!CAUTION]
>
>Om du inte har åtkomst till servern och databasen (värdmiljöer) kan du inte utföra de procedurer som beskrivs nedan. Kontakta Adobe.

För att använda Adobe Campaign måste du installera och konfigurera en eller flera miljöer: utveckling, testning, förproduktion, produktion osv.

Varje miljö innehåller en Adobe Campaign-instans och varje Adobe Campaign-instans är länkad till en eller flera databaser. Programservern kan köra en eller flera processer: nästan alla dessa har direktåtkomst till instansdatabasen.

I det här avsnittet beskrivs de processer som ska användas för att duplicera en Adobe Campaign-miljö, dvs. för att återställa en källmiljö till en målmiljö, vilket resulterar i två identiska arbetsmiljöer.

Gör så här:

1. Skapa en kopia av databaserna för alla instanser i källmiljön,
1. Återställ dessa kopior i alla instanser av målmiljön,
1. Kör **nms:ezeInstance.js** -autentiseringsskriptet i målmiljön innan du startar det.

   Den här processen påverkar inte servrarna och deras konfiguration.

   >[!NOTE]
   >
   >När det gäller Adobe Campaign kombineras åtgärder med en **autentisering** som gör att du kan stoppa alla processer som interagerar med utsidan: loggar, spårning, leveranser, kampanjarbetsflöden osv.\
   >Detta steg är nödvändigt för att undvika att leverera meddelanden flera gånger (en gång från den nominella miljön och en gång från den duplicerade miljön).

   >[!CAUTION]
   >
   >En miljö kan innehålla flera instanser. Varje instans av Adobe Campaign omfattas av ett licensavtal. Se licensavtalet för att se hur många miljöer du kan ha.\
   >Med proceduren nedan kan du överföra en miljö utan att det påverkar antalet miljöer och instanser som du har installerat.

### Innan du börjar {#before-you-start}

>[!CAUTION]
>
>Vi rekommenderar att du kör en fullständig säkerhetskopiering av databaserna för alla instanser av käll- och målmiljöer innan du påbörjar överföringsprocessen. Om ett problem uppstår kan du återställa säkerhetskopiorna och återgå till den ursprungliga konfigurationen.

För att den här processen ska fungera måste käll- och målmiljöerna ha samma antal instanser, samma syfte (marknadsinstans, leveransinstans) och liknande konfigurationer. Den tekniska konfigurationen måste uppfylla programvarukraven. Samma komponenter måste installeras i båda miljöerna.

## Implementering {#implementation}

### Överföringsförfarande {#transfer-procedure}

I det här avsnittet får du hjälp med att förstå hur du överför en källmiljö till en målmiljö via en fallstudie: Vi har som mål att återställa en produktionsmiljö (**prod** instance) till en utvecklingsmiljö (**dev** instance) så att den fungerar i ett sammanhang som ligger så nära live-plattformen som möjligt.

Följande steg måste utföras med stor noggrannhet: vissa processer kanske fortfarande pågår när källmiljöns databaser kopieras. Verifiering (steg 3 nedan) förhindrar att meddelanden skickas två gånger och upprätthåller datakonsekvensen.

>[!CAUTION]
>
>* Följande procedur gäller för PostgreSQL-språk. Om SQL-språket är ett annat (till exempel Oracle) måste SQL-frågorna anpassas.
>* Nedanstående kommandon gäller för en **prod** -instans och en **dev** -instans under PostgreSQL.
>



### Steg 1 - Säkerhetskopiera källmiljöns (prod) data {#step-1---make-a-backup-of-the-source-environment--prod--data}

Kopiera databaserna

Börja med att kopiera alla källmiljödatabaser. Åtgärden beror på databasmotorn och är databasadministratörens ansvar.

Under PostgreSQL är kommandot:

```
pg_dump mydatabase > mydatabase.sql
```

### Steg 2 - Exportera målmiljökonfigurationen (dev) {#step-2---export-the-target-environment-configuration--dev-}

De flesta konfigurationselement är olika för olika miljöer: externa konton (mellanleverantörer, routning osv.), tekniska alternativ (plattformsnamn, DatabaseId, e-postadresser och standard-URL:er osv.).

Innan du sparar källdatabasen i måldatabasen måste du exportera dev-konfigurationen (target environment). Det gör du genom att exportera innehållet i de här två tabellerna: **xtkoption** och **nmsextaccount**.

Med den här exporten kan du behålla dev-konfigurationen och bara uppdatera dev-data (arbetsflöden, mallar, webbprogram, mottagare osv.).

Det gör du genom att utföra en paketexport för följande två element:

* Exportera tabellen **xtk:option** till en &#39;options_dev.xml&#39;-fil, utan posterna med följande interna namn: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; och &#39;NmsBroadcast_RegexRules&#39;.
* I en &#39;extaccount_dev.xml&#39;-fil exporterar du tabellen **nms:extAccount** för alla poster vars ID är 0 (@id &lt;> 0).

Kontrollera att antalet exporterade alternativ/konton är lika med antalet rader som ska exporteras i varje fil.

>[!NOTE]
>
>Antalet rader som ska exporteras i en paketexport är 1 000 rader. Om antalet alternativ eller externa konton är fler än 1 000 måste du utföra flera exporter.
> 
>For more information, refer to [this section](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>När nmsextaccount-tabellen exporteras exporteras inte lösenord som är kopplade till externa konton (till exempel lösenord för MID-källkod, körning av meddelandecenter, SMPP, IMS och andra externa konton). Kontrollera att du har tillgång till rätt lösenord i förväg, eftersom de kan behöva anges igen när de externa kontona har importerats tillbaka till miljön.

### Steg 3 - Stoppa målmiljön (dev) {#step-3---stop-the-target-environment--dev-}

Ni måste stoppa Adobe Campaign-processerna på alla målmiljöservrar. Den här åtgärden beror på operativsystemet.

Du kan stoppa alla processer, eller bara de som skriver till databasen.

Om du vill stoppa alla processer använder du följande kommandon:

* I Windows:

   ```
   net stop nlserver6
   ```

* I Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Använd följande kommando för att kontrollera att alla processer har stoppats:

```
nlserver pdump
```

>[!NOTE]
>
>I Windows kan **webmdl** -processen fortfarande vara aktiv utan att påverka andra åtgärder.

Du kan även kontrollera att inga systemprocesser fortfarande körs.

Gör så här:

* I Windows: öppna **Aktivitetshanteraren** och kontrollera att det inte finns några **nlserver.exe** -processer.
* I Linux: kör **ps aux | grep nlserver** command och kontrollera att det inte finns några **nlserver** -processer.

### Steg 4 - Återställ databaserna i målmiljön (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Använd följande kommando för att återställa källdatabaserna i målmiljön:

```
psql mydatabase < mydatabase.sql
```

### Steg 5 - Skapa målmiljön automatiskt (dev) {#step-5---cauterize-the-target-environment--dev-}

För att undvika felfunktioner får de processer som är länkade till leverans och körning av arbetsflöden inte köras automatiskt när målmiljön aktiveras.

Kör följande kommando för att göra detta:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Steg 6 - Kontrollera auktorisering {#step-6---check-cauterization}

1. Kontrollera att den enda leveransen är den vars ID är inställt på 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Kontrollera att leveransstatusuppdateringen är korrekt:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Kontrollera att statusuppdateringen för arbetsflödet är korrekt:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Steg 7 - Starta om webbprocessen för målmiljön (dev) {#step-7---restart-the-target-environment-web-process--dev-}

Starta om Adobe Campaign-processerna för alla servrar i målmiljön.

>[!NOTE]
>
>Innan du startar om Adobe Campaign i **utvecklingsmiljön** kan du göra ytterligare en säkerhetsåtgärd: starta endast **webbmodulen** .
>  
>Om du vill göra det redigerar du instansens konfigurationsfil (**config-dev.xml**) och lägger sedan till tecknet&quot;_&quot; före alternativen autoStart=&quot;true&quot; för varje modul (mta, stat osv.).

Kör följande kommando för att starta webbprocessen:

```
nlserver start web
```

Använd följande kommando för att kontrollera att bara webbprocessen har startat:

```
nlserver pdump
```

Kontrollera åtkomsten till klientkonsolfunktionerna.

### Steg 8 - Importalternativ och externa konton i målmiljön (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!CAUTION]
>
>Det är bara webbprocessen som ska startas i det här steget. Om så inte är fallet ska du stoppa andra processer som körs innan du fortsätter

Kontrollera framför allt värdena för flera rader i filerna innan du importerar (till exempel: &#39;NmsTracking_Pointer&#39; för alternativtabellen och leverans- eller mittleverantörskonton för den externa kontotabellen)

Så här importerar du konfigurationen från målmiljödatabasen (dev):

1. Öppna administrationskonsolen för databasen och rensa de externa konton (tabell nms:extAccount) vars ID är 0 (@id &lt;> 0).
1. I Adobe Campaign-konsolen importerar du det options_dev.xml-paket som tidigare skapats via importpaketsfunktionen.

   Kontrollera att alternativen verkligen har uppdaterats i **[!UICONTROL Administration > Platform > Options]** noden.

1. I Adobe Campaign-konsolen importerar du den extaccount_dev.xml som tidigare skapats via importpaketsfunktionen

   Kontrollera att externa databaser verkligen har importerats i **[!UICONTROL Administration > Platform > External accounts]** .

### Steg 9 - Starta om alla processer och ändra användare (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Använd följande kommandon för att starta Adobe Campaign-processerna:

* I Windows:

   ```
   net start nlserver6
   ```

* I Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Använd följande kommando för att kontrollera att processerna har startats:

```
nlserver pdump
```

Byt användare för att hitta de användare som redan fanns på dev-plattformen.
