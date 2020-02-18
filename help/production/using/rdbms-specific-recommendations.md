---
title: RDBMS-specifika rekommendationer
seo-title: RDBMS-specifika rekommendationer
description: RDBMS-specifika rekommendationer
seo-description: null
page-status-flag: never-activated
uuid: 637c1b5a-0484-4734-a012-eb4ba8036263
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: b2219912-5570-45d2-8b52-52486e29d008
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 8fd9949ec03b7c2cdf88a9d5fcf5c8d8fd85f7d0

---


# RDBMS-specifika rekommendationer{#rdbms-specific-recommendations}

I det här avsnittet beskrivs några rekommendationer/bästa metoder som är anpassade till de olika RDBMS-motorer som Adobe Campaign stöder, så att du enklare kan konfigurera underhållsplaner. Detta är dock bara rekommendationer. Det är upp till er att anpassa dem efter era behov, i enlighet med era interna rutiner och begränsningar. Databasadministratören ansvarar för att skapa och genomföra dessa planer.

## PostgreSQL {#postgresql}

### Identifiera stora tabeller {#detecting-large-tables}

1. Du kan lägga till följande vy i databasen:

   ```
   create or replace view uvSpace
    as
    SELECT c1.relname AS tablename, c2.relname AS indexname, c2.relpages * 8 / 1024 AS size_mbytes, c2.relfilenode AS filename, 0 AS row_count
    FROM pg_class c1, pg_class c2, pg_index i
    WHERE c1.oid = i.indrelid AND i.indexrelid = c2.oid
    UNION 
    SELECT pg_class.relname AS tablename, NULL::"unknown" AS indexname, pg_class.relpages * 8 / 1024 AS size_mbytes, pg_class.relfilenode AS filename, cast(pg_class.reltuples as integer) AS row_count
    FROM pg_class
    WHERE pg_class.relkind = 'r'::"char"
    ORDER BY 3 DESC, 1, 2 DESC;
   ```

1. Om du kör följande kommando kan du identifiera stora tabeller och index:

   ```
   select * from uvSpace;
   ```

### Enkelt underhåll {#simple-maintenance}

Under PostgreSQL är de kommandon som du kan använda **vakuumfulla** och **omindexerade**.

Här är ett typiskt exempel på en SQL-underhållsplan som ska utföras regelbundet med dessa två kommandon:

```
vacuum full nmsdelivery;
 reindex table nmsdelivery;
 
 vacuum full nmsdeliverystat;
 reindex table nmsdeliverystat;
 
 vacuum full xtkworkflow;
 reindex table xtkworkflow;
 
 vacuum full xtkworkflowevent;
 reindex table xtkworkflowevent;
 
 vacuum full xtkworkflowjob;
 reindex table xtkworkflowjob;
 
 vacuum full xtkworkflowlog;
 reindex table xtkworkflowlog;
 
 vacuum full xtkworkflowtask;
 reindex table xtkworkflowtask;
 
 vacuum full xtkjoblog;
 reindex table xtkjoblog;
 
 vacuum full xtkjob;
 reindex table xtkjob;
 
 vacuum full nmsaddress;
 reindex table nmsaddress;

 vacuum full nmsdeliverypart;
 reindex table nmsdeliverypart;
 
 vacuum full nmsmirrorpageinfo;
 reindex table nmsmirrorpageinfo;
```

>[!NOTE]
>
>* Adobe rekommenderar att du börjar med mindre tabeller: På så sätt har åtminstone en del av underhållet slutförts om processen misslyckas på stora tabeller (där risken för fel är störst).
>* Adobe rekommenderar att du lägger till tabeller som är specifika för din datamodell och som kan uppdateras avsevärt. Detta kan vara fallet för **NmsRecipient** om du har stora dagliga datareplikeringsflöden.
>* Kommandona **vakuum** och **omindexering** låser tabellen, som pausar vissa processer medan underhåll utförs.
>* För mycket stora tabeller (vanligtvis över 5 GB) kan **vakuumfyllnad** bli ganska ineffektivt och ta mycket lång tid. Adobe rekommenderar inte att du använder den för **tabellen YyyNmsBroadLogXx** .
>* Den här underhållsåtgärden kan implementeras av ett Adobe Campaign-arbetsflöde, med en **[!UICONTROL SQL]** aktivitet (mer information finns i [det här avsnittet](../../workflow/using/executing-a-workflow.md#architecture)). Se till att du schemalägger underhåll under en tid med låg aktivitet som inte kolliderar med säkerhetskopieringsfönstret.
>



### Återskapa en databas {#rebuilding-a-database}

PostgreSQL är inte ett enkelt sätt att återskapa en tabell online eftersom **vakuumfullt** låser tabellen, vilket förhindrar normal produktion. Detta innebär att underhåll måste utföras när tabellen inte används. Du kan antingen:

* utföra underhåll när Adobe Campaign-plattformen stoppas,
* stoppa de olika undertjänster i Adobe Campaign som kan tänkas skriva i tabellen som återskapas (**nlserver stop wfserver instance_name** för att stoppa arbetsflödesprocessen).

Här är ett exempel på tabelldefragmentering som använder specifika funktioner för att generera nödvändig DDL. Med följande SQL kan du skapa två nya funktioner: **GenRebuildTablePart1** och **GenRebuildTablePart2**, som kan användas för att generera den DDL som krävs för att återskapa en tabell.

* Med den första funktionen kan du skapa en arbetstabell (** _tmp** här) som är en kopia av den ursprungliga tabellen.
* Den andra funktionen tar sedan bort den ursprungliga tabellen och byter namn på arbetstabellen och dess index.
* Om du använder två funktioner i stället för en innebär det att du inte riskerar att ta bort den ursprungliga tabellen om den första inte fungerar.

```
 -- --------------------------------------------------------------------------
 -- Generate the CREATE TABLE DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenTableDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecFld RECORD;
 vstrDDL text;
 vstrFields text;
 vstrNsTable text;
 vstrTableSpace text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 SELECT
 pg_catalog.quote_ident(n.nspname) || '.' || pg_catalog.quote_ident(c.relname),
 pg_catalog.quote_ident(t.spcname)
 INTO
 vstrNsTable, vstrTableSpace
 FROM
 pg_namespace n, pg_class c left outer join pg_tablespace t on c.reltablespace = t.oid
 WHERE
 n.oid = c.relnamespace AND
 c.relname = vstrTable;
 
 vstrDDL = 'CREATE TABLE ' || vstrNsTable || '_tmp(';
 
 vstrFields = ;
 FOR vrecFld IN
 SELECT
 pg_catalog.quote_ident(a.attname) ||
 ' ' || t.typname ||
 case when t.typname='varchar' then '(' || cast(a.atttypmod-4 as text) || ')'
 when t.typname='numeric' then '(' || cast((a.atttypmod-4)/65536 as text) || ',' || cast((a.atttypmod-4)%65536 as text) || ')'
 else end ||
 case when a.attnotnull then ' not null' else end ||
 case when a.atthasdef then ' default '|| d.adsrc else end as DDL
 FROM
 pg_type t, pg_class c, pg_attribute a LEFT OUTER JOIN pg_attrdef d ON d.adrelid=a.attrelid and d.adnum=a.attnum
 WHERE 
 a.attnum > 0 AND
 a.attrelid = c.oid AND
 t.oid = a.atttypid AND
 c.relname = vstrTable
 ORDER BY
 a.attnum
 LOOP
 IF vstrFields <> THEN
 vstrFields = vstrFields || ',' || chr(10) || ' ';
 ELSE
 vstrFields = vstrFields || chr(10) || ' ';
 END IF;
 vstrFields = vstrFields || vrecFld.DDL;
 END LOOP;
 
 vstrDDL = vstrDDL || vstrFields || chr(10) || ')';
 if vstrTableSpace <> then
 vstrDDL = vstrDDL || ' TABLESPACE ' || vstrTableSpace;
 end if;
 vstrDDL = vstrDDL || ';' || chr(10);
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the CREATE INDEX DDL for a table
 -- --------------------------------------------------------------------------
 create or replace function GenIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 viFld integer;
 vstrFld text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
 SELECT
 i.indkey, i.indisunique,
 pg_catalog.quote_ident(c.relname) as tablename,
 pg_catalog.quote_ident(ic.relname) as indexname,
 pg_catalog.quote_ident(t.spcname) as tablespace
 FROM
 pg_class c, pg_index i, pg_class ic left outer join pg_tablespace t on ic.reltablespace = t.oid
 WHERE
 i.indexrelid = ic.oid AND
 i.indrelid = c.oid AND
 c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'CREATE ';
  if vrecIndex.indisunique then
  vstrDDL = vstrDDL || 'UNIQUE ';
  end if;
  vstrDDL = vstrDDL ||
   'INDEX ' ||vrecIndex.indexname || '_tmp ON ' ||
   vrecIndex.tablename || '_tmp(';
 
  FOR viFld IN array_lower(vrecIndex.indkey, 1) .. array_upper(vrecIndex.indkey, 1) LOOP
  SELECT pg_catalog.quote_ident(a.attname) INTO vstrFld 
  FROM 
   pg_attribute a, pg_class c
  WHERE 
   a.attnum = vrecIndex.indkey[viFld] AND
   a.attrelid = c.oid AND c.relname=vstrTable;
  
  vstrDDL = vstrDDL || vstrFld;
  if viFld <> array_upper(vrecIndex.indkey, 1) then
   vstrDDL = vstrDDL || ', ';
  end if;
  END LOOP;
  vstrDDL = vstrDDL || ')';
 
  if vrecIndex.tablespace <> then
  vstrDDL = vstrDDL || 'TABLESPACE ' || vrecIndex.tablespace;
  end if;
  vstrDDL = vstrDDL || ';' || chr(10);
 
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Generate the ALTER INDEX RENAME for a table
 -- --------------------------------------------------------------------------
 create or replace function GenRenameIndexDDL(text) returns text as $$
 declare
 vstrTable text;
 vrecIndex RECORD;
 vstrDDL text;
 begin
 vstrTable = lower($1);
 
 vstrDDL = ;
 
 FOR vrecIndex IN
  SELECT
  pg_catalog.quote_ident(n.nspname) as namespace,
  pg_catalog.quote_ident(ic.relname) as indexname
  FROM
  pg_namespace n, pg_class c, pg_index i, pg_class ic
  WHERE
  i.indexrelid = ic.oid AND
  n.oid = ic.relnamespace AND
  i.indrelid = c.oid AND
  c.relname = vstrTable
 LOOP
 
  vstrDDL = vstrDDL || 'ALTER INDEX ' || vrecIndex.namespace || '.' || vrecIndex.indexname ||
    '_tmp RENAME TO ' || vrecIndex.indexname ||
    ';' || chr(10);
 END LOOP;
 
 return vstrDDL;
 END;
 $$ LANGUAGE plpgsql;

 -- --------------------------------------------------------------------------
 -- Build a copy of a table, with index
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart1(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = ;
 
 SELECT GenTableDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 vstrDDL = vstrDDL|| 'INSERT INTO ' || vstrTable || '_tmp SELECT * FROM ' || vstrTable || ';'||chr(10);
 SELECT GenIndexDDL(vstrTable) INTO vstrTmp;
 
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 vstrDDL = vstrDDL|| 'VACUUM ANALYSE '|| vstrTable || '_tmp;' ||chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
 
 -- --------------------------------------------------------------------------
 -- Drop the original table and rename the copy
 -- --------------------------------------------------------------------------
 create or replace function GenRebuildTablePart2(text) returns text as $$
 declare
 vstrTable text;
 vstrTmp text;
 vstrDDL text;
 begin
 vstrTable = lower($1);
  
 vstrDDL = 'DROP TABLE ' || vstrTable||';'|| chr(10);
 vstrDDL = vstrDDL|| 'ALTER TABLE ' || vstrTable || '_tmp RENAME TO ' || vstrTable ||';'|| chr(10);
 
 SELECT GenRenameIndexDDL(vstrTable) INTO vstrTmp;
 vstrDDL = vstrDDL|| vstrTmp || chr(10);
 
 return vstrDDL;
 end;
 $$ LANGUAGE plpgsql;
```

Följande exempel kan användas i ett arbetsflöde för att återskapa de tabeller som behövs i stället för att använda kommandot **vakuum/rebuild** :

```
function sqlGetMemo(strSql)
 {
 var res = sqlSelect("s, m:memo", strSql);
 return res.s.m.toString();
 }

 function RebuildTable(strTable)
 {
 // Rebuild a table_tmp
 var strSql = sqlGetMemo("select GenRebuildTablePart1('"+strTable+"')");
 logInfo("Rebuilding table '"+strTable+"'...");
 // logInfo(strSql);
 sqlExec(strSql);
 
 // If fails, there is an exception thrown and so we do not delete the original table
 strSql = sqlGetMemo("select GenRebuildTablePart2('"+strTable+"')");
 logInfo("Swapping table '"+strTable+"'...");
 //logInfo(strSql);
 sqlExec(strSql);
 }
 
 RebuildTable('nmsrecipient');
 RebuildTable('nmsrcpgrlrel');
 // ... other tables here
```

## Oracle {#oracle}

Kontakta din databasadministratör för att ta reda på vilka procedurer som passar din version av Oracle bäst.

## Microsoft SQL Server {#microsoft-sql-server}

>[!NOTE]
>
>För Microsoft SQL Server kan du använda underhållsplanen som beskrivs [på den här sidan](https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html).

Exemplet nedan gäller Microsoft SQL Server 2005. Om du använder en annan version kontaktar du databasadministratören för att få reda på mer om underhållsrutiner.

1. Anslut först till Microsoft SQL Server Management Studio med administratörsbehörighet.
1. Gå till **[!UICONTROL Management > Maintenance Plans]** mappen, högerklicka på den och välj **[!UICONTROL Maintenance Plan Wizard]**
1. Klicka **[!UICONTROL Next]** när den första sidan visas.
1. Välj den typ av underhållsplan som du vill skapa (separata scheman för varje aktivitet eller ett enda schema för hela planen) och klicka sedan på **[!UICONTROL Change...]** knappen.
1. Välj önskade körningsinställningar i **[!UICONTROL Job schedule properties]** fönstret och klicka sedan på **[!UICONTROL OK]** . **[!UICONTROL Next]** .
1. Välj de underhållsåtgärder du vill utföra och klicka sedan på **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >Vi rekommenderar att du utför åtminstone de underhållsåtgärder som visas nedan. Du kan också välja statistikuppdateringsuppgiften, även om den redan har utförts i arbetsflödet för databasrensning.

1. I listrutan väljer du den databas som du vill köra uppgiften på **[!UICONTROL Database Check Integrity]** .
1. Markera databasen och klicka på **[!UICONTROL OK]** och sedan på **[!UICONTROL Next]** .
1. Konfigurera den största storlek som databasen tilldelas och klicka sedan på **[!UICONTROL Next]** .

   >[!NOTE]
   >
   >Om storleken på databasen överstiger det här tröskelvärdet kommer underhållsplanen att försöka ta bort oanvända data för att frigöra utrymme.

1. Ordna om eller återskapa indexet:

   * Om indexfragmenteringsgraden är mellan 10 % och 40 % rekommenderas en omorganisering.

      Välj vilka databaser och objekt (tabeller eller vyer) du vill ordna om och klicka sedan på **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >Beroende på hur konfigurationen ser ut kan du välja antingen de tidigare markerade tabellerna eller alla tabeller i databasen.

   * Om indexfragmenteringshastigheten är högre än 40 % rekommenderas en omgenerering.

      Välj de alternativ du vill använda för att återskapa index och klicka sedan på **[!UICONTROL Next]** .

      >[!NOTE]
      >
      >Återskapandeindexprocessen är mer begränsad vad gäller processoranvändning och låser databasresurserna. Markera **[!UICONTROL Keep index online while reindexing]** alternativet om du vill att indexet ska vara tillgängligt under återskapandet.

1. Välj de alternativ som du vill visa i aktivitetsrapporten och klicka sedan på **[!UICONTROL Next]** .
1. Kontrollera listan över uppgifter som har konfigurerats för underhållsplanen och klicka sedan på **[!UICONTROL Finish]** .

   En sammanfattning av underhållsplanen och statusvärdena för de olika stegen visas.

1. När underhållsplanen är klar klickar du på **[!UICONTROL Close]** .
1. Dubbelklicka på **[!UICONTROL Management > Maintenance Plans]** mappen i Microsoft SQL Server Explorer.
1. Välj underhållsplanen för Adobe Campaign: de olika stegen beskrivs i ett arbetsflöde.

   Observera att ett objekt har skapats i **[!UICONTROL SQL Server Agent > Jobs]** mappen. Med det här objektet kan du starta underhållsplanen. I vårt exempel finns det bara ett objekt eftersom alla underhållsåtgärder ingår i samma plan.

   >[!CAUTION]
   >
   >Microsoft SQL Server-agenten måste vara aktiverad för att det här objektet ska kunna köras.

**Konfigurera en separat databas för arbetsregister**

>[!NOTE]
>
>Den här konfigurationen är valfri.

Med alternativet **WdbcOptions_TempDbName** kan du konfigurera en separat databas för fungerande tabeller på Microsoft SQL Server. Detta optimerar säkerhetskopiering och replikering.

Det här alternativet kan användas om du vill att arbetsregister (t.ex. tabeller som skapas när ett arbetsflöde körs) ska skapas i en annan databas.

När du anger alternativet &quot;tempdb.dbo.&quot; skapas arbetstabeller i standarddatabasen för Microsoft SQL Server. Databasadministratören måste tillåta skrivåtkomst till tempdb-databasen.

Om alternativet är inställt används det på alla Microsoft SQL Server-databaser som är konfigurerade i Adobe Campaign (huvuddatabas och externa konton). Observera att om två externa konton delar samma server kan konflikter uppstå (eftersom tempdb blir unik). På samma sätt kan konflikter uppstå om två Campaign-instanser använder samma MSSQL-server om de använder samma tempdb.
