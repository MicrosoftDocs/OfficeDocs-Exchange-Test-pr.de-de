---
title: 'Konfigurieren Sie den Wert der Aufzeichnung Leerlauftimeout: Exchange Online Help'
TOCTitle: Konfigurieren Sie den Wert der Aufzeichnung Leerlauftimeout
ms:assetid: a7fb9a09-fde9-447d-ad2c-95598405e99b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423550(v=EXCHG.150)
ms:contentKeyID: 50476430
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie den Wert der Aufzeichnung Leerlauftimeout

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-11_

Sie können die Anzahl von Sekunden festlegen, in denen beim Aufzeichnen einer Sprachnachricht geschwiegen werden darf, bevor das Telefonat beendet wird. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung von 5 Sekunden festgelegt werden.

Sie können diesen Wert auf 2 bis 10 festlegen. Wenn Sie diesen Wert zu niedrig ansetzen, trennt das System möglicherweise die Verbindung, bevor die Sprachnachricht vollständig ist. Bei einer zu hohen Einstellung dieses Werts können Sprachnachrichten zu lange Pausen enthalten.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren des Werts "Aufzeichnungsleerlauf-Zeitüberschreitung" mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Geben Sie in **Einstellungen** unter **Aufzeichnungsleerlauf-Zeitüberschreitung (Sekunden)** den Wert in Sekunden ein.

5.  Klicken Sie auf **Speichern**.

## Konfigurieren des Werts "Leerlauftimeout für Aufzeichnung" mithilfe der Shell

In diesem Beispiel wird der Wert "Leerlauftimeout für Aufzeichnung" für die UM-Wähleinstellungen `MyUMDialPlan` auf "10" festgelegt.

    Set-UMDialPlan -identity MyUMDialPlan -RecordingIdleTimeout 10

