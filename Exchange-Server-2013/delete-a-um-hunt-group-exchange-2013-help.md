---
title: 'Dient zum Löschen eines UM-Sammelanschlusses.: Exchange Online Help'
TOCTitle: Dient zum Löschen eines UM-Sammelanschlusses.
ms:assetid: 11ac102d-b58d-486c-85b6-e096428e556d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996318(v=EXCHG.150)
ms:contentKeyID: 50554777
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Dient zum Löschen eines UM-Sammelanschlusses.

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-05_

Nachdem Sie den Unified Messaging-Sammelanschluss (UM) gelöscht haben, verarbeitet oder beantwortet das zum UM-Sammelanschluss gehörende UM-IP-Gateway keine eingehenden Anrufe mehr. Wenn das Löschen des UM-Sammelanschlusses dazu führt, dass keine konfigurierten Sammelanschlüsse für das UM-IP-Gateway verbleiben, ist das UM-IP-Gateway nicht mehr in der Lage, UM-Anrufe anzunehmen oder zu verarbeiten.

Informationen zu weiteren Aufgaben im Zusammenhang mit UM-Sammelanschlüssen finden Sie unter [Um-Sammelanschlüsse Gruppieren von Prozeduren](um-hunt-group-procedures-exchange-2013-help.md).


> [!WARNING]
> Wenn Sie die Einstellungen für den UM-Sammelanschluss ändern möchten, müssen Sie den Sammelanschluss löschen und dann einen neuen Sammelanschluss mit den entsprechenden Einstellungen erstellen.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Sammelanschlüsse" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Sammelanschluss erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Sammelanschlusses](create-a-um-hunt-group-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Löschen eines UM-Sammelanschlusses mit der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Klicken Sie in der Listenansicht auf den Wählplan, den Sie ändern möchten, und klicken Sie auf der Symbolleiste auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Wählen Sie auf der Seite **UM-Wählplan** unterhalb von **UM-Sammelanschlüsse** den Sammelanschluss aus, den Sie löschen möchten, und klicken Sie auf der Symbolleiste auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Klicken Sie auf der Seite **Warnung** auf **Ja**.

## Löschen eines UM-Sammelanschlusses mit der Shell

In diesem Beispiel wird der UM-Sammelanschluss `MyUMHuntGroup` gelöscht.

    Remove-UMHuntGroup -identity MyUMHuntGroup

