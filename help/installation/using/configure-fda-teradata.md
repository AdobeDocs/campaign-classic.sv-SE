---
product: campaign
title: Konfigurera åtkomst till Teradata
description: Lär dig konfigurera åtkomst till Teradata i FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 3a5856c3-b642-4722-97ff-6ae7107efdbe
source-git-commit: 65e80f16a6beaee89b51636017c42766589e179e
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 1%

---

# Konfigurera åtkomst till Teradata {#configure-access-to-teradata}

![](../../assets/v7-only.svg)

Använd kampanj [Åtkomst till federerade data](../../installation/using/about-fda.md) (FDA) om du vill bearbeta information som lagras i en extern databas. Följ stegen nedan för att konfigurera åtkomst till Teradata.

1. Installera och konfigurera [Drivrutiner för teradata](#teradata-config)
1. Konfigurera Teradatan [externt konto](#teradata-external) i Campaign
1. Konfigurera [ytterligare konfiguration](#teradata-additional-configurations) för Teradata- och kampanjserver

## Teradata {#teradata-config}

Du måste installera drivrutiner för att Teradatan ska kunna ansluta till Campaign.

1. Installera [ODBC-drivrutin för Teradata](https://downloads.teradata.com/download/connectivity/odbc-driver/linux).

   Den består av tre paket som kan installeras på Red Hat (eller CentOS)/Suse i följande ordning:

   * TeraGSS
   * tdicu1510 (installera den med setup_wrapper.sh)
   * tdodbc1510 (installera den med setup_wrapper.sh)

1. Konfigurera ODBC-drivrutinen. Konfigurationen kan utföras i standardfilerna: **/etc/odbc.ini** för allmänna parametrar och /etc/odbcinst.ini för att deklarera drivrutiner:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; motsvarar platsen för **odbcinst.ini** -fil.

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/17.10/lib64/tdataodbc_sb64.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. Ange miljövariablerna för Adobe Campaign-servern:

   * **LD_LIBRARY_PATH**: /opt/teradata/client/15.10/lib64 och /opt/teradata/client/15.10/odbc_64/lib.
   * **ODBCINI**: platsen för filen odbc.ini (till exempel /etc/odbc.ini).
   * **NLSPATH**: plats för filen opermsgs.cat (/opt/teradata/client/15.10/msg/opermsgs.cat)

>[!NOTE]
>
>För att ansluta till en extern Teradata-databas i FDA krävs ytterligare konfigurationssteg på Adobe Campaign-servern. [Läs mer](#teradata-additional-configurations).

## Teradatans externa konto{#teradata-external}

Med det externa Teradatan kan du ansluta Campaign-instansen till din Teradatas externa databas.

1. Från kampanj **[!UICONTROL Explorer]**, klicka **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Klicka **[!UICONTROL New]** och markera **[!UICONTROL External database]** as **[!UICONTROL Type]**.

   ![](assets/ext_account_19.png)

1. Så här konfigurerar du **[!UICONTROL Teradata]** externt konto måste du ange:

   * **[!UICONTROL Type]**: Välj **[!UICONTROL Teradata]** typ.

   * **[!UICONTROL Server]**: URL eller namn på Teradata-servern

   * **[!UICONTROL Account]**: Namn på kontot som används för att komma åt Teradata-databasen

   * **[!UICONTROL Password]**: Lösenord som används för att ansluta till Teradata-databasen

   * **[!UICONTROL Database]**: Databasens namn (valfritt)

   * **[!UICONTROL Options]**: Alternativ som ska skickas via Teradatan. Använd följande format: &#39;parameter=value&#39;. Använd semikolon som avgränsare mellan värden.

   * **[!UICONTROL Timezone]**: Tidszonen anges i Teradata. [Läs mer](#timezone)

Kopplingen stöder följande alternativ:

| Option | Beskrivning |
|---|---|
| TD_MAX_SESSIONS | Anger det maximala antalet inloggningssessioner som Teradata Parallel Transporter kan hämta för ett operatorjobb. <br>Mer information finns på [den här sidan](https://documentation.sas.com/doc/en/pgmsascdc/9.4_3.5/ds2ref/p1naft0um1kn3vn1ubgkrjdf7c3a.html). |
| TimeZoneName | Namn på serverns tidszon. |
| CharacterSet | Används för att konfigurera teckenuppsättningen Teradata. <br>Mer information finns på [den här sidan](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/Configuration-of-odbc.ini-in-UNIX/Linux-and-Apple-OS-X/Teradata-DSN-Options#rub1478609534082__table_N102D3_N102B6_N102B3_N10001). |
| IANAAppCodePage | Kodsida för ODBC-program. <br>Mer information finns på [den här sidan](https://docs.teradata.com/r/ODBC-Driver-for-Teradata-User-Guide/May-2017/ODBC-Driver-for-Teradata-Application-Development/International-Character-Set-Support/Application-Code-Page) |

### Lägg till ytterligare ODBC-externa konton {#add-external}

>[!NOTE]
>
> Det här alternativet är inte tillgängligt för byggen som är äldre än 7.3.1-versionen.

Teradata-drivrutinen tillhandahåller ett eget ODBC-bibliotek, men det här biblioteket kanske inte är kompatibelt med andra ODBC-externa konton.

Om du vill konfigurera ett annat externt konto som även använder ODBC, t.ex. Snowflake, måste du lägga till ett ODBCLib-alternativ som är inställt på sökvägen till ODBC-standardbiblioteket (`/usr/lib/x86_64-linux-gnu/libodbc.so` på Debian och `/usr/lib64/libodbc.so` på RHEL/CentOS).

![](assets/ext_account_24.png)

### Frågeränder

När flera Adobe Campaign-användare ansluter till samma externa FDA-Teradata-konto är **[!UICONTROL Query banding]** kan du ställa in ett frågeband, dvs. en uppsättning nyckel/värde-par, för en session.

![](assets/ext_account_20.png)

När det här alternativet är konfigurerat skickar Adobe Campaign metadata varje gång en Campaign-användare utför en fråga i Teradata-databasen, vilket består av en lista med nycklar som är kopplade till den här användaren. Dessa data kan sedan användas av Teradata-administratörer för revision eller för att hantera åtkomsträttigheter.

>[!NOTE]
>
>Mer information om **[!UICONTROL Query banding]**, se [Teradata](https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw).

Så här konfigurerar du Query-ränder:

1. Använd  **[!UICONTROL Default]** för att ange ett standardfrågeband som ska användas om en användare inte har något associerat frågeband. Om det här fältet lämnas tomt kommer användare utan frågeband inte att kunna använda Teradata.

1. Använd **[!UICONTROL Users]** för att ange ett frågeband för varje användare. Du kan lägga till så många nyckel/värde-par du behöver, t.ex. priority=1;workload=high. Om användaren inte har något tilldelat frågeband **[!UICONTROL Default]** -fältet används.

1. Kontrollera **[!UICONTROL Active]** om du vill aktivera den här funktionen

#### Felsökning av externa konton {#external-account-troubleshooting}

Om följande fel uppstår när anslutningen testas **TIM-030008 Datum &#39;2&#39;: tecken som saknas (iRc=-53)** Kontrollera att ODBC-drivrutinen är korrekt installerad och att LD_LIBRARY_PATH (Linux)/PATH (Windows) är inställd för Campaign-servern.

Felet **ODB-240000 ODBC-fel: [Microsoft][ODBC Driver Manager] Det gick inte att hitta namnet på datakällan och ingen standarddrivrutin har angetts.** inträffar med Windows om du använder en 16.X-drivrutin. Adobe Campaign förväntar sig att teradatan får namnet {teradata} i odbcinst.ini.

* Från och med Campaign 18.10 kan du lägga till ODBCDriverName=&quot;Teradata Database ODBC Driver 16.10&quot; i alternativen för det externa kontot. Versionsnumret kan ändras. Du hittar det exakta namnet genom att köra odbcad32.exe och gå till fliken Drivrutiner.

* Om du använder en äldre Campaign-version måste du kopiera Teradatan av odbcinst.ini som skapas av drivrutinsinstallationen till ett nytt avsnitt som kallas Teradata. I det här fallet kan du använda regedit. Om basen är på latin1 måste du lägga till **APICharSize=1** i alternativen.

## Ytterligare konfigurationer {#teradata-additional-configurations}

<!--
### Compatibility {#teradata-compatibility}

**Based in Unicode**

| Database version | Driver version |  Minimal Campaign version required |  Note |
|:-:|:-:|:-:|:-:|
| 15  |  15 |  Campaign Classic 17.9 | Under Linux: Queries with timestamp may fail (fixed in build 8937 for 18.4 and 8977 for 18.10) In debug mode, warnings relative to bad memory usage in the driver may occur. |
| 15  | 16  | Campaign Classic 17.9  | Recommended setup for a Teradata 15 database under Linux.  |
|  16 | 16  | Campaign Classic 18.10 |  Unicode characters with surrogate pairs are not fully handled. Using surrogate characters in data should work. Using surrogates in a filtering condition of a query will not work without this change. |
| 16  |  15 |  Campaign Classic 19.0 |  &nbsp; |

**Based in Latin1**

Versions previous to Adobe Campaign Classic 17.9 only supported Teradata Latin-1 database.

Starting from Adobe Campaign Classic 17.9, we now support by default Teradata database in Unicode.

Customers with a Latin-1 Teradata database migrating to a recent Campaign Classic release will have to add the parameter APICharSize=1 in the options of the external account.
-->

### Användarkonfiguration {#user-configuration}

Följande rättigheter krävs för den externa databasen: skapa/släppa/köra anpassade procedurer, skapa/släppa/infoga/markera tabeller. Du kan också behöva skapa användarlägesfunktioner om du vill använda funktionen md5 och sha2 i din Adobe Campaign-instans.

Kontrollera att du har konfigurerat rätt tidszon. Den ska matcha vad som kommer att anges i det externa konto som skapas i Adobe Campaign-instansen.

Adobe Campaign kommer inte att ange skyddsläge (reserv) för objekten som skapas i databasen. Du kan behöva ange ett standardvärde för den användare som Adobe Campaign ska använda för att ansluta till Teradata-databasen med följande fråga:

| inaktivera standardåtergång |
| :-: |
| ```MODIFY USER $login$ AS NO FALLBACK;``` |

### MD5-installation {#md5-installation}

Om du vill använda md5-funktioner i din Adobe Campaign-instans måste du installera funktionen för användarläge i din Teradata-databas från den här [page](https://downloads.teradata.com/download/extensibility/md5-message-digest-udf) (md5_20080530.zip).

SHA1 för den hämtade filen är som följer 65cc0bb6935f72fcd84fef1ebcd64c00115dfd1e.

Så här installerar du md5:

1. Zippa upp filen md5_20080530.zip.

1. Gå till katalogen md5/src.

1. Anslut till din Teradata-databas med bteq.

1. Kör följande bteq-kommando:

   ```
   .run file = hash_md5.btq
   ```

### SHA2-installation {#sha2-installation}

Om du vill använda sha2-funktioner i din Adobe Campaign-instans måste du installera funktionen för användarläge i din Teradata-databas från den här [page](https://github.com/akuroda/teradata-udf-sha2/archive/v1.0.zip) (teradata-udf-sha2-1.0.zip).

Sha1 för den hämtade filen är som följer e87438d37424836358bd3902cf1adeb629349780.

Så här installerar du SHA2:

1. Zippa upp filen teradata-udf-sha2-1.0.zip.

1. Gå till katalogen teradata-udf-sha2-1.0/src.

1. Anslut till din Teradata-databas med bteq.

1. Kör följande två bteq-kommandon:

   ```
   .run file = hash_sha256.sql
   .run file = hash_sha512.sql
   ```

### UDF_UTF16TO8-installation {#UDF-UTF16TO8-installation}

Om du vill använda funktionerna udf_utf16to8 i din Adobe Campaign-instans måste du installera funktionen för användarläge i din Teradata-databas från **Verktygspaket för Unicode-teradata** i [page](https://downloads.teradata.com/download/tools/unicode-tool-kit) (utk_release1.7.0.0.zip).

SHA1 för den hämtade filen är som följer e58235f434f52c71316a577cb48e20b97d24f470.

Så här installerar du udf_utf16to8:

1. Zippa upp filen utk_release1.7.0.0.zip.

1. Leta efter filen udf_utf16to8.o i de extraherade filerna och navigera till katalogen som innehåller filen. Den ska ha namnet utk_release1.7.0.0/utk_release1.7.0.0/04 TranslationUDFs/01 Teradata UDFs/suselinux-x8664/udf_installation/.

1. Anslut till din Teradata-databas med bteq.

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
   ```

## Kampanjserverkonfiguration för Linux {#campaign-server-linux}

Följande krävs för drivrutinsinstallationen:

* ODBC-drivrutin för teradata, som finns i detta [page](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)

* Teradata Tools and Utilities (används för massinläsning), som finns i detta [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-linux-installation-package-0)

Filnamn och SHA1:

* tdodbc1620__linux_indep.16.20.00.00-1.tar.gz 121fdd978b56fe1304fc5cb7819741b0847f4 4fd

* TeradataToolsAndUtilitiesBase__linux_indep.16.20.01.00.tar.gz b 29d0af5ffd8dcf68a9dbbaa6f8639387b19c563

Om det inte finns något paket för din Linux-distribution kan du installera enligt anvisningarna på en CentOS 7 (t.ex. med docker) och sedan kopiera innehållet i /opt/teradata på din Adobe Campaign-server.

### Installation av ODBC-drivrutin {#odbc-installation}

Så här installerar du ODBC-drivrutinen:

1. Extrahera filen tdodbc1620__linux_indep.16.20.00.00-1.tar.gz.

1. Gå till katalogen tdodbc1620.

1. Du kan behöva åtgärda installationsskriptet:

   ```
   "sed -i s/16.10/16.20/ setup_wrapper.sh".
   ```

1. Kör setup_wrapper.sh.

### Installation av verktyg och verktyg för teradata {#teradata-tools-installation}

Så här installerar du verktyg:

1. Extrahera filen TeradataToolsAndUtilitiesBase_linux_indep.16.20.01.00.tar.gz.

1. Gå till katalogen TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tdicu.

1. Kör setup_wrapper.sh.

1. Gå till katalogen TeradataToolsAndUtilitiesBase/Linux/i386-x8664/cliv2.

1. Kör setup_wrapper.sh.

1. Gå till katalogen TeradataToolsAndUtilitiesBase/Linux/i386-x8664/tptbase.

1. Kör setup_wrapper.sh.

1. En libtelapi.so-fil ska vara tillgänglig i /opt/teradata/client/16.20/lib64.

## Kampanjserverkonfiguration för Windows {#campaign-server-windows}

Du måste först ladda ned Teradata Tools and Utilities för Windows. Du kan hämta den här [page](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package)

Installera ODBC-drivrutinen och Teradata Parallel Transporter Base. Den installerar telapi.dll som används för massinläsning på Teradata-databasen.

Kontrollera att sökvägen till drivrutinen och verktygen finns i variabeln PATH som ingen server kommer att ha under körningen. Som standard är sökvägen C:\Program Files (x86)\Teradata\Client\15.10\bin on Windows 32 bits or C:\Program Files\Teradata\Client\15.10\bin on 64 bit).

## Tidszon {#timezone}

Teradata använder ett namn på en tidszon som inte är standard finns i listan på [Teradata](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/oGKvgl7gCeBMTGrp59BnwA). Adobe Campaign kommer att försöka konvertera tidszonen som anges i den externa konfigurationen till något som Teradatan förstår. Om ingen korrespondens hittas kommer tidszonen GMT+X (eller GMT-X) som stängs att hittas för sessionen, med en varning i loggen.

Konverteringen är klar med läsningen av en fil med namnet teradata_timezone.txt som ska finnas i följande datakatalog: /usr/local/neolane/nl6/datakit under linux. Om du redigerar den här filen måste du kontakta Adobe Campaign-teamet för att ändra källkoden, annars skrivs den här filen över vid nästa Campaign-uppdatering.

Tidszonen som används för att ansluta anges när en lserver körs med växeln -verbose, till exempel:

```
15:04:04 >   ODB-240007 Teradata: will use 'Europe Central' as session time zone.
```

Om den tidszon som används inte är korrekt kan ett alternativ med namnet&quot;TimeZoneName&quot; läggas till på det externa kontot. I så fall använder du Teradata Value, till exempel&quot;TimeZoneName=Europe Central&quot;.

När massinläsning eller&quot;snabb inläsning&quot; används i Teradata-dokument kan Campaign inte ange tidszonen. Därför rekommenderar vi att du anger standardtidszonen för användaren som ska användas i Campaign för att ansluta:

```
MODIFY USER $login$ AS TIME ZONE = 'Europe Central';
```
