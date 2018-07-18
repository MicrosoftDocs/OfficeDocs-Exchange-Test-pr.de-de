---
title: 'Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen: Exchange 2013 Help'
TOCTitle: Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen
ms:assetid: f703e153-98e2-4268-8a6e-07a86b0a1d22
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn594521(v=EXCHG.150)
ms:contentKeyID: 61170763
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In reinen Exchange 2013-Hybridbereitstellungen wird bei Verwendung des Assistenten für die Hybridkonfiguration die OAuth-Authentifizierung konfiguriert. Bei gemischten Exchange 2013/2010- und Exchange 2013/2007-Hybridbereitstellungen wird die neue OAuth-basierte Authentifizierungsverbindung zwischen Office 365 und lokalen Exchange-Organisationen für Hybridbereitstellungen nicht vom Assistenten für die Hybridkonfiguration konfiguriert. In diesen Bereitstellungen wird standardmäßig weiterhin der Verbundvertrauensstellungsprozess verwendet. Bestimmte Exchange 2013-Funktionen sind jedoch nur vollständig in Ihrer gesamten Organisation verfügbar, wenn das neue Exchange OAuth-Authentifizierungsprotokoll benutzt wird.

Mit dem neuen Exchange OAuth-Authentifizierungsprozess werden derzeit die folgenden Exchange-Funktionen aktiviert:

  - Message Rights Management (MRM)

  - Compliance-eDiscovery-Suche unter Exchange

  - Compliance-Archivierung in Exchange

Sie sollten in allen gemischten Exchange-Organisationen, in denen eine Hybridbereitstellung mit Exchange 2013 und Exchange Online implementiert wird, die Exchange-OAuth-Authentifizierung konfigurieren, nachdem Sie die Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration konfiguriert haben.


> [!IMPORTANT]
> Wenn in Ihrer lokalen Organisation nur Exchange 2013-Server mit installiertem kumulativen Update 5 oder höher ausgeführt werden, führen Sie den Assistenten für die Hybridbereitstellung anstelle der Schritte in diesem Thema aus.<BR>Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verbund- und Zertifikatberechtigungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Abgeschlossene Konfiguration Ihrer Hybridbereitstellung mit dem Hybridbereitstellungs-Assistenten. Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/de-de/library/jj200581\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie konfigurieren Sie die OAuth-Authentifizierung zwischen Ihren lokalen Exchange- und den Exchange-Online-Organisationen?

## Schritt 1: Erstellen eines Autorisierungsserverobjekts für Ihre Exchange-Online-Organisation

Bei diesem Verfahren müssen Sie eine verifizierte Domäne für Ihre Exchange-Online-Organisation angeben. Diese Domäne sollte der als primäre SMTP-Domäne verwendeten Domäne entsprechen, welche für die cloudbasierten E-Mail-Konten verwendet wird. Diese Domäne wird im folgenden Verfahren als *\<Ihre verifizierte Domäne\>* bezeichnet.

Führen Sie in der Exchange-Verwaltungsshell (Exchange PowerShell) den folgenden Befehl für Ihre lokale Exchange-Organisation aus.

    New-AuthServer -Name "WindowsAzureACS" -AuthMetadataUrl https://accounts.accesscontrol.windows.net/<your verified domain>/metadata/json/1

## Schritt 2: Aktivieren der Partneranwendung für Ihre Exchange-Online-Organisation

Führen Sie den folgenden Befehl in der Exchange PowerShell in Ihrer lokalen Exchange-Organisation aus.

    Get-PartnerApplication |  ?{$_.ApplicationIdentifier -eq "00000002-0000-0ff1-ce00-000000000000" -and $_.Realm -eq ""} | Set-PartnerApplication -Enabled $true

## Schritt 3: Exportieren des lokalen Autorisierungszertifikats

In diesem Schritt müssen Sie ein PowerShell-Skript ausführen, um das lokale Autorisierungszertifikat zu exportieren, welches dann im nächsten Schritt in Ihre Exchange-Online-Organisation importiert wird.

1.  Speichern Sie den folgenden Text in einer PowerShell-Skriptdatei, die etwa **ExportAuthCert.ps1** benannt werden kann.
    
        $thumbprint = (Get-AuthConfig).CurrentCertificateThumbprint
         
        if((test-path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
        {
            md $env:SYSTEMDRIVE\OAuthConfig
        }
        cd $env:SYSTEMDRIVE\OAuthConfig
         
        $oAuthCert = (dir Cert:\LocalMachine\My) | where {$_.Thumbprint -match $thumbprint}
        $certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
        $certBytes = $oAuthCert.Export($certType)
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        [System.IO.File]::WriteAllBytes($CertFile, $certBytes)

2.  Führen Sie unter Exchange PowerShell in Ihrer lokalen Exchange-Organisation das PowerShell-Skript aus, welches Sie im vorherigen Schritt erstellt haben. Beispiel:
    
        .\ExportAuthCert.ps1

## Schritt 4: Hochladen des lokalen Autorisierungszertifikats auf Azure Active Directory ACS

Als Nächstes müssen Sie Windows PowerShell verwenden, um das lokale Autorisierungszertifikat hochzuladen, das Sie im vorhergehenden Schritt an Azure Active Directory-Zugriffssteuerungsdienste (Access Control Services, ACS) exportiert haben. Dafür müssen Sie die Azure Active Directory-Modul für Windows PowerShell-Cmdlets installieren. Sollten diese noch nicht installiert sein, navigieren Sie zu <https://aka.ms/aadposh>, um das Azure Active Directory-Modul für Windows PowerShell zu installieren. Führen Sie die folgenden Schritte aus, nachdem Sie das Azure Active Directory-Modul für Windows PowerShell installiert haben.

1.  Klicken Sie auf die Verknüpfung **Azure Active Directory-Modul für Windows PowerShell**, um einen Windows PowerShell-Arbeitsbereich zu öffnen, in dem die Azure AD-Cmdlets installiert sind. Alle Befehle in diesem Schritt werden unter Verwendung der Windows PowerShell für die Azure Active Directory-Konsole ausgeführt.

2.  Speichern Sie den folgenden Text in einer PowerShell-Skriptdatei, die etwa **UploadAuthCert.ps1** benannt werden kann.
    
        Connect-MsolService;
        Import-Module msonlineextended;
        
        $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
        
        $objFSO = New-Object -ComObject Scripting.FileSystemObject;
        $CertFile = $objFSO.GetAbsolutePathName($CertFile);
        
        $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
        $cer.Import($CertFile);
        $binCert = $cer.GetRawCertData();
        $credValue = [System.Convert]::ToBase64String($binCert);
        
        $ServiceName = "00000002-0000-0ff1-ce00-000000000000";
        
        $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName
        New-MsolServicePrincipalCredential -AppPrincipalId $p.AppPrincipalId -Type asymmetric -Usage Verify -Value $credValue

3.  Führen Sie das PowerShell-Skript aus, welches Sie im vorherigen Schritt erstellt haben. Beispiel:
    
        .\UploadAuthCert.ps1

4.  Nachdem Sie das Skript gestartet haben, wird ein Dialogfeld für Anmeldeinformationen angezeigt. Geben Sie die Anmeldeinformationen für das Mandantenadministratorkonto in Ihrer Microsoft Online Azure AD-Organisation ein. Lassen Sie Windows PowerShell nach der Ausführung des Skripts für die Azure AD-Sitzung geöffnet. Sie werden diese zum Ausführen eines PowerShell-Skripts im nächsten Schritt erneut nutzen.

## Schritt 5: Registrieren aller Hostnamenautoritäten für Ihre externen lokalen Exchange HTTP-Endpunkte mit Azure Active Directory

In diesem Schritt müssen Sie das Skript für jeden Endpunkt in Ihrer lokalen Exchange-Organisation ausführen, auf den öffentlich zugegriffen werden kann. Es wird empfohlen, nach Möglichkeit Platzhalter zu verwenden. Nehmen Sie beispielsweise an, dass Exchange von außerhalb unter **https://mail.contoso.com/ews/exchange.asmx** verfügbar ist. In diesem Fall könnte ein einzelnes Platzhalterzeichen verwendet werden: **\*.contoso.com**. Damit sind Endpunkte wie etwa autodiscover.contoso.com und mail.contoso.com abgedeckt. Allerdings ist dadurch nicht die Top-Level-Domain **contoso.com** abgedeckt. Wenn auf Ihre Exchange 2013-Clientzugriffsserver von außerhalb aus mit der Top-Level-Hostnamen-Berechtigung zugegriffen werden kann, so muss diese Hostnamen-Berechtigung ebenfalls als **contoso.com** registriert werden. Bei der Registrierung zusätzlicher externer Hostnamen-Berechtigungen besteht keine Begrenzung.

Wenn Sie sich über die externen Exchange-Endpunkte in Ihrer lokalen Exchange-Organisation nicht sicher sind, können Sie eine Liste der extern konfigurierten Webdienst-Endpunkte beziehen, indem Sie den folgenden Befehl in der Exchange PowerShell Ihrer lokalen Exchange-Organisation ausführen:

    Get-WebServicesVirtualDirectory | FL ExternalUrl


> [!NOTE]
> Für eine erfolgreiche Ausführung des folgenden Skripts ist eine Verbindung der Windows PowerShell für Azure Active Directory mit Ihrem Microsoft Online Azure AD-Mandanten erforderlich, wie unter Schritt 4 im vorherigen Abschnitt erläutert.



1.  Speichern Sie den folgenden Text in einer PowerShell-Skriptdatei, die etwa **RegisterEndpoints.ps1** benannt werden kann. In diesem Beispiel wird ein Platzhalterzeichen verwendet, um alle Endpunkte auf contoso.com zu registrieren. Ersetzen Sie**contoso.com** durch eine Hostname-Stelle für Ihre lokale Exchange-Organisation.
    
        $externalAuthority="*.contoso.com"
         
        $ServiceName = "00000002-0000-0ff1-ce00-000000000000";
         
        $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName;
         
        $spn = [string]::Format("{0}/{1}", $ServiceName, $externalAuthority);
        $p.ServicePrincipalNames.Add($spn);
         
        Set-MsolServicePrincipal -ObjectID $p.ObjectId -ServicePrincipalNames $p.ServicePrincipalNames;

2.  Führen Sie in Windows PowerShell für Azure Active Directory das PowerShell-Skript aus, das Sie im vorherigen Schritt erstellt haben. Beispiel:
    
        .\RegisterEndpoints.ps1

## Schritt 6: Erstellen eines IntraOrganizationConnector aus Ihrer lokalen Organisation für Office 365

Sie müssen eine Zieladresse für Ihre Postfächer definieren, die in Exchange Online gehostet werden. Diese Zieladresse wird automatisch erstellt, wenn Ihr Office 365-Mandant erstellt wird. Wenn beispielsweise die im Office 365-Mandanten gehostete Domäne Ihrer Organisation "contoso.com" lautet, ist Ihre Zieldienstadresse "contoso.mail.onmicrosoft.com".

Führen Sie unter Verwendung der Exchange PowerShell das folgende Cmdlet in Ihrer lokalen Organisation aus:

    New-IntraOrganizationConnector -name ExchangeHybridOnPremisesToOnline -DiscoveryEndpoint https://outlook.office365.com/autodiscover/autodiscover.svc -TargetAddressDomains <your service target address>

## Schritt 7: Erstellen eines IntraOrganizationConnector von Ihrem Office 365-Mandanten aus für Ihre lokale Exchange-Organisation

Sie müssen eine Zieladresse für die Postfächer definieren, die in Ihrer lokalen Organisation gehostet werden. Wenn die primäre SMTP-Adresse Ihrer Organisation "contoso.com" lautet, so ist dies "contoso.com".

Sie müssen außerdem den externen Autodiscover-Endpunkt für Ihre lokale Organisation definieren. Wenn Ihr Unternehmen "contoso.com" ist, so ist dies in der Regel einer der folgenden:

  - https://autodiscover.\<Ihre primäre SMTP-Domäne\>/autodiscover/autodiscover.svc

  - https://\<Ihre primäre SMTP-Domäne\>/autodiscover/autodiscover.svc


> [!NOTE]
> Sie können das <A href="https://technet.microsoft.com/de-de/library/dn551183(v=exchg.150)">Get-IntraOrganizationConfiguration</A>-Cmdlet sowohl in Ihren lokalen als auch den Office 365-Mandanten verwenden, um die vom <A href="https://technet.microsoft.com/de-de/library/dn551178(v=exchg.150)">New-IntraOrganizationConnector</A>-Cmdlet benötigten Endpunktwerte festzulegen.



Führen Sie unter Verwendung der Windows PowerShell das folgende Cmdlet aus:

    $UserCredential = Get-Credential
    
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    
    Import-PSSession $Session
    
    New-IntraOrganizationConnector -name ExchangeHybridOnlineToOnPremises -DiscoveryEndpoint <your on-premises Autodiscover endpoint> -TargetAddressDomains <your on-premises SMTP domain>

## Schritt 8: Konfigurieren eines AvailabilityAddressSpace für alle Exchange-Server vor Version 2013 SP1

Wenn Sie eine Hybridbereitstellung in einer Organisation mit Exchange vor Version 2013 konfigurieren, müssen Sie mindestens einen Server mit Exchange 2013 SP1 oder höher mit den Clientzugriffs- und Postfachserverrollen in Ihrer vorhandenen Exchange-Organisation installieren. Die Exchange 2013-Clientzugriffs- und -Postfachserver fungieren als Front-End-Server und koordinieren die Kommunikation zwischen Ihrer vorhandenen lokalen Exchange-Organisation und der Exchange Online-Organisation. Diese Kommunikation beinhaltet auch den Nachrichtentransport zwischen der lokalen und der Exchange Online-Organisation sowie Messagingfunktionen. Für eine bessere Zuverlässigkeit und höhere Verfügbarkeit der Funktionen der Hybridbereitstellung sollten Sie mehrere Exchange 2013-Server in der lokalen Organisation installieren.

In einer gemischten Bereitstellung mit Exchange 2013/2010 oder Exchange 2013/2007 wird empfohlen, dass alle mit dem Internet verbundenen Front-End-Server für Ihre lokale Organisation Clientzugriffsserver sind, auf denen Exchange 2013 SP1 oder höher ausgeführt wird. Alle Exchange-Webdienste-Anforderungen, die von Office 365 und Exchange Online stammen, müssen eine Verbindung zu einem Exchange 2013-Clientzugriffsserver in Ihrer lokalen Bereitstellung herstellen. Darüber hinaus müssen alle Exchange-Webdienste-Anforderungen für Exchange Online, die von Ihren lokalen Exchange-Organisationen stammen, mittels Proxy über einen Clientzugriffsserver weitergeleitet werden, auf dem Exchange 2013 SP1 oder höher ausgeführt wird. Da diese Exchange 2013-Clientzugriffsserver diese zusätzlichen eingehenden und ausgehenden Exchange-Webdienste-Anforderungen verarbeiten müssen, ist es wichtig, eine ausreichende Anzahl von Exchange 2013-Clientzugriffsservern verfügbar zu haben, um die Verarbeitungslast handhaben und Verbindungsredundanz bereitstellen zu können. Die Anzahl der erforderlichen Clientzugriffsserver hängt von der durchschnittlichen Menge von Exchange-Webdienste-Anforderungen ab und ist je nach Organisation unterschiedlich.

Bevor Sie den folgenden Schritt ausführen, stellen Sie Folgendes sicher:

  - Auf den Front-End-Hybridservern wird Exchange 2013 SP1 oder höher ausgeführt.

  - Sie verfügen über eine eindeutige externe Exchange-Webdienste-URL für die Exchange 2013-Server. Der Office 365-Mandant muss eine Verbindung mit diesen Servern herstellen, damit cloudbasierte Anforderungen für Hybridfunktionen ordnungsgemäß ausgeführt werden.

  - Die Server verfügen sowohl über die Postfach- als auch die Clientzugriffsrolle.

  - Für alle vorhandenen Exchange 2010/2007-Postfach- und -Clientzugriffsserver wurde das neueste kumulative Update oder Service Pack (SP) angewendet.
    

    > [!NOTE]
    > Vorhandene Exchange 2010/2007-Postfachserver können weiterhin Exchange 2010/2007-Clientzugriffsserver als Front-End-Server für Verbindungen mit nicht hybriden Funktionen verwenden. Nur bei Anforderungen für Hybridbereitstellungsfunktionen vom Office 365-Mandanten muss eine Verbindung mit Exchange 2013-Servern hergestellt werden.



Ein *AvailabilityAddressSpace* muss auf Clientzugriffsservern mit Exchange vor Version 2013 konfiguriert sein, der auf den Exchange-Webdienste-Endpunkt Ihrer lokalen Exchange 2013 SP1-Clientzugriffsserver verweist. Dieser Endpunkt ist derselbe Endpunkt, der zuvor in Schritt 5 dargelegt wurde, oder kann durch das Ausführen des folgenden Cmdlets auf Ihrem lokalen Exchange 2013 SP1-Clientzugriffsserver festgelegt werden.

    Get-WebServicesVirtualDirectory | FL AdminDisplayVersion,ExternalUrl


> [!NOTE]
> Wenn virtuelle Verzeichnisinformationen von mehreren Servern zurückgegeben werden, vergewissern Sie sich, dass Sie den für einen Exchange 2013 SP1-Clientzugriffsserver zurückgegebenen Endpunkt verwenden. Dieser enthält im Parameter <EM>AdminDisplayVersion</EM> den Eintrag 15.0 (Build 847.32) oder höher.



Um den *AvailabilityAddressSpace* zu konfigurieren, verwenden Sie Exchange PowerShell und starten Sie das folgende Cmdlet in Ihrer lokalen Organisation:

    Add-AvailabilityAddressSpace -AccessMethod InternalProxy -ProxyUrl <your on-premises External Web Services URL> -ForestName <your Office 365 service target address> -UseServiceAccount $True

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie können die Korrektheit der OAuth-Konfiguration verifizieren, indem Sie das [Test-OAuthConnectivity](https://technet.microsoft.com/de-de/library/jj218623\(v=exchg.150\))-Cmdlet verwenden. Mit diesem Cmdlet kann überprüft werden, ob die lokalen Exchange- und Exchange Online-Endpunkte erfolgreich gegenseitige Anforderungen authentifizieren können.


> [!IMPORTANT]
> Wenn Sie über Remote PowerShell eine Verbindung mit Ihrer Exchange Online-Organisation herstellen, müssen Sie möglicherweise den Parameter <EM>AllowClobber</EM> mit dem Cmdlet <STRONG>Import-PSSession</STRONG> verwenden, um die neuesten Befehle in die lokale PowerShell-Sitzung zu importieren.



Wenn Sie überprüfen möchten, ob Ihre lokale Exchange-Organisation erfolgreich eine Verbindung mit Exchange Online herstellen kann, müssen Sie den folgenden Befehl in der Exchange PowerShell in Ihrer lokalen Organisation ausführen:

    Test-OAuthConnectivity -Service EWS -TargetUri https://outlook.office365.com/ews/exchange.asmx -Mailbox <On-Premises Mailbox> -Verbose | fl

Wenn Sie überprüfen möchten, ob Ihre Exchange Online-Organisation erfolgreich eine Verbindung mit Ihrer lokalen Exchange-Organisation herstellen kann, verwenden Sie [Remote PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\)), um die Verbindung mit Ihrer Exchange Online-Organisation aufzubauen, und führen Sie den folgenden Befehl aus:

    Test-OAuthConnectivity -Service EWS -TargetUri <external hostname authority of your Exchange On-Premises deployment>/metadata/json/1 -Mailbox <Exchange Online Mailbox> -Verbose | fl

Beispiel: Test-OAuthConnectivity -Service EWS -TargetUri https://lync.contoso.com/metadata/json/1 -Mailbox ExchangeOnlineBox1 -Verbose | fl


> [!IMPORTANT]
> Sie können die Fehlermeldung "Der SMTP-Adresse ist kein Postfach zugeordnet." ignorieren. Es ist lediglich von Bedeutung, dass der Parameter <EM>ResultTask</EM> einen Wert über den <STRONG>Erfolg</STRONG> zurückgibt. Der letzte Abschnitt des Testergebnisses sollte beispielsweise wie folgt lauten:<BR><CODE>ResultType: Success</CODE><BR><CODE>Identity: Microsoft.Exchange.Security.OAuth.ValidationResultNodeId</CODE><BR><CODE>IsValid: True</CODE><BR><CODE>ObjectState: New</CODE>




> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


