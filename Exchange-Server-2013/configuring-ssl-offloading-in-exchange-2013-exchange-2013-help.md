---
title: 'Konfigurieren der SSL-Abladung in Exchange 2013: Exchange 2013 Help'
TOCTitle: Konfigurieren der SSL-Abladung in Exchange 2013
ms:assetid: 654cc2c2-918b-48fc-9532-9c8e3012810d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn635115(v=EXCHG.150)
ms:contentKeyID: 61201340
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der SSL-Abladung in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-08-22_

Die folgenden Hinweise unterstützen Sie beim Konfigurieren der SSL-Abladung für die Protokolle und zugehörigen Dienste auf Exchange 2013-Clientzugriffsservern mit installiertem Service Pack 1 (SP1). Wenn Sie mehrere Clientzugriffsserver verwenden, müssen Sie die erforderlichen Schritte für jedes Protokoll bzw. jeden Dienst auf jedem Clientzugriffsserver mit installiertem SP1 in Ihrer lokalen Organisation ausführen. Alle Clientzugriffsserver in der Organisation müssen gleich konfiguriert sein. Wenn Sie ein Upgrade auf neuere kumulative Updates oder Service Packs vornehmen und weiterhin SSL-Abladung verwenden möchten, müssen Sie die folgenden Schritte nach dem Upgrade bzw. der Anwendung dieser Updates auf die Exchange 2013-Clientzugriffsserver erneut ausführen.

Einer der größten Vorteile der SSL-Abladung besteht darin, dass sich die verwendeten Zertifikate einfacher verwalten lassen. Statt separater SSL-Zertifikate für jeden Clientzugriffsserver mit SP1 wird ein einzelnes SSL-Zertifikat verwendet, das auf allen Clientzugriffsservern importiert wird. Das verwendete Zertifikat kann ein vorhandenes oder ein neu erstelltes SSL-Zertifikat sein.


> [!WARNING]
> Wenn Sie den Internetinformationsdienste-Manager, die Exchange-Verwaltungsshell oder eine Befehlszeilenschnittstelle zum Konfigurieren der SSL-Abladung verwenden, beachten Sie, dass es eine <STRONG>Standardwebsite</STRONG> und eine <STRONG>Exchange-Back-End</STRONG>-Website gibt. Konfigurieren Sie für die SSL-Abladung nur die <STRONG>Standardwebsite</STRONG>, und lassen Sie die <STRONG>Exchange-Back-End</STRONG>-Website unverändert.



**Inhalt**

Konfigurieren der SSL-Abladung für Outlook Web App

Konfigurieren der SSL-Abladung für die Exchange-Verwaltungskonsole

Konfigurieren der SSL-Abladung für Outlook Anywhere

Konfigurieren der SSL-Abladung für das Offlineadressbuch (OAB)

Konfigurieren der SSL-Abladung für Exchange ActiveSync (EAS)

Konfigurieren der SSL-Abladung für Exchange-Webdienste (EWS)

Konfigurieren der SSL-Abladung für den AutoErmittlungsdienst

Konfigurieren der SSL-Abladung für den Proxydienst für die Postfachreplikation (MRSProxy)

Konfigurieren der SSL-Abladung für Outlook-Clients (virtuelles Verzeichnis MAPI)

Aktivieren der SSL-Abladung für alle Protokolle und Dienste mithilfe eines Skripts

Konfigurieren der Koexistenz mit Exchange 2007 und Exchange 2010

## Was sollten Sie wissen, bevor Sie beginnen?

  - Installieren Sie alle erforderlichen Clientzugriffs- und Postfachserver in Ihrer Organisation.

  - Installieren Sie Service Pack 1 (SP1) auf jedem Clientzugriffs- und Postfachserver in der Organisation. SP1 können Sie unter [Updates für Exchange 2013](updates-for-exchange-2013-exchange-2013-help.md) herunterladen.

  - Bestimmen Sie die erforderlichen Berechtigungen für Exchange 2013. Informationen dazu finden Sie unter [Funktionsberechtigungen](feature-permissions-exchange-2013-help.md).

  - Informationen zu den erforderlichen Berechtigungen für Clientzugriffsserver finden Sie unter "Clientzugriffsserver – Berechtigungen" in [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu den erforderlichen Berechtigungen für Clientzugriffsserver finden Sie unter "Berechtigungen für Outlook Web App" in [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Möglicherweise können Sie einige Verfahren nur mit der Shell durchführen. Wie eine Shell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

  - Um ein vorhandenes Zertifikat auf den Clientzugriffsservern und dem Gerät, mit dem Sie die SSL-Verbindungen beenden, zu verwenden, exportieren Sie das Zertifikat mit dem privaten Schlüssel auf einem Clientzugriffsserver und importieren oder installieren es auf dem Gerät. Weitere Informationen finden Sie unter [Export-ExchangeCertificate](https://technet.microsoft.com/de-de/library/aa996305\(v=exchg.150\)).

  - Um ein neues Zertifikat zu verwenden, müssen Sie dieses mit der Exchange-Verwaltungskonsole oder der Shell erstellen, importieren und aktivieren. Weitere Informationen finden Sie unter [Exchange 2013-Benutzeroberfläche zur Zertifikatsverwaltung](exchange-2013-certificate-management-ui-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der SSL-Abladung für Outlook Web App

Um die SSL-Abladung für Outlook Web App zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **owa** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **owa** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **owa** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd set config "Default Web Site/owa" /section:access /sslFlags:None /commit:APPHOST
```

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeOWAAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeOWAAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für die Exchange-Verwaltungskonsole

Um die SSL-Abladung für die Exchange-Verwaltungskonsole zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **ecp** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **ecp** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **ecp** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd set config "Default Web Site/ecp" /section:access /sslFlags:None /commit:APPHOST
```
        

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeECPAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeECPAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für Outlook Anywhere

Die SSL-Abladung für Outlook Anywhere ist standardmäßig aktiviert. Outlook Anywhere-Clients können E-Mail aus einem privaten oder öffentlichen Netzwerk empfangen. Standardmäßig wird der interne Hostname oder FQDN des Servers verwendet, um internen Outlook-Clients die Verbindung zu ermöglichen. Wird Outlook Anywhere jedoch nicht intern verwendet, sollten Sie den internen Hostnamen entfernen. Um internen und externen Zugriff für Outlook-Clients zuzulassen, müssen Sie die internen und externen Hostnamen konfigurieren, die jeweilige Authentifizierungsmethode für beide festlegen sowie die Anforderung von SSL für interne und externe Clients festlegen. Zum Konfigurieren der Authentifizierungsmethode für die externen Clients können Sie die Exchange-Verwaltungskonsole oder die Exchange-Verwaltungsshell verwenden. Für interne Clients müssen Sie dagegen die Shell verwenden:

  - **Schritt 1**   Sie können die Exchange-Verwaltungskonsole oder die Shell verwenden, wenn Sie keinen externen Hostnamen für Outlook Anywhere hinzugefügt haben:
    
      - In der Exchange-Verwaltungskonsole: Gehen Sie zu **Server**, wählen Sie in der Liste den Namen des Clientzugriffsservers aus, und klicken Sie dann auf **Bearbeiten**. Klicken Sie im Fenster **Exchange-Server** auf **Outlook Anywhere**, und geben Sie dann im Feld **Geben Sie den externen Hostnamen (z. B. „contoso.com“) an, den Benutzer zum Herstellen der Verbindung mit Ihrer Organisation verwenden** den externen Hostnamen ein. Stellen Sie sicher, dass die Option **SSL-Abladung zulassen** ausgewählt ist, und klicken Sie dann auf **Speichern**.
    
      - In der Exchange-Verwaltungsshell: Klicken Sie auf **Start**, und klicken Sie dann im Menü **Start** auf **Exchange-Verwaltungsshell**. Geben Sie im Fenster Folgendes ein, und drücken Sie dann die EINGABETASTE:
        
            Set-OutlookAnywhere -Identity ClientAccessServer1\Rpc* -Externalhostname ClientAccessServer1.contoso.com -ExternalClientsRequireSsl:$True -ExternalClientAuthenticationMethod Basic

  - **Schritt 2** Die SSL-Abladung ist standardmäßig aktiviert. Falls sie jedoch deaktiviert wurde, können Sie sie auf Wunsch mit der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell wieder aktivieren:
    
      - In der Exchange-Verwaltungskonsole: Gehen Sie zu **Server**, wählen Sie in der Liste den Namen des Clientzugriffsservers aus, und klicken Sie dann auf **Bearbeiten**. Klicken Sie im Fenster **Exchange-Server** auf **Outlook Anywhere**, auf die Option **SSL-Abladung zulassen**, und dann auf **Speichern**.
    
      - Mit der Shell: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            Set-OutlookAnywhere -Identity ClientAccessServer1\Rpc* -SSLOffloading $true

  - **Schritt 3**   Die Option **SSL erforderlich** ist standardmäßig für das virtuelle Verzeichnis **Rpc** deaktiviert, aber wenn Sie überprüfen möchten, ob SSL deaktiviert ist, können Sie dies im Internetinformationsdienste-Manager tun.
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **Rpc** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Stellen Sie im Ergebnisbereich **SSL-Einstellungen** sicher, dass das Kontrollkästchen **SSL erforderlich** deaktiviert ist, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.

  - **Schritt 4**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeRpcProxyFrontEndAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeRpcProxyFrontEndAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.


> [!IMPORTANT]
> Sie müssen warten, bis der Diensthostprozess alle 15 Minuten Änderungen von Active Directory in Internetinformationsdienste (IIS) übernimmt. Dies gilt auch, wenn Sie IIS auf einem Clientzugriffsserver neu starten.



Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für das Offlineadressbuch (OAB)

Um die SSL-Abladung für das Offlineadressbuch (OAB) zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **OAB** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **OAB** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **OAB** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd set config "Default Web Site/OAB" /section:access /sslFlags:None /commit:APPHOST
```

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeOABAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeOABAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für Exchange ActiveSync (EAS)

Um die SSL-Abladung für Exchange ActiveSync (EAS) zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **Microsoft-Server-ActiveSync** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **Microsoft-Server-ActiveSync** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **Microsoft-Server-ActiveSync** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
            appcmd set config "Default Web Site/MSExchangeSyncAppPool" /section:access /sslFlags:None /commit:APPHOST

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeSyncAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeSyncAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für Exchange-Webdienste (EWS)

Um die SSL-Abladung für Exchange-Webdienste (EWS) zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **EWS** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **EWS** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **EWS** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd set config "Default Web Site/EWS" /section:access /sslFlags:None /commit:APPHOST
```

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeServicesAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeServicesAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für den AutoErmittlungsdienst

Um die SSL-Abladung für den AutoErmittlungsdienst zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **Autodiscover** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **Autodiscover** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **Autodiscover** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd set config "Default Web Site/autodiscover" /section:access /sslFlags:None /commit:APPHOST
```

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeAutodiscoverAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeAutodiscoverAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Konfigurieren der SSL-Abladung für den Proxydienst für die Postfachreplikation (MRSProxy)

Der Proxydienst für die Postfachreplikation (Mailbox Replication Proxy Service, MRSProxy Service) wird auf jedem Exchange 2013-Clientzugriffsserver installiert. MRSProxy vereinfacht lokale gesamtstrukturübergreifende Verschiebungsanforderungen sowie die Verschiebung lokaler Postfächer nach Office 365. MRSProxy ist jedoch standardmäßig deaktiviert. Wenn Sie es aktivieren, sollten Sie es in der Exchange-Remotegesamtstruktur für gesamtstrukturübergreifende, lokale Postfachverschiebungen oder in der lokalen Exchange-Gesamtstruktur für die Verschiebung eines Postfachs nach Office 365 aktivieren. Auch wenn der MRSProxy-Dienst unter den Exchange-Webdiensten (EWS) ausgeführt wird, wird die Konfiguration der SSL-Abladung dafür nicht unterstützt.

Dies liegt daran, dass der MRSProxy-Dienst signierten/verschlüsselten Datenverkehr erwartet. Jegliche Lastenausgleichshardware oder Firewall muss den MRSProxy-Verkehr vor der Übertragung an Clientzugriffsserver erneut verschlüsseln. In diesem Fall wird empfohlen, SSL-Bridging zu konfigurieren, damit die Abladung funktioniert.

**Reverse SSL oder SSL-Bridging**   Wenn Sie Reverse SSL oder SSL-Bridging auf Hardwaregeräten zum Lastenausgleich aktivieren, müssen Sie die vorherigen Schritte nicht auf jedem Clientzugriffsserver ausführen. Allerdings bedeutet die Aktivierung von Reverse SSL auf den Hardwaregeräten zum Lastenausgleich, dass die SSL-Verschlüsselung und -Entschlüsselung auf den Clientzugriffsservern erhalten bleibt. Dann erfolgt die SSL-Verschlüsselung und -Entschlüsselung sowohl auf den Hardwaregeräten für den Lastenausgleich als auch auf den Clientzugriffsservern. Die Entscheidung für die Verwendung der Exchange 2013 SSL-Abladung oder von Reverse SSL (SSL-Bridging) hängt von den zu implementierenden Unternehmenszielen und Sicherheitspraktiken ab. Die folgende Abbildung zeigt die Clientkonnektivität mit aktiviertem SSL-Bridging (Reverse SSL).

![SSL-Bridging](images/Dn635115.a08aacc1-0ab4-46b3-bdae-b9518a3f5748(EXCHG.150).jpg "SSL-Bridging")

## Konfigurieren der SSL-Abladung für Outlook-Clients (virtuelles Verzeichnis MAPI)

Um die SSL-Abladung für Outlook-Clients zu aktivieren, müssen Sie die SSL-Anforderung für das virtuelle Verzeichnis **MAPI** auf der **Standardwebsite** entfernen:

  - **Schritt 1**   Sie können den Internetinformationsdienste-Manager oder eine Befehlszeile verwenden, um SSL für das virtuelle Verzeichnis **MAPI** zu deaktivieren:
    
      - Erweitern Sie im Internetinformationsdienste-Manager **Websites** \> **Standardwebsite**, und wählen Sie dann das virtuelle Verzeichnis **MAPI** aus. Doppelklicken Sie im Ergebnisbereich unter **IIS** auf **SSL-Einstellungen**. Deaktivieren Sie im Ergebnisbereich **SSL-Einstellungen** das Kontrollkästchen **SSL erforderlich**, und klicken Sie dann im Bereich **Aktionen** auf **Übernehmen**.
    
      - Geben Sie in der Befehlszeile den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd set config "Default Web Site/MAPI" /section:access /sslFlags:None /commit:APPHOST
```

  - **Schritt 2**   Sie müssen mit einer der folgenden Methoden den richtigen Anwendungspool wiederverwenden oder die Internetinformationsdienste neu starten:
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
appcmd Recycle AppPool MSExchangeMapiFrontEndAppPool
```
    
      - Mit einem Windows PowerShell-Cmdlet: Geben Sie Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
            IIS:\>Restart-WebAppPool MSExchangeMapiFrontEndAppPool
    
      - Mit einer Befehlszeile: Gehen Sie zu **Start** \> **Ausführen**, geben Sie **cmd** ein, und drücken Sie dann die EINGABETASTE. Geben Sie im Eingabeaufforderungsfenster Folgendes ein, und drücken Sie dann die EINGABETASTE.
        
        ```powershell
iisreset /noforce
```
    
      - Mit dem Internetinformationsdienste-Manager: Klicken Sie im Internetinformationsdienste-Manager im Bereich **Aktionen** auf **Neu starten**.

Zurück zum Seitenanfang

## Aktivieren der SSL-Abladung für alle Protokolle und Dienste mithilfe eines Skripts

Wenn Sie eine umfangreiche Organisation mit mehreren Exchange 2013-Clientzugriffsservern verwenden, können Sie die vorherigen Schritte beschleunigen. Sie können die Befehle aus jedem der folgenden Skripts kopieren und in Editor einfügen, dort Änderungen vornehmen, die Datei mit der Erweiterung ".ps1" speichern und dann in der Exchange-Verwaltungsshell ausführen. Sie können beide Skripts je nach Ihren Anforderungen verwenden, um die SSL-Abladung für alle Protokolle und Dienste für einen einzelnen oder mehrere Clientzugriffsserver zu konfigurieren.


> [!NOTE]
> Ersetzen Sie für die Einträge des Cmdlets <STRONG>Set-OutlookAnywhere</STRONG> "MyServer" durch den Namen Ihres/Ihrer Clientzugriffsserver(s).



**Mithilfe von "Set-WebConfigurationProperty"**

    Set-OutlookAnywhere -Identity MyServer\Rpc* -Externalhostname MyServer.mail.contoso.com -ExternalClientsRequireSsl $True -ExternalClientAuthenticationMethod Basic
    Set-OutlookAnywhere -Identity MyServer\Rpc* -SSLOffloading $true
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS:  -Location "Default Web Site/OWA"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/ecp"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/EWS"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/Autodiscover"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/Microsoft-Server-ActiveSync"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/OAB"
    Set-WebConfigurationProperty -Filter //security/access -name sslflags -Value "None" -PSPath IIS: -Location "Default Web Site/MAPI"
```powershell
iisreset /noforce
```

**Mithilfe von "appcmd"**


> [!NOTE]
> Ersetzen Sie für die Einträge des Cmdlets <STRONG>Set-OutlookAnywhere</STRONG> "MyServer" durch den Namen Ihres/Ihrer Clientzugriffsserver(s).



    Set-OutlookAnywhere -Identity MyServer\Rpc* -Externalhostname MyServer.mail.contoso.com -ExternalClientsRequireSsl $True -ExternalClientAuthenticationMethod Basic
    Set-OutlookAnywhere -Identity MyServer\Rpc* -SSLOffloading $true
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/owa" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/ecp" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/EWS" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/Autodiscover" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/Microsoft-Server-ActiveSync" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/OAB" /section:access /sslFlags:None /commit:APPHOST
    &$env:systemroot\system32\inetsrv\appcmd set config "Default Web Site/MAPI" /section:access /sslFlags:None /commit:APPHOST
```powershell
iisreset /noforce
```

Zurück zum Seitenanfang

## Konfigurieren der Koexistenz mit Exchange 2007 und Exchange 2010

In einem Koexistenzszenario, bei dem sowohl Exchange 2003- als auch Exchange 2010-Server in der Organisation verwendet werden, besteht einer der ersten Schritte nach der Bereitstellung der Exchange 2010-Clientzugriffsserver in der Änderung von DNS, sodass Exchange 2003-Benutzer von einer Gruppe von Exchange 2010-Clientzugriffsservern auf ihre Postfächer zugreifen. In einem solchen Szenario wird die Aktivierung der SSL-Abladung auf der Lastenausgleichshardware, mit der der Clientdatenverkehr auf die Clientzugriffsserver verteilt wird, vollständig unterstützt.

**Koexistenz mit anderen Versionen von Outlook Web App**

Wenn die SSL-Abladung auf den Exchange 2013-Clientzugriffsservern konfiguriert ist, ist Koexistenz mit Exchange 2007 und Exchange 2010 möglich:

  - Für die Koexistenz mit Exchange 2007 ist ein früherer Namespace erforderlich, und die Umleitung zu diesem erfolgt nur für Outlook Web App und Exchange-Webdienste. AutoErmittlung, Outlook Anywhere und Exchange ActiveSync werden über einen Proxy an die früheren Versionen weitergeleitet.

  - Für die Koexistenz mit Exchange 2010 wird, wenn Sie die externe URL festgelegt haben, eine Umleitung verwendet. Andernfalls wird ein Proxy verwendet.

Zurück zum Seitenanfang

