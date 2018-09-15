---
title: 'Festl. v. Postfachfkt. f. Outlook Voice Access-Benutzer: Exchange 2013-Hilfe'
TOCTitle: Festlegen von Postfachfunktionen für Outlook Voice Access-Benutzer
ms:assetid: 10960bf0-65cf-4d0b-bae5-d203c53662db
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996307(v=EXCHG.150)
ms:contentKeyID: 50554812
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen von Postfachfunktionen für Outlook Voice Access-Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Outlook Voice Access enthält zwei Schnittstellen: eine Benutzerschnittstelle für Telefoneingaben (Telephone User Interface, TUI) und eine Benutzerschnittstelle für Spracheingaben (Voice User Interface, VUI). Sie können die TUI-Einstellungen eines UM-aktivierten Benutzers konfigurieren, wenn der Benutzer mithilfe des Unified Messaging-Systems (UM) in Exchange 2013 auf ein Postfach zugreift. Wenn Sie die TUI-Einstellungen eines UM-aktivierten Benutzers für eine UM-Postfachrichtlinie ändern, wirken sich die Änderungen auf alle Benutzer aus, die der UM-Postfachrichtlinie zugeordnet sind. Sie können die folgenden TUI-Einstellungen für eine UM-Postfachrichtlinie ändern:

  - Zugriff ohne PIN auf Voicemail

  - Sprachantworten auf andere Nachrichten

  - TUI-Zugriff auf eigenen Kalender

  - TUI-Zugriff auf Verzeichnis

  - TUI-Zugriff auf eigene E-Mails

  - TUI-Zugriff auf eigene persönliche Kontakte


> [!NOTE]
> Nur mithilfe der Shell können Sie die TUI-Einstellungen für Outlook Voice Access für UM-aktivierte Benutzer ändern.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](https://technet.microsoft.com/de-de/library/JJ851061(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Ändern von TUI-Einstellungen für eine UM-Postfachrichtlinie

In diesem Beispiel werden TUI-bezogene Einstellungen für die UM-Postfachrichtlinie `MyUMMailboxPolicy` festgelegt.

    Set-UMMailbox -identity MyUMMailboxPolicy -AllowSubscriberAccess $true -AllowTUIAccessToCalendar $false -AllowTUIAccessToDirectory $false -AllowTUIAccessToEmail -$true -AllowTUIAccessToPersonalContacts $true

