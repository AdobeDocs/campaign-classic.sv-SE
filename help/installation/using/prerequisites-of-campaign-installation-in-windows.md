---
title: Krav för installationen av Campaign i Windows
description: Krav för installationen av Campaign i Windows
page-status-flag: never-activated
uuid: 3c030186-d2ab-4845-b5c6-2ed49da00756
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: faaecbd6-f707-4307-8921-04d8993c2c47
translation-type: tm+mt
source-git-commit: f8539433274e531e34b7512ce1b6385d67e8e332
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 15%

---


# Krav för installationen av Campaign i Windows{#prerequisites-of-campaign-installation-in-windows}

Den tekniska konfiguration och programvara som behövs för att installera Adobe Campaign finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html).

Adobe Campaign serverinstallationsprocess för användning av flera instanser beskrivs nedan när du [installerar servern](../../installation/using/installing-the-server.md).

De huvudsakliga stegen är följande:

1. Installera programservern, se [Köra installationsprogrammet](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrera med en webbserver (valfritt, beroende på vilka komponenter som används), se [Konfigurera IIS-webbservern](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om den inledande konfigurationen](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>När Adobe Campaign distribueras till en Windows-miljö kan användare med nödvändiga åtkomsträttigheter använda UNC-syntax (Universal.Uniform Naming Convention) för åtkomstsökvägar under filhantering i nätverket.

