---
product: campaign
title: SpamAssassin
description: Lär dig hur du konfigurerar identifiering av skräppost med SpamAssets
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email, Deliverability
role: User
exl-id: 8be6836d-f7dc-4199-b2b2-b6a9cac9d162
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 5%

---

# SpamAssassin{#spamassassin}

Adobe Campaign kan konfigureras för att fungera med [SpamAssassin](https://spamassassin.apache.org), en tredjepartstjänst som används för skräppostfiltrering. På så sätt kan du poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

SpamAssassin utnyttjar en mängd olika tekniker för skräppostavkänning, bland annat:

* DNS-baserad och otydlig kontrollsummebaserad skräppostavkänning
* Bayesisk filtrering
* Externa program
* Blockeringslista
* Online-databaser

>[!NOTE]
>
>SpamAssassin måste installeras och konfigureras på Adobe Campaign programserver. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-spamassassin.md).
>
>Reglerna som styr om ett element är spam eller inte hanteras via SpamAssets och kan redigeras av en administratör med behörighet.

## Använd SpamAssassin i Campaign {#using-spamassassin}

När du har skapat din e-postleverans och definierat innehållet följer du stegen nedan för att utvärdera riskerna.

Mer information om hur du skapar och utformar en leverans finns i [det här avsnittet](about-email-channel.md).

1. Gå till **[!UICONTROL Preview]** -fliken.
1. Välj en mottagare om du vill förhandsgranska leveransen.

   ![](assets/s_tn_del_preview_spamassassin_recipient.png)

   >[!NOTE]
   >
   >Om du inte väljer någon mottagare kan skräppostkontrollen inte utföras.

1. Ett varningsmeddelande ger resultatet av testet. Om en hög risknivå upptäcks visas följande varningsmeddelande:

   ![](assets/s_tn_del_preview_spamassassin_ko.png)

1. Klicka på **[!UICONTROL More...]** -länk bredvid varningen.
1. Klicka på fliken **[!UICONTROL Anti-spam checking]**.  
1. Gå till **[!UICONTROL Points / Rule / Description]** för att se orsakerna till denna risk.

   ![](assets/s_tn_del_msg_spamassassin_ko.png)

>[!NOTE]
>
>Varje gång du klickar på **[!UICONTROL Anti-spam checking]**, anropas SpamAssassin-tjänsten och meddelandet analyseras igen för att upptäcka skräppost. Kontrollera att du har ändrat innehållet innan du kör skräppostanalysen igen.
