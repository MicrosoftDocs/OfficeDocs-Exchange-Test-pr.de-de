---
title: 'Aktivieren oder Deaktivieren der Exchange-Suche: Exchange 2013 Help'
TOCTitle: Aktivieren oder Deaktivieren der Exchange-Suche
ms:assetid: 195b25be-53fb-4215-90a5-04340d640bcc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996416(v=EXCHG.150)
ms:contentKeyID: 52062836
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der Exchange-Suche

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-05-07_

Standardmäßig ist die Exchange-Suche für alle neuen Postfachdatenbanken aktiviert und benötigt keine zusätzliche Konfiguration. Wenn die Exchange-Suche jedoch keinen Postfachinhalt indizieren soll, können Sie sie für einzelne Postfachdatenbanken oder einen ganzen Postfachserver deaktivieren.


> [!WARNING]
> Wenn Sie die Exchange-Suche deaktivieren, wird die Funktion und Leistung der Volltextsuchvorgänge beeinträchtigt, die von Ihren Benutzern mit Outlook im Onlinemodus oder auf Windows Mobile-Geräten ausgeführt werden.<BR><A href="in-place-ediscovery-exchange-2013-help.md">Compliance-eDiscovery</A> stützt sich ebenfalls auf die Exchange-Suche. Wenn Sie die Exchange-Suche für eine Postfachdatenbank oder einen Postfachserver deaktivieren, gibt die Compliance-eDiscovery keine Nachrichten von der Datenbank oder vom Server zurück.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Exchange-Suche finden Sie unter [Exchange-Suchverfahren](exchange-search-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 1 Minute

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Die Exchange-Suche kann für Server oder Postfachdatenbanken aktiviert bzw. deaktiviert werden, nicht jedoch für einzelne Postfachbenutzer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Was möchten Sie machen?

## Deaktivieren oder Aktivieren der Exchange-Suche für eine Postfachdatenbank

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Exchange-Suche" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).


> [!NOTE]
> Die Exchange-Verwaltungskonsole kann nicht zum Deaktivieren oder Aktivieren der Exchange-Suche für eine Postfachdatenbank verwendet werden.



Dieser Befehl deaktiviert die Exchange-Suche für die Postfachdatenbank "EXCH01".

    Set-MailboxDatabase "Mailbox Database (EXCH01)" -IndexEnabled $false

Dieser Befehl aktiviert die Exchange-Suche für die Postfachdatenbank "EXCH01".

    Set-MailboxDatabase "Mailbox Database (EXCH01)" -IndexEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)).

## Deaktivieren oder Aktivieren der Exchange-Suche für einen Postfachserver

Zum Deaktivieren der Exchange-Suche für einen Postfachserver müssen Sie den den Microsoft Exchange-Suchdienst deaktivieren und anhalten. Ebenso müssen Sie zum Aktivieren der Exchange-Suche für einen Postfachserver den Microsoft Exchange-Suchdienst aktivieren und starten. Sie können zu diesem Zweck die Konsole "Dienste" oder die Shell verwenden.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwalten des Exchange-Suchdiensts auf einem Postfachserver" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

**Verwenden der Konsole "Dienste"**

1.  Gehen Sie zu **Start** \> **Verwaltung** \> **Dienste**.

2.  Klicken Sie im Detailbereich **Dienste** mit der rechten Maustaste auf den Dienst **Microsoft Exchange-Suche**, und wählen Sie dann **Eigenschaften** aus.

3.  Wählen Sie auf der Registerkarte **Allgemein** in der Liste **Starttyp** die Option **Deaktiviert** aus, um den Dienst zu deaktivieren, oder wählen Sie **Automatisch** aus, damit der Dienst automatisch gestartet wird.
    

    > [!NOTE]
    > Der Starttyp macht sich beim nächsten Versuch, den Dienst zu starten, bemerkbar: Der Dienst wird entweder automatisch nach einem Neustart des Servers oder manuell gestartet. Im nächsten Schritt wird der Dienst beendet oder manuell gestartet.



4.  Klicken Sie auf **Beenden**, um den Dienst zu beenden, oder auf **Starten**, um den Dienst zu starten.

5.  Klicken Sie auf **OK**, um die Änderungen zu speichern.

**Verwenden der Shell**

Führen Sie die folgenden Befehle aus, um den Microsoft Exchange-Suchdienst anzuhalten und zu deaktivieren.

    Stop-Service MSExchangeFastSearch

    Set-Service MSExchangeFastSearch -StartupType Disabled

Führen Sie die folgenden Befehle aus, um den Exchange-Suchdienst für den automatischen Start zu konfigurieren und den Dienst anschließend zu starten.

    Set-Service MSExchangeFastSearch -StartupType Automatic

    Start-Service MSExchangeFastSearch

