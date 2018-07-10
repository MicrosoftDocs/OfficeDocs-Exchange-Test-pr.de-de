---
title: 'Deaktivieren von ausgewählten Features für Outlook Voice Access-Benutzer: Exchange Online Help'
TOCTitle: Deaktivieren von ausgewählten Features für Outlook Voice Access-Benutzer
ms:assetid: 37421edf-af60-4ca9-9e8b-262b8b851607
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg602126(v=EXCHG.150)
ms:contentKeyID: 50554770
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren von ausgewählten Features für Outlook Voice Access-Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Outlook Voice Access enthält zwei Schnittstellen: die Benutzerschnittstelle für Telefoneingabe (Telephone User Interface, TUI) und die Benutzerschnittstelle für Spracheingabe (Voice User Interface, VUI). Wenn sich ein Benutzer in Outlook Voice Access eingewählt hat, kann er standardmäßig auf seinen Kalender, seine E-Mails und seine persönlichen Kontakte zugreifen sowie das Verzeichnis durchsuchen. Sie können die Shell dazu verwenden, die Benutzer am Zugriff auf eines oder mehrere dieser Features zu hindern, wenn sie Outlook Voice Access für den Zugriff auf ihre Postfächer nutzen. Wenn Sie Outlook Voice Access-Funktionen in einer Unified Messaging-Postfachrichtlinie (UM) ändern, wirken sich die Änderungen auf alle Benutzer aus, denen die UM-Postfachrichtlinie zugeordnet ist.

In einer UM-Postfachrichtlinie können Sie für Benutzer den Zugriff auf folgende Outlook Voice Access-Funktionen deaktivieren:

  - Kalender

  - Verzeichnis

  - E-Mail

  - Persönliche Kontakte

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

Sie können die Shell auch dazu verwenden, Outlook Voice Access-Features im Postfach eines einzelnen UM-aktivierten Benutzers zu deaktivieren. Dann werden die Features nur für diesen Benutzer deaktiviert. Sie können zwar nicht alle Outlook Voice Access-Features einer UM-Postfachrichtlinie für einen einzelnen Benutzer deaktivieren, aber Sie können den Zugriff auf seinen Kalender und seine E-Mails deaktivieren.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit UM-Postfächern finden Sie unter [Voicemail für Benutzer](voice-mail-for-users-exchange-2013-help.md).


> [!NOTE]
> Sie können die Outlook Voice Access-Features für UM-aktivierte Benutzer in einer UM-Postfachrichtlinie oder im Postfach eines einzelnen UM-aktivierten Benutzers nur mithilfe der Shell ändern.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Weitere Informationen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein Benutzer für UM aktiviert wurde. Weitere Informationen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren von ausgewählten Outlook Voice Access-Funktionen für UM-aktivierte Benutzer in einer UM-Postfachrichtlinie mithilfe der Shell

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

In diesem Beispiel werden Benutzer, denen die UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet ist, am Zugriff auf ihren Kalender gehindert, wenn sie sich in Outlook Voice Access einwählen.

    Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToCalendar $false

In diesem Beispiel werden Benutzer, denen die UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet ist, am Zugriff auf das Verzeichnis gehindert, wenn sie sich in Outlook Voice Access einwählen.

    Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToDirectory $false

In diesem Beispiel werden Benutzer, denen die UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet ist, am Zugriff auf ihre E-Mails gehindert, wenn sie sich in Outlook Voice Access einwählen.

    Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToEmail -$false

In diesem Beispiel werden Benutzer, denen die UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet ist, am Zugriff auf ihre persönlichen Kontakte gehindert, wenn sie sich in Outlook Voice Access einwählen.

    Set-UMMailboxPolicy -id MyUMMailboxPolicy -AllowTUIAccessToPersonalContacts $false

## Deaktivieren von ausgewählten Outlook Voice Access-Funktionen im Postfach eines einzelnen UM-aktivierten Benutzers mithilfe der Shell

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

In diesem Beispiel wird der Zugriff auf den Kalender in einem UM-Postfach mit dem Namen "tony@contoso.com" deaktiviert, wenn sich der Benutzer in Outlook Voice Access einwählt.

    Set-UMMailbox -id tony@contoso.com -TUIAccessToCalendarEnabled $false

In diesem Beispiel wird der Zugriff auf die E-Mails in einem UM-Postfach mit dem Namen "tony@contoso.com" deaktiviert, wenn sich der Benutzer in Outlook Voice Access einwählt.

    Set-UMMailbox -id tony@contoso.com -TUIAccessToEmailEnabled $false

