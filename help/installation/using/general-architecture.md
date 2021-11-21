---
product: campaign
title: Allmän arkitektur
description: Lär dig hur du installerar och konfigurerar Campaign Classic.
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: 04e6dc17-427b-4745-84cc-bf45c03dbf81
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 0%

---

# Allmän arkitektur{#general-architecture}

![](../../assets/v7-only.svg)

Den typiska driftsättningen av Adobe Campaign-lösningar består av följande komponenter:

* **Anpassad klientmiljö**

   Intuitivt grafiskt gränssnitt där användare kan kommunicera och spåra marknadsföringserbjudanden, skapa kampanjer, granska och hantera alla marknadsföringsaktiviteter, program och planer - inklusive e-post, arbetsflöden och landningssidor -, skapa och hantera kundprofiler och definiera kundtyper.

* **Utvecklingsmiljö**

   Program på serversidan som kör marknadsföringskampanjer via valda kommunikationskanaler, inklusive e-post, SMS, push-meddelanden, direktreklam, webb eller sociala, baserat på de regler och arbetsflöden som definieras i användargränssnittet.

* **Databasbehållare**

   Adobe Campaign-databasen lagrar all kundinformation, kampanjkomponenter, erbjudanden och arbetsflöden samt kampanjresultat i kunddatabasbehållare, baserat på relationsdatabasteknik.

Adobe Campaign bygger på en tjänsteinriktad arkitektur (SOA) och består av flera funktionella moduler. Dessa moduler kan distribueras på en eller flera datorer, i en eller flera instanser, beroende på begränsningar i fråga om skalbarhet, tillgänglighet och isolering av tjänster. Distributionskonfigurationerna är därför mycket omfattande och omfattar en enda central dator till konfigurationer som omfattar flera dedikerade servrar över flera platser.

>[!NOTE]
>
>Som programvaruleverantör anger vi kompatibel infrastruktur för maskin- och programvara. De maskinvarurekommendationer som ges här är endast avsedda som information och baseras på vår erfarenhet. Adobe skall inte vara ansvarig för beslut som fattas på grundval av dessa beslut. Det beror också på era affärsregler och rutiner samt kritiken och de prestandanivåer som krävs för projektet.

![](assets/s_ncs_install_architecture.png)

>[!CAUTION]
>
>Om inget annat uttryckligen anges är installation, uppdatering och underhåll av alla komponenter i en Adobe Campaign-plattform datoradministratörens ansvar. Detta innebär att man måste implementera förutsättningarna för Adobe Campaign-program samt följa Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md) mellan komponenter.

## Presentationslager {#presentation-layer}

Programmet kan nås på olika sätt, beroende på användarnas behov: Rich Client, Thin Client eller API Integration.

* **Rich Client**: Programmets huvudanvändargränssnitt är en avancerad klient, d.v.s. ett inbyggt program (Windows) som kommunicerar med Adobe Campaign programserver enbart med standardInternetprotokoll (SOAP, HTTP osv.). Den här konsolen är mycket användarvänlig och ger mycket liten bandbredd (med hjälp av ett lokalt cacheminne) och är utformad för enkel driftsättning. Konsolen kan distribueras från en webbläsare, kan uppdateras automatiskt och kräver ingen specifik nätverkskonfiguration eftersom den bara genererar HTTP(S)-trafik.
* **Tunn klient**: Vissa delar av applikationen kan nås via en enkel webbläsare via ett användargränssnitt i HTML, inklusive rapporteringsmodulen, godkännandefaser, funktioner i modulen Distributed Marketing (central/lokal), instansövervakning osv. I det här läget kan du inkludera Adobe Campaign-funktioner i ett intranät eller ett extranät.
* **Integrering via API:er**: I vissa fall kan systemet anropas från ett externt program med hjälp av de API:er för webbtjänster som exponeras via SOAP-protokollet.

## Logiskt programlager {#logical-application-layer}

Adobe Campaign är en enda plattform med olika program som tillsammans utgör en öppen och skalbar arkitektur. Adobe Campaign-plattformen är skriven i ett flexibelt programlager och kan enkelt konfigureras för att tillgodose företagets behov. Detta tillgodoser företagets växande behov ur funktionell och teknisk synvinkel. Den distribuerade arkitekturen säkerställer linjär skalbarhet av systemet från tusentals meddelanden till miljontals meddelanden.

Adobe Campaign förlitar sig på en uppsättning processer på serversidan som fungerar tillsammans.

De viktigaste processerna är:

**Programserver** (nlserver web)

Den här processen visar alla Adobe Campaign-funktioner via Web Services API:er (SOAP - HTTP + XML). Dessutom kan man dynamiskt generera webbsidor för åtkomst via HTML (rapporter, webbformulär etc.). För att uppnå detta innehåller den här processen en Apache Tomcat JSP-server. Detta är den process som konsolen ansluter till.

**Arbetsflödesmotor** (nlserver wfserver)

Den kör de arbetsflödesprocesser som definierats i programmet.

Den hanterar också regelbundet genomförda tekniska arbetsflöden, inklusive:

* Spårning: Återställer och konsoliderar spårningsloggar. Det gör att du kan hämta loggarna från omdirigeringsservern och skapa de aggregerade indikatorer som används av rapportmodulen.
* Rensa: Databasrengöring. Används för att rensa gamla poster och undvika att databasen växer exponentiellt.
* Fakturering: Automatisk sändning av en aktivitetsrapport för plattformen (databasstorlek, antal marknadsföringsåtgärder, antal aktiva profiler osv.).

**Delivery Server** (nlserver mta)

Adobe Campaign har inbyggd e-postsändningsfunktion. Den här processen fungerar som en MTA (SMTP mail transfer agent). Den personaliserar meddelanden från en till en och hanterar deras fysiska leverans. Den fungerar med leveransjobb och hanterar automatiska återförsök. När spårning är aktiverat ersätts URL-adresserna automatiskt så att de pekar på omdirigeringsservern.

Den här processen kan hantera anpassning och automatisk sändning till en tredjepartsrouter för SMS, fax och direktreklam.

**Omdirigeringsserver** (nlserver webmdl)

För e-post hanterar Adobe Campaign automatiskt öppnings- och klickspårning (transaktionsspårning på webbplatsnivå är en ytterligare möjlighet). För att uppnå detta skrivs de URL:er som ingår i e-postmeddelandena om så att de pekar på den här modulen, som registrerar den överförda Internet-användaren innan de dirigeras om till den önskade URL:en.

För att garantera högsta tillgänglighet är denna process helt oberoende av databasen: de andra serverprocesserna kommunicerar med den endast med SOAP-anrop (HTTP, HTTP(S) och XML). Tekniskt sett implementeras den här funktionen i en tilläggsmodul för en HTTP-server (ISAPI-tillägg i IIS eller en DSO Apache-modul osv.) och finns endast i Windows.

Det finns även andra tekniska processer:

**Hantera studsmeddelanden** (nlserver inMail)

Med den här processen kan du automatiskt hämta e-post från postlådor som konfigurerats för att ta emot studsade meddelanden som returneras om leveransen misslyckas. Dessa meddelanden genomgår sedan regelbaserad bearbetning för att fastställa orsaken till utebliven leverans (okänd mottagare, kvoten har överskridits osv.) och för att uppdatera leveransstatus i databasen.

Alla dessa åtgärder är helt automatiska och förkonfigurerade.

**SMS-leveransstatus** (nlserver sms)

Den här processen avsöker SMS-routern för att samla in förloppsstatus och uppdatera databasen.

**Skriver loggmeddelanden** (nlserver syslogd)

Den här tekniska processen hämtar loggmeddelanden och spårningar som genererats av andra processer och skriver dem till hårddisken. Detta gör att det finns gott om information som kan användas för diagnostik i händelse av problem.

**Skrivspårningsloggar** (nlserver trackinglogd)

Den här processen sparar spårningsloggarna som genereras av omdirigeringsprocessen.

**Skriver inkommande händelser** (nlserver interactiond)

Denna process gör att inkommande händelser spelas in på disken inom ramen för Interaction.

**Tillsynsmoduler** (nlserver watchdog)

Denna tekniska process fungerar som en huvudprocess som sporrar de andra. Den övervakar dem också och startar om dem automatiskt i händelse av incidenter, vilket ger maximal aktiv systemtid.

**Statistikserver** (nlserver-status)

Den här processen innehåller statistik om antalet anslutningar, de meddelanden som skickas för varje e-postserver som meddelanden skickas till samt deras begränsningar (högsta antal samtidiga anslutningar, meddelanden per timme och/eller anslutning). Du kan också federera flera instanser eller datorer om de delar samma offentliga IP-adresser.

>[!NOTE]
>
>Den fullständiga listan över Adobe Campaign-moduler finns i [det här dokumentet](../../production/using/operating-principle.md).

## Beständigt lager {#persistence-layer}

Databasen används som ett beständigt lager och innehåller nästan all information som hanteras av Adobe Campaign. Detta omfattar både funktionell information (profiler, prenumerationer, innehåll osv.), teknisk information (leveransjobb och loggar, spårningsloggar osv.) och arbetsdata (inköp, leads).

Databasens tillförlitlighet är av yttersta vikt eftersom de flesta Adobe Campaign-komponenter kräver åtkomst till databasen för att kunna utföra sina uppgifter (med undantag för omdirigeringsmodulen).

Plattformen levereras fördefinierad med en marknadsföringscentrerad datamarknad eller kan enkelt placeras ovanpå en befintlig datamarknad och ett befintligt schema med hjälp av något av de större Relational Database Management Systems (RDBMS). Alla data i datafilen nås av Adobe Campaign-plattformen via SQL-anrop från Adobe Campaign till databasen. Adobe Campaign har också en komplett uppsättning ETL-verktyg (Extract Transform and Load) för import och export av data till och från systemet.
