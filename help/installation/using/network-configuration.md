---
product: campaign
title: Nätverkskonfiguration
description: Läs riktlinjerna för systemkommunikation
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: b86236ae-95e9-4406-b60f-6d90ad0d4a01
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 2%

---

# Nätverkskonfiguration{#network-configuration}



## Kommunikation mellan processer {#communication-between-processes}

Vissa processer i programmet måste kommunicera med andra eller för att få tillgång till LAN och Internet. Detta innebär att vissa TCP-portar måste vara öppna för dessa processer.

Använd den inbäddade Apache Tomcat-porten som prioritet (8080 som standard) för intern kommunikation mellan olika programservrar på en Adobe Campaign-plattform.

### Leveransserver {#delivery-server}

För leveransservern (**nlserver mta**) måste följande portar vara öppna:

<table> 
 <tbody> 
  <tr> 
   <td> Portar<br /> </td> 
   <td> Mål<br /> </td> 
   <td> Kommentar<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> SMTP-trafik för e-postutsändning.<br /> </td> 
  </tr> 
  <tr> 
   <td> 53/udp (domän)<br /> </td> 
   <td> DNS-servrar<br /> </td> 
   <td> DNS-frågor.<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (standardport)<br /> </td> 
   <td> SMS-gateway<br /> </td> 
   <td> Används för att skicka SMS-trafik till NetSize SMS-routern [alternativ].<br /> </td> 
  </tr> 
  <tr> 
   <td> 7777/udp<br /> </td> 
   <td> Statistikserver<br /> </td> 
   <td> Åtkomst till statistikservern.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Inkommande e-post {#inbound-mail}

För processen för återställning av inkommande e-post (**nlserver inMail**) måste följande portar vara öppna:

<table> 
 <tbody> 
  <tr> 
   <td> Portar<br /> </td> 
   <td> Mål<br /> </td> 
   <td> Kommentar<br /> </td> 
  </tr> 
  <tr> 
   <td> 110/tcp (pop3)<br /> </td> 
   <td> Intern e-postserver<br /> </td> 
   <td> POP3-trafik för att hämta studsmeddelanden.<br /> </td> 
  </tr> 
  <tr> 
   <td> 25/tcp (smtp)<br /> </td> 
   <td> Intern e-postserver<br /> </td> 
   <td> SMTP-trafik för att skicka återstående studsmeddelanden som inte bearbetas automatiskt av de fördefinierade reglerna.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Programserver {#application-server}

För programservern (**nlserver web**) måste följande portar vara öppna:

<table> 
 <tbody> 
  <tr> 
   <td> Portar<br /> </td> 
   <td> Mål<br /> </td> 
   <td> Kommentar<br /> </td> 
  </tr> 
  <tr> 
   <td> 80/tcp (http)<br /> 443/tcp (https)<br /> </td> 
   <td> Anywhere<br /> </td> 
   <td> HTTP- eller HTTPS-trafik (inklusive för leveranserbjudandet).<br /> </td> 
  </tr> 
 </tbody> 
</table>

När flera programservrar på en Adobe Campaign-plattform behöver kommunicera med varandra rekommenderar vi att du använder porten på Apache Tomcat-servern (som standard: 8080) i stället för HTTP-porten på webbservern som integreringen av omdirigeringsmodulen utfördes med. Detta innebär att porten måste vara öppen mellan dessa servrar.

### SMS-leveransstatus {#sms-delivery-status}

För att spåra SMS-leveranser (**nlserver sms**) måste följande port vara öppen:

<table> 
 <tbody> 
  <tr> 
   <td> Portar<br /> </td> 
   <td> Mål<br /> </td> 
   <td> Kommentar<br /> </td> 
  </tr> 
  <tr> 
   <td> 38000/tcp (standardport)<br /> </td> 
   <td> SMS-gateway<br /> </td> 
   <td> Frågar status för leveranskön som hanteras av SMS-gatewayen för NetSize [alternativ].<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Rich Client {#rich-client}

För Adobe Campaign Rich Client (**nlclient**) måste följande portar vara öppna:

<table> 
 <tbody> 
  <tr> 
   <td> Portar<br /> </td> 
   <td> Mål<br /> </td> 
   <td> Kommentar<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p>443/tcp (https)</p><br /> </td> 
   <td> Programserver<br /> </td> 
   <td> SOAP-trafik (HTTP).<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Databasåtkomst {#database-access}

Alla komponenter som använder databasen måste kunna ansluta till den. Detta gäller de flesta komponenter, med undantag för omdirigeringsservern, som kan fungera fristående, och den tunna Win32-klienten, som bara använder HTTP (eller HTTPS) för att kommunicera med programservern.

Standardportarna är följande:

<table> 
 <tbody> 
  <tr> 
   <td> Databastyp<br /> </td> 
   <td> Port (standard)<br /> </td> 
   <td> Mål<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> 1521/tcp<br /> </td> 
   <td> Databasserver<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>PostgreSQL</strong><br /> </td> 
   <td> 5432/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Microsoft SQL Server</strong><br /> </td> 
   <td> 1433/tcp<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>DB2</strong><br /> </td> 
   <td> 50000/tcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Extern åtkomst {#external-access}

Dessutom måste vissa komponenter vara tillgängliga från det publika Internet så att e-postkampanjer som körs direkt från Adobe Campaign kan visas. Det innebär att vissa portar måste vara öppna för komponenter.

### Omdirigeringsserver {#redirection-server}

<table> 
 <tbody> 
  <tr> 
   <td> Avlyssningsport<br /> </td> 
   <td> Plats<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Var som helst. Varje klickning på en spårad länk genererar en HTTP-begäran på servern.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Extern webbserver {#external-web-server}

Den här servern är värd för webbformulär, spegelsidor osv. Följande portar måste vara öppna:

<table> 
 <tbody> 
  <tr> 
   <td> Avlyssningsport<br /> </td> 
   <td> Plats<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Var som helst. Nödvändigt när webbformulär hanteras direkt från Adobe Campaign eller när spegelsidor används.<br /> </td> 
  </tr> 
 </tbody> 
</table>

### Intern programserver (webb) {#internal-application-server--web-}

<table> 
 <tbody> 
  <tr> 
   <td> Avlyssningsport<br /> </td> 
   <td> Plats<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 80/tcp (http)</p><p> 443/tcp (https)</p><br /> </td> 
   <td> Alla datorer som kör den tunna klienten eller den avancerade klienten.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Integrering med Adobe Experience Manager {#integration-with-adobe-experience-manager}

Integrering mellan Adobe Campaign och Adobe Experience Manager kräver att flera portar öppnas om installationen är lokal. Mer information om hur du konfigurerar integreringen finns i [detaljerad dokumentation](../../integrations/using/about-adobe-experience-manager.md).

<table> 
 <tbody> 
  <tr> 
   <td> Avlyssningsport<br /> </td> 
   <td> Beskrivning<br /> </td> 
  </tr> 
  <tr> 
   <td> 80<br /> </td> 
   <td> AEM anslutning till Adobe Campaign<br /> </td> 
  </tr> 
  <tr> 
   <td><p> 4502</p><p> 4503</p><br /> </td> 
   <td> Adobe Campaign-anslutning till AEM"authoring" och"publishing"-instanser. Portarna som ska öppnas kan skilja sig från standardportarna, beroende på AEM konfiguration.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Bandbredd {#bandwidth}

En annan nyckelparameter i nätverkskonfigurationen som ska beaktas. Det är nästan alltid utgående och mycket efterfrågat under e-postsändningar. Här är några exempel på konfigurationer som bygger på vår erfarenhet:

* 1 MB/s för 10 000 e-postmeddelanden per timme (genomsnittlig storlek 30 kB)
* 8 till 10 MB/s för 100 000 e-postmeddelanden per timme (genomsnittlig storlek 30 kB)

Om ni har begränsningar i fråga om bandbredd är det möjligt att schemalägga kampanjer som ska köras under natten när efterfrågan är lägre.
