---
title: 'Konfigurieren eines vollqualifizierten Domänennamens: Exchange 2013 Help'
TOCTitle: Konfigurieren eines vollqualifizierten Domänennamens
ms:assetid: af093f87-59b7-44a8-a9a2-8f17f0cc7db8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee423553(v=EXCHG.150)
ms:contentKeyID: 50476483
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren eines vollqualifizierten Domänennamens

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-09_

Sie können ein Unified Messaging-IP-Gateway entweder mit einer IP-Adresse oder mit einem vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) konfigurieren. Wenn Sie ein UM-IP-Gateway erstellen, müssen Sie die IP-Adresse oder den FQDN definieren, die bzw. der für das verwendete VoIP-Gateway, die verwendete IP-Nebenstellenanlage oder den verwendeten Session Border Controller (SBC) konfiguriert ist. Sie können die IP-Adresse oder den FQDN nach dem Erstellen des UM-IP-Gateways ändern.

Wenn Sie ein UM-IP-Gateway mit einem FQDN erstellen, müssen Sie in Ihrer DNS-Forward-Lookupzone die geeigneten HOST (A)-Einträge erstellen. Wenn Sie ein UM-IP-Gateway mit einem FQDN erstellen und die DNS-Konfiguration für das UM-IP-Gateway geändert wird, müssen Sie das UM-IP-Gateway deaktivieren und dann wieder aktivieren, damit sichergestellt ist, dass die Konfigurationsinformationen ordnungsgemäß aktualisiert werden.

Um MTLS (Mutual Transport Layer Security) zwischen einem UM-IP-Gateway und Wähleinstellungen zu aktivieren, die im SIP-gesicherten oder gesicherten Modus betriebenen werden, müssen Sie das UM-IP-Gateway mit einem FQDN konfigurieren. Außerdem müssen Sie das Gateway so konfigurieren, dass es den Port 5061 überwacht, und sicherstellen, dass das VoIP-Gateway, die IP-Nebenstellenanlage oder der SBC ebenfalls für die Überwachung von Port 5061 auf Mutual TLS-Anforderungen konfiguriert ist. Führen Sie den folgenden Befehl aus, um ein UM-IP-Gateway zu konfigurieren: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-ip-gateway-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren eines FQDN mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Geben Sie auf der Seite **UM-IP-Gateway** in **Adresse** den FQDN für das VoIP-Gateway, die für SIP aktivierte Nebenstellenanlage, die IP-Nebenstellenanlage oder den SBC ein.

3.  Klicken Sie auf **Speichern**.


> [!IMPORTANT]
> Wenn Sie anstelle einer IP-Adresse einen FQDN für das UM-IP-Gateway verwenden, vergewissern Sie sich, dass die richtigen DNS-Einträge erstellt wurden.



## Konfigurieren eines FQDN mithilfe der Shell

In diesem Beispiel wird ein UM-IP-Gateway namens `MyUMIPGateway` mit dem FQDN "voipgateway.contoso.com" konfiguriert.

    Set-UMIPGateway -Identity MyUMIPGateway -Address voipgateway.contoso.com

In diesem Beispiel wird ein UM-IP-Gateway namens `MySBC` mit dem FQDN "sbc.contoso.com" konfiguriert, das den TCP-Port 5061 auf SIP-Anforderungen überwacht.

    Set-UMIPGateway -Identity MySBC -Address sbc.contoso.com -Port 5061

