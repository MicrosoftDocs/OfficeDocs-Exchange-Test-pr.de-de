---
title: 'Festl. d. Anz. der vorh. Voicemail-PINs für Recycling: Exchange Online-Hilfe'
TOCTitle: Festlegen Sie die Anzahl der vorherigen Voicemail PINs Recycling
ms:assetid: b094e68e-c493-4576-a6b1-4c780e635405
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124254(v=EXCHG.150)
ms:contentKeyID: 50554879
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen Sie die Anzahl der vorherigen Voicemail PINs Recycling

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Wenn sich Benutzer von Outlook Voice Access bei einer Outlook Voice Access-Nummer einwählen, werden sie aufgefordert, ihre PIN einzugeben, damit das Voicemailsystem sie authentifizieren kann. Nachdem sie authentifiziert wurden, können sie auf die Voicemail-, E-Mail-, Kalender- und persönlichen Kontaktinformationen in ihrem jeweiligen Postfach über jedes beliebige Telefon zugreifen.

Für eine UM-Postfachrichtlinie (Unified Messaging) können mehrere PIN-bezogene Einstellungen konfiguriert werden. Verwenden Sie die Einstellung **Anzahl der PIN-Wiederverwendungen**, um die Anzahl der eindeutigen PINs festzulegen, die Benutzer verwenden müssen, bevor eine alte PIN erneut verwendet werden darf. Sie können diese Einstellung auf einen Wert von 1 bis 20 festlegen. In den meisten Organisationen sollte dieser Wert auf die Standardeinstellung (fünf PINs) festgelegt werden. Wenn Sie diesen Wert zu hoch festlegen, kann dies die Benutzer verärgern, weil sie zu häufig neue PINS erstellen und sich merken müssen. Wird er zu niedrig festgelegt, kann dies eine Sicherheitsbedrohung für Ihr Netzwerk bedeuten.


> [!IMPORTANT]
> Die Anzahl der PIN-Wiederverwendungen kann nicht deaktiviert werden.



Informationen zu weiteren Aufgaben im Zusammenhang mit der Outlook Voice Access-PIN-Sicherheit finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der Anzahl der PIN-Wiederverwendungen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf **PIN-Richtlinien**, und geben Sie neben **Anzahl der PIN-Wiederverwendungen** einen Wert von 1 bis 20 ein.

5.  Klicken Sie auf **Speichern**.

## Ändern der Anzahl der PIN-Wiederverwendungen mithilfe der Shell

In diesem Beispiel wird die Anzahl der PIN-Wiederverwendungen für die UM-Postfachrichtlinie `MyUMMailboxPolicy` auf 10 festgelegt.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -PINHistoryCount 10

