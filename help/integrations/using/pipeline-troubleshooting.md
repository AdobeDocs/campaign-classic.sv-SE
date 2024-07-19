---
product: campaign
title: Felsöka pipelines
description: Felsöka pipelines
feature: Triggers
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# Felsöka pipelines {#pipeline-troubleshooting}



**Överföringen misslyckas med felet&quot;Ingen aktivitet motsvarar maskens pipeline@&lt; instans >&quot;**

Din version av Adobe Campaign Classic stöder inte pipeline.

1. Kontrollera om elementet [!DNL pipelined] finns i konfigurationsfilen. Annars betyder det att det inte stöds.
1. Uppgradera till Campaign 20.3 / [!DNL Gold Standard] 11 eller senare.

**Pipelined misslyckas med &#39;&#39; aurait d¢commencer par `[` ou `{` (iRc=16384)&quot;**

Alternativet **NmsPipeline_Config** har inte angetts. Det är faktiskt ett JSON-tolkningsfel.
Ange JSON-konfigurationen i alternativet **NmsPipeline_Config**. Se&quot;routningsalternativ&quot; på den här sidan.

**Överföringen misslyckas med &quot;ämnet måste vara en giltig organisation eller klient&quot;**

Organisations-ID-konfigurationen är inte giltig.

1. Kontrollera att organisations-ID (ImsOrgId) har angetts i serverConf.xml.
1. Kontrollera om ett tomt organisations-ID i instanskonfigurationsfilen kan åsidosätta standardvärdet. Ta i så fall bort den.
1. Kontrollera att organisations-ID:t är korrekt. Information om hur du hittar ditt organisations-ID finns på [den här sidan](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=sv){_blank}

**Överföringen misslyckas med &quot;ogiltig nyckel&quot;**

Parametern @authPrivateKey i instanskonfigurationsfilen är felaktig.

1. Kontrollera att authPrivateKey har angetts.
1. Kontrollera att authPrivateKey: börjar med @, slutar med = och är ca 4 000 tecken långt.
1. Leta efter originalnyckeln och kontrollera att den är: i RSA-format, 4096 bitar lång och börjar med `-----BEGIN RSA PRIVATE KEY-----`.
   <br> Om det behövs skapar du nyckeln igen och registrerar den på Adobe Analytics.
1. Kontrollera att nyckeln har kodats i samma instans som [!DNL pipelined]. <br>Om det behövs kan du göra om kodningen med JavaScript eller arbetsflödet.

**Överföringen misslyckades med &quot;det går inte att läsa token under autentiseringen&quot;**

Den privata nyckeln har ett ogiltigt format.

1. Kör stegen för nyckelkryptering på den här sidan.
1. Kontrollera att nyckeln är krypterad på samma instans.
1. Kontrollera att authPrivateKey i konfigurationsfilen matchar den genererade nyckeln. <br>Använd OpenSSL för att generera nyckelparet. PuttyGen genererar till exempel inte rätt format.

**Överföringen misslyckas med &quot;får inte längre hämta åtkomsttoken&quot;**

Loggarna ska vara som följer:

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

Det här felmeddelandet betyder att autentiseringen har konfigurerats med den gamla Omniture base OAuth. Mer information om hur du uppgraderar din autentisering finns i [Konfigurera Adobe I/O för Adobe Experience Cloud Triggers](../../integrations/using/about-triggers.md#implement) .

**Inga utlösare hämtas**

När processen [!DNL pipelined] körs och inga utlösare hämtas:

1. Kontrollera att utlösaren är aktiv i Analytics och genererar händelser.
1. Kontrollera att processen [!DNL pipelined] körs.
1. Sök efter fel i loggen [!DNL pipelined].
1. Sök efter fel på statussidan för [!DNL pipelined]. utlösare-ignorerad, utlösare-fel ska vara noll.
1. Kontrollera att utlösarnamnet har konfigurerats i alternativet **[!UICONTROL NmsPipeline_Config]**. Om du är osäker kan du använda alternativet jokertecken.
1. Kontrollera att Analytics har en aktiv utlösare och genererar händelser. Det kan dröja några timmar innan konfigurationen har gjorts i Analytics innan den är aktiv.

**Händelser är inte länkade till en kund**

När vissa händelser inte är länkade till en kund:

1. Kontrollera att avstämningsarbetsflödet körs, om tillämpligt.
1. Kontrollera att händelsen innehåller ett kund-ID.
1. Gör en fråga i kundregistret med användar-ID:t.
1. Kontrollera frekvensen för kundimporten. Nya kunder importeras till Adobe Campaign med ett arbetsflöde.

**Latens i händelsebearbetning**

När tidsstämpeln för Analytics är mycket äldre än datumet då händelsen skapades i Campaign.

I allmänhet kan en utlösare ta 15-90 minuter att starta en marknadsföringskampanj. Detta varierar beroende på implementering av datainsamling, inläsning på pipeline, anpassad konfiguration av den definierade utlösaren och arbetsflödet i Adobe Campaign.

1. Kontrollera om processen [!DNL pipelined] har körts.
1. Leta efter fel i pipelined.log som kan orsaka nya försök. Åtgärda felen, om tillämpligt.
1. Kontrollera storleken på kön på statussidan för [!DNL pipelined]. Om köstorleken är stor kan du förbättra JS-prestanda.
1. Eftersom en fördröjning verkar öka med volymen bör du konfigurera utlösarna i Analytics med färre meddelanden.

**Uppgraderar sceninstanser från äldre autentisering till Adobe IO-autentisering**

Om du ändrar integreringsautentiseringen på sceninstansen påverkas inte konfigurationen av produktionsinstansen. Du kan välja att uppgradera din sceninstans och sedan uppdatera autentiseringen till Adobe IO och testa utlösarna på din sceninstans.

Din produktionsinstans kommer att fortsätta använda den gamla autentiseringen och påverkas inte av den här ändringen.
