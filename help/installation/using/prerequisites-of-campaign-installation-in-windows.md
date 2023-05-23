---
product: campaign
title: Krav för installationen av Campaign i Windows
description: Krav för installationen av Campaign i Windows
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Kom igång med att installera Campaign i Windows {#prerequisites-of-campaign-installation-in-windows}



Den tekniska konfiguration och programvara som behövs för att installera Adobe Campaign finns i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

Adobe Campaign serverinstallationsprocess för användning av flera instanser beskrivs nedan [Installera servern](../../installation/using/installing-the-server.md).

De huvudsakliga stegen är följande:

1. Installera programservern, se [Köra installationsprogrammet](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. Integrera med en webbserver (valfritt, beroende på vilka komponenter som används), se [Konfigurera IIS-webbservern](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om inledande konfiguration](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>När Adobe Campaign distribueras till en Windows-miljö kan användare med nödvändiga åtkomsträttigheter använda UNC-syntax (Universal.Uniform Naming Convention) för åtkomstsökvägar under filhantering i nätverket.
