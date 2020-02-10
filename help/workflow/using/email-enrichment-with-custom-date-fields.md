---
title: E-postberikning med anpassade datumfält
seo-title: E-postberikning med anpassade datumfält
description: E-postberikning med anpassade datumfält
seo-description: null
page-status-flag: never-activated
uuid: 6dd240b1-f995-4e12-90a5-55aeb584bcdc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9cb3be65-6652-47fa-b8a4-e088530aab4a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# E-postberikning med anpassade datumfält{#email-enrichment-with-custom-date-fields}

I det här exemplet vill vi skicka ett e-postmeddelande med anpassade datafält till mottagare som kommer att fira sina födelsedagar den här månaden. E-postmeddelandet innehåller en kupong som är giltig en vecka före och efter deras födelsedagar.

Vi måste inrikta oss på mottagare från en lista som kommer att fira sina födelsedagar den här månaden med en **[!UICONTROL Split]** aktivitet. När du sedan använder aktiviteten fungerar det anpassade datafältet som giltighetsdatum i e-postmeddelandet för kundens specialerbjudande. **[!UICONTROL Enrichment]**

![](assets/uc_enrichment.png)

Så här skapar du det här exemplet:

1. Dra och släpp en aktivitet på fliken **[!UICONTROL Targeting and workflows]** **[!UICONTROL Read list]** i kampanjen för att ange en lista över mottagare som mål.
1. Listan som ska bearbetas kan anges explicit, beräknas av ett skript eller lokaliseras dynamiskt enligt de alternativ som valts och parametrar som definierats här.

   ![](assets/uc_enrichment_1.png)

1. Lägg till en **[!UICONTROL Split]** aktivitet för att skilja mottagare som kommer att fira sina födelsedagar den här månaden från andra mottagare.
1. Om du vill dela listan väljer du **[!UICONTROL Filtering of selected records]** i **[!UICONTROL Add a filtering condition on the inbound population]** kategorin. Klicka sedan på **[!UICONTROL Edit]**.

   ![](assets/uc_enrichment_2.png)

1. Markera **[!UICONTROL Filtering conditions]** och klicka sedan på **[!UICONTROL Edit expression]** knappen för att filtrera månaden för mottagarens födelsedag.

   ![](assets/uc_enrichment_3.png)

1. Klicka **[!UICONTROL Advanced Selection]** sedan **[!UICONTROL Edit the formula using an expression]** och lägg till följande uttryck: Month(@bornDate).
1. Markera i **[!UICONTROL Operator]** kolumnen **[!UICONTROL equal to]**.
1. Du kan filtrera villkoret ytterligare genom att lägga till **[!UICONTROL Value]** månaden för aktuellt datum: Month(GetDate()).

   Detta skickar en fråga till mottagare vars födelsedag motsvarar den aktuella månaden.

   ![](assets/uc_enrichment_4.png)

1. Klicka **[!UICONTROL Finish]**. Klicka sedan på fliken **[!UICONTROL General]** i **[!UICONTROL Split]** aktiviteten **[!UICONTROL Generate complement]** i **[!UICONTROL Results]** kategorin.

   Med **[!UICONTROL Complement]** resultatet kan du lägga till en leveransaktivitet eller uppdatera en lista. Här har vi just lagt till en **[!UICONTROL End]** aktivitet.

   ![](assets/uc_enrichment_6.png)

Nu måste du konfigurera din **[!UICONTROL Enrichment]** aktivitet:

1. Lägg till en **[!UICONTROL Enrichment]** aktivitet efter din delmängd för att lägga till anpassade datumfält.

   ![](assets/uc_enrichment_7.png)

1. Öppna din **[!UICONTROL Enrichment]** aktivitet. Klicka på i **[!UICONTROL Complementary information]** kategorin **[!UICONTROL Add data]**.

   ![](assets/uc_enrichment_8.png)

1. Välj **[!UICONTROL Data linked to the filtering dimension]** sedan **[!UICONTROL Data of the filtering dimension]**.
1. Klicka på **[!UICONTROL Add]** knappen.

   ![](assets/uc_enrichment_9.png)

1. Lägg till en **[!UICONTROL Label]**. Klicka sedan i **[!UICONTROL Expression]** kolumnen **[!UICONTROL Edit expression]**.

   ![](assets/uc_enrichment_10.png)

1. Först måste vi rikta in veckan före födelsedatumet som **giltighetsstartdatum** med följande **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. Om du sedan vill skapa det anpassade datumfältet **Giltighetsslutdatum** som är målveckan efter födelsedatumet måste du lägga till **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   Du kan lägga till en etikett i uttrycket.

   ![](assets/uc_enrichment_12.png)

1. Klicka **[!UICONTROL Ok]**. Din berikning är nu klar.

Efter din **[!UICONTROL Enrichment]** aktivitet kan du lägga till en leverans. I det här fallet har vi lagt till en e-postleverans för att skicka ett specialerbjudande med giltighetsdatum till kunder som firar sina födelsedagar den här månaden.

1. Dra och släpp en **[!UICONTROL Email delivery]** aktivitet efter din **[!UICONTROL Enrichment]** aktivitet.

   ![](assets/uc_enrichment_15.png)

1. Dubbelklicka på din **[!UICONTROL Email delivery]** aktivitet för att börja personalisera leveransen.
1. Lägg till en **[!UICONTROL Label]** till leveransen och klicka på **[!UICONTROL Continue]**.
1. Klicka **[!UICONTROL Save]** för att skapa e-postleveransen.
1. Kontrollera på fliken **[!UICONTROL Approval]** för e-postleveransen **[!UICONTROL Properties]** att **[!UICONTROL Confirm delivery before sending option]** kryssrutan är markerad.

   Starta sedan arbetsflödet för att berika den utgående övergången med målinformationen.

   ![](assets/uc_enrichment_18.png)

Nu kan du börja designa din e-postleverans med de anpassade datumfälten som skapas i **[!UICONTROL Enrichment]** aktiviteten.

1. Dubbelklicka på din **[!UICONTROL Email delivery]** aktivitet.
1. Lägg till måltilläggen i e-postmeddelandet. Den ska finnas i följande uttryck för att konfigurera formatet för dina giltighetsdatum:

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. Klicka på ![](assets/uc_enrichment_16.png) . Välj **[!UICONTROL Target extension]** sedan de tidigare skapade anpassade giltighetsdatumen med aktiviteten för **[!UICONTROL Enrichment]** att lägga till tillägget i formatetDate-uttrycket.

   ![](assets/uc_enrichment_19.png)

1. Konfigurera e-postinnehållet efter behov.

   ![](assets/uc_enrichment_17.png)

1. Förhandsgranska din e-post för att kontrollera om dina anpassade datumfält är korrekt konfigurerade

   ![](assets/uc_enrichment_20.png)

Din e-postadress är nu klar. Du kan börja skicka dina korrektur och bekräfta leveransen för att skicka dina födelsedag via e-post.
