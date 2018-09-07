---
title: 'Konfigurieren Sie den Überwachungsport: Exchange Online Help'
TOCTitle: Konfigurieren Sie den Überwachungsport
ms:assetid: 200ecbd8-18c3-4594-9cc8-924b3ab4eca1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee633457(v=EXCHG.150)
ms:contentKeyID: 50554804
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren Sie den Überwachungsport

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können den TCP-Port konfigurieren, der für die Überwachung auf SIP-Anforderungen (Session Initiation-Protokoll) für ein UM-IP-Gateway (Unified Messaging) verwendet wird. Beim Erstellen eines UM-IP-Gateways wird die Nummer des TCP-Ports für die Überwachung auf SIP-Anforderungen standardmäßig auf 5060 festgelegt. Der TCP-SIP-Überwachungsport kann nicht mithilfe der Exchange-Verwaltungskonsole konfiguriert oder geändert werden. Sie müssen die Nummer des TCP-SIP-Überwachungsports mithilfe des Cmdlets **Set-UMIPGateway** konfigurieren.

Möglicherweise müssen Sie die Nummer des TCP-Überwachungsports auf 5061 festlegen, um folgende Aufgaben ausführen zu können:

  - Festlegen der VoIP-Sicherheitseinstellung für einen Satz UM-Wähleinstellungen auf "SIP-gesichert".

  - Festlegen der VoIP-Sicherheitseinstellung für einen Satz UM-Wähleinstellungen auf "Gesichert".

  - Integrieren in MicrosoftOffice Communications Server 2007 R2 oder Microsoft Lync Server.

  - Verwenden Sie MTLS (Mutual Transport Layer Security) zur Verschlüsselung von Netzwerkdaten zwischen Exchange-Servern und einem VoIP-Gateway, einer SIP-fähigen Nebenstellenanlage (Private Branch eXchange, PBX), einer IP-Nebenstellenanlage oder einem SBC (Session Border Controller).

Wenn Sie MTLS zwischen einem UM-IP-Gateway und einem Wählplan im Modus "SIP-gesichert" oder "Gesichert" verwenden möchten, müssen Sie beim Erstellen des UM-IP-Gateways dieses mit einem vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) konfigurieren und dann mithilfe der Shell das UM-IP-Gateway für die Überwachung von TCP-Port 5061 konfigurieren. Zudem müssen Sie überprüfen, ob alle VoIP-Gateways, für SIP aktivierten Nebenstellenanlagen, IP-Nebenstellenanlagen und SBCs auch für die Überwachung auf MTLS-Anforderungen an Port 5061 konfiguriert wurden.


> [!IMPORTANT]
> Wenn Sie ein UM-IP-Gateway mit einem FQDN erstellen, müssen Sie in Ihrer DNS-Forward-Lookupzone die geeigneten HOST (A)-Einträge erstellen. Wenn Sie ein UM-IP-Gateway mit einem FQDN erstellen und die DNS-Konfiguration für das UM-IP-Gateway geändert wird, müssen Sie das UM-IP-Gateway deaktivieren und dann wieder aktivieren, damit sichergestellt ist, dass die Konfigurationsinformationen des UM-IP-Gateways ordnungsgemäß aktualisiert werden.



Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-ip-gateway-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieses Verfahrens, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-ip-gateway).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Konfigurieren des TCP-Überwachungsports mit der Shell

In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` mit dem FQDN "mTLS.MyUMIPGateway.contoso.com" konfiguriert und überwacht TCP-Port 5061 auf SIP-Anforderungen.

    Set-UMIPGateway -Identity MyUMIPGateway -Address mTLS.MYUMIPGateway.contoso.com -Port 5061

In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` mit dem FQDN "SIPSecured.MyUMIPGateway.contoso.com" konfiguriert und überwacht TCP-Port 5061 auf SIP-Anforderungen.

    Set-UMIPGateway -Identity MyUMIPGateway -Address SIPSecured.MyUMIPGateway.contoso.com -Port 5061

In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` mit dem FQDN "MyOCSUMIPGateway.contoso.com" konfiguriert und überwacht TCP-Port 5061 auf SIP-Anforderungen.

    Set-UMIPGateway -Identity MyUMIPGateway -Address MyOCSUMIPGateway.contoso.com -Port 5061

