---
solution: Campaign Classic
product: campaign
title: Konfigurera säkerhetszoner
description: Lär dig konfigurera säkerhetszoner
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---


# Definiera säkerhetszoner {#defining-security-zones}

Varje operator måste länkas till en zon för att kunna logga in på en instans och operatörens IP-adress måste inkluderas i adresserna eller adressuppsättningarna som definieras i säkerhetszonen. Säkerhetszonskonfigurationen utförs i Adobe Campaign-serverns konfigurationsfil.

Operatorer är länkade till en säkerhetszon från sin profil i konsolen ( **[!UICONTROL Administration > Access management > Operators]**-nod). Lär dig hur du länkar zoner till Campaign-operatorer i [det här avsnittet](#linking-a-security-zone-to-an-operator).

## Skapa säkerhetszoner {#creating-security-zones}

En zon definieras av:

* ett eller flera intervall med IP-adresser (IPv4 och IPv6)
* ett tekniskt namn länkat till varje IP-adressintervall

Säkerhetszoner är låsta, vilket innebär att om du definierar en ny zon inom en annan zon minskar antalet operatorer som kan logga in på den samtidigt som de rättigheter som tilldelats varje operator ökas.

Zoner måste definieras under serverkonfigurationen i filen **serverConf.xml**. Alla parametrar som är tillgängliga i **serverConf.xml** listas i [det här avsnittet](../../installation/using/the-server-configuration-file.md).

Varje zon definierar rättigheter, till exempel:

* HTTP-anslutning i stället för HTTPS
* Felvisning (Java-fel, JavaScript, C++ osv.)
* Report and webApp preview
* Autentisering via inloggning/lösenord
* Osäkert anslutningsläge

>[!NOTE]
>
>**Varje operator måste länkas till en zon**. Om operatorns IP-adress tillhör det intervall som definieras av zonen kan operatorn logga in på instansen.\
>Operatorns IP-adress kan definieras i flera zoner. I det här fallet tar operatorn emot **uppsättningen** av tillgängliga rättigheter för varje zon.

Filen **serverConf.xml** som är klar att användas innehåller tre zoner: **public, VPN och LAN**.

>[!NOTE]
>
>**Körklar konfiguration är säker**. Innan du migrerar från en tidigare version av Adobe Campaign kan det dock vara nödvändigt att tillfälligt minska säkerheten för att migrera och godkänna de nya reglerna.

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
* **allowEmptyPassword**: godkänner en anslutning till en instans utan lösenord
* **allowHTTP**: en session kan skapas utan att HTTPS-protokollet används
* **allowUserPassword**: sessionstoken kan ha följande format &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: säkerhetstoken krävs inte i anslutnings-URL
* **showErrors**: fel på serversidan vidarebefordras och visas

>[!IMPORTANT]
>
>I en zondefinition minskar varje attribut med **true**-värdet säkerheten.

Om det finns flera körningsinstanser i Message Center måste du skapa en extra säkerhetszon med attributet **sessionTokenOnly** definierat som **true**, där endast de nödvändiga IP-adresserna ska läggas till. Mer information om hur du konfigurerar instanser finns i [det här dokumentet](../../message-center/using/creating-a-shared-connection.md).

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

När en proxy refereras och en anslutning matas in via den här proxyn (synlig via HTTP X-Forwarded-For-huvudet), är den verifierade zonen den för proxyns klienter och inte proxyns.

>[!IMPORTANT]
>
>Om en proxy är konfigurerad och det går att åsidosätta den (eller om den inte finns), kommer den IP-adress som testas att kunna förfalskas.
>
>Dessutom genereras nu reläer som proxies. Du kan därför lägga till IP-adressen 127.0.0.1 i listan över proxy i din säkerhetszonskonfiguration.
>
>Exempel: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Olika fall kan inträffa:

* Ett undernätverk refereras direkt i säkerhetszonen och ingen proxy har konfigurerats: användare av undernätverket kan ansluta direkt till Adobe Campaign-servern.

   ![](assets/8101_proxy1.png)

* En proxy anges för ett undernätverk i säkerhetszonen: -användare från det här undernätverket har åtkomst till Adobe Campaign-servern via den här proxyn.

   ![](assets/8101_proxy2.png)

* En proxy ingår i ett undernätverk för säkerhetszoner: användare som har åtkomst via den här proxyn, oavsett ursprung, har åtkomst till Adobe Campaign-servern.

   ![](assets/8101_proxy3.png)

IP-adresserna för proxies som sannolikt kommer att få åtkomst till Adobe Campaign-servern måste anges i både **`<subnetwork>`** och undernätverket **`<subnetwork name="all"/>`** på första nivån. Här gäller till exempel en proxy vars IP-adress är 10.131.146.102:

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

Zonernas tekniska konfiguration görs i konfigurationsfilen för Campaign Server: **serverConf.xml**.

Du måste börja med att konfigurera uppräkningen **[!UICONTROL Security zone]** som är klar att användas för att länka en etikett till zonens interna namn som definieras i filen **serverConf.xml**.

Den här konfigurationen görs i Campaign Explorer:

1. Klicka på noden **[!UICONTROL Administration > Platform > Enumerations]**.
1. Välj systemuppräkningen **[!UICONTROL Security zone (securityZone)]**.

   ![](assets/enum_securityzone.png)

1. Klicka på knappen **[!UICONTROL Add]** för varje säkerhetszon som definieras i serverns konfigurationsfil.
1. I fältet **[!UICONTROL Internal name]** anger du namnet på zonen som definierats i filen **serverConf.xml**. Det motsvarar attributet **@name** för `<securityzone>`-elementet. Ange den etikett som är länkad till det interna namnet i fältet **Etikett** fält.

   ![](assets/enum_addsecurityvalue.png)

1. Klicka på OK och spara ändringarna.

När zonerna har definierats och **[!UICONTROL Security zone]**-uppräkningen har konfigurerats måste du länka varje operator till en säkerhetszon:

1. Klicka på noden **[!UICONTROL Administration > Access management > Operators]**.
1. Markera den operator som du vill länka en säkerhetszon till och klicka på fliken **[!UICONTROL Edit]**.
1. Gå till fliken **[!UICONTROL Access rights]** och klicka på länken **[!UICONTROL Edit access parameters...]**.

   ![](assets/zone_operator.png)

1. Välj en zon i listrutan **[!UICONTROL Authorized connection zone]**

   ![](assets/zone_operator_selection.png)

1. Klicka på **[!UICONTROL OK]** och spara ändringarna för att tillämpa ändringarna.