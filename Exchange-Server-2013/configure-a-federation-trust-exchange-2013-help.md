---
title: 'Konfigurieren einer Verbundvertrauensstellung: Exchange 2013 Help'
TOCTitle: Konfigurieren einer Verbundvertrauensstellung
ms:assetid: 7c2b539f-faed-4374-8578-9f329ca628db
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657462(v=EXCHG.150)
ms:contentKeyID: 50476007
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren einer Verbundvertrauensstellung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-07-26_

Mit einer Verbundvertrauensstellung wird eine Vertrauensstellung zwischen einer Microsoft Exchange 2013-Organisation und dem Azure Active Directory-Authentifizierungssystem erstellt. Durch Konfigurieren einer Verbundvertrauensstellung können Sie Verbundfreigaben mit anderen Exchange-Verbundorganisationen erstellen, damit Benutzer Frei/Gebucht-Informationen gemeinsam nutzen können. Verbundfreigaben können zwischen zwei Exchange 2013-Verbundorganisationen oder zwischen einer Exchange 2013-Verbundorganisation und Exchange 2010-Verbundorganisationen konfiguriert werden. Sie können die gemeinsame Nutzung auch mit einer Office 365-Organisation einrichten.


> [!NOTE]  
> Das Erstellen einer Verbundvertrauensstellung ist einer von mehreren Schritten, die zum Einrichten von Verbundfreigaben in Ihrer Exchange-Organisation ausgeführt werden müssen. Eine Liste aller Schritte finden Sie unter <A href="configure-federated-sharing-exchange-2013-help.md">Konfigurieren der Verbundfreigabe</A>.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf den Partnerverbund finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).


> [!IMPORTANT]  
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „Verbund- und Zertifikatberechtigungen“ im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Die Domäne, die zum Erstellen einer Verbundvertrauensstellung verwendet wird, muss vom Internet aufgelöst werden können. Dazu muss die Domäne bei einer Domänenregistrierungsstelle registriert sein, und die DNS-Zone (Domain Name System) für die Domäne muss auf einem vom Internet zugänglichen DNS-Server gehostet werden. Wenn die Organisation Internet-E-Mail für die Domäne erhält, sind diese Bedingungen bereits erfüllt.

  - Sie müssen Ihrem öffentlichen DNS einen TXT-Eintrag hinzufügen. Überprüfen Sie die Anforderungen für das Hinzufügen eines TXT-Eintrags mit der Organisation, die Ihre öffentlichen DNS-Einträge hostet.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Die beiden Exchange-Organisationen in einer Verbundfreigabebeziehung müssen dasselbe Azure AD-Authentifizierungssystem für ihre Verbundvertrauensstellungen verwenden. Diese Anforderung gilt beim Konfigurieren der Verbundfreigabe zwischen zwei lokalen Exchange Organisationen oder zwischen einer lokalen Exchange Organisation und einer Exchange Organisation, die von [Office 365](https://go.microsoft.com/fwlink/?linkid=392576) gehostet wird.

  - Wenn Sie eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem für Ihre Exchange 2013-Organisation erstellen, nutzt die Verbundvertrauensstellung die Business-Instanz des Azure AD-Authentifizierungssystems. Andere Exchange-Verbundorganisationen mit früheren Exchange-Versionen und vorhandenen Verbundvertrauensstellungen verwenden möglicherweise entweder die Business- oder die Consumer-Instanz des Azure AD-Authentifizierungssystems.
    
    Die folgenden Exchange-Organisationen verwenden standardmäßig die Business-Instanz des Azure AD-Authentifizierungssystems:
    
      - Exchange 2013-Organisationen durch Verwendung des Assistenten zum Aktivieren von Verbundvertrauensstellungen und durch Verwendung selbstsignierter Zertifikate für eine Verbundvertrauensstellung.
    
      - Organisationen mit Exchange 2010 SP1 oder höher durch Verwendung des Assistenten für neue Verbundvertrauensstellungen und durch Verwendung selbstsignierter Zertifikate für eine Verbundvertrauensstellung.
    
      - Exchange Organisationen, die von Office 365 gehostet werden, wie etwa Exchange Online.
    
    Die folgenden Exchange-Organisationen verwenden standardmäßig die Consumer-Instanz des Azure AD-Authentifizierungssystems:
    
      - Die RTM-Version (Release to Manufacturing) von Exchange 2010-Organisationen, die von Drittanbieterzertifizierungsstellen ausgestellte Zertifikate verwenden.
    
    Es wird empfohlen, für sämtliche Exchange-Organisationen die Business-Instanz des Azure AD-Authentifizierungssystems für Verbundvertrauensstellungen zu verwenden. Vor der Konfiguration der Verbundfreigabe zwischen den zwei Exchange-Organisationen müssen Sie überprüfen, welche Azure AD-Authentifizierungssysteminstanz die Exchange-Organisationen jeweils für vorhandene Verbundvertrauensstellungen verwenden. Zum Ermitteln, welche Azure AD-Authentifizierungssysteminstanz eine Exchange-Organisation für eine vorhandene Verbundvertrauensstellung verwendet, führen Sie den folgenden Shellbefehl aus.
    
    ```powershell
    Get-FederationInformation -DomainName <hosted Exchange domain namespace>
    ```
    
    Die Business-Instanz gibt für den Parameter *TokenIssuerURIs* den Wert `<uri:federation:MicrosoftOnline>` zurück.
    
    Die Consumer-Instanz gibt für den Parameter *TokenIssuerURIs* den Wert `<uri:WindowsLiveID>` zurück.
    
    Zum Konfigurieren der Verbundfreigabe mit einer Exchange-Organisation, die über eine vorhandene Verbundvertrauensstellung unter Verwendung der Business-Instanz des Azure AD-Authentifizierungssystems verfügt, führen Sie die in diesem Thema beschriebenen Schritte aus. Sie müssen nur diese Schritte ausführen, um Verbundvertrauensstellungen zu erstellen, die zur Aktivierung von Verbundfreigaben zwischen zwei Exchange 2013-Organisationen oder zwischen einer Exchange 2013-Organisation und einer Exchange 2010-Organisation verwendet werden können, die bereits die Business-Instanz des Azure AD-Authentifizierungssystems verwenden.
    
    Zum Konfigurieren einer Verbundfreigabe zwischen Ihrer Exchange 2013-Organisation und einer Exchange-Organisation, die bereits über eine Verbundvertrauensstellung unter Verwendung der Consumer-Instanz des Azure AD-Authentifizierungssystems verfügt, muss die Organisation, die die Consumer-Instanz verwendet, Exchange 2010 SP2 oder höher installieren oder ein Upgrade auf Exchange 2013 durchführen. Wenn Sie Exchange 2010 SP2 oder höher installieren möchten, verwenden Sie den Assistenten für neue Verbundvertrauensstellungen, um die vorhandenen Verbunddomänen und Verbundvertrauensstellungen zu entfernen und neu zu erstellen. Bei der Neuerstellung der Verbundvertrauensstellungen wird die Business-Instanz Azure AD-Authentifizierungssystems verwendet.

## Erstellen und Konfigurieren einer Verbundvertrauensstellung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie auf einem Exchange 2013-Server in Ihrer lokalen Organisation zu **Organisation** \> **Freigabe**.

2.  Klicken Sie auf **Aktivieren**, um den Assistenten zum Aktivieren von Verbundvertrauensstellungen zu starten.

3.  Nach Fertigstellung des Assistenten klicken Sie auf **Schließen**.

4.  Klicken Sie auf der Registerkarte **Freigabe** im Abschnitt **Verbundvertrauensstellung** auf **Ändern**.

5.  Klicken Sie in **Freigabeaktivierte Domänen** neben **Schritt 1** auf **Durchsuchen**.

6.  Wählen Sie in **Akzeptierte Domänen auswählen** die primäre freigegebene Domäne aus der Liste, und klicken Sie auf **OK**.
    

    > [!NOTE]  
    > Die ausgewählte Domäne wird zur Konfiguration der Organisations-ID für die Verbundvertrauensstellung verwendet. Weitere Informationen zur Organisations-ID finden Sie unter <A href="federation-exchange-2013-help.md">Verbund</A>.



7.  Notieren Sie sich den Nachweis für die Verbunddomäne, der für die primäre freigegebene Domäne generiert wird. Sie benötigen diese Zeichenfolge, um einen TXT-Eintrag auf Ihrem öffentlichen DNS-Server zu erstellen.
    

    > [!IMPORTANT]  
    > Die Zeichenfolge des Nachweises für die Verbunddomäne besteht aus alphanumerischen Zeichen. Zur Vermeidung von Eingabefehlern empfiehlt es sich, die Zeichenfolge aus der Exchange-Verwaltungskonsole zu kopieren und in einen Text-Editor wie Editor einzufügen. Zum Erstellen des TXT-Eintrags können Sie die Zeichenfolge aus dem Text-Editor in die Zwischenablage und dann in das Feld <STRONG>Text</STRONG> einfügen. Wenn der TXT-Eintrag mit einer falschen Zeichenfolge des Nachweises für die Verbunddomäne erstellt wird, kann das Azure AD-Authentifizierungssystem den Nachweis der Domäneneigentümerschaft nicht überprüfen, und Sie können sie nicht der Verbundorganisations-ID hinzufügen.



8.  Klicken Sie in **Schritt 2** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um der Verbundvertrauensstellung weitere Domänen hinzuzufügen, damit Benutzern in Ihrer Organisation, die Verbundfreigabefunktionen benötigen, die entsprechenden E-Mail-Adressen zur Verfügung stehen. Wenn Benutzer z. B. eine Subdomäne wie „sales.contoso.com“ in ihren E-Mail-Adressen verwenden, sollten Sie die Domäne "sales.contoso.com" der Verbundvertrauensstellung hinzufügen.
    

    > [!NOTE]
    > Für jede ausgewählte zusätzliche Domäne wird eine Zeichenfolge des Nachweises für die Verbunddomäne erstellt. Für jede zusätzliche Domäne muss ein separater TXT-Eintrag in Ihrem öffentlichen DNS erstellt werden.



9.  Verwenden Sie die für die jeweiligen Domänen erstellte Zeichenfolgen des Nachweises für die Verbunddomäne, um die entsprechenden TXT-Einträge auf Ihrem öffentlichen DNS-Server zu erstellen. In Abhängigkeit vom Aktualisierungszeitplan Ihres öffentlichen DNS-Hosts kann die Replikation von DNS-Änderungen 15 Minuten oder länger dauern.

10. Nachdem die TXT-Einträge erstellt und repliziert wurden, klicken Sie auf **Aktualisieren**.

## Erstellen und Konfigurieren einer Verbundvertrauensstellung mithilfe der Shell

1.  Führen Sie diesen Befehl aus, um eine Schlüssel-ID des Antragstellers für das Zertifikat für die Verbundvertrauensstellung zu erstellen:
    
    ```powershell
    $ski = [System.Guid]::NewGuid().ToString("N")
    ```

2.  Verwenden Sie diese Syntax, um ein selbstsigniertes Zertifikat für die Verbundvertrauensstellung zu erstellen:
    
    ```powershell
    New-ExchangeCertificate -FriendlyName "<Descriptive Name>" -DomainName <domain> -Services Federation -KeySize 2048 -PrivateKeyExportable $true -SubjectKeyIdentifier $ski
    ```
    
    In diesem Beispiel wird ein selbstsigniertes Zertifikat für die Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem erstellt. Das Zertifikat verwendet den Anzeigenamen „Exchange-Verbundfreigabe“, und der Domänenwert wird von der **USERDNSDOMAIN**-Umgebungsvariablen abgerufen.
    
    ```powershell
    New-ExchangeCertificate -FriendlyName "Exchange Federated Sharing" -DomainName $env:USERDNSDOMAIN -Services Federation -KeySize 2048 -PrivateKeyExportable $true -SubjectKeyIdentifier $ski
    ```

3.  Verwenden Sie die folgende Syntax, um die Verbundvertrauensstellung zu erstellen und das selbstsignierte Zertifikat, das Sie im vorherigen Schritt für die Exchange-Server in Ihrer Organisation erstellt haben, automatisch bereitzustellen:
    
    ```powershell
    Get-ExchangeCertificate | ?{$_.FriendlyName -eq "<FriendlyName>"} | New-FederationTrust -Name "<Descriptive Name>"
    ```
    
    In diesem Beispiel werden die Verbundvertrauensstellung „Azure AD-Authentifizierung“ erstellt und das selbstsignierte Zertifikat mit dem Namen „Exchange-Verbundfreigabe“ bereitgestellt.
    
    ```powershell
    Get-ExchangeCertificate | ?{$_.FriendlyName -eq "Exchange Federated Sharing"} | New-FederationTrust -Name "Azure AD Authentication"
    ```

4.  Verwenden Sie diese Syntax, um den Nachweis des Domänenbesitzes anhand eines TXT-Eintrags zurückzugeben, der für jede Domäne erforderlich ist, die Sie für die Verbundvertrauensstellung konfigurieren.
    
    ```powershell
    Get-FederatedDomainProof -DomainName <domain>
    ```
    
    In diesem Beispiel wird der Nachweis des Domänenbesitzes anhand eines TXT-Eintrags zurückgegeben, der für die primäre freigegebene Domäne „contoso.com“ erforderlich ist.
    
    ```powershell
    Get-FederatedDomainProof -DomainName contoso.com
    ```
    
    **Hinweise:** 
    
      - Für jede für die Verbundvertrauensstellung konfigurierte Domäne oder Unterdomäne ist ein Nachweis des Domänenbesitzes anhand eines TXT-Eintrags erforderlich. Daher müssen Sie diesen Befehl möglicherweise mehrmals mit verschiedenen *DomainName*-Werten ausführen.
    
      - Es wird empfohlen, die Zeichenfolge für den Domänennachweis mit der rechten Maustaste in der Shell zu kopieren, **Markieren** und dann den **Nachweis**-Wert auszuwählen und anschließend die EINGABETASTE zu drücken, damit Sie sie beim Erstellen des TXT-Eintrags verwenden können. Wenn Sie den TXT-Eintrag mit einer falschen Zeichenfolge des Nachweises für die Verbunddomäne erstellen, kann das Azure AD-Authentifizierungssystem den Domänenbesitz nicht überprüfen, und Sie können sie nicht der Verbundorganisations-ID hinzufügen.

5.  Erstellen Sie anhand der Informationen aus dem vorherigen Schritt die TXT-Einträge auf Ihrem öffentlichen DNS-Server in jeder Domäne, die der Verbundvertrauensstellung hinzugefügt wird. In Abhängigkeit vom Aktualisierungszeitplan Ihres öffentlichen DNS-Hosts kann die Replikation von DNS-Änderungen 15 Minuten oder länger dauern. Fahren Sie fort, nachdem Sie sichergestellt haben, dass die neuen TXT-Einträge verfügbar sind.

6.  Führen Sie diesen Befehl zum Abrufen der Metadaten und des Zertifikats von Azure AD aus:
    
    ```powershell
    Set-FederationTrust -RefreshMetadata -Identity "Azure AD authentication"
    ```

7.  Verwenden Sie diese Syntax, um die primäre freigegebene Domäne für die Verbundvertrauensstellung zu konfigurieren, die Sie in Schritt 3 erstellt haben. Die Domäne, die Sie angeben, wird zum Konfigurieren der Organisations-ID (OrgID) für die Verbundvertrauensstellung verwendet. Weitere Informationen zu der Organisations-ID finden Sie unter [Federated organization identifier](federation-exchange-2013-help.md).
    
    ```powershell
    Set-FederatedOrganizationIdentifier -DelegationFederationTrust "<Federation Trust Name>" -AccountNamespace <Accepted Domain> -Enabled $true
    ```
    
    In diesem Beispiel wird die akzeptierte Domäne „contoso.com“ als die primäre freigegebene Domäne für die Verbundvertrauensstellung mit dem Namen „Azure Active Directory-Authentifizierung“ konfiguriert.
    
    ```powershell
    Set-FederatedOrganizationIdentifier -DelegationFederationTrust "Azure AD authentication" -AccountNamespace contoso.com -Enabled $true
    ```

8.  Verwenden Sie zum Hinzufügen anderer Domänen die folgende Syntax:
    
    ```powershell
    Add-FederatedDomain -DomainName <AdditionalDomain>
    ```
    
    In diesem Beispiel wird die Unterdomäne „sales.contoso.com“ der Verbundvertrauensstellung hinzugefügt, da Benutzer mit E-Mail-Adressen in der Domäne „sales.contoso.com“ Verbundfreigabefunktionen benötigen.
    
    ```powershell
    Add-FederatedDomain -DomainName sales.contoso.com
    ```
    
    Denken Sie daran, dass für jede der Verbundvertrauensstellung hinzugefügte Domäne oder Unterdomäne ein Nachweis des Domänenbesitzes anhand eines TXT-Eintrags erforderlich ist.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ExchangeCertificate](https://technet.microsoft.com/de-de/library/aa998327\(v=exchg.150\)), [New-FederationTrust](https://technet.microsoft.com/de-de/library/dd351047\(v=exchg.150\)), [Get-FederatedDomainProof](https://technet.microsoft.com/de-de/library/ff717833\(v=exchg.150\)), [Set-FederationTrust](https://technet.microsoft.com/de-de/library/dd298034\(v=exchg.150\)), [Set-FederatedOrganizationIdentifier](https://technet.microsoft.com/de-de/library/dd351037\(v=exchg.150\)) und [Add-FederatedDomain](https://technet.microsoft.com/de-de/library/dd351208\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Der erfolgreiche Abschluss der Assistenten zum Aktivieren von Verbundvertrauensstellungen und für freigabeaktivierte Domänen ist ein erster Hinweis darauf, dass die Verbundvertrauensstellung erwartungsgemäß konfiguriert wurde.

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Verbundvertrauensstellung erfolgreich erstellt und konfiguriert wurde:

1.  Führen Sie den folgenden Shellbefehl aus, um die Informationen der Verbundvertrauensstellung zu überprüfen.
    
    ```powershell
    Get-FederationTrust | Format-List
    ```

2.  Ersetzen Sie *\<PrimarySharedDomain\>* durch die primäre freigegebene Domäne, und führen Sie den folgenden Shellbefehl aus, um zu überprüfen, ob die Verbundinformationen von Ihrer Organisation abgerufen werden können.
    
    ```powershell
    Get-FederationInformation -DomainName <PrimarySharedDomain>
    ```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-FederationTrust](https://technet.microsoft.com/de-de/library/dd351262\(v=exchg.150\)) und [Get-FederationInformation](https://technet.microsoft.com/de-de/library/dd351221\(v=exchg.150\)).


> [!TIP]  
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


