---
title: 'Ermöglichen o. Verhindern d. Weiterleit. von Anr. von autom. Telefonzentrale'
TOCTitle: Ermöglichen oder verhindern, dass Weiterleiten von Anrufen von eine automatische Telefonzentrale
ms:assetid: ca961cc8-cc24-4e05-b72d-79979c155cf9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423558(v=EXCHG.150)
ms:contentKeyID: 52062817
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ermöglichen oder verhindern, dass Weiterleiten von Anrufen von eine automatische Telefonzentrale

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können für Anrufer das Weiterleiten von Anrufen an Benutzer über eine automatische Telefonzentrale aktivieren oder deaktivieren. Diese Option ist standardmäßig aktiviert und ermöglicht die Weiterleitung von Anrufern an UM-aktivierte Benutzer im Unified Messaging-Wählplan (UM), der der automatischen UM-Telefonzentrale zugeordnet ist.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://technet.microsoft.com/de-de/library/JJ822155(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://technet.microsoft.com/de-de/library/Aa998875(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Verhindern der Anrufweiterleitung an Benutzer von einer automatischen UM-Telefonzentrale mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie die Anrufweiterleitung konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Zugriff auf Adressbuch und Vermittlungsstelle** unter **Optionen für das Kontaktieren von Benutzern** das Kontrollkästchen neben **Anrufer dürfen Benutzer wählen**, um das Weiterleiten von Anrufen zu ermöglichen. Deaktivieren Sie das Kontrollkästchen, um die Anrufweiterleitung zu verhindern.

4.  Klicken Sie auf **Speichern**.


> [!NOTE]
> Wenn Sie dieses Kontrollkästchen und auch das Kontrollkästchen <STRONG>Anrufer dürfen Sprachnachrichten für Benutzer hinterlassen</STRONG> deaktivieren, stehen die Optionen unter <STRONG>Optionen zum Durchsuchen des Adressbuchs</STRONG> nicht zur Verfügung.



## Aktivieren oder Verhindern der Anrufweiterleitung an Benutzer von einer automatischen UM-Telefonzentrale mithilfe der Shell

In diesem Beispiel wird die Anrufweiterleitung für die automatische UM-Telefonzentrale `MyUMAutoAttendant` verhindert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -AllowDialPlanSubscribers $false

In diesem Beispiel wird die Anrufweiterleitung für die automatische UM-Telefonzentrale `MyUMAutoAttendant` erlaubt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -AllowDialPlanSubscribers $true

