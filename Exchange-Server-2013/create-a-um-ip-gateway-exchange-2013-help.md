---
title: 'Erstellen eines UM-IP-Gateways: Exchange 2013 Help'
TOCTitle: Erstellen eines UM-IP-Gateways
ms:assetid: 542d6b50-147b-4cec-b54d-61c7b8fc0fc7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)
ms:contentKeyID: 50475703
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.CreateUMIPGatewayWizardForm.CreateUMIPGatewayWizardPage
ms.translationtype: HT
---

# Erstellen eines UM-IP-Gateways

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-16_

Wenn Sie ein Unified Messaging-IP-Gateway erstellen, ermöglichen Sie Exchange-Servern das Herstellen einer Verbindung mit einem neuen VoIP-Gateway (Voice over IP), einer SIP-fähigen (Session Initiation Protocol) Nebenstellenanlage, einer IP-Nebenstellenanlage oder einem SBC (Session Border Controller). Unmittelbar nach dem Erstellen eines UM-IP-Gateways sollten Sie einen UM-Sammelanschluss erstellen und den UM-Sammelanschluss dann dem UM-IP-Gateway zuordnen. Das UM-IP-Gateway kann mehreren UM-Wähleinstellungen zugeordnet werden, indem ein oder mehrere UM-Sammelanschlüsse erstellt werden.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/um-ip-gateway-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines UM-IP-Gateways mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, und klicken Sie dann auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie auf der Seite **Neues UM-IP-Gateway** die folgenden Informationen ein:
    
      - **Name**   Geben Sie in diesem Feld einen eindeutigen Namen für das UM-IP-Gateway ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Namen des UM-IP-Gateways nach dem Erstellen ändern müssen, muss zuerst das vorhandene UM-IP-Gateway gelöscht und dann ein anderes UM-IP-Gateway mit dem gewünschten Namen erstellt werden. Der UM-IP-Gatewayname ist erforderlich, wird aber nur zur Anzeige verwendet. Da in Ihrer Organisation unter Umständen mehrere UM-IP-Gateways verwendet werden, sollten Sie aussagekräftige Namen für Ihre UM-IP-Gateways verwenden. Die maximale Länge eines UM-IP-Gatewaynamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Adresse**   Ein UM-IP-Gateway kann entweder mit einer IP-Adresse oder mit einem vollqualifizierten Domänennamen (FDQN) konfiguriert werden. Verwenden Sie dieses Feld, um die auf VoIP-Gateway, SIP-aktivierter Nebenstellenanlage, IP-Nebenstellenanlage oder SBC konfigurierte IP-Adresse oder einen vollqualifizierten Domänennamen (FQDN) anzugeben. In dieses Textfeld können nur gültige FQDNs eingegeben werden, die ordnungsgemäß formatiert sind.
        
        Sie können in diesem Feld Buchstaben und Zahlen eingeben. Es werden IPv4-Adressen, IPv6-Adressen und FQDNs unterstützt. Um MTLS (Mutual Transport Layer Security) zwischen einem UM-IP-Gateway und Wähleinstellungen zu aktivieren, die im SIP-gesicherten oder gesicherten Modus betriebenen werden, müssen Sie das UM-IP-Gateway mit einem FQDN konfigurieren. Außerdem müssen Sie das Gateway für die Überwachung von Port 5061 konfigurieren und sicherstellen, dass VoIP-Gateways oder IP-Nebenstellenanlagen ebenfalls für die Überwachung von Port 5061 auf Mutual TLS-Anforderungen konfiguriert wurden. Führen Sie zum Konfigurieren eines UM-IP-Gateways den folgenden Befehl aus: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`.
        
        Wenn Sie einen FQDN verwenden, müssen Sie außerdem sicherstellen, dass Sie für das VoIP-Gateway einen gültigen DNS-Hosteintrag konfiguriert haben, sodass der Hostname fehlerfrei in eine IP-Adresse aufgelöst werden kann. Auch wenn Sie anstelle einer IP-Adresse einen vollqualifizierten Domänennamen (FQDN) verwenden und die DNS-Konfiguration für das UM-IP-Gateway ändern, müssen Sie das UM-IP-Gateway deaktivieren und erneut aktivieren, um sicherzustellen, dass die Konfigurationsinformationen für das UM-IP-Gateway ordnungsgemäß aktualisiert werden.
    
      - **UM-Wählplan**   Klicken Sie auf **Durchsuchen**, um den UM-Wählplan auszuwählen, den Sie dem UM-IP-Gateway zuordnen möchten. Wenn Sie UM-Wähleinstellungen für die Zuordnung zu einem UM-IP-Gateway auswählen, wird außerdem ein UM-Sammelanschluss erstellt und diesen UM-Wähleinstellungen zugeordnet. Wenn Sie keine UM-Wähleinstellungen auswählen, müssen Sie einen UM-Sammelanschluss manuell erstellen und diesen dann dem erstellten UM-IP-Gateway zuordnen.

3.  Klicken Sie auf **Speichern**.

## Erstellen eines UM-IP-Gateways mit der Shell

In diesem Beispiel wird ein UM-IP-Gateway namens `MyUMIPGateway` erstellt, durch den Exchange-Server Anrufe von einem VoIP-Gateway, einer SIP-fähigen Nebenstellenanlage, einer IP-Nebenstellenanlage oder einem SBC mit der IP-Adresse 10.10.10.1 annehmen können.

    New-UMIPGateway -Name MyUMIPGateway -Address 10.10.10.1

In diesem Beispiel wird ein UM-IP-Gateway namens `MyUMIPGateway` erstellt, durch den Exchange-Server Anrufe von einem VoIP-Gateway, einer SIP-fähigen Nebenstellenanlage, einer IP-Nebenstellenanlage oder einem SBC mit dem FQDN "MyUMIPGateway.contoso.com" und Überwachung von Port 5061 annehmen können.

    New-UMIPGateway -Name MyUMIPGateway -Address "MyUMIPGateway.contoso.com" -Port 5061

In diesem Beispiel wird ein UM-IP-Gateway mit dem Namen `MyUMIPGateway` erstellt und verhindert, dass das UM-IP-Gateway eingehende Anrufe annimmt oder ausgehende Anrufe sendet, wird eine IPv6-Adresse festgelegt und wird für das UM-IP-Gateway die Verwendung von IPv4- und IPV6-Adressen unterstützt.

    New-UMIPGateway -Identity MyUMIPGateway -Address fe80::39bd:88f7:6969:d223%11 -IPAddressFamily Any -Status Disabled -OutcallsAllowed $false

