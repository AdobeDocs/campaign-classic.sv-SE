---
product: campaign
title: Versionsinformation för Campaign 18.6
description: Versionsinformation för Campaign 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
feature: Overview
role: User
level: Beginner
exl-id: a849ce10-0972-4c42-b10e-67a81c79bc65
source-git-commit: c281d437907efb4d514bec7cacc698c383f3fe53
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 7%

---

# Version 18.6{#release-18-6}

![](../../assets/v7-only.svg)

## Version 18.6.2 – build 8949{#release-18-6-3-build-8949}

22 augusti 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md) eller kontakt [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> Funktionalitet<br /> </th> 
   <th> Beskrivning<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Frågeränder<br /> </td> 
   <td> <p>När flera Campaign-användare ansluter till samma externa FDA-Teradata-konto kan du nu skicka ett frågeband (nyckel/värde-par) som är specifikt för varje användare. Varje gång en Campaign-användare utför en fråga i Teradata-databasen kan Adobe Campaign nu skicka metadata som är kopplade till användaren. Dessa data, som består av en lista med nycklar och värden, kan sedan användas av Teradata-administratörer för revision eller för att hantera åtkomsträttigheter, till exempel.</p><p>Mer information finns i den <a href="../../installation/using/external-accounts.md">detaljerade dokumentationen</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Förbättringar**

* Loggarna för e-postarkivering har förbättrats, vilket gör det enklare och tydligare att kontrollera vilka e-postmeddelanden som har levererats eller misslyckats via BCC-arkivering. (NEO-10675)
* Korrigerade ett problem som ledde till att IP-adresser för belastningsutjämnare visades i stället för IP-adresser för kunder i spårningsloggarna. (NEO-11295)
* Korrigerade ett slumpmässigt problem som medförde att egenskaperna för en leverans skrevs över felaktigt. (NEO-11015)
* Korrigerade ett syntaxfel vid sortering av resultat för anrikningsaktivitet. (NEO-11394)
* Ett problem har korrigerats när beräknade fält används i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-11382)
* Tomcat har uppdaterats för att förhindra utnyttjande av sårbarheter. (NEO-11503)
* Korrigerade ett fel med LATIN1-kodning vid användning av en FDA-anslutning till en PostgreSQL-databas. (NEO-11299)
* Ett problem som uppstod när **[!UICONTROL Prepare the personalization data with a workflow]** leveransalternativ. (NEO-11047)
* Korrigerade ett efteruppgraderingsfel som förhindrade att SMS skickades när en utökad anslutning användes.
* Förbättrad import/export av paket (logg och region lades till i gränssnittet).
* Ett problem som visade oanvändbara fel i efteruppgraderingsloggen när en **[!UICONTROL Survey answers]** arbetsflödesaktiviteten har inte konfigurerats fullständigt.

**Tekniska utvecklingar**

Frågeränder

En specifik nyckel (PROXYUSER eller PROXYROLE) används för att associera en Teradata användare eller roll med en Campaign-användare. En ny behörighet har lagts till för att använda den här proxyanvändaren/rollen. Du måste lägga till behörigheten GRANT CONNECT VIA till databaskontot (den som definieras i Teradatans externa konto).

En ny flik har lagts till i Teradatans externa konton. The **[!UICONTROL Query banding]** -fliken innehåller följande alternativ:

* **[!UICONTROL Active]**: om du vill aktivera funktionen.
* **[!UICONTROL Default]**: Ange ett standardfrågeband som ska användas om en användare inte har något associerat frågeband. Om inget standardfrågeband har definierats kan de användare som inte har något associerat frågeband inte använda Teradata.
* **[!UICONTROL Users]**: för varje användare anger du ett frågefält. Du kan lägga till så många nyckel-/värdepar du behöver. Till exempel: &quot;priority=1;workload=high;&quot;

Mer information om frågeflätning finns i följande artiklar:

* [https://docs.teradata.com/reader/cY5B~oeEUFWjgN2kBnH3Vw/a5G1iz~ve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Version 18.6 – build 8947{#release-18-6-build-8947}

25 juni 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Please [uppgradera till den senaste versionen](../../production/using/build-upgrade.md) eller kontakt [teknisk support](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> Funktionalitet<br /> </th> 
   <th> Beskrivning<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Säkerhetsförbättringar<br /> </td> 
   <td> Ett antal säkerhetsförbättringar har lagts till i Campaign Classic. Förbättringar och korrigeringar visas nedan.<br /> </td> 
  </tr> 
  <tr> 
   <td> Stöd för Windows Server 2016<br /> </td> 
   <td> Adobe Campaign är nu kompatibelt med Windows Server 2016. Se <a href="https://helpx.adobe.com/campaign/kb/compatibility-matrix.html">Kompatibilitetsmatris för Campaign Classic</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

decryptString

The **decryptString** funktionen är föråldrad. Se [Föråldrade och borttagna funktioner](deprecated-features.md) artikel.

För nya kunder används den här funktionen nu bara för att dekryptera mottagarens krypterade ID på landningssidor. Om du vill dekryptera lösenord som lagras i ett externt konto använder du det nya **decryptPassword** funktion.

För befintliga kunder ändras inte funktionens beteende, men vi rekommenderar att du använder **decryptPassword** i stället för **decryptString**. The **XtkSecurity_Unsafe_DecryptString** Kompatibilitetsalternativet läggs till av efteruppgraderingen och aktiveras som standard, så att du kan fortsätta använda funktionen. Om du vill inaktivera **decryptString**, avaktivera alternativet.

decryptPassword

The **decryptPassword** funktionen har lagts till. Du kan dekryptera ett lösenord som lagras i ett externt konto. Se [JSAPI](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html) mer information.

Fil-API:er

För nya installationer är mappåtkomst via fil-API:er begränsad till **var**, **sftp** och temporära mappar för Adobe Campaign.

För befintliga kunder har fil-API:er inte längre åtkomst till **conf** Adobe Campaign. The **XtkSecurity_Disable_JSFileSandboxing** Kompatibilitetsalternativet läggs till av efteruppgraderingen och aktiveras som standard, så att du kan fortsätta komma åt de andra mapparna. Om du vill begränsa åtkomsten till **var**, **sftp** och tillfälliga mappar med Adobe Campaign inaktiverar du alternativet.

**Lappa**

* Ett problem som kunde påverka SMS-transaktionsmeddelandets prestanda har åtgärdats. (NEO-9812)
