---
solution: Campaign Classic
product: campaign
title: Leveransstatus
description: Läs mer om de statusar som finns på din kontrollpanel för leverans.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 3%

---


# Leveransstatus {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

När en leverans har skickats visar kontrollpanelen en status som gör att du kan övervaka om sändningen har slutförts. Möjliga statusar beskrivs i avsnittet nedan.

![](assets/delivery-status.png)

Mer information om olika leveransfel som du kan träffa på och hur du löser dem finns på [den här sidan](../../delivery/using/understanding-delivery-failures.md).

**Relaterade ämnen:**

* [Kontrollpanel för leverans](../../delivery/using/delivery-dashboard.md)
* [Leveransfelsökning](../../delivery/using/delivery-troubleshooting.md)
* [Om leverans](../../delivery/using/about-deliverability.md)

## Lista över leveransstatus {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> Status<br /> </th> 
   <th> Definitioner och lösningar<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Skickat<br /> </td> 
   <td> Leveransen skickades korrekt till meddelandeleverantören (men mottagaren tog inte emot den).<br /> </td> 
  </tr> 
  <tr> 
   <td> Ignorerad<br /> </td> 
   <td> Leveransen skickades inte till mottagaren på grund av ett fel med hans adress. Den fanns antingen på blockeringslista, i karantän, inte tillhandahållen eller en dubblett. <br /> </td> 
  </tr> 
  <tr> 
   <td> Misslyckades<br /> </td> 
   <td> Leveransen kunde inte nå mottagaren på grund av en ogiltig adress eller en fullständig inkorg, till exempel. Den kan även länkas till ett problem med personaliseringsblock eftersom de kan generera fel när scheman inte matchar leveransmappningen. Se <a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">Förstå leveransfel</a><br /> </td> 
  </tr>
  <tr> 
   <td> Väntande<br /> </td> 
   <td> Leveransen är klar att skickas och kommer att bearbetas av leveransservern (MTA). Se <a href="#pending-status" target="_blank">Väntande status</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> Ej tillämpligt<br /> </td> 
   <td> Leveransen togs med i beräkningen av servern (MTA) men bearbetades inte.<br /> </td> 
  </tr>  
  <tr> 
   <td> Leveransen har avbrutits<br /> </td> 
   <td> Leveransen avbröts av en operator.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tjänsteleverantören<br /> har tagit hänsyn till </td> 
   <td> SMS-tjänstleverantören tog emot leveransen.<br /> Om du har uppgraderat till  <a href="../../delivery/using/sending-with-enhanced-mta.md" target="_blank">Förbättrat MTA</a> för värdbaserade eller hybridbaserade installationer vidarebefordrades meddelandet från Campaign till det förbättrade MTA-avtalet.</td> 
  </tr> 
  <tr> 
   <td> Mottaget på mobilen<br /> </td> 
   <td> Mottagaren tog emot SMS på sin mobila enhet.<br /> </td> 
  </tr>
  <tr> 
   <td> Skickat till tjänsteleverantören<br /> </td> 
   <td> Leveransen skickades till SMS-tjänstleverantören men har inte tagits emot ännu.<br />
   </td> 
  </tr> 
  <tr> 
   <td> Förberedd<br /> </td> 
   <td> Mellanliggande status används endast för externa anslutningar som mobilkanalen. Det följer statusen Väntande och är den externa kopplingen som avgör följande status.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Mer information om hur du optimerar leveransen av dina e-postmeddelanden från Adobe Campaign finns i [det här avsnittet](../../delivery/using/about-deliverability.md). En djupdykning i leveransförmåga finns i [Adobe Deliverability Best Practice Guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html).

## Väntande status {#pending-status}

När du har bekräftat leveransen ser du att leveransstatus är **[!UICONTROL Pending]**. Den här statusen innebär att körningsprocessen väntar på att vissa resurser ska vara tillgängliga.

**[!UICONTROL Pending]**-statusen kan först innebära att din leverans har schemalagts och väntar tills det angivna datumet. Mer information finns i avsnittet [Leveransplanering](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending).

Om leveransen inte skickas och dess status är **[!UICONTROL Pending]** kan det bero på:

* MTA-agenten (Message Transfert Agent) som kör moduler och processer på leveransservern och som hanterar e-postutskick kanske inte har startats eller behöver startas om.

   Gör så här om du vill kontrollera detta och starta modulen om det behövs:

   >[!NOTE]
   >
   >Den här åtgärden kan utföras med en **lokal** eller **hybridvärdmodell** med åtkomst till Campaign-servern (se [värdmodeller](../../installation/using/hosting-models.md)).

   1. Kontrollera att dina `mta@<instance>`-moduler har startats på dina MTA-servrar.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. Om MTA inte finns med i listan startar du det med följande kommando:

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >Ersätt `<INSTANCENAME>` med namnet på din instans (produktion, utveckling osv.). Instansnamnet identifieras via konfigurationsfilerna: `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* Leveransen kan ha en tillhörighet som inte har konfigurerats på den sändande servern.

   I det här fallet kontrollerar du konfigurationen för trafikhanteringen (IP-tillhörighet) och använder fältet **[!UICONTROL Managing affinities with IP addresses]** för att länka leveranser till den MTA som hanterar tillhörigheten. Mer information om tillhörigheter finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* När för många kampanjer körs förblir leveransstatusen Väntande.

   Gränsen för samtidiga kampanjer definieras i alternativet **[!UICONTROL NmsOperation_LimitConcurrency]**. Standardvärdet är 10.

   Läs mer om alternativen i [den här sidan](../../installation/using/configuring-campaign-options.md).


**Relaterade ämnen:**

* [Leveransloggar och historik](#delivery-logs-and-history)
* [Förstå leveransfel](../../delivery/using/understanding-delivery-failures.md)
* [Typ av leveransfel och orsaker](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
