---
title: 'Bereitst. v. Exchange 2013 in ges.strukturübergr. Topol.: Exchange 2013-Hilfe'
TOCTitle: Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie
ms:assetid: 65be650f-d435-4f60-9ff0-5cb88a726abb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998597(v=EXCHG.150)
ms:contentKeyID: 51409310
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema wird erklärt, wie Exchange 2013 in einer gesamtstrukturübergreifenden Topologie mithilfe von Microsoft Forefront Identity Manager 2010 R2 SP1 bereitgestellt wird. Zum Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie müssen Sie zuerst Exchange 2013 in jeder Gesamtstruktur installieren und die Gesamtstrukturen dann so verbinden, dass die Benutzer Adressen und Verfügbarkeitsdaten gesamtstrukturübergreifend anzeigen können.

Die folgende Abbildung veranschaulicht die Benutzersynchronisierung zwischen zwei Exchange 2013-Gesamtstrukturen.

**Beispiel einer gesamtstrukturübergreifenden Exchange 2013-Synchronisierung**

![Beispiel einer Exchange 2010-Konfiguration mit mehreren Gesamtstrukturen](images/Aa998597.df0ba5dd-cb96-4542-98bd-2a425defe317(EXCHG.150).gif "Beispiel einer Exchange 2010-Konfiguration mit mehreren Gesamtstrukturen")

In diesem Thema wird *nicht* beschrieben, wie Exchange 2013 in einer dedizierten Exchange-Gesamtstrukturtopologie (oder Ressourcengesamtstruktur-Topologie) bereitgestellt wird. Weitere Informationen zum Bereitstellen von Exchange 2013 in einer Ressourcengesamtstrukturtopologie finden Sie unter [Bereitstellen von Exchange 5.113,02 cm einer Exchange-Ressourcengesamtstruktur-Topologie](deploy-exchange-2013-in-an-exchange-resource-forest-topology-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

Es müssen die folgenden Voraussetzungen erfüllt sein, um das nachstehende Verfahren in Exchange 2013 auszuführen:

  - Sie haben DNS (Domain Name System) für die gesamtstrukturübergreifende Namensauflösung in Ihrer Organisation ordnungsgemäß konfiguriert. Führen Sie einen Verbindungstest mittels Ping für jede Gesamtstruktur von den anderen Gesamtstrukturen in der Organisation sowie von dem Server durch, auf dem der GALSync-Agent ausgeführt werden soll, um sicherzustellen, dass DNS ordnungsgemäß konfiguriert ist.

  - Der GALSync-Verwaltungs-Agent kommuniziert über Exchange 2013 PowerShell V2.0 RTM mit der Windows-Gesamtstruktur. Stellen Sie sicher, dass Windows PowerShell V1.0 nicht auf diesem Computer installiert ist, indem Sie in der Systemsteuerung auf "Programme und Funktionen" klicken.

  - Stellen Sie sicher, dass die Windows-Remoteverwaltung nicht von Windows Update installiert wurde.

  - Installieren Sie Windows PowerShell und die Windows-Remoteverwaltung. Weitere Informationen finden Sie im Microsoft Knowledge Base-Artikel 968930, [Windows Management Framework-Kernpaket (Windows PowerShell 2.0 und WinRM 2.0)](http://go.microsoft.com/fwlink/p/?linkid=3052&kbid=968930).

  - Laden Sie Forefront Identity Manager 2010 R2 SP1 herunter. Siehe [Herunterladen von Microsoft Forefront Identity Manager 2010 R2 SP1](https://go.microsoft.com/fwlink/p/?linkid=279868).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Bereitstellen von Exchange 2013 in einer gesamtstrukturübergreifenden Topologie mit Forefront Identity Manager 2010 R2 SP1

1.  Installieren Sie Exchange 2013 in jeder Gesamtstruktur einzeln. Bei der Installation von Exchange 2013 führen Sie dieselben Schritte aus wie bei der Installation von Exchange 2013 in einer Topologie mit einer einzigen Gesamtstruktur. Ausführliche Informationen finden Sie in den folgenden Themen:
    
      - [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md)
    
      - [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md)
        

        > [!NOTE]
        > In diesem Thema wird davon ausgegangen, dass Sie nicht über eine vorhandene Exchange 2007- oder Exchange 2010-Topologie verfügen. Wenn Sie über eine vorhandene Exchange-Topologie verfügen und ein Upgrade ausführen möchten, lesen Sie <A href="upgrade-from-exchange-2010-to-exchange-2013-exchange-2013-help.md">Aktualisieren von Exchange&nbsp;2010 auf Exchange&nbsp;2013</A> oder <A href="upgrade-from-exchange-2007-to-exchange-2013-exchange-2013-help.md">Aktualisieren von Exchange&nbsp;2007 auf Exchange&nbsp;2013</A>.



2.  Erstellen Sie in jeder Gesamtstruktur in Active Directory-Benutzer und -Computer einen Container, in dem FIM 2010 R2 SP1 Kontakte für jedes Postfach der anderen Gesamtstruktur erstellt. Nennen Sie diesen Container am besten **VonFIM**. Zum Erstellen des Containers wählen Sie die Domäne aus, in der der Container erstellt werden soll, klicken mit der rechten Maustaste auf die Domäne und wählen **Neu** \> **Organisationseinheit** aus. Unter **Neues Objekt - Organisationseinheit** geben Sie **VonFIM** ein, und klicken Sie dann auf **OK**.

3.  Erstellen Sie mithilfe von Forefront Identify Manager für jede Gesamtstruktur einen GALSync-Verwaltungs-Agent. Auf diese Weise können Sie die Benutzer in den einzelnen Gesamtstrukturen synchronisieren und eine gemeinsame globalen Adressliste (GAL) erstellen. Detaillierte Anweisungen finden Sie in den folgenden Ressourcen:
    
      - [Konfigurieren der GAL-Synchronisierung (globale Adressliste) mit Forefront Identity Manager (FIM) 2010](https://go.microsoft.com/fwlink/p/?linkid=279869)
    
      - [Arbeiten mit Management Packs](https://go.microsoft.com/fwlink/p/?linkid=279870)
    
      - [Geplante Dokumentation für Forefront Identity Manager 2010 R2 Documentation Roadmap](https://go.microsoft.com/fwlink/p/?linkid=279871)
    

    > [!IMPORTANT]
    > Wenngleich in diesen Ressourcen Exchange 2010 behandelt wird, unterstützt FIM 2010 R2 SP1 auch Exchange 2013. Stellen Sie sich, dass <STRONG>Erweiterungen</STRONG> in FIM 2010 R2 SP1 für Exchange 2013 konfiguriert sind.

    
    1.  Wählen Sie auf der Seite **Configure Extensions** unter **Configure partition display name(s)** neben **Provision for** die Option **Exchange 2013** aus. Das Feld **Exchange 2013 RPS URI** wird angezeigt. Geben Sie den URI eines Exchange 2013-Clientzugriffsservers ein, um sicherzustellen, dass die Remote-PowerShell-Verbindung funktioniert. Der **Exchange 2013-RPS-URI** sollte das folgende Format aufweisen: http://CAS\_Server\_FQDN/Powershell. Klicken Sie auf **OK**.
        

        > [!NOTE]
        > Stellen Sie sicher, dass die für die Verbindung mit der Exchange 2013-Gesamtstruktur verwendeten Administratoranmeldeinformationen auch für Remote-PowerShell-Verbindungen mit dieser Gesamtstruktur verwendet werden können.<BR>Die folgende Abbildung zeigt, wie Sie die Bereitstellung für Exchange 2013 auswählen.

        
        **Bereitstellen des GalSync-Verwaltungs-Agents für Exchange 2013**
        
        ![Exchange 2010 Verwaltungs-Agent-Bereitstellung](images/Aa998597.8f403cda-e5e4-4edf-887f-c1ed46cee3f5(EXCHG.150).gif "Exchange 2010 Verwaltungs-Agent-Bereitstellung")  

4.  Erstellen Sie in jeder Gesamtstruktur einen SMTP-Sendeconnector. Ausführliche Anleitungen finden Sie unter [Konfigurieren eines gesamtstrukturübergreifenden Sendeconnectors](configure-a-cross-forest-send-connector-exchange-2013-help.md).

5.  Aktivieren Sie in jeder Gesamtstruktur den Verfügbarkeitsdienst, so dass die Benutzer in jeder Gesamtstruktur die Frei/Gebucht-Daten der Benutzer in der anderen Gesamtstruktur anzeigen können. Weitere Informationen finden Sie unter [Verfügbarkeitsdienst in Exchange 2013](availability-service-in-exchange-2013-exchange-2013-help.md).

6.  Wenn gewünscht ist, dass E-Mail mittels Relay durch eine beliebige Gesamtstruktur innerhalb Ihrer Organisation weitergeleitet werden kann, müssen Sie eine Domäne in dieser Gesamtstruktur als autoritative Domäne konfigurieren. Ausführliche Anleitungen finden Sie unter [Konfigurieren von Exchange für das Annehmen von Nachrichten für mehrere autoritative Domänen](configure-exchange-to-accept-mail-for-multiple-authoritative-domains-exchange-2013-help.md).

