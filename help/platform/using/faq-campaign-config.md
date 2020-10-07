---
title: Vanliga frågor och svar om inställningar i Campaign
seo-title: Så konfigurerar du Campaign
description: Vanliga frågor och svar om Campaign Classic
page-status-flag: never-activated
uuid: 3f719ac2-cc26-4fb0-adda-84666c8c38e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 16dbe423-018f-4666-9901-2120a8dc609a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 100%

---


# Vanliga frågor och svar om inställningar i Campaign {#settings-faq}

Lär dig viktiga konfigurationer för att ställa in instansen i Campaign så att den passar dina behov.

## Kan jag ändra språket på gränssnittet i Campaign? {#can-i-change-the-language-of-campaign-interface-}

Språket i Campaign väljs när instansen skapas. Du kan inte ändra det i efterhand. Mer information om detta finns i [det här avsnittet](../../installation/using/creating-an-instance-and-logging-on.md).

Användargränssnittet i Adobe Campaign finns på fyra språk: engelska, franska, tyska och japanska. Observera att klientkonsolen och servern måste vara inställda på samma språk. Varje instans i Campaign kan bara köras på ett språk.

För engelska kan du välja antingen amerikansk engelska eller brittisk engelska när du installerar Campaign. De skiljer sig åt när det gäller datum- och tidsformat. Mer information om dessa skillnader finns i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#date-and-time).

## Kan jag använda Campaign Classic tillsammans med andra Adobe-lösningar? {#can-i-use-campaign-classic-with-other-adobe-solutions-}

Du kan kombinera leveransfunktionerna och de avancerade funktionerna för kampanjhantering i Adobe Campaign med en uppsättning lösningar som hjälper till att personalisera användarnas upplevelse.

Klicka här för att läsa mer om [hur man arbetar med andra Adobe-lösningar](../../integrations/using/about-campaign-integrations.md) och [hur man konfigurerar IMS i Campaign](../../integrations/using/about-adobe-id.md).

## Hur ställer jag in spårningsfunktioner för min instans i Campaign? {#how-can-i-set-up-tracking-capabilities-on-my-campaign-instance-}

Som expertanvändare kan du konfigurera spårningsfunktioner via instansen i Campaign.

[Klicka här för att läsa mer](../../installation/using/deploying-an-instance.md#tracking-configuration).

## Hur konfigurerar man e-postmeddelandets levererbarhet? {#how-to-configure-email-deliverability-}

Förutom avsnittet [Konfiguration av levererbarhet](../../delivery/using/about-deliverability.md#configuration) kan du läsa de tekniska rekommendationerna för leveranser för att förstå hur du konfigurerar instansen för att maximera levererbarheten i Campaign.

[Klicka här för att läsa mer](../../delivery/using/technical-recommendations.md).

## Hur kan jag implementera innehållsgodkännande? {#how-can-i-implement-content-approval-}

Med Campaign kan du skapa godkännandeprocesser för de viktigaste stegen i marknadsföringskampanjen i samarbetsläge. För varje kampanj kan du godkänna leveransmålet, innehållet och kostnaderna. Operatörer som ansvarar för godkännande i Adobe Campaign kan meddelas via e-post och kan godkänna eller ej från konsolen eller via en webbanslutning.

[Klicka här för att läsa mer](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries) och se hur du implementerar ditt godkännande av leveransinnehåll i Campaign.

## Hur får jag åtkomst till data som lagras i en extern databas? {#how-can-i-access-data-stored-in-an-external-database-}

Adobe Campaign tillhandahåller alternativet federerad dataåtkomst (FDA) för att bearbeta information som lagras i en eller flera externa databaser. Du kan få åtkomst till externa data utan att ändra datastrukturen i Adobe Campaign.

[Klicka här för att läsa mer](../../platform/using/connecting-to-database.md).

## Vilka externa databaser kan jag ansluta Campaign till? {#which-external-databases-can-i-connect-campaign-to-}

Externa databaser som är kompatibla med Campaign via federerad dataåtkomst (FDA) listas i [kompatibilitetsmatrisen](https://helpx.adobe.com/se/campaign/kb/compatibility-matrix.html).

## Kan Adobe Campaign integreras med LDAP? {#can-adobe-campaign-integrate-with-ldap-}

Som lokal/hybrid-kund kan du integrera Campaign Classic med LDAP-katalogen.

[Klicka här för att läsa mer](../../installation/using/connecting-through-ldap.md).

## Hur konfigurerar jag CRM-kopplingar i Campaign? {#how-can-i-set-up-crm-connectors-in-campaign-}

Adobe Campaign tillhandahåller olika CRM-kopplingar för att länka din plattform i Adobe Campaign till dina tredjepartssystem. Med dessa CRM-kopplingar kan du synkronisera kontakter, konton och inköp osv. De låter dig enkelt integrera din applikation med olika tredjeparts- och företagsapplikationer.

Dessa kopplingar möjliggör snabb och enkel dataintegrering. Adobe Campaign erbjuder en dedikerad guide för att samla in och välja bland tabellerna i CRM. Detta garanterar dubbelriktad synkronisering för att säkerställa att data alltid är aktuella i alla system.

Läs mer i [Konfigurera CRM-kopplingar](../../platform/using/crm-connectors.md) för att veta hur du synkroniserar CRM-verktyget med Adobe Campaign. Titta på den här videon med användningsfall om [integrering mellan Adobe Campaign och Microsoft Dynamics 365](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html).

## Hur utför jag en rensning av mjukt cacheminne när problemen är dator- eller användarspecifika? {#perform-soft-cache-clear}

Om du har problem med till exempel att de nya logotyperna återspeglas korrekt och att kunna exportera data som är datorspecifika/användarspecifika kan du behöva utföra en rensning av mjukt cacheminne med Windows (Windows 7, Windows XP och Windows 10).

Logga ut och gå till **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]**. Logga sedan ut och in igen.

![](assets/faq_soft_cache.png)

Om detta fortfarande inte hjälper kan du försöka utföra en rensning av hårt cacheminne genom att utföra stegen nedan.

## Hur utför jag en rensning av hårt cacheminne när problemen är dator- eller användarspecifika? {#perform-hard-cache-clear}

Om du har problem med till exempel att de nya logotyperna återspeglas korrekt och att kunna exportera data som är datorspecifika/användarspecifika kan du behöva utföra en rensning av hårt cacheminne med Windows (Windows 7, Windows XP och Windows 10).

1. Välj **[!UICONTROL File]** > **[!UICONTROL Clear the local cache]** på klientkonsolen.

1. Logga ut och stäng klientkonsolen (rich client).

1. Gå till följande platser beroende på version av operativsystemet:

   * Windows 7: C:\Users\&lt; Användarnamn >\AppData\Roaming\Neolane\NL_5\
   * Windows XP: C:\Documents and Settings\&lt; Användarnamn >\Application Data\Neolane\NL_5

   Här ser du många xml-filer med namnet nlclient-config-&lt; alfanumeriskt värde >.xml.

1. Radera dessa xml-filer och associerade mappar.

   >[!IMPORTANT]
   >
   >Radera inte filen nlclient_cnx.xml.

1. Logga in på klientkonsolen.