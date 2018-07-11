---
title: 'Konfigurieren Sie die maximale Aufzeichnung Dauer: Exchange Online Help'
TOCTitle: Konfigurieren Sie die maximale Aufzeichnung Dauer
ms:assetid: 18eeb567-1048-4c82-93cf-612cb12ec5e3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423539(v=EXCHG.150)
ms:contentKeyID: 50475104
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie die maximale Aufzeichnung Dauer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-09_

Sie können die maximale Anzahl an Minuten festlegen, die pro Sprachaufzeichnung zulässig ist, wenn ein Anrufer eine Sprachnachricht hinterlässt. Dieser Wert kann auf eine Zahl von 1 bis 100 festgelegt werden. In den meisten Organisationen kann die Standardeinstellung von 20 Minuten verwendet werden. Wenn Sie diesen Wert zu niedrig ansetzen, werden lange Sprachnachrichten möglicherweise vor ihrem Abschluss unterbrochen. Wird dieser Wert zu hoch eingestellt, können Benutzer übermäßig lange Sprachnachrichten im Posteingang speichern.

Diese Einstellung ist wichtig, wenn Sie strikte Datenträgerkontingente für Benutzer eingerichtet haben. Der Wert muss unterhalb des Werts der Einstellung für **Maximale Anrufdauer (Minuten)** liegen.

Zusätzliche Aufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der maximalen Aufzeichnungsdauer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Geben Sie im Abschnitt **Einstellungen** unter **Maximale Aufzeichnungsdauer (Minuten)** einen Wert in Minuten ein.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren der maximalen Aufzeichnungsdauer

In diesem Beispiel wird die maximale Aufzeichnungsdauer für den Satz UM-Wähleinstellungen "`MyUMDialPlan`" auf 10 Minuten festgelegt.

    Set-UMDialPlan -identity MyUMDialPlan -MaxRecordingDuration 10

