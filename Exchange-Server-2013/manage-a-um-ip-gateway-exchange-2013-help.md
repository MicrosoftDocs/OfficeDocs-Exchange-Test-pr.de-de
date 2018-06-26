---
title: 'Verwalten eines UM-IP-Gateways: Exchange 2013 Help'
TOCTitle: Verwalten eines UM-IP-Gateways
ms:assetid: 387e540f-8c59-42d2-a423-99fcf97e00aa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997283(v=EXCHG.150)
ms:contentKeyID: 50475322
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.UMIPGatewayGeneralPropertyPageControl
ms.translationtype: HT
---

# Verwalten eines UM-IP-Gateways

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-21_

Nachdem Sie ein UM-IP-Gateway erstellt haben, können Sie verschiedene Einstellungen anzeigen bzw. konfigurieren. Sie können beispielsweise die IP-Adresse oder einen vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) sowie Einstellungen für ausgehende Anrufe konfigurieren und die MWI-Funktion (Message Waiting Indicator) aktivieren bzw. deaktivieren.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](um-ip-gateway-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](create-a-um-dial-plan-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](create-a-um-ip-gateway-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Anzeigen oder Konfigurieren der Eigenschaften von UM-IP-Gateways mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**. Wählen Sie in der Listenansicht das UM-IP-Gateway aus, den Sie verwalten möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  
    
    Verwenden Sie die Seite **UM-IP-Gateway**, um die Einstellungen für das UM-IP-Gateway anzuzeigen und zu konfigurieren. Sie können außerdem die folgenden Einstellungen anzeigen oder konfigurieren:
    
      - **Status**   Dieses schreibgeschützte Feld zeigt den Status des UM-IP-Gateways an.
    
      - **Name**   Geben Sie in diesem Feld einen eindeutigen Namen für das UM-IP-Gateway ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Namen des UM-IP-Gateways nach dem Erstellen ändern müssen, muss zuerst das vorhandene UM-IP-Gateway gelöscht und dann ein anderes UM-IP-Gateway mit dem entsprechenden Namen erstellt werden. Der UM-IP-Gatewayname ist erforderlich, wird aber nur zur Anzeige verwendet. Da in Ihrer Organisation unter Umständen mehrere UM-IP-Gateways verwendet werden, sollten Sie aussagekräftige Namen für Ihre UM-IP-Gateways verwenden. Die maximale Länge eines UM-IP-Gatewaynamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen.
    
      - **Adresse**   Ein UM-IP-Gateway kann entweder mit einer IP-Adresse oder mit einem vollqualifizierten Domänennamen (FDQN) konfiguriert werden. Verwenden Sie dieses Feld, um die auf VoIP-Gateway, SIP-aktivierter Nebenstellenanlage, IP-Nebenstellenanlage oder SBC konfigurierte IP-Adresse oder einen vollqualifizierten Domänennamen (FQDN) anzugeben.
        
        Sie können in diesem Feld Buchstaben und Zahlen eingeben. Es werden IPv4-Adressen, IPv6-Adressen und FQDNs unterstützt. Wenn Sie einen FQDN verwenden, müssen Sie außerdem sicherstellen, dass Sie für das VoIP-Gateway einen gültigen DNS-Hosteintrag konfiguriert haben, sodass der Hostname fehlerfrei in eine IP-Adresse aufgelöst werden kann. Auch wenn Sie anstelle einer IP-Adresse einen vollqualifizierten Domänennamen (FQDN) verwenden und die DNS-Konfiguration für das UM-IP-Gateway ändern, müssen Sie das UM-IP-Gateway deaktivieren und erneut aktivieren, um sicherzustellen, dass die Konfigurationsinformationen für das UM-IP-Gateway ordnungsgemäß aktualisiert werden.
        
        Um MTLS (Mutual Transport Layer Security) zwischen einem UM-IP-Gateway und Wähleinstellungen zu aktivieren, die im SIP-gesicherten oder gesicherten Modus betriebenen werden, müssen Sie das UM-IP-Gateway mit einem FQDN konfigurieren. Außerdem müssen Sie das Gateway für die Überwachung von Port 5061 konfigurieren und sicherstellen, dass IP-Gateways oder IP-PBX-Anlagen ebenfalls für die Überwachung von Port 5061 auf Mutual TLS-Anforderungen konfiguriert wurden. Führen Sie zum Konfigurieren eines UM-IP-Gateways den folgenden Befehl aus: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`.
    
      - **Ausgehende Anrufe über diesen UM-IP-Gateway zulassen**   Aktivieren Sie dieses Kontrollkästchen, damit das UM-IP-Gateway ausgehende Anrufe akzeptiert und verarbeitet. Diese Einstellung wirkt sich nicht auf Anrufübergaben oder über ein VoIP-Gateway eingehende Anrufe aus.
        
        Beim Erstellen des UM-IP-Gateways ist diese Einstellung standardmäßig aktiviert. Wenn Sie diese Einstellung deaktivieren, können Anrufer, die dem Wählplan zugeordnet sind, keine ausgehenden Anrufe über das im Feld **Adresse** angegebene VoIP-Gateway, die definierte IP-Nebenstellenanlage oder den SBC tätigen.
    
      - **MWI (Message Waiting Indicator) zulassen**   Aktivieren Sie dieses Kontrollkästchen, wenn bei Anrufen über das UM-IP-Gateway Voicemailbenachrichtigungen an die Benutzer gesendet werden sollen. Mit dieser Einstellung kann das UM-IP-Gateway SIP-NOTIFY-Nachrichten für Benutzer empfangen und senden. Die Einstellung ist standardmäßig aktiviert und ermöglicht das Senden von Benachrichtigungen über wartende Nachrichten an Benutzer.
        
        MWI (Message Waiting Indicator) kann sich auf jeden Mechanismus beziehen, der das Vorhandensein einer neuen oder noch nicht abgehörten Nachricht signalisiert. Der Hinweis auf den Eingang einer neuen Sprachnachricht befindet sich bei Clients wie Outlook und Outlook Web App im Posteingang. Er kann in Form einer SMS (Short Messaging Service) oder Textnachricht an ein registriertes Mobiltelefon, als ausgehender Anruf von einem Exchange-Server an eine vorkonfigurierte Telefonnummer oder als Signalleuchte am Telefon eines Benutzers erfolgen.

## Konfigurieren der Eigenschaften von UM-IP-Gateways mit der Verwaltungsshell

In diesem Beispiel wird die IP-Adresse des UM-IP-Gateways `MyUMIPGateway` geändert.

    Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.1

In diesem Beispiel wird verhindert, dass das UM-IP-Gateway namens `MyUMIPGateway` eingehende Anrufe empfängt, und dass ausgehende Anrufe getätigt werden.

    Set-UMIPGateway -Identity MyUMIPGateway -Address voipgateway.contoso.com -Status 2 -OutcallsAllowed $false

In diesem Beispiel wird es dem UM-IP-Gateway ermöglicht, als VoIP-Gatewaysimulator zu fungieren. Das Beispiel kann mit dem Cmdlet **Test-UMConnectivity** verwendet werden.

    Set-UMIPGateway -Identity MyUMIPGateway -Simulator $true


> [!IMPORTANT]
> Es tritt eine gewisse Latenz auf, bevor alle Änderungen, die Sie an der Konfiguration eines UM-IP-Gateways vorgenommen haben, auf alle Exchange-Server repliziert wurden, die sich in demselben UM-Wählplan wie das UM-IP-Gateway befinden.



In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` so konfiguriert, dass keine eingehenden Anrufe akzeptiert und ausgehende Anrufe unterbunden werden. Außerdem wird eine IPv6-Adresse festgelegt, und das UM-IP-Gateway wird zur Verwendung von IPv4- und IPv6-Adressen konfiguriert.

    Set-UMIPGateway -Identity MyUMIPGateway -Address fe80::39bd:88f7:6969:d223%11 -IPAddressFamily Any -Status Disabled -OutcallsAllowed $false

## Anzeigen der Eigenschaften von UM-IP-Gateways mit der Verwaltungsshell

In diesem Beispiel wird eine formatierte Liste aller UM-IP-Gateways in der Active Directory-Gesamtstruktur angezeigt.

    Get-UMIPGateway |Format-List

In diesem Beispiel werden die Eigenschaften eines UM-IP-Gateways namens `MyUMIPGateway` angezeigt.

    Get-UMIPGateway -Identity MyUMIPGateway

In diesem Beispiel werden alle UM-IP-Gateways einschließlich der VoIP-Gatewaysimulatoren in der Active Directory-Gesamtstruktur angezeigt.

    Get-UMIPGateway -IncludeSimulator $true

