---
title: 'Deaktivieren eines UM-IP-Gateways: Exchange Online Help'
TOCTitle: Deaktivieren eines UM-IP-Gateways
ms:assetid: fe3a8797-1230-49cb-a839-ccec238266b6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125257(v=EXCHG.150)
ms:contentKeyID: 50477147
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren eines UM-IP-Gateways

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-13_

Beim Erstellen eines UM-IP-Gateways (Unified Messaging) wird dessen Status standardmäßig auf "Aktiviert" festgelegt. Nachdem Sie das UM-IP-Gateway erstellt haben, können Sie dessen Betrieb deaktivieren, indem Sie seinen Status auf "Deaktiviert" festlegen. Nachdem Sie das UM-IP-Gateway deaktiviert haben, können das VoIP-Gateway (Voice over IP), die IP-Nebenstellenanlage (Private Branch eXchange, PBX) bzw. der Session Border Controller (SBC) eingehende Unified Messaging-Anrufe nicht länger verarbeiten.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://technet.microsoft.com/de-de/library/JJ822153(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt und aktiviert wurde. Weitere Informationen finden Sie unter [Erstellen eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)) und [Aktivieren eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa996857(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren eines UM-IP-Gateways mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie deaktivieren möchten, und klicken Sie dann auf die **NACH-UNTEN-TASTE**![NACH-UNTEN-TASTE (Symbol)](images/JJ150576.ef5ca57d-a033-457b-bd92-6361877c33d0(EXCHG.150).gif "NACH-UNTEN-TASTE (Symbol)").

2.  Klicken Sie auf der Seite **Warnung** auf **Ja**.

## Deaktivieren eines UM-IP-Gateways mithilfe der Shell

In diesem Beispiel wird das UM-IP-Gateway namens `MyUMIPGateway` deaktiviert. Es werden keine eingehenden Anrufe des VoIP-Gateways, der IP-PBX oder des SBC mehr akzeptiert.

    Disable-UMIPGateway -Identity MyUMIPGateway

In diesem Beispiel wird das UM-IP-Gateway namens `MyUMIPGateway` deaktiviert, und alle aktuellen Anrufe werden sofort unterbrochen.

    Disable-UMIPGateway -Identity MyUMIPGateway -Immediate $true

