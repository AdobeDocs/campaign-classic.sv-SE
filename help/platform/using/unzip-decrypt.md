---
solution: Campaign Classic
product: campaign
title: Zippa upp eller dekryptera en fil
description: Lär dig hur du packar upp eller dekrypterar en fil i Campaign Classic innan du bearbetar den.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 1cde12d33551206da12e03a7e8deb198d427ab3a
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 2%

---


# Zippa upp eller dekryptera en fil {#unzipping-or-decrypting-a-file-before-processing}

Med Adobe Campaign kan du importera komprimerade eller krypterade filer. Innan de kan läsas in i en [datainläsning (fil)](../../workflow/using/data-loading--file-.md)-aktivitet kan du definiera en förbearbetning för att packa upp eller dekryptera filen.

Så här kan du göra:

1. Använd [Kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) för att generera ett nyckelpar för offentlig/privat nyckel.

   >[!NOTE]
   >
   >Kontrollpanelen är tillgänglig för alla kunder som har AWS som värd (med undantag för kunder som har sina marknadsföringsinstanser på plats).

1. Om din installation av Adobe Campaign ligger hos Adobe kontaktar du Adobe kundtjänst för att få de verktyg som behövs installerade på servern.
1. Om du har en installation av Adobe Campaign installerad installerar du verktyget som du vill använda (till exempel: GPG, GZIP) och nödvändiga nycklar (krypteringsnyckel) på programservern.

Du kan sedan använda de förbehandlingskommandon du vill i dina arbetsflöden:

1. Lägg till och konfigurera en **[!UICONTROL File transfer]**-aktivitet i ditt arbetsflöde.
1. Lägg till en **[!UICONTROL Data loading (file)]**-aktivitet och definiera filformatet.
1. Markera alternativet **[!UICONTROL Pre-process the file]**.
1. Ange det förbehandlingskommando som du vill använda.
1. Lägg till andra aktiviteter för att hantera data som kommer från filen.
1. Spara och kör arbetsflödet.

Ett exempel visas i användningsexemplet nedan.

**Relaterade ämnen:**

* [Aktivitet](../../workflow/using/data-loading--file-.md) för datainläsning (fil).
* [Zippa eller kryptera en fil](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Användningsfall: Importera data krypterade med en nyckel som genererats av Kontrollpanelen {#use-case-gpg-decrypt}

I det här fallet skapar vi ett arbetsflöde för att importera data som har krypterats i ett externt system med hjälp av en nyckel som genererats på Kontrollpanelen.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#video)

Så här utför du det här användningsfallet:

1. Använd Kontrollpanelen för att generera ett nyckelpar (public/private). Detaljerade steg finns i [dokumentationen till kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * Den offentliga nyckeln delas med det externa systemet, som kommer att använda den för att kryptera data som ska skickas till Campaign.
   * Den privata nyckeln används av Campaign Classic för att dekryptera inkommande krypterade data.

   ![](assets/gpg_generate.png)

1. I det externa systemet använder du den offentliga nyckel som hämtats från Kontrollpanelen för att kryptera de data som ska importeras till Campaign Classic.

1. Bygg ett arbetsflöde i Campaign Classic för att importera krypterade data och dekryptera dem med den privata nyckel som har installerats via Kontrollpanelen. För att göra detta ska vi skapa ett arbetsflöde enligt följande:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** aktivitet: Överför filen från en extern källa till Campaign Classic. I det här exemplet vill vi överföra filen från en SFTP-server.
   * **[!UICONTROL Data loading (file)]** aktivitet: Läser in data från filen i databasen och dekrypterar den med den privata nyckel som genereras på Kontrollpanelen.

1. Öppna aktiviteten **[!UICONTROL File transfer]** och ange sedan det externa konto som du vill importera den krypterade GPG-filen från.

   ![](assets/gpg_key_transfer.png)

   Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

1. Öppna aktiviteten **[!UICONTROL Data loading (file)]** och konfigurera den efter dina behov. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/data-loading--file-.md).

   Lägg till en förbearbetningsfas i aktiviteten för att dekryptera inkommande data. Det gör du genom att markera alternativet **[!UICONTROL Pre-process the file]** och sedan kopiera och klistra in dekrypteringskommandot i fältet **[!UICONTROL Command]**:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >I det här exemplet använder vi den lösenfras som används som standard av Kontrollpanelen, som är&quot;lösenfras&quot;.
   >
   >Om du redan har installerat GPG-nycklar på din instans via en kundtjänstförfrågan tidigare kan lösenfrasen ha ändrats och vara en annan som standard.

1. Klicka på **[!UICONTROL OK]** för att bekräfta aktivitetskonfigurationen.

1. Du kan nu köra arbetsflödet. När dekrypteringen är klar kan du kontrollera i arbetsflödets loggar att den har körts och att data från filen har importerats.

   ![](assets/gpg_run.png)

## Självstudievideo {#video}

I den här videon visas hur du använder en GPG-nyckel för att dekryptera data.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
