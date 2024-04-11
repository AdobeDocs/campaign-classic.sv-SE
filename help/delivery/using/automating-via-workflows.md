---
product: campaign
title: Automatisera via arbetsflöden
description: Lär dig automatisera innehållshantering via arbetsflöden
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Workflows
role: User
exl-id: bc6ebf5d-cc21-4750-9713-2bf259e7d6bf
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 0%

---

# Automatisera med arbetsflöden{#automating-via-workflows}

## Innehållshanteringsaktivitet {#content-management-activity}

Det går att automatisera skapandet, redigeringen och publiceringen med hjälp av ett arbetsflöde som konfigurerats via Adobe Campaign klientgränssnitt.

The **Innehållshantering** -aktiviteten nås via **[!UICONTROL Tools]** i arbetsflödesdiagrammet.

Aktivitetsegenskaperna delas in i fyra steg:

* **[!UICONTROL Content]** : låter dig ange befintligt innehåll eller skapa innehåll,
* **[!UICONTROL Update content]** : låter dig ändra innehållets ämne eller uppdatera innehållet via ett XML-dataflöde,
* **[!UICONTROL Action to execute]** : låter dig spara eller generera innehåll,
* **[!UICONTROL Transition]** : låter dig välja om du vill generera en utdataövergång och ge den ett namn.

![](assets/d_ncs_content_wf.png)

### Innehåll {#content}

* **Anges av övergången**

  Innehållet som ska användas har skapats tidigare. Processerna rör den innehållsinstans som sprids av den inkommande händelsen. Innehållsidentifieraren nås via händelsens contentId-variabel.

* **Explicit**

  Gör att du kan välja innehåll som du skapat tidigare.

* **Beräknas av ett skript**

  Väljer en innehållsinstans baserad på en JavaScript-mall. Med den kod som ska utvärderas kan du hämta innehållsidentifieraren.

* **Nytt, skapat via en publiceringsmall**

  Skapar ett nytt innehåll via en publiceringsmall. Innehållsinstansen sparas i den ifyllda strängmappen.

### Uppdatera innehållet {#update-the-content}

* **Ämne**

  Gör att du kan ändra föremålet för leveransåtgärden vid publicering.

* **Åtkomst till data från en XML-feed**

  Innehållet uppdateras från en XML-feed från en extern källa. En URL måste anges för att nedladdning av data ska ske.

  En XSL-formatmall kan användas för att omforma inkommande XML-data.

### Åtgärd som ska köras {#action-to-execute}

* **Spara**

  Sparar det skapade eller ändrade innehållet. Identifieraren för det sparade innehållet sprids i variabeln contentId för den utgående händelsen.

* **Generera**

  Genererar utdatafilerna för varje omformningsmall med en publikation av typen &quot;Fil&quot;. Den utgående övergången aktiveras för varje genererad fil med följande parametrar: identifieraren för innehållet som sparats i variabeln contentId och filnamnet i variabeln filename.

### Övergång {#transition}

The **Generera en utdataövergång** kan du lägga till en utdataövergång i **[!UICONTROL Content management]** aktivitet som länkar en ny aktivitet till körning av arbetsflöde. När du har markerat det här alternativet anger du en etikett för övergången.

## Exempel {#examples}

### Automatisera framtagning och leverans av innehåll {#automating-content-creation-and-delivery}

I följande exempel automatiseras skapandet och leveransen av ett innehållsblock.

![](assets/d_ncs_content_workflow2.png)

Innehållet konfigureras via aktiviteten Innehållshantering:

![](assets/d_ncs_content_workflow3.png)

En ny innehållsinstans skapas via publiceringsmodellen och innehållssträngsmappen.

I vårt exempel har vi överbelastat leveransämnet. Den kommer att tas med i stället för den som anges i **[!UICONTROL Delivery]** mall.

Innehållet fylls i automatiskt av ett XML-flöde som kommer från den URL som anges:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

Dataformatet matchar inte det dataschema som anges i publiceringsmallen (**cus:bok** i vårt exempel); **`<section>`** -elementet måste ersättas med **`<chapter>`** -element. Vi måste använda formatmallen&quot;cus:book-workflow.xsl&quot; för att kunna göra nödvändiga ändringar.

Källkod för XSLT-formatmallen som används:

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

Den sista åtgärden i aktiviteten är att spara innehållsinstansen och fortsätta till nästa uppgift.

Riktlinjerna genomförs via **Fråga** aktivitet.

An **AND-join** aktiviteten lades till för att säkerställa att leveransen bara startas när målfrågan och innehållsuppdateringarna är klara.

Leveransåtgärden konfigureras via **Leverans** aktivitet:

![](assets/d_ncs_content_workflow4.png)

En ny leveransåtgärd skapas utifrån en mall.

Leveransmallen för aktiviteten används för att välja omformningsmallarna för publiceringsmallen. Vid generering av innehåll tas hänsyn till alla HTML- och textmallar utan leveransmallar eller mallar som refereras till med samma mall som aktiviteten.

Målet som ska levereras anges via den inkommande händelsen.

Leveransinnehållet fylls i via den inkommande händelsen.

Det sista steget i att slutföra aktiviteten är att förbereda och sedan starta leveransen.

### Skapa innehåll för senare publicering {#creating-content-and-publishing-it-later}

I det här exemplet skapas ett innehållsblock och filpubliceringen startas efter en viss tidsfördröjning.

![](assets/d_ncs_content_workflow5.png)

Den första **Innehållshantering** skapar en innehållsinstans.

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>The **[!UICONTROL Publication]** -fliken i fönstret med omformningsmallar måste fyllas i med platsen för det mål som ska genereras.

En väntande aktivitet läggs till för att pausa nästa övergång i en vecka.

![](assets/d_ncs_content_workflow7.png)

Innehåll anges manuellt under den här tidsperioden.

Nästa uppgift startar genereringen av innehåll.

![](assets/d_ncs_content_workflow8.png)

Innehållet som ska publiceras anges via den inkommande övergången.

Den sista åtgärden är att generera innehållet genom att tvinga fram publikationskatalogen.

The **JavaScript-kod** aktiviteten hämtar det fullständiga namnet för varje genererad fil.

![](assets/d_ncs_content_workflow9.png)

### Skapa leveransen och dess innehåll {#creating-the-delivery-and-its-content}

I det här exemplet används samma koncept som i det första exemplet, men bara leveransåtgärden skapas i det första steget.

![](assets/d_ncs_content_workflow10.png)

Den första **Skapa leverans** skapar leveransåtgärden.

Med gaffelaktiviteten kan du starta målberäkning och skapa innehållsinstansen parallellt.

När åtgärderna har utförts aktiverar AND-join-rutan **Leverans** för att lansera den tidigare leveransen av innehåll och målinriktning.

![](assets/d_ncs_content_workflow11.png)

Leveransåtgärden som ska startas fylls i via övergången.

Målet som ska levereras anges via den inkommande händelsen.

Leveransinnehållet fylls i via den inkommande händelsen.

Den sista åtgärden i aktiviteten är att förbereda och starta leveransen.

### Importera innehåll från FTP {#importing-content-from-ftp}

Om ditt leveransinnehåll finns i en HTML-fil på FTP- eller SFTP-servrar kan du enkelt läsa in det i Adobe Campaign-leveranser. Se [detta exempel](../../workflow/using/loading-delivery-content.md).

### Importera innehåll från kopplingen för Amazon Simple Storage Service (S3) {#importing-content-from-amazon-simple-storage-service--s3--connector}

Om ditt leveransinnehåll finns i Amazon Simple Storage Service (S3)-bucket kan du enkelt läsa in det i Adobe Campaign-leveranser. Se [detta exempel](../../workflow/using/loading-delivery-content.md).

## Halvautomatisk uppdatering {#semi-automatic-update}

Innehållsdata kan uppdateras i halvautomatiskt läge. Data återställs från ett XML-flöde via en URL.

Aktiveringen av dataåterställning sker manuellt via inmatningsformuläret.

Målet är att deklarera en **editBtn** type **`<input>`** i formuläret. Den här kontrollen består av en redigeringszon och en knapp för att starta bearbetningen.

Med redigeringszonen kan du fylla i variabeldata som används för att skapa URL:en för XML-flödet med data som ska hämtas.

Knappen kör **GetAndTransform** SOAP-metod ifylld under **`<input>`** -tagg.

Kontrolldeklarationen i formuläret är följande:

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

The **GetAndTransform** -metoden måste deklareras under **`<enter>`** -elementet i **`<input>`** -tagg. Den här taggen fungerar som parametrar för URL-återställningen av XML-data från ett uttryck som konstruerats dynamiskt. Den andra parametern för funktionen är valfri och refererar till en formatmall som används för en mellanliggande omformning när inkommande XML-data inte har samma format som innehållet.

Utdata uppdaterar innehållet baserat på den sökväg som angavs i den sista parametern.

**Exempel**: För att illustrera det här exemplet börjar vi från &quot;cus:book&quot;-schemat.

Ett halvautomatiskt indataformulär för redigeringskontroll för uppdatering läggs till:

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://myserver.adobe.com/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

I redigeringszonen kan du ange namnet på filen som ska hämtas. URL:en skapas utifrån det här namnet, till exempel: https://myserver.adobe.com/incomin/data.xml

Formatet på de data som ska hämtas är detsamma som i exempel 1 av automatisering av arbetsflöden. Vi ska använda formatmallen&quot;cus:book-workflow.xsl&quot; som finns i det här exemplet.

Resultatet av jobbkörningen uppdaterar innehållsinstansen från sökvägen &#39;.&#39;.
