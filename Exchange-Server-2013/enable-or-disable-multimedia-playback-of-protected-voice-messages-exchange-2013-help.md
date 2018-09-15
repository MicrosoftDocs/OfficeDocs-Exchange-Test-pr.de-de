---
title: 'Aktiv.o. Deaktiv. der Multimediawiedergabe von geschützten Sprachnachrichten'
TOCTitle: Aktivieren oder Deaktivieren der Multimediawiedergabe von geschützten Sprachnachrichten
ms:assetid: 3c33370c-4262-42b1-8d83-d61fc7c426cd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423543(v=EXCHG.150)
ms:contentKeyID: 52062692
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren der Multimediawiedergabe von geschützten Sprachnachrichten

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Für Benutzer, die geschützte Voicemailnachrichten empfangen, kann für das Abhören der Nachrichten die Verwendung der Funktion "Wiedergabe über Telefon" erzwungen werden. Falls die Clientsoftware keine Rechteverwaltung unterstützt, müssen die Benutzer Outlook Voice Access zum Abhören von Nachrichten verwenden.

Zum Abhören von Sprachnachrichten können UM-aktivierte Benutzer (Unified Messaging) entweder die Wiedergabe über Telefon oder Multimedia-Software auf einem Computer oder Mobilgerät verwenden. Bei der Multimediawiedergabe kann ein UM-aktivierter Benutzer zum Abhören der Sprachnachricht eine Medienwiedergabe über die Computerlautsprecher oder auf einem Mobilgerät verwenden.


> [!NOTE]
> Geschützte Sprachnachrichten sind nur bei Clients verfügbar, die eine Version von&nbsp;Outlook mit Unterstützung der Rechteverwaltung verwenden. Falls die Clientsoftware keine Rechteverwaltung unterstützt, müssen die Benutzer Outlook Voice Access zum Abhören der Sprachnachrichten verwenden.



Standardmäßig ist der Wert der Eigenschaft **RequireProtectedPlayOnPhone** in einer UM-Postfachrichtlinie auf "False" eingestellt. Das bedeutet, dass UM-aktivierte Benutzer, die dieser UM-Postfachrichtlinie zugeordnet sind, geschützte Sprachnachrichten wie folgt abhören können:

  - Verwenden von Outlook Voice Access.

  - Verwenden der integrierten Medienwiedergabe oder Drücken der Schaltfläche "Wiedergabe über Telefon" in Outlook 2010 oder einer höheren Version.

  - Verwenden der integrierten Medienwiedergabe oder Drücken der Schaltfläche "Wiedergabe über Telefon" in Outlook Web App.

Ist dieser Wert auf "True" eingestellt, ist die Multimediawiedergabe geschützter Sprachnachrichten nicht zulässig. UM-aktivierte Benutzer, die einer UM-Postfachrichtlinie zugeordnet sind, für die dieser Wert festgelegt ist, können geschützte Sprachnachrichten nur wie folgt abhören:

  - Verwenden von Outlook Voice Access.

  - Verwenden der Schaltfläche "Wiedergabe über Telefon" in Outlook 2010 oder einer höheren Version.

  - Verwenden der Schaltfläche "Wiedergabe über Telefon" in Outlook Web App.

Diese Einstellung ist insbesondere dann sinnvoll, wenn UM-aktivierte Benutzer öffentliche Computer, Laptops an öffentlich zugänglichen Orten oder die Medienwiedergabe ihres Mobilgeräts zum Abhören von Sprachnachrichten verwenden, die private Informationen enthalten können.

Weitere Verwaltungsaufgaben im Zusammenhang mit Verfahren zum Schutz von Voicemail finden Sie unter [Geschützte Voicemail-Prozeduren](https://technet.microsoft.com/de-de/library/JJ938013(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Multimediawiedergabe geschützter Sprachnachrichten mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **UM-Postfachrichtlinie** \> **Geschützte Voicemail** das Kontrollkästchen neben **"Wiedergabe über Telefon" für geschützte Sprachnachrichten anfordern**, um diese Einstellung zu aktivieren. Deaktivieren Sie das Kontrollkästchen, um diese Einstellung zu deaktivieren.

4.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Aktivieren oder Deaktivieren der Multimediawiedergabe geschützter Sprachnachrichten

In diesem Beispiel wird den Benutzern, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, die Wiedergabe von Sprachnachrichten über die Medienwiedergabe gestattet.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -RequireProtectedPlayOnPhone $false

In diesem Beispiel wird verhindert, dass Benutzer, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, Sprachnachrichten über die Medienwiedergabe wiedergeben.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -RequireProtectedPlayOnPhone $true

