---
title: 'Zugriff auf Active Directory: Exchange 2013 Help'
TOCTitle: Zugriff auf Active Directory
ms:assetid: 61080b45-8bce-4c23-b744-ed264d5f0b7d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998561(v=EXCHG.150)
ms:contentKeyID: 50475797
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zugriff auf Active Directory

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Exchange Server 2013 speichert alle Konfigurations- und Empfängerinformationen in der Active Directory-Verzeichnisdienstdatenbank. Wenn ein Computer mit Exchange 2013 Informationen zu den Empfängern sowie zur Konfiguration der Exchange-Organisation benötigt, muss er Active Directory abfragen, um auf diese Informationen zugreifen zu können. Active Directory-Server müssen verfügbar sein, um eine ordnungsgemäße Funktionsweise von Exchange 2013 sicherstellen zu können.

In diesem Thema wird erläutert, wie Exchange 2013 Informationen in Active Directory speichert und abruft, damit Sie den Zugriff auf Active Directory planen können. In diesem Thema werden auch Probleme erläutert, an die Sie denken sollten, wenn Sie versuchen, gelöschte Exchange 2013 Active Directory-Objekte wiederherzustellen.

## In Active Directory gespeicherte Exchange-Informationen

In der Active Directory-Datenbank werden Informationen in drei Typen logischer Partitionen gespeichert. Diese werden in den folgenden Abschnitten beschrieben:

  - Schemapartition

  - Konfigurationspartition

  - Domänenpartition

## Schemapartition

In der Schemapartition werden zwei Arten von Informationen gespeichert:

  - **Schemaklassen** definieren alle Objekttypen, die in Active Directory erstellt und gespeichert werden können.

  - **Schemaattribute** definieren alle Eigenschaften, die zum Beschreiben der in Active Directory gespeicherten Objekte verwendet werden können.

Beim Installieren der ersten Exchange 2013-Serverrolle in der Gesamtstruktur oder beim Ausführen der Active Directory-Vorbereitung werden dem Active Directory-Schema durch die Active Directory-Vorbereitung viele Klassen und Attribute hinzugefügt. Die dem Schema hinzugefügten Klassen werden zum Erstellen Exchange-spezifischer Objekte (wie Agents und Connectors) verwendet. Die dem Schema hinzugefügten Attribute werden zum Konfigurieren der Exchange-spezifischen Objekte und der E-Mail-aktivierten Benutzer und Gruppen verwendet. Diese Attribute umfassen Eigenschaften wie MicrosoftOffice Outlook Web Access- und MicrosoftExchange Unified Messaging-Einstellungen (UM). Alle Domänencontroller und globalen Katalogserver in der Gesamtstruktur enthalten ein vollständiges Replikat der Schemapartition.

Weitere Informationen zu Schemaänderungen in Exchange 2013 finden Sie unter [Änderungen des Active Directory-Schemas in Exchange 2013](exchange-2013-active-directory-schema-changes-exchange-2013-help.md).

## Konfigurationspartition

In der Konfigurationspartition werden Informationen zur Gesamtstrukturkonfiguration gespeichert. Diese Konfigurationsinformationen umfassen die Konfiguration von Active Directory-Standorten, globalen Exchange-Einstellungen, Transporteinstellungen und Postfachrichtlinien. Jeder Konfigurationsinformationstyp wird in der Konfigurationspartition in einem Container gespeichert. Exchange-Konfigurationsinformationen werden in einem dem Dienstecontainer der Konfigurationspartition untergeordneten Ordner gespeichert. Die in diesem Container gespeicherten Informationen umfassen Folgendes:

  - Adresslisten

  - Adressbuchrichtlinien für Postfächer

  - Administrative Gruppen

  - Clientzugriffseinstellungen

  - Verbindungen

  - Einstellungen für mobile Postfächer

  - Globale Einstellungen

  - Überwachungseinstellungen

  - Systemrichtlinien

  - Container für Aufbewahrungsrichtlinien

  - Transporteinstellungen

Alle Domänencontroller und globalen Katalogserver in der Gesamtstruktur enthalten ein vollständiges Replikat der Konfigurationspartition.

## Domänenpartition

In der Domänenpartition werden Informationen in Standardcontainern und Organisationseinheiten gespeichert, die der Active Directory-Administrator erstellt. In diesen Containern werden domänenspezifische Objekte verwaltet. Diese Daten umfassen Exchange-Systemobjekte sowie Informationen zu den Computern, Benutzern und Gruppen in dieser Domäne. Wenn Exchange 2013 installiert ist, werden die Objekte in dieser Partition zur Unterstützung der Exchange-Funktionen von Exchange aktualisiert. Diese Funktionen wirken sich auf die Speicherung von und den Zugriff auf Empfängerinformationen aus.

Jeder Domänencontroller enthält ein vollständiges Replikat der Domänenpartition der Domäne, für die er autoritativ ist. Jeder globale Katalogserver in der Gesamtstruktur enthält eine Teilmenge der Informationen in jeder Domänenpartition der Gesamtstruktur.

## Zugriff auf Active Directory-Informationen in Exchange 2013

Exchange 2013 verwendet eine Active Directory-API, um auf in Active Directory gespeicherte Informationen zuzugreifen. Der Microsoft ExchangeActive Directory-Topologiedienst wird für alle Serverrollen von Exchange 2013 ausgeführt. Dieser Dienst liest Informationen aus allen Active Directory-Partitionen. Die abgerufenen Daten werden zwischengespeichert und von Exchange 2013-Servern verwendet, um den Active Directory-Standort aller Exchange-Dienste in der Organisation zu erkennen.

Weitere Informationen zur Topologie und Diensterkennung finden Sie unter [Planen der Verwendung von Active Directory-Standorten für das E-Mail-Routing](planning-to-use-active-directory-sites-for-routing-mail-exchange-2013-help.md).

Exchange 2013 ist eine für Active Directory-Standorte aktivierte Anwendung, die zur Optimierung des Netzwerkdatenverkehrs mit Verzeichnisservern kommuniziert, die sich am selben Standort wie der Exchange-Server befinden. Jede einzelne Exchange 2013-Organisationsserverrolle muss mit Active Directory kommunizieren, um Informationen zu den Empfängern und anderen Exchange 2013-Serverrollen abrufen zu können. Die von den einzelnen Serverrolle abgerufenen Daten werden in den folgenden Abschnitten beschrieben.

Standardmäßig erfolgt bei jedem Start eines Exchange 2013-Servers die Bindung an einen zufällig ausgewählten Domänencontroller sowie an einen globalen Katalogserver am eigenen Standort. Diese Informationen können über das Cmdlet **Get-ExchangeServer** in der Exchange-Verwaltungsshell angezeigt werden. Sie können auch das Cmdlet **Set-ExchangeServer** verwenden, um eine statische Liste mit Domänencontrollern zu konfigurieren, an die die Bindung eines Exchange 2013-Servers erfolgen soll. Eine andere Möglichkeit besteht in der Konfiguration einer Liste mit Domänencontrollern, die ausgeschlossen werden sollen.


> [!IMPORTANT]
> Ein Windows Server 2008-Domänencontroller kann als schreibgeschützter Verzeichnisserver konfiguriert werden. Diese Konfiguration ist geeignet, wenn Sie einen Domänencontroller oder einen globalen Katalogserver zu Authentifizierungs- und Autorisierungszwecken an einem Remotestandort bereitstellen möchten, Administratoren an diesem Standort jedoch nicht erlauben möchten, Änderungen in Active Directory zu schreiben. Ein Exchange 2013-Server kann jedoch an keinem Standort bereitgestellt werden, der nur schreibgeschützte Verzeichnisserver enthält.



## Postfachserverrolle

Die Postfachserverrolle speichert Konfigurationsinformationen zu Postfachbenutzern. Die Daten werden in Active Directory gespeichert. Für Exchange 2013 umfasst der Postfachserver zusätzlich alle traditionellen Serverkomponenten aus Exchange 2010: Clientzugriffsprotokolle, Transportdienst, Postfachdatenbanken und Unified Messaging. Der Postfachserver verarbeitet alle Vorgänge für die aktiven Postfächer auf diesem Server.

## Clientzugriffs-Serverrolle

In Exchange 2013 stellt der Clientzugriffsserver Authentifizierungs-, eingeschränkte Umleitungs- und Proxydienste bereit. Der Clientzugriffsserver führt kein Datenrendering durch. Der Clientzugriffsserver ist ein zustandsloser Thin Server. Auf einem Clientzugriffsserver werden keine Daten gespeichert oder in Warteschlangen gestellt. Der Clientzugriffsserver bietet alle üblichen Clientzugriffsprotokolle: HTTP, POP und IMAP und SMTP.

## Wiederherstellung gelöschter Exchange-Objekte

Der Active Directory-Papierkorb hilft, die Downtime des Verzeichnisdiensts zu minimieren, da versehentlich gelöschte Active Directory-Objekte aufbewahrt und wiederhergestellt werden können, ohne Active Directory-Daten aus Sicherungen wiederherstellen oder Active Directory-Domänendienste (AD DS) oder Domänencontroller neu starten zu müssen.

Der wichtigste Aspekt bei der Wiederherstellung gelöschter, zu Exchange gehöriger Active Directory-Objekte ist der, dass Exchange-Objekte nicht isoliert vorhanden sind. Wenn Sie beispielsweise einen Benutzer für E-Mail aktivieren, werden für diesen Benutzer verschiedene Richtlinien und Verknüpfungen auf der Grundlage Ihrer aktuellen Exchange-Konfiguration berechnet. Zwei Probleme können bei der Wiederherstellung eines gelöschten Exchange-Konfigurations- oder -Empfängerobjekts auftreten:

  - **Kollisionen**   Einige Exchange-Attribute müssen in einer Gesamtstruktur eindeutig sein. So dürfen Proxyadressen (E-Mail-Adressen) nicht für zwei verschiedene Benutzer gleich sein. Active Directory erzwingt keine eindeutigen Proxyadressen – die Eindeutigkeit wird von Exchange-Verwaltungstools überprüft. Exchange-Richtlinien für E-Mail-Adressen lösen mögliche Konflikte außerdem automatisch bei der auf deterministischen Regeln basierenden Proxyadressenzuweisung auf. Auf diese Weise ist es möglich, ein Exchange-Benutzerobjekt wiederherzustellen und damit für eine Kollision mit Proxyadressen oder anderen Attributen, die eindeutig sein sollten, zu sorgen.

  - **Fehlkonfigurationen**   Exchange verfügt über automatische Regeln, die verschiedene Richtlinien oder Einstellungen zuweisen. Wenn Sie einen Empfänger löschen und dann die Regeln oder Richtlinien ändern, kann das Wiederherstellen eines Exchange-Benutzerobjekts dazu führen, dass einem Benutzer die falsche Richtlinie (oder auch eine bereits nicht mehr vorhandene Richtlinie) zugewiesen wird.

Mithilfe der folgenden Richtlinien können Sie Probleme bei der Wiederherstellung gelöschter, zu Exchange gehörender Objekte vermeiden:

  - Wenn Sie ein Exchange-Konfigurationsobjekte mithilfe von Exchange-Verwaltungstools gelöscht haben, sollten Sie das Objekt nicht wiederherstellen. Erstellen Sie stattdessen das Objekt mit den Exchange-Verwaltungstools (Exchange Admin Center oder Exchange-Verwaltungsshell) neu.

  - Wenn Sie ein Exchange-Konfigurationsobjekt ohne Verwenden der Exchange-Verwaltungstools gelöscht haben, sollten Sie dieses so bald wie möglich wiederherstellen. Je mehr Verwaltungs- und Konfigurationsänderungen seit dem Löschvorgang im System vorgenommen wurde, desto wahrscheinlicher ist es, dass die Wiederherstellung der Objekte zu einer Fehlkonfiguration führt.

  - Wenn Sie gelöschte Exchange-Empfänger (Kontakte, Benutzer oder Verteilergruppen) wiederherstellen, achten Sie genau auf Kollisionen und Fehler im Zusammenhang mit den wiederhergestellten Objekten. Falls Exchange-Richtlinien oder andere Einstellungen in Bezug auf Empfänger seit dem Löschvorgang möglicherweise geändert wurden, wenden Sie aktuelle Richtlinien neu auf die wiederhergestellten Empfänger an, um sicherzustellen, dass diese richtig konfiguriert sind.

## Weitere Informationen

[Schrittweise Anleitung zum Active Directory-Papierkorb](https://go.microsoft.com/fwlink/p/?linkid=178720)

[Einführung in Verbesserungen des Active Directory-Verwaltungscenters (Level 100)](https://go.microsoft.com/fwlink/p/?linkid=267641)

[Erweiterte AD DS-Verwaltung mit dem Active Directory-Verwaltungscenter (Level 200)](https://go.microsoft.com/fwlink/p/?linkid=267642)

