---
product: campaign
title: Krav för Campaign-installation i Linux
description: Krav för Campaign-installation i Linux
feature: Installation, Instance Settings
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---

# Krav för att installera Campaign på Linux{#prerequisites-of-campaign-installation-in-linux}



## Programvarukrav {#software-prerequisites}

I det här avsnittet beskrivs de preliminära konfigurationssteg som krävs innan du installerar Adobe Campaign.

Den tekniska konfiguration och programkonfiguration som krävs för att installera Adobe Campaign finns i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

Som en påminnelse måste följande komponenter installeras och konfigureras korrekt:

* Apache, se [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md),
* Java JDK och OpenJDK, se [Java Development Kit - JDK,](../../installation/using/application-server.md#java-development-kit---jdk)
* Bibliotek, se [Bibliotek](#libraries),
* Lager för databasåtkomst, se [Åtkomstlager för databaser](#database-access-layers),
* LibreOffice, se [Installerar LibraryOffice för Debian](#installing-libreoffice-for-debian) och [Installerar LibraryOffice för CentOS](#installing-libreoffice-for-centos),
* Teckensnitt, se [Teckensnitt för MTA-statistik](#fonts-for-mta-statistics) och [Teckensnitt för japanska förekomster](#fonts-for-japanese-instances).

>[!NOTE]
>
>Om du vill installera ett bygge som är lägre än eller lika med 8 709 på plattformarna CentOS 7 och Debian 8 måste modulen apache access_compat vara aktiverad.

### Bibliotek {#libraries}

Om du vill installera Adobe Campaign i Linux måste du se till att du har de bibliotek som krävs.

* Bibliotek C måste ha stöd för TLS-läge (Thread Local Storage). Detta läge är aktivt i de flesta fall förutom med vissa kärnor för vilka Xen-stöd har inaktiverats.

  För att kontrollera detta kan du till exempel använda **kommandot uname -a | grep xen** .

  Om kommandot inte returnerar något (tom rad) betyder det att konfigurationen är korrekt.

* Du måste ha OpenSSL-version **1.0.2** eller senare.

  För RHEL 7/8-distributioner krävs version 1.0 av OpenSSL.

* Om du vill använda Adobe Campaign måste du ha **libicu** bibliotek installerat.

  Följande versioner av **libicu** stöds (32 eller 64 bitar):

   * RHEL 7/8, CentOS 7: libicu50
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

När SELinux-modulen används måste den vara korrekt konfigurerad.

Om du vill göra det loggar du in som rot och anger följande kommando:

```
echo 0 >/selinux/enforce
```

Förutom detta finns i **/etc/sysconfig/httpd** filen lades följande rad till som referens till konfigurationsskriptet för Adobe Campaign-miljön:

```
. ~neolane/nl6/env.sh
```

I RHEL och CentOS noterades kompatibilitetsproblem med klientlagren i databaser när SELinux är aktiverat. För att vara säker på att Adobe Campaign fungerar som det ska rekommenderar vi att du inaktiverar SELinux.

**Använd följande process:**

* Redigera filen **/etc/selinux/config**

* Ändra SELINUX-raden på följande sätt:

```
SELINUX=disabled
```

### Teckensnitt för MTA-statistik {#fonts-for-mta-statistics}

Om du vill att rapporter om MTA-statistik (nms/fra/jsp/stat.jsp) ska visas korrekt lägger du till teckensnitt.

I Debian, lägg till kommandot:

```
aptitude install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Använd följande kommando i Redhat:

* För CentOS/RHEL 7:

  ```
  yum install xorg-x11-fonts-base xorg-x11-fonts-75dpi bitstream-vera-fonts dejavu-lgc-fonts
  ```

* För RHEL 8:

  ```
  dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
  ```

### Teckensnitt för japanska förekomster {#fonts-for-japanese-instances}

Teckensnitt med särskilda tecken krävs för de japanska instanserna för att du ska kunna exportera rapporterna till PDF-format.

I Debian lägger du till kommandot:

```
aptitude install fonts-ipafont
```

I Red Hat lägger du till kommandot:

* För RHEL 7:

  ```
  yum install ipa-gothic-fonts ipa-mincho-fonts
  ```

* För RHEL 8:

  ```
  dnf install vlgothic-fonts
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

### Installera LibreOffice för CentOS {#installing-libreoffice-for-centos}

Följande konfigurationer är nödvändiga med CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Lager för databasåtkomst {#database-access-layers}

Åtkomstlagren för databasmotorn som du använder måste vara installerade på servern och tillgängliga via Adobe Campaign-kontot. Versioner och installationslägen kan variera beroende på vilken databasmotor som används.

Pilotversionen som stöds finns i [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md).

Kontrollera även det allmänna [Databas](../../installation/using/database.md) -avsnitt.

### PostgreSQL {#postgresql}

Adobe Campaign stöder alla versioner av PostgreSQL-klientbibliotek från version 7.2: (**libpq.so.5**, **libpq.so.4**, **libpq.so.3.2** och **libpq.so.3.1**).

Om du använder PostgreSQL med Adobe Campaign måste du även installera motsvarande **pgcrypto** bibliotek.

### Oracle {#oracle}

Hämta biblioteksversionen för 64-bitars Debian, dvs: **libclntsh.so**, **libclntsh.so.11.1** och **libclntsh.so.10.1**.

Du kan hämta ett Linux RPM-paket från Oracle Technology Network.

>[!NOTE]
>
>Om du redan har installerat Oracle-klienten men den globala miljön (till exempel /etc/profile) inte är korrekt konfigurerad, kan du lägga till saknad information i **nl6/customer.sh** skript Mer information finns i [Miljövariabler](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Felsökning och bästa praxis**

Problem kan uppstå efter en Oracle-klient- eller serveruppdatering, versionsändring eller vid den första installationen av instansen.

Om du märker på klientkonsolen att det finns oväntade tidsfördröjningar (en eller flera timmar) i loggar, arbetsflödets senaste bearbetning, nästa bearbetning och så vidare, kan det finnas ett problem mellan Oracle-klientens bibliotek och Oracle Server. För att undvika sådana problem

1. Se till att du använder **fullständig klient**.

   Olika problem har identifierats när du använder Oraclet Instant Client-version. Dessutom är det omöjligt att ändra tidszonsfilen på snabbklienten.

1. Se till att **klientversion** och **databasserverversion** är **samma**.

   Att blanda versioner trots Oracles kompatibilitetsmatris och rekommendation att justera klient- och serverversioner är känt för att orsaka problem.

   Kontrollera också ORACLE_HOME värdet för att se till att det pekar på den förväntade klientversionen (om flera versioner är installerade på datorn).

1. Kontrollera att klienten och servern använder samma **tidszonsfil**.

### DB2 (på engelska) {#db2}

Den biblioteksversion som stöds är **libdb2.so**.

## Implementeringssteg {#implementation-steps}

Adobe Campaign-installationer för Linux måste utföras i följande sekvens: serverinstallation följt av instanskonfiguration.

Installationsprocessen beskrivs i det här kapitlet. Installationsstegen är följande:

* Steg 1: Installera programservern, se [Installera paket med Linux](../../installation/using/installing-packages-with-linux.md).
* Steg 2: Integrera med en webbserver (valfritt, beroende på vilka komponenter som används).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om inledande konfiguration](../../installation/using/about-initial-configuration.md).
