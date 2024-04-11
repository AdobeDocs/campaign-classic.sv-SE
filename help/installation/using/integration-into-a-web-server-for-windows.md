---
product: campaign
title: Integrering med en webbserver för Windows
description: Integrering med en webbserver för Windows
feature: Installation, Instance Settings
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 2%

---

# Integrering med en webbserver för Windows{#integration-into-a-web-server-for-windows}



Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP (och SOAP).

Du kan använda den här integrerade Tomcat-servern för att hantera HTTP-begäranden.

I detta fall:

* Standardlyssningsporten är 8080. Om du vill ändra den kan du läsa [det här avsnittet](../../installation/using/configure-tomcat.md).
* Klientkonsolerna ansluter sedan med en URL som ```https:// `<computer>`:8080```.

Av säkerhets- och administrationsskäl rekommenderar vi dock att du använder en dedikerad webbserver som huvudstartpunkt för HTTP-trafik när datorn som kör Adobe Campaign exponeras på Internet och du vill öppna konsolen utanför nätverket.

Med en webbserver kan du också garantera datasekretess med HTTP-protokollet.

På samma sätt måste du använda en webbserver när du vill använda spårningsfunktionen, som bara är tillgänglig som en webbservertilläggsmodul.

>[!NOTE]
>
>Om du inte använder spårningsfunktionen kan du utföra en standardinstallation av Apache eller IIS med en omdirigering till Campaign. Modulen för spårning av webbservertillägg krävs inte.

## Konfigurera IIS-webbservern {#configuring-the-iis-web-server}

Konfigurationsproceduren för en IIS-webbserver är vanligtvis grafisk. Det handlar om att använda en webbplats (som redan har skapats eller väntar på att skapas) för att komma åt Adobe Campaign-serverns resurser: Java-filer (.jsp), formatmallar (.css, .xsl), bilder (.png), ISAPI DLL för omdirigering osv.

I följande avsnitt beskrivs konfigurationen i IIS 7. Konfigurationen för IIS8 är i stort sett densamma.

Om Web IIS-servern inte redan är installerad på datorn kan du installera den via **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** -menyn.

I IIS 7 måste du, förutom standardtjänster, installera ISAPI-tillägg och ISAPI-filter.

![](assets/s_ncs_install_iis7_isapi.png)

### Konfigurationssteg {#configuration-steps}

Använd följande konfigurationssteg:

1. Öppna IIS via **[!UICONTROL Control panel > Administrative tools > Services]** -menyn.
1. Skapa och konfigurera platsen (t.ex. Adobe Campaign) beroende på parametrarna för nätverket (TCP-anslutningsporten, DNS-värden, IP-adressen).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Du måste ange platsens namn och åtkomstsökvägen till den virtuella katalogen. Eftersom sökvägen för åtkomst till webbplatskatalogen inte används kan du använda följande katalog.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** Med hjälp av skript kan du automatiskt konfigurera de resurser som används av Adobe Campaign-servern i den virtuella katalog som vi just har skapat. Dubbelklicka på **iis_neolane_setup.vbs** filen som finns i `[INSTALL]\conf` mapp, var `[INSTALL]` är sökvägen till Adobe Campaign installationsmapp.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >Om du har en Windows Server 2008/IIS7-installation måste du vara inloggad som administratör för att köra VBS-skriptet eller köra skriptet som administratör.

   Klicka **[!UICONTROL OK]** om webbservern används som en server för spårningsomdirigering, i annat fall klickar du **[!UICONTROL Cancel]**.

   När flera platser redan har konfigurerats på webbservern visas en mellanliggande sida som anger vilken webbplats som installationen gäller för: ange numret som är länkat till platsen och klicka på **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Ett bekräftelsemeddelande visas:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. I **[!UICONTROL Content View]** kontrollerar du att webbplatsen är korrekt konfigurerad med Adobe Campaign resurser:

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Om trädet inte visas startar du om IIS.

### Hantera rättigheter {#managing-rights}

Du måste sedan konfigurera säkerhetsinställningarna för ISAPI DLL och för resurserna i Adobe Campaign installationskatalog.

Gör så här:

1. Välj **[!UICONTROL Features View]** och dubbelklicka på **Autentisering** länk.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. I **Katalogsäkerhet** se till att anonym åtkomst är aktiverat. Klicka vid behov på **[!UICONTROL Edit]** om du vill ändra inställningarna.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Starta webbservern och testa konfigurationen {#launching-the-web-server-and-testing-the-configuration}

Du måste nu testa om konfigurationen är korrekt.

Gör så här:

1. Starta om IIS-servern med **iisreset** kommandorad.

1. Starta tjänsten Adobe Campaign och kontrollera att den körs.

1. Testa spårningsmodulen genom att infoga följande URL i en webbläsare:

   ```
   https://<computer>/r/test
   ```

   Webbläsaren bör visa följande svar:

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

Kör följande kommandorad om du vill testa om det finns en omdirigeringsmodul:

```
nlserver pdump
```

Den måste returnera följande information:

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Du kan också kontrollera att ISAPI DLL har lästs in korrekt.

Gör så här:

1. Redigera ISAPI-filter för Adobe Campaign webbplats genom att klicka på **[!UICONTROL Driver mapping]** -ikon.
1. Kontrollera innehållet i ISAPI-filtret:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Ytterligare konfigurationer {#additional-configurations}

### Ändra överföringsfilens storleksgräns {#changing-the-upload-file-size-limit}

När du konfigurerar IIS-webbservern är en gräns på cirka 28 MB automatiskt för uppsättningsfiler som överförs till servern.

Detta kan påverka Adobe Campaign, särskilt om du vill överföra filer som är större än denna gräns.

Om du till exempel använder en **Inläsning av data (fil)** typaktivitet i ett arbetsflöde för att importera en 50 MB-fil kommer ett fel att stoppa arbetsflödet från att köras korrekt.

I så fall måste du öka den här gränsen:

1. Öppna IIS via **[!UICONTROL Start > (Control panel) > Administration tools]** -menyn.
1. I **Anslutningar** väljer du den plats som du har skapat för Adobe-installationen och dubbelklickar sedan på **Begärandefiltrering** i huvudfönstret.
1. I **Åtgärder** ruta, markera **Redigera funktionsinställningar** för att kunna redigera värdet i **Största tillåtna innehållsstorlek (byte)** fält.

   Om du till exempel vill tillåta att filer på 50 MB överförs måste du ange ett värde på mer än &quot;52428800&quot; byte.

>[!NOTE]
>
>Mer information om det här IIS-alternativet finns i avsnittet &quot;Använda&quot; i [officiell dokumentation](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

