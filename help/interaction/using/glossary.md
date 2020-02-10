---
title: Ordlista
seo-title: Ordlista
description: Ordlista
seo-description: null
page-status-flag: never-activated
uuid: 7c96d243-99d8-4402-9e2a-75beb8b2fbee
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: interaction-overview
discoiquuid: 5b2b7682-6bac-4282-8d27-e8a259934e7d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Ordlista{#glossary}

Nedan finns definitionen av de huvudsakliga interaktionselementen.

* **Miljö**: som innehåller en erbjudandekatalog och krokar (erbjudandeplatser). Ni måste skapa en miljö genom att inrikta er på olika aspekter. Det finns två typer av miljöer:

   * **Designmiljö**: miljö där erbjudanden skapas och/eller typologiregler definieras (regler som avgör vilka erbjudanden som ska presenteras eller inte visas för en målperson). Tabellen över de enskilda personer som erbjudandena riktar sig till och tabellen för lagring av alla erbjudandeförslag definieras också här. Noden innehåller undermappar för **[!UICONTROL Design environment]** utrymme, fördefinierade filter och kategorier för erbjudanden. För varje **[!UICONTROL Design environment]** finns det en motsvarande skrivskyddad **[!UICONTROL Live environment]** som genereras av samma **[!UICONTROL Design environment]**.
   * **Live-miljö**: miljö som är länkad till en **[!UICONTROL Design environment]**. Det innehåller skrivskyddade erbjudanden vars innehåll och behörighet har godkänts via **[!UICONTROL Design environment]**. De ska väljas för att presenteras på en webbplats eller infogas i ett meddelande.

* **Utrymme**: mapp som definierar platsen där erbjudandet visas. Om du definierar ett mellanslag kan du ange vilken kanal som ska användas, ange om den kan användas i enställningsläge eller inte (som standard: endast i gruppläge), bygg innehållet i erbjudandet med hjälp av återgivningsfunktioner och ange erbjudandet. Ett blanksteg är ett gränssnitt mellan kanalen och erbjudandemotorn.

   >[!CAUTION]
   >
   >Ett erbjudandeutrymme är inte en kommunikationskanal, det sammanfaller med en specifik exponeringsplats i kanalen. Erbjudanden som visas på en webbplats kan till exempel innehålla två mellanslag på samma sida. I det här fallet har vi två mellanslag för samma kanal.
   >
   >Blanksteg måste definieras i specifikationerna och får inte ändras under projektet.

* **Erbjudandekatalog**: en uppsättning erbjudanden som definieras i Adobe Campaign och som kan väljas under en interaktion. Katalogen ordnas hierarkiskt med varje nod som motsvarar en kategori.
* **Kategori**: en mapp som är länkad till erbjudandekatalogen i en miljö, där erbjudandena ordnas baserat på typ, datum för behörighet och programtema. En kategori kan innehålla underkategorier, som ärver alla egenskaper i den överordnade kategorin. Kvalifikationsregler kan definieras för en kategori så att de kan delas för flera erbjudanden.
* **Programteman**: nyckelord som definieras i kategorin, vilket gör att du kan filtrera erbjudanden när de presenteras för en inkommande eller utgående kanal genom att begränsa urvalet av erbjudanden till en eller två kategorier.

   >[!NOTE]
   >
   >Underordnade kategorier ärver de teman som identifieras i den överordnade kategorin.

* **Villkor**: Begränsningar som tillämpas på en miljö, kategori eller erbjudande avseende giltighetsperiod, mål och vikt. Med dem kan ni se till att ett erbjudande är i linje med den avsedda kontakten.

   I miljöerna omfattar reglerna för rätt till uppgradering presentationsregler som tillämpas på erbjudandena och vilka personer som ska målgruppsanpassas.

   I kategorierna kan du begränsa kategoriens giltighet i tid, definiera programteman och avgöra vilka personer som ska väljas. De kan också få en multiplikatvikt för en viss tidsperiod. På så sätt kan du dela reglerna för erbjudanden i andra kategorier och på så sätt förenkla hanteringen av dem.

   I erbjudandena kan ni begränsa giltigheten för erbjudanden i tid och avgöra vilka personer som ska målgruppsanpassas.

* **Godtycke**: välja erbjudanden som ska visas i en miljö (berättigade erbjudanden). Principen om arbitrage rangordnar erbjudanden efter prioritet enligt de kriterier som definieras i kategorierna, erbjudandena och sammanhangserbjudandena.
* **Kontakt**: en kontakt från en inkommande interaktion. Under motorsamtalsbearbetningen är kontakten kopplad till en måldimension. Det finns två typer av kontakter:

   * **[!UICONTROL Identified contact]** : en kontakt som frivilligt har identifierats i kanalen. Vid utgående interaktioner identifieras kontakten automatiskt.
   * **[!UICONTROL Anonymous contact]** : en kontakt som inte frivilligt har prenumererat via kanalen men som kan identifieras implicit via en cookie. Den här terminologin används bara för inkommande interaktioner.

      >[!NOTE]
      >
      >Ej identifierade anonyma kontakter tillskrivs besökarens målgruppsdimension.

* **Utgående interaktion**: anrop till interaktionsmotorn från en kontaktlista (används för att leverera e-post, direktreklam osv.). Samma regler och processer tillämpas för varje kontakt. Den här typen av interaktion bearbetas vanligtvis i gruppläge.
* **Inkommande interaktion**: interaktion efter ett inkommande samtal som genererats av åtgärden för en kontakt i kanalen. Den här typen av interaktion bearbetas vanligtvis i enskärmsläge.
* **Batchläge**: I gruppläge kan du välja det bästa erbjudandet för en uppsättning kontakter. Regler för behörighet/prioritering tillämpas på alla kontakter i uppsättningen. Det här läget används vanligtvis för utgående interaktioner.
* **Enhetsläge**: en enda kontakt bearbetas åt gången. Det här läget används vanligtvis för inkommande interaktioner och transaktionsmeddelanden.
* **Identifieringsläge**: hänvisar till en kontakts status.

   * **[!UICONTROL explicit]** : kontakten identifieras efter inloggningen i kanalgränssnittet.
   * **[!UICONTROL implicit]** : kontakten har identifierats genom en cookie (permanent eller session). Den kan behandlas som en anonym eller identifierad kontakt.
   * **[!UICONTROL anonymous]** : kontakten inte kan identifieras.

* **Berättigat erbjudande**: erbjudandet uppfyller de krav som definieras uppströms och som konsekvent kan erbjudas ett mål.
* **Presentationsregler**: typologiregler som refereras i erbjudandemiljön, som gör att du kan exkludera vissa erbjudanden genom att ta hänsyn till förslagshistoriken.
* **Bredd**: formler som gör det möjligt att exakt beräkna hur relevant ett erbjudande är för att välja det mest relevanta erbjudandet. Vikten definieras i erbjudandena. Berättigade erbjudanden beaktas i minskande viktordning.
* **Återgivningsfunktion**: funktionen som definieras i erbjudandeutrymmet för att konstruera sin offertrepresentation utifrån de attribut som definieras i erbjudandet. Det finns tre olika återgivningsfunktionslägen: HTML, XML och text.
* **Erbjudande**: resultatet av åtgärden som består av att presentera ett eller flera erbjudanden för en kontakt i ett visst utrymme (banderoll på en webbplats, ett e-postmeddelande eller ett SMS-meddelande). Det här resultatet lagras i tabellen för erbjudandeförslag. Det är dock inte obligatoriskt att spara förslagen.
* **Simulering**: som gör att du kan testa hur erbjudandet visas för målmottagarna innan du skickar erbjudandena.
* **Förhandsgranska**: förhandsgranskning av erbjudandet så som det visas i dess mapp. Den är tillgänglig från inställningsfönstret för erbjudandet eller kontaktprofilen.
* **Fördefinierade filter**: fördefinierade filtreringsregler kan ta hänsyn till erbjudandeparametrar (till exempel en erbjudandekod). De kan återanvändas efter att erbjudandena har skapats.
* **Erbjudanderepresentation**: information som används av kanalen för att visa erbjudandet. Erbjudanderepresentationen kan skapas med hjälp av återgivningsfunktionen i det utrymme där erbjudandet finns representerat eller anges direkt i gränssnittet (t.ex. i HTML-blocket). Ett erbjudande kan representeras av space.
* **Övergångsprocess**: en aktiverad process i en identifierad miljö som ansvarar för att dirigera anropet till en anonym miljö om kontakten inte uttryckligen och/eller implicit har identifierats.

