---
title: Moduler och vanliga problem
seo-title: Moduler och vanliga problem
description: Moduler och vanliga problem
seo-description: null
page-status-flag: never-activated
uuid: d53324ce-b6e2-40d7-932d-36ce4a6f5cf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: a44f5e71-3f9b-4d02-8b7a-a9782bb6bdd8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

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
   <td> Körning av en exportprocess<br /> </td> 
   <td> Operatorn som har schemalagt den här exporten måste starta om den. Antingen delta eller fullständig omstart.<br /> </td> 
  </tr> 
  <tr> 
   <td> import </td> 
   <td> Körning av en importprocess<br /> </td> 
   <td> Operatorn som har schemalagt den här exporten måste starta om den. Kontrollera om det finns dubbletter i databasen.<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> Läsning av studsmeddelanderutan<br /> </td> 
   <td> Markera den här modulen om studsmeddelanden inte längre vidarebefordras.<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> Levererar e-postmeddelanden<br /> </td> 
   <td> Markera den här modulen om e-postmeddelanden inte längre skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> Underhåller statistik för MTA-anslutning<br /> </td> 
   <td> Markera den här modulen om e-postmeddelanden inte längre skickas.<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> Loggskrivning<br /> </td> 
   <td> Om några loggar saknas i loggfilerna kontrollerar du att modulen använder port 6666. Se <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">Lista över öppna portar</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> spårning </td> 
   <td> Konsolidera och hämta spårningsloggar<br /> </td> 
   <td> Markera den här modulen om spårningsloggar inte längre vidarebefordras.<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> Spåra loggskrivnings- och tömningsserver<br /> </td> 
   <td> Markera den här modulen om spårningsloggar inte längre vidarebefordras och det inte finns några spårningar av loggar i filerna på servern. Se Problem med <a href="../../production/using/tracking-logs-issues.md" target="_blank">spårningsloggar</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> övervakningsenhet </td> 
   <td> Instans för start och övervakning<br /> </td> 
   <td> Markera den här modulen om inga processer startar.<br /> </td> 
  </tr> 
  <tr> 
   <td> webb </td> 
   <td> Programserver (HTTP och SOAP)<br /> </td> 
   <td> Markera den här modulen om konsolen och webbanslutningarna inte fungerar och utlöser ett <strong>xtk:session</strong> -typfel<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> Styr körning av arbetsflödesinstansen.<br /> </td> 
   <td> Starta om den här modulen om du råkar ut för problem. Om det behövs kan du använda proceduren för att öka precisionen för loggarna i avsnittet <a href="../../production/using/log-precision.md" target="_blank">Loggprecision</a> .<br /> </td> 
  </tr> 
 </tbody> 
</table>

