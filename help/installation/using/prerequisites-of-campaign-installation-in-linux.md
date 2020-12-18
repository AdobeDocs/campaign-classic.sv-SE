---
solution: Campaign Classic
product: campaign
title: Krav för installationen av Campaign i Linux
description: Krav för installationen av Campaign i Linux
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 2%

---


# Krav för installationen av Campaign i Linux{#prerequisites-of-campaign-installation-in-linux}

## Programvarukrav {#software-prerequisites}

I det här avsnittet beskrivs de preliminära konfigurationssteg som krävs innan du installerar Adobe Campaign.

Den tekniska konfiguration och programkonfiguration som krävs för att installera Adobe Campaign finns i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Följande komponenter måste installeras och konfigureras korrekt:

* Apache, se [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md),
* Java JDK och OpenJDK, se [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotek, se [Bibliotek](#libraries),
* Lager för databasåtkomst, se [Lager för databasåtkomst](#database-access-layers),
* LibraryOffice, se [Installera LibraryOffice för Debian](#installing-libreoffice-for-debian) och [Installera LibraryOffice för CentOS](#installing-libreoffice-for-centos).
* Teckensnitt finns i [Teckensnitt för MTA-statistik](#fonts-for-mta-statistics) och [Teckensnitt för japanska förekomster](#fonts-for-japanese-instances).

>[!NOTE]
>
>Om du vill installera ett bygge som är lägre än eller lika med 8 709 på plattformarna CentOS 7 och Debian 8 måste modulen apache access_compat vara aktiverad.

### Bibliotek {#libraries}

Kontrollera att du har de bibliotek som krävs för att installera Adobe Campaign i Linux.

* Bibliotek C måste ha stöd för TLS-läge (trådlokal lagring). Det här läget är aktivt i de flesta fall utom med vissa kärnor för vilka Xen-stöd har inaktiverats.

   Om du vill kontrollera detta kan du använda **uname -a | grep xen**-kommando till exempel.

   Om kommandot inte returnerar något (tom rad) betyder det att konfigurationen är korrekt.

* Du måste ha **version 0.9.8** eller **1.0** av OpenSSL.

   För RHEL 7-distributioner krävs version 1.0 av OpenSSL.

* Om du vill använda Adobe Campaign måste du ha **libicu**-biblioteket installerat.

   Följande versioner av **libicu** stöds (32 eller 64 bitar):

   * RHEL 7, CentOS 7: libicu50
   * Debian 8: libicu52
   * Debian 9: libicu57

   Om du vill använda Adobe Campaign måste du ha biblioteket för biblioteksservrar installerat. Kör följande kommando på RHEL/CentOS:

   ```
   yum install c-ares
   ```

   På Debian:

   ```
   aptitude install libc-ares2
   ```

### SELinux {#selinux}

SELinux-modulen måste vara korrekt konfigurerad när den används.

Om du vill göra det loggar du in som rot och anger följande kommando:

```
echo 0 >/selinux/enforce
```

I filen **/etc/sysconfig/httpd** lades dessutom följande rad till som referens till konfigurationsskriptet för Adobe Campaign-miljön:

```
. ~neolane/nl6/env.sh
```

I RHEL och CentOS noterades kompatibilitetsproblem med klientlagren i databaser när SELinux är aktiverat. För att vara säker på att Adobe Campaign fungerar som det ska rekommenderar vi att du inaktiverar SELinux.

**Använd följande process:**

* Redigera filen **/etc/selinux/config**

* Ändra SELINUX-raden enligt följande:

```
SELINUX=disabled
```

### Teckensnitt för MTA-statistik {#fonts-for-mta-statistics}

Lägg till teckensnitt för att rapporter om MTA-statistik (nms/fra/jsp/stat.jsp) ska visas korrekt.

I Debian lägger du till kommandot:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Använd följande kommando i Redhat:

```
yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
```

### Teckensnitt för japanska förekomster {#fonts-for-japanese-instances}

Teckensnitt med särskilda tecken krävs för de japanska instanserna för att rapporterna ska kunna exporteras till PDF-format.

I Debian lägger du till kommandot:

```
aptitude install fonts-ipafont
```

Lägg till kommandot i Red Hat:

```
yum install ipa-gothic-fonts ipa-mincho-fonts
```

### Installerar LibraryOffice för Debian {#installing-libreoffice-for-debian}

För Debian krävs följande konfigurationer:

1. Installera följande standardpaket:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installera följande teckensnitt (valfritt, men rekommenderas varmt för japanska förekomster):

   ```
   apt-get install fonts-ipafont
   ```

### Installerar LibraryOffice för CentOS {#installing-libreoffice-for-centos}

Följande konfigurationer är nödvändiga med CentOS:

1. Installera följande standardpaket:

   ```
   yum install libreoffice-headless libreoffice-writer libreoffice-calc
   ```

1. Installera följande teckensnitt (tillval, men rekommenderas för japanska förekomster):

   ```
   yum install ipa-gothic-fonts ipa-mincho-fonts
   ```

## Lager för databasåtkomst {#database-access-layers}

Åtkomstlagren för databasmotorn som du använder måste vara installerade på servern och tillgängliga via Adobe Campaign-kontot. Versioner och installationslägen kan variera beroende på vilken databasmotor som används.

Den pilotversion som stöds finns i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Kontrollera även det allmänna avsnittet [Databas](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign stöder alla versioner av PostgreSQL-klientbibliotek från version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** och **libpq.so.3.1**).

Om du använder PostgreSQL med Adobe Campaign måste du också installera motsvarande **pgcrypto**-bibliotek.

### Oracle {#oracle}

Hämta biblioteksversionen för 64-bitars Debian, d.v.s.: **libclntsh.so**, **libclntsh.so.11.1** och **libclntsh.so.10.1**.

Du kan hämta ett Linux RPM-paket från Oracle Technology Network.

>[!NOTE]
>
>Om du redan har installerat Oracle-klienten men den globala miljön (till exempel: /etc/profile) inte är korrekt konfigurerad kan du lägga till saknad information i **nl6/customer.sh**-skriptet Mer information finns i [Miljövariabler](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Felsökning och bästa praxis**

Problem kan uppstå efter en Oracle-klient eller en serveruppdatering, vid versionsändring eller vid den första installationen av instansen.

Om du på klientkonsolen ser att loggarna har tagit oväntade lång tid (en eller flera timmar), arbetsflödets senaste bearbetning, nästa bearbetning och så vidare, kan det bero på ett problem mellan Oracle-klientens bibliotek och Oracle Server. För att undvika sådana problem

1. Se till att du använder den fullständiga **klienten**.

   Olika problem har identifierats när du använder Oracle Instant Client-versionen. Dessutom är det omöjligt att ändra tidszonsfilen på snabbklienten.

1. Kontrollera att **klientversionen** och **databasserverversionen** är **samma**.

   Det är känt att blandningsversioner trots Oracle kompatibilitetsmatris och rekommendationer för att justera klient- och serverversioner orsakar problem.

   Kontrollera även ORACLE_HOME-värdet för att se till att det pekar på den förväntade klientversionen (om flera versioner är installerade på datorn).

1. Se till att klienten och servern använder samma **tidszonsfil**.

### DB2 {#db2}

Den biblioteksversion som stöds är **libdb2.so**.

## Implementeringssteg {#implementation-steps}

Adobe Campaign-installationer för Linux måste utföras i följande sekvens: serverinstallation följt av instanskonfiguration.

Installationsprocessen beskrivs i det här kapitlet. Installationsstegen är följande:

* Steg 1: Information om hur du installerar programservern finns i [Installera paket med Linux](../../installation/using/installing-packages-with-linux.md).
* Steg 2: Integrering med en webbserver (valfritt, beroende på vilka komponenter som används).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om inledande konfiguration](../../installation/using/about-initial-configuration.md).
