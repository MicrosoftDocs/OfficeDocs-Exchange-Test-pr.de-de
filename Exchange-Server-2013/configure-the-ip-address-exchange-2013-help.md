---
title: 'Konfigurieren der IP-Adresse: Exchange 2013 Help'
TOCTitle: Konfigurieren der IP-Adresse
ms:assetid: 100541c1-2297-4c46-9602-b304736541a8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266940(v=EXCHG.150)
ms:contentKeyID: 50475100
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der IP-Adresse

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-11_

Bevor Sie ein Unified Messaging-IP-Gateway (UM) erstellen, müssen Sie die IP-Adresse oder den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) für das VoIP-Gateway, die IP-Nebenstellenanlage oder den Session Border Controller (SBC) definieren. Beim Erstellen des UM-IP-Gateways geben Sie diese IP-Adresse oder diesen FQDN an. Sie können die IP-Adresse oder den FQDN später ändern.

Die IP-Adresse und der FQDN können über die Exchange-Verwaltungskonsole oder über die Shell konfiguriert werden. In der Exchange-Verwaltungskonsole können Sie auf der Seite **UM-IP-Gateway** im Feld **Adresse** eine IPv4-IP-Adresse, eine IPv6-Adresse oder einen FQDN eingeben. Sie können die IPv4-IP-Adresse, die IPv6-Adresse oder den FQDN auch über den Parameter *Address* mit dem Cmdlet **Set-UMIPGateway** in der Shell angeben. Wenn Sie ein UM-IP-Gateway mit einem FQDN erstellen, müssen Sie die entsprechenden Hosteinträge (A) in der DNS-Forward-Lookupzone erstellen. Wenn die DNS-Konfiguration für das UM-IP-Gateway geändert wird, müssen Sie das UM-IP-Gateway deaktivieren und erneut aktivieren, damit sichergestellt ist, dass die Konfigurationsinformationen ordnungsgemäß aktualisiert werden.

Zusätzliche Verwaltungstasks im Zusammenhang mit UM-IP-Gateways finden Sie unter [UM-IP-Gateway – Verfahren](https://technet.microsoft.com/de-de/library/JJ822153(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-IP-Gateways" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-IP-Gateway erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-IP-Gateways](https://technet.microsoft.com/de-de/library/Aa998045(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren der IP-Adresse für ein UM-IP-Gateway mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, wählen Sie das UM-IP-Gateway aus, das Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Geben Sie auf der Seite **UM-IP-Gateway** im Feld **Adresse** die IP-Adresse für das VoIP-Gateway, die IP-Nebenstellenanlage oder den Session Border Controller (SBC) ein.

3.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.


> [!IMPORTANT]
> Wenn Sie anstelle einer IP-Adresse einen FQDN für das UM-IP-Gateway verwenden, vergewissern Sie sich, dass die richtigen DNS-Datensätze erstellt wurden.



## Konfigurieren der IP-Adresse für ein UM-IP-Gateway mithilfe der Shell

In diesem Beispiel wird ein UM-IP-Gateway namens `MyUMIPGateway` mit der IP-Adresse 10.10.10.1 konfiguriert.

    Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.1

In diesem Beispiel wird ein UM-IP-Gateway namens `MyUMIPGateway` mit der IP-Adresse 10.10.10.10 erstellt, das TCP-Port 5061 auf SIP-Anforderungen überwacht.

    Set-UMIPGateway -Identity MyUMIPGateway -Address 10.10.10.10 -Port 5061

In diesem Beispiel wird das UM-IP-Gateway `MyUMIPGateway` so konfiguriert, dass keine eingehenden und ausgehenden Anrufe akzeptiert werden. Außerdem wird eine IPv6-Adresse festgelegt, und das UM-IP-Gateway wird zur Verwendung von IPv4- und IPv6-Adressen konfiguriert.

    Set-UMIPGateway -Identity MyUMIPGateway -Address fe80::39bd:88f7:6969:d223%11 -IPAddressFamily Any -Status Disabled -OutcallsAllowed $false

