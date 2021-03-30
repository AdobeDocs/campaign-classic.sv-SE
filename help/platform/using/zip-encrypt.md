---
solution: Campaign Classic
product: campaign
title: Zippa eller kryptera en fil
description: Lär dig hur du komprimerar eller krypterar en fil i Campaign Classic innan du bearbetar den.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 3%

---


# Zippa eller kryptera en fil {#zipping-or-encrypting-a-file}

Med Adobe Campaign kan du exportera komprimerade eller krypterade filer. När du definierar en export via en **[!UICONTROL Data extraction (file)]**-aktivitet kan du definiera en efterbearbetning för att komprimera eller kryptera filen.

Så här kan du göra:

1. Installera ett GPG-nyckelpar för instansen med [Kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

   >[!NOTE]
   >
   >Kontrollpanelen är tillgänglig för alla administratörsanvändare. Anvisningar om hur du beviljar administratörsåtkomst till en användare finns på [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
   >
   >Observera att din instans måste vara värd på AWS och uppgraderas med den senaste [Gold Standard](../../rn/using/gs-overview.md)-versionen eller den [senaste GA-versionen (21.1)](../../rn/using/latest-release.md). Lär dig hur du kontrollerar din version i [det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Om du vill kontrollera om din instans finns på AWS följer du stegen som beskrivs i [den här sidan](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

1. Om din installation av Adobe Campaign ligger hos Adobe kontaktar du [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att få nödvändiga verktyg installerade på servern.
1. Om du har en installation av Adobe Campaign installerad installerar du verktyget som du vill använda (till exempel: GPG, GZIP) och nödvändiga nycklar (krypteringsnyckel) på programservern.

Du kan sedan använda kommandon eller kod på fliken **[!UICONTROL Script]** för aktiviteten eller i en **[!UICONTROL JavaScript code]**-aktivitet. Ett exempel visas i användningsexemplet nedan.

**Relaterade ämnen:**

* [Zippa upp eller dekryptera en fil före bearbetning](../../platform/using/unzip-decrypt.md)
* [Dataextraheringsaktivitet](../../workflow/using/extraction--file-.md).

## Användningsfall: Kryptera och exportera data med en tangent som är installerad på Kontrollpanelen {#use-case-gpg-encrypt}

I det här fallet skapar vi ett arbetsflöde för att kryptera och exportera data med en nyckel som installeras på Kontrollpanelen.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#video)

Så här utför du det här användningsfallet:

1. Generera ett GPG-nyckelpar (public/private) med ett GPG-verktyg och installera sedan den offentliga nyckeln på Kontrollpanelen. Detaljerade steg finns i [dokumentationen till kontrollpanelen](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data).

1. Bygg ett arbetsflöde i Campaign Classic för att exportera data och kryptera dem med den privata nyckel som har installerats via Kontrollpanelen. För att göra detta ska vi skapa ett arbetsflöde enligt följande:

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** aktivitet: I det här exemplet vill vi köra en fråga för att rikta data från den databas som vi vill exportera.
   * **[!UICONTROL Data extraction (file)]** aktivitet: Extraherar data till en fil.
   * **[!UICONTROL JavaScript code]** aktivitet: Krypterar de data som ska extraheras.
   * **[!UICONTROL File transfer]** aktivitet: Skickar data till en extern källa (i det här exemplet en SFTP-server).

1. Konfigurera aktiviteten **[!UICONTROL Query]** för att ange önskade data från databasen som mål. Mer information om detta finns i [det här avsnittet](../../workflow/using/query.md).

1. Öppna aktiviteten **[!UICONTROL Data extraction (file)]** och konfigurera den efter dina behov. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/extraction--file-.md).

   ![](assets/gpg-data-extraction.png)

1. Öppna aktiviteten **[!UICONTROL JavaScript code]** och kopiera och klistra sedan in kommandot nedan för att kryptera de data som ska extraheras.

   >[!IMPORTANT]
   >
   >Se till att du ersätter värdet **fingertryck** från kommandot med fingeravtrycket för den offentliga nyckeln som är installerad på kontrollpanelen.

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

1. Öppna aktiviteten **[!UICONTROL File transfer]** och ange sedan den SFTP-server som du vill skicka filen till. Globala koncept för hur du konfigurerar aktiviteten finns i [det här avsnittet](../../workflow/using/file-transfer.md).

   ![](assets/gpg-file-transfer.png)

1. Du kan nu köra arbetsflödet. När den har körts exporteras datamål som omfattas av frågan till SFTP-servern till en krypterad GPG-fil.

## Självstudievideo {#video}

I den här videon visas hur du använder en GPG-nyckel för att kryptera data som även finns i

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
