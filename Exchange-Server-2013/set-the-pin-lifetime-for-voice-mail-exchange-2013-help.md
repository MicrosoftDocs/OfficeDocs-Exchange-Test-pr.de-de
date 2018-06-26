---
title: 'Legen Sie die PIN-Gültigkeitsdauer für Voicemail: Exchange Online Help'
TOCTitle: Legen Sie die PIN-Gültigkeitsdauer für Voicemail
ms:assetid: d17f0bf6-0ad6-40a4-bdd5-f7098f39250d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124712(v=EXCHG.150)
ms:contentKeyID: 50554915
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie die PIN-Gültigkeitsdauer für Voicemail

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-22_

Sie können die PIN-Gültigkeitsdauer für UM-aktivierte (Unified Messaging) Benutzer konfigurieren. Die PIN-Gültigkeitsdauer ist der maximale Zeitraum, den eine Outlook Voice Access-PIN für UM-aktivierte Empfänger gültig ist. Die PIN-Gültigkeitsdauereinstellung wird für eine UM-Postfachrichtlinie konfiguriert und gilt für alle UM-aktivierten Benutzer, die der UM-Postfachrichtlinie zugeordnet sind.

Für eine UM-Postfachrichtlinie können mehrere PIN-bezogene Einstellungen konfiguriert werden. Die PIN-Gültigkeitsdauer bestimmt den Zeitraum in Tagen ab dem Datum, an dem ein Outlook Voice Access-Benutzer seine PIN zuletzt geändert hat, bis zum Datum, an dem er gezwungen wird, diese erneut zu ändern. Der Wertebereich ist 0 bis 999, der Standardwert 60 Tage. Bei Eingabe von 0 läuft die PIN nicht ab. Diese Einstellung sollte nicht auf 0 festgelegt werden, da dadurch die Sicherheit Ihres Netzwerks stark gefährdet wird.


> [!IMPORTANT]
> Unified Messaging benachrichtigt Benutzer nicht, wenn ihre PIN in Kürze abläuft.



Informationen zu weiteren Aufgaben im Zusammenhang mit der Outlook Voice Access-PIN-Sicherheit finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfachrichtlinien" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der PIN-Gültigkeitsdauer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Wählen Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** die UM-Postfachrichtlinie aus, die Sie ändern möchten, und klicken Sie dann auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

4.  Klicken Sie auf **PIN-Richtlinien**, und geben Sie neben **PIN-Gültigkeitsdauer (Tage) erzwingen** einen Wert von 0 bis 999 ein.

5.  Klicken Sie auf **Speichern**.

## Konfigurieren der PIN-Gültigkeitsdauer mithilfe der Shell

In diesem Beispiel wird die PIN-Gültigkeitsdauer für Outlook Voice Access-Benutzer, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` unterliegen, auf 30 festgelegt.

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -PINLifetime 30

In diesem Beispiel werden die folgenden PIN-bezogenen Einstellungen für Outlook Voice Access Benutzer konfiguriert, die der UM-Postfachrichtlinie `MyUMMailboxPolicy` unterliegen.

  - Legt die Anzahl von Anmeldefehlern vor dem Zurücksetzen der Benutzer-PIN auf 3 fest.

  - Legt die maximale Anzahl von Anmeldeversuchen auf 5 fest.

  - Legt die minimale PIN-Länge auf 9 Ziffern fest.

  - Legt eine PIN-Gültigkeitsdauer von 40 Tagen fest.

<!-- end list -->

    Set-UMMailboxPolicy -Identity MyUMMailboxPolicy -LogonFailuresBeforePINReset 3
    -MaxLogonAttempts 5 -MinPINLength 9 -PINLifetime 40

