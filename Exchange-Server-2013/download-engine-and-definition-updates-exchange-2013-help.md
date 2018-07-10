---
title: 'Downloadmodul und Definitionsupdates: Exchange 2013 Help'
TOCTitle: Downloadmodul und Definitionsupdates
ms:assetid: 8f2ca383-e463-4df0-aa5d-29afe2f81aaf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657471(v=EXCHG.150)
ms:contentKeyID: 50476151
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Downloadmodul und Definitionsupdates

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Microsoft Exchange Server 2013-Administratoren können manuell das Antischadsoftware-Modul sowie Updates der Definitionen (Signaturen) herunterladen. Es wird dringend empfohlen, das Modul und die Definitionsupdates auf den Exchange-Server herunterzuladen, bevor er in der Produktion verwendet wird.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Zum Herunterladen von Updates muss Ihr Computer über Internetzugriff verfügen und muss in der Lage sein, eine Verbindung über TCP-Port 80 (HTTP) einzurichten.

  - UNRESOLVED\_TOKEN\_VAL(PD\_Shell\_Only\_Procedure)

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antischadsoftware" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Manuelles Herunterladen von Modul-und Definitionsupdates mithilfe der Shell

Um Modul-und Definitionsupdates herunterzuladen, führen Sie folgenden Befehl aus:

    & $env:ExchangeInstallPath\Scripts\Update-MalwareFilteringServer.ps1 -Identity <FQDN of server>

In diesem Beispiel werden die Modul-und Definitionsupdates manuell auf einen Server mit dem Namen "mailbox01.contoso.com" heruntergeladen:

    & $env:ExchangeInstallPath\Scripts\Update-MalwareFilteringServer.ps1 -Identity mailbox01.contoso.com

Optional können Sie den Parameter "–EngineUpdatePath" angeben, mit dem Sie Updates von einem anderen Speicherort als dem standardmäßigen http://forefrontdl.microsoft.com/server/scanengineupdate herunterladen können. Dabei kann es sich um eine HTTP-Adresse oder einen UNC-Pfad handeln. Bei letzterem benötigt der Netzwerkdienst Zugriff auf den Pfad. In diesem Beispiel werden die Modul-und Definitionsupdates aus einem lokalen Verzeichnis auf einen Server mit dem Namen "mailbox01.contoso.com" heruntergeladen:

    & $env:ExchangeInstallPath\Scripts\Update-MalwareFilteringServer.ps1 -Identity mailbox01.contoso.com -EngineUpdatePath \\Server\sharename

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um zu überprüfen, ob Updates erfolgreich heruntergeladen wurden, müssen Sie auf die Ereignisanzeige zugreifen und das Ereignisprotokoll anzeigen. Es wird empfohlen, nur FIPFS-Ereignisse zu filtern, wie im folgenden Verfahren beschrieben.

1.  Klicken Sie im Menü **Start** auf **Alle Programme** \> **Verwaltung** \> **Ereignisanzeige**.

2.  Erweitern Sie in der Ereignisanzeige den Ordner **Windows-Protokolle** und klicken Sie dann auf **Anwendung**.

3.  Klicken Sie im Menü **Aktionen** auf **Aktuelles Protokoll filtern**.

4.  Aktivieren Sie im Dialogfeld **Aktuelles Protokoll filtern** in der Dropdownliste **Ereignisquellen** das Kontrollkästchen **FIPFS**, und klicken Sie dann auf **OK**.

Wenn Modulupdates erfolgreich heruntergeladen wurden, wird das Ereignis mit der ID 6033 etwa wie folgt angezeigt:

`MS Filtering Engine Update process performed a successful scan engine update.`

`Scan Engine: Microsoft`

`Update Path: http://forefrontdl.microsoft.com/server/scanengineupdate`

`Last Update time: ‎2012‎-‎08‎-‎16T13:22:17.000Z`

`Engine Version: 1.1.8601.0`

`Signature Version: 1.131.2169.0`

## Weitere Informationen

[Konfigurieren von Antischadsoftwarerichtlinien](configure-anti-malware-policies-exchange-2013-help.md)

