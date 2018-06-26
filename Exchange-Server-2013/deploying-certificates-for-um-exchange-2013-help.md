---
title: 'Bereitstellen von Zertifikaten für Unified Messaging: Exchange 2013 Help'
TOCTitle: Bereitstellen von Zertifikaten für Unified Messaging
ms:assetid: 95658f6f-eac2-4674-90e7-f2d3f25c5242
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee681661(v=EXCHG.150)
ms:contentKeyID: 52062878
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Zertifikaten für Unified Messaging

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-04-29_

Sie können MTLS (Mutual Transport Layer Security) verwenden, um Unified Messaging (UM) das Verschlüsseln von Daten zu ermöglichen, die zwischen Ihren Microsoft Exchange 2013-Servern und VoIP-Gateways, IP-Nebenstellenanlagen und Session Border Controllers (SBCs) und Microsoft Lync Server gesendet wurden. Zertifikate dienen zum Binden der Identität des Zertifikatbesitzers an ein Paar elektronischer Schlüssel (öffentlich und privat), die zum Verschlüsseln und digitalen Signieren von Informationen verwendet werden.

Wenn Sie SIP-gesicherte oder gesicherte Wählpläne in Ihrer Exchange 2010-Organisation verwenden, müssen Sie die verwendeten Zertifikate auf den Exchange 2013-Clientzugriffsservern mit dem Microsoft Exchange UM-Anrufrouterdienst und Postfachservern mit dem Microsoft Exchange UM-Dienst importieren. Sie können eines der folgenden Zertifikate für den UM-Dienst und den UM-Anrufrouterdienst verwenden:

  - Ein selbstsigniertes (Exchange-)Zertifikat

  - Ein internes PKI-Zertifikat (Public Key-Infrastruktur)

  - Ein Drittanbieterzertifikat

Bei der Installation von Unified Messaging wird standardmäßig ein selbstsigniertes Zertifikat erstellt und anschließend verwendet. Dieses selbstsignierte Zertifikate kann mit VoIP-Gateways, IP-Nebenstellenanlagen und SBCs, aber nicht bei Integration von UM mit Lync Server verwendet werden. Wenn Sie Zertifikate für die Nutzung mit Lync Server bereitstellen, müssen Sie mit dem Assistenten für Exchange-Zertifikate oder dem Cmdlet **New-ExchangeCertificate** ein Zertifikat beziehen, das von einer internen oder PKI-Zertifizierungsstelle ausgestellt wurde, oder ein Zertifikat eines anderen Anbieters erwerben, dem Unified Messaging und Lync Server gegenseitig vertrauen.

## Bereitstellen von Zertifikaten für VoIP-Gateways, IP-Nebenstellenanlagen und SBCs

Führen Sie die folgenden Schritte aus, um UM das Verschlüsseln von Daten zu ermöglichen, die zwischen VoIP-Gateways, IP-Nebenstellenanlagen und SBCs gesendet werden:

  - Verwenden Sie das selbstsignierte UM-Zertifikat, erstellen Sie eine neue Exchange-Zertifikatanforderung und beziehen Sie ein internes PKI-Zertifikat, oder erwerben Sie ein Drittanbieterzertifikat, das Sie für MTLS zwischen UM und VoIP-Gateways, IP-Nebenstellenanlagen und SBCs nutzen können.

  - Importieren Sie das Zertifikat, das auf allen Clientzugriffs- und Postfachservern in Ihrer Organisation verwendet wird.

  - Aktivieren Sie das Zertifikat für die Verwendung durch UM-Dienste.

  - Importieren Sie das Zertifikat auf Ihre VoIP-Gateways, IP-Nebenstellenanlagen und SBCs.

  - Konfigurieren Sie den UM-Wählplan als "SIP-gesichert" oder "Gesichert".

  - Konfigurieren Sie den UM-Startmodus auf den Clientzugriffs- und Postfachservern in Ihrer Organisation.

  - Erstellen Sie die benötigten UM-IP-Gateways mit einem vollständig qualifizierten Domänennamen (FQDN).

  - Konfigurieren Sie den Lauschport für die UM-IP-Gateways für die Verwendung von TCP-Port 5061.

  - Starten Sie den Unified Messaging-Anrufrouterdienst auf alle Clientzugriffsservern und den Microsoft Exchange Unified Messaging-Dienst auf allen Postfachservern neu.

## Bereitstellen von Zertifikaten für Lync Server

Führen Sie die folgenden Schritte aus, um zwischen UM und Lync Server gesendete Daten zu verschlüsseln:

  - Erstellen Sie eine neue Exchange-Zertifikatanforderung und beziehen Sie ein internes PKI-Zertifikat, oder erwerben Sie ein Drittanbieterzertifikat. Dem Zertifikat müssen UM und Lync Server gegenseitig vertrauen.

  - Importieren Sie das Zertifikat, das auf allen Clientzugriffs- und Postfachservern in Ihrer Organisation verwendet wird.

  - Aktivieren Sie das Zertifikat für die Verwendung durch UM-Dienste.

  - Importieren Sie das Zertifikat auf die Computer mit Lync Server.

  - Konfigurieren Sie den SIP-URI-UM-Wählplan als "SIP-gesichert" oder "Gesichert".

  - Konfigurieren Sie den UM-Startmodus auf den Clientzugriffs- und Postfachservern in Ihrer Organisation.

  - Führen Sie "OcsUmUtil.exe" auf einem Computer mit Lync Server aus.

  - Starten Sie den Unified Messaging-Anrufrouterdienst auf alle Clientzugriffsservern und den Microsoft Exchange Unified Messaging-Dienst auf allen Postfachservern in Ihrer Organisation neu. Weitere Informationen finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

  - Starten Sie den Lync Server-Front-End-Dienst auf allen Computern mit Lync Server neu, die zu einem Front-End-Pool der Enterprise Edition gehören, oder Front-End-Server der Standard Edition neu. Mit dem Cmdlet **Stop-CsWindowsService** können Sie Lync Server-Dienste beenden. Mit dem Cmdlet **Start-CsWindowsService** können Sie Lync Server-Dienste starten.
    
    Die Cmdlets **Start-CsWindowsService** und **Stop-CsWindowsService** ähneln den allgemeinen Windows PowerShell-Cmdlets **Start-Service** und **Stop-Service**. Sie können nach Wunsch einen Lync Server-Dienst mit dem Cmdlet **Start-Service** starten und mit dem Cmdlet **Stop-Service** beenden. Die Cmdlets **Start-CsWindowsService** und **Stop-CsWindowsService** enthalten den Parameter *ComputerName*, der das Beenden und Starten eines Lync Server-Diensts auf einem Remotecomputer vereinfacht. Hierzu müssen Sie den Parameter *ComputerName* und anschließend den vollqualifizierten Domänennamen des Remotecomputers angeben. Die Cmdlets **Start-Service** und **Stop-Service** haben keinen vergleichbaren Parameter.
    

    > [!NOTE]
    > Für die vollständige Integration von UM und Lync Server müssen Sie auch das Skript "ExchUcUtil.ps1" auf einem der Clientzugriffs- oder Postfachserver in der Organisation ausführen


