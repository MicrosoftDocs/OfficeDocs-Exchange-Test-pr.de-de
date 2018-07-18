---
title: 'Zuweisen einer um-Postfachrichtlinie: Exchange Online Help'
TOCTitle: Zuweisen einer um-Postfachrichtlinie
ms:assetid: c8da6cbe-3d22-4fff-8b5a-416b1c8adb6c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201728(v=EXCHG.150)
ms:contentKeyID: 50476718
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Zuweisen einer um-Postfachrichtlinie

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-30_

Wenn Sie einen Benutzer für Unified Messaging (UM) und Voicemail aktivieren, müssen Sie die UM-Postfachrichtlinie auswählen, die dem Postfach des Benutzers zugeordnet wird. Sie können die UM-Postfachrichtlinie ändern, die dem Postfach des Benutzers zugeordnet ist, nachdem der Benutzer für Unified Messaging aktiviert wurde.

UM-Postfachrichtlinien werden erstellt, um eine allgemeine Zusammenstellung von Richtlinien und Sicherheitseinstellungen auf eine Gruppe von Postfächern UM-aktivierter Benutzer anzuwenden. Mithilfe von UM-Postfachrichtlinien können Sie beispielsweise die folgenden Einstellungen anwenden:

  - PIN-Richtlinien

  - Wähleinschränkungen

  - Andere allgemeine Eigenschaften von UM-Postfachrichtlinien


> [!NOTE]
> Standardmäßig wird jedes Mal, wenn Sie einen Satz mit UM-Wähleinstellungen erstellen, eine UM-Postfachrichtlinie erstellt. Abhängig von den Anforderungen Ihrer Organisation können Sie die standardmäßigen UM-Postfachrichtlinien löschen oder zusätzliche UM-Postfachrichtlinien erstellen.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der Benutzer für Unified Messaging aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern der einem UM-aktivierten Benutzer zugeordneten UM-Postfachrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dessen UM-Postfachrichtlinie Sie ändern möchten.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** \> **Unified Messaging** auf **Details anzeigen**.

4.  Klicken Sie auf der Seite **UM-Postfach** auf **UM-Postfacheinstellungen** und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

5.  Klicken Sie auf der Seite **UM-Postfach** neben **UM-Postfachrichtlinie** auf **Durchsuchen**, um die UM-Postfachrichtlinie für den Benutzer zu suchen.

6.  Klicken Sie auf **Speichern**.

## Ändern der einem UM-aktivierten Benutzer zugeordneten UM-Postfachrichtlinie mithilfe der Shell

In diesem Beispiel wird der UM-aktivierte Benutzer Tony Smith der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet.

    Set-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy

