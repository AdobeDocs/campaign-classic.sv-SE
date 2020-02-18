---
title: Installera paket med Linux
seo-title: Installera paket med Linux
description: Installera paket med Linux
seo-description: null
page-status-flag: never-activated
uuid: d83f00b5-500b-406a-a3d6-ea5639f244f0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
discoiquuid: 04faa9f3-d160-4060-b26e-44333f2faf71
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Installera paket med Linux{#installing-packages-with-linux}

Installera 32-bitarsversionen av Adobe Campaign för en 32-bitarsplattform för Linux. Installera 64-bitarsversionen av Adobe Campaign för en 64-bitarsplattform i Linux.

För var och en av dessa versioner har Adobe Campaign ett paket: **nlserver**. Det här paketet innehåller binärfiler och konfigurationsfiler för en viss version.

Med installationskommandona kan du:

* Kopiera filerna till **/usr/local/neolane**
* Skapa ett Adobe Campaign Linux-konto (och den associerade gruppen) som skapas med **/usr/local/neolane** som hemkatalog
* Skapa ett automatiskt skript **/etc/init.d/nlserver6** för användning vid start, eller skapa en systemenhet (med början 20.1).

>[!NOTE]
>
>Systemanvändaren **neolane** får inte ha skapats innan kommandot kördes. **Neolane** -användaren skapas automatiskt under installationen.
>
>Den **hemkatalog** som är länkad till **neolane** -användaren skapas också automatiskt i **[!UICONTROL /usr/local/neolane]**. Kontrollera att det finns tillräckligt med utrymme på **[!UICONTROL /usr/local]** disken (flera GB).

Du kan köra **ping-`hostname`**kommandot för att kontrollera att servern kan nå sig själv.

## Distribution baserad på RPM-paket {#distribution-based-on-rpm--packages}

Så här installerar du Adobe Campaign på ett RPM-operativsystem (RHEL, CentOS och SUSE):

1. Du måste först skaffa Adobe Campaign-paketet.

   Filen namnges nedan, där **XXXX** är Adobe Campaign-numret:

   * **nlserver6-v7-XXXX-0.x86_64.rpm** för v7.
   * **nlserver6-XXXX-0.x86_64.rpm** för v6.1.
   >[!CAUTION]
   >
   >Se till att du använder rätt filnamn för din version av Adobe Campaign i kommandoexemplen i det här avsnittet.

1. Installera den genom att ansluta som **rot** och köra följande kommando (där **XXXX** är byggnumret för Adobe Campaign):

   ```
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   RPM-filen är beroende av paket som du kan hitta på CentOS/Red Hat-distributioner. Om du inte vill använda vissa av dessa beroenden (till exempel om du vill använda Oracle JDK i stället för OpenJDK), kan du behöva använda alternativet &quot;nodeps&quot; för rpm:

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Kommandot &#39;bc&#39;, som krävs för att köra netreport (se [det här avsnittet](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts) för mer information), är inte tillgängligt som standard för alla Linux-distributioner. Om du vill kontrollera om kommandot är tillgängligt kör du kommandot &#39;which bc&#39;. Annars måste du installera det.

Med CentOS måste du installera paketet bc.x86_64: ansluta som **rot** och kör följande kommando:

```
yum install bc.x86_64
```

## Distribution baserad på APT (Debian) {#distribution-based-on-apt--debian-}

### I Debian 64 bitar {#in-debian-64-bits}

Så här installerar du 64-bitars Adobe Campaign på ett 64-bitars Debian-operativsystem:

1. Du måste först skaffa Adobe Campaign-paketet.

   * **nlserver6-v7-XXXX-linux-2.6-amd64.deb** för v7.
   * **nlserver6-XXXX-linux-2.6-amd64.deb** för v6.1.
   **XXXX** är byggnumret för Adobe Campaign.

   >[!CAUTION]
   >
   >Se till att du använder rätt filnamn för din version av Adobe Campaign i kommandoexemplen i det här avsnittet.

1. Installera den genom att ansluta som **rot** och köra följande kommando (där **XXXX** är byggnumret för Adobe Campaign):

   ```
   dpkg -i nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```

   Om beroenden saknas kör du följande kommando:

   ```
   apt-get install -f
   ```

**Specifikationer för Debian 8/9**

När du installerar Adobe Campaign på ett Debian 8/9-operativsystem bör du tänka på följande:

* OpenSSL måste vara installerat i förväg.
* Installera libicu52 (Debian 8) eller libicu57 (Debian 9), libprotobuf9 (Debian8) och libc-ares2 med följande kommandon:

   ```
   aptitude install libicu52 (Debian 8) libicu57 (Debian 9)
   ```

   ```
   aptitude install libc-ares2
   ```

   ```
   aptitude install libprotobuf9 (only Debian 8)
   ```

* Installera JDK7 med följande kommando:

   ```
   aptitude install openjdk-7-jdk (Debian 8)
   ```

   ```
   aptitude install openjdk-7-jdk (Debian 9)
   ```

## Anpassa parametrar {#personalizing-parameters}

Vissa parametrar kan anpassas via filen **customer.sh**

Om du utför installationen för första gången kanske filen **customer.sh** inte finns på servern än. Skapa den och kontrollera att den har körningsbehörighet. Om så inte är fallet anger du följande kommando:

```
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Serverkodning {#server-encoding}

Som standard startas servern i en iso8859-15-miljö. Servern kan dock startas i en UTF-8-miljö.

>[!CAUTION]
>
>Den här ändringen påverkar interaktionen med filsystemet (filer som läses in via ett arbetsflöde eller ett JavaScript-skript) och filkodningen. Därför rekommenderar vi att du använder standardmiljön.

Om du vill skapa en **japansk instans** måste du emellertid använda en UTF-8-miljö.

Använd följande kommando för att aktivera UTF-8-miljön:

```
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Standardspråk för servern {#default-language-for-the-server}

Installationen stöder både engelska och franska. Engelska används som standard.

Om du vill växla till franska anger du följande kommandon:

```
su - neolane
vi nl6/customer.sh
```

och lägg till följande rad:

```
export neolane_LANG=fra
```

För att systemmeddelanden ska kunna läsas på rätt sätt måste konsolerna finnas på en teckentabell som motsvarar språket (ISO-8859-1 eller -15 för franska).

### Miljövariabler {#environment-variables}

Följande miljövariabler måste definieras korrekt.

Vissa kombinationer kräver ändringar i den miljö som används för att köra Adobe Campaign. En specifik fil (`/usr/local/neolane/nl6/customer.sh`) kan skapas och redigeras för att lägga till ändringar som är specifika för Adobe Campaign-miljön.

Om det behövs kan du redigera filen **customer.sh** med kommandot **vi customer.sh** och anpassa konfigurationen eller lägga till saknade rader:

* För Oracle-klienten:

   ```
   export ORACLE_HOME=/usr/local/instantclient_10_2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
   ```

   Innehållet i miljövariabeln ORACLE_HOME matchar Oracles installationskatalog.

   Innehållet i variabeln TNS_ADMIN måste matcha platsen för filen **DNNAMes.ora** .

* För LibreOffice:

   För att köra Adobe Campaign på en befintlig version av LibraryOffice krävs ytterligare konfigurationer: du måste ange åtkomstsökvägarna till installationskatalogen. Till exempel:

   * Debian

      Standardvärden för OOO_INSTALL_DIR, OOO_BASIS_INSTALL_DIR, OOO_URE_INSTALL_DIR anges. Du kan åsidosätta dem i **customer.sh** om layouten för installationen av LibreOffice är annorlunda:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
      export OOO_INSTALL_DIR=/usr/lib/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib/ure/share/
      ```

   * CentOs

      Använd följande standardvärden:

      ```
      export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
      export OOO_URE_INSTALL_DIR=/usr/lib64/libreoffice/ure/share/
      ```

* För Java Development Kit (JDK):

   Som standard söker konfigurationsskriptet i Adobe Campaign-miljön (`~/nl6/env.sh`) efter JDK-installationskatalogen. Eftersom detta inte är helt tillförlitligt måste du ange vilken JDK som ska användas. För att göra detta kan du tvinga miljövariabeln **JDK_HOME** med följande kommando:

   ```
   export JDK_HOME=/usr/java/jdk1.6.0_07
   ```

   >[!NOTE]
   >
   >Detta är ett exempel. Kontrollera att den JDK-version som används matchar katalognamnet.

   Om du vill testa JDK-konfigurationen loggar du in som Adobe Campaign-systemanvändare med följande kommando:

   ```
   su - neolane
   ```

Du måste starta om Adobe Campaign-tjänsten för att ändringarna ska kunna beaktas.

Följande kommandon används:

```
/etc/init.d/nlserver6 stop
/etc/init.d/nlserver6 start
```

Från och med 20.1 rekommenderar vi att du använder följande kommandon i stället:

```
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client i Linux {#oracle-client-in-linux}

När du använder Oracle med Adobe Campaign måste du konfigurera Oracle-klientlagren i Linux.

* Använd hela klienten
* TNS-definition

   TNS-definitionerna måste läggas till under installationsfasen. Använd följande kommandon om du vill göra det:

   ```
   cd /etc
   mkdir oracle
   cd oracle
   vi tnsnames.ora
   ```

* Miljövariabler

   Se [Miljövariabler](../../installation/using/installing-packages-with-linux.md#environment-variables).

* Konfiguration för Adobe Campaign

   För att slutföra installationen av Oracle-klienten för Adobe Campaign måste du skapa en symbolisk länk för filen **.so** som används av Adobe Campaign.

   Använd följande kommandon om du vill göra det:

   ```
   cd /usr/lib/oracle/10.2.0.4/client/lib
   ln -s libclntsh.so.10.1 libclntsh.so
   ```

Om du råkar ut för ett problem kontrollerar du att paketen i [Oracles installationsdokumentation](https://www.oracle.com/pls/db112/portal.portal_db?selected=11) är korrekt installerade.

## Installationskontroller {#installation-checks}

Du kan nu utföra ett inledande installationstest med följande kommandon:

```
su - neolane
nlserver pdump
```

När Adobe Campaign inte startas är svaret:

```
no task
```

## Serverns första start {#first-start-up-of-the-server}

När installationstestet är klart anger du följande kommando:

```
nlserver web
```

Därefter visas följande information:

```
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Med dessa kommandon kan du skapa konfigurationsfilerna **config-default.xml** och **serverConf.xml** . Alla parametrar som finns i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

Tryck på **Ctrl+C** för att avbryta processen och ange följande kommando:

```
nlserver start web
```

Därefter visas följande information:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Om du vill stoppa den anger du:

```
nlserver stop web
```

Därefter visas följande information:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Lösenord för intern identifierare {#password-for-the-internal-identifier}

Adobe Campaign-servern definierar en teknisk inloggning som kallas **intern** som har alla rättigheter för alla instanser. Precis efter installationen har inloggningen inget lösenord. Det är obligatoriskt att definiera en.

Se avsnittet [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).
