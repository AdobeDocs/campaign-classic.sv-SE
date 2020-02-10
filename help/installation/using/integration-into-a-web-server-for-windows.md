---
title: Integrering med en webbserver för Windows
seo-title: Integrering med en webbserver för Windows
description: Integrering med en webbserver för Windows
seo-description: null
page-status-flag: never-activated
uuid: a5042221-44fe-46a6-9322-288b108396e2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: a4f2ae0e-e631-4ab6-934e-8298e4ce6f2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: abddb3cdfcee9e41cab2e7e662d5bfd5d53d6f7e

---


# Integrering med en webbserver för Windows{#integration-into-a-web-server-for-windows}

Adobe Campaign innehåller Apache Tomcat som fungerar som startpunkt i programservern via HTTP (och SOAP).

Du kan använda den här integrerade Tomcat-servern för att hantera HTTP-begäranden.

I detta fall:

* Standardlyssningsporten är 8080. Mer information om hur du ändrar den finns i [Konfigurera Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat).
* Klientkonsolerna ansluter sedan med en URL som [https:// `<computer>`:8080](https://machine:8080).

Av säkerhets- och administrationsskäl rekommenderar vi dock att du använder en dedikerad webbserver som huvudstartpunkt för HTTP-trafik när datorn som kör Adobe Campaign exponeras på Internet och du vill öppna åtkomst till konsolen utanför nätverket.

Med en webbserver kan du också garantera datasekretess med HTTP-protokollet.

På samma sätt måste du använda en webbserver när du vill använda spårningsfunktionen, som bara är tillgänglig som en webbservertilläggsmodul.

>[!NOTE]
>
>Om du inte använder spårningsfunktionen kan du utföra en standardinstallation av Apache eller IIS med en omdirigering till Campaign. Modulen för spårning av webbservertillägg krävs inte.

## Konfigurera IIS-webbservern {#configuring-the-iis-web-server}

Konfigurationsproceduren för en IIS-webbserver är vanligtvis grafisk. Det handlar om att använda en webbplats (som redan har skapats eller väntar på att skapas) för att komma åt resurserna på Adobe Campaign-servern: Java-filer (.jsp), formatmallar (.css, .xsl), bilder (.png), ISAPI DLL för omdirigering osv.

I följande avsnitt beskrivs konfigurationen i IIS 7. Konfigurationen för IIS8 är i stort sett densamma.

Om Web IIS-servern inte redan är installerad på datorn kan du installera den via **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** menyn.

I IIS 7 måste du, förutom standardtjänster, installera ISAPI-tillägg och ISAPI-filter.

![](assets/s_ncs_install_iis7_isapi.png)

### Konfigurationssteg {#configuration-steps}

Använd följande konfigurationssteg:

1. Öppna IIS via **[!UICONTROL Control panel > Administrative tools > Services]** menyn.
1. Skapa och konfigurera platsen (till exempel Adobe Campaign) beroende på parametrarna för nätverket (TCP-anslutningsporten, DNS-värddatorn, IP-adressen).

   ![](assets/s_ncs_install_iis7_add_site.png)

   Du måste ange platsens namn och åtkomstsökvägen till den virtuella katalogen. Eftersom sökvägen för åtkomst till webbplatskatalogen inte används kan du använda följande katalog.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. Med ett **VBS** -skript kan ni automatiskt konfigurera de resurser som används av Adobe Campaign-servern i den virtuella katalog som vi nyss har skapat. Starta programmet genom att dubbelklicka på filen **is_neolane_setup.vbs** som finns i `[INSTALL]\tomcat-7\conf` mappen, där du `[INSTALL]` hittar sökvägen till installationsmappen för Adobe Campaign.

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >Om du har en Windows Server 2008/IIS7-installation måste du vara inloggad som administratör för att köra VBS-skriptet eller köra skriptet som administratör.

   Klicka **[!UICONTROL OK]** om webbservern används som en omdirigeringsserver för spårning, och klicka annars på **[!UICONTROL Cancel]**.

   När flera platser redan har konfigurerats på webbservern visas en mellanliggande sida som anger vilken webbplats som installationen gäller för: Ange numret som är länkat till platsen och klicka på **[!UICONTROL OK]**.

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   Ett bekräftelsemeddelande ska visas:

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. Kontrollera att webbplatsen är korrekt konfigurerad med resurserna för Adobe Campaign på fliken **[!UICONTROL Content View]** :

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   Om trädet inte visas startar du om IIS.

### Hantera rättigheter {#managing-rights}

Du måste sedan konfigurera säkerhetsinställningarna för ISAPI DLL och för resurserna i installationskatalogen för Adobe Campaign.

Gör så här:

1. Markera **[!UICONTROL Features View]** fliken och dubbelklicka på länken **Autentisering** .

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. Kontrollera att anonym åtkomst är aktiverat på fliken **Katalogsäkerhet** på webbplatsen. Klicka vid behov på **[!UICONTROL Edit]** länken för att ändra inställningarna.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### Starta webbservern och testa konfigurationen {#launching-the-web-server-and-testing-the-configuration}

Du måste nu testa om konfigurationen är korrekt.

Gör så här:

1. Starta om IIS-servern med kommandoraden **iisreset** .
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

1. Redigera ISAPI-filtren för Adobe Campaign-webbplatsen genom att klicka på **[!UICONTROL Driver mapping]** -ikonen.
1. Kontrollera innehållet i ISAPI-filtret:

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## Ytterligare konfigurationer {#additional-configurations}

### Ändra överföringsfilens storleksgräns {#changing-the-upload-file-size-limit}

När du konfigurerar IIS-webbservern är en gräns på cirka 28 MB automatiskt för uppsättningsfiler som överförs till servern.

Detta kan påverka Adobe Campaign, särskilt om du vill överföra filer som är större än denna gräns.

Om du till exempel använder en aktivitet av typen **Datainläsning (fil)** i ett arbetsflöde för att importera en 50 MB-fil kommer ett fel att stoppa arbetsflödet från att köras korrekt.

I så fall måste du öka den här gränsen:

1. Öppna IIS via **[!UICONTROL Start > (Control panel) > Administration tools]** menyn.
1. I rutan **Anslutningar** väljer du den webbplats som skapats för din Adobe-installation och dubbelklickar sedan på **Begärandefiltrering** i huvudfönstret.
1. I rutan **Åtgärder** väljer du **Redigera funktionsinställningar** för att kunna redigera värdet i fältet **Maximal tillåten innehållsstorlek (byte)** .

   Om du till exempel vill tillåta att filer på 50 MB överförs måste du ange ett värde på mer än &quot;52428800&quot; byte.

>[!NOTE]
>
>Mer information om det här IIS-alternativet finns i avsnittet &quot;Använda&quot; i den [officiella dokumentationen](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits).

### Konfigurera visning av http-felmeddelande {#configuring-http-error-message-display}

Om du använder en IIS-server av version 6.1 kan genererade felmeddelanden vara svåra att läsa eftersom en oönskad HTML-kod visas i meddelandet.

Använd följande konfiguration för att åtgärda detta och visa felet korrekt:

1. Öppna IIS via **[!UICONTROL Start > Control Panel > Administrative tools]** menyn.
1. I rutan **Anslutningar** väljer du den plats som skapats för Adobe Campaign-installationen och dubbelklickar sedan på **Konfigurationsredigeraren** i huvudfönstret.
1. I listrutan **Avsnitt** väljer du **system.webServer** > **httpErrors**.
1. Välj värdet **PassThrough** på raden **existingResponse** .

![](assets/ins_iis_httperrors.png)

