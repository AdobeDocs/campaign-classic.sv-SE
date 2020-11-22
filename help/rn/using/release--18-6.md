---
solution: Campaign Classic
product: campaign
title: Version 18.6
description: Version 18.6
audience: rn
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 6%

---


# Version 18.6{#release-18-6}

## Version 18.6.2 – build 8949{#release-18-6-3-build-8949}

22 augusti 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Uppgradera [till den senaste versionen](../../production/using/build-upgrade.md) eller kontakta [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> <p>När flera Campaign-användare ansluter till samma FDA Teradata-externa konto kan du nu skicka ett frågeband (nyckel/värde-par) som är specifikt för varje användare. Varje gång en Campaign-användare utför en fråga i Teradata-databasen kan Adobe Campaign nu skicka metadata som är kopplade till användaren. Dessa data, som består av en lista med nycklar och värden, kan sedan användas av Teradata-administratörer för revision eller för att hantera åtkomsträttigheter, till exempel.</p><p>Mer information finns i den <a href="../../installation/using/external-accounts.md">detaljerade dokumentationen</a>.</p> </td>
  </tr> 
 </tbody> 
</table>

**Förbättringar**

* Loggarna för e-postarkivering har förbättrats, vilket gör det enklare och tydligare att kontrollera vilka e-postmeddelanden som har levererats eller misslyckats via BCC-arkivering. (NEO-10675)
* Korrigerade ett problem som ledde till att IP-adresser för belastningsutjämnare visades i stället för IP-adresser för kunder i spårningsloggarna. (NEO-11295)
* Korrigerade ett slumpmässigt problem som medförde att egenskaperna för en leverans skrevs över felaktigt. (NEO-11015)
* Korrigerade ett syntaxfel vid sortering av resultat för anrikningsaktivitet. (NEO-11394)
* Ett problem har korrigerats när beräknade fält användes i en **[!UICONTROL Survey answers]** arbetsflödesaktivitet. (NEO-11382)
* Tomcat har uppdaterats för att förhindra utnyttjande av sårbarheter. (NEO-11503)
* Korrigerade ett fel med LATIN1-kodning vid användning av en FDA-anslutning till en PostgreSQL-databas. (NEO-11299)
* Ett problem som uppstod när leveransalternativet användes har korrigerats. **[!UICONTROL Prepare the personalization data with a workflow]** (NEO-11047)
* Korrigerade ett efteruppgraderingsfel som förhindrade att SMS skickades när en utökad anslutning användes.
* Förbättrad import/export av paket (logg och region lades till i gränssnittet).
* Korrigerade ett problem som visade oanvändbara fel i efteruppgraderingsloggen när en arbetsflödesaktivitet inte var helt konfigurerad. **[!UICONTROL Survey answers]**

**Tekniska utvecklingar**

Frågeränder

En specifik nyckel (PROXYUSER eller PROXYROLE) används för att associera en Teradata-användare eller -roll med en Campaign-användare. En ny behörighet har lagts till för att använda den här proxyanvändaren/rollen. Du måste lägga till behörigheten GRANT CONNECT VIA till databaskontot (den som definieras i Teradata externa konto).

En ny flik har lagts till i Teradata externa konton. På fliken **[!UICONTROL Query banding]** finns följande alternativ:

* **[!UICONTROL Active]**: om du vill aktivera funktionen.
* **[!UICONTROL Default]**: Ange ett standardfrågeband som ska användas om en användare inte har något associerat frågeband. Om det inte finns någon standardfrågebanding definierad kan de användare som inte har någon associerad frågebanding inte använda Teradata.
* **[!UICONTROL Users]**: för varje användare anger du ett frågefält. Du kan lägga till så många nyckel-/värdepar du behöver. Till exempel: &quot;priority=1;workload=high;&quot;

Mer information om frågeflätning finns i följande artiklar:

* [https://docs.teradata.com/reader/cY5~BoeEUFWjgN2kBnH3Vw/a5G1~izve68yTMa24kVjVw](https://docs.teradata.com/reader/cY5B%7EoeEUFWjgN2kBnH3Vw/a5G1iz%7Eve68yTMa24kVjVw)
* [https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ](https://docs.teradata.com/reader/rgAb27O_xRmMVc_aQq2VGw/qVNfdszBssrZ7ttrE7AtmQ)

## Version 18.6 – build 8947{#release-18-6-build-8947}

25 juni 2018

>[!CAUTION]
>
>Det här bygget har återkallats. Uppgradera [till den senaste versionen](../../production/using/build-upgrade.md) eller kontakta [teknisk support](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

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
   <td> Adobe Campaign är nu kompatibelt med Windows Server 2016. Se <a href="https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html">kompatibilitetsmatrisen</a>för Campaign Classic.<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

decryptString

Funktionen **decryptString** är föråldrad. Mer information finns i artikeln [Borttagna och borttagna funktioner](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html) .

För nya kunder används den här funktionen nu bara för att dekryptera mottagarens krypterade ID på landningssidor. Om du vill dekryptera lösenord som lagras i ett externt konto använder du den nya **funktionen dekryptera lösenord** .

För befintliga kunder ändras inte beteendet för den här funktionen, men vi rekommenderar att du använder **decryptPassword** i stället för **decryptString**. Kompatibilitetsalternativet **XtkSecurity_Unsafe_DecryptString** läggs till av efteruppgraderingen och aktiveras som standard, vilket gör att du kan fortsätta använda funktionen. Inaktivera alternativet om du vill inaktivera **decryptString**.

decryptPassword

Funktionen **decryptPassword** har lagts till. Du kan dekryptera ett lösenord som lagras i ett externt konto. Mer information finns i [JSAPI](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html) -dokumentationen.

Fil-API:er

För nya installationer är mappåtkomst via fil-API:er begränsad till **var**-, **sftp** - och temporära mappar i Adobe Campaign.

För befintliga kunder har fil-API:er inte längre åtkomst till **conf** -mappen i Adobe Campaign. Kompatibilitetsalternativet **XtkSecurity_Disable_JSFileSandboxing** läggs till efter uppgraderingen och aktiveras som standard, vilket gör att du kan fortsätta använda de andra mapparna. Om du vill begränsa åtkomsten till **var**-, **sftp** - och temporära mappar i Adobe Campaign inaktiverar du alternativet.

**Lappa**

* Ett problem som kunde påverka SMS-transaktionsmeddelandets prestanda har åtgärdats. (NEO-9812)
