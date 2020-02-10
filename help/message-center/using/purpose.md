---
title: Syfte
seo-title: Syfte
description: Syfte
seo-description: null
page-status-flag: never-activated
uuid: 4452d839-318a-49d8-8abb-4ba04c803e9f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: use-case
discoiquuid: 7b8ab9d6-e47e-46d8-99df-da793486654c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Syfte{#purpose}

Syftet med det här användningsexemplet är att lägga till e-postbilagor direkt till utgående utskick.

I det här scenariot får vi se hur vi skickar transaktionsmeddelanden med personliga eller personliga bilagor. Bifogade filer överförs inte i förväg till Transactional Messaging-servern utan genereras i farten.

När du hämtar kundinteraktioner eller kundinformation kan du behöva skicka tillbaka informationen till kunden i slutet av processen, till exempel i en PDF-fil som bifogas till ett e-postmeddelande. Här är de allmänna stegen i det här scenariot.

1. Kunden kommer till webbplatsen och hittar en produkt som han/hon vill köpa.
1. Kunden väljer produkten och anpassar några alternativ.
1. Kunden slutför transaktionen.
1. Ett e-postmeddelande skickas till kunden som bekräftar transaktionen. Vi vill inte skicka ut PII-filer (personligt identifierbar information) i e-postmeddelandet så att vi genererar en säker PDF-fil och bifogar den i e-postmeddelandet.
1. Kunden får e-postmeddelandet och den bifogade filen som innehåller alla data som behövs.

I det här scenariot är de bifogade filerna inte färdiga utan läggs till direkt i de utgående e-postmeddelandena. På så sätt kan du också anpassa innehållet i den bifogade filen. Om den bifogade filen dessutom är kopplad till en transaktion (som i exemplet ovan) kan du behöva den för att innehålla dynamiska data som genereras under kundprocessen. Genom att bifoga PDF-filer på det här sättet optimeras även säkerheten eftersom du kan kryptera dem och skicka dem via HTTPS.
