---
product: campaign
title: Installera en server för mellanleverantörer i Campaign
description: I det här avsnittet finns information om installation och konfiguration av en server med mellanleverantörer i Campaign
feature: Installation, Instance Settings
badge-v7-prem: label="lokal och hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=sv" tooltip="Gäller endast lokala och hybrida driftsättningar"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1006'
ht-degree: 0%

---

# Server för mellanleverantörer{#mid-sourcing-server}



I det här avsnittet finns information om installation och konfiguration av en server med mellanlagring, samt om distributionen av en instans som gör det möjligt för tredje part att skicka meddelanden i **medelleverantörer** läge.

Arkitekturen med&quot;mellanleverantörer&quot; presenteras i [Distribution från olika källor](../../installation/using/mid-sourcing-deployment.md).

När du installerar en server med mellanlagring utförs samma process som när du installerar en server på det vanliga sättet (se standardkonfigurationen). Det är en oberoende instans med en egen databas som kan användas för att köra leveranser. Kort och gott: den innehåller en extra konfiguration som tillåter att fjärrinstanser kör leveranser via den i läget mitt i källkoden.

>[!CAUTION]
>
>När mittkällservern har konfigurerats och [synkronisera arbetsflöden](../../workflow/using/about-technical-workflows.md) måste du se till att du inte uppdaterar det interna namnet för de externa konton som används från mellanleverantörer.

## Steg för att installera och konfigurera en instans {#steps-for-installing-and-configuring-an-instance}

### Krav för att installera och konfigurera en instans {#prerequisites-for-installing-and-configuring-an-instance}

* JDK på programservern.
* Åtkomst till en databasserver på programservern.
* Brandväggen är konfigurerad att öppna HTTP- (80) eller HTTPS-portar (443) till mittkällservern.

I proceduren nedan beskrivs en konfiguration som använder en enda server för mellanlagring. Det går också att använda flera servrar. Det går också att skicka vissa meddelanden (till exempel arbetsflödesmeddelanden) från en intern konfiguration.

### Installera och konfigurera programservern för installation på mellannivå {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

Installationsproceduren är identisk med den för en fristående instans. Se [Installera och konfigurera (en dator)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

Du måste dock göra följande:

* I steg **5** måste du inaktivera **mta** (leverans) **inMail** (studsmoduler). The **wfserver** (arbetsflöde) måste dock förbli aktiverat.

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

  Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#enabling-processes).

* Steg **6**, **9** och **10** behövs inte.
* Under steg **12** och **13** måste du ange porten 8080 i anslutnings-URL:en (eftersom konsolen kommunicerar direkt med Tomcat, inte via webbservern). URL:en blir `http://console.campaign.net:8080`. Under steg **13** väljer du **[!UICONTROL Issue towards Mid-sourcing]** samt de som ska installeras.

  ![](assets/s_ncs_install_midsourcing02.png)

  >[!CAUTION]
  >
  >Standardroutningen för tekniska leveranser ersätts automatiskt med e-postroutning via Mid-sourcing.

### Installera och konfigurera servern för mellanlagring {#installing-and-configuring-the-mid-sourcing-server}

Gå till klientkonsolen och leta upp **E-postroutning med medelkällkod** mittleverantörskonto (i **/Administration/Externa konton/** mapp). Fyll i **URL för servern**, **konto**, **lösenord** och **URL för speglingssida** inställningarna med den information som tillhandahålls av den serverleverantör som är värd för den server som använder mellanleverantörer. Testa anslutningen.

>[!NOTE]
>
>The **midsourcingEmitter** option skapar två **Mid-sourcing** arbetsflöden. Det är en process som körs som standard var 1 timme och 20:e minut och som samlar in leveransinformation på servern med mellanlagring.

## Distribuera en server med mellanleverantörer {#deploying-a-mid-sourcing-server}

1. Installerar programservern:

   >[!CAUTION]
   >
   >Om du installerar servern för mellanlagring och vill installera extra Adobe Campaign-moduler rekommenderar vi att du använder modulen Leverans och inte Campaign.

   Följ samma procedur som för standarddistributionen och välj bara **[!UICONTROL Mid-sourcing platform]** alternativ.

   ![](assets/s_ncs_install_midsourcing01.png)

1. Konfiguration för att ta emot i läget mitt i källkoden

   Ange lösenord för överföringskonto: I **/Mid-sourcing/Access Management/Operators/** mapp, **mitten** -operatorn används av fjärrinstansen för att skicka in material i mellankälläge. Du måste ange ett lösenord för den här operatorn och ge det till administratören för inskickningsinstansen.

   The **Plattform för mellanleverantörer** skapar standardmapparna för lagring av skickade leveranser och standardoperatorn som utför skickade leveranser.

## Multiplexing av servern med mellanlagring {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>Multiplexing stöds endast i lokala miljöer.

Det är möjligt att dela en instans med mellanleverantörer genom att skicka in flera instanser. Var och en av de här instanserna måste kopplas till en operator i databasen för mellanleverantörer. Så här skapar du ett andra konto på servern:

1. Skapa en mapp i **[!UICONTROL Mid-sourcing > Deliveries]** nod som ska associeras med standardkontot för mellanleverantörer (till exempel: prod).
1. Skapa en mapp i **[!UICONTROL Mid-sourcing > Deliveries]** nod med samma namn som kontot (till exempel: accept_test).

   ![](assets/mid_recette_account.png)

1. I **[!UICONTROL Mid-sourcing > Access Management > Operators]** skapar du ett nytt konto.

   ![](assets/mid_recette_user_create.png)

1. I **[!UICONTROL Access rights]** ger du den här operatorn rättigheterna för **Mid-sourcing** grupp. Den här åtkomsträttigheten är tillgänglig i **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. Välj **[!UICONTROL Restrict to data in the sub-folders of]** och markera leveransmappen för att begränsa den här operatorn till leveransmappen från mitten.

   ![](assets/mid_recette_user_restrictions.png)

1. Starta om modulen Webb med följande kommando: **omstart av webbserver**.

Du måste ändra serverinställningen för mellanlagring i filen serverConf.xml. Följande rad måste läggas till i avsnittet &quot;Hantering av tillhörigheter med IP-adresser&quot;, under den befintliga raden:

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

Attributet &#39;@name&#39; måste följa följande regler:

**marketing_account_operator_name.affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39; relaterar till det interna namnet på mittkällkontot som deklarerats i mittkällinstansen.

&#39;affinity_name&#39; relaterar till det godtyckliga namn som ges till tillhörigheten. Namnet måste vara unikt. Godkända tecken är `[a-z]``[A-Z]``[0-9]`. Syftet är att deklarera en grupp offentliga IP-adresser.

&#39;affinity_group&#39; relaterar den subaffinitet som deklarerats i målmappningen som används i var och en av leveranserna. Den sista delen som innehåller &quot;.&quot; ignoreras om det inte finns någon undertillhörighet. Godkända tecken är `[a-z]``[A-Z]``[0-9]`.

Du måste stoppa och sedan starta om servern för att ändringen ska kunna beaktas.

## Konfigurera spårning på en server med flera källor {#configuring-tracking-on-a-mid-sourcing-server}

**Konfigurera servern för mellanlagring**

1. Gå till operatorer och välj operatorn **[!UICONTROL mid]**.
1. I **[!UICONTROL Frontal servers]** anger du spårningsserverns anslutningsparametrar.

   Om du vill skapa en spårningsinstans anger du URL:en för spårningsservern, det interna kontolösenordet för spårningsservern och namnet på instansen, dess lösenord och de DNS-masker som är associerade med den.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. När du har angett anslutningsparametrarna klickar du på **[!UICONTROL Confirm the configuration]**.
1. Ange vid behov var bilderna i leveranserna ska lagras. Det gör du genom att välja ett av publikationslägena i listrutan.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   Om du väljer **[!UICONTROL Tracking server(s)]** om du väljer det här alternativet kopieras bilderna till servern för mellanlagring.

**Konfigurera kundplattformen**

1. Gå till det externa kontot för leverans mot mellanleverantörer.
1. I **[!UICONTROL Mid-Sourcing]** anger du anslutningsparametrarna för servern med mellankällkod.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. Bekräfta konfigurationen genom att klicka på **[!UICONTROL Test the connection]**.
1. Deklarera spårningsinstansen som refereras på mellankällservern:

   Klicka på länken **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   Ange namnet på spårningsinstansen och bekräfta sedan anslutningen till spårningsservern.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

Om leveransen av meddelanden ska hanteras av flera servrar med mellanleverantörer väljer du alternativet **[!UICONTROL Routing with alternating mid-sourcing accounts]** och ange olika servrar.

![](assets/s_ncs_install_midsourcing_tracking04.png)
