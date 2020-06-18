---
title: Användning av SFTP-server
seo-title: Användning av SFTP-server
description: Användning av SFTP-server
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Användning av SFTP-server{#sftp-server-usage}

## Bästa praxis för SFTP-server {#sftp-server-best-practices}

När du hanterar filer och data för ETL-ändamål lagras dessa filer på en SFTP-värdserver som tillhandahålls av Adobe. Denna SFTP är avsedd att vara ett tillfälligt lagringsutrymme där du kan styra lagring och borttagning av filer.

Om utrymmet inte används eller övervakas korrekt kan det snabbt fylla det fysiska utrymmet på servern och leda till att filer trunkeras vid efterföljande överföringar. När utrymmet är mättat kan automatisk tömning utlösa och radera de äldsta filerna från SFTP-lagringen.

För att undvika sådana problem rekommenderar Adobe att du följer god praxis nedan.

>[!NOTE]
>
>Om din instans finns på AWS kan du övervaka din SFTP-serverlagring med Campaign Classic på [Kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html).
>
>Följ stegen i [det här avsnittet](https://docs.adobe.com/content/help/en/control-panel/using/faq.html#ims-org-id) för att kontrollera om din instans finns på AWS.

* Serverstorleksmöjligheterna varierar beroende på din licens. Under alla omständigheter bör du behålla minsta möjliga antal uppgifter och endast lagra data så länge som krävs (15 dagar är den högsta tillåtna tidsgränsen).
* Använd nyckelbaserad autentisering i stället för lösenordsautentisering för att undvika att lösenordet förfaller (lösenord har en giltighetsperiod på 90 dagar). Dessutom kan du med nyckelbaserad autentisering generera flera nycklar, till exempel när du hanterar flera enheter. För lösenordsautentisering krävs däremot att du delar lösenordet med alla enheter som du hanterar.

   Nyckelformatet som stöds är SSH-2 RSA 2048. Tangenter kan genereras med verktyg som PyTTY (Windows) eller ssh-keygen (Unix). Du måste ange den offentliga nyckeln till Adobe Support-teamet via en [supportanmälan](https://support.neolane.net) för att få den överförd till Campaign-servern.

* Använd arbetsflöden för att ta bort data på rätt sätt (hantera lagring från arbetsflöden som förbrukar data).
* Använd gruppbearbetning i SFTP-överföringar och i arbetsflöden.
* Hantera fel/undantag.
* Det kan hända att du loggar in på SFTP för att direkt kontrollera vad som finns där.
* Kom ihåg att SFTP-diskhantering i första hand är ditt ansvar.
* Som standard är alla mappar som du skapar i läs-/skrivläge endast för din identifierare. När du skapar mappar som ska vara tillgängliga för Campaign måste du konfigurera dem med läs- och skrivbehörighet för hela gruppen. I annat fall kan arbetsflöden av säkerhetsskäl inte skapa eller ta bort filer eftersom de körs med en annan identifierare inom samma grupp.
* De offentliga IP-adresser som du försöker initiera SFTP-anslutningen från måste läggas till i listan över tillåtna i Campaign-instansen. Du kan begära att få lägga till IP-adresser i listan över tillåtna via en [supportanmälan](https://support.neolane.net).

>[!CAUTION]
>
>Om du använder en egen SFTP-server måste du följa rekommendationerna ovan så mycket som möjligt.

## Felsökning av SFTP-server {#sftp-server-troubleshooting}

I avsnittet nedan visas den information som ska kontrolleras och tillhandahållas Adobe Support-teamet via en [supportanmälan](https://support.neolane.net) när anslutningsproblem med Adobes värdservrar för SFTP uppstår.

1. Kontrollera att instansen körs. Det gör du genom att öppna webbläsaren och sedan göra ett **[!UICONTROL GET]** anrop på instansens **[!UICONTROL /r/test]** slutpunkt:

   ```
   https://instanceUrl/r/test
   ```

   Om instansen körs bör du få den här typen av svar:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   Ange i alla fall kommandotolken i supportbiljetten.

1. Kontrollera om den utgående porten 22 är öppen på den plats som du försöker initiera SFTP-anslutningen från. Använd följande kommando för att göra detta:

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Med nätverksverktyget kan du enkelt hantera nätverksanslutningar på olika operativsystem (se [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Om porten inte öppnas kontrollerar du att du har öppnat utgående anslutningar och försöker sedan igen. Om du fortfarande har problem med anslutningen kan du dela utdata från kommandot med Adobe Support-teamet.

1. Kontrollera att den offentliga IP-adressen som du försöker initiera SFTP-anslutningen från är den som du skickade till Adobe Support för listan över tillåtna.
1. Om du använder en lösenordsbaserad autentisering kan ditt lösenord ha gått ut (lösenorden har en giltighetsperiod på 90 dagar). Därför rekommenderar vi starkt att du använder nyckelbaserad autentisering (se [Bästa praxis](#sftp-server-best-practices)för SFTP-server).
1. Om du använder en nyckelbaserad autentisering kontrollerar du att nyckeln du använder är samma som du angav för Adobe Support-teamet för instanskonfigurationen.
1. Om du använder FileZilla eller ett motsvarande FTP-verktyg anger du anslutningsloggarna i supportbiljetten.

