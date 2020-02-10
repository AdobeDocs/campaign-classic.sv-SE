---
title: Ansluta via LDAP
seo-title: Ansluta via LDAP
description: Ansluta via LDAP
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# Ansluta via LDAP{#connecting-through-ldap}

## Konfigurera kampanj och LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP-konfigurationen är bara möjlig för lokala eller hybridinstallationer.

LDAP-konfigurationen utförs i distributionsguiden. Du måste välja **[!UICONTROL LDAP integration]** alternativet under det första konfigurationssteget. Se [Distributionsguiden](../../installation/using/deploying-an-instance.md#deployment-wizard).

I fönstret kan du konfigurera identifiering av Adobe Campaign-användare via den angivna LDAP-katalogen.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Ange adressen till LDAP-servern i **[!UICONTROL LDAP server]** fältet. Du kan lägga till portnumret. Som standard används porten 389.
* Välj autentiseringsmetod för användare i listrutan:

   * Krypterat lösenord (**md5**)

      Standardläge.

   * Lösenord för oformaterad text + SSL (**TLS**)

      Hela autentiseringsproceduren (inklusive lösenord) är krypterad. Den säkra porten 636 får inte användas i detta läge: Adobe Campaign växlar automatiskt till säkert läge.

      När du använder det här autentiseringsläget verifieras certifikatet i Linux av ett openLDAP-klientbibliotek. Vi rekommenderar att du använder ett giltigt SSL-certifikat så att autentiseringsproceduren krypteras. I annat fall kommer informationen att vara i oformaterad text.

      Certifikatet verifieras också i Windows.

   * Windows NT LAN Manager (**NTLM**)

      Windows-autentisering som tillhandahålls. Det **[!UICONTROL Unique identifier]** används endast som domännamn.

   * Distribuerad lösenordsautentisering (**DPA**)

      Windows-autentisering som tillhandahålls. Den **[!UICONTROL Unique identifier]** används endast som domännamn (domain.com).

   * Lösenord för oformaterad text

      Ingen kryptering (endast för användning i testfaser).

* Välj autentiseringsläge för användare: **[!UICONTROL Automatically compute the unique user identifier]** (se [beräkning](#distinguished-name-calculation)av unikt namn i steg) eller **[!UICONTROL Search the unique user identifier in the directory]** (se [Söka efter identifierare](#searching-for-identifiers)i steg).

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
   <td> oformaterad text<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Beräkning av unikt namn {#distinguished-name-calculation}

Om du vill beräkna identifierarna för unikt namn (DN) kan du konfigurera beräkningssättet i nästa steg i distributionsguiden.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* Ange användarens unika identifierare i katalogen (unikt namn - DN) i **[!UICONTROL Distinguished Name]** fältet.

   **[!UICONTROL (login)]** ersätts med identifieraren för Adobe Campaign-operatorn.

   >[!CAUTION]
   >
   >Inställningen måste vara i gemener **[!UICONTROL dc]** .

* Välj alternativet **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** om du vill synkronisera gruppen och användarassociationerna i LDAP-katalogen samt gruppen och användarassociationerna i Adobe Campaign.

   När du väljer det här alternativet aktiveras **[!UICONTROL Application level DN used for the search]** och **[!UICONTROL Password of the application login]** .

   Om du fyller i dessa två fält kommer Adobe Campaign att ansluta till LDAP-servern med sin egen inloggning och sina egna lösenord. Om de är tomma ansluter Adobe Campaign anonymt till servern.

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

* I **[!UICONTROL Filter]** fältet kan du ange ett element för att förfina sökningen.

## Konfigurera LDAP-auktoriseringar {#configuring-ldap-authorizations}

Det här fönstret visas när du väljer **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** alternativet.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Du måste ange flera parametrar för att kunna hitta gruppen eller grupperna som användaren tillhör och deras motsvarande rättigheter, d.v.s.:

* fältet **[!UICONTROL Database identifier]** ,
* fältet **[!UICONTROL Search scope]** ,

   >[!NOTE]
   >
   >Om du har valt att söka efter det unika namnet kan du välja **[!UICONTROL Reuse the DN search parameters]** att överföra de valda värdena för det unika namnet och sökomfånget från föregående skärm.

* fältet, **[!UICONTROL Rights search filter]** baserat på inloggningen och användarens särskiljande namn,
* det **[!UICONTROL Attribute containing the group or authorization name]** fält som rör användaren,
* det **[!UICONTROL Association mask]** fält som gör det möjligt att extrahera gruppnamnet i Adobe Campaign och tillhörande rättigheter. Du kan använda reguljära uttryck för att söka efter namnet.
* Välj **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** så att användaren automatiskt får åtkomstbehörighet för anslutningen.

Klicka **[!UICONTROL Save]** för att slutföra konfigurationen av instansen.

## Hantera operatorer {#managing-operators}

När du har bekräftat konfigurationen måste du definiera vilka Adobe Campaign-operatorer som ska hanteras via LDAP-katalogen.

Om du vill använda LDAP-katalogen för att autentisera en operator redigerar du motsvarande profil och klickar på **[!UICONTROL Edit the access parameters]** länken. Välj **[!UICONTROL Use LDAP for authentication]** alternativet: Fältet **[!UICONTROL Password]** är nedtonat för den här operatorn.

![](assets/s_ncs_install_operator_in_ldap.png)

## Användningsexempel {#use-cases}

I det här avsnittet finns några enkla användningsexempel som hjälper dig att uppnå de lämpligaste konfigurationerna baserat på dina behov.

1. En användare har skapats i LDAP-katalogen men inte i Adobe Campaign.

   Adobe Campaign kan konfigureras så att användaren får åtkomst till plattformen via sin LDAP-autentisering. Adobe Campaign måste kunna kontrollera giltigheten för ID/lösenord-kombinationen i LDAP-katalogen, så att operatorn kan skapas direkt i Adobe Campaign. Markera **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** alternativet om du vill göra det. I det här fallet måste även gruppsynkronisering konfigureras: du måste välja alternativet **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** .

1. Användaren har skapats i Adobe Campaign men inte i LDAP-katalogen.

   De kommer inte att kunna logga in på Adobe Campaign.

1. Det finns en grupp i LDAP-katalogen som inte finns i Adobe Campaign.

   Den här gruppen kommer inte att skapas i Adobe Campaign. Du måste skapa gruppen och synkronisera grupperna för att aktivera en matchning via **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** alternativet.

1. Det finns grupper i Adobe Campaign och LDAP-katalogen aktiveras efter händelsen: användargrupper i Adobe Campaign ersätts inte automatiskt med innehåll i LDAP-grupper. Om det bara finns en grupp i Adobe Campaign kan inga LDAP-användare läggas till i gruppen förrän gruppen har skapats och synkroniserats i LDAP.

   Grupper skapas aldrig i farten, vare sig det är Adobe Campaign eller LDAP. De måste skapas individuellt, både i Adobe Campaign och i LDAP-katalogen.

   Namnen på grupperna i LDAP-katalogen måste sammanfalla med namnen på Adobe Campaign-grupperna. Deras associationsmask definieras i det sista konfigurationssteget i distributionsguiden: Adobe Campaign_(.*), till exempel.

