---
product: campaign
title: Startar Adobe Campaign
description: Startar Adobe Campaign
feature: Access Management, Permissions
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: 4d9c5b24-83a2-4495-a56c-5bc376d69703
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 5%

---

# Starta Adobe Campaign{#launching-adobe-campaign}



Campaign Client-konsolen är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar. Lär dig hur du hämtar och konfigurerar klientkonsolen på [den här sidan](../../installation/using/installing-the-client-console.md).

>[!CAUTION]
>
>Kontrollera system- och verktygskompatibiliteten med Adobe Campaign Client Console i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

## Starta Adobe Campaign {#starting-adobe-campaign}

Du kan starta Adobe Campaign genom att välja **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

I klientkonsolens anslutningsfönster kan du välja eller konfigurera befintliga databaser och ansluta till dem med ett användarnamn och lösenord:

![](assets/acc-logon.png)

## Anslut till Adobe Campaign {#connecting-to-adobe-campaign}

Du kan ansluta till Adobe Campaign med din Adobe ID. Mer information finns på [den här sidan](../../integrations/using/about-adobe-id.md).

Du kan även ansluta med en dedikerad inloggning/ett dedikerat lösenord:

1. Ange operatorkontots identifierare i fältet **[!UICONTROL Login]**.

   Din identifierare anges av administratören för din Adobe Campaign-plattform.

1. Ange ditt lösenord i fältet **[!UICONTROL Password]**.

   Första gången du öppnar databasen är ditt lösenord det du får av administratören. När du är ansluten kan du ändra ditt lösenord via menyn **[!UICONTROL Tools > Change password...]**. Information om operatorer och anslutningar finns i [Åtkomsthantering](../../platform/using/access-management.md).

1. Bekräfta genom att klicka på **[!UICONTROL LOG IN]**.<!--You can also press the **Enter** key to launch connection.-->

Du har nu åtkomst till [Adobe Campaign-arbetsytan](../../platform/using/adobe-campaign-workspace.md).

Vissa kortkommandon är tillgängliga på **[!UICONTROL Sign in screen]**:
* Alla objekt som kan användas kan markeras med tangenten **Tabb** (uppifrån och ned) eller tangenten **Tabb** + **Skift** (uppifrån och ned).
* Du kan även starta anslutningen genom att trycka på tangenten **Enter**.
* Du kan använda tangenten **Escape** för att återställa fälten **[!UICONTROL Login]** och **[!UICONTROL Password]** till de senast godkända anslutningsvärdena.

## Konfigurera anslutningar {#setting-up-connections}

Du kommer åt inställningarna för serveranslutningen via länken ovanför indatazonen.

![](assets/s_ncs_user_connections_management.png)

Klicka på **[!UICONTROL Add > Connection]** i fönstret **[!UICONTROL Connections]**.

Du måste sedan definiera anslutningsinställningarna. Så här gör du:

1. Ange ett **[!UICONTROL Label]** som du vill tilldela ett namn till din databasanslutning.

1. Lägg till adressen till programservern i fältet **[!UICONTROL URL]**. Kontakta administratören om du inte känner till anslutnings-URL:en.

1. Kontrollera **[!UICONTROL Connect with an Adobe ID]** för att se om operatorerna kan ansluta till konsolen med hjälp av deras Adobe ID. Mer information finns på [den här sidan](../../integrations/using/about-adobe-id.md).

1. Klicka på **[!UICONTROL OK]** för att validera.

## Operatörer och behörigheter {#operators-and-permissions}

Identifierare och lösenord för operatorer med åtkomst till programvaran och deras respektive behörigheter definieras av din Adobe Campaign-systemadministratör i noden **[!UICONTROL Administration > Access management > Operators]** i Adobe Campaign-trädet.

Den här funktionen beskrivs i avsnittet [Åtkomsthantering](../../platform/using/access-management.md).

## Koppla från Adobe Campaign {#disconnecting-from-adobe-campaign}

Om du vill koppla från Adobe Campaign använder du den första ikonen i ikonfältet.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Du kan också stänga programmet utan att logga ut först.

## Skaffa en Adobe Campaign-version {#getting-your-campaign-version}

På menyn **[!UICONTROL Help > About...]** kan du komma åt följande information:

* **version**-nummer för Campaign-klientkonsolen och programservern
* **build**-nummer för Campaign-klientkonsolen och programservern
* en länk till att kontakta Adobe kundtjänst
* länkar till Adobe sekretesspolicy, användarvillkor och cookies

![](assets/about-acc.png)

När du kontaktar kundtjänstteamet på Adobe måste du ange versionsnummer och build-nummer för Adobe Campaign klientkonsol och programserver.

**Relaterade ämnen**:

* [Adobe Campaign hjälp- och supportalternativ](../../support.md)
* [Adobe Campaign Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [Adobe Experience Cloud support- och expertsessioner](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
