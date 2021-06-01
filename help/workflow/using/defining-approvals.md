---
product: campaign
title: Definiera godkännanden
description: Godkännanden gör det möjligt för operatorer att fatta beslut som styr ett arbetsflöde eller att bekräfta att det fortsätter att köras
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 4d413d51-ae5d-4e5e-bfaf-4160a6075281
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Definiera godkännanden {#defining-approvals}

Godkännanden gör det möjligt för operatorer att fatta beslut som styr ett arbetsflöde eller att bekräfta att det fortsätter att köras.

Ett meddelande skickas till en grupp operatorer och arbetsflödet väntar på ett svar innan det återupptas. Arbetsflödet har inte stoppats och andra åtgärder kan utföras. Det kan till exempel finnas flera väntande samtidiga godkännanden.

Ett godkännande kan innehålla flera alternativ som operatorn kan välja. Det är dock möjligt att begränsa antalet val till ett för att skicka en uppgift som ska utföras till en operator, till exempel utföra målinriktning. Operatorn kan sedan svara när uppgiften har utförts (processen återupptas sedan). I följande exempel visas dessa typer av godkännanden:

![](assets/validation-1.png)

I operationer baseras alla faser som kräver godkännande på samma princip.

![](assets/validation-1-in-op.png)

Godkännandeexempel finns i det här [avsnittet](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

En operator kan svara på ett av två sätt: validera med webbsidan som är länkad i e-postmeddelandet eller via konsolen.

>[!NOTE]
>
>När svaret har sparats kan det inte ändras.

## Skicka e-postmeddelanden {#sending-emails}

Det går att få ett meddelande om godkännande som innehåller en länk till en webbsida där det går att svara. Om måloperatorn ska få ett e-postmeddelande om godkännande måste operatörens e-postadress vara fullständig. Om så inte är fallet måste operatören använda konsolen för att svara

Operatorhantering beskrivs i det här [avsnittet](../../platform/using/access-management.md).

E-postmeddelanden om godkännande skickas kontinuerligt. Standardleveransmallen är **[!UICONTROL notifyAssignee]**: Den sparas i mappen **[!UICONTROL Administration > Campaign management > Technical delivery templates]**. Scenariot kan anpassas och vi rekommenderar att du skapar en kopia och ändrar mallar för varje aktivitet.

Leveranser som skapas med den här mallen lagras i mappen **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**.

## Godkännande via konsolen {#approval-via-the-console}

I åtgärder visas element som ska godkännas på kontrollpanelen för kampanjer.

I tekniska arbetsflöden kan du komma åt de uppgifter som användaren kan godkänna från trädstrukturen i mappen **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]**.

![](assets/validation-node.png)

## Grupper {#groups}

Ett godkännande tilldelas en grupp operatorer, en enstaka operator eller en uppsättning operatorer som väljs via ett filtreringsvillkor.

1. För den enklaste formen av godkännande slutförs uppgiften så snart en operator svarar. Alla andra operatorer som försöker svara får ett meddelande om att någon redan har gjort det.
1. Mer information om flera godkännanden finns i [Flera godkännanden](#multiple-approval).

Operatörsgrupperna för godkännanden bör utses som roller eller funktioner i stället för namngivna personer. En&quot;Kampanjbudgetgrupp&quot; är till exempel att föredra framför&quot;Harry&#39;s Group&quot;. Vi rekommenderar att du har minst två personer i en grupp som kan godkänna en uppgift. På så sätt kan den andre svara om någon inte är närvarande.

## Förfallodatum {#expirations}

Förfallodatum är specifika övergångar som används i olika typer av aktiviteter, och särskilt vid godkännanden. Du kan använda en förfallotid för att utlösa en åtgärd efter en viss tid utan att svara. Den kan också användas för att till exempel fortsätta med arbetsflödet och tilldela ett godkännande till en annan grupp.

På den andra fliken i egenskaperna för aktivitetsgodkännande kan du definiera en eller flera förfallotider. Du kan definiera flera olika förfallotyper.

![](assets/expiration.png)

Om du vill lägga till en ny förfallotid klickar du på **[!UICONTROL Add]**. En övergång läggs till för varje förfallodatum som skapas. Du kan:

* ändra de typiska parametrarna direkt genom att klicka på en cell i listan (eller genom att trycka på F2),
* eller redigera uttrycket genom att klicka på knappen **[!UICONTROL Detail...]**.

>[!NOTE]
>
>Det är inte nödvändigt att ange en ordning för förfallodatumen eftersom de bearbetas i kronologisk ordning.

Alternativet **[!UICONTROL Do not terminate the task]** lämnar godkännandet aktivt när fördröjningen överskrids. I det här läget kan du hantera påminnelser medan du låter godkännandet vara aktivt: -operatorer kan fortfarande svara. Det här alternativet är inaktiverat som standard, vilket innebär att uppgiften anses vara slutförd när den upphör att gälla och att operatorerna kanske inte längre svarar.

Du kan skapa fyra typer av förfallodatum:

* **Fördröjning efter att aktiviteten har startats**: Utgångsdatumet beräknas genom att en angiven tidsperiod läggs till det datum då godkännandet aktiveras.
* **Fördröjning efter ett visst datum**: Förfallotiden beräknas genom att lägga till en tidslängd till ett datum som du anger.
* **Fördröjning före ett visst datum**: Förfallodatumet beräknas genom att en tidslängd subtraheras från ett datum som du anger.
* **Förfallotid beräknat av skript**: Förfallotiden beräknas med JavaScript.

   I följande exempel beräknas en förfallotid 24 timmar innan det datum då en leverans påbörjas (identifieras av **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

## Flera godkännanden {#multiple-approval}

Flera godkännanden är en mekanism som gör det möjligt för alla godkännandeoperatörer att svara. En övergång aktiveras för varje svar.

Flera godkännanden är användbara för röstnings- eller undersökningsmetoder. Du kan räkna svar och bearbeta resultatet efter en viss period genom att lägga till en deadline.

## Nödvändiga rättigheter {#required-rights}

Operatörerna i en grupp måste minst ha följande rättigheter för att kunna besvara en begäran om godkännande:

* Skriva behörigheter för arbetsflöde.
* Läsa- och skrivbehörigheter för mappen som innehåller de uppgifter som ska godkännas.

Gruppen Workflow execution har dessa rättigheter. En operator som lagts till i den här gruppen har behörighet att svara på en godkännandebegäran.
