---
product: campaign
title: Konfiguration av webbserver
description: Lär dig mer om de effektivaste strategierna för webbserverkonfiguration
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: fc0d3f16-5f62-473d-a1de-aab574eff734
source-git-commit: dba90a154e08400ae6ab6478623a50d48d72207c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Konfiguration av webbserver {#web-server-configuration}



Nedan hittar du några av de effektivaste strategierna för webbserverkonfiguration (Apache/IIS).

* Ändra standardfelsidor.

* Inaktivera tidigare SSL-version och ciphers:

  **På Apache**, redigera /etc/apache2/mods-available/ssl.conf. Här är ett exempel:

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **På IIS** (se [dokumentation](https://support.microsoft.com/en-us/kb/245030)) utför du följande konfiguration:

   * Lägg till registerundernyckel i HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Om du vill att systemet ska kunna använda de protokoll som inte ska förhandlas som standard (till exempel TLS 1.2) ändrar du DWORD-värdedata för värdet DisabledByDefault till 0x0 i följande registernycklar under **Protokoll** nyckel:

     SCHANNEL\Protokoll\TLS 1.2\Client

     SCHANNEL\Protokoll\TLS 1.2\Server

  **Inaktivera SSL x.0**

  SCHANNEL\Protokoll\SSL 3.0\Client: DisabledByDefault: DWORD (32-bitars) Value to 1

  SCHANNEL\Protokoll\SSL 3.0\Server: Aktiverad: DWORD (32-bitars) värde till 0

* Ta bort **TRACE** metod:

  **På Apache**, redigera i /etc/apache2/conf.d/security: TraceEnable **Av**

  **På IIS** (se [dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)) utför du följande konfiguration:

   * Se till att **Begärandefiltrering** rolltjänsten eller funktionen är installerad.
   * I **Begärandefiltrering** klickar du på fliken för HTTP-verb och sedan på Neka verb. Ange TRACE i den öppna dialogrutan i åtgärdsrutan.

* Ta bort banderollen:

  **På Apache**, redigera /etc/apache2/conf.d/säkerhet:

   * ServerSignature **Av**
   * ServerTokens **Prod**

  **På IIS** utför du följande konfiguration:

   * Installera **URLScan**.
   * Redigera **Urlscan.ini** fil att ha **RemoveServerHeader=1**

* Begränsa frågestorleken för att förhindra att viktiga filer överförs:

  **På Apache**, lägg till **LimitRequestBody** -direktiv (storlek i byte) i /-katalog.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **På IIS** (se [dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)), ange **maxAllowedContentLength** (maximal tillåten innehållslängd) i alternativen för innehållsfiltrering.

Relaterade ämnen:

* [Adobe Marketing Cloud Compliance overview](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign Security - översikt](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/overview#security)
