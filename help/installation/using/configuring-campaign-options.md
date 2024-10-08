---
product: campaign
title: Konfigurera kampanjalternativ
description: Lär dig konfigurera Campaign-alternativ
feature: Installation, Application Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: a979cd99-afa7-4ce6-ba0f-9495089cba08
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '3831'
ht-degree: 0%

---

# Lista med alternativ för Campaign Classic{#configuring-campaign-options}

Med noden **[!UICONTROL Administration / Platform / Options]** kan du konfigurera Adobe Campaign-alternativ. Vissa av dem är inbyggda när du installerar Campaign och andra kan läggas till manuellt vid behov. Vilka alternativ som är tillgängliga varierar beroende på vilka paket som installeras med instansen.


>[!CAUTION]
>
>* Alternativ som inte finns med på den här sidan är bara interna och **får inte ändras**.
>
>* Det går endast att ändra eller uppdatera Adobe Campaign-alternativ med expertanvändare.

## Leverans {#delivery}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgDate</span> <br /> </td> 
   <td> Datum för det senaste bredaLogMsg-objektet som har hämtats från leveransinstansen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Deliverability_LastBroadLogMsgSent</span> <br /> </td> 
   <td> Datum för det senaste bredaLogMsg-objektet som skickats till leveransinstansen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_cuid</span> <br /> </td> 
   <td> Identifierare för leveransrapporter. Kontakta supporten för att få din identifierare.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">DmRendering_SeedTargets</span> <br /> </td> 
   <td> Lista med scheman som du vill använda testadresser för inkorgsåtergivning. (elementnamn avgränsas med kommatecken) T.ex.: custom_nms_ecified.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC-e-postadress dit Enhanced MTA skickar en rå kopia av skickade e-postmeddelanden. <br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NMS_ActivateOwnerConfirmation</span> <br /> </td> 
   <td><p> Gör att du kan tillåta den operatör som ansvarar för leveransen att bekräfta sändningen, om en viss operator eller grupp av operatorer har angetts för att starta en leverans i leveransegenskaperna.</p><p> Om du vill göra det aktiverar du alternativet genom att ange "1" som värde. Om du vill inaktivera det här alternativet anger du "0".</p><p> Bekräftelseprocessen för att skicka kommer då att fungera som standard: endast den operator eller grupp av operatorer som har angetts för sändning i leveransegenskaperna (eller en administratör) kommer att kunna bekräfta och utföra sändningen. Se <a href="../../campaign/using/marketing-campaign-deliveries.md#starting-an-online-delivery">det här avsnittet</a>.</p> </td> 
   <tr> 
   <td> <span class="uicontrol">Nms_DefaultRcpSchema</span> <br /> </td> 
   <td> Adobe Campaign använder den globala variabeln "Nms_DefaultRcpSchema" för att öppna en dialogruta med standardmottagardatabasen (nms:receive).<br /> Alternativvärdet måste motsvara namnet på schemat som matchar den externa mottagartabellen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBilling_MainActionThreshold</span> <br /> </td> 
   <td> Minsta antal mottagare för att en leverans ska betraktas som den viktigaste i faktureringsrapporten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_DefaultProvider</span> <br /> </td> 
   <td> Standardleverantör för routningstjänst för de nya mallarna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_LogsPerTransac</span> <br /> </td> 
   <td> Minimal batchstorlek (antal rader) för infogning av bredaLogs under en leveransförberedelse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MaxDelayPerTransac</span> <br /> </td> 
   <td> Tröskelvärde för batchvaraktighet (antal millisekunder) under vilket batchstorleken för infogning av bredaLogs dubbleras under en leveransförberedelse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MidAnalyzeBatchSize</span> <br /> </td> 
   <td> Grupperingsstorlek för leveransdelar vid analys av leveranser från mellanleverantörer.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgValidityDuration</span> <br /> </td> 
   <td> Standardleveransperiod för en leverans (i sekunder).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RegexRules</span> <br /> </td> 
   <td> Reguljära uttryck för normalisering av leveransmeddelanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveBlackList</span> <br /> </td> 
   <td> Om du anger "1" som värde kan du exkludera mottagare som inte längre vill bli kontaktade.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_RemoveDuplicatesRecipients</span> <br /> </td> 
   <td> Om du anger "1" som värde kan du automatiskt ignorera dubbletter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ErrorAddressMasks</span> <br /> </td> 
   <td> Här kan du definiera syntaxen för feladressen som används vid svar på ett meddelande.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_FromAddressMasks</span> <br /> </td> 
   <td> Här kan du definiera syntaxen för den Från-adress som används när ett meddelande skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageServerTimeout</span> <br /> </td> 
   <td> Gör att du kan ange en tidsgräns (i sekunder) för hur du får ett svar från servern när du hämtar en bild som har hämtats från en anpassad URL och bifogats till ett e-postmeddelande. Om det här värdet överskrids kan meddelandet inte skickas. Standardvärdet är 60 sekunder.<br /> </td> 
  </tr> 
 <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxDownloadedImageSize</span> <br /> </td> 
   <td> Här kan du ange den största tillåtna storleken (i byte) för en bild som hämtats från en anpassad URL och bifogats till ett e-postmeddelande. Standardvärdet är 100 000 byte (100 kB). När du skickar ett korrektur och hämtar bilden/bilderna för att bearbeta e-postmeddelandet, om storleken på en bild överskrider det här värdet eller om det finns ett hämtningsproblem, visas ett fel i leveransloggarna och korrekturleveransen misslyckas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRecommendedAttachments</span> <br /> </td> 
   <td> Gör att du kan ange ett maximalt antal bilagor i en e-postmall eller transaktionsmall. Om det här värdet överskrids visas en varning i leveransanalysloggarna eller när du publicerar e-postmallen för transaktioner. Standardvärdet är 1 bifogad fil.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MaxRetry</span> <br /> </td> 
   <td> Maximalt antal återförsök under analys.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_PublishingScript</span> <br /> </td> 
   <td> Publikationsskript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_NoCountBroadLogMsgPush</span> <br /> </td> 
   <td> Inaktivera värdet för broadLogMsg för push-meddelanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDeliveryWizard_ShowDeliveryWeight</span> <br /> </td> 
   <td> Visa meddelandevikten i leveransassistenten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultErrorAddr</span> <br /> </td> 
   <td> E-postadressen för standardfelmeddelandet på instansnivå som används för e-postleverans om den lämnas tom av användaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultFromAddr</span> <br /> </td> 
   <td> Standarde-postadressen 'from' på instansnivå som används för e-postleverans om den lämnas tom av användaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_DefaultReplyToAddr</span> <br /> </td> 
   <td> Standarde-postadressen för svar på instansnivå som används för e-postleverans om den lämnas tom av användaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ExpOrganization</span> <br /> </td> 
   <td> Kundens namn. Används i vissa varningsmeddelanden som visas för mottagarna.<br /> "Du får det här meddelandet eftersom du har varit i kontakt med "Organisation" eller ett anknutet företag. Så här tar du inte längre emot meddelanden från "Organisation"<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_FromName</span> <br /> </td> 
   <td> E-postetiketten 'from' som standard på instansnivå används för e-postleverans om den lämnas tom av användaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_ReplyToName</span> <br /> </td> 
   <td> E-postetiketten för svar på instansnivå som används för e-postleverans om den lämnas tom av användaren.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryCount</span> <br /> </td> 
   <td> Period mellan två försök av ett e-postmeddelande (i sekunder).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsEmail_RetryPeriod</span> <br /> </td> 
   <td> Period med återförsök för e-postmeddelanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsForecast_MsgWeightFormula</span> <br /> </td> 
   <td> Formel som används för att beräkna viktningen för ett meddelande för en preliminär leverans.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInmail_allowListEmails</span> <br /> </td> 
   <td> Lista över auktoriserade e-postadresser för vidarebefordran (från modulen för inkommande e-postbearbetning). Adresserna måste avgränsas med kommatecken (eller * för att tillåta alla). Exempel: xyz@abc.com,pqr@abc.com.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_AESKey</span> <br /> </td> 
   <td> AES-nyckeln som används i serverleten lineImage för att koda URL:er (LINE-kanal).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailMaxError</span> <br /> </td> 
   <td> I kanalen "email" (använd som standard): Maximalt antal fel som accepteras för SOFT-fel under sändning innan mottagaren sätts i karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_EmailSignificantErrorDelay</span> <br /> </td> 
   <td> I kanalen "email" (använd som standard): Minimal tid sedan föregående SOFT-fel inträffade, innan ett nytt SOFT-fel togs med i beräkningen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileMaxError</span> <br /> </td> 
   <td> I kanalen "mobile": Maximalt antal fel som accepteras för SOFT-fel under sändning innan mottagaren sätts i karantän.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsNPAI_MobileSignificantErrorDelay</span> <br /> </td> 
   <td> I kanalen "mobile": Den minimala tid som har använts sedan föregående SOFT-fel refererades, innan ett nytt SOFT-fel har beaktats.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_LogsPeriodHour</span> <br /> </td>
   <td> Tillåter att en maximal period (uttryckt i timmar) anges som för att begränsa antalet utsändning som återställs varje gång synkroniseringsarbetsflödet körs.</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMidSourcing_PrepareFlow</span> <br /> </td> 
   <td> Maximalt antal anrop i MidSourcing-sessionen, som kan köras parallellt (3 som standard).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMTA_Alert_Delay</span> <br /> </td> 
   <td> Anpassad fördröjning (i minuter) efter vilken en leverans betraktas som"fördröjd". Standardvärdet är 30 minuter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_DeliveryPreparationWindow</span> <br /> </td> 
   <td><p>Det här alternativet används av det tekniska arbetsflödet <span class="uicontrol"><a href="../../workflow/using/about-technical-workflows.md">operationMgt</a></span> när antalet pågående leveranser räknas.</p>Det gör att du kan definiera antalet dagar över vilka leveranser med inkonsekvent status ska uteslutas från antalet pågående leveranser.</p><p>Som standard är värdet 7, vilket innebär att inkonsekventa leveranser som är äldre än 7 dagar kommer att exkluderas.</p></td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine1</span> <br /> </td> 
   <td> Rad 1 i avsändarens adress.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine3</span> <br /> </td> 
   <td> Rad 3 i avsändarens adress.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine4</span> <br /> </td> 
   <td> Rad 4 i avsändarens adress.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine6</span> <br /> </td> 
   <td> Rad 6 i avsändarens adress.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsPaper_SenderLine7</span> <br /> </td> 
   <td> Rad 7 i avsändarens adress.<br /> </td> 
  </tr>
  <tr> 
   <td> <span class="uicontrol">NmsServer_MirrorPageUrl</span> <br /> </td> 
   <td> URL:en för spegelsidservern (ska som standard vara identisk med NmsTracking_ServerUrl).<br /> Det är standardvärdet för e-postleveranser när URL inte har angetts i routningsdefinitionen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_Priority</span> <br /> </td> 
   <td> Parametrar för skickade SMS-meddelanden: information som skickas till SMS-gatewayen för att ange meddelandeprioriteten.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryCount</span> <br /> </td> 
   <td> Antal försök när SMS-meddelanden skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsSMS_RetryPeriod</span> <br /> </td> 
   <td> Period under vilken nya försök med SMS-meddelanden utförs.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsUserAgentStats_LastConsolidation</span> <br /> </td> 
   <td> Senaste konsolideringsdatum för <span class="uicontrol">NmsUserAgent</span>-statistik.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsWebSegments_LastStates</span> <br /> </td> 
   <td> Namnet på alternativet som innehåller webbsegmenten och deras lägen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkBarcode_SpecialChar</span> <br /> </td> 
   <td> Aktivera/inaktivera stöd för specialtecken för Code128.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkEmail_Characters</span> <br /> </td> 
   <td> Giltiga tecken för en e-postadress.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSecurity_Restrict_EditXML</span> </td> 
   <td> Lägg till det här alternativet med värdet "0" för att inaktivera XML-koden för leveransutgåvan (högerklicka / <span class="uicontrol">Redigera XML-källa</span> eller genvägen <span class="uicontrol">CTRL + F4</span>).<br /> </td> 
  </tr>  
 </tbody> 
</table>

<!--<tr> 
   <td> <span class="uicontrol">EMTA_BCC_ADDRESS</span> </td> 
   <td> BCC email address for Momentum to send a raw copy of the sent emails. <br /> </td> 
  </tr>
-->

## Resurs {#resources}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDir</span> <br /> </td> 
   <td> Plats för publiceringsresurser i Adobe Campaign klientkonsol. Se <a href="../../delivery/using/formatting.md#image-referencing">det här avsnittet</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmRessourcesDirPreview</span> <br /> </td> 
   <td> Sökväg till resurser för förhandsgranskning i Adobe Campaign klientkonsol. Se <a href="../../delivery/using/formatting.md#image-referencing">det här avsnittet</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_DefaultIgnoredImage</span> <br /> </td> 
   <td> Lista över URL-masker för de bilder som hoppades över under överföringen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImagePublishing</span> </td> 
   <td> Konfiguration av bildöverföring. Värdena kan vara none / tracking / script / list (kan åsidosättas av operatorns valfria inställningar). </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_ImageSubDirectory</span> <br /> </td> 
   <td> Mappen som bilderna på servern ska lagras i.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LogoPath</span> <br /> </td> 
   <td> Utrymme för att visa logotyper.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NcmPublishingDir</span> <br /> </td> 
   <td> Rotmapp för publikationer.<br /> Mer information om generering av HTML och textinnehåll finns i <a href="../../delivery/using/using-a-content-template.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkImageUrl</span> <br /> </td> 
   <td> Gör att du kan definiera på vilken server bilderna som används i leveranserna ska lagras så att webbläsaren kan hämta dem.<br /> För byggversioner &lt;= 5098 använder vi URL:en för bilderna som överfördes till instansen.<br /> För byggversioner &gt; 5098 använder vi i stället leveransens offentliga URL eller URL:en för alternativet <span class="uicontrol">XtkFileRes_Public_URL</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaInstance</span> <br /> </td> 
   <td> Gör att du kan konfigurera instansnamnet för bildöverföring.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaPassword</span> <br /> </td> 
   <td> Gör att du kan konfigurera lösenordet för bildöverföring.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsDelivery_MediaServers</span> <br /> </td> 
   <td> Här kan du konfigurera medie-URL:er för bildöverföring.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsBroadcast_MsgWebValidityDuration</span> <br /> </td> 
   <td> Standardgiltighetslängd för onlineresurser för en leverans (i sekunder).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkFileRes_Public_URL</span> <br /> </td> 
   <td> Ny URL för offentliga resursfiler.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Kampanj- och arbetsflödeshantering {#campaign-e-workflow-management}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">CrmMarketingActivityWindow</span> <br /> </td> 
   <td> Marknadsföringshistorik visas för det här antalet månader.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_Duration</span> <br /> </td> 
   <td> Standardgiltighetsperiod för en kampanj (i sekunder).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_LimitConcurrency</span> <br /> </td> 
   <td> Maximalt antal leverans-/arbetsflödes-/hypotes-/simuleringsjobb som kan bearbetas i taget, startat av operationMgt-arbetsflödet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_OperationMgtDebug</span> <br /> </td> 
   <td> Låter dig övervaka det tekniska arbetsflödets körning för <a href="../../workflow/using/about-technical-workflows.md">operationMgt</a>. När det är aktiverat (värdet 1) loggas körningsinformationen i arbetsflödets granskningsloggar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsOperation_TimeRange</span> <br /> </td> 
   <td> Tidsperiod för mål- och extraheringsvillkor i schemalagt läge.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Workflow_AnalysisThreshold</span> <br /> </td> 
   <td> Antal berörda poster efter vilka tabellstatistik beräknas om automatiskt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkReport_Logo</span> <br /> </td> 
   <td> Logotyp som ska visas i det övre högra hörnet av de exporterade rapporterna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_PausedWorkflowPeriod</span> <br /> </td> 
   <td> Antal dagar att vänta mellan kontroller för pausade arbetsflöden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCampaign_Activate_OwnerConfirmation</span> <br /> </td> 
   <td> Aktivera leveransvalideringen av åtgärdens ägare genom att ange "1" som värde. Om du vill inaktivera det här alternativet anger du 0.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsAsset_JavascriptExt</span> <br /> </td> 
   <td> Ytterligare JS-bibliotek som ska läsas in i arbetsflödets aktivitet"Marknadsföringsresursmeddelanden".<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Säkerhet {#security}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBSchema</span> <br /> </td> 
   <td> (från och med version 21.1.3) Om 1 har valts (standardvärde) inaktiverar det här alternativet utgåva av inbyggda scheman.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">RestrictEditingOOTBJavascript</span> <br /> </td> 
   <td> (från och med version 21.1.3) Om 1 har valts (standardvärde) inaktiverar det här alternativet utgåva av inbyggda JavaScript-koder.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkAcceptOldPassword</span> <br /> </td> 
   <td> (Kompatibilitetsläge för installation: build&gt;6000) När det aktiveras (värdet "1") tillåter det här alternativet att gamla lösenord som lagras i databasen används för anslutning till externa konton eller till instansen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkKey</span> <br /> </td> 
   <td> Den här nyckeln används för att kryptera de flesta lösenord i databasen. (externa konton, LDAP-lösenord..).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSecurity_Allow_PrivilegeEscalation</span> <br /> </td> 
   <td> Om 1 har valts kan det här alternativet tillåta privilegeEscalation i JavaScript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSecurity_Disable_ControlsOnFileDownload</span> <br /> </td> 
   <td> Om du väljer 1 inaktiveras ACL-kontroller under en filhämtning (via fileDownload.jsp).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSecurity_Disable_JSFileSandboxing</span> <br /> </td> 
   <td> Om 1 väljs inaktiverar det här alternativet filsandlådan i Javascript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSecurity_SaveOptions_AllowNonAdmin</span> <br /> </td> 
   <td> Om värdet är "true" har en auktoriserad icke-admin-operator som uppdaterar xtkOption-värdena via distributionsguiden.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSecurity_Unsafe_DecryptString</span> <br /> </td> 
   <td> Om 1 är markerat tillåter det här alternativet att dekryptera vissa lösenord med hjälp av decryptString.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkTraceDeleteLogin</span> <br /> </td> 
   <td> Ange värdet "1" om du vill spåra borttagningen av element med granskningsversionsinformation i mData, genom att ändra fältet "ändrad av" innan posten tas bort.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Meddelandecenter {#message-center}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">MC_EnrichmentCustomJs</span> <br /> </td> 
   <td> JavaScript-bibliotek som ska personaliseras för spännande event. Måste innehålla implementeringen av dessa två funktioner:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">enrichRtEvents(aiEventId);</span> : berikar och sparar händelser i databasen (där <span class="uicontrol">aiEventId</span> motsvarar tabellen med händelser i realtid som bearbetas).</p> </li> 
     <li> <p> <span class="uicontrol">enrichBatchEvents(aiEventId);</span> : berikar och sparar händelser i databasen (där <span class="uicontrol">aiEventId</span> motsvarar ID-tabellen för grupphändelser som bearbetas).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastUpdateFromBL</span> <br /> </td> 
   <td> Datum för den senaste händelsestatusuppdateringen via leveransloggar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RoutingCustomJs</span> <br /> </td> 
   <td> JavaScript-bibliotek som ska personaliseras för routningshändelser. Måste innehålla implementeringen av dessa två funktioner:<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">dispatchRtEvent(iEventId);</span> : returnerar det interna namnet på det transaktionsmeddelande som har valts för att bearbeta realtidshändelsen (där <span class="uicontrol">iEventId</span> motsvarar ID:t för den bearbetade realtidshändelsen).</p> </li> 
     <li> <p> <span class="uicontrol">dispatchBatchEvent(iEventId);</span> : returnerar det interna namnet på det transaktionsmeddelande som har valts för att bearbeta batchhändelsen (där <span class="uicontrol">iEventId</span> motsvarar ID:t för batchhändelsen som bearbetas).</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeAlert</span> <br /> </td> 
   <td> Varningströskelvärde för genomsnittlig sändningstid för realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgDeliveryTimeWarning</span> <br /> </td> 
   <td> Varningströskelvärde för genomsnittlig sändningstid för realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeAlert</span> <br /> </td> 
   <td> Varningströskelvärde för genomsnittlig bearbetningstid för realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgProcessTimeWarning</span> <br /> </td> 
   <td> Varningströskelvärde för genomsnittlig bearbetningstid för realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueAlert</span> <br /> </td> 
   <td> Varningströskelvärde för det genomsnittliga antalet händelser i realtid som står i kö.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeAlert</span> <br /> </td> 
   <td> Varningströskelvärde för genomsnittlig kötid för realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueTimeWarning</span> <br /> </td> 
   <td> Varningströskel för genomsnittlig kötid för realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventAvgQueueWarning</span> <br /> </td> 
   <td> Varningströskel för det genomsnittliga antalet händelser i realtid som köas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorAlert</span> <br /> </td> 
   <td> Varningströskelvärde för bearbetning av fel i realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventErrorWarning</span> <br /> </td> 
   <td> Varningströskel för bearbetning av fel i realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueAlert</span> <br /> </td> 
   <td> Varningströskel för maximalt antal händelser i realtid som står i kö.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMaxQueueWarning</span> <br /> </td> 
   <td> Varningströskel för maximalt antal händelser i realtid som står i kö.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueAlert</span> <br /> </td> 
   <td> Varningströskelvärde för minsta antal realtidshändelser som står i kö.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventMinQueueWarning</span> <br /> </td> 
   <td> Varningströskel för minsta antal realtidshändelser som köas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueAlert</span> <br /> </td> 
   <td> Tröskelvärde före kritiskt villkor för kön med väntande realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventQueueWarning</span> <br /> </td> 
   <td> Tröskelvärde före varning för kön med väntande realtidshändelser.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThrottputAlert</span> <br /> </td> 
   <td> Varningströskelvärde för händelsegenomströmning i realtid.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_RtEventThrottputWarning</span> <br /> </td> 
   <td> Varningströskel för händelsegenomströmning i realtid.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsMessageCenter_RoutingBatchSize</span> <br /> </td> 
   <td> Storlek på omgruppering för händelseroutning.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MC_LastRtEventStat</span> <br /> </td> 
   <td> Uppdateringspekare för RtEvent-status (senaste datum tills data hämtades).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLine_MessageCenterURL</span> <br /> </td> 
   <td> URL för Message Center-server som används för att skicka välkomstmeddelanden (LINE-kanal).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Databas {#database}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_LastCleanup</span> <br /> </td> 
   <td> Definierar den senaste gången rensningsprocessen kördes.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_BroadLogPurgeDelay</span> <br /> </td> 
   <td> <p>Här kan du ange efter vilken fördröjning som utsändning ska raderas från databasen.</p><p>Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventHistoryPurgeDelay</span> <br /> </td> 
   <td><p> Gör att du kan definiera efter hur lång tid händelsehistoriken ska tas bort från databasen.</p><p>
   Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventPurgeDelay</span> <br /> </td> 
   <td><p> Här kan du definiera efter vilken fördröjning händelser tas bort från databasen.</p><p>Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_EventStatPurgeDelay</span> <br /> </td> 
   <td><p> Gör att du kan definiera efter hur lång tid händelsestatistiken tas bort från databasen.</p><p>Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_PropositionPurgeDelay</span> <br /> </td> 
   <td><p> Här kan du definiera efter vilken fördröjning som förslag tas bort från databasen.</p><p> Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_QuarantineMailboxFull</span> <br /> </td> 
   <td> <p>Här kan du ange efter vilken tid som karantänerna ska raderas från databasen.</p><p> Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RecycledDeliveryPurgeDelay</span> <br /> </td> 
   <td> <p>Här kan du ange efter hur lång tid återvunna leveranser ska raderas från databasen.</p><p> Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_RejectsPurgeDelay</span> <br /> </td> 
   <td> <p>Här kan du definiera efter vilken tid som avvisade tas bort från databasen.</p><p>Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingLogPurgeDelay</span> <br /> </td> 
   <td> <p>Gör att du kan ange efter hur lång tid spårningsloggarna tas bort från databasen.</p><p>Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_TrackingStatPurgeDelay</span> <br /> </td> 
   <td><p> Här kan du ange efter vilken tid spårningsstatistik ska raderas från databasen.</p><p> Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_VisitorPurgeDelay</span> <br /> </td> 
   <td> <p>Här kan du definiera efter vilken tid besökare ska raderas från databasen.</p><p> Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsCleanup_WorkflowResultPurgeDelay</span> <br /> </td> 
   <td> <p>Här kan du definiera efter vilken fördröjning arbetsflödesresultaten ska raderas från databasen.</p><p> Det här alternativet skapas automatiskt när fördröjningen ändras i gränssnittet. Om du ändrar värdet från alternativlistan bör det anges i sekunder.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_AzureDw</span> <br /> </td> 
   <td> Azure SQL Datawarehouse-anslutningsalternativ.<br /> </td> 
  </tr>
   <tr> 
   <td> <span class="uicontrol">WdbcKillSessionPolicy</span> <br /> </td> 
   <td>Gör att du kan påverka beteendet Ovillkorligt stopp i alla arbetsflöden och PostgreSQL-databasfrågor enligt följande möjliga värden:<ul>
    <li><p>0 - standard: avbryter arbetsflödesprocessen, påverkar inte databasen<p></li>
    <li><p>1 - pg_cancel_backend: stoppar arbetsflödesprocessen och avbryter frågan i databasen<p></li>
    <li><p>2 - pg_terminate_backend: stoppar arbetsflödesprocessen och avslutar frågan i databasen<p></li></ul></td> 
  </tr>  
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceUser</span> <br /> </td> 
   <td> Namnet på det tabellutrymme som är avsett att innehålla data från Adobe Campaign tabeller.<br />Se <a href="../../installation/using/creating-and-configuring-the-database.md">Skapa och konfigurera databasen</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceIndex</span> <br /> </td> 
   <td> Namnet på det tabellutrymme som är avsett att innehålla indexen för Adobe Campaign tabeller.<br />Se <a href="../../installation/using/creating-and-configuring-the-database.md">Skapa och konfigurera databasen</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWork</span> <br /> </td> 
   <td> Namnet på det tabellutrymme som ska innehålla data från Adobe Campaign arbetstabeller.<br />Se <a href="../../installation/using/creating-and-configuring-the-database.md">Skapa och konfigurera databasen</a>.</td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcOptions_TableSpaceWorkIndex</span> <br /> </td> 
   <td> Namnet på det tabellutrymme som är avsett att innehålla indexen för Adobe Campaign arbetstabeller.<br />Se <a href="../../installation/using/creating-and-configuring-the-database.md">Skapa och konfigurera databasen</a>.</td> 
  </tr> 
    <tr> 
   <td> <span class="uicontrol">WdbcOptions_TempDbName</span> <br /> </td> 
   <td> Gör att du kan konfigurera en separat databas för arbetstabeller på Microsoft SQL Server för att optimera säkerhetskopiering och replikering. Alternativet motsvarar namnet på den tillfälliga databasen: Arbetstabeller skrivs i den här databasen om det anges. Exempel: 'tempdb.dbo.' (Observera att namnet måste sluta med en punkt). <a href="../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server">Läs mer</a> <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcTimeZone</span> <br /> </td> 
   <td> Tidszon för Adobe Campaign-instansen. Se <a href="../../installation/using/time-zone-management.md#configuration" target="_blank">Konfiguration</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseNChar</span> <br /> </td> 
   <td> Är databasens strängfält definierade med NChar?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcUseTimeStampWithTZ</span> <br /> </td> 
   <td> Lagrar databasens datetime-fält tidszonsinformation?<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkDatabaseId</span> <br /> </td> 
   <td> ID för databasen. Börjar av 'u' för Unicode DataBase.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkInstancePrefix</span> <br /> </td> 
   <td> Prefixet har lagts till i interna namn som genereras automatiskt.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkQuery_Schema_LineCount</span> <br /> </td> 
   <td> Maximalt antal resultat som returnerats av en fråga i xtk:schema och xtk:srcSchema.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkSequence_AutoGeneration</span> <br /> </td> 
   <td> Alla anpassade scheman, som skapats efter den här tiden, med autopk="true" och utan attributet "pkSequence" får den autogenererade sekvensen "auto_ 
    &lt;schemanamespace&gt; 
     &lt;schemanamn&gt;
       _seq. 
   </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NlMigration_KeepFolderStructure</span> <br /> </td> 
   <td> Under migreringen ordnas trädstrukturen automatiskt om baserat på de nya versionsstandarderna.<br /> Med det här alternativet kan du inaktivera automatisk migrering av navigeringsträdet. Om du använder den efter migreringen måste du ta bort gamla mappar, lägga till de nya mapparna och köra alla nödvändiga kontroller.<br /> 
    <ul> 
     <li> <p> <span class="uicontrol">Datatyp:</span> Heltal</p> </li> 
     <li> <p> <span class="uicontrol">Värde (text)</span> : 1 </p> </li> 
    </ul> Det här alternativet bör bara användas om navigeringsträdet som finns utanför rutan har genomgått för många ändringar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsLastErrorStatusCoalesce</span> <br /> </td> 
   <td> Senaste bearbetningsdatum för tabellrensningen <span class="uicontrol">NmsEmailErrorStat</span>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">PostUpgradeLastError</span> <br /> </td> 
   <td> Information om felet som uppstod i Poengrade, enligt syntaxen nedan:<br /> <strong>{Build number}:{mode: pre/post/..}:{The lessThan/'greaterOrEquelThan' där felet inträffade + substep}</strong> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkCleanup_NoStats</span> <br /> </td> 
   <td> Ange värdet "1" så att statistikuppdateringen inte utförs via rensningsarbetsflödet.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integrering {#integration}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">AEMResourceTypeFilter</span> <br /> </td> 
   <td> Typer av AEM resurser som kan användas i Adobe Campaign. Värden måste avgränsas med kommatecken.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">nmsPipeline_config</span> <br /> </td> 
   <td> Gör att du kan konfigurera utlösare för Experience Cloud. Datatypen är "lång text" och måste vara i JSON-format. Se <a class="anchorLink" href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html#PipelineoptionNmsPipelineConfig" target="_blank">Använda Experience Cloud-utlösare med Adobe Campaign Classic</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</span> <br /> </td> 
   <td> Det här alternativet används vid import av data från ett tredjepartssystem via en CRM-anslutning. Om du aktiverar alternativet kan du bara samla in objekt som har ändrats sedan den senaste importen. Det här alternativet måste skapas och fyllas i manuellt enligt nedan: 
    <ul> 
     <li> <p> <span class="uicontrol">Internt namn</span> : LASTIMPORT_&lt;%=instance.internalName%&gt;_&lt;%=activityName%&gt;</p> </li> 
     <li> <p> <span class="uicontrol">Värde (fält)</span> : datum för den senaste importen, med formatet åååå/MM/dd hh:mm:ss. </p> </li> 
    </ul><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_EdgeServer</span> <br /> </td> 
   <td> Adobe Target-server som används för integreringen. Det här alternativet är redan markerat som standard. Detta värde motsvarar Adobe Target Domain Server, följt av värdet /m2. Till exempel: tt.omtrdc.net/m2.<br /> Se <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">TNT_TenantName</span> <br /> </td> 
   <td> Adobe Target organisationsnamn. Detta värde motsvarar namnet på Adobe Target-klienten.<br /> Se <a href="../../integrations/using/configuring-the-integration-with-adobe-target.md">det här avsnittet</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DataSourceId</span> <br /> </td> 
   <td> Alternativ som används för integrering med Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">AAM_DestinationId</span> <br /> </td> 
   <td> Alternativ som används för integrering med Adobe Audience Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Teradata</span> <br /> </td> 
   <td> Anslutningsalternativ för teradata.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">WdbcCapabilities_Hive</span> <br /> </td> 
   <td> Alternativ för Hive-koppling.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Erbjudanden {#offers}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsCoupons_MaxPerTransac</span> <br /> </td> 
   <td> Antal kuponger som uppdateras per SQL-transaktion.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchControl_</span> <br /> </td> 
   <td> '+ [propositionens schema] + "_" + extAccountSource.@executionInstanceId + [propositionens schema] + "_" + vars.executionInstanceIdFilter<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_LastPropositionSynchExec_</span> <br /> </td> 
   <td> '+ [ propositionens schema] + "_" + extAccountSource.@executionInstanceId + "_" + extAccountTarget.@executionInstanceId<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_SynchWorkflowIds</span> <br /> </td> 
   <td> Spårning av synkroniseringsarbetsflöde.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsInteraction_UseDaemon</span> <br /> </td> 
   <td> Aktivera/inaktivera asynkron offert-skrivning ("0" för att inaktivera, "1" för att aktivera).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsModule_CouponsEnabled</span> <br /> </td> 
   <td> Låter dig aktivera kuponger.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Server {#server}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsExecutionInstanceId</span> <br /> </td> 
   <td> Identifierare för körningsinstans.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_CustomerId</span> <br /> </td> 
   <td> Kundidentifierare som används när faktureringsrapporten skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_IntranetURL</span> <br /> </td> 
   <td> Intern bas-URL för åtkomst till programservern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_LastPostUpgrade</span> <br /> </td> 
   <td> Kontextinstansens byggnummer före den senaste uppgraderingen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsServer_URL</span> <br /> </td> 
   <td> Bas-URL för den offentliga webbprogramservern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkPassUnknownSQLFunactionsToRDBMS</span> <br /> </td> 
   <td> Gör att du kan fortsätta använda gamla odeklarerade SQL-funktioner efter migrering. Vi rekommenderar att du inte använder det här alternativet på grund av säkerhetsriskerna som det medför.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Spåra {#tracking}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Available</span> <br /> </td> 
   <td> Alternativ som låter dig aktivera spårning.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ClickFormula</span> <br /> </td> 
   <td> Beräkningsskript för spårad URL.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ExtAccount</span> <br /> </td> 
   <td> Här kan du definiera spårningsserverns externa konto.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Instance</span> <br /> </td> 
   <td> Gör att du kan definiera instansnamnet på spårningsservern.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_LastConsolidation</span> <br /> </td> 
   <td> Senaste gången spårningsinformationen har konsoliderats med nya data.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_OpenFormula</span> <br /> </td> 
   <td> Öppna URL-beräkningsskript.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Password</span> <br /> </td> 
   <td> Lösenord för spårningsservern <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_Pointer</span> <br /> </td> 
   <td> Pekaren håller reda på de senaste meddelandehändelserna som bearbetades via deras ID:n och datum.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_SecureServerUrl</span> <br /> </td> 
   <td> Säker URL för servern för frontspårning.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrl</span> <br /> </td> 
   <td> URL för servern för frontspårning.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_ServerUrlList</span> <br /> </td> 
   <td> Lista över URL:er som används för att kontakta spårningsservrarna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_UserAgentRules</span> <br /> </td> 
   <td> Regeluppsättning för identifiering av webbläsare.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebFormula</span> <br /> </td> 
   <td> Skript som används för att beräkna webbspårningstaggar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingDelivery</span> <br /> </td> 
   <td> Namnet på den virtuella leveransen som är avsedd för hantering av webbspårning.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">NmsTracking_WebTrackingMode</span> <br /> </td> 
   <td> Gör att du kan definiera webbspårningsläget.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Sekretess {#privacy}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePending</span> <br /> </td> 
   <td> Om alternativ 1 är markerat måste du bekräfta borttagningen manuellt i gränssnittet i ett andra steg. Annars tas data bort utan bekräftelse.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_ConfirmDeletePendingDelay</span> <br /> </td> 
   <td> Fördröjning mellan begäran väntar på att ta bort bekräftelse och begäran avbryts.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_MaxErrorAllowed</span> <br /> </td> 
   <td> Det högsta antalet fel som tillåts vid bearbetning/borttagning av en sekretessbegäran.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Privacy_Request_PurgeDelay</span> <br /> </td> 
   <td> Fördröjning mellan begäran skapas i kön och data för begäran tas bort.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## LDAP {#ldap}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_Active</span> <br /> </td> 
   <td> Aktivera LDAP-servern som ska användas för att autentisera användare och ge behörigheter till användare.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppLogin</span> <br /> </td> 
   <td> Programinloggning för att kontakta servern för olika sökningar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_AppPassword</span> <br /> </td> 
   <td> Krypterat lösenord för programinloggningen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_AutoOperator</span> <br /> </td> 
   <td> Aktivera automatiskt skapande av operatorer och rättigheter i Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DN</span> <br /> </td> 
   <td> Beräkningsformel för LDAP DN baserat på inloggning.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearch</span> <br /> </td> 
   <td> Aktivera DN-sökning i katalogen.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchBase</span> <br /> </td> 
   <td> Sökbas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchFilter</span> <br /> </td> 
   <td> DN-sökfilter.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_DNSearchScope</span> <br /> </td> 
   <td> Sökomfång.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_Mechanism</span> <br /> </td> 
   <td> Autentiseringstyp som används för att kontakta LDAP-servern (normal, md5, lds, ntlm, dpa).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_Rights</span> <br /> </td> 
   <td> Aktivera synkronisering av auktoriseringar och grupper från LDAP-katalogen till namngivna behörigheter i Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_RightsAttr</span> <br /> </td> 
   <td> LDAP-attribut som innehåller auktoriseringsnamnet.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">XtkLdap_RightsBase</span> <br /> </td> 
   <td> Sökbas.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_RightsFilter</span> <br /> </td> 
   <td> Sökfilter för användarauktoriseringar.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_RightsMask</span> <br /> </td> 
   <td> Uttryck för att extrahera namnen på Adobe Campaign-rättigheterna från LDAP-auktoriseringarna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_RightsScope</span> <br /> </td> 
   <td> Sökomfång.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkLdap_Server</span> <br /> </td> 
   <td> LDAP-serveradress (det går att ange en port genom att ange ':' som avgränsare).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Webbformulär {#web-forms}

<table> 
 <thead> 
  <tr> 
   <th> Alternativnamn </th> 
   <th> Beskrivning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">XtkUseScrollBar</span> <br /> </td> 
   <td> Värdet 1 tillåter rullningslist förutom detaljformulär.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkWebForm_Instance</span> <br /> </td> 
   <td> Instans som ska användas för webformulärogiltigförklaring i läget 'andra servrar'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkWebForm_Password</span> <br /> </td> 
   <td> Lösenord för instansen som ska användas för webformulärogiltigförklaring i läget "andra servrar".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkWebForm_ServersMode</span> <br /> </td> 
   <td> Alternativ som låter dig ange ogiltighetsläge för webbformulär: lokalt som standard använder spårningsservrar om alternativet är spårning och använder en anpassad lista med alternativet "andra servrar".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">xtkWebForm_ServersURL:er</span> <br /> </td> 
   <td> Personlig adresslista över servrar som ska kontaktas för ogiltigförklaring av webbformulär (läge för andra servrar).<br /> </td> 
  </tr> 
 </tbody> 
</table>
