---
title: 'Ermöglichen o. Verhindern der Weiterleitung von Anr. v. Outlook Voice Access'
TOCTitle: Ermöglichen oder verhindern, dass Weiterleiten von Anrufen von Outlook Voice Access
ms:assetid: b80c57f1-394c-4608-8ad3-52a3e6d697db
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423554(v=EXCHG.150)
ms:contentKeyID: 52062772
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ermöglichen oder verhindern, dass Weiterleiten von Anrufen von Outlook Voice Access

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können für Outlook Voice Access-Benutzer das Weiterleiten von Anrufen an Benutzer, die einem Unified Messaging-Wählplan (UM) zugeordnet sind, aktivieren oder deaktivieren. Standardmäßig sind sowohl diese Option als auch die Option **Sprachnachrichten ohne Klingeln des Telefons des Benutzers hinterlassen** aktiviert, sodass Outlook Voice Access-Benutzer Anrufe an Benutzer im selben UM-Wählplan weiterleiten und Sprachnachrichten für sie hinterlassen können. Diese Einstellung gilt nur für Outlook Voice Access-Benutzer, die ihre PIN eingegeben und sich authentifiziert haben.

Zusätzliche Aufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Weiterleitung von Anrufen durch Outlook Voice Access-Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

3.  Aktivieren Sie in **Weiterleitung und Suche** unter **Ermöglicht Anrufern Folgendes** das Kontrollkästchen neben **Weiterleiten an Benutzer**, um Anrufern das Weiterleiten von Anrufen an andere Benutzer im Wählplan zu ermöglichen. Wenn Sie nicht möchten, dass Outlook Voice Access-Benutzer Anrufe an Benutzer weiterleiten, deaktivieren Sie dieses Kontrollkästchen.

4.  Klicken Sie auf **Speichern**.

## Aktivieren oder Deaktivieren der Weiterleitung von Anrufen durch Outlook Voice Access-Benutzer mithilfe der Shell

Dieses Beispiel ermöglicht Outlook Voice Access-Benutzern das Weiterleiten von Anrufen an Benutzer im selben Wählplan für den UM-Wählplan `MyUMDialPlan`.

    Set-UMDialPlan -identity MyUMDialPlan -AllowDialPlanSubscribers $true

Dieses Beispiel hindert Outlook Voice Access-Benutzern am Weiterleiten von Anrufen an Benutzer im selben Wählplan im UM-Wählplan `MyUMDialPlan`.

    Set-UMDialPlan -identity MyUMDialPlan -AllowDialPlanSubscribers $false

