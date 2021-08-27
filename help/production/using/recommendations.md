---
product: campaign
title: Rekommendationer
description: Rekommendationer
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Rekommendationer{#recommendations}

![](../../assets/v7-only.svg)

Adobe Campaign är ett mycket transaktionssystem (OLTP-databas). Detta innebär att den underliggande databasen uppdateras ofta, vilket leder till försämrade prestanda över tiden. För att undvika den här typen av problem krävs regelbundet databasunderhåll.

>[!IMPORTANT]
>
>En databas fungerar bara optimalt om den upprätthålls regelbundet. Det automatiska underhåll som erbjuds av vissa RDBMS är inte tillräckligt och ersätter inte djupgående underhåll, som för alla transaktionsdatabassystem.
>  
>Procedurer som beskrivs i detta dokument är rekommendationer. Underhållsplaner är databasadministratörens ansvar, och dessa måste vara den första kontakten om problem uppstår.
