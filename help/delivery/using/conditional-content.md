---
product: campaign
title: Villkorligt innehåll
description: Lär dig hur du lägger till villkorsstyrt innehåll
badge-v7: label="v7" type="Informative" tooltip="Gäller Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Personalization, Multilingual Messages
role: User
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 6%

---

# Villkorligt innehåll{#conditional-content}

Genom att konfigurera fält för villkorligt innehåll kan du skapa dynamisk personalisering baserat på mottagarens profil, till exempel. Textblock och/eller bilder ersätts när ett visst villkor uppfylls.

![](assets/do-not-localize/how-to-video.png) [Upptäck den här funktionen i en video](#conditionnal-content-video)


## Använd villkor i ett e-postmeddelande {#using-conditions-in-an-email}

I exemplet nedan får du lära dig att skapa ett meddelande som dynamiskt anpassas efter mottagarens kön och intressen.

* Visning som visar &quot;Mr.&quot; eller&quot;Fröken&quot; enligt värdet på **[!UICONTROL Gender]** fält (M eller F) i datakällan,
* Personligt anpassade nyhetsbrev eller kampanjerbjudanden enligt angivna eller identifierade intressen:

   * Ränta 1 - > Block 1
   * Ränta 2 - > Block 2
   * Ränta 3 - > Block 3
   * Ränta 4 - > Block 4

Om du vill skapa villkorligt innehåll enligt värdet för ett fält gör du så här:

1. Klicka på ikonen för anpassning och välj **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Anpassningselementen infogas i meddelandetexten. Du måste konfigurera dem nu.

1. Fyll sedan i parametrarna för **if** -uttryck.

   Så här gör du:

   * Markera det första elementet i uttrycket, **`<field>`**, (som standard markeras det här elementet när du infogar **if** och klicka på personaliseringsikonen för att ersätta den med testfältet.

     ![](assets/s_ncs_user_conditional_content03.png)

   * Ersätt **`<value>`** med värdet för det fält för vilket villkoret kommer att uppfyllas. Värdet måste vara inom citattecken.
   * Ange det innehåll som ska infogas när villkoret är uppfyllt. Detta kan bestå av text, en bild, ett formulär, en hypertextlänk osv.

     ![](assets/s_ncs_user_conditional_content04.png)

1. Klicka på **[!UICONTROL Preview]** för att visa innehållet i meddelandet enligt leveransmottagaren:

   * Välja en mottagare för vilken villkoret är sant:

     ![](assets/s_ncs_user_conditional_content05.png)

   * Välja en mottagare för vilken villkoret inte är sant:

     ![](assets/s_ncs_user_conditional_content06.png)

Du kan lägga till andra fall och definiera olika innehåll utifrån värdena i ett eller flera fält. Om du vill göra det använder du **[!UICONTROL Conditional content > Else]** och **[!UICONTROL Conditional content > Else if]**. Uttrycken är konfigurerade på samma sätt som **if** -uttryck.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Om du vill följa JavaScript-syntaxen **%> &lt;%** tecken måste tas bort efter att de lagts till **Annars** och **Annars om** villkor.

Klicka **[!UICONTROL Preview]** och välj en mottagare för att visa det villkorliga innehållet.

![](assets/s_ncs_user_conditional_content08.png)

## Skapa flerspråkig e-post {#creating-multilingual-email}

I exemplet nedan får du lära dig att skapa ett flerspråkigt e-postmeddelande. Innehållet visas på det ena språket eller det andra beroende på vilket språk mottagaren föredrar.

1. Skapa ett e-postmeddelande och välj målpopulation. I det här exemplet baseras villkoret för att visa en version eller den andra på **Språk** värdet för mottagarens profil. I det här exemplet är dessa värden inställda på **EN**, **FR**, **ES**.
1. I e-postinnehållet i HTML klickar du på **[!UICONTROL Source]** och klistra in följande kod:

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

1. Testa e-postinnehåll i **[!UICONTROL Preview]** genom att välja mottagare med olika språk.

   >[!NOTE]
   >
   >Eftersom ingen alternativ version har definierats i e-postinnehållet måste du filtrera målpopulationen innan du skickar e-postmeddelandet.

## Självstudievideo {#conditionnal-content-video}

Lär dig hur du lägger till villkorsstyrt innehåll i en leverans med ett exempel som visar ett flerspråkigt nyhetsbrev.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

Det finns fler videor med Campaign Classic om hur man gör [här](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=sv).
