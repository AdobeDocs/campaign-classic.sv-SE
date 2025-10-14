---
product: campaign
title: Användning av SFTP-server
description: Läs mer om de effektivaste strategierna för SFTP-servrar och felsökning
feature: Troubleshooting
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 9%

---

# Bästa praxis och felsökning för SFTP-servrar {#sftp-server-usage}

## Globala rekommendationer för SFTP-server {#global-recommendations}

När du hanterar filer och data för ETL-ändamål lagras dessa filer på en SFTP-värdserver som tillhandahålls av Adobe. Se till att du följer rekommendationerna nedan när du använder SFTP-servrar.

* Använd nyckelbaserad autentisering i stället för lösenordsautentisering för att undvika att lösenordet förfaller (lösenord har en giltighetsperiod på 90 dagar). Dessutom kan du med nyckelbaserad autentisering generera flera nycklar, till exempel när du hanterar flera enheter. För lösenordsautentisering krävs tvärtom att du delar lösenordet med alla enheter som du hanterar.

  Nyckelformatet som stöds är SSH-2 RSA 2048. Verktyget för att generera SSH-nycklar för Windows är PuTTYgen och ssh-keygen för Linux. Du kan överföra offentliga SSH-nycklar via Campaign-kontrollpanelen. [Läs mer](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/key-management){target="_blank"}

* Använd batchbearbetning i SFTP-överföringar och i arbetsflöden.

* Hantera fel/undantag.

* Som standard är alla mappar som du skapar i läs-/skrivläge endast för din identifierare. När du skapar mappar som ska vara tillgängliga för Campaign måste du konfigurera dem med läs- och skrivbehörighet för hela gruppen. I annat fall kan arbetsflöden av säkerhetsskäl inte skapa eller ta bort filer eftersom de körs med en annan identifierare inom samma grupp.

* De offentliga IP-adresserna som du försöker initiera SFTP-anslutningen från måste läggas till i tillåtelselista i Campaign-instansen. De offentliga IP-adresserna kan läggas till via Kontrollpanelen. [Läs mer](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/ip-range-allow-listing){target="_blank"}

## Bästa praxis för användning av SFTP-lagring {#sftp-server-best-practices}

SFTP-servrar är avsedda att vara tillfälliga lagringsutrymmen där du kan styra kvarhållande och borttagning av filer.

Om de inte används eller övervakas på rätt sätt kan de här utrymmena snabbt fylla det fysiska utrymmet på servern och leda till att filer trunkeras vid efterföljande överföringar. I Adobe-värdbaserade SFTP-servrar komprimeras filer om SFTP-lagringen når ett tröskelvärde på 80 %. Processen är automatisk och utlöses av Adobe övervakningssystem.

För att undvika sådana problem rekommenderar Adobe att du följer god praxis nedan.

>[!NOTE]
>
>* Du kan övervaka din SFTP-serverlagring med Campaign Classic [Kontrollpanel](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html){target="_blank"}.
>
>* Kontrollpanelen är tillgänglig för alla administratörsanvändare. Stegen för att bevilja administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv#discover-control-panel){target="_blank"}.
>
>* Observera att din instans måste uppgraderas med den [senaste GA-versionen](../../rn/using/rn-overview.md). Lär dig hur du kontrollerar din version i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version){target="_blank"}.

* Serverstorleksmöjligheterna varierar beroende på din licens. Under alla omständigheter bör du behålla minsta möjliga antal uppgifter och endast lagra data så länge som krävs (15 dagar är den högsta tillåtna tidsgränsen).

* Använd arbetsflöden för att ta bort data på rätt sätt (hantera lagring från arbetsflöden som förbrukar data).

* Det kan hända att du loggar in på SFTP för att direkt kontrollera vad som finns där.

* Kom ihåg att SFTP-diskhantering i första hand är ditt ansvar.

## Extern SFTP-serveranvändning {#external-SFTP-server}

Om du använder en egen SFTP-server måste du följa rekommendationerna ovan så mycket som möjligt.

När du i Campaign Classic anger en sökväg till en extern SFTP-server skiljer sig dessutom sökvägssyntaxen åt beroende på operativsystemet för SFTP-servern:

* Använd alltid en relativ sökväg om din SFTP-server finns på **Windows**.
* Om STP-servern är på **Linux** ska du alltid använda en relativ sökväg till hemmet (med början från &quot;~/&quot;) eller en absolut sökväg (med början från &quot;/&quot;).

## Anslutningsproblem med Adobe värdserver för SFTP-server {#sftp-server-troubleshooting}

I avsnittet nedan visas den information som ska kontrolleras och tillhandahållas Adobe supportteam via [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"} när anslutningsproblem med Adobe värdservrar för SFTP uppstår.

1. Kontrollera att instansen körs. Om du vill göra det öppnar du webbläsaren och gör sedan ett **[!UICONTROL GET]**-anrop för instansens **[!UICONTROL /r/test]**-slutpunkt:

   ```xml
   https://instanceUrl/r/test
   ```

   Om instansen körs bör du få den här typen av svar:

   ```xml
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
   ```

   Ange i alla fall kommandotolken i supportbiljetten.

1. Kontrollera om den utgående porten 22 är öppen på den plats som du försöker initiera SFTP-anslutningen från. Använd följande kommando för att göra detta:

   ```xml
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   Om porten inte är öppen kontrollerar du att du har öppnat utgående anslutningar och försöker sedan igen. Om du fortfarande stöter på anslutningsproblem kan du dela utdata från kommandot med [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) -teamet.

1. Kontrollera att den offentliga IP-adressen som du försöker initiera SFTP-anslutningen från är den som du skickade till Adobe Support för tillåtelselista.
1. Om du använder en lösenordsbaserad autentisering kan ditt lösenord ha gått ut (lösenorden har en giltighetsperiod på 90 dagar). Därför rekommenderar vi starkt att du använder nyckelbaserad autentisering (se [Bästa praxis för SFTP-server](#sftp-server-best-practices)).
1. Om du använder en nyckelbaserad autentisering kontrollerar du att nyckeln du använder är samma som du angav för [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) -teamet för instanskonfigurationen.
1. Om du använder FileZilla eller ett motsvarande FTP-verktyg anger du anslutningsloggarna i supportbiljetten.

## Felet &quot;Det gick inte att matcha värdnamnet&quot;

I det här avsnittet finns information om de kontroller och åtgärder som ska utföras vid hämtning av felet&quot;Det gick inte att lösa värdnamnet&quot; efter anslutning till FTP-servern från Campaign Classic.

I arbetsflödesjournalen visas följande loggar:

```xml
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Det här felet inträffar när du försöker ansluta FTP-servern från ett arbetsflöde och hämta filerna från servern, medan du fortfarande kan ansluta via FTP med FileZilla eller WinSCP.

Det här felet indikerar att FTP-serverns domännamn inte kunde matchas korrekt. Så här felsöker du:

1. Felsök **DNS-serverkonfigurationen**:

   1. Kontrollera om servernamnet har lagts till i den lokala DNS-servern.
   1. Om ja, kör följande kommando på Adobe Campaign-servern för att hämta IP-adressen:

      `nslookup <server domain name>`

      Detta bekräftar att FTP-servern fungerar och kan nås från Adobe Campaign programserver.

1. Felsök **sessionsloggar**:

   1. Dubbelklicka på aktiviteten [Filöverföring](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html){target="_blank"} i arbetsflödet.
   1. Gå till fliken **[!UICONTROL File Transfer]** och klicka sedan på **[!UICONTROL Advanced Parameters]**.
   1. Markera alternativet **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Gå till arbetsflödet Granskning och kontrollera om loggarna visar felet &quot;Det gick inte att lösa värdnamnet&quot;.

1. Om Adobe är värd för SFTP-servern kontrollerar du om IP har lagts till i tillåtelselista genom att kontakta Kundtjänst.

   Annars validera:

   * Lösenordet innehåller inte tecknet `@`. Anslutningen misslyckas om det finns ett `@`-tecken i lösenordet.
   * Det finns inga brandväggsproblem som kan hindra kommunikationen mellan Adobe Campaign programserver och SFTP-server.
   * Kör spårnings- och telnet-kommandon från kampanjservern till programsviten för att se om det finns några anslutningsproblem.
   * Det finns inga problem med kommunikationsprotokoll.
   * Porten är öppen.
