---
product: campaign
title: Kom igång med behörigheter
description: Lär dig hur du ger tillgång till Campaign-funktioner
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: e1a085384fb27ec165c487c112fbc70fe9738d9e
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 4%

---

# Kom igång med behörigheter{#access-management}


>[!CAUTION]
>
>Från och med Campaign Classic v7.3.1 bör alla operatorer använda [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} för att ansluta till Campaign.
>
>Som en del i arbetet med att stärka säkerhets- och autentiseringsprocessen rekommenderar Adobe Campaign att man migrerar alla befintliga operatörers autentiseringsläge från den inbyggda autentiseringen av inloggnings-/lösenordsinformationen till Adobe Identity Management System (IMS). Lär dig hur du migrerar dina operatorer i [den här sidan](../../technotes/using/migrate-users-to-ims.md).
> 
>Observera att följande avsnitt inte längre gäller efter migreringen.  Lär dig hur du ställer in behörigheter med Adobe IMS i [Kampanjdokumentation v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.


Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna. Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner (via namngivna rättigheter).
* Tillgång till vissa register.
* Skapa, ändra och/eller ta bort poster (åtgärder, kontakter, kampanjer, grupper osv.).

Behörigheterna gäller för operatorprofiler eller operatorgrupper.

De fylls i av säkerhetsparametrar som är kopplade till operatörens anslutningsläge till Adobe Campaign. Mer information om säkerhetszoner i [den här sidan](../../installation/using/security-zones.md).

Det finns två typer av behörigheter som du kan ge en användare:

* Du kan definiera grupper av operatorer som du tilldelar rättigheter till och sedan associera operatorerna med en eller flera grupper. På så sätt kan du återanvända behörigheter och göra operatörsprofilerna mer enhetliga. Det underlättar också hantering och underhåll av profiler. Framtagning och hantering av grupper presenteras i [det här avsnittet](access-management-groups.md).

* Du kan tilldela namngivna rättigheter direkt till användare, i vissa fall för att överlagra rättigheterna som tilldelats via grupper. Dessa rättigheter presenteras i [den här sidan](access-management-named-rights.md).

>[!NOTE]
>
>Innan du börjar definiera behörigheter rekommenderar Adobe att du läser [Checklista för säkerhetskonfiguration](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy.html?lang=sv).

Lär dig hur du ger åtkomst och konfigurerar behörigheter i följande avsnitt:

* [Skapa operatorer](access-management-operators.md)

* [Definiera grupper](access-management-groups.md)

* [Lägg till namngivna rättigheter](access-management-named-rights.md)

* [Hantera mappåtkomst för kampanj](access-management-folders.md)

* [Matris för åtkomsträttigheter](access-management-named-rights.md#access-rights-matrix)


Se även:

* [Hantera behörigheter för arbetsflöden](../../workflow/using/managing-rights.md)
* [Hantera behörigheter för distribuerad marknadsföring](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Hantera behörigheter för interaktionsmodulen](../../interaction/using/operator-profiles.md)
* [Filtrera åtkomst till scheman](../../configuration/using/filtering-schemas.md)
* [Begränsa PI-vyn](../../configuration/using/restricting-pii-view.md)
