---
product: campaign
title: Lista över rapporter
description: Lista över rapporter
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: abaeef25b03a9699a4851786380d467bfa299c9f
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 2%

---

# Lista över rapporter{#list-of-reports}



## Rapporter om leveranser {#reports-on-deliveries}

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i [det här avsnittet](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Användaraktiviteter (receiveActivity)<br /> </td> 
   <td> Uppdelning av öppningar, klick och transaktioner efter tidsperiod.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransdataflöde (dataflöde)<br /> </td> 
   <td> Leveransdataflödesdiagram, i meddelanden/timme och Mbit/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel och studsar (fel)<br /> </td> 
   <td> Begränsningar och icke-levererbara produkter utifrån orsak och domän.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsindikatorer (deliveryFeedback)<br /> </td> 
   <td> Sammanfattning av nyckelindikatorer för spårning av mottagarbeteende.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsindikatorer (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Spåra indikatorer för en leverans till ett mobilprogram.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Webbläsare (browserStatistics)<br /> </td> 
   <td> Statistik för webbläsare som används av mottagare som klickat i meddelanden.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Delning till sociala nätverk (deliveryForward)<br /> </td> 
   <td> Delningsaktivitet och statistik för att öppna e-post.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Snabbklickningar (hoturls)<br /> </td> 
   <td> Visar meddelandet och klickfrekvenserna som ligger ovanpå.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypotesrapport (deliveryHypothesis)<br /> </td> 
   <td> Visar en sammanfattning av mått för leveranshypoteser.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransstatistik (StatisticsPerDelivery)<br /> </td> 
   <td> Statistik (bearbetade meddelanden, levererade meddelanden, hårda studsar, mjuka studsar, klick, avbeställningar) per e-postdomän.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Dela aktivitetsstatistik (forwardActivities)<br /> </td> 
   <td> Analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsstatistik (trackingStatistics)<br /> </td> 
   <td> Öppna, klicka och rapportera transaktionsräntor.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveranssammanfattning (deliverySending)<br /> </td> 
   <td> Sammanfattning av leveransindikatorer: mål, undantag och skickade meddelanden.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveranssammanfattning (deliveryStatistics)<br /> </td> 
   <td> Sammanfattningstabell för valda leveranser: Mål, undantag och skickade meddelanden.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Operativsystem (osStatistics)<br /> </td> 
   <td> Statistik för operativsystem som används av mottagare som klickade i ett meddelande.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktivitetsfrekvens (deliveryFeedbackSocial)<br /> </td> 
   <td> Leveransreaktivitet och reaktionsnedbrytning.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL:er och klickdataflöde (topUrlDelivery)<br /> </td> 
   <td> De flesta reaktiva URL:erna och associerade klickströmmar.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om kampanjer {#reports-on-campaigns}

Rapporter om kampanjer rör data i tabellen **nms:operation**.

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i [det här avsnittet](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Användaraktiviteter (operationRecipientActivity)<br /> </td> 
   <td> Uppdelningen av öppningar, klick och transaktioner efter tidsperiod beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveransdataflöde (operationThoutput)<br /> </td> 
   <td> Leveransdataflödesdiagram, i e-post/timme och Mbit/s, är beroende av Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Kampanjutgifter (budgetOperationExpenses)<br /> </td> 
   <td> Visar kampanjradobjekten i detalj, beroende på kampanj.<br /> </td> 
  </tr> 
  <tr> 
   <td> Fel och studsar (operationErrors)<br /> </td> 
   <td> Begränsningar och icke-levererbara produkter beroende på orsak och domän, är beroende av Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerOperation)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader, beror på MRM.<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårningsindikatorer (operationFeedback)<br /> </td> 
   <td> Översikt över nyckelspårningsindikatorer: Öppningar, klick och transaktioner, beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delning till sociala nätverk (operationForward)<br /> </td> 
   <td> Delningsaktivitet och statistik för att öppna e-post är beroende av Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Hypotesrapport (operationHypothesis)<br /> </td> 
   <td> Visar sammanfattningen av hypotesmått för kampanjleveranser, beroende på kampanj.<br /> </td> 
  </tr> 
  <tr> 
   <td> Delningsaktivitetsstatistik (forwardActivityOpt)<br /> </td> 
   <td> Analys av delningsaktiviteter, öppningar och prenumerationer per tidsperiod, beror på Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Leveranssammanfattning (operationStatistics)<br /> </td> 
   <td> Översiktsdiagram över kampanjleveranser: Mål, undantag och skickade meddelanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL:er och klickdataflöde (operationTopUrlDelivery)<br /> </td> 
   <td> De flesta reaktiva URL:er och associerade klickströmmar är beroende av Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om tjänster {#reports-on-services}

Rapporter om tjänster rör data i tabellen **nms:service**.

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i de relaterade guiderna.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fläktförvärv (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Vilka webbprogram aktiverade köp av potentiella kunder? Beroende på tillägg för social marknadsföring.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning av prenumerationer (mobileAppDistribution)<br /> </td> 
   <td> Uppdelning av aktiva prenumerationer per mobilprogram, beroende på kanaltillägg för mobilappen.<br /> </td> 
  </tr> 
  <tr> 
   <td> Prenumerationsspårning (subscriptionsProgress)<br /> </td> 
   <td> Prenumerationernas utveckling för informationstjänster <br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktivitetsfrekvens (socialReactionRate)<br /> </td> 
   <td> Vilka är reaktivitetsfrekvenserna för de senaste leveranserna? Beroende på tillägg för social marknadsföring.<br /> </td> 
  </tr> 
  <tr> 
   <td> Reaktivitetsfrekvens (mobileAppReactivityRate)<br /> </td> 
   <td> Reaktivitetsfrekvensen för de senaste leveranserna är beroende av kanaltillägg för mobilappen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Budgetrapporter {#budget-reports}

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i [det här avsnittet](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Kostnader kopplade till program (budgetProgramCost)<br /> </td> 
   <td> Uppdelning av programkostnader.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Budgetutveckling (budgetEvolution)<br /> </td> 
   <td> Utveckling av budgetkostnader per åtagandenivå.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Kumulativ utveckling av budgeten (budgetCumulativeEvolution)<br /> </td> 
   <td> Utveckling av de kumulerade budgetkostnaderna uppdelat efter implementeringsnivå för <br />. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerBudget)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorer)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerPlan)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Utforska kostnadsrader (budgetExplorerProgram)<br /> </td> 
   <td> Beskrivande analys av kostnadsrader.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Sammanfattning av budget(er) (budget)<br /> </td> 
   <td> Ögonblicksbild av huvudkostnader, utgiftskategorier och budgetar.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om simuleringar {#reports-on-simulations}

Rapporter om simuleringar rör data i tabellen **nms:simulation**.

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i de relaterade guiderna.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Information om simuleringsundantag (dlvSimuLossesDetail)<br /> </td> 
   <td> Detaljerad tabell över alla orsaker till uteslutning.<br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning av erbjudanden efter rangordning (offerSimulationRanking)<br /> </td> 
   <td> Uppdelning av erbjudanden i simuleringen, efter rangordning.<br /> </td> 
  </tr> 
  <tr> 
   <td> Simuleringssammanfattning (dlvSimuLossesSummary)<br /> </td> 
   <td> Sammanfattning av simuleringsvolymer och undantag.<br /> </td> 
  </tr> 
  <tr> 
   <td> Överlappningsstatistik (dlvSimuOverlapping)<br /> </td> 
   <td> Leveransmål för överlappande volymer.<br /> </td> 
  </tr> 
  <tr> 
   <td> Sammanfattning av undantag på grund av simuleringen (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabell över undantag på grund av simuleringen.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporter om webbprogram {#reports-on-web-applications}

Rapporter om webbprogram rör data i tabellen **nms:WebApp**.

De inbyggda rapporterna från Adobe Campaign finns i tabellen nedan.

Mer information om innehållet i dessa rapporter finns i [det här avsnittet](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dokumentation (surveyDictionary)<br /> </td> 
   <td> Beskrivning av undersökningsstrukturen, beror på tillägget Undersökningshanteraren.<br /> </td> 
  </tr> 
  <tr> 
   <td> Main (surveyProperties)<br /> </td> 
   <td> Undersökningsegenskaper <br /> </td> 
  </tr> 
  <tr> 
   <td> Uppdelning av svar (surveyDistribution)<br /> </td> 
   <td> Uppdelning av svar på frågor.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Andra rapporter {#other-ootb-reports}

Följande rapporter finns också inbyggda. Mer information finns i dokumentet om de funktioner som berörs.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etikett och internt namn</strong><br /> </td> 
   <td> <strong>Beskrivning</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Erbjudandeanalys (offerAnalysis)<br /> </td> 
   <td> Erbjudandeanalys per datum och kanal, beroende på interaktionstillägget.<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> Effektiv ommarknadsföring (remarketingEffect)<br /> </td> 
   <td> Mätning av återmarknadsföringseffektivitet<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Historik över förvärv av sociala potentiella kunder (socialVisitorStatistics)<br /> </td> 
   <td> Historiken för köp av X (tidigare kallat Twitter) och Facebook potentiella kunder beror på tillägget för social marknadsföring.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> Spårning av senaste förslag (recentPropositions)<br /> </td> 
   <td> Spåra offert i realtid <br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
