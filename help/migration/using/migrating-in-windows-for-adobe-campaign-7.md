---
title: Migrera i Windows för Adobe Campaign 7
seo-title: Migrera i Windows för Adobe Campaign 7
description: Migrera i Windows för Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 74464400-bdd4-42f8-bcbe-ace7095ae4e4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: f459dc07-b7db-4526-b428-852b51c9c00e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# Migrera i Windows för Adobe Campaign 7{#migrating-in-windows-for-adobe-campaign}

## Allmänt förfarande {#general-procedure}

För Windows är migreringsstegen följande:

1. Stoppa tjänster: se [Tjänststopp](#service-stop).
1. Säkerhetskopiera databasen: se [Säkerhetskopiera databasen och den aktuella installationen](#back-up-the-database-and-the-current-installation).
1. Migrera plattformen: se [Distribuera Adobe Campaign v7](#deploying-adobe-campaign-v7).
1. Migrera omdirigeringsservern (IIS): se [Migrera omdirigeringsservern (IIS)](#migrating-the-redirection-server--iis-).
1. Starta om tjänsten: se [Starta om tjänsterna](#re-starting-the-services).
1. Ta bort och rensa tidigare Adobe Campaign-version: se Ta [bort och rensa tidigare versioner](#deleting-and-cleansing-adobe-campaign-previous-version)av Adobe Campaign.

## Tjänststopp {#service-stop}

Stoppa först alla processer med tillgång till databasen på alla berörda datorer.

1. Alla servrar som använder omdirigeringsmodulen (**webmdl** -tjänsten) måste stoppas. Kör följande kommando för IIS:

   ```
   iisreset /stop
   ```

1. Modulen **mta** och dess underordnade moduler (**mtachild**) måste stoppas med följande kommandon:

   ```
   nlserver stop mta@<instance name>
   nlserver stop mtachild@<instance name>
   ```

1. Stoppa Adobe Campaign-tjänsterna på alla servrar. Logga in med administratörsbehörighet och kör följande kommando:

   ```
   net stop nlserver6
   ```

   Om du migrerar från v5.11 kör du följande kommando:

   ```
   net stop nlserver5
   ```

1. Kontrollera att Adobe Campaign-tjänsterna har stoppats korrekt för varje server. Logga in med administratörsbehörighet och kör följande kommando:

   ```
   tasklist /FI "IMAGENAME eq nlserver*"
   ```

   Listan över aktiva processer tillsammans med deras ID (PID) visas.

   ```
   Image Name                     PID Session Name        Session#    Mem Usage
   ========================= ======== ================ =========== ============
   nlserver.exe                  3192 Console                    1     13,108 K
   ```

1. Om en eller flera Adobe Campaign-processer fortfarande är aktiva eller blockerade efter några minuter ska du döda dem. Logga in med administratörsbehörighet och kör följande kommando:

   ```
   taskkill /IM nlserver* /T
   ```

1. Om vissa processer fortfarande är aktiva efter några minuter kan du tvinga dem att stängas med kommandot:

   ```
   taskkill /F /IM nlserver* /T
   ```

## Säkerhetskopiera databasen och den aktuella installationen {#back-up-the-database-and-the-current-installation}

Proceduren beror på din tidigare version av Adobe Campaign.

### Migrera från Adobe Campaign v5.11 {#migrating-from-adobe-campaign-v5-11}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Säkerhetskopiera katalogen **Neolane v5** med följande kommando:

   ```
   ren "Neolane v5" "Neolane v5.back"
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar mappen **Neolane v5.back** och sparar den någon annanstans på en säker plats som inte finns på servern.

1. I Windows Service Management Console inaktiverar du den automatiska starten av programservertjänsten 5.11. Du kan också använda följande kommando:

   ```
   sc config nlserver5 start= disabled
   ```

1. Redigera **config-`<instance name>`.xml** (i **Neolane v5). back** folder) för att förhindra **mta**, **wfserver**, **stat** osv. från att starta automatiskt. Ersätt till exempel **autoStart** med **_autoStart**.

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

### Migrera från Adobe Campaign v6.02 {#migrating-from-adobe-campaign-v6-02}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Säkerhetskopiera katalogen **Neolane v6** med följande kommando:

   ```
   ren "Neolane v6" "Neolane v6.back"
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar mappen **Neolane v6.back** och sparar den någon annanstans på en säker plats som inte är servern.

1. Inaktivera automatisk start av 6.02-programservern i Windows Service Manager. Du kan också använda följande kommando:

   ```
   sc config nlserver6 start= disabled
   ```

1. Redigera **config-`<instance name>`.xml** (i **Neolane v6). back** folder) för att förhindra **mta**, **wfserver**, **stat** osv. från att starta automatiskt. Ersätt till exempel **autoStart** med **_autoStart**.

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

### Migrera från Adobe Campaign v6.1 {#migrating-from-adobe-campaign-v6-1}

1. Säkerhetskopiera Adobe Campaign-databasen.
1. Säkerhetskopiera katalogen **Adobe Campaign v6** med följande kommando:

   ```
   ren "Adobe Campaign v6" "Adobe Campaign v6.back"
   ```

   >[!IMPORTANT]
   >
   >Som en försiktighetsåtgärd rekommenderar vi att du packar mappen **Adobe Campaign v6.back** och sparar den någon annanstans på en säker plats som inte är servern.

1. I Windows Service Management Console inaktiverar du den automatiska starten av 6.11-programservertjänsten. Du kan också använda följande kommando:

   ```
   sc config nlserver6 start= disabled
   ```

## Distribuera Adobe Campaign v7 {#deploying-adobe-campaign-v7}

Distributionen av Adobe Campaign omfattar två faser:

* Installerar version 7: den här åtgärden måste utföras på varje server.
* Uppgraderingen: det här kommandot måste startas för varje instans.

Så här distribuerar du Adobe Campaign:

1. Installera den senaste versionen av Adobe Campaign v7 genom att köra installationsfilen **setup.exe** . Mer information om hur du installerar Adobe Campaign-servern i Windows finns i [det här avsnittet](../../installation/using/installing-the-server.md).

   ![](assets/migration_wizard_1_7.png)

   >[!NOTE]
   >
   >Adobe Campaign v7 installeras som standard i katalogen **C:\Program Files\Adobe\Adobe Campaign v7** .

1. Om du vill göra installationsprogrammet för klientkonsolen tillgängligt kopierar du filen **setup-client-7.0.XXXX.exe** till installationskatalogen för Adobe Campaign: **C:\Program Files\Adobe\Adobe Campaign v7\datakit\nl\eng\jsp**.

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
   >Med dessa kommandon kan du skapa det interna filsystemet Adobe Campaign v7: **conf** -katalog (med **filerna config-default.xml** och **serverConf.xml** ), **var** -katalog osv.

1. Kopiera och klistra in (skriv över) konfigurationsfilerna och undermapparna för varje instans via säkerhetskopieringsfilen **Neolane v5.back**, **Neolane v6.back** eller **Adobe Campaign v6.back** (beroende på vilken version du migrerar från - se [det här avsnittet](#back-up-the-database-and-the-current-installation)).
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
   >För det första kommandot ovan ska du inte kopiera filen **config-default.xml** .

1. I **filerna serverConf.xml** och **config-default.xml** i Adobe Campaign v7 använder du de specifika konfigurationer du hade i den tidigare versionen av Adobe Campaign. För **filen serverConf.xml** använder du **filen Neolane v5/conf/serverConf.xml.diff**, **Neolane v6/conf/serverConf.xml.diff** eller **Adobe Campaign v6/conf/serverConf.xml.diff** .

   >[!NOTE]
   >
   >När du rapporterar konfigurationer från Adobe Campaign i tidigare version till Adobe Campaign v7 ska du kontrollera att sökvägarna till de fysiska katalogerna leder till Adobe Campaign v7 (och inte till Neolane v5, Neolane v6 eller Adobe Campaign v6).

1. Läs in konfigurationen för Adobe Campaign v7 igen med följande kommando:

   ```
   nlserver config -reload
   ```

1. Starta efteruppgraderingen med följande kommando:

   ```
   nlserver config -postupgrade -instance:<instance name>
   ```

>[!IMPORTANT]
>
>Starta inte Adobe Campaign-tjänsterna än: vissa ändringar måste göras i IIS.

## Migrerar omdirigeringsservern (IIS) {#migrating-the-redirection-server--iis-}

I det här skedet måste IIS-servern stoppas. Se [servicestopp](#service-stop).

1. Öppna IIS-hanterarkonsolen ( **Internet Information Services)** .
1. Ändra bindningarna (lyssningsportar) för webbplatsen som används för den tidigare versionen av Adobe Campaign:

   * Högerklicka på webbplatsen som användes för den tidigare versionen av Adobe Campaign och välj **[!UICONTROL Edit bindings]**.
   * För varje typ av lyssningsport (**[!UICONTROL http]** och/eller **[!UICONTROL https]**) väljer du önskad rad och klickar på **[!UICONTROL Edit]**.
   * Ange en annan port. Som standard är lyssningsporten 80 för http och 443 för https. Kontrollera att den nya porten är tillgänglig.

      ![](assets/_migration_iis_3_611.png)

      >[!NOTE]
      >
      >Om din IIS-server innehåller flera webbplatser för Adobe Campaign med en avancerad konfiguration (delad port och olika IP-adresser) kontaktar du administratören.

1. Skapa en ny webbplats för Adobe Campaign v7:

   * Högerklicka på **[!UICONTROL Sites]** mappen och välj **[!UICONTROL Add Web Site...]**.

      ![](assets/_migration_iis_4.png)

   * Ange namnet på webbplatsen, till exempel **Adobe Campaign v7** .
   * Åtkomstsökvägen till webbplatsens baskatalog används inte, men fältet måste anges **[!UICONTROL Physical access path]** . Ange standardåtkomstsökvägen för IIS: **C:\inetpub\wwwroot**.
   * Klicka på knappen **[!UICONTROL Connect as...]** som och kontrollera att **[!UICONTROL Application user]** alternativet är markerat.
   * Du kan lämna standardvärdena i fälten **[!UICONTROL IP address]** och **[!UICONTROL Port]** . Om du vill använda andra värden kontrollerar du att IP-adressen och/eller porten är tillgängliga.
   * Markera **[!UICONTROL Start Web site immediately]** rutan.

      ![](assets/_migration_iis_5_7.png)

1. Kör skriptet iis_ **neolane_setup.vbs** för att automatiskt konfigurera resurserna som används av Adobe Campaign-servern i den virtuella katalog som skapades tidigare.

   * Den här filen finns i **`[Adobe Campaign v7]`\tomcat-7\conf file **, där **`[Adobe Campaign v7]`**finns åtkomstsökvägen till installationskatalogen för Adobe Campaign. Kommandot för att köra skriptet är följande (för administratörer):

      ```
      cd C:\Program Files (x86)\Adobe Campaign\Adobe Campaign v7\tomcat-7\conf
      cscript iis_neolane_setup.vbs
      ```

   * Klicka **[!UICONTROL OK]** för att bekräfta skriptkörningen.

      ![](assets/s_ncs_install_iis7_parameters_step2_7.png)

   * Ange numret på den webbplats som tidigare skapats för Adobe Campaign v7 och klicka på **[!UICONTROL OK]**.

      ![](assets/s_ncs_install_iis7_parameters_step3_7.png)

   * Ett bekräftelsemeddelande ska visas:

      ![](assets/s_ncs_install_iis7_parameters_step7_7.png)

   * Kontrollera att webbplatskonfigurationen är korrekt konfigurerad med resurserna för Adobe Campaign på fliken **[!UICONTROL Content view]** :

      ![](assets/s_ncs_install_iis7_parameters_step6_7.png)

      >[!NOTE]
      >
      >Om trädstrukturen inte visas startar du om IIS.
      >
      >Följande konfigurationssteg för IIS beskrivs i [det här avsnittet](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

## Säkerhetszoner {#security-zones}

Om du migrerar från v6.02 eller tidigare måste du konfigurera dina säkerhetszoner innan du startar tjänster. Mer information finns i [Säkerhet](../../migration/using/general-configurations.md#security).

## Starta om tjänsterna {#re-starting-the-services}

Starta IIS och Adobe Campaign-tjänsterna på var och en av följande servrar:

1. Spårnings- och omdirigeringsserver.
1. Server för mellanpublicering.
1. Marknadsföringsserver.

Innan du går vidare till nästa steg kör du ett fullständigt test av den nya installationen, kontrollerar att det inte finns några regressioner och att allt fungerar genom att följa alla rekommendationer i avsnittet [Allmänna konfigurationer](../../migration/using/general-configurations.md) .

## Ta bort och rensa tidigare version av Adobe Campaign {#deleting-and-cleansing-adobe-campaign-previous-version}

Proceduren beror på din tidigare version av Adobe Campaign.

### Adobe Campaign v5 {#adobe-campaign-v5}

Innan du tar bort och rensar installationen av Adobe Campaign v5 måste du följa följande rekommendationer:

* Få funktionsteamen att göra en fullständig kontroll av den nya installationen.
* Avinstallera bara Adobe Campaign v5 när du är säker på att ingen återställning behövs.

1. I IIS tar du bort webbplatsen **Neolane v5** och sedan programpoolen **Neolane v5** .
1. Byt namn på mappen **Neolane v5.back** till **Neolane v5**.
1. Avinstallera Adobe Campaign v5 med guiden Lägg till/ta bort komponenter.

   ![](assets/migration_wizard_2.png)

1. Ta bort Windows-tjänsten **nlserver5** med följande kommando:

   ```
   sc delete nlserver5
   ```

1. Starta om servern.

### Adobe Campaign v6.02 {#adobe-campaign-v6-02}

Innan du tar bort och rensar installationen av Adobe Campaign v6.02 måste du följa följande rekommendationer:

* Få funktionsteamen att göra en fullständig kontroll av den nya installationen.
* Avinstallera bara Adobe Campaign v6.02 när du är säker på att ingen återställning behövs.

1. I IIS tar du bort webbplatsen **Neolane v6** och sedan programpoolen **Neolane v6** .
1. Byt namn på mappen **Neolane v6.back** till **Neolane v6**.
1. Avinstallera Adobe Campaign v6.02 med guiden Lägg till/ta bort komponenter.

   ![](assets/migration_wizard_2.png)

1. Starta om servern.

### Adobe Campaign v6.1 {#adobe-campaign-v6-1}

Innan du tar bort och rensar installationen av Adobe Campaign v6 måste du följa följande rekommendationer:

* Få funktionsteamen att göra en fullständig kontroll av den nya installationen.
* Avinstallera bara Adobe Campaign v6 när du är säker på att ingen återställning behövs.

1. I IIS tar du bort webbplatsen **Adobe Campaign v6** och sedan programpoolen **Adobe Campaign v6** .
1. Byt namn på mappen **Adobe Campaign v6.back** till **Adobe Campaign v6**.
1. Avinstallera Adobe Campaign v6 med guiden för att lägga till/ta bort komponenter.

   ![](assets/migration_wizard_2.png)

1. Starta om servern.

