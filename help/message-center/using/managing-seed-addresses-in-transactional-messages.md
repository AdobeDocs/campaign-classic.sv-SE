---
solution: Campaign Classic
product: campaign
title: Hantera fröadresser i transaktionsmeddelanden
description: Hantera fröadresser i transaktionsmeddelanden
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 11%

---


# Hantera fröadresser i transaktionsmeddelanden{#managing-seed-addresses-in-transactional-messages}

Med en dirigerad adress kan du visa en förhandsgranskning av ditt meddelande, skicka ett korrektur och testa meddelandepersonalisering innan e-post eller SMS-leverans. Seed-adresserna är kopplade till leveransen och kan inte användas för andra leveranser.

## Skapa fröadresser {#creating-a-seed-address}

1. Klicka på fliken **[!UICONTROL Seed addresses]** i mallen för transaktionsmeddelanden.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Tilldela en etikett till den så att du enkelt kan välja den senare.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Ange startadressen (e-post eller mobiltelefon beroende på kommunikationskanalen).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Ange den externa identifieraren: I det här valfria fältet kan du ange en affärsnyckel (unikt ID, namn + e-post osv.) som är gemensamma för alla program på webbplatsen och som används för att identifiera dina profiler. Om det här fältet också finns i Adobe Campaign marknadsföringsdatabas kan du sedan koppla en händelse till en profil i databasen.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Infoga testdata (se [Personaliseringsdata](../../message-center/using/personalization-data.md)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Klicka på länken **[!UICONTROL Add other seed addresses]** och klicka sedan på knappen **[!UICONTROL Add]**.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Upprepa processen för att skapa så många adresser du behöver.

   ![](assets/messagecenter_create_seedaddr_008.png)

När adresserna har skapats kan du visa deras förhandsgranskning och personalisering. Se [Förhandsgranska transaktionsmeddelande](../../message-center/using/transactional-message-preview.md).
