---
title: Konfiguration
seo-title: Konfiguration
description: Konfiguration
seo-description: null
page-status-flag: never-activated
uuid: 4316d4b2-0964-4e25-9e4f-f2378f044c85
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 12f13b8d-afc3-4b55-a31b-080d31f84fc9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 779d9162b7296339a796512838612ede1186ddcc

---


# Konfiguration{#configuration}

## Ändra lyssningsporten för systemlogd {#changing-the-syslogd-listening-port}

Som standard är **systemets** avlyssningsport 666 (udp). Du kan ändra den med en miljövariabel om det behövs.

När variabeln har konfigurerats beaktas den av alla Adobe Campaign-moduler.

### I Linux {#in-linux}

Redigera filen **customer.sh** och lägg till följande rad:

```
export TRACE_ADDR=localhost:<listening port>
```

### I Windows {#in-windows}

Du måste skapa miljövariabeln **TRACE_ADDR** med **localhost** -värdet: **`<listening port="" />`**.

>[!CAUTION]
>
>Vi rekommenderar att du kör några tester för att kontrollera att plattformen fungerar när du har skapat den här miljövariabeln.

## Konfigurera säkerhetszoner {#configuring-security-zones}

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Konfigurationen av den tekniska zonen utförs i konfigurationsfilen för Adobe Campaign-servern. Länkningen av en operator till en säkerhetszon måste definieras i konsolen ( **[!UICONTROL Administration > Access management > Operators]** nod).

>[!NOTE]
>
>Mer information om hur du konfigurerar säkerhetszoner finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#defining-security-zones).

