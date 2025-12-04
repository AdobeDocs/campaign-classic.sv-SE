---
product: campaign
title: Förstå karantänhantering
description: Förstå karantänhantering
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# Förstå karantänhantering{#understanding-quarantine-management}

>[!NOTE]
>
>Omfattande vägledning om karantänhantering finns på sidan [Kampanj v8 Karantänhantering](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines). Det här innehållet gäller både Campaign Classic v7- och Campaign v8-användare, och omfattar:
>
>* Karantän jämfört med koncept för blockeringslista
>* Varför adresser skickas till karantän (hårda/mjuka fel)
>* Mjuk felhantering och felräkningströsklar
>* Åtkomst till och identifiering av adresser i karantän
>* Ta bort adresser från karantän (automatisk, manuell, massvis)
>* Karantänhanteringsrapporter
>
>Den här sidan innehåller **Campaign Classic v7-specifik konfiguration** för karantänhantering i hybriddistributioner och lokala distributioner.

Omfattande riktlinjer för karantänhantering finns i [dokumentationen för karantänhantering för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}.

## Konfiguration av karantän {#v7-quarantine-config}

Följande konfigurationsalternativ är tillgängliga för **hybriddistributioner i Campaign Classic v7** för att anpassa karantänbeteendet.

### Konfiguration av tröskelvärde för mjukt fel {#soft-error-threshold}

För lokala installationer som använder det gamla Campaign MTA kan du ändra antalet fel och perioden mellan två fel innan en adress sätts i karantän.

Så här konfigurerar du dessa inställningar:

1. Öppna distributionsguiden från **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**
2. Navigera till **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**
3. Konfigurera:
   * **Antal fel**: Maximalt antal mjuka fel innan en adress sätts i karantän (standard: 5)
   * **Period mellan två signifikanta fel**: Tidsfönstret (i sekunder) för felräkning (standard: 86 400 sekunder = 1 dag)

När felräknaren når tröskelvärdet sätts adressen i karantän. Om det senaste allvarliga felet inträffade för mer än 10 dagar sedan initieras felräknaren om.

Mer information finns på [den här sidan](communication-channels.md) under **Leveranssändning** > **Konfigurera återförsök**.

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 hanteras inställningar för nya försök och feltrösklar av Adobe utifrån IP-prestanda och domänens anseende. Ingen konfiguration krävs.

### Arbetsflöde för databasrensning {#database-cleanup-workflow}

För lokala installationer tar det tekniska arbetsflödet **[!UICONTROL Database cleanup]** automatiskt bort adresser i karantän som matchar specifika villkor.

Få åtkomst till det här arbetsflödet från **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**.

Arbetsflödet tar bort adresser från karantän i följande fall:

* Adresser i statusen **[!UICONTROL With errors]** efter en slutförd leverans
* Adresser i statusen **[!UICONTROL With errors]** om den senaste mjuka studsen inträffade för mer än 10 dagar sedan
* Adresser i statusen **[!UICONTROL With errors]** med felet **[!UICONTROL Mailbox full]** efter 30 dagar

Se till att arbetsflödet körs regelbundet (rekommenderas: dagligen) för att upprätthålla karantänlistans hygien.

Mer information om databasrensning finns i [det här avsnittet](../../production/using/database-cleanup-workflow.md).

>[!NOTE]
>
>För användare av hanterade molntjänster i Campaign v8 övervakas och hanteras arbetsflödet för databasrensning av Adobe.

### Karantänsdetaljer för push-meddelanden {#push-quarantine-specifics}

För Campaign Classic v7 följer karantänmekanismen för push-meddelanden med kanalspecifika beteenden.

För push-meddelanden för **iOS** och **Android** använder karantänmekanismen enhetstoken i stället för e-postadresser. När ett mobilprogram avinstalleras eller installeras om placeras den associerade token i karantän.

Detaljerad information om karantänscenarier för push-meddelanden (iOS- och Android-feltyper, återförsöksbeteende osv.) finns i [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} -dokumentationen som innehåller omfattande feltyper för push-meddelanden.

### Specifikationer för SMS-karantän {#sms-quarantine-specifics}

För Campaign Classic v7 följer SMS-karantäner den allmänna karantänmekanismen med vissa kanalspecifika beteenden som är relaterade till telefonnummer i stället för e-postadresser.

SMS-karantänmekanismen varierar beroende på vilken koppling som används:

* **Standard SMPP-anslutningar**: Felkvalificeringsregler som definieras i **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** gäller för SMS-leveranser.

* **Utökad generisk SMPP-anslutning**: Felhantering hanteras på olika sätt med reguljära uttryck (regex) för att tolka SR-meddelanden som returneras av SMSC-providern.

Detaljerad information om SMS-karantänscenarier och feltyper finns i [Förstå leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} -dokumentationen som innehåller omfattande tabeller för feltyper av SMS.

## Relaterade ämnen

* [Karantänhantering](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (Campaign v8-dokumentation)
* [Om leveransfel](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (dokumentation för Campaign v8)
* [Bästa praxis för leverans](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"} (dokumentation för Campaign v8)
* [Arbetsflöde för databasrensning](../../production/using/database-cleanup-workflow.md) (v7-hybrid/lokal)
* [Konfigurera leveransförsök](communication-channels.md) (v7-hybrid/lokal)
