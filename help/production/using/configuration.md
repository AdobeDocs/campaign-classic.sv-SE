---
product: campaign
title: Konfiguration
description: Konfiguration
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 1%

---

# Konfiguration{#configuration}

![](../../assets/v7-only.svg)

## Ändra lyssningsporten för systemlogd {#changing-the-syslogd-listening-port}

Som standard är avlyssningsporten **syslogd** 666 (udp). Du kan ändra den med en miljövariabel om det behövs.

När variabeln har konfigurerats beaktas den av alla Adobe Campaign-moduler.

### I Linux {#in-linux}

Redigera filen **customer.sh** och lägg till följande rad:

```
export TRACE_ADDR=localhost:<listening port>
```

### I Windows {#in-windows}

Du måste skapa miljövariabeln **TRACE_ADDR** med värdet **localhost**: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Vi rekommenderar att du kör några tester för att kontrollera att plattformen fungerar när du har skapat den här miljövariabeln.

## Konfigurera säkerhetszoner {#configuring-security-zones}

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Konfigurationen av den tekniska zonen utförs i konfigurationsfilen för Adobe Campaign-servern. Länkningen av en operator till en säkerhetszon måste definieras i konsolen ( **[!UICONTROL Administration > Access management > Operators]**-nod).

>[!NOTE]
>
>Mer information om hur du konfigurerar säkerhetszoner finns i [det här avsnittet](../../installation/using/security-zones.md).
