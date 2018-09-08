---
title: 'Festlegen von Outlook Voice Access-PIN-Richtlinien: Exchange Online Help'
TOCTitle: Festlegen von Outlook Voice Access-PIN-Richtlinien
ms:assetid: 5b2800b7-bfa6-4282-975c-0706ae25ad64
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998285(v=EXCHG.150)
ms:contentKeyID: 50554822
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Festlegen von Outlook Voice Access-PIN-Richtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können PIN-Richtlinien für eine Unified Messaging-Postfachrichtlinie (UM) festlegen. UM-Postfachrichtlinien können konfiguriert werden, um die Sicherheitsstufe für UM-aktivierte Benutzer zu erhöhen, die Outlook Voice Access verwenden, indem von Benutzern verlangt wird, dass sie die vordefinierten PIN-Richtlinien für Ihre Organisation einhalten.

Wenn Sie PIN-Richtlinien für Outlook Voice Access-Benutzer festlegen möchten, können Sie entweder eine neue UM-Postfachrichtlinie erstellen oder eine vorhandene UM-Postfachrichtlinie ändern. Nach dem Erstellen einer neuen UM-Postfachrichtlinie können Sie die UM-Postfachrichtlinie konfigurieren, indem Sie die folgenden PIN-Einstellungen konfigurieren:

  - `MinPasswordLength`

  - `PINLifetime`

  - `LogonFailuresBeforePINReset`

  - `MaxLogonAttempts`

  - `AllowCommonPatterns`

  - `PINHistoryCount`

Aus Sicherheitsgründen empfiehlt es sich, strenge PIN-Anforderungen für UM-Benutzer zu implementieren. Dies wird erreicht, indem Sie UM-PIN-Richtlinien erstellen, die PINs mit 6 oder mehr Stellen erfordern und den Grad an Sicherheit für das Netzwerk erhöhen.

Wenn Sie die PIN-Richtlinie ändern, wird die neue PIN-Einstellung auf die Benutzer angewendet, die zurzeit der UM-Postfachrichtlinie zugeordnet sind. Wenn Sie z. B. die UM-Postfachrichtlinie ändern und die PIN-Mindestlänge von 7 auf 10 Stellen erhöhen, werden Benutzer bei ihrer nächsten Anmeldung gezwungen, ihre PIN zu ändern, um der geänderten PIN-Anforderung zu genügen.

Informationen zu weiteren Aufgaben im Zusammenhang mit der Sicherheit der Outlook Voice Access-PIN finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Festlegen von PIN-Richtlinien für Outlook Voice Access-Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Klicken Sie in der Listenansicht auf den UM-Wählplan, den Sie bearbeiten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** eine UM-Postfachrichtlinie aus, die Sie bearbeiten möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf **Eigenschaften**.

4.  Klicken Sie auf der Seite **UM-Postfachrichtlinie** auf **PIN-Richtlinien**.

5.  Konfigurieren Sie auf der Seite **PIN-Richtlinien** die PIN-Einstellungen für Outlook Voice Access-Benutzer, die einer UM-Postfachrichtlinie zugeordnet sind, und klicken Sie dann auf **Speichern**.

## Festlegen von PIN-Richtlinien für Outlook Voice Access-Benutzer mithilfe der Shell

In diesem Beispiel werden die PIN-Einstellungen für Benutzer festgelegt, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugeordnet sind.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 8 -MaxLogonAttempts 12 -MinPINLength 8 -PINHistoryCount 10 -PINLifetime 60 -ResetPINText "The PIN used to allow you access to your mailbox using Outlook Voice Access has been reset."

