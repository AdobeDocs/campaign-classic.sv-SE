---
product: campaign
title: Rekommendationer för maskinvarustorlek för Campaign Classic v7
description: Rekommendationer för maskinvarustorlek för Campaign Classic v7
feature: Technote
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: c47e73a0-dbd8-43f5-a363-7e6783dc7685
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '2519'
ht-degree: 1%

---

# Rekommendationer på maskinvarustorlek{#hardware-sizing-reco}



## Översikt

>[!CAUTION]
>
>Den här artikeln finns endast som en allmän exempelguide. Ni måste kontakta Adobe Campaign Customer Success Manager för att mäta den exakta storleken på er driftsättning innan ni påbörjar ert Campaign-projekt. **Gör inte** förvärva eller driftsätta infrastruktur eller maskinvara tills detta är klart.

Det här dokumentet innehåller allmänna rekommendationer för Adobe Campaign Classic v7-distribution på ditt lokala datacenter eller i en virtualiserad molnmiljö. Den här typen av distribution, kallas **hybrid** eller **medelleverantörer**, placerar Campaign-marknadsföringsinstansen och marknadsföringsdatabasen under din operativa kontroll, samtidigt som du använder meddelandetjänster i Adobe Cloud för att skicka e-postmeddelanden, SMS eller SMPP och samlar in e-postmeddelanden som är öppna, studsar och klickar på spårningsdata.

Marknadsföringsinstansen är den del av Adobe Campaign-arkitekturen som driver all marknadsföringsaktivitet och lagrar alla mottagardata och analysdata som returneras av kampanjer. Marknadsinstansen är en uppsättning lokala servrar som kör Adobe Campaign-tjänster och en relationsdatabas.

>[!CAUTION]
>
>Informationen i det här dokumentet gäller inte om du använder en Adobe Campaign-instans som är helt värd (distribuerad i Adobe-Cloud Services).

Programkompatibiliteten beskrivs i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).


### Scenarier

Distributionsdiagram och rekommendationer för maskinvarustorlek finns för tre representativa scenarier:

1. [Måttlig storlek](#scenario-1) - 5 miljoner aktiva mottagare i systemet
1. [Stor storlek](#scenario-2) - 20 miljoner aktiva mottagare i systemet
1. [Enterprise](#scenario-3) - 50 miljoner aktiva mottagare med transaktionsmeddelanden

### Antaganden

I det här dokumentet förutsätts även följande typer av användning för alla tre scenarierna:

* Stora e-postkampanjer skickas två gånger i veckan till ungefär 50 procent av de aktiva mottagarna
* Direktutskick genereras en gång per månad för varje mottagare i systemet
* SMS-meddelanden skickas till ungefär 10 % av dina aktiva mottagare varje månad
* Databasschemat som definierar varje mottagare har utökats med ytterligare en tabell, som innehåller cirka 200 byte data för varje mottagare
* Adobe Campaign Interaction Module används för att lägga till erbjudanden i utgående e-post
* Data för e-postspårning sparas i Campaign-systemet i 90 dagar

## Allmänna riktlinjer

Kampanjen är en databascentrerad applikation och databasserverns prestanda är avgörande. Körande arbetsflöden, segmentering, uppföljning av dataöverföringar, inkommande interaktioner, analys och andra aktiviteter genererar alla databasaktiviteter. I allmänhet avgör storleken och frekvensen för dessa åtgärder storleken på databasservrarna.

Programservrarna i din marknadsinstans kräver tillräckligt med processor och minne för att köra arbetsflöden och svara på SOAP API-anrop, inklusive förfrågningar från användare av Campaign Console. Processorkraven kan vara betydande för arbetsflöden där utgående interaktioner används med komplexa erbjudanderegler, arbetsflöden som kör anpassade JavaScript-skript och webbapplikationer med hög trafiknivå.

Kampanjwebbprogram kan också distribueras på marknadsinstansens appservrar eller på separata webbserversystem. Eftersom arbetsbelastningar för webbapplikationer är i konflikt med kritiska arbetsflöden och Campaign Console-användare, kan webbapplikationer och inkommande interaktioner distribueras till separata servrar för att säkerställa att de centrala Campaign-funktionerna fungerar tillförlitligt med bra prestanda.

För säkerhets- och tillgänglighetens skull rekommenderar Adobe att trafiken på Internet skiljs från den trafik som genereras av företagsanvändarna. Av den anledningen innehåller diagrammen två grupper med servrar: webbservern (Internet-riktad mot Web1 och Web2) och appservrarna (affärsprocesserna App1 och App2).

Det är ett juridiskt krav att e-postavsändare som är kommersiellt ska ha en funktionell avanmälningswebbsida. Adobe rekommenderar att det finns en redundant dator i varje gruppserver för redundansväxling. Det gäller särskilt om Adobe Campaign är värd för avanmälningssidorna.

### Invertera proxies

Kampanjarkitekturen tvingar fram hög säkerhet genom att använda SSL över HTTP (HTTPS) för att kommunicera mellan er marknadsföringsinstans och Adobe Cloud Messaging. Säkerhet, tillförlitlighet och tillgänglighet upprätthålls genom användning av omvända proxies i ett undernät av typen&quot;demilitariserad zon&quot; (DMZ) för att isolera och skydda marknadsföringsinstansservrarna och databasen.

### Belastningsutjämnare

Belastningsutjämnaren för appservrarna konfigureras i en aktiv/passiv konfiguration, där HTTPS avslutas vid proxyn. Belastningsutjämnaren för webbservrarna konfigureras i en aktiv/aktiv konfiguration med HTTPS avslutat vid proxyn.

Adobe ger dig en exklusiv lista över URL-sökvägar som kan vidarebefordras till Adobe Campaign-servern i din distributionsmiljö.

### Arkitektur

Den allmänna arkitekturen är nästan identisk oavsett volym. Kraven på säkerhet och hög tillgänglighet kräver minst fyra servrar, två servrar om inga WebApps används. Skillnaden i konfigurationen varierar i huvudsak i maskinvarukonfigurationen, som CPU-kärna och minne.

## Scenario 1: Distribution i medelstor storlek{#scenario-1}

![](assets/scenario-1.png)

Beräknad volym:

| Kanal | Volym |
| ----------------------- | ----------------- |
| Aktiva mottagare | 5 miljoner |
| E-post | 4,2 miljoner/månad |
| Direktmeddelande | 1 miljon/månad |
| SMS för mobiler | 100 000/månad |
| Högsta dagliga e-postvolym | 500 |

För dessa volymer har ett par Adobe Campaign-system alla funktioner för Adobe Campaign Client-användare och arbetsflödeskörning. För 5 miljoner aktiva mottagare och den här e-postvolymen är programserverns arbetsbelastning inte processorintensiv eller I/O-intensiv. Större delen av belastningen ligger på databasen.

Adobe Campaign webbservrar visas i den säkra zonen.

### Webb- och programservrar

I det här scenariot rekommenderas installation av Adobe Campaign på fyra datorer, med följande specifikation:

**3 GHz+ processor med fyra kärnor, 8 GB RAM, RAID 1 eller 10, 2 x 80 GB SSD**

Dessa system skapar en Application Server för marknadsinstansen, som har direkt stöd för dina Campaign Console-användare och kör kampanjarbetsflödena.

Omvänd proxies i en DMZ-lastbalanstrafik till Adobe Campaign webbservrar. Du behöver inte installera Adobe Campaign programstack på proxydatorer. Du kan använda omvänd proxyprogramvara eller nätverksutrustning.

Funktioner för anmälan/avanmälan av prenumerationer och inställningscenter kan tillhandahållas av Campaign eller på din egen webbplats. Om du väljer att implementera den här funktionen på din webbplats måste du se till att information om inställningar och prenumerationer sprids till marknadsföringsdatabasen för Campaign. Det görs normalt genom att extraheringsfiler skapas som automatiskt överförs av Campaign-arbetsflöden.

Diskutrymme som används på programservrar beror på lagringstiden för filer som utbyts med tredjepartstjänsteleverantörer (till exempel utskriftsleverantörer för direktreklam) och på storleken och kvarhållandet av importerade platta filer, till exempel prenumerations- eller inställningsuppdateringar från din webbplats, eller extraheringar från ditt eget CRM- eller marknadsföringssystem.

### Databas

Maskinvarurekommendationerna för databasservern är följande:

**3 GHz+ 4-kärnig processor, 16 GB RAM, RAID 1 eller 10, minst 128 GB SSD**

Minnesuppskattningen förutsätter fullständig cachelagring av ungefär 500 000 mottagare för en stor kampanjstart, plus RDBMS-buffertutrymme för körning av arbetsflöden, import av spårningsdata och andra samtidiga aktiviteter.

Det beräknas att det diskutrymme som krävs i databasen för att lagra alla Adobe Campaign tekniska data (kampanjer, spårning, arbetsregister och så vidare) är cirka 35 GB baserat på en kvarhållningsperiod på tre månader. Om du väljer att behålla spårningsdata i 6 månader ökar databasstorleken till cirka 40 GB och om du sparar data i 12 månader ökar databasstorleken till cirka 45 GB. Mottagardata förbrukar cirka 5 GB för den här miljön.

>[!CAUTION]
>
>Denna uppskattning innehåller inga ytterligare kunddata. Om du planerar att replikera ytterligare kolumner eller tabeller med kunddata till Adobe Campaign-databasen måste du beräkna behovet av ytterligare diskutrymme. Överförda segment/listor kräver också mer lagringsutrymme beroende på storlek, frekvens och kvarhållningsperiod.

Tänk också på att databasserverns IOPS är viktig på grund av den mängd information som behandlas dagligen. På en toppendag kan ni till exempel driftsätta kampanjer riktade till totalt 500 000 mottagare. För att genomföra varje kampanj lägger Adobe Campaign in 500 000 poster i en tabell som innehåller ungefär 12 miljoner poster (leveransloggtabellen). Adobe rekommenderar minst 60 000 4 kB slumpmässiga läs-/skrivåtgärder för det här scenariot för att få godtagbara prestanda under kampanjdistributionen.


## Scenario 2: Distribution i stor storlek{#scenario-2}

![](assets/scenario-2.png)

Beräknad volym:

| Kanal | Volym |
| ----------------------- | ----------------- |
| Aktiva mottagare | 20 miljoner |
| E-post | 42 miljoner/månad |
| Direktmeddelande | 10 miljoner/månad |
| SMS för mobiler | 1 000 000/månad |
| Högsta dagliga e-postvolym | 5,000,000 |

### Webb- och programservrar

I det här scenariot rekommenderar Adobe att Adobe Campaign installeras på fyra datorer, två programservrar och två webbservrar, med följande specifikation:

**3 GHz+ processor med fyra kärnor, 8 GB RAM, RAID 1 eller 10, 80 GB SSD**

Programservrarna har direkt stöd för Campaign Console-användare och körning av kampanjarbetsflöden. Den här funktionen distribueras på två identiska servrar för hög tillgänglighet och delar ett NAS-filsystem (Network-Attached Storage) för att möjliggöra failover.

Webbservrarna är värdar för Campaign-webbprogram som stöder de 10 miljoner aktiva mottagarna i systemet.

Se [Scenario 1: Distribution i medelstor storlek](#scenario-1) om du vill ha fler kommentarer om proxies, inställningscenter/prenumerationshantering och användning av diskutrymme.

### Databas

Maskinvarurekommendationerna för databasservern är följande:

**3 GHz+ 8-kärnig processor, 64 GB RAM, RAID 1 eller 10, 2 x 320 GB SSD eller RAID 10, 640 GB SSD-hårddisk**

Minnesuppskattningen förutsätter fullständig cachelagring av ungefär 5 000 000 mottagare för en stor kampanjstart, plus RDBMS-buffertutrymme för körning av arbetsflöden, import av spårningsdata och andra samtidiga aktiviteter.

Det beräknas att det diskutrymme som krävs i databasen för att lagra alla Adobe Campaign tekniska data (kampanjer, spårning, arbetsregister och så vidare) är cirka 280 GB baserat på en kvarhållningsperiod på 3 månader. Om du väljer att behålla spårningsdata i 6 månader ökar databasstorleken till cirka 450 GB och om du sparar data i 12 månader ökar databasstorleken till cirka 900 GB. Mottagardata förbrukar cirka 15 GB för den här miljön.

## Scenario 3: Företagsdistribution med Message Center{#scenario-3}

![](assets/scenario-3.png)

Beräknad volym:

| Kanal | Volym |
| ----------------------- | ----------------- |
| Aktiva mottagare | 50 miljoner |
| E-post | 108 miljoner/månad |
| Direktmeddelande | 25 miljoner/månad |
| SMS för mobiler | 2,5 miljoner/månad |
| Transaktionsmeddelanden | 2,5 miljoner/månad |
| Högsta dagliga e-postvolym | 2,5 miljoner |


Driftsättningen med stöd för 50 miljoner mottagare är i stort sett densamma som i [Scenario 2](#scenario-2): Kampanjens webbapplikationstrafik dirigeras till webbservrar för Campaign, vilket innebär att webbtrafiken efter lanseringen av stora kampanjer inte påverkar arbetsflödena för Campaign och användare av klientkonsolen.

Den här distributionen innehåller även Message Center-samtal som drivs av dina egna webbplatser och applikationer.


### Webb- och programservrar

I det här scenariot rekommenderar Adobe att du installerar Adobe Campaign på fyra datorer enligt följande:

* Programservrar
  **Två system, 3 GHz+ processorer med fyra kärnor, 8 GB RAM, RAID 1 eller 10, 80 GB SSD**

* Webbservrar
  **Två system, 3 GHz+ processorer med fyra kärnor, 16 GB RAM, RAID 1 eller 10, 80 GB SSD**


Programservrarna har direkt stöd för Campaign Console-användare och körning av kampanjarbetsflöden. Den här funktionen distribueras på två identiska servrar för hög tillgänglighet och delar ett NAS-filsystem (Network-Attached Storage) för att möjliggöra failover.

Webbservrarna är värdar för Campaign-webbprogram som stöder de 10 miljoner aktiva mottagarna i systemet.

Se [Scenario 1: Distribution i medelstor storlek](#scenario-1) om du vill ha fler kommentarer om proxies, inställningscenter/prenumerationshantering och användning av diskutrymme.

### Databas

Maskinvarurekommendationerna för databasservern är följande:

**3 GHz+ 8-kärnig processor, 96 GB RAM, RAID 1 eller 10, minst 1,5 TB SSD**

Minnesuppskattningen förutsätter fullständig cachelagring av ungefär 12 500 000 mottagare för en stor kampanjstart, plus RDBMS-buffertutrymme för körning av arbetsflöden, import av spårningsdata och andra samtidiga aktiviteter.

Det beräknas att det diskutrymme som krävs i databasen för att lagra alla Adobe Campaign tekniska data (kampanjer, spårning, arbetstabeller och så vidare) är cirka 700 GB baserat på en kvarhållningsperiod på 3 månader. Om du väljer att behålla spårningsdata i 6 månader ökar databasstorleken till cirka 1,2 TB och om du sparar data i 12 månader ökar databasstorleken till cirka 2 TB. Mottagardata förbrukar cirka 50 GB för den här miljön.

## Riktlinjer för att ändra antaganden

De antaganden som gjorts för dessa scenarier påverkar alla maskinvarurekommendationerna och driftsättningsarkitekturen avsevärt. I det här avsnittet behandlas riktlinjer kring olika antaganden. Kontakta Adobe Campaign Consulting-teamet för specifika rekommendationer.

* **Antal mottagare**
Aktiva mottagare kräver både lagringsutrymme och databasbuffertutrymme, så fler mottagare kräver vanligtvis mer minne och processorkapacitet på databasservern. Lagringsökningarna är relativt små för mottagarna själva, men kan vara betydande för händelsespårningsdata som lagras för e-postkampanjer.

* **Storlek på e-postkampanj**
Hur ofta kampanjer startas påverkar databasserverns processorkrav. I kombination med direktutskick, inkommande interaktioner och andra arbetsflöden innebär segmenteringsåtgärder för e-postkampanjer en avsevärd belastning för databasservern.

* **Frekvens för direktreklam**
Hur ofta direktutskick skickas kan påverka databasserverns processorkrav. I kombination med kampanjlanseringar och andra arbetsflöden innebär segmenteringsåtgärder för direktutskick en avsevärd belastning på databasservern.

* **SMS-meddelandevolym**
Precis som storleken på e-postkampanjer gör inte SMS-meddelandevolymen stora belastningar på Campaign-servrar på plats. Inläsningen görs huvudsakligen på meddelandeservrar i Adobe Cloud i molnet. Segmentering för SMS-kampanjer, som e-post och direktreklam, kan innebära en avsevärd belastning för marknadsföringsdatabasen. Därför är frekvensen för lanseringar av SMS-kampanjer och komplexiteten i segmenteringen mer relevant än volymen för SMS-meddelanden.

* **Komplexitet för databasschema**
Mängden data för varje aktiv mottagare kräver både lagringsutrymme och buffertutrymme för databasen, så fler mottagare behöver vanligtvis mer minne och processorkapacitet på databasservern. Komplexa scheman kräver också att fler tabeller förenas för segmentering, så segmenteringsåtgärder kan köras mycket långsammare och kräver mer databasprocessor och minne när data sprids över flera tabeller.

  Databasserverminnet beräknas genom att säkerställa att databasbuffertpoolen kan vara tillräckligt stor för att innehålla alla mottagardata, plus tillfälliga tabeller för att köra arbetsflöden, plus en marginal för andra databasåtgärder.

* **Användning av utgående interaktion**
Regler för interaktion i gruppläge utvärderas i arbetsflöden som överför all beräkningskomplexitet till databasen. Den största ansträngningsfaktorn för databasen är det totala antalet giltiga erbjudanden som beräknas under ett motoranrop (målstorlek X genomsnittligt antal erbjudanden per mottagare innan de bästa N-erbjudandena behålls). Databasserverns processorhastighet är den första prestandafaktionen.

* **Inkommande interaktioner eller SOAP API-användning**
Regler och erbjudanden för inkommande interaktion utvärderas i marknadsföringsdatabasen, vilket kräver stora databasserverresurser, särskilt CPU. Kraftig användning av inkommande interaktioner eller SOAP API:er kräver separata webbservrar för att separera arbetsbelastningen från pågående Campaign-arbetsflöden.

* **Lagringsperiod för spårningsdata**
Om du vill öka lagringen av spårningsdata i mer än 90 dagar krävs mer databaslagring och systemet kan bli långsammare eftersom nya spårningsdata läggs in i stora tabeller. Spårningsdata är inte användbara för kampanjsegmentering efter 90 dagar, så den kortare kvarhållningsperioden rekommenderas.

  Spårningsdata bör flyttas till Adobe Analytics eller något annat analyssystem om ni behöver en långsiktig analys av mottagarnas marknadsföringsupplevelser.

## Virtualisering

Alla Campaign-servrar är bra lämpade för virtualisering. Flera frågor måste åtgärdas för att säkerställa lämplig tillgänglighet och prestanda.

* **Konfiguration av redundans**
Klustrade servrar, till exempel redundanta programservrar under en belastningsutjämnad proxy, måste distribueras på separat maskinvara för att säkerställa att båda virtuella maskiner inte kraschar om maskinvarufel uppstår.

* **I/O-konfiguration**
Alla rekommenderade RAID-konfigurationer måste upprätthållas för databassäkerhet för att säkerställa att en förlust av en lagringsenhet inte orsakar dataförlust.

* **I/O-prestanda**
Den rekommenderade IOPS-klassificeringen för databaslagring måste respekteras. Molntjänster som Amazon EC2 kanske inte ger den prestanda som krävs och måste utvärderas noggrant. Amazon EC2-provisionerade SSD-volymer är till exempel för närvarande klassificerade till 20 000 IOPS var. Läs mer i [Amazon-dokumentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html)), så en RAID-konfiguration med 4 volymer skulle få värdet 80 000 IOPS, vilket kanske inte är tillräckligt.

Adobe rekommenderar prestandatestning för virtualiserad driftsättning av Adobe Campaign innan systemet börjar användas.

## Relaterade ämnen

* [Processer för kampanjövervakning](../../production/using/monitoring-processes.md)
* [Allmän kampanjarkitektur](../../installation/using/general-architecture.md)
* [Prestanda- och genomströmningsproblem](../../production/using/performance-and-throughput-issues.md)
* [Checklista för säkerhet och sekretess](../../installation/using/get-started-security-privacy.md)
