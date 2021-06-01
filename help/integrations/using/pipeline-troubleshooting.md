---
product: campaign
title: Konfigurera integreringen
description: Konfigurera integreringen
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# Felsöka pipelines {#pipeline-troubleshooting}

**Pipelined misslyckas med felet&quot;Ingen aktivitet motsvarar maskens pipelined@&lt;>&quot;**

Din version av Adobe Campaign Classic stöder inte pipeline.

1. Kontrollera om [!DNL pipelined]-elementet finns i konfigurationsfilen. Annars betyder det att det inte stöds.
1. Uppgradera till Campaign 20.3 eller [!DNL Gold Standard] 11.

**Pipelined misslyckas med &#39;&#39; aurait d¢commencer par  `[` ou  `{` (iRc=16384)&quot;**

Alternativet **NmsPipeline_Config** har inte angetts. Det är faktiskt ett JSON-tolkningsfel.
Ställ in JSON-konfigurationen i alternativet **NmsPipeline_Config**. Se&quot;routningsalternativ&quot; på den här sidan.

**Överföringen misslyckas med &quot;ämnet måste vara en giltig organisation eller kund&quot;**

Organisationsidentifierarkonfigurationen är inte giltig.

1. Kontrollera att IMSOrgId har angetts i serverConf.xml.
1. Leta efter ett tomt IMSOrgId i instansens konfigurationsfil som kan åsidosätta standardvärdet. Ta i så fall bort den.
1. Kontrollera att IMSOrgId matchar kundens i Experience Cloud.

**Överföringen misslyckas med &quot;ogiltig nyckel&quot;**

Parametern @authPrivateKey i instanskonfigurationsfilen är felaktig.

1. Kontrollera att authPrivateKey har angetts.
1. Kontrollera att authPrivateKey: börjar med @, slutar med = och är ca 4 000 tecken långt.
1. Leta efter originalnyckeln och kontrollera att den är: i RSA-format, 4096 bitar långt och börjar med —BEGIN RSA PRIVATE KEY—.
   <br> Om det behövs skapar du nyckeln igen och registrerar den på Adobe Analytics.
1. Kontrollera att nyckeln har kodats i samma instans som [!DNL pipelined]. <br>Om det behövs kan du göra om kodningen med JavaScript eller arbetsflödet.

**Överföringen misslyckades med &quot;det går inte att läsa token under autentiseringen&quot;**

Den privata nyckeln har ett ogiltigt format.

1. Kör stegen för nyckelkryptering på den här sidan.
1. Kontrollera att nyckeln är krypterad på samma instans.
1. Kontrollera att authPrivateKey i konfigurationsfilen matchar den genererade nyckeln. <br>Se till att använda OpenSSL för att generera nyckelparet. PuttyGen genererar till exempel inte rätt format.

**Inga utlösare har hämtats**

När [!DNL pipelined]-processen körs och inga utlösare hämtas:

1. Kontrollera att utlösaren är aktiv i Analytics och genererar händelser.
1. Kontrollera att [!DNL pipelined]-processen körs.
1. Sök efter fel i [!DNL pipelined]-loggen.
1. Sök efter fel på statussidan för [!DNL pipelined]. utlösare-ignorerad, utlösare-fel ska vara noll.
1. Kontrollera att utlösarnamnet är konfigurerat i alternativet **[!UICONTROL NmsPipeline_Config]**. Om du är osäker kan du använda alternativet jokertecken.
1. Kontrollera att Analytics har en aktiv utlösare och genererar händelser. Det kan dröja några timmar innan konfigurationen har gjorts i Analytics innan den är aktiv.

**Händelser är inte länkade till en kund**

När vissa händelser inte är länkade till en kund:

1. Kontrollera att avstämningsarbetsflödet körs, om tillämpligt.
1. Kontrollera att händelsen innehåller ett kund-ID.
1. Gör en fråga i kundregistret med användar-ID:t.
1. Kontrollera frekvensen för kundimporten. Nya kunder importeras till Adobe Campaign med ett arbetsflöde.

**Svarstid i händelsebearbetning**

När tidsstämpeln för Analytics är mycket äldre än datumet då händelsen skapades i Campaign.

I allmänhet kan en utlösare ta 15-90 minuter att starta en marknadsföringskampanj. Detta varierar beroende på implementering av datainsamling, inläsning på pipeline, anpassad konfiguration av den definierade utlösaren och arbetsflödet i Adobe Campaign.

1. Kontrollera om [!DNL pipelined]-processen har körts.
1. Leta efter fel i pipelined.log som kan orsaka nya försök. Åtgärda eventuella fel.
1. Kontrollera storleken på kön på statussidan för [!DNL pipelined]. Om köstorleken är stor kan du förbättra JS-prestanda.
1. Eftersom en fördröjning verkar öka med volymen bör du konfigurera utlösarna i Analytics med färre meddelanden.
