---
title: 'IRM in Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: IRM in Exchange-Hybridbereitstellungen
ms:assetid: ba6ec48b-8f79-4807-b74b-fd442bbbe82f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659052(v=EXCHG.150)
ms:contentKeyID: 50477186
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# IRM in Exchange-Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

**Zusammenfassung:**  Funktionsweise von IRM in einer Exchange-Hybridumgebung und Konfigurieren von IRM für die Funktion zwischen Exchange Online und Ihren lokalen Exchange-Servern.

Die Verwaltung von Informationsrechten (Information Rights Management, IRM) unterstützt Sie beim Schutz vor dem Verlust vertraulicher Daten, indem ein dauerhafter Online- und Offlineschutz von E-Mail-Nachrichten und -Anlagen bereitgestellt wird. Sowohl Exchange in Ihrer lokalen Organisation und Exchange Online in Office 365 für Unternehmen unterstützen die Verwaltung von Verwaltungsrechten. Es gibt jedoch Unterschiede zwischen den beiden Implementierungen, und Sie müssen die Verwaltung von Informationsrechten in der Exchange Online-Organisation konfigurieren, bevor diese von Benutzern in dieser Organisation verwendet werden kann.

IRM verwendet die Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS), eine Komponente von Windows Server 2008 und höher. Die Rechteverwaltungsdienste gestatten es den Benutzern, durch Rechte geschützte Inhalte zu erstellen, z. B. E-Mail-Nachrichten und Anlagen. Anschließend können sie steuern, wie dieser Inhalt verwendet wird und an wen dieser verteilt wird. Benutzer können Vorlagen angeben, die bestimmen, wie der Inhalt verwendet werden kann. Ein Benutzer kann z. B. angeben, dass eine E-Mail nicht an andere Empfänger weitergeleitet werden darf oder dass Informationen in der Nachricht nicht kopiert werden können.

Weitere Informationen zu IRM in Exchange 2010 erhalten Sie unter: [Grundlegendes zu Information Rights Management](https://technet.microsoft.com/de-de/library/dd638140\(v=exchg.141\).aspx).

Weitere Informationen zur Verwaltung von Informationsrechten in Exchange 2013 und Exchange 2016 finden Sie unter [Verwaltung von Informationsrechten](https://technet.microsoft.com/de-de/library/dd638140\(v=exchg.150\)).

Weitere Informationen zu AD RMS finden Sie unter [Active Directory-Rechteverwaltungsdienste (Übersicht)](http://go.microsoft.com/fwlink/p/?linkid=215243).

## Unterschiede zwischen IRM in Exchange lokal und Exchange Online

Die IRM-Funktion, die in Ihrer lokalen Exchange-Organisation verfügbar ist, unterscheidet sich von der in der Exchange Online-Organisation verfügbaren Funktion. In der folgenden Tabelle wird eine Übersicht über die Features und Funktionen bereitgestellt, die in den einzelnen Organisationen verfügbar sind. (Weitere Informationen zu diesen Features finden Sie unter: [Verwaltung von Informationsrechten](https://technet.microsoft.com/de-de/library/dd638140\(v=exchg.150\)))

### Verfügbare IRM-Funktionen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Feature</th>
<th>Verfügbar in Exchange 2007 und früher</th>
<th>Verfügbar in Exchange 2010</th>
<th>Verfügbar in Exchange Online und Exchange 2013 und höher</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Manueller Schutz von Nachrichten in Outlook</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Manueller Schutz von Nachrichten in Outlook Web App</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Anzeigen von IRM-geschützten Nachrichten in Outlook</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Anzeigen von IRM-geschützten Nachrichten in Outlook Web App</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>IRM-Vorlizenzierungs-Agent</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>RMS-Richtlinienvorlagen</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Transportentschlüsselung</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Journalberichtentschlüsselung</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Suche und Discovery-Entschlüsselung</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Automatische Outlook-Schutzregeln</p></td>
<td><p>Nein</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Automatische Transportschutzregeln</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


## IRM in Hybridbereitstellungen

Exchange verwendet AD RMS-Server in der Active Directory-Gesamtstruktur, in der der Exchange-Server installiert ist. Für Ihre lokalen Exchange-Server werden die AD RMS-Server verwendet. Für Ihre Exchange Online-Organisation werden AD RMS-Server verwendet, die innerhalb der Office 365-Rechenzentren verwaltet werden. Die in den einzelnen Exchange-Organisationen verwendete AD RMS-Konfiguration ist von anderen AD RMS-Bereitstellungen unabhängig.

Die AD RMS-Konfiguration, und daher die IRM-Konfiguration, wird nicht automatisch zwischen Ihrer lokalen Exchange-Organisation und der Exchange Online-Organisation repliziert. Von Ihnen definierte AD RMS-Vorlagen werden nicht automatisch in die Exchange Online-Organisation kopiert. Wenn dieselben AD RMS-Vorlagen in der Exchange Online-Organisation verfügbar sein sollen, müssen Sie die Vorlagen manuell aus Ihrer lokalen Organisation exportieren und auf die Office 365-Organisation anwenden. Siehe Konfiguration von IRM in Hybrid-Bereitstellungen weiter unten in diesem Thema.

## Benutzerführung

Die auf einen Benutzer angewendete IRM-Konfiguration hängt vom Client ab, den der Benutzer verwendet, und vom Speicherort des Benutzerpostfachs. In der folgenden Tabelle wird der von einem Benutzer verwendete AD RMS-Server angezeigt.

### Aktiver AD RMS-Server

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Client</th>
<th>Lokales Postfach</th>
<th>Exchange Online-Postfach</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook-Desktopclients</p></td>
<td><p>Lokaler AD RMS</p></td>
<td><p>Lokaler AD RMS</p></td>
</tr>
<tr class="even">
<td><p>Outlook im Web</p></td>
<td><p>Lokaler AD RMS</p></td>
<td><p>Exchange Online-AD RMS</p></td>
</tr>
<tr class="odd">
<td><p>ActiveSync-Gerät</p></td>
<td><p>Lokaler AD RMS</p></td>
<td><p>Exchange Online-AD RMS</p></td>
</tr>
</tbody>
</table>


In Abhängigkeit davon, welche AD RMS-Konfiguration Sie in Ihren lokalen und Exchange Online-Organisationen einrichten, können einem Benutzer, der Outlook 2007 und Outlook im Web verwendet, möglicherweise abweichende AD RMS-Vorlagen angezeigt werden. Aus diesem Grund wird dringend empfohlen, dass Sie dieselben Vorlagen sowohl auf Ihre lokalen als auch auf Exchange Online-Organisationen anwenden.

Für Outlook-Clientbenutzer sollte sich unabhängig davon kein Unterschied bei der IRM-Erfahrung ergeben, ob sich ihr Postfach in der lokalen oder in der Exchange Online-Organisation befindet.

Ein Outlook im Web-Benutzer, dessen Postfach sich auf einem lokalen Exchange-Server befindet, kann durch Rechte geschützte Nachrichten nur öffnen, nachdem das Internet Explorer-Add-In für die Rechteverwaltung installiert wurde. Sie können weder auf Nachrichten antworten, die durch Rechte geschützt sind, noch neue durch Rechte geschützte Nachrichten erstellen.

Ein Outlook im Web-Benutzer, dessen Postfach sich in Exchange Online befindet, kann durch Rechte geschützte Nachrichten ohne zusätzliche Software öffnen, beantworten und neue durch Rechte geschützte Nachrichten erstellen.

## Serverfunktionalität

Lokale Exchange-Server verwenden den AD RMS-Vorlizenzierungs-Agent zum Entschlüsseln von Nachrichten, die durch Rechte geschützt sind, damit die Benutzer keine Anmeldeinformationen bereitstellen müssen, wenn sie diese Nachrichten öffnen. Der lokale Exchange-Server kontaktiert den lokalen AD RMS-Server, um die Verwendungsrichtlinien und -rechte zu überprüfen und die Autorisierung zum Entschlüsseln der Nachricht anzufordern.

Die Exchange Online-Organisation stellt verschiedene IRM-bezogene Funktionen bereit, die Exchange Online-AD RMS nutzen. Diese Funktionen, z. B. die Journalberichtentschlüsselung, stellen den Inhalt von Nachrichten, die durch Rechte geschützt sind, für Exchange-Dienste zur weiteren Verarbeitung zur Verfügung. Die verschlüsselten Inhalte einer Journalnachricht können z. B. zusammen mit der ursprünglichen, durch Rechte geschützten Nachricht gespeichert werden, um eine einfachere Erkennung zu ermöglichen. Zusätzlich können IRM-Vorlagen automatisch auf Nachrichten angewendet werden, die entweder Outlook-Schutzregeln oder -Transportregeln verwenden, um sicherzustellen, dass die Nachrichten hinsichtlich dem Informationsschutz den Unternehmensrichtlinien entsprechen.

## Konfiguration von IRM in Hybrid-Bereitstellungen

IRM in Exchange ist von der Bereitstellung von AD RMS in der Active Directory-Gesamtstruktur abhängig, in der sich der Exchange-Server befindet. Die AD RMS-Konfiguration wird nicht automatisch zwischen den lokalen Organisationen und den Exchange Online-Organisationen synchronisiert. Sie müssen die AD RMS-Konfiguration, die sogenannte vertrauenswürdige Veröffentlichungsdomäne (Trusted Publishing Domain, TPD), manuell von Ihrem lokalen AD RMS-Server exportieren und diese Konfiguration in die Exchange Online-Organisation importieren. Die vertrauenswürdige Veröffentlichungsdomäne enthält die AD RMS-Konfiguration, einschließlich der Vorlagen, die von der Exchange Online-Organisation für die Verwaltung der Informationsrechte benötigt werden.

Weitere Informationen finden Sie unter [Aspekte zur vertrauenswürdigen AD RMS-Veröffentlichungsdomäne](http://go.microsoft.com/fwlink/p/?linkid=215244).

Zusätzlich zum Anwenden Ihrer lokalen AD RMS-Konfiguration auf die Exchange Online-Organisation müssen Sie sicherstellen, dass Outlook- und ActiveSync-Clients außerhalb Ihres lokalen Netzwerks eine Verbindung mit Ihren AD RMS-Servern herstellen können. Dies ist erforderlich, wenn diese Clients Zugriff auf durch Rechte geschützte Nachrichten außerhalb Ihres lokalen Netzwerks erhalten sollen.

Nachdem Sie das lokale Netzwerk konfiguriert und die Daten der vertrauenswürdigen Veröffentlichungsdomäne exportiert haben, müssen Sie die Exchange Online-Organisation konfigurieren, indem Sie die Daten der vertrauenswürdigen Veröffentlichungsdomäne importieren und die Verwaltung der Informationsrechte aktivieren.


> [!NOTE]
> Bei jeder Änderung Ihrer lokalen AD&nbsp;RMS-Konfiguration müssen Sie die neue Konfiguration manuell in der Exchange Online-Organisation anwenden. Dazu exportieren Sie die Daten der vertrauenswürdigen Veröffentlichungsdomäne vom lokalen AD&nbsp;RMS-Server und importieren sie in die Exchange Online-Organisation.



## Konfigurieren von IRM in Exchange-Hybridbereitstellungen

Wenn Sie die IRM in Ihrer lokalen Exchange-Organisation verwenden und die Exchange Online-Benutzer ebenfalls IRM verwenden sollen, müssen Sie folgende Aufgaben ausführen:

1.  Konfigurieren Sie den lokalen Active Directory-Rechteverwaltungsdienst (AD RMS)-Server.

2.  Aktivieren Sie IRM in Ihrer Exchange Online-Organisation.

3.  Verteilen Sie die importierten AD RMS-Vorlagen an Benutzer in der Exchange Online-Organisation.

## Wie konfiguriere ich lokale AD RMS-Server?

Zum Konfigurieren von IRM in einer Hybridbereitstellung müssen Sie Windows PowerShell für den Zugriff auf die lokalen AD RMS-Server verwenden. Weitere Informationen finden Sie unter: [Verwenden von Windows PowerShell zum Verwalten von AD RMS](http://go.microsoft.com/fwlink/p/?linkid=214938)

Gehen Sie wie folgt vor, um Daten der vertrauenswürdigen Veröffentlichungsdomäne (Trusted Publishing Domain, TPD) von dem lokalen AD RMS-Server zu exportieren und dann den Zugriff auf den AD RMS-Server für externe Clients zu konfigurieren.

1.  Exportieren Sie TPD-Daten aus der lokalen Organisation. Weitere Informationen finden Sie unter: [Exportieren einer vertrauenswürdigen Veröffentlichungsdomäne](http://go.microsoft.com/fwlink/p/?linkid=214942)

2.  Konfigurieren Sie den Zugriff auf AD RMS-Server für externe Clients. Weitere Informationen finden Sie unter: [Hinzufügen einer Extranet-Cluster-URL](http://go.microsoft.com/fwlink/p/?linkid=214945)

## Wie aktiviere ich IRM in der Exchange Online-Organisation?

Wenn Sie die TPD-Daten von den lokalen AD RMS-Servern exportiert haben, müssen Sie diese Daten in die Exchange Online-Organisation importieren und dann IRM aktivieren.

1.  Importieren Sie die TPD-Daten in die Exchange Online-Organisation.
    
        Import-RMSTrustedPublishingDomain -FileData $( [Byte[]] (Get-Content -Encoding Byte -Path "<Path to exported TPD file>" -ReadCount 0))

2.  Aktivieren Sie IRM in der Exchange Online-Organisation.
    
        Set-IRMConfiguration -InternalLicensingEnabled $True

## Wie verteile ich AD RMS-Vorlagen in der Exchange Online-Organisation?

Nachdem Sie IRM in der Exchange Online-Organisation aktiviert haben, müssen Sie die importierten AD RMS-Vorlagen verteilen. Folgende Exchange Online-Benutzer und -Funktionen verwenden AD RMS-Vorlagen:

  - Outlook im Web-Benutzer

  - Exchange ActiveSync-Benutzer

  - Transportregeln

  - Journalberichtentschlüsselung

  - Outlook-Schutzregeln

<!-- end list -->

1.  Rufen Sie in der Exchange Online-Organisation eine Liste mit AD RMS-Vorlagen ab.
    
        Get-RMSTemplate -Type All

2.  Verteilen Sie die importierten AD RMS-Vorlagen an Benutzer und Funktionen in der Exchange Online-Organisation.
    
        Set-RMSTemplate <template name> -Type Distributed
    

    > [!NOTE]
    > Sie können die AD RMS-Vorlage "Nicht weiterleiten" nicht ändern.



3.  Wiederholen Sie Schritt 2 für jede AD RMS-Vorlage, die verteilt werden soll.

## Woher weiß ich, dass der Vorgang erfolgreich war?

Outlook im Web-Benutzer müssen in der Lage sein, AD RMS-Vorlagen auf neue Nachrichten anzuwenden. Outlook im Web- und Exchange ActiveSync-Benutzer müssen in der Lage sein, Nachrichten zu lesen, auf die AD RMS-Vorlagen angewendet wurden. Außerdem sollten alle AD RMS-Vorlagen, die von der lokalen Organisation importiert wurden, aufgelistet werden, wenn Sie das Cmdlet **Get-RMSTemplate** ausführen.

Führen Sie folgenden Befehl in der Exchange Online-Organisation aus.

    Get-RMSTemplate 

Weitere Informationen finden Sie unter: [Verwaltung von Informationsrechten in Outlook Web App](https://technet.microsoft.com/de-de/library/dd876891\(v=exchg.150\))

