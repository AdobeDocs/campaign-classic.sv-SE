---
product: campaign
title: Startar Adobe Campaign
description: Startar Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b4059e43d98643f0f8b5b3f68f03e10b755e8ba3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 1%

---

# Starta Adobe Campaign {#launching-adobe-campaign}

Campaign Client-konsolen är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar. Lär dig hur du hämtar och konfigurerar klientkonsolen på [den här sidan](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Kontrollera system- och verktygskompatibiliteten med Adobe Campaign Client Console i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Starta Adobe Campaign {#starting-adobe-campaign}

Du kan starta Adobe Campaign genom att välja **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

I klientkonsolens anslutningsfönster kan du välja eller konfigurera befintliga databaser och ansluta till dem med ett användarnamn och lösenord:

![](assets/acc-logon.png)

## Anslut till Adobe Campaign {#connecting-to-adobe-campaign}

### Kommunicera med din Adobe ID

Kampanjanvändare ansluter till Adobe Campaign-konsolen med sin Adobe ID via Adobe Identity Management System (IMS). De kan använda samma ID för alla Adobe-lösningar. Anslutningen sparas när du använder Adobe Campaign med andra lösningar. Läs mer om Adobe IMS [på den här sidan](https://helpx.adobe.com/se/enterprise/using/identity.html).

Information om hur du konfigurerar Campaign Classic v7-anslutningen med Adobe Identity Management Service (IMS) finns på [den här sidan](../../integrations/using/about-adobe-id.md).

Lär dig hur du ansluter till Campaign med din Adobe ID i [Campaign v8-dokumentationen (konsolen)](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/new/connect){target=_blank} när konfigurationen är klar.


### Anslut med en inloggning/ett lösenord

Du kan även ansluta med en dedikerad inloggning/ett dedikerat lösenord. Den här anslutningen kallas för Campaign &#39;Native Authentication&#39;:

1. Ange operatorkontots identifierare i fältet **[!UICONTROL Login]**.

   Din identifierare anges av administratören för din Adobe Campaign-plattform.

1. Ange ditt lösenord i fältet **[!UICONTROL Password]**.

   Första gången du öppnar databasen är ditt lösenord det du får av administratören. När du är ansluten kan du ändra ditt lösenord via menyn **[!UICONTROL Tools > Change password...]**. Information om operatorer och anslutningar finns i [Åtkomsthantering](../../platform/using/access-management.md).

1. Klicka på **[!UICONTROL LOG IN]** för att bekräfta.

Du har nu åtkomst till [Adobe Campaign-arbetsytan](../../platform/using/adobe-campaign-workspace.md).

## Konfigurera anslutningar {#setting-up-connections}

Du kommer åt inställningarna för serveranslutningen via länken ovanför indatazonen.

![](assets/s_ncs_user_connections_management.png)

Lär dig hur du konfigurerar anslutningar i [dokumentationen för Campaign v8 (konsolen)](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/new/connect#create-your-connection){target=_blank}.

## Operatörer och behörigheter {#operators-and-permissions}

Identifierare och lösenord för operatorer med åtkomst till programvaran och deras respektive behörigheter definieras av din Adobe Campaign-systemadministratör i noden **[!UICONTROL Administration > Access management > Operators]** i Adobe Campaign-trädet.

Den här funktionen beskrivs i avsnittet [Åtkomsthantering](../../platform/using/access-management.md).

## Skaffa en Adobe Campaign-version {#getting-your-campaign-version}

På menyn **[!UICONTROL Help > About...]** kan du komma åt följande information:

* **version**-nummer för Campaign-klientkonsolen och programservern
* **build**-nummer för Campaign-klientkonsolen och programservern
* en länk för att kontakta Adobe kundtjänst
* länkar till Adobe integritetspolicy, användarvillkor och cookies

![](assets/about-acc.png)

När du kontaktar Adobe kundtjänstteam måste du ange versionsnummer och byggnummer för Adobe Campaign klientkonsol och programserver.

