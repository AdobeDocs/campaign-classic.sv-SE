---
product: campaign
title: Kom igång med uppgraderingar
description: Lär dig de viktigaste stegen för att uppgradera till en ny version
feature: Monitoring, Upgrade
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '2324'
ht-degree: 0%

---

# Utföra en bygguppgradering{#performing-a-build-upgrade}



I det här avsnittet får du en detaljerad genomgång av uppgraderingsprocessen och hur du identifierar och löser konflikter.

Uppgraderingen av bygget måste utföras med försiktighet, dess effekter måste beaktas fullt ut i förväg och förfarandet måste avslutas med en hög nivå av disciplin. För att uppgraderingen ska lyckas måste du se till att endast expertanvändare utför de steg som beskrivs nedan. Dessutom rekommenderar vi att du kontaktar [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) innan du påbörjar en uppgradering.

Följande krav krävs:

* Förståelse för Campaign-arkitekturen
* Kunskap om system och serversidor
* Administrativa rättigheter och behörigheter

Mer information finns i följande avsnitt: [Uppdatera Adobe Campaign](../../production/using/upgrading.md), [Migrerar till en ny version](../../migration/using/about-migration.md).

För värdbaserade och hybridinstanser måste du begära en uppgradering till Adobe Technical Operations Team. Mer information finns i avsnittet Frågor och svar längst ned på den här sidan. Se även [frågor och svar om uppgradering av bygget](../../platform/using/faq-build-upgrade.md).

## Förbered uppgraderingen

![](assets/do-not-localize/icon_planification.png)

Innan du påbörjar uppgraderingen måste du utföra en fullständig förberedelse enligt beskrivningen nedan.
När systemet är klart för uppgradering tar en bygguppgradering **minst** 2 timmar.

Bygguppgraderingsprocessen kräver följande resurser:

* en Adobe-arkitekt - för att förstå databasstrukturerna (färdiga scheman och eventuella ytterligare scheman som lagts till, kampanjdesign och alla viktiga sökvägsfunktioner som måste startas och testas i en viss ordning).
* en projektledare - Om bygguppgraderingen omfattar många olika instanser (produktion, testning, testning) och andra tredjepartsservrar och -program (databaser, SFTP-platser, meddelandetjänster), anses det vara en god praxis att ha en projektledare som koordinerar all testning.
* en Adobe Campaign-administratör - administratören känner till serverns konfiguration, inklusive men inte begränsat till: säkerhet, mapplayout, rapportering och import\export. Utför ingen bygguppgradering utan att administratören behöver göra det.
* en Adobe Campaign-operator (marknadsföringsanvändare) - en lyckad uppgradering förutsätter att användaren kan utföra sina dagliga uppgifter med framgång. Därför bör du alltid ta med minst en av dina dagliga operatorer när du testar de uppgraderade servrarna.

### Planering

Här är de viktigaste punkterna på hur du planerar en bygguppgradering:

1. Reservera minst 2 timmar för uppgraderingen.
1. Distribuera kontaktuppgifter för Adobe och kundpersonal.
1. För värdinstanser: Adobe och kundpersonal koordinerar tiden för uppgraderingen och vem som ska genomföra den.
1. För lokala instanser: kundpersonalen hanterar hela processen - om hjälp med testning av anpassade arbetsflöden och leveranslogik behövs bör konsulttjänster tas in.
1. Kontrollera vilken version av Adobe Campaign du vill uppgradera till i [versionsinformationen för Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Bekräfta innehavet av uppgraderingsfiler.

### Viktiga personer

Bygguppgraderingsprocessen kräver att följande personer deltar:

* Adobe-arkitekt: för hostade eller hybridarkitekturer måste arkitekten koordinera med Adobe Campaign Client Care.

* Projektledare:
   * för On Premise-installationer: kundens interna projektledare leder uppgraderingen och hanterar livscykeltester.

   * för värdbaserad installation: värdteamet samarbetar med Adobe Campaign Client Care-teamet och kunden för att samordna uppgraderingstidslinjen för alla instanser.

* Adobe Campaign Administrator:
   * för On Premise-installationer: administratören utför uppgraderingen.

   * för värdbaserade installationer: värdteamet utför uppgraderingen.

* Adobe Campaign operator\marknadsföringsanvändare: operatorn kör tester på instanser för utveckling, test och produktion.

### Förbered uppgraderingen av bygget

Innan du påbörjar uppgraderingen måste lokala kunder utföra följande förberedelser:

1. Se till att utvecklingsarbetet kan exporteras före uppgraderingen och exportera som paket.

1. Utför en fullständig säkerhetskopiering av databaserna för alla instanser av käll- och målmiljöerna.

1. Hämta den senaste versionen av [serverkonfigurationsfilen](../../installation/using/the-server-configuration-file.md).

1. [Hämta den senaste versionen](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html). [Läs mer](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=sv-SE).

Du måste också känna till alla [användbara kommandorader](../../installation/using/command-lines.md) innan du påbörjar en bygguppgradering:

* **nlserver pdump**: visar processer som körs
* **nlserver pdump -who**: visar aktiva klientsessioner
* **nlserver monitor -missing**: visar saknade egenskaper
* **nlserver start process@instance-name**: startar en process
* **nlserver stop process@instance-name**: stoppar en process
* **nlserver startar om process@instance-name**: startar om en process
* **ingen avstängning**: stoppar alla Campaign-processer
* **nlserver watchdog -svc**: startar övervakningsenheten (endast UNIX)

## Utför uppgraderingen

![](assets/do-not-localize/icon_process.png)

Procedurer nedan utförs endast av **lokala**-kunder. För värdkunder hanteras det av värdteamet. Nedan beskrivs hur du uppdaterar Adobe Campaign till en ny version.

### Duplicera miljön

Så här duplicerar du en Adobe Campaign-miljö för att återställa en källmiljö till en målmiljö, vilket ger två identiska arbetsmiljöer.

Gör så här:

1. Skapa en kopia av databaserna på alla instanser i källmiljön.

1. Återställ dessa kopior i alla instanser av målmiljön.

1. Kör autentiseringsskriptet **nms:ezeInstance.js** i målmiljön innan du startar det. Detta stoppar alla processer som interagerar med utsidan: loggar, spårning, leveranser, kampanjarbetsflöden osv.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Kontrollera auktorisering enligt följande:

   * Kontrollera att den enda leveransdelen är den som har ID inställt på **0**:

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * Kontrollera att leveransstatusuppdateringen är korrekt:

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * Kontrollera att statusuppdateringen för arbetsflödet är korrekt:

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### Stäng av tjänster

Om du vill ersätta alla filer med den nya versionen måste alla instanser av nlserverservice stängas.

1. Stäng av följande tjänster:

   * Webbtjänster (IIS): **iisreset /stop**
   * Adobe Campaign-tjänst: **net stop nlserver6**

   >[!NOTE]
   >
   >Kontrollera att omdirigeringsservern (webmdl) har stoppats så att filen nlsrvmod.dll som används av IIS kan ersättas med den nya versionen.
   >

1. Verifiera att inga aktiviteter är aktiva genom att köra kommandot **nlserver pdump**. Om det inte finns några uppgifter bör utdata likna följande:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Kontrollera att alla processer har stoppats i Aktivitetshanteraren.

### Uppgradera Adobe Campaign Server-programmet

1. Kör filen **Setup.exe**. Om du behöver hämta den här filen öppnar du [Hämtningscenter](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Välj installationsläge: **Uppdatera** eller **Reparera**.

1. Klicka på **Nästa**.

1. Klicka på **Slutför**: installationsprogrammet kopierar de nya filerna.

1. När åtgärden är klar klickar du på **Slutför**.

### Synkronisera resurser

1. Öppna kommandoraden.

1. Kör **nlserver config -postupgrade -allinstances** för att utföra följande:

   * Synkronisera resurser
   * Uppdatera scheman
   * Uppdatera databasen

   >[!NOTE]
   >
   >Den här åtgärden ska bara utföras en gång och endast på en nlserverweb-programserver.
   >

   Om du bara vill synkronisera en databas kör du följande kommando:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Kontrollera om synkroniseringen har genererat fel eller varningar.

### Starta om tjänster

Följande tjänster måste startas om:

* Webbtjänster (IIS): **issreset /start**
* Adobe Campaign-tjänst: **net start nlserver6**

### Klientkonsoluppdatering

Klientkonsolen måste finnas på samma version som serverinstansen.

Hämta och kopiera filen på den dator där Adobe Campaign programserver är installerad (nlserverweb):

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Nästa gång klientkonsolerna är anslutna visas ett fönster som informerar användarna om att det finns en ny uppdatering och som ger dem möjlighet att ladda ned och installera den.

### Specifika ytterligare uppgifter

Vissa konfigurationer kräver specifika ytterligare uppgifter för att kunna uppdateras till en ny version.

#### Transaktionsmeddelanden

När Transactional Messaging (Message Center) är aktiverat i Campaign-instansen måste du utföra följande steg för att uppgradera:

1. Uppdatera produktionsservern för Message Center till den valda versionen.
1. Kör efteruppgraderingsskripten.
1. Kör tester och se till att e-postmeddelanden tas emot via produktionsinstansen i meddelandecentret.
1. Uppgradera klienter och rensa cache.
1. Exportpaket:
   * Exportera paket med exportverktyget för klientpaket
   * Importera schemapaket
   * Koppla från och återansluta klient
   * Uppdatera databas
   * Koppla från och koppla från
   * Importera Admin-paket
   * Importera innehållspaket
   * Importera innehållshanteringspaket
   * Koppla från och koppla från
   * Genomför en snabb rimlighetskontroll av arbetsflöden

1. Publish Message Center-mallar för att säkerställa att gränssnittet mellan servrar och Message Center-instansen fungerar.
1. Kör tester för att se till att e-postmeddelanden tas emot via produktionsinstansen i meddelandecentret.
1. Kör arbetsflödestester i produktionen för att säkerställa att leveranser tas emot.

#### Mid-sourcing

I en miljö med flera leverantörer behöver du utföra följande steg för att uppgradera:

1. Kontakta [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att koordinera uppgraderingen av MID-Source-servern.
1. Verifiera att versionen har uppdaterats genom att köra en testlänk. Exempel:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Servern för medelhög källkod måste alltid ha samma version (eller senare) som marknadsföringsservrarna.
>

## Vid konflikter

### Identifiera konflikter

Du måste kontrollera synkroniseringsresultatet. Den här proceduren utförs endast av lokala kunder. För värdkunder hanteras det av värdteamet. Det finns två sätt att visa synkroniseringsresultatet:

I kommandoradsgränssnittet materialiseras fel av en trippelkniv (>>>>) och synkroniseringen stoppas automatiskt. Varningar materialiseras av en dubbel skiftning &#39;>>&#39; och måste åtgärdas när synkroniseringen är klar. När uppgraderingen är klar visas en sammanfattning i kommandotolken. Den kan se ut så här:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Om varningen gäller en resurskonflikt måste användaren åtgärda den.

Filen **postupgrade_ServerVersionNumber_TimeOfPodumgrade.log** innehåller synkroniseringsresultatet. Den är som standard tillgänglig i följande katalog: **installationDirectory/var/`<instance-name>`/postupgrade**. Fel och varningar indikeras av fel- och varningsattributen.

### Analysera konflikter

**Hur hittas en konflikt?**

Konflikter kan hittas i postupgrade.log på den aktuella servern eller i Campaign-klientgränssnittet (Administration > Konfiguration > Pakethantering > Redigera konflikter).

Dokumentet med identifieraren&quot;stockOverview&quot; och typen&quot;nms:webApp&quot; är i konflikt med den nya versionen.

Om en konflikt hittas kontrollerar du om följande villkor matchar:

* Har objektet ändrats eller anpassats av kunden?
* Har objektet ändrats i produkten?

Om inget av dessa villkor gäller är detta falskt positivt. Om båda dessa villkor är uppfyllda har en verklig konflikt hittats.

**Har objektet ändrats av kunden?**

1. Identifiera objektet som är i konflikt.
1. Fråga kunden om de har ändrat objektet.
1. Är det något ovanligt med objektet?
1. Är det senast ändrade datumet angivet i objektets kod?
1. Undersök XML-koden från konflikten för att se om det finns &quot;_conflict&quot;-attribut. Ser det ut som en anpassning?

**Har objektet ändrats i den nya versionen?**

1. &quot;Vanliga misstänkta?&quot; Inbyggda webbprogram eller rapporter (t.ex. &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Sök i ändringsloggarna efter uppdateringar.
1. Fråga Adobe Campaign experter.
1. Utför en&quot;diff&quot; på koden.

### Lösa en konflikt

Använd följande process för att lösa konflikter:

1. Gå till **Administration > Konfiguration > Pakethantering > Redigera konflikter** i Adobe Campaign Utforskaren.

1. Markera den konflikt som du vill lösa i listan.
Det finns tre alternativ för att lösa konflikter: **Acceptera den nya versionen**, **Behåll den aktuella versionen**, **Sammanfoga koden (och deklarera som löst)**, **Ignorera konflikten (rekommenderas inte)**.

**När kan jag godkänna den nya versionen?**

* Om du vill ha standardfunktionerna.
* Om du inte har anpassningar (alla anpassningar tas bort)

**När kan jag behålla den aktuella versionen?**

* Om du har anpassningar
* Om du inte vill sammanfoga
* Om du inte behöver åtgärda det objekt som står i konflikt från uppgraderingen

**När ska en sammanslagning utföras?**

* Endast formulär, rapporter och webbprogram kan sammanfogas.
* Vissa små sammanfogningar kan lösas utan att koden tolkas.
* Komplexare sammanslagningar ska utföras av någon med lämplig kompetens och förmåga.
* Se [Utför en sammanslagning](#perform-a-merge).

**Vad händer om jag ignorerar konflikterna?**

* Konflikten kvarstår
* Objektet uppgraderas inte
* Långsiktiga effekter: versionsinkompatibiliteter - kunden har ingen nytta av felkorrigeringar.

>[!IMPORTANT]
>Vi rekommenderar att du löser konflikter.
>

### Utför en sammanslagning{#perform-a-merge}

Det finns olika typer av sammanfogningar:

1. Enkel sammanslagning: anpassade och nya element är små och orelaterade, och ingen kodning behövs.
1. Inga ändringar: acceptera ny version, endast senaste uppdateringsdatum ändrat, endast kommentarer, tabbar, blanksteg eller nya rader. Exempel: spara av misstag.
1. Triviala ändringar: endast en rad har ändrats. Exempel: xpathToLoad
1. Komplex sammanfogning: när kodning krävs. Utvecklingskunskaper krävs. Se [Komplexa sammanslagningar](#complex-merges).

#### Hur man sammanfogar?

1. Få alla tre versionerna: originalversionen, den nya versionen och den anpassade versionen.
1. Kör ett&quot;diff&quot; mellan den ursprungliga och den nya versionen.
1. Isolera ändringarna.
1. Lös problemet genom att behålla den aktuella versionen om inga ändringar görs.

#### Var hittar du koden?

1. Inbyggd kod lagras i XML-filer i datamappen. Hitta XML-filen som matchar objektet som är i konflikt. Exempel: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Hämta den ursprungliga versionen: via [Hämtningscenter](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) eller någon annan ej uppgraderad installation av produkten.
1. Hämta den nya versionen: via [Hämtningscenter](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) eller kundens installerade filer.
1. Hämta den anpassade versionen: hämta objektets källkod från Campaign-klienten.

### Hur skiljer jag dig från mängden?

1. Installera en text- eller sammanfogningsredigerare, till exempel Anteckningar ++, AraxisMerge eller WinMerge.
1. Öppna originalfilen och den nya filen i redigeraren.
1. Kör differensen (jämför de två filerna).
1. Identifiera eventuella skillnader.

### Hur man sammanfogar?

1. Starta från den anpassade versionen.
1. Använd ändringarna.
1. Lös konflikten genom att deklarera den som löst.
1. Kontrollera om det finns icke-regressioner.

Om du väljer att lösa konflikten manuellt gör du så här:

1. I fönstrets nedre del söker du efter **_conflict_string_** för att hitta entiteterna med konflikter. Entiteten som installerades med den nya versionen innehåller det nya argumentet, entiteten som matchar den tidigare versionen innehåller det anpassade argumentet.
1. Ta bort den version som du inte vill behålla. Ta bort strängen **_conflict_argument_** för entiteten som du håller kvar.
1. Gå till konflikten som du har löst. Klicka på ikonen **Åtgärder** och välj **Deklarera som löst**.
1. Spara dina ändringar: konflikten är nu löst.

#### Komplexa sammanslagningar{#complex-merges}

1. Förstå vad ändringen innebär: bakåtkompilera ändringarna, granska ändringsloggarna, följ upp med Adobe Campaign experter.
1. Bestäm vad du ska göra med ändringen.
1. Förstå vad anpassningarna gör: bakåtkompilera ändringarna

Så här utför du en komplex sammanfogning:

1. Kopiera kodbitar från ändringslistan
1. Klistra in i den anpassade versionen
1. Test för icke-regressioner av anpassning
1. Testa om ändringarna fungerar
1. Testa användarens godkännande
1. Utför i testmiljö


>[!IMPORTANT]
>Det krävs utvecklingskunskaper för att utföra komplexa sammanfogningar.
>

**Relaterade ämnen**

* [Vanliga frågor och svar om builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Versionsinformation om Campaign Classic](../../rn/using/rn-overview.md)
* [Hjälp- och supportalternativ för Campaign Classic](../../support.md)
* [Kampanjårsuppgraderingsprogram](../../rn/using/rn-overview.md)
