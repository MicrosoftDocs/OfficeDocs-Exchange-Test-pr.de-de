---
title: 'Deaktivieren von Voicemailvorschau für Benutzer: Exchange Online Help'
TOCTitle: Deaktivieren von Voicemailvorschau für Benutzer
ms:assetid: 362fed13-3a9c-4111-bfa4-8c45ab6a3a01
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335199(v=EXCHG.150)
ms:contentKeyID: 51409288
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren von Voicemailvorschau für Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Sie können die Funktion "Voicemailvorschau" für Benutzer deaktivieren, die mit einer UM-Postfachrichtlinie verknüpft sind. Bei Deaktivierung dieser Einstellung wird verhindert, dass Benutzer den Text einer Voicemailnachricht im Nachrichtentext einer E-Mail- oder Textnachricht empfangen. Die Standardeinstellung ist "Aktiviert".

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf UM-Postfachrichtlinien finden Sie unter [UM-Postfachrichtlinien – Verfahren](um-mailbox-policy-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Weitere Informationen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren der Voicemailvorschau mithilfe der Exchange-Verwaltungskonsole

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, wählen Sie den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie verwalten möchten, und klicken Sie anschließend auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Deaktivieren Sie auf der Seite **UM-Postfachrichtlinie** \> **Allgemein** das Kontrollkästchen **Voicemailvorschau zulassen**.

4.  Klicken Sie auf **Speichern**.

## Deaktivieren der Voicemailvorschau mithilfe der Shell

In diesem Beispiel wird verhindert, dass Benutzer, die mit der UM-Postfachrichtlinie `MyUMMailboxPolicy` verknüpft sind, die Voicemailvorschau verwenden können.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy - AllowVoiceMailPreview $false

