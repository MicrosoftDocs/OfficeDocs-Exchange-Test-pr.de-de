---
title: 'Testen und Problembehandlung mit dem UM-Problembehandlungstool: Exchange 2013 Help'
TOCTitle: Testen und Problembehandlung mit dem UM-Problembehandlungstool
ms:assetid: 1fab2e52-bd2d-4e46-b222-53fee9d34cba
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg621148(v=EXCHG.150)
ms:contentKeyID: 56271560
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Testen und Problembehandlung mit dem UM-Problembehandlungstool

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Das Microsoft Exchange 2010 UM-Problembehandlungstool ist ein Cmdlet der Exchange-Verwaltungsshell mit dem Namen **Test-ExchangeUMCallFlow**. Sie können das Cmdlet zur Diagnose von Konfigurationsfehlern in Szenarien mit Mailboxansage oder zum Testen der Voicemailfunktion verwenden, sowohl für lokale als auch für standortübergreifende UM-Bereitstellungen mit Microsoft Exchange Server 2010 Service Pack 1 (SP1) oder höher. Sie können dieses Cmdlet in Bereitstellungen mit Microsoft Office , Microsoft Lync Server 2010 oder später oder in UM-Bereitstellungen mit VoIP-Gateways, IP/PBX-Anlagen oder SBCs (Session Border Controller) verwenden.

## Übersicht

Dieses Cmdlet emuliert Anrufe und führt eine Reihe von Diagnosetests aus, mit denen lokale Administratoren Konfigurationsfehler in Telefoniegeräten, Einstellungen für Exchange 2010 SP1 Unified Messaging oder höher sowie Probleme bei der Konnektivität zwischen lokalen und standortübergreifenden Bereitstellungen von Exchange 2010 SP1 Unified Messaging oder höher identifizieren können.

Wenn das Cmdlet ausgeführt wird, gibt es die Ursache und mögliche Lösungen für die erkannten Probleme an. Außerdem gibt es Metriken für die allgemeine Audioqualität aus, mit denen Probleme bei der Audioqualität im Zusammenhang mit der Netzwerkkonnektivität diagnostiziert werden können, z. B. Jitter und durchschnittlicher Paketverlust. Das Cmdlet **Test-ExchangeUMCallFlow** unterstützt das Testen von UM-Komponenten in Anrufen vom Typ `Secured`, `SIP Secured` und `Unsecured`. Es kann im Modus `Gateway` oder `SIPClient` ausgeführt werden.

Wenn Sie das UM-Problembehandlungstool ausführen, verwendet es standardmäßig die Anmeldeinformationen, die beim Anmelden am Computer verwendet wurden. Die verwendeten Anmeldeinformationen sind diejenigen, die für den anrufenden Teilnehmer angegeben sind. Sie müssen die Anmeldeinformationen festlegen oder angeben, wenn Sie das UM-Problembehandlungstool im `SIPClient`-Modus ausführen. Sie müssen die Anmeldeinformationen jedoch nicht festlegen, wenn Sie das UM-Problembehandlungstool im `Gateway`-Modus ausführen. Wenn Sie das UM-Problembehandlungstool im `SIPClient`-Modus verwenden möchten, sind weitere Anforderungen und Voraussetzungen für Office Communications Server 2007 R2 oder Lync Server 2010 zu erfüllen. Weitere Informationen finden Sie unter [Prüfliste: Bereitstellen von Office Communications Server 2007 R2 und Exchange 2010 Unified Messaging](https://go.microsoft.com/fwlink/p/?linkid=311961) oder [Prüfliste: Integrieren von Exchange 2013 UM in Lync Server](checklist-integrate-exchange-2013-um-with-lync-server-exchange-2013-help.md).


> [!IMPORTANT]
> Um nur die Voicemailfunktionalität eines Microsoft Exchange Server 2010 Unified Messaging-Servers zu testen, auf dem Exchange 2010 Service Pack 1 (SP1) oder Microsoft Exchange 2013 installiert ist, muss das Cmdlet <STRONG>Test-ExchangeUMCallFlow</STRONG> verwendet werden.



Das Cmdlet **Test-ExchangeUMCallFlow** kann auf einem lokalen Exchange 2010 Unified Messaging-Server, einem Exchange 2013-Postfachserver oder einem anderen 64-Bit-Computer installiert werden, auf dem eines der folgenden Betriebssysteme ausgeführt wird:

  - Betriebssystem Windows 7 oder Windows 8

  - Das Windows Server 2008- oder Windows Server 2008 R2-Betriebssystem

  - Das Windows Server 2012- oder Windows Server 2012 R2-Betriebssystem

Vor der Installation des Cmdlets **Test-ExchangeUMCallFlow** müssen auf einem Windows 7, Windows 8, Windows Server 2008 oder einem Windows Server 2012 64-Bit-Computer die folgenden Komponenten installiert werden:

  - Microsoft .NET Framework 3.5 Service Pack 1 (SP1). Informationen zum Herunterladen des Service Packs finden Sie unter [Microsoft .NET Framework 3.5 Service Pack 1](https://go.microsoft.com/fwlink/p/?linkid=152380).

  - Update der Microsoft .NET Framework 3.5-Familie für Windows Vista x64 und Windows Server 2008 x64-Updates, wenn das Tool auf einem Windows Vista oder Windows Server 2008-Computer ausgeführt wird. Das Update kann unter [Update der Microsoft .NET Framework 3.5-Familie für Windows Vista x64 und Windows Server 2008 x64](https://go.microsoft.com/fwlink/p/?linkid=178998) heruntergeladen werden.

  - Windows Remote Management (WinRM) 2.0 und Windows PowerShell V2 (Windows6.0-KB968930.msu). Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel 968930, [Windows Management Framework-Kernpaket (Windows PowerShell 2.0 und WinRM 2.0)](http://go.microsoft.com/fwlink/?linkid=3052%26kbid=968930).

  - Unified Communications Managed API 2.0, Core Runtime (64-Bit). Die Programmdatei "UcmaRuntimeWebDownloadX64.msi" steht unter [Unified Communications Managed API 2.0, Core Runtime (64-Bit)](https://go.microsoft.com/fwlink/?linkid=198175) zum Download bereit.

Das Cmdlet **Test-ExchangeUMCallFlow** ist auf der Exchange 2010 SP1-DVD bzw. im Exchange 2010 SP1-Download oder auf den Exchange 2013-Installationsmedien nicht enthalten. Sie können das Cmdlet jedoch über das [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=182625) herunterladen.

Weitere Informationen zu Syntax und Parametern finden Sie unter [Test-ExchangeUMCallFlow](https://technet.microsoft.com/de-de/library/ff630913\(v=exchg.150\)).

