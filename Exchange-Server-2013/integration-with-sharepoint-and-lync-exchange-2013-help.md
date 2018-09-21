---
title: 'Integration in SharePoint und Lync: Exchange 2013 Help'
TOCTitle: Integration in SharePoint und Lync
ms:assetid: 056b29f6-e0e9-4974-b763-002518857a93
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150480(v=EXCHG.150)
ms:contentKeyID: 50474971
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Integration in SharePoint und Lync

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

MicrosoftExchange Server 2013 umfasst eine Vielzahl von Funktionen, die sich mit Microsoft SharePoint 2013 und Microsoft Lync 2013 integrieren lassen. Zusammen bieten diese Produkte eine breite Palette an Features, die Szenarien wie Unternehmens-eDiscovery und Zusammenarbeit mit Websitepostfächern ermöglichen.

## Archivierung, Aufbewahrung und eDiscovery

In den meisten Organisationen ist die Archivierung und Aufbewahrung von E-Mails und Dokumenten äußerst wichtig, um rechtliche Vorgaben und geschäftliche Anforderungen zu erfüllen. Außerdem müssen diese archivierten Elemente zur Erfüllung von eDiscovery-Anforderungen schnell durchsucht werden können. Exchange 2013, SharePoint 2013 und Lync Server 2013 bieten gemeinsam integrierte Archivierungs-, Aufbewahrungs- und eDiscovery-Funktionen, sodass Sie wichtige Daten in Exchange-Postfächern, SharePoint-Dokumenten und -Websites sowie archivierten Lync-Inhalten beibehalten können. Das eDiscovery Center in SharePoint 2013 bietet autorisierten Discovery-Managern die Möglichkeit, eine eDiscovery-Suche für Inhalte in diesen Informationsspeichern durchzuführen, eine Vorschau für Suchergebnisse anzuzeigen und die Daten zur juristischen Überprüfung zu exportieren.

## Archivieren von Lync Server 2013-Inhalten in Exchange 2013

Wenn Lync Server 2013 in einer Organisation mit Exchange 2013 bereitgestellt wird, kann Lync so konfiguriert werden, dass Inhalte aus Chats und Onlinebesprechungen, wie z. B. freigegebene Präsentationen oder Dokumente, im Exchange 2013-Postfach des Benutzers archiviert werden. Beim Archivieren von Lync-Daten in Exchange 2013 können Aufbewahrungsrichtlinien auf die Daten angewendet werden. Archivierte Lync-Inhalte werden auch bei der eDiscovery-Suche berücksichtigt. Weitere Einzelheiten zur Lync-Archivierung und zur Bereitstellung dieser Funktion finden Sie in den folgenden Themen:

  - [Planung der Archivierung](https://go.microsoft.com/fwlink/p/?linkid=265005)

  - [Bereitstellung der Archivierungsfunktion](https://go.microsoft.com/fwlink/p/?linkid=265006)

## Suchen nach Exchange-, SharePoint- und Lync-Daten über das SharePoint 2013 eDiscovery Center

Exchange 2013 ermöglicht SharePoint 2013 das Durchsuchen von Exchange-Postfachinhalten über eine API für die Verbundsuche. SharePoint 2013 umfasst ein eDiscovery Center, über das autorisierte Mitarbeiter eine eDiscovery-Suche durchführen können. Microsoft Search Foundation bietet eine einheitliche Indizierungs- und Suchinfrastruktur für Exchange 2013 und SharePoint 2013. Außerdem können Sie für beide Anwendungen dieselbe Abfragesyntax verwenden. Dadurch wird sichergestellt, dass eine eDiscovery-Suche in SharePoint 2013 dieselben Exchange 2013-Inhalte zurückgibt wie eine identische Suche über die Compliance-eDiscovery in Exchange 2013. Über das SharePoint 2013 eDiscovery Center können die in einer eDiscovery-Suche zurückgegebenen Inhalte zudem exportiert werden. Dies umfasst u. a. einen Export der Exchange 2013-Inhalte in eine PST-Datei.

Weitere Informationen finden Sie in den folgenden Themen:

  - [Compliance-eDiscovery](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [In-Place Hold and Litigation Hold](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-and-litigation-holds)

  - [Konfigurieren von eDiscovery in SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=257727)

  - [Neuigkeiten in eDiscovery in SharePoint Server 2013](https://go.microsoft.com/fwlink/?linkid=275091)

  - [Konfigurieren von Exchange für SharePoint eDiscovery Center](configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md)

## Websitepostfächer

In vielen Organisationen werden Informationen in zwei separaten Informationsspeichern gespeichert – E-Mails in Microsoft Exchange und Dokumente in SharePoint. Der Zugriff erfolgt dabei über zwei unterschiedliche Schnittstellen. Dies hat ein uneinheitliches Benutzererlebnis zur Folge und verhindert eine effektive Zusammenarbeit. Mit Websitepostfächern können Benutzer effektiv zusammenarbeiten, indem Exchange-E-Mails und SharePoint-Dokumente zusammengeführt werden. Für Benutzer dient ein Websitepostfach als zentrale Aktenablage, um Projekt-E-Mails und -Dokumente abzulegen, auf die nur Mitglieder der Website zugreifen und die nur von diesen Mitgliedern bearbeitet werden können. Websitepostfächer sind in Outlook 2013 sichtbar und ermöglichen Benutzern den einfachen Zugriff auf E-Mails und Dokumenten zu den Projekten, die sie bearbeiten. Außerdem kann auf diesen Inhalt direkt über die SharePoint-Website zugegriffen werden.

Im Kontext eines Websitepostfachs wird der Inhalt an der richtigen Stelle beibehalten. Exchange speichert die E-Mail, sodass Benutzer dieselbe Nachrichtenansicht für E-Mail-Unterhaltungen angezeigt wird, die sie tagtäglich für ihre eigenen Postfächer verwenden. SharePoint speichert die Dokumente und ermöglicht eine gemeinsame Dokumenterstellung sowie Versionsverwaltung. Exchange synchronisiert gerade so viele Metadaten von SharePoint, damit die Dokumentansicht in Outlook erstellt werden kann (beispielsweise Dokumenttitel, Datum der letzten Änderung, Autor der letzten Änderung und Größe).

Websitepostfächer werden über SharePoint 2013 bereitgestellt und verwaltet. Weitere Informationen finden Sie in den folgenden Themen:

  - [Websitepostfächer](site-mailboxes-exchange-2013-help.md)

  - [Konfigurieren von Websitepostfächern in SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?linkid=258264)

## Einheitlicher Kontaktspeicher

Der einheitliche Kontaktspeicher ermöglicht ein konsistentes Kontakterlebnis für verschiedene Microsoft Office-Produkte. Mit dieser Funktion können Benutzer sämtliche Kontaktinformationen in ihrem Exchange 2013-Postfach speichern, und diese Kontaktinformationen sind anschließend global in Lync, Exchange, Outlook und Outlook Web App verfügbar.

Nachdem Lync Server 2013 in einer Umgebung mit Exchange 2013 installiert wurde und Sie die Server-zu-Server-Authentifizierung zwischen den beiden Komponenten konfiguriert haben, können Benutzer die Migration vorhandener Kontakte von Lync Server 2013 zu Exchange 2013 starten. Details finden Sie unter [Planen und Bereitstellen des einheitlichen Kontaktspeichers in Lync Server 2013](https://go.microsoft.com/fwlink/p/?linkid=275092).

## Benutzerfotos

Die Benutzerfotofunktion bietet die Möglichkeit, Bilder mit hoher Auflösung in Exchange 2013 zu speichern, auf die über Clientanwendungen (einschließlich Outlook, Outlook Web App, SharePoint 2013, Lync 2013 und mobile E-Mail-Clients) zugegriffen werden kann. Gleichzeitig wird ein Foto mit geringer Auflösung in Active Directory gespeichert. Wie einheitliche Kontaktspeicher bietet auch die Benutzerfotofunktion Ihrer Organisation die Möglichkeit, ein einheitliches Foto für Benutzerprofile zu verwenden. Dieses kann von Clientanwendungen verwendet werden, ohne dass in jeder Anwendung ein eigenes Benutzerfoto gespeichert werden muss. Außerdem müssen nicht länger verschiedene Methoden zum Hinzufügen und Verwalten dieser Fotos verwendet werden. Die Benutzer können ihre Fotos über Outlook Web App, SharePoint 2013 oder Lync 2013 verwalten. Einzelheiten zum Verwalten von Fotos für Outlook Web App finden Sie unter [Mein Konto](https://go.microsoft.com/fwlink/p/?linkid=269646).

## Lync-Anwesenheitsinformationen in Outlook Web App

Exchange 2013-Umgebungen mit Lync Server 2013 können so konfiguriert werden, dass Benutzer Anwesenheitsinformationen in Outlook Web App anzeigen können. Benutzer können ihre Chatkontakte und -gruppen im Navigationsbereich von Outlook Web App anzeigen, aus Outlook Web App auf Chatsitzungen reagieren bzw. diese starten und ihre Chatkontakte und -gruppen verwalten.

## OAuth-Authentifizierung

Exchange 2013, SharePoint 2013 und Lync Server 2013 bieten die umfassende produktübergreifende Funktionalität, die bereits anhand des OAuth-Autorisierungsprotokolls für die Server-zu-Server-Authentifizierung beschrieben wurde. Unter Verwendung desselben Authentifizierungsprotokolls ist eine nahtlose und sichere Authentifizierung zwischen diesen Anwendungen möglich. Der Authentifizierungsmechanismus unterstützt die Authentifizierung als Anwendung unter Verwendung des Kontexts eines verknüpften Kontos und des Benutzeridentitätswechsels, wobei Zugriffsanforderungen im Benutzerkontext erfolgen.

OAuth ist ein standardmäßiges Autorisierungsprotokoll, das von vielen Websites und Webdiensten verwendet wird. Über dieses Protokoll können Clients auf die von einem Ressourcenserver bereitgestellten Ressourcen zugreifen, ohne einen Benutzernamen und ein Kennwort angeben zu müssen. Die Authentifizierung erfolgt über einen Autorisierungsserver, der vom Ressourcenbesitzer als vertrauenswürdig eingestuft wird. Dieser stellt ein Zugriffstoken für den Client bereit. Über dieses Token kann für einen angegebenen Zeitraum auf einen bestimmten Satz an Ressourcen zugegriffen werden. Einzelheiten zur Exchange 2013-Implementierung von OAuth finden Sie unter [\[MS-XOAUTH\]: OAuth 2.0-Autorisierungsprotokollerweiterungen](https://go.microsoft.com/fwlink/p/?linkid=275093).

**OAuth in lokalen Bereitstellungen**

In einer lokalen Bereitstellung benötigen Exchange 2013, SharePoint 2013 und Lync Server 2013 keinen Autorisierungsserver, um Token auszustellen. Jede dieser Anwendungen stellt selbstsignierte Token für den Zugriff auf Ressourcen aus, die von einer anderen Anwendung bereitgestellt werden. Die Anwendung, die den Zugriff auf Ressourcen ermöglicht (z. B. Exchange 2013), muss die selbstsignierten Token der aufrufenden Anwendung als vertrauenswürdig einstufen. Eine Vertrauensstellung wird eingerichtet, indem für die aufrufende Anwendung eine *Partneranwendungskonfiguration* erstellt wird, die die ApplicationID, das Zertifikat und die AuthMetadataUrl dieser Anwendung enthält. Exchange 2013, SharePoint 2013 und Lync Server 2013 veröffentlichen ihr Dokument mit den Autorisierungsmetadaten über eine bekannte URL.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p><strong>AuthMetadataUrl</strong></p></td>
</tr>
<tr class="even">
<td><p>Exchange 2013</p></td>
<td><p><code>https://&lt;serverfqdn&gt;/autodiscover/metadata/json/1</code></p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013</p></td>
<td><p><code>https://&lt;serverfqdn&gt;/metadata/json/1</code></p></td>
</tr>
<tr class="even">
<td><p>SharePoint 2013</p></td>
<td><p><code>https://&lt;serverfqdn&gt;/_layouts/15/metadata/json/1</code></p></td>
</tr>
</tbody>
</table>


**Exchange 2013-Zertifikat für die Serverauthentifizierung**

Exchange 2013 Setup erstellt ein selbstsigniertes Zertifikat mit dem Anzeigenamen "Microsoft Exchange Server Auth Certificate". Dieses Zertifikat wird auf alle Front-End-Server in der Exchange 2013-Organisation repliziert. Der Fingerabdruck des Zertifikats wird in der Autorisierungskonfiguration von Exchange 2013 gemeinsam mit dem Dienstnamen angegeben. Bei diesem Namen handelt es sich um eine bekannte GUID, die die lokale Exchange 2013-Bereitstellung darstellt. Exchange verwendet die Autorisierungskonfiguration zum Veröffentlichen des Dokuments mit den Autorisierungsmetadaten.


> [!IMPORTANT]
> Das standardmäßige Zertifikat für die Serverauthentifizierung, das von Exchange 2013 erstellt wird, ist fünf Jahre gültig. Sie müssen sicherstellen, dass die Autorisierungskonfiguration ein aktuelles Zertifikat enthält.



Wenn Exchange 2013 die Zugriffsanforderung einer Partneranwendung über die Exchange-Webdienste empfängt, analysiert die Anwendung den `www-authenticate`-Header der HTTPS-Anforderung. Dieser enthält das Zugriffstoken, das vom aufrufenden Server unter Verwendung seines privaten Schlüssels signiert wurden. Das Authentifizierungsmodul überprüft das Zugriffstoken anhand der Partneranwendungskonfiguration. Anschließend wird der Zugriff auf die Ressourcen basierend auf den RBAC-Berechtigungen der Anwendung gewährt. Wenn das Zugriffstoken für einen Benutzer ausgestellt wurde, werden die RBAC-Berechtigungen des Benutzers überprüft. Wenn ein Benutzer z. B. eine eDiscovery-Suche über das eDiscovery Center in SharePoint 2013 ausführt, überprüft Exchange, ob der Benutzer Mitglied der Rollengruppe "Discoveryverwaltung" ist oder über die Rolle "Postfachsuche" verfügt. Außerdem wird sichergestellt, dass der Benutzer über die erforderlichen RBAC-Berechtigungen für die durchsuchten Postfächer verfügt. Weitere Informationen finden Sie unter [Berechtigungen](permissions-exchange-2013-help.md).

## Verwalten der OAuth-Authentifizierung

In Exchange 2013 müssen zwei Konfigurationsobjekte für die OAuth-Authentifizierung mit Partneranwendungen verwaltet werden:

  - **AuthConfig** Das AuthConfig-Objekt wird von Exchange 2013 Setup erstellt und zum Veröffentlichen der Autorisierungsmetadaten verwendet. Die Authentifizierungskonfiguration muss nicht verwaltet werden. Die einzige Ausnahme stellt die Bereitstellung eines neuen Zertifikats dar, wenn das vorhandene Zertifikat in Kürze abläuft. In diesem Fall können Sie das vorhandene Zertifikat erneuern und das neue Zertifikat im AuthConfig-Objekt gemeinsam mit seinem Gültigkeitsdatum als das nächste Zertifikat konfigurieren. Das neue Zertifikat wird automatisch auf andere Exchange 2013-Server in der Organisation repliziert, das Dokument mit den Autorisierungsmetadaten wird mit den Details des neuen Zertifikats aktualisiert und AuthConfig verwendet ab dem festgelegten Startdatum das neue Zertifikat.

  - **Partneranwendungen** Damit Partneranwendungen Zugriffstoken von Exchange 2013 anfordern können, müssen Sie eine Partneranwendungskonfiguration erstellen. Exchange 2013 umfasst das Skript `Configure-EnterprisePartnerApplication.ps1`, mit dem Sie schnell und problemlos Partneranwendungskonfigurationen erstellen und Konfigurationsfehler minimieren können. Weitere Informationen finden Sie unter [Konfigurieren der OAuth-Authentifizierung mit SharePoint 2013 und Lync 2013](configure-oauth-authentication-with-sharepoint-2013-and-lync-2013-exchange-2013-help.md).

