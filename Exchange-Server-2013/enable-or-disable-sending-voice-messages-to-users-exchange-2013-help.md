---
title: 'Aktivieren oder Deaktivieren des Versands von Sprachnachrichten an Benutzer: Exchange Online Help'
TOCTitle: Aktivieren oder Deaktivieren des Versands von Sprachnachrichten an Benutzer
ms:assetid: faa300d8-2534-40db-8ef9-428be8bb7934
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351277(v=EXCHG.150)
ms:contentKeyID: 52062799
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren des Versands von Sprachnachrichten an Benutzer

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-12-13_

Sie können Anrufern das Senden von Sprachnachrichten an Benutzer von einer automatischen UM-Telefonzentrale ermöglichen oder das Senden solcher Sprachnachrichten verhindern. Diese Option ist standardmäßig aktiviert und ermöglicht Anrufern das Senden von Sprachnachrichten an Benutzer in einem Satz mit UM-Wähleinstellungen (Unified Messaging), der der automatischen UM-Telefonzentrale zugeordnet ist. Wenn Sie diese Option deaktivieren, stellt die automatische Telefonzentrale Anrufern während einer Systemansage nicht das Senden einer Sprachnachricht zur Wahl.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren von Anrufern für das Senden von Sprachnachrichten mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Zugriff auf Adressbuch und Vermittlungsstelle** unter **Optionen für das Kontaktieren von Benutzern** das Kontrollkästchen **Anrufer dürfen Sprachnachrichten für Benutzer hinterlassen**, um Anrufern das Hinterlassen von Sprachnachrichten zu ermöglichen. Wenn Sie verhindern möchten, dass Anrufer Sprachnachrichten hinterlassen, deaktivieren Sie das Kontrollkästchen.

4.  Klicken Sie auf **Speichern**.


> [!NOTE]
> Wenn Sie diese Option und die Option <STRONG>Anrufer dürfen Benutzer wählen</STRONG> deaktivieren, wird auch <STRONG>Optionen zum Durchsuchen des Adressbuchs</STRONG> deaktiviert.



## Aktivieren oder Deaktivieren von Anrufern für das Senden von Sprachnachrichten mithilfe der Shell

In diesem Beispiel werden Benutzer, die bei der automatischen UM-Telefonzentrale namens `MyUMAutoAttendant` anrufen, am Senden von Sprachnachrichten gehindert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -SendVoiceMsgEnabled $false

In diesem Beispiel wird Benutzern, die bei der automatischen UM-Telefonzentrale namens `MyUMAutoAttendant` anrufen, das Senden von Sprachnachrichten ermöglicht.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -SendVoiceMsgEnabled $true

