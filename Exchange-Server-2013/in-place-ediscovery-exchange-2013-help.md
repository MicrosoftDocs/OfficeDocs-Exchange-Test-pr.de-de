---
title: 'Compliance-eDiscovery: Exchange 2013 Help'
TOCTitle: Compliance-eDiscovery
ms:assetid: 6377cb7a-3416-4e15-8571-c45d2160fc6f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298021(v=EXCHG.150)
ms:contentKeyID: 50475821
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Compliance-eDiscovery

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-01-17_


> [!NOTE]
> Wir haben den Stichtag (1. Juli 2017) für das Erstellen neuer In-Situ-eDiscovery-Suchen in Exchange Online (in Office 365 und eigenständigen Exchange Online-Plänen) verschoben. Im späteren Verlauf dieses Jahres oder Anfang des nächsten Jahres können Sie keine neuen Suchen mehr in Exchange Online erstellen. Um eDiscovery-Suchen zu erstellen, müssen Sie <A href="https://go.microsoft.com/fwlink/?linkid=847843">Inhaltssuche</A> im Office 365 Security &amp; Compliance Center verwenden. Nachdem die Erstellung neuer In-Situ-eDiscovery-Suchen eingestellt ist, können vorhandene In-Situ-eDiscovery-Suchen nach wie vor geändert werden, und das Erstellen neuer In-Situ-eDisvocery-Suchen in Exchange Server&nbsp;2013- und Exchange-Hybridbereitstellungen wird weiterhin unterstützt.



Wenn in Ihrer Organisation rechtliche Bestimmungen im Hinblick auf die Offenlegung erfüllt werden müssen (im Zusammenhang mit Organisationsrichtlinien, Richtlinientreue oder Rechtsstreitigkeiten), können Sie mithilfe der Compliance-eDiscovery-Funktion in Microsoft Exchange Server 2013 und Exchange Online in Postfächern nach relevanten Inhalten suchen. Exchange 2013 und Exchange Online bieten außerdem eine Verbundsuchfunktion und Integration mit Microsoft SharePoint 2013 und Microsoft SharePoint Online. Im eDiscovery Center in SharePoint können Sie alle Inhalte in Bezug auf einen Fall, z. B. SharePoint 2013- und SharePoint Online-Websites, Dokumente, von SharePoint (nur SharePoint 2013) indizierte Dateifreigaben, Postfachinhalte in Exchange und archivierte Lync 2013-Inhalte, von einem zentralen Standort aus durchsuchen und in einem Archiv platzieren. Zudem können Sie mit Compliance-eDiscovery in einer hybriden Exchange-Umgebung lokale und cloudbasierte Postfächer innerhalb einer Suche durchsuchen.

**Inhalt**

Funktionsweise von Compliance-eDiscovery

Exchange-Suche

Die Rollengruppe "Discoveryverwaltung" und Verwaltungsrollen

Benutzerdefinierte Verwaltungsbereiche für Compliance-eDiscovery

Integration mit SharePoint Server 2013 und SharePoint Online

eDiscovery in einer Exchange-Hybridbereitstellung

Discoverypostfächer

Verwenden der Compliance-eDiscovery-Suche

Schätzung, Vorschau und Kopieren von Suchergebnissen

Exportieren von Suchergebnissen in eine PST-Datei

Unterschiedliche Suchergebnisse

Protokollierung für Compliance-eDiscovery-Suchen

Compliance-eDiscovery und Compliance-Archiv

Aufbewahrung von Postfächern zu Compliance-eDiscovery-Zwecken

Compliance-eDiscovery-Begrenzungen und Einschränkungsrichtlinien

Dokumentation zu Compliance-eDiscovery


> [!IMPORTANT]
> Compliance-eDiscovery ist eine leistungsfähige Funktion, mit der ein Benutzer mit den entsprechenden Berechtigungen potenziell auf alle Nachrichtendatensätze zugreifen kann, die innerhalb der Exchange 2013- oder Exchange Online-Organisation gespeichert sind. Es ist wichtig, die Discoveryaktivitäten zu kontrollieren und zu überwachen. Diese Aktivitäten umfassen das Hinzufügen von Mitgliedern zur Rollengruppe "Discoveryverwaltung", das Zuweisen der Verwaltungsrolle "Postfachsuche" sowie das Zuweisen der Berechtigung für den Postfachzugriff zu Discoverypostfächern.



## Funktionsweise von Compliance-eDiscovery

Für die Compliance-eDiscovery-Suche werden die von der Exchange-Suche erstellten Inhaltsindizes verwendet. Die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC) stellt die Rollengruppe [Erkennungsverwaltung](discovery-management-exchange-2013-help.md) zum Delegieren von Suchaufgaben an nicht technische Mitarbeiter bereit, ohne dass erhöhte Rechte erteilt werden müssen, mit denen ein Benutzer möglicherweise Änderungen an der Exchange-Konfiguration vornehmen kann. Die Exchange-Verwaltungskonsole stellt eine benutzerfreundliche Suchoberfläche für nicht technisches Personal wie z. B. Mitarbeiter der Rechtsabteilung, Richtlinienbeauftragte, Datensatzmanager und Mitarbeiter der Personalabteilung (Human Resources, HR) bereit.

Autorisierte Benutzer können Compliance-eDiscovery-Suchen durchführen, indem sie die Postfächer auswählen und dann Suchkriterien wie Stichwörter, Start- und Enddaten, Absender- und Empfängeradressen und Nachrichtentypen angeben. Nach der Suche können autorisierte Benutzer eine der folgenden Aktionen auswählen:

  - **Suchergebnisse schätzen**   Diese Option liefert eine Schätzung der Gesamtgröße und -anzahl der Objekte, die von der Suche auf der Grundlage der angegebenen Kriterien zurückgegeben werden.

  - **Vorschau auf Suchergebnisse anzeigen**   Diese Option bietet eine Vorschau der Ergebnisse. Die von den einzelnen durchsuchten Postfächern zurückgegebenen Meldungen werden angezeigt.

  - **Suchergebnisse kopieren**   Mit dieser Option können Sie Nachrichten in ein Discoverypostfach kopieren.

  - **Suchergebnisse exportieren**   Nachdem die Suchergebnisse in ein Discoverypostfach kopiert wurden,können Sie sie in eine PST-Datei exportieren.

![Schätzung, Vorschau, Kopieren und Exportieren von Suchergebnissen](images/Dd298021.6356971a-34ed-4586-8229-030448d4fe2d(EXCHG.150).gif "Schätzung, Vorschau, Kopieren und Exportieren von Suchergebnissen")

## Exchange-Suche

Für die Compliance-eDiscovery-Suche werden die von der Exchange-Suche erstellten Inhaltsindizes verwendet. Die Exchange-Suche basiert nun auf Microsoft Search Foundation, einer umfassenden Suchplattform mit einer wesentlich verbesserten Indizierungs- und Abfrageleistung und Suchfunktionalität. Da Microsoft Search Foundation auch von anderen Office-Produkten verwendet wird, SharePoint 2013 eingeschlossen, wird eine höhere Interoperabilität und eine ähnliche Abfragesyntax für diese Produkte bereitgestellt.

Dank eines einzigen Inhaltsindizierungsmoduls müssen keine zusätzlichen Ressourcen zum Durchforsten und Indizieren von Postfachdatenbanken für die Compliance-eDiscovery-Suche verwendet werden, wenn Mitarbeiter von IT-Abteilungen eDiscovery-Anforderungen erhalten.

Die Compliance-eDiscovery-Suche verwendet KQL (Keyword Query Language) – eine Abfragesyntax, die der von der Sofortsuche in Microsoft Outlook und Outlook Web App verwendeten AQS (Advanced Query Syntax) ähnelt. Benutzer mit KQL-Kenntnissen können auf einfache Weise leistungsstarke Suchabfragen zum Durchsuchen von Inhaltsindizes erstellen.

Weitere Informationen zu den von der Exchange-Suche indizierten Dateiformaten finden Sie unter [Von der Exchange-Suche indizierte Dateiformate](file-formats-indexed-by-exchange-search-exchange-2013-help.md).

## Die Rollengruppe "Discoveryverwaltung" und Verwaltungsrollen

Damit autorisierte Benutzer Compliance-eDiscovery-Suchen durchführen können, müssen Sie die Benutzer der Rollengruppe [Erkennungsverwaltung](discovery-management-exchange-2013-help.md) hinzufügen. Diese Rollengruppe umfasst zwei Verwaltungsrollen: [Rolle „Postfachsuche“](mailbox-search-role-exchange-2013-help.md), die einem Benutzer das Ausführen einer Compliance-eDiscovery-Suche ermöglicht, und [Rolle „Gesetzliche Aufbewahrungspflicht“](legal-hold-role-exchange-2013-help.md), mit der Benutzer ein Postfach in einem Compliance-Archiv platzieren oder ein Beweissicherungsverfahren für das Postfach aktivieren können.

Standardmäßig werden Benutzern oder Exchange-Administratoren keine Berechtigungen zur Ausführung von Compliance-eDiscovery-Aufgaben zugewiesen. Exchange-Administratoren, die Mitglieder der Rollengruppe "Organisationsverwaltung" sind, können Benutzer zur Rollengruppe "Discoveryverwaltung" hinzufügen und benutzerdefinierte Rollengruppen erstellen, um die Berechtigungen für einen Discoverymanager auf einen bestimmten Benutzersatz zu beschränken. Weitere Informationen zum Hinzufügen von Benutzern zur Rollengruppe "Discoveryverwaltung" finden Sie unter [Zuweisen von eDiscovery-Berechtigungen in Exchange](assign-ediscovery-permissions-in-exchange-exchange-2013-help.md).


> [!IMPORTANT]
> Wenn ein Benutzer nicht zur Rollengruppe "Discoveryverwaltung" hinzugefügt oder ihm nicht die Rolle "Postfachsuche" zugewiesen wurde, wird die Benutzeroberfläche <STRONG>Compliance-eDiscovery und -Archiv</STRONG> nicht im EAC angezeigt, und die Compliance-eDiscovery-Cmdlets stehen in der Exchange-Verwaltungsshell nicht zur Verfügung.



Durch das Überwachen von Änderungen an RBAC-Rollen (diese Funktion ist standardmäßig aktiviert) wird sichergestellt, dass die richtigen Datensätze gespeichert werden, um die Zuweisung der Rollengruppe "Discoveryverwaltung" nachverfolgen zu können. Sie können den Administrator-Rollengruppenbericht verwenden, um nach Änderungen an Administratorrollengruppen zu suchen. Weitere Informationen finden Sie unter [Durchsuchen der Rollengruppenänderungen oder Administratorüberwachungsprotokolle](search-the-role-group-changes-or-administrator-audit-logs-exchange-2013-help.md).

Zurück zum Seitenanfang

## Benutzerdefinierte Verwaltungsbereiche für Compliance-eDiscovery

Sie können einen benutzerdefinierten Verwaltungsbereich verwenden, damit bestimmte Personen oder Gruppen Compliance-eDiscovery verwenden können, um eine Teilmenge der Postfächer in Ihrer Exchange 2013- oder Exchange Online-Organisation zu durchsuchen. Beispielsweise können Sie einen Discovery-Manager nur die Postfächer der Benutzer an einem bestimmten Standort oder in einer bestimmten Abteilung durchsuchen lassen. Hierfür erstellen Sie einen benutzerdefinierten Verwaltungsbereich, in dem über einen benutzerdefinierten Empfängerfilter gesteuert wird, welche Postfächer durchsucht werden können. In Bereichen mit Empfängerfiltern werden Filter verwendet, um bestimmte Empfänger basierend auf dem Empfängertyp oder anderen Eigenschaften zu erfassen.

Bei Verwendung von Compliance-eDiscovery ist die einzige Eigenschaft eines Benutzerpostfachs, die Sie zum Erstellen eines Empfängerfilters für einen benutzerdefinierten Bereich verwenden können, die Mitgliedschaft in Verteilergruppen. Wenn Sie andere Eigenschaften verwenden, wie beispielsweise *CustomAttributeN*, *Department* oder *PostalCode* schlägt die Suche fehl, wenn sie von einem Mitglied der Rollengruppe ausgeführt wird, der der benutzerdefinierte Bereich zugewiesen ist. Weitere Informationen finden Sie unter [Erstellen eines benutzerdefinierten Verwaltungsbereichs für die Compliance-eDiscovery-Suche](create-a-custom-management-scope-for-in-place-ediscovery-searches-exchange-2013-help.md).

## Integration mit SharePoint Server 2013 und SharePoint Online

Exchange 2013 und Exchange Online ermöglichen eine Integration mit SharePoint 2013 und SharePoint Online, wodurch Discoverymanager das eDiscovery Center in SharePoint zum Ausführen der folgenden Aufgaben nutzen können:

  - **Durchsuchen und Archivieren von Inhalten von einem einzigen Standort aus** Ein autorisierter Discoverymanager kann Inhalte aus SharePoint und Exchange, einschließlich von Lync-Inhalten wie z. B. in Exchange-Postfächern archivierte Chatunterhaltungen und freigegebene Besprechungsdokumente, durchsuchen und archivieren.

  - **Fall-Verwaltung** Das eDiscovery Center verwendet einen Ansatz zur Fall-Verwaltung mit eDiscovery, der das Erstellen von Fällen und Suchen sowie für jeden Fall das Aufbewahren von Inhalten über verschiedene Repositorys hinweg ermöglicht.

  - **Export von Suchergebnissen** Ein Discoverymanager kann das eDiscovery Center zum Exportieren von Suchergebnissen verwenden. In Suchergebnissen zurückgegebene Postfachinhalte werden in eine PST-Datei exportiert.

SharePoint verwendet für Inhaltsindizierung und -abfrage ebenfalls Microsoft Search Foundation. Unabhängig davon, ob ein Discoverymanager die Exchange-Verwaltungskonsole oder das eDiscovery Center zum Durchsuchen von Exchange-Inhalten verwendet, werden dieselben Postfachinhalte zurückgegeben.

Bevor Sie in lokalen Bereitstellungen das eDiscovery Center in SharePoint zum Durchsuchen von Exchange-Postfächern verwenden können, müssen Sie eine Vertrauensstellung zwischen den beiden Anwendungen einrichten. In Exchange 2013 und SharePoint 2013 wird dies mithilfe der OAuth-Authentifizierung erreicht. Ausführliche Informationen finden Sie unter [Konfigurieren von Exchange für SharePoint eDiscovery Center](configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md). Über SharePoint ausgeführte eDiscovery-Suchen werden von Exchange mithilfe von RBAC autorisiert. Damit ein SharePoint-Benutzer eine eDiscovery-Suche in Exchange-Postfächern durchführen kann, müssen diesem delegierte Discoveryverwaltungsberechtigungen in Exchange zugewiesen werden. Zur Anzeige einer Vorschau von Postfachinhalten, die bei einer eDiscovery-Suche mit einem SharePoint eDiscovery Center zurückgegeben werden, muss der Discoverymanager über ein Postfach in derselben Exchange-Organisation verfügen.

Schrittweise Anleitungen zum Einrichten eines eDiscovery Center in einer Office 365-Organisation finden Sie unter [Einrichten eines eDiscovery Center in SharePoint Online](https://go.microsoft.com/fwlink/p/?linkid=331600).

## eDiscovery in einer Exchange-Hybridbereitstellung

Um in einer Exchange 2013-Hybridorganisation eine erfolgreiche standortübergreifende eDiscovery-Suche durchführen zu können, müssen Sie die OAuth (Open Authorization)-Authentifizierung zwischen Ihrer lokalen Exchange-Organisation und der Exchange Online-Organisation einrichten, damit Sie Compliance-eDiscovery zum Durchsuchen der lokalen und cloudbasierten Postfächer verwenden können. Die OAuth-Authentifizierung ist ein Server-zu-Server-Authentifizierungsprotokoll, das es Anwendungen ermöglichlicht, sich gegenseitig zu authentifizieren.

Die OAuth-Authentifizierung wird in den folgenden eDiscovery-Szenarien in einer Exchange-Hybridbereitstellung unterstützt:

  - Durchsuchen lokaler Postfächer, für die die Exchange Online-Archivierung für cloudbasierte Archivpostfächer verwendet wird.

  - Durchsuchen der lokalen und cloudbasierten Postfächer in derselben eDiscovery-Suche.

  - Durchsuchen lokaler Postfächer mit dem eDiscovery Center in SharePoint Online.

Weitere Informationen zu den eDiscovery-Szenarien, für die die OAuth-Authentifizierung in einer Exchange-Hybridbereitstellung konfiguriert werden muss, finden Sie unter [Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung](using-oauth-authentication-to-support-ediscovery-in-an-exchange-hybrid-deployment-exchange-2013-help.md). Schrittweise Anleitungen zum Konfigurieren der OAuth-Authentifizierung, sodass eDiscovery unterstützt wird, finden Sie unter [Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen](configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help.md).

## Discoverypostfächer

Nachdem Sie eine Compliance-eDiscovery-Suche erstellt haben, können Sie die Suchergebnisse in ein Zielpostfach kopieren. Die Exchange-Verwaltungskonsole ermöglicht Ihnen die Auswahl eines Discoverypostfachs als Zielpostfach. Bei einem Discoverypostfach handelt es sich um einen speziellen Postfachtyp, mit dem die folgenden Funktionen bereitgestellt werden:

  - **Einfache und sichere Zielpostfachauswahl**   Wenn Sie die Exchange-Verwaltungskonsole zum Erstellen einer Compliance-eDiscovery-Suche verwenden, stehen nur Discoverypostfächer als Repository zum Speichern der Suchergebnisse zur Verfügung. Sie müssen keine potenziell lange Liste der in der Organisation verfügbaren Postfächer durchsehen. Dadurch wird auch vermieden, dass ein Discoverymanager versehentlich das Postfach eines anderen Benutzers oder ein ungesichertes Postfach auswählt, um darin potenziell vertrauliche Nachrichten zu speichern.

  - **Große Postfachspeicherkontingente**   Das Zielpostfach muss ausreichend Kapazität zum Speichern einer großen Menge an Nachrichtendaten bieten, die möglicherweise bei einer Compliance-eDiscovery-Suche zurückgegeben werden. Discoverypostfächer verfügen standardmäßig über ein Postfachspeicherkontingent von 50 GB. Dieses Speicherkontingent kann nicht erhöht werden.

  - **Standardmäßige hohe Sicherheit**   Wie allen Postfachtypen ist auch einem Discoverypostfach ein Active Directory-Benutzerkonto zugeordnet. Dieses Konto ist jedoch standardmäßig deaktiviert. Nur explizit zum Zugreifen auf ein Discoverypostfach autorisierte Benutzer haben Zugriff auf dieses Postfach. Mitglieder der Rollengruppe "Discoveryverwaltung" erhalten standardmäßig Vollzugriff auf das Standarddiscoverypostfach. Für weitere Discoverypostfächer, die Sie ggf. erstellen, werden Benutzern keine Postfachzugriffsberechtigungen zugewiesen.

  - **E-Mail-Zustellung deaktiviert**   Wenngleich Discoverypostfächer in Exchange-Adresslisten angezeigt werden, können Benutzer keine E-Mails an diese Postfächer senden. Die E-Mail-Zustellung an Discoverypostfächer ist aufgrund von Zustellungseinschränkungen unzulässig. Auf diese Weise wird die Integrität der Suchergebnisse gewährleistet, die in ein Discoverypostfach kopiert werden.

Von Exchange 2013-Setup wird ein Discoverypostfach mit dem Anzeigenamen **Discoverysuchpostfach** erstellt. Mithilfe der Shell können Sie weitere Discoverypostfächer erstellen. Standardmäßig werden den von Ihnen erstellten Discoverypostfächern keine Zugriffsberechtigungen gewährt. Sie können einem Discoverymanager Vollzugriff erteilen, damit ein Zugriff auf die in ein Discoverypostfach kopierten Nachrichten möglich ist. Weitere Informationen finden Sie unter [Erstellen eines Discoverypostfachs](create-a-discovery-mailbox-exchange-2013-help.md).

Für die Compliance-eDiscovery-Suche wird außerdem ein Systempostfach mit dem Anzeigenamen **SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}** zum Speichern von Compliance-eDiscovery-Metadaten verwendet. Systempostfächer werden weder in der Exchange-Verwaltungskonsole noch in Exchange-Adresslisten angezeigt. Bevor Sie in Organisationen mit lokalem Exchange eine Postfachdatenbank entfernen können, in der sich das Systempostfach für die Compliance-eDiscovery-Suche befindet, müssen Sie das Postfach in eine andere Postfachdatenbank verschieben. Wenn das Postfach entfernt wird oder beschädigt ist, können die Discoverymanager erst wieder eDiscovery-Suchen durchführen, nachdem das Postfach neu erstellt wurde. Weitere Informationen finden Sie unter [Re-create the Discovery system mailbox](re-create-the-discovery-system-mailbox-exchange-2013-help.md).

Zurück zum Seitenanfang

## Verwenden der Compliance-eDiscovery-Suche

Benutzer, die zur Rollengruppe "Discoveryverwaltung" hinzugefügt wurden, können Compliance-eDiscovery-Suchen ausführen. Sie können mithilfe der webbasierten Oberfläche in der Exchange-Verwaltungskonsole Suchen durchführen. Dadurch wird das Verwenden der Compliance-eDiscovery-Suche für nicht technische Benutzer wie Datensatzmanager, Richtlinienbeauftragte oder Mitarbeiter der Rechts- und Personalabteilung vereinfacht. Sie können Suchläufe auch mit der Shell durchführen. Weitere Informationen finden Sie unter [Erstellen einer Compliance-eDiscovery-Suche](create-an-in-place-ediscovery-search-exchange-2013-help.md)


> [!NOTE]
> Mithilfe der Compliance-eDiscovery-Funktion können Sie in lokalen Bereitstellungen Postfächer auf Exchange 2013-Postfachservern durchsuchen. Zum Durchsuchen von Postfächern auf Exchange 2010-Postfachservern verwenden Sie die Suche in mehreren Postfächern auf einem Exchange 2010-Server.<BR>In einer Hybridbereitstellung – dies ist eine Umgebung, in der einige Postfächer auf lokalen Postfachservern und andere Postfächer in einer cloudbasierten Organisation vorliegen – können Sie Compliance-eDiscovery-Suchen für cloudbasierte Postfächer mithilfe der Exchange-Verwaltungskonsole in Ihrer lokalen Organisation durchführen. Wenn Sie Nachrichten in ein Discoverypostfach kopieren möchten, müssen Sie ein lokales Discoverypostfach auswählen. Nachrichten aus cloudbasierten Postfächern, die in Suchergebnissen zurückgegeben werden, werden in das angegebene lokale Discoverypostfach kopiert. Weitere Informationen zu Hybridbereitstellungen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/jj200581(v=exchg.150)">Hybridbereitstellungen in Exchange Server</A>.



Der Assistent für **Compliance-eDiscovery und -Archiv** in der Exchange-Verwaltungskonsole ermöglicht Ihnen das Erstellen einer Compliance-eDiscovery-Suche und verwendet ein Compliance-Archiv, um die Suchergebnisse aufzubewahren. Wenn Sie eine Compliance-eDiscovery-Suche erstellen, wird ein Suchobjekt im Compliance-eDiscovery-Systempostfach erstellt. Dieses Objekt kann bearbeitet werden, um die Suche zu starten, zu beenden, zu ändern und zu entfernen. Nachdem Sie die Suche erstellt haben, können Sie eine Schätzung der Suchergebnisse abrufen, die eine Schlüsselwortstatistik zur Ermittlung der Effektivität einer Abfrage umfasst. Sie können auch eine Livevorschau der bei der Suche zurückgegebenen Elemente anzeigen, in der Sie die Nachrichteninhalte, die Anzahl der von jedem Quellpostfach zurückgegebenen Nachrichten sowie die Gesamtzahl an Nachrichten anzeigen können. Diese Informationen können Sie bei Bedarf zur weiteren Optimierung Ihrer Abfrage verwenden.

Wenn Sie mit den Suchergebnissen zufrieden sind, können Sie sie in ein Discoverypostfach kopieren. Sie können auch die Exchange-Verwaltungskonsole oder Outlook verwenden, um ein Discoverypostfach oder Teile seiner Inhalte in eine PST-Datei zu exportieren.

Wenn Sie eine Compliance-eDiscovery-Suche erstellen, müssen Sie die folgenden Parameter angeben:

  - **Name** Der Suchname wird verwendet, um die Suche zu identifizieren. Wenn Sie Suchergebnisse in ein Discoverypostfach kopieren, wird ein Ordner mit dem Suchnamen und dem Zeitstempel im Discoverypostfach erstellt, um die Suchergebnisse in einem Discoverypostfach eindeutig zu identifizieren.

  - **Postfächer** Sie können alle Postfächer in Ihrer Exchange 2013- oder Exchange Online-Organisation durchsuchen oder die zu durchsuchenden Postfächer angeben. . Bei der Suche werden die primären und Archivpostfächer eines Benutzers eingeschlossen. Wenn Sie dieselbe Suche dazu verwenden möchten, um Elemente aufzubewahren, müssen Sie die Postfächer angeben. Sie können eine Verteilergruppe angeben, um Postfachbenutzer einzuschließen, die Mitglieder dieser Gruppe sind. Die Mitgliedschaft der Gruppe wird bei Erstellung der Suche berechnet, und spätere Änderungen an der Gruppenmitgliedschaft werden nicht automatisch in der Suche berücksichtigt.
    
    In Exchange Online können Sie auch Office 365-Gruppen als eine Inhaltsquelle angeben, sodass die das Gruppenpostfach durchsucht (oder archiviert) wird. Beachten Sie, dass beim Hinzufügen einer Office 365-Gruppe zu einer Compliance-eDiscoverysuche nur das Gruppenpostfach durchsucht wird; die Postfächer der Gruppenmitglieder werden nicht durchsucht.

  - **Suchabfrage** Sie können entweder alle Postfachinhalte der angegebenen Postfächer einschließen, oder mithilfe einer Suchabfrage Elemente zurückgeben, die für einen Fall oder eine Untersuchen von besonderer Relevanz sind. Sie können in einer Suchabfrage die folgenden Parameter angeben:
    
      - **Schlüsselwörter**   Sie können Schlüsselwörter und Ausdrücke angeben, nach denen der Nachrichteninhalt durchsucht werden soll. Sie können auch die logischen Operatoren **AND**, **OR** und **NOT** verwenden. Zusätzlich unterstützt Exchange 2013 den Operator **NEAR**, mit dem Sie nach einem Wort oder Ausdruck in der Nähe eines anderen Worts oder Ausdrucks suchen können.
        
        Wenn Sie nach einer genauen Übereinstimmung eines Ausdrucks, der mehrere Wörter enthält, suchen möchten, müssen Sie den Ausdruck in Anführungszeichen setzen. Wenn Sie z. B. nach der Zeichenfolge "Planung und Wettbewerb" suchen, werden Nachrichten mit einer exakten Übereinstimmung für diese Zeichenfolge zurückgegeben. Wenn Sie hingegen **Planung AND Wettbewerb** angeben, werden Nachrichten zurückgegeben, die die Wörter **Planung** und **Wettbewerb** an einer beliebigen Position innerhalb der Nachricht enthalten.
        
        Exchange 2013 unterstützt außerdem die KQL-Syntax (Keyword Query Language) für Compliance-eDiscovery-Suchen.
        

        > [!NOTE]
        > Reguläre Ausdrücke werden in Compliance-eDiscovery-Suchen nicht unterstützt.

        
        Logische Operatoren wie **AND** und **OR** müssen in Großbuchstaben angegeben werden, damit diese nicht als Suchzeichenfolgen, sondern als Operatoren behandelt werden. Zum Vermeiden von Fehlern oder Fehlinterpretationen sollten Sie bei jeder Suche mit mehreren logischen Operatoren eindeutige Klammern verwenden. Wenn Sie z. B. nach Nachrichten suchen, die entweder "WortA" oder "WortB" UND "WortC" oder "WortD" enthalten, verwenden Sie die folgende Syntax: **(WortA OR WortB) AND (WortC OR WortD)**.
    
      - **Start- und Enddaten**   Compliance-eDiscovery-Suchen sind standardmäßig nicht auf einen Datumsbereich beschränkt. Wenn Sie nach Nachrichten suchen möchten, die innerhalb eines bestimmten Zeitraums gesendet wurden, können Sie die Suche durch die Angabe von Start- und Enddaten einschränken. Wenn Sie kein Enddatum angeben, werden bei jedem erneuten Starten der Suche die neuesten Ergebnisse zurückgegeben.
    
      - **Absender und Empfänger** Zum Einschränken einer Suche können Sie die Absender oder Empfänger von Nachrichten angeben. Sie können mithilfe von E-Mail-Adressen, Anzeigenamen oder des Namens einer Domäne nach Elementen suchen, die an alle Benutzer in der Domäne oder von diesen gesendet wurden. Wenn Sie beispielsweise nach E-Mails suchen möchten, die an eine oder von einer beliebigen Person bei Contoso, Ltd. gesendet wurde, geben Sie im Feld **Von** oder **An/Cc** in der Exchange-Verwaltungskonsole den Wert **@contoso.com** ein. Sie können den Wert **@contoso.com** auch in den Parametern *Senders* oder *Recipients* in der Shell angeben.
    
      - **Nachrichtentypen** Standardmäßig werden alle Nachrichtentypen durchsucht. Sie können die Suche einschränken, indem Sie spezifische Nachrichtentypen wie E-Mail, Kontakte, Dokumente, Journal, Besprechungen, Notizen und Lync-Inhalt auswählen.

Der folgende Screenshot zeigt ein Beispiel für eine Suchabfrage in der Exchange-Verwaltungskonsole.

![eDiscovery-Suchabfrage konfigurieren](images/Dd298021.a3626569-8700-421e-8b4e-7ec520b28272(EXCHG.150).png "eDiscovery-Suchabfrage konfigurieren")

Bei der Verwendung von Compliance-eDiscovery-Suchen müssen Sie außerdem Folgendes beachten:

  - **Anlagen** Bei einer Compliance-eDiscovery-Suche können Anlagen mit Unterstützung der Exchange-Suche durchsucht werden. Weitere Informationen finden Sie unter [Von der Exchange-Suche indizierte Dateiformate](file-formats-indexed-by-exchange-search-exchange-2013-help.md). In lokalen Bereitstellungen können Sie Unterstützung für weitere Dateitypen hinzufügen. Hierzu müssen Sie Suchfilter (auch als iFilter bezeichnet) für den Dateityp auf den Postfachservern installieren.

  - **Nicht durchsuchbare Elemente**   Bei nicht durchsuchbaren Elementen handelt es sich um Postfachelemente, die von der Exchange-Suche nicht indiziert werden können. Ursachen hierfür können nicht installierte Suchfilter für eine angefügte Datei, Filterfehler und verschlüsselte Nachrichten sein. Für eine erfolgreiche eDiscovery-Suche muss Ihre Organisation diese Elemente möglicherweise zur Überprüfung einschließen. Wenn Sie Suchergebnisse in ein Discoverypostfach kopieren oder in eine PST-DAtei exportieren, können Sie nicht durchsuchbare Elemente einschließen. Weitere Informationen finden Sie unter [Nicht durchsuchbare Elemente in Exchange eDiscovery](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md).

  - **Verschlüsselte Elemente** Da mittels S/MIME verschlüsselte Nachrichten nicht von der Exchange-Suche indiziert werden, können diese Nachrichten auch nicht bei einer Compliance-eDiscovery-Suche durchsucht werden. Wenn Sie die Option auswählen, um nicht durchsuchbare Elemente in Suchergebnissen zu berücksichtigen, werden diese S/MIME-verschlüsselten Nachrichten in das Discoverypostfach kopiert.

  - **IRM-geschützte Elemente** Durch die Verwaltung von Informationsrechten (Information Rights Management, IRM) geschützte Nachrichten werden von der Exchange-Suche indiziert und daher in die Suchergebnisse eingeschlossen, wenn sie den Abfrageparametern entsprechen. Nachrichten müssen mithilfe eines AD RMS-Clusters (Active Directory Rights Management Service, Active Directory Rechteverwaltungsdienst) in derselben Active Directory-Gesamtstruktur wie der Postfachserver geschützt werden. Weitere Informationen finden Sie unter [Verwaltung von Informationsrechten](information-rights-management-exchange-2013-help.md).
    

    > [!IMPORTANT]
    > Wenn die Exchange-Suche eine IRM-geschützte Nachricht nicht indizieren kann, weil entweder ein Entschlüsselungsfehler aufgetreten oder IRM deaktiviert ist, wird die geschützte Nachricht nicht zur Liste der fehlerhaften Elemente hinzugefügt. Wenn Sie die Option auswählen, um nicht durchsuchbare Elemente in Suchergebnissen zu berücksichtigen, fehlen in den Ergebnissen möglicherweise IRM-geschützte Nachrichten, die nicht entschlüsselt werden konnten.<BR>Wenn Sie IRM-geschützte Nachrichten in eine Suche einbeziehen möchten, können Sie eine weitere Suche erstellen, um Nachrichten mit RPMSG-Anlagen zurückzugeben. Sie können die Abfragezeichenfolge <CODE>attachment:rpmsg</CODE> verwenden, um alle IRM-geschützten Nachrichten in den angegebenen Postfächern zu durchsuchen – unabhängig davon, ob diese erfolgreich indiziert wurden oder nicht. Dies kann in Szenarien, in denen für eine Suche Nachrichten (einschließlich von IRM-geschützten Nachrichten, die erfolgreich indiziert wurden) zurückgegeben werden, die den Suchkriterien entsprechen, zu doppelt vorhandenen Suchergebnissen führen. Bei der Suche werden keine IRM-geschützten Nachrichten zurückgegeben, die nicht indiziert werden konnten.<BR>Beim Durchführen einer zweiten Suche nach allen IRM-geschützten Nachrichten werden auch IRM-geschützte Nachrichten berücksichtigt, die erfolgreich indiziert und bei der ersten Suche zurückgegeben wurden. Darüber hinaus besteht die Möglichkeit, dass die von der zweiten Suche zurückgegebenen IRM-geschützten Nachrichten nicht den für die erste Suche verwendeten Suchkriterien (z.&nbsp;B. Schlüsselwörter) entsprechen.



  - **Deduplizierung** Wenn Sie Suchergebnisse in ein Discoverypostfach kopieren, können Sie die *Deduplizierung* von Suchergebnissen aktivieren, um nur eine Instanz einer eindeutigen Nachricht in das Discoverypostfach zu kopieren. Eine Deduplizierung hat folgende Vorteile:
    
      - Niedrigere Speicheranforderungen und geringere Größe des Discoverypostfachs aufgrund der verringerten Anzahl von kopierten Nachrichten.
    
      - Geringere Arbeitslast für Discoverymanager, Rechtsberater und andere Personen, die die Ergebnisse der Suche durchsehen.
    
      - Geringere eDiscovery-Kosten, abhängig von der Anzahl von doppelten Elementen, die aus den Suchergebnissen ausgeschlossen werden.

Zurück zum Seitenanfang

## Schätzung, Vorschau und Kopieren von Suchergebnissen

Nach Abschluss einer Compliance-eDiscovery-Suche können Sie eine Schätzung der Suchergebnisse im Detailbereich der Exchange-Verwaltungskonsole anzeigen. Die Schätzwerte umfassen die Anzahl von zurückgegebenen Elementen und die Gesamtgröße dieser Elemente. Sie können auch eine Schlüsselwortstatistik anzeigen, die Details zur Anzahl von Elementen angibt, die für jedes Schlüsselwort in der Suchabfrage zurückgegeben wurden. Diese Informationen sind nützlich, um die Effektivität der Abfrage zu ermitteln. Wenn die Abfrage zu allgemein ist, wird möglicherweise ein zu großer Datensatz angezeigt, für dessen Durchsicht mehr Ressourcen benötigt und höhere eDiscovery-Kosten erzeugt werden. Wenn die Suche zu eingeschränkt ist, werden möglicherweise nur sehr wenige oder gar keine Datensätze angezeigt. Sie können die Schätzwerte und die Schlüsselwortstatistik dazu verwenden, die Abfrage gemäß Ihren Anforderungen zu optimieren.


> [!NOTE]
> In Exchange 2013 umfasst die Schlüsselwortstatistik auch statistische Werte zu Nicht-Schlüsselwort-Eigenschaften, wie z.&nbsp;B. Datumswerten, Nachrichtentypen und Absendern/Empfängern, die in einer Suchabfrage angegeben wurden.



Sie können auch eine Vorschau der Suchergebnisse anzeigen, um sicherzustellen, dass die zurückgegebenen Nachrichten die Inhalte umfassen, nach denen Sie suchen. Basierend auf der Vorschau können Sie die Abfrage bei Bedarf optimieren. Die eDiscovery-Suchvorschau zeigt die Anzahl von Nachrichten, die vom jedem durchsuchten Postfach zurückgegeben wurden, und gibt die Gesamtzahl an Nachrichten an, die von der Suche zurückgegeben wurden. Die Vorschau wird schnell generiert und erfordert nicht, dass Nachrichten in ein Discoverypostfach kopiert werden.

Wenn Sie mit der Menge und Qualität der Suchergebnisse zufrieden sind, können Sie sie in ein Discoverypostfach kopieren. Beim Kopieren von Nachrichten haben Sie folgende Möglichkeiten:

  - **Nicht durchsuchbare Elemente einschließen** Ausführliche Informationen zu den Elementtypen, die als nicht durchsuchbar eingestuft werden, finden Sie im vorherigen Abschnitt zu den Erwägungen bei der eDiscovery-Suche.

  - **Deduplizierung aktivieren** Mit der Deduplizierung wird der Datensatz verringert, indem nur eine Instanz eines eindeutigen Datensatzes eingeschlossen wird, wenn mehrere Instanzen in einem oder mehreren der durchsuchten Postfächer gefunden werden.

  - **Vollständige Protokollierung aktivieren** Standardmäßig wird beim Kopieren von Elementen nur die Basisprotokollierung aktiviert. Sie können die vollständige Protokollierung aktivieren, um Informationen zu allen bei der Suche zurückgegebenen Datensätzen einzuschließen.

  - **Nach Abschluss des Kopiervorgangs E-Mail an mich senden** Bei einer Compliance-eDiscovery-Suche können sehr viele Datensätze zurückgegeben werden. Das Kopieren der zurückgegebenen Nachrichten in ein Discoverypostfach kann sehr viel Zeit in Anspruch nehmen. Verwenden Sie diese Option, um per E-Mail benachrichtigt zu werden, wenn der Kopiervorgang abgeschlossen wurde. Für einen leichteren Zugriff bei Verwendung von Outlook Web App enthält die Benachrichtigung einen Link zum Speicherort in einem Discoverypostfach, in das die Nachrichten kopiert wurden.

Weitere Informationen finden Sie unter [Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach](copy-ediscovery-search-results-to-a-discovery-mailbox-exchange-2013-help.md).

Zurück zum Seitenanfang

## Exportieren von Suchergebnissen in eine PST-Datei

Nachdem die Suchergebnisse in ein Discoverypostfach kopiert wurden,können Sie sie in eine PST-Datei exportieren.

![Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei](images/Dd298021.4ddca8af-1af5-4cb2-852c-e3a292099a58(EXCHG.150).gif "Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei")

Nach dem Export der Suchergebnisse in eine PST-Datei können Sie oder andere Benutzer sie in Outlook öffnen, um die in den Suchergebnissen zurückgegebenen Nachrichten zu lesen oder zu drucken. Weitere Informationen finden Sie unter [Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei](export-ediscovery-search-results-to-a-pst-file-exchange-2013-help.md).

## Unterschiedliche Suchergebnisse

Da die Compliance-eDiscovery Live-Daten durchsucht, ist es möglich, dass zwei Suchläufe derselben Inhaltsquellen mit derselben Suchabfrage unterschiedliche Ergebnisse zurückgeben. Die geschätzten Suchergebnisse können ebenfalls von den tatsächlichen Suchergebnissen abweichen, die in ein Discoverypostfach kopiert werden. Das passiert auch, wenn dieselbe Suche innerhalb kurzer Zeit wiederholt wird. Es gibt verschiedene Faktoren, die sich auf die Konsistenz der Suchergebnisse auswirken:

  - Die kontinuierliche Indizierung eingehender E-Mails, da die Exchange-Suche ständig die Postfachdatenbanken und die Transportpipelines Ihrer Organisation durchforstet und indiziert.

  - Löschen von E-Mails durch Benutzer oder automatisierte Prozesse.

  - Massenimport von großen Mengen an E-Mails, deren Indizierung Zeit erfordert.

Falls Sie unterschiedliche Ergebnisse für dieselbe Suche erhalten, erwägen Sie die Aufbewahrung von Postfächern, um den Inhalt beizubehalten, führen Sie die Suche außerhalb der Spitzenzeiten durch oder lassen Sie genügend Zeit nach dem Importieren großer Mengen an E-Mails.

## Protokollierung für Compliance-eDiscovery-Suchen

Für Compliance-eDiscovery-Suchen stehen zwei Arten von Protokollierung zur Verfügung:

  - **Basisprotokollierung** Die Basisprotokollierung ist standardmäßig für alle Compliance-eDiscovery-Suchen aktiviert. Sie schließt Informationen über die Suche und den Benutzer ein, der die Suche durchgeführt hat. Die mit der Basisprotokollierung erfassten Informationen werden im Nachrichtentext der E-Mail angezeigt, die an das Postfach gesendet wird, in dem die Suchergebnisse gespeichert werden. Die Nachricht befindet sich in dem Ordner, der zum Speichern der Suchergebnisse erstellt wurde.

  - **Vollständige Protokollierung**   Die vollständige Protokollierung umfasst Informationen über alle von der Suche zurückgegebenen Nachrichten. Diese Informationen werden in einer durch Trennzeichen getrennten Datei (CSV-Datei) bereitgestellt und an die E-Mail-Nachricht angefügt, welche die Informationen der Basisprotokollierung enthält. Der Name der Suche wird als Name der CSV-Datei verwendet. Diese Informationen können aus Gründen der Einhaltung von Vorschriften oder für Aufzeichnungszwecke erforderlich sein. Zur Aktivierung der vollständigen Protokollierung müssen Sie die Option **Vollständige Protokollierung aktivieren** auswählen, wenn Sie mithilfe der Exchange-Verwaltungskonsole Suchergebnisse in ein Discoverypostfach kopieren. Wenn Sie die Shell verwenden, geben Sie die vollständige Protokollierung über den Parameter *LogLevel* an.


> [!NOTE]
> Beim Verwenden der Shell zum Erstellen oder Ändern einer Compliance-eDiscovery-Suche können Sie die Protokollierung auch deaktivieren.



Neben dem Suchprotokoll, das beim Kopieren von Suchergebnissen in ein Discoverypostfach erstellt wird, protokolliert Exchange auch von der Exchange-Verwaltungskonsole oder der Shell verwendete Cmdlets zum Erstellen, Ändern oder Entfernen von Compliance-eDiscovery-Suchen. Diese Informationen werden in den Administratorüberwachungsprotokolleinträgen erfasst. Weitere Informationen finden Sie unter [Administratorüberwachungsprotokollierung](administrator-audit-logging-exchange-2013-help.md).

Zurück zum Seitenanfang

## Compliance-eDiscovery und Compliance-Archiv

Im Rahmen von eDiscovery-Anforderungen ist es möglicherweise erforderlich, dass Sie Postfachinhalte aufbewahren, bis ein Rechtsstreit oder eine Untersuchung beendet ist. Nachrichten, die vom Postfachbenutzer oder durch andere Prozesse gelöscht oder geändert wurden, müssen ebenfalls aufbewahrt werden. In Exchange 2013 wird dies über den Einsatz eines Compliance-Archivs erreicht. Weitere Informationen finden Sie unter [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md).

In Exchange 2013 können Sie den neuen Assistenten für **Compliance-eDiscovery und -Archiv** dazu verwenden, um Elemente zu durchsuchen und diese so lange aufzubewahren, wie dies aufgrund von eDiscovery- oder anderen geschäftlichen Anforderungen erforderlich ist. Wenn Sie dieselbe Suche für Compliance-eDiscovery und Compliance-Archiv verwenden, müssen Sie Folgendes beachten:

  - Die Option zum Durchsuchen aller Postfächer kann nicht verwendet werden. Sie müssen die gewünschten Postfächer oder Verteilergruppen auswählen.

  - Sie können eine Compliance-eDiscovery-Suche nicht entfernen, wenn die Suche auch für ein Compliance-Archiv verwendet wird. Sie müssen zuerst die Compliance-Archiv-Option in einer Suche deaktivieren und die Suche dann entfernen.

## Aufbewahrung von Postfächern zu Compliance-eDiscovery-Zwecken

Wenn ein Mitarbeiter eine Organisation verlässt, wird das Mitarbeiterpostfach in der Regel deaktiviert oder entfernt. Wenn Sie ein Postfach deaktivieren, wird es vom Benutzerkonto getrennt, verbleibt jedoch für einen bestimmten Zeitraum (standardmäßig 30 Tage) weiterhin in der Postfachdatenbank. Der Assistent für verwaltete Ordner verarbeitet keine getrennten Postfächer, und Aufbewahrungsrichtlinien werden in diesem Zeitraum nicht angewendet. Sie können die Inhalte eines getrennten Postfachs nicht durchsuchen. Bei Ablauf des für die Postfachdatenbank konfigurierten Aufbewahrungszeitraums für gelöschte Postfächer wird das Postfach aus der Postfachdatenbank entfernt.


> [!IMPORTANT]
> In Exchange Online kann die Compliance-eDiscovery-Funktion Inhalte in inaktiven Postfächern durchsuchen. Inaktive Postfächer sind Postfächer, die in einem Compliance-Archiv platziert oder einem Beweissicherungsverfahren unterliegen und anschließend entfernt werden. Inaktive Postfächer werden so lange beibehalten, bis sie im Archiv abgelegt werden. Nachdem ein inaktives Postfach aus dem Compliance-Archiv entfernt oder das Beweissicherungsverfahren aufgehoben wurde, wird es endgültig gelöscht. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/dn144876(v=exchg.150)">Verwalten inaktiver Postfächer in Exchange Online</A>.



Wenn es in lokalen Bereitstellungen in Ihrer Organisation erforderlich ist, Aufbewahrungseinstellungen auf Nachrichten von Mitarbeitern anzuwenden, die nicht länger in der Organisation tätig sind, oder wenn Sie ein Postfach eines ehemaligen Mitarbeiters für eine fortlaufende oder zukünftige eDiscovery-Suche beibehalten müssen, dürfen Sie das Postfach weder deaktivieren noch entfernen. Sie können die folgenden Schritte ausführen, um sicherzustellen, dass kein Zugriff auf das Postfach möglich ist und keine neuen Nachrichten an das Postfach übermittelt werden.

1.  Deaktivieren Sie das Active Directory-Benutzerkonto über das Snap-In **Active Directory-Benutzer und -Computer** oder andere Active Directory-Tools oder -Skripts für die Kontobereitstellung. Auf diese Weise wird eine Postfachanmeldung mit dem zugeordneten Benutzerkonto verhindert.
    

    > [!IMPORTANT]
    > Benutzer mit Vollzugriff für das Postfach können weiterhin auf das Postfach zugreifen. Wenn Sie den Zugriff durch andere Personen verhindern möchten, müssen Sie den Vollzugriff auf das Postfach deaktivieren. Informationen zum Aufheben von Postfachberechtigungen für den Vollzugriff auf ein Postfach finden Sie unter <A href="manage-permissions-for-recipients-exchange-online-help.md">Verwalten von Berechtigungen für Empfänger</A>.



2.  Legen Sie den Grenzwert für die Größe der Nachrichten, die über das Postfach gesendet oder empfangen werden können, auf einen sehr niedrigen Wert fest, beispielsweise auf 1 KB. Auf diese Weise wird verhindert, dass neue E-Mails über das Postfach gesendet oder empfangen werden. Weitere Informationen finden Sie unter [Konfigurieren von Beschränkungen der Nachrichtengröße für ein Postfach](configure-message-size-limits-for-a-mailbox-exchange-2013-help.md).

3.  Konfigurieren Sie Übermittlungseinschränkungen für das Postfach, sodass niemand Nachrichten an das Postfach senden kann. Weitere Informationen finden Sie unter [Konfigurieren von Nachrichtenübermittlungseinschränkungen für ein Postfach](configure-message-delivery-restrictions-for-a-mailbox-exchange-2013-help.md).


> [!IMPORTANT]
> Sie müssen die oben genannten Schritte und weitere Prozesse zur Kontoverwaltung ausführen, die in Ihrer Organisation erforderlich sind, jedoch ohne das Postfach zu deaktivieren oder zu entfernen oder das zugeordnete Benutzerkonto zu entfernen.



Wenn Sie die Postfachaufbewahrung zur Verwaltung der Nachrichtenaufbewahrung oder für die Compliance-eDiscovery-Suche implementieren möchten, müssen Sie die Mitarbeiterfluktuation berücksichtigen. Die langfristige Aufbewahrung von Postfächern ehemaliger Mitarbeiter belegt zusätzlichen Speicherplatz auf den Postfachservern und vergrößert die Active Directory-Datenbank, da das zugeordnete Benutzerkonto für denselben Zeitraum beibehalten werden muss. Zusätzlich kann es erforderlich sein, die Prozesse für Kontobereitstellung und -verwaltung in Ihrer Organisation zu ändern.

Zurück zum Seitenanfang

## Compliance-eDiscovery-Begrenzungen und Einschränkungsrichtlinien

In Exchange 2013 und Exchange Online werden die einsetzbaren Ressourcen für Compliance-eDiscovery-Suchen über Einschränkungsrichtlinien gesteuert.

Die Standardeinschränkungsrichtlinie enthält folgende Parameter.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
<th>Standardwert</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DiscoveryMaxConcurrency</p></td>
<td><p>Die maximale Anzahl der Compliance-eDiscovery-Suchen, die in Ihrer Organisation gleichzeitig ausgeführt werden können</p></td>
<td><p>2</p>

> [!NOTE]
> Wenn eine eDiscovery-Suche gestartet wird, während zwei andere Suchvorgänge ausgeführt werden, wird die dritte Suche nicht in die Warteschlange eingereiht, sondern es tritt bei dieser ein Fehler auf. Sie müssen warten, bis eine der vorherigen Suchen abgeschlossen ist, bevor sie eine neue Suche starten können.


</td>
</tr>
<tr class="even">
<td><p>DiscoveryMaxMailboxes</p></td>
<td><p>Die maximale Anzahl von Postfächern, die in einer einzelnen Compliance-eDiscovery-Suche durchsucht werden können.</p></td>
<td><p>Exchange Online: 10,0001</p>
<p>Exchange 2013: 5,000</p></td>
</tr>
<tr class="odd">
<td><p>DiscoveryMaxStatsSearchMailboxes</p></td>
<td><p>Die maximale Anzahl von Postfächern, die in einer einzelnen Compliance-eDiscovery-Suche durchsucht werden können, die die Anzeige von Schlüsselwortstatistiken erlaubt.</p></td>
<td><p>100</p>

> [!NOTE]
> Nach der Ausführung einer eDiscovery-Suchergebnisschätzung können Sie die Schlüsselwortstatistik anzeigen. Diese Statistik enthält detaillierte Informationen über die Anzahl der Elemente, die für jedes in der Suchanfrage verwendete Schlüsselwort zurückgegeben werden. Wenn mehr als 100 Quellpostfächer in die Suche einbezogen werden, wird beim Versuch, die Schlüsselwortstatistik anzuzeigen, eine Fehlermeldung zurückgegeben.


</td>
</tr>
<tr class="even">
<td><p>DiscoveryMaxKeywords</p></td>
<td><p>Die maximale Anzahl von Schlüsselwörtern, die in einer einzelnen Compliance-eDiscovery-Suche angegeben werden können.</p></td>
<td><p>500</p></td>
</tr>
<tr class="odd">
<td><p>DiscoveryMaxSearchResultsPageSize</p></td>
<td><p>Die maximale Anzahl von Elementen, die auf einer einzelnen Vorschauseite der Compliance-eDiscovery-Suchergebnisse angezeigt werden.</p></td>
<td><p>200</p></td>
</tr>
<tr class="even">
<td><p>DiscoverySearchTimeoutPeriod</p></td>
<td><p>Die Zeitdauer in Minuten, während der eine Compliance-eDiscovery-Suche ausgeführt wird, bevor eine Zeitüberschreitung auftritt.</p></td>
<td><p>10 Minuten</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> 1&nbsp;&nbsp;&nbsp;Wenn Sie eine eDiscovery-Suche über das eDiscovery Center in SharePoint Online in einer Office 365-Organisation starten, können Sie maximal 1500 Postfächer in einem einzelnen Suchvorgang durchsuchen.



In Exchange Server 2013 können Sie die Standardwerte dieser Parameter gemäß Ihren Anforderungen ändern, oder Sie können zusätzliche Einschränkungsrichtlinien erstellen und diese Benutzern mit delegierten Discoveryverwaltungsberechtigungen zuweisen. In Exchange Online können die Standardwerte für diese Einschränkungsparameter nicht geändert werden.

## Dokumentation zu Compliance-eDiscovery

Die folgende Tabelle enthält Links zu Themen, in denen Sie weitere Informationen zu Compliance-eDiscovery und dessen Verwaltung finden.


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
<td><p><a href="assign-ediscovery-permissions-in-exchange-exchange-2013-help.md">Zuweisen von eDiscovery-Berechtigungen in Exchange</a></p></td>
<td><p>Erfahren Sie, wie Sie einem Benutzer in der Exchange-Verwaltungskonsole Zugriff auf Compliance-eDiscovery zum Durchsuchen von Exchange-Postfächern gewähren. Wenn Sie einen Benutzer zur Rollengruppe &quot;Discoveryverwaltung&quot; hinzufügen, kann dieser auch das eDiscovery Center in SharePoint 2013 und SharePoint Online verwenden, um Exchange-Postfächer zu durchsuchen.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-a-discovery-mailbox-exchange-2013-help.md">Erstellen eines Discoverypostfachs</a></p></td>
<td><p>Erfahren Sie, wie Sie mit der Shell ein Discoverypostfach erstellen und Zugriffsberechtigungen zuweisen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="create-an-in-place-ediscovery-search-exchange-2013-help.md">Erstellen einer Compliance-eDiscovery-Suche</a></p></td>
<td><p>Erfahren Sie, wie Sie eine Compliance-eDiscovery-Suche erstellen und wie Sie eDiscovery-Suchergebnisse schätzen und eine Vorschau davon anzeigen.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=506799">Nachrichteneigenschaften und Suchoperatoren für Compliance-eDiscovery</a></p></td>
<td><p>Erfahren Sie, welche E-Mail-Nachrichteneigenschaften mithilfe der Compliance-eDiscovery-Funktion durchsucht werden können. Dieses Thema bietet Syntaxbeispiele für jede Eigenschaft, Informationen zu Suchoperatoren wie <strong>AND</strong> und <strong>OR</strong> sowie zu anderen Suchabfragemethoden wie z. B. Verwenden doppelter Anführungszeichen (&quot; &quot;) und Präfixplatzhaltern.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/de-de/library/dn798915(v=exchg.150)">Suchbeschränkungen für Compliance-eDiscovery in Exchange Online</a></p></td>
<td><p>Erfahren Sie über die Beschränkungen für Compliance-eDiscovery in Exchange Online, mit denen die Integrität und Qualität von eDiscovery-Diensten für Office 365-Organisationen sichergestellt werden.</p></td>
</tr>
<tr class="even">
<td><p><a href="start-or-stop-an-in-place-ediscovery-search-exchange-2013-help.md">Starten oder Stoppen einer Compliance-eDiscovery-Suche</a></p></td>
<td><p>Erfahren Sie, wie Sie eDiscovery-Suchen starten, beenden und neu starten.</p></td>
</tr>
<tr class="odd">
<td><p><a href="modify-an-in-place-ediscovery-search-exchange-2013-help.md">Ändern einer Compliance-eDiscovery-Suche</a></p></td>
<td><p>Erfahren Sie, wie Sie eine vorhandene eDiscovery-Suche ändern.</p></td>
</tr>
<tr class="even">
<td><p><a href="copy-ediscovery-search-results-to-a-discovery-mailbox-exchange-2013-help.md">Kopieren der eDiscovery-Suchergebnisse in ein Discoverypostfach</a></p></td>
<td><p>Erfahren Sie, wie Sie die Ergebnisse einer eDiscovery-Suche in ein Discoverypostfach kopieren.</p></td>
</tr>
<tr class="odd">
<td><p><a href="export-ediscovery-search-results-to-a-pst-file-exchange-2013-help.md">Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei</a></p></td>
<td><p>Erfahren Sie, wie Sie die Ergebnisse einer eDiscovery-Suche in eine PST-Datei exportieren.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-a-custom-management-scope-for-in-place-ediscovery-searches-exchange-2013-help.md">Erstellen eines benutzerdefinierten Verwaltungsbereichs für die Compliance-eDiscovery-Suche</a></p></td>
<td><p>Erfahren Sie, wie Sie mit benutzerdefinierten Verwaltungsbereichen die Anzahl der Postfächer einschränken können, die ein Discovery-Manager durchsuchen kann.</p></td>
</tr>
<tr class="odd">
<td><p><a href="remove-an-in-place-ediscovery-search-exchange-2013-help.md">Entfernen einer Compliance-eDiscovery-Suche</a></p></td>
<td><p>Erfahren Sie, wie Sie eine eDiscovery-Suche löschen.</p></td>
</tr>
<tr class="even">
<td><p><a href="search-for-and-delete-messages-admin-help-exchange-2013-help.md">Suchen nach und Löschen von Nachrichten – Administratorhilfe</a></p></td>
<td><p>Erfahren Sie, wie Sie mit dem Cmdlet <strong>Search-Mailbox</strong> E-Mail-Nachrichten suchen und löschen können.</p></td>
</tr>
<tr class="odd">
<td><p><a href="reduce-the-size-of-a-discovery-mailbox-in-exchange-exchange-2013-help.md">Verkleinern eines Discoverypostfachs in Exchange</a></p></td>
<td><p>Verwenden Sie dieses Verfahren, um ein Discoverypostfach, das größer als 50 GB ist, zu verkleinern.</p></td>
</tr>
<tr class="even">
<td><p><a href="delete-and-re-create-the-default-discovery-mailbox-in-exchange-exchange-2013-help.md">Löschen und Neuerstellen des Standarddiscoverypostfachs in Exchange</a></p></td>
<td><p>Erfahren Sie, wie Sie ein Standarddiscoverypostfach löschen, es neu erstellen und ihm dann erneut Berechtigungen zuweisen können. Verwenden Sie dieses Verfahren, wenn das Postfach die Größenbeschränkung von 50 GB überschritten hat und Sie die Suchergebnisse nicht benötigen.</p></td>
</tr>
<tr class="odd">
<td><p><a href="re-create-the-discovery-system-mailbox-exchange-2013-help.md">Re-create the Discovery system mailbox</a></p></td>
<td><p>Erfahren Sie, wie Sie das Discoverypostfach neu erstellen. Diese Aufgabe eignet sich nur für Exchange 2013-Organisationen.</p></td>
</tr>
<tr class="even">
<td><p><a href="using-oauth-authentication-to-support-ediscovery-in-an-exchange-hybrid-deployment-exchange-2013-help.md">Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung</a></p></td>
<td><p>Erfahren Sie mehr über die eDiscovery-Szenarien in einer hybriden Exchange-Bereitstellung, die es erforderlich machen, dass Sie die OAuth-Authentifizierung konfigurieren.</p></td>
</tr>
<tr class="odd">
<td><p><a href="configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md">Konfigurieren von Exchange für SharePoint eDiscovery Center</a></p></td>
<td><p>Erfahren Sie, wie Sie Exchange 2013 so konfigurieren, dass Sie das eDiscovery Center in SharePoint 2013 zum Durchsuchen von Exchange-Postfächern verwenden können.</p></td>
</tr>
<tr class="even">
<td><p><a href="unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md">Nicht durchsuchbare Elemente in Exchange eDiscovery</a></p></td>
<td><p>Erfahren Sie mehr über Postfachelemente, die nicht von der Exchange-Suche indiziert werden und in eDiscovery-Suchergebnissen als nicht durchsuchbare Elemente zurückgegeben werden.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu eDiscovery in Office 365, Exchange 2013, SharePoint 2013 und Lync 2013 finden Sie unter [Häufig gestellte Fragen zu eDiscovery (FAQ)](https://go.microsoft.com/fwlink/p/?linkid=386633).

Zurück zum Seitenanfang

