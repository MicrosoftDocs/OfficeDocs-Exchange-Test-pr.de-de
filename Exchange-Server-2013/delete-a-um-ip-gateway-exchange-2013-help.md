---
title: 'Löschen eines UM-IP-Gateways: Exchange Online Help'
TOCTitle: Löschen eines UM-IP-Gateways
ms:assetid: 569d3741-67dd-4597-8d28-010011be0c12
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998214(v=EXCHG.150)
ms:contentKeyID: 50475688
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Löschen eines UM-IP-Gateways

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Wenn Sie ein UM-IP-Gateway (Unified Messaging) löschen, können Exchange-Server eingehende Anrufe von dem VoIP-Gateway (Voice over IP), der SIP-fähigen Nebenstellenanlage (Session Initiation Protocol), der IP-Nebenstellenanlage oder dem Session Border Controller (SBC), die dem UM-IP-Gateway zugeordnet sind, nicht länger annehmen.


> [!IMPORTANT]
> Sie sollten ein UM-IP-Gateway nur löschen, wenn Sie genau wissen, wie sich die Deaktivierung der Kommunikation mit einem VoIP-Gateway, einer IP-Nebenstelle oder einem SBC auswirkt.



Informationen zu weiteren Aufgaben in Bezug auf UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-ip-gateway-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Löschen eines UM-IP-Gateways mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie löschen möchten, und klicken Sie auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

2.  Klicken Sie auf der Seite **Warnung** auf **Ja**.

## Verwenden der Shell zum Löschen eines UM-IP-Gateways

In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` gelöscht.

    Remove-UMIPGateway -Identity MyUMIPGateway

