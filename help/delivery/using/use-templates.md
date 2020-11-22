---
solution: Campaign Classic
product: campaign
title: Använd leveransmallar
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---


# Använda mallar {#use-templates}

Leveransmallar ger ökad effektivitet genom färdiga scenarier för de flesta vanliga typer av aktiviteter. Med mallar kan marknadsförarna driftsätta nya kampanjer med minimal anpassning på kortare tid.

Learn more about delivery templates in [this section](../../delivery/using/creating-a-delivery-template.md).

## Kom igång med leveransmallar {#gs-templates}

Med en [leveransmall](../../delivery/using/creating-a-delivery-template.md) kan du definiera en uppsättning tekniska och funktionella egenskaper som passar dina behov och som kan återanvändas för framtida leveranser. Sedan kan ni spara tid och standardisera leveranser vid behov.

När du hanterar flera varumärken i Adobe Campaign rekommenderar Adobe att du har en underdomän per varumärke. En bank kan till exempel ha flera underdomäner som motsvarar var och en av dess regionala myndigheter. Om en bank äger domänen bluebank.com kan dess underdomäner vara @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com osv. Med en leveransmall per underdomän kan ni alltid använda rätt förkonfigurerade parametrar för varje varumärke, vilket undviker fel och sparar tid.

**Tips**:  För att undvika konfigurationsfel i Campaign Standarden rekommenderar vi att du duplicerar en inbyggd mall och ändrar dess egenskaper i stället för att skapa en ny mall.

## Konfigurera adresser

* Avsändarens adress är obligatorisk för att tillåta att ett e-postmeddelande skickas.

* En del Internet-leverantörer (Internet Service Providers) kontrollerar avsändarens adress innan de accepterar meddelanden.

* En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges.

* Adressen måste uttryckligen identifiera avsändaren. Domänen måste ägas av och registreras hos avsändaren.

* Adobe rekommenderar att du skapar e-postkonton som motsvarar adresserna som angetts för leveranser och svar. Kontakta systemadministratören för meddelanden.

Följ stegen nedan för att konfigurera adresser i Campaign-gränssnittet:

1. Klicka på [länken i](../../delivery/using/creating-a-delivery-template.md)leveransmallen **[!UICONTROL From]** . I **[!UICONTROL Email header parameters]** fönstret fyller du i följande fält:

   ![](assets/d_best_practices_email_header.png)

1. I **[!UICONTROL Sender address]** fältet kontrollerar du att adressdomänen är densamma som den underdomän som du delegerade till Adobe. Du kan ändra den del som föregår @ men inte domänadressen.

1. I **[!UICONTROL From]** fältet använder du ett namn som mottagarna lätt kan identifiera, till exempel ert varumärke, för att öka öppningshastigheten för era leveranser. Om du vill förbättra mottagarens upplevelse ytterligare kan du lägga till en persons namn, till exempel&quot;Emma from Megastore&quot;.

1. I **[!UICONTROL Reply address text]** fälten används avsändarens adress som standard för svar. Adobe rekommenderar dock att man använder en befintlig riktig adress som till exempel kundtjänst för ert varumärke. Om en mottagare skickar ett svar kan kundtjänst hantera det.

### Konfigurera en kontrollgrupp

När leveransen har skickats kan du jämföra beteendet hos de uteslutna mottagarna med mottagarna som tog emot leveransen. Sedan kan ni mäta effektiviteten i era kampanjer. Läs mer om kontrollgrupper i [det här avsnittet](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Klicka på **[!UICONTROL To]** länken om du vill konfigurera en kontrollgrupp. Välj **[!UICONTROL Select target]** fliken i **[!UICONTROL Control group]** fönstret. Du kan extrahera en del av målet, till exempel ett slumpmässigt urval på 5 %.

![](assets/d_best_practices_control_group.png)

## Använd typografi för att tillämpa filter eller kontrollregler

En typologi innehåller kontrollregler som tillämpas under analysfasen innan ett meddelande skickas.

Ändra standardtypologin efter behov på fliken **[!UICONTROL Typology]** för mallens egenskaper.

Om du till exempel vill ha bättre kontroll över utgående trafik kan du definiera vilka IP-adresser som kan användas genom att definiera en tillhörighet per underdomän och skapa en typologi per tillhörighet. Tillhörigheterna definieras i instansens konfigurationsfil. Kontakta Adobe Campaign-administratören.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).
