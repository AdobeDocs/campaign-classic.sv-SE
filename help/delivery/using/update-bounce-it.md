---
product: campaign
title: Uppdatera studskompetens efter avbrott i Italia Online
description: Lär dig hur du uppdaterar studentkvalificering efter avbrott i Italia Online
feature: Deliverability
hide: true
hidefromtoc: true
source-git-commit: 3fa54f83ee6a119a4566866933aaee20ec378e91
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Uppdatera felaktiga fasta studsar efter avbrott i Italia Online {#update-bounce-italia}

![](../../assets/common.svg)

## Kontext{#outage-context}

Sedan den 22 januari (lokal tid) har Italia Online råkat ut för ett driftstopp som lett till flera förseningar och avvisat e-postmeddelanden. Tjänsten började återupptas med begränsad kapacitet den 26 jan.

Följande domäner påverkas: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** och **blu.it**.

Detta problem inträffade 2023-1-26, men de flesta av de felaktiga karantänerna inträffade den 26 januari 2023.

Läs mer i det officiella meddelandet [här](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Effekt{#outage-impact}

Precis som i de flesta fall när det uppstår ett avbrott i en Internet-leverantör markerades vissa e-postmeddelanden som skickades via Campaign felaktigt som studsar. Detta påverkade inte bara Adobe, utan alla som försökte få e-post levererad till Italia Online under driftstoppet.

Symtomen var:

* **Periodiseringsgränser** med meddelandet `452 requested action aborted: try again later` - dessa prövades automatiskt igen och inga åtgärder behövs.

* **Hårda studsar** med meddelandet `550 <email address> recipient rejected` har returnerats av Internet-leverantören den 26 januari, mellan 8.00 och 2.00 lokal tid, för att förhindra att avsändare fortsätter överbelasta sina servrar. Som Italia Online Postmaster har bekräftat är dessa inte riktigt hårda studsar, så vi rekommenderar att alla e-postadresser som uteslöts den 26 januari 2023 på grund av det meddelandet tas bort från karantänen.

## Process som ska uppdateras{#outage-update}

Adobe Campaign har automatiskt lagt till de här mottagarna i karantänlistan med en **[!UICONTROL Status]** inställning för **[!UICONTROL Quarantine]**. För att korrigera detta måste du uppdatera din karantäntabell i Campaign genom att hitta och ta bort de här mottagarna eller ändra deras **[!UICONTROL Status]** till **[!UICONTROL Valid]** så att nattrensningsarbetsflödet tar bort dem.

Om du vill hitta de mottagare som påverkades av det här problemet, eller om det händer igen med någon annan Internet-leverantör, kan du läsa instruktionerna [på den här sidan](../../delivery/using/understanding-quarantine-management.md#unquarantine-bulk).
