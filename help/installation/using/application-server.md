---
product: campaign
title: Programserver
description: Programserver
feature: Installation
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 87103c31-1530-4f8d-ab3a-6ff73093b80c
source-git-commit: 7e1c3b256cf43232e49d9daa0bf44d1e114b565b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 1%

---

# Programserver{#application-server}

De nödvändiga lagren för databasåtkomst måste vara installerade på servern och tillgängliga från Adobe Campaign-kontot.

## Java Development Kit - JDK {#java-development-kit---jdk}

Java Development Kit, eller JDK, är ett programutvecklingspaket. Det är den grundläggande komponenten som möjliggör utveckling av Java-program och Java-applet.

Den dynamiska generatorn för webbsidor använder JSP 1.2-teknik. För detta ingår en Tomcat-motor (från Apache) i programmet. Det kräver ett Java Development Kit (JDK) som är installerat på alla servrar där Adobe Campaign-programmet är installerat.

Du måste först installera en JDK på de datorer där du vill köra Adobe Campaign-programservern (**nlserver web** eftersom den innehåller en serverbehållare, Apache Tomcat, som används för att generera dynamiska webbsidor (rapporter, webbformulär osv.).

Ansökan har godkänts för Java Development Kit (JDK) som utvecklats av Oraclet samt för **OpenJDK**.

Versionerna som stöds finns i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).


### Rekommendationer

När du installerar och uppgraderar ditt Java Development Kit bör du följa följande rekommendationer:

* Java Development Kit kan installeras med rätt JDK-version som redan används av andra program på datorn.

* När du installerar JDK krävs ingen integration med webbläsarna.

* På en dator som bara kör leveransagenter (**nlserver mta** process) eller arbetsflödesservern (**nlserver wfserver** ) krävs inte installation av JDK.

* För att bevara prestanda för plattformsåtgärder och säkerställa kompatibilitet med den installerade versionen måste du inaktivera automatiska JDK-uppdateringsfunktioner i Windows och Linux.

* När du uppgraderar din Java-version måste du först avinstallera den tidigare versionen. Båda versionerna av Java som är installerade på samma dator kan orsaka konflikter.

  Som lokal kund kan du kontrollera `LD_LIBRARY_PATH` [miljövariabel](installing-packages-with-linux.md#environment-variables) är inställd på den senaste versionen (t.ex. java1). Om den är inställd på en tidigare version (t.ex. Java8) behöver uppdateras. För JDK 11 är sökvägen till JDK-bibliotek `/usr/lib/jvm/java-11-openjdk-amd64/lib`.


### Installationssteg

Java Development Kit är plattformsspecifikt: separata installationsprogram krävs för varje operativsystem.

Om du vill hämta JDK ansluter du till [Oraclets webbplats](https://www.oracle.com/technetwork/java/javase/downloads/index.html){target="_blank"}.

>[!CAUTION]
>
> Se till att hämta ett Java Development Kit (JDK), inte en Java Runtime Environment (JRE).


Om du vill installera JDSL i en Linux-miljö rekommenderar Adobe att du använder en pakethanterare.

Använd följande kommando för Debian:

```sql
aptitude install openjdk-8-jdk
```

Använd följande kommando för RHEL:

```sql
yum install java-1.8.0-openjdk
```


## OpenSSL {#openssl}

I Linux måste OpenSSL vara installerat. Adobe Campaign stöder OpenSSL version 1.0.2 eller senare.

## Exportera rapporter {#exporting-reports}

Du kan använda Adobe Campaign för att exportera rapporter till Microsoft Excel och Adobe PDF.

* För Microsoft Excel-formatet använder Adobe Campaign **LibreOffice**.

* För Adobe PDF-formatet använder Adobe Campaign **PhantomJS** konverterare. PhantomJs ingår i fabrikspaketet och LibreOffice måste vara installerat på de datorer som Adobe Campaign-programservern körs på (**nlserver web** -processen).

>[!NOTE]
>
>För Linux måste du lägga till teckensnitt. Mer information finns i [Teckensnitt för MTA-statistik](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Med SpamAssassin kan du tilldela ett poängvärde till e-postmeddelanden för att avgöra om ett meddelande riskerar att betraktas som oönskat av antispam-verktyg som används vid mottagning. Installationen är valfri.

SpamAssasins klassificering av e-post som oönskad baseras helt på filtrerings- och poängregler. Dessa regler måste därför uppdateras minst en gång om dagen för att din SpamAssassin-installation och dess integrering i Adobe Campaign ska fungera fullt ut och för att säkerställa att poängen som tilldelats dina leveranser är relevanta innan de skickas. Den här uppdateringen görs av serveradministratören som är värd för SpamAssassin.

Den lägsta version som stöds är: **3.4**

SpamAssassin kräver HTTP-internetåtkomst (tcp/80).

Installations- och konfigurationsfaserna för SpamAssassin presenteras i [Konfigurera SpamAssassin](../../installation/using/configuring-spamassassin.md).
