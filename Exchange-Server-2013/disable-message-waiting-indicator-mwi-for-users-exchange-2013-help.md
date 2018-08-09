---
title: 'Deaktivieren der Anzeige für wartende Nachrichten: Exchange 2013-Hilfe'
TOCTitle: Deaktivieren der Nachricht wartet Indicator (MWI) für Benutzer
ms:assetid: 51cd6dc4-11d1-4eb9-a6c6-1965fcd24267
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673525(v=EXCHG.150)
ms:contentKeyID: 50554821
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren der Nachricht wartet Indicator (MWI) für Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Der Message Waiting Indicator (MWI) kann für Benutzer, die einer UM-Postfachrichtlinie (Unified Messaging) zugeordnet sind, aktiviert oder deaktiviert werden. Die meisten Legacy-Voicemailsysteme umfassen eine MWI-Funktion (Message Waiting Indicator). In der Regel wird dabei durch eine LED am Telefon des Voicemail-Teilnehmers signalisiert, dass eine neue Voicemailnachricht vorliegt. Der MWI kann auch eine SMS an das Mobiltelefon eines UM-aktivierten Benutzers senden. Die Standardeinstellung ist "Aktiviert".

Falls Message Waiting Indicator am UM IP-Gateway deaktiviert wird, ist das Feature für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, nicht verfügbar.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren von Message Waiting Indicator mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie auf der Seite **UM-Postfachrichtlinie** das Kontrollkästchen für **MWI (Message Waiting Indicator) zulassen**.

4.  Klicken Sie auf **Speichern**.

## Deaktivieren von Message Waiting Indicator mithilfe der Shell

In diesem Beispiel wird der Message Waiting Indicator für Benutzer deaktiviert, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowMessageWaitingIndicator $false

