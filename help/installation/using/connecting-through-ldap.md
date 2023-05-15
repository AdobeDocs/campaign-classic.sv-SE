---
product: campaign
title: Ansluta via LDAP
description: Lär dig hur du använder LDAP för att logga in på Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 1%

---

# Ansluta via LDAP{#connecting-through-ldap}

## Konfigurera kampanj och LDAP {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP-konfigurationen är bara möjlig för lokala eller hybridinstallationer.

LDAP-konfigurationen utförs i distributionsguiden. The **[!UICONTROL LDAP integration]** Du måste välja alternativ under det första konfigurationssteget. Se [Distributionsguide](../../installation/using/deploying-an-instance.md#deployment-wizard).

I fönstret kan du konfigurera identifieringen av Adobe Campaign-användare via den angivna LDAP-katalogen.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* Ange adressen till LDAP-servern i **[!UICONTROL LDAP server]** fält. Du kan lägga till portnumret. Som standard används porten 389.
* Välj autentiseringsmetod för användare i listrutan:

   * Krypterat lösenord (**md5**)

      Standardläge.

   * Lösenord för oformaterad text + SSL (**TLS**)

      Hela autentiseringsproceduren (inklusive lösenord) är krypterad. Den säkra porten 636 får inte användas i detta läge: Adobe Campaign växlar automatiskt till säkert läge.

      När du använder det här autentiseringsläget verifieras certifikatet i Linux av ett openLDAP-klientbibliotek. Vi rekommenderar att du använder ett giltigt SSL-certifikat så att autentiseringsproceduren krypteras. I annat fall kommer informationen att vara i oformaterad text.

      Certifikatet verifieras också i Windows.

   * Windows NT LAN Manager (**NTLM**)

      Windows-autentisering som tillhandahålls. The **[!UICONTROL Unique identifier]** används endast för domännamnet.

   * Autentisering av distribuerat lösenord (**DPA**)

      Windows-autentisering som tillhandahålls. The **[!UICONTROL Unique identifier]** används endast för domännamnet (domain.com).

   * Lösenord för oformaterad text

      Ingen kryptering (endast för användning i testfaser).

* Välj autentiseringsläge för användare: **[!UICONTROL Automatically compute the unique user identifier]** (se steg [Beräkning av unikt namn](#distinguished-name-calculation)) eller **[!UICONTROL Search the unique user identifier in the directory]** (se steg [Söker efter identifierare](#searching-for-identifiers)).

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

* Ange användarens unika identifierare i katalogen (unikt namn - DN) i dialogrutan **[!UICONTROL Distinguished Name]** fält.

   **[!UICONTROL (login)]** ersätts med identifieraren för operatorn Adobe Campaign.

   >[!CAUTION]
   >
   >The **[!UICONTROL dc]** inställningen måste vara i gemener.

* Välj alternativet **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** för att synkronisera gruppen och användarassociationerna i LDAP-katalogen samt gruppen och användarassociationerna i Adobe Campaign.

   När du väljer det här alternativet visas **[!UICONTROL Application level DN used for the search]** och **[!UICONTROL Password of the application login]** är aktiverade.

   Om du fyller i dessa två fält kommer Adobe Campaign att ansluta till LDAP-servern med sin egen inloggning och lösenord. Om de är tomma ansluter Adobe Campaign anonymt till servern.

## Söker efter identifierare {#searching-for-identifiers}

Om du väljer att söka efter en identifierare kan du konfigurera sökningen i distributionsguiden.

* I **[!UICONTROL Application level DN used for the search]** och **[!UICONTROL Password of the application login]** anger du den identifierare och det lösenord som Adobe Campaign ska ansluta till för att söka efter identifieraren. Om de är tomma ansluter Adobe Campaign anonymt till servern.
* Ange **[!UICONTROL Base identifier]** och **[!UICONTROL Search scope]** fält för att fastställa en deluppsättning av LDAP-katalogen att starta sökningen från.

   Välj önskat läge i listrutan:

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      LDAP-katalogen genomsöks i sin helhet från en viss nivå.

   1. **[!UICONTROL Limited to the base]**.

      Alla attribut tas med i sökningen.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      Sökningen utförs på alla attribut i katalogen och börjar på den första nivån i attributet.

* The **[!UICONTROL Filter]** I kan du ange ett element för att förfina sökningen.

## Konfigurera LDAP-auktoriseringar {#configuring-ldap-authorizations}

Det här fönstret visas när du väljer **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** alternativ.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

Du måste ange flera parametrar för att kunna hitta gruppen eller grupperna som användaren tillhör och deras motsvarande rättigheter, d.v.s.:

* den **[!UICONTROL Database identifier]** fält,
* den **[!UICONTROL Search scope]** fält,

   >[!NOTE]
   >
   >Om du har valt att söka efter det unika namnet kan du välja **[!UICONTROL Reuse the DN search parameters]** för att överföra de valda värdena för det unika namnet och sökomfånget från föregående skärm.

* den **[!UICONTROL Rights search filter]** fält, baserat på inloggning och användarens särskiljande namn,
* den **[!UICONTROL Attribute containing the group or authorization name]** fält som rör användaren,
* den **[!UICONTROL Association mask]** fält som gör det möjligt att extrahera gruppnamnet i Adobe Campaign och tillhörande rättigheter. Du kan använda reguljära uttryck för att söka efter namnet.
* Välj **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** så att användaren automatiskt får åtkomsträttigheter vid anslutningen.

Klicka **[!UICONTROL Save]** för att slutföra konfigurationen av instansen.

## Hantera operatorer {#managing-operators}

När du har bekräftat konfigurationen måste du definiera vilka Adobe Campaign-operatorer som ska hanteras via LDAP-katalogen.

Om du vill använda LDAP-katalogen för att autentisera en operator redigerar du motsvarande profil och klickar på **[!UICONTROL Edit the access parameters]** länk. Välj **[!UICONTROL Use LDAP for authentication]** alternativ: The **[!UICONTROL Password]** fältet är nedtonat för den här operatorn.

![](assets/s_ncs_install_operator_in_ldap.png)

## Användningsfall {#use-cases}

I det här avsnittet finns några enkla användningsexempel som hjälper dig att uppnå de lämpligaste konfigurationerna baserat på dina behov.

1. En användare har skapats i LDAP-katalogen men inte i Adobe Campaign.

   Adobe Campaign kan konfigureras så att användaren kommer åt plattformen via sin LDAP-autentisering. Adobe Campaign måste kunna kontrollera giltigheten för ID/lösenord-kombinationen i LDAP-katalogen, så att operatorn kan skapas direkt i Adobe Campaign. Om du vill göra det går du till **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** alternativ. I det här fallet måste även gruppsynkronisering konfigureras: den **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** måste vara markerat.

1. Användaren har skapats i Adobe Campaign men inte i LDAP-katalogen.

   De kommer inte att kunna logga in på Adobe Campaign.

1. Det finns en grupp i LDAP-katalogen som inte finns i Adobe Campaign.

   Den här gruppen kommer inte att skapas i Adobe Campaign. Du måste skapa gruppen och synkronisera grupperna för att aktivera en matchning via **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** alternativ.

1. Det finns grupper i Adobe Campaign och LDAP-katalogen aktiveras efter händelsen: användargrupper i Adobe Campaign ersätts inte automatiskt med innehåll i LDAP-grupper. Om det bara finns en grupp i Adobe Campaign kan inga LDAP-användare läggas till förrän gruppen har skapats och synkroniserats i LDAP.

   Grupper skapas aldrig i farten, vare sig av Adobe Campaign eller LDAP. De måste skapas individuellt, både i Adobe Campaign och i LDAP-katalogen.

   Namnen på grupperna i LDAP-katalogen måste sammanfalla med namnen på Adobe Campaign-grupperna. Deras associationsmask definieras i det sista konfigurationssteget i distributionsguiden: Adobe Campaign_(.&#42;), till exempel.
