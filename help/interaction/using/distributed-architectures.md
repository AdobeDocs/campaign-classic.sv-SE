---
title: Distribuerade arkitekturer
seo-title: Distribuerade arkitekturer
description: Distribuerade arkitekturer
seo-description: null
page-status-flag: never-activated
uuid: f672446f-18e6-4fff-81a1-01ee22792755
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: advanced-parameters
discoiquuid: 811a42a4-552c-49cb-bffd-7e124ef83735
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# Distribuerade arkitekturer{#distributed-architectures}

## Princip {#principle}

För att få stöd för skalbarhet och dygnet runt-service på den inkommande kanalen kan ni använda Interaction med en distribuerad arkitektur. Den här typen av arkitektur används redan i Message Center och består av flera instanser:

* en eller flera kontrollinstanser som är dedikerade till den utgående kanalen och som innehåller bas för design av marknadsföring och miljö
* en eller flera körningsinstanser som är dedikerade till inkommande kanal

![](assets/interaction_powerbooster_schema.png)

>[!NOTE]
>
>Kontrollinstanser är dedikerade till den inkommande kanalen och innehåller katalogversionen online. Varje instans för körning är oberoende och dedikerad till ett kontaktsegment (till exempel en exekveringsinstans per land). Anrop till offertmotorn måste utföras direkt på körningen (en specifik URL per körningsinstans). Eftersom synkroniseringen mellan instanser inte är automatisk måste interaktioner från samma kontakt skickas via samma instans.

## Förslagssynkronisering {#proposition-synchronization}

Synkronisering av erbjudanden utförs via paket. I körningsinstanser föregås alla katalogobjekt av det externa kontonamnet. Detta innebär att flera kontrollinstanser (till exempel utvecklings- och produktionsinstanser) kan stödjas på samma körningsinstans.

>[!CAUTION]
>
>Vi rekommenderar att du använder korta och explicita interna namn.

Erbjudandena distribueras automatiskt och publiceras sedan på körnings- och kontrollinstanser.

Erbjudanden som tas bort i designmiljön är inaktiverade på alla onlineförekomster. Föråldrade offerter och erbjudanden tas automatiskt bort i alla instanser efter tömningsperioden (som anges i varje instans distributionsassistent) och glidperioden (som anges i de inkommande förslagens typologiregler).

![](assets/interaction_powerbooster_schema2.png)

Ett arbetsflöde skapas för varje miljö och ett externt konto för förslagssynkronisering. Synkroniseringsfrekvensen kan justeras för varje miljö och externt konto.

## Begränsningar {#limitations}

* Om du använder funktionen för säkerhetskopiering från en anonym miljö till en identifierad miljö måste dessa två miljöer finnas i samma körningsinstans.
* Synkroniseringen mellan flera körningsinstanser utförs inte i realtid. Interaktioner av samma kontakt måste skickas till samma instans. Kontrollinstansen måste dedikeras till den utgående kanalen (ingen realtid).
* Marknadsföringsdatabasen synkroniseras inte automatiskt. Marknadsföringsdata som används i viktnings- och berättigandereglerna måste dupliceras i körningsinstanser. Den här processen kommer inte som standard, du måste utveckla den under integreringsperioden.
* Propositionssynkronisering utförs uteslutande av FDA-anslutning.
* Om du använder Interaction och Message Center på samma instans, synkroniseras i båda fallen via FDA-protokollet.

## Paketkonfiguration {#packages-configuration}

Schematillägg som är direkt länkade till **Interaktion** (erbjudanden, erbjudanden, mottagare osv.) måste distribueras på körningsinstanserna.

Interaktionspaketet måste installeras på alla instanser (kontroll och körning). Ytterligare två paket finns: ett paket som ska installeras på kontrollinstanserna och ett annat som ska installeras på varje körningsinstans.

>[!NOTE]
>
>När paketet installeras blir de **långa** typfälten i **nms:proposition** -tabellen, till exempel förslags-ID, **int64** -typfält. Den här typen av data beskrivs i [det här avsnittet](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data).

Varaktigheten för datalagring måste konfigureras för varje instans (via **[!UICONTROL Data purge]** fönstret i distributionsguiden). För körningsinstanser måste denna period motsvara det historiska djup som krävs för att typologiregler (glidande period) och regler för stödberättigande ska kunna beräknas.

På kontrollinstanserna:

1. Skapa ett externt konto genom körningsinstansen:

   ![](assets/interaction_powerbooster1.png)

   * Fyll i etiketten och lägg till ett kort och explicit internt namn.
   * Markera **[!UICONTROL Execution instance]**.
   * Markera **[!UICONTROL Enabled]** alternativet.
   * Slutför anslutningsparametrarna för körningsinstansen.
   * Alla körningsinstanser måste länkas till ett ID. Detta ID tilldelas när du klickar på **[!UICONTROL Initialize connection]** knappen.
   * Kontrollera vilken typ av program som används: **[!UICONTROL Message Center]**, **[!UICONTROL Interaction]** eller båda.
   * Ange det FDA-konto som används. En operator måste skapas för körningsinstanserna och måste ha följande läs- och skrivrättigheter i databasen för instansen i fråga:

      ```
      grant SELECT ON nmspropositionrcp, nmsoffer, nmsofferspace, xtkoption, xtkfolder TO user;
      grant DELETE, INSERT, UPDATE ON nmspropositionrcp TO user;
      ```
   >[!NOTE]
   >
   >IP-adressen för kontrollinstansen måste auktoriseras för körningsinstanserna.

1. Konfigurera miljön:

   ![](assets/interaction_powerbooster2.png)

   * Lägg till listan med körningsinstanser.
   * För var och en av dem anger du synkroniseringsperiod och filtervillkor (till exempel per land).

      >[!NOTE]
      >
      >Om du råkar ut för ett fel kan du läsa arbetsflödena för synkronisering och visa meddelanden. Dessa finns i programmets tekniska arbetsflöden.

Om bara en del av marknadsföringsdatabasen dupliceras på körningsinstanserna av optimeringsskäl kan du ange ett begränsat schema som är länkat till miljön, så att användarna bara kan använda data som är tillgängliga på körningsinstanserna. Du kan skapa ett erbjudande med data som inte är tillgängliga för körningsinstanser. Om du vill göra det måste du inaktivera regeln för de andra kanalerna genom att begränsa den här regeln för den utgående kanalen (**[!UICONTROL Taken into account if]** fältet).

![](assets/ita_filtering.png)

## Underhållsalternativ {#maintenance-options}

Här är en lista över underhållsalternativ som är tillgängliga för kontrollinstansen:

>[!CAUTION]
>
>Dessa alternativ får endast användas för särskilda underhållsfall.

* **`NmsInteraction_LastOfferEnvSynch_<offerEnvId>_<executionInstanceId>`**: det senaste datumet då en miljö synkroniserades på en viss instans.
* **`NmsInteraction_LastPropositionSynch_<propositionSchema>_<executionInstanceIdSource>_<executionInstanceIdTarget>`**: det senaste datumet som förslag från ett givet schema synkroniserades från en instans till en annan.
* **`NmsInteraction_MapWorkflowId`**: ett alternativ med en lista över alla synkroniseringsarbetsflöden som genereras.

Följande alternativ är tillgängligt för körningsinstanser:

**NmsExecutionInstanceId**: som innehåller instans-ID:t.

## Paketinstallation {#packages-installation}

Om din instans inte tidigare har Interaction-paketet behövs ingen migrering. Som standard kommer förslagstabellen att vara 64 bitar efter att paketen har installerats.

>[!CAUTION]
>
>Beroende på volymen av befintliga förslag i din instans kan den här åtgärden ta en stund.

* Om instansen har små eller inga förslag behövs ingen manuell ändring av förslagstabellen. Ändringen görs när paket installeras.
* Om instansen har många förslag är det bättre att ändra strukturen på förslagstabellen innan du installerar kontrollpaketen och kör dem. Vi rekommenderar att du kör frågorna under en period med låg aktivitet.

>[!NOTE]
>
>Om du har utfört specifika konfigurationer i förslagstabellen, anpassar du frågorna därefter.

### PostgreSQL {#postgresql}

Det finns två metoder. Den första (med en arbetstabell) är något snabbare.

**Arbetsregister**

```
CREATE TABLE NmsPropositionRcp_tmp AS SELECT * FROM nmspropositionrcp WHERE 0=1;
ALTER TABLE nmspropositionrcp_tmp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
INSERT INTO nmspropositionrcp_tmp SELECT * FROM nmspropositionrcp;
DROP TABLE nmspropositionrcp;
CREATE INDEX proposition_id ON NmsPropositionRcp (ipropositionid);
CREATE INDEX nmspropositionrcp_deliveryid ON NmsPropositionRcp (ideliveryid);
CREATE INDEX nmspropositionrcp_lastmodified ON NmsPropositionRcp (tslastmodified);
CREATE INDEX nmspropositionrcp_offerid ON NmsPropositionRcp (iofferid);
CREATE INDEX nmspropositionrcp_offerspaceid ON NmsPropositionRcp (iofferspaceid);
CREATE INDEX nmspropositionrcp_recipientidid ON NmsPropositionRcp (irecipientid);
ALTER TABLE nmspropositionrcp_tmp RENAME TO nmspropositionrcp;
```

**Ändra tabell**

```
ALTER TABLE nmspropositionrcp
  ALTER COLUMN ipropositionid TYPE bigint,
  ALTER COLUMN iinteractionid TYPE bigint;
```

### Oracle {#oracle}

Att ändra storleken på en **Number** -typ leder inte till värden eller att indexet skrivs om. Den är därför omedelbar.

Följande fråga ska köras:

```
ALTER TABLE nmspropositionrcp MODIFY (
ipropositionid NUMBER(19, 0),
iinteractionid NUMBER(19, 0)
);
```

### MSSQL {#mssql}

Följande frågor ska utföras:

```
SELECT * INTO NmsPropositionRcp_tmp FROM NmsPropositionRcp WHERE 1 = 0;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN ipropositionid BIGINT;
GO
ALTER TABLE NmsPropositionRcp_tmp ALTER COLUMN iinteractionid BIGINT;
GO
INSERT INTO NmsPropositionRcp_tmp SELECT * FROM NmsPropositionRcp;
GO
DROP TABLE NmsPropositionRcp;
GO
sp_rename 'NmsPropositionRcp_tmp', NmsPropositionRcp
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR dWeight
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iDeliveryId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iEngineType
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iInteractionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iOfferSpaceId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iPropositionId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRank
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iRecipientId
GO
ALTER TABLE NmsPropositionRcp ADD DEFAULT ((0)) FOR iStatus
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_deliveryId ON NmsPropositionRcp (iDeliveryId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_eventDate ON NmsPropositionRcp (tsEvent)
GO
CREATE UNIQUE NONCLUSTERED INDEX NmsPropositionRcp_id ON NmsPropositionRcp (iPropositionId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_lastModified ON NmsPropositionRcp (tsLastModified)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerId ON NmsPropositionRcp (iOfferId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_offerSpaceI ON NmsPropositionRcp (iOfferSpaceId)
GO
CREATE NONCLUSTERED INDEX NmsPropositionRcp_recipientId ON NmsPropositionRcp (iRecipientId)
GO
```

