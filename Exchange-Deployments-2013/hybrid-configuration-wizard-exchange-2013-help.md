---
title: 'Assistent für die Hybridkonfiguration: Exchange 2013 Help'
TOCTitle: Assistent für die Hybridkonfiguration
ms:assetid: 2e6ed294-ee74-4038-8b71-b61786372ba4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529921(v=EXCHG.150)
ms:contentKeyID: 50477179
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Assistent für die Hybridkonfiguration

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In diesem Thema finden Sie eine Übersicht über die Konfiguration von Exchange-Hybridbereitstellungen, verfügbare Hybridbereitstellungsfeatures und -optionen und das Modul für die Hybridkonfiguration, mit dem die Hauptaktionen beim Konfigurieren und Aktualisieren einer Hybridbereitstellung ausgeführt werden.

Weitere Informationen zu Hybridbereitstellungen finden Sie unter [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md).

**Inhalt**

Hybridkonfiguration

Features der Hybridkonfiguration

Hybridkonfigurationsoptionen

Modul für die Hybridkonfiguration

## Hybridkonfiguration

Im Folgenden können Sie sich einen raschen Überblick über den Assistenten für die Hybridkonfiguration verschaffen. Zuerst erstellt der Assistent das Objekt **HybridConfiguration** im lokalen Active Directory. Dieses Active Directory-Objekt speichert die Informationen zur Hybridkonfiguration für die Hybridbereitstellung und wird mithilfe des Assistenten für die Hybridkonfiguration aktualisiert. Anschließend erfasst der Assistent vorhandene lokale Konfigurationsdaten der Exchange- und Active Directory-Topologie, Office 365-Mandanten- und Exchange Online-Konfigurationsdaten, definiert verschiedene Organisationsparameter und führt dann eine Vielzahl von Konfigurationstasks in der lokalen und der Exchange Online-Organisation aus.


> [!IMPORTANT]
> Es gibt verschiedene wichtige Überlegungen und Voraussetzungen, die berücksichtigt bzw. erfüllt werden müssen, bevor Sie den Assistenten für die Hybridkonfiguration verwenden können. Sie müssen die unter <A href="hybrid-deployment-prerequisites-exchange-2013-help.md">Voraussetzungen für die Hybridbereitstellung</A> beschriebenen Anforderungen für Hybridbereitstellungen erfüllen. Dann können Sie mithilfe des Assistenten für die Hybridkonfiguration die Exchange-Organisation für die Hybridbereitstellung konfigurieren.



Die Hybridbereitstellungskonfiguration umfasst folgende allgemeine Phasen:

1.  **Überprüfen der Voraussetzungen und Durchführen von Topologieüberprüfungen**   Der Assistent für die Hybridkonfiguration überprüft, ob die lokale und die Exchange Online-Organisation eine Hybridbereitstellung unterstützen können. Einige der vom Assistenten in einer lokalen und einer Exchange Online-Organisation überprüften Elemente sind:
    
      - Lokale Exchange-Serverversionen
    
      - Exchange Online-Version
    
      - Active Directory-Synchronisierung und -Konfiguration
    
      - Verbund- und akzeptierte Domänen
    
      - Vorhandene Verbundvertrauensstellungen und Organisationsbeziehungen
    
      - Virtuelle Verzeichnisse von Webdiensten
    
      - Exchange-Zertifikate

2.  **Testen der Kontoanmeldeinformationen**   Bestimmte lokale Konten und Konten der Office 365-Organisation für die Hybridverwaltung greifen auf die lokale und die Exchange Online-Organisation zu, um erforderliche Überprüfungsinformationen zu erfassen und Konfigurationsänderungen an den Organisationsparametern zum Aktivieren der Funktionalität der Hybridbereitstellung auszuführen. Der Assistent für die Hybridkonfiguration überprüft, ob die Konten die richtigen Anmeldeinformationen aufweisen und eine Verbindung mit der lokalen und der Exchange Online-Organisation herstellen können. Die Konten für die Verwaltung der Hybridbereitstellung der lokalen und der Office 365-Organisation müssen Mitglied der Rollengruppe "Organisationsverwaltung" sein, damit der Assistent für die Hybridkonfiguration die Tasks erfolgreich abschließen kann.

3.  **Ausführen der Änderungen an der Hybridkonfiguration**: Nach dem Testen der Konten für die Hybridverwaltung, dem Überprüfen der Voraussetzungen und dem Ausführen von Topologieüberprüfungen sowie dem Erfassen der im Rahmen des Assistenten definierten Konfigurationsinformationen führt der Assistent für die Hybridkonfiguration die Konfigurationsänderungen aus, um die Hybridbereitstellung zu erstellen und zu aktivieren. Alle Änderungen an der Hybridkonfiguration werden automatisch im Protokoll der Hybridkonfiguration gespeichert. Standardmäßig befindet sich das Protokoll der Hybridkonfiguration auf dem lokalen Postfachserver unter `%UserProfile%\AppData\Roaming\Microsoft\Exchange Hybrid Configuration`.
    

    > [!IMPORTANT]
    > Die Übermittlung eingehender Nachrichten wird vom MX-Eintrag der Organisation gesteuert. Eingehende Internet-E-Mail für eine Hybridbereitstellung wird nicht vom Assistenten für die Hybridkonfiguration konfiguriert.



## Features der Hybridkonfiguration

Der Assistent für die Hybridkonfiguration aktiviert bei jeder Ausführung standardmäßig automatisch alle Features der Hybridbereitstellung. Wenn Sie ein bestimmtes Feature der Hybridkonfiguration deaktivieren möchten, müssen Sie die Exchange-Verwaltungsshell und das Cmdlet **Set-HybridConfiguration** verwenden. Die folgenden Funktionen der Hybridkonfiguration werden standardmäßig vom Assistenten aktiviert:

  - **Freigabe von Frei/Gebucht-Informationen**   Dieses Feature ermöglicht, dass Kalenderinformationen zwischen lokalen und Exchange Online-Organisationsbenutzern freigegeben werden. Die Funktion wird im Rahmen der Konfiguration von Verbundfreigaben und Organisationsbeziehungen für die lokale und die Exchange Online-Organisation aktiviert. Weitere Informationen finden Sie unter [Freigabe](https://technet.microsoft.com/de-de/library/dd638083\(v=exchg.150\)).

  - **E-Mail-Infos**   E-Mail-Infos sind informative Meldungen, die Benutzern beim Erstellen einer Nachricht angezeigt werden. Durch Aktivieren von E-Mail-Infos in der Hybridbereitstellung können lokale und Exchange Online-Absender die verfasste Nachricht korrigieren, um unerwünschte Situationen oder Unzustellbarkeitsberichte (Non-Delivery Reports, NDRs) zwischen den Organisationen zu vermeiden. Weitere Informationen finden Sie unter [MailTips](https://technet.microsoft.com/de-de/library/jj649091\(v=exchg.150\)).

  - **Online-Archivierung**   Diese Funktion ermöglicht es der Exchange Online-Organisation, Benutzer-E-Mail-Archive für lokale und Exchange Online-Benutzer zu hosten. Weitere Informationen finden Sie unter [Konfigurieren der Exchange Online-Archivierung](http://go.microsoft.com/fwlink/p/?linkid=266565).

  - **Umleitung für Outlook im Web**   Mit der Umleitung für Outlook im Web wird eine einzige, allgemeine URL für den Zugriff auf lokale und Exchange Online-Postfächer bereitgestellt. Clientzugriffsserver leiten Outlook im Web-Anforderungen automatisch an die lokalen Postfachserver um oder stellen Benutzern einen Link zu ihrem Postfach in der Exchange Online-Organisation bereit.

  - **Exchange ActiveSync-Umleitung**   Wenn Sie ein Postfach aus Ihrer lokalen Exchange-Organisation zu Exchange Online verschieben, müssen alle auf das Postfach zugreifenden Clients aktualisiert werden, um Exchange Online verwenden zu können. Dazu zählen auch Exchange ActiveSync-Geräte. Die meisten Exchange ActiveSync-Clients werden inzwischen automatisch erneut konfiguriert, wenn das Postfach zu Exchange Online verschoben wird. Weitere Informationen finden Sie unter [Exchange ActiveSync-Geräteeinstellungen mit Exchange-Hybridbereitstellungen](exchange-activesync-device-settings-with-exchange-hybrid-deployments-exchange-2013-help.md).

  - **Sichere E-Mail**   Diese Funktion aktiviert die sichere Nachrichtenübermittlung über das TLS-Protokoll (Transport Layer Security) zwischen der lokalen und der Exchange Online-Organisation. Die lokale und die Exchange Online-Organisation werden gegenseitig über die Antragsteller digitaler Zertifikate authentifiziert, und E-Mail-Kopfzeilen und die RTF-Nachrichtenformatierung werden organisationsübergreifend beibehalten.

## Hybridkonfigurationsoptionen

Der Assistent für die Hybridkonfiguration ermöglicht eine Auswahl bestimmter Optionen in verschiedenen Bereichen für die Hybridbereitstellung. Wenn Sie bestimmte Hybridkonfigurationsoptionen aktualisieren möchten, nachdem zuerst die Hybridbereitstellung konfiguriert wurde, können Sie entweder den Assistenten für die Hybridkonfiguration oder die Exchange-Verwaltungsshell zur Auswahl verschiedener Konfigurationsoptionen verwenden.

Die Tabelle unten beschreibt die Hauptoptionen, die der Assistent für die Hybridkonfiguration ändert und konfiguriert.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Konfigurationsbereich</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Domänen</p></td>
<td><p>Der Assistent fügt der lokalen Organisation eine akzeptierte Domäne für die Hybridnachrichtenübermittlung und Anfragen der AutoErmittlung für die Cloud-Organisation hinzu. Diese Domäne wird als <em>Koexistenzdomäne</em> bezeichnet und als sekundäre Proxydomäne zu allen Richtlinien für E-Mail-Adressen hinzugefügt, die <em>PrimarySmtpAddress</em>-Vorlagen für im Assistenten für die Hybridkonfiguration ausgewählte Domänen aufweisen. In der Standardeinstellung ist das die Domäne &quot;&lt;Domäne&gt;.mail.onmicrosoft.com&quot;.</p>
<p>Sie können die akzeptierte Domäne anzeigen, indem Sie den folgenden Befehl in der Exchange-Verwaltungsshell in Exchange Online ausführen.</p>
<pre><code>Get-AcceptedDomain | FL DomainName, IsCoexistenceDomain</code></pre></td>
</tr>
<tr class="even">
<td><p>Zertifikat für sichere E-Mail</p></td>
<td><p>Im Assistenten müssen Sie ein bestimmtes Zertifikat auswählen, das von einer externen Zertifizierungsstelle stammt und mit dem E-Mail-Nachrichten, die zwischen lokalen und Exchange Online-Organisationen gesendet werden, authentifiziert und geschützt werden.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Verbundfreigabe</p></td>
<td><p>Der Assistent prüft, ob für die lokale Organisation eine vorhandene OAuth-Authentifizierungsbeziehung oder eine Verbundvertrauensstellung mit dem Azure Active Directory-Authentifizierungssystem vorliegt. Ist dies der Fall, wird die vorhandene OAuth-Authentifizierung oder die Verbundvertrauensstellung zur Unterstützung der Hybridbereitstellung verwendet. Ist dies nicht der Fall konfiguriert der Assistent je nach Art der lokalen Exchange-Konfiguration die OAuth-Authentifizierung oder erstellt eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem. Der Assistent fügt zudem bei Bedarf der Verbundvertrauensstellung alle im Assistenten für die Hybridkonfiguration ausgewählten Domänen hinzu.</p>
<p>Neben der Konfiguration der OAuth-Authentifizierung oder der Verbundvertrauensstellung erstellt und konfiguriert der Assistent Organisationsbeziehungen für die lokale und die Exchange Online-Organisation. Diese Organisationsbeziehungen ermöglichen dem Assistenten die Aktivierung mehrerer Funktionen der Hybridbereitstellung, u. a. Freigabe von Frei/Gebucht-Informationen, Outlook im Web-Umleitung und E-Mail-Infos.</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenübermittlung</p></td>
<td><p>Im Assistenten können Sie Exchange-Server auswählen und konfigurieren, sodass der sichere E-Mail-Transport zwischen der lokalen und der Exchange Online-Organisation sichergestellt wird. In Exchange 2010 handelt es sich dabei um den Hub-Transportserver. In Exchange 2013 handelt es sich um einem Clientzugriffsserver. In Exchange 2016 und neuer handelt es sich dabei um einen Postfachserver.</p>
<p>Der Assistent konfiguriert Ihre lokale Exchange- und Exchange Online-Organisation für das Hybridnachrichtenrouting. Durch die Konfiguration von neuen und vorhandenen Sende- und Empfangsconnectors in der lokalen Organisation und von eingehenden und ausgehenden Connectors in Exchange Online können Sie auswählen, ob ausgehende Nachrichten, die von der Exchange Online-Organisation an das Internet zugestellt werden, direkt an externe E-Mail-Empfänger gesendet oder über die lokalen Exchange-Server in der Hybridbereitstellung geroutet werden.</p>

> [!IMPORTANT]
> Die Übermittlung eingehender Nachrichten wird vom MX-Eintrag der Organisation gesteuert. Eingehende Internet-E-Mail für eine Hybridbereitstellung wird nicht vom Assistenten für die Hybridkonfiguration konfiguriert.


</td>
</tr>
</tbody>
</table>


## Modul für die Hybridkonfiguration

Das Modul für die Hybridkonfiguration führt die Hauptaktionen beim Konfigurieren und Aktualisieren einer Hybridbereitstellung aus. Es ist für die Verarbeitung der `Update-HybridConfiguration`-Cmdlet-Aktionen zuständig und vergleicht den Zustand des *HybridConfiguration*Active Directory-Objekts mit aktuellen lokalen Exchange- und Exchange Online-Konfigurationseinstellungen. Danach führt es Aufgaben zum Zuordnen der Konfigurationseinstellungen für die Bereitstellung zu den Parametern aus, die im *HybridConfiguration*Active Directory-Objekt definiert sind. Wenn der aktuelle Konfigurationszustand der lokalen Exchange- und Exchange Online-Bereitstellung bereits den im *HybridConfiguration*Active Directory-Objekt definierten Einstellungen entspricht, werden vom Modul für die Hybridkonfiguration weder an der lokalen noch an der Exchange Online-Organisation Änderungen ausgeführt.

Beim Aktualisieren einer vorhandenen Hybridbereitstellung werden vom Modul für die Hybridkonfiguration die folgenden Schritte ausgeführt:

1.  Das *Update-HybridConfiguration*-Cmdlet löst das Modul für die Hybridkonfiguration aus, sodass es gestartet wird.

2.  Das Modul für die Hybridkonfiguration liest den "gewünschten Zustand", der im `HybridConfiguration`Active Directory-Objekt gespeichert ist.

3.  Das Modul für die Hybridkonfiguration ermittelt Topologiedaten und die aktuelle Konfiguration aus der lokalen Exchange-Organisation.

4.  Das Modul für die Hybridkonfiguration ermittelt Topologiedaten und die aktuelle Konfiguration aus der Exchange Online-Organisation.

5.  Basierend auf gewünschtem Zustand, Topologiedaten und aktueller Konfiguration stellt das Modul für die Hybridkonfiguration den "Unterschied" zwischen der lokalen Exchange- und der Exchange Online-Organisation fest und führt dann Konfigurationstasks aus, um den gewünschten Zustand zu erreichen.

Die folgende Abbildung enthält eine Übersicht darüber, wie das Modul für die Hybridkonfiguration während der Hybridbereitstellung Konfigurationseinstellungen des lokalen Exchange-Servers und von Exchange Online abruft und ändert.

![Flussdiagramm des Moduls für die Hybridkonfiguration](images/Hh529921.7e01b239-b978-4377-9eac-aa5bc4561866(EXCHG.150).gif "Flussdiagramm des Moduls für die Hybridkonfiguration")

