---
title: 'Problembehandlung in einer Hybridbereitstellung: Exchange 2013 Help'
TOCTitle: Problembehandlung in einer Hybridbereitstellung
ms:assetid: bbae72f3-6a1e-4cbf-80da-d8f73d969c6b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659053(v=EXCHG.150)
ms:contentKeyID: 50477189
ms.date: 01/03/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung in einer Hybridbereitstellung

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-04-29_

Durch die Konfiguration einer Hybridbereitstellung in Exchange mit dem Assistenten für die Hybridkonfiguration wird das Risiko von Problemen in der Hybridbereitstellung minimiert. Es gibt jedoch einige typische Bereiche, die den Rahmen des Assistenten für die Hybridkonfiguration übersteigen. Sofern dieser fehlerhaft konfiguriert ist, kann dies zu Problemen in der Hybridbereitstellung führen. In diesem Thema werden die folgenden gängigen Bereiche erläutert, in denen Probleme auftreten können. Ferner werden grundlegende Schritte beschrieben, um die Probleme zu überprüfen und zu korrigieren:

  - Lokale Exchange-Server

  - Zertifikate

  - Spezifische Fehler im Assistenten für die Hybridkonfiguration


> [!NOTE]
> In diesem Thema beziehen sich „Exchange-Server“ auf Folgendes: 
> <UL>
> <LI>
> <P><STRONG>Clientzugriffsserver</STRONG> Exchange 2013 und früher</P>
> <LI>
> <P><STRONG>Postfachserver</STRONG> Exchange 2016 und höher</P></LI></UL>



Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Hybridbereitstellungen finden Sie unter [Hybrid-Bereitstellungsverfahren](hybrid-deployment-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: Variiert je nach Art der Hybridbereitstellungsprobleme

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Hybridbereitstellungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](https://technet.microsoft.com/de-de/library/dd638114\(v=exchg.150\)).

  - Die Anleitungen in diesem Thema gelten für Hybridbereitstellungen, die mithilfe des Assistenten für die Hybridkonfiguration konfiguriert wurden. Manuell konfigurierte Hybridbereitstellungen werden nicht unterstützt.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://technet.microsoft.com/de-de/library/jj150484\(v=exchg.150\)).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Problembehandlung bei lokalen Exchange-Servern

Bei der Konfiguration der lokalen Exchange-Server handelt es sich für gewöhnlich um den Bereich, in dem die meisten Probleme in einer Hybridbereitstellung auftreten. Für gewöhnlich müssen die folgenden Bereiche untersucht werden:

  - **Verfügbarkeit**: Die ordnungsgemäße Veröffentlichung der lokalen Exchange-Server im Internet ist dahingehend wichtig, dass die Features in der Hybridbereitstellung richtig funktionieren. Damit eine Hybridbereitstellung problemlos funktioniert, müssen die lokale Firewall und andere Sicherheits-Appliances so konfiguriert werden, dass der eingehende Zugriff vom Internet auf die AutoErmittlungs- und Exchange-Webdienst-Endpunkte auf den lokalen Exchange-Servern zugelassen wird. Außerdem müssen Exchange-Server so konfiguriert werden, dass eingehende SMTP-E-Mails akzeptiert werden. Wenn der Microsoft Exchange Online Protection-Dienst (EOP) in der Office 365-Organisation die lokalen Exchange-Server nicht erreichen kann, funktioniert der sichere E-Mail-Transport von der Exchange Online-Organisation zur lokalen Organisation nicht ordnungsgemäß.

  - **Zertifikate**: Das für den sicheren E-Mail-Transport zwischen der lokalen und der Exchange Online-Organisation verwendete digitale Zertifikat muss auf allen lokalen Exchange-Servern mit Internetzugriff installiert sein, die mit Exchange Online kommunizieren. Es muss von einer externen Zertifizierungsstelle ausgegeben worden sein. Zudem darf es nicht abgelaufen und ihm müssen IIS- und SMTP-Dienste zugewiesen sein. Wenn diese Zertifikatsanforderungen nicht erfüllt werden, funktioniert der sichere E-Mail-Transport zwischen der Exchange Online-Organisation und der lokalen Organisation nicht ordnungsgemäß. Weitere Informationen zu Zertifikatsanforderungen finden Sie im Abschnitt „Behandlung von Zertifikatsproblemen“ weiter unten in diesem Thema.

## Woran kann erkannt werden, ob Ihre Exchange-Server richtig konfiguriert sind?

Zum Überprüfen der erfolgreichen Veröffentlichung der lokalen Exchange-Server können Sie die Microsoft-Remoteverbindungsuntersuchung verwenden, um die eingehende Internetanbindung zu den lokalen Exchange-Servern zu überprüfen. Gehen Sie wie folgt vor:

1.  Rufen Sie das Tool [Remoteverbindungsuntersuchung](https://www.testexchangeconnectivity.com/) auf.

2.  Dieser Schritt dient zum allgemeinen Testen der Funktion von Exchange-Webdienste-Tasks und der Konfiguration des -Endpunkts.
    
    Führen Sie den Test **Synchronisierung, Benachrichtigung, Verfügbarkeit und automatische Antworten (Abwesenheitsnachrichten)** im Abschnitt **Verbindungstests für Microsoft Exchange-Webdienste** aus, und überprüfen Sie, ob Fehler vorliegen. Wenn Fehler auftreten, korrigieren Sie die Elemente, die durch den Test ermittelt wurden.

3.  Dieser Schritt dient zum allgemeinen Testen der Funktion des AutoErmittlungs-Diensts und der Konfiguration des -Endpunkts.
    
    Führen Sie den Test **Outlook-AutoErmittlung** im Abschnitt **Verbindungstests für Microsoft Office Outlook** aus, und überprüfen Sie, ob Fehler vorliegen. Wenn Fehler auftreten, korrigieren Sie die Elemente, die durch den Test ermittelt wurden.

4.  Dieser Schritt dient dem allgemeinen Testen der SMTP-Konnektivität und der Bestätigung, dass die Exchange-Server eingehende Internet-E-Mails empfangen können.
    
    Führen Sie den Test **Eingehende SMTP-E-Mail** im Abschnitt **Tests für Internet-E-Mail** aus, und überprüfen Sie, ob Fehler vorliegen. Wenn Fehler auftreten, korrigieren Sie die Elemente, die durch den Test ermittelt wurden.

## Behandlung von Zertifikatsproblemen

Die Konfiguration von Zertifikaten, die auf lokalen Exchange-Servern installiert sind, verursacht möglicherweise Probleme in einer Hybridbereitstellung. In den meisten Fällen beeinflussen die folgenden zertifikatsbezogenen Probleme die Hybridfunktionalität:

  - **Zertifikattyp**   Das digitale Zertifikat, das für den sicheren Hybridtransport verwendet wird und im Assistenten für die Hybridkonfiguration definiert ist, muss von einer externen Zertifizierungsstelle ausgegeben werden. Selbstsignierte Zertifikate können nicht für die Authentifizierung des Hybridtransports verwendet werden. Wenn ein selbstsigniertes Zertifikat versehentlich ausgewählt oder zugewiesen wird, funktioniert der sichere E-Mail-Transport zwischen der Exchange Online- und der lokalen Organisation nicht ordnungsgemäß.

  - **Zugewiesene Dienste**   IIS- (Internetinformationsdienste) und SMTP-Dienste (Simple Mail Transport Protocol) müssen dem digitalen Zertifikat zugewiesen werden, das für den Hybridtransport verwendet wird. Wenn diese Dienste nicht zugewiesen werden, funktioniert der sichere E-Mail-Transport zwischen der Exchange Online-Organisation und der lokalen Organisation nicht ordnungsgemäß.

  - **Installation:**  Das für den sicheren E-Mail-Transport zwischen der lokalen und der Exchange Online-Organisation verwendete digitale Zertifikat muss auf allen lokalen Exchange-Servern installiert sein. Wenn Sie eine Hybridbereitstellung mit lokalen Edge-Transport-Servern einrichten, muss das digitale Zertifikat auch auf den Edge-Transport-Servern installiert werden. Wenn das Zertifikat nicht auf den lokalen Servern installiert ist, funktioniert der sichere E-Mail-Transport zwischen der Exchange Online-Organisation und der lokalen Organisation nicht ordnungsgemäß.

  - **Ablauf**   Das digitale Zertifikat, das für den sicheren E-Mail-Transport zwischen der lokalen und der Exchange Online-Organisation verwendet wird, darf nicht ablaufen. Wenn das Zertifikat abläuft, funktioniert der sichere E-Mail-Transport zwischen der Exchange Online-Organisation und der lokalen Organisation nicht ordnungsgemäß.

## So erkennen Sie, ob Ihre Zertifikate ordnungsgemäß konfiguriert sind?

Gehen Sie wie folgt vor, um zu überprüfen, ob das Zertifikat für den Hybrid-E-Mail-Transport ordnungsgemäß auf den lokalen Exchange-Servern konfiguriert ist:

1.  Öffnen Sie auf einem lokalen Exchange-x-Server die Exchange-Verwaltungsshell.

2.  Führen Sie in der Exchange-Verwaltungsshell den folgenden Befehl aus.
    
        Get-ExchangeCertificate| format-list

3.  Suchen Sie die Informationen für das Zertifikat, das im Assistenten für die Hybridkonfiguration zur Verwendung für den sicheren E-Mail-Transport definiert wurde.

4.  Überprüfen Sie, ob die folgenden Parameterwerte dem Zertifikat zugewiesen wurden:
    
      - **IsSelfSigned-Parameter**   Dieser Parameterwert sollte *False* lauten.
    
      - **RootCAType-Parameter**   Dieser Parameterwert sollte *Third Party* lauten.
    
      - **Services-Parameter**   Dieser Parameterwert sollte *IIS, SMTP* lauten.
    
      - **NotAfter-Parameter**   Dieser Parameterwert ist das Ablaufdatum. Das hier aufgeführte Datum sollte nicht abgelaufen sein.

## Beheben spezifischer Fehler im Assistenten für die Hybridkonfiguration

Wenn bei der Ausführung des Assistenten für die Hybridkonfiguration ein Fehler angezeigt wird, lässt sich das Problem häufig beheben, indem sie ein paar einfache Prüfungen und Schritte ausführen. Hier finden Sie Vorschläge zur Behebung bestimmter Meldungen oder Probleme, die bei Ausführung des Assistenten für die Hybridkonfiguration angezeigt bzw. auftreten können.

  - **Meldung: „Default Receive Connector cannot be found on server \<Server Name\>“**. Diese Meldung wird angezeigt, wenn der Empfangsconnector auf einem im folgenden Attribut aufgeführten Exchange 25-Exchange-Server sowohl bei IPv4- als auch bei IPv6-Protokollen den TCP-Port 25 nicht überwacht: `(Get-HybridConfiguration).ReceivingTransportServers.`
    
      -  
        Führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus, um zu überprüfen, ob die auf den Exchange-Servern aufgelisteten Empfangsconnectors beim Ausführen von `(Get-HybridConfiguration).ReceivingTransportServers.` über die richtigen Verbindungen verfügen.
        
            Get-ReceiveConnector -Server <Server Name> | FT Identity, Bindings
        
        Der folgende Eintrag sollte für Ihre Exchange-Server aufgeführt werden: `{[::]:25, 0.0.0.0:25}`
        
        Wenn diese Anschlussbindung nicht aufgeführt wird, müssen Sie sie mithilfe des Parameters *Bindings* des Cmdlets **Set-ReceiveConnector** zur Ihrem Empfangsconnector hinzufügen. Weitere Informationen finden Sie unter [Set-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125140\(v=exchg.150\)).

