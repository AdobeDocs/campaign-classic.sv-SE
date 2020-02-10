---
title: Programserver
seo-title: Programserver
description: Programserver
seo-description: null
page-status-flag: never-activated
uuid: 837c6a5c-53a4-4d1b-a084-9cf77e7a0eee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 7a9e028c-255d-4aad-9827-d19f9a7897b2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# Programserver{#application-server}

De nödvändiga lagren för databasåtkomst måste vara installerade på servern och tillgängliga från Adobe Campaign-kontot.

## Java Development Kit - JDK {#java-development-kit---jdk}

Den dynamiska generatorn för webbsidor använder JSP 1.2-teknik. För detta ingår en Tomcat-motor (från Apache) i programmet. Det kräver ett Java Development Kit (JDK) som är installerat på alla servrar där Adobe Campaign-programmet är installerat.

Du måste först installera en JDK på de datorer där du vill köra Adobe Campaign-programservern (**webbprocessen** på lserver) eftersom den innehåller en serverbehållare, Apache Tomcat, som används för att generera dynamiska webbsidor (rapporter, webbformulär osv.).

Ansökan har godkänts för Java Development Kit (JDK) som utvecklats av Oracle samt för **OpenJDK**.

De versioner som stöds finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

>[!NOTE]
>
>Den kan installeras med rätt JDK-version som redan används av andra program på datorn.
>  
>När du installerar behöver du inte utföra integreringen med webbläsarna.
>
>På en dator som bara kör leveransagenter (**nlserver mta** -processen) eller arbetsflödesservern (**nlserver wfserver** -processen) behöver du inte installera en JDK.

Om du vill hämta Java JDK ansluter du till: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Varning: du måste hämta en JDK, inte en JRE.**

>[!CAUTION]
>
>För att bevara prestanda för plattformsåtgärder och säkerställa kompatibilitet med den installerade versionen måste du inaktivera automatiska JDK-uppdateringsfunktioner i Windows och Linux.

Om du vill installera JDSL i en Linux-miljö bör du använda en pakethanterare.

I Debian 7 och 8 använder du följande kommando:

```
aptitude install openjdk-7-jdk
```

Använd följande kommando för RHEL 6:

```
yum install java-1.8.0-openjdk
```

Använd följande kommando för RHEL 7:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

I Linux måste OpenSSL vara installerat. De versioner som stöds av Adobe Campaign är **OpenSSL 1.0.1** och **OpenSSL 0.9.8**. Underversionerna 0.9.8g till 0.9.8o godkänns.

>[!NOTE]
>
>För RHEL 6 och CentOS 6 krävs openSSL 1.0.

## Exportera rapporter {#exporting-reports}

Med Adobe Campaign kan du exportera plattformsrapporter i Microsoft Excel- och Adobe PDF-format. Adobe Campaign använder **LibraryOffice** för Microsoft Excel-formatet. Adobe Campaign använder **PhantomJS** -konverteraren för Adobe PDF-formatet. PhantomJs ingår i fabrikspaketet och LibraryOffice måste vara installerat på de datorer som Adobe Campaign-programservern körs på (**webbprocessen** på lserver).

>[!NOTE]
>
>För Linux måste du lägga till teckensnitt. Mer information finns i [Teckensnitt för MTA-statistik](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Med SpamAssassin kan du tilldela ett poängvärde till e-postmeddelanden för att avgöra om ett meddelande riskerar att betraktas som oönskat av antispam-verktyg som används vid mottagning. Installationen är valfri.

SpamAssasins klassificering av e-post som oönskad baseras helt på filtrerings- och poängregler. Dessa regler måste därför uppdateras minst en gång om dagen för att din SpamAssassin-installation och dess integrering i Adobe Campaign ska fungera fullt ut och för att säkerställa relevansen av poängen som tilldelats dina leveranser innan de skickas. Den här uppdateringen görs av serveradministratören som är värd för SpamAssassin.

De lägsta versionerna som stöds är: **3.2.5** och **3.3.2**.

SpamAssassin kräver HTTP-internetåtkomst (tcp/80).

Installations- och konfigurationsfaserna för SpamAssassin presenteras i [Konfigurera SpamAssassin](../../installation/using/configuring-spamassassin.md).
