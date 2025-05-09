---
product: campaign
title: Konfigurerar Campaign-server
description: Konfigurerar Campaign-server
feature: Installation, Instance Settings
badge-v7-prem: label="Endast lokal/hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 1%

---

# Kom igång med Campaign-serverkonfigurationen{#gs-campaign-server-config}



I det här kapitlet beskrivs serverkonfigurationer som kan utföras för att passa dina behov och dina miljöegenskaper.

## Begränsningar

Dessa procedurer är begränsade till **lokala**/**hybriddistributioner** och kräver administrationsbehörigheter.

För **värdbaserade**-distributioner kan inställningarna på serversidan endast konfigureras av Adobe. Vissa inställningar kan dock ställas in på [Campaign-kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=sv), till exempel IP tillåtelselista-hantering eller URL-behörigheter. [Läs mer](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=sv-SE).

Mer information finns i följande avsnitt:

* [Dokumentation för kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=sv)
* [Värdmodeller](../../installation/using/hosting-models.md)
* [Funktionsmatris för lokal och värdbaserad Campaign Classic](../../installation/using/capability-matrix.md)

## Konfigurationsfiler

Konfigurationsfiler för Campaign Classic lagras i mappen **conf** i installationsmappen för Adobe Campaign. Konfigurationen sprids över två filer:

* **serverConf.xml**: Allmän konfiguration för alla instanser. Den här filen kombinerar de tekniska parametrarna för Adobe Campaign-servern: dessa delas av alla instanser. Beskrivningen av några av dessa parametrar beskrivs nedan. De olika noderna och parametrarna listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (där **instance** är namnet på instansen): specifik konfiguration för instansen. Om du delar servern mellan flera instanser anger du parametrarna som är specifika för varje instans i den aktuella filen.

## Konfigurationsomfattning

Konfigurera eller anpassa Campaign-servern beroende på dina behov och din konfiguration. Du kan:

* Skydda den [interna identifieraren](#internal-identifier)
* Aktivera [kampanjprocesser](#enabling-processes)
* Konfigurera [URL-behörigheter](url-permissions.md)
* Definiera [säkerhetszoner](security-zones.md)
* Konfigurera [Tomcat-inställningar](configure-tomcat.md)
* Anpassa [leveransparametrar](configure-delivery-settings.md)
* Definiera [dynamisk sidsäkerhet och reläer](#dynamic-page-security-and-relays)
* Begränsa listan med [tillåtna externa kommandon](#restricting-authorized-external-commands)
* Konfigurera [Spårning av överflödiga](#redundant-tracking)
* Hantera [Hög tillgänglighet och arbetsflödestillhörigheter](#high-availability-workflows-and-affinities)
* Konfigurera filhantering - [Läs mer](file-res-management.md)
   * Begränsa filformat för överföring
   * Ge åtkomst till offentliga resurser
   * Konfigurera proxyanslutning
* [Automatisk processomstart](#automatic-process-restart)


## Intern identifierare {#internal-identifier}

Identifieraren **internal** är en teknisk inloggning som används för installation, administration och underhåll. Inloggningen är inte kopplad till någon instans.

Operatörer som är anslutna med den här inloggningen har alla rättigheter för alla instanser. Den här inloggningen har inget lösenord vid en ny installation. Du måste definiera det här lösenordet manuellt.

Använd följande kommando:

```sql
nlserver config -internalpassword
```

Därefter visas följande information. Ange och bekräfta lösenordet:

```sql
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Möjliggör processer {#enabling-processes}

Adobe Campaign-processer på servern aktiveras (och inaktiveras) via filerna **config-default.xml** och **`config-<instance>.xml`**.

Om du vill tillämpa ändringarna på de här filerna måste du köra kommandot **nlserver config -reload** om Adobe Campaign-tjänsten startas.

Det finns två typer av processer: flera instanser och en instans.

* **flera instanser**: en enda process startas för alla instanser. Detta gäller för processerna **web**, **syslogd** och **trackinglogd**.

  Aktivering kan konfigureras från filen **config-default.xml**.

  Deklarera en Adobe Campaign-server för åtkomst till klientkonsoler och för omdirigering (spårning):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  I det här exemplet redigeras filen med ett **vi** -kommando i Linux. Den kan redigeras med en **.txt** - eller **.xml** -redigerare.

* **mono-instance**: en process startas för varje instans (moduler: **mta**, **wfserver**, **inMail**, **sms** och **stat**).

  Aktivering kan konfigureras med hjälp av instansens konfigurationsfil:

  ```
  config-<instance>.xml
  ```

  Deklarera en server för leverans, köra arbetsflödesinstanser och återställa studentpost:

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Kampanjdatalagring**

Du kan konfigurera lagringskatalogen (**var** -katalog) för Adobe Campaign-data (loggar, hämtningar, omdirigeringar osv.). Använd systemvariabeln **XTK_VAR_DIR** för att göra detta:

* I Windows anger du följande värde i systemvariabeln **XTK_VAR_DIR**

  ```
  D:\log\AdobeCampaign
  ```

* I Linux går du till filen **customer.sh** och anger: **exportera XTK_VAR_DIR=/app/log/AdobeCampaign**.

  Mer information finns i [Anpassa parametrar](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Dynamisk sidsäkerhet och vidarebefordran {#dynamic-page-security-and-relays}

Som standard är alla dynamiska sidor automatiskt relaterade till den **lokala** Tomcat-servern på datorn vars webbmodul har startats. Den här konfigurationen anges i avsnittet **`<url>`** i frågereläkonfigurationen för filen **ServerConf.xml**.

Du kan vidarebefordra körningen av den dynamiska sidan på en **fjärr**-server, om webbmodulen inte är aktiverad på datorn. För att göra detta måste du ersätta **localhost** med namnet på fjärrdatorn för JSP och JSSP, webbprogram, rapporter och strängar.

Mer information om de olika tillgängliga parametrarna finns i konfigurationsfilen **serverConf.xml**.

För JSP-sidor är standardkonfigurationen:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign använder följande JSP-sidor:

* /nl/jsp/**soaprouter.jsp**: klientkonsolen och anslutningar för webbtjänster (SOAP API:er),
* /nl/jsp/**m.jsp**: spegelsidor,
* /nl/jsp/**logon.jsp**: Webbaserad åtkomst till rapporter och distribution av klientkonsolen,
* /nl/jsp/**s.jsp** : Använder viral marknadsföring (sponsring och sociala nätverk).

De JSSP som används för Mobile App Channel är följande:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Exempel:**

Det går att förhindra klientdatoranslutningar från utsidan. Det gör du genom att begränsa körningen av **soaprouter.jsp** och bara tillåta körning av spegelsidor, virala länkar, webbformulär och offentliga resurser.

Parametrarna är följande:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

I det här exemplet sammanfaller värdet **`<IP_addresses>`** med listan över IP-adresser (avgränsade med kommatecken) som har behörighet att använda relämodulen för den här masken.

>[!NOTE]
>
>Värdena ska anpassas efter din konfiguration och dina nätverksbegränsningar, särskilt om specifika konfigurationer har utvecklats för din installation.

### Hantera HTTP-huvuden {#managing-http-headers}

Som standard skickas inga HTTP-huvuden vidare. Du kan lägga till specifika rubriker i svar som skickas via relä. Så här gör du:

1. Gå till filen **serverConf.xml**.
1. Gå till listan med vidarebefordrade HTTP-rubriker i noden **`<relay>`**.
1. Lägg till ett **`<responseheader>`**-element med följande attribut:

   * **namn**: rubriknamn
   * **värde**: värdenamn.

   Exempel:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Begränsa behöriga externa kommandon {#restricting-authorized-external-commands}

Från och med bygge 8780 kan teknikadministratörer begränsa listan över auktoriserade externa kommandon som kan användas i Adobe Campaign.

Om du vill göra det måste du skapa en textfil med en lista över kommandon som du inte kan använda, till exempel:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Denna lista är inte uttömmande.

I noden **exec** i serverkonfigurationsfilen måste du referera till den tidigare skapade filen i attributet **svartlistFile**.

**För Linux endast**: i serverkonfigurationsfilen rekommenderar vi att du anger en användare som är dedikerad till att köra externa kommandon för att förbättra säkerhetskonfigurationen. Den här användaren anges i noden **exec** i konfigurationsfilen. Alla parametrar som är tillgängliga i **serverConf.xml** listas i det här [avsnittet](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Om ingen användare anges körs alla kommandon i användarkontexten för Adobe Campaign-instansen. Användaren måste vara en annan än den som kör Adobe Campaign.

Exempel:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Den här användaren måste läggas till i användarlistan för Adobe Campaign-operatorn neolane.

>[!IMPORTANT]
>
>Du bör inte använda en anpassad sudo. En standardsudo måste installeras på datorn.


## Spårning av överflödiga {#redundant-tracking}

När flera servrar används för omdirigering måste de kunna kommunicera med varandra via SOAP anrop för att kunna dela information från de URL:er som ska omdirigeras. När leveransen startar är det möjligt att inte alla omdirigeringsservrar är tillgängliga. Därför har de kanske inte samma informationsnivå.

>[!NOTE]
>
>När du använder standardarkitekturen eller företagsarkitekturen måste huvudprogramservern ha behörighet att överföra spårningsinformation på varje dator.

URL:erna för de redundanta servrarna måste anges i omdirigeringskonfigurationen via filen **serverConf.xml** .

**Exempel:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

Egenskapen **enableIf** är valfri (tom som standard) och du kan bara aktivera anslutningen om resultatet är sant. På så sätt kan du få en identisk konfiguration på alla omdirigeringsservrar.

Om du vill hämta datorns värdnamn kör du följande kommando: **värdnamn -s**.



## Arbetsflöden och tillhörighet med hög tillgänglighet {#high-availability-workflows-and-affinities}

Du kan konfigurera flera arbetsflödesservrar (wfserver) och distribuera dem på två eller flera datorer. Om du väljer den här typen av arkitektur konfigurerar du anslutningsläget för belastningsutjämnarna enligt Adobe Campaign-åtkomsten.

Om du vill få åtkomst från webben väljer du **belastningsutjämnarläget** för att begränsa anslutningstiderna.

Välj **hash** - eller **sticky ip**-läge om du kommer åt via Adobe Campaign-konsolen. Detta gör att du kan upprätthålla anslutningen mellan klienten och servern och förhindra att en användarsession avbryts under en import- eller exportåtgärd, till exempel.

Du kan välja att framtvinga körningen av ett arbetsflöde eller en arbetsflödesaktivitet på en viss dator. För att kunna göra detta måste du definiera en eller flera tillhörigheter för arbetsflödet eller aktiviteten.

1. Skapa tillhörigheterna för arbetsflödet eller aktiviteten genom att ange dem i fältet **[!UICONTROL Affinity]**.

   Du kan välja vilket tillhörighetsnamn som helst, men se till att du inte använder blanksteg eller skiljetecken. Om du använder olika servrar anger du olika namn.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   Listrutan innehåller tillhörigheter som tidigare använts. Den slutförs över tiden med de olika angivna värdena.

1. Öppna filen **nl6/conf/config-`<instance>.xml`**.
1. Ändra raden som matchar modulen **[!UICONTROL wfserver]** enligt följande:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Om du definierar flera tillhörigheter måste de avgränsas med kommatecken utan mellanslag:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   Kommatecknet efter tillhörighetens namn är nödvändigt för körning av arbetsflöden där ingen tillhörighet har definierats.

   Om du bara vill köra arbetsflöden för vilka en tillhörighet har definierats, ska du inte lägga till ett kommatecken i slutet av listan med dina tillhörigheter. Ändra till exempel raden enligt följande:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Automatisk omstart {#automatic-process-restart}

Som standard startas de olika Adobe Campaign-processerna om automatiskt kl. 6.00 (servertid) varje dag.

Du kan dock ändra den här konfigurationen.

Det gör du genom att gå till filen **serverConf.xml** som finns i databasen **conf** i din installation.

Varje process som konfigureras i den här filen har ett **processRestartTime**-attribut. Du kan ändra värdet för det här attributet för att anpassa starttiden för varje process efter dina behov.

>[!IMPORTANT]
>
>Ta inte bort attributet. Alla processer måste startas om varje dag.
