---
product: campaign
title: SMS-anslutningsmigrering stöds inte
description: Migrera en SMS-koppling som inte stöds till den utökade allmänna SMPP-anslutningen
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---

# Migrera en SMS-koppling som inte stöds till den utökade allmänna SMPP-anslutningen{#unsupported-connector-migration}

![](../../assets/v7-only.svg)

Från och med version 20.2 har äldre anslutningar tagits bort. Det här dokumentet hjälper dig att migrera anslutningar som fortfarande körs på det gamla systemet till den rekommenderade SMPP-anslutningen.

>[!CAUTION]
>
>Migreringen är inte obligatorisk, men rekommenderas av Adobe och säkerställer att du kör den senaste versionen av programmet som stöds.

## Om SMS-anslutningar {#about-sms-connectors}

Följande kopplingar är borttagna från och med version 20.2:

* **[!UICONTROL Generic SMPP]** (SMPP version 3.4 med stöd för binärt läge)
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

Funktioner som inte används är fortfarande tillgängliga och stöds, men de kommer inte att förbättras ytterligare. Vi rekommenderar att du använder **[!UICONTROL Extended generic SMPP]** koppling.

Mer information om borttagna och borttagna funktioner finns i [page](../../rn/using/deprecated-features.md).

Gamla SMS-anslutningar använder Java SMS-kopplingen som överför webbprocessen. Migrera till nya **[!UICONTROL Extended Generic SMPP]** kommer att flytta den här inläsningen till den MTA som stöder den.

## Migrera till den utökade allmänna SMPP-anslutningen {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>Även om du kan transponera parametrarna konfigurerar du **[!UICONTROL Extended Generic SMPP]** kräver att du pratar med leverantören som ger dig den information som behövs för att fylla i resten av parametrarna. Se denna [sida](sms-protocol.md) för mer information om detta.

Först måste du skapa ett nytt **[!UICONTROL Extended Generic SMPP]** externt konto och sedan kan du kanske ta med vissa parametrar. Du hittar de detaljerade stegen i det här [page](sms-set-up.md#creating-an-smpp-external-account).

Du måste nu fylla i parametrarna från **[!UICONTROL Mobile]** -flik i dina nyskapade **[!UICONTROL Extended Generic SMPP]** externt konto beroende på din tidigare anslutning.

### Från den allmänna kopplingen {#from-generic-connector}

När du väljer **[!UICONTROL Generic]** bör du ha en anpassad JavaScript-koppling som anpassar sig efter varje situation.

Om du vet att den här kopplingen redan använder SMPP-protokollet kan du migrera till **[!UICONTROL Extended Generic SMPP]** koppling. Om så inte är fallet, fråga leverantören om de stöder SMPP-protokollet och konfigurera en ny anslutning med hjälp av en konsult.

Från **[!UICONTROL Generic]** kan du använda din nya **[!UICONTROL Extended SMPP]** konto:

![](assets/smpp_generic.png)

I **[!UICONTROL Connection Settings]** tab:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### Från den allmänna SMPP-anslutningen {#from-generic-smpp-connector}

Från **[!UICONTROL Generic SMPP]** kan du använda din nya **[!UICONTROL Extended SMPP]** konto:

![](assets/smpp_generic_2.png)

I **[!UICONTROL Connection Settings]** tab:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

I **[!UICONTROL SMPP Channel Settings]** tab:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

I **[!UICONTROL Mapping of Encoding]** tab:

* **[!UICONTROL Outbound SMS coding]**

I **[!UICONTROL SMSC specificities]** tab:

* **[!UICONTROL Coding when sending]** motsvarar **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** motsvarar **[!UICONTROL ID Format in the SR]**

### Från Sybase365-kontakten {#from-sybase}

Från **[!UICONTROL Sybase365]** kan du använda din nya **[!UICONTROL Extended SMPP]** konto:

![](assets/smpp_3.png)

I **[!UICONTROL Connection Settings]** tab:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### Från CLX-koppling {#from-clx}

Från **[!UICONTROL CLX]** kan du använda din nya **[!UICONTROL Extended SMPP]** konto:

![](assets/smpp_4.png)

I **[!UICONTROL Connection Settings]** tab:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

I **[!UICONTROL SMPP Channel Settings]** tab:

* **[!UICONTROL Source number]**

I **[!UICONTROL SMSC specificities]** tab:

* **[!UICONTROL Coding when sending]** motsvarar **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** motsvarar **[!UICONTROL ID Format in the SR]**

### Från Tele2-kontakten {#from-tele2}

Från **[!UICONTROL Tele2]** kan du använda din nya **[!UICONTROL Extended SMPP]** konto:

![](assets/smpp_6.png)

I **[!UICONTROL Connection Settings]** tab:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

I **[!UICONTROL SMPP Channel Settings]** tab:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

I **[!UICONTROL Mapping of Encoding]** tab:

* **[!UICONTROL Outbound SMS coding]**

### Från O2-kontakten {#from-O2}

Från **[!UICONTROL O2]** kan du använda din nya **[!UICONTROL Extended SMPP]** konto:

![](assets/smpp_5.png)

I **[!UICONTROL Connection Settings]** tab:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

I **[!UICONTROL SMPP Channel Settings]** tab:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
