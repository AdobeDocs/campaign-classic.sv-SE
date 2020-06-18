---
title: E-postarkivering
seo-title: E-postarkivering
description: E-postarkivering
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7de74feb61cc8f4b386a6ff86fc58b9c9e9ca1d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---


# E-postarkivering{#email-archiving}

Du kan konfigurera Adobe Campaign så att en kopia av e-postmeddelanden som skickas från din plattform sparas.

Adobe Campaign hanterar dock inte själva arkiverade filer. Det gör att du kan skicka meddelanden till en dedikerad adress, varifrån de kan bearbetas och arkiveras i ett externt system.

För att göra detta överförs e-postfiler som motsvarar skickade e-postmeddelanden till en fjärrserver, till exempel en SMTP-e-postserver. Arkiveringsmålet är en e-postadress (osynlig för leveransmottagarna) som du måste ange.

## Rekommendationer och begränsningar {#recommendations-and-limitations}

* Funktionen för e-postarkivering är valfri. Kontrollera licensavtalet.
* Kontakta er kontoansvarige för att aktivera **hostingarkitekturer och hybridarkitekturer**. Den valfria BCC-adressen måste skickas till Adobe-teamet som konfigurerar den åt dig.
* För **lokala installationer** följer du riktlinjerna nedan för att aktivera den - se avsnitten [Aktivera e-postarkivering (lokalt)](#activating-email-archiving--on-premise-) och [Konfigurera e-postadressen (lokalt)](#configuring-the-bcc-email-address--on-premise-) för BCC.
* Du kan bara använda en e-postadress för hemlig kopia.
* När BCC för e-post har konfigurerats kontrollerar du att funktionen är aktiverad i leveransmallen eller i leveransen via **[!UICONTROL Archive emails]** alternativet. Mer information finns i [det här avsnittet](../../delivery/using/sending-messages.md#archiving-emails).
* Det är bara skickad e-post som räknas, studenterna gör det inte.
* E-postarkiveringssystemet ändrades med Adobe Campaign 17.2 (build 8795). Om du redan har använt e-postarkivering måste du uppgradera manuellt till det nya systemet för e-postarkivering. Mer information finns i avsnittet [Uppdaterat arkiveringssystem för e-post (BCC)](#updated-email-archiving-system--bcc-) .

## Aktivera e-postarkivering (lokalt) {#activating-email-archiving--on-premise-}

Följ stegen nedan för att aktivera BCC-e-postarkivering när Adobe Campaign är installerat lokalt.

### Lokal mapp {#local-folder}

Om du vill aktivera överföring av skickade e-postmeddelanden till en e-postadress för hemlig kopia, måste du först spara exakta kopior av skickade e-postmeddelanden som .eml-filer i en lokal mapp.

Sökvägen till den lokala mappen måste anges i filen **config-`<instance>`.xml** från konfigurationen. Exempel:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Det är teamets ansvar att se till att skyddsinställningarna tillåter åtkomst till den mapp som definieras med **dataLogPath** -parametrarna.

Den fullständiga sökvägen är följande: **`<datalogpath>  YYYY-MM-DDHHh`**. Datum och tid anges enligt MTA-serverns klocka (UTC). Exempel:

```
C:\emails\2018-12-02\13h
```

Arkivfilens namn är **`<deliveryid>-<broadlogid>.eml`** när e-postmeddelandets status inte är **[!UICONTROL Sent]**. När statusen har ändrats till **[!UICONTROL Sent]** blir filnamnet **`<deliveryid>-<broadlogid>-sent.eml`**. Exempel:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>I en instans med mellanlagring finns katalogen för de arkiverade e-postmeddelandena på servern med mellanlagring.
>
>DeliveryID och broadcastID kommer från mittkällservern när status för e-postmeddelanden inte skickas. När statusen har ändrats till **[!UICONTROL Sent]** kommer dessa ID:n från marknadsföringsservern.

### Parametrar {#parameters}

När den lokala mappsökvägen har definierats lägger du till och redigerar följande element som du vill i **config-`<instance name>.xml`**filen. Nedan finns standardvärdena:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: det format som används vid komprimering av .eml-filer. Möjliga värden är:

   **0**: ingen komprimering (standardvärde)

   **1**: komprimering (.zip-format)

* **compressBatchSize**: antal .eml-filer som lagts till i ett arkiv (.zip-fil).
* **archivingType**: arkiveringsstrategi som ska användas. Möjliga värden är:

   **0**: obearbetade kopior av skickade e-postmeddelanden sparas i .eml-format till mappen **dataLogPath** (standardvärde). En arkiverande kopia av **`<deliveryid>-<broadlogid>-sent.eml`** filen sparas i mappen **dataLogPath/archives** . Sökvägen till den skickade e-postfilen blir **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: obearbetade kopior av skickade e-postmeddelanden sparas i .eml-format till mappen **dataLogPath** och skickas till BCC-e-postadressen via SMTP. När e-postkopiorna har skickats till BCC-adressen ändras arkivfilens namn **`<deliveryid>-<broadlogid>-sent-archived.eml`** och filen flyttas till **mappen dataLogPath/archives** . Sökvägen till den skickade och BCC-arkiverade e-postfilen är sedan **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: antal dagar som .eml-filer sparas för arkivering. Efter den fördröjningen flyttas de automatiskt till mappen **dataLogPath/archives** för komprimering. Som standard upphör .eml-filer att gälla efter två dagar.
* **purgeArchivesDelay**: Antal dagar som arkiv sparas i mappen **dataLogPath/`<archives>`**. Efter den perioden tas de bort permanent. Tömningen börjar när MTA startas. Som standard utförs den var sjunde dag.
* **pollDelay**: kontrollfrekvens (i sekunder) för nya inkommande skickade e-postmeddelanden till mappen **dataLogPath** . Om den här parametern till exempel är inställd på 60 innebär det att varje minut går arkiveringsprocessen igenom .eml-filerna i **dataLogPath/`<date and time>`**-mapparna, tillämpar en tömning vid behov och skickar e-postkopior till BCC-adressen och/eller komprimerar de arkiverade filerna vid behov.
* **obtainLimit**: antalet .eml-filer som bearbetas samtidigt innan arkiveringsprocessen tillämpas igen enligt parametern **pollDelay** . Om du till exempel ställer in parametern **obtainLimit** på 100 medan parametern **pollDelay** är inställd på 60, bearbetas 100 .eml-filer per minut.
* **smtpNbConnection**: antal SMTP-anslutningar till BCC-e-postadressen.

Se till att du justerar parametrarna efter e-postsändningens genomströmning. I en konfiguration där MTA skickar 30 000 e-postmeddelanden per timme kan du ange parametern **pollDelay** till 600, parametern **obtainLimit** till 5 000 och parametern **smtpNbConnection** till 2. Det innebär att med 2 SMTP-anslutningar skickas 5 000 e-postmeddelanden till BCC-adressen var 10:e minut.

## Konfigurera e-postadressen för den lokala kopian (lokal) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>Av sekretesskäl måste e-post från innehållsförteckningen behandlas av ett arkiveringssystem som kan lagra säkert personligt identifierbar information (PII).

Använd följande parametrar i **config-`<instance name>.xml`**-filen för att definiera SMTP-e-postservern som de lagrade filerna ska överföras till:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: arkiveringsmål
* **smtpEnableTLS**: med en säker SMTP-anslutning (TLS/SSL-protokoll)
* **smtpRelayAddress**: reläadress att använda
* **smtpRelayPort**: reläport att använda

>[!NOTE]
>
>Om du använder ett SMTP-relä beaktas inte de ändringar i e-postmeddelanden som görs av reläet i arkiveringsprocessen.
>
>Dessutom tilldelar reläet en **[!UICONTROL Sent]** status till alla e-postmeddelanden, även de som inte skickas. Därför arkiveras alla meddelanden.

## Uppdaterat arkiveringssystem för e-post (BCC) {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>E-postarkiveringssystemet (BCC) har ändrats med Adobe Campaign 17.2 (build 8795). Om du uppgraderar från en äldre version och redan har använt e-postarkiveringsfunktioner måste du uppgradera manuellt till det nya systemet för e-postarkivering.

Gör följande ändringar i **`config-<instance>.xml`** filen:

1. Ta bort parametern **zipPath** från **`<archiving>`** noden.
1. Ställ in parametern **compressionFormat** på **1** om det behövs.
1. Ställ in parametern **archivingType** på **1**.

När du har konfigurerat BCC för e-post måste du välja **[!UICONTROL Archive emails]** alternativet i leveransmallen eller leveransmallen. Mer information finns i [det här avsnittet](../../delivery/using/sending-messages.md#archiving-emails).

## God praxis {#best-practices}

* **BCC-adresspostlåda**: Se till att den har tillräcklig mottagningskapacitet för att arkivera alla e-postmeddelanden som skickas av MTA.
* **MTA-mutualisering**: arkiveringsfunktionen i innehållsförteckningen fungerar på MTA-nivå. Du kan duplicera alla e-postmeddelanden som skickas av MTA. Eftersom MTA kan mutualiseras i flera instanser (t.ex. dev, test eller prod) eller till och med i flera klienter (i en miljö där flera leverantörer finns) påverkar konfigurationen säkerheten:

   * Om du delar en MTA med flera klienter och en av dem har det här alternativet aktiverat, får den här klienten tillgång till alla e-postmeddelanden från andra klienter som delar samma MTA. För att undvika en sådan situation bör du använda olika MTA för varje kund.
   * Om du använder samma MTA för flera instanser (utveckling, test, prod) för en enskild klient, dupliceras meddelandena som skickas från alla tre instanserna med alternativet dataLogPath.

* **E-post per anslutning**: BCC-arkivering av e-post fungerar genom att öppna en anslutning och försöka skicka alla e-postmeddelanden via den anslutningen. Adobe rekommenderar att du kontaktar din interna tekniska kontakt för att kontrollera antalet e-postmeddelanden som accepteras för en viss anslutning. Om du ökar det här antalet kan det påverka genomströmningen av BCC avsevärt.
* **BCC skickar IP**: För närvarande skickas inte BCC-e-post via de vanliga MTA-proxyadresserna. I stället öppnas en direktanslutning från MTA-servern till målservern för e-post. Det innebär att du kan behöva lägga till ytterligare IP-adresser i listan över tillåtna IP-adresser i nätverket, beroende på din e-postserverkonfiguration.

