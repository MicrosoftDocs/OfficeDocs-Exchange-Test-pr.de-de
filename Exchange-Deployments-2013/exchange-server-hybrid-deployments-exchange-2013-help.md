---
title: 'Hybridbereitstellungen in Exchange Server: Exchange 2013 Help'
TOCTitle: '@NoTitle'
ms:assetid: 59e32000-4fcf-417f-a491-f1d8f9aeef9b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ200581(v=EXCHG.150)
ms:contentKeyID: 50477182
ms.date: 05/05/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hybridbereitstellungen in Exchange Server

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2018-04-16_

**Zusammenfassung:** Wissenswertes zum Planen einer Exchange-Hybridbereitstellung

Eine Hybridbereitstellung bietet Unternehmen die Möglichkeit, die Funktionsvielfalt und die Verwaltungskontrolle, die die vorhandene lokale Microsoft Exchange-Organisation bietet, auf die Cloud auszudehnen. Eine Hybridbereitstellung bietet für eine lokale Exchange-Organisation und Exchange Online in Microsoft Office 365 ein einheitliches Erscheinungsbild als nahtlose Exchange-Organisation. Darüber hinaus kann eine Hybridbereitstellung als Zwischenschritt vor dem vollständigen Wechsel zu einer Exchange Online-Organisation dienen.

**Inhalt**

Features einer Exchange-Hybridbereitstellung

Überlegungen zur Exchange-Hybridbereitstellung

Komponenten einer Exchange-Hybridbereitstellung

Beispiel für eine Exchange-Hybridbereitstellung

Wichtige Überlegungen vor der Konfiguration einer Exchange-Hybridbereitstellung

Wichtige Terminologie

Dokumentation zur Exchange-Hybridbereitstellung

## Features einer Exchange-Hybridbereitstellung

Eine Hybridbereitstellung bietet die folgenden Funktionen:

  - Sicheres E-Mail-Routing zwischen lokalen und Exchange Online-Organisationen.

  - E-Mail-Routing mit einem freigegebenen Domänennamespace. Beispielsweise verwenden sowohl lokale als auch Exchange Online-Organisationen die SMTP-Domäne "@contoso.com".

  - Eine einheitliche globale Adressliste (GAL), auch als „freigegebenes Adressbuch“ bezeichnet.

  - Austausch von Frei/Gebucht- und Kalenderinformationen zwischen lokalen und Exchange Online-Organisationen.

  - Zentrale Steuerung des eingehenden und ausgehenden Nachrichtenflusses. Sie können alle eingehenden und ausgehenden Exchange Online-Nachrichten über die lokale Exchange-Organisation routen.

  - Eine einzelne Outlook im Web-URL für die lokale und die Exchange Online-Organisation.

  - Möglichkeit zum Verschieben vorhandener lokaler Postfächer in die Exchange Online-Organisation. Exchange Online-Postfächer können bei Bedarf auch in die lokale Organisation zurückverschoben werden.

  - Zentrale Postfachverwaltung über die lokale Exchange-Verwaltungskonsole.

  - Nachrichtenverfolgung, E-Mail-Infos und Suche in mehreren Postfächern in der lokalen und der Exchange Online-Organisation.

  - Cloudbasierte Nachrichtenarchivierung für lokale Exchange-Postfächer. Die Exchange Online-Archivierung kann mit einer Hybridbereitstellung verwendet werden. Weitere Informationen zur Exchange Online-Archivierung finden Sie unter [Weitere Microsoft Office 365-Dienste](https://go.microsoft.com/fwlink/p/?linkid=233231).

## Überlegungen zur Exchange-Hybridbereitstellung

Ziehen Sie vor der Implementierung einer Exchange-Hybridbereitstellung folgende Überlegungen in Betracht:

  - **Anforderungen an Hybridbereitstellungen** Bevor Sie eine Hybridbereitstellung konfigurieren, müssen Sie sicherstellen, dass die lokale Organisation alle Voraussetzungen erfüllt, die für eine erfolgreiche Bereitstellung erforderlich sind. Weitere Informationen finden Sie unter [Voraussetzungen für die Hybridbereitstellung](hybrid-deployment-prerequisites-exchange-2013-help.md).

  - **Exchange ActiveSync-Clients**   Wenn Sie ein Postfach aus Ihrer lokalen Exchange-Organisation zu Exchange Online verschieben, müssen alle auf das Postfach zugreifenden Clients aktualisiert werden, um Exchange Online verwenden zu können. Dazu zählen auch Exchange ActiveSync-Geräte. Die meisten Exchange ActiveSync-Clients werden inzwischen automatisch erneut konfiguriert, wenn das Postfach zu Exchange Online verschoben wird. Einige ältere Geräte werden aber möglicherweise nicht ordnungsgemäß aktualisiert. Weitere Informationen finden Sie unter [Exchange ActiveSync-Geräteeinstellungen mit Exchange-Hybridbereitstellungen](exchange-activesync-device-settings-with-exchange-hybrid-deployments-exchange-2013-help.md).

  - **Migration von Postfachberechtigungen** Lokale Postfachberechtigungen wie „Senden als“, „Vollzugriff“,“Senden im Auftrag von“ und Ordnerberechtigungen, die explizit für das Postfach gelten, werden zu Exchange Online migriert. Geerbte (nicht explizite) Postfachberechtigungen und Berechtigungen, die Objekten gewährt wurden, die in Exchange Online nicht E-Mail-aktiviert sind, werden nicht migriert. Sie sollten vor der Migration sicherstellen, dass alle Berechtigungen explizit gewährt werden und dass alle Objekte E-Mail-aktiviert sind. Aus diesem Grund müssen Sie die Konfiguration dieser Berechtigungen bei Bedarf in Office 365 planen. Im Falle der Berechtigung „Senden als“ müssen Sie diese explizit in Exchange Online mithilfe des Cmdlets **Add-RecipientPermission** hinzufügen, wenn der Benutzer und die Ressource für „Senden als“ nicht gleichzeitig verschoben werden.

  - **Unterstützung von standortübergreifenden Postfachberechtigungen** Von Exchange-Hybridbereitstellungen wird die Verwendung der Postfachberechtigungen „Vollzugriff“ und „Senden im Auftrag von“ zwischen Postfächern in einer lokalen Exchange-Organisation und Postfächern in Office 365 unterstützt. Für die Berechtigungen „Senden als“ sind zusätzliche Schritte erforderlich. Außerdem ist in Abhängigkeit von der in Ihrer lokalen Organisation installierten Exchange-Version eine zusätzliche Konfiguration erforderlich, damit standortübergreifende Postfachberechtigungen unterstützt werden. Weitere Informationen finden Sie unter [Delegieren von Berechtigungen für Postfächer](permissions-in-exchange-hybrid-deployments-exchange-2013-help.md) in [Berechtigungen in Exchange-Hybridbereitstellungen](permissions-in-exchange-hybrid-deployments-exchange-2013-help.md) und in [Konfigurieren von Exchange für delegierte Postfachberechtigungen in einer Hybridbereitstellung](configure-exchange-to-support-delegated-mailbox-permissions-in-a-hybrid-deployment-exchange-2013-help.md).
    

    > [!NOTE]
    > Ab Februar 2018 wird das Feature für die Unterstützung von „Vollzugriff“, „Senden im Auftrag von“ und strukturübergreifenden Ordnerrechten eingeführt und voraussichtlich im April 2018 abgeschlossen.



  - **Offboarding** Im Rahmen der laufenden Empfängerverwaltung müssen Sie ggf. Exchange Online-Postfächer zurück in die lokale Umgebung verschieben.
    
    Weitere Informationen darüber, wie Sie Postfächer in einer Exchange 2010-basierten Hybridbereitstellung verschieben, finden Sie unter[Verschieben eines Exchange Online-Postfachs in die lokale Organisation](https://technet.microsoft.com/de-de/library/hh882527\(v=exchg.150\)).
    
    Weitere Informationen zum Verschieben von Postfächern in Hybridbereitstellungen basierend auf Exchange 2013 oder neuer finden Sie unter [Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen](move-mailboxes-between-on-premises-and-exchange-online-organizations-in-hybrid-deployments-exchange-2013-help.md).

  - **Einstellungen der Postfachweiterleitung** Postfächer können automatisch so eingerichtet werden, dass sie E-Mails automatisch an ein anderes Postfach weiterleiten. Obwohl die Postfachweiterleitung in Exchange Online unterstützt wird, wird die Konfiguration für die Weiterleitung nicht zu Exchange Online kopiert, wenn das Postfach dorthin migriert wird. Bevor Sie ein Postfach zu Exchange Online migrieren, exportieren Sie die Konfiguration für die Weiterleitung für jedes Postfach. Die Weiterleitungskonfiguration ist in den `DeliverToMailboxAndForward`-, `ForwardingAddress`- und `ForwardingSmtpAddress`-Eigenschaften eines Postfachs gespeichert.

## Komponenten einer Exchange-Hybridbereitstellung

Eine Hybridbereitstellung umfasst verschiedene Dienste und Komponenten:

  - **Exchange-Server** Mmindestens ein Exchange-Server muss in Ihrer lokalen Organisation konfiguriert werden, wenn Sie eine Hybridbereitstellung konfigurieren möchten. Wenn Sie Exchange 2013 oder älter ausführen, müssen Sie mindestens einen Server mit den Postfach- und Clientzugriffsrollen installieren. Wenn Sie Exchange 2016 oder neuer ausführen, muss mindestens einen Server mit der Postfachrolle installiert werden. Bei Bedarf können Exchange-Edge-Transport-Server auch in einem Umkreisnetzwerk installiert werden und den sicheren E-Mail-Fluss mit Office 365 unterstützen.
    

    > [!NOTE]
    > Die Installation von Exchange-Servern mit den Postfach- oder Clientzugriffsserverrollen in einem Umkreisnetzwerk werden nicht unterstützt.



  - **Microsoft Office 365**   Der Office 365-Dienst umfasst im Rahmen des Abonnementdiensts eine Exchange Online-Organisation. Organisationen, die eine Hybridbereitstellung konfigurieren, müssen eine Lizenz für jedes Postfach erwerben, in das migriert wird oder das in der Exchange Online-Organisation erstellt wird.

  - **Assistent für die Hybridkonfiguration**Exchange enthält einen Assistenten für die Hybridkonfiguration, der Ihnen einen optimierten Prozess zum Konfigurieren einer Hybridbereitstellung mit lokalen Exchange- und Exchange Online-Organisationen bietet.
    
    Weitere Informationen finden Sie unter [Assistent für die Hybridkonfiguration](hybrid-configuration-wizard-exchange-2013-help.md).

  - **Azure AD-Authentifizierungssystem**   Das Azure Active Directory-Authentifizierungssystem ist ein kostenloser, cloudbasierter Dienst, der als Vertrauensbroker zwischen der lokalen Exchange 2016-Organisation und der Exchange Online-Organisation fungiert. Lokale Organisationen, die eine Hybridbereitstellung konfigurieren, müssen eine Verbundvertrauensstellung mit dem Windows Azure AD-Authentifizierungssystem einrichten. Die Verbundvertrauensstellung kann manuell während der Konfiguration von Verbundfreigabefeatures zwischen einer lokalen Exchange-Organisation und anderen Exchange-Verbundorganisationen oder während der Konfiguration einer Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration erstellt werden. Eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem wird automatisch für Ihren Office 365-Mandanten konfiguriert, wenn Sie Ihr Office 365-Dienstkonto aktivieren.
    
    Weitere Informationen finden Sie unter [Azure AD-Authentifizierungssystem](https://go.microsoft.com/fwlink/p/?linkid=135986).

  - **Azure Active Directory-Synchronisierung**   Bei der Azure AD-Synchronisierung werden mithilfe von Azure AD Connect lokale Active Directory-Informationen für E-Mail-aktivierte Objekte in die Office 365-Organisation repliziert, um die einheitliche globale Adressliste (GAL) und die Benutzerauthentifizierung zu unterstützen. Organisationen, die eine Hybridbereitstellung konfigurieren, müssen Azure AD Connect auf einem separaten, lokalen Server bereitstellen, um das lokale Active Directory mit Office 365 zu synchronisieren.
    
    Weitere Informationen finden Sie unter: [Azure AD Connect - Übersicht](https://go.microsoft.com/fwlink/p/?linkid=203007)

Wichtige Terminologie

## Beispiel für eine Hybridbereitstellung

Sehen Sie sich das folgende Szenario an. Hierbei handelt es sich um eine Beispieltopologie, die einen Überblick über eine typische Exchange 2016-Bereitstellung bietet. Contoso, Ltd. ist eine Organisation mit einer Gesamtstruktur, einer Domäne und zwei Domänencontrollern sowie einem Exchange 2016-Server. Contoso-Remotebenutzer verwenden Outlook im Web, um über das Internet eine Verbindung mit Exchange 2016 herzustellen, ihre Postfächer zu überprüfen und auf ihren Outlook-Kalender zuzugreifen.

![Lokale Exchange-Bereitstellung vor der Hybridbereitstellung mit Office 365 konfiguriert](images/JJ200581.dad133ae-d18a-42ec-8f0a-dd1de391200e(EXCHG.150).png "Lokale Exchange-Bereitstellung vor der Hybridbereitstellung mit Office 365 konfiguriert")

Angenommen, Sie sind der Netzwerkadministrator für Contoso und möchten eine Hybridbereitstellung konfigurieren. Sie stellen einen erforderlichen Azure AD Connect-Server bereit, konfigurieren ihn und möchten das Azure AD Connect-Kennwortsynchronisierungsfeature verwenden, damit Benutzer die gleichen Anmeldeinformationen für das lokale Netzwerkkonto und für das Office 365-Konto verwenden können. Nachdem Sie die Voraussetzungen für die Hybridbereitstellung erfüllt haben und mit dem Assistenten für die Hybridkonfiguration Optionen für die Hybridbereitstellung ausgewählt haben, sieht die Konfiguration der neuen Topologie wie folgt aus:

  - Benutzer verwenden die gleichen Anmeldeinformationen bestehend aus Benutzername und Kennwort für die Anmeldung bei der lokalen und der Exchange Online-Organisation („einmaliges Anmelden“).

  - Die lokal und in der Exchange Online-Organisation befindlichen Postfächer verwenden dieselbe E-Mail-Adressdomäne. Zum Beispiel verwenden Postfächer in der lokalen Organisation und Postfächer in der Exchange Online-Organisation beide "@contoso.com" in den E-Mail-Adressen der Benutzer.

  - Alle ausgehenden E-Mails von der lokalen Organisation an das Internet zugestellt. Die lokale Organisation steuert den gesamten Nachrichtentransport und dient als Relay für die Exchange Online-Organisation ("zentraler E-Mail-Transport").

  - Benutzer der lokalen und der Exchange Online-Organisation können einander die Frei/Gebucht-Informationen in ihrem Kalender freigeben. Die für beide Organisationen konfigurierten Organisationsbeziehungen ermöglichen zudem die standortübergreifende Nachrichtenverfolgung, E-Mail-Infos und die Nachrichtensuche.

  - Lokale und Exchange Online-Benutzer verwenden dieselbe URL zum Herstellen einer Verbindung mit ihren Postfächern über das Internet.

![Lokale Exchange-Bereitstellung nach der Hybridbereitstellung mit Office 365 konfiguriert](images/JJ200581.e8681849-f15d-4d0e-b77e-6105b6096c4b(EXCHG.150).png "Lokale Exchange-Bereitstellung nach der Hybridbereitstellung mit Office 365 konfiguriert")

Wenn Sie die vorhandene Organisationskonfiguration von Contoso mit der Konfiguration der hybriden Bereitstellung vergleichen, stellen Sie fest, dass bei der Konfiguration der hybriden Bereitstellung Server und Dienste hinzugefügt wurden, welche die zusätzliche Kommunikation und die Features unterstützen, die von der lokalen und der Exchange Online-Organisation gemeinsam genutzt werden. Im Folgenden erhalten Sie einen Überblick über die Änderungen, die für die Hybridbereitstellung an der anfänglichen lokalen Exchange-Organisation vorgenommen wurden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Konfiguration</th>
<th>Vor der Hybridbereitstellung</th>
<th>Nach der Hybridbereitstellung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Speicherort des Postfachs</p></td>
<td><p>Nur lokale Postfächer.</p></td>
<td><p>Lokale und Office 365-Postfächer.</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtentransport</p></td>
<td><p>Lokale Postfachserver verarbeiten das gesamte Routing eingehender und ausgehender Nachrichten.</p></td>
<td><p>Lokale Postfachserver verarbeiten das interne Nachrichtenrouting zwischen der lokalen und der Office 365-Organisation.</p></td>
</tr>
<tr class="odd">
<td><p>Outlook im Web</p></td>
<td><p>Lokale Postfachserver empfangen alle Outlook im Web-Anforderungen und zeigen Postfachinformationen an.</p></td>
<td><p>Lokale Postfachserver leiten Outlook im Web-Anforderungen entweder an die lokalen Exchange 2016-Postfachserver weiter oder stellen einen Link zur Anmeldung bei Office 365 bereit.</p></td>
</tr>
<tr class="even">
<td><p>Einheitliche GAL (globale Adressliste) für beide Organisationen</p></td>
<td><p>Nicht zutreffend; nur einzelne Organisation.</p></td>
<td><p>Der lokale Active Directory-Synchronisierungsserver repliziert Active Directory-Informationen für E-Mail-aktivierte Objekte in Office 365.</p></td>
</tr>
<tr class="odd">
<td><p>Einmaliges Anmelden wird für beide Organisationen verwendet</p></td>
<td><p>Nicht zutreffend; nur einzelne Organisation.</p></td>
<td><p>Das lokale Active Directory und Office 365 verwenden den gleichen Benutzernamen und das gleiche Kennwort für lokale und für Office 365-Postfächer.</p></td>
</tr>
<tr class="even">
<td><p>Organisationsbeziehung und eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem werden hergestellt</p></td>
<td><p>Die Vertrauensstellung mit dem Azure AD-Authentifizierungssystem und Organisationsbeziehungen mit anderen Exchange-Verbundorganisationen können konfiguriert werden.</p></td>
<td><p>Eine Vertrauensstellung mit dem Azure AD-Authentifizierungssystem ist erforderlich. Organisationsbeziehungen werden zwischen der lokalen und der Office 365-Organisation hergestellt.</p></td>
</tr>
<tr class="odd">
<td><p>Freigabe von Frei/Gebucht-Informationen</p></td>
<td><p>Freigabe von Frei/Gebucht-Informationen nur zwischen lokalen Benutzern.</p></td>
<td><p>Freigabe von Frei/Gebucht-Informationen zwischen lokalen und Office 365-Benutzern.</p></td>
</tr>
</tbody>
</table>


## Wichtige Überlegungen vor der Konfiguration einer Hybridbereitstellung

Da Sie nun ein wenig mit dem Konzept einer Hybridbereitstellung vertraut sind, sollten Sie einige wichtige Aspekte genauer untersuchen. Die Konfiguration einer Hybridbereitstellung kann sich auf verschiedene Bereiche innerhalb des aktuellen Netzwerks und innerhalb der aktuellen Exchange-Organisation auswirken.

## Verzeichnissynchronisierung und einmaliges Anmelden

Die Active Directory-Synchronisierung zwischen den lokalen und den Office 365-Organisationen, die alle drei Stunden von einem Server mit Azure Active Directory Connect ausgeführt wird, ist eine Voraussetzung für das Konfigurieren einer Hybridbereitstellung. Die Verzeichnissynchronisierung ermöglicht Empfängern in jeder Organisation die gegenseitige Anzeige in der globalen Adressliste. Außerdem werden Benutzernamen und Kennwörter synchronisiert, sodass sich die Benutzer mit denselben Anmeldeinformationen an der lokalen und der Office 365-Organisation anmelden können.


> [!NOTE]
> Wenn Sie Azure AD Connect mit AD FS konfigurieren, werden Benutzernamen und Kennwörter lokaler Benutzer standardmäßig weiterhin mit Office 365 synchronisiert. Benutzer authentifizieren sich allerdings als primäre Methode der Authentifizierung mit Ihrem lokalen Active Directory über AD FS. Für den Fall, dass AD FS aus irgendeinem Grund keine Verbindung mit Ihrem lokalen Active Directory herstellen kann, versuchen Clients, die Authentifizierung über Benutzernamen und Kennwörter durchzuführen, die mit Office 365 synchronisiert werden.



Für alle Kunden von Azure Active Directory und Office 365 gilt eine maximale Anzahl von 50.000 Objekten (Benutzer, E-Mail-aktivierte Kontakte und Gruppen). Dieser Grenzwert legt fest, wie viele Objekte Sie in Ihrer Office 365-Organisation erstellen können. Beim Überprüfen Ihrer ersten Domäne wird dieser Objektgrenzwert automatisch auf 300.000 Objekte erhöht. In folgenden Fällen müssen Sie sich an den Azure Active Directory-Support wenden, um eine Erhöhung der Objektkontingentgrenze zu bitten: Wenn Sie eine Domäne überprüft haben und mehr als 300.000 Objekte synchronisieren müssen oder wenn Sie keine Domänen überprüfen und mehr als 50.000 Objekte synchronisieren müssen.

Zusätzlich zu einem Server mit Azure AD Connect müssen Sie auch einen Webanwendungs-Proxyserver bereitstellen, wenn Sie AD FS konfigurieren möchten. Dieser Server sollte in Ihrem Umkreisnetzwerk platziert werden und als Vermittler zwischen Ihrem internen Azure AD Connect-Server und dem Internet fungieren. Der Webanwendungs-Proxyserver muss Verbindungen von Clients und Servern über das Internet mit TCP-Port 443 akzeptieren.

## Verwaltung der Hybridbereitstellung

Sie verwalten eine Hybridbereitstellung in Exchange 2016 über eine einzige einheitliche Verwaltungskonsole, mit der Sie die lokale und die Exchange Online-Organisation verwalten können. Die *Exchange-Verwaltungskonsole* (Exchange Administration Center, EAC) ersetzt die frühere Exchange-Verwaltungskonsole (Exchange Management Console, EMC) und die Exchange-Systemsteuerung, und Sie können damit eine Verbindung herstellen und Funktionen für beide Organisationen konfigurieren. Wenn Sie den Assistenten für die Hybridkonfiguration zum ersten Mal ausführen, werden Sie aufgefordert, eine Verbindung zur Exchange Online-Organisation herzustellen. Sie müssen ein Office 365-Konto verwenden, das Mitglied der Rollengruppe „Organisationsverwaltung“ ist, um die Exchange-Verwaltungskonsole mit Ihrer Exchange Online-Organisation zu verbinden.

## Zertifikate

Digitale SSL-Zertifikate (Secure Sockets Layer) spielen bei der Konfiguration einer Hybridbereitstellung eine wichtige Rolle. Sie sichern die Kommunikation zwischen dem lokalen Hybridserver und der Exchange Online-Organisation. Zertifikate sind erforderlich, um mehrere Arten von Diensten zu konfigurieren. Wenn Sie in Ihrer Exchange-Organisation bereits digitale Zertifikate einsetzen, müssen Sie die Zertifikate möglicherweise auf weitere Domänen erweitern oder zusätzliche Zertifikate von einer vertrauenswürdigen Zertifizierungsstelle erwerben. Wenn Sie noch keine Zertifikate verwenden, müssen Sie ein oder mehrere Zertifikate von einer vertrauenswürdigen Zertifizierungsstelle erwerben.

Weitere Informationen finden Sie unter: [Zertifikatanforderungen für Hybridbereitstellungen](certificate-requirements-for-hybrid-deployments-exchange-2013-help.md)

## Bandbreite

Ihre Netzwerkverbindung mit dem Internet besitzt direkte Auswirkungen auf die Kommunikationsleistung zwischen der lokalen und der Office 365-Organisation. Dies gilt vor allem dann, wenn Postfächer von Ihrem lokalen Exchange 2016-Server in die Office 365-Organisation verschoben werden. Der erforderliche Zeitraum für die Durchführung von Postfachverschiebungen hängt von der verfügbaren Netzwerkbandbreite sowie von der Postfachgröße und der Anzahl der gleichzeitig verschobenen Postfächer ab. Außerdem können sich auch andere Office 365-Dienste wie SharePoint Server 2016 und Skype for Business auf die Bandbreite auswirken, die für Nachrichtendienste zur Verfügung steht.

Vor dem Verschieben von Postfächern zu Office 365, sollten Sie folgende Aktionen ausführen:

  - Ermitteln Sie die durchschnittliche Postfachgröße der Postfächer, die zu Office 365 verschoben werden sollen.

  - Ermitteln Sie die durchschnittliche Verbindungs- und Durchsatzgeschwindigkeit für die Verbindung vom Internet zur lokalen Organisation.

  - Berechnen Sie durchschnittliche erwartete Übertragungsgeschwindigkeit, und planen Sie die Postfachverschiebungen entsprechend.

Weitere Informationen finden Sie unter: [Netzwerk](http://go.microsoft.com/fwlink/p/?linkid=280178)

## Unified Messaging

Unified Messaging (UM) wird in einer Hybridbereitstellung zwischen lokalen und Office 365-Organisationen unterstützt. Ihre lokale Telefonielösung sollte in der Lage sein, mit Office 365 zu kommunizieren. Dazu kann möglicherweise der Erwerb zusätzlicher Hardware und Software erforderlich sein.

Wenn Sie Postfächer von der lokalen Organisation zu Office 365 verschieben möchten und die Postfächer für UM konfiguriert sind, müssen Sie vor dem Verschieben der Postfächer UM in der Hybridbereitstellung konfigurieren. Wenn Sie Postfächer vor dem Konfigurieren von UM in der Hybridbereitstellung verschieben, haben diese Postfächer keinen Zugriff mehr auf UM-Funktionen.

Weitere Informationen finden Sie unter: [Einrichten von Unified Messaging in einer Hybridbereitstellung](https://go.microsoft.com/fwlink/p/?linkid=842271)

## Verwaltung von Informationsrechten

Die Verwaltung von Informationsrechten (Information Rights Management, IRM) ermöglicht Benutzern, auf von ihnen gesendete Nachrichten Active Directory RMS-Vorlagen (Active Directory Rights Management Services, AD RMS) anzuwenden. AD RMS-Vorlagen helfen, Informationsverluste zu verhindern, da Benutzer kontrollieren können, wer eine mit Rechten geschützte Nachricht öffnen und was er mit dieser Nachricht nach dem Öffnen tun kann.

In einer Hybridbereitstellung erfordert IRM die Planung und die manuelle Konfiguration der Office 365-Organisation sowie Kenntnisse darüber, wie Clients AD RMS-Server abhängig davon verwenden, ob sich das Postfach in der lokalen oder Exchange Online-Organisation befindet.

Weitere Informationen finden Sie unter: [IRM in Exchange-Hybridbereitstellungen](irm-in-exchange-hybrid-deployments-exchange-2013-help.md)

## Mobile Geräte

Mobile Geräte werden in einer Hybridbereitstellung unterstützt. Wenn Exchange ActiveSync bereits auf den vorhandenen Servern aktiviert ist, leiten sie Anforderungen von mobilen Geräten weiterhin an Postfächer auf dem lokalen Postfachserver um. Für mobile Geräte, die eine Verbindung mit vorhandenen Postfächern herstellen, die von der lokalen Organisation zu Office 365 verschoben werden, werden Exchange ActiveSync-Profile auf den meisten Telefonen automatisch für die Verbindung mit Office 365 aktualisiert. Alle mobilen Geräte, die Exchange ActiveSync unterstützen, sollten mit einer Hybridbereitstellung kompatibel sein.

Weitere Informationen finden Sie unter: [Mobiltelefone](http://go.microsoft.com/fwlink/p/?linkid=206387)

## Clientanforderungen

Es empfiehlt sich, auf den Clients Outlook 2016 oder Outlook 2013 einzusetzen, um in der Hybridbereitstellung ein optimales Benutzererlebnis und eine optimale Leistung zu erzielen. Clients vor Outlook 2010 werden in Hybridbereitstellungen oder mit Office 365 nicht unterstützt.

## Lizenzierung für Office 365

Zum Erstellen oder zum Verschieben von Postfächern in Office 365 müssen Sie sich bei Office 365 für Unternehmen anmelden und Lizenzen besitzen. Bei der Anmeldung für Office 365 erhalten Sie eine bestimmte Anzahl von Lizenzen, die Sie neuen Postfächern oder aus der lokalen Organisation verschobenen Postfächern zuordnen können. Jedes Postfach in Office 365 muss über eine Lizenz verfügen.

## Antivirus- und Antispamdienste

Postfächer, die zu Office 365 verschoben werden, erhalten automatisch einen Antivirus- und Antispamschutz durch Exchange Online Protection (EOP), ein von Office 365 bereitgestellter Dienst. Sie müssen möglicherweise zusätzliche EOP-Lizenzen für Ihre lokalen Benutzer erwerben, wenn Sie sich entscheiden, alle eingehenden Internet-E-Mails über den Exchange Online Protection-Dienst weiterzuleiten. Sie sollten sorgfältig überprüfen, ob der EOP-Schutz in Office 365 auch geeignet ist, um die Antivirus- und Antispamanforderungen Ihrer lokalen Organisation zu erfüllen. Wenn Sie über eine Lösung zum Schutz Ihrer lokalen Organisation verfügen, müssen Sie Ihre lokalen Antivirus- und Antispamlösungen möglicherweise aktualisieren oder konfigurieren, um einen maximalen Schutz für die gesamte Organisation zu bieten.

Weitere Informationen finden Sie unter: [Antispam- und Antischadsoftwareschutz](https://technet.microsoft.com/de-de/library/jj200731\(v=exchg.150\))

## Öffentliche Ordner

Öffentliche Ordner werden in Office 365 unterstützt, und lokale öffentliche Ordner können zu Office 365 migriert werden. Darüber hinaus können öffentliche Ordner in Office 365 in die lokale Exchange 2016-Organisation verschoben werden. Sowohl lokale als auch Office 365-Benutzer können auf öffentliche Ordner in beiden Organisation mithilfe von Outlook im Web, Outlook 2016, Outlook 2013 oder Outlook 2010 SP2 oder neuer zugreifen. Die vorhandene Konfiguration lokaler öffentlicher Ordner und der Zugriff für lokale Postfächer werden beim Konfigurieren einer Hybridbereitstellung nicht geändert.

Weitere Informationen finden Sie unter: [Öffentliche Ordner](https://technet.microsoft.com/de-de/library/jj150538\(v=exchg.150\))

## Barrierefreiheit

Informationen zu Tastenkombinationen für die Verfahren in dieser Prüfliste finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](https://technet.microsoft.com/de-de/library/jj150484\(v=exchg.150\)).

## Wichtige Terminologie

Die folgende Liste enthält Definitionen der wichtigsten Komponenten im Zusammenhang mit Hybridbereitstellungen in Exchange 2013.

  - **Zentraler E-Mail-Transport**  
    Die Option für die Hybridkonfiguration, bei der alle eingehenden und ausgehenden Exchange Online-Internetnachrichten über die lokale Exchange-Organisation geroutet werden. Diese Routingoption wird im Assistenten für die Hybridkonfiguration festgelegt. Weitere Informationen finden Sie unter [Transportoptionen in Exchange-Hybridbereitstellungen](transport-options-in-exchange-hybrid-deployments-exchange-2013-help.md).

<!-- end list -->

  - **Koexistenzdomäne**  
    Eine akzeptierte Domäne, die der lokalen Organisation für die hybride Nachrichtenübermittlung und die Verarbeitung von AutoErmittlungsanforderungen für den Office 365-Dienst hinzugefügt wird. Diese Domäne wird als sekundäre Proxydomäne zu allen E-Mail-Adressrichtlinien hinzugefügt, die über *PrimarySmtpAddress*-Vorlagen für Domänen verfügen, die im Assistenten für die Hybridkonfiguration ausgewählt wurden. In der Standardeinstellung ist das die Domäne "\<Domäne\>.mail.onmicrosoft.com".

<!-- end list -->

  - ***HybridConfiguration* Active Directory-Objekt**  
    Das Active Directory-Objekt in der lokalen Organisation, das die gewünschten Konfigurationsparameter für die Hybridbereitstellung enthält, die im Assistenten für die Hybridbereitstellung ausgewählt wurden. Das Hybridkonfigurationsmodul verwendet diese Parameter beim Konfigurieren der lokalen und Exchange Online-Einstellungen, um die Hybridfunktionen zu aktivieren. Die Inhalte des *HybridConfiguration*-Objekts werden bei jeder Ausführung des Assistenten für Hybridkonfigurationen zurückgesetzt.

<!-- end list -->

  - **Modul für die Hybridkonfiguration**  
    Das Modul für die Hybridkonfiguration (Hybrid Configuration Engine, HCE) führt die Hauptaktionen beim Konfigurieren und Aktualisieren einer Hybridbereitstellung aus. Das Hybridkonfigurationsmodul vergleicht den Status des Active Directory-Objekts *HybridConfiguration* mit den aktuellen lokalen Exchange- und Exchange Online-Konfigurationseinstellungen und führt anschließend Tasks aus, um die Konfigurationseinstellungen der Bereitstellung an die im Active Directory-Objekt *HybridConfiguration* definierten anzupassen. Weitere Informationen finden Sie unter [Hybrid Configuration Engine](hybrid-configuration-wizard-exchange-2013-help.md).

<!-- end list -->

  - **Assistent für die Hybridkonfiguration**  
    Ein mit Exchange bereitgestelltes anpassbares Tool, das Administratoren durch die Konfiguration einer Hybridbereitstellung zwischen den lokalen und den Exchange Online-Organisationen leitet. Der Assistent definiert die Konfigurationsparameter für die Hybridbereitstellung im Objekt *HybridConfiguration* und weist das Hybridkonfigurationsmodul an, die erforderlichen Konfigurationstasks zur Aktivierung der definierten Hybridfunktionen auszuführen. Weitere Informationen finden Sie unter [Assistent für die Hybridkonfiguration](hybrid-configuration-wizard-exchange-2013-help.md).

<!-- end list -->

  - **Exchange 2010-basierte Hybridbereitstellung**  
    Eine Hybridbereitstellung, die zur Verwendung von Service Pack 3 (SP3) für lokale Exchange Server 2010-Server konfiguriert ist, die als Verbindungsendpunkte für die Office 365- und Exchange Online-Dienste dienen. Eine Hybridbereitstellungsoption für lokale Exchange 2010-, Exchange Server 2007- und Exchange Server 2003-Organisationen.

<!-- end list -->

  - **Exchange 2013-basierte Hybridbereitstellung**  
    Eine Hybridbereitstellung, die zur Verwendung von lokalen Exchange Server 2013-Servern konfiguriert ist, die als Verbindungsendpunkte für die Office 365- und Exchange Online-Dienste dienen. Eine Hybridbereitstellungsoption für lokale Exchange 2013-, Exchange Server 2010- und Exchange Server 2007-Organisationen.

<!-- end list -->

  - **Exchange 2016-basierte Hybridbereitstellung**  
    Eine Hybridbereitstellung, die zur Verwendung von lokalen Exchange Server 2016-Servern konfiguriert ist, die als Verbindungsendpunkte für die Office 365- und Exchange Online-Dienste dienen. Eine Hybridbereitstellungsoption für lokale Exchange 2016-, Exchange Server 2013- und Exchange Server 2010-Organisationen.

<!-- end list -->

  - **Sicherer E-Mail-Transport**  
    Eine automatisch konfigurierte Funktion einer Hybridbereitstellung, die einen sicheren Nachrichtenverkehr zwischen den lokalen Organisationen und Exchange Online-Organisationen ermöglicht. Nachrichten werden mithilfe von TLS (Transport Layer Security) und einem im Assistenten für die Hybridkonfiguration ausgewählten Zertifikat verschlüsselt und authentifiziert. Der Office 365-Mandant ist der Endpunkt für Hybridtransportverbindungen mit Ursprung in der lokalen Organisation und die Quelle für Hybridtransportverbindungen, die von Exchange Online zur lokalen Organisation hergestellt werden.

Wichtige Terminologie

## Dokumentation zur Exchange-Hybridbereitstellung

Die folgende Tabelle enthält Links zu Themen, in denen Sie weitere Informationen zu Hybridbereitstellungen in Microsoft Exchange und deren Verwaltung erhalten.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Thema</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="hybrid-configuration-wizard-exchange-2013-help.md">Assistent für die Hybridkonfiguration</a></p></td>
<td><p>Weitere Informationen zur Konfiguration einer Hybridbereitstellung mit dem Assistenten für die Hybridkonfiguration und dem Modul für die Hybridkonfiguration.</p></td>
</tr>
<tr class="even">
<td><p><a href="hybrid-deployment-prerequisites-exchange-2013-help.md">Voraussetzungen für die Hybridbereitstellung</a></p></td>
<td><p>Weitere Informationen zu Voraussetzungen für eine Hybridbereitstellung, einschließlich kompatibler Exchange Server-Organisationen, Office 365-Anforderungen und weiterer lokaler Konfigurationsanforderungen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="certificate-requirements-for-hybrid-deployments-exchange-2013-help.md">Zertifikatanforderungen für Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zu Anforderungen für digitale Zertifikate in Hybridbereitstellungen.</p></td>
</tr>
<tr class="even">
<td><p><a href="transport-options-in-exchange-hybrid-deployments-exchange-2013-help.md">Transportoptionen in Exchange-Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zu Transportoptionen für eingehende und ausgehende Nachrichten in Hybridbereitstellungen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="transport-routing-in-exchange-hybrid-deployments-exchange-2013-help.md">Transportweiterleitung in Exchange-Hybrid-Bereitstellungen</a></p></td>
<td><p>Weitere Informationen zu Routingoptionen für eingehende und ausgehende Nachrichten in Hybridbereitstellungen.</p></td>
</tr>
<tr class="even">
<td><p><a href="hybrid-management-in-exchange-hybrid-deployments-exchange-2013-help.md">Hybridverwaltung in Exchange-Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zur Verwaltung einer Hybridbereitstellung mit der Exchange-Verwaltungskonsole und der Exchange-Verwaltungsshell.</p></td>
</tr>
<tr class="odd">
<td><p><a href="shared-free-busy-in-exchange-hybrid-deployments-exchange-2013-help.md">Freigegebene Frei/Gebucht-Informationen in Exchange-Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zur Freigabe von Frei/Gebucht-Kalenderinformationen zwischen lokalen und Exchange Online-Organisationen in einer Hybridbereitstellung.</p></td>
</tr>
<tr class="even">
<td><p><a href="server-roles-in-exchange-hybrid-deployments-exchange-2013-help.md">Serverrollen in Exchange-Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zur Funktionsweise von Exchange-Serverrollen in einer Hybridbereitstellung.</p></td>
</tr>
<tr class="odd">
<td><p><a href="irm-in-exchange-hybrid-deployments-exchange-2013-help.md">IRM in Exchange-Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zur Funktionsweise der Verwaltung von Informationsrechten in einer Hybridbereitstellung.</p></td>
</tr>
<tr class="even">
<td><p><a href="permissions-in-exchange-hybrid-deployments-exchange-2013-help.md">Berechtigungen in Exchange-Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zur Verwendung der rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC) für die Berechtigungssteuerung in einer Hybridbereitstellung.</p></td>
</tr>
<tr class="odd">
<td><p><a href="edge-transport-servers-with-hybrid-deployments-exchange-2013-help.md">Edge-Transport-Server in Hybridbereitstellungen</a></p></td>
<td><p>Weitere Informationen zu Exchange-Edge-Transport-Servern und deren Bereitstellung und Betrieb in einer Hybridbereitstellung.</p></td>
</tr>
<tr class="even">
<td><p><a href="single-sign-on-with-hybrid-deployments-exchange-2013-help.md">Einmaliges Anmelden in Hybrid-Bereitstellungen</a></p></td>
<td><p>Weitere Informationen zur Funktionweise des einmaligen Anmeldens mit der Kennwortsynchronisierung und AD FS in einer Hybridbereitstellung.</p></td>
</tr>
<tr class="odd">
<td><p><a href="hybrid-deployment-procedures-exchange-2013-help.md">Hybrid-Bereitstellungsverfahren</a></p></td>
<td><p>Verfahren zur Erstellung und Änderung von Hybridbereitstellungen für lokale und Exchange Online-Organisationen mit Exchange.</p></td>
</tr>
<tr class="even">
<td><p><a href="hybrid-deployments-with-exchange-2013-and-exchange-2010-exchange-2013-help.md">Hybrid-Bereitstellungen mit Exchange 2013 und Exchange 2010</a></p></td>
<td><p>Erfahren Sie mehr über Exchange 2013-basierte Hybridbereitstellungen in Exchange 2010-Organisationen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="hybrid-deployments-with-exchange-2013-and-exchange-2007-exchange-2013-help.md">Hybridbereitstellungen mit Exchange 2013 und Exchange 2007</a></p></td>
<td><p>Erfahren Sie mehr über Exchange 2013-basierte Hybridbereitstellungen in Exchange 2007-Organisationen.</p></td>
</tr>
</tbody>
</table>


## Neu bei Office 365?


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Dn249373.eac8a413-9498-4220-8544-1e37d1aaea13(EXCHG.150).png" title="Das Kurzsymbol für LinkedIn Learning" alt="Das Kurzsymbol für LinkedIn Learning" /> <strong>Neu bei Office 365?</strong><br />
Entdecken Sie die kostenlosen Videokurse für <a href="https://support.office.com/de-de/article/office-365-admin-and-it-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5">Office 365 admins and IT pros</a>, präsentiert von LinkedIn Learning.</p></td>
</tr>
</tbody>
</table>

