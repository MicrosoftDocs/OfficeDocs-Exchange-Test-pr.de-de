---
title: 'Verwalten von UM-Einstellungen auf Clientzugriffsservern: Exchange 2013-Hilfe'
TOCTitle: Verwalten von UM-Einstellungen auf einem Clientzugriffsserver
ms:assetid: 08667911-fa86-404e-84b1-65cedd94d579
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673507(v=EXCHG.150)
ms:contentKeyID: 50554772
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von UM-Einstellungen auf einem Clientzugriffsserver

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-09_

Nach der Installation eines Clientzugriffsservers, auf dem der Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung ausgeführt wird, können Sie verschiedene Optionen konfigurieren. Dazu gehören die Anzahl gleichzeitiger Anrufe, die TCP- und TLS-Überwachungsports (Transport Layer Security), der Status und der Startmodus.


> [!NOTE]
> Es ist nicht erforderlich, dass Clientzugriffsserver einem UM-Wählplan hinzugefügt werden, bevor sie Anrufe für Unified Messaging (UM) verarbeiten können. Dies ist nur notwendig, wenn UM und Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integriert werden. Standardmäßig sind alle Clientzugriffsserver in einer Organisation für die Beantwortung eingehender Anrufe verfügbar.



Informationen zu weiteren Aufgaben im Zusammenhang mit Unified Messaging und Clientzugriffsservern finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Clientzugriffsserver (UM-Anrufrouterdienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass der Clientzugriffsserver auf demselben Computer wie der Postfachserver oder auf einem gesonderten Computer installiert ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren von Unified Messaging-Eigenschaften auf einem Clientzugriffsserver mithilfe der Shell

In diesem Beispiel wird ein Clientzugriffsserver mit dem Namen `MyClientAccessServer` aus allen SIP-Wählplänen (Session Initiation-Protokoll) entfernt.

    Set-UMCallRouterSettings -DialPlans $null - Server MyClientAccessServer

In diesem Beispiel wird der Clientzugriffsserver `MyClientAccessServer` zu einem SIP-Wählplan mit dem Namen `MySIPDialPlan` hinzugefügt. Darüber hinaus wird die maximale Anzahl eingehender Sprachanrufe festgelegt.

    Set-UMCallRouterSettings -DialPlans MySIPDialPlan -MaxCalls 150 -Server MyClientAccessServer

In diesem Beispiel wird auf einem Clientzugriffsserver mit dem Namen `MyClientAccessServer` der SIP-TCP-Überwachungsport auf 5077 und der Startmodus auf den Dualmodus festgelegt.

    Set-UMCallRouterSettings  -Server MyClientAccessServer-SipTCPListeningPort 5077 -UMStartUpMode -Dual 

## Verwenden der Shell zum Anzeigen von Clientzugriffsserver-Eigenschaften

In diesem Beispiel wird eine Liste aller Clientzugriffsserver angezeigt.

    Get-UMCallRouterSettings

In diesem Beispiel wird eine formatierte Liste der Eigenschaften für den Clientzugriffsserver angezeigt.

    Get-UMCallRouterSettings | Format-List

