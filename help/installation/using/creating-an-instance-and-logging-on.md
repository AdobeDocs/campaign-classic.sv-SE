---
product: campaign
title: Skapa en instans och logga in
description: Skapa en instans och logga in
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: c38150aa8de90f314e1f2a43c6751d4db4059533
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 1%

---

# Skapa en instans och logga in{#creating-an-instance-and-logging-on}



Så här skapar du en ny instans och en Adobe Campaign-databas:

1. Skapa anslutningen.
1. Logga in för att skapa den relaterade instansen.
1. Skapa och konfigurera databasen.

>[!NOTE]
>
>Endast identifieraren **internal** kan utföra dessa åtgärder. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

När Adobe Campaign-konsolen startas kommer du åt en inloggningssida.

Så här skapar du en ny instans:

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration. Den här länken kan vara antingen **[!UICONTROL New...]** eller ett befintligt instansnamn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka på **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda URL-typen `https://<machine>.<domain>.com`.

   >[!CAUTION]
   >
   >Använd endast följande tecken för anslutnings-URL: `[a-z]`, `[A-Z]`, `[0-9]` och streck (-) eller fullständiga stopp.

1. Klicka på **[!UICONTROL Ok]** för att bekräfta inställningarna: du kan nu börja med att skapa instansen.
1. I fönstret **[!UICONTROL Connection settings]** anger du inloggningen **internal** och dess lösenord för att ansluta till Adobe Campaign-programservern. När du är ansluten får du tillgång till instansskaparassistenten för att deklarera en ny instans
1. Ange **[!UICONTROL Name]** instansnamnet **i fältet**. Eftersom det här namnet används för att generera konfigurationsfilen **config-`<instance>`.xml** och används i kommandoradsparametrarna för att identifiera instansen, måste du välja ett kort namn utan specialtecken. Till exempel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Namnet på instansen som läggs till i domännamnet får inte vara längre än 40 tecken. På så sätt kan du begränsa storleken på meddelandehuvuden och förhindra att meddelanden betraktas som skräppost, särskilt med verktyg som SpamAssassin.

1. I fälten **[!UICONTROL DNS masks]** anger du listan **med DNS-masker** som instansen ska kopplas till. Adobe Campaign-servern använder värdnamnet som visas i HTTP-begäranden för att avgöra vilken instans som ska nås.

   Värdnamnet finns mellan strängen **https://** och det första snedstrecket **/** i serveradressen.

   Du kan definiera en lista med värden avgränsade med kommatecken.

   Den? och &#42; tecken kan användas som jokertecken för att ersätta ett eller flera tecken (DNS, port, osv.). Värdet **demo&#42;** fungerar till exempel med&quot;https://demo&quot; på samma sätt som med&quot;https://demo:8080&quot; och till och med&quot;https://demo2&quot;.

   Namn som används måste definieras i din DNS. Du kan också informera om korrespondensen mellan ett DNS-namn och en IP-adress i filen **c:/windows/system32/drivers/etc/hosts** i Windows och i filen **/etc/hosts** i Linux. Du måste därför ändra anslutningsinställningarna för att kunna använda det här DNS-namnet för att ansluta till den valda instansen.

   Servern måste identifieras med det här namnet, särskilt för överföring av bilder i e-postmeddelanden.

   Dessutom måste servern kunna ansluta till sig själv med det här namnet, och om möjligt med en loopback-adress - 127.0.0.1 - särskilt för att rapporter ska kunna exporteras i PDF-format.

1. I listrutan **[!UICONTROL Language]** väljer du **instansspråk**: engelska (USA), engelska (Storbritannien), franska eller japanska.

   Skillnader mellan amerikansk engelska och brittisk engelska beskrivs i [Campaign v8-dokumentationen (konsol)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/new/campaign-ui).

   >[!CAUTION]
   >
   >Instansspråket kan inte ändras efter det här steget. Adobe Campaign-instanser är inte flerspråkiga: du kan inte växla mellan olika språk.

1. Klicka på **[!UICONTROL Ok]** för att bekräfta instansdeklarationen. Logga ut och sedan in igen för att deklarera databasen.

   >[!NOTE]
   >
   >Instansen kan skapas från kommandoraden. Mer information finns i [Kommandorader](../../installation/using/command-lines.md).
