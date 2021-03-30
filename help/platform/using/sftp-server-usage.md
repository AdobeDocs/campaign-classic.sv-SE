---
solution: Campaign Classic
product: campaign
title: Använda en SFTP-server
description: Läs mer om de effektivaste strategierna för SFTP-servrar och felsökning.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 6%

---


# Bästa praxis och felsökning för SFTP-servrar {#sftp-server-usage}

## Globala rekommendationer för SFTP-servern {#global-recommendations}

När du hanterar filer och data för ETL-ändamål lagras dessa filer på en SFTP-värdserver som tillhandahålls av Adobe. Se till att du följer rekommendationerna nedan när du använder SFTP-servrar.

* Använd nyckelbaserad autentisering i stället för lösenordsautentisering för att undvika att lösenordet förfaller (lösenord har en giltighetsperiod på 90 dagar). Dessutom kan du med nyckelbaserad autentisering generera flera nycklar, till exempel när du hanterar flera enheter. För lösenordsautentisering krävs däremot att du delar lösenordet med alla enheter som du hanterar.

   Nyckelformatet som stöds är SSH-2 RSA 2048. Tangenter kan genereras med verktyg som PyTTY (Windows) eller ssh-keygen (Unix). Du måste ange den offentliga nyckeln till supportteamet via [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att kunna överföra den till Campaign-servern.

* Använd batchbearbetning i SFTP-överföringar och i arbetsflöden.

* Hantera fel/undantag.

* Som standard är alla mappar som du skapar i läs-/skrivläge endast för din identifierare. När du skapar mappar som ska vara tillgängliga för Campaign måste du konfigurera dem med läs- och skrivbehörighet för hela gruppen. I annat fall kan arbetsflöden av säkerhetsskäl inte skapa eller ta bort filer eftersom de körs med en annan identifierare inom samma grupp.

* De offentliga IP-adresserna som du försöker initiera SFTP-anslutningen från måste läggas till i tillåtelselista i Campaign-instansen. Du kan begära att få lägga till IP-adresser till tillåtelselista via [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Bästa praxis för databasanvändning {#sftp-server-best-practices}

SFTP-servrar är avsedda att vara tillfälliga lagringsutrymmen där du kan styra kvarhållande och borttagning av filer.

Om de inte används eller övervakas på rätt sätt kan de här utrymmena snabbt fylla det fysiska utrymmet på servern och leda till att filer trunkeras vid efterföljande överföringar. När utrymmet är mättat kan automatisk tömning utlösa och radera de äldsta filerna från SFTP-lagringen.

För att undvika sådana problem rekommenderar Adobe att du följer de bästa metoderna nedan.

>[!NOTE]
>
>Om din instans finns på AWS kan du övervaka din SFTP-serverlagring med Campaign Classic [Kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html). Om du vill kontrollera om din instans finns på AWS följer du stegen som beskrivs i [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).
>
>Kontrollpanelen är tillgänglig för alla administratörsanvändare. Anvisningar om hur du beviljar administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
>
>Observera att din instans måste uppgraderas med den senaste [Gold Standard](../../rn/using/gs-overview.md)-versionen eller den [senaste GA-versionen (21.1)](../../rn/using/latest-release.md). Lär dig hur du kontrollerar din version i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

* Serverstorleksmöjligheterna varierar beroende på din licens. Under alla omständigheter bör du behålla minsta möjliga antal uppgifter och endast lagra data så länge som krävs (15 dagar är den högsta tillåtna tidsgränsen).

* Använd arbetsflöden för att ta bort data på rätt sätt (hantera lagring från arbetsflöden som förbrukar data).

* Det kan hända att du loggar in på SFTP för att direkt kontrollera vad som finns där.

* Kom ihåg att SFTP-diskhantering i första hand är ditt ansvar.

## Extern SFTP-serveranvändning {#external-SFTP-server}

Om du använder en egen SFTP-server måste du följa rekommendationerna ovan så mycket som möjligt.

När du i Campaign Classic anger en sökväg till en extern SFTP-server skiljer sig dessutom sökvägssyntaxen åt beroende på operativsystemet för SFTP-servern:

* Om SFTP-servern är på **Windows** ska du alltid använda en relativ sökväg.
* Om STP-servern är på **Linux** ska du alltid använda en sökväg som är relativ till hemmet (med början från &quot;~/&quot;) eller en absolut sökväg (med början från &quot;/&quot;).

## Anslutningsproblem med värdserver för SFTP-Adobe {#sftp-server-troubleshooting}

I avsnittet nedan visas den information som ska kontrolleras och tillhandahållas till supportteamet via [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) när anslutningsproblem med värdbaserade SFTP-servrar från Adobe inträffar.

1. Kontrollera att instansen körs. Det gör du genom att öppna webbläsaren och sedan göra ett **[!UICONTROL GET]**-anrop på instansen **[!UICONTROL /r/test]**-slutpunkten:

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

   Om porten inte öppnas kontrollerar du att du har öppnat utgående anslutningar och försöker sedan igen. Om du fortfarande stöter på anslutningsproblem kan du dela utdata från kommandot med [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)-teamet.

1. Kontrollera att den offentliga IP-adressen som du försöker initiera SFTP-anslutningen från är den som du skickade till Adobe Support för tillåtelselista.
1. Om du använder en lösenordsbaserad autentisering kan ditt lösenord ha gått ut (lösenorden har en giltighetsperiod på 90 dagar). Därför rekommenderar vi starkt att du använder nyckelbaserad autentisering (se [SFTP-serverns bästa praxis](#sftp-server-best-practices)).
1. Om du använder en nyckelbaserad autentisering kontrollerar du att nyckeln du använder är samma som du angav för [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)-teamet för instanskonfigurationen.
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

Detta fel indikerar att FTP-serverns domännamn inte kunde matchas korrekt. Så här felsöker du:

1. Felsök **DNS-serverkonfiguration**:

   1. Kontrollera om servernamnet har lagts till i den lokala DNS-servern.
   1. Om ja, kör följande kommando på Adobe Campaign-servern för att hämta IP-adressen:

      `nslookup <server domain name>`

      Detta bekräftar att FTP-servern fungerar och kan nås från Adobe Campaign programserver.

1. Felsök **sessionsloggar**:

   1. Dubbelklicka på aktiviteten [Filöverföring](../../workflow/using/file-transfer.md) i arbetsflödet.
   1. Gå till fliken **[!UICONTROL File Transfer]** och klicka sedan på **[!UICONTROL Advanced Parameters]**.
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
