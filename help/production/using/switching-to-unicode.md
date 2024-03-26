---
product: campaign
title: Växla till Unicode
description: Växla till Unicode
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 5%

---

# Växla till Unicode{#switching-to-unicode}



För en befintlig **prod** i Linux/PostgreSQL är stegen för att växla till unicode följande:

1. Stoppa processerna som skriver till databasen:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Dumpa databasen:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Skapa en Unicode-databas:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Återställ databasen:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Uppdatera alternativet som anger att databasen är Unicode:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. På spårningsservrarna:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Lägg till **u** tecken framför värdet som relaterar till databasidentifieraren (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. På servrar som anropar databasen:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Ändra databasreferensen:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Starta om alla datorer:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Bekräfta bytet. Det gör du genom att ansluta via Adobe Campaign-konsolen och:

   * kontrollera att data visas korrekt, särskilt de framhävda tecknen:
   * starta en leverans och kontrollera att spårningshämtningen fungerar.
