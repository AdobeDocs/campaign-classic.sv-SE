---
product: campaign
title: Moduler och vanliga problem
description: Moduler och vanliga problem
feature: Monitoring, Troubleshooting
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 5%

---

# Moduler och vanliga problem{#modules-and-frequent-issues}



Här är en lista över moduler som påverkas av vanliga problem:

<table> 
 <thead> 
  <tr> 
   <th> Modul </th> 
   <th> Körningsomfång </th> 
   <th> Felsökning </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> export </td> 
   <td> Körning av en exportprocess <br /> </td> 
   <td> Operatorn som har schemalagt den här exporten måste starta om den. Delta eller fullständig omstart.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Körning av en importprocess <br /> </td> 
   <td> Operatorn som har schemalagt den här exporten måste starta om den. Kontrollera om databasen innehåller dubbletter.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Läsning av studsmeddelanderutan <br /> </td> 
   <td> Kontrollera den här modulen om studsmeddelanden inte längre vidarebefordras.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Levererar e-postmeddelanden<br /> </td> 
   <td> Kontrollera den här modulen om e-postmeddelanden inte längre skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Underhåller MTA-anslutningsstatistik<br /> </td> 
   <td> Kontrollera den här modulen om e-postmeddelanden inte längre skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Loggskrivning<br /> </td> 
   <td> Om några loggar saknas i loggfilerna kontrollerar du att modulen använder port 6666. Se <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista över öppna portar</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> spårning </td> 
   <td> Konsoliderar och hämtar spårningsloggar <br /> </td> 
   <td> Kontrollera den här modulen om spårningsloggar inte längre vidarebefordras.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Spårningsloggen skriver och rensar servern <br /> </td> 
   <td> Markera den här modulen om spårningsloggar inte längre vidarebefordras och det inte finns några spårningar av loggar i filerna på servern. Se <a href="../../production/using/tracking-logs-issues.md" target="_blank">Problem med spårningsloggar</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> övervakningsenhet </td> 
   <td> Instansen <br /> startas och övervakas </td> 
   <td> Kontrollera den här modulen om inga processer startar.<br /> </td> 
  </tr> 
  <tr> 
   <td> webb </td> 
   <td> Programserver (HTTP och SOAP)<br /> </td> 
   <td> Kontrollera den här modulen om konsolen och webbanslutningarna inte fungerar och utlöser ett <strong>xtk:session</strong>-typfel<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Kontrollerar körning av arbetsflödesinstans.<br /> </td> 
   <td> Starta om den här modulen om du råkar ut för problem. Om det behövs använder du proceduren för att öka precisionen för loggar som anges i avsnittet <a href="../../production/using/log-precision.md" target="_blank">Loggprecision</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>
