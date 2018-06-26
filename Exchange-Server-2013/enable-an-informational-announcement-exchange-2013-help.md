---
title: 'Aktivieren einer Informationsansage: Exchange Online Help'
TOCTitle: Aktivieren einer Informationsansage
ms:assetid: 07f6c13e-3781-4127-9321-f0f85f054259
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266918(v=EXCHG.150)
ms:contentKeyID: 50554796
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren einer Informationsansage

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-04-19_

Sie können eine Informationsansage für eine automatische Unified Messaging-Telefonzentrale (UM) aktivieren. Wenn eine Informationsansage aktiviert wird, erfolgt die Wiedergabe unmittelbar nach der Begrüßung während oder außerhalb der Geschäftszeiten. Standardmäßig ist keine Informationsansage konfiguriert. Wenn Sie eine Informationsansage aktivieren möchten, erstellen Sie eine WAV- oder WMA-Datei, die als Informationsansage verwendet werden soll. Konfigurieren Sie die automatische Telefonzentrale dann für die Verwendung dieser Audiodatei.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Erstellen Sie eine WAV- oder WMA-Datei, die als Informationsansage verwendet werden soll.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren einer Informationsansage mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie eine Informationsansage aktivieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Begrüßungen** unter **Informationsansage** auf **Ändern** und dann auf **Durchsuchen**, um die Datei mit der Informationsansage zu suchen, die Sie vor der Ausführung dieses Verfahrens erstellt haben.
    

    > [!IMPORTANT]
    > Bei der Datei, die Sie für die Begrüßung verwenden, muss es sich um eine WAV- oder WMA-Datei handeln.



4.  Sobald Sie die Datei gefunden haben, klicken Sie auf **Öffnen** und dann auf **Speichern**.

## Aktivieren einer Informationsansage mithilfe der Shell

In diesem Beispiel wird die Informationsansage, die die Datei `MyInfoAnnouncement.wav` verwendet, für die automatische UM-Telefonzentrale `MyUMAutoAttendant` aktiviert.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -InfoAnnouncementEnabled $true -InfoAnnouncementFilename MyInfoAnnouncement.wav

