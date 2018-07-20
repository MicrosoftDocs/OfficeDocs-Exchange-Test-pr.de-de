---
title: 'Beschränkungen der Nachrichtengröße: Exchange 2013 Help'
TOCTitle: Beschränkungen der Nachrichtengröße
ms:assetid: b6a3840d-b821-4e53-877b-59c16be77206
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124345(v=EXCHG.150)
ms:contentKeyID: 50476544
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Beschränkungen der Nachrichtengröße

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-08-20_

Sie können Beschränkungen auf Nachrichten anwenden, die die Exchange Server 2013-Organisation durchlaufen. Sie können die Gesamtgröße einer Nachricht oder die Größe der einzelnen Komponenten einer Nachricht beschränken, z. B. den Nachrichtenkopf, die Nachrichtenanlagen und die Anzahl der Empfänger. Sie können die Beschränkungen global für die gesamte Exchange-Organisation oder speziell auf einen Connector oder ein Benutzerobjekt anwenden.

Berücksichtigen Sie beim Planen der Beschränkungen der Nachrichtengröße für Ihre Exchange-Organisation die folgenden Fragen:

  - Welche Größenbeschränkungen sollen für alle eingehenden Nachrichten gelten?

  - Welche Größenbeschränkungen sollen für alle ausgehenden Nachrichten gelten?

  - Wie groß ist das Postfachkontingent für meine Exchange-Organisation?

  - Wie stehen die ausgewählten Beschränkungen der Nachrichtengröße zur Größe des Postfachkontingents in Beziehung?

  - Gibt es Benutzer in meiner Exchange-Organisation, die Nachrichten senden oder empfangen müssen, deren Größe die angegebene zulässige Größe überschreitet?

  - Enthält die Exchange-Netzwerktopologie andere Messagingsysteme oder eindeutig getrennte Geschäftseinheiten, für die andere Beschränkungen der Nachrichtengröße gelten?

In diesem Thema finden Sie Anleitungen, wie Sie diese Fragen beantworten können.

**Inhalt**

Typen von Beschränkungen der Nachrichtengröße

Gültigkeitsbereich der Beschränkungen

Prioritätsreihenfolge für Nachrichtengrößenbeschränkungen

Nachrichten, die von Größenbeschränkungen ausgenommen werden

## Typen von Beschränkungen der Nachrichtengröße

Die folgenden Kategorien sind die Basiskategorien der Größenbeschränkungen, die für einzelne Nachrichten verfügbar sind:

  - **Größenbeschränkungen für Nachrichtenkopf**   Diese Beschränkungen gelten für die Gesamtgröße aller Nachrichtenkopffelder, die in einer Nachricht vorhanden sind. Die Größe des Nachrichtentexts oder der Anlagen wird nicht berücksichtigt. Da die Kopffelder unformatierten Text enthalten, wird die Größe des Kopfes durch die Anzahl der Zeichen in jedem Kopffeld sowie durch die Gesamtanzahl der Kopffelder bestimmt. Jedes Textzeichen belegt 1 Byte.
    

    > [!NOTE]
    > Einige Firewalls und Proxyserver von Drittanbietern wenden eigene Größenbeschränkungen für Nachrichtenköpfe an. Bei solchen Firewalls bzw. Proxyservern von Drittherstellern kann es bei der Verarbeitung von Nachrichten, die Anlagen mit Dateinamen enthalten, die länger als 50&nbsp;Zeichen sind bzw. Nicht-US-ASCII-Zeichen enthalten, zu Problemen kommen.



  - **Beschränkungen der Nachrichtengröße**   Diese Beschränkungen gelten für die Gesamtgröße einer Nachricht, wozu der Nachrichtenkopf, der Nachrichtentext und alle Anlagen gehören. Beschränkungen der Nachrichtengröße können für eingehende oder ausgehende Nachrichten festgelegt werden. Für den internen Nachrichtenfluss verwendet Exchange den benutzerdefinierten Nachrichtenkopf `X-MS-Exchange-Organization-OriginalSize:`, um die ursprüngliche Nachrichtengröße der Nachricht aufzuzeichnen, wenn diese bei der Exchange-Organisation eingeht. Bei jeder Überprüfung der Nachricht hinsichtlich der angegebenen Beschränkungen der Nachrichtengröße wird der niedrigere Wert der aktuellen Nachrichtengröße oder der ursprünglichen Größe des Nachrichtenkopfs verwendet. Die Größe der Nachricht kann sich aufgrund von Inhaltskonvertierung, Codierung sowie Agent-Verarbeitung ändern.

  - **Beschränkungen der Anlagengröße**   Diese Beschränkungen gelten für die maximal zulässige Größe einer einzelnen Anlage in einer Nachricht. Die Nachricht enthält möglicherweise viele Anlagen, die die Gesamtgröße der Nachricht extrem erhöhen. Eine Beschränkung der Anlagengröße gilt jedoch nur für die Größe einer einzelnen Anlage.

  - **Empfängerbeschränkungen**   Diese Beschränkungen gelten für die Gesamtanzahl von Nachrichtenempfängern. Beim erstmaligen Verfassen einer Nachricht sind die Empfänger in den Kopfzeilenfeldern `To:`, `Cc:` und `Bcc:` vorhanden. Wenn die Nachricht für die Zustellung übermittelt wird, werden die Nachrichtenempfänger in `RCPT TO:`-Einträge im Nachrichtenumschlag konvertiert. Eine Verteilergruppe wird während der Nachrichtenübermittlung als einzelner Empfänger gezählt.

Zurück zum Seitenanfang

## Gültigkeitsbereich der Beschränkungen

Die folgenden Kategorien sind die Basiskategorien für den Gültigkeitsbereich der Beschränkungen, die für einzelne Nachrichten verfügbar sind:

  - **Organisationsbeschränkungen**   Diese Beschränkungen gelten für alle Exchange 2013-Postfachserver sowie Exchange 2010- und Exchange 2007-Hub-Transport-Server, die in der Organisation vorhanden sind. Wenn im Umkreisnetzwerk ein Edge-Transport-Server installiert ist, gelten die angegebenen Beschränkungen für den speziellen Server.

  - **Connectorbeschränkungen**   Diese Beschränkungen gelten für alle Nachrichten, für die der angegebene Sendeconnector, Empfangsconnector, Zustellungs-Agent-Connector oder Fremdconnector für die Nachrichtenübermittlung verwendet wird. Sendeconnectors sind im Transportdienst auf Postfachservern und auf Edge-Transport-Servern definiert. Empfangsconnectors sind im Transportdienst auf Postfachservern, im Front-End-Transport-Dienst auf Clientzugriffsservern und auf Edge-Transport-Servern definiert.

  - **Active Directory-Standortverknüpfungen**   Für den Transportdienst auf Postfachservern werden Active Directory-Standorte und die Kosten, die den Active Directory-IP-Standortverknüpfungen zugewiesen sind, als einer der Faktoren verwendet, anhand der der kostengünstigste Routingpfad zwischen Postfachservern in der Organisation ermittelt wird. Sie können den Active Directory-Standortverknüpfungen in der Organisation spezielle Nachrichtengrößenbeschränkungen zuweisen.

  - **Serverbeschränkungen**   Diese Beschränkungen gelten für einen bestimmten Postfachserver oder Edge-Transport-Server. Sie können die angegebenen Nachrichtenbeschränkungen eigenständig für jeden Postfachserver oder Edge-Transport-Server festlegen.
    
    In Outlook Web App wird über die Einstellung für die HTTP-Anforderungsgrößenbeschränkung auf den Clientzugriffsservern auch die Größe von Nachrichten gesteuert, die von Outlook Web App-Benutzern gesendet werden können.

  - **Benutzerbeschränkungen**   Diese Beschränkungen gelten für ein bestimmtes Benutzerobjekt, z. B. für ein Postfach, einen Kontakt, eine Verteilergruppe oder einen Öffentlichen Ordner.

In der folgenden Tabelle sind die Nachrichtenbeschränkungen samt Informationen darüber zusammengestellt, wie die Beschränkungen in der Exchange-Verwaltungsshell oder in der Exchange-Verwaltungskonsole konfiguriert werden können.

### Organisationsbeschränkungen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Größenbeschränkung</th>
<th>Standardwert</th>
<th>Konfiguration in Shell</th>
<th>Konfiguration der Exchange-Verwaltungskonsole</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Maximale Größe für empfangene Nachrichten</p></td>
<td><p>10 MB</p></td>
<td><p>Cmdlet: <strong>Set-TransportConfig</strong></p>
<p>Parameter: <em>MaxReceiveSize</em></p></td>
<td><p><strong>Nachrichtenfluss</strong> &gt; <strong>Empfangsconnectors</strong> &gt; <strong>Weitere Optionen</strong><img src="images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif" title="Weitere Optionen (Symbol)" alt="Weitere Optionen (Symbol)" /> &gt; <strong>Einstellungen für Organisationstransport</strong> &gt; Registerkarte <strong>Grenzwerte</strong> &gt; <strong>Maximale Größe für empfangene Nachricht</strong></p></td>
</tr>
<tr class="even">
<td><p>Maximale Größe für gesendete Nachrichten</p></td>
<td><p>10 MB</p></td>
<td><p>Cmdlet: <strong>Set-TransportConfig</strong></p>
<p>Parameter: <em>MaxSendSize</em></p></td>
<td><p><strong>Nachrichtenfluss</strong> &gt; <strong>Empfangsconnectors</strong> &gt; <strong>Weitere Optionen</strong><img src="images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif" title="Weitere Optionen (Symbol)" alt="Weitere Optionen (Symbol)" /> &gt; <strong>Einstellungen für Organisationstransport</strong> &gt; Registerkarte <strong>Grenzwerte</strong> &gt; <strong>Maximale Größe für gesendete Nachricht</strong></p></td>
</tr>
<tr class="odd">
<td><p>Maximale Anzahl von Empfängern pro Nachricht</p>

> [!NOTE]  
>  

</td>
<td><p>5000</p></td>
<td><p>Cmdlet: <strong>Set-TransportConfig</strong></p>
<p>Parameter: <em>MaxRecipientEnvelopeLimit</em></p></td>
<td><p><strong>Nachrichtenfluss</strong> &gt; <strong>Empfangsconnectors</strong> &gt; <strong>Weitere Optionen</strong><img src="images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif" title="Weitere Optionen (Symbol)" alt="Weitere Optionen (Symbol)" /> &gt; <strong>Einstellungen für Organisationstransport</strong> &gt; Registerkarte <strong>Grenzwerte</strong> &gt; <strong>Maximale Anzahl von Empfängern</strong></p></td>
</tr>
<tr class="even">
<td><p>Maximale Anlagengröße in Transportregeln, die für alle Postfachserver in der Organisation gelten</p></td>
<td><p>Nicht konfiguriert</p></td>
<td><p>Cmdlets: <strong>New-TransportRule</strong>, <strong>Set-TransportRule</strong></p>
<p>Parameter: <em>AttachmentSizeOver</em></p></td>
<td><p><strong>Nachrichtenübermittlung</strong> &gt; <strong>Regeln</strong> &gt; <strong>Hinzufügen</strong><img src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif" title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" /> oder <strong>Bearbeiten</strong><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" />.</p>
<p>Verwenden Sie das Prädikat <strong>Diese Regel anwenden, wenn</strong> &gt; <strong>Mindestens eine Anlage</strong> &gt; <strong>ist größer oder gleich</strong></p>
<p>Verwenden Sie das Prädikat <strong>Diese Regel anwenden, wenn</strong> &gt; <strong>Die Nachricht ist</strong> &gt; <strong>größer als oder gleich</strong></p></td>
</tr>
<tr class="odd">
<td><p>Maximale Nachrichtengröße in Transportregeln, die für alle Postfachserver in der Organisation gelten</p></td>
<td><p></p></td>
<td><p>Cmdlets: <strong>New-TransportRule</strong>, <strong>Set-TransportRule</strong></p>
<p>Parameter: <em>MessageSizeOver</em></p></td>
<td><p><strong>Nachrichtenübermittlung</strong> &gt; <strong>Regeln</strong> &gt; <strong>Hinzufügen</strong><img src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif" title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" /> oder <strong>Bearbeiten</strong><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" />.</p>
<p>Verwenden Sie das Prädikat <strong>Diese Regel anwenden, wenn</strong> &gt; <strong>Die Nachricht ist</strong> &gt; <strong>größer als oder gleich</strong></p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

### Connectorbeschränkungen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Größenbeschränkung</th>
<th>Standardwert</th>
<th>Konfiguration in Shell</th>
<th>Konfiguration der Exchange-Verwaltungskonsole</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Maximale Kopfzeilengröße durch einen Empfangsconnector</p></td>
<td><p>128 KB</p></td>
<td><p>Cmdlets: <strong>New-ReceiveConnector</strong>, <strong>Set-ReceiveConnector</strong></p>
<p>Parameter: <em>MaxHeaderSize</em></p></td>
<td><p>Nicht zutreffend</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Maximale Nachrichtengröße durch einen Empfangsconnector</p>

> [!NOTE]
> Die jeweilige Nachricht kann wegen Nachrichtencodierung und Inhaltskonvertierung tatsächlich kleiner sein.


</td>
<td><p><strong>Transport-Service auf Postfachservern</strong></p>
<p>35 MB für den Standard- und den Clientproxy-Empfangsconnector</p>
<p><strong>Front-End-Transport-Dienst auf Clientzugriffsservern</strong></p>
<p>36 MB für den Standard-Front-End- und den Front-End-Connector für den ausgehenden Proxy.</p>
<p>35 MB für den Client-Front-End-Empfangsconnector.</p></td>
<td><p>Cmdlets: <strong>New-ReceiveConnector</strong>, <strong>Set-ReceiveConnector</strong></p>
<p>Parameter: <em>MaxMessageSize</em></p></td>
<td><p><strong>Nachrichtenfluss</strong> &gt; <strong>Empfangsconnectors</strong> &gt; <strong>Bearbeiten</strong><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" /> &gt; Registerkarte <strong>Allgemein</strong> &gt; <strong>Maximale Größe für empfangene Nachricht</strong></p></td>
</tr>
<tr class="odd">
<td><p>Maximale Anzahl von Empfängern pro Nachricht durch einen Empfangsconnector</p></td>
<td><p><strong>Transport-Service auf Postfachservern</strong></p>
<p>5.000 für den Standardempfangsconnector</p>
<p>200 für den Clientproxy-Empfangsconnector</p>
<p><strong>Front-End-Transport-Dienst auf Clientzugriffsservern</strong></p>
<p>200 für den Standard-Front-End-, den Client-Front-End- und den Clientproxy-Front-End-Connector.</p>

> [!NOTE]
> Wenn die Anzahl von Empfängern für einen anonymen Absender überschritten wird, wird die Nachricht für die ersten 200&nbsp;Empfänger angenommen. Die Mehrzahl der SMTP-Messagingserver erkennt, dass eine Empfängerbeschränkung wirksam ist. Der SMTP-Messagingserver sendet die Nachricht auch weiterhin erneut in Gruppen von 200&nbsp;Empfängern, bis die gesamte Nachricht allen Empfängern zugestellt wurde.


</td>
<td><p>Cmdlets: <strong>New-ReceiveConnector</strong>, <strong>Set-ReceiveConnector</strong></p>
<p>Parameter: <em>MaxRecipientsPerMessage</em></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>Maximale Nachrichtengröße durch einen Sendeconnector</p></td>
<td><p>10 MB</p></td>
<td><p>Cmdlets: <strong>New-SendConnector</strong>, <strong>Set-SendConnector</strong></p>
<p>Parameter: <em>MaxMessageSize</em></p></td>
<td><p><strong>Nachrichtenfluss</strong> &gt; <strong>Sendeconnectors</strong> &gt; <strong>Bearbeiten</strong><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" /> &gt; Registerkarte <strong>Allgemein</strong> &gt; <strong>Maximale Größe für gesendete Nachricht</strong></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Maximale Nachrichtengröße durch eine Active Directory-Standortverknüpfung</p></td>
<td><p>Unbegrenzt</p></td>
<td><p>Cmdlet: <strong>Set-AdSiteLink</strong></p>
<p>Parameter: <em>MaxMessageSize</em></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>Maximale Nachrichtengröße durch einen Zustellungs-Agent-Connector</p></td>
<td><p>Unbegrenzt</p></td>
<td><p>Cmdlets: <strong>New-DeliveryAgentConnector</strong>, <strong>Set-DeliveryAgentConnector</strong></p>
<p>Parameter: <em>MaxMessageSize</em></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>Maximale Nachrichtengröße durch einen fremden Connector</p></td>
<td><p>Unbegrenzt</p></td>
<td><p><strong>Cmdlet: Set-ForeignConnector</strong> Parameter: <em>MaxMessageSize</em></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

### Serverbeschränkungen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Größenbeschränkung</th>
<th>Standardwert</th>
<th>Konfiguration in Shell</th>
<th>Konfiguration der Exchange-Verwaltungskonsole</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Maximale Kopfgröße für Nachrichten im PICKUP-Verzeichnis</p></td>
<td><p>64 KB</p></td>
<td><p>Cmdlet: <strong>Set-TransportService</strong></p>
<p>Parameter: <em>PickupDirectoryMaxHeaderSize</em></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td><p>Maximale Anzahl von Empfängern pro Nachricht für Nachrichten im PICKUP-Verzeichnis</p></td>
<td><p>100</p></td>
<td><p>Cmdlet: <strong>Set-TransportService</strong></p>
<p>Parameter: <em>PickupDirectoryMaxRecipientsPerMessage</em></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td><p>Clientspezifische Grenzwerte für die maximale Nachrichtengröße für Outlook Web App, Exchange ActiveSync und Exchange-Webdiensteclients</p></td>
<td><p>Outlook Web App35 MB</p>
<p>Exchange ActiveSync10 MB</p>
<p>Exchange-Webdienste   64 MB</p>

> [!NOTE]
> Diese Werte sind ca. 33&nbsp;% höher als die tatsächlich nutzbare maximale Nachrichtengröße und zwar aufgrund der zusätzlichen Daten durch die Base64-Codierung.


</td>
<td><p>Sie können diese Werte auf Clientzugriffsservern in der dazugehörigen XML-Anwendungskonfigurationsdatei &quot;web.config&quot; konfigurieren. Weitere Informationen finden Sie unter <a href="configure-client-specific-message-size-limits-exchange-2013-help.md">Konfigurieren von clientspezifischen Nachrichtengrößenbegrenzungen</a>.</p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

### Benutzerbeschränkungen

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Größenbeschränkung</th>
<th>Standardwert</th>
<th>Konfiguration in Shell</th>
<th>Konfiguration der Exchange-Verwaltungskonsole</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Maximale Größe von Nachrichten, die dieser Empfänger senden kann</p></td>
<td><p>Unbegrenzt</p></td>
<td><p>Cmdlets:</p>
<p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-RemoteMailbox</strong></p>
<p>Parameter: <em>MaxSendSize</em></p></td>
<td><p>Für Postfächer:</p>
<p><strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Bearbeiten</strong><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" /> &gt; <strong>Postfachfunktionen</strong> &gt; <strong>Nachrichtenfluss</strong> &gt; <strong>Größeneinschränkungen für Nachrichten</strong> &gt; <strong>Details anzeigen</strong> &gt; <strong>Gesendete Nachrichten</strong></p>

> [!NOTE]
> Diese Einstellung kann mit der Exchange-Verwaltungskonsole nicht für andere Empfängertypen konfiguriert werden.


</td>
</tr>
<tr class="even">
<td><p>Maximale Größe von Nachrichten, die an diesen Empfänger gesendet werden können</p></td>
<td><p>Unbegrenzt</p>
<p>Für Bereitstellungsrichtlinien für Websitepostfächer: 36 MB</p></td>
<td><p>Cmdlets:</p>
<p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailUser</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>New-SiteMailboxProvisioningPolicy</strong></p>
<p><strong>Set-SiteMailboxProvisioningPolicy</strong></p>
<p>Parameter: <em>MaxReceiveSize</em></p></td>
<td><p>Für Postfächer:</p>
<p><strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Bearbeiten</strong><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" /> &gt; <strong>Postfachfunktionen</strong> &gt; <strong>Nachrichtenfluss</strong> &gt; <strong>Größeneinschränkungen für Nachrichten</strong> &gt; <strong>Details anzeigen</strong> &gt; <strong>Empfangene Nachrichten</strong></p>

> [!NOTE]
> Diese Einstellung kann mit der Exchange-Verwaltungskonsole nicht für andere Empfängertypen konfiguriert werden.


</td>
</tr>
<tr class="odd">
<td><p>Maximale Anzahl von Empfängern pro Nachricht, die von diesem Empfänger gesendet wurde</p></td>
<td><p>Unbegrenzt</p></td>
<td><p>Cmdlets:</p>
<p><strong>Set-Mailbox</strong>, <strong>Set-MailUser</strong></p>
<p>Parameter: <em>RecipientLimits</em></p>
<p></p></td>
<td><p>Nicht zutreffend</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Prioritätsreihenfolge für Nachrichtengrößenbeschränkungen

Sie können verschiedene Nachrichtengrößenbeschränkungen auf verschiedenen Ebenen in der Exchange-Organisation festlegen. Beim Weiterleiten einer Nachricht durch die Transportinfrastruktur kann die Nachricht verschiedenen Beschränkungen der Nachrichtengröße unterliegen. Sie sollten die Nachrichtengrößenbeschränkungen so planen, dass Nachrichten, die nicht den Größenbeschränkungen entsprechen, möglichst früh in der Transportpipeline zurückgewiesen werden. Grundsätzlich heißt das, Sie sollten restriktivere Beschränkungen für die Stellen festlegen, an denen Nachrichten in Ihre Infrastruktur eingehen. Beispielsweise sollten Beschränkungen der Nachrichtengröße für die Empfangsconnectors, die Nachrichten aus dem Internet empfangen, kleiner als oder gleich den Beschränkungen der Nachrichtengröße sein, die Sie für Ihre interne Exchange-Organisation konfiguriert haben. Es wäre eine Verschwendung von Systemressourcen für den Exchange-Server, wenn er eine Nachricht aus dem Internet annehmen und verarbeiten würde, die vom Transportdienst auf den Postfachservern zurückgewiesen würde. Achten Sie darauf, dass Ihre Organisations-, Server- und Connectorbeschränkungen so konfiguriert sind, dass jede unnötige Verarbeitung von Nachrichten vermieden wird.

Eine Ausnahme zu dieser Vorgehensweise sind die Benutzerbeschränkungen. Beschränkungen auf Benutzerebene haben Vorrang vor anderen Beschränkungen der Nachrichtengröße. Daher können Sie einen Benutzer so konfigurieren, dass seine Beschränkungen die für Ihre Organisation festgelegten Standardbeschränkungen der Nachrichtengröße überschreiten. Beispielsweise können Sie es einer bestimmten Gruppe von Benutzerpostfächern gestatten, größere Nachrichten zu senden als die anderen Gruppen der Organisation. Sie erreichen dies, indem Sie benutzerdefinierte Sende- und Empfangsbeschränkungen für die entsprechenden Postfächer konfigurieren.

Die Ausnahmen für Benutzerbeschränkungen gelten nur für den Nachrichtenaustausch zwischen authentifizierten Benutzern. Wenn eine Nachricht an einen Empfänger im Internet gesendet oder von diesem empfangen wird, werden die Organisationsbeschränkungen angewendet. Beispielsweise verwenden Sie eine organisationsweite Einschränkung der Nachrichtengröße auf 10 MB. Sie haben die Benutzer in Ihrer Marketingabteilung jedoch so konfiguriert, dass sie Nachrichten von bis zu 50 MB senden und empfangen können. Diese Benutzer können untereinander große Nachrichten austauschen, können jedoch dennoch keine großen Nachrichten von Internetbenutzern empfangen, da diese Nachrichten von nicht authentifizierten Absendern stammen.

Zurück zum Seitenanfang

## Nachrichten, die von Größenbeschränkungen ausgenommen werden

Die folgende Liste zeigt die Nachrichtentypen, die von einem Postfachserver oder einem Edge-Transport-Server generiert und von allen Beschränkungen der Nachrichtengröße ausgenommen werden:

  - Systemnachrichten

  - Von Agents generierte Nachrichten

  - Benachrichtigungen über den Zustellungsstatus (DSN-Nachrichten)

  - Journalberichtnachrichten

  - Isolierte Nachrichten

Für diese Nachrichten gilt allerdings weiterhin der Organisationswert für die maximale Anzahl von Empfängern in einer Nachricht.

Zurück zum Seitenanfang

