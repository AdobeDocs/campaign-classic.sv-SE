---
product: campaign
title: Använd namngivna rättigheter för att ställa in behörigheter
description: Lär dig hur du använder namngivna rättigheter för att ställa in behörigheter
feature: Åtkomsthantering
role: User, Admin
level: Beginner
exl-id: 07470a91-d8d2-4c41-9555-05522c8068f0
source-git-commit: 6c28e6cd78ce7a8ee5c0dc7e671de780787b9f57
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 6%

---

# Använd namngivna rättigheter för att ställa in behörigheter{#named-rights}

Som standard föreslår Adobe Campaign en uppsättning namngivna rättigheter som gör att du kan definiera de behörigheter som tilldelats operatorer och grupper av operatorer. Dessa rättigheter kan redigeras från noden **[!UICONTROL Administration > Access management > Named rights]** i trädet.

![](assets/s_ncs_admin_named_rights.png)

Dessa rättigheter är följande:

* **[!UICONTROL ADMINISTRATION]**: Operatorer med  **[!UICONTROL ADMINISTRATION]** rättigheten har fullständig åtkomst till instansen. Administratörsanvändare kan köra/skapa/redigera/ta bort objekt som arbetsflöde, leverans, skript osv.

* **[!UICONTROL APPROVAL ADMINISTRATION]**: Du kan ange flera godkännandesteg i arbetsflöden och leveranser för att säkerställa att det aktuella läget har godkänts av en tilldelad operator eller grupp. Användare med rättigheten **[!UICONTROL APPROVAL ADMINISTRATION]** kan ange godkännandesteg och även tilldela en operator eller operatörsgrupp som ska godkänna dessa steg.

* **[!UICONTROL CENTRAL]**: Rätt till central hantering (distribuerad marknadsföring).

* **[!UICONTROL DELETE FOLDER]**: Rätt att ta bort mappar. Med den här rättigheten kan användare ta bort mappar från utforskarvyn.

* **[!UICONTROL EDIT FOLDERS]**: Rätt att ändra mappegenskaper som internt namn, etikett, associerad bild, undermappsordning osv.

* **[!UICONTROL EXPORT]**: Användare kan exportera data från sina Adobe Campaign-instanser till en fil på servern eller den lokala datorn med hjälp av  **[!UICONTROL EXPORT]** arbetsflödesaktiviteten.

* **[!UICONTROL FILES ACCESS]**: Rätt att läsa och skriva för filer via ett skript som kan skrivas i  **[!UICONTROL JavaScript]** arbetsflödesaktiviteten för att läsa och skriva filer på en server.

* **[!UICONTROL IMPORT]**: Rätt för allmän dataimport. **[!UICONTROL IMPORT]** tillåter att du importerar data till andra tabeller, medan  **[!UICONTROL RECIPIENT IMPORT]** rättigheten bara tillåter import till mottagartabellen.

* **[!UICONTROL INSERT FOLDERS]**: Rätt att infoga mappar. Användare med rättigheten **[!UICONTROL INSERT FOLDERS]** kan skapa nya mappar i mappträdet i utforskarvyn.

* **[!UICONTROL LOCAL]**: Rätt till lokal hantering (distribuerad marknadsföring).

* **[!UICONTROL MERGE]**: Höger om du vill sammanfoga de markerade posterna till en. Om mottagarna finns som dubbletter kan användaren med **[!UICONTROL MERGE]**-rättigheten välja dubbletter och sammanfoga dem till en primär mottagare.

* **[!UICONTROL PREPARE DELIVERIES]**: Rätt att skapa, redigera och spara en leverans. Användare med rättigheten **[!UICONTROL PREPARE DELIVERIES]** kan också starta leveransanalysprocessen.

* **[!UICONTROL PRIVACY DATA RIGHT]**: Rätt att samla in och ta bort personuppgifter. Se denna [sida](https://helpx.adobe.com/se/campaign/kb/acc-privacy.html) för mer information om detta.

* **[!UICONTROL PROGRAM EXECUTION]**: Rätt att köra kommandon på olika programmeringsspråk.

* **[!UICONTROL RECIPIENT IMPORT]**: Rätt att importera mottagare. Användare med rättigheten **[!UICONTROL RECIPIENT IMPORT]** kan importera en lokal fil till mottagartabellen.

* **[!UICONTROL SQL SCRIPT EXECUTION]** Rätt att köra ett SQL-kommando direkt i databasen.

* **[!UICONTROL START DELIVERIES]**: Rätt att godkänna tidigare analyserade leveranser. Efter leveransanalysen pausas leveransen vid olika godkännandesteg och måste godkännas för att kunna återupptas. Användare med rättigheten **[!UICONTROL START DELIVERIES]** kan godkänna leveranser.

* **[!UICONTROL USE SQL DATA MANAGEMENT ACTIVITY]**: Rätt att skriva egna SQL-skript med SQL Data Management-aktiviteten för att skapa och fylla i arbetstabeller (se  [det här avsnittet](../../workflow/using/sql-data-management.md)).

* **[!UICONTROL WORKFLOW]**: Rätt att köra arbetsflöden. Utan den här rättigheten kan användare inte starta, stoppa eller starta om arbetsflöden.

* **[!UICONTROL WEBAPP]**: Rätt att använda webbprogram.

>[!NOTE]
>
>Listan kan variera beroende på vilka tillägg som är installerade på plattformen.

## Matris för åtkomsträttigheter {#access-rights-matrix}

Standardgrupper och namngivna rättigheter ger operatorer åtkomst till vissa mappar i navigeringshierarkin och ger behörighet att läsa, skriva och ta bort.

Matrisen för Adobe Campaign-åtkomsträttigheter är tillgänglig [här](/help/platform/using/assets/access-rights-matrix.pdf).

[![image](assets/do-not-localize/user_management.png)](https://experienceleague.adobe.com/docs/campaign-classic/assets/access-rights-matrix.pdf?lang=en)
