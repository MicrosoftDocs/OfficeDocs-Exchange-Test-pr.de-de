---
title: 'Aktivieren von Faxen für eine Gruppe von Benutzern: Exchange Online Help'
TOCTitle: Aktivieren von Faxen für eine Gruppe von Benutzern
ms:assetid: b8d9f54d-ff06-4942-83e1-fc6c4ad02178
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423556(v=EXCHG.150)
ms:contentKeyID: 52062773
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren von Faxen für eine Gruppe von Benutzern

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können eingehende Faxe für Benutzer aktivieren, die einer Unified Messaging-Postfachrichtlinie (UM) zugeordnet sind. Beim Aktivieren von Benutzern für Unified Messaging können Benutzer Faxnachrichten standardmäßig erst empfangen, nachdem Sie den URI für den Server des Faxpartners angegeben, einen Server des Faxpartners für die Organisation bereitgestellt und den Faxbetrieb in einer UM-Postfachrichtlinie aktiviert haben. Wenn die Option zum Zulassen eingehender Faxnachrichten im UM-Wählplan deaktiviert ist, können Benutzer, die der UM-Postfachrichtlinie zugeordnet sind, keine Faxnachrichten empfangen. Wenn die Option zum Zulassen eingehender Faxnachrichten für einen einzelnen Benutzer deaktiviert ist, kann dieser Benutzer keine Faxnachrichten empfangen.

Weitere Informationen zu Fax Partner finden Sie unter [Microsoft Hindernissen bei für Fax Partner](https://go.microsoft.com/fwlink/?linkid=190238).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Faxnachrichten finden Sie unter [Faxfunktion – Verfahren](faxing-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren des Eingangs von Faxnachrichten über die Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die Postfachrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Aktivieren Sie auf der Seite **UM-Postfachrichtlinie** \> **Allgemein** das Kontrollkästchen neben **Eingehende Faxe zulassen**.

4.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Aktivieren des Eingangs von Faxnachrichten über die Shell

Im folgenden Beispiel wird Benutzern, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind, die Verwendung des Faxeingangs ermöglicht.

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -AllowFax $true

