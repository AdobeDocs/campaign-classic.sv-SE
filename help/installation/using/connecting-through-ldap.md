---
product: campaign
title: Ansluta via LDAP
description: 'Lär dig hur du använder LDAP för att logga in på Campaign '
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Ansluta via LDAP{#connecting-through-ldap}

![](../../assets/v7-only.svg)

## Konfigurera kampanj och LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP-konfigurationen är bara möjlig för lokala eller hybridinstallationer.

LDAP-konfigurationen utförs i distributionsguiden. Alternativet **[!UICONTROL LDAP integration]** måste väljas under det första konfigurationssteget. Se [Distributionsguiden](../../installation/using/deploying-an-instance.md#deployment-wizard).

I fönstret kan du konfigurera identifieringen av Adobe Campaign-användare via den angivna LDAP-katalogen.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Ange adressen till LDAP-servern i fältet **[!UICONTROL LDAP server]**. Du kan lägga till portnumret. Som standard används porten 389.
* Välj autentiseringsmetod för användare i listrutan:

   * Krypterat lösenord (**md5**)

      Standardläge.

   * Lösenord för oformaterad text + SSL (**TLS**)

      Hela autentiseringsproceduren (inklusive lösenord) är krypterad. Den säkra porten 636 får inte användas i detta läge: Adobe Campaign växlar automatiskt till säkert läge.

      När du använder det här autentiseringsläget verifieras certifikatet i Linux av ett openLDAP-klientbibliotek. Vi rekommenderar att du använder ett giltigt SSL-certifikat så att autentiseringsproceduren krypteras. I annat fall kommer informationen att vara i oformaterad text.

      Certifikatet verifieras också i Windows.

   * Windows NT LAN Manager (**NTLM**)

      Windows-autentisering som tillhandahålls. **[!UICONTROL Unique identifier]** används endast för domännamnet.

   * Autentisering av distribuerat lösenord (**DPA**)

      Windows-autentisering som tillhandahålls. **[!UICONTROL Unique identifier]** används endast för domännamnet (domain.com).

   * Lösenord för oformaterad text

      Ingen kryptering (endast för användning i testfaser).

* Välj autentiseringsläge för användare: **[!UICONTROL Automatically compute the unique user identifier]** (se steg [Beräkning av unikt namn](#distinguished-name-calculation)) eller **[!UICONTROL Search the unique user identifier in the directory]** (se steg [Söka efter identifierare](#searching-for-identifiers)).

## Kompatibilitet {#compatibility}

Vilka system som är kompatibla beror på den valda autentiseringsmekanismen. Följande är en kompatibilitetsmatris för operativsystem och LDAP-servrar.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM och DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> normal text<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Beräkning av unikt namn {#distinguished-name-calculation}

Om du vill beräkna identifierarna för unikt namn (DN) kan du konfigurera beräkningssättet i nästa steg i distributionsguiden.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Ange användarens unika identifierare i katalogen (unikt namn - DN) i fältet **[!UICONTROL Distinguished Name]**.

   **[!UICONTROL (login)]** ersätts med identifieraren för operatorn Adobe Campaign.

   >[!CAUTION]
   >
   >Inställningen **[!UICONTROL dc]** måste vara i gemener.

* Välj alternativet **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** om du vill synkronisera gruppen och användarassociationerna i LDAP-katalogen samt gruppen och användarassociationerna i Adobe Campaign.

   När du väljer det här alternativet aktiveras **[!UICONTROL Application level DN used for the search]** och **[!UICONTROL Password of the application login]**.

   Om du fyller i dessa två fält kommer Adobe Campaign att ansluta till LDAP-servern med sin egen inloggning och lösenord. Om de är tomma ansluter Adobe Campaign anonymt till servern.

## Söker efter identifierare {#searching-for-identifiers}

Om du väljer att söka efter en identifierare kan du konfigurera sökningen i distributionsguiden.

* I fälten **[!UICONTROL Application level DN used for the search]** och **[!UICONTROL Password of the application login]** anger du den identifierare och det lösenord som Adobe Campaign ska ansluta till för att söka efter identifieraren. Om de är tomma ansluter Adobe Campaign anonymt till servern.
* Ange fälten **[!UICONTROL Base identifier]** och **[!UICONTROL Search scope]** för att bestämma en delmängd av LDAP-katalogen som sökningen ska starta från.

   Välj önskat läge i listrutan:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      LDAP-katalogen genomsöks i sin helhet från en viss nivå.

   1. **[!UICONTROL Limited to the base]**.

      Alla attribut tas med i sökningen.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      Sökningen utförs på alla attribut i katalogen och börjar på den första nivån i attributet.

* I fältet **[!UICONTROL Filter]** kan du ange ett element som ska förfina sökningen.

## Konfigurera LDAP-auktoriseringar {#configuring-ldap-authorizations}

Fönstret visas när du väljer alternativet **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Du måste ange flera parametrar för att kunna hitta gruppen eller grupperna som användaren tillhör och deras motsvarande rättigheter, d.v.s.:

* fältet **[!UICONTROL Database identifier]**,
* fältet **[!UICONTROL Search scope]**,

   >[!NOTE]
   >
   >Om du har valt att söka efter det unika namnet kan du välja **[!UICONTROL Reuse the DN search parameters]** för att överföra de valda värdena för det unika namnet och sökomfånget från föregående skärm.

* fältet **[!UICONTROL Rights search filter]**, baserat på inloggningen och användarens unika namn,
* fältet **[!UICONTROL Attribute containing the group or authorization name]** för användaren,
* det **[!UICONTROL Association mask]**-fält som möjliggör extrahering av gruppnamnet i Adobe Campaign och tillhörande rättigheter. Du kan använda reguljära uttryck för att söka efter namnet.
* Välj **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** så att användaren automatiskt får åtkomstbehörighet för anslutningen.

Klicka på **[!UICONTROL Save]** för att slutföra konfigurationen av instansen.

## Hantera operatorer {#managing-operators}

När du har bekräftat konfigurationen måste du definiera vilka Adobe Campaign-operatorer som ska hanteras via LDAP-katalogen.

Om du vill använda LDAP-katalogen för att autentisera en operator redigerar du motsvarande profil och klickar på länken **[!UICONTROL Edit the access parameters]**. Välj alternativet **[!UICONTROL Use LDAP for authentication]**: Fältet **[!UICONTROL Password]** är nedtonat för den här operatorn.

![](assets/s_ncs_install_operator_in_ldap.png)

## Användningsfall {#use-cases}

I det här avsnittet finns några enkla användningsexempel som hjälper dig att uppnå de lämpligaste konfigurationerna baserat på dina behov.

1. En användare har skapats i LDAP-katalogen men inte i Adobe Campaign.

   Adobe Campaign kan konfigureras så att användaren kommer åt plattformen via sin LDAP-autentisering. Adobe Campaign måste kunna kontrollera giltigheten för ID/lösenord-kombinationen i LDAP-katalogen, så att operatorn kan skapas direkt i Adobe Campaign. Det gör du genom att markera alternativet **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**. I det här fallet måste även gruppsynkronisering konfigureras: **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**-alternativet måste vara markerat.

1. Användaren har skapats i Adobe Campaign men inte i LDAP-katalogen.

   De kommer inte att kunna logga in på Adobe Campaign.

1. Det finns en grupp i LDAP-katalogen som inte finns i Adobe Campaign.

   Den här gruppen kommer inte att skapas i Adobe Campaign. Du måste skapa gruppen och synkronisera grupperna för att aktivera en matchning via alternativet **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]**.

1. Det finns grupper i Adobe Campaign och LDAP-katalogen aktiveras efter händelsen: användargrupper i Adobe Campaign ersätts inte automatiskt med innehåll i LDAP-grupper. Om det bara finns en grupp i Adobe Campaign kan inga LDAP-användare läggas till förrän gruppen har skapats och synkroniserats i LDAP.

   Grupper skapas aldrig i farten, vare sig av Adobe Campaign eller LDAP. De måste skapas individuellt, både i Adobe Campaign och i LDAP-katalogen.

   Namnen på grupperna i LDAP-katalogen måste sammanfalla med namnen på Adobe Campaign-grupperna. Deras associationsmask definieras i det sista konfigurationssteget i distributionsguiden: Adobe Campaign_(.*), till exempel.
