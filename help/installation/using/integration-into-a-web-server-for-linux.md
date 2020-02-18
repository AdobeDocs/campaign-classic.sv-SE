---
title: Integrering med en webbserver för Linux
seo-title: Integrering med en webbserver för Linux
description: Integrering med en webbserver för Linux
seo-description: null
page-status-flag: never-activated
uuid: 7b18d176-4458-46a8-8da4-3621f90c6b13
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 752ba848-aee9-4bb0-b2c5-490f3124f74e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a37daa8e31afd3d2ab7d5b70bd8ae02c59ce9ee0

---


# Integrering med en webbserver för Linux{#integration-into-a-web-server-for-linux}

Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP (och SOAP).

Du kan använda den här integrerade Tomcat-servern för att hantera HTTP-begäranden.

I detta fall:

* Standardlyssningsporten är 8080. Mer information om hur du ändrar den finns i [Konfigurera Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Klientkonsolerna ansluter sedan med en URL som:

   ```
   http://<computer>:8080
   ```

Av säkerhets- och administrationsskäl rekommenderar vi dock att du använder en dedikerad webbserver som huvudstartpunkt för HTTP-trafik när datorn som kör Adobe Campaign exponeras på Internet och du vill öppna åtkomst till konsolen utanför nätverket.

Med en webbserver kan du också garantera datasekretess med HTTP-protokollet.

På samma sätt måste du använda en webbserver när du vill använda spårningsfunktionen, som bara är tillgänglig som en tilläggsmodul till en webbserver.

>[!NOTE]
>
>Om du inte använder spårningsfunktionen kan du utföra en standardinstallation av Apache eller IIS med en omdirigering till Campaign. Modulen för spårning av webbservertillägg krävs inte.

## Konfigurera Apache-webbservern med Debian {#configuring-the-apache-web-server-with-debian}

Detta gäller om du har installerat Apache under en distribution som baseras på APT.

Använd följande steg:

1. Inaktivera modulerna som läses in som standard med följande kommando:

   ```
   a2dismod auth_basic authn_file authz_default authz_user autoindex cgi dir env negotiation userdir
   ```

   Kontrollera att modulerna **alias**, **authz_host** och **mime** fortfarande är aktiverade. Använd följande kommando för att göra detta:

   ```
   a2enmod  alias authz_host mime
   ```

1. Skapa filen **nlsrv.load** i **/etc/apache2/mods-available** och infoga följande innehåll:

   I Debian 8:

   ```
   LoadModule requesthandler24_module /usr/local/[INSTALL]/nl6/lib/libnlsrvmod.so
   ```

1. Skapa filen **nlsrv.conf** i **/etc/apache2/mods-available** med följande kommando:

   ```
   ln -s /usr/local/[INSTALL]/nl6/tomcat-7/conf/apache_neolane.conf /etc/apache2/mods-available/nlsrv.conf
   ```

1. Aktivera den här modulen med följande kommando:

   ```
    a2enmod nlsrv
   ```

   Om du använder modulen **mod_rewrite** för Adobe Campaign-sidor måste du byta namn på **filerna nlsrv.load** och **nlsrv.conf** till **zz-nlsrv.load** och **zz-nlsrv.conf**. Om du vill aktivera modulen kör du följande kommando:

   ```
   a2enmod zz-nlsrv
   ```

1. Redigera filen **/etc/apache2/envvars** , lägg till följande rader:

   ```
   # Added Neolane
   if [ "$LD_LIBRARY_PATH" != "" ]; then export LD_LIBRARY_PATH="/usr/local/neolane/nl6/lib:$LD_LIBRARY_PATH"; else export LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib; fi
   export USERPATH=/usr/local/neolane
   ```

   Spara ändringarna.

1. Lägg sedan till Adobe Campaign-användare i Apache-användargruppen och vice versa med följande kommandotyp:

   ```
   usermod neolane -G www-data
   usermod www-data -G neolane
   ```

1. Starta om Apache:

   ```
   invoke-rc.d apache2 restart
   ```

## Konfigurera Apache-webbservern i RHEL {#configuring-apache-web-server-in-rhel}

Den här proceduren gäller om du har installerat och skyddat Apache under ett RPM-baserat (RHEL, CentOS och Suse) paket.

Använd följande steg:

1. Aktivera följande Apache-moduler i `httpd.conf` filen:

   ```
   alias
   authz_host
   mime
   ```

1. Inaktivera följande moduler:

   ```
   auth_basic
   authn_file
   authz_default
   authz_user
   autoindex
   cgi
   dir
   env
   negotiation
   userdir
   ```

   Kommentera de funktioner som är kopplade till inaktiverade moduler:

   ```
   DirectoryIndex
   IndexOptions    
   AddIconByEncoding    
   AddIconByType    
   AddIcon    
   DefaultIcon    
   ReadmeName    
   HeaderName    
   IndexIgnore    
   LanguagePriority    
   ForceLanguagePriority
   ```

1. Skapa en Adobe Campaign-specifik konfigurationsfil i `/etc/httpd/conf.d/` mappen. Till exempel `CampaignApache.conf`

1. För **RHEL7** lägger du till följande instruktioner i filen:

   ```
   LoadModule requesthandler24_module /usr/local/neolane/nl6/lib/libnlsrvmod.so
   Include /usr/local/neolane/nl6/tomcat-7/conf/apache_neolane.conf
   ```

1. För **RHEL7**:

   Lägg till `/etc/systemd/system/httpd.service` filen med följande innehåll:

   ```
   .include /usr/lib/systemd/system/httpd.service
   
   [Service]
   Environment=USERPATH=/usr/local/neolane LD_LIBRARY_PATH=/usr/local/neolane/nl6/lib
   ```

   Uppdatera modulen som används av systemet:

   ```
   systemctl daemon-reload
   ```

1. Lägg sedan till Adobe Campaign-operatorer i Apache-operatorgruppen och vice versa genom att köra kommandot:

   ```
   usermod -a -G neolane apache
   usermod -a -G apache neolane
   ```

   Vilka gruppnamn som ska användas beror på hur Apache har konfigurerats.

1. Kör Apache och Adobe Campaign-servern.

   För RHEL7:

   ```
   systemctl start httpd
   systemctl start nlserver
   ```

## Starta webbservern och testa konfigurationen{#launching-the-web-server-and-testing-the-configuration}

Nu kan du testa konfigurationen genom att starta Apache. Adobe Campaign-modulen bör nu visa sin banderoll på konsolen (två banderoller på vissa operativsystem):

```
 /etc/init.d/apache start
```

Följande information visas:

```
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
12:26:28 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:26:28 >   Web server start (pid=29698, tid=-1212463424)...
12:26:28 >   Server started
```

Kontrollera sedan att den svarar genom att skicka en test-URL.

Du kan testa detta från kommandoraden genom att köra:

```
 telnet localhost 80  
```

Du bör få:

```
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
````

Ange sedan:

```
GET /r/test
````

Följande information visas:

```
<redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='' localHost='XXXX'/>
Connection closed by foreign host.
````

Du kan också begära URL:en [`https://<computer>`](https://machine/r/test) från en webbläsare.