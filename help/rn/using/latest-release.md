---
product: campaign
title: Senaste versionen
description: Senaste versionsinformation för Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 8fec4d038eddaa3c5a2aade1b619f2543453d4de
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 100%

---

# Senaste versionen{#latest-release}

Den här sidan listar nya funktioner, förbättringar och korrigeringar som kommer med den **senaste versionen av Campaign Classic v7**. Varje ny version kommer med en status som visas med en färg. Läs mer om versionsstatusen för Campaign Classic v7 på [den här sidan](rn-overview.md).

## Version 7.3.5 – build 9368 {#release-7-3-5}

[!BADGE Allmän tillgänglighet]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=sv#rn-statuses" tooltip="Allmän tillgänglighet"}


_5 december 2023_


### Säkerhetsförbättringar {#release-7-3-5-security}


* Med Campaign Classic v7.3.5 har autentiseringsprocessen förbättrats och säkrats. Tekniska operatörer bör nu använda Adobe Identity Management System (IMS) för att ansluta till Campaign. Lär dig hur du migrerar dina befintliga tekniska konton i [det här tekniska dokumentet](../../technotes/using/ims-migration.md).

* Dessutom, som en del av arbetet med att förstärka säkerheten och autentiseringsprocessen, rekommenderar Adobe Campaign starkt att du migrerar slutanvändarautentiseringsläget från den inbyggda inloggnings-/lösenordsautentiseringen till Adobe Identity Management System (IMS). Läs om hur du migrerar dina operatörer i [det här tekniska dokumentet](../../technotes/using/migrate-users-to-ims.md).

* När ett webbformulär har statusen **Väntande publikation** blir den inte automatiskt aktiv. För att förhindra säkerhetsproblem måste den publiceras innan den kommer **Online** och kan nås via webbformulärets URL i en webbläsare. [Läs mer](../../web/using/publishing-a-web-form.md#life-cycle-of-a-form)

### Korrigeringar {#release-7-3-5-patches}

* Korrigerade ett problem när data från en Google Big Query-databas användes och data uppdaterades i en Oracle-databas: alla nycklar var inställda på `0` i arbetsflödets temporära tabell. (NEO-65091)
* Korrigerade ett problem som medförde att en arbetsflödeskörning misslyckades när två frågor i en Google Big Query-databas kombinerades i en arbetsflödesaktivitet med **sammanslutning**. (NEO-63705)
* Korrigerade ett problem som begärde att användaren skulle autentisera sig igen när användaren klickade på knappen `Back` i en Campaign-rapport. (NEO-65087)
* Korrigerade ett fel i arbetsflödet för databasrensning som inträffade när en leverans togs bort före leveransen. (NEO-48114)
* Korrigerade ett problem vid anslutning till klientkonsolen: senaste uppdateringar av TLS-verifiering ledde till anslutningsfel. (NEO-50488)
* Korrigerade ett problem med HTTP-proxyautentiseringen efter det att Campaign-efteruppgraderingen till 7.3.1. HTTP-begäranden i Campaign-arbetsflöden misslyckades med `error 407 – proxy auth required is returned`. (NEO-49624)
* Korrigerade ett tillfälligt fel med GPG-dekryptering i arbetsflödesaktiviteter med **skript**. Det associerade felmeddelandet var: `gpg: decryption failed: No secret key`. (NEO-50257)
  <!--* Workflow temporary tables now have a primary index in Teradata with a Federated Data Access (FDA) connection. (NEO-62575)-->

