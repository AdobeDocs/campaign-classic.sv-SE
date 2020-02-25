---
title: Standarddistribution
seo-title: Standarddistribution
description: Standarddistribution
seo-description: null
page-status-flag: never-activated
uuid: e2f9c4d9-4b36-4899-9954-493135597057
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: d714b759-cc08-4656-876c-9820d5c56216
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# Standarddistribution{#standard-deployment}

För den här konfigurationen krävs tre datorer:

* En programserver i LAN för slutanvändarna (förbereder kampanjer, rapporter osv.),
* Två frontservrar i DMZ bakom en belastningsutjämnare.

De två servrarna i DMZ hanterar spårning, spegelsidor och leverans och är redundanta för hög tillgänglighet.

Programservern i LAN betjänar slutanvändarna och utför alla återkommande processer (arbetsflödesmotor). När toppbelastningen uppnås på frontservrarna påverkas alltså inte programanvändarna.

Databasservern kan finnas på en annan dator än dessa. I annat fall måste programservern och databasservern dela samma dator inom LAN så länge som operativsystemet stöds av Adobe Campaign (Linux eller Windows).

Allmän kommunikation mellan servrar och processer sker enligt följande schema:

![](assets/s_001_ncs_install_standardconfig.png)

Den här typen av konfiguration kan hantera ett stort antal mottagare (500 000 till 1 000 000) eftersom databasservern (och den tillgängliga bandbredden) är den viktigaste begränsningsfaktorn.

## Funktioner {#features}

### Fördelar {#advantages}

* Redundansfunktion: Möjlighet att växla mellan processer och datorer om det uppstår maskinvaruproblem.
* Bättre övergripande prestanda eftersom funktionerna för MTA och omdirigering kan användas på båda datorerna bakom en belastningsutjämnare. Med två aktiva MTA:er och tillräckligt med bandbredd är det möjligt att få en sändningsfrekvens på cirka 100 000 e-postmeddelanden per timme.

## Installations- och konfigurationssteg {#installation-and-configuration-steps}

### Förutsättningar {#prerequisites}

* JDK på alla tre datorerna,
* Webbserver (IIS, Apache) på båda frontalerna,
* Åtkomst till en databasserver på alla tre datorerna,
* Studsa postlåda tillgänglig via POP3,
* Skapa två DNS-alias:

   * Den första som exponeras för allmänheten för spårning och som pekar mot belastningsutjämnaren på en virtuell IP-adress (VIP) och som sedan distribueras till de två frontservrarna.
   * den andra som visas för interna användare för åtkomst via konsolen och som pekar på samma programserver.

* Brandväggen har konfigurerats för att öppna STMP (25), DNS (53), HTTP (80), HTTPS (443), SQL (1521 för Oracle, 5432 för PostgreSQL osv.) portar. Mer information finns i avsnittet [Databasåtkomst](../../installation/using/network-configuration.md#database-access).

### Installera programservern {#installing-the-application-server}

Följ stegen för att installera en fristående instans från Adobe Campaign-programservern när du skapar databasen (steg 12). Se [Installera och konfigurera (en dator)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Eftersom datorn inte är en spårningsserver ska du inte ta hänsyn till integreringen med webbservern.

I följande exempel är parametrarna för instansen:

* Instansens namn: **demo**
* DNS-mask: **console.campaign.net*** (endast för klientkonsolanslutningar och för rapporter)
* Språk: Engelska
* Databas: **kampanj:demo@dbsrv**

### Installera de två frontservrarna {#installing-the-two-frontal-servers}

Installations- och konfigurationsproceduren är identisk på båda datorerna.

Stegen är följande:

1. Installera Adobe Campaign-servern.

   Mer information finns i [Krav för Campaign-installation i Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux) och [Krav för Campaign-installation i Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows).

1. Följ integreringsproceduren för webbservrar (IIS, Apache) som beskrivs i följande avsnitt:

   * För Linux: Integrering [med en webbserver för Linux](../../installation/using/integration-into-a-web-server-for-linux.md)
   * För Windows: Integrering [med en webbserver för Windows](../../installation/using/integration-into-a-web-server-for-windows.md)

1. Skapa **demoinstansen** . Det finns två sätt att göra detta:

   * Skapa instansen via konsolen:

      ![](assets/install_create_new_connexion.png)

      Mer information finns i [Skapa en instans och logga in](../../installation/using/creating-an-instance-and-logging-on.md).

      eller

   * Skapa instansen med kommandorader:

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      Mer information finns i [Skapa en instans](../../installation/using/command-lines.md#creating-an-instance).
   Namnet på instansen är detsamma som på programservern.

   Anslutningen till servern med **webbmodulen** på servern (spegelsidor, avprenumeration) görs från URL:en för belastningsutjämnaren (tracking.campaign.net).

1. Ändra den **interna** till samma som programservern.

   Mer information finns i [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. Länka databasen till instansen:

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. Aktivera modulerna **web** , **trackinglog** och **mta** i filerna config-default.xml **och** config-demo.xml **** .

   Mer information finns i [Aktivera processer](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. Redigera filen **serverConf.xml** och fyll i den:

   * DNS-konfigurationen för MTA-modulen:

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >Parametern **nameServers** används bara i Windows.

      Mer information finns i [Leveransinställningar](../../installation/using/campaign-server-configuration.md#delivery-settings).

   * redundanta spårningsservrar i omdirigeringsparametrarna:

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      Mer information finns i [Spårning](../../installation/using/configuring-campaign-server.md#redundant-tracking)av överflödiga objekt.

1. Starta webbplatsen och testa omdirigeringen från URL:en: [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test).

   Webbläsaren bör visa följande meddelanden (beroende på vilken URL som omdirigeras av belastningsutjämnaren):

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   eller

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   Mer information finns i följande avsnitt:

   * För Linux: Starta [webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * För Windows: Starta [webbservern och testa konfigurationen](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. Starta Adobe Campaign-servern.
1. I Adobe Campaign-konsolen ansluter du med **administratörsinloggningen** utan lösenord och startar distributionsguiden.

   Mer information finns i [Distribuera en instans](../../installation/using/deploying-an-instance.md).

   Konfigurationen är identisk med en fristående instans förutom konfigurationen för spårningsmodulen.

1. Fyll i den externa URL-adressen (den för belastningsutjämnaren) som används för omdirigering och de interna URL-adresserna för de två frontservrarna.

   Mer information finns i [Spårningskonfiguration](../../installation/using/deploying-an-instance.md#tracking-configuration).

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >Vi använder den befintliga instansen av de två spårningsservrarna som har skapats tidigare och använder den **interna** inloggningen.

