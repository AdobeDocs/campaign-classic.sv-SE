---
product: campaign
title: Typ av underhåll
description: Typ av underhåll
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# Typ av underhåll{#types-of-maintenance}



## Programunderhåll {#application-maintenance}

Adobe Campaign har ett inbyggt arbetsflöde där du kan schemalägga vissa underhållsåtgärder för databaser: den **arbetsflöde för databasrensning**. Det här arbetsflödet utför följande uppgifter:

* Borttagning av utgångna poster.
* Borttagning av överblivna poster och återinitiering av status för utgångna objekt.
* uppdatera databasstatistiken.

>[!IMPORTANT]
>
>Observera att rensningsaktiviteten huvudsakligen handlar om underhåll på programnivå, inte om underhåll på RDBMS-nivå (med undantag för statistikuppdatering). Underhållsåtgärder krävs dock för databasen. Även om arbetsflödet för databasrensning fungerar som det ska betyder det inte att databasen är optimalt justerad.

## Tekniskt underhåll {#technical-maintenance}

Arbetsflödet för databasrensning innehåller inte något databasunderhållsverktyg: det är upp till dig att organisera underhållet. Om du vill göra det kan du antingen:

* samarbeta med databasadministratören för att konfigurera databasunderhåll med verktyg från tredje part,
* använda Adobe Campaign arbetsflödesmotor för att schemalägga och spåra underhållsaktiviteterna.

Dessa underhållsförfaranden skall utföras regelbundet och skall omfatta följande:

* indexera om tabeller som uppdateras ofta,
* kompakt/återskapa tabeller för att undvika fragmentering.

### Underhållsschema {#maintenance-schedule}

Du måste hitta lämpliga platser för att utföra dessa underhållsaktiviteter. De kan påverka databasens prestanda avsevärt när programmet körs eller till och med blockeras (på grund av låsning).

Dessa uppgifter körs vanligtvis en gång i veckan under en period med låg aktivitet som inte kolliderar med säkerhetskopiering, datainläsning eller aggregeringsberäkning. Vissa system som är mycket efterfrågade kräver oftare underhåll.

Mer ingående underhåll, till exempel fullständiga tabellversioner, kan utföras en gång i månaden, helst med program som är helt stoppade eftersom systemet ändå inte kan användas.

### Återskapa en tabell {#rebuilding-a-table}

Flera strategier är tillgängliga:

<table> 
 <thead> 
  <tr> 
   <th> Operationer </th> 
   <th> Beskrivning </th> 
   <th> Fördelar </th> 
   <th> Nackdelar </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Onlinedefragmentering<br /> </td> 
   <td> De flesta databasmotorer har defragmenteringsmetoder.<br /> </td> 
   <td> Använd helt enkelt databasdefragmenteringsmetoden. Dessa metoder hanterar vanligtvis integritetsproblem genom att låsa data under defragmentering.<br /> </td> 
   <td> Beroende på databasen kan dessa defragmenteringsmetoder anges som ett RDBMS-alternativ (Oracle) och är inte alltid det mest effektiva sättet att hantera större tabeller.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dumpa och återställa<br /> </td> 
   <td> Dumpa tabellen till en fil, ta bort tabellen i databasen och återställ från dumpen.<br /> </td> 
   <td> Det här är det enklaste sättet att defragmentera en tabell. Den enda lösningen när databasen är nästan full.<br /> </td> 
   <td> Eftersom tabellen tas bort och återskapas går det inte att lämna programmet online, inte ens i skrivskyddat läge (tabellen är inte tillgänglig under återställningsfasen).<br /> </td> 
  </tr> 
  <tr> 
   <td> Duplicera, byta namn och släppa<br /> </td> 
   <td> Då skapas en kopia av en tabell och dess index, den befintliga kopian tas bort och kopians namn ändras så att den ersätts.<br /> </td> 
   <td> Den här metoden är snabbare än den första metoden eftersom den genererar mindre I/O (ingen kopia som fil och läsning från den här filen).<br /> </td> 
   <td> Kräver dubbelt så mycket utrymme som utrymmet.<br /> Alla aktiva processer som skriver till tabellen under processen måste stoppas. Läsprocesserna påverkas dock inte eftersom tabellen byts ut i sista stund när den har byggts om. <br /> </td> 
  </tr> 
 </tbody> 
</table>
