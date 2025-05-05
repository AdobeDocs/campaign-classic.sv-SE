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

  **I Apache** kan du redigera /etc/apache2/mods-available/ssl.conf. Här är ett exempel:

   * `SSLProtocol all -SSLv2 -SSLv3 -TLSv1`
   * `SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5:!SSLv3:!SSLv2:!TLSv1`

  **Utför följande konfiguration på IIS** (se [dokumentationen](https://support.microsoft.com/en-us/kb/245030)):

   * Lägg till registerundernyckel i HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL
   * Om du vill att systemet ska kunna använda de protokoll som inte ska förhandlas som standard (till exempel TLS 1.2), ändrar du DWORD-värdedata för värdet DisabledByDefault till 0x0 i följande registernycklar under nyckeln **Protokoll**:

     SCHANNEL\Protokoll\TLS 1.2\Client

     SCHANNEL\Protokoll\TLS 1.2\Server

  **Inaktivera SSL x.0**

  SCHANNEL\Protokoll\SSL 3.0\Client: DisabledByDefault: DWORD (32-bitars) Value to 1

  SCHANNEL\Protokoll\SSL 3.0\Server: Aktiverad: DWORD (32-bitars) värde till 0

* Ta bort metoden **TRACE**:

  **I Apache** kan du redigera i /etc/apache2/conf.d/security: TraceEnable **Off**

  **Utför följande konfiguration på IIS** (se [dokumentationen](https://www.iis.net/configreference/system.webserver/security/requestfiltering/verbs)):

   * Kontrollera att rolltjänsten eller funktionen **Begär filtrering** är installerad.
   * Klicka på fliken HTTP-verb i rutan **Begär filtrering** och klicka sedan på Neka verb. Ange TRACE i den öppna dialogrutan i åtgärdsrutan.

* Ta bort banderollen:

  **I Apache** kan du redigera /etc/apache2/conf.d/säkerhet:

   * ServerSignature **Off**
   * ServerTokens **Prod**

  **Utför följande konfiguration på IIS**:

   * Installera **URLScan**.
   * Redigera filen **Urlscan.ini** så att den har **RemoveServerHeader=1**

* Begränsa frågestorleken för att förhindra att viktiga filer överförs:

  **I Apache** lägger du till direktivet **LimitRequestBody** (storlek i byte) i katalogen /.

  ```
  <Directory />
      Options FollowSymLinks
      AllowOverride None
      LimitRequestBody 10485760
  </Directory>
  ```

  **På IIS** (se [dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)) anger du **maxAllowedContentLength** (maximal tillåten innehållslängd) i alternativen för innehållsfiltrering.

Relaterade ämnen:

* [Adobe Marketing Cloud Compliance - översikt](https://experienceleague.adobe.com/sv/docs/experience-platform/landing/governance-privacy-security/overview#privacy)
* [Adobe Campaign - säkerhetsöversikt](https://experienceleague.adobe.com/sv/docs/experience-platform/landing/governance-privacy-security/overview#security)
