---
product: campaign
title: Ytterligare konfiguration
description: Konfiguration
feature: Monitoring, Configuration
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
exl-id: 80d388fd-873c-4a08-b8b6-697988f2a18c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 5%

---

# Konfiguration{#configuration}



## Ändra lyssningsporten för systemlogd {#changing-the-syslogd-listening-port}

Som standard är **syslogd** avlyssningsporten är 666 (udp). Du kan ändra den med en miljövariabel om det behövs.

När variabeln har konfigurerats beaktas den av alla Adobe Campaign-moduler.

### I Linux {#in-linux}

Redigera **customer.sh** och lägg till följande rad:

```
export TRACE_ADDR=localhost:<listening port>
```

### I Windows {#in-windows}

Du måste skapa **TRACE_ADDR** systemvariabel med **localhost** värde: **`<listening port="" />`**.

>[!IMPORTANT]
>
>Vi rekommenderar att du kör några tester för att kontrollera att plattformen fungerar när du har skapat den här miljövariabeln.

## Konfigurera säkerhetszoner {#configuring-security-zones}

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Konfigurationen av den tekniska zonen utförs i konfigurationsfilen för Adobe Campaign-servern. Länkningen av en operator till en säkerhetszon måste definieras i konsolen ( **[!UICONTROL Administration > Access management > Operators]** nod).

>[!NOTE]
>
>Mer information om hur du konfigurerar säkerhetszoner finns i [det här avsnittet](../../installation/using/security-zones.md).
