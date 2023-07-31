---
product: campaign
title: E-postarkivering
description: E-postarkivering
feature: Installation, Instance Settings, Email
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1366'
ht-degree: 5%

---

# Konfigurera dold e-postkopia {#email-archiving}



Du kan konfigurera Adobe Campaign att behålla en kopia av e-postmeddelanden som skickas från din plattform.

Men Adobe Campaign hanterar inte själva arkiverade filer. Det gör att du kan skicka meddelanden till en dedikerad adress, varifrån de kan bearbetas och arkiveras i ett externt system.

För att göra detta överförs e-postfiler som motsvarar skickade e-postmeddelanden till en fjärrserver, till exempel en SMTP-e-postserver. Arkiveringsmålet är en e-postadress (osynlig för leveransmottagarna) som du måste ange.

## Recommendations och begränsningar {#recommendations-and-limitations}

* Funktionen för e-postkopia är valfri. Kontrollera licensavtalet.
* För **hostingarkitektur och hybridarkitektur**, kontakta er kontoansvarige för att aktivera det. Du måste ange valfri e-postadress till BCC för det Adobe-team som konfigurerar den åt dig.
* För **lokala installationer** följer du riktlinjerna nedan för att aktivera det - se [Aktivera e-postkopia (lokalt)](#activating-email-archiving--on-premise-) och [Konfigurera e-postadressen för den lokala kopian (lokal)](#configuring-the-bcc-email-address--on-premise-) -avsnitt.
* Du kan bara använda en e-postadress för hemlig kopia.
* Kontrollera att funktionen är aktiverad i leveransmallen eller i leveransen via **[!UICONTROL Email BCC]** alternativ. Mer information finns i [det här avsnittet](../../delivery/using/sending-messages.md#archiving-emails).
* Det är bara skickad e-post som räknas, men studenterna gör det inte.
* E-postarkiveringssystemet har ändrats med Adobe Campaign 17.2 (build 8795). Om du redan har arkiverat via e-post måste du uppgradera manuellt till det nya BCC-systemet för e-post. Mer information finns i [Byt till den nya e-postkontrollen](#updated-email-archiving-system--bcc-) -avsnitt.

## Aktiverar e-postkopia (lokalt) {#activating-email-archiving--on-premise-}

[!BADGE Lokal och hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"}


Följ stegen nedan för att aktivera arkivering av e-post i webbläsare när Adobe Campaign är installerat lokalt.

### Lokal mapp {#local-folder}

Om du vill aktivera överföring av skickade e-postmeddelanden till en e-postadress för hemlig kopia, måste du först spara exakta kopior av skickade e-postmeddelanden som .eml-filer i en lokal mapp.

Sökvägen till den lokala mappen måste anges i **config-`<instance>`XML** från konfigurationen. Exempel:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>Det är teamets ansvar att se till att skyddsinställningarna tillåter åtkomst till den mapp som definierats via **dataLogPath** parametrar.

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
>I en instans där flera källor finns finns katalogen för BCC-e-postmeddelanden på servern där flera leverantörer finns.
>
>DeliveryID och broadcastID kommer från mittkällservern när status för e-postmeddelanden inte skickas. När statusen har ändrats till **[!UICONTROL Sent]** kommer dessa ID:n från marknadsföringsservern.

### Parametrar {#parameters}

När den lokala mappsökvägen har definierats lägger du till och redigerar följande element som du vill ha i dialogrutan **config-`<instance name>.xml`** -fil. Nedan finns standardvärdena:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: det format som används vid komprimering av EML-filer. Möjliga värden är:

  **0**: ingen komprimering (standardvärde)

  **1**: komprimering (.zip-format)

* **compressBatchSize**: antal .eml-filer som lagts till i ett arkiv (.zip-fil).
* **archivingType**: arkiveringsstrategi som ska användas. Möjliga värden är:

  **0**: obearbetade kopior av skickade e-postmeddelanden sparas i .eml-format till **dataLogPath** mapp (standardvärde). En arkiverande kopia av **`<deliveryid>-<broadlogid>-sent.eml`** filen sparas i **dataLogPath/archives** mapp. Sökvägen till den skickade e-postfilen ändras **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

  **1**: obearbetade kopior av skickade e-postmeddelanden sparas i .eml-format till **dataLogPath** och skickas till BCC-e-postadressen via SMTP. När e-postkopiorna har skickats till BCC-adressen blir arkivfilens namn **`<deliveryid>-<broadlogid>-sent-archived.eml`** och filen flyttas till **dataLogPath/archives** mapp. Sökvägen till den skickade och BCC-arkiverade e-postfilen är sedan **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: antal dagar som .eml-filer sparas för arkivering. Efter den fördröjningen flyttas de automatiskt till **dataLogPath/archives** mapp för komprimering. Som standard upphör .eml-filer att gälla efter två dagar.
* **purgeArchivesDelay**: antal dagar arkiveras i **dataLogPath/`<archives>`** mapp. Efter den perioden tas de bort permanent. Tömningen börjar när MTA startas. Som standard utförs den var sjunde dag.
* **pollDelay**: kontrollfrekvens (i sekunder) för nya inkommande e-postmeddelanden till **dataLogPath** mapp. Om den här parametern till exempel är inställd på 60 innebär det att varje minut går arkiveringsprocessen igenom .eml-filerna i **dataLogPath/`<date and time>`** lägger du till en tömning om det behövs och skickar e-postkopior till BCC-adressen och/eller komprimerar de arkiverade filerna vid behov.
* **obtainLimit**: antal .eml-filer som bearbetas samtidigt innan arkiveringsprocessen tillämpas igen enligt **pollDelay** parameter. Om du till exempel anger **obtainLimit** parametern till 100 medan **pollDelay** parametern är inställd på 60, 100 .eml-filer per minut kommer att bearbetas.
* **smtpNbConnection**: antal SMTP-anslutningar till BCC-e-postadressen.

Se till att du justerar parametrarna efter e-postsändningens genomströmning. I en konfiguration där MTA skickar 30 000 e-postmeddelanden per timme kan du till exempel ange **pollDelay** -parametern till 600, **obtainLimit** parametern till 5000 och **smtpNbConnection** parameter till 2. Det innebär att med 2 SMTP-anslutningar skickas 5 000 e-postmeddelanden till BCC-adressen var 10:e minut.

## Konfigurera e-postadressen för den lokala kopian (lokal) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE Lokal och hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"}


>[!IMPORTANT]
>
>Av sekretesskäl måste e-post från innehållsförteckningen behandlas av ett arkiveringssystem som kan lagra säkert personligt identifierbar information (PII).

I **config-`<instance name>.xml`** använder du följande parametrar för att definiera SMTP-e-postservern som de lagrade filerna ska överföras till:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: arkiveringsmål
* **smtpEnableTLS**: med en säker SMTP-anslutning (TLS/SSL-protokoll)
* **smtpRelayAddress**: reläadress som ska användas
* **smtpRelayPort**: reläport att använda

>[!NOTE]
>
>Om du använder ett SMTP-relä beaktas inte de ändringar i e-postmeddelanden som görs av reläet i arkiveringsprocessen.
>
>Dessutom tilldelar reläet **[!UICONTROL Sent]** status för alla e-postmeddelanden, även de som inte skickas. Därför arkiveras alla meddelanden.

## Byt till den nya e-postkontrollen {#updated-email-archiving-system--bcc-}

[!BADGE Lokal och hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"}



>[!IMPORTANT]
>
>BCC (e-postarkivering) har ändrats med Adobe Campaign 17.2 (build 8795). Om du uppgraderar från en äldre version och redan har använt e-postarkiveringsfunktioner måste du uppgradera manuellt till det nya systemet för e-postarkivering.

Om du vill göra det gör du följande ändringar i **`config-<instance>.xml`** fil:

1. Ta bort **zipPath** parametern från **`<archiving>`** nod.
1. Ange **compressionFormat** parameter till **1** vid behov.
1. Ange **archivingType** parameter till **1**.

Kontrollera att du har valt **[!UICONTROL Email BCC]** i leveransmallen eller leveransformuläret. Mer information finns i [det här avsnittet](../../delivery/using/sending-messages.md#archiving-emails).

## Bästa praxis för e-postkopia {#best-practices}

* **BCC-adresspostlåda**: Kontrollera att den har tillräcklig mottagningskapacitet för att arkivera alla e-postmeddelanden som skickas av MTA.
* **MTA-poolning**: arkiveringsfunktionen i innehållsförteckningen fungerar på MTA-nivå. Du kan duplicera alla e-postmeddelanden som skickas av MTA. Eftersom MTA kan slås samman i flera instanser (till exempel dev, test eller prod) eller till och med i flera klienter (i en miljö med mellanlagring) påverkar konfigurationen säkerheten:

   * Om du delar en MTA med flera klienter och en av dem har det här alternativet aktiverat, får den här klienten tillgång till alla e-postmeddelanden från andra klienter som delar samma MTA. För att undvika en sådan situation bör du använda olika MTA för varje kund.
   * Om du använder samma MTA för flera instanser (utveckling, test, prod) för en enskild klient, dupliceras meddelandena som skickas från alla tre instanserna med alternativet dataLogPath.

* **E-post per anslutning**: BCC-arkivering av e-post sker genom att en anslutning öppnas och alla e-postmeddelanden skickas via den anslutningen. Adobe rekommenderar att du kontaktar din interna tekniska kontakt för att kontrollera antalet e-postmeddelanden som accepteras för en viss anslutning. Om du ökar det här antalet kan det påverka genomströmningen av BCC avsevärt.
* **BCC skickar IP-adresser**: för närvarande skickas inte e-post för hemlig kopia via de vanliga MTA-proxyadresserna. I stället öppnas en direktanslutning från MTA-servern till målservern för e-post. Det innebär att du kan behöva lägga till ytterligare IP-adresser till tillåtelselista i nätverket, beroende på din e-postserverkonfiguration.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->