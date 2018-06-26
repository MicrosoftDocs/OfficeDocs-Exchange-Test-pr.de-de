---
title: 'Business Speicherort festlegen: Exchange Online Help'
TOCTitle: Business Speicherort festlegen
ms:assetid: 19bbc20d-d11e-4e75-9bb4-c5d85cf17fc5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423540(v=EXCHG.150)
ms:contentKeyID: 52062672
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Business Speicherort festlegen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-23_

Sie können den Standort eines Unternehmens in einer automatischen UM-Telefonzentrale (Unified Messaging) angeben, sodass dieser den Anrufern wiedergegeben wird. Standardmäßig ist kein Unternehmensstandort eingegeben.

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](um-auto-attendant-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](create-a-um-auto-attendant-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren eines Unternehmensstandorts mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-Wählplan** unter **Automatische UM-Telefonzentralen** die automatische UM-Telefonzentrale, für die Sie den Geschäftsstandort festlegen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Geben Sie auf der Seite **Automatische UM-Telefonzentrale** \> **Allgemein**, unter **Unternehmensstandort** den Standort des Unternehmens ein.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren eines Unternehmensstandorts

In diesem Beispiel wird ein Unternehmensstandort in der automatischen UM-Telefonzentrale "`MyUMAutoAttendant`" festgelegt.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -BusinessLocation 'Redmond'

