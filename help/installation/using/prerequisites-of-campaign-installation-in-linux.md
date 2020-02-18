---
title: Krav för Campaign-installation i Linux
seo-title: Krav för Campaign-installation i Linux
description: Krav för Campaign-installation i Linux
seo-description: null
page-status-flag: never-activated
uuid: 65c7af3f-ca1d-4255-b54a-6a3c83af40ae
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 3e2ccb70-6c0c-435f-9c06-f3e5e40367bb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Krav för Campaign-installation i Linux{#prerequisites-of-campaign-installation-in-linux}

## Programvarukrav {#software-prerequisites}

I det här avsnittet beskrivs de preliminära konfigurationssteg som krävs innan Adobe Campaign installeras.

Den tekniska konfiguration och programkonfiguration som krävs för att installera Adobe Campaign finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Följande komponenter måste installeras och konfigureras korrekt:

* Apache, se [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html),
* Java JDK och OpenJDK, se [Java Development Kit - JDK](../../installation/using/application-server.md#java-development-kit---jdk),
* Bibliotek, se [Bibliotek](#libraries),
* Lager för databasåtkomst, se [Lager](#database-access-layers)för databasåtkomst.
* LibreOffice, se [Installera LibraryOffice för Debian](#installing-libreoffice-for-debian) och [installera LibraryOffice för CentOS](#installing-libreoffice-for-centos).
* Teckensnitt finns i [Teckensnitt för MTA-statistik](#fonts-for-mta-statistics) och [Teckensnitt för japanska förekomster](#fonts-for-japanese-instances).

>[!NOTE]
>
>Om du vill installera ett bygge som är lägre än eller lika med 8 709 på plattformarna CentOS 7 och Debian 8 måste modulen apache access_compat vara aktiverad.

### Bibliotek {#libraries}

Kontrollera att du har de bibliotek som krävs för att installera Adobe Campaign i Linux.

* Bibliotek C måste ha stöd för TLS-läge (trådlokal lagring). Det här läget är aktivt i de flesta fall utom med vissa kärnor för vilka Xen-stöd har inaktiverats.

   Om du vill kontrollera det kan du använda **namnet -a| grep xen** command till exempel.

   Om kommandot inte returnerar något (tom rad) betyder det att konfigurationen är korrekt.

* Du måste ha **version 0.9.8** eller **1.0** av OpenSSL.

   För RHEL 7-distributioner krävs version 1.0 av OpenSSL.

* Om du vill använda Adobe Campaign måste du ha **biblioteket libicu** installerat.

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

I filen **/etc/sysconfig/httpd** lades dessutom följande rad till för att referera till konfigurationsskriptet för Adobe Campaign-miljön:

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

## Åtkomstlager för databaser {#database-access-layers}

Åtkomstlagren för databasmotorn som du använder måste vara installerade på servern och tillgängliga via Adobe Campaign-kontot. Versioner och installationslägen kan variera beroende på vilken databasmotor som används.

Den pilotversion som stöds finns i [kompatibilitetsmatrisen](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html).

Kontrollera även det allmänna avsnittet [Databas](../../installation/using/database.md) .

### PostgreSQL {#postgresql}

Adobe Campaign stöder alla versioner av PostgreSQL-klientbibliotek från version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** och **libpq.so.3.1**).

Om du använder PostgreSQL med Adobe Campaign måste du även installera motsvarande **pgcrypto** -bibliotek.

### Oracle {#oracle}

Hämta biblioteksversionen för 64-bitars Debian, d.v.s.: **libclntsh.so**, **libclntsh.so.11.1** och **libclntsh.so.10.1**.

Du kan hämta ett Linux RPM-paket från Oracle Technology Network.

>[!NOTE]
>
>Om du redan har installerat Oracle-klienten men den globala miljön (till exempel: /etc/profile) inte är korrekt konfigurerad kan du lägga till saknad information i **nl6/customer.sh** . Mer information finns i [Miljövariabler](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Felsökning och bästa praxis**

Problem kan uppstå efter en Oracle-klient eller en serveruppdatering, vid versionsändring eller vid den första installationen av instansen.

Om du på klientkonsolen noterar att loggarna har oväntat lång tid (en eller flera timmar), att arbetsflödet har bearbetats senast, att nästa bearbetning har utförts och så vidare, kan det bero på ett problem mellan biblioteket för Oracle-klienten och Oracle-servern. För att undvika sådana problem

1. Se till att använda den **fullständiga klienten**.

   Olika problem har identifierats vid användning av Oracle Instant Client-versionen. Dessutom är det omöjligt att ändra tidszonsfilen på snabbklienten.

1. Kontrollera att **klientversionen** och **databasserverversionen** är **samma**.

   Det är känt att blandningsversioner trots Oracles kompatibilitetsmatris och rekommendationer för att justera klient- och serverversioner orsakar problem.

   Kontrollera också ORACLE_HOME-värdet för att se till att det pekar på den förväntade klientversionen (om flera versioner är installerade på datorn).

1. Se till att klienten och servern använder samma **tidszonsfil**.

### DB2 {#db2}

Den biblioteksversion som stöds är **libdb2.so**.

## Implementeringssteg {#implementation-steps}

Adobe Campaign-installationer för Linux måste utföras i följande sekvens: serverinstallation följt av instanskonfiguration.

Installationsprocessen beskrivs i det här kapitlet. Installationsstegen är följande:

* Steg 1: Information om hur du installerar programservern finns i [Installera paket med Linux](../../installation/using/installing-packages-with-linux.md).
* Steg 2: Integrering med en webbserver (valfritt, beroende på vilka komponenter som används).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om den inledande konfigurationen](../../installation/using/about-initial-configuration.md).
