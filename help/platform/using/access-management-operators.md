---
solution: Campaign Classic
product: campaign
title: Kom igång med Campaign-operatorer
description: Lär dig hur du skapar och hanterar kampanjanvändare
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 2%

---


# Skapa och hantera operatorer {#operators}

## Kom igång med Campaign-operatorer {#about-operators}

En operator är en Adobe Campaign-användare som har behörighet att logga in och utföra åtgärder.

Som standard lagras operatorer i noden **[!UICONTROL Administration > Access management > Operators]**.

![](assets/s_ncs_user_list_operators.png)

Operatorer kan skapas manuellt eller mappas på en befintlig LDAP-katalog.

En fullständig procedur för att skapa en operator beskrivs i [den här sidan](#creating-an-operator).

Mer information om integrering av Adobe Campaign och LDAP finns på [den här sidan](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>Operatorer måste länkas till en säkerhetszon för att kunna logga in på en instans. Mer information om säkerhetszoner i Adobe Campaign finns på [den här sidan](../../installation/using/security-zones.md).

Användare kan även ansluta direkt till Adobe Campaign via sin Adobe ID. Se denna [sida](../../integrations/using/about-adobe-id.md) för mer information om detta.

## Skapa en operator {#creating-an-operator}

Så här skapar du en ny operator och tilldelar behörigheter:

1. Klicka på knappen **[!UICONTROL New]** ovanför listan med operatorer och ange information om operatorn new.

   ![](assets/s_ncs_user_operator_new.png)

1. Ange **[!UICONTROL Identification parameters]** för användaren: användar-ID, lösenord och namn. Inloggningen och lösenordet används av operatören för att logga in på Adobe Campaign. När användaren är inloggad kan han/hon ändra sitt lösenord via **[!UICONTROL Tools > Change password]**-menyn. Operatorns e-postadress är viktig eftersom den gör det möjligt för operatorn att ta emot meddelanden, till exempel när godkännanden behandlas.

   I det här avsnittet kan du även länka en operator till en organisationsenhet. Mer information finns på [den här sidan](../../campaign/using/about-distributed-marketing.md).

1. Välj behörigheter för operatorn i avsnittet **[!UICONTROL Operator access rights]**.

   Om du vill tilldela behörigheter till operatorn klickar du på knappen **[!UICONTROL Add]** ovanför listan över rättigheter och väljer sedan en grupp med operatorer i listan över tillgängliga grupper:

   ![](assets/s_ncs_user_permissions_operators.png)

   Du kan också välja en eller flera namngivna rättigheter (se [Namngivna rättigheter](#named-rights)). Det gör du genom att klicka på pilen till höger om fältet **[!UICONTROL Folder]** och välja **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   Markera grupper och/eller namngivna rättigheter som ska tilldelas och klicka på **[!UICONTROL OK]** för att validera.

1. Klicka på **[!UICONTROL Ok]** för att skapa operatorn: profilen läggs till i listan över befintliga operatorer.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>Du kan ordna operatorerna efter dina behov genom att skapa nya operatormappar. Om du vill göra det högerklickar du på operatormappen och väljer **[!UICONTROL Add an 'Operators' folder]**.

När operatörens profil har skapats kan du lägga till eller uppdatera informationen för den. Det gör du genom att klicka på fliken **[!UICONTROL Edit]**.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>I fältet **[!UICONTROL Session timeout]** kan du justera fördröjningen före FDA-sessionens timeout. Mer information om detta finns i [Om dataåtkomst med federerade data](../../installation/using/about-fda.md).

## Definiera operatorns tidszon {#time-zone-of-the-operator}

På fliken **[!UICONTROL General]** kan du välja operatörens tidszon. Som standard arbetar operatorer i serverns tidszon. Det går dock att välja en annan tidszon i listrutan.

Konfigurationen av tidszoner beskrivs i [den här sidan](../../installation/using/time-zone-management.md).

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

* Med alternativet **[!UICONTROL Disable account]** kan du inaktivera operatörens konto: Han kommer inte längre att ha tillgång till Adobe Campaign.

   >[!NOTE]
   >
   >Även om det här kontot är inaktiverat kan operatorn fortfarande få aviseringar eller meddelanden från Campaign. Om du inte längre vill skicka Campaign-meddelanden till den här operatorn rekommenderar Adobe att du tar bort e-postadressen från den här profilen.

* Med alternativet **[!UICONTROL Forbid access from the rich client]** kan du begränsa användningen av Adobe Campaign till [webbåtkomst](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) eller via API:er: åtkomst till Adobe Campaign klientkonsol inte längre är tillgänglig.
* Det går att länka en säkerhetszon till operatören. Se denna [sida](../../installation/using/security-zones.md) för mer information om detta.
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
   >Detta är en mycket noggrann restriktion som måste användas med försiktighet. En operator som är inloggad med den här typen av rättigheter kan BARA se innehållet i den angivna mappen och har inte åtkomst till någon annan nod i trädet via Utforskaren. Beroende på vilka funktioner han har tillgång till (t.ex.: arbetsflöden) kan han visa data som vanligtvis lagras i noder som han inte kan se.

### Kontrollera inställningar {#check-settings}

På fliken **[!UICONTROL Audit]** kan du visa information om operatorn. De olika flikarna läggs till automatiskt baserat på inställningarna som anges i operatorområdet.

Du kan komma åt:

* Listan över rättigheter för mappar som är länkade till operatorn.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >Mer information finns i [Mappåtkomsthantering](#folder-access-management).

* Operatörens godkännandelogg.

   ![](assets/operator_profile_validations.png)

* Listan med diskussionsforum som de prenumererar på.
* Händelser i deras kalender.
* Listan över uppgifter som tilldelats dem.

## Standardoperatorer {#default-operators}

Adobe Campaign använder tekniska operatorer med profiler som är konfigurerade som standard: Administratör (&#39;admin&#39;), fakturering (&#39;billing&#39;), övervakning, webbprogramagent (&#39;webapp&#39;) osv. Vissa av dessa beror på vilka program och alternativ som är installerade på plattformen: Operatorer av typen central och lokal är till exempel bara synliga om alternativet Distribuerad marknadsföring är installerat.

>[!IMPORTANT]
>
>Dessa tekniska operatorer meddelas som standard när informationsmeddelanden returneras av plattformen. Vi rekommenderar att du skickar ett e-postmeddelande till dem.
>
>För att webbprogrammen ska fungera på rätt sätt rekommenderar vi att du inte definierar specifika regionala inställningar för webbprogramsoperatorn.

Som standard har den tekniska operatorn&quot;webapp&quot; namngiven ADMINISTRATION-behörighet, vilket kan leda till säkerhetsrisker. För att åtgärda det här problemet rekommenderar vi att du tar bort den här rättigheten. Så här gör du:

1. Klicka på **[!UICONTROL New]** i noden **[!UICONTROL Administration > Access management > Named rights]** för att skapa en rättighet och ge den namnet WEBAPP.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   Namngivna rättigheter beskrivs i avsnittet [Namngivna rättigheter](#named-rights).

1. I noden **[!UICONTROL Administration > Access management > Operators]** väljer du webbprogramagentens operator (&#39;webapp&#39;).

   Välj fliken **[!UICONTROL Edit]**, klicka på fliken **[!UICONTROL Access rights]** och ta bort den ADMINISTRATION som är namngiven direkt från listan.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   Klicka på **[!UICONTROL Add]** och välj WEBAPP till höger som du just har skapat. Spara sedan ändringarna.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. Tilldela operatorn &#39;webapp&#39; behörighet att läsa och skriva data i de mappar som berör den här operatorn, som i första hand är mapparna &#39;Recipient&#39;.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   Rättighetsändringar för trädmappar beskrivs i [Mappåtkomsthantering](#folder-access-management)-avsnittet.

>[!NOTE]
>
>Mer information om säkerhetsriktlinjer finns i [checklistan för Adobe Campaign-säkerhetskonfiguration](https://helpx.adobe.com/se/campaign/kb/acc-security.html).
