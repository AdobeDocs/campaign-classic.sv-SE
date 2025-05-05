---
product: campaign
title: Kom igång med Campaign-operatörer
description: Lär dig hur du skapar och hanterar kampanjanvändare
badge: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 2%

---

# Skapa och hantera operatörer {#operators}

>[!CAUTION]
>
>Från och med Campaign Classic v7.3.1 ska alla operatorer använda [Adobe Identity Management System (IMS)](https://helpx.adobe.com/se/enterprise/using/identity.html){target="_blank"} för att ansluta till Campaign.
>
>Som en del i arbetet med att stärka säkerhets- och autentiseringsprocessen rekommenderar Adobe Campaign att man migrerar alla befintliga operatörers autentiseringsläge från den inbyggda autentiseringen av inloggnings-/lösenordsinformationen till Adobe Identity Management System (IMS). Lär dig hur du migrerar dina operatorer på [den här sidan](../../technotes/using/migrate-users-to-ims.md).
> 
>Observera att följande avsnitt inte längre gäller efter migreringen.  Lär dig hur du ställer in behörigheter med Adobe IMS i [dokumentationen för Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=sv-SE){target="_blank"}.


## Kom igång med Campaign-operatörer {#about-operators}

>[!NOTE]
>
>Dessa procedurer gäller endast för operatorer som ansluter till Campaign med inbyggd autentisering. Information om Adobe IMS-autentisering finns i [den här dokumentationen](https://helpx.adobe.com/se/enterprise/using/manage-users-individually.html#_blank).

En operator är en Adobe Campaign-användare som har behörighet att logga in och utföra åtgärder.

Som standard lagras operatorer i noden **[!UICONTROL Administration > Access management > Operators]**.

![](assets/s_ncs_user_list_operators.png)

Operatorer kan skapas manuellt eller mappas på en befintlig LDAP-katalog.

En fullständig procedur för att skapa en operator beskrivs på [den här sidan](#creating-an-operator).

Mer information om Adobe Campaign- och LDAP-integrering finns på [den här sidan](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>Operatorer måste länkas till en säkerhetszon för att kunna logga in på en instans. Mer information om säkerhetszoner i Adobe Campaign finns på [den här sidan](../../installation/using/security-zones.md).

Användare kan även ansluta direkt till Adobe Campaign via sin Adobe ID. Se denna [sida](../../integrations/using/about-adobe-id.md) för mer information om detta.

## Skapa en operator {#creating-an-operator}

Så här skapar du en ny operator och tilldelar behörigheter:

1. Klicka på knappen **[!UICONTROL New]** ovanför listan med operatorer och ange information om operatorn new.

   ![](assets/s_ncs_user_operator_new.png)

1. Ange användarens **[!UICONTROL Identification parameters]**: användarens inloggning, lösenord och namn. Inloggningen och lösenordet används av operatören för att logga in på Adobe Campaign. När användaren är inloggad kan han/hon ändra sitt lösenord via menyn **[!UICONTROL Tools > Change password]**. Operatorns e-postadress är viktig eftersom den gör det möjligt för operatorn att ta emot meddelanden, till exempel när godkännanden bearbetas.

   I det här avsnittet kan du även länka en operator till en organisationsenhet. Mer information finns på [den här sidan](../../distributed/using/about-distributed-marketing.md).

1. Välj behörigheter för operatorn i avsnittet **[!UICONTROL Operator access rights]**.

   Om du vill tilldela behörigheter till operatorn klickar du på knappen **[!UICONTROL Add]** ovanför listan med rättigheter och väljer sedan en grupp med operatorer i listan över tillgängliga grupper:

   ![](assets/s_ncs_user_permissions_operators.png)

   Du kan också välja en eller flera namngivna rättigheter (se [Namngivna rättigheter](#named-rights)). Det gör du genom att klicka på pilen till höger om fältet **[!UICONTROL Folder]** och välja **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Välj grupper och/eller namngivna rättigheter som ska tilldelas och klicka på **[!UICONTROL OK]** för att validera.

1. Klicka på **[!UICONTROL Ok]** för att skapa operatorn: profilen läggs till i listan med befintliga operatorer.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>Du kan ordna operatorerna efter dina behov genom att skapa nya operatormappar. Om du vill göra det högerklickar du på operatormappen och väljer **[!UICONTROL Add an 'Operators' folder]**.

När operatörens profil har skapats kan du lägga till eller uppdatera informationen för den. Klicka på fliken **[!UICONTROL Edit]** om du vill göra det.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>I fältet **[!UICONTROL Session timeout]** kan du justera fördröjningen innan tidsgränsen för FDA-sessionen har uppnåtts. Mer information finns i [Om åtkomst till federerade data](../../installation/using/about-fda.md).

## Definiera operatorns tidszon {#time-zone-of-the-operator}

På fliken **[!UICONTROL General]** kan du välja operatörens tidszon. Som standard arbetar operatorer i serverns tidszon. Det går dock att välja en annan tidszon med hjälp av listrutan.

Konfigurationen av tidszoner beskrivs på [den här sidan](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>För samarbete inom olika tidszoner krävs att datum lagras i UTC. Datum konverteras i lämplig tidszon i följande sammanhang: när ett datum visas i användartidszonen, när filer importeras och exporteras, när en e-postleverans schemaläggs, när aktiviteter schemaläggs i ett arbetsflöde (schemaläggare, vänta, tidsbegränsning osv.)
>
>Begränsningar och rekommendationer som är kopplade till dessa sammanhang presenteras i relaterade avsnitt i Adobe Campaign-dokumentationen.

I listrutan **[!UICONTROL Regional settings]** kan du dessutom välja format för att visa datum och nummer.

## Lägg till behörigheter {#access-rights-options}

Använd fliken **[!UICONTROL Access rights]** för att uppdatera grupper och namngivna rättigheter som är länkade till operatorn.

![](assets/operator_profile_security_options.png)

Med länken **[!UICONTROL Edit the access parameters...]** kan du komma åt följande alternativ:

* Med alternativet **[!UICONTROL Disable account]** kan du inaktivera operatörens konto: den här användaren kommer inte längre att ha åtkomst till Adobe Campaign.

  >[!NOTE]
  >
  >Även om deras konto är inaktiverat kan operatorn fortfarande ta emot aviseringar eller meddelanden från Campaign. Om du inte längre vill skicka Campaign-meddelanden till den här operatorn rekommenderar Adobe att du tar bort e-postadressen från deras profil.

* Med alternativet **[!UICONTROL Forbid access from the rich client]** kan du begränsa användningen av Adobe Campaign till [webbåtkomst](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) eller via API:er: åtkomst till Adobe Campaign klientkonsol är inte längre tillgängligt.
* Det går att länka en säkerhetszon till operatören. Mer information finns på [den här sidan](../../installation/using/security-zones.md).
* Du kan också definiera en betrodd IP-mask med hjälp av lämplig länk.

  Operatören kan ansluta till Adobe Campaign utan att ange sitt lösenord om IP-adressen finns i listan.

  Du kan också ange en uppsättning IP-adresser som ska auktoriseras att ansluta utan lösenord, som i följande exempel:

  ![](assets/operator_trustip.png)

  >[!NOTE]
  >
  >För att åtkomsten till din plattform ska vara säker måste det här alternativet användas med försiktighet.

* Med alternativet **[!UICONTROL Restrict to information found in sub-folders of:]** kan du begränsa rättigheterna som tilldelats en mapps operator. Endast undermapparna för noden som anges i det här alternativet visas för användaren:

  ![](assets/s_ncs_user_restrictions_operators.png)

  >[!IMPORTANT]
  >
  >Detta är en mycket noggrann restriktion som måste användas med försiktighet. En operator som är inloggad med den här typen av rättigheter kan BARA se innehållet i den angivna mappen och har inte åtkomst till någon annan nod i trädet via Utforskaren. Beroende på vilka funktioner den här operatorn har åtkomst till (till exempel arbetsflöden) kan användaren visa data som vanligtvis lagras i noder som inte är tillgängliga.

### Kontrollera inställningar {#check-settings}

På fliken **[!UICONTROL Audit]** kan du visa information om operatorn. De olika flikarna läggs till automatiskt baserat på inställningarna som anges i operatorområdet.

Du kan komma åt:

* Listan över rättigheter för mappar som är länkade till operatorn.

  ![](assets/operator_folder_permissions.png)

  >[!NOTE]
  >
  >Mer information finns i [Hantering av mappåtkomst](#folder-access-management).

* Operatörens godkännandelogg.

  ![](assets/operator_profile_validations.png)

* Listan med diskussionsforum som de prenumererar på.
* Händelser i deras kalender.
* Listan över uppgifter som tilldelats dem.

## Standardoperatorer {#default-operators}

Adobe Campaign använder tekniska operatorer med profiler som konfigurerats som standard: Administratör (&#39;admin&#39;), Fakturering (&#39;billing&#39;), Övervakning, Webbprogramagent (&#39;webapp&#39;) osv. Vissa av dessa är beroende av vilka program och alternativ som är installerade på plattformen: till exempel operatorerna central och lokal bara visas om alternativet Distribuerad marknadsföring är installerat.

>[!IMPORTANT]
>
>Dessa tekniska operatorer meddelas som standard när informationsmeddelanden returneras av plattformen. Vi rekommenderar att du skickar ett e-postmeddelande till dem.
>
>För att webbprogrammen ska fungera på rätt sätt rekommenderar vi att du inte definierar specifika regionala inställningar för webbprogramsoperatorn.

Som standard har den tekniska operatorn&quot;webapp&quot; namngiven ADMINISTRATION-behörighet, vilket kan leda till säkerhetsrisker. Vi rekommenderar att du tar bort den här rättigheten för att åtgärda problemet. Så här gör du:

1. Klicka på **[!UICONTROL New]** i noden **[!UICONTROL Administration > Access management > Named rights]** för att skapa en högersida och ge den namnet WEBAPP.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   Namngivna rättigheter beskrivs i avsnittet [Namngivna rättigheter](#named-rights).

1. På noden **[!UICONTROL Administration > Access management > Operators]** väljer du webbprogramagentoperatorn (&#39;webapp&#39;).

   Välj fliken **[!UICONTROL Edit]**, klicka på fliken **[!UICONTROL Access rights]** och ta bort ADMINISTRATIONEN som är namngiven till höger från listan.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Klicka på **[!UICONTROL Add]** och välj WEBAPP-höger som du just har skapat. Spara sedan ändringarna.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Tilldela operatorn &#39;webapp&#39; behörighet att läsa och skriva data i de mappar som berör den här operatorn, som i första hand är mapparna &#39;Recipient&#39;.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   Rättighetsändringar för trädmappar beskrivs i avsnittet [Mappåtkomsthantering](#folder-access-management).

>[!NOTE]
>
>Mer information om säkerhetsriktlinjer finns i [Checklista för Adobe Campaign-säkerhetskonfiguration](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/security-privacy/get-started-security-privacy.html?lang=sv).
