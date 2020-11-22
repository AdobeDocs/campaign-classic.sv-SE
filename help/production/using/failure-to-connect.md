---
solution: Campaign Classic
product: campaign
title: Det gick inte att ansluta
description: Det gick inte att ansluta
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Det gick inte att ansluta{#failure-to-connect}

Orsaken till detta kan vara flera och beror på olika sammanhang.

Kontrollera den allmänna konfigurationen för säkerhetszonerna.

>[!NOTE]
>
>Mer information om hur du konfigurerar säkerhetszoner finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Kontrollera följande information:

1. **Nätverkskontroller**

   * Har du Internetåtkomst från datorn?

      Kontrollera att du kan ansluta till webbplatser på Internet (till exempel). Om du inte kan ansluta finns problemet på datorn. Kontakta systemadministratören.

   * Kan du ansluta till servern som är värd för Adobe Campaign via en annan tjänst?

      Anslut till servern via SSH eller på något annat sätt. Om detta inte är möjligt har värdföretaget ett problem. Kontakta systemadministratören.

1. **Kontrollerar på webbserversidan** (IIS/apache/etc.)

   * svarar webbservern?

      Anslut till Adobe Campaign server access URL med en webbläsare: **http(s)://`<urlserver>`**. Om den inte svarar stoppas webbservern på datorn. Kontakta systemadministratören för värdföretaget för att starta om tjänsten.

   * Har Adobe Campaign integrerats korrekt?

      Logga in på: **http(s):// `<urlserver>`/r/test** -URL. Servern ska returnera följande typ av meddelande

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Om du inte får det här resultatet bör du kontrollera i webbserverkonfigurationen att integreringen beaktas.

1. **Kontroller på Adobe Campaign sida**

   * Har Adobe Campaign webbmodul startats?

      Anslut till följande URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Om du får ett Tomcat Java-fel:

         Är JAVA-integreringen korrekt genomförd? Adobe Campaign kräver SUN JDK.

         Den är integrerad i filen **`[path of application]`/nl6/customer.sh**

      * Om du får en tom sida:

         Har Adobe Campaign webbmodul startats? Du bör få:

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * Om inte, starta om den med följande kommando:

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Om du får ett svar av följande typ när du listar Adobe Campaign-modulerna: **nlserver pdump**
>HH:MM:SS > Programserver för Adobe Campaign Classic (7.X YY.R build XXX@SHA1) för DD/MM/YYY Inga åtgärder Du måste starta om hela Adobe Campaign-programmet. Använd följande kommando för att göra detta: **nlserver watchdog -svc -noconsole **
