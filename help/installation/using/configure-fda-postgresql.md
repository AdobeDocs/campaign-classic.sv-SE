---
product: campaign
title: Konfigurera åtkomst till PostgreSQL
description: Lär dig konfigurera åtkomst till PostgreSQL
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Konfigurera åtkomst till PostgreSQL {#configure-fda-postgresql}



Använd alternativet **FDA (Federated Data Access**) för Campaign om du vill bearbeta information som lagras i en extern PostgreSQL-databas.

## PostgreSQL-konfiguration {#postgresql-configuration}

Du måste först installera Libpq. Med Libpq kan klientprogram skicka frågor till PostgreSQL-serverdelen och ta emot dessa frågeresultat.

Följ stegen nedan för att konfigurera åtkomst till [!DNL PostgreSQL]:

* Kör följande kommando `sudo apt-get -y install libpq-dev` för CentOS.

* Kör följande kommando `yum install postgresql-devel` för Linux.

* För Windows implementeras Libpq via `libpq.dll`, som ingår i Adobe Campaign-installationen.

I Adobe Campaign kan du sedan konfigurera ditt [!DNL PostgreSQL]-externa konto. Mer information om hur du konfigurerar ditt externa konto finns i [det här avsnittet](#postgresql-external).

## PostgreSQL-externt konto {#postgresql-external}

>[!NOTE]
>
> PostgreSQL finns i CentOS 7 och 6.

Du måste skapa ett externt [!DNL PostgreSQL]-konto för att ansluta Campaign-instansen till din [!DNL PostgreSQL]-externa databas.

1. Klicka på **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i Campaign **[!UICONTROL Explorer]**.

1. Klicka på **[!UICONTROL New]**.

1. Välj **[!UICONTROL External database]** som det externa kontots **[!UICONTROL Type]**.

1. Under **[!UICONTROL Configuration]** väljer du [!DNL PostgreSQL, Greenplum] i listrutan **[!UICONTROL Type]**.

   ![](assets/postgresql_1.png)

1. Konfigurera autentiseringen av det externa kontot **[!UICONTROL PostgreSQL]**:

   * **[!UICONTROL Server]**: URL för servern [!DNL PostgreSQL].

   * **[!UICONTROL Account]**: Användarens namn.

   * **[!UICONTROL Password]**: Lösenord för användarkonto.

   * **[!UICONTROL Database]**: Namn på databasen (valfritt).

   * **[!UICONTROL Working schema]**: Namnet på ditt arbetsschema. [Läs mer](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Tidszonen har angetts i [!DNL PostgreSQL]. [Läs mer](https://www.postgresql.org/docs/7.2/timezones.html)

1. Klicka på fliken **[!UICONTROL Parameters]** och sedan på knappen **[!UICONTROL Deploy functions]** för att skapa funktioner.

   >[!NOTE]
   >
   >För att alla funktioner ska vara tillgängliga måste du skapa Adobe Campaign SQL-funktionerna i fjärrdatabasen. Mer information finns på [sidan](../../configuration/using/adding-additional-sql-functions.md).

1. Klicka på **[!UICONTROL Save]** när konfigurationen är klar.

Kopplingen stöder följande alternativ:

| Alternativ | Beskrivning |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Maximal väntetid på anslutningen, i sekunder. <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Antal sekunder av inaktivitet efter vilket TCP ska skicka ett meddelande om keepalive till servern. <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Antal sekunder efter vilket TCP-keepalive-meddelandet som inte har bekräftats av servern ska skickas igen.  <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Antal TCP-nycklar som kan förloras innan klientens anslutning till servern anses vara död. <br>Mer information finns i [PostgreSQL-dokumentation](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
