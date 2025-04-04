---
product: campaign
title: Fil- och resurshantering
feature: Installation, Application Settings
description: Lär dig hur du konfigurerar fil- och resurshantering i Campaign
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 236afdfe-fb23-4ebb-b000-76e14bf01d9e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 1%

---

# Fil- och resurshantering{#file-and-resmanagement}



## Begränsa filformat för överföring {#limiting-uploadable-files}

Använd attributet **uploadWhiteList** för att begränsa vilka filtyper som är tillgängliga för överföring på Adobe Campaign-servern.

Det här attributet är tillgängligt i elementet **dataStore** i filen **serverConf.xml**. Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

Standardvärdet för attributet är **.+** och låter dig överföra vilken filtyp som helst.

Om du vill begränsa möjliga format ersätter du attributvärdet med ett giltigt reguljärt uttryck för java. Du kan ange flera värden genom att separera dem med kommatecken.

Exempel: **uploadWhiteList=&quot;.&#42;.png,Med &#42;.jpg** kan du överföra PNG- och JPG-format till servern. Inga andra format accepteras.

Du kan också förhindra att viktiga filer överförs genom att konfigurera webbservern. [Läs mer](web-server-configuration.md)

>[!NOTE]
>
>Attributet **uploadWhiteList** begränsar de filtyper som är tillgängliga för överföring på Adobe Campaign-servern. Men om publiceringsläget är **Spårningsservrar** eller **Andra Adobe Campaign-servrar** måste även attributet **uploadWhitelist** uppdateras på dessa servrar.

## Konfiguration för proxyanslutning {#proxy-connection-configuration}

Du kan ansluta Campaign-servern till ett externt system via en proxy, till exempel med hjälp av en **filöverföringsaktivitet** . För att uppnå detta måste du konfigurera avsnittet **proxyConfig** i filen **serverConf.xml** via ett specifikt kommando. Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

Följande proxyanslutningar är möjliga: HTTP, HTTPS, FTP, SFTP. Observera att från och med Campaign 20.2 är HTTP- och HTTPS-protokollparametrarna **inte längre tillgängliga**. Dessa parametrar nämns fortfarande nedan eftersom de fortfarande är tillgängliga i tidigare versioner - inklusive 9032.

>[!CAUTION]
>
>Endast det grundläggande autentiseringsläget stöds. NTLM-autentisering stöds inte.
>
>SOCKS-proxies stöds inte.
>

Du kan använda följande kommando:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

protokollparametrar kan vara&quot;http&quot;,&quot;https&quot; eller&quot;ftp&quot;.

Om du anger FTP på samma port som HTTP/HTTPS-trafik kan du använda följande:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Alternativen http och https används bara när protokollparametern är ftp och anger om tunnlingen på den angivna porten ska utföras via HTTPS eller via HTTP.

Om du använder olika portar för FTP-/SFTP- och HTTP/HTTPS-trafik över proxyservern bör du ange protokollparametern ftp.


Exempel:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Ange sedan lösenordet.

HTTP-anslutningar definieras i parametern proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS-anslutningar definieras i parametern proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP-/FTPS-anslutningar definieras i parametern proxyFTP:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Om du använder samma proxy för flera anslutningstyper definieras bara proxyHTTP med useSingleProxy inställt på &quot;1&quot; eller &quot;true&quot;.

Om du har interna anslutningar som inte ska gå igenom proxyn lägger du till dem i parametern override.

Om du tillfälligt vill inaktivera proxyanslutningen anger du parametern enabled till &quot;false&quot; eller &quot;0&quot;.

Om du behöver använda iOS HTTP/2-anslutningen via en proxy stöds följande HTTP-proxylägen:

* HTTP utan autentisering
* Grundläggande HTTP-autentisering

Om du vill aktivera proxyläget måste följande ändring göras i filen `serverconf.xml`:

```
<nmac useHTTPProxy="true">
```

Mer information om den här iOS HTTP/2-anslutningen finns på [sidan](../../delivery/using/about-mobile-app-channel.md).

## Hantera offentliga resurser {#managing-public-resources}

För att vara allmänt tillgängliga måste de bilder som används i e-postmeddelanden och offentliga resurser som är kopplade till kampanjer finnas på en externt tillgänglig server. De kan sedan vara tillgängliga för externa mottagare eller operatorer. [Läs mer](../../installation/using/deploying-an-instance.md#managing-public-resources).

Offentliga resurser lagras i katalogen **/var/res/instance** i Adobe Campaign installationskatalog.

Den matchande URL:en är: **http://server/res/instance** där **instance** är namnet på spårningsinstansen.

Du kan ange en annan katalog genom att lägga till en nod i filen **conf-`<instance>`.xml** för att konfigurera lagring på servern. Det innebär att följande rader läggs till:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

I det här fallet bör den nya URL:en för de offentliga resurserna som anges i den övre delen av fönstret i distributionsguiden peka på den här mappen.
