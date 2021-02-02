---
solution: Campaign Classic
product: campaign
title: Version 19.2
description: Version 19.2
audience: rns
content-type: reference
topic-tags: latest-release-notes
translation-type: tm+mt
source-git-commit: b5b9e42eca25193cf4d69f654e74a02afd8adca9
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 9%

---


# Version 19.2{#release-19-2}

## ![](assets/do-not-localize/limited_2.png) Version 19.2.4 – build 9082 {#release-19-2-4-build-9082}

_23 december 2020_

>[!CAUTION]
>
> * Den här versionen innehåller ett nytt anslutningsprotokoll: Om du ansluter till Campaign via Adobe Identity Service (IMS) är uppgradering obligatoriskt för både Campaign-servern och klientkonsolen för att kunna ansluta till Campaign efter den 31 mars 2021 **.**
   >
   > 
* Den här versionen innehåller en [säkerhetskorrigering](https://helpx.adobe.com/security/products/campaign/apsb21-04.html): uppgradering är obligatoriskt för att öka din miljösäkerhet.



* Anslutningsprotokollet har uppdaterats för att följa den nya IMS-autentiseringsmekanismen.
* Korrigerade ett säkerhetsproblem för att förstärka skyddet mot problem med SSRF (Server Side Request Forgery). (NEO-27777)

## ![](assets/do-not-localize/red_2.png) Version 19.2.3 – build 9081 {#release-19-2-3-build-9081}

_7 februari 2020_

**Förbättringar**

* Korrigerade ett regressionsproblem på grund av implementeringen av SSL-certifieringen som gjorde att användaranslutningen misslyckades på Windows-servern. (NEO-20629)
* Ett problem som visade ett felaktigt versionstaggnummer på menyn **Om** har korrigerats.

## ![](assets/do-not-localize/red_2.png) Version 19.2 – build 9080 {#release-19-2-build-9080}

_2 december 2019_

**Nyheter**

<table> 
 <thead> 
  <tr> 
   <th> <strong>California Consumer Privacy Act (CCPA)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>CCPA är delstaten Kaliforniens nya integritetslagstiftning som harmoniserar och moderniserar dataskyddskraven som träder i kraft den 1 januari 2020. CCPA gäller Adobe Campaign-kunder som lagrar data för registrerade i Kalifornien.</p>
    <p>Förutom de sekretessfunktioner som redan finns (inklusive samtyckeshantering, datalagringsinställningar och användarroller) kan Adobe Campaign underlätta din beredskap för CCPA:</p>
    <ul>
      <li>Rätt till åtkomst och rätt att ta bort: vi utnyttjar de funktioner som tillkommit för GDPR. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#righttoaccess">Läs mer</a></li>
      <li>Ni kan spåra om en konsument har valt att sälja personuppgifter. Därför måste du utöka profiltabellen och lägga till ett <strong>avanmäl dig för CCPA</strong>-fält. <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html#ccpa">Läs mer</a></li></td> 
  </tr> 
 </tbody> 
</table>

<table> 
 <thead> 
  <tr> 
   <th> <strong>Övervakning av direktarbetsflöde</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <p>Nu kan du övervaka körningsstatusen för alla arbetsflöden på instansen med fördefinierade vyer.</p>
   <p>Mer information finns i den <a href="../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status">detaljerade dokumentationen</a>.</p></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Interaktivt material med AMP</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Med Adobe Campaign kan du testa det nya interaktiva <a href="https://amp.dev/about/email/">AMP for Email</a>-formatet, som gör att marknadsförarna kan inkludera AMP-komponenter i meddelanden för att förbättra e-postupplevelsen med avancerat, dynamiskt och interaktivt innehåll som kan användas direkt i själva meddelandet.</p>
   <p>Den här funktionen lanseras som en betaversion.</p>
   <p>Mer information finns i den <a href="../../delivery/using/defining-interactive-content.md">detaljerade dokumentationen</a> och <a href="https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html">självstudievideon</a>.</p><br /></td> 
  </tr> 
 </tbody> 
</table>


<table> 
 <thead> 
  <tr> 
   <th> <strong>Säkra SMS-meddelanden (TLS)</strong><br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
<td> <p>Skyddat SMS stöds nu via den utökade allmänna SMPP-anslutningen. Detta tillåter en krypterad anslutning till providern.</p> <p><strong>Varning </strong> Den här funktionen kräver ett aktuellt certifikat på alla servrar. Ogiltiga, återkallade eller utgångna certifikat genererar fel som påverkar SMS-sändningsfunktionerna.</p><p>Mer information finns i den <a href="https://helpx.adobe.com/se/campaign/kb/sms-connector-protocol-and-settings.html">detaljerade dokumentationen</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Säkerhetsförbättringar**

* Korrigerade säkerhetsluckor med cross site scripting i Campaign-gränssnittet - validering av indata och utdatakodning. (NEO-16810)
* Ett säkerhetsproblem i profilauktoriseringen som kunde ge åtkomst till obehöriga data har åtgärdats genom att principen för begränsning av inloggning förstärks. (NEO-14445)

**Förbättringar**

* Optimering av minnesförbrukning för push-meddelanden.
* Hanteringen av filen **logins.log** har förbättrats för optimering av prestanda och lagring. Filen delas nu upp i flera filer, en gång om dagen med högst 365 filer bevarade. [Läs mer](../../production/using/log-files.md)
* Det externa Microsoft Dynamics CRM-kontot kan nu konfigureras med hjälp av lösenordsautentiseringsuppgifter (lösenord + användarnamn) eller certifikat (privat nyckel). [Läs mer](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)
* Vissa förbättringar har lagts till i Hadoop FDA-anslutningen för att förbättra tillförlitligheten
* En särskild skyddsmodul har lagts till för att kontrollera diskutrymmet innan offentliga resurser kan överföras till servern.
* Nya [kampanjalternativ](../../installation/using/configuring-campaign-options.md) har lagts till:
   * Med konfigurationsalternativet **WdbcKillSessionPolicy** kan du påverka **ovillkorlig Stop**-funktion för alla arbetsflöden och PostgreSQL-databasfrågor.
   * Med alternativet **NmsOperation_DeliveryPreparationWindow** kan du definiera antalet dagar över vilka leveranser med inkonsekvent status ska uteslutas från antalet pågående leveranser.
   * Med alternativet **WdbcOptions_TempDbName** kan du konfigurera en separat databas för fungerande tabeller på Microsoft SQL Server. Detta optimerar säkerhetskopiering och replikering. [Läs mer](../../production/using/rdbms-specific-recommendations.md#microsoft-sql-server)
   * Alternativet **XtkCleanup_NoStats** har förbättrats för PostgreSQL för att bättre kunna styra beteendet för lagringsoptimeringssteget i databasrensningsarbetsflödet. [Läs mer](../../production/using/database-cleanup-workflow.md#statistics-update)
* En mekanism för kontoutelåsning har lagts till i API:t **logon()**. Det förhindrar ytterligare inloggningsförsök efter ett visst antal misslyckade inloggningsförsök i följd inom en angiven tidsram.
* Med ett nytt **alternativ för maximal körtid för personalisering** i leveransegenskaperna kan du definiera en timeout-period för personalisering, för att förhindra att personaliseringsfasen körs för länge. [Läs mer](../../delivery/using/personalization-fields.md#timing-out-personalization)
* Alternativet **ftp protocol** har lagts till så att du kan använda en proxykonfiguration för SFTP-anslutningar. [Läs mer](../../installation/using/configuring-campaign-server.md#proxy-connection-configuration)
* Nytt stöd för proxyåtkomst till en extern SFTP-server för lokala miljöer.
* Ett specifikt skyddsutkast har lagts till för att förhindra installation av paket som inte är kompatibla med Campaign-instansen. [Läs mer](../../installation/using/installing-campaign-standard-packages.md)

_Föråldrade system_

Följande system är nu [inaktuella](https://helpx.adobe.com/se/campaign/kb/deprecated-and-removed-features.html) för implementeringar av Campaign Classic:
* Apache 2.2
* Centrum 6

Kontrollera att du har de versioner av alla system som stöds och som finns i den senaste kampanjkompatibilitetsmatrisen. [Läs mer](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html)

_Campaign Mobile SDK_

Version 1.0.26 av iOS SDK är nu tillgänglig. I den här nya versionen har vi lagt till stöd för iOS 13. Den nya versionen har nu stöd för meddelandeprioritet och den nya processen för hantering av registreringstoken för push-meddelanden i iOS 13. Om du kör program på en tidigare version av SDK måste du kompilera om programmen med den nya SDK:n. Kontakta [Adobe kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att få SDK.

**Felkorrigeringar**

* Korrigerade ett kraschproblem när fältet **Lägg till länkad tabell** var tomt i arbetsflödesaktiviteten **Datainläsning (RDBMS)**. (NEO-12213)
* Korrigerade ett problem som kunde leda till att vissa meddelanden inte bearbetades av servern för medelkällkod. (NEO-12395)
* Korrigerade ett problem i databasrensningsarbetsflödet när frågebandningsalternativet användes med Teradata. (NEO-12399)
* Ett problem som påverkade leveransanalysen med typologiregeln inklusive domänen ne.jp har korrigerats. (NEO-12609)
* Korrigerade ett problem relaterat till SMS över TLS-uppdateringar som innebar en mer restriktiv certifikatprincip. Uppdateringarna kan leda till ett anslutningsfel mellan marknadsförings- och mellanleverantörsservrar om certifikatet är inaktuellt. (NEO-17698)
* Ett problem har korrigerats när knappen **Testa anslutningen** användes på ett externt konto i en miljö med flera källor och vaultautentisering användes. (NEO-12722)
* Korrigerade ett problem med frågor som använder datumfunktioner med en FDA Hadoop-anslutning. (NEO-12847)
* Korrigerade ett problem när en bild skulle ersättas i e-postredigeraren. (NEO-13098)
* Korrigerade ett problem som kan leda till fel efter uppgraderingen i mappar som har tagits bort eller flyttats till en annan plats. (NEO-13118)
* Korrigerade ett fel vid bildvisning när alternativet **Definiera bild per enhet och skärmstorlek** användes i LINE-meddelanden. (NEO-13228)
* Ett leveransförberedelseproblem har korrigerats när alternativet **Uteslut dubblettadress under leverans** inte har valts. (NEO-13240)
* Korrigerade ett problem i arbetsflöden när aktiviteten **Filöverföring** användes för att hämta filer med alternativet **Ta bort källfilerna efter överföring**, med ett namn som innehåller ett blanksteg. (NEO-13411)
* Ett problem med rensning av Tomcat-cachen som kan leda till minnesproblem har åtgärdats. (NEO-13456)
* Ett problem har korrigerats vid installation av **kontrollen av erbjudandemotorn med körningsinstansen** inbyggt paket på en befintlig kontrollinstans som körs i Microsoft SQL 2017. (NEO-13539)
* Korrigerade ett kraschproblem i konsolen som kunde inträffa när spårade URL:er i ett e-postmeddelande avkontrollerades från fliken **Textinnehåll** på grund av en variabel som inte initierats. (NEO-13545)
* Korrigerade ett kodningsproblem för det kinesiska avsändarnamnet. (NEO-13837)
* Korrigerade ett fel som kunde uppstå när undersökningssvarsdata från Utforskaren visades. (NEO-14590)
* Korrigerade ett problem som kunde leda till diskrepans mellan leveransloggklassificeringen och karantäntabellen. (NEO-16547)
* Ett problem med DKIM-nycklar som inte var inbäddade i e-postmeddelanden har korrigerats. (NEO-16804)
* Korrigerade ett problem som visade fel felkod när en ogiltig sessionstoken användes i kontexten för API-anrop för att utlösa händelser. Felkoden var HTTP 200 OK i stället för HTTP 403 Forbidden. (NEO-16826)
* Ett problem som orsakade att leveransrapporter visades via webbåtkomst har korrigerats. (NEO-17015)
* Ett IMS-autentiseringsproblem som uppstod vid inloggning på Adobe Campaign har korrigerats. (NEO-17312)
* Korrigerade ett problem som förhindrade att e-postmeddelanden i karantän togs bort av sekretesshanteringsprocessen. (NEO-17314)
* Problem med genomströmning har korrigerats efter uppgradering till 9031 med SQL-databas. (NEO-17558)
* Ett problem som påverkade CRM Connector med Salesforce har korrigerats. (NEO-17712)
* Ett timeout-problem vid import av data från en extern SFTP har korrigerats. (NEO-19723)
* Ett problem har korrigerats vid åtkomst till prediktiva modeller. (NEO-19713)
* Korrigerade ett problem som påverkade slumpmässig sampling i **Dela** arbetsflödesaktivitet med Hadoop FDA-databas. (NEO-16636)
* Korrigerade en regression på Oracle som gjorde att vissa funktioner ansågs vara ogiltiga efter efteruppgraderingen. (NEO-12759)


