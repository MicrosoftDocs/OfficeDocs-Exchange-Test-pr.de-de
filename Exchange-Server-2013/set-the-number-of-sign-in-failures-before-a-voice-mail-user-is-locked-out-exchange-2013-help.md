---
title: 'Festlegen Sie die Zahl der ungünstigen-Anmeldung, bevor ein Voice Mail-Benutzer gesperrt ist: Exchange Online Help'
TOCTitle: Festlegen Sie die Zahl der ungünstigen-Anmeldung, bevor ein Voice Mail-Benutzer gesperrt ist
ms:assetid: 855e1980-2868-4983-b097-0b5f63f202b8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123544(v=EXCHG.150)
ms:contentKeyID: 50554864
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen Sie die Zahl der ungünstigen-Anmeldung, bevor ein Voice Mail-Benutzer gesperrt ist

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können konfigurieren, welche Anzahl fehlerhafter Anmeldeversuchen zulässig ist, bevor das Postfach eines Outlook Voice Access-Benutzers gesperrt wird. Die maximal zulässige Anzahl fehlerhafter Anmeldeversuche vor dem Sperren eines Postfachs wird in einer UM-Postfachrichtlinie konfiguriert und gilt für alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie unterliegen. Die Standardeinstellung ist 15.

Verringern Sie zum Erhöhen der Sicherheit die maximale Anzahl der Fehlversuche. Bei Festlegung auf einen Wert, der wesentlich kleiner als der Standardwert ist, werden Benutzerpostfächer jedoch gegebenenfalls unnötigerweise gesperrt. Wenn Fehler bei der PIN-Authentifizierung von UM-aktivierten Benutzern auftreten oder Anmeldeversuche von Benutzern beim System fehlschlagen, erzeugt Unified Messaging Warnereignisse, die Sie in der Ereignisanzeige anzeigen können. Diese Einstellung muss höher als die Einstellung für die Anzahl fehlerhafter Anmeldeversuche sein, ehe die PIN zurückgesetzt wird.

Weitere Aufgaben im Zusammenhang mit der Sicherheit von Outlook Voice Access-PINs finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Konfigurieren der maximalen Anzahl fehlerhafter Anmeldeversuche vor dem Sperren eines Voicemailbenutzers

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf **PIN-Richtlinien**, und geben Sie neben **Anzahl der Anmeldefehler vor dem Sperren** einen Wert von 1 bis 999 ein.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren der maximalen Anzahl fehlerhafter Anmeldeversuche vor dem Sperren eines Voicemailbenutzers

In diesem Beispiel wird die maximal zulässige Anzahl fehlerhafter Anmeldeversuchen für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` unterliegen, auf 10 festgelegt.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -MaxLogonAttempts 10

In diesem Beispiel wird die Anzahl der Anmeldefehler auf 3 festgelegt, bevor die PIN des Outlook Voice Access-Benutzers zurückgesetzt wird. Die maximale Anzahl der Anmeldeversuche wird auf 5 begrenzt, und die minimale PIN-Länge beträgt für UM-aktivierte Benutzer, die einer UM-Postfachrichtlinie mit der Bezeichnung `MyUMMailboxPolicy` zugewiesen sind, 9 Zeichen.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3
    -MaxLogonAttempts 5 -MinPINLength 9

