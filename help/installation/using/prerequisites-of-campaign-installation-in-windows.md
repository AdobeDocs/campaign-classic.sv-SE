---
title: Krav för Campaign-installation i Windows
seo-title: Krav för Campaign-installation i Windows
description: Krav för Campaign-installation i Windows
seo-description: null
page-status-flag: never-activated
uuid: 3c030186-d2ab-4845-b5c6-2ed49da00756
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: faaecbd6-f707-4307-8921-04d8993c2c47
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Krav för Campaign-installation i Windows{#prerequisites-of-campaign-installation-in-windows}

Den tekniska konfiguration och programvara som krävs för att installera Adobe Campaign finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Installationsprocessen för Adobe Campaign-servern för användning i flera instanser beskrivs nedan när du [installerar servern](../../installation/using/installing-the-server.md).

De huvudsakliga stegen är följande:

1. Installera programservern, se [Köra installationsprogrammet](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrera med en webbserver (valfritt, beroende på vilka komponenter som används), se [Konfigurera IIS-webbservern](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om den inledande konfigurationen](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>När Adobe Campaign distribueras till en Windows-miljö kan användare med nödvändiga åtkomsträttigheter använda UNC-syntax (Universal.Uniform Naming Convention) för åtkomstsökvägar under filhantering i nätverket.

