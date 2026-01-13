---
product: campaign
title: Använd namngivna rättigheter för att ställa in behörigheter
description: Lär dig hur du använder namngivna rättigheter för att ställa in behörigheter
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 02ecc0e6bb3bd361f512baeefc9e0f2271063387
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 3%

---

# Använd namngivna rättigheter för att ställa in behörigheter{#named-rights}

Som standard föreslår Adobe Campaign en uppsättning namngivna rättigheter som gör att du kan definiera de behörigheter som tilldelats operatorer och grupper av operatorer. Dessa rättigheter kan redigeras från noden **[!UICONTROL Administration > Access management > Named rights]** i trädet.

![](assets/s_ncs_admin_named_rights.png)

Dessa rättigheter är följande:

* **[!UICONTROL ADMINISTRATION]**: Operatorer med rättigheten **[!UICONTROL ADMINISTRATION]** har fullständig åtkomst till instansen. Administratörsanvändare kan köra/skapa/redigera/ta bort objekt som arbetsflöde, leverans, skript osv.

  >[!IMPORTANT]
  >
  >**När du har migrerat till IMS:** När du har migrerat till Adobe Identity Management System (IMS) kommer alla produktprofiler eller namngivna rättigheter som innehåller ordet &quot;admin&quot; i namnet (till exempel &quot;Administratörer&quot;, &quot;admin&quot;, &quot;administratörer&quot; osv.) automatiskt att ge åtkomst till Campaign-kontrollpanelen. Vi rekommenderar att du undviker att använda admin i namngivna höger- eller rollnamn, såvida du inte avser att ge dessa användare åtkomst till Kontrollpanelen. Läs mer om [IMS-migrering](../../technotes/using/migrate-users-to-ims.md) och [hantering av åtkomst till Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv-SE){target="_blank"}.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: Du kan ange flera godkännandesteg i arbetsflöden och leveranser för att säkerställa att det aktuella tillståndet har godkänts av en tilldelad operator eller grupp. Användare med rättigheten **[!UICONTROL APPROVAL ADMINISTRATION]** kan ange godkännandesteg och även tilldela en operator eller operatorgrupp som ska godkänna dessa steg.

  >[!IMPORTANT]
  >
  >**Efter migrering till IMS:** Produktprofiler eller namngivna rättigheter som innehåller ordet &quot;admin&quot; (till exempel &quot;Godkännandeadministratör&quot;) ger åtkomst till Campaign-kontrollpanelen. Läs mer om [IMS-migrering](../../technotes/using/migrate-users-to-ims.md) och [hantering av åtkomst till Kontrollpanelen](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=sv-SE){target="_blank"}.

* **[!UICONTROL CENTRAL]**: Rätt till central hantering (distribuerad marknadsföring).

* **[!UICONTROL DELETE FOLDER]**: Rätt att ta bort mappar. Med den här rättigheten kan användare ta bort mappar från utforskarvyn.

* **[!UICONTROL EDIT FOLDERS]**: Rätt att ändra mappegenskaper som internt namn, etikett, associerad bild, undermappsordning osv.

* **[!UICONTROL EXPORT]**: Användare kan exportera data från sina Adobe Campaign-instanser till en fil på servern eller den lokala datorn med hjälp av arbetsflödesaktiviteten i **[!UICONTROL EXPORT]**.

* **[!UICONTROL FILES ACCESS]**: Rätt att läsa och skriva åtkomst för filer via ett skript som kan skrivas i arbetsflödesaktiviteten i **[!UICONTROL JavaScript]** för att läsa/skriva filer på en server.

* **[!UICONTROL IMPORT]**: Rätt för allmän dataimport. **[!UICONTROL IMPORT]** tillåter att du importerar data till andra tabeller, medan rättigheten **[!UICONTROL RECIPIENT IMPORT]** bara tillåter import till mottagartabellen.

* **[!UICONTROL INSERT FOLDERS]**: Rätt att infoga mappar. Användare med rättigheten **[!UICONTROL INSERT FOLDERS]** kan skapa nya mappar i mappträdet i utforskarvyn.

* **[!UICONTROL LOCAL]**: Rätt till lokal hantering (distribuerad marknadsföring).

* **[!UICONTROL MERGE]**: Höger att sammanfoga de markerade posterna till en. Om mottagarna finns som dubbletter tillåter rättigheten **[!UICONTROL MERGE]** användaren att välja dubbletter och sammanfoga dem till en primär mottagare.

* **[!UICONTROL PREPARE DELIVERIES]**: Rätt att skapa, redigera och spara en leverans. Användare med rättigheten **[!UICONTROL PREPARE DELIVERIES]** kan också starta leveransanalysprocessen.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Rätt att samla in och ta bort sekretessdata. Se denna [sida](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html) för mer information om detta.

* **[!UICONTROL PROGRAM EXECUTION]**: Rätt att köra kommandon på olika programmeringsspråk.

* **[!UICONTROL RECIPIENT IMPORT]**: Rätt att importera mottagare. Användare med rättigheten **[!UICONTROL RECIPIENT IMPORT]** kan importera en lokal fil till mottagartabellen.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Rätt att köra ett SQL-kommando direkt i databasen.

* **[!UICONTROL START DELIVERIES]**: Rätt att godkänna tidigare analyserade leveranser. Efter leveransanalysen pausas leveransen vid olika godkännandesteg och måste godkännas för att kunna återupptas. Användare med rättigheten **[!UICONTROL START DELIVERIES]** kan godkänna leveranser.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Rätt att skriva egna SQL-skript med SQL Data Management-aktiviteten för att skapa och fylla i arbetstabeller. Se [Campaign v8-dokumentationen](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/sql-data-management.html?lang=sv-SE){target="_blank"}.

* **[!UICONTROL WORKFLOW]**: Rätt att köra arbetsflöden. Utan den här rättigheten kan användare inte starta, stoppa eller starta om arbetsflöden.

* **[!UICONTROL WEBAPP]**: Rätt att använda webbprogram.

>[!NOTE]
>
>Listan kan variera beroende på vilka tillägg som är installerade på plattformen.

## Matris för åtkomsträttigheter {#access-rights-matrix}

Standardgrupper och namngivna rättigheter ger operatorer åtkomst till vissa mappar i navigeringshierarkin och ger behörighet att läsa, skriva och ta bort.

Adobe Campaign åtkomsträttighetsmatris är tillgänglig [här](/help/platform/using/assets/access-rights-matrix.pdf).

[![bild](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=sv-SE)
