---
title: Felsöka ACS Connector
seo-title: Felsöka ACS Connector
description: Felsöka ACS Connector
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# Felsöka ACS Connector{#troubleshooting-the-acs-connector}

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

* **Mottagarna av Campaign v7-instansen är inte synkroniserade eller synliga för Campaign Standard.**

   Det här fallet kan inträffa av olika orsaker:

   * Mottagarna skapades eller uppdaterades just i Campaign v7. Synkroniseringen startar var 15:e minut. Det innebär att uppdaterade eller nyligen skapade mottagare visas i Campaign Standard efter nästa synkronisering.
   * Implementeringen kan ha ställts in på att bara synkronisera mottagare från specifika mappar. Mottagare från andra mappar är inte synkroniserade.
   * Mottagaren kan synkroniseras men inte visas i Campaign Standard. Kontrollera mappningen av mapprättigheter.

* **Jag hittar inte de profilfält som jag behöver basera min fråga på i Campaign Standard.**

   Som standard synkroniseras 20 fält från tabellen nms:mottagare med Campaign Standard. Se den detaljerade listan över synkroniserade fält. Alla ytterligare fält som du behöver hämta i Campaign Standard måste mappas och konfigureras av din konsult.

   Om du vill vara säker på att fältet som du vill använda är tillgängligt kan du kontrollera profilresursdefinitionen från **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   Dessutom synkroniseras inte alla data som bifogas till mottagare och lagras i tabeller som är relaterade till nms:templates som standard till Campaign Standard.

   Om du fortfarande vill kunna använda relaterade data kan du utföra din målgruppsanpassning i Campaign v7 och lägga till ytterligare data enligt beskrivningen i avsnittet [Synkronisera målgrupper](../../integrations/using/synchronizing-audiences.md) , eller så kan du kontakta din konsult för att utforska anpassningsmöjligheterna.

* **Jag använder en annan profildimension än standardvärdet nms:receive i Campaign v7, hur kan jag synkronisera dem med Campaign Standard?**

   Campaign Standard använder en unik målinriktningsresurs som kallas **profiler**. Den grundläggande implementeringen av Campaign Standard Connect-funktionen ger en standardmappning mellan Campaign v7-mottagare och Campaign Standard-profiler.

   Om du använder en annan profildimension i Campaign v7, eller om du använder flera, måste alla mappas med Campaign Standard-profiler. Kontakta din konsult för att diskutera just detta behov.

* **Jag vill dela en lista med profiler med Campaign Standard via ett arbetsflöde, men kan inte hitta min målgrupp i Campaign Standard**.

   Målgrupper finns på menyn **[!UICONTROL Audiences]** i Campaign Standard. De har den etikett som anges i **[!UICONTROL List update]** aktiviteten i Campaign v7-arbetsflödet. De omfattas av mappmappmappningen som definieras under implementeringen.

   Det första som ska kontrolleras är om arbetsflödet har slutförts utan fel. Om du märker ett fel i **[!UICONTROL List update]** aktiviteten betyder det att synkroniseringen med Campaign Standard kan ha misslyckats. Om du vill se mer information om vad som gick fel går du till **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Den här mappen innehåller synkroniseringsarbetsflöden som utlöses av **[!UICONTROL List update]** aktivitetskörningen.

   Kontrollera också att **[!UICONTROL Share with ACS]** alternativet är incheckat i **[!UICONTROL List update]** aktiviteten och att arbetsflödet har körts korrekt.

   Observera att mottagarprofilerna i listan måste ha synkroniserats med Campaign Standard innan arbetsflödet körs. När de väl har delats med Campaign Standard är mottagarna av listan avstämda med Campaign Standard-profiler, vilket innebär att de måste finnas där. Mottagare från listan som inte kan avstämas med profiler i Campaign Standard ignoreras.

   Om du delar en lista som består av profiler och om ingen är synkroniserad med Campaign Standard skapas en tom frågepublik i Campaign Standard som inte kan användas.

* **Jag fick ett meddelande om att ett synkroniseringsarbetsflöde är i feltillstånd. Vad ska jag göra?**

   Kontrollera konfigurationen av det externa kontot i både Campaign Standard och Campaign v7 genom att testa anslutningen:

   * **[!UICONTROL acsDefaultRelayAccount]** i Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** i Campaign v7.

* **Jag har ingen säkerhetsgrupp tillgänglig när mappar mappas mellan Campaign v7 och Campaign Standard.**

   Du måste först synkronisera dina säkerhetsgrupper från **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. Den här åtgärden kontrollerar de säkerhetsgrupper som är tillgängliga i Campaign Standard. När du har synkroniserat kan du hitta säkerhetsgrupperna när du konfigurerar mappmappningen.

* **Jag kan inte redigera en profil, en målgrupp eller en landningssida i Campaign Standard. Vad betyder det?**

   Resurser som synkroniseras från Campaign v7 är i skrivskyddat läge i Campaign Standard för att säkerställa att alla data är konsekventa. Om du behöver redigera något av dessa element kan du göra det i Campaign v7 och sedan upprepa ändringen i Campaign Standard.

