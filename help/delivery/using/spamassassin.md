---
product: campaign
title: SpamAssassin
description: Lär dig hur du konfigurerar skräppostavkänning med SpamAssassin
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# SpamAssassin{#spamassassin}

![](../../assets/common.svg)

## Om SpamAssassin {#about-spamassassin}

Adobe Campaign kan konfigureras för att fungera med [SpamAssassin](https://spamassassin.apache.org), en tredjepartstjänst som används för skräppostfiltrering. På så sätt kan du poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

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

Mer information om hur du skapar och utformar en leverans finns i [det här avsnittet](about-email-channel.md).

1. Gå till fliken **[!UICONTROL Preview]**.
1. Välj en mottagare om du vill förhandsgranska leveransen.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Om du inte väljer någon mottagare kan skräppostkontrollen inte utföras.

1. Ett varningsmeddelande ger resultatet av testet. Om en hög risknivå upptäcks visas följande varningsmeddelande:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Klicka på länken **[!UICONTROL More...]** bredvid varningen.
1. Klicka på fliken **[!UICONTROL Anti-spam checking]**.  
1. Gå till avsnittet **[!UICONTROL Points / Rule / Description]** för att se orsaken till risken.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Varje gång du klickar på **[!UICONTROL Anti-spam checking]** anropas tjänsten SpamAssassin och meddelandet analyseras igen för att identifiera skräppostskydd. Kontrollera att du har ändrat innehållet innan du kör skräppostanalysen igen.
