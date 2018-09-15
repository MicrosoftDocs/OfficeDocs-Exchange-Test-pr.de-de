---
title: 'Konfig. d. Anz. Eingabefehl. vor Trennung der Outlook Voice Access-Benutzer'
TOCTitle: Die Anzahl der Eingabefehler zu konfigurieren, bevor Outlook Voice Access-Benutzer getrennt sind
ms:assetid: 64c13d17-a26a-4c9b-b495-bd69c716456a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423547(v=EXCHG.150)
ms:contentKeyID: 50475835
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Die Anzahl der Eingabefehler zu konfigurieren, bevor Outlook Voice Access-Benutzer getrennt sind

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-09_

Sie können die Anzahl der zulässigen fehlerhaften Eingaben konfigurieren, die Benutzer beim Anruf einer Outlook Voice Access-Nummer machen können, bevor die Verbindung beendet wird. Diese Einstellung gilt sowohl für Outlook Voice Access-Benutzer als auch für nicht authentifizierte Benutzer, die die Verzeichnissuche verwenden.

Im Folgenden werden Beispiele für Datentypen aufgeführt, die als falsch betrachtet werden:

  - Ein Anrufer fordert eine Durchwahl an, die nicht im System gefunden wird.

  - Das System kann die Durchwahl des Benutzers nicht finden, um den Anruf weiterzuleiten.

  - Ein Anrufer drückt eine Menüoption, die nicht gültig ist.

Der Wert dieser Einstellung kann zwischen 1 und 20 liegen. Für die meisten Organisationen sollte ein Standardwert von drei Versuchen festgelegt werden. Wird dieser Wert zu niedrig festgelegt, können Anrufer vorzeitig getrennt werden.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der Eingabefehler vor dem Trennen der Verbindung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Geben Sie im Abschnitt **Einstellungen** unter **Anzahl der Eingabefehler vor dem Trennen der Verbindung** die Anzahl von Eingabefehlern ein.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren der Eingabefehler vor dem Trennen der Verbindung

In diesem Beispiel wird die Anzahl der Eingabefehler vor dem Trennen der Verbindung in dem Satz UM-Wähleinstellungen `MyUMDialPlan` auf "5" festgelegt.

    Set-UMDialPlan -identity MyUMDialPlan -InputFailuresBeforeDisconnect 5

