---
title: 'Testen des UM-Betriebs: Exchange 2013 Help'
TOCTitle: Testen des UM-Betriebs
ms:assetid: 06c9ab4e-8272-47b1-a217-e366f7e9dbaa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995957(v=EXCHG.150)
ms:contentKeyID: 56271558
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Testen des UM-Betriebs

 

_**Gilt für:**Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-06-25_

In diesem Thema wird erläutert, wie die Shell zum Testen des Betriebs des Voicemailsystems verwendet wird. Wenn Sie das folgende Verfahren ausführen, leitet der Postfachserver, der den Microsoft Exchange Unified Messaging-Dienst ausführt, einen SIP-Diagnoseaufruf (Session Initiation Protocol) ein und gibt dann eine Statusvariable des UM-Servers zurück.

Dieser Diagnosetest kann nur auf einem lokalen Postfachserver ausgeführt werden, und Sie können den Betrieb des Postfachservers nicht mithilfe der Exchange-Verwaltungskonsole testen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Clientzugriffs- und Postfachservern finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" und \&quot;Clientzugriffsserver (UM-Anrufrouterdienst)\&quot; im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Um die folgenden Verfahren ausführen zu können, müssen Sie sich beim Postfachserver mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" ist.

  - Stellen Sie sicher, dass der Postfachserver installiert ist, entweder auf demselben Computer wie der Clientzugriffsserver oder auf einem anderen Computer.

  - Stellen Sie sicher, dass der Clientzugriffsserver installiert ist, entweder auf demselben Computer wie der Postfachserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Testen des Betriebs des Unified Messaging-Dienstes

In diesem Beispiel werden Verbindungs- und Betriebstests für den lokalen Postfachserver ausgeführt und dann VoIP-Verbindungsinformationen (Voice over IP) angezeigt.

    Test-UMConnectivity

In diesem Beispiel wird die Möglichkeit des lokalen Clientzugriffsservers getestet, den TCP-Port 5060 auf eingehende, nicht verschlüsselte SIP-Anforderungen abzuhören.

    Test-UMConnectivity -ListenPort 5060

In diesem Beispiel wird die Möglichkeit des lokalen Clientzugriffsservers getestet, den TCP-Port 5061 auf eingehende, verschlüsselte SIP-Anforderungen abzuhören.

    Test-UMConnectivity -ListenPort 5061


> [!NOTE]
> Verwenden Sie Modus&nbsp;1, wenn der Parameter <CODE>-UMIPGateway</CODE> nicht angegeben ist.




> [!NOTE]
> Sie können den Parameter <CODE>-Timeout</CODE> auf einen Wert von unter 5 Sekunden festlegen. Es wird jedoch empfohlen, diesen Parameter immer mit einem Wert von mindestens 5 Sekunden zu konfigurieren.


