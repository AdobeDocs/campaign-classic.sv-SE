---
title: Meddelandeserver
seo-title: Meddelandeserver
description: Meddelandeserver
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Meddelandeserver{#messaging-server}

Adobe Campaign hanterar utgående e-post internt, men en traditionell e-postserver krävs för att ta emot inkommande meddelanden som är länkade till returnerad e-post (från e-postmeddelanden). De postlådor som konfigureras på den här servern bearbetas automatiskt av programmet.

Alla servrar som konfigurerats för POP3-åtkomst kan användas för att ta emot returpost om de behåller rubrikerna för SMTP-meddelande-ID när de hämtar e-postmeddelandet. Implementeringar som använder Qmail, SendMail och Microsoft Exchange är till exempel under produktion. I vissa installationer av Lotus Notes/domino upptäcktes dock ett problem med att behålla meddelandehuvuden.

>[!CAUTION]
>
>Den här e-postservern kan behöva hantera stora mängder: I initiala faser kan typiska listor producera upp till 10 % studsfrekvens (om du skickar 100 000 meddelanden förväntas ta emot 10 000 studsar).
>
>Därför rekommenderar vi att du inte använder företagets meddelandeserver för den här uppgiften eftersom den kan påverkas mycket.
>
>Det är tillrådligt att konfigurera en specifik underdomän till din DNS och en dedikerad server för studentpost.
