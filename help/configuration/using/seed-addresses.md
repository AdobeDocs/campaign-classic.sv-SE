---
title: Fröadresser
seo-title: Fröadresser
description: Fröadresser
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# Fröadresser{#seed-addresses}

Om mottagartabellen är en anpassad tabell krävs ytterligare konfigurationer. Schemat måste utökas **[!UICONTROL nms:seedMember]** . Ytterligare en flik läggs till i startadresserna för att definiera lämpliga fält, vilket visas nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Mer information om hur du använder dirigerade adresser finns i [det här avsnittet](../../delivery/using/about-seed-addresses.md).

## Implementering {#implementation}

Schemat **nms:seedMember** och det länkade formulär som visas i rutan ska utökas för kundkonfiguration, så att alla nödvändiga fält refereras. Schemadefinitionen innehåller kommentarer som beskriver dess konfigurationsläge.

Definition av det utökade schemat för mottagartabellen:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Använd följande steg:

1. Skapa ett tillägg till **schemat nms:seedMember** . Mer information finns i [Utöka ett schema](../../configuration/using/extending-a-schema.md).
1. I det nya tillägget lägger du till ett nytt element i roten för **[!UICONTROL seedMember]** med följande parametrar:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Det här elementet måste innehålla de fält som krävs för att exportera kampanjer. Dessa fält ska ha samma namn som motsvarande fält i det externa schemat. Om schemat till exempel är **[!UICONTROL cus:person]** bör **[!UICONTROL nms:seedMember]** schemat utökas enligt följande:

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >Utbyggnaden av **nms:seedMember** -schemat måste överensstämma med strukturen för en kampanj och en leverans i Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Under tillägget måste du ange ett **SQL-namn (@sqlname)** för fältet&quot;email&quot;. SQL-namnet måste skilja sig från &#39;sEmail&#39; som är reserverat för mottagarschemat.
   >    * Du måste uppdatera databasstrukturen med det schema som skapas när du utökar **nms:seedMember**.
   >    * I tillägget **nms:seedMember** måste fältet som innehåller e-postadressen ha **namn=&quot;email&quot;** som attribut. SQL-namnet måste skilja sig från sEmail som redan används för mottagarschemat. Det här attributet måste deklareras omedelbart under **`<element name="custom_cus_person" />`** elementet.


1. Ändra formuläret **[!UICONTROL seedMember]** så att det definierar en ny flik för&quot;intern mottagare&quot; i **[!UICONTROL Seed addresses]** fönstret. Mer information finns i [Formulärstruktur](../../configuration/using/form-structure.md).

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Om inga attribut för startadressen anges ersätter Adobe Campaign automatiskt profilerna: kommer de att anges automatiskt under personaliseringen med data från en befintlig profil.
