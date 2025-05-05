---
title: Uppdatera Campaign-gränssnittet efter IMS-migrering
description: Lär dig hur du aktiverar Adobe Identity Management systemmigreringsgränssnitt
exl-id: 8b13fe4d-d8d3-43b3-bbe4-c8c5574f585a
source-git-commit: 8eadea9f9cc0a44522726024bfbc825e3b4cad98
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# Uppdatera Campaign-gränssnittet efter IMS-migrering {#impact-ims-migration}

När du har [migrerat de tekniska operatorerna för Campaign till Developer Console](ims-migration.md) och [gått över till IMS för autentisering av slutanvändare](migrate-users-to-ims.md) är det sista steget att aktivera användargränssnittet och API-begränsningarna för att ta bort alternativ och funktioner som är specifika för inbyggd autentisering. Den här uppdateringen är tillgänglig från och med Campaign v7.4.1.

## Aktivera IMS-begränsningar {#ims-restrictions}

För att slutföra migreringen till IMS (Adobe Identify Management System) måste du blockera nya inbyggda användargenereringar, inbyggda användarinloggningar och API-åtkomst för inbyggda operatorer. Miljön är sedan säker och standardiserad.

Som hanterad Cloud Service/värdanvändare kontaktar du Adobe för att aktivera begränsningen och tillhörande uppdateringar i produktanvändargränssnittet.

Följ de här stegen om du är lokal/hybridanvändare:

1. Bläddra till avsnittet `<imsConfig>` i instanskonfigurationsfilen.
1. Om du vill aktivera gränssnittsbegränsningarna uppdaterar du alternativet `nonIMSOperatorMgmtInClientConsoleRestricted` i elementet `nonIMSOperatorMgmtInClientConsole` till `true` enligt nedan:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Om du vill aktivera API-begränsningar ska du uppdatera alternativet `disableAPI` i elementet `nonIMSAuthnAPI` till `true` enligt nedan:

   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSAuthnAPI disableAPI="true">
               ...
           </nonIMSAuthnAPI>
       </imsConfig>
   </shared>
   </serverConf>
   ```

Observera att ett fåtal operatorer tillåts ansluta till Adobe Campaign med inbyggd autentisering. Dessa tekniska operatorer är aktiverade som standard och får inte ändras. Om du vill tillåta det här undantaget läggs dessa tekniska operatorer till i listan över tillåtna som standard. Den här listan finns i avsnittet `<imsConfig>` i instanskonfigurationsfilen, i alternativet `allowOperator` i elementet `nonIMSAuthnAPI`.

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

Om du behöver lägga till en operator i tillåtelselista lägger du till ett nytt `allowOperator`-element med operatörens namn. Om du till exempel vill lägga till en ny operator med namnet `test` uppdaterar du det här avsnittet så här:

```xml
<serverConf>
  <shared>
    <imsConfig>
        <nonIMSAuthnAPI disableAPI="true">
            <allowOperator name="admin"/>
            <allowOperator name="aemserver"/>
            <allowOperator name="campaign-loginmonitor"/>
            <allowOperator name="internal|monitoring"/>
            <allowOperator name="test"/>
        </nonIMSAuthnAPI>
    </imsConfig>
  </shared>
</serverConf>
```

## Påverkar användargränssnittet {#ims-impacts}

När migreringen är klar och begränsningarna har tillämpats enligt beskrivningen nedan tillämpas följande ändringar på produkten och användargränssnittet.

### Operatörshantering {#manage-admin}

Du kan inte längre skapa, redigera, uppdatera eller ta bort operatorer med inbyggd autentisering från klientkonsolen.

Därför har dessa åtgärder inaktiverats i klientkonsolen.

Administrationen av operatorer är centraliserad i Adobe Admin Console och följande uppgifter hanteras nu uteslutande via denna konsol. Lär dig hur du skapar användare och tilldelar behörigheter i [Campaign v8-dokumentationen](https://experienceleague.adobe.com/sv/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Otillgängliga alternativ {#unavailable-migration}

Efter migreringen är följande uppgifter inte längre tillgängliga i klientkonsolen:

* Använd alternativet [Sammanfoga markerade rader](../../platform/using/updating-data.md#merge-data) för att sammanfoga operatorer.

* Uppdatera följande fält för dina operatorer:
   * Namn
   * Lösenord
   * Etikett
   * E-post

* [Återställ ditt kampanjlösenord](../../production/using/lost-password.md)

* Redigera operatorernas XML-källa

* Duplicera operatorer.


>[!MORELIKETHIS]
>
>* [Migrering av slutanvändare till IMS](migrate-users-to-ims.md)
>* [Migrering av tekniska operatorer till Adobe Developer-konsolen](ims-migration.md)
>* [Information om den senaste utgåvan av Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Vad är Adobe Identity Management System (IMS)](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"}
