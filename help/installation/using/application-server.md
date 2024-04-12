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
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 1%

---

# Programserver{#application-server}



De nödvändiga lagren för databasåtkomst måste vara installerade på servern och tillgängliga från Adobe Campaign-kontot.

## Java Development Kit - JDK {#java-development-kit---jdk}

Den dynamiska generatorn för webbsidor använder JSP 1.2-teknik. För detta ingår en Tomcat-motor (från Apache) i programmet. Det kräver ett Java Development Kit (JDK) som är installerat på alla servrar där Adobe Campaign-programmet är installerat.

Du måste först installera en JDK på de datorer där du vill köra Adobe Campaign-programservern (**nlserver web** eftersom den innehåller en serverbehållare, Apache Tomcat, som används för att generera dynamiska webbsidor (rapporter, webbformulär osv.).

Ansökan har godkänts för Java Development Kit (JDK) som utvecklats av Oraclet samt för **OpenJDK**.

Versionerna som stöds finns i Campaign [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

>[!NOTE]
>
>Den kan installeras med rätt JDK-version som redan används av andra program på datorn.
>  
>När du installerar behöver du inte utföra integreringen med webbläsarna.
>
>På en dator som bara kör leveransagenter (**nlserver mta** process) eller arbetsflödesservern (**nlserver wfserver** ) behöver du inte installera JDK.

Om du vill hämta Java JDK ansluter du till: [https://www.oracle.com/technetwork/java/javase/downloads/index.html](https://www.oracle.com/technetwork/java/javase/downloads/index.html).

**Varning: du måste hämta en JDK, inte en JRE.**

>[!CAUTION]
>
>För att bevara prestanda för plattformsåtgärder och säkerställa kompatibilitet med den installerade versionen måste du inaktivera automatiska JDK-uppdateringsfunktioner i Windows och Linux.

Om du vill installera JDSL i en Linux-miljö bör du använda en pakethanterare.

I Debian 8 och 9 använder du följande kommando:

```
aptitude install openjdk-8-jdk
```

Använd följande kommando för RHEL 7:

```
yum install java-1.8.0-openjdk
```

## OpenSSL {#openssl}

I Linux måste OpenSSL vara installerat. Adobe Campaign stöder OpenSSL version 1.0.2 eller senare.

## Exportera rapporter {#exporting-reports}

Med Adobe Campaign kan du exportera plattformsrapporter i Microsoft Excel- och Adobe PDF-format. För Microsoft Excel-formatet använder Adobe Campaign **LibreOffice**. För Adobe PDF-formatet använder Adobe Campaign **PhantomJS** konverterare. PhantomJs ingår i fabrikspaketet och LibreOffice måste vara installerat på de datorer som Adobe Campaign-programservern körs på (**nlserver web** -processen).

>[!NOTE]
>
>För Linux måste du lägga till teckensnitt. Mer information finns i [Teckensnitt för MTA-statistik](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#fonts-for-mta-statistics).

## SpamAssassin {#spamassassin}

Med SpamAssassin kan du tilldela ett poängvärde till e-postmeddelanden för att avgöra om ett meddelande riskerar att betraktas som oönskat av antispam-verktyg som används vid mottagning. Installationen är valfri.

SpamAssasins klassificering av e-post som oönskad baseras helt på filtrerings- och poängregler. Dessa regler måste därför uppdateras minst en gång om dagen för att din SpamAssassin-installation och dess integrering i Adobe Campaign ska fungera fullt ut och för att säkerställa att poängen som tilldelats dina leveranser är relevanta innan de skickas. Den här uppdateringen görs av serveradministratören som är värd för SpamAssassin.

Den lägsta version som stöds är: **3.4**

SpamAssassin kräver HTTP-internetåtkomst (tcp/80).

Installations- och konfigurationsfaserna för SpamAssassin presenteras i [Konfigurera SpamAssassin](../../installation/using/configuring-spamassassin.md).
