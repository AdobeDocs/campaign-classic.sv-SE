---
product: campaign
title: Checklista för säkerhet och sekretess
description: Läs mer om de viktigaste elementen för att kontrollera säkerhet och integritet
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 7%

---

# Checklista för säkerhet och sekretess{#get-started-security-privacy}



I det här avsnittet beskrivs de viktigaste elementen för att kontrollera säkerhet och integritet. Vissa konfigurationer kan bara utföras av lokala kunder.

## Sekretess

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

Konfiguration och skärpning av sekretess är en viktig del av säkerhetsoptimeringen. Här följer några tips om sekretess:

* Protect er kund-PII genom att använda HTTPS istället för HTTP
* Använd PII-visningsbegränsningar för att skydda din integritet och förhindra att data används på ett felaktigt sätt.
* Kontrollera att krypterade lösenord är begränsade.
* Protect de sidor som kan innehålla personlig information, t.ex. spegelsidor, webbtillämpningar osv.

[Läs mer](../../installation/using/privacy.md)

## Åtkomsthantering

<img src="assets/do-not-localize/icon_access.svg" width="60px">

Åtkomshantering är en viktig del av säkerhetsbehärskningen. Här är några av de bästa sätten:

* Skapa tillräckligt många säkerhetsgrupper
* Kontrollera att alla operatorer har rätt åtkomsträttigheter
* Undvik att använda admin-operatorn och undvik att ha för många operatorer i admin-gruppen

[Läs mer](../../installation/using/access-management.md)

## Riktlinjer för skript och kodning

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

När du utvecklar i Adobe Campaign (arbetsflöden, Javascript, JSSP osv.) ska du alltid följa dessa riktlinjer:

* **Skript**: Undvik SQL-satser, använd parametriserade funktioner i stället för strängsammanfogning, undvik SQL-injektion genom att lägga till de SQL-funktioner som ska användas i tillåtelselista.

* **Skydda datamodellen**: använd namngivna rättigheter för att begränsa operatoråtgärder, lägg till systemfilter (sysFilter)

* **Lägg till hämtningar i webbprogram**: lär dig hur du lägger till hämtningar på dina offentliga landningssidor och prenumerationssidor.

[Läs mer](../../installation/using/scripting-coding-guidelines.md)

## Nätverk, databaser och SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

En mycket viktig sak att kontrollera när du distribuerar en lokal typ av arkitektur är nätverkskonfigurationen.

Det är också viktigt att du följer datasäkerheten för databasmotorn.

[Läs mer](../../installation/using/network-database.md)


## Serverkonfiguration

<img src="assets/do-not-localize/icon_server.svg" width="60px">

Konfigurationen måste utföras på alla servrar. Konfigurationsfilerna är av typen **serverConf.xml** och **`config-<instance>.xml`**. Här är de viktigaste elementen som behöver verifieras:

* **Säkerhetszoner**: Konfigurera säkerhetszoner så att de direkt tar hänsyn till IP-adresserna för klienterna för en proxy.

* **Filöverföringsskydd**: Begränsa de typer av filer som kan överföras till Adobe Campaign-servern med ett nytt uploadAllowList-attribut. Detta kan användas i serverkonfigurationsfilen.

* **Relay**: finjustera reläkonfigurationen genom att inaktivera reläreglerna för oanvända moduler/program.

* **Utgående anslutningsskydd** och **Kommandobegränsning** (på serversidan)

* Du kan också lägga till extra HTTP-huvuden, aktivera checkIPConsistent, enableTLS, sessionTimeOutSec osv. Mer information finns i [konfigurationsdokumentationen för Campaign-servern](../../installation/using/configuring-campaign-server.md) och [beskrivningen av serverkonfigurationsfilen](../../installation/using/the-server-configuration-file.md).

[Läs mer](../../installation/using/server-configuration.md)

## Konfiguration av webbserver

<img src="assets/do-not-localize/icon_web.svg" width="60px">

Flera metodtips bör följas när du konfigurerar webbservern (Apache/IIS):

* Inaktivera gammal SSL-version och ciphers
* Ta bort metoden TRACE
* Ta bort bannern
* Begränsa frågestorleken för att förhindra att viktiga filer överförs

[Läs mer](../../installation/using/web-server-configuration.md)
