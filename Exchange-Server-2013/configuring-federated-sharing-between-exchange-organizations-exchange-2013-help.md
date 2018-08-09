---
title: 'Konfigurieren von Verbundfreigaben zwischen Exchange-Organisationen'
TOCTitle: Konfigurieren von Verbundfreigaben zwischen Exchange-Organisationen
ms:assetid: 94e31454-b027-4757-b52f-d3c2ead6d916
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657473(v=EXCHG.150)
ms:contentKeyID: 50476282
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Verbundfreigaben zwischen Exchange-Organisationen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mithilfe der Verbundfreigabe können Benutzer in einer lokalen Exchange-Organisation Frei/Gebucht-Kalenderinformationen mit Empfängern in anderen Exchange-Organisationen, die ebenfalls für die Verbundfreigabe konfiguriert sind, gemeinsam nutzen. Die gemeinsame Nutzung von Frei/Gebucht-Informationen kann zwischen zwei Organisationen mit Exchange 2013 und zwischen Organisationen in einer gemischten Exchange-Bereitstellung aktiviert werden. Weitere Informationen zu Verbundfreigaben finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

Das vorliegende Thema liefert eine Zusammenfassung der Anforderungen sowie der erforderlichen Konfigurationsschritte zum Aktivieren der gemeinsamen Nutzung von Frei/Gebucht-Informationen zwischen verschiedenen gängigen Exchange-Bereitstellungen:

  - Zwei Exchange 2013-Organisationen.

  - Eine Exchange 2013-Organisation und eine Exchange 2010 SP2-Organisation.

  - Eine Exchange 2007-Organisation (oder eine gemischte Organisation mit Exchange 2007 und Exchange 2010 SP2) eine Exchange 2013-Organisation.

  - Eine Exchange 2003-Organisation (oder eine gemischte Organisation mit Exchange 2003 und Exchange 2010 SP2) eine Exchange 2013-Organisation.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Verbundfreigabe finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Stunden.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Bevor Sie die Verfahren in diesem Thema durchführen, stellen Sie zuerst sicher, dass Sie die Einschränkungen der Freigabe von Frei/Gebucht-Informationen in Exchange-Organisationen verstehen. Weitere Informationen finden Sie unter [Limitations of free/busy sharing](sharing-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Konfigurieren der Freigabe von Frei/Gebucht-Informationen zwischen Exchange 2013-Organisationen

Führen Sie die Schritte unter [Konfigurieren der Verbundfreigabe](configure-federated-sharing-exchange-2013-help.md) für beide Organisationen durch.

## Konfigurieren der Freigabe von Frei/Gebucht-Informationen zwischen einer Exchange 2013- und einer Exchange 2010 SP2-Organisation

  - Konfigurieren Sie Verbundfreigaben für die Exchange 2013-Organisation. Führen Sie die unter [Konfigurieren der Verbundfreigabe](configure-federated-sharing-exchange-2013-help.md) beschriebenen Schritte aus.

  - Konfigurieren Sie die Verbunddelegierung (dies ist der frühere Name für die Verbundfreigabe) für die Exchange 2010 SP2-Organisation. Führen Sie die Schritte unter [Konfigurieren der Verbunddelegierung](https://go.microsoft.com/fwlink/p/?linkid=268410) aus.

## Konfigurieren der Freigabe von Frei/Gebucht-Informationen zwischen einer Exchange 2013- und einer Exchange 2007-Organisation

  - Konfigurieren Sie Verbundfreigaben für die Exchange 2013-Organisation. Führen Sie die unter [Konfigurieren der Verbundfreigabe](configure-federated-sharing-exchange-2013-help.md) beschriebenen Schritte aus.

  - Führen Sie die folgenden Schritte in der Exchange 2007-Organisation aus:
    
    1.  **Hinzufügen eines Servers mit Exchange 2010 SP2**
        
        In der Exchange 2007-Organisation muss ein Exchange 2010 SP2-Server mit installierter Clientzugriffs-Serverrolle vorhanden sein. Wenn Sie über vorhandene Exchange 2010-Server verfügen, sollten diese ebenfalls auf Exchange 2010 SP2 aktualisiert werden. Informationen zum Installieren von Exchange 2010 in einer Exchange 2007-Organisation finden Sie unter [Exchange 2007 – Planungswegweiser für Upgrade und Koexistenz](https://go.microsoft.com/fwlink/p/?linkid=268411).
    
    2.  **Konfigurieren der Verbunddelegierung**
        
        Konfigurieren Sie die Verbunddelegierung für die Exchange 2007-Organisation. Führen Sie auf einem Exchange 2010 SP2-Server in der Exchange 2007-Organisation die unter [Konfigurieren der Verbunddelegierung](https://go.microsoft.com/fwlink/p/?linkid=268410) beschriebenen Schritte aus.
    
    3.  **Konfigurieren der Active Directory-Synchronisierung**
        
        Sie müssen die Active Directory-Synchronisierung für alle Benutzer konfigurieren, die Frei/Gebucht-Informationen mit Benutzern der anderen Organisationen gemeinsam nutzen müssen. Sie können die Active Directory-Synchronisierung entweder manuell konfigurieren, oder Sie verwenden einen automatisierten Active Directory-Synchronisierungsdienst. Um die Active Directory-Synchronisierung zu konfigurieren, führen Sie die folgenden Schritte aus:
        
          - **Voraussetzungen**   Stellen Sie sicher, dass Ihre Organisation die Voraussetzungen für die Installation der Active Directory-Synchronisierung erfüllt.
            
            Weitere Informationen finden Sie unter [Vorbereiten der Active Directory-Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=247302)
        
          - **Planung**   Machen Sie sich mit der Microsoft Online Services-Verzeichnissynchronisierung und der Roadmap für die Installation vertraut.
            
            Weitere Informationen finden Sie unter [Active Directory-Synchronisierung: Roadmap](http://go.microsoft.com/fwlink/p/?linkid=203007)
        
          - **Installation und Konfiguration**   Konfigurieren Sie die Active Directory-Synchronisierung zwischen der lokalen und der Office 365-Mandantendienstorganisation.
            
            Weitere Informationen finden Sie unter [Installieren und Aktualisieren des Microsoft Online Services-Verzeichnissynchronisierungstools](https://go.microsoft.com/fwlink/p/?linkid=247303)
    
    4.  **Erstellen eines Verfügbarkeitsadressraums**
        
        Erstellen Sie einen Verfügbarkeitsadressraum für die Exchange 2013-Remoteorganisation, mit dem Verfügbarkeitsanforderungen von Exchange 2007-Postfachbenutzern an den Clientzugriffsserver mit Exchange 2010 SP2 in der Exchange 2007-Organisation weitergeleitet werden. Diese Einstellung ermöglicht es, dass Benutzerverfügbarkeitsanforderungen von Exchange 2007-Benutzern für Benutzer in der Exchange 2013-Remoteorganisation über den Exchange 2010-Clientzugriffsserver in der Exchange 2007-Organisation weitergeleitet werden. Der Exchange 2010-Clientzugriffsserver in der Exchange 2007-Organisation verwendet die Verbundvertrauensstellung und die Organisationsbeziehung, um Verfügbarkeitsanforderungen an den Gesamtstrukturverfügbarkeitsendpunkt der Exchange 2013-Remoteorganisation zu senden.
        
        Um den Verfügbarkeitsadressraum zu konfigurieren, führen Sie auf dem Exchange 2010-Clientzugriffsserver in der Exchange 2007-Organisation den folgenden Befehl in der Exchange-Verwaltungsshell aus:
        
            Add-AvailabilityAddressSpace -AccessMethod InternalProxy -ProxyUrl https://<Exchange 2010 CAS server name>/ews/exchange.asmx -ForestName <SMTP domain of the remote Exchange organization> -UseServiceAccount $True
        
        Ausführliche Syntax- und Parameterinformationen finden Sie unter [Add-AvailabilityAddressSpace](https://go.microsoft.com/fwlink/p/?linkid=268413)

## Konfigurieren der Freigabe von Frei/Gebucht-Informationen zwischen einer Exchange 2013- und einer Exchange 2003-Organisation

  - Konfigurieren Sie Verbundfreigaben für die Exchange 2013-Organisation. Führen Sie die unter [Konfigurieren der Verbundfreigabe](configure-federated-sharing-exchange-2013-help.md) beschriebenen Schritte aus.

  - Führen Sie die folgenden Schritte in der Exchange 2003-Organisation aus:
    
    1.  **Hinzufügen eines Exchange 2010 SP2-Servers**.
        
        In der Exchange 2003-Organisation muss ein Exchange 2010 SP2-Server mit installierter Clientzugriffs-Serverrolle vorhanden sein. Wenn Sie über vorhandene Exchange 2010-Server verfügen, sollten diese ebenfalls auf Exchange 2010 SP2 aktualisiert werden. Informationen zum Installieren von Exchange 2010 in einer Exchange 2003-Organisation finden Sie unter [Exchange 2003 – Planungswegweiser für Upgrade und Koexistenz](https://go.microsoft.com/fwlink/?linkid=268414).
        

        > [!WARNING]
        > Damit die Freigabe von Frei/Gebucht-Informationen zwischen einer Exchange&nbsp;2013- und einer Exchange&nbsp;2003-Organisation ordnungsgemäß funktioniert, muss in der Ordnerhierarchie der öffentliche Ordner <STRONG>OU=EXTERNAL (FYDIBOHF25SPDLT)</STRONG> vorhanden sein. Dieser Ordner wird nur dann automatisch auf dem Exchange&nbsp;2010-Postfachserver in der Exchange&nbsp;2003-Organisation erstellt, wenn Sie die Option zum Erstellen öffentlicher Ordner verwenden, die zur Konfiguration der Clienteinstellungen für die Outlook&nbsp;2003-Unterstützung beim Setup von Exchange&nbsp;2010 gehört. Darüber hinaus wird diese Option beim Setup nur dann zur Auswahl angeboten, wenn es sich beim Exchange&nbsp;2010-Postfachserver um den ersten installierten Postfachserver in der Organisation handelt. Wenn der öffentliche Ordner <STRONG>OU=EXTERNAL (FYDIBOHF25SPDLT)</STRONG> während des Setups nicht erstellt wurde, müssen Sie ihn manuell erstellen. Einzelheiten zum Erstellen dieses öffentlichen Ordners finden Sie unter <A href="http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=2555008">Behandeln von Frei/Gebucht-Problemen bei Verwendung des Exchange-Partnerverbunds in der Microsoft Office 365-Umgebung für Unternehmen</A>.

    
    2.  **Konfigurieren Sie die Verbunddelegierung**.
        
        Konfigurieren Sie die Verbunddelegierung für die Exchange 2003-Organisation. Führen Sie auf einem Exchange 2010 SP2-Server in der Exchange 2003-Organisation die unter [Konfigurieren der Verbunddelegierung](https://go.microsoft.com/fwlink/p/?linkid=268410) beschriebenen Schritte aus.
    
    3.  **Konfigurieren der Active Directory-Synchronisierung**.
        
        Sie müssen die Active Directory-Synchronisierung für alle Benutzer konfigurieren, die Frei/Gebucht-Informationen mit Benutzern der anderen Organisationen gemeinsam nutzen müssen. Sie können die Active Directory-Synchronisierung entweder manuell konfigurieren, oder Sie verwenden einen automatisierten Active Directory-Synchronisierungsdienst. Weitere Informationen zur Active Directory-Synchronisierung finden Sie unter [Forefront Identity Management](https://go.microsoft.com/fwlink/?linkid=294645).
        
          - **Voraussetzungen**   Stellen Sie sicher, dass Ihre Organisation die Voraussetzungen für die Installation der Active Directory-Synchronisierung erfüllt.
            
            Weitere Informationen finden Sie unter [Vorbereiten der Active Directory-Synchronisierung](https://go.microsoft.com/fwlink/p/?linkid=247302)
        
          - **Planung**   Machen Sie sich mit der Microsoft Online Services-Verzeichnissynchronisierung und der Roadmap für die Installation vertraut.
            
            Weitere Informationen finden Sie unter [Active Directory-Synchronisierung: Roadmap](http://go.microsoft.com/fwlink/p/?linkid=203007)
        
          - **Installation und Konfiguration**   Konfigurieren Sie die Active Directory-Synchronisierung zwischen der lokalen und der Office 365-Mandantendienstorganisation.
            
            Weitere Informationen finden Sie unter [Installieren und Aktualisieren des Microsoft Online Services-Verzeichnissynchronisierungstools](https://go.microsoft.com/fwlink/p/?linkid=247303)
    
    4.  **Konfigurieren Sie öffentliche Ordner für die Freigabe von Frei/Gebucht-Informationen in Ihrer Exchange 2003-Organisation.**
        
        Führen Sie die folgenden Schritte auf einem Exchange 2003-Server aus:
        
          - Navigieren Sie im Exchange-System-Manager in der Konsolenstruktur zu **Administrative Gruppen** \> **Erste administrative Gruppe** \> **Server**.
        
          - Wählen Sie Ihren Exchange 2003-Server aus, und navigieren Sie dann zu **Erste Speichergruppe** \> **Informationsspeicher für Öffentliche Ordner** \> **Öffentliche Ordner** \> **Schedule+ Frei/Gebucht-Informationen**.
        
          - Wählen Sie im Aktionsbereich den Ordner **OU=EXTERNAL (FYDIBOHF25SPDLT)** für **Erste administrative Gruppe** aus.
        
          - Klicken Sie mit der rechten Maustaste auf den Ordner **OU=EXTERNAL (FYDIBOHF25SPDLT)** und anschließend auf **Eigenschaften**.
        
          - Wählen Sie in den Eigenschaften von **OU=EXTERNAL (FYDIBOHF25SPDLT)** die Registerkarte **Replikation**.
        
          - Klicken Sie auf **Hinzufügen**, um den Ordner **OU=EXTERNAL (FYDIBOHF25SPDLT)** auf den Exchange 2010-Clientzugriffsserver/Postfachserver zu replizieren.
        
          - Wählen Sie unter **Informationsspeicher für Öffentliche Ordner auswählen** die **Öffentliche Ordner-Datenbank** für den Exchange 2010-Clientzugriffsserver/Postfachserver aus, und klicken Sie anschließend auf **OK**.
            

            > [!NOTE]
            > Standardmäßig verwendet Exchange den Replikationszeitplan, der in der Datenbank für öffentliche Ordner angegeben wird.

        
          - Klicken Sie auf **OK**, um die Eigenschaften von **OU=EXTERNAL (FYDIBOHF25SPDLT)** zu schließen und Ihre Änderungen zu speichern.
        
          - Führen Sie diese Schritte auch für den Ordner **OU=Exchange Administrative Group (FYDIBOHF23SPDLT)** aus.
            

            > [!WARNING]
            > Abhängig von der Größe der Öffentlichen Ordner kann diese Replikation mehrere Stunden dauern.

        
          - Nach der Replikation der Öffentlichen Ordner **OU=EXTERNAL (FYDIBOHF25SPDLT)** und **OU=Exchange Administrative Group (FYDIBOHF23SPDLT)** auf den Exchange 2010-Clientzugriffsserver/Postfachserver müssen die Replikate dieser Öffentlichen Ordner auf dem Exchange 2003-Server entfernt werden.
    
    5.  **Ändern des Parameters "LegacyExchangeDN"**
        
        Ändern Sie den Parameter *LegacyExchangeDN* für alle E-Mail-aktivierten Objekte in der Exchange 2003-Organisation, die auf die Exchange 2013-Remoteorganisation verweisen. Ändern Sie den vorhandenen OU-Wert für das E-Mail-aktivierte Objekt in **External (FYDIBOHF25SPDLT)**. Beispiel: **LegacyExchangeDN=/o=First Organization/ou=External (FYDIBOHF25SPDLT)/cn=Recipients/cn=User Name**.
        
        Um E-Mail-aktivierte Objekte in der Exchange 2003-Organisation zu ändern, können Sie das Tool [Active Directory Service Interfaces Editor (ADSI Edit)](https://go.microsoft.com/fwlink/?linkid=294644) oder das Hilfsprogramm [Microsoft Exchange Server LegacyDN](https://go.microsoft.com/fwlink/?linkid=294643) verwenden.

