---
product: campaign
title: Dirigerade adresser
description: Dirigerade adresser
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 6%

---

# Dirigerade adresser{#seed-addresses}

![](../../assets/common.svg)

Om mottagartabellen är en anpassad tabell krävs ytterligare konfigurationer. The **[!UICONTROL nms:seedMember]** schemat måste utökas. Ytterligare en flik läggs till i startadresserna för att definiera lämpliga fält, vilket visas nedan:

![](assets/s_ncs_user_seedlist_new_tab.png)

Mer information om hur du använder dirigerade adresser finns i [det här avsnittet](../../delivery/using/about-seed-addresses.md).

## Implementering {#implementation}

The **nms:seedMember** schemat och det länkade formulär som kommer ut i lådan ska utökas för kundkonfiguration, så att alla nödvändiga fält refereras. Schemadefinitionen innehåller kommentarer som beskriver dess konfigurationsläge.

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

1. Skapa ett tillägg till **nms:seedMember** schema. Mer information om detta finns i [det här avsnittet](../../configuration/using/extending-a-schema.md).
1. I det nya tillägget lägger du till ett nytt element i roten för **[!UICONTROL seedMember]** med följande parametrar:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Det här elementet måste innehålla de fält som krävs för att exportera kampanjer. Dessa fält ska ha samma namn som motsvarande fält i det externa schemat. Om schemat till exempel är **[!UICONTROL cus:person]** , **[!UICONTROL nms:seedMember]** schemat ska utökas enligt följande:

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
   >Utbyggnaden av **nms:seedMember** schemat måste överensstämma med strukturerna för en kampanj och en leverans i Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Under tillägget måste du ange en **SQL-namn (@sqlname)** för fältet &#39;email&#39;. SQL-namnet måste skilja sig från &#39;sEmail&#39; som är reserverat för mottagarschemat.
   >    * Du måste uppdatera databasstrukturen med det schema som skapades när du utökar **nms:seedMember**.
   >    * I **nms:seedMember** tillägg måste fältet som innehåller e-postadressen ha **name=&quot;email&quot;** som ett attribut. SQL-namnet måste skilja sig från sEmail som redan används för mottagarschemat. Detta attribut måste omedelbart deklareras under **`<element name="custom_cus_person" />`** -element.


1. Ändra **[!UICONTROL seedMember]** formulär för att definiera en ny&quot;intern mottagare&quot;-flik i **[!UICONTROL Seed addresses]** -fönstret. Mer information finns på [den här sidan](../../configuration/using/form-structure.md).

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
