---
product: campaign
title: Krav för Campaign-installation i Linux
description: Förutsättningar för Campaign-installation i Linux
feature: Installation, Instance Settings
badge-v7-prem: label="Endast på plats/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala distributioner och hybriddistributioner"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: acbd2873-7b1c-4d81-bc62-cb1246c330af
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Krav för att installera Campaign på Linux{#prerequisites-of-campaign-installation-in-linux}

## Programvarukrav {#software-prerequisites}

I det här avsnittet beskrivs de preliminära konfigurationssteg som krävs innan du installerar Adobe Campaign.

Den tekniska konfiguration och programkonfiguration som krävs för att installera Adobe Campaign finns i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Som en påminnelse måste följande komponenter installeras och konfigureras korrekt:

* Apache, se [Kompatibilitetsmatris](../../rn/using/compatibility-matrix.md),
* Java JDK och OpenJDK, se [Java Development Kit - JDK](../../installation/using/application-server.md#jdk),
* Bibliotek, se [Bibliotek](#libraries),
* Lager för databasåtkomst, se [Lager för databasåtkomst](#database-access-layers),
* LibreOffice, se [Installera LibraryOffice för Debian](#installing-libreoffice-for-debian) och [Installera LibraryOffice för CentOS](#installing-libreoffice-for-centos),
* Teckensnitt finns i [Teckensnitt för MTA-statistik](#fonts-for-mta-statistics) och [Teckensnitt för japanska förekomster](#fonts-for-japanese-instances).


### Bibliotek {#libraries}

Om du vill installera Adobe Campaign i Linux måste du se till att du har de bibliotek som krävs.

* Bibliotek C måste ha stöd för TLS-läge (Thread Local Storage). Det här läget är aktivt i de flesta fall förutom med vissa kärnor för vilka Xen-stöd har inaktiverats.

  För att kontrollera detta kan du till exempel använda **kommandot uname -a | grep xen** .

  Om kommandot inte returnerar en tom rad betyder det att konfigurationen är korrekt.

* Du måste ha OpenSSL-version **1.0.2** eller senare.

  För RHEL-distributioner krävs version 1.0 av OpenSSL.

* Om du vill använda Adobe Campaign måste du ha **libicu**-biblioteket installerat.

### SELinux {#selinux}

När den används måste SELinux-modulen vara korrekt konfigurerad.

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
apt install xfonts-base xfonts-75dpi ttf-bitstream-vera ttf-dejavu
```

Använd följande kommando för RHEL:

```
dnf install xorg-x11-fonts-misc xorg-x11-fonts-75dpi dejavu-lgc-sans-fonts  dejavu-sans-fonts dejavu-sans-mono-fonts dejavu-serif-fonts
```

### Teckensnitt för japanska förekomster {#fonts-for-japanese-instances}

Teckensnitt med specifika tecken är nödvändiga för de japanska instanserna för att kunna exportera rapporterna till PDF-format.

I Debian, lägg till kommandot:

```
apt install fonts-ipafont
```

För RHEL lägger du till följande kommando:

```
dnf install epel-release # if required
dnf install vlgothic-fonts
```

### Installerar LibraryOffice för Debian {#installing-libreoffice-for-debian}

För Debian krävs följande konfigurationer:

1. Installera följande standardpaket:

   ```
   apt-get install libreoffice-writer libreoffice-calc libreoffice-java-common
   ```

1. Installera följande teckensnitt (valfritt men rekommenderas starkt för japanska instanser):

   ```
   apt-get install fonts-ipafont
   ```

### Installera LibreOffice för CentOS {#installing-libreoffice-for-centos}

Följande konfigurationer är nödvändiga med CentOS:

```
yum install libreoffice-headless libreoffice-writer libreoffice-calc
```

## Lager för databasåtkomst {#database-access-layers}

Åtkomstlagren för den databasmotor du använder måste vara installerade på servern och vara tillgängliga via Adobe Campaign-kontot. Versioner och installationslägen kan variera beroende på vilken databasmotor som används.

Den pilotversion som stöds finns i [kompatibilitetsmatrisen](../../rn/using/compatibility-matrix.md).

Kontrollera även det allmänna avsnittet [Databas](../../installation/using/database.md).

### PostgreSQL {#postgresql}

Adobe Campaign stöder alla versioner av PostgreSQL-klientbibliotek från version 9.6: **libpq.so.5**.

Om du använder PostgreSQL med Adobe Campaign måste du även installera motsvarande **pgcrypto** -bibliotek.

### Oracle {#oracle}

Hämta biblioteksversionen för 64-bitars Debian, d.v.s. **: libclntsh.so**, **libclntsh.so.19.1**, **libclntsh.so.18.1**, **libclntsh.so.12.1**, **libclntsh.so.11.1** eller **libclntsh.so.10.1**.

Du kan hämta ett Linux RPM-paket från Oracle Technology Network.

>[!NOTE]
>
>Om du redan har installerat Oracle-klienten men den globala miljön (till exempel: /etc/profile) inte är korrekt konfigurerad kan du lägga till information som saknas i skriptet **nl6/customer.sh** Mer information finns i [Miljövariabler](../../installation/using/installing-packages-with-linux.md#environment-variables).

**Felsökning och metodtips**

Problem kan uppstå efter en Oraclena klient eller serveruppdatering, vid versionsändring eller vid den första installationen av instansen.

Om du på klientkonsolen ser att det finns oväntade tidsfördröjningar (en eller flera timmar) i loggar, senaste arbetsflödesbearbetning, nästa bearbetning och så vidare, kan det vara problem mellan Oraclets bibliotek och Oracle Server. För att undvika sådana problem

1. Se till att använda den **fullständiga klienten**.

   Olika problem har identifierats vid användning av Oracle Instant Client-versionen. Dessutom är det omöjligt att ändra tidszonsfilen på direktklienten.

1. Kontrollera att klientversionen och databasserverversionen **är desamma**&#x200B;**.**&#x200B;**&#x200B;**

   Att blanda versioner trots Oraclets kompatibilitetsmatris och rekommendation att justera klient- och serverversioner är känt för att orsaka problem.

   Kontrollera även ORACLE_HOME-värdet för att se till att det pekar på den förväntade klientversionen (om flera versioner är installerade på datorn).

1. Kontrollera att klienten och servern använder samma **timezone-fil**.

## Implementeringssteg {#implementation-steps}

Adobe Campaign-installationer för Linux måste utföras i följande sekvens: serverinstallation följt av instanskonfiguration.

Installationsprocessen beskrivs i det här kapitlet. Installationsstegen är följande:

* Steg 1: Installera programservern, se [Installera paket med Linux](../../installation/using/installing-packages-with-linux.md).
* Steg 2: Integrera med en webbserver (valfritt, beroende på vilka komponenter som används).

När installationen är klar måste du konfigurera instanserna, databasen och servern. Mer information finns i [Om den inledande konfigurationen](../../installation/using/about-initial-configuration.md).
