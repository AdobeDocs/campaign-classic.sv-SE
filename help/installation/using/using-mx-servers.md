---
product: campaign
title: Använda MX-servrar med Campaign
description: Se hur MX-servrar fungerar med Adobe Campaign Classic
feature: Installation, Instance Settings
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
hidefromtoc: true
exl-id: 47f50bf5-4d5b-4c07-af71-de4390177cf5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 1%

---

# Använda MX-servrar med Campaign {#using-mx-servers}



Lär dig hur MX-servrar fungerar med Adobe Campaign Classic.

## MX-servrar {#mx-servers}

### Vad är en MX-server?

En post för e-postväxlare (MX-post) är en typ av resurspost i DNS (Domain Name System) som anger en e-postserver som ansvarar för att ta emot e-postmeddelanden för en domäns räkning.

### Hur fungerar en MX-server?

När du skickar ett e-postmeddelande upprättar programservern en anslutning till den mottagande domänservern. Kommunikationen mellan de två servrarna använder SMTP-språk och en domän kan ha mer än en MX-server. Anslutningen till den här domänen börjar med den högsta prioriteten (minsta siffran) och andra servrar kallas för säkerhetskopieringsservrar. Anslutningsprotokollet måste respekteras.

### Hur fungerar en MX-server med Adobe Campaign?

I anslutningsprotokollet måste regler iakttas för att förhindra spamning och monopolering av servrar. De viktigaste är följande:

* **Maximalt antal tillåtna anslutningar**: När det här numret respekteras finns IP-adresser inte på blockeringslista och e-postmeddelanden nekas inte på grund av extra anslutningar.
* **Maximalt antal meddelanden**: Under anslutningen måste antalet meddelanden som får skickas definieras. Om det här numret inte är definierat skickas så många som möjligt av servern. Detta leder till att Internet-leverantören identifierar den som en skräppost och lägger till den i blockeringslista.
* **Meddelanden per timme**: För att matcha ditt rykte med e-post kommer Adobe Campaign att kontrollera hur många e-postmeddelanden som IP-adresserna kan skicka per timme. Det här systemet kommer att skydda dig mot e-postavslag eller/och blockeringslista.

## Studsa e-post

### Vad är ett studentmejl?

Det är den process som Adobe Campaign använder för att bearbeta fel under serverkommunikation.

### Hur fungerar ett studentmejl?

Feladressen bearbetar studsar som skickas tillbaka av Internet-leverantörer. Processen analyserar olika SMTP-felkoder och tillämpar rätt åtgärd enligt RegEx-standarden.

En e-postadress har t.ex. en feedback om &quot;550 User Unknown&quot; som skickas av en Internet-leverantör. Felkoden behandlas av Adobe Campaign feladress (retursökvägsadress). Detta fel jämförs sedan med RegEx-standarden och rätt regel gäller. E-postmeddelandet betraktas som *Hård studs* (matcha typen) och sedan *Okänd användare* (matcha orsaken) och placerade i karantän efter den första slingan i systemet.

### Hur hanterar Adobe Campaign det?

Adobe Campaign hanterar den här processen med en matchning mellan en feltyp och en orsak:

* **[!UICONTROL User Unknown]**: Adress som är syntaktiskt korrekt men inte finns. Det här felet kategoriseras som ett hårt studsande och placeras i karantän inom det första felet.
* **[!UICONTROL Mailbox full]**: Postlåda som har nått maximal kapacitet. Det här felet kan även tyda på att användaren inte längre använder den här postlådan. Det här felet kategoriseras som ett mjukt studsande och förs in i karantän inom det tredje felet och tas bort från karantänen efter en period på 30 dagar.
* **[!UICONTROL Inactive User]**: Postlådan har inaktiverats av Internet-leverantören på grund av en inaktiv användare under de senaste sex månaderna. Det här felet kategoriseras som en mjuk studsning och placeras i karantän inom det tredje felet.
* **[!UICONTROL Invalid domain]**: Domänen i e-postadressen finns inte. Det här felet kategoriseras som en mjuk studsning och placeras i karantän inom det tredje felet.
* **[!UICONTROL Refused]**: Internet-leverantören vägrade att leverera e-postmeddelandet till sina användare. Det här felet kategoriseras som ett mjukt studsande och skickas inte till karantän eftersom felet inte är länkat till e-postadressen utan IP-adress eller ett domänanseende.

>[!NOTE]
>
>Mer information om leveransfel och orsaker finns i [section](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

## Leveransinstans {#deliveratbility-env}

En daglig uppdatering av MX-reglerna och faktureringsreglerna hanteras av ett specifikt arbetsflöde i klientinstansen som är ansluten till ägaren av slutprodukten av dessa regler.

Den här dagliga uppdateringen körs för alla klienter som vill hålla sin instans uppdaterad genom en genomskinlighetsprocess.

MX-reglerna har sex olika nivåer av genomströmning som huvudsakligen används under rampprocessen:

![](assets/mx-rules-throughput.png)

Det anpassade läget är till för avancerade klienter som vill ange sina egna MX-regler. När det anpassade läget är aktiverat kommer klienten inte att uppdateras av leveransinstansen eftersom synkroniseringen kommer att inaktiveras.

## Exempel på studs

* **Okänd användare** (hård studs): 550 5.1.1 ... Användaren är okänd {mx003}
* **Postlådan är full** (mjuk studs): 550 5.2.2 Användarkvoten har överskridits
* **Inaktiv postlåda** (mjuk studsa): 550 5.7.1: Mottagaradressen avvisades: Inaktiv MailBox, inte öppnad på mer än 6 månader
* **Domänen är ogiltig** (mjuk studs): DNS-frågan misslyckades för ourdan.com
* **Avvisad** (mjuk studsa): Studsa inkommande e-post (regeln Feedback_loop_Hotmail har matchat denna studsa)
* **Onåbar** (mjuk studsa): 421 4.16.55 [TS01] Meddelanden från x.x.x.x som tillfälligt skjutits upp på grund av för många användarklagomål

**Relaterade ämnen:**
* [MX-konfiguration](../../installation/using/email-deliverability.md#mx-configuration)
* [Konfiguration av teknisk e-post](../../installation/using/email-deliverability.md)
* [Förstå leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Campaign Classic - Tekniska Recommendations](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html)
