---
product: campaign
title: Installera servern
description: Installera servern
feature: Installation, Instance Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# Installera servern{#installing-the-server}

## Köra installationsprogrammet {#executing-the-installation-program}

Installera 32-bitarsversionen av Adobe Campaign för en 32-bitarsplattform för Windows. Installera Adobe Campaign 64-bitarsversionen för en 64-bitarsplattform för Windows.

Installationsstegen för Adobe Campaign-servern är följande:

1. Kör filen **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Välj installationstyp.

   ![](assets/s_ncs_install_installer_01a.png)

   Det finns flera installationstyper:

   * **[!UICONTROL Installation of an application server]** : Installera Adobe Campaign programserver och klientkonsolen.
   * **[!UICONTROL Minimal installation (Network)]** : Installation av klientdatorn från nätverket. Endast ett begränsat antal DLL-filer kommer att installeras på datorn, om det behövs, och alla andra komponenter kommer att användas från en nätverksenhet.
   * **[!UICONTROL Installation of a client]** : Installation av nödvändiga komponenter för Adobe Campaign-klienten.
   * **[!UICONTROL Custom installation]** : Användaren väljer vilka element som ska installeras.

   Välj **Installation av en programserver** och gå igenom de olika stegen som visas nedan:

   ![](assets/s_ncs_install_installer_02.png)

1. Välj installationskatalog:

   ![](assets/s_ncs_install_installer_03.png)

1. Klicka **[!UICONTROL Finish]** för att starta installationen:

   ![](assets/s_ncs_install_installer_04.png)

   Förloppsindikatorn visar hur långt installationen är:

   ![](assets/s_ncs_install_installer_05.png)

   När installationen är klar visas ett meddelande om att:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >När serverinstallationen är klar krävs en omstart av servern för att undvika eventuella nätverksproblem.

   När installationen är klar startar du Adobe Campaign för att skapa konfigurationsfilerna. Se [Serverns första start](#first-start-up-of-the-server).

## Sammanfattad installationstestning {#summary-installation-testing}

Du kan testa den inledande installationen med följande kommando:

```sql
nlserver pdump
```

Om Adobe Campaign inte startas är svaret:

```sql
No task
```

## Serverns första start {#first-start-up-of-the-server}

När installationen är klar öppnar du en kommandotolk via **[!UICONTROL Start > Programs > Adobe Campaign]** och ange följande kommando:

```sql
nlserver web
```

Filerna i installationskatalogen används för att konfigurera Adobe Campaign servermoduler.

Följande information visas:

```sql
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Tryck **Ctrl+C** om du vill stoppa processen anger du följande kommando:

```sql
nlserver start web
```

Följande information visas:

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Om du vill stoppa den anger du:

```sql
nlserver stop web
```

Följande information visas:

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Lösenord för intern identifierare {#password-for-the-internal-identifier}

Adobe Campaign-servern definierar en teknisk inloggning som kallas **internal** som har alla rättigheter för alla instanser. Precis efter installationen har inloggningen inget lösenord. Det är obligatoriskt att definiera en.

Läs mer i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Startar Adobe Campaign-tjänster {#starting-adobe-campaign-services}

Om du vill starta Adobe Campaign-tjänsterna kan du använda tjänsthanteraren eller ange följande på kommandoraden (med rätt behörighet):

```sql
net start nlserver6
```

Om du behöver stoppa Adobe Campaign-processerna senare kan du använda kommandot:

```sql
net stop nlserver6
```

## Installerar LibraryOffice {#installing-libreoffice}

Ladda ned LibraryOffice och följ de vanliga installationsstegen.

Lägg till följande miljövariabel:

```sql
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
