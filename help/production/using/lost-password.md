---
product: campaign
title: Borttappat lösenord
description: Borttappat lösenord
feature: Monitoring, Access Management
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 3%

---

# Borttappat lösenord{#lost-password}

>[!NOTE]
>
>Den här sidan gäller endast för operatorer som ansluter till Campaign med inbyggd autentisering.

Du kan ändra eller återställa ett förlorat lösenord.
Det finns två möjliga scenarier:

* [Lösenord som gått förlorat av en Adobe Campaign-operatör](#password-lost-by-campaign-operator)
* [Lösenordet har tagits bort](#internal-password-lost) (endast lokala kunder)

## Lösenord som har gått förlorat av en kampanjoperator {#password-lost-by-campaign-operator}

Om en Adobe Campaign-operator förlorar sitt lösenord kan du ändra det.

>[!NOTE]
>
>Den här proceduren gäller endast för operatorer som ansluter till Campaign med inbyggd autentisering. För Adobe IMS-autentisering, se [den här dokumentationen](https://helpx.adobe.com/ie/manage-account/using/change-or-reset-password.html){target="_blank"}.

Så här återställer du ett Campaign-lösenord:

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

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. Ta bort strängen inom citattecken, i det här fallet: `myPassword`. Du får följande rad:

   ```xml
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/>
   ```

1. Spara ändringarna och stäng filen.

1. Stoppa `nlserver` -processen.

1. Konfigurera det nya lösenordet. Ange följande kommandon om du vill göra det:

   ```javascript
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. Starta `nlserver` -processen.

1. Nu kan du använda ditt nya lösenord för att ansluta till **Intern** läge.
