---
product: campaign
title: Felsöka ACS Connector
description: Felsöka ACS Connector
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Felsöka ACS Connector{#troubleshooting-the-acs-connector}

![](../../assets/v7-only.svg)

Beroende på implementeringen kan du stöta på flera vanliga problem.

* **Vilka är gränssnittsskillnaderna mellan Campaign Standard och Campaign v7?**

   Campaign Standard och Campaign v7 fungerar på ungefär samma sätt. De flesta koncept är desamma, men i vissa fall kan tillvägagångssättet skilja sig något. Här följer några av de koncept som kan skilja sig åt i kontexten för ACS Connector:

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> mottagare (eller någon annan profildimension)<br /> </td> 
   <td> profiler<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> publik<br /> </td> 
  </tr> 
  <tr> 
   <td> kampanjarbetsflöden, målgruppsarbetsflöden<br /> </td> 
   <td> arbetsflöden<br /> </td> 
  </tr> 
  <tr> 
   <td> operationer<br /> </td> 
   <td> kampanjer<br /> </td> 
  </tr> 
  <tr> 
   <td> webbprogram<br /> </td> 
   <td> landningssidor<br /> </td> 
  </tr> 
  <tr> 
   <td> anpassat tabell- och schematillägg<br /> </td> 
   <td> anpassad resurs och resurstillägg<br /> </td> 
  </tr> 
  <tr> 
   <td> dirigerade medlemmar<br /> </td> 
   <td> testprofiler<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **Mottagarna av Campaign v7-instansen är inte synkroniserade eller synliga för Campaign Standarden.**

   Det här fallet kan inträffa av olika orsaker:

   * Mottagarna skapades eller uppdaterades just i Campaign v7. Synkroniseringen startar var 15:e minut. Detta innebär att uppdaterade eller nyligen skapade mottagare visas i Campaign Standarden efter nästa synkronisering.
   * Implementeringen kan ha ställts in på att bara synkronisera mottagare från specifika mappar. Mottagare från andra mappar är inte synkroniserade.
   * Mottagaren kan synkroniseras men inte visas i Campaign Standard. Kontrollera mappningen av mapprättigheter.

* **Jag hittar inte de profilfält som jag behöver basera min fråga på i Campaign Standarden.**

   Som standard synkroniseras 20 fält från nms:mottagartabellen med Campaign Standard. Se den detaljerade listan över synkroniserade fält. Alla ytterligare fält som du behöver hämta i Campaign Standarden måste mappas och konfigureras av din konsult.

   Om du vill vara säker på att fältet som du vill använda är tillgängligt kan du kontrollera profilresursdefinitionen från **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Dessutom synkroniseras inte alla data som bifogas till mottagare och lagras i tabeller som är relaterade till nms:templates som standard med Campaign Standard.

   Om du fortfarande vill kunna använda relaterade data kan du utföra målanpassningen i Campaign v7 och lägga till ytterligare data enligt anvisningarna i [Synkronisera målgrupper](../../integrations/using/synchronizing-audiences.md) eller så kan du kontakta en konsult för att utforska olika anpassningsmöjligheter.

* **Jag använder en annan profildimension än standardvärdet nms:receive i Campaign v7, hur kan jag synkronisera dem med Campaign Standard?**

   Campaign Standarden använder en unik målinriktningsresurs med namnet **profiler**. Den grundläggande implementeringen av funktionen Campaign Standard Connect ger en standardmappning mellan Campaign v7-mottagare och Campaign Standard-profiler.

   Om du använder en annan profildimension i Campaign v7, eller om du använder flera, måste alla mappas med Campaign Standard-profiler. Kontakta din konsult för att diskutera just detta behov.

* **Jag vill dela en lista med profiler med Campaign Standard via ett arbetsflöde, men kan inte hitta min målgrupp i Campaign Standard**.

   Målgrupper finns i **[!UICONTROL Audiences]** i Campaign Standard. De har etiketten som anges i **[!UICONTROL List update]** aktivitet i Campaign v7-arbetsflödet. De omfattas av mappmappmappningen som definieras under implementeringen.

   Det första som ska kontrolleras är om arbetsflödet har slutförts utan fel. Om du ser ett fel på **[!UICONTROL List update]** -aktiviteten, vilket innebär att synkroniseringen med Campaign Standarden kan ha misslyckats. Om du vill se mer information om vad som gick fel går du till **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Den här mappen innehåller synkroniseringsarbetsflöden som utlöses av **[!UICONTROL List update]** aktivitetskörning.

   Se även till att **[!UICONTROL Share with ACS]** alternativet är markerat i **[!UICONTROL List update]** och att arbetsflödet har körts korrekt.

   Observera att mottagarprofilerna i listan måste ha synkroniserats med Campaign Standarden innan arbetsflödet körs. När Campaign Standarden har delats med Campaign Standarden är mottagarna i listan avstämda med profiler, vilket innebär att de måste finnas där. Mottagare från listan som inte kan avstämas med profiler i Campaign Standarden ignoreras.

   Om du delar en lista som består av profiler och om ingen är synkroniserad med Campaign Standard skapas en tom frågepublik i Campaign Standard som inte kan användas.

* **Jag fick ett meddelande om att ett synkroniseringsarbetsflöde är i feltillstånd. Vad ska jag göra?**

   Kontrollera konfigurationen av det externa kontot i både Campaign Standard och Campaign v7 genom att testa anslutningen:

   * **[!UICONTROL acsDefaultRelayAccount]** i Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** i Campaign v7.

* **Jag har ingen säkerhetsgrupp tillgänglig när mappar mappas mellan Campaign v7 och Campaign Standard.**

   Du måste först synkronisera dina säkerhetsgrupper från **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Den här åtgärden kontrollerar vilka säkerhetsgrupper som är tillgängliga i Campaign Standard. När du har synkroniserat kan du hitta säkerhetsgrupperna när du konfigurerar mappmappningen.

* **Jag kan inte redigera en profil, en målgrupp eller en landningssida i Campaign Standarden. Vad betyder det?**

   Resurser som synkroniseras från Campaign v7 är i skrivskyddat läge i Campaign Standard för att säkerställa att data är konsekventa. Om du behöver redigera något av dessa element kan du göra det i Campaign v7 och sedan replikera ändringen av Campaign Standarden.
