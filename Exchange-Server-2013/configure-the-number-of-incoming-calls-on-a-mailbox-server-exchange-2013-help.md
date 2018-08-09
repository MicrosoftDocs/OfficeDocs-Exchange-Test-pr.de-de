---
title: 'Konfigurieren der Anz. eingeh. Anrufe auf Postfachserver: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren Sie die Anzahl eingehender Anrufe auf einem Postfachserver
ms:assetid: 419e1de9-2bf8-48a8-824d-2a536b0a6d90
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997637(v=EXCHG.150)
ms:contentKeyID: 50554780
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die Anzahl eingehender Anrufe auf einem Postfachserver

 

_**Gilt für:** Exchange Server, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-23_

Sie können die Anzahl eingehender gleichzeitiger Verbindungen konfigurieren, die ein Postfachserver akzeptiert, auf dem der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird. Hierzu gehören alle eingehenden Anrufe, einschließlich Outlook Voice Access, Mailboxansage, automatische Telefonzentralen und Faxanrufe. Wenn Sie die Anzahl gleichzeitiger Verbindungen auf einem Postfachserver erhöhen, sind mehr Systemressourcen erforderlich, als wenn Sie die Anzahl gleichzeitiger Anrufe verringern. Das Verringern der Anzahl gleichzeitiger Anrufe ist besonders auf langsamen Computern wichtig, auf denen Unified Messaging-Dienste installiert sind. Der Bereich für die Anzahl gleichzeitiger Sprachanrufe liegt zwischen 0 und 200; der Standardwert ist 100.

Informationen zu weiteren Aufgaben im Zusammenhang mit Unified Messaging und Postfachservern finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich, dass die Clientzugriffs- und Postfachserver korrekt installiert wurden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Anzahl eingehender Anrufe auf einem Postfachserver mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Geben Sie unter **UM-Diensteinstellungen** unter **Maximale Anzahl von zulässigen Anrufen** eine Zahl zwischen 0 und 200 ein, und klicken Sie auf **Speichern**.

## Konfigurieren der Anzahl eingehender Anrufe auf einem Postfachserver mithilfe der Shell

In diesem Beispiel wird die Anzahl eingehender Sprach-, Outlook Voice Access- und Faxanrufe, die von dem Postfachserver `MyMailboxServer1` akzeptiert werden, auf den Wert "50" festgelegt.

    Set-UMService -Identity MyMailboxServer1 -MaxCallsAllowed 50

