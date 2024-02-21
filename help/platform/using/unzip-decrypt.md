---
product: campaign
title: Zippa upp eller dekryptera en fil
description: Lär dig packa upp eller dekryptera en fil i Campaign innan du bearbetar den
feature: Workflows, Encryption
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 8%

---


# Zippa upp eller dekryptera en fil {#unzipping-or-decrypting-a-file-before-processing}

Med Adobe Campaign kan du importera komprimerade eller krypterade filer. Innan de kan läsas i en [Inläsning av data (fil)](../../workflow/using/data-loading-file.md) kan du definiera en förbearbetning för att packa upp eller dekryptera filen.

>[!IMPORTANT]
>
>Du kan inte dekomprimera zippade filer som är större än 4 GB.

Så här kan du göra:

1. Använd [Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) för att skapa ett nyckelpar för offentlig/privat nyckel för att tillåta fildekryptering.

   >[!NOTE]
   >
   >Kontrollpanelen är tillgänglig för alla administratörsanvändare. Stegen för att bevilja administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv#discover-control-panel).
   >
   >Observera att din instans måste lagras på AWS och uppgraderas med [senaste GA-version](../../rn/using/rn-overview.md). Läs om hur du kontrollerar din version i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Följ stegen på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=sv) för att kontrollera om instanser har AWS som värd.

1. Om du har installerat Adobe Campaign lokalt installerar du det verktyg du vill använda (till exempel GPG, GZIP) samt de nödvändiga nycklarna (krypteringsnyckeln) på programservern.

   Om din installation av Adobe Campaign ligger hos Adobe kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att ha nödvändiga verktyg installerade på servern.

Du kan sedan använda de förbehandlingskommandon du vill i dina arbetsflöden:

1. Lägg till och konfigurera en **[!UICONTROL File transfer]** i ditt arbetsflöde.
1. Lägg till en **[!UICONTROL Data loading (file)]** och definiera filformatet.
1. Markera alternativet **[!UICONTROL Pre-process the file]**.
1. Ange det förbehandlingskommando som du vill använda.
1. Lägg till andra aktiviteter för att hantera data som kommer från filen.
1. Spara och kör arbetsflödet.

Ett exempel visas i användningsexemplet nedan.

**Relaterade ämnen:**

* [Aktivitet för inläsning av data (fil)](../../workflow/using/data-loading-file.md).
* [Zippa eller kryptera en fil](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## Användningsfall: Importera data som krypterats med en nyckel som genererats av Kontrollpanelen {#use-case-gpg-decrypt}

I det här fallet skapar vi ett arbetsflöde för att importera data som har krypterats i ett externt system med hjälp av en nyckel som genererats på Kontrollpanelen.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#video)

Så här utför du det här användningsfallet:

1. Använd Kontrollpanelen för att generera ett nyckelpar (public/private). Detaljerade steg finns i [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * Den offentliga nyckeln delas med det externa systemet, som kommer att använda den för att kryptera data som ska skickas till Campaign.
   * Den privata nyckeln används som Campaign Classic för att dekryptera inkommande krypterade data.

   ![](assets/gpg_generate.png)

1. I det externa systemet använder du den offentliga nyckel som hämtats från Kontrollpanelen för att kryptera de data som ska importeras till Campaign Classicen.

1. Bygg ett arbetsflöde i Campaign Classic för att importera krypterade data och dekryptera dem med den privata nyckel som har installerats via Kontrollpanelen. För att göra detta ska vi skapa ett arbetsflöde enligt följande:

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** aktivitet: Överför filen från en extern källa till Campaign Classic. I det här exemplet vill vi överföra filen från en SFTP-server.
   * **[!UICONTROL Data loading (file)]** aktivitet: Läser in data från filen i databasen och dekrypterar den med den privata nyckel som genereras på Kontrollpanelen.

1. Öppna **[!UICONTROL File transfer]** anger sedan det externa konto som du vill importera den krypterade GPG-filen från.

   ![](assets/gpg_key_transfer.png)

   Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

1. Öppna **[!UICONTROL Data loading (file)]** och sedan konfigurera den efter dina behov. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/data-loading-file.md).

   Lägg till en förbearbetningsfas i aktiviteten för att dekryptera inkommande data. Om du vill göra det väljer du **[!UICONTROL Pre-process the file]** och sedan kopiera och klistra in dekrypteringskommandot i **[!UICONTROL Command]** fält:

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >I det här exemplet använder vi den lösenfras som används som standard av Kontrollpanelen, som är&quot;lösenfras&quot;.
   >
   >Om du redan har installerat GPG-nycklar på din instans via en kundtjänstförfrågan tidigare kan lösenfrasen ha ändrats och vara en annan som standard.

1. Klicka **[!UICONTROL OK]** för att bekräfta aktivitetskonfigurationen.

1. Du kan nu köra arbetsflödet. När dekrypteringen är klar kan du kontrollera i arbetsflödets loggar att den har körts och att data från filen har importerats.

   ![](assets/gpg_run.png)

## Självstudievideo {#video}

I den här videon visas hur du använder en GPG-nyckel för att dekryptera data.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

Det finns fler videor med Campaign Classic om hur man gör [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
