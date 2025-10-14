---
product: campaign
title: Vanliga frågor
description: Vanliga frågor och svar om Adobe Campaign Classic
feature: Overview
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 9f1b0974-f8bd-430f-88fe-9c09b0074d3b
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 79%

---

# Vanliga frågor{#common-questions}



Behöver du hjälp eftersom du arbetar med Campaign Classic? Läs de tio vanligaste frågorna nedan samt andra vanliga frågor och svar på den sidan. Du kan även:

* [Titta på självstudievideor](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv)
* Hittar du inte svaret? [Fråga experten](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-classic/ct-p/adobe-campaign-classic-community)
* Behöver du support? [Mer information finns i hjälpen och supportalternativen i Campaign](../../support.md)

## &#x200B;1. Hur uppgraderar jag Campaign till den senaste versionen? {#how-can-i-upgrade-campaign-to-the-latest-version-}

Adobe Campaign Classic använder en rad olika teknologier för att leverera värde. Den här kombinationen av tekniker kräver att du regelbundet uppgraderar dina instanser i Campaign Classic för att säkerställa att de senaste versionerna används så att de kan leverera överlägsen säkerhet, stabilitet och prestanda.

Som värdkund kan ni få en årlig uppgradering av Campaign. Mer information om detta finns i [den här artikeln](../../rn/using/rn-overview.md#yearly-upgrade).

[Läs det här avsnittet](../../production/using/build-upgrade.md) för att lära dig hur du uppdaterar din miljö samt läs [vanliga frågor](../../platform/using/faq-build-upgrade.md) om det här specifika ämnet.

## &#x200B;2. Vad är arbetsflödet för att rensa databasen? {#what-is-the-database-cleanup-workflow-}

Arbetsflödet för databasrensning raderar föråldrade data för att undvika exponentiell tillväxt i databasen. Det inbyggda tekniska arbetsflödet aktiveras automatiskt utan användaråtgärder. Det är tillgänglig via **[!UICONTROL Administration > Production > Technical workflows]**-noden i Campaign Explorer.

[Klicka här för att läsa mer](../../production/using/database-cleanup-workflow.md) om arbetsflödet för databasrensning.

## &#x200B;3. Hur konfigurerar jag säkerhetszoner? {#how-can-i-configure-security-zones-}

Självbetjäningsgränssnittet i Säkerhetszoner kan användas för att hantera poster i konfigurationen av VPN-säkerhetszoner för en driftsättning av Adobe Campaign Classic. Läs [det här avsnittet](../../installation/using/security-zones.md) för att veta mer om säkerhetszoner i Campaign.

[Klicka här för att läsa mer](https://helpx.adobe.com/se/campaign/kb/configuring-security-zones-self-service.html) om självbetjäningsgränssnittet i Säkerhetszoner.

## &#x200B;4. Hur kan jag säkerställa att min leverans skickas utan fel? {#how-can-i-make-sure-my-delivery-is-sent-without-errors-}

Adobe Campaign har en uppsättning instrumentpaneler och verktyg för att övervaka e-postleveranser.

[Klicka här för att veta](../../delivery/using/about-delivery-monitoring.md) om hur du kontrollerar att dina meddelanden skickas, övervakar körningen och utför en åtgärd om ett fel inträffar.

## &#x200B;5. Kan jag övervaka arbetsflödets körning? {#can-i-monitor-workflow-execution}

Förstå hur du övervakar körningen av Campaign-arbetsflödet i [Campaign v8-dokumentationen]&#x200B;(https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution)
.html){target="_blank"}.

## &#x200B;6. Hur ansluter jag till Campaign Classic? {#how-can-i-connect-to-campaign-classic-}

För att ansluta till Adobe Campaign Classic måste du starta klientkonsolen i Adobe Campaign och ange dina inloggningsuppgifter för din instans.

[Klicka här för att läsa mer](../../platform/using/launching-adobe-campaign.md).

## &#x200B;7. Vilka system och komponenter är Campaign Classic kompatibelt med? {#which-systems-and-components-campaign-classic-is-compatible-with-}

Du kan se listan över alla system och komponenter som den senaste versionen av Campaign har stöd för i [kompatibilitetsmatrisen för Adobe Campaign Classic](../../rn/using/compatibility-matrix.md).

## &#x200B;8. Var finns Campaign Classic versionsinformation? {#where-are-campaign-classic-release-notes-}

Du kan komma åt den senaste versionsinformationen om Campaign Classic [på den här sidan](../../rn/using/latest-release.md).

## &#x200B;9. Hur gör jag för att konfigurera en domän? {#what-is-the-procedure-for-domain-delegation-}

En underdomän är en division av din domän som kan användas för att isolera dina varumärken eller olika typer av trafik (transaktionsmeddelanden och marknadsföringsinformation osv.).
Adobe tar hänsyn till domännamnssystemet (DNS) för e-postleverans vilket innebär att klienten kan behålla sitt varumärkes stil genom att använda ett DNS-alias med sina domännamn. Adobe kan även självständigt implementera alla tekniska bästa praxis som gör att kunden kan optimera levererbarheten under e-postutskick.

[Klicka här för att läsa mer](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=sv).
