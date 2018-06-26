---
title: 'Ändern des SMTP-Banners für einen Empfangsconnector: Exchange 2013 Help'
TOCTitle: Ändern des SMTP-Banners für einen Empfangsconnector
ms:assetid: d667704e-fd69-4aca-9c35-eef7006944b2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124740(v=EXCHG.150)
ms:contentKeyID: 52062911
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ändern des SMTP-Banners für einen Empfangsconnector

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Das *SMTP-Banner* ist die SMTP-Verbindungsantwort, die ein SMTP-Remotemessagingserver erhält, nachdem er eine Verbindung mit einem Empfangsconnector hergestellt hat, der für einen Computer mit Microsoft Exchange Server 2013 konfiguriert ist.

Dies ist die Standardantwort, die ein SMTP-Remotemessagingserver erhält, nachdem er eine Verbindung mit dem Empfangsconnector hergestellt hat:

    220 <Servername> Microsoft ESMTP MAIL service ready at <RegionalDay-Date-24HourTimeFormat> <RegionalTimeZoneOffset>

Wenn Sie einen benutzerdefinierten Wert für das SMTP-Banner für einen Empfangsconnector angeben, empfängt ein SMTP-Remotemessagingserver, der eine Verbindung mit diesem SMTP-Empfangsconnector herstellt, die folgende Antwort.

    220 <Banner Text>

Sie können das SMTP-Banner für SMTP-Empfangsconnectors mit Internetverbindung ändern, damit das SMTP-Banner den Servernamen und die Messagingserversoftware nicht preisgibt.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Die Ersetzungs-Textzeichenfolge für das SMTP-Banner muss immer mit `220` beginnen. Wie in RFC 2821 definiert, lautet der SMTP-Standardantwortcode für "Service ready" (Dienst bereit) 220.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Ändern des SMTP-Banners eines Empfangsconnectors mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Set-ReceiveConnector <ConnectorIdentity> -Banner "220 <Banner Text>"

In diesem Beispiel wird das SMTP-Banner für den vorhandenen Empfangsconnector "From the Internet" so geändert, dass das SMTP-Banner `220 Contoso Corporation` anzeigt.

    Set-ReceiveConnector "From the Internet" -Banner "220 Contoso Corporation"

In diesem Beispiel wird das SMTP-Banner für den Empfangsconnector "From the Internet" entfernt, wodurch das SMTP-Banner auf den Standardwert zurückgesetzt wird.

    Set-ReceiveConnector "From the Internet" -Banner $null

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass das SMTP-Banner für einen Empfangsconnector erfolgreich geändert wurde:

1.  Öffnen Sie einen Telnet-Client auf einem Computer, der auf den Empfangsconnector zugreifen kann, und führen Sie den folgenden Befehl aus:
    
        open <Connector FQDN or IP address> <Port>

2.  Prüfen Sie, ob die Antwort des Empfangsconnectors das von Ihnen konfigurierte SMTP-Banner enthält.

Dieses Verfahren funktioniert nur bei Empfangsconnectors, die die anonyme oder Standardauthentifizierung zulassen. Weitere Informationen finden Sie unter [Verwenden von Telnet zum Testen der SMTP-Kommunikation](use-telnet-to-test-smtp-communication-exchange-2013-help.md).

