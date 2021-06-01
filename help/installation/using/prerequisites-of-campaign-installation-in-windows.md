---
product: campaign
title: Krav för installationen av Campaign i Windows
description: Krav för installationen av Campaign i Windows
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Kom igång med att installera Campaign i Windows {#prerequisites-of-campaign-installation-in-windows}

Den tekniska konfiguration och programvara som behövs för att installera Adobe Campaign finns i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Installationsprocessen för Adobe Campaign-servern för användning av flera instanser beskrivs nedan i [Installera servern](../../installation/using/installing-the-server.md).

De huvudsakliga stegen är följande:

1. Installera programservern, se [Köra installationsprogrammet](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrera med en webbserver (valfritt, beroende på vilka komponenter som används), se [Konfigurera IIS-webbservern](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om inledande konfiguration](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>När Adobe Campaign distribueras till en Windows-miljö kan användare med nödvändiga åtkomsträttigheter använda UNC-syntax (Universal.Uniform Naming Convention) för åtkomstsökvägar under filhantering i nätverket.
