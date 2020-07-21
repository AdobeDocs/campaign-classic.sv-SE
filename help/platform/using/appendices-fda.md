---
title: Tillägg
seo-title: FDA-tillägg
description: FDA-tillägg
seo-description: null
page-status-flag: never-activated
uuid: 2596fabc-679a-45c8-a62a-165c221654b7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: a84a73a9-9930-449f-8b81-007a0e9d5233
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 789799f79608c26126d70e896bd1b7a6df33e4fa
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---


# Tillägg {#fda-appendices}

## Ytterligare Teradata-konfigurationer {#teradata-configuration}

### Kompatibilitet {#teradata-compatibility}

**Baserad i Unicode**

| Databasversion | Drivrutinsversion | Minimal kampanjversion krävs | Anteckning |
|:-:|:-:|:-:|:-:|
| 15 | 15 | Campaign Classic 17.9 | Under Linux: Frågor med tidsstämpel kan misslyckas (som har korrigerats i version 8937 för 18.4 och 8977 för 18.10) I felsökningsläge kan det uppstå varningsmeddelanden som gäller felaktig minnesanvändning i drivrutinen. |
| 15 | 16 | Campaign Classic 17.9 | Rekommenderad installation av en Teradata 15-databas i Linux. |
| 16 | 16 | Campaign Classic 18.10 | Unicode-tecken med surrogatpar hanteras inte helt. Det bör gå att använda surrogattecken i data. Det går inte att använda surrogater i ett filtervillkor för en fråga utan den här ändringen. |
| 16 | 15 | stöds inte |   |

**Baserat på Latin1**

Tidigare versioner än Adobe Campaign Classic 17.9 har endast stöd för Teradata Latin-1-databaser.

Från och med Adobe Campaign Classic 17.9 har vi nu stöd för Teradata-databasen i Unicode som standard.

Kunder med en Latin-1 Teradata-databas som migrerar till en nyligen släppt Campaign Classic måste lägga till parametern APICharSize=1 i alternativen för det externa kontot.

### Databaskonfiguration {#database-configuration}

#### Användarkonfiguration {#user-configuration}

Följande rättigheter krävs: skapa/släppa/köra anpassade procedurer, skapa/släppa/infoga/markera tabeller. Du kan också behöva skapa användarlägesfunktioner om du vill använda funktionen md5 och sha2 i Adobe Campaign-instansen.

Kontrollera att du har konfigurerat rätt tidszon. Den ska matcha vad som kommer att anges i det externa konto som skapas i Adobe Campaign-instansen.

Adobe Campaign anger inte skyddsläge (reserv) för de objekt som skapas i databasen. Du kan behöva ange ett standardvärde för användaren som Adobe Campaign ska använda för att ansluta till Teradata-databasen med följande fråga:

| inaktivera standardåtergång |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

#### MD5-installation {#md5-installation}

Om du vill använda md5-funktioner i din Adobe Campaign-instans måste du installera funktionen för användarläge i Teradata-databasen från den här [sidan](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

SHA1 för den hämtade filen är som följer 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Så här installerar du md5:

1. Zippa upp filen md5_20080530.zip.

1. Gå till katalogen md5/src.

1. Anslut till Teradata-databasen med hjälp av bteq.

1. Kör följande bteq-kommando:

   ```
   .run file = hash_md5.btq
   ```

#### SHA2-installation {#sha2-installation}

Om du vill använda sha2-funktioner i Adobe Campaign måste du installera funktionen för användarläge i Teradata-databasen från den här [sidan](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

Sha1 för den hämtade filen är som följer e87438d37424836358bd3902cf1adeb629349780.

Så här installerar du SHA2:

1. Zippa upp filen teradata-udf-sha2-1.0.zip.

1. Gå till katalogen teradata-udf-sha2-1.0/src.

1. Anslut till Teradata-databasen med hjälp av bteq.

1. Kör följande två bteq-kommandon:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

#### UDF_UTF16TO8-installation {#UDF-UTF16TO8-installation}

Om du vill använda udf_utf16to8-funktioner i din Adobe Campaign-instans måste du installera funktionen för användarläge i Teradata-databasen från verktygslådan **för** Teradata på den här [sidan](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

SHA1 för den hämtade filen är som följer e58235f434f52c71316a577cb48e20b97d24f470.

Så här installerar du udf_utf16to8:

1. Zippa upp filen utk_release1.7.0.0.zip.

1. Leta efter filen udf_utf16to8.o i de extraherade filerna och navigera till katalogen som innehåller filen. Den ska ha namnet utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Anslut till Teradata-databasen med hjälp av bteq.

1. Skriv i följande bteq-kommando:

   ```
   REPLACE FUNCTION udf_utf16to8 (
   inputString VARCHAR(8000) CHARACTER SET UNICODE
   ) RETURNS VARCHAR(16000) CHARACTER SET LATIN
   LANGUAGE C
   NO SQL
   EXTERNAL NAME 'CO!i18n103!udf_utf16to8.o!F!udf_utf16to8'
   PARAMETER STYLE SQL;
   
   -- Test: should return 410042
   SELECT CAST(Char2HexInt(UDF_UTF16to8(_UNICODE'004100000042'XC)) AS VARCHAR(100));
   
### Kampanjserverkonfiguration för Linux {#campaign-server-linux}

Följande krävs för drivrutinsinstallationen:

* Teradata ODBC Driver, som finns på den här [sidan](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (används för massinläsning), som finns på den här [sidan](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Filnamn och SHA1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f4 4fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Om det inte finns något paket för din Linux-distribution kan du installera enligt anvisningarna på en CentOS 7 (t.ex. med docker) och sedan kopiera innehållet i /opt/teradata på Adobe Campaign-servern.

#### Installation av ODBC-drivrutin {#odbc-installation}

Så här installerar du ODBC-drivrutinen:

1. Extrahera filen tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Gå till katalogen tdodbc1620.

1. Du kan behöva åtgärda installationsskriptet:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Kör setup_wrapper.sh.

#### Installation av Teradata-verktyg och -verktyg {#teradata-tools-installation}

Så här installerar du verktyg:

1. Extrahera filen TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz.

1. Gå till katalogen TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Kör setup_wrapper.sh.

1. Gå till katalogen TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Kör setup_wrapper.sh.

1. Gå till katalogen TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Kör setup_wrapper.sh.

1. En libtelapi.so-fil bör vara tillgänglig i /opt/teradata/client/16.20/lib64.

#### Drivrutinskonfiguration {#driver-configuration}

Mer information om drivrutinskonfigurationen finns i det här [avsnittet](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

#### Miljövariabler {#environment-varaiables}

Mer information om miljövariablerna på Adobe Campaign-servern finns i det här [avsnittet](../../platform/using/legacy-connectors.md#configure-access-to-teradata).

### Kampanjserverkonfiguration för Windows #campaign-server-windows}

Du måste först ladda ned Teradata Tools och Utilities för Windows. Du kan hämta den från den här [sidan](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Installera ODBC-drivrutinen och Teradata Parallel Transporter Base. Den installerar telapi.dll som används för massinläsning på Teradata-databasen.

Kontrollera att sökvägen till drivrutinen och verktygen finns i variabeln PATH som ingen server kommer att ha under körningen. Som standard är sökvägen C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

### Felsökning av externa konton {#external-account-troubleshooting}

Om följande fel uppstår när anslutningen **TIM-030008 testas Datum &#39;2&#39;: tecken som saknas (iRc=-53)** kontrollerar att ODBC-drivrutinen är korrekt installerad och att LD_LIBRARY_PATH (Linux)/PATH (Windows) är inställd för Campaign-servern.

Felet **ODB-240000 ODBC:[Det gick inte att hitta namnet på Microsoft][ODBC Driver Manager]-datakällan och ingen standarddrivrutin har angetts.** inträffar med Windows om du använder en 16.X-drivrutin. Adobe Campaign förväntar sig att teradata får namnet {teradata} i odbcinst.ini.
Om du har en 18.10 Adobe Campaign-serverversion kan du lägga till ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; i alternativen för det externa kontot. Versionsnumret kan ändras. Du hittar det exakta namnet genom att köra odbcad32.exe och gå till fliken Drivrutiner.
För version under 18.10 måste du kopiera Teradata-delen av odbcinst.ini som skapas av drivrutinsinstallationen till ett nytt avsnitt som kallas Teradata. I det här fallet kan regedit användas.

Om basen är i latin1 måste du lägga till APICharSize=1 i alternativen.

### Tidszon {#timezone}

Teradata använder ett tidszonsnamn som inte är standard. Du hittar listan på [Teradata-webbplatsen](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign kommer att försöka konvertera tidszonen som anges i den externa konfigurationen till något som Teradata förstår. Om ingen korrespondens hittas kommer tidszonen GMT+X (eller GMT-X) som stängs att hittas för sessionen, med en varning i loggen.

Konverteringen är klar med läsningen av en fil med namnet teradata_timezone.txt som ska finnas i följande datakatalog: /usr/local/neolane/nl6/datakit under linux. Om du redigerar den här filen måste du kontakta Adobe Campaign-teamet för att ändra källkoden, annars skrivs den här filen över vid nästa Campaign-uppdatering.

Tidszonen som används för att ansluta anges när en lserver körs med växeln -verbose, till exempel:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Om den tidszon som används inte är korrekt kan ett alternativ med namnet&quot;TimeZoneName&quot; läggas till på det externa kontot. I så fall använder du Teradata-värdet, till exempel&quot;TimeZoneName=Europe Central&quot;.

När massinläsning eller&quot;snabb inläsning&quot; används i Teradata-dokument kan Campaign inte ange tidszonen. Därför rekommenderar vi att du anger standardtidszonen för användaren som ska användas i Campaign för att ansluta:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```

## MySQL 5.7-konfiguration {#mysql-57-configuration}

### Serverkonfiguration {#server-configuration-mysql}

Serverkonfigurationen kräver inga specifika installationssteg. Adobe Campaign bör arbeta med en latin1-databas, standard i MySQL eller en Unicode-databas.

### Drivrutinsinstallation {#driver-installation-mysql}

#### Debian {#debian-mysql}

Hämta mysql-apt-config.deb från den här [sidan](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en).

Installera klientbiblioteket:

```
$ dpkg -i mysql-apt-config_*_all.deb # choose mysql-5.7 in the configuration menu
$ apt update
$ apt install libmysqlclient20
```

#### Windows {#windows-mysql}

Hämta C-anslutningen från den här [sidan](https://dev.mysql.com/downloads/connector/c). Vi rekommenderar att du laddar ned version 5.7.

Kontrollera att katalogen som innehåller libmysqlclient.dll läggs till i den PATH-miljövariabel som nlserver ska använda.

#### CentOS {#centos-mysql}

Hämta mysql57-community-release.noarch.rpm från den här [sidan](https://dev.mysql.com/downloads/repo/yum).

Installera klientbiblioteket:

$ yum install mysql57-community-release-el7-9.noarch.rpm$ yum install mysql-community-libs

### Konfiguration av externt konto {#external-account-mysql}

Konfigurationen av det externa kontot kräver inga specifika steg. Kontrollera att tidszonen och Använd unicode-data är inställda enligt databasen.
