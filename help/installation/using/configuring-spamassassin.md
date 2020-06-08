---
title: Konfigurera SpamAssassin
seo-title: Konfigurera SpamAssassin
description: Konfigurera SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1a9d4c9eadf996d37481f33636eae98e482ac115
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 0%

---


# Konfigurera SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>Vissa konfigurationer kan bara utföras av Adobe för distributioner som hanteras av Adobe. Om du till exempel vill komma åt server- och instanskonfigurationsfilerna. Mer information om de olika distributionerna finns i avsnittet [Värdmodeller](../../installation/using/hosting-models.md) eller i [den här artikeln](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Översikt {#overview}

SpamAssassin är en programvara som är utformad för att filtrera bort oönskade e-postmeddelanden. I kombination med den här programvaran kan Adobe Campaign poängsätta e-postmeddelanden och avgöra om ett meddelande troligtvis kommer att anses oönskat innan leverans startas. För att göra detta måste SpamAssassin installeras och konfigureras på programservrar i Adobe Campaign och ett visst antal ytterligare Perl-moduler krävs för att fungera.

Distributionen och integreringen av SpamAssassin enligt beskrivningen i detta kapitel baseras på standardprogramvaruinstallation, liksom filtrerings- och poängregler, som tillhandahålls av SpamAssassin utan ändringar eller optimeringar. Poängattribuering och meddelandekvalificering baseras enbart på konfigurationen av SpamAssets-alternativen och på filtreringsregler. Nätverksadministratörer ansvarar för att anpassa dem till företagets behov.

>[!IMPORTANT]
>
>SpamAssasins klassificering av e-post som oönskad baseras helt på filtrerings- och poängregler.
>
>Dessa regler måste därför uppdateras minst en gång om dagen för att din SpamAssassin-installation och dess integrering i Adobe Campaign ska fungera fullt ut och för att säkerställa relevansen av poängen som tilldelats dina leveranser innan de skickas.
>
>Den här uppdateringen görs av serveradministratören som är värd för SpamAssassin.

Om du använder SpamAssassin i Adobe Campaign får du en indikation på det möjliga beteendet hos e-postservrar som använder SpamAssassin när de tar emot e-post som skickas av Adobe Campaign. Det är dock möjligt att e-postservrarna hos internetleverantörer eller e-postservrar fortfarande anser att de meddelanden som skickas av Adobe Campaign är oönskade.

För att kunna distribuera SpamAssassin och dess moduler i Perl krävs Adobe Campaign-programservrar med Internetåtkomst via en HTTP-anslutning (TCP/80-flöde).

## Installera på en Windows-dator {#installing-on-a-windows-machine}

Så här installerar och konfigurerar du SpamAssets på Windows för att aktivera integrering med Adobe Campaign:

1. Installera SpamAssassin
1. Integrera SpamAssassin i Adobe Campaign

### Installera SpamAssassin {#installing-spamassassin}

1. Anslut till [extranätportalen](http://support.neolane.net) med dina användaruppgifter.
1. Gå till **Hämtningscenter** och bläddra på sidan för att hitta **verktygsavsnittet** .
1. Ladda ned filen **Neolane Spam Assassin (Windows-installation) (2.0)** (neolane_spamassassin.2.0.zip).
1. Kopiera den här filen till Adobe Campaign-servern och packa upp den.

   >[!NOTE]
   >
   >Du kan välja att packa upp filen var du vill, förutsatt att sökvägen består av något av följande reguljära uttryckstecken: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Installationssökvägen får inte innehålla blankstegstecken.

1. Gå till filen där du packade upp filen och dubbelklicka sedan på filen **run_me.bat** för att starta installationsskriptet.

   Om ett Windows Shell visas och fortsätter att visas i några sekunder väntar du tills installationen och uppdateringen har slutförts och klickar sedan på **Enter**.

   Om Windows Shell inte visas eller inte visas innan du omedelbart försvinner, dubbelklickar du på **portableShell.bat** -filen för att visa ett Windows Shell och kontrollerar att Shell-sökvägen motsvarar den mapp där **spamassassin.zip** -filen har packats upp. Om så inte är fallet kan du komma åt det med **cd** -kommandot.

   Ange **run_me.bat** och klicka sedan på **Enter** för att starta installations- och uppdateringsprocessen. Åtgärden returnerar ett av följande värden för att ange resultatet av uppdateringen.

   * **0**: en uppdatering har utförts.
   * **1**: Det finns ingen ny uppdatering.
   * **2**: ingen ny uppdatering tillgänglig.
   * **3**: uppdatering misslyckades under tidigare verifiering.
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

   1. Dubbelklicka på filen **portableShell.bat** för att visa ett Windows Shell och starta sedan följande kommando (eller &quot;`<root>`&quot; anger den skapade mappen när **filen spamassassin.zip** packas upp):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Innehållet i det här testmeddelandet utlöser ett 1 000 poäng av SpamAssassin. Det innebär att den har identifierats som oönskad och att installationen lyckades och fungerar fullt ut.

### Integrera SpamAssassin i Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Redigera **`[INSTALL]/conf/serverConf.xml`** filen. Alla parametrar som finns i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).
1. Ändra värdet för **spamCheck** -elementets **command** -attribut i **webbnoden** . Kör följande kommando för att göra detta:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Alla sökvägar måste vara absoluta.

   Stoppa och starta **[!UICONTROL Adobe Campaign]** tjänsten.

1. För att kontrollera integreringen av SpamAssassin i Adobe Campaign använder du ett GTBUE-test (Generic Test for Unsolicited Bulk Email):

   Dubbelklicka på **filen portableshell.bat** . Detta aktiverar visningen av ett Windows-gränssnitt. Kör sedan följande kommando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Innehållet i det här testmeddelandet utlöser 1 000 poäng som tilldelats av SpamAssassin. Det innebär att det har identifierats som oönskat och att integrationen i Adobe Campaign lyckades och fungerar fullt ut.

1. Uppdatera SpamAssassin-filtrerings- och bedömningsregler

   Starta **portableShell.bat** och kör följande kommando för en inledande uppdatering av filtrerings- och poängsättningsreglerna:

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

* I **filen serverConf.xml** (finns i `/usr/local/[INSTALL]/nl6/conf/`) ändrar du **spamCheck** -raden enligt följande:

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

Filterregler kan uppdateras automatiskt med **uppdateringsverktyget** . Mer information finns på den officiella SpamAssassin-webbplatsen [http://spamassassin.apache.org/](http://spamassassin.apache.org/) .

I Debian sker uppdateringar automatiskt varje dag.

Om så inte är fallet (till exempel när Debian installeras manuellt) skapar du ett skript som automatiserar regeluppdateringar.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Infoga skriptet på **crontab** med följande kommando:

```
crontab-e
```

### Prestandaoptimering {#performance-optimization}

Om du vill förbättra prestanda i Linux redigerar du filen **/etc/spamassassin/local.cf** och lägger till följande rad i slutet av filen:

```
dns_available no
```

