---
title: 'Delegieren der Installation eines Exchange 2013-Servers: Exchange 2013 Help'
TOCTitle: Delegieren der Installation eines Exchange 2013-Servers
ms:assetid: f2fc8680-0c7c-4a29-b8f5-d77404fec280
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201741(v=EXCHG.150)
ms:contentKeyID: 62615195
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Delegieren der Installation eines Exchange 2013-Servers

 

_**Gilt für:** Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-07-31_

Mit Exchange Server 2013 können Sie die Installation von Exchange-Servern an Personen delegieren, die keine Mitglieder der Rollengruppe "Exchange 2013-Organisationsverwaltung" sind. Dies hilft oft in großen Firmen, in denen die Mitarbeiter, die Server installieren und einrichten, nicht dieselben Personen sind, die Dienste wie Exchange verwalten. Wenn dies eine Option ist, die Sie nutzen möchten, ist dieses Thema genau für Sie geeignet.

Normalerweise müssen die Mitarbeiter, die Exchange installieren, Mitglieder der Rollengruppe [Organisationsverwaltung](organization-management-exchange-2013-help.md) sein. Dies hat folgenden Grund: Wenn Exchange installiert wird, werden Änderungen an Active Directory vorgenommen, und nur Exchange-Administratoren, die Mitglieder der Rollengruppe "Organisationsverwaltung" sind, können diese Änderungen durchführen. Die folgende Liste enthält die Änderungen, die vorgenommen werden:

  - Ein Serverobjekt wird in der Konfigurationspartition **CN=Server,CN=Administrative Exchange-Gruppe (FYDIBOHF23SPDLT),CN=Administrative Gruppe,CN=\<Organisationsname\>,CN=Microsoft Exchange,CN=Dienste,CN=Konfiguration,DC=\<Stammdomäne\>** erstellt.

  - Die folgenden Zugriffssteuerungseinträge (Access Control Entries, ACEs) werden zum Serverobjekt in der Konfigurationspartition für die Rollengruppe "Delegiertes Setup" hinzugefügt:
    
      - Vollzugriff auf das Serverobjekt und seine untergeordneten Objekte
    
      - DENY-Zugriffssteuerungseintrag für das erweiterte Recht "Senden als"
    
      - DENY-Zugriffssteuerungseintrag für das erweiterte Recht "Empfangen als"
    
      - Verweigern der CreateChild- und DeleteChild-Berechtigung für Objekte des Informationsspeichers für öffentliche Ordner von Exchange
    

    > [!NOTE]
    > Öffentliche Ordner werden auf Organisationsebene verwaltet, weshalb das Erstellen und das Löschen von Informationsspeichern für öffentliche Ordner auf Exchange-Administratoren beschränkt sind.



  - Das Active Directory-Computerkonto für den Server wird zur Servergruppe Exchange hinzugefügt.

  - Der Server wird als bereitgestellter Server im Exchange-Admin Center hinzugefügt.

In großen Firmen sind die Mitarbeiter, die neue Server installieren und einrichten, oft keine Exchange-Administratoren. Um diesen Mitarbeitern die Installation von Exchange zu ermöglichen, kann ein Exchange-Administrator den Server in Active Directory*bereitstellen*. Wenn ein Server bereitgestellt wird, werden alle Änderungen, die erforderlich sind, damit der neue Exchange-Server funktioniert, getrennt von der tatsächlichen Installation von Exchange auf einem Computer an Active Directory durchgeführt. Ein Exchange-Administrator kann einen neuen Server in Active Directory schon Stunden oder sogar Tage bereitstellen, bevor Exchange auf dem neuen Computer installiert wird. Nach der Bereitstellung eines Servers muss die Person, die die Installation durchführt, nur Mitglied der Rollengruppe [Delegiertes Setup](delegated-setup-exchange-2013-help.md) sein, um Exchange zu installieren. Die Rollengruppe "Delegiertes Setup" erlaubt Ihren Mitgliedern, bereitgestellte Server zu installieren.

Bedenken Sie Folgendes, wenn Sie die Verwendung des delegierten Setups planen:

  - Mindestens ein Exchange 2013-Server muss bereits installiert sein, bevor Sie die Installation zusätzlicher Server delegieren können. Der Mitarbeiter, der den ersten Server installiert, muss ein Exchange-Administrator sein. Weitere Informationen finden Sie unter [Prüfliste: Ausführen einer Neuinstallation von Exchange 2013](checklist-perform-a-new-installation-of-exchange-2013-exchange-2013-help.md).

  - Ein delegierter Benutzer kann einen Exchange-Server nicht deinstallieren. Um einen Exchange-Server deinstallieren zu können, müssen Sie ein Exchange-Administrator sein.

## Wie stelle ich einen Exchange 2013-Server bereit?

Um einen Server für Exchange bereitstellen zu können, müssen Sie die Befehlszeilen-Version des Exchange 2013-Setups verwenden. Wenn Sie nicht sehr vertraut mit der Windows-Eingabeaufforderung sind, machen Sie sich keine Sorgen. In diesem Thema werden Sie durch die einzelnen Schritte geführt, die Sie ausführen müssen. Bevor wir beginnen, sind noch einige Punkte zu beachten:

  - Sie müssen Mitglied der Rollengruppe "Organisationsverwaltung" sein, um einen Server bereitstellen zu können.

  - Sie sollten über die neueste Version von Exchange 2013 verfügen. Sie können den Download-Link von [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md) abrufen.

Welchen Befehl Sie verwenden müssen, um den Server bereitzustellen, hängt davon ab, ob Sie das Setup auf dem Computer, den Sie bereitstellen, oder auf einem anderen Computer ausführen. Wählen Sie in den folgenden Schritten den passenden Befehl für Ihre Ausführung des Setup:

1.  Drücken Sie die Windows-Taste + 'R', um das Fenster **Ausführen** zu öffnen.

2.  Geben Sie unter **Öffnen** die Zeichenfolge **cmd.exe** ein, und drücken Sie die ENTER-Taste, um die **Windows-Eingabeaufforderung** zu öffnen.

3.  Ändern Sie die Verzeichnisse in diejenigen, in die Sie die Exchange 2013-Installationsdateien heruntergeladen und erweitert haben. Wenn die Installationsdateien sich unter `C:\Downloads\Exchange 2013` befinden, verwenden Sie den folgenden Befehl.
    
      ```powershell
        CD "C:\Downloads\Exchange 2013"
      ```
        
4.  Wählen Sie den Befehl, der am besten passt, wenn Sie das Setup ausführen:
    
      - **Wenn Sie das Setup auf dem Computer ausführen, der bereitgestellt wird**, führen Sie den folgenden Befehl aus:
        
        ```powershell
        Setup.exe /NewProvisionedServer /IAcceptExchangeServerLicenseTerms
        ```
    
      - **Wenn Sie das Setup auf einem anderen Computer ausführen**, führen Sie den folgenden Befehl aus:
        
        ```powershell
        Setup.exe /NewProvisionedServer:<ComputerName> /IAcceptExchangeServerLicenseTerms
        ```

5.  Nach der Bereitstellung des Servers müssen Sie sicherstellen, dass Sie die Benutzer hinzugefügt haben, die Exchange auf bereitgestellten Servern für die Rollengruppe "Delegiertes Setup" installieren können. Informationen zum Hinzufügen von Benutzern zu einer Rollengruppe finden Sie unter [Add members to a role group](manage-role-group-members-exchange-2013-help.md).

Wenn Sie mit der Ausführung dieser Schritte fertig sind, ist der Computer bereit für die Installation von Exchange. Exchange 2013 kann mithilfe der unter [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md) aufgeführten Schritte auf einem bereitgestellten Server installiert werden.

## Woher weiß ich, dass der Vorgang erfolgreich war?

Um sicherzustellen, dass der Server korrekt für Exchange bereitgestellt wurde, können Sie Folgendes tun:

1.  Wechseln Sie zu **Start** \> **Verwaltung**, und öffnen Sie dann **Active Directory-Benutzer und -Computer**.

2.  Wählen Sie **Microsoft Exchange-Sicherheitsgruppen** aus, doppelklicken Sie auf **Exchange-Server**, und wählen Sie dann die Registerkarte **Mitglieder**.

3.  Prüfen Sie auf der Registerkarte **Mitglieder**, ob der Server, den Sie gerade bereitgestellt haben, als Mitglied der Sicherheitsgruppe aufgelistet wird.

Wenn Ihr Server als Mitglied der Sicherheitsgruppe "Exchange-Server" aufgelistet wird, wurde er korrekt bereitgestellt. Ein Mitglied der Rollengruppe "Delegiertes Setup" kann nun Exchange auf diesem Server installieren.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Haben Sie gefunden, was Sie suchen? Nehmen Sie sich bitte einen Moment Zeit und [senden Sie uns Feedback](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedbac) zu den Informationen, die Sie in diesem Thema gerne finden möchten.

