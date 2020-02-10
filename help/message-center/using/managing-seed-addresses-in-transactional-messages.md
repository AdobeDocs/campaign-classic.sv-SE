---
title: Hantera dirigerade adresser i transaktionsmeddelanden
seo-title: Hantera dirigerade adresser i transaktionsmeddelanden
description: Hantera dirigerade adresser i transaktionsmeddelanden
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Hantera dirigerade adresser i transaktionsmeddelanden{#managing-seed-addresses-in-transactional-messages}

Med en dirigerad adress kan du visa en förhandsgranskning av ditt meddelande, skicka ett korrektur och testa meddelandepersonalisering innan e-post eller SMS-leverans. Seed-adresserna är kopplade till leveransen och kan inte användas för andra leveranser.

## Skapa en startadress {#creating-a-seed-address}

1. Klicka på **[!UICONTROL Seed addresses]** fliken i transaktionsmeddelandemallen.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Tilldela en etikett till den så att du enkelt kan välja den senare.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Ange startadressen (e-post eller mobiltelefon beroende på kommunikationskanalen).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Ange den externa identifieraren: I det här valfria fältet kan du ange en affärsnyckel (unikt ID, namn + e-post osv.) som är gemensamma för alla program på webbplatsen och som används för att identifiera dina profiler. Om det här fältet också finns i marknadsföringsdatabasen för Adobe Campaign kan du sedan koppla en händelse till en profil i databasen.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Infoga testdata (se [personaliseringsdata](../../message-center/using/personalization-data.md)).

   ![](assets/messagecenter_create_custo_001.png)

## Skapa flera dirigeringsadresser {#creating-several-seed-addresses}

1. Klicka på **[!UICONTROL Add other seed addresses]** länken och sedan på **[!UICONTROL Add]** knappen.

   ![](assets/messagecenter_create_seedaddr_004.png)

1. Följ konfigurationsstegen för en startadress som anges i avsnittet [Skapa en startadress](#creating-a-seed-address) .
1. Upprepa processen för att skapa så många adresser du behöver.

   ![](assets/messagecenter_create_seedaddr_008.png)

När adresserna har skapats kan du visa deras förhandsgranskning och personalisering. Se Förhandsgranska [transaktionsmeddelande](../../message-center/using/transactional-message-preview.md).
