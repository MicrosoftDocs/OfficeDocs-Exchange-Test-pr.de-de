---
title: 'Hybridverwaltung in Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Hybridverwaltung in Exchange-Hybridbereitstellungen
ms:assetid: 233f9f34-3ff5-47e1-a9e8-3244ee868d6e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659048(v=EXCHG.150)
ms:contentKeyID: 50477187
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hybridverwaltung in Exchange-Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

Bei der Installation eines Exchange-Servers werden automatisch die Exchange-Verwaltungstools auf dem Server installiert. Mit den folgenden Tools konfigurieren und verwalten Sie sowohl die lokale Exchange als auch die Exchange Online-Organisation:

  - **Exchange-Verwaltungskonsole (Exchange Administration Center, EAC)**   Die EAC ist eine webbasierte Verwaltungskonsole, die sich durch einfache Bedienung auszeichnet und für lokale, Online- oder Hybridbereitstellungen von Exchange optimiert ist. Die EAC ersetzt die bisherige Exchange-Verwaltungskonsole (Exchange Management Console, EMC) und Exchange-Systemsteuerung (Exchange Control Panel, ECP), die zur Verwaltung von Exchange Server 2010 verwendet wurden.

  - **Exchange-Verwaltungsshell (Exchange Management Shell, EMS)**   Die Exchange-Verwaltungsshell ist eine Befehlszeilenschnittstelle auf Basis von Windows PowerShell.

## Exchange Admin Center

Mithilfe der EAC können Sie vielfältige Bereitstellungstasks und die häufigsten alltäglichen Verwaltungstasks sowohl an den lokalen Exchange-Servern als auch in der Exchange Online-Organisation ausführen. Sie wird standardmäßig auf jedem Exchange 2013- oder neuerem Server installiert. Da es sich um eine webbasierte Verwaltungskonsole handelt, können Sie darauf auch mit Webbrowsern auf anderen Computern in Ihrem Netzwerk oder über das Internet unter Verwendung der URL des virtuellen Verzeichnisses der ECP zugreifen.

Für den Zugriff auf die Exchange Online-Organisation in der EAC wählen Sie die Office 365-Registerkarte für standortübergreifende Navigation aus. Mithilfe der standortübergreifenden Navigation können Sie schnell zwischen Ihrer Exchange Online-Organisation und Ihrer lokalen Exchange-Organisation wechseln. Falls Sie eine Hybridbereitstellung konfiguriert haben, können Sie auf der Office 365-Registerkarte die Exchange Online-Organisation sowie Empfängerobjekte verwalten. Wenn Sie keine Exchange Online-Organisation haben, gelangen Sie durch Klicken auf den Office 365-Link auf die Anmeldeseite für Office 365.

Weitere Informationen zur EAC finden Sie unter [Exchange Admin Center in Exchange 2013](https://technet.microsoft.com/de-de/library/jj150562\(v=exchg.150\)).

## Die Exchange-Verwaltungsshell

Mithilfe der Exchange-Verwaltungsshell können Sie alle Tasks der EAC sowie einige zusätzliche Tasks ausführen, die ausschließlich in der Exchange-Verwaltungsshell möglich sind. Die Exchange-Verwaltungsshell ist eine Sammlung von Windows PowerShell-Skripts und -Cmdlets, die zusammen mit den Exchange-Verwaltungstools auf dem Computer installiert werden. Diese Skripts und Cmdlets werden nur dann geladen, wenn Sie die Exchange-Verwaltungsshell über das Symbol Exchange-Verwaltungsshell öffnen. Wenn Sie Windows PowerShell direkt öffnen, werden die Exchange-Skripts und -Cmdlets nicht geladen, und Sie können die lokale Organisation nicht verwalten.


> [!NOTE]
> Sie können eine manuelle Windows PowerShell-Verbindung mit Ihrer lokalen Organisation auf ähnliche Weise erstellen wie eine manuelle Verbindung mit der Exchange Online-Organisation. Es empfiehlt sich jedoch, die Exchange-Verwaltungsshell zum Verwalten Ihrer lokalen Exchange-Server über das entsprechende Symbol Exchange-Verwaltungsshell zu öffnen.



Wenn Sie die Exchange-Verwaltungsshell über das Symbol Exchange-Verwaltungsshell auf einem Computer öffnen, auf dem die Verwaltungstools installiert sind, können Sie die lokale Organisation verwalten. Allerdings können Sie die Exchange Online-Organisation nicht verwalten, wenn Sie die Exchange-Verwaltungsshell über dieses Symbol öffnen. Der Grund hierfür ist, dass beim Öffnen der Exchange-Verwaltungsshell über das entsprechende Symbol Exchange-Verwaltungsshell automatisch eine Verbindung mit einem lokalen Exchange-Server hergestellt wird.

Wenn Sie die Exchange Online-Organisation über die Windows PowerShell verwalten möchten, müssen Sie die Windows PowerShell direkt und nicht über das Symbol Exchange-Verwaltungsshell öffnen. Beim Öffnen der Windows PowerShell können Sie anschließend manuell die herzustellende Verbindung angeben. Beim Erstellen einer manuellen Verbindung geben Sie ein Administratorkonto in der Office 365-Mandantenorganisation an und führen anschließend einen Befehl zum Erstellen einer Verbindung aus. Sobald die Verbindung hergestellt ist, stehen Ihnen die Exchange-Cmdlets zur Verfügung, für deren Ausführung Sie eine Berechtigung besitzen. Weitere Informationen finden Sie unter [Verwenden von Windows PowerShell](http://go.microsoft.com/fwlink/p/?linkid=209660).

Grundlegende Informationen zur Exchange-Verwaltungsshell und Funktionsweise, Befehlssyntax und anderen Aspekten der Exchange-Verwaltungsshell finden Sie unter dem Thema [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)).

