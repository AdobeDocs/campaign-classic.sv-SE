---
solution: Campaign Classic
product: campaign
title: Om leveransbarhet i Adobe Campaign Classic
description: Läs mer om hur du hanterar leveranser i Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Kontrollera meddelandeinnehåll{#control-message-content}

För att förbättra e-postleveransen och se till att dina e-postmeddelanden når dina mottagare måste e-postmeddelandet följa ett visst antal regler som anges nedan.

## Avsändarens adress {#sender-address}

Vissa Internet-leverantörer kontrollerar giltigheten för avsändaradressen (Från) innan de accepterar meddelanden. En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges på förekomstnivå (meny **[!UICONTROL Tools > Advanced > Deployment wizard...]**) eller i de vanligaste scenarierna.

## Avanmäl länk och formulär {#opt-out}

När meddelandet analyseras kontrollerar en typologiregel som standard om en avanmälningslänk har inkluderats och genererar en varning om den saknas. Du kan ändra den här regeln så att ett fel uppstår i stället för en enkel varning och stoppa en leverans från att gå ut utan den här länken.

Du måste kontrollera att avanmälningslänken fungerar som den ska innan du skickar iväg den. När du t.ex. skickar korrekturet kontrollerar du att länken är giltig, att formuläret är online och att valideringen ändrar värdet för fältet **[!UICONTROL No longer contact this recipient]** till **[!UICONTROL Yes]**. Du bör göra den här kontrollen systematiskt eftersom det alltid är möjligt att göra mänskliga fel när du anger länken eller när du ändrar formuläret.

Om ett problem upptäcks med att prenumerationen inte längre kan tas emot efter att leveransen har startats går det fortfarande att göra en manuell avanmälan (med funktionen för massuppdatering till exempel) för de mottagare som klickar på avanmälningslänken, även om de inte kunde bekräfta sitt val.

Som allmän regel ska du inte försöka hindra mottagare som vill avanmäla sig genom att kräva att de fyller i fält som e-postadress eller namn, till exempel. Formuläret ska bara ha en valideringsknapp och avstämning ska endast utföras på den krypterade identifieraren. Begäran om ytterligare bekräftelse är inte tillförlitlig: en användare kan ha två e-postadresser som omdirigeras till samma ruta (till exempel: firstname.lastname@club.com och firstname.lastname@internet-club.com). Om mottagaren bara kommer ihåg den första adressen och vill avbeställa prenumerationen via ett meddelande som skickas till den andra, kommer formuläret att avslå detta eftersom den krypterade identifieraren och den angivna e-postadressen inte matchar.

## SpamAssassin {#spamassassin}

Adobe Campaign kan konfigureras för att fungera med SpamAssassin. Detta gör det möjligt att poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

Innan du påbörjar en leverans kan du på fliken Förhandsgranska utvärdera riskerna. Ett varningsmeddelande ger resultatet av testet.

Läs mer i det här [avsnittet](../../delivery/using/spamassassin.md).