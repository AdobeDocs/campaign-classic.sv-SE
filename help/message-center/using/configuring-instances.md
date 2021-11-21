---
product: campaign
title: Konfigurera instanser
description: Lär dig hur du konfigurerar Transactional Messaging-kontroll och körningsinstanser i Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 23a384d1-27ce-46c2-98c3-0fb60a5c50ee
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1222'
ht-degree: 1%

---


# Konfigurera instanser {#creating-a-shared-connection}

![](../../assets/v7-only.svg)

Om du vill använda funktionerna för transaktionsmeddelanden måste du konfigurera instanser för kontroll och körning. Du kan använda antingen:
* [En kontrollinstans](#control-instance) associerat med en eller flera körningsinstanser
* [Flera kontrollinstanser](#using-several-control-instances) associerat med flera körningsinstanser

>[!IMPORTANT]
>
>Schematillägg påverkade resurserna som används av [Tekniska arbetsflöden för meddelandecenter](../../message-center/using/additional-configurations.md#technical-workflows) på antingen kontroll- eller körningsinstanser måste dupliceras på de andra instanser som används av Transactional Messaging-modulen.

Du måste också ange och ansluta körningsinstansen/körningsinstanserna till kontrollinstansen/kontrollinstanserna.

Alla steg som krävs för att konfigurera och ansluta kontroll- och körningsinstanserna beskrivs i det här avsnittet.

>[!IMPORTANT]
>
>Kontrollinstansen och körningsinstansen/körningsinstanserna måste vara installerade på olika datorer. De kan inte dela samma Campaign-instans.

## Konfigurera kontrollinstansen {#control-instance}

Om du vill ansluta kontrollinstansen och körningsinstanserna måste du först skapa och konfigurera en **[!UICONTROL Execution instance]** typ av externt konto **på kontrollinstansen**. Därför, en gång [publicerad](../../message-center/using/publishing-message-templates.md#template-publication), kan transaktionsmeddelandemallar distribueras till körningsinstanserna.

Om du använder flera körningsinstanser måste du skapa lika många externa konton som det finns körningsinstanser.

>[!NOTE]
>
>När körningsinstanser används av flera kontrollinstanser kan data delas upp efter mapp och operator. Mer information finns i [Använda flera kontrollinstanser](#using-several-control-instances).

### Skapa ett externt konto

>[!NOTE]
>
>Stegen nedan måste utföras **på kontrollinstansen**.

Skapa en **[!UICONTROL Execution instance]** skriv ett externt konto, använd följande:

1. Gå till **[!UICONTROL Administration > Platform > External accounts]** mapp.
1. Välj ett av de externa konton av körningsinstanstyp som finns i Adobe Campaign, högerklicka och välj **[!UICONTROL Duplicate]** .

   ![](assets/messagecenter_create_extaccount_001.png)

1. Ändra etiketten efter dina behov.

   ![](assets/messagecenter_create_extaccount_002.png)

1. Välj **[!UICONTROL Enabled]** möjlighet att göra det externa kontot operativt.

   ![](assets/messagecenter_create_extaccount_003.png)

1. Ange adressen till den server där körningsinstansen är installerad.

   ![](assets/messagecenter_create_extaccount_004.png)

1. Kontot måste matcha Message Center Agent enligt operatormappen. Som standard är det färdiga konto som tillhandahålls av Adobe Campaign **[!UICONTROL mc]** .

   ![](assets/messagecenter_create_extaccount_005.png)

1. Ange lösenordet för kontot enligt definitionen i mappen operator.

   >[!NOTE]
   >
   >Du kan undvika att ange ett lösenord varje gång du loggar in på instansen genom att ange IP-adressen för kontrollinstansen i körningsinstansen. Mer information finns i [Konfigurera körningsinstansen/instanserna](#execution-instance).

1. Ange den återställningsmetod som ska användas av körningsinstansen. De data som ska återställas vidarebefordras till kontrollinstansen av körningsinstansen för att läggas till i transaktionsmeddelanden och händelsearkiv.

   ![](assets/messagecenter_create_extaccount_007.png)

   Datainsamling sker antingen via en webbtjänst som använder HTTP/HTTPS-åtkomst eller via FDA-modulen (Federated Data Access).

   >[!NOTE]
   >
   >Observera att när du använder FDA över HTTP stöds endast körningsinstanser med en PostgreSQL-databas. MSSQL- eller Oraclena-databaser stöds inte.

   Den andra metoden (FDA) rekommenderas om kontrollinstansen har direktåtkomst till databasen med körningsinstanserna. Välj i annat fall webbtjänståtkomst. Det FDA-konto som ska anges sammanfaller med anslutningen till databaserna för de olika körningsinstanserna som skapas i kontrollinstansen.

   ![](assets/messagecenter_create_extaccount_008.png)

   Mer information om FDA (Federated Data Access) finns i [det här avsnittet](../../installation/using/about-fda.md).

1. Klicka **[!UICONTROL Test the connection]** för att kontrollera att kontrollinstansen och körningsinstansen är länkade till varandra.

   ![](assets/messagecenter_create_extaccount_006.png)

Om du använder flera körningsinstanser upprepar du dessa steg för att skapa så många externa konton som det finns körningsinstanser.

### Identifiera körningsinstanser {#identifying-execution-instances}

Varje körningsinstans måste associeras med en unik identifierare för att särskilja historiken för varje körningsinstans när de visas på kontrollinstansen.

Den här identifieraren kan tilldelas för varje körningsinstans **manuellt**. I det här fallet måste det här steget utföras **på varje körningsinstans**. Det gör du genom att använda distributionsguiden enligt nedan:

1. Öppna distributionsguiden på en körningsinstans.
1. Gå till **[!UICONTROL Message Center]** -fönstret.
1. Tilldela den valda identifieraren till instansen.

   ![](assets/messagecenter_id_execinstance_001.png)

1. Upprepa stegen ovan för varje körningsinstans.

Identifieraren kan också **automatiskt** attribut. För att göra det går du till **kontrollinstans** och klickar på **[!UICONTROL Initialize connection]** -knappen.

![](assets/messagecenter_create_extaccount_006bis.png)

## Konfigurera körningsinstansen/instanserna {#execution-instance}

>[!NOTE]
>
>Stegen nedan måste utföras **på körningsinstansen/instanserna**.

Följ stegen nedan för att ansluta körningsinstansen/körningsinstanserna till kontrollinstansen.

För att kontrollinstansen ska kunna ansluta till körningsinstansen utan att behöva ange ett lösenord anger du bara IP-adressen för kontrollinstansen i **Meddelandecenter** behörighetssektion. Tomma lösenord tillåts dock inte som standard.

Om du vill använda ett tomt lösenord går du till körningsinstanserna och definierar en säkerhetszon som är begränsad till IP-adressen för det informationssystem som skickar händelserna. Den här säkerhetszonen måste tillåta tomma lösenord och acceptera `<identifier> / <password>` typanslutningar. Mer information om detta finns i [det här avsnittet](../../installation/using/security-zones.md).

>[!NOTE]
>
>När körningsinstanser används av flera kontrollinstanser kan data delas upp efter mapp och operator. Mer information finns i [Använda flera kontrollinstanser](#using-several-control-instances).

1. På en körningsinstans går du till mappen operator ( **[!UICONTROL Administration > Access management > Operators]** ).
1. Välj **Meddelandecenter** agent.

   ![](assets/messagecenter_operator_001.png)

1. Välj **[!UICONTROL Edit]** flik, klicka **[!UICONTROL Access rights]** och klickar sedan på **[!UICONTROL Edit the access parameters...]** länk.

   ![](assets/messagecenter_operator_002.png)

1. I **[!UICONTROL Access settings]** klickar du på **[!UICONTROL Add a trusted IP mask]** länka och lägg till IP-adressen för kontrollinstansen.

   ![](assets/messagecenter_operator_003.png)

Om du använder flera körningsinstanser upprepar du dessa steg för varje körningsinstans.

## Använda flera kontrollinstanser {#using-several-control-instances}

Du kan dela ett körningskluster med olika kontrollinstanser. Den här typen av arkitektur kräver följande konfiguration.

Tänk dig att ditt företag hanterar två varumärken, var och en med sin egen kontrollinstans: **Kontroll 1** och **Kontroll 2**. Två körningsinstanser används också. Du måste ange en annan Message Center-operator för varje kontrollinstans: en **mc1** operatorn för **Kontroll 1** -instans och en **mc2** operatorn för **Kontroll 2** -instans.

I trädet med alla körningsinstanser skapar du en mapp per operator (**Mapp 1** och **Mapp 2**) och begränsa varje operatörs dataåtkomst till deras mapp.

### Konfigurera kontrollinstanser {#configuring-control-instances}

>[!NOTE]
>
>Stegen nedan måste utföras **på kontrollinstanserna**.

1. På **Kontroll 1** kontrollinstans, skapa ett externt konto per körningsinstans och ange **mc1** i varje externt konto. The **mc1** operatorn skapas sedan för alla körningsinstanser (se [Konfigurera körningsinstanser](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_1.png)

1. På **Kontroll 2** kontrollinstans, skapa ett externt konto per körningsinstans och ange **mc2** i varje externt konto. The **mc2** operatorn skapas sedan för alla körningsinstanser (se [Konfigurera körningsinstanser](#configuring-execution-instances)).

   ![](assets/messagecenter_multi_control_2.png)

   >[!NOTE]
   >
   >Mer information om hur du konfigurerar en kontrollinstans finns i [det här avsnittet](#control-instance).

### Konfigurera körningsinstanser {#configuring-execution-instances}

>[!NOTE]
>
>Stegen nedan måste utföras **på körningsinstanserna**.

Om du vill använda flera kontrollinstanser måste den här konfigurationen utföras på ALLA körningsinstanser.

1. Skapa en mapp per operator i **[!UICONTROL Administration > Production > Message Center]** nod: **Mapp 1** och **Mapp 2**. Mer information om hur du skapar mappar och vyer finns i [den här sidan](../../platform/using/access-management-folders.md).

   ![](assets/messagecenter_multi_control_3.png)

1. Skapa **mc1** och **mc2** genom att duplicera operatorn i meddelandecentret som anges som standard (**mc**). Mer information om hur du skapar operatorer finns i [det här avsnittet](../../platform/using/access-management-operators.md).

   ![](assets/messagecenter_multi_control_4.png)

   >[!NOTE]
   >
   >**mc1** och **mc2** operatorn måste ha **[!UICONTROL Message Center execution]** och de har inte åtkomst till Adobe Campaign klientkonsol. En operator måste alltid länkas till en säkerhetszon. Mer information om detta finns i [det här avsnittet](../../installation/using/security-zones.md).

1. För varje operator ska du kontrollera **[!UICONTROL Restrict to information found in sub-folders of]** och välj lämplig mapp (**Mapp 1** för **mc1** operator och **Mapp 2** för **mc2** -operator).

   ![](assets/messagecenter_multi_control_5.png)

1. Ge varje operator läs- och skrivbehörighet för sin mapp. Om du vill göra det högerklickar du på mappen och väljer **[!UICONTROL Properties]** . Välj sedan **[!UICONTROL Security]** tabba och lägg till den relevanta operatorn (**mc1** for **Mapp 1** och **mc2** for **Mapp 2**). Se till att **[!UICONTROL Read/Write data]** är markerade.

   ![](assets/messagecenter_multi_control_6.png)
