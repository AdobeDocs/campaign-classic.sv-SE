---
product: campaign
title: Arbeta med Adobe Campaign och Adobe Analytics
description: Arbeta med Adobe Campaign och Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 13%

---

# Arbeta med Adobe Campaign och Adobe Analytics {#adobe-analytics-connector-gs}

Adobe Analytics Connector gör att Adobe Campaign och Adobe Analytics kan interagera via **[!UICONTROL Web Analytics connectors]**-paketet. Den skickar data till Adobe Campaign i form av segment som rör användarbeteende efter en kampanj. Omvänt skickas indikatorer och attribut för kampanjer från Adobe Campaign till Adobe Analytics.

## Garantier och krav {#adobe-analytics-connector-guardrails}

Innan du börjar arbeta med Adobe Campaign-Adobe Analytics-kontakten bör du tänka på följande skyddsanvisningar och villkor.

* För den här integreringen krävs anslutning till Campaign med Adobe Identity Management System (IMS). [Läs mer](../../integrations/using/about-adobe-id.md).

* Adobe Analytics Connector är inte kompatibel med transaktionsmeddelanden (meddelandecentret).

* Tillägget för Web Analytics-anslutningen måste installeras i din miljö via det dedikerade paketet.

   * För hybridimplementeringar och lokala implementeringar måste du följa stegen för etablering som beskrivs på den här [sidan](adobe-analytics-provisioning.md).
   * Som hoster- eller Managed Cloud Services-användare kan du kontakta Adobe för att få kontakt med Adobe Experience Cloud tjänster och lösningar.


## Konfiguration och användning {#adobe-analytics-connector-usage}

Om du vill aktivera den här integreringen måste du skapa ditt Adobe-tekniska konto enligt informationen på [den här sidan](oauth-technical-account.md).

Lär dig hur du arbetar med Adobe Campaign och Adobe Analytics i [Adobe Campaign v8-dokumentationen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.
