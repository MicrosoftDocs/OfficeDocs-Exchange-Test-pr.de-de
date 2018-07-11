---
title: 'Voraussetzungen für die Hybridbereitstellung: Exchange 2013 Help'
TOCTitle: Voraussetzungen für die Hybridbereitstellung
ms:assetid: e7454db0-fed4-4662-8890-9501126b1ba2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh534377(v=EXCHG.150)
ms:contentKeyID: 50477195
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Voraussetzungen für die Hybridbereitstellung

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2017-07-25_

**Zusammenfassung:**  Anforderungen an Ihre Exchange-Umgebung vor dem Einrichten einer Hybridbereitstellung.

Vor dem Erstellen und Konfigurieren einer Hybridbereitstellung mithilfe des Assistenten für die Hybridkonfiguration muss die vorhandene lokale Exchange-Organisation bestimmte Anforderungen erfüllen. Wenn diese Anforderungen nicht erfüllt sind, können Sie die Schritte des Assistenten für die Hybridkonfiguration nicht abschließen, und Sie können keine Hybridbereitstellung zwischen Ihrer lokalen Exchange-Organisation und Exchange Online konfigurieren.

## Voraussetzungen für die Hybridbereitstellung

Für die Konfiguration einer Hybridbereitstellung müssen die folgenden Voraussetzungen erfüllt sein:

  - **Lokale Exchange-Organisation**   Hybridbereitstellungen können für lokale Exchange 2007-basierte Organisationen oder höher konfiguriert werden.
    
    Die Version von Exchange, die Sie in Ihrer lokalen Organisation installiert haben, bestimmt die Version der installierbaren Hybridbereitstellung. Sie sollten in der Regel die neueste Version der Hybridbereitstellung konfigurieren, die in Ihrer Organisation unterstützt wird. Wenn z. B. Exchange 2007 in Ihrer lokalen Organisation ausgeführt wird, müssen Sie eine Exchange 2013-basierte Hybridbereitstellung konfigurieren. Eine vollständige Auflistung der Kompatibilität in Hybridbereitstellungen mit Exchange Server und Office 365 für Unternehmen finden Sie in der folgenden Tabelle.
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Lokale Umgebung</th>
    <th>Exchange 2016-basierte Hybridbereitstellung</th>
    <th>Exchange 2013-basierte Hybridbereitstellung</th>
    <th>Exchange 2010-basierte Hybridbereitstellung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Exchange 2016</p></td>
    <td><p>Unterstützt</p></td>
    <td><p>Nicht unterstützt</p></td>
    <td><p>Nicht unterstützt</p></td>
    </tr>
    <tr class="even">
    <td><p>Exchange 2013</p></td>
    <td><p>Unterstützt</p></td>
    <td><p>Unterstützt</p></td>
    <td><p>Nicht unterstützt</p></td>
    </tr>
    <tr class="odd">
    <td><p>Exchange 2010</p></td>
    <td><p>Unterstützt</p></td>
    <td><p>Unterstützt</p></td>
    <td><p>Unterstützt</p></td>
    </tr>
    <tr class="even">
    <td><p>Exchange 2007</p></td>
    <td><p>Nicht unterstützt</p></td>
    <td><p>Unterstützt</p></td>
    <td><p>Unterstützt</p></td>
    </tr>
    </tbody>
    </table>


  - **Lokale Exchange-Versionen** Für Hybridbereitstellungen sind das neueste kumulative Update oder das Updaterollup erforderlich, die für die in Ihrer lokalen Organisation installierte Exchange-Version verfügbar sind. Wenn Sie nicht das neueste kumulative Update oder Updaterollup installieren, wird die unmittelbar vorherige Version ebenfalls auch unterstützt. Ältere kumulativen Updates oder Updaterollups werden nicht unterstützt.
    
    Nehmen wir beispielsweise an, dass Exchange 2013 kumulatives Update 8 in Ihrer lokalen Organisation installiert ist, dann ist das kumulative Update 10 die neueste verfügbare Version von Exchange 2013. Um weiterhin in einer unterstützen Hybridkonfiguration zu bleiben, müssen Sie die Exchange 2013-Server mindestens auf kumulatives Update 9 aktualisieren. Es wird jedoch dringend empfohlen diese auf kumulatives Update 10 zu aktualisieren.
    
    Kumulative Updates und Updaterollups werden vierteljährlich veröffentlicht, sodass Sie durch Aktualisierung Ihrer Server auf die neuesten kumulativen Updates oder Updaterollups von zusätzlicher Flexibilität profitieren, wenn Sie regelmäßig mehr Zeit zum Abschließen von Upgrades benötigen.

  - **Lokale Serverrollen** Die Serverrollen, die Sie in Ihrer lokalen Organisation installieren müssen, sind von der installierten Exchange-Version abhängig.
    
      - **Exchange 2010** Mindestens ein Server mit installierten Postfach-, Hubtransport- und Clientzugriffsserverrollen. Es ist zwar möglich, die Postfach-, Hubtransport- und Clientzugriffsrollen auf separaten Servern zu installieren, es wird jedoch dringend empfohlen, alle Rollen auf jedem Server zu installieren, um zusätzliche Zuverlässigkeit und verbesserte Leistung bereitzustellen.
    
      - **Exchange 2013** Mindestens ein Server mit installierten Postfach- und Clientzugriffsserverrollen. Es ist zwar möglich, die Postfach- und Clientzugriffsrollen auf separaten Servern zu installieren, es wird jedoch dringend empfohlen, beide Rollen auf jedem Server zu installieren, um zusätzliche Zuverlässigkeit und verbesserte Leistung bereitzustellen.
    
      - **Exchange 2016 und neuer** Mindestens ein Server mit der installierten Postfachserverrolle.
    
    Hybridbereitstellungen unterstützen auch die Exchange-Server, auf denen die Edge-Transport-Serverrolle ausgeführt wird. Edge-Transport-Server müssen auf das neueste kumulative Update oder Updaterollup aktualisiert werden, die für die installierte Exchange-Version verfügbar sind. Es wird dringend empfohlen, Edge-Transport-Server in einem Umkreisnetzwerk bereitzustellen. Postfach- und Clientzugriffsserver können nicht in einem Umkreisnetzwerk bereitgestellt werden.

  - **Office 365:**  Hybridbereitstellungen werden in allen Office 365-Plänen unterstützt, die Azure Active Directory-Synchronisierung unterstützen. Alle Pläne für Office 365 Enterprise, Government, Academic und Midsize unterstützen Hybridbereitstellungen. Pläne für Office 365 Small Business und Home unterstützen keine Hybridbereitstellungen.
    
    Weitere Informationen finden Sie unter [Registrieren bei Office 365](https://go.microsoft.com/fwlink/p/?linkid=203981).

  - **Benutzerdefinierte Domänen**   Registrieren Sie benutzerdefinierte Domänen, die in der Hybridbereitstellung verwendet werden sollen, für Office 365. Sie können die Registrierung über das Office 365-Verwaltungsportal durchführen oder optional durch die Konfiguration der Active Directory-Verbunddienste (AD FS) in Ihrer lokalen Organisation vornehmen.
    
    Weitere Informationen finden Sie unter [Hinzufügen Ihrer Domäne zu Office 365](https://go.microsoft.com/fwlink/p/?linkid=229238).

  - **Active Directory-Synchronisierung:**  Stellen Sie das Azure Active Directory Connect-Tool für die Active Directory-Synchronisierung in Ihrer lokalen Organisation bereit.
    
    Weitere Informationen finden Sie unter [Azure AD Connect-Optionen für die Benutzeranmeldung](http://go.microsoft.com/fwlink/p/?linkid=723514).

  - **DNS-Einträge für die AutoErmittlung**   Konfigurieren Sie die öffentlichen DNS-Einträge für die AutoErmittlung für Ihre vorhandenen SMTP-Domänen so, dass sie auf einen lokalen Exchange 2013-Clientzugriffsserver zeigen.

  - **Office 365-Organisationen in der Exchange-Verwaltungskonsole (EAC):**  Der Office 365-Organisationsknoten ist standardmäßig in der lokalen Verwaltungskonsole enthalten. Sie können den Assistenten für die Hybridkonfiguration jedoch erst verwenden, wenn Sie der Office 365-Organisation die Verwaltungskonsole mit den Anmeldeinformationen für den Office 365-Administrator hinzugefügt haben. So können Sie sowohl die lokale als auch die Exchange Online-Organisation über eine einzige Verwaltungskonsole verwalten.
    
    Weitere Informationen finden Sie unter [Hybridverwaltung in Exchange-Hybridbereitstellungen](hybrid-management-in-exchange-hybrid-deployments-exchange-2013-help.md).

  - 
    
    **Zertifikate:**  Installieren Sie Exchange-Dienste, und weisen Sie sie einem gültigen digitalen Zertifikat zu, das Sie von einer vertrauenswürdigen öffentlichen Zertifizierungsstelle erworben haben. Wenngleich für die lokale Verbundvertrauensstellung mit Microsoft Federation Gateway selbstsignierte Zertifikate verwendet werden sollen, können diese Zertifikate nicht für Exchange-Dienste in einer Hybridbereitstellung verwendet werden. Die IIS-Instanz (Internet Information Services, Internetinformationsdienste) auf den Exchange-Servern, die in der Hybridbereitstellung konfiguriert sind, muss über ein gültiges digitales Zertifikat verfügen, das von einer vertrauenswürdigen Zertifizierungsstelle erworben wurde. Zusätzlich müssen die externe URL der Exchange-Webdienste und der in Ihren öffentlichen DNS-Einträgen angegebene AutoErmittlungsendpunkt als alternativer Antragstellername des Zertifikats aufgeführt sein. Die auf den Exchange-Servern installierten Zertifikate, die für den E-Mail-Transport in der Hybridbereitstellung verwendet werden, müssen dieselben Eigenschaften aufweisen (d. h., sie müssen von derselben Zertifizierungsstelle stammen und denselben Antragstellernamen enthalten).
    
    Weitere Informationen finden Sie unter [Zertifikatanforderungen für Hybridbereitstellungen](certificate-requirements-for-hybrid-deployments-exchange-2013-help.md).

  - **EdgeSync**   Wenn Sie Edge-Transport-Server in der lokalen Organisation bereitgestellt haben und die Edge-Transport-Server für sicheren Hybrid-E-Mail-Transport konfigurieren möchten, müssen Sie EdgeSync vor der Verwendung des Assistenten für die Hybridkonfiguration konfigurieren. Sie müssen zudem EdgeSync bei jeder Anwendung eines neuen kumulativen Updates oder Updaterollups auf einen Edge Transport-Server ausführen.
    

    > [!IMPORTANT]
    > EdgeSync ist zwar eine Voraussetzung in Bereitstellungen mit Edge-Transport-Servern, es sind jedoch zusätzliche manuelle Transportkonfigurationseinstellungen erforderlich, wenn Sie Edge-Transport-Server für den sicheren Hybrid-E-Mail-Transport konfigurieren.

    
    Weitere Informationen finden Sie unter [Edge-Transport-Server in Hybridbereitstellungen](edge-transport-servers-with-hybrid-deployments-exchange-2013-help.md).

  - **UM-fähige Postfächer (Unified Messaging)** Wenn Sie UM-fähige Postfächer haben und diese nach Office 365 verschieben möchten, müssen Sie neben einer Exchange-Hybridbereitstellung Folgendes ausführen: Diese Anforderungen müssen erfüllt sein, **bevor** Sie UM-fähige Postfächer nach Office 365 verschieben.
    
      - Lync Server 2010, Lync Server 2013 oder Skype for Business Server 2015 oder höher, integriert in Ihr lokales Telefonsystem **oder**
    
      - Skype for Business Online, integriert in Ihrer lokales Telefonsystem **oder**
    
      - Eine herkömmliche lokale Festnetztelefonanlage oder IP-Nebenstellenanlage.
    
      - In Exchange Online erstellte UM-Postfachrichtlinien, die die Namen der UM-Postfachrichtlinien in Ihrer lokalen Organisation spiegeln.
        

        > [!NOTE]
        > Sie können mehrere lokale UM-Postfachrichtlinien einer UM-Postfachrichtlinie in Exchange Online zuordnen. Hierfür müssen Sie die Exchange-Verwaltungsshell verwenden, um die einzelnen UM-Postfachrichtlinien einer Exchange Online-Richtlinie zuzuordnen.

    
    Weitere Informationen finden Sie unter [Telefonsystemintegration mit UM](https://technet.microsoft.com/de-de/library/jj673558\(v=exchg.150\)), [Telefonieratgeber für Exchange 2013](https://technet.microsoft.com/de-de/library/ee364753\(v=exchg.150\)) und [Einrichten von Cloud PBX-Voicemail - Administratorhilfe](https://go.microsoft.com/fwlink/p/?linkid=826207).

## Protokolle, Ports und Endpunkte für Hybridbereitstellungen

Features und Komponenten von Hybridbereitstellungen erfordern für einen ordnungsgemäßen Betrieb, dass Office 365 Zugriff auf bestimmte Eingangsprotokolle, Ports und Verbindungsendpunkte hat. Bevor Sie Ihre Hybridbereitstellung konfigurieren, vergewissern Sie sich, dass Ihre lokale Netzwerk- und Sicherheitskonfiguration die Features und Komponenten in der nachstehenden Tabelle unterstützen kann: Zusätzlich dazu, dass bestimmte eingehende Protokolle, Ports und Endpunkte zugelassen werden, müssen Computer in Ihrem Netzwerk auch in der Lage sein, auf die IP-Adressen, Ports und URLs zuzugreifen, die in [URLs und IP-Adressbereiche für Office 365](https://go.microsoft.com/fwlink/?linkid=823100) aufgeführt sind.


<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th>Transportprotokoll</th>
<th>Protokoll oberer Ebene</th>
<th>Feature/Komponente</th>
<th>Lokaler Endpunkt</th>
<th>Lokaler Pfad</th>
<th>Authentifizierungsanbieter</th>
<th>Autorisierungsmethode</th>
<th>Unterstützung für Pre-Auth?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP 25 (SMTP)</p></td>
<td><p>SMTP/TLS</p></td>
<td><p>Nachrichtenübermittlung zwischen Office 365 und der lokalen Umgebung</p></td>
<td><p>Exchange 2016-Postfach/Edge</p>
<p>Exchange 2013 CAS/EDGE</p>
<p>Exchange 2010 HUB/EDGE</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Zertifikatbasiert</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>AutoErmittlung</p></td>
<td><p>AutoErmittlung</p></td>
<td><p>Exchange 2016-Postfach</p>
<p>Exchange 2013/2010 CAS</p></td>
<td><p>/autodiscover/autodiscover.svc/wssecurity</p>
<p>/autodiscover/autodiscover.svc</p></td>
<td><p>Azure AD-Authentifizierungssystem</p></td>
<td><p>WS-Security-Authentifizierung</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>EWS</p></td>
<td><p>Frei/Gebucht, E-Mail-Infos, Nachrichtenverfolgung</p></td>
<td><p>Exchange 2016-Postfach</p>
<p>Exchange 2013/2010 CAS</p></td>
<td><p>/ews/exchange.asmx/wssecurity</p></td>
<td><p>Azure AD-Authentifizierungssystem</p></td>
<td><p>WS-Security-Authentifizierung</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>EWS</p></td>
<td><p>Suche in mehreren Postfächern</p></td>
<td><p>Exchange 2016-Postfach</p>
<p>Exchange 2013/2010 CAS</p></td>
<td><p>/ews/exchange.asmx/wssecurity</p>
<p>/autodiscover/autodiscover.svc/wssecurity</p>
<p>/autodiscover/autodiscover.svc</p></td>
<td><p>Authentifizierungsserver</p></td>
<td><p>WS-Security-Authentifizierung</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>EWS</p></td>
<td><p>Postfachmigrationen</p></td>
<td><p>Exchange 2016-Postfach</p>
<p>Exchange 2013/2010 CAS</p></td>
<td><p>/ews/mrsproxy.svc</p></td>
<td><p>NTLM</p></td>
<td><p>Basic</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>AutoErmittlung</p>
<p>EWS</p></td>
<td><p>OAuth</p></td>
<td><p>Exchange 2016-Postfach</p>
<p>Exchange 2013/2010 CAS</p></td>
<td><p>/ews/exchange.asmx/wssecurity</p>
<p>/autodiscover/autodiscover.svc/wssecurity</p>
<p>/autodiscover/autodiscover.svc</p></td>
<td><p>Authentifizierungsserver</p></td>
<td><p>WS-Security-Authentifizierung</p></td>
<td><p>Nr.</p></td>
</tr>
<tr class="odd">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>AD FS (im Lieferumfang von Windows enthalten)</p></td>
<td><p>Windows 2008/2012 Server</p></td>
<td><p>/adfs/*</p></td>
<td><p>Azure AD-Authentifizierungssystem</p></td>
<td><p>Variiert je nach Konfiguration</p></td>
<td><p>Zwei Faktoren</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Azure Active Directory Connect mit AD FS</p></td>
<td><p>Windows 2012 R2 Server</p></td>
<td><p>/adfs/*</p></td>
<td><p>Azure AD-Authentifizierungssystem</p></td>
<td><p>Variiert je nach Konfiguration</p></td>
<td><p>Zwei Faktoren</p></td>
</tr>
</tbody>
</table>


## Empfohlene Tools und Dienste

Zusätzlich zu den oben aufgeführten Voraussetzungen sind weitere Tools und Dienste von Vorteil, wenn Sie Hybridbereitstellungen mit dem Assistenten für die Hybridkonfiguration konfigurieren:

  - **Bereitstellungs-Assistent für Exchange Server:**  Der Bereitstellungs-Assistent für Exchange Server ist ein kostenloses webbasiertes Tool, mit dem Sie Exchange in Ihrer lokalen Organisation bereitstellen, eine Hybridbereitstellung zwischen Ihrer lokalen Organisation und Office 365 konfigurieren oder eine vollständige Migration zu Office 365 vornehmen können. Der Assistent stellt Ihnen einige einfache Fragen und erstellt dann anhand Ihrer Antworten eine angepasste Checkliste mit Anweisungen bereit, um Exchange Server bereitzustellen und zu konfigurieren. Der Bereitstellungs-Assistent liefert Ihnen genau die Informationen, die Sie zum Konfigurieren Ihrer Hybridumgebung benötigen.
    
    Weitere Informationen finden Sie unter [Bereitstellungs-Assistent für Exchange Server](https://technet.microsoft.com/exdeploy2013).
    
     

  - **Remoteverbindungsuntersuchung**   Die Microsoft-Remoteverbindungsuntersuchung überprüft die externen Verbindungen Ihrer lokalen Exchange-Organisation und stellt sicher, dass Sie die Voraussetzungen für die Konfiguration Ihrer Hybridbereitstellung erfüllen. Es wird dringend empfohlen, Ihre lokale Organisation mit der Remoteverbindungsuntersuchung zu überprüfen, bevor Sie Ihre Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration konfigurieren.
    
    Weitere Informationen finden Sie unter [Microsoft-Remoteverbindungsuntersuchung](https:////testconnectivity.microsoft.com/)
    
     

  - **Einmaliges Anmelden:**  Benutzer können mithilfe der einmaligen Anmeldung unter Verwendung derselben Anmeldeinformationen sowohl auf die lokale als auch auf die Exchange Online-Organisation zugreifen. Sie bietet Benutzern ein vertrautes Anmeldeerlebnis und ermöglicht Administratoren das problemlose Steuern von Kontorichtlinien für Postfächer in der Exchange Online-Organisation über die lokalen Active Directory-Verwaltungstools.
    
    Beim Bereitstellen des einmaligen Anmeldens haben Sie zwei Optionen: Synchronisierung von Kennwörtern und Active Directory-Verbunddienste (AD FS). Beide Optionen werden von Azure Active Directory Connect bereitgestellt. Die Kennwortsynchronisierung ermöglicht nahezu jeder Organisation (unabhängig von der jeweiligen Größe), die einmalige Anmeldung einfach zu implementieren. Daher und weil die Benutzerfreundlichkeit in einer Hybridbereitstellung mit aktivierter einmaliger Anmeldung wesentlich besser ist, sollten Sie sie implementieren. Bei äußerst großen Organisationen (die beispielsweise mehrere Active Directory-Gesamtstrukturen aufweisen, die mit der Hybridbereitstellung verbunden werden müssen) sind die Active Directory-Verbunddienste (AD FS) erforderlich.
    
    Weitere Informationen finden Sie unter: [Einmaliges Anmelden in Hybrid-Bereitstellungen](single-sign-on-with-hybrid-deployments-exchange-2013-help.md)

