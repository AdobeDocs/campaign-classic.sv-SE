---
title: Leveransvillkor i Adobe Campaign Classic
description: Läs mer om hur du hanterar leveranser i Adobe Campaign Classic.
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 68756f920fbc8658cff552615adbf023b4c5e3aa

---


# Styra meddelandeinnehållet{#control-message-content}

För att förbättra e-postleveransen och se till att dina e-postmeddelanden når dina mottagare måste e-postmeddelandet följa ett visst antal regler som anges nedan.

## Avsändarens adress {#sender-address}

Vissa Internet-leverantörer kontrollerar giltigheten för avsändaradressen (Från) innan de accepterar meddelanden. En felformaterad adress kan leda till att den nekas av den mottagande servern. Du måste se till att rätt adress anges på förekomstnivå (meny **[!UICONTROL Tools > Advanced > Deployment wizard...]**) eller i de vanligaste scenarierna.

## Länk och formulär för avanmälan {#opt-out}

När meddelandet analyseras kontrollerar en typologiregel som standard om en avanmälningslänk har inkluderats och genererar en varning om den saknas. Du kan ändra den här regeln så att ett fel uppstår i stället för en enkel varning och stoppa en leverans från att gå ut utan den här länken.

Du måste kontrollera att avanmälningslänken fungerar som den ska innan du skickar iväg den. När du t.ex. skickar korrekturet ska du kontrollera att länken är giltig, att formuläret är online och att det ändras till **[!UICONTROL No longer contact this recipient]** fältets värde om du validerar det **[!UICONTROL Yes]**. Du bör göra den här kontrollen systematiskt eftersom det alltid är möjligt att göra mänskliga fel när du anger länken eller när du ändrar formuläret.

Om ett problem upptäcks med att prenumerationen inte längre kan tas emot efter att leveransen har startats går det fortfarande att göra en manuell avanmälan (med funktionen för massuppdatering till exempel) för de mottagare som klickar på avanmälningslänken, även om de inte kunde bekräfta sitt val.

Som allmän regel ska du inte försöka hindra mottagare som vill avanmäla sig genom att kräva att de fyller i fält som e-postadress eller namn, till exempel. Formuläret ska bara ha en valideringsknapp och avstämning ska endast utföras på den krypterade identifieraren. Begäran om ytterligare bekräftelse är inte tillförlitlig: en användare kan ha två e-postadresser som omdirigeras till samma ruta (till exempel: firstname.lastname@club.com och firstname.lastname@internet-club.com). Om mottagaren bara kommer ihåg den första adressen och vill avbeställa prenumerationen via ett meddelande som skickas till den andra, kommer formuläret att avslå detta eftersom den krypterade identifieraren och den angivna e-postadressen inte matchar.

## SpamAssassin {#spamassassin}

Adobe Campaign kan konfigureras för att fungera med SpamAssassin. Detta gör det möjligt att poängsätta e-postmeddelanden för att avgöra om ett meddelande löper risk att betraktas som skräppost av de antispam-verktyg som används vid mottagande.

Innan du påbörjar en leverans kan du på fliken Förhandsgranska utvärdera riskerna. Ett varningsmeddelande ger resultatet av testet.

Läs mer i det här [avsnittet](../../delivery/using/spamassassin.md).