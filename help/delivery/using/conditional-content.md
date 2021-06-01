---
product: campaign
title: Villkorligt innehåll
description: Villkorligt innehåll
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 4%

---

# Villkorligt innehåll{#conditional-content}

Genom att konfigurera fält för villkorligt innehåll kan du skapa dynamisk personalisering baserat på mottagarens profil, till exempel. Textblock och/eller bilder ersätts när ett visst villkor uppfylls.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#conditionnal-content-video)


## Använda villkor i ett e-postmeddelande {#using-conditions-in-an-email}

I exemplet nedan får du lära dig att skapa ett meddelande som dynamiskt anpassas efter mottagarens kön och intressen.

* Visning som visar &quot;Mr.&quot; eller&quot;Fröken&quot; enligt värdet för fältet **[!UICONTROL Gender]** (M eller F) i datakällan,
* Personligt anpassade nyhetsbrev eller kampanjerbjudanden enligt angivna eller identifierade intressen:

   * Ränta 1 - > Block 1
   * Ränta 2 - > Block 2
   * Ränta 3 - > Block 3
   * Ränta 4 - > Block 4

Om du vill skapa villkorligt innehåll enligt värdet för ett fält gör du så här:

1. Klicka på ikonen för anpassning och välj **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Anpassningselementen infogas i meddelandetexten. Du måste konfigurera dem nu.

1. Fyll sedan i parametrarna för uttrycket **if**.

   Så här gör du:

   * Markera det första elementet i uttrycket, **`<field>`**, (som standard markeras det här elementet när uttrycket **if** infogas) och klicka på personaliseringsikonen för att ersätta det med testfältet.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Ersätt **`<value>`** med värdet för det fält som villkoret ska uppfyllas för. Värdet måste vara inom citattecken.
   * Ange det innehåll som ska infogas när villkoret är uppfyllt. Detta kan bestå av text, en bild, ett formulär, en hypertextlänk osv.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Klicka på fliken **[!UICONTROL Preview]** för att visa innehållet i meddelandet enligt leveransmottagaren:

   * Välja en mottagare för vilken villkoret är sant:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Välja en mottagare för vilken villkoret inte är sant:

      ![](assets/s_ncs_user_conditional_content06.png)

Du kan lägga till andra fall och definiera olika innehåll utifrån värdena i ett eller flera fält. Använd **[!UICONTROL Conditional content > Else]** och **[!UICONTROL Conditional content > Else if]** för att göra detta. Uttrycken konfigureras på samma sätt som uttrycket **if**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Om du vill ta hänsyn till JavaScript-syntaxen måste du ta bort tecknen **%> &lt;%** efter att du har lagt till **Annars** och **Annars om** villkor.

Klicka på **[!UICONTROL Preview]** och välj en mottagare för att visa det villkorliga innehållet.

![](assets/s_ncs_user_conditional_content08.png)

## Skapar flerspråkig e-post {#creating-multilingual-email}

I exemplet nedan får du lära dig att skapa ett flerspråkigt e-postmeddelande. Innehållet visas på det ena språket eller det andra beroende på vilket språk mottagaren föredrar.

1. Skapa ett e-postmeddelande och välj målpopulation. I det här exemplet baseras villkoret för att visa en version eller den andra på värdet **Språk** för mottagarens profil. I det här exemplet är dessa värden inställda på **EN**, **FR**, **ES**.
1. Klicka på fliken **[!UICONTROL Source]** i HTML-innehåll som skickas via e-post och klistra in följande kod:

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Testa e-postinnehåll på fliken **[!UICONTROL Preview]** genom att välja mottagare med olika språk.

   >[!NOTE]
   >
   >Eftersom ingen alternativ version har definierats i e-postinnehållet måste du filtrera målpopulationen innan du skickar e-postmeddelandet.

## Självstudievideo {#conditionnal-content-video}

Lär dig hur du lägger till villkorligt innehåll i en leverans med ett exempel på ett flerspråkigt nyhetsbrev.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

Ytterligare Campaign Classic-instruktionsvideor finns [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
