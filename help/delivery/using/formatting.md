---
product: campaign
title: Formatering
description: Formatering
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Email Design
role: User, Developer, Data Engineer
exl-id: d9688dc4-20c6-4a9a-990f-465f39b2faa2
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 0%

---

# Formatering{#formatting}

## JavaScript-mallar {#javascript-templates}

En JavaScript-mall är ett HTML- eller textdokument som innehåller JavaScript-kod. Den är konstruerad på samma sätt som ett e-postinnehåll i en leveransåtgärd.

### Identifiering av en JavaScript-mall {#identification-of-a-javascript-template}

En JavaScript-mall identifieras av sitt namn och namnutrymme på samma sätt som scheman och formulär. Vi rekommenderar dock att du lägger till **.js** till mallnamnet.

### Struktur för en JavaScript-mall {#structure-of-a-javascript-template}

Exempel på en JavaScript HTML-formateringsmall som baseras på &quot;cus:book&quot;-schemat:

```
<html>
  <body>
    <!-- Title of book -->
    <h1><%= content.@name %></h1>
    <ul>
      <% for each(var chapter in content.chapter) { %>
        <li><%= chapter.@name %></li>
      <% }%>
    </ul>
  </body>
</html>
```

De olika JavaScript-direktiven visas i följande format:

* Sammanfoga fält: visar innehållet i data med **`<%= <source> %>`** syntax där `<source>`är källfältet för de data som ska visas.
* Instruktionsblock: kör en serie JavaScript-instruktioner som finns mellan &lt;% och %>-taggarna.

The **innehåll** -objektet representerar huvudelementet i XML-indatadokumentet.

I följande exempel visas innehållet i namnet book name:

```
<h1><%= content.@name %></h1>
```

Följande kod itererar på `<chapter>` samlingselement:

```
<% for each(var chapter in content.chapter) { %>
  <li><%= chapter.@name %></li>
<% }%>
```

Innehållets attribut och element representeras som JavaScript-objekt och följer källdokumentets struktur.

**Exempel**:

* **innehåll.@name**: hämtar värdet för huvudelementets name-attribut
* **innehåll.@`['name']`**: identisk med **innehåll.@name** syntax
* **content.kapitel.length**: returnerar antalet element på `<chapter` samlingselement
* **content.kapitel`[0]`.@name**: hämtar namnet på den första `<chapter>` element
* **chapter.name()**: returnerar namnet på `<chapter>` element
* **chapter.parent().name()**: returnerar namnet på det överordnade elementet för `<chapter>`

>[!CAUTION]
>
>Eftersom tecknet &#39;-&#39; är reserverat i JavaScript-språket måste alla attribut och element som innehåller det här tecknet återställas via `['<field>']` syntax.
>
>Till exempel: `content.@['offer-id']`.

Alla funktioner i ett programmeringsspråk (variabler, slingor, villkorstester, funktioner etc.). ) är tillgängligt för att skapa utdatadokumentet. SOAP API:er är tillgängliga för att berika utdatadokumentet.

Exempel:

* Villkorstest:

  ```
  <% if (content.@number == 1 || content.@language == 'en') { %>
  <!-- Content to be displayed if test is true--> 
  <% } %>
  ```

* Funktionsanrop:

  ```
  <!-- Displays a horizontal bar -->
  ;<% function DisplayHorizontalBar() { %>
    <hr/>
  <% } %> 
  
  <!-- The same function in a block  -->
  <% 
  function DisplayHorizontalBar2()
  {
    document.write('<hr/>');
  }
  %> 
  
  <!-- Returns the value in uppercase -->
  <% 
  function formatName(value)
  { 
    return value.toUpperCase(); 
  }
  %>
  
  <!-- Call functions -->
  <%= DisplayHorizontalBar1() %>
  <%= DisplayHorizontalBar2() %>
  <%= formatName(content.@name) %>
  ```

* Deklarationer och variabelanrop:

  ```
  <%  var counter = 0; %>
  
  <%= counter += 10 %>
  ```

* Hämta och visa ett mottagarnamn med statiska metoder:

  ```
  <% var recipient = nms.recipient.get(1246); %>
  <%= recipient.lastName %>
  ```

* Återställning och visning av ett mottagarnamn med icke-statiska metoder:

  ```
  <% var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr="@id=1246"/>
      </where>
    </queryDef>);
  
    var recipient = query.ExecuteQuery();
  %>
  
  <%= recipient.@lastName %>
  ```

### Inkludera en JavaScript-mall {#including-a-javascript-template}

Du kan skapa ett bibliotek med funktioner eller variabler för senare bruk. Om du vill göra det importerar du JavaScript-mallen med **eval** funktion. På så sätt kan du förbättra kontexter med ytterligare funktioner som deklarerats i andra JavaScript-mallar.

**Exempel**: importerar **common.jsp** mall.

```
<% eval(xtk.javascript.get("cus:common.js").data);  %>
```

### Redigera en JavaScript-mall {#editing-a-javascript-template}

Med redigeringszonen kan du fylla i innehållet i JavaScript-mallen:

![](assets/d_ncs_content_form16.png)

>[!NOTE]
>
>Det associerade datamodellschemat måste fyllas i för initiering av JavaScript-objekt.

Om du vill generera en förhandsgranskning av utdatadokumentet markerar du ett innehåll och ett utdataformat (HTML, Text, XML) och klickar sedan på **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form17.png)

>[!NOTE]
>
>Du behöver inte spara ändringarna för att kunna förhandsgranska utdatadokumentet.

### Exempel på hur du skapar och använder en JavaScript-mall {#example-of-how-to-create-and-use-a-javascript-template}

Nedan hittar du den konfiguration som krävs för att implementera följande innehållshantering med en JavaScript-mall:

![](assets/d_ncs_content_sample_1.png)

I det här exemplet beskrivs följande steg:

1. Skapa följande schema (i det här fallet: **neo:news**):

   ```
   <srcSchema _cs="Invitation (neo)"   entitySchema="xtk:srcSchema" img="xtk:schema.png" label="Invitation" mappingType="sql" name="news" namespace="neo" xtkschema="xtk:srcSchema">
   
     <enumeration basetype="string" default="en" name="language">
       <value label="Français" name="fr" value="fr"/>
       <value label="English" name="gb" value="gb"/>
     </enumeration>
   
     <enumeration basetype="string" name="css">
       <value label="Blue" name="bl" value="blue"/>
       <value label="Orange" name="or" value="orange"/>
     </enumeration>
   
     <element label="Intervenants" name="attendee">
       <key internal="true" name="id">
         <keyfield xpath="@id"/>
       </key>
       <attribute label="Name" name="name" type="string"/>
       <element label="Image" name="image" target="xtk:fileRes" type="link"/>
       <attribute label="Description" name="description" type="string"/>
       <attribute default="Gid()" label="Id" name="id" type="long"/>
     </element>
   
     <element label="Invitation" name="news" template="ncm:content" xmlChildren="true">
   
       <compute-string expr="@name"/>
       <attribute enum="language" label="Language" name="language" type="string"/>
       <attribute enum="css" label="Stylesheet" name="css" type="string"/>
       <attribute label="Title" name="title" type="string"/>
       <element label="Presentation" name="presentation" type="html"/>
       <attribute label="Date" name="date" type="date"/>
       <element label="Attendees list" name="attendeesList" ordered="true" ref="attendee" unbound="true"/>
   
     </element>
   </srcSchema>
   ```

1. Skapa den länkade **[!UICONTROL Content management]** textform (**neo:news**)

   ```
   <form _cs="News (neo)" entitySchema="xtk:form"  img="xtk:form.png" label="News"  name="news" namespace="neo" type="contentForm" xtkschema="xtk:form">
   
     <container type="iconbox">
       <container label="Invitation">
         <input xpath="@langue"/>
         <input xpath="@css"/>
         <input xpath="@title"/>
         <input xpath="@date"/>
         <input xpath="presentation"/>
       </container>
   
       <container label="Intervenants">
         <container toolbarCaption="Liste des intervenants" type="notebooklist" xpath="attendeesList" xpath-label="@nom">
           <container>
             <input xpath="@nom"/>
             <input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
               <sysFilter>
                 <condition expr="@isImage = true"/>
               </sysFilter>
             </input>
             <input xpath="@description"/>
           </container>
         </container>
       </container>
     </container>
   
   </form>
   ```

1. Skapa JavaScript-mallarna med meddelandeinnehåll för HTML och textformat.

   * I vårt exempel, för HTML:

     ```
     <html>     
       <head>         
         <title>Newsletter</title>
          <style type="text/css">
           .body {font-family:Verdana, Arial, Helvetica, sans-serif; font-size:10px; color:#514c48; margin-left: auto; margin-right: auto;}
           .body table {width:748; border: solid 1px; cellpadding:0; cellspacing:0"}
          </style>
       </head>     
       <body>
         <p><center><%= mirrorPage %></center></p>
         <center>
           <table>      
            <tr>
             <td>                                                         
               <img src="[LOGO]"/>                                   
             </td>
             <td>
               <h1><%= content.@title %></h1>
             </td>
            </tr>
            <tr>
     
            <td>
             <div >                                    
               <h0><%= hello,</h0>                              
               <p><%= content.presentation %></p>                                          
     
               <h0>Useful information</h0>                              
               <p>                                  
                 <img src="[IMAGE 1]"/>When? <br/><%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.</p><br/>                                       
               <p>                                  
                 <img src="[IMAGE 2]"/>Who? <br>Meet our favorite authors and illustrators and get a signed copy of their book.</p><br/>                                                         
               <p>                                  
                 <img src="[IMAGE 3]"/>Attendance is free but there is a limited number of seats: sign up now!</p>
           </div>
           </td>
     
             <td>                                                    
              <div style="text-align:left; width:210; height:400px; background:url([IMAGE DE FOND])">
     
                 <h0><%= participant %></h0>
                 <%
                 var i
                 var iLength = content.attendeesList.length()
                 for (i=0; i<iLength; i++)
                 { %>
                 <p>
                   <%= generateImgTag(content.attendeesList[i].@["image-id"]) %>  <%= content.attendeesList[i].@description %>
                 </p>  
                 <% }  
                 %>                              
              </div2>
             </td>
         </tr>
       </table>
     </center>
     </body>    
     </html>
     ```

   * För texten:

     ```
     <%= content.@title %>
     <%= content.presentation %>
     
     *** When? On <%= formatDate(content.@date, "%2D %Bl %4Y") %> From 10 AM in your bookshop.
     
     *** Who? Come and meet our favorite authors and illustrators and get a signed copy of their books. 
     
     *** Attendance is free but there is a limited number of seats: sign up now!
     
     Guests:
     ******************
     <%
     var i
     var iLength = content.attendeesList.length()
     //for (i=(iLength-1); i>-1; i--)
     for( i=0 ; i<iLength ; i++ )
       { %>
       Description <%= i %> : <%= content.attendeesList[i].@description %>
       <% }  
     %>
     ```

1. Skapa nu en publiceringsmall som används för båda formaten:

   * För HTML:

     ![](assets/d_ncs_content_sample_2.png)

   * För text:

     ![](assets/d_ncs_content_sample_3.png)

1. Du kan sedan använda den här innehållsmallen i dina leveranser.

   Mer information finns i [Använda en innehållsmall](using-a-content-template.md).

## XSL-formatmallar {#xsl-stylesheets}

Med XSLT-språk kan du ändra ett XML-dokument till ett utdatadokument. Beroende på formatmallens utdatametod kan det resulterande dokumentet genereras i HTML, oformaterad text eller ett annat XML-träd.

Omformningen beskrivs i sin tur i XML i ett dokument som kallas formatmall.

### Identifiera en formatmall {#identifying-a-stylesheet}

En formatmall identifieras av sitt namn och namnutrymme, precis som scheman och formulär. Vi rekommenderar dock att du lägger till **.xsl** tillägg till formatmallens namn.

Identifieringsnyckeln för en formatmall är en sträng som består av namnutrymmet och namnet avgränsat med ett kolon, till exempel: **cus:book.xsl**.

### Struktur för en formatmall {#structure-of-a-stylesheet}

Exempel på en formateringsmall för HTML baserad på exempelschemat &quot;cus:book&quot;:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>
  <!-- Point of entry of the stylesheet -->
  <xsl:template match="/book">
    <html>
      <body>
        <!-- Book title -->
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <!-- List of chapters -->
          <xsl:for-each select="child::chapter">
            <li><xsl:value-of select="@name"/></li>
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

En formatmall är ett XML-dokument som följer följande regler:

* attributvärdena ligger mellan citattecken,
* ett element måste ha en öppningsmarkör och en slutmarkör,
* ersätt tecknen &#39;&lt;&#39; eller &#39;&amp;&#39; med **&#39;&lt;&#39;** eller **&#39;&amp;&#39;** enheter,
* varje XSL-element måste använda **xsl** namnutrymme.

En formatmall måste börja med XSL-rotelementets markör **`<xsl:stylesheet>`** och avsluta med **`</xsl:stylesheet>`** markör. XSL-namnutrymmet måste definieras i öppningsmarkören enligt följande:

```
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

The **`<xsl:output>`** -element anger formatet för det dokument som genereras. Ange önskad teckenuppsättning och utdataformat.

```
<xsl:output encoding="ISO-8859-1" method="html"/>
```

Följande instruktioner beskriver formatmallens konfiguration för formateringen av utdatadokumentet.

```
<xsl:template match="/book">
  <html>
    <body>
      <!-- Book title -->
      <h1><xsl:value-of select="@name"/></h1>
      <lu>
        <!-- List of chapters -->
        <xsl:for-each select="child::chapter">
          <li><xsl:value-of select="@name"/></li>
        </xsl:for-each>
      </lu>
    </body>
  </html>
</xsl:template>
```

Som standard söker XSLT-processorn efter **mall** som gäller för rot- eller huvudnoden i XML-indatadokumentet. Byggandet av utdatadokumentet börjar med det här **mall**.

I vårt exempel genereras en HTML-sida från &quot;cus:book&quot;-schemat genom att bokens namn och listan med kapitel visas.

>[!NOTE]
>
>Mer information om XSLT-språket finns i ett XSLT-referensdokument.

### Visa HTML/XML {#displaying-html-xml}

Visa en **html** fält, använd **disable-output-escape=&quot;yes&quot;** från **`<xsl:value-of>`** -direktivet. På så sätt kan du undvika att ersätta tecken med deras XML-enhet (till exempel &lt; med &lt;).

The **`<xsl:text>`** -direktivet med **disable-output-escape=&quot;yes&quot;** gör att du kan infoga JavaScript-taggar för anpassningsfält eller villkorstester.

Exempel:

* Visa innehållet i ett fält av typen&quot;html&quot;:

  ```
  <xsl:value-of select="summary" disable-output-escaping="yes"/>
  ```

* Infoga anpassningsfältet **&lt;%= mottagare.email %>**:

  ```
  <xsl:text disable-output-escaping="yes"><%= recipient.email %></xsl:text>
  ```

* Lägga till villkorstestet **&lt;% if (mottagare.språk == &#39;en&#39;) `{` %>**:

  ```
  <xsl:text disable-output-escaping="yes"><% if (recipient.language == 'en') { %></xsl:text>
  ```

### Inkludera formatmallar {#including-stylesheets}

Du kan skapa ett bibliotek med mallar eller variabler som ska delas mellan flera formatmallar. The &quot;longMonth&quot; **mall**(se ovan) är ett typiskt exempel på fördelarna med att fjärrsöka efter en mall i en formatmall så att den kan återanvändas senare.

The **`<xsl:include>`** -direktivet anger namnet på den formatmall som ska inkluderas i dokumentet.

**Exempel**: inklusive formatmallen&quot;common.xsl&quot;.

```
<? xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:include href="common.xsl"/> 
  <xsl:output encoding="ISO-8859-1" method="jsp" indent="yes"/>
  ...
</xsl:stylesheet>
```

>[!NOTE]
>
>Namnutrymmets namn får inte anges i referensen till den formatmall som ska inkluderas. Som standard skapas den här formatmallen med användarnamnutrymmet.

### Redigera en formatmall {#editing-a-stylesheet}

Med redigeringszonen kan du fylla i formatmallens innehåll:

![](assets/d_ncs_content_form14.png)

Om du vill generera en förhandsgranskning av utdatadokumentet markerar du en innehållsinstans och formatet (HTML, Text, XML) och klickar sedan på **[!UICONTROL Generate]** :

![](assets/d_ncs_content_form15.png)

>[!NOTE]
>
>Du behöver inte spara ändringarna i formatmallen för att kunna förhandsgranska utdatadokumentet.

## Bildhantering {#image-management}

### Bildreferenser {#image-referencing}

De bilder som anges i utdatadokumentet för HTML kan refereras med absoluta eller relativa referenser.

Med Relativ referens kan du ange webbadressen till servern som innehåller bilderna i **NcmRessourcesDir** och **NcmRessourcesDirPreview** alternativ. Dessa alternativ innehåller platsen för bilder som ska publiceras och förhandsgranskas i Adobe Campaign klientkonsol.

De här två alternativen är tillgängliga via alternativhanteringsskärmen i dialogrutan **[!UICONTROL Administration > Platform > Options]** mapp.

**Exempel**:

* NcmResourcesDir = &quot;https://server/images/&quot;
* NcmResourcesDirPreview = &quot;x:/images/&quot;

Vid bearbetning av formatmallar **_resPath** -attributet på huvudelementet i XML-indatadokumentet fylls automatiskt i med ett eller flera av alternativen beroende på sammanhanget (förhandsgranskning eller publicering).

Exempel på hur du använder bildplaceringsalternativet och dess användning med en bild:

```
<img src="<%= content.@_resPath %>/newsletter/image.png"/>
```

>[!NOTE]
>
>Vi rekommenderar att du deklarerar en variabel som innehåller referensen för servern där bilderna lagras (&quot;resPath&quot; i vårt exempel).

### Använda offentliga resurser {#using-public-resources}

Du kan också använda **[!UICONTROL Public resources]** för att deklarera bilder och överföra dem till servern beroende på instansinställningarna som anges i distributionsguiden.

Du kan sedan anropa dessa bilder i innehållet. Om du vill göra det använder du följande syntax i innehållshanteringsschemat:

```
<element label="Image" name="image" target="xtk:fileRes" type="link"/>
```

I formuläret läggs fältet för att välja bilden till med följande syntax:

```
<input img="nl:sryimage.png" newEntityFormChoice="true" xpath="image">
    <sysFilter>
      <condition expr="@isImage = true"/>
    </sysFilter>
  </input>
```

>[!NOTE]
>
>Om du vill ha mer **[!UICONTROL Public resources]** och hur du konfigurerar och använder dem, se [det här avsnittet](../../installation/using/deploying-an-instance.md#managing-public-resources).

## Datumvisning {#date-display}

I XML-indatadokumentet sparas datumen i ett internt XML-format: **`YYYY/MM/DD HH:MM:SS`** (exempel `2018/10/01 12:23:30`).

Adobe Campaign tillhandahåller datumformateringsfunktioner för JavaScript-mallar och XSL-formatmallar som beskrivs nedan.

### JavaScript-datumformatering {#javascript-date-formatting}

För att visa ett datum i det önskade formatet innehåller Adobe Campaign **formatDate** funktion som tar innehållet i datumet och en sträng som anger utdataformatet med följande syntax: **%4Y/%2M/%2D %2H%2N%2S**

Exempel:

* Visa datumet i **31/10/2018** format:

  ```
   <%= formatDate(content.@date, "%2D/%2M/%4Y") %>
  ```

* Visa datumet i **Juli 2018** format:

  ```
  <%
   function displayDate(date)
    {
      var aMonth = 
      [ 'January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December' ];
  
      var month = formatDate(content.@date, "%2M")
      var year = formatDate(content.@date, "%4Y")
  
      return aMonth[month-1]+" "+year;
    }
  %>
  
  <%= displayDate(content.@date) %>
  ```

### XSL-datumformatering {#xsl-date-formatting}

Det finns ingen standardfunktion för datumhantering i XSLT-syntax. För att visa ett datum i det önskade formatet tillhandahåller Adobe Campaign den externa funktionen **date-format**. Den här funktionen tar innehållet i datumet som indata och en sträng som anger utdataformatet med följande syntax: **%4Y/%2M/%2D %2H%2N%2S**

Exempel:

* Visa datumet i **01/10/2018** format:

  ```
  <xsl:value-of select="external:date-format(@date, '%2D/%2M/%4Y')"/>
  ```

* Visa datumet i **Juli 2018** format:

  ```
  <!-- Returns the month in the form of a string with the month number as input -->
  <xsl:template name="longMonth">
    <xsl:param name="monthNumber"/>
  
    <xsl:choose>
      <xsl:when test="$monthNumber = 1">January</xsl:when>
      <xsl:when test="$monthNumber = 2">February</xsl:when>
      <xsl:when test="$monthNumber = 3">March</xsl:when>
      <xsl:when test="$monthNumber = 4">April</xsl:when>
      <xsl:when test="$monthNumber = 5">May</xsl:when>
      <xsl:when test="$monthNumber = 6">June</xsl:when>
      <xsl:when test="$monthNumber = 7">July</xsl:when>
      <xsl:when test="$monthNumber = 8">August</xsl:when>
      <xsl:when test="$monthNumber = 9">September</xsl:when>
      <xsl:when test="$monthNumber = 10">October</xsl:when>
      <xsl:when test="$monthNumber = 11">November</xsl:when>
      <xsl:when test="$monthNumber = 12">December</xsl:when>
    </xsl:choose>
  </xsl:template> 
  
  <!-- Display date -->
  <xsl:call-template name="longMonth">
    <xsl:with-param name="monthNumber">
      <xsl:value-of select="external:date-format(@date, '%2M')"/>
    </xsl:with-param>
  </xsl:call-template>
   <xsl:value-of select="external:date-format(@date, '%4y')"/>
  ```
