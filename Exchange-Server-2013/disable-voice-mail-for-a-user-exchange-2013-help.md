---
title: 'Deaktivieren von Voicemail für einen Benutzer: Exchange Online Help'
TOCTitle: Deaktivieren von Voicemail für einen Benutzer
ms:assetid: cecc9c0d-377d-489e-9db4-d487e9c0b552
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124691(v=EXCHG.150)
ms:contentKeyID: 50476717
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren von Voicemail für einen Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Sie können die Unified Messaging (UM) für einen UM-aktivierten Benutzer deaktivieren. Wenn Sie dies tun, kann der Benutzer die Voicemailfunktionen in Unified Messaging nicht mehr verwenden. Wenn Sie bevorzugen, wenn Sie, UM für einen Benutzer deaktivieren, können Sie die UM-Einstellungen für den Benutzer belassen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der vorhandene Benutzer für Unified Messaging aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren von Unified Messaging und Voicemail für einen Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger**.

2.  Wählen Sie in der Listenansicht den Benutzer aus, dessen Postfach für Unified Messaging deaktiviert werden soll.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** unter **Unified Messaging** auf **Deaktivieren**.

4.  Klicken Sie im Dialogfeld mit der Warnung auf **Ja**, um zu bestätigen, dass Unified Messaging für diesen Benutzer deaktiviert wird.

## Deaktivieren von Unified Messaging und Voicemail für einen Benutzer mithilfe der Shell

In diesem Beispiel werden Unified Messaging und Voicemail für "tonysmith@contoso.com" deaktiviert, die UM-Postfacheinstellungen werden jedoch beibehalten.

    Disable-UMMailbox -Identity tonysmith@contoso.com -KeepProperties $True

