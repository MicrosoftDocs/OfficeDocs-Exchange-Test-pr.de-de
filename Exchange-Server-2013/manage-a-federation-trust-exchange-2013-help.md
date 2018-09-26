---
title: 'Verwalten einer Verbundvertrauensstellung: Exchange 2013 Help'
TOCTitle: Verwalten einer Verbundvertrauensstellung
ms:assetid: 0439839f-2052-4bc9-9d30-aa6e7d51b733
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673036(v=EXCHG.150)
ms:contentKeyID: 50474959
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten einer Verbundvertrauensstellung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-01_

Eine Verbundvertrauensstellung richtet eine Vertrauensstellung zwischen einer Microsoft Exchange 2013-Organisation und dem Azure Active Directory-Authentifizierungssystem ein und unterstützt eine Verbundfreigabe mit anderen Exchange-Organisationen im Partnerverbund. Die Verbundvertrauensstellung muss nach ihrer Erstellung normalerweise nicht verwaltet oder geändert werden. In bestimmten Situationen müssen Sie jedoch möglicherweise Verbunddomänen hinzufügen oder entfernen bzw. die zur Konfiguration der Organisations-ID (OrgID) für die Verbundvertrauensstellung verwendete Domäne zurücksetzen.


> [!NOTE]
> Beim Ändern einer vorhandenen Verbundvertrauensstellung, insbesondere der primären, zur Definition der OrgID verwendeten freigegebenen Domäne, kann die Verbundfreigabe zwischen Exchange-Organisationen oder für Hybridbereitstellungen mit Office 365-Organisationen unterbrochen werden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf den Partnerverbund finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "*Federation and certificates*-Berechtigungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Für jede neue Verbunddomäne, die zur Verbundvertrauensstellung hinzugefügt wird, muss ein TXT-Eintrag zu Ihrem öffentlichen DNS hinzugefügt werden. Überprüfen Sie die Anforderungen für das Hinzufügen eines TXT-Eintrags mit der Organisation, die Ihre öffentlichen DNS-Einträge hostet.

  - Zur Veranschaulichung in diesem Thema wurde eine vorhandene Verbundvertrauensstellung mit den folgenden Einstellungen konfiguriert:
    
      - Die primäre freigegebene Domäne für die Verbundvertrauensstellung ist **Contoso.com**. (Diese Domäne wird nicht geändert.)
    
      - Die Verbunddomänen **service.contoso.com** und **sales.contoso.com** wurden in die vorhandene Verbundvertrauensstellung aufgenommen.
    
      - **Marketing.contoso.com** ist eine akzeptierte Domäne in der Exchange-Organisation.

  - In diesem Thema werden darüber hinaus weitere Verwaltungsaufgaben für den Partnerverbund behandelt, z. B. das Anzeigen und Verwalten von Zertifikaten, die für die Verbundvertrauensstellung verwendet werden, sowie das Anzeigen von Parameterinformationen zur Verbundvertrauensstellung in der Shell.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Verwalten einer Verbundvertrauensstellung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie auf einem Exchange 2013-Server in Ihrer lokalen Organisation zu **Organisation** \> **Freigabe**.

2.  Klicken Sie im Abschnitt **Verbundvertrauensstellung** auf **Ändern**.

3.  Da die primäre freigegebene Domäne nicht geändert wird, können Sie **Schritt 1** in **Freigabeaktivierte Domänen** überspringen.

4.  Wählen Sie in **Schritt 2** die Domäne **service.contoso.com** aus, und klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um die Domäne aus der Verbundvertrauensstellung zu entfernen.

5.  Klicken Sie in **Schritt 2** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

6.  Wählen Sie in **Akzeptierte Domänen auswählen** aus der Liste der akzeptierten Domänen **marketing.contoso.com** aus, und klicken Sie auf **OK**, um die Domäne zur Verbundvertrauensstellung hinzuzufügen.
    

    > [!IMPORTANT]
    > Für die Domäne <STRONG>marketing.contoso.com</STRONG> wird eine Zeichenfolge des Nachweises für die Verbunddomäne erstellt. Für diese Domäne muss ein separater TXT-Eintrag in Ihrem öffentlichen DNS erstellt werden.



7.  Erstellen Sie unter Verwendung der Zeichenfolge des Nachweises für die Verbunddomäne, der für die Domäne **marketing.contoso.com** erstellt wurde, einen TXT-Eintrag auf Ihrem öffentlichen DNS-Server. In Abhängigkeit vom Aktualisierungszeitplan Ihres öffentlichen DNS-Hosts kann die Replikation von DNS-Änderungen 15 Minuten oder länger dauern.

8.  Nachdem der TXT-Eintrag erstellt und repliziert wurde, klicken Sie auf **Aktualisieren**.

## Verwalten einer Verbundvertrauensstellung mithilfe der Shell

1.  In diesem Beispiel wird die Domäne "service.contoso.com" aus der Verbundvertrauensstellung entfernt.
    
    ```powershell
    Remove-FederatedDomain -DomainName service.contoso.com
    ```

2.  In diesem Beispiel wird die Domäne "marketing.contoso.com" zur Verbundvertrauensstellung hinzugefügt.
    
    ```powershell
    Add-FederatedDomain -DomainName marketing.contoso.com
    ```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-FederatedDomain](https://technet.microsoft.com/de-de/library/dd298128\(v=exchg.150\)) und [Add-FederatedDomain](https://technet.microsoft.com/de-de/library/dd351208\(v=exchg.150\)).

Führen Sie die folgenden Shell-Befehle aus, um weitere Aspekte einer Verbundvertrauensstellung zu verwalten:

1.  **Anzeigen der Verbundorganisations-ID und Verbunddomänen**
    
    In diesem Beispiel werden die Verbundorganisations-ID und die dazugehörigen Informationen (einschließlich Verbunddomänen und Status) für die Exchange-Organisation angezeigt.
    
    ```powershell
    Get-FederatedOrganizationIdentifier
    ```

2.  **Anzeigen von Zertifikaten der Verbundvertrauensstellung**
    
    In diesem Beispiel werden die von der Verbundvertrauensstellung "Azure AD authentication" verwendeten vorherigen, aktuellen und nächsten Zertifikate angezeigt.
    
    ```powershell
        Get-FederationTrust "Azure AD authentication" | Select Org*certificate
    ```
    
3.  **Überprüfen des Verbundzertifikatstatus**
    
    In diesem Beispiel wird der Status von Verbundzertifikaten auf allen Postfach- und Clientzugriffsservern in der Organisation angezeigt.
    
    ```powershell
    Test-FederationTrustCertificate
    ```

4.  **Konfigieren der Verbundvertrauensstellung zum Verwenden eines Zertifikats als das nächste Zertifikat**
    
    In diesem Beispiel wird die Verbundvertrauensstellung "Azure AD authentication" zum Verwenden des Zertifikats mit dem bereitgestellten Fingerabdruck als das nächste Zertifikat konfiguriert. Nachdem das Zertifikat auf allen Exchange-Servern in der Organisation bereitgestellt wurde, können Sie die Verbundvertrauensstellung mithilfe der Option *PublishCertificate* so konfigurieren, dass dieses Zertifikat als das aktuelle Zertifikat verwendet wird.
    
    ```powershell
    Set-FederationTrust "Azure AD authentication" -Thumbprint AC00F35CBA8359953F4126E0984B5CCAFA2F4F17
    ```

5.  **Konfigurieren der Verbundvertrauensstellung zum Verwenden des nächsten Zertifikats als das aktuelle Zertifikat**
    
    In diesem Beispiel wird die Verbundvertrauensstellung "Azure AD authentication" so konfiguriert, dass das nächste Zertifikat als das aktuelle Zertifikat verwendet und für das Azure AD-Authentifizierungssystem veröffentlicht wird.
    
    ```powershell
    Set-FederationTrust "Azure AD authentication" -PublishFederationCertificate
    ```
    

    > [!WARNING]
    > Bevor die Verbundvertrauensstellung so konfiguriert wird, dass das nächste Zertifikat als das aktuelle Verbundzertifikat verwendet wird, stellen Sie sicher, dass das Zertifikat auf allen Exchange-Servern in der Organisation bereitgestellt wurde. Verwenden Sie das Cmdlet <A href="https://technet.microsoft.com/de-de/library/dd335228(v=exchg.150)">Test-FederationTrustCertificate</A>, um den Bereitstellungsstatus des Zertifikats zu überprüfen.



6.  **Aktualisieren der Verbundmetadaten und des Zertifikats vom Azure AD-Authentifizierungssystem**
    
    In diesem Beispiel wird das Verbundzertifikat samt Metadaten des Azure AD-Authentifizierungssystems für die Verbundvertrauensstellung "Azure AD authentication" aktualisiert.
    
    ```powershell
    Set-FederationTrust "Azure AD authentication" -RefreshMetadata
    ```

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-FederatedOrganizationIdentifier](https://technet.microsoft.com/de-de/library/dd298149\(v=exchg.150\))

  - [Get-FederationTrust](https://technet.microsoft.com/de-de/library/dd351262\(v=exchg.150\))

  - [Test-FederationTrustCertificate](https://technet.microsoft.com/de-de/library/dd335228\(v=exchg.150\))

  - [Set-FederationTrust](https://technet.microsoft.com/de-de/library/dd298034\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Der erfolgreiche Abschluss des Assistenten für freigabeaktivierte Domänenist ein erster Hinweis, dass die Verbundvertrauensstellung wie erwartet konfiguriert wurde.

Gehen Sie wie folgt vor, um die erfolgreiche Konfiguration zusätzlich zu überprüfen:

1.  Führen Sie den folgenden Shellbefehl aus, um die Informationen der Verbundvertrauensstellung zu überprüfen.
    
    ```powershell
    Get-FederationTrust | format-list
    ```

2.  Führen Sie den folgenden Shellbefehl aus, um zu überprüfen, ob die Verbundinformationen von Ihrer Organisation abgerufen werden können. Überprüfen Sie z. B., ob im Parameter *DomainNames* die Domänen "sales.contoso.com" und "marketing.contoso.com" zurückgegeben werden.
    
    ```powershell
    Get-FederationInformation -DomainName <your primary sharing domain>
    ```


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.


