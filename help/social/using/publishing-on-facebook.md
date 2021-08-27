---
product: campaign
title: Publicera på Facebook
description: Publicera på Facebook
audience: social
content-type: reference
topic-tags: publishing-on-facebook-twitter
exl-id: 84d6cb2e-c7f9-43d7-a98c-22613d456193
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 3%

---

# Publicera på Facebook{#publishing-on-facebook}

![](../../assets/v7-only.svg)

När konfigurationen är klar kan du med Social Marketing publicera publikationer på Facebook-sidans väggar.

## Begränsningar {#limitations}

Facebook har följande begränsningar:

* Meddelanden får inte innehålla fler än 1 000 tecken.
* HTML stöds inte.

## Skapa leveransen {#creating-the-delivery}

Skapa en ny leverans med leveransmallen **[!UICONTROL Publish to a brand page]**.

![](assets/social_facebook_delivery_001.png)

## Välja huvudmål {#selecting-the-main-target}

Du måste markera de sidor du vill publicera publikationen på.

1. Klicka på länken **[!UICONTROL To]**.

   ![](assets/social_facebook_delivery_010.png)

1. Klicka på knappen **[!UICONTROL Add]**.

   ![](assets/social_facebook_delivery_011.png)

1. Välj **[!UICONTROL A Facebook page]**.

   ![](assets/social_facebook_delivery_012.png)

1. I fältet **[!UICONTROL Folder]** väljer du den tjänstmapp som innehåller Facebook-sidan. Som standard lagras sidorna i roten för **[!UICONTROL Facebook]**-tjänstmappen. Markera sedan den Facebook-sida som du vill publicera på.

   ![](assets/social_facebook_delivery_013.png)

## Välja korrekturmål {#selecting-the-proof-target}

På fliken **[!UICONTROL Target of the proofs]** kan du definiera den Facebook-sida som du vill använda för att testa leveranser innan du skickar ut dem. Vi rekommenderar att du skapar en dedikerad privat Facebook-sida för detta ändamål. Mer information om hur du skapar en privat Facebook-sida finns i [Skapa en test-Facebook-sida](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Om du vill välja korrekturmålet ska du utföra samma steg som för huvudmålet: [Markera huvudmålet](#selecting-the-main-target).

![](assets/social_facebook_delivery_004.png)

>[!NOTE]
>
>Om du använder samma Facebook-testsida för alla leveranser kan du spara korrekturmålet i leveransmallen **[!UICONTROL Publish to a brand page]**, som nås via noden **[!UICONTROL Resources > Templates > Delivery templates]**. Korrekturmålet anges som standard för varje ny leverans.

## Definiera målgruppen {#defining-the-audience}

Om du vill använda lokala segment för att förfina den typ av publik som har behörighet att visa publikationen rekommenderar vi att du skapar en Facebook-sida per segment (till exempel: Adobe Campaign Paris, Adobe Campaign London osv.).

Men det går också att använda målgruppsfiltren som används av Facebook. På fliken **[!UICONTROL Audience]** i **[!UICONTROL Select target window]** finns fyra filter:

* **[!UICONTROL Country]**
* **[!UICONTROL Regions]**
* **[!UICONTROL Cities]**
* **[!UICONTROL Languages]**

>[!IMPORTANT]
>
>Använd den här funktionen med försiktighet. I leveransrapporter kommer indikatorn **[!UICONTROL Number of fans]** inte att ta hänsyn till dessa Facebook-filter.
>
>Facebook kan ändra listan över målgruppsfilter och deras värden.

## Definiera meddelandeinnehåll {#defining-message-content}

Välj typ av publikation med listrutan **[!UICONTROL Content type]**.

![](assets/social_facebook_delivery_006.png)

Följande typer av leveranser är tillgängliga:

* a **[!UICONTROL Status]**
* a **[!UICONTROL Status with a link]**
* a **[!UICONTROL Status with a YouTube link]**
* a **[!UICONTROL Photo album]**

### Publicera en status {#publishing-a-status}

Leverans av en statustyp kan bara innehålla text, som i exemplet nedan:

![](assets/social_create_facebook_wall_post_004.png)

Ange publiceringsstatus i indatazonen.

![](assets/social_facebook_delivery_015.png)

### Publicera en status med en länk {#publishing-a-status-with-a-link}

En statustyp som levereras med en länk kan innehålla text, bilder och en länk. I följande avsnitt beskrivs symmetrin mellan fälten på leveransredigeringsskärmen och det slutliga dokumentet på Facebook:

![](assets/social_facebook_delivery_007.png)

Ange de olika fälten:

>[!IMPORTANT]
>
>Alla URL-adresser måste börja med **&quot;http://&quot;** eller **&quot;https://&quot;**.

1. I fältet **[!UICONTROL Status]** anger du den text som ska visas under sidans namn.
1. Ange publikationstiteln i fältet **[!UICONTROL Name]**.
1. I fältet **[!UICONTROL Link]** anger du den URL som publikationen pekar på.

   >[!NOTE]
   >
   >Om du vill lägga till fältet **[!UICONTROL Link]** i URL:en för ett Facebook-program för att marknadsföra det rekommenderar vi att du anpassar det efter villkoren för smartphone-visning:
   >
   >1. Markera Facebook [https://developers.facebook.com/apps](https://developers.facebook.com/apps) och välj fliken **[!UICONTROL Settings > Basic]**.
   >1. Ange fältet **[!UICONTROL Namespace]**.
   >1. Ange fältet **[!UICONTROL Mobile Site URL]**: När en användare klickar på publiceringslänken på sin smarttelefon dirigeras de automatiskt om av Facebook till den URL som definieras i det här fältet.
   >1. Skapa webbprogrammet så att Facebook-skärmen anpassas efter den enhet som används (smartphone eller PC).
   >1. Gå till fältet **[!UICONTROL Link]** för publikationen via Adobe Campaign-konsolen och ange URL:en för fältet **[!UICONTROL Canvas page]**.


1. I fältet **[!UICONTROL Image]** anger du URL-adressen till bilden som ska visas till vänster om publikationen.

   >[!IMPORTANT]
   >
   >Bilden måste lagras på en offentlig webbplats för att Facebook ska kunna överföra den.

1. I fältet **[!UICONTROL Caption]** anger du den text som ska visas i slutet av publikationen.
1. Gå till fältet **[!UICONTROL Description]** och ange texten som ska visas under rubriken.

![](assets/social_facebook_delivery_005.png)

### Publicera en status med en YouTube-länk {#publishing-a-status-with-a-youtube-link}

Med den här typen av innehåll kan du publicera en länk till en YouTube-video. Precis som med en status med en vanlig länk kan du definiera en status, ett namn, en bildtext, en beskrivning och ytterligare en länk. Bilden läggs till automatiskt av Facebook. Symtomen mellan fälten på leveransskärmen och det slutliga dokumentet på Facebook är följande:

![](assets/social_facebook_delivery_youtube_1.png)

Ange de olika fälten:

>[!IMPORTANT]
>
>Alla URL-adresser måste börja med **&quot;http://&quot;** eller **&quot;https://&quot;**.

1. I fältet **[!UICONTROL Status]** anger du den text som ska visas under sidans namn.
1. Ange publikationstiteln i fältet **[!UICONTROL Name]**.
1. I fältet **[!UICONTROL Video code]** anger du koden för YouTube-videon. För exempelvis https://www.youtube.com/watch?v=abc123456&#39; blir videokoden abc123456.
1. I fältet **[!UICONTROL Caption]** anger du den text som ska visas i slutet av publikationen.
1. Gå till fältet **[!UICONTROL Description]** och ange texten som ska visas under rubriken.

![](assets/social_facebook_delivery_youtube.png)

### Publicera ett fotoalbum {#publishing-a-photo-album}

Med den här typen av innehåll kan du publicera ett fotoalbum. Du kan lägga till ett namn och en beskrivning för albumet samt en beskrivning för varje foto. Symtomen mellan fälten på leveransskärmen och det slutliga dokumentet på Facebook är följande:

![](assets/social_facebook_delivery_photos_1.png)

Ange de olika fälten:

1. Börja med att ange **[!UICONTROL Album name]**.
1. Ange sedan **[!UICONTROL Description]** som ska visas ovanför fotona.
1. Om du vill lägga till ett foto klickar du på knappen **[!UICONTROL Add]**, markerar fotot och klickar på **[!UICONTROL Open]**.
1. En bildtext kan läggas till i varje foto.

![](assets/social_facebook_delivery_photos.png)

## Förhandsgranska {#previewing}

På fliken **[!UICONTROL Preview]** kan du visa återgivningen av publikationen.

1. Klicka på fliken **[!UICONTROL Preview]**.
1. Klicka på listrutan **[!UICONTROL Test personalization]** och välj **[!UICONTROL Service]**.
1. I fältet **[!UICONTROL Folder]** väljer du den tjänstmapp som innehåller dina Facebook-sidor. Som standard lagras sidorna i roten i **[!UICONTROL Facebook]**-tjänstmappen.
1. Markera den Facebook-sida där du vill testa förhandsvisningen.

![](assets/social_facebook_delivery_008.png)

>[!NOTE]
>
>Förhandsgranskningen kan skilja sig något från den slutliga Facebook-publikationen. Vi rekommenderar starkt att du skickar ett bevis före slutleverans för en exakt återgivning av publikationen. Se [Skicka korrektur](#sending-the-proof).

## Konfigurerar spårning {#configuring-tracking}

Spårning kan visas i leveransrapporterna och på fliken **[!UICONTROL Edit > Tracking]** för leverans och tjänst.

Klickningar på URL:en som finns i leveransen mäts av Adobe Campaign. Antalet klick på **[!UICONTROL Like]**-knappen, antalet kommentarer och antalet fans mäts av Facebook.

Spårningskonfigurationen är densamma som för en e-postleverans. Mer information om detta finns i [det här avsnittet](../../delivery/using/about-delivery-monitoring.md).

>[!NOTE]
>
>Spårning är aktiverat som standard i leveransmallen **[!UICONTROL Publish to a brand page]**.

## Skicka korrekturet {#sending-the-proof}

Vi rekommenderar starkt att du skickar ett bevis på din publikation före slutleveransen för att se exakt hur den återges på en privat testsida i Facebook. Mer information om hur du skapar en privat testsida för Facebook finns i [Skapa en testsida för Facebook](../../social/using/publishing-on-facebook-walls.md#creating-a-test-facebook-page). Stegen för att välja provtryck finns i [Välja provmålet](#selecting-the-proof-target).

Korrekturleveranser är identiska med e-postleveranser. Se [det här avsnittet](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Skicka meddelandet {#sending-the-message}

1. När innehållet har godkänts klickar du på **[!UICONTROL Send]**.
1. Välj **[!UICONTROL Deliver as soon as possible]** och klicka på knappen **[!UICONTROL Analyze]**.

   >[!NOTE]
   >
   >Med alternativet **[!UICONTROL Postpone the delivery]** kan du skjuta upp leveransen till ett senare datum.

   ![](assets/social_facebook_delivery_009.png)

1. Kontrollera resultatet när analysen är klar.
1. Klicka på **[!UICONTROL Confirm delivery]** och sedan på **[!UICONTROL Yes]**.

   ![](assets/social_facebook_delivery_016.png)
