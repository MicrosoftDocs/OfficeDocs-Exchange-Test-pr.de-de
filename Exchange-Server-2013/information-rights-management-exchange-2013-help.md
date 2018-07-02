---
title: 'Verwaltung von Informationsrechten: Exchange 2013 Help'
TOCTitle: Verwaltung von Informationsrechten
ms:assetid: 6ea3a695-3ddd-4d53-b3c6-90041f44ef64
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638140(v=EXCHG.150)
ms:contentKeyID: 50475918
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwaltung von Informationsrechten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Tagtäglich tauschen Information-Worker sensible Informationen, wie beispielsweise Finanzberichte und -daten, juristische Verträge, vertrauliche Produktinformationen, Verkaufsberichte und -planungen, Wettbewerbsanalysen, Forschungsdaten und patentrechtlich geschützte Informationen sowie Kunden- und Mitarbeiterdaten, über E-Mail aus. Da jeder von nahezu überall auf seine E-Mails zugreifen kann, sind aus Postfächern sogenannte Repositorys (d. h. Datenspeicher) geworden, die große Mengen potenziell vertraulicher Daten enthalten. Daher können Informationslecks eine ernste Bedrohung für Organisationen darstellen. Um Informationslecks zu verhindern, schließt Microsoft Exchange Server 2013 Funktionen für die Verwaltung von Informationsrechten (Information Rights Management, IRM) ein, mit denen dauerhafter Online- und Offlineschutz von E-Mail-Nachrichten und Anlagen bereitgestellt wird.

**Inhalt**

Was ist ein "Informationsleck"?

Herkömmliche Lösungen zur Verhinderung von Informationslecks

Verwaltung von Informationsrechten (IRM) in Exchange 2013

Anwenden von IRM-Schutz auf Nachrichten

Szenarien für den IRM-Schutz

Entschlüsseln von IRM-geschützten Nachrichten zum Erzwingen von Messagingrichtlinien

Vorlizenzierung

IRM-Agents

IRM-Anforderungen

Konfigurieren und Testen von IRM

Erweitern der Rechteverwaltung mit dem Rights Management-Verbindungsdienst

## Was ist ein "Informationsleck"?

Wenn potenziell vertrauliche Informationen nach außen dringen, können der Organisation umfangreiche finanzielle Schäden entstehen, und sonstige weitreichende Auswirkungen auf die Organisation und ihre Geschäfte, Mitarbeiter, Kunden und Partner sind möglich. Es gibt immer mehr länder- und branchenspezifische Vorschriften für die Speicherung, die Übertragung und den Schutz bestimmter Arten von Informationen. Um nicht gegen die geltenden Bestimmungen zu verstoßen, müssen sich Organisationen selbst gegen absichtliche, unabsichtliche oder zufällige Informationslecks schützen.

Informationslecks können u. a. folgende Konsequenzen haben:

  - **Finanzielle Schäden**   Abhängig von der Unternehmensgröße, der Branche und den länderspezifischen Vorschriften können Informationslecks finanzielle Konsequenzen durch Umsatzverluste oder durch gerichtliche oder behördliche Strafgebühren bedeuten. Aktiengesellschaften riskieren einen Einbruch des Börsenwerts aufgrund negativer Schlagzeilen in den Medien.

  - **Imageschaden und Glaubwürdigkeitsverluste**   Informationslecks können dem Image eines Unternehmens und dessen Glaubwürdigkeit bei seinen Kunden schaden. Darüber hinaus können bekannt gewordene E-Mail-Nachrichten, je nach Art des Inhalts, peinlich für den Absender und das Unternehmen sein.

  - **Verlust von Wettbewerbsvorteilen**   Eine der schwerwiegendsten Bedrohungen durch Informationslecks ist der Verlust von geschäftlichen Wettbewerbsvorteilen. Wenn strategische Pläne oder Informationen zu Fusionen und Übernahmen nach außen gelangen, kann dies Umsatz- oder Börsenwerteinbußen bedeuten. Eine weitere Bedrohung kann der Verlust von Forschungsergebnissen, Analysedaten und sonstigem geistigem Eigentum darstellen.

Was ist ein "Informationsleck"?

## Herkömmliche Lösungen zur Verhinderung von Informationslecks

Herkömmliche Lösungen gegen Informationslecks schützen zwar möglicherweise gegen den anfänglichen Zugriff auf Daten, sie stellen jedoch häufig keinen dauerhaften Schutz bereit. In der folgenden Tabelle sind einige herkömmliche Lösungen und ihre Grenzen aufgeführt.

### Herkömmliche Lösungen

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Lösung</th>
<th>Beschreibung</th>
<th>Einschränkungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Transport Layer Security (TLS)</p></td>
<td><p>TLS ist ein Standardinternetprotokoll, das mithilfe von Verschlüsselung eine sichere Kommunikation in einem Netzwerk ermöglicht. In einer Messagingumgebung wird TLS verwendet, um die Server/Server- und Client/Server-Kommunikation zu schützen.</p>
<p>Standardmäßig verwendet Exchange 2010 TLS für alle internen Nachrichtenübertragungen. Opportunistisches TLS ist außerdem standardmäßig für Sitzungen mit externen Hosts aktiviert. Exchange versucht zuerst, die TLS-Verschlüsselung für die Sitzung zu verwenden. Wenn jedoch keine TLS-Verbindung mit dem Zielserver eingerichtet werden kann, verwendet Exchange SMTP. Sie können auch die Domänensicherheit konfigurieren, um die Verwendung von Mutual TLS mit externen Organisationen zu erzwingen.</p></td>
<td><p>TLS schützt nur die SMTP-Sitzung zwischen zwei SMTP-Hosts. Dies bedeutet, dass TLS Informationen während der Übertragung schützt, nicht jedoch auf der Nachrichtenebene und nicht, während die Informationen gespeichert sind. Nachrichten in den Postfächern des Absenders und der Empfänger sind nur dann geschützt, wenn sie mithilfe einer anderen Methode verschlüsselt werden. Bei E-Mail-Nachrichten, die das Unternehmen verlassen, kann TLS nur für den ersten Hop festgelegt werden. Nachdem ein SMTP-Remotehost außerhalb der Organisation die Nachricht empfangen hat, kann er sie über eine unverschlüsselte Sitzung an einen anderen SMTP-Host weiterleiten. Da es sich bei TLS um eine Technologie auf der Transportschicht handelt, kann darüber nicht gesteuert werden, wie der Empfänger mit der Nachricht umgeht.</p></td>
</tr>
<tr class="even">
<td><p>E-Mail-Verschlüsselung</p></td>
<td><p>Benutzer können Technologien wie S/MIME zum Verschlüsseln von Nachrichten verwenden.</p></td>
<td><p>Der Benutzer entscheidet, ob eine Nachricht verschlüsselt wird. Es entstehen zusätzliche Kosten für eine Bereitstellung mit einer Public Key-Infrastruktur, da Zusatzaufwand für die Zertifikatverwaltung für Benutzer sowie für den Schutz privater Schlüssel entsteht. Nachdem eine Nachricht entschlüsselt wurde, kann nicht gesteuert werden, welche Schritte der Empfänger für die Informationen ausführen kann. Entschlüsselte Informationen können kopiert, gedruckt oder weitergeleitet werden. Gespeicherte Anlagen sind standardmäßig nicht geschützt.</p>
<p>Ihre Organisation kann nicht auf Nachrichten zugreifen, die mit Technologien wie S/MIME verschlüsselt wurden. Die Organisation kann den Inhalt der Nachricht nicht überprüfen und daher auch keine Richtlinien für Nachrichten erzwingen, Nachrichten nach Viren oder bösartigem Inhalt durchsuchen bzw. andere Aktionen ausführen, die einen Zugriff auf den Inhalt voraussetzen.</p></td>
</tr>
</tbody>
</table>


Schließlich fehlen bei herkömmlichen Lösungen häufig die Tools, mit denen zur Vermeidung von Informationslecks die Anwendung einheitlicher Messagingrichtlinien erzwungen werden kann. Beispiel: Ein Benutzer sendet eine Nachricht mit vertraulichen Informationen und kennzeichnet diese mit **Firma (vertraulich)** und **Nicht weiterleiten**. Nachdem die Nachricht dem Empfänger zugestellt wurde, hat der Absender oder die Organisation jedoch keine Kontrolle mehr über die Informationen. Der Empfänger kann die Nachricht wissentlich oder unabsichtlich an externe E-Mail-Konten weiterleiten (mithilfe von Funktionen wie den Regeln für die automatische Weiterleitung) und so Ihre Organisation dem nicht unerheblichen Risiko von Informationslecks aussetzen.

Was ist ein "Informationsleck"?

## Verwaltung von Informationsrechten (IRM) in Exchange 2013

In Exchange 2013 können Sie mithilfe von IRM-Funktionen Nachrichten und Anlagen dauerhaft schützen. Für IRM werden die Active Directory-Rechteverwaltungsdienste (AD RMS), eine Datenschutztechnologie in Windows Server 2008 und höher, verwendet. Mit den IRM-Funktionen in Exchange 2013 können Ihre Organisation und die Benutzer steuern, welche Rechte den Empfängern für E-Mail-Nachrichten eingeräumt werden. Mit IRM können außerdem Aktionen der Empfänger, wie beispielsweise das Weiterleiten einer Nachricht an andere Empfänger, das Drucken einer Nachricht oder einer Anlage oder das Extrahieren von Nachrichteninhalten oder Anlagen mittels Kopieren und Einfügen, zugelassen oder eingeschränkt werden. Der IRM-Schutz kann durch Benutzer in Microsoft Outlook oder Microsoft Office Outlook Web App angewendet werden. Er kann sich jedoch auch nach den Messagingrichtlinien Ihrer Organisation richten und anhand von Transportschutzregeln oder Outlook-Schutzregeln angewendet werden. Im Gegensatz zu anderen Lösungen für die E-Mail-Verschlüsselung bietet IRM Ihrer Organisation außerdem die Möglichkeit, geschützte Inhalte zu entschlüsseln und die Einhaltung von Richtlinien zu erzwingen.

AD RMS verwendet zum Zertifizieren von Computern und Benutzern sowie zum Schutz von Inhalten XrML-basierte Zertifikate (eXtensible Rights Markup Language) und -Lizenzen. Wenn Inhalte, wie ein Dokument oder eine Nachricht, mithilfe von AD RMS geschützt sind, wird eine XrML-Lizenz angefügt, aus der die Rechte hervorgehen, die autorisierte Benutzer in Bezug auf den Inhalt haben. Für den Zugriff auf IRM-geschützte Inhalte müssen AD RMS-aktivierte Anwendungen vom AD RMS-Cluster eine Verwendungslizenz für den autorisierten Benutzer abrufen.


> [!NOTE]
> In Exchange 2013 fügt der Vorlizenzierungs-Agent den Nachrichten, die mithilfe des AD&nbsp;RMS-Clusters in Ihrer Organisation geschützt sind, eine Verwendungslizenz an. Weitere Informationen finden Sie im Abschnitt Vorlizenzierung weiter unten in diesem Thema.



Zum Erstellen von Inhalten verwendete Anwendungen müssen RMS-aktiviert sein, um mithilfe von AD RMS die Inhalte dauerhaft zu schützen. Microsoft Office-Anwendungen wie Word, Excel, PowerPoint und Outlook sind RMS-aktiviert und können zum Erstellen und Beanspruchen geschützter Inhalte verwendet werden.

IRM bietet folgende Möglichkeiten:

  - Verhindern von Weiterleiten, Ändern, Drucken, Faxen, Speichern oder Ausschneiden und Einfügen von IRM-geschützten Inhalten durch autorisierte Empfänger.

  - Schützen von Anlagen in unterstützten Dateiformaten mit der gleichen Schutzstufe wie die Nachricht.

  - Ablaufunterstützung für IRM-geschützte Nachrichten und Anlagen, damit sie nach einem bestimmten Zeitraum nicht mehr angezeigt werden können.

  - Kopierschutz für IRM-geschützte Inhalte beim Kopieren mit dem Snipping Tool in Microsoft Windows.

IRM kann jedoch nicht verhindern, dass Informationen mithilfe der folgenden Methoden kopiert werden:

  - Verwendung von Drittanbieterprogrammen für Bildschirmaufnahmen

  - Verwendung bildgebender Geräte (z. B. Kameras) zum Fotografieren IRM-geschützter Inhalte, die auf dem Bildschirm angezeigt werden

  - Merken oder Abschreiben der Informationen durch den Benutzer

Weitere Informationen zu AD RMS finden Sie unter [Active Directory-Rechteverwaltungsdienste](https://go.microsoft.com/fwlink/p/?linkid=129823).

## Vorlagen für AD RMS-Benutzerrechterichtlinien

AD RMS verwendet XrML-basierte Vorlagen für Benutzerrechterichtlinien, mit deren Hilfe kompatible IRM-aktivierte Anwendungen konsistente Schutzrichtlinien anwenden können. In Windows Server 2008 und höher stellt der AD RMS-Server einen Webdienst bereit, der zum Aufzählen und Abrufen von Vorlagen verwendet werden kann. Im Lieferumfang von Exchange 2013 ist die Vorlage "Nicht weiterleiten" enthalten. Wenn die Vorlage "Nicht weiterleiten" auf eine Nachricht angewendet wird, können nur die in der Nachricht genannten Empfänger die Nachricht entschlüsseln. Die Empfänger können die Nachricht weder an andere Personen weiterleiten noch den Inhalt der Nachricht kopieren oder die Nachricht drucken. Auf dem AD RMS-Server in Ihrer Organisation können Sie weitere RMS-Vorlagen erstellen, um die Anforderungen an den jeweiligen IRM-Schutz zu erfüllen.

Der IRM-Schutz wird durch Verwendung einer AD RMS-Vorlage für Benutzerrechterichtlinien angewendet. Mithilfe von Richtlinienvorlagen können Sie die Berechtigungen steuern, die Empfänger für eine Nachricht haben. Durch Anwenden der entsprechenden Vorlage für Benutzerrechterichtlinien auf die Nachricht können Aktionen wie Antworten, Allen antworten, Weiterleiten, Extrahieren von Informationen aus einer Nachricht, Speichern oder Drucken einer Nachricht gesteuert werden.

Weitere Informationen zu Vorlagen für Benutzerrechterichtlinien finden Sie unter [Überlegungen zu AD RMS-Vorlagen für Benutzerrechterichtlinien](https://go.microsoft.com/fwlink/p/?linkid=179455).

Weitere Informationen zum Erstellen von Vorlagen für Benutzerrechterichtlinien finden Sie unter [Schrittweise Anleitung zum Erstellen und Bereitstellen von Active Directory-Rechteverwaltungsdienste-Vorlagen für Benutzerrechterichtlinien](https://go.microsoft.com/fwlink/p/?linkid=136593).

Was ist ein "Informationsleck"?

## Anwenden von IRM-Schutz auf Nachrichten

In Exchange 2010 kann der IRM-Schutz mit den folgenden Methoden auf Nachrichten angewendet werden:

  - **Manuell von Outlook-Benutzern**Outlook-Benutzer können mithilfe der für sie verfügbaren AD RMS-Vorlagen für Benutzerrechterichtlinien Nachrichten durch IRM schützen. Bei diesem Prozess wird die IRM-Funktionalität in Outlook (nicht in Exchange) verwendet. Sie können jedoch mit Exchange auf Nachrichten zugreifen und Aktionen ausführen (z. B. Anwenden von Transportregeln), um die Messagingrichtlinie Ihrer Organisation zu erzwingen. Weitere Informationen zur Verwendung von IRM in Outlook finden Sie unter [Einführung in die Verwendung von IRM (Information Rights Management) für E-Mail-Nachrichten](https://go.microsoft.com/fwlink/p/?linkid=166897).

  - **Manuell von Outlook Web App-Benutzern**   Wenn IRM in Outlook Web App aktiviert wird, können Benutzer ausgehende Nachrichten durch IRM schützen und eingehende, IRM-geschützte Nachrichten anzeigen. Im Exchange 2013 kumulativen Update 1 (CU1) können Outlook Web App-Benutzer außerdem durch IRM geschützte Anlagen mithilfe der webfähigen Dokumentenanzeige anzeigen. Weitere Informationen zu IRM in Outlook Web App finden Sie unter [Verwaltung von Informationsrechten in Outlook Web App](information-rights-management-in-outlook-web-app-exchange-2013-help.md).

  - **Manuell von Benutzern mit Geräten mit Windows Mobile und Exchange ActiveSync**   In der RTM-Version (Release to Manufacturing) von Exchange 2010 können Benutzer von Windows Mobile-Geräten durch IRM geschützte Nachrichten anzeigen und erstellen. Hierfür müssen Benutzer ihre unterstützten Windows Mobile-Geräte mit einem Computer verbinden und sie für IRM aktivieren. In Exchange 2010 SP1 können Sie IRM in Microsoft Exchange ActiveSync aktivieren, damit Benutzer von Geräten mit Exchange ActiveSync (einschließlich Geräten unter Windows Mobile) durch IRM geschützte Nachrichten anzeigen, beantworten, weiterleiten und erstellen können. Weitere Informationen zu IRM in Exchange ActiveSync finden Sie unter [Verwaltung von Informationsrechten in Exchange ActiveSync](information-rights-management-in-exchange-activesync-exchange-2013-help.md).

  - **Automatisch in Outlook 2010 und höher**   Sie können Outlook-Schutzregeln erstellen, mit deren Hilfe Nachrichten in Outlook 2010 und höher automatisch durch IRM geschützt werden. Outlook-Schutzregeln werden automatisch auf Outlook 2010-Clients bereitgestellt, und der IRM-Schutz wird von Outlook 2010 automatisch angewendet, wenn ein Benutzer eine Nachricht erstellt. Weitere Informationen zu Outlook-Schutzregeln finden Sie unter [Outlook-Schutzregeln](outlook-protection-rules-exchange-2013-help.md).

  - **Automatisch auf Postfachservern**   Sie können Transportschutzregeln erstellen, mit deren Hilfe Nachrichten auf Exchange 2013-Postfachservern automatisch durch IRM geschützt werden. Weitere Informationen zu Transportschutzregeln finden Sie unter [Transportschutzregeln](transport-protection-rules-exchange-2013-help.md).
    

    > [!NOTE]
    > Der IRM-Schutz wird nicht erneut auf Nachrichten angewendet, die bereits durch IRM geschützt sind. Wenn beispielsweise ein Benutzer eine Nachricht in Outlook oder Outlook Web App durch IRM schützt, wird der IRM-Schutz durch die Verwendung einer Transportschutzregel nicht noch einmal auf die Nachricht angewendet.



Was ist ein "Informationsleck"?

## Szenarien für den IRM-Schutz

Szenarien für den IRM-Schutz werden in der folgenden Tabelle beschrieben.

### Szenarien für den IRM-Schutz

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Senden von Nachrichten mit IRM-Schutz</th>
<th>Unterstützt</th>
<th>Voraussetzungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Innerhalb derselben lokalen Exchange 2013-Bereitstellung</p></td>
<td><p>Ja</p></td>
<td><p>Anforderungen finden Sie unter IRM-Anforderungen weiter unten in diesem Thema.</p></td>
</tr>
<tr class="even">
<td><p>Zwischen unterschiedlichen Gesamtstrukturen in einer lokalen Bereitstellung</p></td>
<td><p>Ja</p></td>
<td><p>Anforderungen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=199009">Konfigurieren von AD RMS für die gesamtstrukturübergreifende Integration mit Exchange Server 2010</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Zwischen einer lokalen Exchange 2013-Bereitstellung und einer Cloud-basierten Exchange-Organisation</p></td>
<td><p>Ja</p></td>
<td><ul>
<li><p>Verwenden Sie einen lokalen AD RMS-Server.</p></li>
<li><p>Exportieren Sie die vertrauenswürdige Veröffentlichungsdomäne vom lokalen AD RMS-Server.</p></li>
<li><p>Importieren Sie die vertrauenswürdige Veröffentlichungsdomäne in die Cloud-basierte Organisation.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>An externe Empfänger</p></td>
<td><p>Nein</p></td>
<td><p>Exchange 2010 enthält keine Lösung, mit der in einer Organisation ohne Verbund IRM-geschützte Nachrichten an externe Empfänger gesendet werden können. AD RMS bietet Lösungen mit Vertrauensrichtlinien. Sie können eine Vertrauensrichtlinie zwischen Ihrem AD RMS-Cluster und Ihrem Microsoft-Konto (vormals Windows Live ID) konfigurieren. Für Nachrichten, die zwischen zwei Organisationen gesendet werden, können Sie mithilfe der Active Directory-Verbunddienste (Active Directory Federation Services, AD FS) eine Verbundvertrauensstellung zwischen den beiden Active Directory-Gesamtstrukturen erstellen. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=182909">Grundlegendes zu AD RMS-Vertrauensrichtlinien</a>.</p></td>
</tr>
</tbody>
</table>


Was ist ein "Informationsleck"?

## Entschlüsseln von IRM-geschützten Nachrichten zum Erzwingen von Messagingrichtlinien

Damit Sie Messagingrichtlinien erzwingen und behördliche Bestimmungen einhalten können, müssen Sie in der Lage sein, auf verschlüsselte Nachrichteninhalte zuzugreifen. Außerdem müssen Sie zum Erfüllen der Anforderungen an eDiscovery (elektronische Beweiserhebung) aufgrund von Rechtsstreitigkeiten, behördlichen Prüfungen oder internen Untersuchungen verschlüsselte Nachrichten durchsuchen können. Zur Unterstützung dieser Aufgaben enthält Exchange 2013 die folgenden IRM-Funktionen:

  - **Transportentschlüsselung**   Damit Messagingrichtlinien angewendet werden können, sollten Transport-Agents, wie beispielsweise der Transportregel-Agent, Zugriff auf die Nachrichteninhalte haben. Die Transportentschlüsselung ermöglicht es Transport-Agents, die auf Exchange 2013-Servern installiert sind, auf Nachrichteninhalte zuzugreifen. Weitere Informationen finden Sie unter [Transportentschlüsselung](transport-decryption-exchange-2013-help.md).

  - **Journalberichtentschlüsselung**   Zur Einhaltung behördlicher Bestimmungen oder geschäftlicher Anforderungen können Unternehmen Nachrichteninhalte mithilfe der Journalfunktion aufbewahren. Der Journal-Agent erstellt für Nachrichten, auf die die Journalfunktion angewendet wird, einen Journalbericht und schließt Metadaten über die Nachricht in den Bericht ein. Die ursprüngliche Nachricht wird dem Journalbericht angefügt. Ist die Nachricht in einem Journalbericht durch IRM geschützt, fügt die Journalberichtentschlüsselung dem Journalbericht eine Kopie der Nachricht im Klartext an. Weitere Informationen finden Sie unter [Journalberichtentschlüsselung](journal-report-decryption-exchange-2013-help.md).

  - **IRM-Entschlüsselung für die Exchange-Suche**   Mit der IRM-Entschlüsselung für die Exchange-Suche kann die Exchange-Suche Inhalte in IRM-geschützten Nachrichten indizieren. Wenn ein Discovery-Manager eine Compliance-eDiscovery-Suche durchführt, werden auch die indizierten, IRM-geschützten Nachrichten in die Suchergebnisse einbezogen. Weitere Informationen finden Sie unter [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md).
    

    > [!NOTE]
    > In Exchange 2010 SP1 und höher können Mitglieder der Rollengruppe "Discoveryverwaltung" auf IRM-geschützte Nachrichten zugreifen, die von einer Discoverysuche zurückgegeben werden und sich in einem Discoverypostfach befinden. Verwenden Sie zum Aktivieren dieser Funktion den Parameter <EM>EDiscoverySuperUserEnabled</EM> mit dem Cmdlet <A href="https://technet.microsoft.com/de-de/library/dd979792(v=exchg.150)">Set-IRMConfiguration</A>. Weitere Informationen finden Sie unter <A href="configure-irm-for-exchange-search-and-in-place-ediscovery-exchange-2013-help.md">Konfigurieren von IRM für Exchange-Suche und Compliance-eDiscovery</A>.



Damit diese Entschlüsselungsfunktionen aktiviert werden, müssen Exchange-Server auf die Nachricht zugreifen können. Dies wird durch Hinzufügen des Verbundpostfachs, eines beim Exchange-Setup erstellten Systempostfachs, zur Administratorengruppe auf dem AD RMS-Server erreicht. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

Was ist ein "Informationsleck"?

## Vorlizenzierung

Damit IRM-geschützte Nachrichten und Anlagen angezeigt werden können, fügt Exchange 2013 geschützten Nachrichten automatisch eine Vorlizenz an. Dadurch wird vermieden, dass der Client wiederholt auf den AD RMS-Server zugreifen muss, um eine Verwendungslizenz abzurufen. Außerdem wird so die Offlineanzeige von IRM-geschützten Nachrichten und Anlagen ermöglicht. Durch die Vorlizenzierung können IRM-geschützte Nachrichten auch in Outlook Web App angezeigt werden. Bei Aktivierung der IRM-Funktionen wird die Vorlizenzierung standardmäßig aktiviert.

Was ist ein "Informationsleck"?

## IRM-Agents

In Exchange 2013 werden IRM-Funktionen mithilfe von Transport-Agents im Transportdienst auf Postfachservern bereitgestellt. IRM-Agents werden vom Exchange-Setup auf einem Postfachserver installiert. und können nicht mithilfe der Verwaltungstasks für Transport-Agents gesteuert werden.


> [!NOTE]
> IRM-Agents sind in Exchange 2013 integrierte Agents. Integrierte Agents sind nicht in der Agent-Liste enthalten, die vom Cmdlet <STRONG>Get-TransportAgent</STRONG> zurückgegeben wird. Weitere Informationen finden Sie unter <A href="transport-agents-exchange-2013-help.md">Transport-Agents</A>.



In der folgenden Tabelle sind die im Transportdienst auf Postfachservern implementierten IRM-Agents aufgelistet.

### IRM-Agents im Transportdienst auf Postfachservern

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Agent</th>
<th>Ereignis</th>
<th>Funktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RMS-Entschlüsselungs-Agent</p></td>
<td><p>&quot;OnEndOfData&quot; (SMTP) und &quot;OnSubmittedMessage&quot;</p></td>
<td><p>Entschlüsselt Nachrichten, um den Zugriff auf Transport-Agents zu ermöglichen.</p></td>
</tr>
<tr class="even">
<td><p>Transportregel-Agent</p></td>
<td><p>OnRoutedMessage</p></td>
<td><p>Kennzeichnet Nachrichten, die Regelbedingungen in einer Transportschutzregel entsprechen, damit der RMS-Verschlüsselungs-Agent den IRM-Schutz auf sie anwendet.</p></td>
</tr>
<tr class="odd">
<td><p>RMS-Verschlüsselungs-Agent</p></td>
<td><p>OnRoutedMessage</p></td>
<td><p>Wendet IRM-Schutz auf Nachrichten an, die vom Transportregel-Agent gekennzeichnet wurden, und verschlüsselt beim Transport entschlüsselte Nachrichten erneut.</p></td>
</tr>
<tr class="even">
<td><p>Vorlizenzierungs-Agent</p></td>
<td><p>OnRoutedMessage</p></td>
<td><p>Fügt IRM-geschützten Nachrichten eine Vorlizenz an.</p></td>
</tr>
<tr class="odd">
<td><p>Journalberichtentschlüsselungs-Agent</p></td>
<td><p>OnCategorizedMessage</p></td>
<td><p>Entschlüsselt IRM-geschützte Nachrichten, die an Journalberichte angefügt sind, und bettet neben den ursprünglichen, verschlüsselten Nachrichten Klartextversionen mit ein.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Transport-Agents finden Sie unter [Transport-Agents](transport-agents-exchange-2013-help.md).

Was ist ein "Informationsleck"?

## IRM-Anforderungen

Wenn IRM in Ihrer Exchange 2013-Organisation implementiert werden soll, muss Ihre Bereitstellung die in der folgenden Tabelle beschriebenen Anforderungen erfüllen.

### IRM-Anforderungen

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Server</th>
<th>Anforderungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AD RMS-Cluster</p></td>
<td><ul>
<li><p><strong>Betriebssystem</strong>   Windows Server 2012, Windows Server 2008 R2 oder Windows Server 2008 SP2 mit dem <a href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=973247">Hotfix für die Active Directory-Rechteverwaltungsdienste-Rolle in Windows Server 2008</a> ist erforderlich.</p></li>
<li><p><strong>Dienstverbindungspunkt (Service Connection Point, SCP)</strong>   Exchange 2010 und AD RMS-fähige Anwendungen verwenden für die Erkennung eines AD RMS-Clusters und von URLs den in Active Directory registrierten Dienstverbindungspunkt. AD RMS ermöglicht die Registrierung des Dienstverbindungspunkts im Verlauf des AD RMS-Setups. Wenn das zum Einrichten von AD RMS verwendete Konto nicht zur Sicherheitsgruppe &quot;Organisations-Admins&quot; gehört, kann die Registrierung des Dienstverbindungspunkts nach Abschluss des Setups vorgenommen werden. Es gibt nur einen Dienstverbindungspunkt für AD RMS in einer Active Directory-Gesamtstruktur.</p></li>
<li><p><strong>Berechtigungen</strong>   Lese- und Ausführungsberechtigungen für die AD RMS-Serverzertifizierungspipeline (<code>ServerCertification.asmx</code>-Datei auf AD RMS-Servern) müssen den folgenden Entitäten zugewiesen werden:</p>
<ul>
<li><p>Exchange-Servergruppe oder einzelne Exchange-Server</p></li>
<li><p>AD RMS-Dienstgruppe auf AD RMS-Servern</p></li>
</ul>
<p>Standardmäßig befindet sich die Datei &quot;ServerCertification.asmx&quot; im Ordner <code>\inetpub\wwwroot\_wmcs\certification\</code> auf AD RMS-Servern. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=186951">Festlegen von Berechtigungen für die AD RMS-Serverzertifizierungspipeline</a>.</p></li>
<li><p><strong>AD RMS-Administratoren</strong>   Wenn Sie die Transportentschlüsselung, die Journalberichtentschlüsselung, IRM in Outlook Web App und IRM für die Exchange-Suche aktivieren möchten, müssen Sie der Administratorengruppe des AD RMS-Clusters das Verbundpostfach hinzufügen. Dabei handelt es sich um ein Systempostfach, das vom Exchange 2013-Setupprogramm erstellt wird. Weitere Informationen finden Sie unter <a href="add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md">Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe</a>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Exchange</p></td>
<td><ul>
<li><p>Exchange 2010 oder höher ist erforderlich.</p></li>
<li><p>Der Hotfix <a href="http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=973136">FIX: Fehlermeldung aufgrund einer ArgumentNullException-Ausnahme, wenn eine .NET Framework 2.0 SP2-basierte Anwendung versucht, eine Antwort mit Inhalt der Länge 0 auf eine asynchrone ASP.NET-Web Service-Anforderung zu verarbeiten: &quot;Der Wert darf nicht Null sein&quot;</a> wird für Microsoft .NET Framework 2.0 SP2 empfohlen.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook</p></td>
<td><ul>
<li><p>Benutzer können den IRM-Schutz für Nachrichten in Outlook anwenden. Outlook 2003 und höher unterstützen AD RMS-Vorlagen für den IRM-Schutz von Nachrichten.</p></li>
<li><p>Outlook-Schutzregeln sind eine Funktion von Exchange 2010 und Outlook 2010. In früheren Versionen von Outlook wird diese Funktion nicht unterstützt.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Exchange ActiveSync</p></td>
<td><ul>
<li><p>Geräte, die das Exchange ActiveSync-Protokoll in der Version 14.1 unterstützen, einschließlich Geräte unter Windows Mobile, können IRM in Exchange ActiveSync unterstützen. Die mobile E-Mail-Anwendung auf einem Gerät muss das Tag <strong>RightsManagementInformation</strong> unterstützen, das im Exchange ActiveSync-Protokoll, Version 14.1, definiert ist. In Exchange 2013 können Benutzer, deren Geräte von IRM in Exchange ActiveSync unterstützt werden, durch IRM geschützte Nachrichten anzeigen, beantworten, weiterleiten und erstellen, ohne zuvor das Gerät an einen Computer anzuschließen und es für IRM zu aktivieren. Weitere Informationen finden Sie unter <a href="information-rights-management-in-exchange-activesync-exchange-2013-help.md">Verwaltung von Informationsrechten in Exchange ActiveSync</a>.</p></li>
</ul></td>
</tr>
</tbody>
</table>



> [!NOTE]
> Der Begriff <EM>AD&nbsp;RMS-Cluster</EM> steht für eine AD&nbsp;RMS-Bereitstellung in einer Organisation (einschließlich der Bereitstellung eines einzelnen Servers). AD&nbsp;RMS ist ein Webdienst. Er setzt keine Einrichtung eines Windows Server-Failoverclusters voraus. Zur Realisierung von Hochverfügbarkeit und zum Lastenausgleich können Sie mehrere AD&nbsp;RMS-Server im Cluster bereitstellen und mit Netzwerklastenausgleich arbeiten.




> [!IMPORTANT]
> In einer Produktionsumgebung wird die gleichzeitige Installation von AD&nbsp;RMS und Exchange auf einem Server nicht unterstützt.



Die IRM-Funktionen von Exchange 2013 unterstützen die Microsoft Office-Dateiformate. Sie können den IRM-Schutz auf andere Dateiformate erweitern, indem Sie benutzerdefinierte Schutzkomponenten bereitstellen. Weitere Informationen zu benutzerdefinierten Schutzkomponenten finden Sie im Abschnitt über "Partner für Informationsschutz und -kontrolle" unter [Unabhängige Softwareanbieter](https://go.microsoft.com/fwlink/p/?linkid=210336).

Was ist ein "Informationsleck"?

## Konfigurieren und Testen von IRM

Zum Konfigurieren der IRM-Funktionen in Exchange 2013 müssen Sie die Exchange-Verwaltungsshell verwenden. Mit dem Cmdlet [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)) können Sie einzelne IRM-Funktionen konfigurieren. Sie können IRM für interne Nachrichten, die Transportentschlüsselung, die Journalberichtentschlüsselung, die Exchange-Suche und Outlook Web App aktivieren oder deaktivieren. Weitere Informationen zum Konfigurieren von IRM-Funktionen finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

Nach dem Einrichten eines Exchange 2013-Servers können Sie mithilfe des Cmdlets [Test-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979798\(v=exchg.150\)) End-to-End-Tests für Ihre IRM-Bereitstellung ausführen. Diese Tests sind hilfreich, um die IRM-Funktionalität unmittelbar nach der ersten IRM-Konfiguration und auf regelmäßiger Basis zu überprüfen. Das Cmdlet führt die folgenden Tests aus:

  - Überprüfen der IRM-Konfiguration für Ihre Exchange 2013-Organisation.

  - Überprüfen des AD RMS-Servers auf Versions- und Hotfixinformationen.

  - Abrufen eines Rechtekontozertifikats (RAC) und eines Client-Lizenzgeberzertifikats (CLC), um zu prüfen, ob ein Exchange-Server für RMS aktiviert werden kann.

  - Abrufen von AD RMS-Vorlagen für Benutzerrechterichtlinien vom AD RMS-Server.

  - Überprüfen, ob der angegebene Absender IRM-geschützte Nachrichten senden kann.

  - Abrufen einer Administratornutzungslizenz für den angegebenen Empfänger.

  - Abrufen einer Vorlizenz für den angegebenen Empfänger.

Was ist ein "Informationsleck"?

## Erweitern der Rechteverwaltung mit dem Rights Management-Verbindungsdienst

Der Microsoft Rights Management-Verbindungsdienst (RMS-Verbindungsdienst) ist eine optionale Anwendung, die den Datenschutz für Ihren Exchange 2013-Server mithilfe von cloudbasierten Rechteverwaltungsdiensten (Microsoft Rights Management-Diensten) verbessert. Nachdem Sie den RMS-Verbindungsdienst installiert haben, bietet er kontinuierlichen Datenschutz während der gesamten Lebensspanne der Informationen. Da diese Dienste anpassbar sind, können Sie das gewünschte Sicherheitsniveau festlegen. Sie können beispielsweise den E-Mail-Nachrichtenzugriff auf bestimmte Benutzer beschränken oder für bestimmte Nachrichten nur Leserechte festlegen.

Weitere Informationen zum RMS-Verbindungsdienst und zur Installation finden Sie unter [Rights Management-Verbindungsdienst](https://technet.microsoft.com/de-de/library/dn375964.aspx).

