---
title: 'Verbund: Exchange 2013 Help'
TOCTitle: Verbund
ms:assetid: 0046e2eb-6940-4941-bd5b-cbe6bffa3b94
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335047(v=EXCHG.150)
ms:contentKeyID: 50474927
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verbund

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Information-Worker müssen häufig mit externen Empfängern, Lieferanten, Partnern und Kunden zusammenarbeiten und ihre Frei/Gebucht-Informationen (die sogenannte "Kalenderverfügbarkeit") freigeben. Die Verbundfunktion von Microsoft Exchange Server 2013 unterstützt die Zusammenarbeit in diesem Bereich. *Verbundfunktion* bezieht sich auf die zugrunde liegende Vertrauensstellungsinfrastruktur, die die *Verbundfreigabe* unterstützt, eine einfache Methode für Benutzer, die Kalenderinformationen für Empfänger in anderen externen Verbundorganisationen freigeben möchten. Weitere Informationen zu Verbundfreigaben finden Sie unter [Freigabe](sharing-exchange-2013-help.md).


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



**Inhalt**

Wichtige Terminologie

Azure AD-Authentifizierungssystem

Verbundvertrauensstellung

Verbundorganisations-ID

Beispiel für einen Verbund

Zertifikatanforderungen für den Verbund

Wechseln zu einem neuen Zertifikat

Überlegungen zur Firewall bei Verbund

## Wichtige Terminologie

Die folgende Tabelle zeigt die Hauptkomponenten in Zusammenhang mit der Partnerverbundfunktion in Exchange 2013.

  - **Anwendungs-ID (AppID)**  
    Eine eindeutige Nummer, die vom Azure Active Directory-Authentifizierungssystem generiert wird, um Exchange-Organisationen zu identifizieren. Die AppID wird automatisch generiert, wenn Sie eine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem erstellen.

<!-- end list -->

  - **Delegierungstoken**  
    Ein SAML-Token (Security Assertion Markup Language), das vom Azure Active Directory-Authentifizierungssystem ausgegeben wird und Benutzern aus einer Verbundorganisation ermöglicht, von einer anderen Verbundorganisation als vertrauenswürdig angesehen zu werden. Ein Delegierungstoken enthält die E-Mail-Adresse des Benutzers, eine nicht änderbare ID sowie Informationen, die zu dem Angebot gehören, für das das Token zur Aktion ausgegeben wurde.

<!-- end list -->

  - **Externe Verbundorganisation**  
    Eine externe Exchange-Organisation, die eine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem eingerichtet hat.

<!-- end list -->

  - **Verbundfreigabe**  
    Eine Gruppe von Exchange-Funktionen, die eine Verbundvertrauensstellung mit demAzure Active Directory-Authentifizierungssystem nutzen, um über Exchange-Organisationen hinweg zu arbeiten (einschließlich standortübergreifender Exchange-Bereitstellungen). Diese Funktionen werden zusammen verwendet, um im Namen von Benutzern über mehrere Exchange-Organisationen hinweg authentifizierte Anforderungen zwischen Servern zu stellen.

<!-- end list -->

  - **Verbunddomäne**  
    Eine akzeptierte autoritative Domäne, die der Organisations-ID (OrgID) einer Exchange-Organisation hinzugefügt wird.

<!-- end list -->

  - **Verschlüsselungszeichenfolge für Domänennachweis**  
    Eine kryptografisch sichere Zeichenfolge, mit der eine Exchange-Organisation den Nachweis erbringt, dass die Organisation Eigentümer der mit dem Azure Active Directory-Authentifizierungssystem verwendeten Domäne ist. Diese Zeichenfolge wird bei Verwendung des Assistenten zum Aktivieren von Verbundvertrauensstellungenautomatisch generiert oder kann mithilfe des Cmdlets **Get-FederatedDomainProof** generiert werden.

<!-- end list -->

  - **Verbundfreigaberichtlinie**  
    Eine Richtlinie auf Organisationsebene, die eine von einem Benutzer eingerichtete gemeinsame Nutzung von Kalenderinformationen zwischen Personen ermöglicht und steuert.

<!-- end list -->

  - **Partnerverbund**  
    Eine auf einer Vertrauensstellung basierende Vereinbarung zwischen zwei Exchange-Organisationen, um ein gemeinsames Ziel zu erreichen. Mit dem Partnerverbund möchten beide Organisationen, dass die Authentifizierungserklärungen einer Organisation von der jeweils anderen anerkannt werden.

<!-- end list -->

  - **Verbundvertrauensstellung**  
    Eine Beziehung mit dem Azure Active Directory-Authentifizierungssystem, die die folgenden Komponenten für Ihre Exchange-Organisation definiert:
    
      - Kontonamespace
    
      - Anwendungs-ID (AppID)
    
      - Organisations-ID (OrgID)
    
      - Verbunddomänen
    
    Zum Konfigurieren einer Verbundfreigabe mit anderen Exchange-Verbundorganisationen muss eine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem eingerichtet sein.

<!-- end list -->

  - **Verbundfreie Organisation**  
    Eine Organisation, die keine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem eingerichtet hat.

<!-- end list -->

  - **Organisations-ID (OrgID)**  
    Definiert, welche der autoritativen akzeptierten Domänen, die in einer Organisation konfiguriert sind, für den Partnerverbund aktiviert sind. Nur Empfänger, die über E-Mail-Adressen mit Verbunddomänen verfügen, die in der OrgID konfiguriert sind, werden vom Azure Active Directory-Authentifizierungssystem erkannt und können die Verbundfreigabefunktionen nutzen. Diese Organisations-ID ist eine Kombination aus einer vordefinierten Zeichenfolge und der ersten akzeptierten Domäne, die im Assistenten zum Aktivieren von Verbundvertrauensstellungen für den Verbund ausgewählt wurde. Wenn Sie beispielsweise die Verbunddomäne **contoso.com** als primäre SMTP-Domäne Ihrer Organisation angeben, wird der Kontonamespace FYDIBOHF25SPDLT.contoso.com automatisch als Organisations-ID für die Verbundvertrauensstellung erstellt.

<!-- end list -->

  - **Organisationsbeziehung**  
    Eine Eins-zu-eins-Beziehung zwischen zwei Exchange-Verbundorganisationen, die es Empfängern ermöglicht, Frei/Gebucht-Informationen (Kalenderverfügbarkeit) gemeinsam zu nutzen. Eine Organisationsbeziehung erfordert eine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem und macht die Nutzung von Active Directory-Gesamtstruktur- oder Domänenvertrauensstellungen zwischen Exchange-Organisationen überflüssig.

<!-- end list -->

  - **Azure Active Directory Authentifizierungssystem**  
    Ein kostenloser, cloudbasierter Identitätsdienst, der als Vertrauensbroker zwischen Microsoft Exchange-Verbundorganisationen fungiert. Der Dienst ist für die Ausgabe von Delegierungstoken an Exchange-Empfänger verantwortlich, wenn diese Informationen von Empfängern anfordern, die zu anderen Exchange-Verbundorganisationen gehören. Weitere Informationen finden Sie unter [Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=392500).

## Azure AD-Authentifizierungssystem

Das Azure Active Directory-Authentifizierungssystem, ein kostenloser cloudbasierter Dienst von Microsoft, fungiert als Vertrauensbroker zwischen der lokalen Exchange 2013-Organisation und anderen Exchange 2010- und Exchange 2013-Verbundorganisationen. Wenn Sie in Ihrer Exchange-Organisation die Verbundfunktion konfigurieren möchten, müssen Sie einmalig eine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem einrichten, damit dieses System als Verbundpartner Ihrer Organisation definiert wird. Nach Einrichtung dieser Vertrauensstellung stellt das Azure AD-Authentifizierungssystem für die über Active Directory authentifizierten Benutzer (die sogenannten *Identitätsanbieter*) SAML-Delegierungstoken (Security Assertion Markup Language) aus. Anhand dieser Delegierungstoken werden Benutzer einer Exchange-Verbundorganisation von einer anderen Exchange-Verbundorganisation als vertrauenswürdig eingestuft. Durch die Funktion des Azure AD-Authentifizierungssystem als Vertrauensbroker brauchen Organisationen nicht mehr mehrere einzelne Vertrauensstellungen zu anderen Organisationen zu erstellen, und die Benutzer können über eine einmalige Anmeldung auf externe Ressourcen zugreifen. Weitere Informationen finden Sie unter [Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=392500).

Wichtige Terminologie

## Verbundvertrauensstellung

Sollen die Verbundfreigabefunktionen von Exchange 2013 genutzt werden, müssen Sie zwischen Ihrer Exchange 2013-Organisation und dem Azure AD-Authentifizierungssystem eine Verbundvertrauensstellung einrichten. Bei der Einrichtung einer Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem wird das digitale Sicherheitszertifikat Ihrer Organisation mit dem Azure AD-Authentifizierungssystem ausgetauscht. Zudem werden das Zertifikat des Azure AD-Authentifizierungssystems und Verbundmetadaten abgerufen. Eine Verbundvertrauensstellung kann mithilfe des Assistenten zum Aktivieren von Verbundvertrauensstellungen in der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets **New-FederationTrust** in der Exchange-Verwaltungsshell eingerichtet werden. Der Assistent zum **Aktivieren von Verbundvertrauensstellungen**erstellt automatisch ein selbstsigniertes Zertifikat, das zum Signieren und Verschlüsseln von Delegierungstoken aus dem Azure AD-Authentifizierungssystem verwendet wird, anhand derer externe Verbundorganisationen die Benutzer als vertrauenswürdig einstufen können. Ausführliche Informationen zu Zertifikatanforderungen finden Sie unter Zertifikatanforderungen für den Verbund weiter unten in diesem Thema.

Beim Erstellen einer Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem wird für Ihre Exchange-Organisation automatisch eine *Anwendungs-ID* (AppID) generiert und in der Ausgabe des Cmdlets **Get-FederationTrust** bereitgestellt. Anhand der Anwendungs-ID kann das Azure AD-Authentifizierungssystem Ihre Exchange-Organisation eindeutig identifizieren. Sie wird auch von der Exchange-Organisation als Nachweis verwendet, dass Ihre Organisation Eigentümer der Domäne ist, die mit dem Azure AD-Authentifizierungssystem verwendet wird. Dazu wird in der öffentlichen DNS-Zone (Domain Name System) für jede Verbunddomäne ein TXT-Eintrag erstellt.

Wichtige Terminologie

## Verbundorganisations-ID

Anhand der *Verbundorganisations-ID* (OrgID) wird definiert, welche der autoritativen akzeptierten Domänen, die in Ihrer Organisation konfiguriert sind, für die Verbundfunktion aktiviert sind. Nur Empfänger, die über E-Mail-Adressen mit akzeptierten Domänen verfügen, die in der OrgID konfiguriert sind, werden vom Azure AD-Authentifizierungssystem erkannt und können die Verbundfreigabefunktionen nutzen. Beim Erstellen einer neuen Verbundvertrauensstellung wird mit dem Azure AD-Authentifizierungssystem automatisch eine Verbundorganisations-ID (OrgID) erstellt. Diese Verbundorganisations-ID ist eine Kombination aus einer vordefinierten Zeichenfolge und der akzeptierten Domäne, die im Assistenten als primäre freigegebene Domäne ausgewählt wurde. Wenn Sie im Assistenten zum Bearbeiten von freigabeaktivierten Domänen beispielsweise die Verbunddomäne **contoso.com** als primäre freigegebene Domäne in Ihrer Organisation angeben, wird der Kontonamespace **FYDIBOHF25SPDLT.contoso.com** automatisch als Organisations-ID für die Verbundvertrauensstellung für Ihre Exchange-Organisation erstellt.

Wenngleich dies typischerweise die primäre SMTP-Domäne für die Exchange-Organisation ist, muss es sich nicht um eine akzeptierte Domäne in Ihrer Exchange-Organisation handeln. Außerdem ist kein Texteintrag (TXT-Eintrag) in DNS (Domain Name System) erforderlich, um den Besitz nachzuweisen. Die einzige Voraussetzung ist, dass die für den Verbund ausgewählten akzeptierten Domänen höchstens 32 Zeichen enthalten. Diese Unterdomäne dient ausschließlich dem Zweck, als Verbundnamespace für das Azure AD-Authentifizierungssystem zu fungieren und für Empfänger, die SAML-Delegierungstoken (Security Assertion Markup Language) anfordern, eindeutige IDs bereitzustellen. Weitere Informationen zu SAML-Token finden Sie unter [SAML-Token und SAML-Ansprüche](https://go.microsoft.com/fwlink/?linkid=198561)

Sie können akzeptierte Domänen jederzeit zur Vertrauensstellung hinzufügen oder aus dieser entfernen. Wenn alle Verbundfreigabefunktionen in Ihrer Organisation aktiviert bzw. deaktiviert werden sollen, müssen Sie lediglich die Organisations-ID für die Verbundvertrauensstellung aktivieren bzw. deaktivieren.


> [!IMPORTANT]
> Eine Änderung der Verbundorganisations-ID (OrgID), der akzeptierten Domänen oder der Anwendungs-ID (AppID) für die Verbundvertrauensstellung wirkt sich auf alle Verbundfreigabefunktionen in Ihrer Organisation aus. Und damit auch auf alle externen Exchange-Verbundorganisationen, einschließlich Exchange Online- und Hybridbereitstellungskonfigurationen. Es ist empfehlenswert, alle externen Verbundpartner über Änderungen an diesen Konfigurationseinstellungen für die Verbundvertrauensstellung zu informieren.



Wichtige Terminologie

## Beispiel für einen Verbund

Zwei Exchange-Organisationen, Contoso, Ltd. und Fabrikam, Inc., möchten es ihren Benutzern ermöglichen, Frei/Gebucht-Kalenderinformationen miteinander auszutauschen. Jede Organisation erstellt eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem und konfiguriert ihren Kontonamespace so, dass er die Domäne enthält, die für die E-Mail-Adressen der Benutzer verwendet wird.

Die Mitarbeiter von Contoso verwenden eine der folgenden E-Mail-Adressendomänen: contoso.com, contoso.co.uk oder contoso.ca. Die Mitarbeiter von Fabrikam verwenden eine der folgenden E-Mail-Adressendomänen: fabrikam.com, fabrikam.org oder fabrikam.net. Beide Organisationen stellen sicher, dass alle akzeptierten E-Mail-Domänen im Kontonamespace für die Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem enthalten sind. Statt einer komplexen Active Directory-Grundstruktur oder Domänenvertrauensstellung zwischen den Organisationen konfigurieren beide Organisationen eine Organisationsbeziehung zueinander, um die Freigabe von Frei/Gebucht-Kalenderinformationen zu ermöglichen.

Die folgende Abbildung zeigt die Verbundkonfiguration zwischen Contoso, Ltd. und Fabrikam, Inc.

**Beispiel für eine Verbundfreigabe**

![Verbundvertrauensstellungen und Verbundfreigabe](images/Dd335047.310f0698-b67d-4b0e-91e4-231c6e9db952(EXCHG.150).gif "Verbundvertrauensstellungen und Verbundfreigabe")

## Zertifikatanforderungen für den Verbund

Zum Einrichten einer Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem muss entweder ein selbstsigniertes Zertifikat oder ein von einer Zertifizierungsstelle signiertes X.509-Zertifikat erstellt und auf dem Exchange 2013-Server installiert werden, der zum Erstellen der Vertrauensstellung verwendet wird. Es wird dringend empfohlen, ein selbstsigniertes Zertifikat zu verwenden, das automatisch vomAssistenten zum Aktivieren von Verbundvertrauensstellungen in der Exchange-Verwaltungskonsole erstellt und installiert wird. Dieses Zertifikat wird nur zum Signieren und Verschlüsseln von Delegierungstoken verwendet, die für die Verbundfreigabe verwendet werden. Für die Verbundvertrauensstellung wird nur ein Zertifikat benötigt. Exchange 2013 verteilt das Zertifikat automatisch an die anderen Exchange 2013-Server in der Organisation.

Soll ein von einer externen Zertifizierungsstelle signiertes X.509-Zertifikat verwendet werden, muss dieses die folgenden Anforderungen erfüllen:

  - **Vertrauenswürdige Zertifizierungsstelle**   Das X.509-SSL-Zertifikat (Secure Sockets Layer) sollte nach Möglichkeit von einer Zertifizierungsstelle ausgestellt werden, die von Windows Live als vertrauenswürdig eingestuft wird. Sie können jedoch auch Zertifikate von Zertifizierungsstellen verwenden, die derzeit noch nicht von Microsoft zertifiziert sind. Eine aktuelle Liste der vertrauenswürdigen Zertifizierungsstellen finden Sie unter [Vertrauenswürdige Stammzertifizierungsstellen für Verbundvertrauensstellungen](trusted-root-certification-authorities-for-federation-trusts-exchange-2013-help.md).

  - **Schlüssel-ID des Antragstellers**   Das Zertifikat muss über ein Feld mit der Schlüssel-ID des Antragstellers verfügen. Die meisten, von kommerziellen Zertifizierungsstellen ausgestellten X.509-Zertifikate enthalten diese ID.

  - **CryptoAPI-Kryptografiedienstanbieter (Cryptographic Service Provider, CSP)**   Das Zertifikat muss einen CryptoAPI-CSP verwenden. Zertifikate von CNG-Anbietern: (Cryptography API: Next Generation) werden für die Verbundfunktion nicht unterstützt. Beim Erstellen einer Zertifikatanforderung mit Exchange wird ein CryptoAPI-Anbieter verwendet. Weitere Informationen finden Sie unter [Cryptography API: Next Generation](https://go.microsoft.com/fwlink/?linkid=187890).

  - **RSA-Signaturalgorithmus**   Das Zertifikat muss RSA als Signaturalgorithmus verwenden.

  - **Exportierbarer privater Schlüssel**   Der zum Generieren des Zertifikats verwendete private Schlüssel muss exportiert werden können. Beim Erstellen der Zertifikatanforderung mit dem Assistenten für neue Exchange-Zertifikatein der Exchange-Verwaltungskonsole oder mit dem Cmdlet [New-ExchangeCertificate](https://technet.microsoft.com/de-de/library/aa998327\(v=exchg.150\)) in der Shell können Sie angeben, dass der private Schlüssel exportierbar sein muss.

  - **Aktuelles Zertifikat**   Das Zertifikat muss aktuell sein. Eine Verbundvertrauensstellung kann nicht mit einem abgelaufenen oder gesperrten Zertifikat erstellt werden.

  - **Erweiterte Schlüsselverwendung (Enhanced Key Usage, EKU)**   Das Zertifikat muss den EKU-Typ **Clientauthentifizierung (1.3.6.1.5.5.7.3.2)** enthalten. Dieser Verwendungstyp dient auf einem Remotecomputer zum Nachweis Ihrer Identität. Wenn Sie die Zertifikatanforderung über die Exchange-Verwaltungskonsole oder die Verwaltungsshell generieren, ist dieser Verwendungstyp standardmäßig enthalten.


> [!NOTE]
> Da das Zertifikat nicht für die Authentifizierung verwendet wird, bestehen dafür auch keine Anforderungen in Bezug auf einen Antragstellernamen oder einen alternativen Antragstellernamen. Sie können für das Zertifikat den Hostnamen, den Domänennamen oder einen beliebigen anderen Namen als Antragstellernamen verwenden.



Wichtige Terminologie

## Wechseln zu einem neuen Zertifikat

Das zum Erstellen der Verbundvertrauensstellung verwendete Zertifikat wird als aktuelles Zertifikat festgelegt. Sie müssen für die Verbundvertrauensstellung jedoch u. U. von Zeit zu Zeit ein neues Zertifikat installieren und verwenden. Sie müssen beispielsweise ein neues Zertifikat verwenden, wenn die Gültigkeitsdauer des aktuellen Zertifikats abläuft oder neue Geschäfts- oder Sicherheitsanforderungen zu erfüllen sind. Um einen nahtlosen Übergang zu einem neuen Zertifikat zu gewährleisten, müssen Sie das neue Zertifikat auf Ihrem Exchange 2013-Server speichern und die Verbundvertrauensstellung konfigurieren, um es als neues Zertifikat auszuweisen. Exchange 2013 verteilt das neue Zertifikat automatisch an die anderen Exchange 2013-Server in der Organisation. Je nach Active Directory-Topologie nimmt die Verteilung des Zertifikats einige Zeit in Anspruch. Sie können den Zertifikatstatus mit dem Cmdlet [Test-FederationTrustCertificate](https://technet.microsoft.com/de-de/library/dd335228\(v=exchg.150\)) in der Shell überprüfen.

Nachdem Sie den Verteilstatus des Zertifikats überprüft haben, können Sie die Vertrauensstellung für die Verwendung des neuen Zertifikats konfigurieren. Nach dem Austausch der Zertifikate wird das aktuelle Zertifikat als vorheriges Zertifikat und das neue Zertifikat als aktuelles Zertifikat ausgewiesen. Das neue Zertifikat wird auf dem Azure AD-Authentifizierungssystem veröffentlicht, und alle neuen, mit dem Azure AD-Authentifizierungssystem ausgetauschten Token werden unter Verwendung des neuen Zertifikats verschlüsselt.


> [!NOTE]
> Dieser Zertifikatswechsel wird nur vom Verbund verwendet. Wenn Sie für andere Exchange 2013-Funktionen, die Zertifikate erfordern, dasselbe Zertifikat verwenden, müssen Sie beim Beschaffen und Installieren eines neuen Zertifikats bzw. beim Zertifikatswechsel die Anforderungen dieser Funktionen berücksichtigen.



Wichtige Terminologie

## Überlegungen zur Firewall bei Verbund

Für Verbundfunktionen müssen die Postfach- und Clientzugriffsserver in Ihrer Organisation ausgehenden HTTPS-Zugriff auf das Internet haben. Sie müssen für alle Exchange 2013-Postfach- und Clientzugriffsserver in der Organisation ausgehenden HTTPS-Zugriff einrichten (Port 443 für TCP).

Damit eine externe Organisation auf die Frei/Gebucht-Informationen Ihrer Organisation zugreifen kann, müssen Sie einen Clientzugriffsserver im Internet veröffentlichen. Hierzu ist eingehender HTTPS-Zugriff aus dem Internet auf den Clientzugriffsserver erforderlich. Clientzugriffsserver an Active Directory-Standorten, die nicht über einen im Internet veröffentlichten Clientzugriffsserver verfügen, können Clientzugriffsserver an anderen Active Directory-Standorten verwenden, auf die über das Internet zugegriffen werden kann. Für nicht im Internet veröffentlichte Clientzugriffsserver muss die externe URL des virtuellen Verzeichnisses der Webdienste auf die URL festgelegt sein, die für externe Organisationen sichtbar ist.

[Zurück zum Seitenanfang](sharing-exchange-2013-help.md)

