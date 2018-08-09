---
title: 'Aktiv. o. Deakt. der Sendung von Sprachnachrichten aus Outlook Voice Access'
TOCTitle: Aktivieren Sie oder deaktivieren Sie der sendenden Sprachnachrichten aus Outlook Voice Access
ms:assetid: 63544ae2-6a28-40b2-82fc-3df83e93ee56
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423546(v=EXCHG.150)
ms:contentKeyID: 52062710
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren Sie oder deaktivieren Sie der sendenden Sprachnachrichten aus Outlook Voice Access

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-12-13_

Sie können für Outlook Voice Access-Benutzer das Senden von Voicemailnachrichten an andere UM-aktivierte Benutzer, die demselben Wählplan zugeordnet sind, aktivieren oder deaktivieren.

Diese Einstellung ist standardmäßig aktiviert. Wenn Sie diese Einstellung deaktivieren, können Outlook Voice Access-Benutzer, die eine Outlook Voice Access-Nummer anrufen, keine Sprachnachrichten an Benutzer im selben Wählplan senden.

Zusätzliche Aufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole, um zu ermöglichen oder zu verhindern, dass Outlook Voice Access-Benutzer Sprachnachrichten an Benutzer im selben Wählplan senden

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Aktivieren Sie in **Weiterleitung und Suche** unter **Ermöglicht Anrufern Folgendes** die Option **Sprachnachrichten ohne Klingeln des Telefons des Benutzers hinterlassen**, um das Senden von Sprachnachrichten zuzulassen. Wenn Sie Benutzer am Senden von Sprachnachrichten hindern möchten, deaktivieren Sie diese Einstellung.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell, um zu ermöglichen oder zu verhindern, dass Outlook Voice Access-Benutzer Sprachnachrichten an Benutzer im selben Wählplan senden

In diesem Beispiel wird das Senden von Sprachnachrichten durch Outlook Voice Access-Benutzer, die dem Wählplan `MyUMDialPlan` zugeordnet sind, an Benutzer, die demselben Wählplan angehören, ermöglicht.

    Set-UMDialPlan -identity MyUMDialPlan -SendVoiceMsgEnabled $true

In diesem Beispiel wird das Senden von Sprachnachrichten durch Outlook Voice Access-Benutzer, die dem Wählplan `MyUMDialPlan` zugeordnet sind, an Benutzer, die demselben Wählplan angehören, verhindert.

    Set-UMDialPlan -identity MyUMDialPlan -SendVoiceMsgEnabled $false

