---
title: SpamAssassin
description: Lär dig hur du konfigurerar skräppostavkänning med SpamAssassin
page-status-flag: never-activated
uuid: 4f439432-4215-42ed-8f92-b4ca8dd92726
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: d41658ab-ee79-4a5c-a165-d94b81eb2b33
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---


# SpamAssassin{#spamassassin}

## Om SpamAssassin {#about-spamassassin}

Adobe Campaign kan konfigureras för att fungera med [SpamAssets](https://spamassassin.apache.org), en tredjepartstjänst som används för skräppostfiltrering. På så sätt kan du poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

SpamAssassin utnyttjar en mängd olika tekniker för skräppostavkänning, bland annat:

* DNS-baserad och otydlig kontrollsummebaserad skräppostavkänning
* Bayesisk filtrering
* Externa program
* Blockeringslista
* Onlinedatabaser

>[!NOTE]
>
>SpamAssassin måste installeras och konfigureras på Adobe Campaign programserver. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-spamassassin.md).
>
>Reglerna som styr om ett element är spam eller inte hanteras via SpamAssets och kan redigeras av en administratör med behörighet.

## Använda SpamAssassin {#using-spamassassin}

När du har skapat din e-postleverans och definierat innehållet följer du stegen nedan för att utvärdera riskerna.

Mer information om hur du skapar och utformar en leverans finns i [det här avsnittet](../../delivery/using/about-email-channel.md).

1. Gå till fliken **[!UICONTROL Preview]**.
1. Välj en mottagare om du vill förhandsgranska leveransen.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Om du inte väljer någon mottagare kan skräppostkontrollen inte utföras.

1. Ett varningsmeddelande ger resultatet av testet. Om en hög risknivå upptäcks visas följande varningsmeddelande:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Klicka på **[!UICONTROL More...]** länken bredvid varningen.
1. Klicka på fliken **[!UICONTROL Anti-spam checking]**.  
1. Gå till **[!UICONTROL Points / Rule / Description]** avsnittet för att se orsaken till risken.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Varje gång du klickar på **[!UICONTROL Anti-spam checking]** anropas SpamAssassin-tjänsten och meddelandet analyseras igen för att upptäcka skräppost. Kontrollera att du har ändrat innehållet innan du kör skräppostanalysen igen.
