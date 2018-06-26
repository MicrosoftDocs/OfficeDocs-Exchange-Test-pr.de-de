---
title: 'Konfigurieren der maximalen Anrufdauer: Exchange 2013 Help'
TOCTitle: Konfigurieren der maximalen Anrufdauer
ms:assetid: 01aa40d2-f918-472b-bace-158222143484
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423535(v=EXCHG.150)
ms:contentKeyID: 50474941
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der maximalen Anrufdauer

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-09_

Sie können die maximale Anzahl der Minuten angeben, für die bei einem eingehenden Anruf die Verbindung mit dem System ohne Umleitung auf eine zulässige Durchwahl erhalten bleibt, bevor der Anruf abgebrochen wird. Für die meisten Organisationen sollte dieser Wert auf die Standardeinstellung festgelegt werden: 30 Minuten. Diese Einstellung gilt für alle Anrufe, u. a. eingehende Outlook Voice Access-Anrufe, interne Sprachanrufe innerhalb der Organisation, Sprachanrufe an automatische UM-Telefonzentralen (Unified Messaging) sowie Faxanrufe von außerhalb der Organisation.

Dieser Wert kann auf eine Zahl zwischen 10 und 120 festgelegt werden. Wenn Sie diesen Wert zu niedrig ansetzen, werden eingehende Anrufe möglicherweise vor ihrem Abschluss unterbrochen. Wenn Ihre Organisation beispielsweise lange Faxnachrichten erhält, sollten Sie diesen Wert höher als den Standardwert festlegen, damit alle Seiten der Faxnachricht empfangen werden.

Zusätzliche Aufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der maximalen Anrufdauer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**.

2.  Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **UM-Wählplan** auf **Konfigurieren**.

4.  Geben Sie im Abschnitt **Einstellungen** unter **Maximale Anrufdauer (Minuten)** einen Wert in Minuten ein.

5.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Konfigurieren der maximalen Anrufdauer

In diesem Beispiel wird die maximale Anrufdauer für den Satz UM-Wähleinstellungen `MyUMDialPlan` auf 10 Minuten festgelegt.

    Set-UMDialPlan -identity MyUMDialPlan -MaxCallDuration 10

