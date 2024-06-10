---
product: campaign
title: Integrering med en webbserver för Windows
description: Integrering med en webbserver för Windows
feature: Installation, Instance Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 0e88ac270423ad419237264e562a03ab0c42efb5
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 2%

---

# Integrering med en webbserver för Windows {#integration-into-a-web-server-for-windows}

Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP (och SOAP).

Du kan använda den här integrerade Tomcat-servern för att hantera HTTP-begäranden.

I detta fall:

* Standardlyssningsporten är 8080. Om du vill ändra den kan du läsa [det här avsnittet](../../installation/using/configure-tomcat.md).
* Klientkonsolerna ansluter sedan med en URL som ```https:// `<computer>`:8080```.

Av säkerhets- och administrationsskäl rekommenderar vi dock att du använder en dedikerad webbserver som huvudstartpunkt för HTTP-trafik när datorn som kör Adobe Campaign exponeras på Internet och du vill öppna konsolen utanför nätverket.

Med en webbserver kan du också garantera datasekretess med HTTP-protokollet.

På samma sätt måste du använda en webbserver när du vill använda spårningsfunktionen, som bara är tillgänglig som en webbservertilläggsmodul.

## Konfigurera IIS-webbservern {#configuring-the-iis-web-server}

Konfigurationsproceduren för en Microsoft IIS-webbserver är vanligtvis grafisk. Det handlar om att använda en webbplats för att komma åt resurserna på Adobe Campaign-servern: Java-filer (.jsp), formatmallar (.css, .xsl), bilder (.png), ISAPI DLL för omdirigering osv.


### Konfigurationssteg {#configuration-steps}

Så här integrerar du Adobe Campaign med Microsoft IIS-webbserver:

1. Öppna Microsoft IIS.
1. Skapa och konfigurera platsen (t.ex. Adobe Campaign) beroende på parametrarna för nätverket (TCP-anslutningsporten, DNS-värden, IP-adressen).

   Du måste ange platsens namn och åtkomstsökvägen till den virtuella katalogen. Eftersom sökvägen för åtkomst till webbplatskatalogen inte används kan du använda följande katalog.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. A **VBS** Med hjälp av skript kan du automatiskt konfigurera de resurser som används av Adobe Campaign-servern i den virtuella katalog som vi just har skapat. Dubbelklicka på **iis_neolane_setup.vbs** filen som finns i `[INSTALL]\conf` mapp, var `[INSTALL]` är sökvägen till Adobe Campaign installationsmapp.

   >[!NOTE]
   >
   >Du måste vara inloggad som administratör för att kunna köra VBS-skriptet eller köra skriptet som administratör.

   Klicka **[!UICONTROL OK]** om webbservern används som en server för spårningsomdirigering, i annat fall klickar du **[!UICONTROL Cancel]**.

   När flera platser redan har konfigurerats på webbservern visas en mellanliggande sida som anger vilken webbplats som installationen gäller för: ange numret som är länkat till platsen och klicka på **[!UICONTROL OK]**.

1. I **[!UICONTROL Content View]** kontrollerar du att webbplatsen är korrekt konfigurerad med Adobe Campaign resurser:

   Om trädet inte visas startar du om Microsoft IIS.

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

1. Starta om Microsoft IIS-servern med **iisreset** kommandorad.

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
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

Du kan också kontrollera att ISAPI DLL har lästs in korrekt.

Gör så här:

1. Redigera ISAPI-filter för Adobe Campaign webbplats genom att klicka på **[!UICONTROL Driver mapping]** -ikon.
1. Kontrollera innehållet i ISAPI-filtret.


## Ändra överföringsfilens storleksgräns {#changing-the-upload-file-size-limit}

När du konfigurerar IIS-webbservern är en gräns på cirka 28 MB automatiskt för uppsättningsfiler som överförs till servern.

Detta kan påverka Adobe Campaign, särskilt om du vill överföra filer som är större än denna gräns.

Om du till exempel använder en **Inläsning av data (fil)** typaktivitet i ett arbetsflöde för att importera en 50 MB-fil kommer ett fel att stoppa arbetsflödet från att köras korrekt.

I så fall måste du öka den här gränsen.

Mer information om det här Microsoft IIS-alternativet finns i avsnittet &quot;HowTo&quot; i [Microsoft-dokumentation](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}.

