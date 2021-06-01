---
product: campaign
title: Nätverk, databaser och SSL/TLS
description: Läs mer om de effektivaste strategierna för nätverk, databaser och SSL/TLS-konfigurationer.
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 2a66dfaa-7fff-48de-bdd4-62f3ebfbab19
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 9%

---

# Nätverk, databaser och SSL/TLS {#network-database}

## Nätverkskonfiguration

Det är viktigt att kontrollera när du distribuerar en lokal typ av arkitektur [nätverkskonfigurationen](../../installation/using/network-configuration.md). Kontrollera att Tomcat-servern INTE är direkt tillgänglig utanför servern:

* Stäng Tomcat-porten (8080) på externa IP-adresser (måste fungera på localhost)
* Mappa inte standardporten för HTTP (80) till Tomcat (8080)

Använd en säker kanal när det är möjligt: POP3S istället för POP3 (eller POP3 över TLS).

## Databas

Du måste tillämpa de bästa säkerhetsrutinerna för din databasmotor.

## SSL-/TLS-konfiguration

Om du vill kontrollera certifikatet kan du använda openssl. Om du vill kontrollera aktiva ciphers kan du använda nmap:

```
#!/bin/sh
#
# usage: testSSL.sh remote.host.name [port]
#
REMHOST=$1
REMPORT=${2:-443}
 
echo |\
openssl s_client -connect ${REMHOST}:${REMPORT} -servername ${REMHOST} 2>&1 |\
sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' |\
openssl x509 -noout -subject -dates
   
nmap --script ssl-enum-ciphers -p ${REMPORT} ${REMHOST}
```

Du kan också använda ett [sslyze](https://github.com/nabla-c0d3/sslyze/releases)-python-skript som gör båda.

```
python sslyze.py --sslv2 --sslv3 --tlsv1 --reneg --resum --certinfo=basic --hide_rejected_ciphers --sni=SNI myserver.com
```
