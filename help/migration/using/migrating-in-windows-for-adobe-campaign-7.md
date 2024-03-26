---
product: campaign
title: Migrera en Microsoft Windows-plattform till Adobe Campaign v7
description: Lär dig hur du migrerar en Microsoft Windows-plattform till Adobe Campaign v7
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
hide: true
hidefromtoc: true
exl-id: 3743d018-3316-4ce3-ae1c-25760aaf5785
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---

# Migrera en Microsoft Windows-plattform till Campaign v7{#migrating-in-windows-for-adobe-campaign}



I en Microsoft Windows-miljö är migreringsstegen följande:

1. Stoppa alla tjänster - [Läs mer](#service-stop).
1. Säkerhetskopiera databasen - [Läs mer](#back-up-the-database).
1. Migrera plattformen - [Läs mer](#deploying-adobe-campaign-v7).
1. Migrera omdirigeringsservern (IIS) - [Läs mer](#migrating-the-redirection-server--iis-).
1. Starta om tjänsten - [Läs mer](#re-starting-the-services).
1. Ta bort och rensa tidigare Adobe Campaign-version - [Läs mer](#deleting-and-cleansing-adobe-campaign-previous-version).

## Tjänststopp {#service-stop}

Stoppa först alla processer med tillgång till databasen på alla berörda datorer.

1. Alla servrar som använder omdirigeringsmodulen (**webmdl** måste stoppas. Kör följande kommando för IIS:

   ```
   iisreset /stop
   ```

1. The **mta** modul och dess underordnade moduler (**mtachild**) måste stoppas med följande kommandon:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Stoppa Adobe Campaign-tjänster på alla servrar. Logga in med administratörsbehörighet och kör följande kommando:

   ```
   net stop nlserver6
   ```

<!--

   If you are migrating from v5.11, run the following command:

   ```
   net stop nlserver5
   ```

-->

1. Kontrollera att Adobe Campaign-tjänsterna är korrekt stoppade för varje server. Logga in med administratörsbehörighet och kör följande kommando:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Listan över aktiva processer tillsammans med deras ID (PID) visas.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Om en eller flera Adobe Campaign-processer fortfarande är aktiva eller blockerade efter några minuter kan du döda dem. Logga in med administratörsbehörighet och kör följande kommando:

   ```
   taskkill /IM nlserver* /T
   ```

1. Om vissa processer fortfarande är aktiva efter några minuter kan du tvinga dem att stängas med kommandot:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Säkerhetskopiera kampanjdatabasen {#back-up-the-database}

Så här säkerhetskopierar du Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v5** directory using the following command:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v5.back** folder and save it elsewhere in a safe location other than the server.

1. In the windows service management console, disable the automatic startup of the 5.11 application server service. You can also use the following command:

   ```
   sc config nlserver5 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v5. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword"  provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

<!--
### For Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Make a backup of the Adobe Campaign database.
1. Make a backup of the **Neolane v6** directory using the following command:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >As a precaution, we recommend that you zip the **Neolane v6.back** folder and save it elsewhere in a safe location other than the server.

1. In the Windows service manager, deactivate the 6.02 application server automatic startup. You can also use the following command:

   ```
   sc config nlserver6 start= disabled
   ```

1. Edit the **config-`<instance name>`.xml** (in the **Neolane v6. back** folder) to prevent the **mta**, **wfserver**, **stat**, etc. services from starting automatically. For instance, replace **autoStart** with **_autoStart**.

   ```
   <?xml version='1.0'?>
   <serverconf>
     <shared>
       <dataStore hosts="myServer*" lang="en_US">
         <dataSource name="default">
           <dbcnx encrypted="1" login="myLogin" password="myPassword" provider="postgresql" server="myServer"/>
         </dataSource>
       </dataStore>
     </shared>
   
     <mta _autoStart="true" statServerAddress="myStatServer"/>
     <stat _autoStart="true"/>
     <wfserver _autoStart="true"/>
     <inMail _autoStart="true"/>
     <sms _autoStart="false"/>
   </serverconf>
   ```

-->

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Säkerhetskopiera **Adobe Campaign v6** katalog med följande kommando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar **Adobe Campaign v6.back** och spara den någon annanstans på en säker plats som inte är servern.

1. I Windows Service Management Console inaktiverar du den automatiska starten av 6.11-programservertjänsten. Du kan också använda följande kommando:

   ```
   sc config nlserver6 start= disabled
   ```

## Distribuera Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Distribuera Adobe Campaign i två steg:

* Installerar build v7: Den här åtgärden måste utföras på varje server.
* Efteruppgraderingen: det här kommandot måste startas för varje instans.

Så här distribuerar du Adobe Campaign:

1. Installera den senaste Adobe Campaign v7-versionen genom att köra **setup.exe** installationsfil. Mer information om hur du installerar Adobe Campaign-servern i Windows finns i [det här avsnittet](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 installeras som standard i **C:\Program Files\Adobe\Adobe Campaign v7** katalog.

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du **setup-client-7.0.XXXX.exe** till Adobe Campaign installationskatalog: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

   >[!NOTE]
   >
   >Mer information om hur du installerar Adobe Campaign i Windows finns i [det här avsnittet](../../installation/using/installing-the-server.md).

1. Starta instansen för första användning med följande kommandon:

   ```
   net start nlserver6-v7
   net stop nlserver6-v7
   ```

   >[!NOTE]
   >
   >Med dessa kommandon kan du skapa det interna filsystemet Adobe Campaign v7: **conf** katalog (med **config-default.xml** och **serverConf.xml** filer), **var** katalog, osv.

1. Kopiera och klistra in (skriv över) konfigurationsfilerna och undermapparna för varje instans via **Neolane v5.back**, **Neolane v6.back** eller **Adobe Campaign v6.back** säkerhetskopieringsfil (beroende på vilken version du migrerar från - se [det här avsnittet](#back-up-the-database-and-the-current-installation)).
1. Kör följande kommandon beroende på vilken version du migrerar från:

   ```
   copy "Neolane v5.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v5.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v5.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Neolane v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Neolane v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Neolane v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   ```
   copy "Adobe Campaign v6.back"/conf/config-<instance name>.xml "Adobe Campaign v7"/conf/
   copy "Adobe Campaign v6.back"/customers/* "Adobe Campaign v7"/customers/
   copy "Adobe Campaign v6.back"/var/* "Adobe Campaign v7"/var/
   ```

   >[!IMPORTANT]
   >
   >För det första kommandot ovan ska du inte kopiera **config-default.xml** -fil.

1. I **serverConf.xml** och **config-default.xml** filer i Adobe Campaign v7, tillämpa de specifika konfigurationer som du hade i en tidigare version av Adobe Campaign. För **serverConf.xml** -filen använder du **Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** eller **Adobe Campaign v6/conf/serverConf.xml.diff** -fil.

   >[!NOTE]
   >
   >När du rapporterar konfigurationer från Adobe Campaign tidigare version till Adobe Campaign v7 ska du kontrollera att sökvägarna till de fysiska katalogerna leder till Adobe Campaign v7 (och inte till Neolane v5, Neolane v6 eller Adobe Campaign v6).

1. Läs in Adobe Campaign v7-konfigurationen igen med följande kommando:

   ```
   nlserver config -reload
   ```

1. Starta efteruppgraderingen med följande kommando:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Starta inte Adobe Campaign-tjänster än: vissa ändringar måste göras i IIS.

## Migrera omdirigeringsservern {#migrating-the-redirection-server--iis-}

I det här skedet måste IIS-servern stoppas. Se [Tjänststopp](#service-stop).

1. Öppna **IIS-hanteraren (Internet Information Services)** konsol.
1. Ändra bindningarna (avlyssningsportar) för webbplatsen som används för Adobe Campaign tidigare version:

   * Högerklicka på webbplatsen som användes för Adobe Campaign tidigare version och välj **[!UICONTROL Edit bindings]**.
   * För varje typ av lyssningsport (**[!UICONTROL http]** och/eller **[!UICONTROL https]**) väljer du lämplig rad och klickar på **[!UICONTROL Edit]**.
   * Ange en annan port. Som standard är lyssningsporten 80 för http och 443 för https. Kontrollera att den nya porten är tillgänglig.

     ![](assets/_migration_iis_3_611.png)

     >[!NOTE]
     >
     >Om din IIS-server innehåller flera webbplatser för Adobe Campaign med en avancerad konfiguration (delad port och olika IP-adresser) kontaktar du administratören.

1. Skapa en ny webbplats för Adobe Campaign v7:

   * Högerklicka på **[!UICONTROL Sites]** mapp och markera **[!UICONTROL Add Web Site...]**.

     ![](assets/_migration_iis_4.png)

   * Ange platsens namn, **Adobe Campaign v7** till exempel.
   * Åtkomstsökvägen till webbplatsens grundläggande katalog används inte, men **[!UICONTROL Physical access path]** fältet måste anges. Ange standardåtkomstsökvägen för IIS: **C:\inetpub\wwwroot**.
   * Klicka på **[!UICONTROL Connect as...]** som och kontrollera att **[!UICONTROL Application user]** är markerat.
   * Du kan lämna standardvärdena i **[!UICONTROL IP address]** och **[!UICONTROL Port]** fält. Om du vill använda andra värden kontrollerar du att IP-adressen och/eller porten är tillgängliga.
   * Kontrollera **[!UICONTROL Start Web site immediately]** box.

     ![](assets/_migration_iis_5_7.png)

1. Kör **iis_neolane_setup.vbs** för att automatiskt konfigurera de resurser som används av Adobe Campaign-servern i den virtuella katalog som tidigare skapats.

   * Den här filen finns i **`[Adobe Campaign v7]`\conf** katalog, var **`[Adobe Campaign v7]`** är åtkomstsökvägen till Adobe Campaign installationskatalog. Kommandot för att köra skriptet är följande (för administratörer):

     ```
     cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\conf
     cscript iis_neolane_setup.vbs
     ```

   * Klicka **[!UICONTROL OK]** för att bekräfta skriptkörning.

     ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Ange numret på den webbplats som tidigare skapats för Adobe Campaign v7 och klicka på **[!UICONTROL OK]**.

     ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Ett bekräftelsemeddelande visas:

     ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * I **[!UICONTROL Content view]** kontrollerar du att webbplatskonfigurationen är korrekt konfigurerad med Adobe Campaign-resurser:

     ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

     >[!NOTE]
     >
     >Om trädstrukturen inte visas startar du om IIS.
     >
     >Följande konfigurationssteg för IIS beskrivs i [det här avsnittet](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

<!--
## Security zones {#security-zones}

If you are migrating from v6.02 or earlier, you must configure your security zones before starting services. [Learn more](../../migration/using/general-configurations.md#security)
-->

## Starta om tjänster {#re-starting-the-services}

Starta IIS- och Adobe Campaign-tjänsterna på följande servrar:

1. Spårnings- och omdirigeringsserver.
1. Server för mellanpublicering.
1. Marknadsföringsserver.

Innan du går vidare till nästa steg kör du ett fullständigt test av den nya installationen, kontrollerar att det inte finns några regressioner och att allt fungerar.

## Ta bort föregående version {#deleting-and-cleansing-adobe-campaign-previous-version}

Så här tar du bort Adobe Campaign v6.1.

<!--

### For Adobe Campaign v5 {#adobe-campaign-v5}

Before you delete and cleanse the Adobe Campaign v5 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v5 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v5** website, then the **Neolane v5** application pool. 
1. Rename the **Neolane v5.back** folder as **Neolane v5**.
1. Uninstall Adobe Campaign v5 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Delete the **nlserver5** Windows service using the following command:

   ```
   sc delete nlserver5
   ```

1. Re-start the server.

### For Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Before you delete and cleanse the Adobe Campaign v6.02 installation, you must apply the following recommendations:

* Get the functional teams to run a full check of the new installation.
* Only uninstall Adobe Campaign v6.02 once you are certain that no rollback is necessary.

1. In IIS, delete the **Neolane v6** website, then the **Neolane v6** application pool. 
1. Rename the **Neolane v6.back** folder as **Neolane v6**.
1. Uninstall Adobe Campaign v6.02 using the Add/remove components wizard. 

   ![](assets/migration_wizard_2.png)

1. Re-start the server.

-->

Innan du tar bort och rensar installationen av Adobe Campaign v6 måste du följa följande rekommendationer:

* Få funktionsteamen att göra en fullständig kontroll av den nya installationen.
* Avinstallera endast Adobe Campaign v6 när du är säker på att ingen återställning behövs.

1. I IIS tar du bort **Adobe Campaign v6** webbplatsen och sedan **Adobe Campaign v6** programpool.
1. Byt namn på **Adobe Campaign v6.back** mapp som **Adobe Campaign v6**.
1. Avinstallera Adobe Campaign v6 med hjälp av guiden för att lägga till/ta bort komponenter.

   ![](assets/migration_wizard_2.png)

1. Starta om servern.
