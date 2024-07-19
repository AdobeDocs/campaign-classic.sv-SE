---
product: campaign
title: Ordlista för kampanjintegrering
description: Ordlista för kampanjintegrering
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 9e199b7c-9307-4797-bf86-7940388555bc
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Ordlista för kampanjintegrering{#i-glossary}



Nedan finns definitionen av de huvudsakliga interaktionselementen.

* **Miljö**: en uppsättning som innehåller en erbjudandekatalog och kopplingar (erbjudandeutrymmen). Ni måste skapa en miljö genom att inrikta er på olika aspekter. Det finns två typer av miljöer:

   * **Designmiljö**: En miljö där erbjudanden skapas och/eller typologiregler definieras (regler som avgör vilka erbjudanden som ska visas eller inte visas för en målperson). Tabellen över de enskilda personer som erbjudandena riktar sig till och tabellen för lagring av alla erbjudandeförslag definieras också här. Noden **[!UICONTROL Design environment]** innehåller utrymmesundermappar, fördefinierade filter och kategorier för erbjudanden. För varje **[!UICONTROL Design environment]** finns det en motsvarande skrivskyddad **[!UICONTROL Live environment]** som genereras från samma **[!UICONTROL Design environment]**.
   * **Live-miljö**: miljö länkad till en **[!UICONTROL Design environment]**. Den innehåller skrivskyddade erbjudanden vars innehåll och behörighet har godkänts via **[!UICONTROL Design environment]**. De ska väljas för att presenteras på en webbplats eller infogas i ett meddelande.

* **Erbjud utrymme**: mapp som definierar platsen där erbjudandet visas. Genom att definiera ett utrymme kan du ange vilken kanal som används, ange om den kan användas i enställningsläge (som standard: endast i gruppläge), bygga innehållet i erbjudandet med hjälp av återgivningsfunktioner och ange erbjudandet. Ett blanksteg är ett gränssnitt mellan kanalen och erbjudandemotorn.

  >[!IMPORTANT]
  >
  >Ett erbjudandeutrymme är inte en kommunikationskanal, det sammanfaller med en specifik exponeringsplats i kanalen. Erbjudanden som visas på en webbplats kan till exempel innehålla två mellanslag på samma sida. I det här fallet har vi två utrymmen för samma kanal.
  >
  >Blanksteg måste definieras i specifikationerna och får inte ändras under projektet.

* **Erbjudandekatalog**: en uppsättning erbjudanden som definieras i Adobe Campaign och som kan väljas under en interaktion. Katalogen ordnas hierarkiskt med varje nod som motsvarar en kategori.
* **Kategori**: en mapp som är länkad till erbjudandekatalogen i en miljö, där erbjudandena ordnas baserat på typ, berättigandedatum och programtema. En kategori kan innehålla underkategorier, som ärver alla egenskaper i den överordnade kategorin. Kvalifikationsregler kan definieras för en kategori så att de kan delas för flera erbjudanden.
* **Programteman**: nyckelord som definieras i kategorin, vilket gör att du kan filtrera erbjudanden när de presenteras för en inkommande eller utgående kanal genom att begränsa urvalet av erbjudanden till en eller två kategorier.

  >[!NOTE]
  >
  >Underordnade kategorier ärver de teman som identifieras i den överordnade kategorin.

* **Kvalifikationsregler**: Begränsningar för en miljö, kategori eller erbjudande som gäller giltighetsperiod, mål och vikt. De gör att ni kan försäkra er om att ett erbjudande är i linje med den avsedda kontakten.

  I miljöerna omfattar reglerna för rätt till uppgradering presentationsregler som gäller för erbjudandena och de personer som ska väljas ut.

  I kategorierna kan du begränsa kategoriens giltighet i tid, definiera programteman och avgöra vilka personer som ska väljas. De kan också få en multiplikatvikt för en viss tidsperiod. På så sätt kan du dela reglerna för erbjudanden i andra kategorier och på så sätt förenkla hanteringen av dem.

  I erbjudandena kan ni begränsa giltigheten för erbjudanden i tid och avgöra vilka personer som ska väljas ut.

* **Medling**: välja erbjudanden som ska visas i en miljö (giltiga erbjudanden). Principen om arbitrage rangordnar erbjudanden efter prioritet enligt de kriterier som definieras i kategorierna, erbjudandena och sammanhangserbjudandena.
* **Kontakt**: en kontakt från en inkommande interaktion. Under motorsamtalsbearbetningen är kontakten kopplad till en måldimension. Det finns två typer av kontakter:

   * **[!UICONTROL Identified contact]** : en kontakt som frivilligt har identifierats i kanalen. Vid utgående interaktioner identifieras kontakten automatiskt.
   * **[!UICONTROL Anonymous contact]** : en kontakt som inte frivilligt har prenumererat via kanalen men som kan identifieras implicit via en cookie. Den här terminologin används bara för inkommande interaktioner.

     >[!NOTE]
     >
     >Ej identifierade anonyma kontakter tillskrivs besökarens målgruppsdimension.

* **Utgående interaktion**: anrop till interaktionsmotorn från en kontaktlista (används för att leverera e-post, direktreklam osv.). Samma regler och processer tillämpas för varje kontakt. Den här typen av interaktion bearbetas vanligtvis i gruppläge.
* **Inkommande interaktion**: interaktion efter ett inkommande samtal som genererats av åtgärden för en kontakt i kanalen. Den här typen av interaktion bearbetas vanligtvis i enskärmsläge.
* **Gruppläge**: I gruppläget kan du välja det bästa erbjudandet för en uppsättning kontakter. Regler för behörighet/prioritering tillämpas på alla kontakter i uppsättningen. Det här läget används vanligtvis för utgående interaktioner.
* **Enhetsläge**: en enskild kontakt bearbetas åt gången. Det här läget används vanligtvis för inkommande interaktioner och transaktionsmeddelanden.
* **Identifieringsläge**: refererar till en kontakts status.

   * **[!UICONTROL explicit]** : kontakten identifieras efter inloggning i kanalgränssnittet.
   * **[!UICONTROL implicit]** : kontakten har identifierats av en cookie (permanent eller session). Den kan behandlas som en anonym eller identifierad kontakt.
   * **[!UICONTROL anonymous]** : det går inte att identifiera kontakten.

* **Berättigat erbjudande**: Erbjudandet uppfyller de begränsningar som definierats uppströms och som konsekvent kan erbjudas ett mål.
* **Presentationsregler**: typologiregler som refereras i erbjudandemiljön, som gör att du kan exkludera vissa erbjudanden genom att ta hänsyn till förslagshistoriken.
* **Vikt**: formler som gör att du kan beräkna relevansen för ett erbjudande exakt för att välja det mest relevanta erbjudandet. Vikten definieras i erbjudandena. Berättigade erbjudanden beaktas i minskande viktordning.
* **Återgivningsfunktion**: funktion definierad i erbjudandeutrymmet för att skapa sin offertrepresentation baserat på attributen som definieras i erbjudandet. Det finns tre olika återgivningsfunktionslägen: HTML, XML och text.
* **Erbjudandeerbjudande**: resultatet av åtgärden som består av att presentera ett eller flera erbjudanden för en kontakt i ett givet utrymme (banner på en webbplats, ett e-postmeddelande eller ett SMS-meddelande till exempel). Det här resultatet lagras i tabellen för erbjudandeförslag. Det är dock inte obligatoriskt att spara förslagen.
* **Simulering**: Med modulen kan du testa erbjudandepresentationen för målmottagarna innan du skickar erbjudandena.
* **Förhandsgranska**: förhandsgranskning av erbjudandet så som det visas i dess mapp. Den är tillgänglig från inställningsfönstret för erbjudandet eller kontaktprofilen.
* **Fördefinierade filter**: fördefinierade filtreringsregler kan ta hänsyn till erbjudandeparametrar (till exempel en erbjudandekod). De kan återanvändas efter att erbjudandena har skapats.
* **Erbjudanderepresentation**: information som används av kanalen för att visa erbjudandet. Erbjudanderepresentationen kan utformas med hjälp av återgivningsfunktionen i det utrymme som erbjudandet avser eller anges direkt i gränssnittet (t.ex. i blocket HTML). Ett erbjudande kan representeras av space.
* **Övergångsprocess**: En aktiverad process i en identifierad miljö, som ansvarar för att dirigera anropet till en anonym miljö om kontakten inte har identifierats explicit och/eller implicit.
