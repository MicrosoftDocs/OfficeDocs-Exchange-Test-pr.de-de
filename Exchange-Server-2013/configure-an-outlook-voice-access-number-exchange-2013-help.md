---
title: 'Konfigurieren einer Outlook Voice Access-Nummer: Exchange 2013 Help'
TOCTitle: Konfigurieren einer Outlook Voice Access-Nummer
ms:assetid: 443c838e-f266-4893-b6b2-e5fc96579b55
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997680(v=EXCHG.150)
ms:contentKeyID: 50554806
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren einer Outlook Voice Access-Nummer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Eine Outlook Voice Access-Nummer ermöglicht es einem für Unified Messaging (UM) und Voicemailzugriff aktivierten Benutzer, mithilfe von Outlook Voice Access auf sein Postfach zuzugreifen. Wenn Sie eine Outlook Voice Access- oder Teilnehmerzugriffsnummer für einen Wählplan konfigurieren, können UM-aktivierte Benutzer die Teilnehmerzugriffsnummer anrufen, sich bei ihrem Postfach anmelden und dann auf E-Mails und Voicemailnachrichten, ihren Kalender und persönliche Kontaktinformationen zugreifen.

Beim Erstellen eines UM-Wählplans werden standardmäßig keine Outlook Voice Access-Nummern konfiguriert. Zum Konfigurieren einer Outlook Voice Access-Nummer müssen Sie zunächst einen Wählplan erstellen und dann eine Outlook Voice Access-Nummer unter der Option **Outlook Voice Access** des Wählplans konfigurieren. Auch wenn keine Outlook Voice Access-Nummer erforderlich ist, müssen Sie mindestens eine Outlook Voice Access-Nummer konfigurieren, um UM-aktivierten Benutzern die Verwendung von Outlook Voice Access für den Zugriff auf ihr Postfach zu ermöglichen. Sie können für einen einzelnen Wählplan auch mehrere Outlook Voice Access-Nummern konfigurieren.

Outlook Voice Access-Nummer können Buchstaben, numerische Zeichen und Sonderzeichen sowie Trennzeichen und Leerzeichen enthalten. Beispiel:

  - \+14255551010

  - \+1-425-555-1010

  - 4255551010

  - \+1 425 555 1010

  - 1-800-555-CALL

Weitere Informationen zu den Menüoptionen, die für Benutzer von Outlook Voice Access verfügbar sind, finden Sie in der Schnellreferenz zu Outlook Voice Access, die im [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?linkid=64645) abgerufen werden kann.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren einer Outlook Voice Access-Nummer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Geben Sie in **Outlook Voice Access** in das Feld unter **Outlook Voice Access-Nummern** die Nummer ein, die Sie verwenden möchten, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Klicken Sie auf **Speichern**.

## Konfigurieren einer Outlook Voice Access-Nummer mithilfe der Shell

In diesem Beispiel wird die Outlook Voice Access-Nummer für einen UM-Wählplan `MyUMDialPlan` auf "4255550100" festgelegt.

    Set-UMDialPlan -identity MyUMDialPlan -AccessTelephoneNumbers 4255550100

