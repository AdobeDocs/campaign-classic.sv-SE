---
product: campaign
title: Använd leveransmallar
description: Använd leveransmallar
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# Använd mallar {#use-templates}



Leveransmallar ger ökad effektivitet genom färdiga scenarier för de flesta vanliga typer av aktiviteter. Med mallar kan marknadsförarna driftsätta nya kampanjer med minimal anpassning på kortare tid.

Läs mer om leveransmallar i [det här avsnittet](creating-a-delivery-template.md).

## Kom igång med leveransmallar {#gs-templates}

A [leveransmall](creating-a-delivery-template.md) Med kan du definiera en uppsättning tekniska och funktionella egenskaper som passar dina behov och som kan återanvändas för framtida leveranser. Sedan kan ni spara tid och standardisera leveranser vid behov.

När du hanterar flera varumärken i Adobe Campaign rekommenderar Adobe att du har en underdomän per varumärke. En bank kan till exempel ha flera underdomäner som motsvarar var och en av dess regionala myndigheter. Om en bank äger domänen bluebank.com kan dess underdomäner vara @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com osv. Med en leveransmall per underdomän kan ni alltid använda rätt förkonfigurerade parametrar för varje varumärke, vilket undviker fel och sparar tid.

**Tips**: För att undvika konfigurationsfel rekommenderar vi att du duplicerar en intern mall och ändrar dess egenskaper i stället för att skapa en ny mall.

## Konfigurera adresser

* Avsändarens adress är obligatorisk för att tillåta att ett e-postmeddelande skickas.

* En del Internet-leverantörer (Internet Service Providers) kontrollerar avsändarens adress innan de accepterar meddelanden.

* En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges.

* Adressen måste uttryckligen identifiera avsändaren. Domänen måste ägas av och registreras hos avsändaren.

* Adobe rekommenderar att du skapar e-postkonton som motsvarar adresserna som angetts för leveranser och svar. Kontakta systemadministratören för meddelanden.

Följ stegen nedan för att konfigurera adresser i Campaign-gränssnittet:

1. I [leveransmall](creating-a-delivery-template.md)klickar du på **[!UICONTROL From]** länk. I **[!UICONTROL Email header parameters]** Fönster, fyll i följande fält:

   ![](assets/d_best_practices_email_header.png)

1. I **[!UICONTROL Sender address]** ska du kontrollera att adressdomänen är densamma som den underdomän som du har delegerat till Adobe. Du kan ändra den del som föregår @ men inte domänadressen.

1. I **[!UICONTROL From]** används ett namn som lätt kan identifieras av mottagarna, till exempel ert varumärkes namn, för att öka öppningshastigheten för era leveranser. Om du vill förbättra mottagarens upplevelse ytterligare kan du lägga till en persons namn, till exempel&quot;Emma from Megastore&quot;.

1. I **[!UICONTROL Reply address text]** används avsändarens adress som standard för svar. Adobe rekommenderar dock att man använder en befintlig riktig adress som till exempel kundtjänst för ert varumärke. Om en mottagare skickar ett svar kan kundtjänst hantera det.

### Konfigurera en kontrollgrupp

När leveransen har skickats kan du jämföra beteendet hos de uteslutna mottagarna med mottagarna som tog emot leveransen. Sedan kan ni mäta effektiviteten i era kampanjer. Läs mer om kontrollgrupper [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Om du vill konfigurera en kontrollgrupp klickar du på **[!UICONTROL To]** länk. I **[!UICONTROL Select target]** väljer du **[!UICONTROL Control group]** -fliken. Du kan extrahera en del av målet, till exempel ett slumpmässigt urval på 5 %.

![](assets/d_best_practices_control_group.png)

## Använd typografi för att tillämpa filter eller kontrollregler

En typologi innehåller kontrollregler som tillämpas under analysfasen innan ett meddelande skickas.

I **[!UICONTROL Typology]** ändra standardtypologin efter behov på fliken för mallens egenskaper.

Om du till exempel vill ha bättre kontroll över utgående trafik kan du definiera vilka IP-adresser som kan användas genom att definiera en tillhörighet per underdomän och skapa en typologi per tillhörighet. Tillhörigheterna definieras i instansens konfigurationsfil. Kontakta Adobe Campaign-administratören.

Mer information om typologier finns i [det här avsnittet](../../campaign-opt/using/about-campaign-typologies.md).
