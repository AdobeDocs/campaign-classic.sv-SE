---
solution: Campaign Classic
product: campaign
title: Integrera med Adobe Target
description: Integrera med Adobe Target
audience: integrations
content-type: reference
topic-tags: adobe-target
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 4%

---


# Integrating with Adobe Target{#integrating-with-adobe-target}

Tack vare integrationen mellan Adobe Campaign och Adobe Target (Classic och Standard) i Adobe Experience Cloud kan du inkludera ett erbjudande från Adobe Target i en e-postleverans från Adobe Campaign.

Följande princip gäller: När en mottagare öppnar ett e-postmeddelande som skickas via Adobe Campaign kan du med ett anrop till Adobe Target visa en dynamisk version av innehållet. Den här dynamiska versionen beräknas utifrån de regler som anges i förväg när e-postmeddelandet skapas.

Läs mer om integrationen mellan Adobe Campaign och Adobe Target med [dessa fyra tips och trick](https://www.adobe.com/content/dam/www/us/en/marketing/campaign/pdfs/Adobe_Campaign_for_Target_Tips_and_Tricks.pdf).
>[!NOTE]
>
>Integreringen stöder bara statiska bilder. Resten av innehållet kan inte personaliseras.

Adobe Target kan använda flera typer av data:

* Data från Adobe Campaign datamart
* Segment som är länkade till besökar-ID i Adobe Target, om de data som används inte omfattas av juridiska begränsningar
* Adobe Target data: användaragent, IP-adress, geolokaliseringsdata

>[!NOTE]
>
>Du hittar även information om integrationen mellan Adobe Campaign och Adobe Target på [Adobe Target hjälpsidor](https://docs.adobe.com/content/help/sv-SE/target/using/integrate/campaign-and-target.html).
