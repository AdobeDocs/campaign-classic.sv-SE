---
solution: Campaign Classic
product: campaign
title: Lösenordet har tappats bort
description: Lösenordet har tappats bort
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 3%

---


# Lösenordet har tappats bort{#lost-password}

Du kan ändra eller återställa ett förlorat lösenord.

Det finns två möjliga scenarier:

* Lösenord som har gått förlorat av en Adobe Campaign-operator.

   I så fall kan du ändra lösenordet för den berörda operatorn. Det gör du genom att ansluta via en operator med administratörsbehörighet, högerklicka på en operator, välja **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** och ange operatörens nya lösenord. Vi rekommenderar att operatorer ändrar sina lösenord när de först återansluter.

   ![](assets/operator-passwd.png)

* **Förlorat** internt lösenord (endast lokala kunder).

   Om det interna **lösenordet för** försvinner måste du initiera om det. Gör så här:

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

