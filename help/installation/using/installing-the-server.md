---
title: Installera servern
seo-title: Installera servern
description: Installera servern
seo-description: null
page-status-flag: never-activated
uuid: 02534211-c267-490d-b9c1-78f56f1284e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1510fd9-995b-46c6-8d57-e1fe3999235e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Installera servern{#installing-the-server}

## Köra installationsprogrammet {#executing-the-installation-program}

Installera 32-bitarsversionen av Adobe Campaign för en 32-bitarsplattform för Windows. Installera 64-bitarsversionen av Adobe Campaign för en 64-bitarsplattform för Windows.

Installationsstegen för Adobe Campaign-servern är följande:

1. Kör filen **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Välj installationstyp.

   ![](assets/s_ncs_install_installer_01a.png)

   Det finns flera installationstyper:

   * **[!UICONTROL Installation of an application server]** : Installera programservern Adobe Campaign och klientkonsolen.
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

   När installationen är klar startar du Adobe Campaign för att skapa konfigurationsfilerna. Se [Första starten av servern](#first-start-up-of-the-server).

## Sammanfattad installationstestning {#summary-installation-testing}

Du kan testa den inledande installationen med följande kommando:

```
nlserver pdump
```

Om Adobe Campaign inte startas är svaret:

```
No task
```

## Serverns första start {#first-start-up-of-the-server}

När installationstestet är klart öppnar du en kommandotolk via **[!UICONTROL Start > Programs > Adobe Campaign]** menyn och anger följande kommando:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

Filerna i installationskatalogen används för att konfigurera servermodulerna för Adobe Campaign.

Följande information visas:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Tryck på **Ctrl+C** för att avbryta processen och ange följande kommando:

```
nlserver start web
```

Följande information visas:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Om du vill stoppa den anger du:

```
nlserver stop web
```

Följande information visas:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Lösenord för intern identifierare {#password-for-the-internal-identifier}

Adobe Campaign-servern definierar en teknisk inloggning som kallas **intern** som har alla rättigheter för alla instanser. Precis efter installationen har inloggningen inget lösenord. Det är obligatoriskt att definiera en.

Se avsnittet [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Starta Adobe Campaign-tjänster {#starting-adobe-campaign-services}

Om du vill starta Adobe Campaign-tjänsterna kan du använda tjänsthanteraren eller ange följande på kommandoraden (med rätt behörighet):

```
net start nlserver6
```

Om du behöver stoppa Adobe Campaign-processerna senare använder du kommandot:

```
net stop nlserver6
```

## Installerar LibraryOffice {#installing-libreoffice}

Hämta LibreOffice, till exempel från [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/) , och följ de vanliga installationsstegen.

Lägg till följande miljövariabel:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 5\"
```

