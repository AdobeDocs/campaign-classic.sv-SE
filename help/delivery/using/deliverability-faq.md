---
product: campaign
title: Viktiga punkter vid hantering av slutprodukter i Adobe Campaign Classic
description: Lär dig viktiga saker när du hanterar slutprodukter i Adobe Campaign
badge-v8: label="Gäller även för v8" type="Positive" tooltip="Gäller även Campaign v8"
feature: Deliverability, Troubleshooting
role: User
exl-id: f94897c1-b44c-4100-ac50-a89b13fa6f2f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---

# Felsökning av slutprodukter{#deliverability-faq}

Har du något leveransproblem? Du kan hitta lösningen här.

## MX-regelfel {#mx-rule-error}

**Vad betyder felmeddelandet &quot;kvoter har uppfyllts&quot;?**

Det här meddelandet anger att du har nått kvotgränsen för en viss MX och att du måste vänta för att kunna skicka ytterligare ett e-postmeddelande till den här providern.

I Adobe Campaign finns en konfiguration för hur många e-postmeddelanden som kan skickas per timme. Denna konfiguration måste användas med vaksamhet, eftersom det nummer som definieras i instansen avser antalet anslutningar som görs med Internet-leverantören och inte antalet e-postmeddelanden som faktiskt skickas.

Det innebär att en anslutning kan använda en MX-regel utan att skicka ett e-postmeddelande. I det här fallet måste en konfiguration med en IP-adress eller en domän med dåligt rykte försöka med flera anslutningar innan ett e-postmeddelande skickas. För varje försök används ett meddelande per timkredit. Resultatet av marknadsföringskampanjen kommer att få en betydande effekt.

Därför är&quot;kvoter uppfyllda&quot; inte bara ett konfigurationsproblem, utan kan även kopplas till rykte. Det är viktigt att analysera felmeddelanden i [SMTP-loggen](../../production/using/monitoring-processes.md#smtp-errors-per-domain).

Mer information om MX-konfiguration finns i [det här avsnittet](../../installation/using/email-deliverability.md#mx-configuration).

## Samma felmeddelande för en Internet-leverantör {#same-error-for-an-isp}

**Varför får jag alltid samma felmeddelande för en viss Internet-leverantör?**

Om du alltid får samma felmeddelande för en Internet-leverantör, kan din e-postadress eller IP-adress ha identifierats som defekt av Internet-leverantören. Utför följande rekommendationer:
* Kontrollera om du får ett stort antal fel som är kopplade till obefintliga e-postadresser (**Okänd användare**).
* Uppdatera dina prenumerationsformulär för att upptäcka eventuella fel i de angivna domännamnen (till exempel: gmaul.com eller yaho.com).
* Om du märker fel som anger att dina meddelanden har deklarerats som skräppost, eller att dina meddelanden alltid är blockerade, kan du försöka utesluta mottagare som inte har öppnat eller klickat i något av dina meddelanden de senaste 12 månaderna från målet.

Om problemet kvarstår kontaktar du den kommersiella tjänsten eller leveransplatsen, [Adobe kundtjänst](https://helpx.adobe.com/se/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Blockeringslista kontra karantän {#denylist-versus-quarantine}

* **Vad är skillnaden mellan en e-postadress på blockeringslista och en e-postadress i karantän?**

   * Statusen **[!UICONTROL Denylisted]** är ett resultat av en feedbackloop (när en person rapporterar ett meddelande som skräppost).

   * Statusen **[!UICONTROL Quarantined]** är ett resultat av ett mjukt eller hårt studsande.

  Mer information finns i [det här avsnittet](understanding-quarantine-management.md#quarantine-vs-denylist).

* **Vad betyder de olika karantänfelen?**

  Här är tio möjliga orsaker: inte definierad, okänd användare, ogiltig domän, avslagen på blockeringslista, fel ignorerad, ej tillgänglig, kontot inaktiverat, postlådan full, inte ansluten.

  Mer information finns i [Om karantänhantering](understanding-quarantine-management.md).

## Tar bort från blockeringslista {#remove-from-denylist}

* **En av mina mottagare lades till i blockeringslista av misstag. Hur tar jag bort dem från denyisten så att jag kan börja skicka dem igen?**

   * Gå till **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Ange värdet för fältet **[!UICONTROL Status]** till **[!UICONTROL Valid]** i informationen för motsvarande post.
   * Spara posten.

* **Hur kan jag ta reda på om en av mina IP-adresser finns på blockeringslista? Hur tar jag bort mina IP-adresser från en blockeringslista?**

  Om du vill kontrollera om din IP-adress finns på blockeringslista kan du verifiera den på olika webbplatser, till exempel:
   * [MX-verktygslåda](https://mxtoolbox.com/)
   * [Vad är min IP-adress](https://whatismyipaddress.com)

  I allmänhet returnerar resultatet av IP-adresskontrollen en lista som innehåller information om blockeringslista och även namnet på den webbplats som nekade IP-adressen.

  Genom att klicka på motsvarande länk kan du komma åt webbplatsinformationen. Sedan kan du begära att din webbplats tas bort från den webbplats som lade till IP-adressen till blockeringslista.

  >[!NOTE]
  >
  >Borttagningsprocessen kan variera beroende på webbplatsen. Vissa webbplatser kräver att du skapar ett konto, medan andra bara behöver du ange IP-adressen.
