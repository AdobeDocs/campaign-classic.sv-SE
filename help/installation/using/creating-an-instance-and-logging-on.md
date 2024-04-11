---
product: campaign
title: Skapa en instans och logga in
description: Skapa en instans och logga in
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---

# Skapa en instans och logga in{#creating-an-instance-and-logging-on}



Så här skapar du en ny instans och en Adobe Campaign-databas:

1. Skapa anslutningen.
1. Logga in för att skapa den relaterade instansen.
1. Skapa och konfigurera databasen.

>[!NOTE]
>
>Endast den **interna** identifieraren kan utföra dessa åtgärder. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

När Adobe Campaign-konsolen startas kommer du åt en inloggningssida.

Om du vill skapa en ny instans följer du stegen nedan:

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt anslutningskonfigurationsfönstret. Den här länken kan vara antingen **[!UICONTROL New...]** eller ett befintligt instansnamn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda `https://<machine>.<domain>.com` skriv-URL.

   >[!CAUTION]
   >
   >För anslutnings-URL:en använder du bara följande tecken: `[a-z]`, `[A-Z]`och `[0-9]` bindestreck (-) eller punkter.

1. Klicka **[!UICONTROL Ok]** för att bekräfta inställningarna: Nu kan du börja med processen för att skapa instanser.
1. I fönstret **[!UICONTROL Connection settings]** anger du den interna **inloggningen** och lösenordet för att ansluta till Adobe Campaign-programservern. När du är ansluten öppnar du guiden för att skapa instanser för att deklarera en ny instans
1. Ange instansnamnet **** i fältet **[!UICONTROL Name]**. Eftersom det här namnet används för att generera en konfigurationsfil **config-`<instance>`.xml** och används i kommandoradsparametrarna för att identifiera instansen, måste du välja ett kort namn utan specialtecken. Till exempel: **e-marknadsföring**.

   ![](assets/s_ncs_install_create_instance.png)

   Namnet på instansen som läggs till i domännamnet får inte överstiga 40 tecken. På så sätt kan du begränsa storleken på &quot;Meddelande-ID&quot;-rubriker och förhindra att meddelanden betraktas som skräppost, särskilt av verktyg som SpamAssassin.

1. I fälten **[!UICONTROL DNS masks]** anger du listan **över DNS-masker** som instansen ska kopplas till. Adobe Campaign-servern använder värdnamnet som visas i HTTP-begäranden för att avgöra vilken instans som ska nås.

   Värdnamnet finns mellan strängen **https://** och det första snedstrecket **/** serveradressen.

   Du kan definiera en lista med värden avgränsade med kommatecken.

   Den? och &#42; tecken kan användas som jokertecken för att ersätta ett eller flera tecken (DNS, port, etc.). Till exempel **kommer demovärdet&#42;** att fungera med &quot;https://demo&quot; som det kommer att göra med &quot;https://demo:8080&quot; och till och med &quot;https://demo2&quot;.

   Namn som används måste definieras i din DNS. Du kan också informera om korrespondensen mellan ett DNS-namn och en IP-adress i **filen c:/windows/system32/drivers/etc/hosts** i Windows och i **filen /etc/hosts** i Linux. Du måste därför ändra anslutningsinställningarna för att använda det här DNS-namnet för att kunna ansluta till den valda instansen.

   Servern måste identifieras med detta namn, särskilt för att ladda upp bilder i e-postmeddelanden.

   Dessutom måste servern kunna ansluta till sig själv med detta namn, och om möjligt med en loopback-adress - 127.0.0.1 -, särskilt för att tillåta att rapporter exporteras i PDF-format.

1. **[!UICONTROL Language]** I listrutan väljer du **instansspråk**: engelska (USA), engelska (Storbritannien), franska eller japanska.

   Skillnaderna mellan amerikansk engelska och brittisk engelska beskrivs i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Instansspråket kan inte ändras efter det här steget. Adobe Campaign-instanser är inte flerspråkiga: du kan inte växla mellan olika språk.

1. Klicka **[!UICONTROL Ok]** för att bekräfta instansdeklaration. Logga ut och sedan in igen för att deklarera databasen.

   >[!NOTE]
   >
   >Instansen kan skapas från kommandoraden. Mer information finns i [Kommandorader](../../installation/using/command-lines.md).
