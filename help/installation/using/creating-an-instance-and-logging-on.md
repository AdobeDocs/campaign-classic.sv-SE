---
title: Skapa en instans och logga in
seo-title: Skapa en instans och logga in
description: Skapa en instans och logga in
seo-description: null
page-status-flag: never-activated
uuid: cb1620b3-f6e8-41dc-9142-ac0da65b6f8d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: c7395094-c635-45ab-8455-a050f7d16b64
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# Skapa en instans och logga in{#creating-an-instance-and-logging-on}

Gör så här om du vill skapa en ny instans och Adobe Campaign-databasen:

1. Skapa anslutningen.
1. Logga in för att skapa den relaterade instansen.
1. Skapa och konfigurera databasen.

>[!NOTE]
>
>Det är bara den **interna** identifieraren som kan utföra dessa åtgärder. Mer information finns i [Intern identifierare](../../installation/using/campaign-server-configuration.md#internal-identifier).

När Adobe Campaign-konsolen startas kommer du åt en inloggningssida.

Så här skapar du en ny instans:

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration. Länken kan vara antingen **[!UICONTROL New...]** eller ett befintligt instansnamn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda [`https://<machine>.<domain>.com`](https://machine) typen URL.

   >[!CAUTION]
   >
   >Använd endast följande tecken för anslutnings-URL: `[a-z]`, `[A-Z]``[0-9]` och streck (-) eller fullständiga stopp.

1. Bekräfta inställningarna genom **[!UICONTROL Ok]** att klicka: du kan nu börja med att skapa en instans.
1. I **[!UICONTROL Connection settings]** fönstret anger du den **interna** inloggningen och lösenordet för att ansluta till Adobe Campaign-programservern. När du är ansluten öppnar du guiden Skapa instans för att deklarera en ny instans
1. Ange **[!UICONTROL Name]** instansnamnet **i** fältet. Eftersom det här namnet används för att generera en konfigurationsfil **config-`<instance>`.xml** och används i kommandoradsparametrarna för att identifiera instansen, måste du välja ett kort namn utan specialtecken. Till exempel: e **Marketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Namnet på instansen som läggs till i domännamnet får inte vara längre än 40 tecken. På så sätt kan du begränsa storleken på meddelandehuvuden och förhindra att meddelanden betraktas som skräppost, särskilt med verktyg som SpamAssassin.

1. I **[!UICONTROL DNS masks]** fälten anger du **listan med DNS-masker** som instansen ska kopplas till. Adobe Campaign-servern använder värdnamnet som visas i HTTP-begäranden för att avgöra vilken instans som ska nås.

   Värdnamnet finns mellan strängen **https://** och det första snedstrecket **/** i serveradressen.

   Du kan definiera en lista med värden avgränsade med kommatecken.

   Med och * kan användas som jokertecken för att ersätta ett eller flera olika tecken (DNS, port, osv.). Värdet för **demo*** fungerar till exempel med&quot;https://demo&quot; på samma sätt som med&quot;https://demo:8080&quot; och till och med&quot;https://demo2&quot;.

   Namn som används måste definieras i din DNS. Du kan också informera om kommunikationen mellan ett DNS-namn och en IP-adress i **filen c:/windows/system32/drivers/etc/hosts** i Windows och i filen **/etc/hosts** i Linux. Du måste därför ändra anslutningsinställningarna för att kunna använda det här DNS-namnet för att ansluta till den valda instansen.

   Servern måste identifieras med det här namnet, särskilt för överföring av bilder i e-postmeddelanden.

   Dessutom måste servern kunna ansluta till sig själv med det här namnet, och om möjligt med en loopback-adress - 127.0.0.1 - särskilt för att rapporter ska kunna exporteras i PDF-format.

1. I den **[!UICONTROL Language]** nedrullningsbara listan väljer du **instansspråk**: Engelska (USA), engelska (Storbritannien), franska eller japanska.

   Skillnaderna mellan amerikansk engelska och brittisk engelska beskrivs i [detta avsnitt](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Instansspråket kan inte ändras efter det här steget. Adobe Campaign-instanser är inte flerspråkiga: Du kan inte växla mellan olika språk i gränssnittet.

1. Klicka **[!UICONTROL Ok]** för att bekräfta instansdeklarationen. Logga ut och sedan in igen för att deklarera databasen.

   >[!NOTE]
   >
   >Instansen kan skapas från kommandoraden. Mer information finns i [Kommandorader](../../installation/using/command-lines.md).

