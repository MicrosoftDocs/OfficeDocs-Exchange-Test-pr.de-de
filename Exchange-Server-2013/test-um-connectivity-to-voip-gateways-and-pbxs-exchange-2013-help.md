---
title: 'Testen der UM-Verbindung mit VoIP-Gateways und Nebenstellenanlagen: Exchange 2013 Help'
TOCTitle: Testen der UM-Verbindung mit VoIP-Gateways und Nebenstellenanlagen
ms:assetid: 2aca8631-a99a-4e29-aff0-e462385f03b2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996906(v=EXCHG.150)
ms:contentKeyID: 56271561
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Testen der UM-Verbindung mit VoIP-Gateways und Nebenstellenanlagen

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2014-09-17_

Sie können den Betrieb von Unified Messaging (UM) und dazugehöriger, angeschlossener Telefoniegeräte testen. Beim folgenden Verfahren testet der Clientzugriffs- und der Postfachserver den vollständigen End-to-End-Betrieb des Voicemailsystems. Dies schließt die mit den Clientzugriffs- und der Postfachservern verbundenen Telefoniekomponenten, einschließlich VoIP-Gateways, PBX-Ressourcen (Private Branch eXchanges, Nebenstellenanlagen), IP-PBXs und Verkabelung ein.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die UM-Problembehandlung finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" und \&quot;Clientzugriffsserver (UM-Anrufrouterdienst)\&quot; im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Um die folgenden Verfahren ausführen zu können, müssen Sie sich beim Postfachserver mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" ist.

  - Stellen Sie sicher, dass der Postfachserver installiert ist, entweder auf demselben Computer wie der Clientzugriffsserver oder auf einem anderen Computer.

  - Stellen Sie sicher, dass der Clientzugriffsserver installiert ist, entweder auf demselben Computer wie der Postfachserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Exchange-Verwaltungsshell zum Testen des Betriebs von Unified Messaging und der Telefoniekomponenten

In diesem Beispiel wird getestet, ob das UM-IP-Gateway den TCP-Port 5060 auf eingehende SIP-Anforderungen überwachen kann.

    Test-UMConnectivity -ListenPort 5060 -UMIPGateway MyIPGateway

In diesem Beispiel wird die Möglichkeit des lokalen Postfachservers getestet, eine nicht gesicherte TCP-Verbindung anstatt einer sicheren MTLS-Verbindung zu verwenden, um einen Anruf über das UM-IP-Gateway `MyUMIPGateway` mithilfe der Telefonnummer 56780 zu tätigen.

    Test-UMConnectivity -UMIPGateway MyUMIPGateway -Phone 56780 -Secured $false

In diesem Beispiel wird die Outlook Voice Access-Nummer für Wähleinstellungen durch Verwenden eines SIP-URI getestet. Dieses Beispiel gilt für Umgebungen mit Lync Server 2007.

    Test-UMConnectivity -UMIPGateway OCSGateway1 -Phone "sip:SIPdialplan.contoso.com@contoso.com"


> [!NOTE]
> Sie können den Parameter <CODE>-Timeout</CODE> auf einen Wert von unter 5 Sekunden festlegen. Es wird jedoch empfohlen, diesen Parameter immer mit einem Wert von mindestens 5 Sekunden zu konfigurieren. Verwenden Sie Modus&nbsp;2, wenn der Parameter <CODE>&shy;UMIPGateway</CODE> in der Befehlszeilensyntax angegeben wird.


