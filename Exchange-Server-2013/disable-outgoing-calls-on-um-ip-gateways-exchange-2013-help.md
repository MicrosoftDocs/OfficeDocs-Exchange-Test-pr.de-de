---
title: 'Deaktivieren Sie ausgehende Anrufe für UM-IP-gateways: Exchange Online Help'
TOCTitle: Deaktivieren Sie ausgehende Anrufe für UM-IP-gateways
ms:assetid: a3777cc6-37e4-4359-ada3-a962ac0ef0c3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232153(v=EXCHG.150)
ms:contentKeyID: 50476345
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren Sie ausgehende Anrufe für UM-IP-gateways

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-13_

Sie können ausgehende Anrufe für ein UM-IP-Gateway (Unified Messaging) aktivieren oder deaktivieren. Wenn Sie das Kontrollkästchen **Ausgehende Anrufe über dieses UM-IP-Gateway zulassen** in den Eigenschaften des UM-IP-Gateways deaktivieren, konfigurieren Sie das UM-IP-Gateway so, dass ausgehende Anrufe an ein VoIP-Gateway, eine IP-Nebenstellenanlage oder einen SBC (Session Border Controller) nicht akzeptiert und gesendet werden. Obwohl die Einstellung **Ausgehende Anrufe über dieses UM-IP-Gateway zulassen** steuert, ob das UM-IP-Gateway ausgehende Anrufe für Benutzer initiieren kann, wirkt sie sich nicht auf Anrufübergaben oder eingehende Anrufe von einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einem SBC aus.

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

## Deaktivieren ausgehender Anrufe für ein UM-IP-Gateway mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Deaktivieren Sie auf der Seite **UM-IP-Gateway** das Kontrollkästchen für **Ausgehende Anrufe über dieses UM-IP-Gateway zulassen**.

3.  Klicken Sie auf **Speichern**.

## Deaktivieren ausgehender Anrufe für ein UM-IP-Gateway mithilfe der Shell

In diesem Beispiel werden ausgehende Anrufe für ein UM-IP-Gateway namens `MyUMIPGateway` deaktiviert.

    Set-UMIPGateway -Identity MyUMIPGateway -OutcallsAllowed $false

