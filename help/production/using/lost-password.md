---
product: campaign
title: Borttappat lösenord
description: Borttappat lösenord
feature: Monitoring, Access Management
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 7%

---

# Borttappat lösenord{#lost-password}



Du kan ändra eller återställa ett förlorat lösenord.
Det finns två möjliga scenarier:

* [Lösenord som gått förlorat av en Adobe Campaign-operatör](#password-lost-by-campaign-operator)
* [Lösenordet har tagits bort](#internal-password-lost) (endast lokala kunder)

## Lösenord som har gått förlorat av en kampanjoperator {#password-lost-by-campaign-operator}

Om en Adobe Campaign-operator förlorar sitt lösenord kan du ändra det.
Gör så här:

1. Anslut via en operator med administratörsbehörighet.
1. Högerklicka på en operator.
1. Välj **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Ange operatorns nya lösenord. Vi rekommenderar att operatorn ändrar sitt lösenord när han/hon först ansluter igen.

## Lösenordet har tagits bort {#internal-password-lost}

>[!NOTE]
>
>Detta avsnitt gäller endast lokala kunder.

Om det interna lösenordet går förlorat måste du initiera om det.
Gör så här:

1. Redigera **/usr/local/neolane/nl6/conf/serverConf.xml** -fil.

1. Gå till **internalPassword** linje.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Ta bort strängen inom citattecken, i det här fallet: **myPassword**

   Du får alltså följande rad:

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. Spara ändringarna och stäng filen.

1. Konfigurera det nya lösenordet. Ange följande kommandon om du vill göra det:

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Nu kan du använda ditt nya lösenord för att ansluta till **Intern** läge.
