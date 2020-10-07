---
title: Lösenordet har tappats bort
seo-title: Lösenordet har tappats bort
description: Lösenordet har tappats bort
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 5%

---


# Lösenordet har tappats bort{#lost-password}

Du kan ändra eller återställa ett förlorat lösenord.

Det finns två möjliga scenarier:

* Lösenord som har gått förlorat av en Adobe Campaign-operator.

   I så fall kan du ändra lösenordet för den berörda operatorn. Det gör du genom att ansluta via en operator med administratörsbehörighet, högerklicka på en operator, välja **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** och ange operatörens nya lösenord. Vi rekommenderar att operatorer ändrar sina lösenord när de först återansluter.

   ![](assets/operator-passwd.png)

* **Intern** lösenordsförlust (endast lokala kunder).

   Om det **interna** lösenordet går förlorat måste du initiera det igen. Gör så här:

   1. Redigera **/usr/local/neolane/nl6/conf/serverConf.xml** .
   1. Gå till raden **internalPassword** .

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

   1. Nu kan du använda ditt nya lösenord för att ansluta i **internt** läge.

