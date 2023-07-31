---
product: campaign
title: Använda en SFTP-server
description: Läs mer om de effektivaste strategierna för SFTP-servrar och felsökning
feature: Troubleshooting
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 15%

---

# Bästa praxis och felsökning för SFTP-servrar {#sftp-server-usage}



## Globala rekommendationer för SFTP-server {#global-recommendations}

När du hanterar filer och data för ETL-ändamål lagras dessa filer på en SFTP-värdserver som tillhandahålls av Adobe. Se till att du följer rekommendationerna nedan när du använder SFTP-servrar.

* Använd nyckelbaserad autentisering i stället för lösenordsautentisering för att undvika att lösenordet förfaller (lösenord har en giltighetsperiod på 90 dagar). Dessutom kan du med nyckelbaserad autentisering generera flera nycklar, till exempel när du hanterar flera enheter. För lösenordsautentisering krävs tvärtom att du delar lösenordet med alla enheter som du hanterar.

  Nyckelformatet som stöds är SSH-2 RSA 2048. Tangenter kan genereras med verktyg som PyTTY (Windows) eller ssh-keygen (Unix). Du måste ange den offentliga nyckeln till Adobe Support via [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) om du vill att den ska överföras till Campaign-servern.

* Använd batchbearbetning i SFTP-överföringar och i arbetsflöden.

* Hantera fel/undantag.

* Som standard är alla mappar som du skapar i läs-/skrivläge endast för din identifierare. När du skapar mappar som ska vara tillgängliga för Campaign måste du konfigurera dem med läs- och skrivbehörighet för hela gruppen. I annat fall kan arbetsflöden av säkerhetsskäl inte skapa eller ta bort filer eftersom de körs med en annan identifierare inom samma grupp.

* De offentliga IP-adresserna som du försöker initiera SFTP-anslutningen från måste läggas till i tillåtelselista i Campaign-instansen. Du kan begära att få lägga till IP-adresser till tillåtelselista via [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Bästa praxis för databasanvändning {#sftp-server-best-practices}

SFTP-servrar är avsedda att vara tillfälliga lagringsutrymmen där du kan styra kvarhållande och borttagning av filer.

Om de inte används eller övervakas på rätt sätt kan de här utrymmena snabbt fylla det fysiska utrymmet på servern och leda till att filer trunkeras vid efterföljande överföringar. När utrymmet är mättat kan automatisk tömning utlösa och radera de äldsta filerna från SFTP-lagringen.

För att undvika sådana problem rekommenderar Adobe att du följer de bästa metoderna nedan.

>[!NOTE]
>
>Om din instans ligger hos AWS kan du övervaka din SFTP-serverlagring med Campaign Classic [Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). Följ stegen på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=sv) för att kontrollera om instanser har AWS som värd.
>
>Kontrollpanelen är tillgänglig för alla administratörsanvändare. Stegen för att bevilja administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv#discover-control-panel).
>
>Observera att din instans måste uppgraderas med [senaste GA-version](../../rn/using/rn-overview.md). Läs om hur du kontrollerar din version i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

* Serverstorleksmöjligheterna varierar beroende på din licens. Under alla omständigheter bör du behålla minsta möjliga antal uppgifter och endast lagra data så länge som krävs (15 dagar är den högsta tillåtna tidsgränsen).

* Använd arbetsflöden för att ta bort data på rätt sätt (hantera lagring från arbetsflöden som förbrukar data).

* Det kan hända att du loggar in på SFTP för att direkt kontrollera vad som finns där.

* Kom ihåg att SFTP-diskhantering i första hand är ditt ansvar.

## Extern SFTP-serveranvändning {#external-SFTP-server}

Om du använder en egen SFTP-server måste du följa rekommendationerna ovan så mycket som möjligt.

När du i Campaign Classic anger en sökväg till en extern SFTP-server skiljer sig dessutom sökvägssyntaxen åt beroende på operativsystemet för SFTP-servern:

* Om SFTP-servern är på **Windows** använder du alltid en relativ sökväg.
* Om STP-servern är på **Linux** använder du alltid en sökväg som är relativ till hemmet (som börjar med &quot;~/&quot;) eller en absolut sökväg (som börjar med &quot;/&quot;).

## Anslutningsproblem med värdserver för Adobe SFTP-server {#sftp-server-troubleshooting}

I avsnittet nedan listas den information som ska kontrolleras och tillhandahållas Adobe supportteam via [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) när du stöter på anslutningsproblem med värdbaserade SFTP-servrar i Adobe.

1. Kontrollera att instansen körs. Det gör du genom att öppna webbläsaren och sedan skapa en **[!UICONTROL GET]** anrop till instansen **[!UICONTROL /r/test]** slutpunkt:

   ```
   https://instanceUrl/r/test
   ```

   Om instansen körs bör du få den här typen av svar:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
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

   Om porten inte är öppen kontrollerar du att du har öppnat utgående anslutningar och försöker sedan igen. Om du fortfarande har problem med anslutningen kan du dela utdata från kommandot med [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team.

1. Kontrollera att den offentliga IP-adressen som du försöker initiera SFTP-anslutningen från är den som du skickade till Adobe Support för tillåtelselista.
1. Om du använder en lösenordsbaserad autentisering kan ditt lösenord ha gått ut (lösenorden har en giltighetsperiod på 90 dagar). Vi rekommenderar därför starkt att du använder en nyckelbaserad autentisering (se [Bästa praxis för SFTP-server](#sftp-server-best-practices)).
1. Om du använder en nyckelbaserad autentisering kontrollerar du att nyckeln du använder är samma som du angav för [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team för instanskonfigurationen.
1. Om du använder FileZilla eller ett motsvarande FTP-verktyg anger du anslutningsloggarna i supportbiljetten.

## Felet &quot;Det gick inte att matcha värdnamnet&quot;

I det här avsnittet finns information om de kontroller och åtgärder som ska utföras vid hämtning av felet&quot;Det gick inte att lösa värdnamnet&quot; efter anslutning till FTP-servern från Campaign Classic.

I arbetsflödesjournalen visas följande loggar:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Det här felet inträffar när du försöker ansluta FTP-servern från ett arbetsflöde och hämta filerna från servern, medan du fortfarande kan ansluta via FTP med FileZilla eller WinSCP.

Det här felet indikerar att FTP-serverns domännamn inte kunde matchas korrekt. Så här felsöker du:

1. Felsökning **DNS-serverkonfiguration**:

   1. Kontrollera om servernamnet har lagts till i den lokala DNS-servern.
   1. Om ja, kör följande kommando på Adobe Campaign-servern för att hämta IP-adressen:

      `nslookup <server domain name>`

      Detta bekräftar att FTP-servern fungerar och kan nås från Adobe Campaign programserver.

1. Felsökning **sessionsloggar**:

   1. Dubbelklicka på [Filöverföring](../../workflow/using/file-transfer.md) aktivitet.
   1. Gå till **[!UICONTROL File Transfer]** tabbtangenten och klicka sedan på **[!UICONTROL Advanced Parameters]**.
   1. Markera alternativet **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Gå till arbetsflödet Granskning och kontrollera om loggarna visar felet &quot;Det gick inte att lösa värdnamnet&quot;.

1. Om SFTP-servern är värd för Adobe ska du kontrollera om IP har lagts till i tillåtelselista genom att kontakta Kundtjänst.

   Annars validera:

   * Lösenordet innehåller inte @. Anslutningen misslyckades om det finns @ i lösenordet.
   * Det finns inga brandväggsproblem som kan hindra kommunikationen mellan Adobe Campaign programserver och SFTP-server.
   * Kör spårnings- och telnet-kommandon från kampanjservern till programsviten för att se om det finns några anslutningsproblem.
   * Det finns inga problem med kommunikationsprotokoll.
   * Porten är öppen.
