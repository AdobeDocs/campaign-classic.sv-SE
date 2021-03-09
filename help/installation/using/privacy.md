---
solution: Campaign Classic
product: campaign
title: Integritet
description: Läs mer om de bästa sätten att följa när det gäller sekretess.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: f03554302c77a39a3ad68d47417ed930f43302b7
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 4%

---


# Integritet {#privacy}

## Sekretessförfrågningar

Adobe Campaign har en uppsättning verktyg som hjälper dig att följa integritetsefterlevnaden i GDPR och CCPA.

Se [den här sidan](../../platform/using/privacy-management.md) för allmän information om vad sekretesshantering är och implementeringsstegen i Adobe Campaign. Du hittar även bästa praxis och en översikt över användarprocessen och personerna.

## URL-anpassning

När du lägger till anpassade länkar till ditt innehåll bör du alltid undvika att ha en personalisering i värdnamnsdelen av webbadressen för att undvika eventuella säkerhetsbrister. Följande exempel ska aldrig användas i alla URL-attribut &lt;`a href="">` eller `<img src="">`:

* `<%= url >`
* `https://<%= url >`
* `https://<%= domain >/path`
* `https://<%= sub-domain >.domain.tld/path`
* `https://sub.domain<%= main domain %>/path`

### Rekommendation

Om du vill validera och försäkra dig om att du inte använder ovanstående kör du en fråga om spårning av URL-tabell via [Kampanjredigeraren för allmän fråga](../../platform/using/steps-to-create-a-query.md) eller skapar ett arbetsflöde med filtervillkor i [frågeaktiviteten](../../workflow/using/query.md).

Exempel:

1. Skapa ett arbetsflöde och lägg till en Query-aktivitet. Läs mer.

1. Öppna aktiviteten Fråga och skapa ett filter i tabellen nmsTrackingUrl enligt följande: käll-URL:en börjar med http://&lt;% eller käll-URL:en börjar med https://&lt;%.

1. Kör arbetsflödet och kontrollera om det finns några resultat.

1. I så fall öppnar du utdataövergången för att visa listan över URL-adresser.

<img src="assets/privacy-query-dynamic-url.png">

### Signaturmekanism

För att förbättra säkerheten har en ny signaturmekanism för att spåra länkar i e-postmeddelanden introducerats i version 19.1.4 (9032@3a9dc9c), som finns i version 19.1.4 (9032@3a9dc9c) och Campaign 20.2. Det här alternativet är aktiverat som standard för alla kunder.

>[!NOTE]
>
>När användaren klickar på en felformaterad signerad URL returneras följande fel: &quot;Begärd URL &#39;.. &#39; kunde inte hittas.&quot;

Dessutom kan värdkunder och hybridkunder i bygge 19.1.4 (9032@3a9dc9c och 9032@800be2e) och i Campaign 20.2 använda en förbättring för att inaktivera URL:er som genererats från tidigare byggen. Det här alternativet är inaktiverat som standard. Du kan kontakta [kundtjänst](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) för att aktivera den här funktionen.

För att aktivera den här nya mekanismen måste lokala kunder följa dessa steg på alla Campaign-servrar:

1. I serverkonfigurationsfilen (serverConf.xml) ändrar du **blockRedirectForUnsignedTrackingLink** till **true**.
1. Starta om tjänsten **nlserver**.
1. Starta om webbservern på spårningsservern (apache2 på Debian, httpd on CentOS/RedHat, IIS on Windows).

Kunder som kör Build 19.1.4 (9032@3a9dc9c) kan få problem med push-meddelandeleveranser med hjälp av spårningslänk eller leveranser med ankartaggar. I så fall rekommenderar Adobe att du inaktiverar den nya signaturfunktionen för att spåra länkar:

**Värdbaserade och hybridkunder** måste kontakta  [Customer ](https://helpx.adobe.com/se/enterprise/using/support-for-experience-cloud.html) Careto för att denna mekanism ska vara inaktiverad.

**Lokala** kunder kan följa steget nedan:

1. I serverkonfigurationsfilen (serverConf.xml) ändrar du **signEmailLinks** till **false**.
1. Starta om tjänsten **nlserver**.
1. Starta om webbservern på spårningsservern (apache2 på Debian, httpd on CentOS/RedHat, IIS on Windows).

## Databegränsning

Du måste se till att de krypterade lösenorden inte är tillgängliga för en autentiserad användare med låg behörighet. Det finns två huvudsakliga sätt: begränsa åtkomsten till lösenordsfält enbart eller till hela entiteten (behöver ett build >= 8770).

Med den här begränsningen kan du ta bort lösenordsfält men låta det externa kontot vara tillgängligt från gränssnittet för alla användare. Se [den här sidan](../../configuration/using/restricting-pii-view.md).

1. Gå in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]**.

1. Skapa en ny **[!UICONTROL Extension of a schema]**.

   ![](assets/privacy-data-restriction.png)

1. Välj **[!UICONTROL External Account]** (extAccount).

1. I den sista guideskärmen kan du redigera det nya srcSchema för att begränsa åtkomsten till alla lösenordsfält:

   Du kan ersätta huvudelementet (`<element name="extAccount" ... >`) med:

   ```
   <element name="extAccount">
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
       <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
       <element name="s3Account">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
       </element>
       <element name="wapPush">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
       <element name="mms">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
       </element>
   </element>
   ```

   Så din utökade srcSchema kan se ut så här:

   ```
   <srcSchema _cs="External Accounts (cus)" created="2017-05-12 07:53:49.691Z" createdBy-id="0"
               desc="Definition of external accounts (Email, SMS...) used by the modules"
               entitySchema="xtk:srcSchema" extendedSchema="nms:extAccount" img="" label="External Accounts"
               labelSingular="External account" lastModified="2017-05-12 08:33:49.365Z"
               mappingType="sql" md5="E9BB0CD6A4375F500027C86EA854E101" modifiedBy-id="0"
               name="extAccount" namespace="cus" xtkschema="xtk:srcSchema">
       <createdBy _cs="Administrator (admin)"/>
       <modifiedBy _cs="Administrator (admin)"/>
       <element name="extAccount">
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
           <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
   
           <element name="s3Account">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="awsSecret"/>
           </element>
           <element name="wapPush">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
           <element name="mms">
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="password"/>
               <attribute accessibleIf="$(loginId) = 0 or $(login) = 'admin'" name="clientSecret"/>
           </element>
       </element>
   </srcSchema>    
   ```

   >[!NOTE]
   >
   >Du kan ersätta `$(loginId) = 0 or $(login) = 'admin'` med `hasNamedRight('admin')` om du vill att alla användare med administratörsbehörighet ska kunna se lösenorden.

## Skydda sidor som innehåller PII

Vi rekommenderar starkt att kunder på plats skyddar sidor som kan innehålla personlig information som spegelsidor, webbprogram osv.

Målet med detta förfarande är att förhindra att dessa sidor indexeras, vilket förhindrar en potentiell säkerhetsrisk. Här är några användbara artiklar:

* [https://developers.google.com/search/reference/robots_txt](https://developers.google.com/search/reference/robots_txt)
* [https://developers.google.com/search/reference/robots_meta_tag](https://developers.google.com/search/reference/robots_meta_tag)
* [https://www.google.com/webmasters/tools/robots-testing-tool](https://www.google.com/webmasters/tools/robots-testing-tool)

Följ de här stegen för att skydda sidorna:

1. Lägg till en robots.txt-fil i webbserverns rot (Apache eller IIS). Här är filens innehåll:

   ```
   # Make changes for all web spiders
   User-agent:
   *Disallow: /
   ```

   Information om IIS finns på [den här sidan](https://docs.microsoft.com/en-us/iis/extensions/iis-search-engine-optimization-toolkit/managing-robotstxt-and-sitemap-files).

   För Apache kan du placera filen i **/var/www/robots.txt** (Debian).

1. Ibland räcker det inte att lägga till en **robots.txt**-fil när det gäller säkerhet. Om en annan webbplats till exempel innehåller en länk till sidan kan den visas i ett sökresultat.

Förutom filen **robots.txt** bör du lägga till en **X-Robots-Tag**-rubrik. Du kan göra det i Apache eller IIS och i konfigurationsfilen **serverConf.xml**.

Mer information finns i [den här artikeln](https://developers.google.com/search/reference/robots_meta_tag).
