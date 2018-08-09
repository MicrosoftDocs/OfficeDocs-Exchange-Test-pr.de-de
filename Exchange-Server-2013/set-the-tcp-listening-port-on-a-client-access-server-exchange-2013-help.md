---
title: 'Festl. d. TCP-Überwachungsports auf Clientzugriffsserver: Exchange 2013-Hilfe'
TOCTitle: Festlegen des TCP-Überwachungsports auf einem Clientzugriffsserver
ms:assetid: 5f48f21a-d8d4-48b2-868f-9a3647693841
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673530(v=EXCHG.150)
ms:contentKeyID: 50554826
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Festlegen des TCP-Überwachungsports auf einem Clientzugriffsserver

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-09_

Sie können den TCP-Port konfigurieren, der für die Überwachung auf SIP-Anforderungen für einen Clientzugriffsserver mit dem Microsoft Exchange Unified Messaging-Anrufrouterdienst verwendet wird. Standardmäßig wird beim Installieren eines Clientzugriffsservers die Nummer des SIP-TCP-Überwachungsports auf 5060 festgelegt, und der Clientzugriffsserver wird im TCP-Modus gestartet. Der SIP-TCP-Überwachungsport kann nicht mithilfe der Exchange-Verwaltungskonsole konfiguriert werden. Sie müssen die Nummer des SIP-TCP-Überwachungsports mithilfe des Cmdlets **Set-UMCallRouterSettings** konfigurieren.

Möglicherweise müssen Sie den TCP-Überwachungsport auf 5061 festlegen, wenn Ihre VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs (Session Border Controller) zur Verwendung eines TCP-Ports konfiguriert sind, der vom SIP-Standardport 5060 abweicht.

Sie können nur TCP- und TLS-Ports für Clientzugriffsserver konfigurieren. Sie können nicht die Ports für einen Exchange 2013-Postfachserver konfigurieren. Allerdings können Sie mithilfe des Cmdlets **Set-UMService** die TCP- and TLS-Überwachungsports für Exchange 2010-UM-Server konfigurieren.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Unified Messaging und Clientzugriffsserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Clientzugriffsserver (UM-Dienst für die Anrufweiterleitung)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich, dass die Clientzugriffs- und Postfachserver korrekt installiert wurden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren des TCP-Überwachungsports auf einem Clientzugriffsserver mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Server** \> **Server**.

2.  Wählen Sie in der Listenansicht den Exchange-Server aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **Exchange Server** auf **Unified Messaging**.

4.  Geben Sie Im Abschnitt **UM-Anrufroutereinstellungen** unter **TCP-Überwachungsport** die Nummer für den TCP-Port ein, und klicken Sie auf **Speichern**.

## Konfigurieren des TCP-Überwachungsports auf einem Clientzugriffsserver mithilfe der Shell

In diesem Beispiel wird der TCP-Überwachungsport auf einem Clientzugriffsserver namens `MyClientAccessServer` auf 5566 festgelegt.

    Set-UMCallRouterSettings -Server MyClientAccessServer -SipTCPListeningPort 5566

