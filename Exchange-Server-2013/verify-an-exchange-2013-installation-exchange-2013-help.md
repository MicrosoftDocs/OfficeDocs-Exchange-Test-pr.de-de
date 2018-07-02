---
title: 'Überprüfen einer Exchange 2013-Installation: Exchange 2013 Help'
TOCTitle: Überprüfen einer Exchange 2013-Installation
ms:assetid: fdd20a2a-c8c1-4d17-b813-3c05d88a4411
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125254(v=EXCHG.150)
ms:contentKeyID: 50477143
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Überprüfen einer Exchange 2013-Installation

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Nachdem Sie Microsoft Exchange Server 2013 installiert haben, wird empfohlen, die Installation zu überprüfen, indem Sie das Cmdlet **Get-ExchangeServer** ausführen und die Setupprotokolldatei durchgehen. Sollten beim Installationsprozess Fehler auftreten, können Sie anhand des Setupprotokolls die Quelle des Problems isolieren.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

## Ausführen von "Get-ExchangeServer"

Führen Sie zum Überprüfen der erfolgreichen Installation von Exchange 2013 das Cmdlet **Get-ExchangeServer** in der Exchange-Verwaltungsshell aus. Das Cmdlet zeigt eine Liste aller auf dem angegebenen Server installierten Exchange 2013-Serverrollen an.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ExchangeServer](https://technet.microsoft.com/de-de/library/bb123873\(v=exchg.150\)).

## Überprüfen der Setupprotokolldatei

Weitere Informationen zur Installation und Konfiguration von Exchange 2013 erhalten Sie, indem Sie die während der Installation erstellte Setupprotokolldatei überprüfen.

Während der Installation protokolliert das Exchange-Setup Ereignisse im **Anwendungsprotokoll** der **Ereignisanzeige** auf Computern mit Windows Server 2008 R2 Service Pack 1 (SP1) und Windows Server 2012. Überprüfen Sie das **Anwendungsprotokoll**, und stellen Sie sicher, dass keine Warnungen oder Fehlermeldungen bezüglich des Exchange-Setups vorliegen. Diese Protokolldateien enthalten einen Verlauf der Aktionen, die vom System während des Exchange 2013-Setups unternommen werden, sowie alle Fehler, die aufgetreten sind. Standardmäßig ist die Protokollierungsmethode auf `Verbose` festgelegt. Es werden Informationen zu jeder installierten Serverrolle bereitgestellt.

Sie finden die Setupprotokolldatei unter "*\<system drive\>*\\ExchangeSetupLogs\\ExchangeSetup.log". Die Variable *\<system drive\>* steht für das Stammverzeichnis des Laufwerks, auf dem das Betriebssystem installiert ist.

Die Setupprotokolldatei verfolgt den Fortschritt jedes Tasks, der während der Installation und Konfiguration von Exchange 2013 ausgeführt wird. Die Datei enthält Informationen zum Status der Überprüfung von Voraussetzungen und Systembereitschaft, die vor dem Start der Installation ausgeführt werden, sowie den Fortschritt der Anwendungsinstallation und die am System vorgenommenen Konfigurationsänderungen. Überprüfen Sie dieses Protokoll, um sicherzustellen, dass die Serverrollen erwartungsgemäß installiert wurden.

Es wird empfohlen, die Setupprotokolldatei zunächst auf Fehler zu überprüfen. Falls ein Eintrag gefunden wird, der auf einen aufgetretenen Fehler hinweist, lesen Sie den umgebenden Text, um die Ursache für den Fehler zu ermitteln.

