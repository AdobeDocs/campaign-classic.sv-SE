---
solution: Campaign Classic
product: campaign
title: Lösenordet har tappats bort
description: Lösenordet har tappats bort
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 1fdee02e98ce66ec184d8587d0838557f027cf75
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---


# Lösenordet har tappats bort{#lost-password}

Du kan ändra eller återställa ett förlorat lösenord.
Det finns två möjliga scenarier:

* [Lösenord som gått förlorat av en Adobe Campaign-operatör](#password-lost-by-campaign-operator)
* [Internt lösenord har gått förlorat](#internal-password-lost)  (endast lokala kunder)

## Lösenordet har gått förlorat av en kampanjoperator {#password-lost-by-campaign-operator}

Om en Adobe Campaign-operator förlorar sitt lösenord kan du ändra det.
Följ stegen nedan för att göra detta:

1. Anslut via en operator med administratörsbehörighet.
1. Högerklicka på en operator.
1. Välj **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. Ange operatorns nya lösenord. Vi rekommenderar att operatorn ändrar sitt lösenord när han/hon först ansluter igen.

## Det interna lösenordet har tagits bort {#internal-password-lost}

>[!NOTE]
>
>Detta avsnitt gäller endast lokala kunder.

Om det interna lösenordet går förlorat måste du initiera om det.
Gör så här:

1. Redigera filen **/usr/local/neolane/nl6/conf/serverConf.xml**.

1. Gå till raden **internalPassword**.

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

1. Du kan nu använda ditt nya lösenord för att ansluta i läget **Intern**.
