---
title: 'Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungen unter Verwendung von Beispielcode: Exchange 2013 Help'
TOCTitle: Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungen unter Verwendung von Beispielcode
ms:assetid: f35ac7a5-bb84-4653-b6d0-65906e93627b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee861124(v=EXCHG.150)
ms:contentKeyID: 50477076
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungen unter Verwendung von Beispielcode

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Microsoft Exchange 2013 unterstützt Postfachverschiebungen und -migrationen mithilfe der Cmdlets **New-MoveRequest** und **New-MigrationBatch**. Sie können das Postfach auch über die Exchange-Verwaltungskonsole verschieben. Sie können ein Postfach aus einer Exchange-Quellgesamtstruktur in eine Exchange 2010-Zielgesamtstruktur verschieben.

Zum Ausführen von **New-MoveRequest** muss in der Exchange-Zielgesamtstruktur ein E-Mail-Benutzer vorhanden sein, der über einen Mindestsatz an erforderlichen Active Directory-Attributen verfügt. Sie können den erforderlichen E-Mail-Benutzer in der Exchange-Zielgesamtstruktur erstellen, indem Sie Ihre Bereitstellung von Microsoft Identity Lifecycle Manager (ILM) 2007 anpassen. Der in diesem Thema beschriebene ILM-basierte Beispielcode für die Regelerweiterung veranschaulicht, wie Sie Ihre ILM-Bereitstellung anpassen können, um den erforderlichen E-Mail-aktivierten Benutzer in der Exchange 2013-Zielgesamtstruktur zu erstellen.

Weitere Informationen zur Vorbereitung auf gesamtstrukturübergreifende Verschiebungen, einschließlich Beschreibungen der erforderlichen Active Directory-Attribute, finden Sie unter [Vorbereiten von Postfächern für gesamtstrukturübergreifende Verschiebungsanforderungen](prepare-mailboxes-for-cross-forest-move-requests-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Laden Sie den Beispielcode auf der Seite [Vorbereiten auf die Onlinepostfachverschiebung](https://go.microsoft.com/fwlink/p/?linkid=177882) im Microsoft Download Center herunter.

  - Zum Ausführen des Beispielcodes ist ILM 2007 Feature Pack 1 Service Pack 1 (SP1) erforderlich. Informationen zum Herunterladen des Feature Packs finden Sie im Microsoft Knowledge Base-Artikel 977791, [Service Pack 1 (Build 3.3.1139.2) ist für Identity Lifecycle Manager 2007 Feature Pack 1 verfügbar](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=977791).

  - Darüber hinaus benötigen Sie Folgendes:
    
      - Eine Quellgesamtstruktur mit Exchange 2013, in der sich das Postfach zurzeit befindet.
    
      - Eine Zielgesamtstruktur mit Exchange 2013, in die das Postfach verschoben werden soll.

  - Damit Sie die Verbindung zur Exchange 2013-Zielgesamtstruktur herstellen können, müssen Sie über die erforderlichen Berechtigungen zum Aufrufen des Cmdlets **UpdateRecipient** verfügen. Informationen zu den erforderlichen Berechtigungen finden Sie im Abschnitt "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Installieren des ILM-Beispielcodes

1.  Öffnen Sie in Microsoft Visual Studio 2008 "Microsoft.Exchange.Sample.OneWayGALSync.sln", um den Beispielcode anzuzeigen. Der Beispielcode enthält Folgendes:
    
      - **Microsoft.MetadirectoryServicesEx.dll** ist die mit ILM 2007 FP1 SP1 im Ordner **\\Programme\\Microsoft Identity Integration Server\\Bin\\Assemblies** bereitgestellte Binärdatei. Sie wird im Beispielcode referenziert.
    
      - **OneWaySync.xml** wird im Beispielcode referenziert.
    
      - Der Ordner **ILMServerConfig** enthält die ILM-Konfigurationsdateien für den Quellverwaltungs-Agent, den Zielverwaltungs-Agent und die ILM-Metaverse (MV).
    
      - Microsoft.Exchange.Sample.OneWayGALSync.MARules.dll und Microsoft.Exchange.Sample.OneWayGALSync.MVRules.dll (diese Dateien werden aus dem Beispielcode erstellt) befinden sich unter \\obj\\Debug

2.  Kopieren Sie auf dem ILM-Server die folgenden Dateien in den Ordner **\\Programme\\Microsoft Identity Integration Server\\Extensions**:
    
      - OneWaySync.xml
    
      - Microsoft.Exchange.Sample.OneWayGALSync.MARules.dll
    
      - Microsoft.Exchange.Sample.OneWayGALSync.MVRules.dll

3.  Bearbeiten Sie die Datei **OneWaySync.xml**, die Sie in Schritt 1 in den ILM-Ordner **Extensions** kopiert haben, um den Distinguished Name (DN) des Containers für die Zielorganisationseinheit in der Exchange-Zielgesamtstruktur anzugeben, in der die E-Mail-Benutzer erstellt werden sollen. Sie können "LDP.exe" oder "ADSIEdit.exe" für die Suche nach dem Container für die Zielorganisationseinheit verwenden, wenn Sie den Namen dieses Containers nicht kennen.
    

    > [!NOTE]
    > Wenn Sie dieses Beispiel mit ILM GalSync&nbsp;2007 verwenden, schließen Sie diesen Container aus der Liste der von GalSync&nbsp;2007 verwalteten Container aus.



4.  Wechseln Sie in der ILM-Identitäts-Manager-Konsole zu **Datei** \> **Serverkonfiguration importieren**, um die ILM-Serverkonfiguration aus dem Ordner **ILMServerConfig** zu importieren. Bei diesem Vorgang werden zwei Active Directory-Verwaltungs-Agents sowie das Metaverseschema und die Bereitstellungsregel importiert.
    

    > [!NOTE]
    > Während des Imports müssen Sie den Gesamtstrukturnamen sowie Anmeldeinformationen angeben und einen Abgleich der Partitionen des importierten Active Directory-Verwaltungs-Agents mit dem Partitionsnamen in Ihrer Konfiguration durchführen (sowohl für den Quell- als auch für den Zielverwaltungs-Agent).



5.  Damit der Active Directory-Verwaltungs-Agent die Exchange 2013-Zielgesamtstruktur unterstützt, wählen Sie auf der Seite **Verwaltungs-Agent erstellen** im Bereich **Erweiterungen konfigurieren** die Option **Exchange 2013** aus der Dropdownliste **Bereitstellung für** aus und geben für **Exchange 2013 RPS-URI** den Remote-Windows PowerShell-URI eines Exchange 2010-Clientzugriffsservers ein.
    
    **Seite "Verwaltungs-Agent erstellen"**
    
    ![Exchange 2010 Verwaltungs-Agent-Bereitstellung](images/Aa998597.8f403cda-e5e4-4edf-887f-c1ed46cee3f5(EXCHG.150).gif "Exchange 2010 Verwaltungs-Agent-Bereitstellung")  

6.  Öffnen Sie in der ILM-Identitäts-Manager-Konsole im Bereich **Verwaltungs-Agent erstellen** die Eigenschaften für den Verwaltungs-Agent der Quellgesamtstruktur. Wählen Sie den Assistenten **Verzeichnispartitionen konfigurieren**, und klicken Sie zur Auswahl des Containers, in dem die in die Zielgesamtstruktur verschobenen Postfächer platziert werden sollen, auf **Container**. Deaktivieren Sie die Auswahl aller anderen Container, sodass der Verwaltungs-Agent lediglich diesen Container verwaltet. Wählen Sie auf ähnliche Weise für den Verwaltungs-Agent der Zielgesamtstruktur den Container aus, in dem E-Mail-aktivierte Benutzer bereitgestellt werden (also die in Schritt 2 angegebene Zielorganisationseinheit).
    

    > [!NOTE]
    > Wenn Sie dieses Beispiel mit ILM GalSync&nbsp;2007 verwenden, schließen Sie beide Container aus der Liste der von GalSync&nbsp;2007 verwalteten Container aus.



7.  Führen Sie einen anfänglichen vollständigen Import (Nur Bereitstellung) für die Ziel-Verwaltungs-Agents aus, sodass ILM die in Schritt 2 angegebene Zielorganisationseinheit ermitteln kann.

## Schritt 2: Erstellen eines E-Mail-Benutzers in der Exchange-Zielgesamtstruktur

Führen Sie nach der Installation des Beispielcodes zum Erstellen des erforderlichen E-Mail-Benutzers in der Exchange-Zielgesamtstruktur die folgenden Schritte aus, damit **New-MoveRequest** zum Ausführen einer Onlinepostfachverschiebung ausgeführt werden kann.

1.  Verwenden Sie in der Quellgesamtstruktur die Exchange-Verwaltungskonsole, um Postfachbenutzer in dem Container zu erstellen, der in Schritt 4 des Abschnitts "Installieren des ILM-Beispielcodes" ausgewählt wurde. Sie können vorhandene Postfachbenutzer auch mithilfe von "Active Directory-Benutzer und -Computer" in den Container verschieben.

2.  Führen Sie für den Verwaltungs-Agent der Quelle einen Deltaimport und eine Deltasynchronisierung aus, um die zum Quellcontainer hinzugefügten Postfächer zu ermitteln, und stellen Sie E-Mail-Benutzer für den Verwaltungs-Agent des Ziels bereit.

3.  Führen Sie für den Verwaltungs-Agent des Ziels einen Export aus, um die in Schritt 1 für das Active Directory-Ziel bereitgestellten E-Mail-Benutzer zu exportieren.

4.  Führen Sie für den Verwaltungs-Agent des Ziels einen Deltaimport aus, um die in Schritt 2 vorgenommenen Exportänderungen zu bestätigen.

5.  Öffnen Sie in der Zielgesamtstruktur die Exchange-Verwaltungsshell, und verschieben Sie mithilfe des Cmdlets **New-MoveRequest** Postfächer aus der Quellgesamtstruktur.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Migration erfolgreich abgeschlossen wurde:

  - Überprüfen Sie in der Zielgesamtstruktur, ob die aus der Quellgesamtstruktur verschobenen Benutzer vorhanden sind.

