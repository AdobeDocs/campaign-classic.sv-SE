---
product: campaign
title: Rekommendationer
description: Rekommendationer
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-on-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 0429c3608fbcec98a397cc17fd45cd173cf64b6e
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 2%

---

# Rekommendationer{#recommendations}



Adobe Campaign är ett mycket transaktionssystem (OLTP-databas). Detta innebär att den underliggande databasen uppdateras ofta, vilket leder till försämrade prestanda över tiden. För att undvika den här typen av problem krävs regelbundet databasunderhåll.

>[!IMPORTANT]
>
>En databas fungerar bara optimalt om den upprätthålls regelbundet. Det automatiska underhåll som erbjuds av vissa RDBMS är inte tillräckligt och ersätter inte djupgående underhåll, som för alla transaktionsdatabassystem.
>  
>Procedurer som beskrivs i detta dokument är rekommendationer. Underhållsplanerna är databasadministratörens ansvar och måste vara den första kontakten om problemet uppstår.
