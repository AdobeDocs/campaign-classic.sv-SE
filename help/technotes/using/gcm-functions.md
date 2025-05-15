---
product: campaign
title: Nya GCM-baserade funktioner
description: Nya GCM-baserade funktioner
feature: Technote
exl-id: 154dee7a-a1e9-40a2-bfa5-3641382d0574
source-git-commit: b6d64f66d287dba79be5eddec48ee852c2c7740c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# GCM-baserade funktioner {#new-functions}

För att förbättra säkerheten har AES-algoritmen (Advanced Encryption Standard) med CBC-läget (Cipher Block Chaining) för kryptografiska operationer tagits bort. Nya krypteringsfunktioner har införts. Dessa funktioner använder AES med Galois/Counter Mode (AES-GCM), vilket ger ett säkrare alternativ. Dessa funktioner är tillgängliga i JavaScript, JSP, SOAP API:er och XML-scheman, vilket gör att kunder kan gå över från CBC till GCM för kryptering och dekryptering.

I den här dokumentationen listas de nyligen introducerade AES-GCM-funktionerna och de CBC-baserade funktionerna som tas bort.

Nya funktioner:

* [API-funktionen EncryptString](#encryptString-api-xtk)
* [API-funktionen EncryptStringWithServerPassword](#EncryptStringWithServerPassword-api-xtk)
* [funktionen encryptString javascript](#encryptString-javascript)

Äldre funktioner som kan användas för GCM:

* [Funktionen DecryptString javascript](#decryptString-javascript)
* [JavaScript-funktionen DecryptPassword](#decryptPassword-javascript)

[Föråldrade funktioner](#depracated-functions)

## API-funktioner

### EncryptString {#encryptString-api-xtk}

Krypterar teckensträngen med instansnyckeln med AES-algoritmen med GCM-läget.

```
            String 
            encrypted = EncryptString (
            String       
            decrypted
            

      )
         
```

**Parametrar**: Dekrypterad text

**Returvärden**: krypterade

**Schema**: xtk:session

**Statisk**: Ja

## EncryptStringWithServerPassword {#EncryptStringWithServerPassword-api-xtk}

Krypterar teckensträngen med servernyckeln med hjälp av AES-algoritmen med GCM-läge.


```
            String 
            encrypted = EncryptStringWithServerPassword (
            String       
            decrypted
            

      )
         
```

**Parametrar**: Dekrypterad

**Returvärden**: krypterade

**Schema**: xtk:session

**Statisk**: Ja

## Javascript-funktioner

### encryptString() {#encryptString-javascript}

Krypterar en teckensträng med nyckeln för instansen eller någon annan nyckel.

```
            encryptString (str [, key
      ] [, useSalt ])
         
```

**Parametrar**:

* str: Den teckensträng som ska krypteras.
* nyckel: AES-krypteringsnyckeln kodas i bas 64: 256 bitar om nyckellängden är 32, 192 bitar om nyckellängden är 24, 128 bitar om nyckellängden är 16 eller om ingen nyckel anges.
* useSalt: Använd ett salt av data för att kryptera. Sant som standard.

**Returvärde**: Returnerar den krypterade teckensträngen.

**Anmärkningar**

Kryptering utförs enligt följande metod:

* Unicode-teckensträngen omvandlas till en UTF-8-sträng.
* En bock läggs till i utskriften i slutet.
* Strängen krypteras med AES-algoritmen i Galois/Counter Mode (GCM) med salt med en 12 byte initieringsvektor och 16 byte-tagg. Om ingen nyckel anges som parameter används instansnyckeln.
* Texten innehåller tagg- och initieringsvektorn.
* Det krypterade blocket konverteras sedan till bas 64.

Dekrypteringen utförs med funktionen dekrypptString.

**Funktioner**

Finns i:

* Innehållshantering
* Leveransegenskaper
* Leveransmeddelande
* Typologiregel
* Import
* JSSP
* SOAP
* WebApp
* Arbetsflöde

### decryptString() {#decryptString-javascript}

Dekrypterar en teckensträng med instansnyckeln eller någon annan tangent. Den här gamla funktionen kan användas med GCM. Den används inte för dekryptering av chiffertext som krypteras i AES-CBC-läge.

```
            decryptString (str [, key
      ] [, useSalt ])
         
```

**Parametrar**:

* str: Den teckensträng som ska dekrypteras.
* nyckel: AES-krypteringsnyckeln kodas i bas 64: 256 bitar om nyckellängden är 32, 192 bitar om nyckellängden är 24, 128 bitar om nyckellängden är 16 eller om ingen nyckel anges.
* useSalt: Använd ett salt av data för att dekryptera. Sant som standard.

**Returvärde**: Returnerar den dekrypterade teckensträngen.

**Varning**: Lösenord som lagras i databasen (alternativ/externa konton) kan inte längre dekrypteras med den här metoden. Använd [decryptPassword](#decryptPassword-javascript) för det.

### decryptPassword() {#decryptPassword-javascript}

Dekrypterar ett lösenord som lagras i ett externt konto. Den här gamla funktionen kan användas med GCM. Den används inte för dekryptering av chiffertext som krypteras i AES-CBC-läge.

```
            decryptPassword (str)
         
```

**Parametrar**:

* str: Den teckensträng som ska dekrypteras.

**Returvärde**: Returnerar lösenord med oformaterad text.

**Anmärkningar**

Den här funktionen kan inte anropas i arbetsflöden, webbprogram, rapporter eller leveranser. Den kan anropas i JSSP- eller SOAP-samtalsimplementeringar. Exempel:

```
        function nms_extAccount_LogonToRemoteInstance(remoteInstanceUrl, login, encryptedPassword) {
        var cnx = null, sessionService = null;
        try
            {
                var cnx = new HttpSoapConnection(remoteInstanceUrl + '/nl/jsp/soaprouter.jsp', 'utf-8', 0);
                sessionService = new SoapService(cnx, 'xtk:session');
                sessionService.addMethod("Logon", "xtk:session#Logon",
                    ["token", "string", "login", "string", "password", "string", "parameters", "NLElement"],
                    ["sessionToken", "string", "sessionInfo", "NLElement", "securityToken", "string"]);
                return sessionService.Logon("", login, decryptPassword(encryptedPassword), <parameters/>);
            }
        catch( e ) {
        logError(e);
        }
        finally {
        if( sessionService ) sessionService.dispose();
        if( cnx ) cnx.dispose();
        }
        })
      
```

## Föråldrade funktioner {#depracated-functions}

Följande funktioner är helt inaktuella:

* cryptString
* Kryptera
* EncryptServerPassword
