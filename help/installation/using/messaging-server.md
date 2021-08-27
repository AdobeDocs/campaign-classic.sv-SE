---
product: campaign
title: Meddelandeserver
description: Meddelandeserver
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# Meddelandeserver{#messaging-server}

![](../../assets/v7-only.svg)

Adobe Campaign hanterar utgående e-post internt, men en traditionell e-postserver krävs för att ta emot inkommande meddelanden som är länkade till returnerad e-post (från e-postmeddelanden). De postlådor som konfigureras på den här servern bearbetas automatiskt av programmet.

Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returpost om de behåller rubrikerna för SMTP-meddelande-ID när de hämtar e-postmeddelandet. Implementeringar som använder Qmail, SendMail och Microsoft Exchange är till exempel under produktion. I vissa installationer av Lotus Notes/domino upptäcktes dock ett problem med att behålla meddelandehuvuden.

>[!CAUTION]
>
>Den här e-postservern kan behöva hantera stora mängder: I initiala faser kan typiska listor producera upp till 10 % studsfrekvens (om du skickar 100 000 meddelanden förväntas ta emot 10 000 studsar).
>
>Därför rekommenderar vi att du inte använder företagets meddelandeserver för den här uppgiften eftersom den kan påverkas mycket.
>
>Du bör konfigurera en specifik underdomän till din DNS och en dedikerad server för att skicka studsade meddelanden.
