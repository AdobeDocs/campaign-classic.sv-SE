---
product: campaign
title: Konfigurera Campaign SMS-kanal på en infrastruktur för mellanleverantörer
description: Lär dig hur du konfigurerar SMS-kanalen i Campaign för en infrastruktur med mellanleverantörer
feature: SMS
role: User, Developer, Admin
level: Experienced
exl-id: 6987cb5e-8821-4619-b0e4-f0fad3355bfb
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 8%

---

# Konfigurera SMS-kanal på en infrastruktur för mellanleverantörer {#setting-up-sms-channel}

Om du vill skicka till en mobiltelefon med mellanservrar behöver du:

1. En SMS-operator har skapats på Mid-servern som används för det externa SMS-kontot som har skapats på marknadsföringsservern.

1. Ett externt konto på marknadsföringsservern som anger kanalläge och leveranssätt.

1. Ett externt konto på Mid-servern, med information om koppling och meddelandetyp.

1. En leveransmall som refererar till det externa kontot för att effektivisera sändningsprocessen.

>[!NOTE]
>
> För SMS-leveranser bör typologin använda en specifik SMS-tillhörighet som skapats i **en** dedikerad programserverbehållare. [Läs mer](../../installation/using/configure-delivery-settings.md#managing-outbound-smtp-traffic-with-affinities)

## Skapa SMS-operatorn på Mid-servern {#create-sms-operator}

Om du vill starta konfigurationsprocessen måste du skapa en SMS-operator på Mid-servern specifikt för det externa kontot.

>[!IMPORTANT]
>
>Varje SMS-koppling kräver en unik SMS-operator.

1. Klicka på ikonen **[!UICONTROL New]** i noden **[!UICONTROL Administration]** > **[!UICONTROL Access management]** > **[!UICONTROL Operators node]** i trädet.

   ![](assets/sms_operator_mid_3.png)

1. Ange användarens **[!UICONTROL Identification parameters]**, inklusive inloggning, lösenord och namn. Inloggning och lösenord krävs för att operatorn ska kunna logga in på Adobe Campaign på ett säkert sätt.

   Observera att **[!UICONTROL Name (login)]** senare ska användas för att namnge ditt externa SMPP-konto på Mid-servern.

   ![](assets/sms_operator_mid_1.png)

1. Välj de behörigheter som tilldelats operatorn i området Operator access rights.

   Om du vill tilldela behörigheter till operatorn klickar du på knappen **[!UICONTROL Add]** som finns ovanför listan med rättigheter. Välj sedan **[!UICONTROL Operator group]** eller **[!UICONTROL Named rights]** i listan med tillgängliga grupper.

   ![](assets/sms_operator_mid_2.png)

1. Klicka på **[!UICONTROL Save]** för att slutföra skapandet av operatorn. Profilen finns nu med i listan över befintliga operatorer.

## Skapa ett externt SMS-konto på marknadsföringsservern {#create-accound-mkt}

Om du vill skicka ett SMS till en mobiltelefon med mellanservrar måste du först skapa ett externt SMS-konto på marknadsföringsservern.

1. Klicka på ikonen **[!UICONTROL New]** i noden **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i trädet.

   ![](assets/mid_external_account_2.png)

1. Ange **[!UICONTROL Label]** och **[!UICONTROL Internal name]**. Observera att det interna namnet ska användas senare för att namnge ditt SMPP-externa konto på Mid-servern.

1. Definiera kontotypen som **[!UICONTROL Routing]**, kanalen som **[!UICONTROL Mobile (SMS)]** och leveransläget som **[!UICONTROL Mid-sourcing]**.

   ![](assets/mid_external_account_1.png)

1. På fliken **[!UICONTROL Mid-Sourcing]** anger du anslutningsparametrarna för serveranslutning från mitten.

   Ange information om den [tidigare skapade SMS-kopplingen](#create-sms-operator) i fälten **[!UICONTROL Account]** och **[!UICONTROL Password]**.

   ![](assets/mid_external_account_7.png)

1. Bekräfta konfigurationen genom att klicka på **[!UICONTROL Test the connection]**.

1. Klicka på **[!UICONTROL Save]**.

## Skapa ett externt SMPP-konto på Mid-servern {#creating-smpp-mid}

>[!IMPORTANT]
>
>Om du använder samma konto och lösenord för flera externa SMS-konton kan det leda till konflikter och överlappning mellan kontona. Se sidan [SMS-felsökning](troubleshooting-sms.md#external-account-conflict).

När du har konfigurerat ditt externa SMS-konto på marknadsföringsservern är nästa steg att skapa ett externt SMPP-konto på Mid-servern.

Mer information om SMS-protokoll och inställningar finns på [sidan](sms-protocol.md).

Gör så här:

1. Klicka på ikonen **[!UICONTROL New]** i noden **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** i trädet.

1. Ange **[!UICONTROL Label]** och **[!UICONTROL Internal name]**.

   >[!WARNING]
   >
   >När du tilldelar en **[!UICONTROL Internal name]** måste du följa den angivna namnkonventionen:
   > </br>`SMS Operator Name_Internal Name of the Marketing SMS external account`

   ![](assets/mid_external_account_6.png)

1. Definiera kontotypen som **Routning**, kanalen som **Mobil (SMS)** och leveransläget som **Massleverans**.

   ![](assets/mid_external_account_3.png)

1. Markera rutan **[!UICONTROL Enabled]**.

1. Välj **[!UICONTROL Extended generic SMPP]** i listrutan **[!UICONTROL Connector]** på fliken **[!UICONTROL Mobile]**.

   ![](assets/mid_external_account_4.png)

1. Med alternativet **[!UICONTROL Enable verbose SMPP traces in the log file]** kan du dumpa all SMPP-trafik i loggfiler. Det här alternativet bör bara aktiveras för att felsöka anslutningen och jämföra med den trafik som leverantören ser.

1. Kontakta din SMS-tjänstleverantör som förklarar hur du fyller i de olika externa kontofälten på fliken **[!UICONTROL Connection settings]**.

   Kontakta sedan din leverantör, beroende på vilken som valts, som ger dig värdet att ange i fältet **[!UICONTROL SMSC implementation name]**.

   Du kan definiera antalet anslutningar till providern per underordnat MTA-objekt. Som standard är den inställd på 1.

1. Som standard uppfyller antalet tecken i ett SMS GSM-standarden.

   SMS-meddelanden som använder GSM-kodning kan innehålla högst 160 tecken eller 153 tecken per SMS för meddelanden som skickas i flera delar.

   >[!NOTE]
   >
   >Vissa tecken räknas som två (klammerparenteser, eurosymbolen osv.).
   >
   >En lista över tillgängliga GSM-tecken visas i [det här avsnittet](sms-set-up.md#about-character-transliteration).

   Du kan också godkänna teckentranskriberingen genom att markera motsvarande ruta.

   ![](assets/mid_external_account_5.png)

1. På fliken **[!UICONTROL Throughput and delays]** kan du ange maximal genomströmning för utgående meddelanden (&quot;MT&quot;, Mobile Terminated) i MT per sekund. Om du anger &quot;0&quot; i motsvarande fält är dataflödet obegränsat.

   Samtliga fältvärden som motsvarar varaktighet måste fyllas i som sekunder.

1. På fliken **[!UICONTROL Mapping of encodings]** kan du definiera kodningar.

   Mer information om detta finns i [det här avsnittet](sms-set-up.md#about-text-encodings).

1. Alternativet **[!UICONTROL Send full phone number]** är inaktiverat som standard på fliken **[!UICONTROL SMSC specificities]**. Aktivera det inte om du vill respektera SMPP-protokollet och bara överföra siffror till servern för SMS-providern (SMSC).

   Eftersom vissa leverantörer kräver att&quot;+&quot;-prefixet används, bör du kontakta din leverantör och föreslå att du aktiverar det här alternativet om det behövs.

   Med kryssrutan **[!UICONTROL Enable TLS over SMPP]** kan du kryptera SMPP-trafik. Se denna [sida](sms-protocol.md) för mer information om detta.

1. Om du konfigurerar en **[!UICONTROL Extended generic SMPP]**-anslutning kan du konfigurera automatiska svar.

   Mer information om detta finns i [det här avsnittet](sms-set-up.md#automatic-reply).

## Ändra leveransmallen {#changing-the-delivery-template}

Adobe Campaign erbjuder en mobil leveransmall som finns i noden **[!UICONTROL Resources > Templates > Delivery templates]**. Mer information finns i avsnittet [Om mallar](about-templates.md).

Om du vill skicka meddelanden via SMS-kanalen måste du skapa en mall som innehåller en referens till kanalkopplingen.

Om du vill behålla den inbyggda leveransmallen rekommenderar vi att du duplicerar den och sedan konfigurerar den.

I exemplet nedan genererar vi en mall som gör det lättare att leverera meddelanden via det SMPP-konto som skapats tidigare. Så här gör du:

1. Högerklicka på mallen **[!UICONTROL Send to mobiles]** i noden **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]** i trädet och välj **[!UICONTROL Duplicate]**.

   ![](assets/delivery_template_mid_1.png)

1. Ändra mallens etikett, till exempel **Skickat till mobiler (SMPP)**.

   ![](assets/delivery_template_mid_2.png)

1. Klicka på **[!UICONTROL Properties]**.

1. På fliken **[!UICONTROL General]** väljer du ett routningsläge som motsvarar det externa konto som du skapade i avsnittet [Skapa ett externt SMS-konto på marknadsföringsservern](#create-accound-mkt).

   ![](assets/delivery_template_mid_3.png)

1. Klicka på **[!UICONTROL Save]** för att skapa mallen.

   ![](assets/delivery_template_mid_4.png)

Du har nu ett externt konto och en leveransmall som gör att du kan leverera via SMS.

## Relaterade ämnen {#related-topics}

* [SMS-teckentranskribering](sms-set-up.md#about-character-transliteration)
* [Textkodning](sms-set-up.md#about-text-encodings)
* [Automatiskt svar](sms-set-up.md#automatic-reply)
