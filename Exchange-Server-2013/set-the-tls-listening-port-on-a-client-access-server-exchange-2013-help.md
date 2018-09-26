---
title: 'Festl. d. Überw.ports f. TLS auf Clientzugriffsserver: Exchange 2013-Hilfe'
TOCTitle: Legen Sie den Überwachungsport für TLS auf einem Clientzugriffsserver
ms:assetid: f4401923-61fa-4dc5-95f8-c0d2f515b2ea
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673576(v=EXCHG.150)
ms:contentKeyID: 50554943
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Legen Sie den Überwachungsport für TLS auf einem Clientzugriffsserver

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-17_

Sie können den TLS (Transport Layer Security)-Port konfigurieren, der für die Überwachung auf SIP-Anforderungen auf einem Clientzugriffsserver verwendet wird, auf dem der Microsoft Exchange Unified Messaging-Anrufrouterdienst ausgeführt wird. Beim Installieren eines Clientzugriffsservers wird die Nummer des SIP-TLS-Überwachungsports standardmäßig auf 5061 gesetzt.

Möglicherweise müssen Sie den TLS-Überwachungsport auf 5061 festlegen, um folgende Aufgaben ausführen zu können:

  - Festlegen der VoIP-Sicherheitseinstellung für einen Satz UM-Wähleinstellungen auf "SIP-gesichert".

  - Festlegen der VoIP-Sicherheitseinstellung für einen Satz UM-Wähleinstellungen auf "Gesichert".

  - Integration mit MicrosoftOffice Office Communications Server 2007 R2 oder Microsoft Lync Server.

  - Verwenden von gegenseitiger Transport Layer Security (Mutual TLS oder MTLS) zur Verschlüsselung von Netzwerkdaten zwischen Postfachservern mit ausgeführtem Microsoft Exchange Unified Messaging-Dienst und VoIP-Gateways, SIP-fähigen (Session Initiation Protocol) Nebenstellenanlagen, IP-Nebenstellenanlagen oder Session Border Controller (SBCs).

Wenn Sie MTLS zwischen einem UM-IP-Gateway und einem Wählplan im Modus "SIP-gesichert" oder "Gesichert" verwenden möchten, müssen Sie beim Erstellen des UM-IP-Gateways dieses mit einem vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) konfigurieren und dann das UM-IP-Gateway für die Überwachung von TCP-Port 5061 konfigurieren. Zudem müssen Sie überprüfen, ob alle VoIP-Gateways, für SIP aktivierten Nebenstellenanlagen, IP-Nebenstellenanlagen oder SBCs auch für die Überwachung auf MTLS-Anforderungen an Port 5061 konfiguriert wurden.

Sie können TCP- und TLS-Ports nur für Clientzugriffsserver konfigurieren. Sie können die Ports nicht für einen Exchange-2013-Postfachserver konfigurieren. Allerdings können Sie mithilfe des Cmdlets **Set-UMService** die TCP- und TLS-Überwachungsports für Exchange 2010-UM-Server konfigurieren.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Unified Messaging und Clientzugriffsserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Clientzugriffsserver (UM-Anrufrouterdienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich, dass Clientzugriffs- und Postfachserver ordnungsgemäß installiert wurden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren des TLS-Überwachungsports für einen Clientzugriffsserver mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Geben Sie unter **UM-Diensteinstellungen** für **TLS-Überwachungsport** die Nummer des TLS-Ports ein, und klicken Sie dann auf **Speichern**.

## Konfigurieren des TLS-Überwachungsports für einen Clientzugriffsserver mithilfe der Shell

In diesem Beispiel wird der TLS-Überwachungsport für einen Clientzugriffsserver namens `MyClientAccessServer` auf 5561 festgelegt.

```powershell
Set-UMCallRouterSettings -Server MyClientAccessServer -SipTlsListeningPort 5561
```

