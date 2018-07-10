---
title: 'Nachrichtenfluss- oder Transportregeln: Exchange 2013 Help'
TOCTitle: Nachrichtenflussregeln (Transportregeln)
ms:assetid: c3d2031c-fb7b-4866-8ae1-32928d0138ef
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351127(v=EXCHG.150)
ms:contentKeyID: 50476657
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Nachrichtenfluss- oder Transportregeln

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-04-28_

Mithilfe von Nachrichtenflussregeln (auch bekannt als Transportregeln) können Sie Nachrichten, die über Ihre Exchange 2013-Organisation fließen, identifizieren und Maßnahmen dafür ergreifen. Nachrichtenflussregeln sind mit den Posteingangsregeln vergleichbar, die in Outlook und Outlook Web App zur Verfügung stehen. Der Hauptunterschied besteht darin, dass Nachrichtenflussregeln Nachrichten während der Übertragung behandeln und nicht nach der Übermittlung der Nachricht an das Postfach. Nachrichtenflussregeln enthalten einen reichhaltigeren Satz an Bedingungen, Ausnahmen und Aktionen, sodass Sie über die Flexibilität verfügen, viele Arten von Nachrichtenrichtlinien zu implementieren.

In diesem Artikel werden die Komponenten von Nachrichtenflussregeln und deren Funktionsweise erläutert.

Weitere Informationen zu Nachrichtenflussregeln in Exchange Online finden Sie unter [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)). Weitere Informationen zu Nachrichtenflussregeln in Exchange Online Protection finden Sie unter [Nachrichtenflussregeln (Transportregeln) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/dn271424\(v=exchg.150\)).

Sie können die Exchange-Verwaltungskonsole (EAC) oder die Exchange-Verwaltungsshell zum Verwalten von Nachrichtenflussregeln verwenden. Anweisungen zum Verwalten von Transportregeln finden Sie unter [Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md).

Bei jeder Regel haben Sie die Möglichkeit, sie zu erzwingen, sie zu testen oder sie zu testen und den Absender zu benachrichtigen. Weitere Informationen zu den Testoptionen finden Sie unter [Testen einer Nachrichtenflussregel](test-a-mail-flow-rule-exchange-2013-help.md) und [Richtlinientipps](technical-overview-of-policy-tips-in-exchange-online-and-exchange-2013.md).

Informationen zur Implementierung bestimmter Nachrichtenrichtlinien mithilfe von Nachrichtenflussregeln finden Sie in den folgenden Themen:

  - [Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md)

  - [Standardszenarien für Anlagensperre](common-attachment-blocking-scenarios-for-mail-flow-rules-exchange-2013-help.md)

  - [Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen](organization-wide-disclaimers-signatures-footers-or-headers-exchange-online-help.md)

  - [Verwenden von Nachrichtenflussregeln zum Umgehen von unwichtigen Elementen durch Nachrichten](use-mail-flow-rules-so-messages-can-bypass-clutter-exchange-2013-help.md)

  - [Verwenden von Nachrichtenflussregeln zum Routen von E-Mails basierend auf einer Liste von Wörtern, Begriffen oder Mustern](use-mail-flow-rules-to-route-email-based-on-a-list-of-words-phrases-or-patterns-exchange-2013-help.md)

  - [Gängige Szenarien der Nachrichtengenehmigung](common-message-approval-scenarios-exchange-2013-help.md)

## Komponenten von Nachrichtenflussregeln

Eine Nachrichtenflussregel besteht aus Bedingungen, Ausnahmen, Aktionen und Eigenschaften:

  - Anhand von **Bedingungen** werden die Nachrichten ermittelt, auf die Sie die Regel anwenden möchten. Mit einigen Bedingungen werden Nachrichtenkopfzeilenfelder geprüft (z. B. die Felder "An", "Von" oder "Cc"). Andere Bedingungen dienen zum Untersuchen von Nachrichteneigenschaften (z. B. Betreff, Text, Anlagen, Größe oder Klassifizierung der Nachricht). Bei den meisten Bedingungen müssen Sie einen Vergleichsoperator (z. B. Gleich, Ungleich oder Enthält) sowie einen abzugleichenden Wert angeben. Wenn keine Bedingungen oder Ausnahmen angegeben werden, wird die Regel auf alle Nachrichten angewendet.
    
    Weitere Informationen zu Bedingungen für Nachrichtenflussregeln in Exchange 2013 finden Sie unter [Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md).

  - **Ausnahmen** kennzeichnen optional die Nachrichten, auf die die Aktionen nicht angewendet werden sollen. In Ausnahmen sind die gleichen Nachrichten-IDs verfügbar wie in Bedingungen. Mit Ausnahmen werden Bedingungen außer Kraft gesetzt, und es wird verhindert, dass die Regelaktionen auf eine Nachricht angewendet werden, und zwar auch dann, wenn die Nachricht allen konfigurierten Bedingungen entspricht.

  - **Aktionen** geben an, was mit Nachrichten geschehen soll, die den Bedingungen in der Regel und keiner der Ausnahmen entsprechen. Es stehen zahlreiche Aktionen zur Verfügung, wie Ablehnen, Löschen oder Umleiten von Nachrichten, Hinzufügen weiterer Empfänger, Hinzufügen von Präfixen zum Nachrichtenbetreff oder Einfügen von Haftungsausschlüssen in den Nachrichtentext.
    
    Weitere Informationen zu Aktionen für Nachrichtenflussregeln in Exchange 2013 finden Sie unter [Transportregelaktionen](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md).

  - **Eigenschaften** geben weitere Regeleinstellungen an, die keine Bedingungen, Ausnahmen oder Aktionen sind. Zum Beispiel, wann die Regel angewendet werden soll, ob die Regel erzwungen oder getestet werden soll und in welchem Zeitraum die Regel aktiv ist.
    
    Weitere Informationen finden Sie im Abschnitt Eigenschaften von Nachrichtenflussregeln in diesem Thema.

## Mehrere Bedingungen, Ausnahmen und Aktionen

Die folgende Tabelle zeigt, wie mehrere Bedingungen, Bedingungswerte, Ausnahmen und Aktionen in einer Regel verarbeitet werden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Komponente</th>
<th>Logik</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Mehrere Bedingungen</p></td>
<td><p>UND</p></td>
<td><p>Eine Nachricht muss allen Bedingungen in der Regel entsprechen. Wenn eine von zwei Bedingungen erfüllt werden muss, verwenden Sie für die Bedingungen separate Regeln. Wenn Sie z. B. Nachrichten mit Anlagen und Nachrichten, die einen bestimmten Text enthalten, die gleiche Haftungsausschlusserklärung hinzufügen möchten, erstellen Sie für jede Bedingung eine Regel. In der Exchange-Verwaltungskonsole können Sie eine Regel ganz einfach kopieren.</p></td>
</tr>
<tr class="even">
<td><p>Eine Bedingung mit mehreren Werten</p></td>
<td><p>ODER</p></td>
<td><p>Bei einigen Bedingungen können Sie mehr als einen Wert angeben. Die Nachricht muss einem der angegebenen Werte (nicht allen) entsprechen. Beispiel: Wenn eine E-Mail den Betreff <strong>Informationen zum Börsenkurs</strong> hat und die Bedingung <strong>Betreff enthält eines der folgenden Wörter</strong> für die Übereinstimmung mit den Wörtern <strong>Contoso</strong> oder <strong>Börsenkurs</strong> konfiguriert ist, gilt die Bedingung als erfüllt, da der Betreff mindestens einen der angegebenen Werte enthält.</p></td>
</tr>
<tr class="odd">
<td><p>Mehrere Ausnahmen</p></td>
<td><p>ODER</p></td>
<td><p>Wenn eine Nachricht einer der Ausnahmen entspricht, werden die Aktionen nicht angewendet. Die Nachricht muss nicht allen Ausnahmen entsprechen.</p></td>
</tr>
<tr class="even">
<td><p>Mehrere Aktionen</p></td>
<td><p>UND</p></td>
<td><p>Für Nachrichten, die die Bedingungen einer Regel erfüllen, werden alle in der Regel angegebenen Aktionen ausgeführt. Wenn beispielsweise die Aktionen <strong>Dem Betreff der Nachricht Folgendes voranstellen</strong> und <strong>Empfänger zum Feld &quot;Bcc&quot; hinzufügen</strong> ausgewählt wurden, werden beide Aktionen auf die Nachricht angewendet.</p>
<p>Denken Sie daran, dass einige Aktionen, wie <strong>Nachricht ohne Benachrichtigung anderer Benutzer löschen</strong>, verhindern, dass nachfolgende Regeln auf die Nachricht angewendet werden. Bei anderen Aktionen wie <strong>Nachricht weiterleiten</strong> sind keine zusätzlichen Aktionen zulässig.</p>
<p>Sie können für eine Regel auch eine Aktion festlegen, sodass bei Anwendung dieser Regel nachfolgende Regeln nicht auf die Nachricht angewendet werden.</p></td>
</tr>
</tbody>
</table>


Komponenten von Nachrichtenflussregeln

## Eigenschaften von Nachrichtenflussregeln

Die folgende Tabelle beschreibt die Regeleigenschaften, die in Nachrichtenflussregeln zur Verfügung stehen.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaftenname in der Exchange-Verwaltungskonsole</th>
<th>Parametername in PowerShell</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Priority</strong></p></td>
<td><p><em>Priority</em></p></td>
<td><p>Gibt die Reihenfolge an, in der die Regeln auf Nachrichten angewendet werden. Die Standardpriorität basiert auf dem Erstellungsdatum der Regel (ältere Regeln haben eine höhere Priorität als neuere Regeln, und Regeln mit höherer Priorität werden vor Regeln mit niedrigerer Priorität verarbeitet).</p>
<p>Sie ändern die Regelpriorität in der Exchange-Verwaltungskonsole, indem Sie die Regel in der Liste der Regeln nach oben oder unten verschieben. In der PowerShell legen Sie die Prioritätsnummer fest (0 ist die höchste Priorität).</p>
<p>Wenn Sie z. B. eine Regel verwenden, um Nachrichten abzulehnen, die eine Kreditkartennummer enthalten, und eine andere Regel, die eine Genehmigung erfordert, sollte die Ablehnungsregel zuerst angewendet werden, und es sollten keine anderen Regeln mehr angewendet werden.</p>
<p>Weitere Informationen finden Sie unter <a href="manage-mail-flow-rules-exchange-2013-help.md">Festlegen der Priorität von Nachrichtenflussregeln</a>.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mode</strong></p></td>
<td><p><em>Mode</em></p></td>
<td><p>Sie können angeben, ob die Regel sofort mit der Verarbeitung von Nachrichten beginnen soll oder ob Sie Regeln ohne Auswirkungen auf die Übermittlung der Nachricht (mit oder ohne Verhinderung von Datenverlust oder DLP-Richtlinientipps) testen möchten.</p>
<p>Richtlinientipps zeigen dem Ersteller einer Nachricht in Outlook oder Outlook im Web einen Hinweis mit Informationen über mögliche Richtlinienverletzungen an. Weitere Informationen finden Sie unter <a href="technical-overview-of-policy-tips-in-exchange-online-and-exchange-2013.md">Richtlinientipps</a>.</p>
<p>Weitere Informationen zu den Modi finden Sie unter <a href="test-a-mail-flow-rule-exchange-2013-help.md">Testen einer Nachrichtenflussregel</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Diese Regel an folgendem Datum aktivieren</strong></p>
<p><strong>Diese Regel an folgendem Datum deaktivieren</strong></p></td>
<td><p><em>ActivationDate</em></p>
<p><em>ExpiryDate</em></p></td>
<td><p>Gibt den Datumsbereich an, in dem die Regel aktiv ist.</p></td>
</tr>
<tr class="even">
<td><p>Kontrollkästchen <strong>Ein</strong> aktiviert oder nicht aktiviert</p></td>
<td><p>Neue Regeln: Parameter <em>Enabled</em> im Cmdlet <strong>New-TransportRule</strong>.</p>
<p>Vorhandene Regeln: Verwenden Sie die Cmdlets <strong>Enable-TransportRule</strong> oder <strong>Disable-TransportRule</strong>.</p>
<p>Der Wert wird in der <strong>State</strong>-Eigenschaft der Regel angezeigt.</p></td>
<td><p>Sie können eine deaktivierte Regel erstellen und diese aktivieren, wenn Sie sie testen möchten. Alternativ können Sie eine Regel deaktivieren, ohne sie zu löschen, um die Einstellungen beizubehalten.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Nachricht zurückstellen, wenn die Regelverarbeitung nicht abgeschlossen wird</strong></p></td>
<td><p><em>RuleErrorAction</em></p></td>
<td><p>Sie können angeben, wie die Nachricht behandelt werden soll, wenn die Regelverarbeitung nicht abgeschlossen werden kann. Standardmäßig wird die Regel ignoriert, aber Sie können angeben, dass die Nachricht erneut zur Verarbeitung übermittelt werden soll.</p></td>
</tr>
<tr class="even">
<td><p><strong>Absenderadresse in Nachricht vergleichen</strong></p></td>
<td><p><em>SenderAddressLocation</em></p></td>
<td><p>Wenn die Regel Bedingungen oder Ausnahmen verwendet, die die E-Mail-Adresse des Absenders überprüfen, finden Sie den Wert in der Nachrichtenkopfzeile und/oder im Nachrichtenumschlag.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Verarbeiten weiterer Regeln beenden</strong></p></td>
<td><p><em>SenderAddressLocation</em></p></td>
<td><p>Dies ist eine Aktion für die Regel, aber sie sieht in der Exchange-Verwaltungskonsole wie eine Eigenschaft aus. Sie können auswählen, dass keine weiteren Regeln auf eine Nachricht angewendet werden, nachdem eine Nachricht durch eine Regel verarbeitet wurde.</p></td>
</tr>
<tr class="even">
<td><p><strong>Comments</strong></p></td>
<td><p><em>Comments</em></p></td>
<td><p>Sie können beschreibende Kommentare zur Regel eingeben.</p></td>
</tr>
</tbody>
</table>


Komponenten von Nachrichtenflussregeln

## Wie Nachrichtenflussregeln auf Nachrichten angewendet werden

Alle Nachrichten, die Ihre Organisation durchlaufen, werden anhand der aktivierten Nachrichtenflussregeln in Ihrer Organisation ausgewertet. Regeln werden in der im EAC auf der Seite **Nachrichtenfluss** \> **Regeln** angegebenen Reihenfolge oder basierend auf dem entsprechenden Wert des Parameters *Priority* in PowerShell verarbeitet.

Jede Regel bietet außerdem die Möglichkeit, die Verarbeitung weiterer Regeln anzuhalten, wenn die Regel erfüllt wird. Diese Einstellung ist für Nachrichten wichtig, die die Bedingungen in mehreren E-Mail-Flussregeln erfüllen. (Welche Regel soll auf die die Nachricht angewendet werden? Alle? Nur eine?)

## Unterschiede in der Verarbeitung basierend auf dem Nachrichtentyp

Es gibt verschiedene Nachrichtentypen, die eine Organisation durchlaufen. Die folgende Tabelle zeigt, welche Nachrichtentypen von Nachrichtenflussregeln verarbeitet werden können.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Nachrichtentyp</th>
<th>Kann eine Regel angewendet werden?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Gewöhnliche Nachrichten</strong>   Nachrichten, die einen einteiligen RTF-, HTML- oder unformatierten Nachrichtentext bzw. einen mehrteiligen Nachrichtentext oder einen alternativen Satz von Nachrichtentexten enthalten.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>Office 365-Nachrichtenverschlüsselung</strong>    Nachrichten, die von Office 365-Nachrichtenverschlüsselung in Office 365 verschlüsselt werden. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=392525">Verschlüsselung in Office 365</a>.</p></td>
<td><p>Regeln können immer auf Umschlagkopfzeilen zugreifen und Nachrichten auf Grundlage von Bedingungen verarbeiten, mit denen diese Kopfzeilen untersucht werden.</p>
<p>Damit eine Regel den Inhalt einer verschlüsselten Nachricht überprüft oder ändert, müssen Sie überprüfen, ob die Transportentschlüsselung aktiviert ist („Obligatorisch“ oder „Optional“; der Standardwert ist „Optional“). Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=848060">Aktivieren oder Deaktivieren der Transportentschlüsselung</a>.</p>
<p>Sie können auch eine Regel erstellen, die verschlüsselte Nachrichten automatisch entschlüsselt. Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=402846">Definieren von Regeln zum Ver- oder Entschlüsseln von E-Mail-Nachrichten</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>S/MIME-Verschlüsselte Nachrichten</strong></p></td>
<td><p>Regeln können nur auf Umschlagkopfzeilen zugreifen und Nachrichten auf Grundlage von Bedingungen verarbeiten, mit denen diese Kopfzeilen untersucht werden.</p>
<p>Regeln mit Bedingungen, die eine Untersuchung des Nachrichteninhalts erfordern, oder Aktionen, die den Inhalt der Nachricht ändern, können nicht verarbeitet werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>RMS-geschützte Nachrichten</strong>   Nachrichten, auf die eine Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS) (AD RMS)- oder Azure-Rechteverwaltung (RMS)-Richtlinie angewendet wurde.</p></td>
<td><p>Regeln können immer auf Umschlagkopfzeilen zugreifen und Nachrichten auf Grundlage von Bedingungen verarbeiten, mit denen diese Kopfzeilen untersucht werden.</p>
<p>Damit eine Regel den Inhalt einer RMS-geschützten Nachricht überprüft oder ändert, müssen Sie überprüfen, ob die Transportentschlüsselung aktiviert ist („Obligatorisch“ oder „Optional“; der Standardwert ist „Optional“). Weitere Informationen finden Sie unter <a href="https://go.microsoft.com/fwlink/p/?linkid=848060">Aktivieren oder Deaktivieren der Transportentschlüsselung</a>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Transparent signierte Nachrichten</strong>   Nachrichten, die signiert, aber nicht verschlüsselt wurden.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>UM-Nachrichten</strong>   Nachrichten, die vom Unified Messaging-Dienst erstellt oder verarbeitet wurden, z. B. Voicemail, Fax, Benachrichtigungen über verpasste Anrufe und mit Microsoft Outlook Voice Access erstellte oder weitergeleitete Nachrichten.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p><strong>Anonyme Nachrichten</strong>   Nachrichten, die von anonymen Absendern gesendet wurden.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>Lesebestätigungsberichte</strong>   Berichte, die als Reaktion auf Lesebestätigungsanforderungen von Absendern generiert werden. Lesebestätigungsberichte weisen die Nachrichtenklasse <code>IPM.Note*.MdnRead</code> oder <code>IPM.Note*.MdnNotRead</code> auf.</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


## Transportregeln und Gruppenmitgliedschaft

Wenn Sie eine Transportregel mit einer Bedingung definieren, durch die die Mitgliedschaft einer Verteilergruppe erweitert wird, erfolgt die Zwischenspeicherung der daraus resultierenden Empfängerliste durch den Transportdienst auf dem Postfachserver, auf dem die Regel angewendet wird. Dies wird als *Cache für erweiterte Gruppen* bezeichnet, der auch vom Journaling-Agent zum Auswerten der Gruppenmitgliedschaft für Journalregeln verwendet wird. Standardmäßig speichert der Cache für erweiterte Gruppen die Gruppenmitgliedschaft für vier Stunden. Empfänger, die vom Empfängerfilter einer dynamischen Verteilergruppe zurückgegeben werden, werden ebenfalls gespeichert. Der Cache für erweiterte Gruppen führt wiederholt Roundtrips in Active Directory durch, sodass der sich der aus der Auflösung von Gruppenmitgliedschaften ergebende Netzwerkdatenverkehr erübrigt.

In Exchange 2013 sind dieses Intervall und weitere Parameter in Verbindung mit dem Cache für erweiterte Gruppen konfigurierbar. Sie können das Cacheablaufintervall verringern oder das Zwischenspeichern insgesamt deaktivieren, um sicherzustellen, dass Gruppenmitgliedschaften häufiger aktualisiert werden. Sie müssen hierbei allerdings den entsprechende Anstieg der Arbeitslast auf den Active Directory-Domänencontroller für Abfragen der Erweiterung von Verteilergruppen einkalkulieren. Sie können den Cache eines Postfachservers auch löschen, indem Sie den Microsoft Exchange-Transportdienst auf diesem Server neu starten. Sie müssen diesen Schritt für jeden Postfachserver durchführen, auf dem der Cache gelöscht werden soll. Beim Erstellen, Testen und der Problembehandlung von Transportregeln, die Bedingungen basierend auf der Mitgliedschaft in Verteilergruppen verwenden, müssen Sie auch die Auswirkungen des Caches für erweiterte Gruppen berücksichtigen.

## Speichern und Replizieren von Regeln

Nachrichtenflussregeln, die Sie auf Postfachservern erstellen und konfigurieren, werden in Active Directory gespeichert und vom Transportdienst auf allen Postfachservern in der Organisation gelesen und angewendet. Wenn Sie eine Nachrichtenflussregel erstellen, ändern oder entfernen, wird diese Änderung zwischen den Domänencontrollern in der Organisation repliziert. Damit ist Exchange in der Lage, eine konsistente Gruppe von Nachrichtenflussregeln für die gesamte Organisation bereitzustellen.

**Hinweise:** 

  - Die Replikation zwischen Domänencontrollern hängt von Faktoren ab, die nicht von Exchange gesteuert werden (z. B. von der Anzahl der Active Directory-Websites und der Geschwindigkeit der Netzwerkverbindungen). Berücksichtigen Sie daher beim Implementieren von Nachrichtenflussregeln in Ihrer Organisation Replikationsverzögerungen. Weitere Informationen zur Active Directory-Replikation finden Sie unter [Active Directory-Replikation und Topologieverwaltung mithilfe von Windows PowerShell](https://go.microsoft.com/fwlink/p/?linkid=274904).

  - Jeder Postfachserver speichert erweiterte Verteilergruppen zwischen, um wiederholte Active Directory-Abfragen zum Ermitteln der Zugehörigkeit zu einer Gruppe zu vermeiden. Standardmäßig laufen Einträge im erweiterten Gruppencache nach vier Stunden ab. Änderungen an der Gruppenmitgliedschaft können daher erst auf Nachrichtenflussregeln angewendet werden, wenn der erweiterte Gruppencache aktualisiert wurde. Um eine sofortige Aktualisierung des Caches auf einem Postfachserver zu erzwingen, starten Sie den Microsoft Exchange-Transportdienst neu. Sie müssen den Dienst auf jedem Postfachserver, auf dem der Cache zwingend aktualisiert werden soll, neu starten.

Nachrichtenflussregeln, die Sie auf Edge-Transport-Servern erstellen und konfigurieren, werden in der lokalen Instanz von AD LDS auf dem Server gespeichert. Auf Edge-Transport-Servern erfolgt keine automatische Replikation von Nachrichtenflussregeln. Regeln auf dem Edge-Transport-Server gelten nur für Nachrichten, die über den lokalen Server fließen. Wenn Sie denselben Satz von Nachrichtenflussregeln auf mehreren Edge-Transport-Servern anwenden müssen, können Sie die Edge-Transport-Server-Konfiguration klonen oder die Nachrichtenflussregeln exportieren und dann importieren. Weitere Informationen finden Sie unter [Geklonte Edge-Transport-Server-Konfiguration](edge-transport-server-cloned-configuration-exchange-2013-help.md) und unter [Import or export a mail flow rule collection](manage-mail-flow-rules-exchange-2013-help.md).

Immer, wenn der Transportdienst auf einem Postfachserver oder Edge-Transport-Server eine geänderte Nachrichtenflussregel erkennt, wird ein Ereignis im Anwendungsprotokoll der Ereignisanzeige protokolliert (Ereignis-ID 4002 auf Postfachservern und Ereignis-ID 16028 auf Edge-Transport-Servern).

## Regelreplikation und -speicherung in gemischten Umgebungen

Es gibt zwei gängige Typen gemischter Umgebungen in Exchange 2013:

  - **Hybridumgebungen, bei denen sich ein Teil Ihrer Organisation in UNRESOLVED\_TOKEN\_VAL(Office365) befindet**
    
    In einer Hybridumgebung findet keine Replikation von Regeln zwischen Ihrer lokalen Exchange-Organisation und UNRESOLVED\_TOKEN\_VAL(Office365) statt. Wenn Sie also in Exchange eine Regel erstellen, müssen Sie in UNRESOLVED\_TOKEN\_VAL(Office365) eine entsprechende Regel erstellen. Die in UNRESOLVED\_TOKEN\_VAL(Office365) erstellten Regeln werden in der Cloud gespeichert, während die Regeln, die Sie in Ihrer lokalen Organisation erstellen, lokal in Active Directory gespeichert werden. Wenn Sie Regeln in einer Hybridumgebung verwalten, müssen Sie die beiden Regelgruppen synchron halten, indem Sie die Änderung entweder an beiden Stellen vornehmen oder die Änderung in einer Umgebung vornehmen und anschließend die Regeln exportieren und in die andere Umgebung importieren.
    

    > [!IMPORTANT]
    > Es gibt wesentliche Überlappungen zwischen den in UNRESOLVED_TOKEN_VAL(Office365) und Exchange Server verfügbaren Bedingungen und Aktionen, aber es gibt auch Unterschiede. Wenn Sie dieselbe Regel in beiden Konfigurationen erstellen möchten, vergewissern Sie sich, dass alle gewünschten Bedingungen und Aktionen verfügbar sind. Eine Liste der verfügbaren Bedingungen und Aktionen in UNRESOLVED_TOKEN_VAL(Office365) finden Sie in den folgenden Themen:<BR><A href="https://technet.microsoft.com/de-de/library/jj919235(v=exchg.150)">Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online</A><BR><A href="https://technet.microsoft.com/de-de/library/jj919237(v=exchg.150)">Aktionen für Nachrichtenflussregeln in Exchange Online</A>



  - **Koexistenz mitExchange 2010 oder Exchange 2007**
    
    Bei einer Koexistenzlösung mit Exchange 2010 oder Exchange 2007 werden alle Nachrichtenflussregeln in Active Directory gespeichert und in Ihrer gesamten Organisation unabhängig von der Exchange Server-Version repliziert, mit der Sie die Regeln erstellt haben. Alle Nachrichtenflussregeln sind jedoch der Exchange Server-Version zugeordnet, mit der sie erstellt wurden, und werden in Active Directory in einem versionsspezifischen Container gespeichert. Wenn Sie Exchange 2013 erstmalig in Ihrer Organisation bereitstellen, werden vorhandene Regeln im Rahmen des Setups in Exchange 2013 importiert. Allerdings müssen anschließend alle Änderungen an beiden Versionen vorgenommen werden. Wenn Sie beispielsweise eine vorhandene Regel in Exchange 2013 (Exchange-Verwaltungsshell oder EAC) ändern, muss dieselbe Änderung in Exchange 2010 (Exchange-Verwaltungsshell oder UNRESOLVED\_TOKEN\_VAL(exEMC)) erfolgen. Sie können auch die Regeln aus Exchange 2013 exportieren und diese in Exchange 2010 importieren.
    
    Exchange 2010 kann Regeln mit dem **Version**- oder **RuleVersion**-Wert 15.*n*.*n*.*n* nicht verarbeiten. Damit alle Ihre Regeln verarbeitet werden können, sollten Sie nur Regeln mit dem Wert 14.*n*.*n*.*n* verwenden.

## Weitere Informationen

[Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md)

[Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md)

[Transportregelaktionen](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md)

[Transport-Agents](transport-agents-exchange-2013-help.md)

