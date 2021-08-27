---
product: campaign
title: Spåra och övervaka meddelanden
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 3%

---

# Spåra och övervaka {#track-and-monitor}

![](../../assets/common.svg)

Klickade du på knappen **Skicka**? Låt oss se vad som händer. När leveransen har skickats kan du med Adobe Campaign hålla reda på skickade meddelanden och se hur mottagarna svarar på leveransen. Detta hjälper er att förbättra era framtida utskick och optimera era nästa kampanjer.

## Övervaka leveranser {#monitoring-deliveries}

För att kunna styra era kampanjer måste ni se till att meddelandet verkligen har levererats till mottagarna.

På kontrollpanelen för kampanjleverans kan du kontrollera bearbetade meddelanden och leveransgranskningsloggar.
Du kan också styra status för meddelandena i leveransloggarna. [Läs mer](about-delivery-monitoring.md).

Vad händer om leveranserna inte skickas och deras status förblir **Väntande**?

* Körningsprocessen väntar på att vissa resurser ska vara tillgängliga. MTA har kanske inte startats.
Kontrollera att mta@instance startas på dina MTA-servrar och starta MTA-modulen om det behövs. [Läs mer](../../production/using/administration.md).

* Leveransen kan ha en tillhörighet som inte har konfigurerats på den sändande instansen.
Tips: Kontrollera konfigurationen för trafikhantering (IP-tillhörighet). Mer information finns i Kontrollera utgående SMTP-trafik.

>[!NOTE]
>
>Dessa steg kan bara utföras av en expertanvändare.

## Spåra {#tracking-deliveries}

Om du vill veta mer om mottagarnas beteende kan du spåra hur de reagerar på en leverans: mottagning, öppning, klickningar på länkar, avbeställningar osv. I Campaign Classic visas den här informationen på fliken Spårning för mottagarna som leveransmålet gäller och på fliken Spårning för leveransen.

**Tips**: Spårning av meddelanden är aktiverat som standard. Om du vill konfigurera URL-adresser väljer du alternativet Visa URL-adresser i det nedre avsnittet av leveransguiden. För varje URL för meddelandet kan du välja om spårning ska aktiveras.

Mer information finns i avsnittet [Configuring tracking](how-to-configure-tracked-links.md) och beskrivningen av [spårningsindikatorer](../../reporting/using/delivery-reports.md#tracking-indicators).

## Leveransprestanda {#delivery-performances}

Om du vill mäta den hastighet med vilken meddelandena levereras kan du styra leveransflödet. Kriterierna är antalet meddelanden som skickas per timme och storleken på meddelandena (i bitar per sekund). Mer information finns i [Leveransflöde](../../reporting/using/global-reports.md#delivery-throughput).

**Tips**:

* Behåll inte leveranser i felaktigt tillstånd för instansen eftersom detta bevarar tillfälliga tabeller och påverkar prestandan.

* Ta bort leveranser som inte längre behövs och inaktiva mottagare från databasen för att upprätthålla adresskvaliteten.

* Försök inte schemalägga stora leveranser tillsammans. Observera att det kan ta 5 till 10 minuter att sprida belastningen jämnt över systemet.

## Leveransfelsökning {#delivery-troubleshooting}

Du kan utföra specifika åtgärder när du stöter på leveransproblem:

* [Leveransproblem](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Bildvisningsproblem](../../production/using/image-display-issues.md)

* [Problem med leveransresultat](delivery-performances.md)

* [Temporära filproblem](../../production/using/temporary-files.md)  - endast  *lokala kunder*
