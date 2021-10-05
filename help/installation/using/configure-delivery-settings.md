---
product: campaign
title: Konfigurering av inställningar för kampanjleverans
description: Lär dig hur du konfigurerar inställningar för kampanjleverans
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# Konfigurera leveransinställningar {#delivery-settings}

![](../../assets/v7-only.svg)

Leveransparametrarna måste konfigureras i mappen **serverConf.xml**.

* **DNS-konfiguration**: Ange leveransdomänen och IP-adresserna (eller värddatorn) för de DNS-servrar som används för att svara på DNS-frågor av MX-typ som görs av MTA-modulen från  **`<dnsconfig>`** och med.

   >[!NOTE]
   >
   >Parametern **nameServers** är nödvändig för en installation i Windows. För en installation i Linux måste den lämnas tom.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Du kan även göra följande konfigurationer beroende på dina behov och inställningar: konfigurera en [SMTP-relä](#smtp-relay), anpassa antalet [MTA-underordnade processer](#mta-child-processes), [Hantera utgående SMTP-trafik](#managing-outbound-smtp-traffic-with-affinities).

## SMTP-relä {#smtp-relay}

MTA-modulen fungerar som en intern e-postöverföringsagent för SMTP-sändning (port 25).

Det är dock möjligt att ersätta den med en reläserver om säkerhetsprincipen kräver det. I så fall blir den globala genomströmningen relä (förutsatt att reläservergenomströmningen är lägre än Adobe Campaign).

I det här fallet anges dessa parametrar genom att SMTP-servern konfigureras i **`<relay>`**-avsnittet. Du måste ange IP-adressen (eller värddatorn) för den SMTP-server som används för att överföra post och dess associerade port (25 som standard).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Det här operativläget innebär allvarliga leveransbegränsningar eftersom det kan minska genomströmningen avsevärt på grund av reläserverns inneboende prestanda (latens, bandbredd...). Dessutom kommer kapaciteten att kvalificera synkrona leveransfel (som upptäcks genom analys av SMTP-trafik) att vara begränsad och det går inte att skicka om reläservern inte är tillgänglig.

## MTA-underprocesser {#mta-child-processes}

Det går att styra antalet underordnade processer (maxSpareServers som standard 2) för att optimera sändningsprestanda enligt serverns processorkraft och tillgängliga nätverksresurser. Den här konfigurationen ska göras i avsnittet **`<master>`** i MTA-konfigurationen på varje enskild dator.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Se även [E-postoptimering](../../installation/using/email-deliverability.md#email-sending-optimization).

## Hantera utgående SMTP-trafik med tillhörigheter {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>Tillhörighetskonfigurationen måste vara konsekvent från en server till en annan. Vi rekommenderar att du kontaktar Adobe för tillhörighetskonfiguration eftersom konfigurationsändringar bör replikeras på alla programservrar som kör MTA.

Du kan förbättra utgående SMTP-trafik genom tillhörigheter med IP-adresser.

Gör så här:

1. Ange tillhörigheterna i **`<ipaffinity>`**-avsnittet i filen **serverConf.xml**.

   En tillhörighet kan ha flera olika namn: om du vill separera dem använder du tecknet **;**.

   Exempel:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Se filen **serverConf.xml** för att se de relevanta parametrarna.

1. Om du vill aktivera tillhörighetsval i listrutorna måste du lägga till tillhörighetsnamn i uppräkningen **IPAfinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Uppräkningarna beskrivs i [det här dokumentet](../../platform/using/managing-enumerations.md).

   Du kan sedan välja den tillhörighet som ska användas, som visas nedan för typologier:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Du kan även läsa [Leveransserverkonfiguration](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Relaterade ämnen**
* [Tekniska e-postkonfigurationer](email-deliverability.md)
* [Använda MX-servrar med Campaign](using-mx-servers.md)
* [Konfigurera dold e-postkopia](email-archiving.md)
