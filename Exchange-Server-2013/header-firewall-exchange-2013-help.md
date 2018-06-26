---
title: 'Kopfzeilenfirewall: Exchange 2013 Help'
TOCTitle: Kopfzeilenfirewall
ms:assetid: 9b148f7b-47a9-4379-a55b-8d5310c1772f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232136(v=EXCHG.150)
ms:contentKeyID: 52062886
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Kopfzeilenfirewall, X-Kopfzeilen
- Kopfzeilenfirewall, Routingkopfzeilen
- Kopfzeilenfirewall, Organisations-X-Kopfzeilen
- Kopfzeilenfirewall, Gesamtstruktur-X-Kopfzeilen
- Kopfzeilenfirewall, Berechtigungen für Kopfzeilenfirewall
- Kopfzeilenfirewall, Transportarchitektur
ms.translationtype: HT
---

# Kopfzeilenfirewall

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

In Microsoft Exchange Server 2013 ist die *Kopfzeilenfirewall* ein Mechanismus, der bestimmte Kopfzeilenfelder aus ein- und ausgehenden Nachrichten entfernt. Es gibt zwei Typen von Kopfzeilenfeldern, die von der Kopfzeilenfirewall betroffen sind:

  - **X-Header**   Ein *X-Header* ist ein benutzerdefiniertes, inoffizielles Kopfzeilenfeld. X-Header werden in RFC 2822 nicht ausdrücklich erwähnt, doch die Verwendung eines nicht definierten Kopfzeilenfelds, das mit **X-** beginnt, hat sich zu einer akzeptierten Methode entwickelt, um einer Nachricht inoffizielle Kopfzeilenfelder hinzuzufügen. Messaginganwendungen, wie z. B. Antispam-, Antivirus- oder Messagingserver, können einer Nachricht eigene X-Header hinzufügen. In Exchange enthalten die X-Headerfelder Einzelheiten zu den Aktionen, die durch den Transportserver für die Nachricht ausgeführt werden, z. B. für die SCL-Bewertung (Spam Confidence Level), die Ergebnisse der Inhaltsfilterung und den Status der Regelverarbeitung. Die Offenlegung solcher Informationen gegenüber nicht autorisierten Quellen kann ein potenzielles Sicherheitsrisiko darstellen.

  - **Routingkopfzeilen**   Routingkopfzeilen sind SMTP-Standardkopfzeilenfelder, die in RFC 2821 und RFC 2822 definiert sind. Routingkopfzeilen stempeln eine Nachricht mithilfe von Informationen zu den verschiedenen Messagingservern, die für die Zustellung der Nachricht an den Empfänger verwendet wurden. Von böswilligen Benutzern in Nachrichten eingefügte Routingkopfzeilen können verwendet werden, um eine falsche Darstellung des Routingpfads zu geben, den eine Nachricht bis zum Eingang beim Empfänger durchlaufen hat.

Die Kopfzeilenfirewall verhindert das Spoofing dieser Exchange-bezogenen X-Header, indem diese aus eingehenden Nachrichten entfernt werden, die aus nicht vertrauenswürdigen Quellen in die Exchange-Organisation gelangen. Die Kopfzeilenfirewall verhindert die Preisgabe dieser Exchange-bezogenen X-Header, indem diese aus ausgehenden Nachrichten entfernt werden, die an nicht vertrauenswürdige Ziele außerhalb der Exchange-Organisation gesendet werden. Die Kopfzeilenfirewall verhindert auch das Spoofing standardmäßiger Routingkopfzeilen, die zum Nachverfolgen des Routingverlaufs einer Nachricht verwendet werden.

**Inhalt**

Von der Kopfzeilenfirewall in Exchange betroffene Nachrichtenkopffelder

Anwenden der Kopfzeilenfirewall auf Empfangs- und Sendeconnectors

Kopfzeilenfirewall für eingehende Nachrichten für Empfangsconnectors

Kopfzeilenfirewall für ausgehende Nachrichten für Sendeconnectors

Kopfzeilenfirewall für andere Nachrichtenquellen

Organisations- und Gesamtstruktur-X-Header in Exchange

## Von der Kopfzeilenfirewall in Exchange betroffene Nachrichtenkopffelder

Die folgenden Typen von X-Headern und Routingkopfzeilen sind von der Kopfzeilenfirewall betroffen:

  - **Organisations-X-Header**   Diese X-Headerfelder beginnen mit **X-MS-Exchange-Organization-**.

  - **Gesamtstruktur-X-Header**   Diese X-Headerfelder beginnen mit **X-MS-Exchange-Forest-**.
    
    Beispiele von Organisations- und Gesamtstruktur-X-Headern finden Sie im Abschnitt Organisations- und Gesamtstruktur-X-Header in Exchange am Ende dieses Themas.

  - **Received:- Routingkopfzeilen**   Eine andere Instanz dieses Kopfzeilenfelds wird dem Nachrichtenkopf von jedem Messagingserver hinzugefügt, der die Nachricht angenommen und an den Empfänger weitergeleitet hat. Die **Received:**-Kopfzeile enthält normalerweise den Namen des Messagingservers und einen Datums-/Uhrzeitstempel.

  - **Resent-\*:-Routingkopfzeilen**   "Resent"-Kopfzeilenfelder sind Informationskopfzeilenfelder, die zum Bestimmen verwendet werden können, ob eine Nachricht von einem Benutzer weitergeleitet wurde. Die folgenden "Resent"-Kopfzeilenfelder sind verfügbar: **Resent-Date:**, **Resent-From:**, **Resent-Sender:**, **Resent-To:**, **Resent-Cc:**, **Resent-Bcc:** und **Resent-Message-ID:**. Die **Resent-**Felder werden verwendet, damit die Nachricht dem Empfänger so erscheint, als wäre sie direkt vom ursprünglichen Absender gesendet worden. Der Empfänger kann den Nachrichtenkopf anzeigen und ermitteln, wer die Nachricht weitergeleitet hat.

Exchange hat zwei Möglichkeiten, eine Kopfzeilenfirewall auf Organisations-X-Header, Gesamtstruktur-X-Header und Routingkopfzeilen anzuwenden, die in Nachrichten vorhanden sind:

  - Sende- oder Empfangsconnectors werden Berechtigungen zugewiesen, die zum Beibehalten oder Entfernen bestimmter Typen von Kopfzeilen in Nachrichten verwendet werden können, wenn die Nachricht den Connector durchläuft.

  - Die Kopfzeilenfirewall wird automatisch für bestimmte Typen von Kopfzeilen in Nachrichten während anderer Nachrichtenübermittlungsarten implementiert.

Zurück zum Seitenanfang

## Anwenden der Kopfzeilenfirewall auf Empfangs- und Sendeconnectors

Die Kopfzeilenfirewall wird auch auf Nachrichten angewendet, die Sende- und Empfangsconnectors basierend auf bestimmten Berechtigungen durchlaufen, die den Connectors zugewiesen sind.

Wenn die Berechtigung dem Empfangs- oder Sendeconnector zugewiesen ist, wird die Kopfzeilenfirewall nicht auf Nachrichten angewendet, die den Connector durchlaufen. Die betroffenen Kopfzeilenfelder bleiben in den Nachrichten erhalten.

Wenn die Berechtigung nicht dem Empfangs- oder Sendeconnector zugewiesen ist, wird die Kopfzeilenfirewall auf Nachrichten angewendet, die den Connector durchlaufen. Die betroffenen Kopfzeilenfelder werden aus den Nachrichten entfernt.

In der folgenden Tabelle werden die Berechtigungen für Sende- und Empfangsconnectors beschrieben, die zum Anwenden der Kopfzeilenfirewall verwendet werden, und die betroffenen Kopfzeilenfelder beschrieben.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Connectortyp</th>
<th>Berechtigung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Empfangsconnector</p></td>
<td><p><strong>Ms-Exch-Accept-Headers-Organization</strong></p></td>
<td><p>Diese Berechtigung betrifft Organisations-X-Headerfelder, die in eingehenden Nachrichten mit <strong>X-MS-Exchange-Organization-</strong> beginnen.</p></td>
</tr>
<tr class="even">
<td><p>Empfangsconnector</p></td>
<td><p><strong>Ms-Exch-Accept-Headers-Forest</strong></p></td>
<td><p>Diese Berechtigung betrifft Gesamtstruktur-X-Headerfelder, die in eingehenden Nachrichten mit <strong>X-MS-Exchange-Forest-</strong> beginnen.</p></td>
</tr>
<tr class="odd">
<td><p>Empfangsconnector</p></td>
<td><p><strong>Ms-Exch-Accept-Headers-Routing</strong></p></td>
<td><p>Diese Berechtigung betrifft <strong>Received:</strong>- und <strong>Resent-*:</strong>- Routingkopfzeilenfelder in eingehenden Nachrichten.</p></td>
</tr>
<tr class="even">
<td><p>Sendeconnector</p></td>
<td><p><strong>Ms-Exch-Send-Headers-Organization</strong></p></td>
<td><p>Diese Berechtigung betrifft Organisations-X-Headerfelder, die in ausgehenden Nachrichten mit <strong>X-MS-Exchange-Organization-</strong> beginnen.</p></td>
</tr>
<tr class="odd">
<td><p>Sendeconnector</p></td>
<td><p><strong>Ms-Exch-Send-Headers-Forest</strong></p></td>
<td><p>Diese Berechtigung betrifft Gesamtstruktur-X-Headerfelder, die in ausgehenden Nachrichten mit <strong>X-MS-Exchange-Forest-</strong> beginnen.</p></td>
</tr>
<tr class="even">
<td><p>Sendeconnector</p></td>
<td><p><strong>Ms-Exch-Send-Headers-Routing</strong></p></td>
<td><p>Diese Berechtigung betrifft <strong>Received:</strong>- und <strong>Resent-*:</strong>- Routingkopfzeilenfelder in ausgehenden Nachrichten.</p></td>
</tr>
</tbody>
</table>


## Kopfzeilenfirewall für eingehende Nachrichten für Empfangsconnectors

In der folgenden Tabelle wird das standardmäßige Anwenden der Kopfzeilenfirewall-Berechtigungen für Empfangsconnectors beschrieben.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Berechtigung</th>
<th>Exchange-Standardsicherheitsprinzipale, denen die Berechtigung zugewiesen wurde</th>
<th>Berechtigungsgruppe, in der die Sicherheitsprinzipale Mitglieder sind</th>
<th>Standardverwendungstyp, der dem Empfangsconnector die Berechtigungsgruppen zuweist</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ms-Exch-Accept-Headers-Organization</strong> und <strong>Ms-Exch-Accept-Headers-Forest</strong></p></td>
<td><ul>
<li><p>Hub-Transport-Server</p></li>
<li><p>Edge-Transport-Server</p></li>
<li><p>Exchange-Server</p>

> [!NOTE]
> Nur auf Hub-Transport-Servern


</li>
</ul></td>
<td><p><strong>ExchangeServers</strong></p></td>
<td><p><code>Internal</code></p></td>
</tr>
<tr class="even">
<td><p><strong>Ms-Exch-Accept-Headers-Routing</strong></p></td>
<td><p>Anonymes Benutzerkonto</p></td>
<td><p><strong>Anonymous</strong></p></td>
<td><p><code>Internet</code></p></td>
</tr>
<tr class="odd">
<td><p><strong>Ms-Exch-Accept-Headers-Routing</strong></p></td>
<td><p>Authentifizierte Benutzerkonten</p></td>
<td><p><strong>ExchangeUsers</strong></p></td>
<td><p><code>Client</code> (auf Edge-Transport-Servern nicht verfügbar)</p></td>
</tr>
<tr class="even">
<td><p><strong>Ms-Exch-Accept-Headers-Routing</strong></p></td>
<td><ul>
<li><p>Hub-Transport-Server</p></li>
<li><p>Edge-Transport-Server</p></li>
<li><p>Exchange-Server</p>

> [!NOTE]
> nur Hub-Transport-Server


</li>
<li><p>Extern gesicherte Server</p></li>
</ul></td>
<td><p><strong>ExchangeServers</strong></p></td>
<td><p><code>Internal</code></p></td>
</tr>
<tr class="odd">
<td><p><strong>Ms-Exch-Accept-Headers-Routing</strong></p></td>
<td><p>Partnerserverkonto</p></td>
<td><p><strong>Partner</strong></p></td>
<td><p><code>Internet</code> und <code>Partner</code></p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Kopfzeilenfirewall für benutzerdefinierte Empfangsconnectors

Wenn Sie die Kopfzeilenfirewall auf Nachrichten in einem benutzerdefinierten Empfangsconnectorszenario anwenden möchten, verwenden Sie eine der folgenden Methoden:

  - Erstellen Sie den Empfangsconnector mit einem Verwendungstyp, der die Kopfzeilenfirewall automatisch auf Nachrichten anwendet. Den Verwendungstyp können Sie allerdings nur beim Erstellen des Empfangsconnectors festlegen.
    
      - Erstellen Sie zum Entfernen der Organisations- oder Gesamtstruktur-X-Header aus Nachrichten einen Empfangsconnector, und wählen Sie einen anderen Verwendungstyp als `Internal`.
    
      - Führen Sie zum Entfernen von Routingkopfzeilen aus Nachrichten eine der folgenden Aktionen aus:
        
          - Erstellen Sie einen Empfangsconnector, und wählen Sie den Verwendungstyp `Custom` aus. Weisen Sie dem Empfangsconnector keine Berechtigungsgruppen zu.
        
          - Ändern Sie einen vorhandenen Empfangsconnector, und legen Sie den Parameter *PermissionGroups* auf den Wert `None` fest.
        
        Wenn Sie über einen Empfangsconnector verfügen, dem keine Berechtigungsgruppen zugewiesen sind, müssen Sie dem Empfangsconnector Sicherheitsprinzipale hinzufügen (siehe die Beschreibung im letzten Schritt).

  - Verwenden Sie das Cmdlet **Remove-ADPermission**, um die Berechtigungen **Ms-Exch-Accept-Headers-Organization**, **Ms-Exch-Accept-Headers-Forest** und **Ms-Exch-Accept-Headers-Routing** von einem Sicherheitsprinzipal zu entfernen, der für den Empfangsconnector konfiguriert ist. Diese Methode funktioniert nicht, wenn die Berechtigung dem Sicherheitsprinzipal über eine Berechtigungsgruppe für den Empfangsconnector zugewiesen wurde, da Sie die Berechtigungszuweisungen oder Gruppenmitgliedschaft einer Berechtigungsgruppe nicht ändern können.

  - Verwenden Sie das Cmdlet **Add-ADPermission** zum Hinzufügen der entsprechenden Sicherheitsprinzipale, die für den Empfangsconnector für einen ordnungsgemäßen Nachrichtenfluss erforderlich sind. Vergewissern Sie sich, dass Sicherheitsprinzipalen nicht die Berechtigungen **Ms-Exch-Accept-Headers-Organization**, **Ms-Exch-Accept-Headers-Forest** und **Ms-Exch-Accept-Headers-Routing** zugewiesen sind. Verwenden Sie nötigenfalls das Cmdlet **Add-ADPermission**, um den Sicherheitsprinzipalen, die für den Empfangsconnector konfiguriert sind, die Berechtigungen **Ms-Exch-Accept-Headers-Organization**, **Ms-Exch-Accept-Headers-Forest** und **Ms-Exch-Accept-Headers-Routing** zu verweigern.

Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Empfangsconnectors](receive-connectors-exchange-2013-help.md)

  - [Add-ADPermission](https://technet.microsoft.com/de-de/library/bb124403\(v=exchg.150\))

  - [Remove-ADPermission](https://technet.microsoft.com/de-de/library/aa996048\(v=exchg.150\))

Zurück zum Seitenanfang

## Kopfzeilenfirewall für ausgehende Nachrichten für Sendeconnectors

In der folgenden Tabelle wird das standardmäßige Anwenden der Kopfzeilenfirewall-Berechtigungen für Sendeconnectors beschrieben.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Berechtigung</th>
<th>Exchange-Standardsicherheitsprinzipale, denen die Berechtigung zugewiesen wurde</th>
<th>Standardverwendungstyp, der die Sicherheitsprinzipale dem Sendeconnector zuweist</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ms-Exch-Send-Headers-Organization</strong> und <strong>Ms-Exch-Send-Headers-Forest</strong></p></td>
<td><ul>
<li><p>Hub-Transport-Server</p></li>
<li><p>Edge-Transport-Server</p></li>
<li><p>Exchange-Server</p>

> [!NOTE]
> Nur auf Hub-Transport-Servern


</li>
<li><p>Extern gesicherte Server</p></li>
<li><p>Universelle Sicherheitsgruppe <strong>ExchangeLegacyInterop</strong></p></li>
</ul></td>
<td><p><code>Internal</code></p></td>
</tr>
<tr class="even">
<td><p><strong>Ms-Exch-Send-Headers-Routing</strong></p></td>
<td><ul>
<li><p>Hub-Transport-Server</p></li>
<li><p>Edge-Transport-Server</p></li>
<li><p>Exchange-Server</p>

> [!NOTE]
> Nur auf Hub-Transport-Servern


</li>
<li><p>Extern gesicherte Server</p></li>
<li><p>Universelle Sicherheitsgruppe <strong>ExchangeLegacyInterop</strong></p></li>
</ul></td>
<td><p><code>Internal</code></p></td>
</tr>
<tr class="odd">
<td><p><strong>Ms-Exch-Send-Headers-Routing</strong></p></td>
<td><p>Anonymes Benutzerkonto</p></td>
<td><p><code>Internet</code></p></td>
</tr>
<tr class="even">
<td><p><strong>Ms-Exch-Send-Headers-Routing</strong></p></td>
<td><p>Partnerserver</p></td>
<td><p><code>Partner</code></p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Kopfzeilenfirewall für benutzerdefinierte Sendeconnectors

Wenn Sie die Kopfzeilenfirewall auf Nachrichten in einem benutzerdefinierten Sendeconnectorszenario anwenden möchten, verwenden Sie eine der folgenden Methoden:

  - Erstellen Sie den Sendeconnector mit einem Verwendungstyp, der die Kopfzeilenfirewall automatisch auf Nachrichten anwendet. Den Verwendungstyp können Sie allerdings nur beim Erstellen des Sendeconnectors festlegen.
    
      - Erstellen Sie zum Entfernen der Organisations- oder Gesamtstruktur-X-Header aus Nachrichten einen Sendeconnector, und wählen Sie einen anderen Verwendungstyp als `Internal` oder `Partner`.
    
      - Um die Routingkopfzeilen aus Nachrichten zu entfernen, erstellen Sie einen Sendeconnector, und wählen Sie den Verwendungstyp `Custom`. Die Berechtigung **Ms-Exch-Send-Headers-Routing** wird allen Verwendungstypen des Sendeconnectors mit Ausnahme von `Custom` zugewiesen.

  - Entfernen Sie einen Sicherheitsprinzipal, der die Berechtigungen **Ms-Exch-Send-Headers-Organization**, **Ms-Exch-Send-Headers-Forest** und **Ms-Exch-Send-Headers-Routing** dem Connector zuweist.

  - Verwenden Sie das Cmdlet **Remove-ADPermission**, um die Berechtigungen **Ms-Exch-Send-Headers-Organization**, **Ms-Exch-Send-Headers-Forest** und **Ms-Exch-Send-Headers-Routing** von einem der Sicherheitsprinzipale zu entfernen, die für den Sendeconnector konfiguriert sind.

  - Verwenden Sie das Cmdlet **Add-ADPermission**, um die Berechtigungen **Ms-Exch-Send-Headers-Organization**, **Ms-Exch-Send-Headers-Forest** und **Ms-Exch-Send-Headers-Routing** einem der Sicherheitsprinzipale zu verweigern, die für den Sendeconnector konfiguriert sind.

Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Sendeconnectors](send-connectors-exchange-2013-help.md)

  - [Add-ADPermission](https://technet.microsoft.com/de-de/library/bb124403\(v=exchg.150\))

  - [Remove-ADPermission](https://technet.microsoft.com/de-de/library/aa996048\(v=exchg.150\))

Zurück zum Seitenanfang

## Kopfzeilenfirewall für andere Nachrichtenquellen

Nachrichten können in die Transportpipeline auf einem Postfach- oder Edge-Transport-Server eingehen, ohne dass Sendeconnectors oder Empfangsconnectors verwendet werden. Die Kopfzeilenfirewall wird auf diese anderen Nachrichtenquellen wie der folgenden Liste beschrieben angewendet:

  - **PICKUP- und Wiedergabeverzeichnis**   Das PICKUP-Verzeichnis wird von Administratoren oder Anwendungen zum Übermitteln von Nachrichtendateien verwendet. Das Wiedergabeverzeichnis wird zum erneuten Übermitteln von Nachrichten verwendet, die aus Exchange-Nachrichtenwarteschlangen exportiert wurden. Weitere Informationen zum PICKUP- und Wiedergabeverzeichnis finden Sie unter [PICKUP-Verzeichnis und Wiedergabeverzeichnis](pickup-directory-and-replay-directory-exchange-2013-help.md).
    
    Organisations- und Gesamtstruktur-X-Header sowie Routingkopfzeilen werden im PICKUP-Verzeichnis aus den Nachrichtendateien entfernt.
    
    Routingkopfzeilen werden in Nachrichten beibehalten, die vom Wiedergabeverzeichnis übermittelt werden.
    
    Das Entfernen oder Beibehalten von Organisations- und Gesamtstruktur-X-Headern in Nachrichten im Wiedergabeverzeichnis wird vom Kopfzeilenfeld **X-CreatedBy:** in der Nachrichtendatei gesteuert:
    
      - Wenn der Wert von **X-CreatedBy:**`MSExchange15` ist, werden Organisations- und Gesamtstruktur-X-Header in Nachrichten beibehalten.
    
      - Wenn der Wert von **X-CreatedBy:** nicht `MSExchange15` ist, werden Organisations- und Gesamtstruktur-X-Header aus Nachrichten entfernt.
    
      - Wenn das Kopfzeilenfeld **X-CreatedBy:** nicht in der Nachrichtendatei vorhanden ist, werden Organisations- und Gesamtstruktur-X-Header aus Nachrichten entfernt.

  - **Dropverzeichnis**   Das Dropverzeichnis wird von fremden Connectors auf Postfachservern verwendet, um Nachrichten an Messagingserver zu senden, die zum Übertragen von Nachrichten nicht SMTP (Simple Mail Transfer Protocol) verwenden. Weitere Informationen zu fremden Connectors finden Sie unter [Fremde Connectors](foreign-connectors-exchange-2013-help.md).
    
    Organisations- und Gesamtstruktur-X-Header werden aus den Nachrichtendateien entfernt, bevor sie im Dropverzeichnis abgelegt werden.
    
    Routingkopfzeilen bleiben in Nachrichten erhalten, die vom Dropverzeichnis übermittelt werden.

  - **Postfachtransportdienst**   Der Postfachtransportdienst dient auf Postfachservern zum Übertragen von Nachrichten in und aus Postfächern auf Postfachservern. Weitere Informationen zum Postfachtransportdienst finden Sie unter [Nachrichtenübermittlung](mail-flow-exchange-2013-help.md).
    
    Organisations- und Gesamtstruktur-X-Header sowie Routingkopfzeilen werden aus ausgehenden Nachrichten entfernt, die vom Postfachtransport-Zustellungsdienst aus Postfächern gesendet werden.
    
    Routingkopfzeilen werden vom Postfachtransport-Zustellungsdienst für eingehende Nachrichten an Postfachempfänger beibehalten. Die folgenden Organisations-X-Header werden vom Postfachtransport-Zustellungsdienst für eingehende Nachrichten an Postfachempfänger beibehalten:
    
      - **X-MS-Exchange-Organization-SCL**
    
      - **X-MS-Exchange-Organization-AuthDomain**
    
      - **X-MS-Exchange-Organization-AuthMechanism**
    
      - **X-MS-Exchange-Organization-AuthSource**
    
      - **X-MS-Exchange-Organization-AuthAs**
    
      - **X-MS-Exchange-Organization-OriginalArrivalTime**
    
      - **X-MS-Exchange-Organization-OriginalSize**

  - **Benachrichtigungen über den Zustellungsstatus**   Organisations- und Gesamtstruktur-X-Header sowie Routingkopfzeilen werden aus der Originalmeldung oder deren Kopfzeile entfernt, die der Benachrichtigung über die Zustellungsstatus zugeordnet ist. Weitere Informationen zu Benachrichtigungen über den Zustellungsstatus finden Sie unter [DSNs und NDRs in Exchange 2013](dsns-and-ndrs-in-exchange-2013-exchange-2013-help.md).

  - **Transport-Agent-Übermittlung**   Organisations- und Gesamtstruktur-X-Header sowie Routingkopfzeilen werden in Nachrichten beibehalten, die von Transport-Agents zugestellt werden.

Zurück zum Seitenanfang

## Organisations- und Gesamtstruktur-X-Header in Exchange

Der Transportdienst auf Postfach- oder Edge-Transport-Servern fügt benutzerdefinierte X-Headerfelder im Nachrichtenkopf ein.

Organisations-X-Header beginnen mit **X-MS-Exchange-Organization-**. Gesamtstruktur-X-Header beginnen mit **X-MS-Exchange-Forest-**. In der folgenden Tabelle werden einige der Organisations- und Gesamtstruktur-X-Header beschrieben, die in Nachrichten in einer Exchange-Organisation verwendet werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>X-Header</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Forest-RulesExecuted</strong></p></td>
<td><p>Transportregeln, die auf die Nachricht angewendet wurden.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-Antispam-Report</strong></p></td>
<td><p>Eine Zusammenfassung der Ergebnisse der Antispamfilter, die auf die E-Mail-Nachricht vom Inhaltsfilter-Agent angewendet wurden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-AuthAs</strong></p></td>
<td><p>Gibt die Authentifizierungsquelle an. Dieser X-Header ist immer vorhanden, wenn die Sicherheit einer Nachricht bewertet wurde. Die möglichen Werte sind <code>Anonymous</code>, <code>Internal</code>, <code>External</code> oder <code>Partner</code>.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-AuthDomain</strong></p></td>
<td><p>Wird während der domänengesicherten Authentifizierung aufgefüllt. Der Wert ist der FQDN der authentifizierten Remotedomäne.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-AuthMechanism</strong></p></td>
<td><p>Gibt den Authentifizierungsmechanismus für die Zustellung der Nachricht an. Der Wert ist eine zweistellige hexadezimale Zahl.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-AuthSource</strong></p></td>
<td><p>Gibt den FQDN des Servercomputers an, der die Authentifizierung der Nachricht für die Organisation ausgewertet hat.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-Journal-Report</strong></p></td>
<td><p>Bestimmt Journalberichte im Transport. Sobald die Nachricht den Transportdienst verlässt, ändert sich die Kopfzeile in <strong>X-MS-Journal-Report</strong>.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-OriginalArrivalTime</strong></p></td>
<td><p>Bestimmt die Zeit, zu der die Nachricht zuerst in die Exchange-Organisation eingegangen ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-Original-Sender</strong></p></td>
<td><p>Gibt den ursprünglichen Absender einer Nachricht in Quarantäne zum Zeitpunkt an, als sie erstmals in die Exchange-Organisation eingegangen ist.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-OriginalSize</strong></p></td>
<td><p>Gibt die ursprüngliche Größe einer Nachricht in Quarantäne zum Zeitpunkt an, als sie erstmals in die Exchange-Organisation eingegangen ist.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-Original-Scl</strong></p></td>
<td><p>Gibt den ursprünglichen SCL-Wert einer Nachricht in Quarantäne zum Zeitpunkt an, als sie erstmals in die Exchange-Organisation eingegangen ist.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-PCL</strong></p></td>
<td><p>Bestimmt den PCL (Phishing Confidence Level). Die möglichen PCL-Werte sind 1 bis 8. Ein größerer Wert weist auf eine verdächtige Nachricht hin. Weitere Informationen finden Sie unter <a href="anti-spam-stamps-exchange-2013-help.md">Antispamstempel</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-Quarantine</strong></p></td>
<td><p>Gibt an, dass die Nachricht im Quarantänepostfach für Spam isoliert wurde und dass eine Benachrichtigungen über den Zustellungsstatus gesendet wurde. Sie kann auch angeben, dass die Nachricht isoliert und vom Administrator freigegeben wurde. Dieser X-Header verhindert, dass die freigegebene Nachricht erneut an das Quarantänepostfach für Span übermittelt wird. Weitere Informationen finden Sie unter <a href="release-quarantined-messages-from-the-spam-quarantine-mailbox-exchange-2013-help.md">Freigeben von Nachrichten unter Quarantäne aus dem Quarantänepostfach für Spam</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>X-MS-Exchange-Organization-SCL</strong></p></td>
<td><p>Bestimmt den SCL der Nachricht. Die möglichen SCL-Werte sind 0 bis 9. Ein größerer Wert weist auf eine verdächtige Nachricht hin. Der Sonderwert -1 nimmt die Nachricht von der Verarbeitung durch den Inhaltsfilter-Agent aus. Weitere Informationen finden Sie unter <a href="content-filtering-exchange-2013-help.md">Inhaltsfilterung</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>X-MS-Exchange-Organization-SenderIdResult</strong></p></td>
<td><p>Enthält die Ergebnisse des Sender ID-Agents. Der Sender ID-Agent verwendet das SPF (Sender Policy Framework) zum Vergleichen der Quell-IP-Adresse der Nachricht mit der Domäne, die in der E-Mail-Adresse des Absenders verwendet wird. Die Ergebnisse der Sender ID werden verwendet, um die SCL-Bewertung für eine Nachricht zu berechnen. Weitere Informationen finden Sie unter <a href="sender-id-exchange-2013-help.md">Absender-ID</a>.</p></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

