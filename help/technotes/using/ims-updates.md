---
product: campaign
title: Technote - Uppdatera miljön för att ansluta till Adobe Campaign med IMS
description: Campaign - IMS-uppdateringar
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 8%

---

# Så här uppdaterar du miljön för att ansluta till Adobe Campaign med IMS {#acc-ims-faq}

![](../../assets/v7-only.svg)

Den 30 juni 2021 har ändringar gjorts i [Adobe Identity Management System](https://helpx.adobe.com/enterprise/using/identity.html) (IMS) Inloggningsfunktioner som kan påverka din förmåga att fortsätta använda Adobe Campaign. Lär dig hur du kan fortsätta använda Adobe Campaign Classic v7 utan avbrott.

## Vad har ändrats?

Adobe Identity Management-tjänsten (IMS) har slutat stödja tidigare Internet Explorer-versioner på **30 juni 2021**. [Läs mer](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe vill bevara IMS-funktionaliteten för alla kunder sedan 30 juni 2021. IMS är en del av säkerhetsramverket som gör att användare kan logga in på klientkonsolen, alltså Adobe Campaign.

För att bevara den här funktionen måste kunderna uppdatera klientkonsolen på varje användares dator och se till att den senaste uppdateringen av din [Windows-version](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), med **Internet Explorer 11** inbyggd installeras på varje användares dator.

## Påverkas du?

Om du ansluter till Campaign [via en Adobe ID](../../integrations/using/about-adobe-id.md), via Adobe Identity Management Service (IMS) och om du kör en äldre version av Campaign än de som listas nedan påverkas du.

Om du redan har uppgraderat men använder en äldre version av Microsoft Internet Explorer måste du uppgradera till Internet Explorer 11.

## Hur uppdaterar jag?

* Som värdkund uppgraderade Adobe redan dina instanser till den nyare versionen.

* Som en lokal/hybridkund måste du uppgradera till en av de nyare versionerna ovan för att kunna dra nytta av den nya klientkonsolen och säkerställa en smidig övergång **före 30 juni 2021**.

   Uppgradera till en av de nya versionerna som listas nedan är obligatorisk:

   * Gold Standard 11. [Läs mer](../../rn/using/gold-standard.md)
   * Campaign 21.1.3-utgåvan. [Läs mer](../../rn/using/latest-release.md)
   * Campaign 20.2.5-utgåvan. [Läs mer](../../rn/using/release--20-2.md)
   * Campaign 20.1.4-utgåvan. [Läs mer](../../rn/using/release--20-1.md)
   * Campaign 19.2.4-utgåvan. [Läs mer](../../rn/using/release--19-2.md)
   * Campaign 19.1.8-utgåvan. [Läs mer](../../rn/using/release--19-1.md)

   Dessa releaser har ett nytt anslutningsprotokoll. Uppgradering är obligatoriskt för både Campaign-servern och klientkonsolen: När alla instanser har uppgraderats måste klientkonsolen uppgraderas till den här versionen och kunna ansluta till Campaign efter **30 juni 2021**.

Dessutom bör du se till att den senaste uppdateringen av [Windows-version](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), med **Internet Explorer 11** inbyggd installeras på varje användares dator.

## Vanliga frågor och svar 

**Hur kontrollerar jag min Campaign-version?**

Lär dig hur du kontrollerar din version [i det här avsnittet](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**Hur kontrollerar jag om jag använder IMS?**

Om du vill kontrollera anslutningsläget kan du:

* Starta Campaign Client Console och få tillgång till dina instansanslutningsinställningar. Om **Anslut till en Adobe ID** om du väljer det här alternativet används Adobe IMS.

   ![](../../integrations/using/assets/ims_1.png)

eller

* Starta Campaign Client Console och kontrollera anslutningsfönstret. Om du ansluter till en Adobe ID, som visas på skärmen nedan, använder du IMS.

   ![](../../integrations/using/assets/adobeID.png)

**Varningsmeddelande för anslutning**

Följande varningsmeddelande visas för användare som behöver uppdatera sin klientkonsol eller använda en gammal version av Microsoft Internet Explorer: **Du måste installera den senaste uppdateringen för Windows och/eller dina Adobe-program.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

Om du ser en sådan varning måste du installera de senaste uppdateringarna av det operativsystem du använder. [Läs mer](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Om du inte har uppdaterat din Internet Explorer-version visas följande meddelande och du kan inte längre ansluta till Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>Om du har frågor om de här ändringarna kan du kontakta [Adobes kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Användbara länkar

* [Uppgradera din miljö](../../production/using/build-upgrade.md)
* [Vanliga frågor och svar om Builduppgradering](../../platform/using/faq-build-upgrade.md)
* [Gör den nya klientkonsolen tillgänglig för användare](../../installation/using/client-console-availability-for-windows.md)
* [Installera Campaign Client Console](../../installation/using/installing-the-client-console.md)
* [Access Adobe Software Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)
* [Ladda ned Campaign Classic build](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
