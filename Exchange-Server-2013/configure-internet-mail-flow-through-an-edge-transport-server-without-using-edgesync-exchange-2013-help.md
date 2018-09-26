---
title: 'Konfig. d. Internetnachrichtenfluss. über Edge-Transport-Server ohne EdgeSync'
TOCTitle: Konfigurieren der Internetnachrichtenflusses über einen Edge-Transport-Server ohne Verwendung von EdgeSync
ms:assetid: 6bb98d10-6f12-4b08-a58e-36375f605d65
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232082(v=EXCHG.150)
ms:contentKeyID: 61180470
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Internetnachrichtenflusses über einen Edge-Transport-Server ohne Verwendung von EdgeSync

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-01-23_

Es wird empfohlen, den Edge-Abonnementprozess zum Einrichten der Nachrichtenübermittlung zwischen der Exchange-Organisation und einem Edge Transport-Server zu verwenden. Allerdings kann es in bestimmten Situationen nicht möglich sein, den Edge-Transport-Server unter Verwendung des Edge-Abonnementprozesses für die Exchange-Organisation zu abonnieren. Um die Nachrichtenübermittlung zwischen der Exchange-Organisation und einem Edge-Transport-Server manuell einzurichten, müssen Sie die Sende- und Empfangsconnectors auf dem Edge-Transport-Server und den Hub-Transport-Servern in der Exchange-Organisation erstellen und konfigurieren.

## Bevor Sie beginnen

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Sendeconnectors", "Sendeconnectors - Edge-Transport" und "Empfangsconnectors - Edge-Transport" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Dieses Verfahren verwendet Standardauthentifizierung über TLS (Transport Layer Security), um Verschlüsselung und Authentifizierung zur Verfügung zu stellen. Wenn Sie Standardauthentifizierung über TLS verwenden, muss auf dem empfangenden Server ein X.509-SSL-Zertifikat (Secure Sockets Layer) installiert sein. Der für den Empfangsconnector konfigurierte vollqualifizierten Domänenname (Fully Qualified Domain Name, FQDN) muss dem FQDN des SSL-Serverzertifikats entsprechen. Standardmäßig ist der Wert des FQDN für den Empfangsconnector der FQDN des Servers, der den Empfangsconnector enthält.

  - Sie können auch die Authentifizierungsmethode "Extern gesichert" verwenden. Allerdings wird in diesem Fall die Kommunikation zwischen dem Edge-Transport-Server und dem Postfachserver von Exchange weder authentifiziert noch verschlüsselt. Es wird empfohlen, die extern gesicherte Authentifizierungsmethode nur zu verwenden, wenn eine zusätzliche Verschlüsselungsmethode zum Einsatz kommt. Die Verschlüsselungsmethode kann eine IPsec-Zuordnung (Internet Protocol Security) oder ein VPN (Virtual Private Network, virtuelles privates Netzwerk) sein.

  - Der Edge-Transport-Server ist in der Regel *multihomed*. Das bedeutet, dass der Edge-Transport-Server über Netzwerkadapter verfügt, die mit mehreren Netzwerksegmenten verbunden sind. Jeder dieser Netzwerkadapter verfügt über eine eindeutige IP-Konfiguration. Der Netzwerkadapter, der mit dem externen oder öffentlichen Netzwerksegment verbunden ist, sollte so konfiguriert sein, dass er einen öffentlichen DNS-Server (Domain Name System) für die Namensauflösung verwendet. Auf diese Weise kann der Server SMTP-Domänennamen in MX-Ressourceneinträge auflösen und Nachrichten an das Internet routen. Der Netzwerkadapter, der mit dem internen oder privaten Netzwerksegment verbunden ist, sollte so konfiguriert sein, dass er einen DNS-Server im Umkreisnetzwerk verwendet oder über eine Hosts-Datei verfügt.

  - Sie müssen ein Benutzerkonto in Active Directory erstellen und und das Konto der universellen Sicherheitsgruppe auf dem Exchange Server-Computer hinzufügen. Dieses Konto wird vom Sendeconnector auf dem Edge-Transport-Server für die Authentifizierung gegenüber dem Postfachserver in der Exchange-Organisation verwendet.
    

    > [!IMPORTANT]
    > Diesem Konto werden die Berechtigungen erteilt, die Servercomputern mit Exchange Server zugeordnet sind. Stellen Sie sicher, dass die Kontoanmeldeinformationen gesichert sind, um einen Missbrauch des Kontos zu verhindern. Sie können das Konto so konfigurieren, dass das Anmelden nur an bestimmten Computern zulässig ist.



## Verfahren für Edge-Transport-Server

Die folgenden Connectors müssen auf dem Edge-Transport-Server vorhanden sein:

  - Ein Sendeconnector, der für das Senden von Nachrichten in das Internet konfiguriert ist

  - Ein Sendeconnector, der für das Senden von Nachrichten an die Postfachserver in der Exchange-Organisation konfiguriert ist.

  - Ein Empfangsconnector, der so konfiguriert ist, dass er nur Nachrichten von den Postfachservern in der Exchange-Organisation empfängt.

  - Ein Empfangsconnector, der für das Annehmen von Nachrichten nur aus dem Internet konfiguriert ist

Standardmäßig wird bei der Installation der Edge-Transport-Serverrolle ein Empfangsconnector konfiguriert. Dieser Connector kann sowohl für eingehende Nachrichten aus dem Internet als auch für eingehende Nachrichten von den Postfachservern verwendet werden. Normalerweise konfiguriert der Edge-Abonnementprozess automatisch die richtigen Berechtigungen und Authentifizierungsmechanismen für den Standardempfangsconnector. Wenn Sie den Edge-Abonnementprozess nicht verwenden, wird empfohlen, den Standardempfangsconnector auf dem Edge-Transport-Server so zu ändern, dass er nur Nachrichten aus dem Internet annimmt. Anschließend sollten Sie einen Empfangsconnector auf dem Edge-Transport-Server erstellen, der so konfiguriert ist, dass er nur Nachrichten von internen Postfachservern annimmt.

Die folgenden Abschnitte führen Sie durch alle Konfigurationsschritte, die zur Vorbereitung des Edge-Transport-Servers für die Kommunikation mit der Exchange-Organisation erforderlich sind.


> [!NOTE]
> Sie können diese Schritte nur mit der Shell auf Edge-Transport-Servern ausführen.



## Schritt 1: Erstellen eines Sendeconnectors, der zum Senden von Nachrichten an das Internet konfiguriert ist

Dieser Sendeconnector erfordert die folgende Konfiguration:

  - **Name**   An Internet (oder ein anderer beschreibender Name)

  - **Verwendungstyp**   Internet

  - **Adressräume**   "\*" (alle Domänen)

  - **Netzwerkeinstellungen**   Verwenden von DNS MX-Datensätzen, um E-Mail-Nachrichten automatisch weiterzuleiten. Je nach Netzwerkkonfiguration können Sie E-Mail-Nachrichten auch über eine Smarthost weiterleiten. Der Smarthost leitet die E-Mail-Nachrichten dann an das Internet weiter.

Um einen Sendeconnector zu erstellen, der zum Senden von Nachrichten an das Internet konfiguriert ist, führen Sie den folgenden Befehl aus:

```powershell
    New-SendConnector -Name "To Internet" -AddressSpaces * -Usage Internet -DNSRoutingEnabled $true
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-SendConnector](https://technet.microsoft.com/de-de/library/aa998936\(v=exchg.150\)).

## Schritt 2: Erstellen eines Sendeconnectors, der zum Senden von Nachrichten an die Exchange-Organisation konfiguriert ist

Verwenden Sie das Cmdlet **New-SendConnector**, um einen Sendeconnector zu erstellen.


> [!NOTE]
> Vor dem Erstellen des Sendeconnectors müssen Sie zunächst den Befehl <STRONG>Get-Credential</STRONG> ausführen, um den Benutzernamen und das Kennwort, den bzw. das Sie verwenden, in einer temporären Variable zu speichern. Dies ist erforderlich, weil das Cmdlet <STRONG>New-SendConnector</STRONG> die Benutzeranmeldeinformationen nicht im Nur-Text-Format akzeptiert.



Dieser Sendeconnector erfordert die folgende Konfiguration:

  - **Name**   An interne Org (oder ein anderer beschreibender Name)

  - **Verwendungstyp**   Intern

  - **Adressräume**   Alle akzeptierten Domänen für die Exchange-Organisation. Beispielsweise "\*.contoso.com".

  - DNS-Routing deaktiviert (Smarthostrouting aktiviert)

  - **Smarthosts**   FQDN eines oder mehrerer Postfachserver als Smarthosts. Beispielsweise "mbxserver01.contoso.com" und "mbxserver02.contoso.com".

  - **Smart host authentication methods**   Standardauthentifizierung über TLS

  - **Smarthost-Anmeldeinformationen für die Authentifizierung**   Anmeldeinformationen für das Benutzerkonto in der internen Domäne. Benutzername und Kennwort müssen zunächst in einer temporären Variable gespeichert werden, weil das Cmdlet **New-SendConnector** die Benutzeranmeldeinformationen nicht im Nur-Text-Format akzeptiert.

Um einen Sendeconnector zu erstellen, der zum Senden von Nachrichten an die Exchange-Organisation konfiguriert ist, führen Sie den folgenden Befehl aus:

```powershell
    $MailboxCredentials = Get-Credential
    New-SendConnector -Name "To Internal Org" -Usage Internal -AddressSpaces *.contoso.com -DNSRoutingEnabled $false -SmartHosts mbxserver01.contoso.com,mbxserver02.contoso.com -SmartHostAuthMechanism BasicAuthRequireTLS -AuthenticationCredential $MailboxCredentials
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-SendConnector](https://technet.microsoft.com/de-de/library/aa998936\(v=exchg.150\)).

## Schritt 3: Ändern des Standardempfangsconnectors für die ausschließliche Annahme von Nachrichten aus dem Internet

Am Standardempfangsconnector sollten Sie die folgenden Konfigurationsänderungen vornehmen:

  - Ändern Sie den Namen, sodass daraus ersichtlich ist, dass der Connector ausschließlich für den Empfang von E-Mail-Nachrichten aus dem Internet verwendet wird. Der Standardempfangsconnector trägt den Namen "Default internal Receive connector \<Edge-Transport-Servername\>".

  - Ändern Sie die Netzwerkbindungen, sodass Nachrichten nur über den mit dem Internet verbundenen Netzwerkadapter akzeptiert werden. Beispielsweise 10.1.1.1 und den Standardwert 25 für den SMTP TCP-Port.

Um den Standardempfangsconnector so zu ändern, dass er nur Nachrichten aus dem Internet annimmt, führen Sie den folgenden Befehl aus.

```powershell
    Set-ReceiveConnector "Default internal Receive connector Edge01" -Name "From Internet" -Bindings 10.1.1.1:25
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125140\(v=exchg.150\)).

## Schritt 4: Erstellen eines Empfangsconnectors, der für die ausschließliche Annahme von Nachrichten aus der Exchange-Organisation konfiguriert ist

Dieser Empfangsconnector erfordert die folgende Konfiguration:

  - **Name**   Aus interner Org (oder ein anderer beschreibender Name)

  - **Verwendungstyp**   Intern

  - **Lokale Netzwerkbindungen**   Interner, mit dem Netzwerk verbundener Netzwerkadapter. Beispielsweise 10.1.1.2 und den Standardwert 25 für den SMTP TCP-Port.

  - **Remotenetzwerkeinstellungen**   IP-Adresse mindestens eines Postfachservers in der Exchange-Organisation. Beispielsweise 192.168.5.10 und 192.168.5.20.

  - **Authentifizierungsmethoden**   TLS, Standardauthentifizierung, Standardauthentifizierung über TLS und Exchange Server-Authentifizierung.

Um einen Empfangsconnector zu erstellen, der so konfiguriert ist, dass er nur Nachrichten aus der Exchange-Organisation annimmt, führen Sie den folgenden Befehl aus.

```powershell
    New-ReceiveConnector -Name "From Internal Org" -Usage Internal -AuthMechanism TLS,BasicAuth,BasicAuthRequireTLS,ExchangeServer -Bindings 10.1.1.2:25 -RemoteIPRanges 192.168.5.10,192.168.5.20
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125139\(v=exchg.150\)).

## Woher wissen Sie, dass diese Schritte erfolgreich waren?

Um die erfolgreiche Konfiguration der erforderlichen Sende- und Empfangsconnectors zu überprüfen, führen Sie die folgenden Befehle auf dem Edge-Transport-Server aus, und überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

```powershell
    Get-SendConnector | Format-List Name,Usage,AddressSpaces,SourceTransportServers,DSNRoutingEnabled,SmartHosts,SmartHostAuthMechanism
    Get-ReceiveConnector | Format-List Name,Usage,AuthMechanism,Bindings,RemoteIPRanges
```

## Postfachserververfahren

Die Postfachserver in Ihrer Organisation benötigen einen Sendeconnector, der für das Senden von Nachrichten an den Edge-Transport-Server zur Weiterleitung an das Internet konfiguriert ist.

Standardmäßig werden bei der Installation der Postfachserverrolle zwei Empfangsconnectors konfiguriert. Der Connector namens "Client *Servername*" wird so konfiguriert, dass er Nachrichten von allen POP3- und IMAP-Messagingclients annimmt. Der Connector namens "Default *Servername*" wird so konfiguriert, dass er Nachrichten von einem Edge-Transport-Server annimmt. Es sind keine weiteren Änderungen an diesen Connectors erforderlich.

## Schritt 5: Erstellen eines Sendeconnectors, der zum Senden ausgehender Nachrichten an den Edge-Transport-Server konfiguriert ist

Dieser Sendeconnector erfordert die folgende Konfiguration:

  - **Name**   An Edge (oder ein anderer beschreibender Name)

  - **Verwendungstyp**   Intern

  - **Adressräume**   "\*" (alle Domänen)

  - DNS-Routing deaktiviert (Smarthostrouting aktiviert)

  - **Smarthosts**   IP-Adresse oder FQDN des Edge-Transport-Server. Beispielsweise "edge01.contoso.net".

  - **Quellpostfachserver**   FQDN von mindestens einem Postfachserver. Beispielsweise "mbxserver01.contoso.com" und "mbxserver02.contoso.com".

  - **Smart host authentication method**   Standardauthentifizierung über TLS

  - **Smarthost-Anmeldeinformationen für die Authentifizierung**   Anmeldeinformationen für das Benutzerkonto auf dem Edge-Transport-Server. Benutzername und Kennwort müssen zunächst in einer temporären Variable gespeichert werden, weil das Cmdlet **New-SendConnector** die Benutzeranmeldeinformationen nicht im Nur-Text-Format akzeptiert.

Um einen Sendeconnector zu erstellen, der zum Senden von ausgehenden Nachrichten an den Edge-Transport-Server konfiguriert ist, führen Sie den folgenden Befehl aus:

```powershell
    $EdgeCredentials = Get-Credential
    New-SendConnector -Name "To Edge" -Usage Internal -AddressSpaces * -DNSRoutingEnabled $false -SmartHosts edge01.contoso.com -SourceTransportServers mbxserver01.contoso.com,mbxserver02.contoso.com -SmartHostAuthMechanism BasicAuthRequireTLS -AuthenticationCredential $EdgeCredentials
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-SendConnector](https://technet.microsoft.com/de-de/library/aa998936\(v=exchg.150\)).

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Um die erfolgreiche Erstellung eines Sendesconnectors zu überprüfen, der ausgehende Nachrichten an den Edge-Transport-Server sendet, führen Sie die folgenden Befehle auf dem Postfachserver aus, und überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

```powershell
    Get-SendConnector | Format-List Name,Usage,AddressSpaces,DSNRoutingEnabled,SmartHosts,SourceTransportServers,SmartHostAuthMechanism
```
