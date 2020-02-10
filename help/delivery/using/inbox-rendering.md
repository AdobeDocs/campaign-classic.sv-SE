---
title: Inkorgsåtergivning
seo-title: Inkorgsåtergivning
description: Inkorgsåtergivning
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 30f313cecf1c3d7c65f6524a3f86a1c28b35f679

---


# Inkorgsåtergivning{#inbox-rendering}

## Om inkorgsåtergivning {#about-inbox-rendering}

Innan du klickar på knappen **Skicka** måste du se till att ditt meddelande visas för mottagarna på ett optimalt sätt på olika webbklienter, webbmejl och enheter.

Adobe Campaign utnyttjar den webbaserade e-posttestningslösningen [Litmus](https://litmus.com/email-testing) för att hämta in återgivningarna och göra dem tillgängliga i en dedikerad rapport. På så sätt kan du förhandsgranska det skickade meddelandet i olika sammanhang som det kan tas emot i och kontrollera kompatibiliteten i de flesta datorer och program.

Litmus är en funktionell e-postvalidering och förhandsgranskning av program. Med den kan e-postinnehållsförfattare förhandsgranska sitt meddelandeinnehåll i över 70 e-postrenderare, till exempel Gmail-inkorgen eller Apple Mail-klienten.

De mobil-, meddelande- och webbpostklienter som är tillgängliga för **inkorgsåtergivning** i Adobe Campaign finns listade på [Litmus-webbplatsen](https://litmus.com/email-testing) (klicka på **Visa alla e-postklienter**).

>[!NOTE]
>
>Återgivning av inkorgen behövs inte för att testa personalisering i leveranser. Personaliseringen kan kontrolleras med Adobe Campaign-verktyg som **[!UICONTROL Preview]** och [korrektur](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Aktivera inkorgsåtergivning{#activating-inbox-rendering}

För värdbaserade klienter och hybridklienter konfigureras Inkorgsåtergivning av Adobes tekniska support och konsulter. Kontakta er kontoansvarige på Adobe om du vill ha mer information.

För lokala installationer följer du stegen nedan för att konfigurera inkorgsåtergivning.

1. Installera paketet **[!UICONTROL Inbox rendering (IR)]** via **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** . Mer information finns i [Installera standardpaket](../../installation/using/installing-campaign-standard-packages.md)för Campaign Classic.
1. Konfigurera ett externt konto för HTTP-typen via **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** -noden. Mer information finns i [Skapa ett externt konto](../../platform/using/external-accounts.md#creating-an-external-account).
1. Ange externa kontoparametrar enligt följande:
   * **[!UICONTROL Label]**: Information om leveransserver
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**:HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Ingen
   * Markera **[!UICONTROL Enabled]** alternativet.
   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Gå till **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** -noden. Sök efter **[!UICONTROL DmRendering_cuid]** alternativet och kontakta supporten för att få den leveransrapportidentifierare som behöver kopieras till **[!UICONTROL Value (text)]** fältet.
1. Redigera filen **serverConf.xml** så att den tillåter anrop till Litmus-servern. Lägg till följande rad i `<urlPermission>` avsnittet:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Läs in konfigurationen igen med följande kommando:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Du kan behöva logga ut från konsolen och logga in igen för att kunna använda Inkorgsåtergivning.

## Om Litmus-tokens {#about-litmus-tokens}

Eftersom Litmus är en tredjepartstjänst fungerar den på en kreditmodell per användning. Varje gång en användare anropar Litmus-funktionen dras krediten av.

I Adobe Campaign motsvarar krediten antalet tillgängliga återgivningar (kallas tokens).

>[!NOTE]
>
>Antalet tillgängliga Litmus-tokens beror på vilken Campaign-licens du har köpt. Kontrollera licensavtalet.

Varje gång du använder **[!UICONTROL Inbox rendering]** funktionen i en leverans minskar varje återgivning dina tillgängliga tokens med ett.

>[!IMPORTANT]
>
>Tokens-konto för varje enskild återgivning och inte för hela inkorgsåtergivningsrapporten, vilket innebär att:
>
>* Varje gång rapporten för inkorgsåtergivning skapas dras en token per meddelandeklient av: en token för Outlook 2000-återgivning, en för Outlook 2010-återgivningen, en för Apple Mail 9-återgivningen och så vidare.
>* Om du genererar återgivningen av Inkorgen igen för samma leverans minskas antalet tillgängliga tokens igen med antalet genererade återgivningar.
>



Antalet återstående tillgängliga token visas i **[!UICONTROL General summary]** rapporten för [inkorgsåtergivning](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

Återgivningsfunktionen i Inkorgen används vanligtvis för att testa HTML-ramverket i ett nyligen utformat e-postmeddelande. Varje återgivning kräver ungefär 70 token (beroende på hur många miljöer som testas i allmänhet). I vissa fall kan du dock behöva flera rapporter om inkorgsåtergivning för att kunna testa leveransen. Det kan därför ta fler tokens att slutföra flera kontroller.

>[!NOTE]
>
>Om du är en Litmus-klient kan du använda ditt eget Litmus-konto för att etablera och använda Inkorgsåtergivning i Adobe Campaign. Kontakta er kontoansvarige på Adobe om du vill veta mer.
>
>Observera att om du ändrar din Litmus-inloggningsinformation kan det orsaka autentiseringsproblem i Adobe Campaign.

## Få åtkomst till rapporten för inkorgsåtergivning {#accessing-the-inbox-rendering-report}

När du har skapat e-postleveransen och definierat innehållet samt målpopulationen följer du stegen nedan.

Mer information om hur du skapar, utformar och anger mål för en leverans finns i [det här avsnittet](../../delivery/using/about-email-channel.md).

1. Klicka på **[!UICONTROL Inbox rendering]** knappen längst upp i leveransfältet.
1. Välj **[!UICONTROL Analyze]** att starta hämtningsprocessen.

   ![](assets/s_tn_inbox_rendering_button.png)

   Ett bevis skickas. Miniatyrbilderna för återgivning finns tillgängliga i det korrekturet några minuter efter att du skickat e-postmeddelandena. Mer information om hur du skickar korrektur finns i [det här avsnittet](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. När du har skickat korrekturet visas det i leveranslistan. Dubbelklicka på den.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Gå till fliken **Inkorgsåtergivning** i korrekturet.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Återgivningsrapporten för inkorgen visas.

## Återgivningsrapport för inkorgen {#inbox-rendering-report}

I den här rapporten visas inkorgsåtergivningarna så som de visas för mottagaren. Återgivningarna kan variera beroende på hur mottagaren öppnar e-postleveransen: i en webbläsare, på en mobil enhet eller via ett e-postprogram.

Här **[!UICONTROL General summary]** visas antalet mottagna, oönskade (skräppost), ej mottagna eller väntande mottagningar som en lista och med en grafisk färgkodad representation.

![](assets/s_tn_inbox_rendering_summary.png)

Håll pekaren över diagrammet om du vill visa information om varje färg.

Rapportens innehåll är uppdelat i tre delar: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** och **[!UICONTROL Webmails]**. Bläddra nedåt i rapporten för att visa alla återgivningar grupperade i dessa tre kategorier.

![](assets/s_tn_inbox_rendering_report.png)

Klicka på motsvarande kort om du vill ha information om respektive rapport. Återgivningen visas för den valda mottagningsmetoden.

![](assets/s_tn_inbox_rendering_example.png)
