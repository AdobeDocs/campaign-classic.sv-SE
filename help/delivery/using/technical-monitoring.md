---
title: Teknisk övervakning
seo-title: Teknisk övervakning
description: Teknisk övervakning
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# Teknisk övervakning{#technical-monitoring}

## Övervakningsrapport för teknisk leverans {#technical-deliverability-monitoring}

Den tekniska leveransövervakningsrapporten uppdateras dagligen och är tillgänglig genom att gå till **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** och klicka på **[!UICONTROL Technical monitoring]** länken på Adobe Campaign- **[!UICONTROL Home]** fliken. Det innehåller ett antal kvalitetsindikatorer för er plattform.

Dessa indikatorer uppdateras dagligen kl. 9.00.

>[!NOTE]
>
>Dessutom kan du få en daglig rapport via e-post till en angiven adress. Meddela den begärda e-postadressen via e-post eller via Adobe Campaign Extranet.

![](assets/s_tn_del_monitoring.png)

Följande indikatorer används i rapporten:

* **[!UICONTROL Reverse DNS]** : Adobe Campaign kontrollerar om en omvänd DNS anges för en IP-adress och att detta korrekt pekar tillbaka till IP-adressen.

* **[!UICONTROL SPF]** (Sender Policy Framework): En autentiseringsmekanism som gör det möjligt för Internet-leverantörer och postlådeleverantörer att kontrollera om e-postavsändaren är auktoriserad på den sändande domänen.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** : En tjänst som utvecklats av Yahoo och som är avsedd att certifiera identiteten för en e-postavsändare.

* **[!UICONTROL IP and RBL domain]** (Blackutjämlista i realtid): En lista över IP-adresser och domäner som har flaggats av blocklistorganisationer för dåligt sändande rykte. Listorna hanteras av särskilda organisationer som Spamhaus, Spampolis, SURBL/URIBL osv. Adobe Campaign bearbetar för närvarande kontroller mot RBL:er som har en betydande påverkan på leveransen. Dessa URL:er återspeglar avsändarens anseende och kan refereras av Internet-leverantörer innan de godkänner att få dina e-postmeddelanden.

* **[!UICONTROL SNDS]** (Data Services för smarta nätverk): En [Windows Live Hotmail-tjänst mot skräppost](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail är den enda Internet-leverantör som tillhandahåller den här typen av information. Benchmark-poängen är ett grönt filterresultat, en klagofrekvens på mindre än 0,1 % och noll skräppostsvällningar.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
