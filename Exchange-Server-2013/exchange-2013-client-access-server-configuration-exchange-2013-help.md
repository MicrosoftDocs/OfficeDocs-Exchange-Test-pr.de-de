---
title: 'Konfiguration des Exchange 2013-Clientzugriffsservers: Exchange 2013 Help'
TOCTitle: Konfiguration des Exchange 2013-Clientzugriffsservers
ms:assetid: 01432ae4-2a00-44a4-a4dd-4eb8d7e6cfae
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529912(v=EXCHG.150)
ms:contentKeyID: 50474937
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfiguration des Exchange 2013-Clientzugriffsservers

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-07-25_

Nach der Installation des Exchange 2013-Clientzugriffsservers können Sie verschiedene Konfigurationsaufgaben ausführen. Wenngleich der Clientzugriffsserver in Exchange 2013 nicht für die Verarbeitung der Clientprotokolle eingesetzt wird, müssen eine Reihe von Einstellungen auf den Clientzugriffsserver angewendet werden. Dazu zählen u. a. Einstellungen für das virtuelle Verzeichnis sowie Zertifikateinstellungen.

## Konfigurieren von Serverzertifikaten

In Exchange 2013 kann der Zertifikat-Assistent verwendet werden, um ein digitales Zertifikat von einer Zertifizierungsstelle anzufordern. Nachdem Sie ein digitales Zertifikat angefordert haben, muss dieses auf dem Clientzugriffsserver installiert werden.

Auf den Postfachservern in Ihrer Organisation müssen keine digitalen Zertifikate installiert werden. Auf den Postfachservern wird standardmäßig ein selbstsigniertes Zertifikat installiert, das nicht ersetzt werden muss. Die Clientzugriffsserver in Ihrer Organisation stufen das selbstsignierte Zertifikat auf den Postfachservern implizit als vertrauenswürdig ein. Weitere Informationen finden Sie unter [Exchange 2013-Benutzeroberfläche zur Zertifikatsverwaltung](exchange-2013-certificate-management-ui-exchange-2013-help.md).

## Konfigurieren von virtuellen Verzeichnissen

Für die virtuellen Verzeichnisse für das Offlineadressbuch (OAB), die Exchange-Webdienste, Exchange ActiveSync, Outlook Web App und die Exchange-Verwaltungskonsole können verschiedene Einstellungen konfiguriert werden. Weitere Informationen zur Verwaltung von virtuellen Verzeichnissen finden Sie unter [Verwaltung für virtuelle Verzeichnisse](virtual-directory-management-exchange-2013-help.md). Sie können die virtuellen Verzeichnisse mit den folgenden Befehlen konfigurieren.

  - Exchange 2013 bietet zwei Sätze mit HTTP-Verbindungseinstellungen für die Outlook Anywhere-Konfiguration, sodass Administratoren sowohl einen internen als auch einen externen Endpunkt konfigurieren können.
    
    Für die Konfiguration von Outlook Anywhere mit einer einzelnen URL für die Verbindung müssen Sie den Hostnamen angeben, festlegen, ob SSL erforderlich ist, und mit dem folgenden Befehl in der Exchange-Verwaltungsshell ein AuthPackage angeben:
    
        Get-OutlookAnywhere | Set-OutlookAnywhere -InternalHostname "internalServer.contoso.com" -InternalClientAuthenticationMethod Ntlm -InternalClientsRequireSsl $true -IISAuthenticationMethods Negotiate,NTLM,Basic
    
    Sie können außerdem mit dem folgenden Befehl in der Exchange-Verwaltungsshell einen extern erreichbaren Endpunkt angeben:
    
        Get-OutlookAnywhere | Set-OutlookAnywhere -InternalHostname "internalServer.contoso.com" -InternalClientAuthenticationMethod Ntlm -InternalClientsRequireSsl $true -ExternalHostname "externalServer.company.com" -ExternalClientAuthenticationMethod Basic -ExternalClientsRequireSsl $true -IISAuthenticationMethods Negotiate,NTLM,Basic
    

    > [!TIP]
    > Exchange 2013 unterstützt zwar Aushandeln für die HTTP-Authentifizierung in Outlook Anywhere, doch sollte dies nur verwendet werden, wenn auf allen Servern der Umgebung Exchange 2013 ausgeführt wird.



  - Zum Konfigurieren von Exchange ActiveSync führen Sie den folgenden Befehl aus.
    
        Set-ActiveSyncVirtualDirectory -Identity "<CAS2013>\Microsoft-Server-ActiveSync (Default Web Site)" -ExternalUrl "https://mail.contoso.com/Microsoft-Server-ActiveSync"

  - Zum Konfigurieren des virtuellen Verzeichnisses für die Exchange-Webdienste führen Sie den folgenden Befehl aus.
    
        Set-WebServicesVirtualDirectory -Identity "<CAS2013>\EWS (Default Web Site)" -ExternalUrl https://mail.contoso.com/EWS/Exchange.asmx

  - Zum Konfigurieren des Offlineadressbuchs führen Sie den folgenden Befehl aus.
    
        Set-OABVirtualDirectory -Identity "<CAS2013>\OAB (Default Web Site)" -ExternalUrl "https://mail.contoso.com/OAB"

  - Führen Sie zum Konfigurieren des Dienstverbindungspunkts den folgenden Befehl aus.
    
        Set-ClientAccessServer -Identity <CAS2013> -AutoDiscoverServiceInternalURI https://autodiscover.contoso.com/AutoDiscover/AutoDiscover.xml

## Upgrade von Exchange 2007- und 2010-Clientzugriff

Dieser Abschnitt unterstützt Sie bei der Konfiguration des externen Zugriffs auf Protokolle auf dem Exchange 2013-Clientzugriffsserver. Führen Sie sowohl die im obigen Abschnitt zur Konfiguration virtueller Verzeichnisse aufgeführten Befehle der Exchange-Verwaltungsshell als auch die nachfolgenden Befehle aus.

Sie müssen folgende Befehle ausführen, um die virtuellen Verzeichnisse für Exchange 2013 zu konfigurieren.

1.  Zur Konfiguration einer externen URL für Outlook Web App führen Sie den folgenden Befehl in der Exchange-Verwaltungsshell aus.
    
    ```
    Set-OwaVirtualDirectory "<CAS2013>\OWA (Default Web Site)" -ExternalUrl https://mail.contoso.com/OWA
    ```
    
    Führen Sie an einer Eingabeaufforderung die folgenden Befehle aus, nachdem Sie das virtuelle Outlook Web App-Verzeichnis festgelegt haben.
    
    ```
```powershell
Net stop IISAdmin /y
```
    ```

    ```
```powershell
Net start W3SVC
```
    ```


2.  Führen Sie zum Konfigurieren des externen Zugriffs auf die Exchange-Verwaltungskonsole den folgenden Befehl in der Exchange-Verwaltungsshell aus.
    
    ```
    Set-EcpVirtualDirectory "<CAS2013>\ECP (Default Web Site)" -ExternalUrl https://mail.contoso.com/ECP -InternalURL https://mail.contoso.com/ECP 
    ```

3.  Führen Sie zum Konfigurieren des Verfügbarkeitsdiensts den folgenden Befehl in der Exchange-Verwaltungsshell aus.
    
    ```
    Set-WebServicesVirtualDirectory -Identity "<CAS2013>\EWS (Default Web Site)" -ExternalURL https://mail.contoso.com/EWS/Exchange.asmx
    ```

Mit der Remoteverbindungsuntersuchung, einem kostenlosen webbasierten Tool von Microsoft, können Sie prüfen, ob die externe URL ordnungsgemäß für Exchange ActiveSync oder Outlook Web App konfiguriert wurde. Sie finden die Remoteverbindungsuntersuchung [hier](http://go.microsoft.com/fwlink/?linkid=154308).

Mit ExRCA können Sie ferner prüfen, ob die Authentifizierung ordnungsgemäß für Exchange ActiveSync oder Outlook Web App konfiguriert wurde.

Um zu prüfen, ob der direkte Dateizugriff ordnungsgemäß für Outlook Web App konfiguriert wurde, melden Sie sich mithilfe der Option für öffentliche Computer als Benutzer bei Outlook Web App an, und versuchen Sie anschließend, auf eine E-Mail mit Dateianlage zuzugreifen und die Anlage zu speichern.

## Konfigurieren von Protokollen auf den Exchange 2007-Clientzugriffsservern

Sie müssen folgende Befehle ausführen, um die virtuellen Verzeichnisse für Exchange 2007 zu konfigurieren.

  - Zum Konfigurieren der externen URL im virtuellen Exchange ActiveSync-Verzeichnis führen Sie in der Exchange-Verwaltungsshell den folgenden Befehl aus.
    
        Set-ActiveSyncVirtualDirectory -Identity "<CAS2007>\Microsoft-Server-ActiveSync (Default Web Site)" -ExternalUrl https://mail.contoso.com/Microsoft-Server-ActiveSync

  - Zum Konfigurieren der externen URL im virtuellen Outlook Web App-Verzeichnis führen Sie in der Exchange-Verwaltungsshell den folgenden Befehl aus.
    
        Set-OwaVirtualDirectory -Identity "<CAS2007>\owa (Default Web Site)" -ExternalUrl https://legacy.contoso.com/owa
