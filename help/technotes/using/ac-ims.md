---
title: Migrera till Adobe Identity Management System (IMS)
description: Lär dig hur du migrerar autentiseringsprocessen till Adobe Identity Management System (IMS)
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# Migrera till Adobe Identity Management System (IMS) {#migrate-to-ims}

Som en del av arbetet med att förstärka säkerhets- och autentiseringsprocessen rekommenderar Adobe Campaign att du migrerar slutanvändarautentiseringsläget från den inbyggda autentiseringen av inloggnings-/lösenordsinformationen till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

Dessutom anropar Adobe Campaign klientprogram nu Campaign-API:er direkt med IMS-token för tekniskt konto. Du måste migrera dina tekniska operatorer till Adobe Developer Console.

>[!CAUTION]
>
>Den här ändringen gäller redan i Campaign Classic v7 och kommer att vara **obligatorisk** för att gå över till Campaign v8. Inbyggd autentisering av användare/lösenord tillåts inte i Campaign v8. **Adobe rekommenderar att du utför den här migreringen från Campaign v7.3.5 för att smidigt kunna migrera till Campaign v8.**
>

## Migreringssteg {#ims-steps}

Migrering till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} är ett säkerhetskrav för att göra dina miljöer säkra och standardiserade, eftersom de flesta andra Adobe Experience Cloud-lösningar och -appar redan finns på IMS.

Adobe stöder dig i den här migreringen. Detaljerade riktlinjer för sammanhang och steg för steg finns i följande artiklar:

* Migrering för autentisering av slutanvändare beskrivs på [den här sidan](migrate-users-to-ims.md).
* Migreringen för autentisering av tekniska operatorer beskrivs på [den här sidan](ims-migration.md).
* Från och med Campaign v7.4.1 aktiverar du användargränssnittet och API-begränsningarna för att ta bort alternativ och funktioner som är specifika för inbyggd autentisering, vilket beskrivs i [den här sidan](impact-ims-migration.md).


## IMS-migreringskompatibla versioner {#ims-versions}

En förutsättning för migreringen är att du uppgraderar miljön till någon av följande produktversioner:

* Campaign v7.4.1 (rekommenderas)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

De här kampanjversionerna beskrivs i [versionsinformationen](../../rn/using/latest-release.md).

## Vanliga frågor och svar {#ims-migration-faq}

### När kan jag starta migreringen? {#ims-migration-start}

En rekommendation för migrering till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} är att uppgradera din miljö till Campaign Classic v7.4.1 (eller en [IMS-migreringskompatibel version](#ims-versions)).

Du kan starta IMS-migrering på din scenmiljö när den har uppgraderats till den senaste versionen och därefter planera för produktionsmiljön.

### Vad händer efter en uppgradering till Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

När dina miljöer har uppgraderats till Campaign Classic v7.4.1 (eller en [IMS-migreringskompatibel version](#ims-versions)) kan du initiera övergången till [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}.

### När är migreringen klar? {#ims-migration-end}

När migreringen av slutanvändare och migreringen av tekniska operatörer till Adobe Identity Management System (IMS) är klar måste du uppdatera miljön för att ta bort alternativ som är specifika för den inbyggda autentiseringen och inte längre gäller för IMS-autentisering. Den här uppdateringen är bara tillgänglig från och med Campaign v7.4.1. [Läs mer](impact-ims-migration.md)



## Användbara länkar {#ims-useful-links}

* [Migrering av slutanvändare till IMS](migrate-users-to-ims.md)
* [Migrering av tekniska operatörer till Adobe Developer Console](ims-migration.md)
* [Adobe Campaign Classic v7 senaste versionsinformation](../../rn/using/latest-release.md)
* [Vad är Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}
