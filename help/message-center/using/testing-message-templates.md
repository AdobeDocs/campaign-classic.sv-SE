---
product: campaign
title: Testa mallar för transaktionsmeddelanden
description: Lär dig hantera dirigerade adresser i transaktionsmeddelanden för att förhandsgranska och testa dem i Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 3%

---

# Testa mallar för transaktionsmeddelanden {#testing-message-templates}



När du [meddelandemall](../../message-center/using/creating-the-message-template.md) är klart följer du stegen nedan för att förhandsgranska och testa det.

## Hantera dirigerade adresser i transaktionsmeddelanden {#managing-seed-addresses-in-transactional-messages}

Med en dirigerad adress kan du visa en förhandsgranskning av ditt meddelande, skicka ett korrektur och testa meddelandepersonalisering innan e-post eller SMS-leverans. Seed-adresserna är kopplade till leveransen och kan inte användas för andra leveranser.

Följ stegen nedan för att skapa dirigerade adresser i ett transaktionsmeddelande:

1. Klicka på knappen **[!UICONTROL Seed addresses]** -fliken.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. Tilldela en etikett till den så att du enkelt kan välja den senare.

   ![](assets/messagecenter_create_seedaddr_002.png)

1. Ange startadressen (e-post eller mobiltelefon beroende på kommunikationskanalen).

   ![](assets/messagecenter_create_seedaddr_003.png)

1. Ange den externa identifieraren: I det här valfria fältet kan du ange en affärsnyckel (unikt ID, namn + e-post osv.) som är gemensamma för alla program på webbplatsen och som används för att identifiera dina profiler. Om det här fältet också finns i Adobe Campaign marknadsföringsdatabas kan du sedan koppla en händelse till en profil i databasen.

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. Infoga testdata (se [Personaliseringsdata](#personalization-data)).

   ![](assets/messagecenter_create_custo_001.png)

   <!--## Creating several seed addresses {#creating-several-seed-addresses}-->
1. Klicka på **[!UICONTROL Add other seed addresses]** klicka på **[!UICONTROL Add]** -knappen.

   ![](assets/messagecenter_create_seedaddr_004.png)

   <!--1. Follow the configuration steps for a seed address detailed in the [Creating a seed address](#creating-a-seed-address) section.-->
1. Upprepa processen för att skapa så många adresser du behöver.

   ![](assets/messagecenter_create_seedaddr_008.png)

När adresserna har skapats kan du visa deras förhandsgranskning och personalisering. Se [Förhandsgranskning av transaktionsmeddelande](#transactional-message-preview).

## Personaliseringsdata {#personalization-data}

Det går att använda data i meddelandemallen för att testa anpassning av transaktionsmeddelanden. Den här funktionen används för att generera en förhandsgranskning eller skicka ett korrektur. Du kan även visa återgivningen av meddelandet för olika Internetåtkomstleverantörer. Mer information finns i [Inkorgsåtergivning](../../delivery/using/inbox-rendering.md).

Syftet med dessa data är att testa dina meddelanden innan de levereras. Dessa meddelanden sammanfaller inte med faktiska data som ska behandlas. XML-strukturen måste dock vara identisk med den för händelsen som lagras i körningsinstansen, vilket visas nedan:

![](assets/messagecenter_create_custo_006.png)

Med den här informationen kan du anpassa meddelandeinnehåll med personaliseringstaggar (mer information finns i [Skapa meddelandeinnehållet](../../message-center/using/creating-the-message-template.md#creating-message-content)).

1. Välj transaktionsmeddelandemallen.

1. Klicka på **[!UICONTROL Seed addresses]** -fliken.

1. I händelseinnehållet anger du testinformationen i XML-format.

   ![](assets/messagecenter_create_custo_001.png)

1. Klicka på **[!UICONTROL Save]**.

## Förhandsgranskning av transaktionsmeddelande {#transactional-message-preview}

När du har skapat en eller flera dirigerade adresser och meddelandetexten kan du förhandsgranska meddelandet och kontrollera dess personalisering.

1. Klicka på knappen **[!UICONTROL Preview]** -fliken.

   ![](assets/messagecenter_preview_001.png)

1. Välj **[!UICONTROL A seed address]** i listrutan.

   ![](assets/messagecenter_preview_002.png)

1. Välj den startadress som skapades tidigare för att visa det anpassade meddelandet.

   ![](assets/messagecenter_create_seedaddr_009.png)

Med hjälp av dirigerade adresser kan du även visa återgivningen av meddelandet för olika leverantörer av Internetåtkomst. Mer information finns i [Inkorgsåtergivning](../../delivery/using/inbox-rendering.md).

## Skicka en korrektur {#sending-a-proof}

Du kan testa meddelandeleveransen genom att skicka ett korrektur till en startadress som skapats tidigare.

När du skickar ett korrektur utförs samma process som för en [normal leverans](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof). Med transaktionsmeddelanden måste du dock utföra följande åtgärder i förväg:

* Skapa en eller flera [dirigeringsadresser](#managing-seed-addresses-in-transactional-messages) med [personaliseringsdata](#personalization-data).
* [Skapa meddelandeinnehållet](../../message-center/using/creating-the-message-template.md#creating-message-content).

Skicka korrekturet:

1. Klicka på **[!UICONTROL Send a proof]** i leveransfönstret.
1. Analysera leveransen.
1. Åtgärda eventuella fel och bekräfta leveransen.

   ![](assets/messagecenter_send_proof_001.png)

1. Kontrollera att meddelandet levererades till startadressen och att innehållet överensstämmer med din konfiguration.

   ![](assets/messagecenter_send_proof_002.png)

Du kan komma åt korrektur i varje mall via **[!UICONTROL Audit]** -fliken. Mer information finns i [Skicka ett bevis](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

![](assets/messagecenter_send_proof_003.png)

Din meddelandemall är nu klar [publicerad](../../message-center/using/publishing-message-templates.md).