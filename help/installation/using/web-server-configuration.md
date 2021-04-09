---
solution: Campaign Classic
product: campaign
title: Webbserverkonfiguration
description: Lär dig mer om de effektivaste strategierna för webbserverkonfiguration.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Webbserverkonfiguration {#web-server-configuration}

Nedan hittar du några av de effektivaste strategierna för webbserverkonfiguration (Apache/IIS).

* Ändra standardfelsidor.

* Inaktivera tidigare SSL-version och ciphers:

   **Redigera /etc/apache2/mods-available/ssl.conf i Apache**. Här är ett exempel:

   * SSLProtocol all -SSLv2 -SSLv3 -TLSv1
   * SSLCipherSuite HIGH:MEDIUM:!NULL:!MD5:!SSLv3:!SSLv2:!TLSv1

   **Utför följande konfiguration på IIS**  (se  [dokumentationen](https://support.microsoft.com/en-us/kb/245030)):

   * Lägg till registerundernyckel i HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Om du vill att systemet ska kunna använda de protokoll som inte ska förhandlas som standard (till exempel TLS 1.2) ändrar du DWORD-värdedata för värdet DisabledByDefault till 0x0 i följande registernycklar under nyckeln **Protokoll**:

      SCHANNEL\Protocols\TLS 1.2\Client

      SCHANNEL\Protocols\TLS 1.2\Server
   **Inaktivera SSL x.0**

   SCHANNEL\Protocols\SSL 3.0\Client: DisabledByDefault: 32-bitars DWORD-värde till 1

   SCHANNEL\Protocols\SSL 3.0\Server: Aktiverad: 32-bitars DWORD-värde till 0

* Ta bort metoden **TRACE**:

   **I Apache** kan du redigera i /etc/apache2/conf.d/security: TraceEnable  **Off**

   **Utför följande konfiguration på IIS**  (se  [dokumentationen](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)):

   * Kontrollera att **rolltjänsten eller funktionen Begär filtrering** är installerad.
   * Klicka på fliken för HTTP-verb i rutan **Begär filtrering** och klicka sedan på Neka verb. Ange TRACE i den öppna dialogrutan i åtgärdsrutan.

* Ta bort banderollen:

   **I Apache** kan du redigera /etc/apache2/conf.d/säkerhet:

   * ServerSignature **Av**
   * ServerTokens **Prod**

   **Utför följande konfiguration på IIS**:

   * Installera **URLScan**.
   * Redigera filen **Urlscan.ini** så att den har **RemoveServerHeader=1**


* Begränsa frågestorleken för att förhindra att viktiga filer överförs:

   **I Apache** lägger du till direktivet  **** LimitRequestBodyi (storlek i byte) i katalogen /.

   ```
   <Directory />
       Options FollowSymLinks
       AllowOverride None
       LimitRequestBody 10485760
   </Directory>
   ```

   **I IIS**  (se  [dokumentationen](http://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)) anger du  **maxAllowedContentLength**  (maximal tillåten innehållslängd) i alternativen för innehållsfiltrering.

Relaterade ämnen:

* [Adobe Marketing Cloud Compliance overview](https://marketing.adobe.com/resources/help/en_US/xref/Adobe-Marketing-Cloud-Privacy-and-Security-Overview.pdf) (PDF)
* [Adobe Campaign Security overview](https://wwwimages.adobe.com/content/dam/acom/en/marketing-cloud/campaign/pdfs/54658.en.campaign.wp.adb-security.pdf) (PDF)
