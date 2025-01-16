---
product: campaign
title: Installera paket med Linux
description: Installera paket med Linux
feature: Installation, Application Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-linux-
exl-id: f41c7510-5ad7-44f3-9485-01f54994b6cb
source-git-commit: ab38c7fd45513c6f7a8ecf7ef8601f0b5a4b5757
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 1%

---

# Installera paket med Linux {#installing-packages-with-linux}

Adobe Campaign levereras med paketet **nlserver** som innehåller binärfiler och konfigurationsfiler för en viss version.

Med installationskommandona kan du:

* Kopiera filerna till **/usr/local/neolane**
* Skapa ett Adobe Campaign Linux-konto (och den associerade gruppen) som skapas med **/usr/local/neolane** som hemkatalog
* Skapa ett automatiskt skript **/etc/init.d/nlserver6** för användning vid start, eller skapa en systemenhet

>[!NOTE]
>
>Systemanvändaren **neolane** får inte ha skapats innan kommandot kördes. Användaren **neolane** skapas automatiskt under installationen.
>
>Katalogen **home** som är länkad till användaren **neolane** skapas också automatiskt i **[!UICONTROL /usr/local/neolane]**. Kontrollera att det finns tillräckligt med utrymme på disken **[!UICONTROL /usr/local]**.

Du kan köra **ping`hostname`**-kommandot för att kontrollera att servern kan nå sig själv.

## Distribution baserad på RPM-paket {#distribution-based-on-rpm--packages}

>[!AVAILABILITY]
>
>Från och med v7.4.1 ingår inte längre XML-bibliotek för RPM Linux-paket i Campaign. Du måste installera dessa bibliotek.
> 

Så här installerar du Adobe Campaign på ett RPM-operativsystem (RHEL, CentOS):

1. Hämta Adobe Campaign-paketet. Filens namn är **nlserver6-v7-XXXX-0.x86_64.rpm**, där **XXXX** är Adobe Campaign build-numret.

   >[!CAUTION]
   >
   >Se till att du använder rätt filnamn för din version av Adobe Campaign i kommandoexemplen i det här avsnittet.

1. Installera den genom att ansluta som **root** och köra följande kommando, där **XXXX** är Adobe Campaign build-nummer:

   ```sql
   yum install nlserver6-v7-XXXX-0.x86_64.rpm
   ```

   RPM-filen är beroende av paket som du kan hitta på CentOS/Red Hat-distributioner. Om du inte vill använda vissa av dessa beroenden (till exempel om du vill använda Oracle-JDK i stället för OpenJDK), kan du behöva använda alternativet &quot;nodeps&quot; för rpm:

   ```sql
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

Observera att de flesta av de angivna beroendena är obligatoriska och att `nlserver` inte kan starta om de inte är installerade (undantaget är öppet, en annan JDK kan installeras).

Kommandot `bc`, som är obligatoriskt för att köra [netreport](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts), är inte tillgängligt som standard för alla Linux-distributioner. Kör kommandot `which bc` om du vill kontrollera om kommandot är tillgängligt. Annars måste du installera det.

Med CentOS måste du installera paketet bc.x86_64: anslut som **root** och köra följande kommando:

```sql
yum install bc.x86_64
```


### RHEL 9 för anläggningsdistributioner {#rhel-9-update}

Om du vill använda DKIM-autentisering (Domain Keys Identified Mail) måste du uppdatera systeminställningarna för Campaign v7.4.1 som lokal kund med RHEL 9.

Gör så här:

1. Kör följande kommando som rot:

```sql
update-crypto-policies --set LEGACY
```

1. Starta om MTA-modulen:

```sql
nlserver restart mta@<instance-name>
```

## Distribution baserad på APT (Debian) {#distribution-based-on-apt--debian-}

Så här installerar du Adobe Campaign på ett 64-bitars Debian-operativsystem:

1. Hämta Adobe Campaign-paketet. Filens namn är **nlserver6-v7-XXXX-linux-2.6-amd64.deb**, där **XXXX** är Adobe Campaign build-numret.

   >[!CAUTION]
   >
   >Se till att du använder rätt filnamn för din version av Adobe Campaign i kommandoexemplen i det här avsnittet.

1. Installera den genom att ansluta som **root** och köra följande kommando, där **XXXX** är Adobe Campaign build-nummer:

   ```sql
   apt install ./nlserver6-v7-XXXX-linux-2.6-amd64.deb
   ```


## Anpassa parametrar {#personalizing-parameters}

Vissa parametrar kan anpassas via filen **customer.sh**

Om du utför installationen för första gången kanske filen **customer.sh** inte finns på servern än.

Skapa den och kontrollera att den har körningsbehörighet. Om så inte är fallet anger du följande kommando:

```sql
chmod +x /usr/local/neolane/nl6/customer.sh
```

### Serverkodning {#server-encoding}

Som standard startas servern i en iso8859-15-miljö. Servern kan dock startas i en UTF-8-miljö.

>[!CAUTION]
>
>Den här ändringen påverkar interaktionen med filsystemet (filer som läses in via ett arbetsflöde eller ett JavaScript-skript) och filkodningen. Därför rekommenderar vi att du använder standardmiljön.

Om du vill skapa en **japansk instans** måste du använda en UTF-8-miljö.

Använd följande kommando för att aktivera UTF-8-miljön:

```sql
mkdir -p /usr/local/neolane/nl6 
touch /usr/local/neolane/nl6/unicodeenv
```

### Miljövariabler {#environment-variables}

Följande miljövariabler måste definieras korrekt.

Vissa kombinationer kräver ändringar i den miljö som används för att köra Adobe Campaign. En specifik fil (`/usr/local/neolane/nl6/customer.sh`) kan skapas och redigeras för att lägga till ändringar som är specifika för Adobe Campaign-miljön.

Om det behövs kan du redigera filen **customer.sh** med kommandot **vi customer.sh** och anpassa konfigurationen eller lägga till saknade rader:

* För Oraclets klient:

  ```sql
  export ORACLE_HOME=/usr/local/instantclient_10_2
  export TNS_ADMIN=/etc/oracle
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
  ```

  Innehållet i miljövariabeln ORACLE_HOME matchar Oraclets installationskatalog.

  Innehållet i variabeln TNS_ADMIN måste matcha platsen för filen **DNNAMes.ora**.

* För LibreOffice:

  Om du vill köra Adobe Campaign på en befintlig version av LibraryOffice krävs ytterligare konfigurationer: du måste ange åtkomstsökvägarna till installationskatalogen. Till exempel:

   * Debian

     Standardvärden för OOO_INSTALL_DIR och OOO_BASIS_INSTALL_DIR anges. Du kan åsidosätta dem i **customer.sh** om layouten för LibreOffice-installationen är annorlunda:

     ```sql
     export OOO_BASIS_INSTALL_DIR=/usr/lib/libreoffice/ 
     export OOO_INSTALL_DIR=/usr/lib/libreoffice/
     ```

   * CentOs

     Använd följande standardvärden:

     ```sql
     export OOO_BASIS_INSTALL_DIR=/usr/lib64/libreoffice/
     export OOO_INSTALL_DIR=/usr/lib64/libreoffice/
     ```

* För Java Development Kit (JDK):

  Som standard söker konfigurationsskriptet i Adobe Campaign-miljön (`~/nl6/env.sh`) efter JDK-installationskatalogen. Vi rekommenderar dock att du anger vilken JDK som ska användas. Om du vill göra det kan du tvinga miljövariabeln **JDK_HOME** med följande kommando:

  ```sql
  export JDK_HOME=/usr/java/jdkX.Y.Z
  ```

  >[!NOTE]
  >
  >Kontrollera att den JDK-version som används matchar katalognamnet.

  Om du vill testa JDK-konfigurationen loggar du in som Adobe Campaign-systemanvändare med följande kommando:

  ```sql
  su - neolane
  ```

Du måste starta om Adobe Campaign-tjänsten för att ändringarna ska kunna beaktas.

Följande kommandon används:

```sql
systemctl stop nlserver
systemctl start nlserver
```

### Oracle Client i Linux {#oracle-client-in-linux}

När du använder Oracle med Adobe Campaign måste du konfigurera Oraclets klientlager i Linux.

* Använd hela klienten
* TNS-definition

  TNS-definitionerna måste läggas till under installationsfasen. Använd följande kommandon om du vill göra det:

  ```sql
  cd /etc
  mkdir oracle
  cd oracle
  vi tnsnames.ora
  ```

* Miljövariabler

  Se [Miljövariabler](#environment-variables).

* Konfiguration för Adobe Campaign

  Om du vill slutföra installationen av Oracle-klienten för Adobe Campaign måste du skapa en symbolisk länk för filen **.so** som används av Adobe Campaign.

  Använd följande kommandon om du vill göra det:

  ```sql
  cd /usr/lib/oracle/10.2.0.4/client/lib
  ln -s libclntsh.so.10.1 libclntsh.so
  ```

Om ett problem uppstår kontrollerar du att paketen i Oraclets installationsdokumentation är korrekt installerade.

## Installationskontroller {#installation-checks}

Du kan nu utföra ett inledande installationstest med följande kommandon:

```sql
su - neolane
nlserver pdump
```

När Adobe Campaign inte startas är svaret:

```sql
no task
```

## Serverns första start {#first-start-up-of-the-server}

När installationstestet är klart anger du följande kommando:

```sql
nlserver web
```

Därefter visas följande information:

```sql
17:11:03 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
17:11:03 >   Web server start (pid=17546, tid=-151316352)...
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
17:11:03 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/config-default.xml' via '/usr/local/[INSTALL]/nl6/conf/models/config-default.xml'
17:11:03 >   Server started
17:11:08 >   Stop requested (pid=17546)
17:11:08 >   Web server stop(pid=17546, tid=-151316352)...
```

Med dessa kommandon kan du skapa konfigurationsfiler för **config-default.xml** och **serverConf.xml** . Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

Tryck på **Ctrl+C** för att stoppa processen och ange följande kommando:

```sql
nlserver start web
```

Därefter visas följande information:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Running task 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') in a new process
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Creating server configuration file '/usr/local/[INSTALL]/nl6/conf/serverConf.xml' via '/usr/local/[INSTALL]/nl6/conf/fra/serverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Om du vill stoppa den anger du:

```sql
nlserver stop web
```

Därefter visas följande information:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Lösenord för intern identifierare {#password-for-the-internal-identifier}

Adobe Campaign-servern definierar en teknisk inloggning med namnet **internal** som har alla rättigheter för alla instanser. Precis efter installationen har inloggningen inget lösenord. Det är obligatoriskt att definiera en.

Läs mer i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).
