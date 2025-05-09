---
product: campaign
title: Konfigurera säkerhetszoner
description: Lär dig konfigurera säkerhetszoner
feature: Installation, Instance Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 67dda58f-97d1-4df5-9648-5f8a1453b814
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1452'
ht-degree: 0%

---

# Definiera säkerhetszoner (lokalt){#defining-security-zones}



Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Säkerhetszonskonfigurationen utförs i Adobe Campaign-serverns konfigurationsfil.

Operatorer är länkade till en säkerhetszon från sin profil i konsolen, som är tillgänglig i noden **[!UICONTROL Administration > Access management > Operators]**. [Läs mer](#linking-a-security-zone-to-an-operator).

>[!NOTE]
>
>Den här proceduren är begränsad till **lokala**-distributioner.
>
>Om du är en **värdbaserad**-kund och har åtkomst till [Campaign Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv) kan du använda självbetjäningsgränssnittet i säkerhetszonen. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=sv-SE)
>
>Andra **hybridkunder/värdkunder** måste kontakta Adobe supportteam för att kunna lägga till IP i tillåtelselista.
>

## Skapa säkerhetszoner {#creating-security-zones}

En zon definieras av:

* ett eller flera intervall med IP-adresser (IPv4 och IPv6)
* ett tekniskt namn som är associerat med varje IP-adressintervall

Säkerhetszoner är låsta, vilket innebär att om du definierar en ny zon inom en annan zon minskar antalet operatorer som kan logga in på den samtidigt som de rättigheter som tilldelats varje operator ökas.

Zoner måste definieras under serverkonfigurationen i filen **serverConf.xml** . Alla parametrar som är tillgängliga i **serverConf.xml** listas i [det här avsnittet](../../installation/using/the-server-configuration-file.md).

Varje zon definierar rättigheter, till exempel:

* HTTP-anslutning i stället för HTTPS
* Felvisning (Java-fel, JavaScript, C++ osv.)
* Report and webApp preview
* Autentisering via inloggning/lösenord
* Osäkert anslutningsläge

>[!NOTE]
>
>**Varje operator måste länkas till en zon**. Om operatorns IP-adress tillhör det intervall som definieras av zonen kan operatorn logga in på instansen.\
>Operatorns IP-adress kan definieras i flera zoner. I det här fallet tar operatorn emot **uppsättningen** tillgängliga rättigheter för varje zon.

Filen **serverConf.xml** som är klar att användas innehåller tre zoner: **public, VPN och LAN**.

>[!NOTE]
>
>**Konfigurationen som är klar att användas är säker**. Innan du migrerar från en tidigare version av Adobe Campaign kan det dock vara nödvändigt att tillfälligt minska säkerheten för att migrera och godkänna de nya reglerna.

Exempel på hur du definierar en zon i filen **serverConf.xml**:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

Alla rättigheter som definierar en zon är följande:

* **allowDebug**: aktiverar en webApp som ska köras i felsökningsläge
* **allowEmptyPassword**: auktoriserar en anslutning till en instans utan lösenord
* **allowHTTP**: Det går att skapa en session utan att använda HTTPS-protokollet
* **allowUserPassword**: sessionstoken kan ha följande format: `<login>/<password>`
* **sessionTokenOnly**: Säkerhetstoken krävs inte i anslutnings-URL
* **showErrors**: fel på serversidan vidarebefordras och visas

>[!IMPORTANT]
>
>I en zondefinition minskar varje attribut med värdet **true** säkerheten.

Om det finns flera körningsinstanser när du använder Message Center måste du skapa ytterligare en säkerhetszon med attributet **sessionTokenOnly** definierat som **true**, där endast de nödvändiga IP-adresserna ska läggas till. Mer information om hur du konfigurerar instanser finns i [det här dokumentet](../../message-center/using/configuring-instances.md).

## Bästa tillvägagångssätt för säkerhetszoner {#best-practices-for-security-zones}

I definitionen av säkerhetszonen **lan** kan du lägga till en IP-adressmask som definierar teknisk åtkomst. Det här tillägget ger åtkomst till alla instanser på servern.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

Vi rekommenderar att du definierar IP-adressintervall direkt i konfigurationsfilen som är dedikerad till instansen för operatorer som bara har åtkomst till en viss instans.

I filen **`config-<instance>.xml`**:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

## Undernätverk och proxy i en säkerhetszon {#sub-networks-and-proxies-in-a-security-zone}

Parametern **proxy** kan användas i ett **subNetwork**-element för att ange proxyanvändning i en säkerhetszon.

När en proxy refereras och en anslutning matas in via den här proxyn (visas via HTTP X-Forwarded-For-huvudet), är den verifierade zonen den som klienterna för proxyn och inte proxyns.

>[!IMPORTANT]
>
>Om en proxy är konfigurerad och det går att åsidosätta den (eller om den inte finns), kommer den IP-adress som testas att kunna förfalskas.
>
>Dessutom genereras nu reläer som proxies. Du kan därför lägga till IP-adressen 127.0.0.1 i listan över proxies i säkerhetszonskonfigurationen.
>
>Till exempel: `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`.

Olika fall kan inträffa:

* Ett undernätverk refereras direkt i säkerhetszonen och ingen proxy är konfigurerad: användare i undernätverket kan ansluta direkt till Adobe Campaign-servern.

  ![](assets/8101_proxy1.png)

* En proxy har angetts för ett undernätverk i säkerhetszonen: användare från det här undernätverket har åtkomst till Adobe Campaign-servern via den här proxyn.

  ![](assets/8101_proxy2.png)

* En proxy ingår i ett undernätverk för säkerhetszoner: användare som har åtkomst via den här proxyn, oavsett ursprung, har åtkomst till Adobe Campaign-servern.

  ![](assets/8101_proxy3.png)

IP-adresserna för proxies som sannolikt kommer att få åtkomst till Adobe Campaign-servern måste anges i både det **`<subnetwork>`** aktuella och det första delnätverket **`<subnetwork name="all"/>`**. Här gäller till exempel en proxy vars IP-adress är 10.131.146.102:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

## Länka en säkerhetszon till en operator {#linking-a-security-zone-to-an-operator}

När zoner har definierats måste varje operator länkas till en av dem för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressintervallet som refereras i zonen.

Zonernas tekniska konfiguration utförs i konfigurationsfilen för Campaign-servern: **serverConf.xml**.

Du måste börja med att konfigurera den körklara **[!UICONTROL Security zone]**-uppräkningen för att länka en etikett till zonens interna namn som definieras i filen **serverConf.xml**.

Den här konfigurationen görs i Campaign Explorer:

1. Klicka på noden **[!UICONTROL Administration > Platform > Enumerations]**.
1. Välj systemuppräkningen **[!UICONTROL Security zone (securityZone)]**.

   ![](assets/enum_securityzone.png)

1. Klicka på knappen **[!UICONTROL Add]** för varje säkerhetszon som definieras i serverns konfigurationsfil.
1. I fältet **[!UICONTROL Internal name]** anger du namnet på zonen som definierats i filen **serverConf.xml**. Det motsvarar attributet **@name** för elementet `<securityzone>`. Ange den etikett som är länkad till det interna namnet i fältet **Etikett**.

   ![](assets/enum_addsecurityvalue.png)

1. Klicka på OK och spara ändringarna.

När zonerna har definierats och uppräkningen **[!UICONTROL Security zone]** har konfigurerats måste du länka varje operator till en säkerhetszon:

1. Klicka på noden **[!UICONTROL Administration > Access management > Operators]**.
1. Markera den operator som du vill länka en säkerhetszon till och klicka på fliken **[!UICONTROL Edit]**.
1. Gå till fliken **[!UICONTROL Access rights]** och klicka på länken **[!UICONTROL Edit access parameters...]**.

   ![](assets/zone_operator.png)

1. Välj en zon i listrutan **[!UICONTROL Authorized connection zone]**

   ![](assets/zone_operator_selection.png)

1. Klicka på **[!UICONTROL OK]** och spara ändringarna för att tillämpa ändringarna.



## Rekommendationer

* Kontrollera att din omvända proxy inte tillåts i subNetwork. Om så är fallet kommer **all**-trafik att identifieras från den här lokala IP-adressen, så den kommer att betraktas som tillförlitlig.

* Minimera användningen av sessionTokenOnly=&quot;true&quot;:

   * Varning! Om det här attributet är true kan operatorn exponeras för en **CRSF-attack**.
   * Dessutom har cookien sessionToken inte angetts med flaggan httpOnly, vilket innebär att viss JavaScript-kod på klientsidan kan läsa den.
   * Message Center på flera körningsceller behöver sessionTokenOnly: skapa en ny säkerhetszon med sessionTokenOnly inställd på true och lägg till **endast de IP-adresser som behövs** i den här zonen.

* När det är möjligt anger du att alla allowHTTP, showErrors ska vara false (inte för localhost) och markerar dem.

   * allowHTTP = &quot;false&quot;: tvingar operatorer att använda HTTPS
   * showErrors = &quot;false&quot;: döljer tekniska fel (inklusive SQL). Det förhindrar att alltför mycket information visas, men minskar marknadsförarens förmåga att åtgärda fel (utan att be om mer information från en administratör)

* Ange bara allowDebug till true för IP-adresser som används av marknadsföringsanvändare/administratörer som behöver skapa (faktiskt förhandsgranska) undersökningar, webApps och rapporter. Med den här flaggan kan dessa IP-adresser visa reläregler och felsöka dem.

   * När allowDebug är inställd på false blir utdata:

     ```
     <redir status='OK' date='...' sourceIP='...'/>
     ```

   * När allowDebug är true blir utdata:

     ```
     <redir status='OK' date='...' build='...' OR version='...' sha1='...' instance='...' sourceIP='...' host='...' localHost='...'/>
     ```

* Ange aldrig allowEmptyPassword, allowUserPassword, allowSQLInjection till true.

   * Med **allowEmptyPassword** kan operatorer ha ett tomt lösenord. Om så är fallet ska du meddela alla operatorer att de måste ange ett lösenord med en tidsgräns. När den här tidsgränsen har passerats ändrar du attributet till false.

   * Med **allowUserPassword** kan operatorer skicka sina autentiseringsuppgifter som parametrar (så att de loggas av apache/IIS/proxy). Den här funktionen har använts tidigare för att förenkla API-användningen. Du kan kontrollera i din cookbook (eller i specifikationen) om några tredjepartsprogram använder det här. I så fall måste du meddela dem att de ska ändra hur de använder vårt API och så snart som möjligt ta bort den här funktionen.

   * Med **allowSQLInjection** kan användaren utföra SQL-injektioner med en gammal syntax. Attributet ska anges till false. Du kan använda /nl/jsp/ping.jsp?zone=true för att kontrollera säkerhetszonskonfigurationen. På den här sidan visas den aktiva statusen för säkerhetsåtgärder (beräknade med dessa säkerhetsflaggor) för den aktuella IP-adressen.

* HttpOnly cookie/useSecurityToken: referera till flaggan **sessionTokenOnly**.

* Minimera IP-adresser som läggs till i tillåtelselista: i säkerhetsområden har vi lagt till de tre intervallen för privata nätverk. Det är osannolikt att du kommer att använda alla dessa IP-adresser. Så behåll bara de du behöver.

* Uppdatera operatorn webApp/internal så att den bara är tillgänglig i localhost.
