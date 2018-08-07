---
title: 'Verwenden der hybriden modernen Auth. mit Outlook für iOS und Android'
TOCTitle: Using hybrid Modern Authentication with Outlook for iOS and Android
ms:assetid: 0e701643-1f18-4cc3-8595-4fd4b15caf6c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt846639(v=EXCHG.150)
ms:contentKeyID: 74520311
ms.date: 04/25/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Using hybrid Modern Authentication with Outlook for iOS and Android

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-04-19_

**Zusammenfassung:**  Wie Administratoren die moderne Hybridauthentifizierung und Enterprise Mobility + Security-Features für lokale Exchange-Postfächer bereitstellen können, um Unterstützung für Outlook für iOS und Android zu aktivieren.

Die Outlook-App für iOS und Android wurde als beste Möglichkeit zur Nutzung von Office 365 auf Ihrem mobilen Gerät entwickelt, indem Microsoft-Dienste Sie beim Suchen, Planen und Priorisieren Ihres täglichen Lebens und der Arbeit unterstützen. Outlook bietet das Maß an Sicherheit, Datenschutz und Support, das Sie benötigen. Gleichzeitig werden Unternehmensdaten mit Funktionen wie bedingtem Azure Active Directory-Zugriff und Intune-App-Schutzrichtlinien geschützt. Die folgenden Abschnitte geben eine Übersicht über die Architektur der modernen Hybridauthentifizierung, die erforderlichen Voraussetzungen für die Bereitstellung und Verfahren zur sicheren Bereitstellung von Outlook für iOS und Android für lokale Exchange-Postfächer.

## Microsoft Cloud-Architektur für Exchange Server-Hybridkunden

Outlook für IOS und Android ist eine cloudgestützte Anwendung. Dies bedeutet, dass Ihre Benutzeroberfläche aus einer lokal installierten App besteht, die von einem sicheren und skalierbaren Dienst unterstützt wird, der in der Microsoft Cloud ausgeführt wird.

Für Exchange Server-Postfächer ist das Design der neuen Architektur von Outlook für IOS und Android mit dem der Legacy-Architektur vergleichbar. Da der Dienst jetzt jedoch direkt in die Microsoft Cloud integriert ist (mithilfe von Office 365 und Microsoft Azure), erhalten Kunden zusätzliche Vorteile in Form von Sicherheit, Datenschutz, integrierter Compliance und transparenten Vorgängen, zu denen sich Microsoft im [Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-welcome) und [Azure Trust Center](https://www.microsoft.com/trustcenter/cloudservices/azure) verpflichtet.

![Architektur einer modernen Hybridauthentifizierung in Outlook für iOS und Android](images/Mt846639.20a7e963-916d-47e0-bffb-4d86c4777bea(EXCHG.150).png "Architektur einer modernen Hybridauthentifizierung in Outlook für iOS und Android")

Daten, die von Exchange Online an die Outlook-App übergeben werden, werden über eine mit TLS gesicherte Verbindung übertragen. Das auf Azure ausgeführte Protokollkonvertierungsprogramm übernimmt das Weiterleiten von Daten, Befehlen und Benachrichtigungen, kann die eigentlichen Daten jedoch nicht lesen.

Die Exchange ActiveSync-Verbindung zwischen Exchange Online und der lokalen Umgebung ermöglicht die Synchronisierung der lokalen Daten der Benutzer und umfasst das E-Mail-Aufkommen von vier Wochen, alle Kalenderdaten, alle Kontaktdaten und den Abwesenheitsstatus in Ihrem Exchange Online-Mandanten. Diese Daten werden nach 30 Tagen automatisch aus Exchange Online entfernt, wenn das Konto in Azure Active Directory gelöscht wird.

Die Synchronisierung von Daten zwischen der lokalen Umgebung und Exchange Online erfolgt unabhängig vom Benutzerverhalten. Dadurch wird sichergestellt, dass wir neue Nachrichten sehr schnell an die Geräte senden können.

Die Verarbeitung von Informationen in der Microsoft Cloud ermöglicht erweiterte Features und Funktionen, wie die Kategorisierung von E-Mails für den Posteingang mit Fokus, angepasste Benutzeroberflächen für Reise und Kalender sowie eine verbesserte Suchgeschwindigkeit. Indem intensive Verarbeitungsvorgänge in die Cloud ausgelagert und die auf den Benutzergeräten erforderlichen Ressourcen minimiert werden, können die Leistung und Stabilität der App verbessert werden. Und schließlich kann Outlook dadurch Features erstellen, die für alle E-Mail-Konten ausgeführt werden können, unabhängig von den Möglichkeiten Funktionen der zugrunde liegenden Server (z. B. verschiedene Versionen von Exchange Server oder Office 365).

Diese neue Architektur weist insbesondere die folgenden Verbesserungen auf:

1.  **Unterstützung von Enterprise Mobility + Security:**  Kunden können die Vorteile von Microsoft Enterprise Mobility + Security (EMS) einschließlich Microsoft Intune und Azure Active Directory Premium nutzen, um bedingten Zugriff und Intune-App-Schutzrichtlinien zu aktivieren, die Nachrichtendaten von Unternehmen auf dem mobilen Gerät kontrollieren und sichern.

2.  **Vollständig unterstützt von Microsoft Cloud:**  Die lokalen Postfachdaten werden mit Exchange Online synchronisiert, was die Vorteile von Sicherheit, Datenschutz, Compliance und transparenten Vorgängen bietet, zu denen sich Microsoft im [Office 365 Trust Center](https://products.office.com/business/office-365-trust-center-welcome) verpflichtet.

3.  **OAuth schützt Benutzerkennwörter:**  Outlook nutzt die moderne Hybridauthentifizierung (OAuth), um die Anmeldeinformationen von Benutzern zu schützen. Die moderne Hybridauthentifizierung stellt Outlook einen sicheren Mechanismus für den Zugriff auf die Exchange-Daten zur Verfügung, ohne die Anmeldeinformationen eines Benutzers anfassen oder speichern zu müssen. Bei der Anmeldung authentifiziert sich der Benutzer direkt bei einer Identitätsplattform (entweder Azure Active Directory oder ein lokaler Identitätsanbieter wie AD FS) und erhält von dieser ein Zugriffstoken, dass Outlook Zugriff auf das Postfach oder die Dateien des Benutzers gewährt. Zu keinem Zeitpunkt hat der Dienst Zugriff auf das Kennwort des Benutzers.

4.  **Bereitstellung eindeutiger Geräte-IDs:**  Jede Outlook-Verbindung wird in Microsoft Intune eindeutig registriert und kann daher als eindeutige Verbindung verwaltet werden.

5.  **Freischaltung neuer Features unter iOS und Android:**  Mit diesem Update kann die Outlook-App native Office 365-Features nutzen, die im lokalen Exchange heute noch nicht unterstützt werden, z. B. können die vollständige Exchange Online-Suche und der Posteingang mit Fokus genutzt werden. Diese Features stehen nur zur Verfügung, wenn Sie Outlook für iOS und Android verwenden.


> [!NOTE]
> Die Geräteverwaltung über das lokale Exchange Admin Center ist nicht möglich. Intune ist erforderlich, um mobile Geräte zu verwalten.



## Datensicherheit, Zugriff und überwachte Kontrollen

Wenn lokale Daten mit Exchange Online synchronisiert werden, stellen Kunden in der Regel Fragen dazu, wie die Daten in Exchange Online geschützt werden. Im Whitepaper [Encryption in the Microsoft Cloud](http://aka.ms/office365ce) wird erläutert, wie BitLocker zur Verschlüsselung auf Volumeebene verwendet wird. Die im Whitepaper erläuterte Dienstverschlüsselung mit der Kundenschlüsseloption wird in der Architektur von Outlook für iOS und Android unterstützt. Der Benutzer benötigt jedoch eine Lizenz für Office 365 Enterprise E5 (oder die entsprechenden Versionen dieser Pläne für Behörden oder Bildungseinrichtungen), damit ihm eine Verschlüsselungsrichtlinie zugewiesen wird.

Standardmäßig verfügen die Microsoft-Techniker über keine ständigen Administratorrechte und keinen ständigen Zugriff auf Kundeninhalte in Office 365. Im Whitepaper [Office 365 Administrative Access Controls](http://aka.ms/office365aac) werden die Themen Personalüberprüfung, Hintergrundprüfungen, Lockbox und Kunden-Lockbox sowie vieles mehr erläutert.

[ISO Audited Controls on Service Assurance](https://sip.protection.office.com/) gibt den Status von überwachten Kontrollen aus globalen Standards und gesetzlichen Vorschriften zur Informationssicherheit an, die Office 365 implementiert hat.

## Verbindungsfluss

Wenn Outlook für iOS und Android mit moderner Hybridauthentifizierung aktiviert ist, sieht der Verbindungsfluss folgendermaßen aus.

![Authentifizierungsfluss bei der modernen Hybridauthentifizierung](images/Mt846639.d6e20ddb-cf8e-4154-8a17-95657ef696d1(EXCHG.150).png "Authentifizierungsfluss bei der modernen Hybridauthentifizierung")

1.  Nachdem der Benutzer seine E-Mail-Adresse eingegeben hat, stellt Outlook für iOS und Android eine Verbindung mit dem AutoDetect-Dienst her. AutoDetect bestimmt den Postfachtyp, indem eine AutoErmittlungsabfrage an Exchange Online gestartet wird. Exchange Online stellt fest, dass das Postfach des Benutzers lokal ist, und gibt eine 302-Umleitung mit der lokalen AutoErmittlungs-URL an AutoDetect zurück. AutoDetect initiiert eine Abfrage des lokalen AutoErmittlungsdiensts, um den ActiveSync-Endpunkt für die e-Mail-Adresse zu ermitteln. Die lokal versuchte URL ähnelt diesem Beispiel: https://autodiscover.contoso.com/autodiscover/autodiscover.json?Email=test%40contoso.com\&Protocol=activesync\&RedirectCount=3.

2.  AutoDetect initiiert eine Verbindung zur lokalen ActiveSync-URL, die in Schritt 1 oben zurückgegeben wurde, mit einer leeren Bearer-Herausforderung. Die leere Bearer-Herausforderung teilt dem lokalen ActiveSync mit, dass der Client die moderne Authentifizierung unterstützt. Das lokale ActiveSync antwortet mit einer 401-Herausforderungsantwort, die den *WWW-Authentificate: Bearer*-Header enthält. Der „WWW-Authenticate: Bearer“-Header enthält den „authorization\_uri“-Wert, der den AAD-Endpunkt (Azure Active Directory) identifiziert, der zum Abrufen eines OAuth-Tokens verwendet werden soll.

3.  AutoDetect gibt den AAD-Endpunkt an den Client zurück. Der Client beginnt mit dem Anmeldefluss, und dem Benutzer wird ein Webformular angezeigt (oder er wird zur Microsoft Authenticator-App umgeleitet), und er kann Anmeldeinformationen eingeben. Je nach Identitätskonfiguration kann dies eine Verbundendpunktumleitung zu einem lokalen Identitätsanbieter beinhalten. Schließlich erhält der Client ein Zugriffs- und Aktualisierungstokenpaar namens AT1/RT1. Dieses Zugriffstoken gilt für den Outlook für IOS und Android-Client mit einer Zielgruppe des Exchange Online-Endpunkts.

4.  Outlook für IOS und Android stellt eine Verbindung mit dem Stateless Protocol Translator her, in dem das proprietäre Geräteprotokoll des Clients in ein Protokoll übersetzt wird, das Exchange Online versteht.

5.  An Exchange Online wird eine Bereitstellungsanforderung übergeben, die das Zugriffstoken des Benutzers (AT1) und den lokalen Endpunkt ActiveSync-Endpunkt enthält.

6.  Die MRS-Bereitstellungs-API in Exchange Online nutzt AT1 als Eingabe und ruft ein zweites Zugriffs- und Aktualisierungstokenpaar (AT2/RT2) für den Zugriff auf das lokale Postfach über einen Anruf im Auftrag von Azure Active Directory ab. Dieses zweite Zugriffstoken gilt für den Client, also Exchange Online, und eine Zielgruppe des lokalen ActiveSync-Namespace-Endpunkts.

7.  Wenn das Postfach nicht bereitgestellt wurde, erstellt die Bereitstellungs-API ein Postfach.

8.  Die MRS-Bereitstellungs-API richtet eine sichere Verbindung zum lokalen ActiveSync-Endpunkt ein und synchronisiert die Messagingdaten des Benutzers unter Verwendung des Zugriffstokens AT2 als Authentifizierungsmechanismus. RT2 wird in regelmäßigen Abständen verwendet, um ein neues AT2 zu generieren, damit die Daten ohne Eingriff des Benutzers im Hintergrund synchronisiert werden können.

## Technische und Lizenzierungsanforderungen

Für die Architektur der hybriden modernen Authentifizierung gelten die folgenden technischen Anforderungen:

1.  **Lokales Exchange-Setup**:
    
      - Minimale CU-Bereitstellung (Kumuliertes Update) auf allen Exchange-Servern von Exchange Server 2016 CU8 oder Exchange Server 2013 CU19. Beachten Sie, dass Kunden mit Hybridbereitstellungen, in denen Exchange lokal und in der Cloud bereitgestellt wird, oder die Exchange Online-Archivierung (EOA) mit ihrer lokalen Exchange-Bereitstellung verwenden, das aktuelle CU oder ein CU vor dem aktuellen bereitstellen müssen.
    
      - Alle Exchange 2007- oder Exchange 2010-Server müssen aus der Umgebung entfernt werden. Exchange Server 2010 SP3 liegt außerhalb des Mainstream-Supports und funktioniert nicht mit von Intune verwaltetem Outlook für iOS und Android. In dieser Architektur verwendet Outlook für iOS und Android OAuth als Authentifizierungsmechanismus. Eine der lokalen Konfigurationsänderungen, die vorgenommen werden, aktiviert den OAuth-Endpunkt der Microsoft Cloud als standardmäßigen Autorisierungsendpunkt. Wenn diese Änderung vorgenommen wird, können Clients beginnen, die Verwendung von OAuth auszuhandeln. Da dies eine organisationsweite Änderung ist, wird für in Exchange 2013 oder Exchange 2016 verwaltete Exchange 2010-Postfächer fälschlicherweise angenommen, es könnte OAuth ausgeführt werden, und sie werden getrennt, da Exchange 2010 OAuth nicht als Authentifizierungsmechanismus unterstützt.

2.  **Active Directory-Synchronisierung**. Active Directory-Synchronisierung des gesamten lokalen Verzeichnisses mit Azure Active Directory über Azure AD Connect. Sie müssen sicherstellen, dass die folgenden Attribute synchronisiert werden:
    
      - Office 365 ProPlus
    
      - Exchange Online
    
      - Exchange Hybrid-Rückschreiben
    
      - Azure RMS
    
      - Intune

3.  **Exchange Hybrid-Setup:**  Erfordert vollständige Hybridbeziehung zwischen lokalem Exchange und Exchange Online.
    
      - Der Hybrid Office 365-Mandant ist im vollständig hybriden Konfigurationsmodus konfiguriert und wie unter [Exchange-Bereitstellungs-Assistent](http://technet.microsoft.com/exdeploy) eingerichtet.
    
      - Erfordert einen Office 365 Enterprise-, Business- oder Education-Mandanten.
    
      - Die lokalen Postfachdaten werden in der gleichen Rechenzentrumsregion synchronisiert, in der dieser Office 365-Mandant eingerichtet wurde. Weitere Informationen zum Speicherort von Office 365-Daten finden Sie im Abschnitt [Wo befinden sich meine Daten?](http://o365datacentermap.azurewebsites.net/) im Office 365 Trust Center.
    
      - Die Verwendung von Office 365 US Government Community and Defense-Mandanten, Office 365 Deutschland-Mandanten und Mandanten mit Office 365 China, betrieben von 21Vianet, wird nicht unterstützt.
    
      - Die externen URL-Hostnamen für Exchange ActiveSync und AutoErmittlung müssen als Dienstprinzipale in Azure Active Directory über den Hybridkonfigurations-Assistenten veröffentlicht werden.
    
      - Die AutoErmittlungs- und Exchange ActiveSync-Namespaces müssen über das Internet zugänglich sein und können nicht über eine Vorauthentifizierungslösung bereitgestellt werden.
    
      - Stellen Sie sicher, dass keine SSL- oder TLS-Verschiebung zwischen dem Lastenausgleich und Ihren Exchange-Servern verwendet wird, da sich dies auf die Verwendung des OAuth-Tokens auswirkt. SSL- und TLS-Bridging (Terminierung und Wiederverschlüsselung) wird unterstützt.

4.  **Intune-Setup:**  Nur-Cloud- und Hybridbereitstellungen von Intune werden unterstützt (MDM für Office 365 wird nicht unterstützt).

5.  **Office 365-Lizenzierung\*:**  Jeder Benutzer muss eine der folgenden Office 365-Lizenzen besitzen:
    
      - Kommerziell: Enterprise E3-, Enterprise E5-, ProPlus- oder Business-Lizenzen
    
      - Behörden: US-amerikanische Government Community G3, U.S. Government Community G5
    
      - Education: Office 365 Education E3, Office 365 Education E5
    
    Darüber hinaus müssen die Lizenzen die Office-Clientanwendungen umfassen, die für die gewerbliche Nutzung von Outlook für IOS und Android erforderlich sind.

6.  **EMS-Lizenzierung\*:**  Jeder lokale Benutzer muss eine der folgenden Lizenzen besitzen:
    
      - Eigenständiges Intune + eigenständiges Azure Active Directory Premium
    
      - Enterprise Mobility + Security E3, Enterprise Mobility + Security E5

**\*** Microsoft Secure Productive Enterprise (SPE) enthält alle für Office 365 und EMS erforderlichen Lizenzen.

## Implementierungsschritte

Zum Aktivieren der Unterstützung für moderne Hybridauthentifizierung in Ihrer Organisation sind die folgenden Schritte nötig, die in den folgenden Abschnitten erläutert werden:

1.  Erstellen einer Richtlinie für bedingten Zugriff

2.  Erstellen einer Intune-App-Schutzrichtlinie

3.  Aktivieren der modernen Hybridauthentifizierung

4.  Wenden Sie sich an Microsoft

## Erstellen einer Richtlinie für bedingten Zugriff

Sobald sich Ihre Organisation entschlossen hat, den Benutzerzugriff auf Exchange-Daten zu standardisieren und Outlook für iOS und Android als die einzige E-Mail-App für Endbenutzer einzusetzen, kann eine Richtlinie für bedingten Zugriff konfiguriert werden, die andere mobile Zugriffsmethoden blockiert. Outlook für IOS und Android authentifiziert Benutzer über das Azure Active Directory-Identitätsobjekt und stellt dann eine Verbindung mit Exchange Online her. Daher müssen Sie Azure Active Directory-Richtlinien für bedingten Zugriff erstellen, um die Verbindungen von mobilen Geräten zu Exchange Online zu beschränken. Zu diesem Zweck benötigen Sie zwei Richtlinien für bedingten Zugriff, wobei jede Richtlinie auf alle potenziellen Benutzer abzielt. Informationen zum Erstellen dieser Richtlinien finden Sie unter [App-basierter bedingter Zugriff mit Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-mam#exchange-online-policy).

1.  Die erste Richtlinie lässt Outlook für iOS und Android zu und verhindert, dass OAuth-fähige Exchange ActiveSync-Clients eine Verbindung zu Exchange Online herstellen. Weitere Informationen finden Sie unter „Schritt 1 - Konfigurieren einer Azure AD-Richtlinie für bedingten Zugriff für Exchange Online“.

2.  Durch die zweite Richtlinie wird verhindert, dass Exchange ActiveSync-Clients über die Standardauthentifizierung eine Verbindung zu Exchange Online herstellen. Weitere Informationen finden Sie unter „Schritt 2 - Konfigurieren einer Azure AD-Richtlinie für bedingten Zugriff für Exchange Online mit ActiveSync (EAS)“.

Die Richtlinien nutzen das Gewährungssteuerelement [Genehmigte Client-App erfordern](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference), durch das sichergestellt wird, dass nur Microsoft-Apps, in die das Intune SDK integriert ist, Zugriff gewährt wird.


> [!IMPORTANT]
> Um die App-basierten Richtlinien für bedingten Zugriff zu verwenden, muss die Microsoft Authenticator-App auf iOS-Geräten installiert werden. Für Android-Geräte wird die App für das Intune-Unternehmensportal verwendet. Weitere Informationen finden Sie unter <A href="https://docs.microsoft.com/intune/app-based-conditional-access-intune">App-basierter bedingter Zugriff mit Intune</A>.



Um die Verbindung anderer mobiler Geräteclients (z. B. des nativen E-Mail-Clients aus dem mobilen Betriebssystem) mit Ihrer lokalen Umgebung zu blockieren (wobei die Authentifizierung über Standardauthentifizierung beim lokalen Active Directory erfolgt), haben Sie zwei Optionen:

1.  Sie können die integrierten Exchange-Zugriffsregeln für Mobilgeräte nutzen und die Verbindung aller Mobilgeräte blockieren, indem Sie in der Exchange-Verwaltungsshell Folgendes festlegen:
    
        Set-ActiveSyncOrganizationSettings -DefaultAccessLevel Block

2.  Sie können nach der Installation des lokalen Exchange Connectors eine lokale Richtlinie für bedingten Zugriff in Intune nutzen. Weitere Informationen finden Sie unter [Erstellen einer Richtlinie für bedingten Zugriff auf eine lokale Installation von Exchange und auf das ältere Exchange Online Dedicated](https://docs.microsoft.com/intune/conditional-access-exchange-create#configure-exchange-on-premises-access).


> [!NOTE]
> Wenn Sie eine der oben aufgeführten lokalen Optionen implementieren, beachten Sie, dass dies Benutzer daran hindern kann, eine Verbindung mit Exchange auf ihren mobilen Geräten herzustellen.



## Erstellen einer Intune-App-Schutzrichtlinie

Nach dem Aktivieren der modernen Hybridauthentifizierung können alle lokalen mobilen Benutzer Outlook für iOS und Android mithilfe der Office 365-basierten Architektur nutzen. Daher ist es wichtig, Unternehmensdaten mit einer Intune-App-Schutzrichtlinie zu schützen.

Erstellen Sie Intune-App-Schutzrichtlinien für iOS und Android anhand der Schritte in [Erstellen und Zuweisen von App-Schutzrichtlinien](https://docs.microsoft.com/intune/app-protection-policies). Jede Richtlinie muss mindestens Folgendes enthalten:

1.  Sie umfassen alle mobilen Microsoft-Anwendungen, z. B. Word, Excel oder PowerPoint, da dadurch sichergestellt wird, dass Benutzer auf Unternehmensdaten zugreifen und diese auf sichere Weise in einer Microsoft-App bearbeiten können.

2.  Sie simulieren die Sicherheitsfunktionen, die Exchange für mobile Geräte bereitstellt, z. B.:
    
      - Für den Zugriff ist eine PIN erforderlich (die „Typ auswählen“, „PIN-Länge“, „Einfache PIN zulassen“ und „Fingerabdruck zulassen“ umfasst)
    
      - Verschlüsseln von App-Daten
    
      - Blockieren der Ausführung von verwalteten Apps auf per Jailbreak oder Rooting manipulierten Geräten

3.  Sie sind für alle Benutzer zugewiesen. Dadurch wird sichergestellt, dass alle Benutzer geschützt sind, unabhängig davon, ob sie Outlook für iOS und Android verwenden.

Zusätzlich zu den oben genannten minimalen Richtlinienanforderungen, sollten Sie in Erwägung ziehen, Richtlinieneinstellungen für erweiterten Schutz bereitzustellen, z. B. **Ausschneiden, Kopieren und Einfügen mit anderen Apps einschränken**, um Datenlecks weiter zu verhindern. Weitere Informationen zu den verfügbaren Einstellungen finden Sie unter [Einstellungen für Android-App-Schutzrichtlinien in Microsoft Intune](https://docs.microsoft.com/intune/app-protection-policy-settings-android) und [Einstellungen für App-Schutzrichtlinien für iOS](https://docs.microsoft.com/intune/app-protection-policy-settings-ios).


> [!IMPORTANT]
> Um Intune-App-Schutzrichtlinien für Apps auf Android-Geräten anzuwenden, die nicht in Intune registriert sind, muss der Benutzer auch das Intune-Unternehmensportal installieren. Weitere Informationen finden Sie unter<A href="https://docs.microsoft.com/de-de/intune/app-protection-enabled-apps-android">Das passiert, wenn Ihre Android-App von App-Schutzrichtlinien verwaltet wird</A>.



## Aktivieren der modernen Hybridauthentifizierung

Wenn Sie die moderne Hybridauthentifizierung nicht aktiviert haben, überprüfen und implementieren Sie die Schritte in [Übersicht über die moderne Hybridauthentifizierung und Voraussetzungen für ihre Verwendung mit lokalen Skype for Business- und Exchange-Servern](https://support.office.com/article/hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers-ef753b32-7251-4c9e-b442-1a5aec14e58d?).

Wenn Sie die moderne Hybridauthentifizierung bereits aktiviert haben, um andere Versionen von Outlook wie z. B. Outlook für Mac für die lokalen Benutzer zu unterstützen, wie unter [Konfigurieren von lokalem Exchange Server für die Verwendung der modernen Hybridauthentifizierung](https://support.office.com/article/how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication-cef3044d-d4cb-4586-8e82-ee97bd3b14ad?) beschrieben, müssen Sie nur noch ein paar zusätzliche Schritte ausführen:

1.  Erstellen Sie eine Exchange-Zulassungsregel für den Gerätezugriff, um Exchange Online zu ermöglichen, eine Verbindung mit Ihrer lokalen Umgebung mithilfe des ActiveSync-Protokolls herzustellen:
    
        If ((Get-ActiveSyncOrganizationSettings).DefaultAccessLevel -ne "Allow") {New-ActiveSyncDeviceAccessRule -Characteristic DeviceType -QueryString "OutlookService" -AccessLevel Allow}
    
    Beachten Sie, dass die Geräteverwaltung über das lokale Exchange Admin Center nicht möglich ist. Intune ist erforderlich, um mobile Geräte zu verwalten.

2.  Erstellen Sie eine Exchange-Gerätezugriffsregel, die verhindert, dass Benutzer mit Outlook für iOS und Android mit Standardauthentifizierung eine Verbindung mit der lokalen Umgebung über das Exchange ActiveSync-Protokoll herstellen:
    
        New-ActiveSyncDeviceAccessRule -Characteristic DeviceModel -QueryString "Outlook for iOS and Android" -AccessLevel Block
    

    > [!NOTE]
    > Nachdem diese Regel erstellt wurde, werden Benutzer, die Outlook für iOS und Android mit Standardauthentifizierung verwenden, blockiert.



3.  Stellen Sie sicher, dass die EAS-Eigenschaft maxRequestLength entsprechend den Werten MaxSendSize/MaxReceiveSize Ihrer Transportkonfiguration konfiguriert ist:
    
      - Pfad: `%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config`
    
      - Eigenschaft: `maxRequestLength`
    
      - Wert: Größe in KB (Beispiel: 10 MB ist 10240)

## Wenden Sie sich an Microsoft

Um die Unterstützung der modernen Hybridauthentifizierung für Outlook für iOS und Android zu aktivieren, müssen Sie sich an Ihr Microsoft-Kundenteam, Ihren Kundendienst-Kontakt (CSS) oder Ihren Technical Account Manager wenden. Sie müssen alle SMTP-Domänen angeben (und alle UPN-Domänen, falls Ihre UPN-Domänen nicht mit der SMTP-Adresse übereinstimmen). Nachdem die Domänen bereitgestellt und aktiviert wurden, wird die moderne Hybridauthentifizierung für lokale Postfächer mit Outlook für iOS und Android unterstützt.

## Nicht unterstützte Clientfeatures

Die folgenden Features werden für lokale Postfächer mit moderner Hybridauthentifizierung mit Outlook für iOS und Android nicht unterstützt.

  - Ordner „Entwurf“ und Synchronisierung von Nachrichtenentwürfen

  - Gemeinsamer Kalenderzugriff und stellvertretender Kalenderzugriff

  - Cortana – Zeit zu gehen

  - Kalenderanlagen

  - Vorgangsverwaltung mit Microsoft To-Do

## Häufig gestellte Fragen zum Verbindungsfluss

**F:**  Meine Organisation verfügt über eine Sicherheitsrichtlinie, die erfordert, dass eingehende Internetverbindungen auf genehmigte IP-Adressen oder FQDNs beschränkt werden. Ist das mit dieser Architektur möglich?

**A:**  Microsoft empfiehlt, dass die lokalen Endpunkte für AutoErmittlungs- und ActiveSync-Protokolle aus dem Internet ohne jegliche Einschränkungen geöffnet werden und zugänglich sind. In bestimmten Situationen ist dies vielleicht nicht möglich. Beispielsweise möchten Sie in einem Zeitraum der Koexistenz mit einer anderen MDM-Lösung das ActiveSync-Protokoll einschränken, um zu verhindern, dass Benutzer die MDM-Lösung von Drittanbietern während der Migration zu Intune und Outlook für iOS und Android umgehen. Wenn Sie auf Ihren lokalen Firewall- oder Gatewaygeräten Einschränkungen definieren müssen, empfiehlt Microsoft die Filterung basierend auf FQDN-Endpunkten. Wenn FQDN-Endpunkte nicht verwendet werden können, filtern Sie nach IP-Adressen. Stellen Sie sicher, dass die folgenden IP-Subnetze und FQDNs in der Whitelist enthalten sind:

  - Alle Exchange Online-URLs und IP-Subnetzadressbereiche gemäß der Definition in [URLs und IP-Adressbereiche von Office 365](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

  - Alle Outlook für IOS und Android-App-FQDNs gemäß der Definition in [Netzwerkanforderungen in Office 365 ProPlus und Mobile](https://support.office.com/article/network-requests-in-office-365-proplus-and-mobile-eb73fcd1-ca88-4d02-a74b-2dd3a9f3364d?).

  - Alle IP-Subnetze US-amerikanischer und europäischer Azure-Rechenzentrumsregionen gemäß der Definition in [IP-Bereiche des Microsoft Azure-Rechenzentrums](https://www.microsoft.com/download/details.aspx?id=41653). Dies ist erforderlich, da der AutoDetect-Dienst Verbindungen mit der lokalen Infrastruktur herstellt, wie unter Verbindungsfluss beschrieben. Derzeit nutzt der AutoDetect-Dienst keine IP-Reservierungen in Azure.

**F:**  Meine Organisation nutzt derzeit eine Drittanbieter-MDM-Lösung zum Steuern der Konnektivität von Mobilgeräten. Wenn ich den Exchange ActiveSync-Namespace im Internet verfügbar mache, eröffnet dies den Benutzern eine Möglichkeit, die Drittanbieter-MDM-Lösung während des Zeitraums der Koexistenz zu umgehen. Wie kann ich dies verhindern?

**A:**  Es gibt drei mögliche Lösungen für dieses Problem:

1.  Implementieren Sie Exchange-Zugriffsregeln für Mobilgeräte, um zu steuern, welche Geräte zum Herstellen der Verbindung zugelassen werden.

2.  Einige Drittanbieter-MDM-Lösungen lassen sich mit Exchange-Zugriffsregeln für Mobilgeräte integrieren, indem nicht genehmigte Zugriffe gesperrt und gleichzeitig genehmigte Geräte in der ActiveSyncAllowedDeviceIDs-Eigenschaft des Benutzers hinzugefügt werden.

3.  Implementieren Sie IP-Beschränkungen für den Exchange ActiveSync-Namespace.

**F:**  Kann ich Azure ExpressRoute für die Verwaltung des Datenverkehrs zwischen der Microsoft-Cloud und meiner lokalen Umgebung nutzen?

**A:**  Die Verbindung mit der Microsoft-Cloud erfordert eine Internetverbindung. Jedoch kann eine Teilmenge des Office 365-Netzwerkdatenverkehrs über Azure ExpressRoute weitergeleitet werden. Weitere Informationen finden Sie unter [Azure ExpressRoute für Office 365](https://support.office.com/article/azure-expressroute-for-office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).

Mit ExpressRoute gibt es keinen privaten IP-Adressraum für ExpressRoute-Verbindungen noch kann eine „private“ DNS-Auflösung erfolgen. Das bedeutet, dass jeder Endpunkt, den Ihr Unternehmen über ExpressRoute nutzen möchte, im öffentlichen DNS aufgelöst werden muss. Wenn dieser Endpunkt zu einer IP-Adresse aufgelöst wird, die in den angekündigten der ExpressRoute-Leitung zugeordneten Präfixen enthalten ist (Ihr Unternehmen muss diese Präfixe im Azure-Portal konfigurieren, wenn Sie Microsoft-Peering für die ExpressRoute-Verbindung aktivieren), wird die ausgehende Verbindung von Exchange Online zu Ihrer lokalen Umgebung über die ExpressRoute-Leitung weitergeleitet. Ihr Unternehmen muss sicherstellen, dass der zurückkommende Datenverkehr im Zusammenhang mit diesen Verbindungen über die ExpressRoute-Leitung geleitet wird (Vermeiden asymmetrischen Routings).


> [!NOTE]
> Da Ihr Unternehmen den Exchange ActiveSync-Namespace den angekündigten Präfixen in der ExpressRoute-Leitung hinzufügt, kann der Exchange ActiveSync-Endpunkt nur noch über die ExpressRoute erreicht werden. Somit ist Outlook für iOS und Android das einzige Mobilgerät, das eine Verbindung mit der lokalen Umgebung über den ActiveSync-Namespace herstellen kann. Alle anderen ActiveSync-Clients (z. B. native E-Mail-Clients mobiler Geräte) werden nicht mit der lokalen Umgebung verbunden, da von der Microsoft-Cloud keine Verbindung hergestellt wird. Der Grund ist, dass es keine Überlappungen des öffentlichen IP-Adressraums, der Microsoft auf der ExpressRoute-Leitung angekündigt wurde, mit dem öffentlichen IP-Adressraum, der auf Ihren Internetleitungen angekündigt wurde, geben kann.



**F:**  Wenn nur Nachrichtendaten von vier Wochen mit Exchange Online synchronisiert werden, bedeutet das, dass in Outlook für iOS und Android ausgeführte Suchabfragen keine Informationen über die Daten auf dem lokalen Gerät hinaus zurückgeben können?

**A:**  Wenn eine Suchabfrage in Outlook für iOS und Android ausgeführt wird, werden der Suchabfrage entsprechende Elemente zurückgegeben, wenn Sie sich auf dem Gerät befinden. Darüber hinaus wird die Suchabfrage über Exchange Online an das lokale Exchange übergeben. Das lokale Exchange führt die Suchabfrage für das lokale Postfach aus und gibt die Ergebnisse an Exchange Online zurück, das die Ergebnisse an den Client weiterleitet. Die lokalen Abfrageergebnisse werden in Exchange Online einen Tag lang gespeichert und anschließend gelöscht.

**F:**  Wie kann ich feststellen, ob das E-Mail-Konto ordnungsgemäß in Outlook für iOS und Android hinzugefügt wurde?

**A:**  Lokale Postfächer, die über moderne Hybridauthentifizierung hinzugefügt werden, sind in den Kontoeinstellungen in Outlook für iOS und Android als **Exchange (Hybrid)** gekennzeichnet, ähnlich wie im folgenden Beispiel:

![Ein Beispiel für ein Outlook für iOS- und Android-Konto, das für die moderne Hybridauthentifizierung konfiguriert ist.](images/Mt846639.79887a65-e5e1-4501-a274-008393dbb6c9(EXCHG.150).png "Ein Beispiel für ein Outlook für iOS- und Android-Konto, das für die moderne Hybridauthentifizierung konfiguriert ist.")

## Häufig gestellte Fragen zur Authentifizierung

**F:**  Welche Identitätskonfigurationen werden mit moderner Hybridauthentifizierung und Outlook für iOS und Android unterstützt?

**A:**  Die folgenden Identitätskonfigurationen in Azure Active Directory werden mit moderner Hybridauthentifizierung unterstützt:

  - Verbundidentität mit jedem lokalen Identitätsanbieter, der von Azure Active Directory unterstützt wird

  - Kennworthashsynchronisierung über Azure Active Directory Connect

  - Pass-Through-Authentifizierung über Azure Active Directory Connect

**F.:**  Welche Authentifizierungsmethode wird für Outlook für iOS und Android verwendet? Werden Anmeldeinformationen in Office 365 gespeichert?

**A.**:Outlook für iOS und Android nutzt die ADAL (Active Directory Authentication Library)-basierte Authentifizierung für den Zugriff auf die lokalen Postfachdaten, die mit Exchange Online synchronisiert werden. Bei der ADAL-Authentifizierung, die von Office-Apps sowohl auf Desktopgeräten als auch auf mobilen Geräten verwendet wird, meldet sich der Benutzer direkt beim Office 365-Identitätsanbieter (Azure Active Directory) an, statt seine Anmeldeinformationen in Outlook einzugeben.

Die ADAL-basierte Anmeldung ermöglicht die Nutzung von OAuth für lokale Exchange-Hybridkonten und stellt gleichzeitig einen sicheren Mechanismus bereit, über den Outlook für iOS und Android Zugriff auf E-Mails erhält, ohne selbst auf Benutzeranmeldeinformationen zugreifen zu müssen. Der Benutzer authentifiziert sich bei der Anmeldung unmittelbar bei der Microsoft-Cloud und erhält ein Zugriffstoken. Dieses Token gewährt Outlook für iOS und Android Zugriff auf das entsprechende Postfach. OAuth stellt einen sicheren Mechanismus bereit, über den Outlook ohne Benutzeranmeldeinformationen auf Office 365 und den Outlook-Clouddienst zugreifen kann.

Weitere Informationen finden Sie im Office-Blogbeitrag [Neue Zugriffs- und Sicherheitssteuerelemente für Outlook für iOS und Android](https://blogs.office.com/2015/06/10/new-access-and-security-controls-for-outlook-for-ios-and-android/).

**F.:**  Unterstützen Outlook für iOS und Android und andere mobile Microsoft Office-Apps einmaliges Anmelden?

**A.:**  Alle Microsoft-Apps, die die Active Directory-Authentifizierungsbibliothek (ADAL) für die Authentifizierung nutzen, unterstützen einmaliges Anmelden. Darüber hinaus wird einmaliges Anmelden auch unterstützt, wenn die Apps in Verbindung mit dem Microsoft Authenticator oder mit Apps des Microsoft-Unternehmensportals verwendet werden.

Token können freigegeben und von anderen Microsoft-Apps (z. B. Word Mobile) in den folgenden Szenarien wiederverwendet werden:

1.  Wenn die Apps von demselben Signaturzertifikat signiert werden und denselben Dienstendpunkt oder dieselbe Zielgruppen-URL (z.B. die Office 365-URL) verwenden. In diesem Fall wird das Token im freigegebenen App-Speicher gespeichert.

2.  Wenn die Apps einmaliges Anmelden mit einer Broker-App nutzen oder unterstützen. Die Token werden innerhalb der Broker-App gespeichert. Microsoft Authenticator ist ein Beispiel für eine Broker-App. Im Broker-App-Szenario startet ADAL, nachdem Sie versucht haben, sich bei Outlook für iOS und Android anzumelden, die Microsoft Authenticator-App, die eine Verbindung zu Azure Active Directory zum Abrufen des Tokens herstellt. Dann wird das Token gespeichert und erneut für Authentifizierungsanforderungen von anderen Apps verwendet, solange die konfigurierte Token-Gültigkeitsdauer dies zulässt.

Weitere Informationen finden Sie unter [Gewusst wie: Aktivieren von App-übergreifendem SSO unter iOS mit ADAL](https://docs.microsoft.com/de-de/azure/active-directory/develop/active-directory-sso-ios).

**F.:**  Was ist die Gültigkeitsdauer der Token, die von der Active Directory-Authentifizierungsbibliothek (ADAL) in Outlook für iOS und Android generiert und verwendet werden?

**A:**  Es werden mehrere Token generiert, wenn sich ein lokaler Benutzer über ADAL-aktivierte Apps wie Outlook für iOS und Android, die Authenticator-App oder die Unternehmensportal-App authentifiziert. Das erste Zugriffs- und Aktualisierungstokenpaar wird zum Zugriff auf die Daten verwendet, die in Exchange Online synchronisiert werden. Das zweite Zugriffs- und Aktualisierungstokenpaar wird von Exchange Online zum Zugriff auf das lokale Postfach über das Exchange ActiveSync-Protokoll verwendet. Das Zugriffstoken wird zum Zugreifen auf die Ressource (z. B. Exchange-Nachrichtendaten) verwendet, wohingegen ein Aktualisierungstoken zum Abrufen eines neuen Zugriffs- oder Aktualisierungstokenpaars verwendet wird, wenn das aktuelle Zugriffstoken abläuft.

Standardmäßig beträgt die Gültigkeitsdauer des Zugriffstoken eine Stunde und die des Aktualisierungstokens 14 Tage. Diese Werte können angepasst werden: Weitere Informationen finden Sie unter [Konfigurierbare Tokengültigkeitsdauern in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes). Wenn diese Gültigkeitsdauern reduziert werden sollen, beachten Sie, dass möglicherweise auch die Leistung von Outlook für iOS und Android reduziert wird, da durch eine kürzere Gültigkeitsdauer die Anzahl von Versuchen erhöht wird, die die Anwendung zum Abrufen eines frischen Tokens benötigt.

**F.:**  Was geschieht mit dem Zugriffstoken, wenn das Kennwort eines Benutzers geändert wird?

**A:**  Ein zuvor gewährtes Zugriffstoken ist gültig, bis es abläuft. Das Identitätsmodell, das Sie für die Authentifizierung nutzen, hat Einfluss darauf, wie der Kennwortablauf behandelt wird. Es gibt drei Szenarien:

1.  Bei einem Verbundidentitätsmodell müssen Sie sicherstellen, dass Ihr lokaler Identitätsanbieter Kennwortablaufansprüche an Azure Active Directory sendet, andernfalls kann Azure Active Directory nicht auf den Ablauf von Kennwörtern reagieren. Weitere Informationen finden Sie unter [Konfigurieren von AD FS zum Senden von Kennwortablaufansprüchen](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/configure-ad-fs-to-send-password-expiry-claims).

2.  Die Kennworthashsynchronisierung unterstützt den Ablauf von Kennwörtern nicht. Dies bedeutet, dass Apps, die zuvor ein Zugriffs- und Aktualisierungstokenpaar erhalten haben, weiter funktionieren, bis die Lebensdauer des Tokenpaars überschritten wird oder der Benutzer sein Kennwort ändert. Weitere Informationen finden Sie unter [Implementieren der Kennworthashsynchronisierung mit der Azure AD Connect-Synchronisierung](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-implement-password-hash-synchronization#how-password-synchronization-works).

3.  Die Pass-Through-Authentifizierung erfordert, dass das Kennwortrückschreiben in AAD Connect aktiviert ist. Weitere Informationen finden Sie unter [Azure Active Directory-Passthrough-Authentifizierung: Häufig gestellte Fragen](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication-faq#what-happens-if-my-users-password-has-expired-and-they-try-to-sign-in-by-using-pass-through-authentication).

Bei Ablauf des Tokens versucht der Client, das Aktualisierungstoken zu verwenden, um ein neues Zugriffstoken abzurufen, aber da sich das Kennwort des Benutzers geändert hat, wird das Aktualisierungstoken ungültig gemacht (unter der Voraussetzung, dass die Verzeichnissynchronisierung zwischen lokal und Azure Active Directory stattgefunden hat). Das ungültige Aktualisierungstoken erzwingt, dass der Benutzer sich erneut authentifiziert, um ein neues Zugriffstoken- und Aktualisierungstokenpaar abzurufen.

**F:**  Gibt es eine Möglichkeit für einen Benutzer, beim Hinzufügen seines Kontos zu Outlook für iOS und Android AutoDetect zu umgehen?

**A:**  Ja, ein Benutzer kann AutoDetect jederzeit umgehen und die Verbindung mit der Standardauthentifizierung über das Exchange ActiveSync-Protokoll manuell konfigurieren. Um sicherzustellen, dass der Benutzer keine Verbindung mit Ihrer lokalen Umgebung über einen Mechanismus herstellt, der Azure Active Directory-Richtlinien für bedingten Zugriff oder Intune-App-Schutzrichtlinien nicht unterstützt, muss der lokale Exchange-Administrator eine Exchange-Gerätezugriffsregel konfigurieren, die die ActiveSync-Verbindung blockiert. Geben Sie hierzu den folgenden Befehl in der Exchange-Verwaltungsshell ein:

``` 
 New-ActiveSyncDeviceAccessRule -Characteristic DeviceModel -QueryString "Outlook for iOS and Android" -AccessLevel Block
```

