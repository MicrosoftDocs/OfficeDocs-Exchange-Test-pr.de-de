---
title: 'Aktivieren Sie ausgehende Anrufe für UM-IP-gateways: Exchange Online Help'
TOCTitle: Aktivieren Sie ausgehende Anrufe für UM-IP-gateways
ms:assetid: c3ad8e53-d37e-499e-b1f1-defb0ba1bd12
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673562(v=EXCHG.150)
ms:contentKeyID: 50476656
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren Sie ausgehende Anrufe für UM-IP-gateways

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2012-11-13_

Sie können ausgehende Anrufe für ein UM-IP-Gateway (Unified Messaging) aktivieren, wenn ausgehende Anrufe deaktiviert worden sind. Wenn Sie in den Eigenschaften des UM-IP-Gateways die Option **Ausgehende Anrufe über dieses UM-IP-Gateway zulassen** aktivieren, konfigurieren Sie das UM-IP-Gateway für das Annehmen und Senden von ausgehenden Anrufen von einem/an ein VoIP-Gateway (Voice over IP), von einer/an eine Nebenstellenanlage, die für SIP (Session Initiation Protocol) aktiviert ist, von einer/an eine IP-Nebenstellenanlage oder von einem/an einen SBC (Session Border Controller). Obwohl die Einstellung **Ausgehende Anrufe über dieses UM-IP-Gateway zulassen** steuert, ob das UM-IP-Gateway ausgehende Anrufe für Benutzer initiieren kann, wirkt sie sich nicht auf Anrufübergaben oder eingehende Anrufe von einem VoIP-Gateway, einer für SIP aktivierten Nebenstellenanlage, einer IP-Nebenstellenanlage oder einem SBC aus.

Das *Outdialing* beschreibt eine Situation, in der ein Benutzer in einem UM-Wählplan einen UM-aktivierten Benutzer in einem anderen Wählplan oder eine externe Telefonnummer anruft.

Um das Outdialing für UM-aktivierte Benutzer zu ermöglichen, müssen Sie die folgenden Aufgaben ausführen:

  - Bestätigen, dass das UM-IP-Gateway ausgehende Anrufe zulässt.

  - Erstellen von Wählregelgruppen, indem Wählregeleinträge für die UM-Wähleinstellungen erstellt werden, die dem UM-IP-Gateway zugeordnet sind.

  - Hinzufügen der richtigen Wählregelgruppen zur Liste der Wähleinschränkungen unter **Wählautorisierung** im UM-Wählplan, in der automatische Telefonzentrale oder der UM-Postfachrichtlinie.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](um-ip-gateway-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren ausgehender Anrufe für ein UM-IP-Gateway mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Aktivieren Sie auf der Seite **UM-IP-Gateway** das Kontrollkästchen für **Ausgehende Anrufe über dieses UM-IP-Gateway zulassen**.

3.  Klicken Sie auf **Speichern**.

## Aktivieren ausgehender Anrufe für ein UM-IP-Gateway mithilfe der Shell

Im folgenden Beispiel werden ausgehende Anrufe für ein UM-IP-Gateway mit Namen `MyUMIPGateway` aktiviert.

    Set-UMIPGateway -Identity MyUMIPGateway -OutcallsAllowed $true

