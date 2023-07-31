---
product: campaign
title: Skapa en instans och logga in
description: Skapa en instans och logga in
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Gäller endast Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a025026e-688e-4ec1-abc4-40ee040d2b3b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 5%

---

# Skapa en instans och logga in{#creating-an-instance-and-logging-on}



Så här skapar du en ny instans och en Adobe Campaign-databas:

1. Skapa anslutningen.
1. Logga in för att skapa den relaterade instansen.
1. Skapa och konfigurera databasen.

>[!NOTE]
>
>Endast **internal** identifieraren kan utföra dessa åtgärder. Mer information om detta finns i [det här avsnittet](../../installation/using/configuring-campaign-server.md#internal-identifier).

När Adobe Campaign-konsolen startas kommer du åt en inloggningssida.

Så här skapar du en ny instans:

1. Klicka på länken i det övre högra hörnet av inloggningsfälten för att komma åt fönstret för anslutningskonfiguration. Den här länken kan vara antingen **[!UICONTROL New...]** eller ett befintligt instansnamn.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Klicka **[!UICONTROL Add > Connection]** och ange etiketten och URL:en för Adobe Campaign-programservern.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Ange en anslutning till Adobe Campaign-programservern via en URL. Använd antingen en DNS eller ett alias för datorn eller din IP-adress.

   Du kan till exempel använda `https://<machine>.<domain>.com` skriv-URL.

   >[!CAUTION]
   >
   >Använd endast följande tecken för anslutnings-URL: `[a-z]`, `[A-Z]`, `[0-9]` och streck (-) eller fullständiga stopp.

1. Klicka **[!UICONTROL Ok]** för att bekräfta inställningar: du kan nu börja med att skapa en instans.
1. I **[!UICONTROL Connection settings]** -fönstret, ange **internal** inloggning och lösenord för att ansluta till Adobe Campaign programserver. När du är ansluten öppnar du guiden Skapa instans för att deklarera en ny instans
1. I **[!UICONTROL Name]** fält, ange **instansnamn**. Detta namn används för att generera en konfigurationsfil **config-`<instance>`XML** och används i kommandoradsparametrarna för att identifiera instansen, måste du välja ett kort namn utan specialtecken. Till exempel: **eMarketing**.

   ![](assets/s_ncs_install_create_instance.png)

   Namnet på instansen som läggs till i domännamnet får inte vara längre än 40 tecken. På så sätt kan du begränsa storleken på meddelandehuvuden och förhindra att meddelanden betraktas som skräppost, särskilt med verktyg som SpamAssassin.

1. I **[!UICONTROL DNS masks]** fält, ange **lista med DNS-masker** som instansen ska kopplas till. Adobe Campaign-servern använder värdnamnet som visas i HTTP-begäranden för att avgöra vilken instans som ska nås.

   Värdnamnet finns mellan strängen **https://** och det första snedstrecket **/** serveradressen.

   Du kan definiera en lista med värden avgränsade med kommatecken.

   Den? och &#42; kan användas som jokertecken för att ersätta ett eller flera olika tecken (DNS, port, osv.). Till exempel **demo&#42;** fungerar med&quot;https://demo&quot; på samma sätt som med&quot;https://demo:8080&quot; och till och med&quot;https://demo2&quot;.

   Namn som används måste definieras i din DNS. Du kan också informera om kommunikationen mellan ett DNS-namn och en IP-adress i **c:/windows/system32/drivers/etc/hosts** i Windows och i **/etc/värdar** i Linux. Du måste därför ändra anslutningsinställningarna för att kunna använda det här DNS-namnet för att ansluta till den valda instansen.

   Servern måste identifieras med det här namnet, särskilt för överföring av bilder i e-postmeddelanden.

   Dessutom måste servern kunna ansluta till sig själv med det här namnet, och om möjligt med en loopback-adress - 127.0.0.1 - särskilt för att rapporter ska kunna exporteras i PDF-format.

1. I **[!UICONTROL Language]** väljer du **instansspråk**: Engelska (USA), engelska (Storbritannien), franska eller japanska.

   Skillnaderna mellan amerikansk engelska och brittisk engelska beskrivs i [det här avsnittet](../../platform/using/adobe-campaign-workspace.md#date-and-time).

   >[!CAUTION]
   >
   >Instansspråket kan inte ändras efter det här steget. Adobe Campaign-instanser är inte flerspråkiga: du kan inte växla mellan olika språk.

1. Klicka **[!UICONTROL Ok]** för att bekräfta instansdeklaration. Logga ut och sedan in igen för att deklarera databasen.

   >[!NOTE]
   >
   >Instansen kan skapas från kommandoraden. Mer information finns i [Kommandorader](../../installation/using/command-lines.md).
