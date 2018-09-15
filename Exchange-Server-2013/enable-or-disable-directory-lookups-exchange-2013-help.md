---
title: 'Aktivieren oder Deaktivieren der Verzeichnissuche: Exchange Online Help'
TOCTitle: Aktivieren oder Deaktivieren der Verzeichnissuche
ms:assetid: c0768815-8578-4385-8d4c-7d1e40304cec
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423557(v=EXCHG.150)
ms:contentKeyID: 52062814
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren der Verzeichnissuche

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-05-10_

Sie können Verzeichnissuchen aktivieren, damit Anrufer, die bei einer automatischen Unified Messaging-Telefonzentrale (UM) anrufen, über die Tastatur ihres Telefons Namen im Verzeichnis nachschlagen können, ohne das Verzeichnis mithilfe von Spracheingaben durchsuchen zu können. Diese Einstellung ist standardmäßig aktiviert. Wenn diese Einstellung deaktiviert wird, können Anrufer nicht mithilfe der Tonwahl oder mithilfe von Spracheingaben im Verzeichnis nach einer bestimmten Person suchen.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://technet.microsoft.com/de-de/library/JJ822155(v=EXCHG.150)).


> [!NOTE]
> Outlook Voice Access-Benutzer automatische Spracherkennung Spracherkennung (ASR) oder Spracheingaben verwenden können, um Benutzer in das Verzeichnis zu suchen, können sie nur DTMF- oder Mehrfrequenzwahlverfahren verwenden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Verzeichnissuche mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, die Sie für Verzeichnissuchen aktivieren oder deaktivieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Zugriff auf Adressbuch und Vermittlungsstelle** unter **Optionen zum Durchsuchen des Adressbuchs** das Kontrollkästchen neben **Anrufer dürfen Benutzer nach Name oder Alias suchen**, um Anrufern das Suchen nach Benutzern zu ermöglichen. Um Anrufern das Suchen nach Benutzern nicht zu ermöglichen, deaktivieren Sie dieses Kontrollkästchen.

4.  Klicken Sie auf **Speichern**.

## Aktivieren oder Deaktivieren der Verzeichnissuche mithilfe der Shell

In diesem Beispiel wird die Verzeichnissuche für die automatische UM-Telefonzentrale `MyUMAutoAttendant` deaktiviert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -NameLookupEnabled $false

