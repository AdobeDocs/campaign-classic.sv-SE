---
product: campaign
title: Kom igång med behörigheter
description: Lär dig hur du ger tillgång till Campaign-funktioner
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Access Management, Permissions
exl-id: 9b616715-33cd-43ba-8548-8d96a179408e
source-git-commit: b27b85b126e002c0ea8b5d71da1ed60e1e817980
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 8%

---

# Kom igång med behörigheter{#access-management}


>[!CAUTION]
>
>Från och med Campaign Classic v7.3.1 bör alla operatorer använda [Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"} för att ansluta till Campaign.
>
>Som en del i arbetet med att stärka säkerhets- och autentiseringsprocessen rekommenderar Adobe Campaign att man migrerar alla befintliga operatörers autentiseringsläge från den inbyggda autentiseringen av inloggnings-/lösenordsinformationen till Adobe Identity Management System (IMS). Lär dig hur du migrerar dina operatorer på [den här sidan](../../technotes/using/migrate-users-to-ims.md).
> 
>Observera att följande avsnitt inte längre gäller efter den här migreringen.  Lär dig hur du konfigurerar behörigheter med Adobe IMS i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.


Med Adobe Campaign kan du definiera och hantera de rättigheter som tilldelats de olika operatorerna. Detta är en uppsättning rättigheter och begränsningar som tillåter eller nekar:

* Tillgång till vissa funktioner (via namngivna rättigheter).
* Tillgång till vissa register.
* Skapa, ändra och/eller ta bort poster (åtgärder, kontakter, kampanjer, grupper osv.).

>[!BEGINTABS]

>[!TAB Behörighetsdokumentation]

Mer information om behörigheter i Adobe Campaign finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}.

[![bild](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}

>[!TAB Hantera mappåtkomst]

Mer information om mappåtkomst och hur du hanterar dem finns i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/folder-permissions?lang=en#_blank){target=_blank}.

[![Bild](../../assets/do-not-localize/learn-more-button.svg)]([![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions?lang=en#_blank){target=_blank}){target=_blank}

>[!ENDTABS]

<!--
The permissions apply to operator profiles or operator groups.

They are completed by safety parameters linked to the operator's connection mode to Adobe Campaign. For more about security zones in [this page](../../installation/using/security-zones.md).

There are two types of permissions you can grant to a user:

* You can define groups of operators to which you attribute rights, then associate the operators with one or more groups. This enables you to reuse rights and make operator profiles more consistent. It also facilitates the management and maintenance of profiles. Group creation and management are presented in [this section](access-management-groups.md).

* You can attribute named rights directly to users, in some cases to overload the rights allocated via groups. These rights are presented in [this page](access-management-named-rights.md).

>[!NOTE]
>
> * Before starting defining permissions, Adobe recommends you to read the [Security configuration checklist](https://helpx.adobe.com/campaign/kb/acc-security.html).
> * To learn more about permissions, please refer to the detailed explanation on the [Campaign v8 documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/gs-permissions){target=_blank}.

Learn how to grant access and set up permissions in these sections:

* [Create operators](access-management-operators.md)

* [Define groups](access-management-groups.md)

* [Add Named rights](access-management-named-rights.md)

* [Manage Campaign folder access](access-management-folders.md)

* [Access rights matrix](access-management-named-rights.md#access-rights-matrix)


See also:

* [Manage permissions for workflows](../../workflow/using/managing-rights.md)
* [Manage permissions for distributed marketing](../../distributed/using/about-distributed-marketing.md#operators-and-entities)
* [Manage permissions for the interaction module](../../interaction/using/operator-profiles.md)
* [Filter access to schemas](../../configuration/using/filtering-schemas.md)
* [Restricting PI view](../../configuration/using/restricting-pii-view.md)
-->