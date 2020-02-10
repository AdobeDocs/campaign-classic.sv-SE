---
title: Växla till Unicode
seo-title: Växla till Unicode
description: Växla till Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Växla till Unicode{#switching-to-unicode}

För en befintlig **produktinstans** i Linux/PostgreSQL är stegen för att växla till unicode följande:

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

   Lägg till **u** -tecknet framför värdet som relaterar till databasidentifieraren (**databaseId**):

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

