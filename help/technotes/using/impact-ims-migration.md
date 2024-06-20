---
title: Uppdatera Campaign-gränssnittet efter IMS-migrering
description: Lär dig hur du aktiverar Adobe Identity Management systemmigreringsgränssnitt
source-git-commit: ab1bb91bdbc9961b4f3f0feba7cfd354b02b6511
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# Uppdatera Campaign-gränssnittet efter IMS-migrering {#impact-ims-migration}

När du har [migrerade era era tekniska kampanjoperatörer till Developer Console](ims-migration.md) och [har överförts till IMS för autentisering av slutanvändare](migrate-users-to-ims.md)är det sista steget att aktivera användargränssnittet och API-begränsningarna för att ta bort alternativ och funktioner som är specifika för inbyggd autentisering. Den här uppdateringen är tillgänglig från och med Campaign v7.4.1.

## Aktivera IMS-begränsningar {#ims-restrictions}

För att slutföra migreringen till IMS (Adobe Identify Management System) måste du blockera nya inbyggda användargenereringar, inbyggda användarinloggningar och API-åtkomst för inbyggda operatorer. Miljön är sedan säker och standardiserad.

Som hanterad Cloud Service/värdanvändare kontaktar du Adobe för att aktivera begränsningen och tillhörande uppdateringar i produktanvändargränssnittet.

Följ de här stegen om du är lokal/hybridanvändare:

1. Gå till `<imsConfig>` i instanskonfigurationsfilen.
1. Om du vill aktivera gränssnittsbegränsningar uppdaterar du `nonIMSOperatorMgmtInClientConsoleRestricted` -alternativ, i `nonIMSOperatorMgmtInClientConsole` element, till `true`, enligt nedan:


   ```xml
   <serverConf>
   <shared>
       <imsConfig>
           <nonIMSOperatorMgmtInClientConsole nonIMSOperatorMgmtInClientConsoleRestricted="true"/>
       </imsConfig>
   </shared>
   </serverConf>
   ```

1. Om du vill aktivera API-begränsningar uppdaterar du `disableAPI` -alternativ, i `nonIMSAuthnAPI` element, till `true`, enligt nedan:

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

Observera att ett fåtal operatorer tillåts ansluta till Adobe Campaign med inbyggd autentisering. Dessa tekniska operatorer är aktiverade som standard och får inte ändras. Om du vill tillåta det här undantaget läggs dessa tekniska operatorer till i listan över tillåtna som standard. Den här listan finns i `<imsConfig>` i instanskonfigurationsfilen, i `allowOperator` i `nonIMSAuthnAPI` -element.

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

Om du behöver lägga till en operator i tillåtelselista lägger du till en ny `allowOperator` -element med operatorns namn. Om du till exempel vill lägga till en ny operator med namnet `test`uppdaterar du det här avsnittet enligt följande:

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

Administrationen av operatorer är centraliserad i Adobe Admin Console och följande uppgifter hanteras nu uteslutande via denna konsol. Lär dig hur du skapar användare och tilldelar behörigheter i [Kampanjdokumentation v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/admin/permissions/manage-permissions){target="_blank"}.

### Otillgängliga alternativ {#unavailable-migration}

Efter migreringen är följande uppgifter inte längre tillgängliga i klientkonsolen:

* Använd [Lägg samman markerade rader, alternativ](../../platform/using/updating-data.md#merge-data) för att sammanfoga operatorer.

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
>* [Migrering av tekniska operatörer till Adobe Developer Console](ims-migration.md)
>* [Adobe Campaign Classic v7 senaste versionsinformation](../../rn/using/latest-release.md)
>* [Vad är Adobe Identity Management System (IMS)](https://helpx.adobe.com/enterprise/using/identity.html){target="_blank"}

