---
product: campaign
title: Konfigurera SpamAssassin
description: Konfigurera SpamAssassin
feature: Installation, Instance Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# Konfigurera SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>Vissa konfigurationer kan bara utföras av Adobe för distributioner som hanteras av Adobe. Om du till exempel vill komma åt server- och instanskonfigurationsfilerna. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i [den här sidan](../../installation/using/capability-matrix.md).

## Översikt {#overview}

SpamAssassin är en programvara som är utformad för att filtrera bort oönskade e-postmeddelanden. I kombination med den här programvaran kan Adobe Campaign ge e-postmeddelanden poäng och avgöra om ett meddelande troligtvis kommer att anses vara oönskat innan leveransen startas. För att kunna göra detta måste SpamAssassin installeras och konfigureras på programservrar i Adobe Campaign och ett visst antal ytterligare Perl-moduler måste användas.

Distributionen och integreringen av SpamAssassin enligt beskrivningen i detta kapitel baseras på standardprogramvaruinstallation, liksom filtrerings- och poängregler, som tillhandahålls av SpamAssassin utan ändringar eller optimeringar. Poängattribuering och meddelandekvalificering baseras enbart på konfigurationen av SpamAssets-alternativen och på filtreringsregler. Nätverksadministratörer ansvarar för att anpassa dem till företagets behov.

>[!IMPORTANT]
>
>SpamAssasins klassificering av e-post som oönskad baseras helt på filtrerings- och poängregler.
>
>Dessa regler måste därför uppdateras minst en gång om dagen för att din SpamAssassin-installation och dess integrering i Adobe Campaign ska fungera fullt ut och för att säkerställa att poängen som tilldelats dina leveranser är relevanta innan de skickas.
>
>Den här uppdateringen görs av serveradministratören som är värd för SpamAssassin.

Om du använder SpamAssassin i Adobe Campaign får du en indikation på det möjliga beteendet hos e-postservrar som använder SpamAssassin när de tar emot e-post som skickas av Adobe Campaign. Det är dock möjligt att e-postservrarna hos internetleverantörer eller e-postservrar fortfarande anser att de meddelanden som skickas av Adobe Campaign inte är önskade.

För att kunna distribuera SpamAssassin och dess moduler i Perl krävs Adobe Campaign-programservrar med Internetåtkomst via en HTTP-anslutning (TCP/80-flöde).

## Installera på en Windows-dator {#installing-on-a-windows-machine}

Så här installerar och konfigurerar du SpamAssets på Windows för att aktivera integrering med Adobe Campaign:

1. Installera SpamAssassin
1. Integrera SpamAssassin i Adobe Campaign

### Installera SpamAssassin {#installing-spamassassin}

1. Anslut till [programdistributionsportalen](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) med dina användaruppgifter. Läs mer om programvarudistribution på [den här sidan](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=sv-SE).
1. Hämta filen **Neolane Spam Assassin (Windows-installation) (2.0)** (neolane_spamassassin.2.0.zip).
1. Kopiera den här filen till Adobe Campaign-servern och packa upp den.

   >[!NOTE]
   >
   >Du kan välja att packa upp filen var du vill, förutsatt att sökvägen består av något av följande reguljära uttryckstecken: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Installationssökvägen får inte innehålla blanksteg.

1. Gå till filen där du packade upp filen och dubbelklicka sedan på filen **run_me.bat** för att starta installationsskriptet.

   Om ett Windows Shell visas och fortsätter att visas i några sekunder väntar du tills installationen och uppdateringen har slutförts och klickar sedan på **Enter**.

   Om Windows Shell inte visas eller inte visas innan du omedelbart försvinner, dubbelklickar du på filen **portableShell.bat** för att visa ett Windows Shell och kontrollerar att Shell-sökvägen motsvarar mappen där filen **spamassassin.zip** har packats upp. Om så inte är fallet kan du komma åt det med kommandot **cd**.

   Ange **run_me.bat** och klicka sedan på **Enter** för att starta installations- och uppdateringsprocessen. Åtgärden returnerar ett av följande värden för att ange resultatet av uppdateringen.

   * **0**: en uppdatering har utförts.
   * **1**: Det finns ingen ny uppdatering.
   * **2**: Det finns ingen ny uppdatering.
   * **3**: Uppdateringen misslyckades under tidigare verifiering.
   * **4** eller fler: ett fel har inträffat.

1. Om du vill kontrollera att installationen av SpamAssassin lyckades använder du GTUBE-testet (Generic Test for Unsolicited Bulk Email) enligt följande:

   1. Skapa en textfil och spara den under **C:\TestSpamMail.txt**.
   1. Infoga följande innehåll i filen:

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Dubbelklicka på filen **portableShell.bat** för att visa ett Windows Shell och starta sedan följande kommando (eller `<root>` anger den skapade mappen när **spamassassin.zip** -filen packas upp):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Innehållet i det här testmeddelandet utlöser ett 1 000 poäng av SpamAssassin. Det innebär att den har identifierats som oönskad och att installationen lyckades och fungerar fullt ut.

### Integrera SpamAssassin i Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Redigera filen **`[INSTALL]/conf/serverConf.xml`**. Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).
1. Ändra värdet för attributet **spamCheck** elements&#39; **command** i noden **Web**. Kör följande kommando för att göra detta:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alla sökvägar måste vara absoluta.

   Stoppa och starta tjänsten **[!UICONTROL Adobe Campaign]**.

1. Om du vill kontrollera integreringen av SpamAssassin i Adobe Campaign använder du ett GTBUE-test (Generic Test for Unsolicited Bulk Email):

   Dubbelklicka på filen **portableshell.bat**. Detta utlöser visningen av ett Windows-gränssnitt. Kör sedan följande kommando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Innehållet i det här testmeddelandet utlöser 1 000 poäng som tilldelats av SpamAssassin. Det innebär att det har identifierats som oönskat och att integreringen i Adobe Campaign lyckades och fungerar fullt ut.

1. Uppdatera SpamAssassin-filtrerings- och bedömningsregler

   Starta **portableShell.bat** och kör följande kommando för en inledande uppdatering av filtrerings- och bedömningsregler:

   ```
   sa-update --no-gpg
   ```

   Om du vill köra en automatisk uppdatering av filtrerings- och bedömningsregler använder du samma kommando i en schemalagd systemuppgift:

   ```
   sa-update --no-gpg
   ```

## Installera på en Linux-dator {#installing-on-a-linux-machine}

### Installationssteg i Debian {#installation-steps-in-debian}

* Installera Perl och SpamAssassin med följande kommando om det behövs:

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* Ändra raden **spamCheck** på följande sätt i filen **serverConf.xml** (tillgänglig i `/usr/local/[INSTALL]/nl6/conf/`):

  ```
  <spamCheck command="perl
  /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
  ```

### Installationssteg i RHEL/CentOS {#installation-steps-in-rhel-centos}

Installera vid behov Perl och återställ paketen med CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Uppdaterar filterregler {#updating-filter-rules}

Filterregler kan uppdateras automatiskt med verktyget **sa-update** . Mer information finns på den officiella SpamAssassin-webbplatsen [https://spamassassin.apache.org/](https://spamassassin.apache.org/).

I Debian sker uppdateringar automatiskt varje dag.

Om så inte är fallet (till exempel när Debian installeras manuellt) skapar du ett skript som automatiserar regeluppdateringar.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Infoga det här skriptet i **crontab** med följande kommando:

```
crontab-e
```

### Prestandaoptimering {#performance-optimization}

Om du vill förbättra prestanda i Linux redigerar du filen **/etc/spamassassin/local.cf** och lägger till följande rad i slutet av filen:

```
dns_available no
```
