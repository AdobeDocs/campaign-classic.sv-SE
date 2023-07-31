---
product: campaign
title: Zippa eller kryptera en fil
description: Lär dig zippa eller kryptera en fil i Campaign innan du bearbetar den
feature: Data Management
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 7%

---

# Zippa eller kryptera en fil {#zipping-or-encrypting-a-file}



Med Adobe Campaign kan du exportera komprimerade eller krypterade filer. När du definierar en export via en **[!UICONTROL Data extraction (file)]** kan du definiera en efterbearbetning för att komprimera eller kryptera filen.

Så här kan du göra:

1. Installera ett GPG-nyckelpar för instansen med [Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Kontrollpanelen är begränsad till administratörsanvändare och endast tillgänglig för vissa Campaign-versioner. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html)
   >

1. Om din installation av Adobe Campaign ligger hos Adobe kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att ha nödvändiga verktyg installerade på servern.
1. Om du har installerat Adobe Campaign lokalt installerar du det verktyg du vill använda (till exempel GPG, GZIP) samt de nödvändiga nycklarna (krypteringsnyckeln) på programservern.

Du kan sedan använda kommandon eller kod i **[!UICONTROL Script]** aktivitetens flik eller i en **[!UICONTROL JavaScript code]** aktivitet. Ett exempel visas i användningsexemplet nedan.

**Relaterade ämnen:**

* [Zippa upp eller dekryptera en fil före bearbetning](../../platform/using/unzip-decrypt.md)
* [Aktivitet för dataextrahering (fil)](../../workflow/using/extraction--file-.md).

## Användningsfall: Kryptera och exportera data med en tangent som är installerad på Kontrollpanelen {#use-case-gpg-encrypt}

I det här fallet skapar vi ett arbetsflöde för att kryptera och exportera data med en nyckel som installeras på Kontrollpanelen.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#video)

Så här utför du det här användningsfallet:

1. Generera ett GPG-nyckelpar (public/private) med ett GPG-verktyg och installera sedan den offentliga nyckeln på Kontrollpanelen. Detaljerade steg finns i [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. Bygg ett arbetsflöde i Campaign Classic för att exportera data och kryptera dem med den privata nyckel som har installerats via Kontrollpanelen. För att göra detta ska vi skapa ett arbetsflöde enligt följande:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** aktivitet: I det här exemplet vill vi köra en fråga som mål för data från den databas som vi vill exportera.
   * **[!UICONTROL Data extraction (file)]** aktivitet: Extraherar data till en fil.
   * **[!UICONTROL JavaScript code]** aktivitet: Krypterar de data som ska extraheras.
   * **[!UICONTROL File transfer]** aktivitet: Skickar data till en extern källa (i detta exempel en SFTP-server).

1. Konfigurera **[!UICONTROL Query]** -aktivitet för att ange önskade data från databasen som mål. Mer information om detta finns i [det här avsnittet](../../workflow/using/query.md).

1. Öppna **[!UICONTROL Data extraction (file)]** och sedan konfigurera den efter dina behov. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Öppna **[!UICONTROL JavaScript code]** och sedan kopiera och klistra in kommandot nedan för att kryptera de data som ska extraheras.

   >[!IMPORTANT]
   >
   >Se till att du ersätter **fingeravtryck** värdet från kommandot med fingeravtrycket på den offentliga nyckeln som är installerad på kontrollpanelen.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. Öppna **[!UICONTROL File transfer]** anger du sedan den SFTP-server till vilken du vill skicka filen. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Du kan nu köra arbetsflödet. När den har körts exporteras datamål som omfattas av frågan till SFTP-servern till en krypterad GPG-fil.

## Självstudievideo {#video}

I den här videon visas hur du använder en GPG-nyckel för att kryptera data som även finns i

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Det finns fler instruktionsvideor för Campaign Classic [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
