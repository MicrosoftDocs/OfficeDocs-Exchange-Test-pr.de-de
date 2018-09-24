---
title: 'Wiederhers. öfftl. Ordner und Postf. f. öfftl. Ordner aus fehlerhaft. Versch.'
TOCTitle: Wiederherstellen von öffentlichen Ordnern und Postfächern für öffentliche Ordner aus fehlerhaften Verschiebungen
ms:assetid: 2ade83c9-5f9b-4945-bf32-48fa8185b515
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ983802(v=EXCHG.150)
ms:contentKeyID: 52062850
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Wiederherstellen von öffentlichen Ordnern und Postfächern für öffentliche Ordner aus fehlerhaften Verschiebungen

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-13_

Wenn eine Verschiebungsanforderung für einen öffentlichen Ordner oder für ein Postfach für öffentliche Ordner einen Fehler verursacht, können Sie den Ordner oder das Postfach wiederherstellen, sofern die folgenden Bedingungen zutreffen:

  - **Fehler beim Verschieben öffentlicher Ordner**   Eine vorläufig gelöschte Kopie des öffentlichen Ordners ist noch immer im Quellpostfach für öffentliche Ordner vorhanden und liegt noch innerhalb des Aufbewahrungszeitraums.

  - **Fehler beim Verschieben des Postfachs für öffentliche Ordner**   Eine vorläufig gelöschte Kopie des Postfachs für öffentliche Ordner ist noch immer in der Quellpostfachdatenbank vorhanden und liegt noch innerhalb des Aufbewahrungszeitraums.

Wenn der Aufbewahrungszeitraum für das Postfach verstrichen ist, können Sie ein einzelnes Postfach für öffentliche Ordner aus der Sicherung wiederherstellen. Anschließend extrahieren Sie Daten aus dem wiederhergestellten Postfach und kopieren sie in einen Zielordner oder führen sie mit einem anderen Postfach zusammen. Weitere Informationen finden Sie unter [Wiederherstellen von Daten mithilfe einer Wiederherstellungsdatenbank](restore-data-using-a-recovery-database-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachwiederherstellungsanforderung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht mit der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Zum Erstellen einer Wiederherstellungsanforderung müssen Sie die Werte für die Parameter *DisplayName*, *LegacyDN* oder *MailboxGUID* für das vorläufig gelöschte Postfach für öffentliche Ordner bereitstellen.

  - In der Standardeinstellung werden Dumpsterordner zusammen mit regulären Ordnern wiederhergestellt. Dies kann über den Parameter *ExcludeDumpster* verhindert werden.

  - Die Wiederherstellung von Postfächern für öffentliche Ordner unterscheidet sich von der Wiederherstellung normaler Postfächer insofern, als Ordner nicht erstellt werden, wenn sie nicht im Zielpostfach vorhanden sind. Fehlende Ordner werden am Ende der Wiederherstellungsanforderung in einer Warnmeldung angezeigt.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Wiederherstellen eines vorläufig gelöschten öffentlichen Ordners

In diesem Beispiel wird der öffentliche Ordner "\\Dev\\CustomerEnagagements" im Zielpostfach für öffentliche Ordner "Development01" wiederhergestellt.

    New-MailboxRestoreRequest -SourceStoreMailbox Development -SourceDatabase MBX_DB01 -TargetMailbox Development01 -AllowLegacyDNMismatch -IncludeFolders \Dev\CustomerEngagements

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)).

## Wiederherstellen eines vorläufig gelöschten Postfachs für öffentliche Ordner

In diesem Beispiel wird das Postfach für öffentliche Ordner "PF\_Singapore" im neuen Postfach für öffentliche Ordner "PF\_Singapore\_Restore" wiederhergestellt.

    New-MailboxRestoreRequest -SourceStoreMailbox PF_Singapore -SourceDatabase MBX_DB01 -TargetMailbox PF_Singapore_Restore -AllowLegacyDNMismatch

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-MailboxRestoreRequest](https://technet.microsoft.com/de-de/library/ff829875\(v=exchg.150\)).

