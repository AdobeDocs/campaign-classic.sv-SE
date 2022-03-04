---
product: campaign
title: Använd leveransmallar
description: Använd leveransmallar
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# Använd mallar {#use-templates}

![](../../assets/common.svg)

Leveransmallar ger ökad effektivitet genom färdiga scenarier för de flesta vanliga typer av aktiviteter. Med mallar kan marknadsförarna driftsätta nya kampanjer med minimal anpassning på kortare tid.

Läs mer om leveransmallar i [det här avsnittet](creating-a-delivery-template.md).

## Kom igång med leveransmallar {#gs-templates}

A [leveransmall](creating-a-delivery-template.md) Med kan du definiera en uppsättning tekniska och funktionella egenskaper som passar dina behov och som kan återanvändas för framtida leveranser. Sedan kan ni spara tid och standardisera leveranser vid behov.

When you manage several brands in Adobe Campaign, Adobe recommends having one sub-domain per brand. En bank kan till exempel ha flera underdomäner som motsvarar var och en av dess regionala myndigheter. If a bank owns the bluebank.com domain, its sub-domains can be @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, etc. Having one delivery template per sub-domain enables you to always use the right pre-configured parameters for each of your brand, which avoids errors and saves you time.

**Tips**: För att undvika konfigurationsfel rekommenderar vi att du duplicerar en intern mall och ändrar dess egenskaper i stället för att skapa en ny mall.

## Konfigurera adresser

* Avsändarens adress är obligatorisk för att tillåta att ett e-postmeddelande skickas.

* En del Internet-leverantörer (Internet Service Providers) kontrollerar avsändarens adress innan de accepterar meddelanden.

* En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges.

* Adressen måste uttryckligen identifiera avsändaren. Domänen måste ägas av och registreras hos avsändaren.

* Adobe rekommenderar att du skapar e-postkonton som motsvarar adresserna som angetts för leveranser och svar. Check with your messaging system administrator.

To configure addresses in Campaign interface, follow the steps below:

1. In the [delivery template](creating-a-delivery-template.md), click the **[!UICONTROL From]** link. In the **[!UICONTROL Email header parameters]** window, fill in the following fields:

   ![](assets/d_best_practices_email_header.png)

1. I **[!UICONTROL Sender address]** ska du kontrollera att adressdomänen är densamma som den underdomän som du har delegerat till Adobe. Du kan ändra den del som föregår @ men inte domänadressen.

1. I **[!UICONTROL From]** används ett namn som lätt kan identifieras av mottagarna, till exempel ert varumärkes namn, för att öka öppningshastigheten för era leveranser. Om du vill förbättra mottagarens upplevelse ytterligare kan du lägga till en persons namn, till exempel&quot;Emma from Megastore&quot;.

1. I **[!UICONTROL Reply address text]** används avsändarens adress som standard för svar. Adobe rekommenderar dock att man använder en befintlig riktig adress som till exempel kundtjänst för ert varumärke. Om en mottagare skickar ett svar kan kundtjänst hantera det.

### Konfigurera en kontrollgrupp

När leveransen har skickats kan du jämföra beteendet hos de uteslutna mottagarna med mottagarna som tog emot leveransen. Sedan kan ni mäta effektiviteten i era kampanjer. Learn more about control groups [this section](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Om du vill konfigurera en kontrollgrupp klickar du på **[!UICONTROL To]** länk. In the **[!UICONTROL Select target]** window, select the **[!UICONTROL Control group]** tab. Du kan extrahera en del av målet, till exempel ett slumpmässigt urval på 5 %.

![](assets/d_best_practices_control_group.png)

## Använd typografi för att tillämpa filter eller kontrollregler

En typologi innehåller kontrollregler som tillämpas under analysfasen innan ett meddelande skickas.

I **[!UICONTROL Typology]** ändra standardtypologin efter behov på fliken för mallens egenskaper.

Om du till exempel vill ha bättre kontroll över utgående trafik kan du definiera vilka IP-adresser som kan användas genom att definiera en tillhörighet per underdomän och skapa en typologi per tillhörighet. Tillhörigheterna definieras i instansens konfigurationsfil. Kontakta Adobe Campaign-administratören.

Mer information om typologier finns i [det här avsnittet](../../campaign-opt/using/about-campaign-typologies.md).
