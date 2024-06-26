---
product: campaign
title: Rekommendationer
description: Rekommendationer
feature: Monitoring
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 3%

---

# Rekommendationer{#recommendations}



Adobe Campaign är ett mycket transaktionssystem (OLTP-databas). Detta innebär att den underliggande databasen uppdateras ofta, vilket leder till försämrade prestanda över tiden. För att undvika den här typen av problem krävs regelbundet databasunderhåll.

>[!IMPORTANT]
>
>En databas fungerar bara optimalt om den upprätthålls regelbundet. Det automatiska underhåll som erbjuds av vissa RDBMS är inte tillräckligt och ersätter inte djupgående underhåll, som för alla transaktionsdatabassystem.
>  
>Procedurer som beskrivs i detta dokument är rekommendationer. Underhållsplanerna är databasadministratörens ansvar och måste vara den första kontakten om du får problem.
