---
title: 'Hinzuf. d. Verbundpostfachs zur AD RMS-Admingruppe: Exchange 2013-Hilfe'
TOCTitle: Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe
ms:assetid: 44618df9-54f0-4474-a450-dcba48a02901
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee424431(v=EXCHG.150)
ms:contentKeyID: 50475552
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Damit die folgenden Funktionen der Verwaltung von Informationsrechten (Information Rights Management, IRM) von Microsoft Exchange Server 2013 aktiviert werden können, müssen Sie das Verbundpostfach (ein beim Exchange 2013-Setup erstelltes Systempostfach) der Benutzergruppe mit Administratorrechten im Cluster mit den [Active Directory-Rechteverwaltungsdiensten (AD RMS)](https://technet.microsoft.com/de-de/library/hh831364.aspx) in Ihrer Organisation hinzufügen:

  - IRM in Microsoft Office Outlook Web App

  - IRM in Exchange ActiveSync

  - Journalberichtentschlüsselung

  - Transportentschlüsselung

Eine E-Mail-aktivierte Verteilergruppe kann in AD RMS als Administratorengruppe konfiguriert werden. Mitgliedern der Verteilergruppe wird beim Anfordern einer Lizenz vom AD RMS-Cluster eine Besitzernutzungslizenz erteilt. Damit können sie alle von diesem Cluster veröffentlichten Inhalte, die durch den Rechteverwaltungsdienst geschützt sind, entschlüsseln. Ungeachtet der Tatsache, ob Sie eine vorhandene Verteilergruppe verwenden oder eine neue Verteilergruppe erstellen und diese als Administratorengruppe in AD RMS konfigurieren, ist es empfehlenswert, die Verteilergruppe nur für diesen Zweck zu verwenden und die entsprechenden Einstellungen zum Genehmigen, Verfolgen und Überwachen von Mitgliedschaftsänderungen zu konfigurieren.


> [!WARNING]
> Durch das Konfigurieren einer Gruppe mit Administratorrechten in AD&nbsp;RMS können Gruppenmitglieder IRM-geschützte Inhalte entschlüsseln. Es wird empfohlen, geeignete Maßnahmen zur Steuerung und Überwachung der Gruppenmitgliedschaft zu ergreifen und die Überwachung für Mitgliedschaftsänderungen zu aktivieren. Sie können unerwünschte Änderungen an Gruppenmitgliedschaften einschränken, indem Sie die Gruppe mithilfe von Gruppenrichtlinien als eingeschränkte Gruppe konfigurieren. Ausführliche Informationen hierzu finden Sie unter <A href="https://technet.microsoft.com/de-de/library/cc756802(v=ws.10).aspx">Richtlinieneinstellungen für eingeschränkte Gruppen</A> .



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - In der Active Directory-Gesamtstruktur muss ein AD RMS-Cluster bereitgestellt werden.

  - Wurde in einem AD RMS-Cluster bereits eine Administratorengruppe konfiguriert, kann es bis zu 24 Stunden dauern, bis Änderungen an der Verteilergruppe im AD RMS-Cluster aktualisiert werden. Dies ist auf die Zwischenspeicherung der Gruppenmitgliedschaft im Cluster zurückzuführen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Verwenden der Shell zum Hinzufügen des Verbundpostfachs zu einer Verteilergruppe

Wenn eine Verteilergruppe erstellt und im AD RMS-Cluster als Administratorengruppe konfiguriert wurde, können Sie das Exchange 2013-Verbundpostfach als Mitglied dieser Gruppe hinzufügen. Wurde noch keine Administratorengruppe konfiguriert, müssen Sie zuerst eine Verteilergruppe erstellen und das Verbundpostfach als Mitglied hinzufügen.

1.  Erstellen Sie eine Verteilergruppe, die als AD RMS-Administratorengruppe verwendet werden soll. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Verteilergruppen](https://technet.microsoft.com/de-de/library/Bb124513(v=EXCHG.150)).

2.  Fügen Sie der neuen Verteilergruppe den Benutzer **FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042** hinzu. Das Verbundpostfach ist ein Systempostfach und daher in der Exchange-Verwaltungskonsole nicht sichtbar. Zum Hinzufügen einer Verteilergruppe müssen Sie das Cmdlet [Add-DistributionGroupMember](https://technet.microsoft.com/de-de/library/bb124340\(v=exchg.150\)) in der Shell verwenden.
    
    In diesem Beispiel wird das Verbundpostfach der Verteilergruppe "ADRMSSuperUsers" hinzugefügt.
    
        Add-DistributionGroupMember ADRMSSuperUsers -Member FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Add-DistributionGroupMember](https://technet.microsoft.com/de-de/library/bb124340\(v=exchg.150\)).

## Schritt 2: Verwenden von AD RMS zum Einrichten einer Administratorengruppe

Gehen Sie in einem AD RMS-Cluster wie folgt vor. Das für dieses Verfahren verwendete Konto muss zu der lokalen Gruppe "AD RMS-Organisationsadministratoren" auf dem AD RMS-Server gehören.

1.  Öffnen Sie die AD RMS-Konsole, und erweitern Sie den AD RMS-Cluster.

2.  Erweitern Sie in der Konsolenstruktur den Eintrag **Sicherheitsrichtlinien**, und klicken Sie dann auf **Administratoren**.

3.  Klicken Sie im Aktionsbereich auf **Administratoren aktivieren**.

4.  Klicken Sie im Ergebnisbereich auf **Administratorengruppe ändern**, um die Eigenschaftsseite der **Administratoren** zu öffnen.

5.  Geben Sie im Feld **Administratorengruppe** die E-Mail-Adresse der zuvor erstellten Verteilergruppe ein, oder klicken Sie auf **Durchsuchen**, um eine Verteilergruppe auszuwählen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Nachdem Sie das Verbundpostfach zu einer neuen oder vorhandenen Verteilergruppe hinzugefügt haben, können Sie mit dem Cmdlet [Get-DistributionGroupMember](https://technet.microsoft.com/de-de/library/aa996367\(v=exchg.150\)) die Mitgliedschaft der Gruppe überprüfen.

Ein Beispiel zum Überprüfen der Mitgliedschaft für Verteilergruppen finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/aa996367\(exchg.150\)#examples) in **Get-DistributionGroupMember**.

Nachdem Sie mithilfe von AD RMS eine Gruppe mit Administratorrechten eingerichtet haben, können Sie anhand der folgenden Methoden überprüfen, ob die Benutzergruppe mit Administratorrechten ordnungsgemäß konfiguriert wurde. Darüber hinaus können Sie mit dem Cmdlet [Test-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979798\(v=exchg.150\)) die IRM-Funktionalität überprüfen.

  - Stellen Sie mithilfe der AD RMS-Konsole sicher, dass die richtige Gruppe als Benutzergruppe mit Administratorrechten konfiguriert wurde.

  - Verwenden Sie den folgenden PowerShell-Befehl auf einem AD RMS-Server, um die Benutzergruppe mit Administratorrechten abzurufen.
    

    > [!IMPORTANT]
    > Das PowerShell-Modul "ADRMSAdmin" ist unter Windows Server 2008 R2 oder neueren Versionen verfügbar.

    
        Import-Module ADRMSAdmin
        New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost 
        Get-ItemProperty -Path MyRmsAdmin:\SecurityPolicy\SuperUser

