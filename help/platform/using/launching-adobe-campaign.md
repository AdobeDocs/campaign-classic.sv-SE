---
solution: Campaign Classic
product: campaign
title: Starta Adobe Campaign
description: Starta Adobe Campaign
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 8%

---


# Starta Adobe Campaign{#launching-adobe-campaign}

Campaign Client-konsolen är en avancerad klient som gör att du kan ansluta till dina Campaign-programservrar. Lär dig hur du hämtar och konfigurerar klientkonsolen på [den här sidan](../../installation/using/installing-the-client-console.md).

## Startar Adobe Campaign {#starting-adobe-campaign}

Du kan starta Adobe Campaign genom att välja **[!UICONTROL Start / All Programs / Adobe Campaign v.X / Adobe Campaign client console]**.

I klientkonsolens anslutningsfönster kan du välja eller konfigurera befintliga databaser och ansluta till dem med ett användarnamn och lösenord:

![](assets/acc-logon.png)

## Ansluter till Adobe Campaign {#connecting-to-adobe-campaign}

Du kan ansluta till Adobe Campaign med din Adobe ID. Se denna [sida](../../integrations/using/about-adobe-id.md) för mer information om detta.

Du kan även ansluta med en dedikerad inloggning/ett dedikerat lösenord:

1. Ange operatorkontots identifierare i fältet **[!UICONTROL login]**.

   Din identifierare anges av administratören för din Adobe Campaign-plattform.

1. Ange ditt lösenord i fältet **[!UICONTROL Password]**.

   Första gången du öppnar databasen är ditt lösenord det du får av administratören. När du är ansluten kan du ändra ditt lösenord via menyn **[!UICONTROL Tools > Change password...]**. Information om operatorer och anslutningar finns i [Åtkomsthantering](../../platform/using/access-management.md).

1. Bekräfta genom att klicka på **[!UICONTROL LOG IN]**.

Nu kan du komma åt [Adobe Campaign-arbetsytan](../../platform/using/adobe-campaign-workspace.md).

## Konfigurera anslutningar {#setting-up-connections}

Du kommer åt inställningarna för serveranslutningen via länken ovanför indatazonen.

![](assets/s_ncs_user_connections_management.png)

Klicka på **[!UICONTROL Add > Connection]** i fönstret **[!UICONTROL Connections]**.

Du måste sedan definiera anslutningsinställningarna. Så här gör du:

1. Ange ett **[!UICONTROL Label]**-värde för att tilldela en databasanslutning ett namn.

1. Lägg till adressen till programservern i fältet **[!UICONTROL URL]**. Kontakta administratören om du inte känner till anslutnings-URL:en.

1. Kontrollera **[!UICONTROL Connect with an Adobe ID]** för att se om operatorerna kan ansluta till konsolen med sin Adobe ID. Se denna [sida](../../integrations/using/about-adobe-id.md) för mer information om detta.

1. Klicka på **[!UICONTROL OK]** för att validera.

## Operatorer och behörigheter {#operators-and-permissions}

Identifierare och lösenord för operatorer med åtkomst till programvaran och deras respektive behörigheter definieras av din Adobe Campaign-systemadministratör i noden **[!UICONTROL Administration > Access management > Operators]** i Adobe Campaign-trädet.

Den här funktionen beskrivs i avsnittet [Åtkomsthantering](../../platform/using/access-management.md).

## Kopplar från Adobe Campaign {#disconnecting-from-adobe-campaign}

Om du vill koppla från Adobe Campaign använder du den första ikonen i ikonfältet.

![](assets/s_ncs_user_deconnexion.png)

>[!NOTE]
>
>Du kan också stänga programmet utan att logga ut först.

## Hämta din Adobe Campaign-version {#getting-your-campaign-version}

På **[!UICONTROL Help > About...]**-menyn kan du komma åt följande information:

* **versionsnummer** för Campaign-klientkonsolen och programservern
* **build-nummer** för Campaign-klientkonsolen och programservern
* en länk till att kontakta Adobe kundtjänst
* länkar till Adobe sekretesspolicy, användarvillkor och cookies

![](assets/about-acc.png)

När du kontaktar kundtjänstteamet på Adobe måste du ange versionsnummer och build-nummer för Adobe Campaign klientkonsol och programserver.

Om du kör på [Campaign Gold Standard-versionen](../../rn/using/gold-standard.md) måste du också dela SHA/1-tecknen som visas i rutan **[!UICONTROL About]**. Exempel: för Guld **Standard 10** kommer build-numret att visa **build 9032@efd8a94**, vilket visas nedan:

![](assets/about-acc-gs.png)

Läs mer om Gold Standard [i den här artikeln](https://helpx.adobe.com/se/campaign/kb/gold-standard.html).

**Relaterade ämnen**:

* [Adobe Campaign hjälp- och supportalternativ](https://helpx.adobe.com/se/campaign/kb/ac-support.html#acc-support)
* [Adobe Software Distribution](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html)
* [Adobe Experience Cloud support- och expertsessioner](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
