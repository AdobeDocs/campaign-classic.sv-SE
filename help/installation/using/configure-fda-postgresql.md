---
product: campaign
title: Konfigurera åtkomst till PostgreSQL
description: Lär dig konfigurera åtkomst till PostgreSQL
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 2%

---

# Konfigurera åtkomst till PostgreSQL {#configure-fda-postgresql}



Använd kampanj **Åtkomst till federerade data** (FDA) om du vill bearbeta information som lagras i en extern PostgreSQL-databas.

## PostgreSQL-konfiguration {#postgresql-configuration}

Du måste först installera Libpq. Med Libpq kan klientprogram skicka frågor till PostgreSQL-serverdelen och ta emot dessa frågeresultat.

Följ stegen nedan för att konfigurera åtkomst till [!DNL PostgreSQL]:

* För CentOS kör du följande kommando `sudo apt-get -y install libpq-dev`.

* För Linux kör du följande kommando `yum install postgresql-devel`.

* För Windows implementeras Libpq via `libpq.dll` som ingår i Adobe Campaign-installationen.

I Adobe Campaign kan du sedan konfigurera [!DNL PostgreSQL] externt konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#postgresql-external).

## PostgreSQL-externt konto {#postgresql-external}

>[!NOTE]
>
> PostgreSQL finns i CentOS 7 och 6.

Du måste skapa en [!DNL PostgreSQL] externt konto för att ansluta Campaign-instansen till [!DNL PostgreSQL] extern databas.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som ditt externa konto **[!UICONTROL Type]**.

1. Under **[!UICONTROL Configuration]**, markera [!DNL PostgreSQL, Greenplum] från **[!UICONTROL Type]** nedrullningsbar meny.

   ![](assets/postgresql_1.png)

1. Konfigurera **[!UICONTROL PostgreSQL]** autentisering av externt konto:

   * **[!UICONTROL Server]**: URL för [!DNL PostgreSQL] server.

   * **[!UICONTROL Account]**: Användarens namn.

   * **[!UICONTROL Password]**: Lösenord för användarkonto.

   * **[!UICONTROL Database]**: Namn på databasen (valfritt).

   * **[!UICONTROL Working schema]**: Namnet på ditt arbetsschema. [Läs mer](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Tidszon inställd på [!DNL PostgreSQL]. [Läs mer](https://www.postgresql.org/docs/7.2/timezones.html)

1. Klicka på **[!UICONTROL Parameters]** tabben **[!UICONTROL Deploy functions]** för att skapa funktioner.

   >[!NOTE]
   >
   >För att alla funktioner ska vara tillgängliga måste du skapa Adobe Campaign SQL-funktionerna i fjärrdatabasen. Mer information finns i [page](../../configuration/using/adding-additional-sql-functions.md).

1. Klicka **[!UICONTROL Save]** när konfigurationen är klar.

Kopplingen stöder följande alternativ:

| Option | Beskrivning |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Maximal väntetid på anslutningen, i sekunder. <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Antal sekunder av inaktivitet efter vilket TCP ska skicka ett meddelande om keepalive till servern. <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Antal sekunder efter vilket TCP-keepalive-meddelandet som inte har bekräftats av servern ska skickas igen.  <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Antal TCP-nycklar som kan förloras innan klientens anslutning till servern anses vara död. <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
