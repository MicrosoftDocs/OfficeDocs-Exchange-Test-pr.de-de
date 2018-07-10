---
title: 'Aktivieren eines UM-IP-Gateways: Exchange Online Help'
TOCTitle: Aktivieren eines UM-IP-Gateways
ms:assetid: 2706ae06-c45d-41b7-abbe-378a9fca104a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996857(v=EXCHG.150)
ms:contentKeyID: 50475372
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren eines UM-IP-Gateways

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-05_

Beim Erstellen eines UM-IP-Gateways (Unified Messaging) wird dessen Status standardmäßig auf "Aktiviert" festgelegt. Möglicherweise müssen Sie das UM-IP-Gateway jedoch deaktivieren, um es offline zu schalten und zu verhindern, dass es eingehende und ausgehende Anrufe annimmt. Nach dem Erstellen eines UM-IP-Gateways können Sie die Funktionalität über seine Statusvariable aktivieren oder deaktivieren.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](um-ip-gateway-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt und deaktiviert wurde. Weitere Informationen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren eines UM-IP-Gateways mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu \> **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie aktivieren möchten, und klicken Sie dann auf die NACH-OBEN-TASTE ![NACH-OBEN-TASTE (Symbol)](images/JJ150576.1732c727-328b-4a1a-b84d-6d7252c7dcab(EXCHG.150).gif "NACH-OBEN-TASTE (Symbol)").

2.  Klicken Sie auf der Seite **Warnung** auf **Ja**.

## Verwenden der Shell zum Erstellen eines UM-IP-Gateways

In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` aktiviert.

    Enable-UMIPGateway -Identity MyUMIPGateway

