---
title: Startar Adobe Campaign
seo-title: Startar Adobe Campaign
description: Startar Adobe Campaign
seo-description: null
page-status-flag: never-activated
uuid: c1c5bb0d-ae8e-4b0e-ab39-8b2291162557
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 6652b081-66b6-47a8-97e5-383e3251647e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 84f06afb36aa6a9fa13db1fda7034389b762eb99
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Startar Adobe Campaign{#launching-adobe-campaign}

Campaign Client-konsolen är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar. Lär dig hur du hämtar och konfigurerar klientkonsolen på [den här sidan](../../installation/using/installing-the-client-console.md).

## Startar Adobe Campaign {#starting-adobe-campaign}

Du kan starta Adobe Campaign genom att välja **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

I klientkonsolens anslutningsfönster kan du välja eller konfigurera befintliga databaser och ansluta till dem med ett användarnamn och lösenord:

![](assets/s_ncs_user_login.png)

## Ansluta till Adobe Campaign {#connecting-to-adobe-campaign}

Du kan ansluta till Adobe Campaign med Adobe ID. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

Du kan även ansluta med en dedikerad inloggning/ett dedikerat lösenord:

1. Ange operatorkontots identifierare i **[!UICONTROL login]** fältet.

   Din identifierare anges av administratören för din Adobe Campaign-plattform.

1. Ange ditt lösenord i **[!UICONTROL Password]** fältet.

   Första gången du öppnar databasen är ditt lösenord det du får av administratören. När du är ansluten kan du ändra ditt lösenord via **[!UICONTROL Tools > Change password...]** menyn. Information om operatorer och anslutningar finns i [Åtkomsthantering](../../platform/using/access-management.md).

1. Bekräfta genom **[!UICONTROL Log in]** att klicka.

Nu kan du komma åt arbetsytan [i](../../platform/using/adobe-campaign-workspace.md)Adobe Campaign.

## Konfigurera anslutningar {#setting-up-connections}

Du kommer åt inställningarna för serveranslutningen via länken ovanför indatazonen.

![](assets/s_ncs_user_connections_management.png)

Klicka på i **[!UICONTROL Connections]** fönstret **[!UICONTROL Add > Connection]**.

![](assets/s_ncs_user_add_connexion.png)

Du måste sedan definiera anslutningsinställningarna. Så här gör du:

1. Ange ett namn **[!UICONTROL Label]** som ska tilldelas databasanslutningen.

1. Lägg till adressen till programservern i **[!UICONTROL URL]** fältet. Kontakta administratören om du inte känner till anslutnings-URL:en.

1. Kontrollera **[!UICONTROL Connect with an Adobe ID]** att operatorerna har anslutit till konsolen med hjälp av Adobe ID. For more on this, refer to [this page](../../integrations/using/about-adobe-id.md).

1. Klicka **[!UICONTROL OK]** för att validera.

## Operatörer och behörigheter {#operators-and-permissions}

Identifierare och lösenord för operatorer med åtkomst till programvaran och deras respektive behörigheter definieras av systemadministratören i Adobe Campaign i noden **[!UICONTROL Administration > Access management > Operators]** i Adobe Campaign-trädet.

Den här funktionen beskrivs i avsnittet [Åtkomsthantering](../../platform/using/access-management.md) .

## Kopplar från Adobe Campaign {#disconnecting-from-adobe-campaign}

Om du vill koppla från Adobe Campaign använder du den första ikonen i ikonfältet.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Du kan också stänga programmet utan att logga ut först.

## Hämta Campaign-versionen {#getting-your-campaign-version}

På **[!UICONTROL Help > About...]** menyn kommer du åt följande information:

* **versionsnummer** ,
* **build** number,
* en länk för att kontakta supporten för Adobe Campaign.

   >[!CAUTION]
   >
   >När ni kontaktar Adobes supportteam måste ni ange versionsnumret och build-numret för er Campaign-klientkonsol och applikationsserver.

