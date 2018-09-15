---
title: 'Aktivieren der MWI-Funktion für Benutzer: Exchange 2013-Hilfe'
TOCTitle: Aktivieren der MWI-Funktion (Message Waiting Indicator) für Benutzer
ms:assetid: 3d0ca657-00b6-4108-a850-b092fede1f75
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335216(v=EXCHG.150)
ms:contentKeyID: 50554774
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren der MWI-Funktion (Message Waiting Indicator) für Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Der Message Waiting Indicator (MWI) kann für Benutzer, die einer Unified Messaging-Postfachrichtlinie (UM) zugeordnet sind, aktiviert oder deaktiviert werden. Die meisten Legacy-Voicemailsysteme enthalten eine MWI-Funktion. In der Regel wird dabei durch eine LED am Telefon des Voicemail-Teilnehmers signalisiert, dass eine neue Voicemailnachricht vorliegt. Der MWI kann auch eine Textnachricht an das Mobiltelefon des UM-aktivierten Benutzers senden. Die Standardeinstellung lautet "Aktiviert".

Falls der MWI am UM-IP-Gateway deaktiviert wird, ist das Feature für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, nicht verfügbar.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](https://technet.microsoft.com/de-de/library/JJ851061(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren des MWI mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **UM-Postfachrichtlinie** das Kontrollkästchen neben **WMI (Waiting Message Indicator) zulassen**.

4.  Klicken Sie auf **Speichern**.

## Aktivieren des MWI mithilfe der Shell

In diesem Beispiel wird der MWI für Benutzer aktiviert, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowMessageWaitingIndicator $true

