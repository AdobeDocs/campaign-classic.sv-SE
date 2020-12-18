---
solution: Campaign Classic
product: campaign
title: Installera en server för mellanleverantörer i Campaign
description: I det här avsnittet finns information om installation och konfiguration av en server med mellanleverantörer i Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 0%

---


# Server för mid-sourcing{#mid-sourcing-server}

I det här avsnittet beskrivs installation och konfiguration av en server med mellanlagring samt distributionen av en instans som gör det möjligt för tredje part att skicka meddelanden i **mellankällsläge**-läge.

Arkitekturen&quot;från mellanleverantörer&quot; presenteras i [Distribution från mellanleverantörer](../../installation/using/mid-sourcing-deployment.md).

När du installerar en server med mellanlagring utförs samma process som när du installerar en server på det vanliga sättet (se standardkonfigurationen). Det är en oberoende instans med en egen databas som kan användas för att köra leveranser. Kort och gott: den innehåller en extra konfiguration som tillåter att fjärrinstanser kör leveranser via den i läget mitt i källkoden.

>[!CAUTION]
>
>När mittkällservern har konfigurerats och [synkroniseringsarbetsflödena](../../workflow/using/transfer-to-mid-sourcing.md) har körts för första gången, ska du inte uppdatera det interna namnet på mittkällans externa konton.

## Steg för att installera och konfigurera en instans {#steps-for-installing-and-configuring-an-instance}

### Krav för att installera och konfigurera en instans {#prerequisites-for-installing-and-configuring-an-instance}

* JDK på programservern.
* Åtkomst till en databasserver på programservern.
* Brandväggen är konfigurerad att öppna HTTP- (80) eller HTTPS-portar (443) till mittkällservern.

I proceduren nedan beskrivs en konfiguration som använder en enda server för mellanlagring. Det går också att använda flera servrar. Det går också att skicka vissa meddelanden (till exempel arbetsflödesmeddelanden) från en intern konfiguration.

### Installerar och konfigurerar programservern för installation på mellannivå {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

Installationsproceduren är identisk med den för en fristående instans. Se [Installera och konfigurera (en dator)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Du måste dock göra följande:

* I steg **5** måste du inaktivera modulerna **mta** (leverans) och **inMail** (studsmeddelanden). Modulen **wfserver** (arbetsflöde) måste dock vara aktiverad.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   Mer information finns i [Aktivera processer](../../installation/using/campaign-server-configuration.md#enabling-processes).

* Steg **6**, **9** och **10** är inte nödvändiga.
* Under steg **12** och **13** måste du ange porten 8080 i anslutnings-URL:en (eftersom konsolen kommunicerar direkt med Tomcat, inte via webbservern). URL:en blir [http://console.campaign.net:8080](http://console.campaign.net). Under steg **13** markerar du **[!UICONTROL Issue towards Mid-sourcing]**-paketet samt de som ska installeras.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >Standardroutningen för tekniska leveranser ersätts automatiskt med e-postroutning via Mid-sourcing.

### Installation och konfigurering av servern {#installing-and-configuring-the-mid-sourcing-server} för mellanleverantörer

På klientkonsolen letar du reda på **e-postroutningen med mittkällkonto** (i mappen **/Administration/Externa konton/**). Fyll i **URL:en för server**, **konto**, **lösenord** och **Spegla sidans URL**-inställningar med informationen från serverprovidern som är värd för mittkällservern. Testa anslutningen.

>[!NOTE]
>
>Alternativet **midsourcingEmitter** skapar två **Mid-sourcing**-arbetsflöden. Det är en process som körs som standard var 1 timme och 20:e minut och som samlar in leveransinformation på servern med mellanlagring.

## Distribuera en server {#deploying-a-mid-sourcing-server} från mellanleverantörer

1. Installerar programservern:

   >[!CAUTION]
   >
   >Om du installerar servern för mellanlagring och vill installera extra Adobe Campaign-moduler rekommenderar vi att du använder modulen Leverans och inte Campaign.

   Följ samma procedur som för standarddistributionen och välj bara alternativet **[!UICONTROL Mid-sourcing platform]**.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Konfiguration för att ta emot i läget mitt i källkoden

   Ange lösenord för överföringskontot: I mappen **/Mid-sourcing/Access Management/Operators/** används operatorn **mid** av fjärrinstansen för överföringar i mellankälläge. Du måste ange ett lösenord för den här operatorn och ge det till administratören för inskickningsinstansen.

   Alternativet **Plattform för mellanpublicering** skapar standardmapparna för lagring av skickade leveranser och standardoperatorn som utför skickade leveranser.

## Multiplexing av servern {#multiplexing-the-mid-sourcing-server} från mitten

>[!CAUTION]
>
>Multiplexing stöds endast i lokala miljöer.

Det är möjligt att dela en instans från mellanleverantörer med flera instanser. Var och en av de här instanserna måste kopplas till en operator i databasen för mellanleverantörer. Så här skapar du ett andra konto på servern:

1. Skapa en mapp i noden **[!UICONTROL Mid-sourcing > Deliveries]** som ska associeras med standardkontot för mellanlagring (till exempel: prod).
1. Skapa en mapp i noden **[!UICONTROL Mid-sourcing > Deliveries]** med samma namn som kontot (till exempel: accept_test).

   ![](assets/mid_recette_account.png)

1. Skapa ett nytt konto i **[!UICONTROL Mid-sourcing > Access Management > Operators]**.

   ![](assets/mid_recette_user_create.png)

1. På fliken **[!UICONTROL Access rights]** ger du den här operatorn rättigheterna för gruppen **Mid-sourcing-överföringar**. Den här åtkomsträttigheten är tillgänglig i **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Välj alternativet **[!UICONTROL Restrict to data in the sub-folders of]** och markera leveransmappen för att begränsa den här operatorn till mellankällans leveransmapp.

   ![](assets/mid_recette_user_restrictions.png)

1. Starta om modulen Webb med följande kommando: **Servern startar om webb**.

Du måste ändra serverinställningen för mellanlagring i filen serverConf.xml. Följande rad måste läggas till i avsnittet &quot;Hantering av tillhörigheter med IP-adresser&quot;, under den befintliga raden:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Attributet &#39;@name&#39; måste följa följande regler:

**&#39;marketing_account_operator_name&#39;.&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; relaterar till det interna namnet på mittkällkontot som deklarerats i mittkällinstansen.

&#39;affinity_name&#39; relaterar till det godtyckliga namn som ges till tillhörigheten. Namnet måste vara unikt. Godkända tecken är `[a-z]``[A-Z]``[0-9]`. Syftet är att deklarera en grupp offentliga IP-adresser.

&#39;affinity_group&#39; relaterar den subaffinitet som deklarerats i målmappningen som används i var och en av leveranserna. Den sista delen som innehåller &quot;.&quot; ignoreras om det inte finns någon undertillhörighet. Godkända tecken är `[a-z]``[A-Z]``[0-9]`.

Du måste stoppa och sedan starta om servern för att ändringen ska kunna beaktas.

## Konfigurerar spårning på en server {#configuring-tracking-on-a-mid-sourcing-server} med mellankällor

**Konfigurera servern för mellanlagring**

1. Gå till operatorer och välj operatorn **[!UICONTROL mid]**.
1. Ange spårningsserveranslutningsparametrarna på fliken **[!UICONTROL Frontal servers]**.

   Om du vill skapa en spårningsinstans anger du URL:en för spårningsservern, det interna kontolösenordet för spårningsservern och namnet på instansen, dess lösenord och de DNS-masker som är associerade med den.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. När du har angett anslutningsparametrarna klickar du på **[!UICONTROL Confirm the configuration]**.
1. Ange vid behov var bilderna i leveranserna ska lagras. Det gör du genom att välja ett av publikationslägena i listrutan.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Om du väljer alternativet **[!UICONTROL Tracking server(s)]** kopieras bilderna till servern med mellankällor.

**Konfigurera kundplattformen**

1. Gå till det externa kontot för leverans mot mellanleverantörer.
1. På fliken **[!UICONTROL Mid-Sourcing]** anger du anslutningsparametrarna för serveranslutning från mitten.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bekräfta konfigurationen genom att klicka på **[!UICONTROL Test the connection]**.
1. Deklarera spårningsinstansen som refereras på mellankällservern:

   Klicka på länken **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Ange namnet på spårningsinstansen och bekräfta sedan anslutningen till spårningsservern.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Om leveransen av meddelanden ska hanteras av flera servrar med mellanleverantörer väljer du alternativet **[!UICONTROL Routing with alternating mid-sourcing accounts]** och anger de olika servrarna.

![](assets/s_ncs_install_midsourcing_tracking04.png)

