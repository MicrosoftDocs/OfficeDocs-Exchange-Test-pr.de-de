---
title: 'Postfachrichtlinien für mobile Geräte: Exchange 2013 Help'
TOCTitle: Postfachrichtlinien für mobile Geräte
ms:assetid: 9317b3bc-44a1-4e54-bc51-4f0b194b6a55
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123783(v=EXCHG.150)
ms:contentKeyID: 50476253
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Postfachrichtlinien für mobile Geräte

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-06-16_

In MicrosoftExchange Server 2013 können Sie Postfachrichtlinien für mobile Geräte erstellen, um eine allgemeine Zusammenstellung von Richtlinien oder Sicherheitseinstellungen auf eine Gruppe von Benutzern anzuwenden. Nach der Bereitstellung von Exchange ActiveSync in Ihrer Exchange 2013-Organisation können Sie neue Postfachrichtlinien für mobile Geräte erstellen oder vorhandene Richtlinien ändern. Beim Installieren von Exchange 2013 wird eine standardmäßige Postfachrichtlinie für mobile Geräte erstellt. Allen Benutzern wird automatisch diese standardmäßige Postfachrichtlinie für mobile Geräte zugeordnet.


> [!IMPORTANT]
> Mobiltelefone mit Windows Phone 7 unterstützen nur eine Teilmenge aller Richtlinieneinstellungen für Exchange ActiveSync-Postfächer. Eine vollständige Liste finden Sie unter Synchronisieren von Windows Phone 7-Mobiltelefonen.




> [!WARNING]
> Das Fingerabdruck-Lesegerät von iOS7 wird nicht als Gerätekennwort unterstützt. Wenn Sie das Fingerabdruck-Lesegerät aktivieren, um Ihr iOS7-Gerät zu sichern, müssen Sie dennoch ein Kennwort eingeben, falls die Postfachrichtlinien Ihres mobilen Geräts ein Kennwort erfordern.



## Übersicht über Postfachrichtlinien für mobile Geräte

Mit Postfachrichtlinien für mobile Geräte können Sie zahlreiche verschiedene Einstellungen verwalten. Hierzu gehören Folgende:

  - Kennwort anfordern

  - Minimale Kennwortlänge festlegen

  - Zahl oder Sonderzeichen im Kennwort erzwingen

  - Festlegen, nach welcher Inaktivitätsdauer der Benutzer das Kennwort für das Gerät erneut eingeben muss

  - Gerät nach einer bestimmten Anzahl von Fehleingaben des Kennworts vollständig zurücksetzen

Weitere Informationen zu allen Einstellungen, die Sie konfigurieren können, finden Sie unter „Postfachrichtlinien für mobile Geräte“.

## Verwalten von Exchange ActiveSync-Postfachrichtlinien

Postfachrichtlinien für mobile Geräte können in der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell erstellt werden. Wenn Sie eine Richtlinie in der Exchange-Verwaltungskonsole erstellen, können Sie nur einen Teil der verfügbaren Einstellungen konfigurieren. Die restlichen Einstellungen können Sie über die Shell konfigurieren.

## Synchronisieren von Windows Phone 7-Mobiltelefonen

Wenn Ihre Organisation über Mobiltelefone mit Windows Phone 7 verfügt und bestimmte Richtlinieneigenschaften für Exchange ActiveSync-Postfächer konfiguriert sind, treten Synchronisierungsprobleme auf. Um die Synchronisierung von Mobiltelefonen mit Windows Phone 7 mit einem Exchange-Postfach zu ermöglichen, legen Sie die Eigenschaft **AllowNonProvisionableDevices** auf "True" fest, oder konfigurieren Sie nur die folgenden Richtlinieneigenschaften für Exchange ActiveSync-Postfächer:

  - AllowSimplePassword

  - BlockInternetSharing

  - BlockRemoteDesktop

  - DisableDesktopSync

  - DisableIrDA

  - DisableRemovableStorage

  - DeviceWipeThreshold

  - MinPasswordLength

  - IdleTimeoutFrequencyValue

  - PasswordExpiration

  - PasswordHistory

  - PasswordRequired

## Einstellungen für Postfachrichtlinien für mobile Geräte

Die folgende Tabelle enthält eine Zusammenfassung der Einstellungen, die mithilfe von Postfachrichtlinien für mobile Geräte festgelegt werden können.

### Einstellungen für Postfachrichtlinien für mobile Geräte

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Einstellung</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Bluetooth zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob ein mobiles Gerät Bluetooth-Verbindungen zulässt. Die verfügbaren Optionen lauten &quot;Deaktivieren&quot;, &quot;Nur Freisprechen&quot; und &quot;Zulassen&quot;. Der Standardwert ist &quot;Allow&quot;. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Browser zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob Pocket Internet Explorer auf dem mobilen Gerät zulässig ist. Sie hat keine Auswirkungen auf Webbrowser von Drittanbietern, die auf dem mobilen Gerät installiert sind. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="odd">
<td><p>Kamera zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob die Kamera des mobilen Geräts verwendet werden kann. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Consumer-E-Mail zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob der Benutzer des Mobilgeräts hierauf ein persönliches E-Mail-Konto (POP3 oder IMAP4) konfigurieren darf. Der Standardwert ist <code>$true</code>. Mit dieser Einstellung wird nicht der Zugriff auf E-Mail-Konten gesteuert, die E-Mail-Programme von Drittanbietern für Mobilgeräte verwenden. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="odd">
<td><p>Desktop-Synchronisierung zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob das mobile Gerät über eine Kabel-, Bluetooth- oder Infrarotverbindung (IrDA) mit eine Computer synchronisiert werden kann. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Externe Geräteverwaltung zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob ein externes Geräteverwaltungsprogramm das mobile Gerät verwalten darf.</p></td>
</tr>
<tr class="odd">
<td><p>E-Mails im HTML-Format zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob E-Mails, die auf das mobile Gerät synchronisiert werden, im HTML-Format vorliegen dürfen. Ist diese Einstellung auf <code>$false</code> festgelegt, werden alle E-Mail-Nachrichten in das Nur-Text-Format konvertiert.</p></td>
</tr>
<tr class="even">
<td><p>Gemeinsame Nutzung der Internetverbindung zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob das mobile Gerät als Modem für einen Desktopcomputer oder einen tragbaren Computer verwendet werden darf. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="odd">
<td><p>AllowIrDA</p></td>
<td><p>Diese Einstellung gibt an, ob Infrarotverbindungen zu und von dem mobilen Gerät zulässig sind. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>OTA-Update für mobile Geräte zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob die Postfachrichtlinien-Einstellungen für mobile Geräte über eine Mobilfunk-Datenverbindung an das mobile Gerät gesendet werden dürfen. Der Standardwert ist <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Nicht bereitstellbare Geräte zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob Mobilgeräte, die möglicherweise nicht die Anwendung aller Richtlinieneinstellungen unterstützen, mithilfe von Exchange 2013 eine Verbindung mit Exchange ActiveSync herstellen dürfen. Das Zulassen nicht bereitstellbarer Mobilegeräte hat Auswirkungen auf die Sicherheit. Beispielsweise können auf einigen nicht bereitstellbaren Geräten möglicherweise die Kennwortanforderungen einer Organisation nicht implementiert werden.</p></td>
</tr>
<tr class="even">
<td><p>POPIMAPEmail zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob der Benutzer ein POP3- oder ein IMAP4-E-Mail-Konto auf dem Mobilgerät konfigurieren darf. Der Standardwert ist <code>$true</code>. Diese Einstellung steuert nicht den Zugriff durch E-Mail-Programme von Drittanbietern.</p></td>
</tr>
<tr class="odd">
<td><p>Remotedesktop zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob das mobile Geräte eine Remotedesktopverbindung initiieren kann. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Einfaches Kennwort zulassen</p></td>
<td><p>Diese Einstellung aktiviert bzw. deaktiviert die Möglichkeit, ein einfaches Kennwort wie &quot;1111&quot; oder &quot;1234&quot; zu verwenden. Der Standardwert ist <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Aushandlung des S/MIME-Verschlüsselungsalgorithmus zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob die Messaginganwendung auf dem Mobilgerät den Verschlüsselungsalgorithmus aushandeln kann, wenn das Zertifikat eines Empfängers den angegebenen Verschlüsselungsalgorithmus nicht unterstützt.</p></td>
</tr>
<tr class="even">
<td><p>S/MIME-Softwarezertifikate zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob S/MIME-Softwarezertifikate auf dem mobilen Gerät zulässig sind.</p></td>
</tr>
<tr class="odd">
<td><p>Speicherkarte zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob das mobile Gerät auf Informationen zugreifen darf, die auf einer Speicherkarte abgelegt sind. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Textnachrichten zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob Textnachrichten von diesem mobilen Gerät zulässig sind. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="odd">
<td><p>Nicht signierte Anwendungen zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob auf dem mobilen Gerät nicht signierte Anwendungen installiert werden können. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Nicht signierte Installationspakete zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob auf dem mobilen Gerät ein nicht signiertes Installationspaket ausgeführt werden kann. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="odd">
<td><p>WiFi zulassen</p></td>
<td><p>Diese Einstellung gibt an, ob mit dem mobilen Gerät der drahtlose Internetzugriff zulässig ist. Der Standardwert ist <code>$true</code>. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Alphanumerisches Kennwort erforderlich</p></td>
<td><p>Diese Einstellung schreibt vor, dass ein Kennwort numerische und nicht-numerische Zeichen enthalten muss. Der Standardwert ist <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Liste genehmigter Anwendungen</p></td>
<td><p>Mit dieser Einstellung wird eine Liste genehmigter Anwendungen gespeichert, die auf dem mobilen Gerät ausgeführt werden dürfen. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Anlagen aktiviert</p></td>
<td><p>Diese Einstellung ermöglicht das Herunterladen von Anlagen auf das mobile Gerät. Der Standardwert ist <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Geräteverschlüsselung aktiviert</p></td>
<td><p>Diese Einstellung aktiviert die Verschlüsselung auf dem mobilen Gerät. Nicht alle mobilen Geräte können eine Verschlüsselung erzwingen. Weitere Informationen hierzu finden Sie in der Dokumentation zum Gerät sowie zum mobilen Betriebssystem.</p></td>
</tr>
<tr class="even">
<td><p>Geräterichtlinien-Aktualisierungsintervall</p></td>
<td><p>Diese Einstellung gibt an, wie oft die Postfachrichtlinie für das mobile Gerät vom Server an das mobile Gerät gesendet wird.</p></td>
</tr>
<tr class="odd">
<td><p>IRM aktiviert</p></td>
<td><p>Diese Einstellung gibt an, ob auf dem mobilen Gerät die Verwaltung von Informationsrechten (Information Rights Management, IRM) aktiviert ist.</p></td>
</tr>
<tr class="even">
<td><p>Max. Anlagengröße</p></td>
<td><p>Diese Einstellung steuert die maximale Größe von Anlagen, die auf das mobile Gerät heruntergeladen werden können. Der Standardwert ist &quot;Unbegrenzt&quot;.</p></td>
</tr>
<tr class="odd">
<td><p>Filter für max. Kalenderalter</p></td>
<td><p>Diese Einstellung gibt den maximalen Bereich der Kalendertage an, die auf das mobile Gerät synchronisiert werden können. Die folgenden Werte werden akzeptiert:</p>
<ol>
<li><p>All</p></li>
<li><p>OneDay</p></li>
<li><p>ThreeDays</p></li>
<li><p>OneWeek</p></li>
<li><p>TwoWeeks</p></li>
<li><p>OneMonth</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p>Filter für max. E-Mail-Alter</p></td>
<td><p>Mit dieser Einstellung wird die maximale Anzahl von Tagen angegeben, für die E-Mail-Elemente auf das mobile Gerät synchronisiert werden. Die folgenden Werte werden akzeptiert:</p>
<ol>
<li><p>All</p></li>
<li><p>OneDay</p></li>
<li><p>ThreeDays</p></li>
<li><p>OneWeek</p></li>
<li><p>TwoWeeks</p></li>
<li><p>OneMonth</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Max. Größe für E-Mail-Textkörperkürzung</p></td>
<td><p>Mit dieser Einstellung wird die maximale Größe angegeben, bei der E-Mail-Nachrichten bei der Synchronisierung auf das mobile Gerät abgeschnitten werden. Der Wert wird in Kilobytes (KB) angegeben.</p></td>
</tr>
<tr class="even">
<td><p>Max. Größe für E-Mail-Textkörperkürzung, HTML</p></td>
<td><p>Mit dieser Einstellung wird die maximale Größe angegeben, bei der E-Mail-Nachrichten im HTML-Format bei der Synchronisierung auf das mobile Gerät abgeschnitten werden. Der Wert wird in Kilobytes (KB) angegeben.</p></td>
</tr>
<tr class="odd">
<td><p>Zeitsperre für max. Inaktivität</p></td>
<td><p>Dieser Wert gibt an, wie lange das mobile Gerät inaktiv sein kann, bevor es mithilfe eines Kennworts erneut aktiviert werden muss. Sie können ein Intervall zwischen 30 Sekunden und einer Stunde eingeben. Der Standardwert beträgt 15 Minuten.</p></td>
</tr>
<tr class="even">
<td><p>Max. fehlgeschlagene Kennwortversuche</p></td>
<td><p>Diese Einstellung gibt die Anzahl von Versuchen an, die einem Benutzer zur Verfügung stehen, um das korrekte Kennwort für das Gerät einzugeben. Sie können einen Wert von 4 bis 16 eingeben. Der Standardwert ist 8.</p></td>
</tr>
<tr class="odd">
<td><p>Min. komplexe Zeichen im Kennwort</p></td>
<td><p>Diese Einstellung gibt die Anzahl von Zeichensätzen an, die für das Kennwort des Mobilgeräts erforderlich sind. Diese Zeichensätze sind:</p>
<ul>
<li><p>Kleinbuchstaben.</p></li>
<li><p>Großbuchstaben</p></li>
<li><p>Ziffern von 0-9</p></li>
<li><p>Sonderzeichen (z. B. Ausrufezeichen)</p></li>
</ul>
<p>Sie können einen Wert von 1 bis 4 eingeben. Der Standardwert ist 1.</p>
<p>Für Windows Phone 8-Geräte gibt diese Einstellung die Anzahl von Zeichensätzen an, die für das Kennwort erforderlich sind. Beispiel: Bei dem Wert 3 ist mindestens ein Zeichen aus jedem der drei Zeichensätze erforderlich.</p>
<p>Für Windows Phone 10-Geräte gibt diese Einstellung die folgenden Kennwortkomplexitätsanforderungen an:</p>
<ol>
<li><p>Nur Ziffern</p></li>
<li><p>Ziffern und Kleinbuchstaben</p></li>
<li><p>Ziffern, Kleinbuchstaben und Großbuchstaben</p></li>
<li><p>Ziffern, Kleinbuchstaben, Großbuchstaben und Sonderzeichen</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p>Min. Kennwortlänge</p></td>
<td><p>Diese Einstellung gibt die Mindestanzahl der Zeichen für das Kennwort des mobilen Geräts an. Sie können einen Wert von 1 bis 16 eingeben. Der Standardwert ist 4.</p></td>
</tr>
<tr class="odd">
<td><p>Kennwort aktiviert</p></td>
<td><p>Diese Einstellung aktiviert das Kennwort für das mobile Gerät.</p></td>
</tr>
<tr class="even">
<td><p>Kennwortablauf</p></td>
<td><p>Diese Einstellung ermöglicht dem Administrator das Konfigurieren eines Zeitraums, nach dem das Kennwort für das mobile Gerät geändert werden muss.</p></td>
</tr>
<tr class="odd">
<td><p>Kennwortverlauf</p></td>
<td><p>Diese Einstellung gibt die Anzahl der letzten Kennwörter an, die im Postfach eines Benutzers gespeichert werden dürfen. Ein gespeichertes Kennwort kann vom Benutzer nicht erneut verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p>Kennwortwiederherstellung aktiviert</p></td>
<td><p>Wenn diese Einstellung aktiviert ist, generiert das mobile Gerät ein Wiederherstellungskennwort, das an den Server gesendet wird. Wenn ein Benutzer das Kennwort für das mobile Gerät vergisst, kann die Sperrung des mobilen Geräts mithilfe des Wiederherstellungskennworts aufgehoben werden. Der Benutzer kann dann ein neues Kennwort für das mobile Gerät erstellen.</p></td>
</tr>
<tr class="odd">
<td><p>Geräteverschlüsselung anfordern</p></td>
<td><p>Diese Einstellung gibt an, ob eine Geräteverschlüsselung erforderlich ist. Bei Festlegung auf <code>$true</code> muss das mobile Gerät in der Lage sein, eine Verschlüsselung zu unterstützen und zu implementieren, damit es mit dem Server synchronisiert werden kann.</p></td>
</tr>
<tr class="even">
<td><p>Verschlüsselte S/MIME-Nachrichten anfordern</p></td>
<td><p>Diese Einstellung gibt an, ob S/MIME-Nachrichten verschlüsselt werden müssen. Der Standardwert ist <code>$false</code>.</p></td>
</tr>
<tr class="odd">
<td><p>S/MIME-Verschlüsselungsalgorithmus anfordern</p></td>
<td><p>Mit dieser Einstellung wird angegeben, welcher erforderliche Algorithmus beim Verschlüsseln von S/MIME-Nachrichten verwendet werden muss.</p></td>
</tr>
<tr class="even">
<td><p>Manuelle Synchronisierung beim Roaming anfordern</p></td>
<td><p>Diese Einstellung gibt an, ob das mobile Gerät beim Roaming manuell synchronisiert werden muss. Das Zulassen der automatischen Synchronisierung beim Roaming führt häufig zu höheren Datenkosten für den Datentarif des mobilen Geräts als erwartet.</p></td>
</tr>
<tr class="odd">
<td><p>Algorithmus für signiertes S/MIME anfordern</p></td>
<td><p>Mit dieser Einstellung wird angegeben, welcher erforderliche Algorithmus beim Signieren einer Nachricht verwendet werden muss.</p></td>
</tr>
<tr class="even">
<td><p>Signierte S/MIME-Nachrichten anfordern</p></td>
<td><p>Mit dieser Einstellung wird angegeben, ob das mobile Gerät nur signierte S/MIME-Nachrichten versenden darf.</p></td>
</tr>
<tr class="odd">
<td><p>Verschlüsselung der Speicherkarte anfordern</p></td>
<td><p>Diese Einstellung gibt an, ob die Speicherkarte verschlüsselt werden muss. Nicht alle Betriebssysteme für mobile Geräte unterstützen die Verschlüsselung von Speicherkarten. Weitere Informationen hierzu finden Sie in der Dokumentation zum mobilen Gerät sowie zum mobilen Betriebssystem.</p></td>
</tr>
<tr class="even">
<td><p>Liste nicht genehmigter InROM-Anwendungen</p></td>
<td><p>Diese Einstellung gibt eine Liste von Anwendungen an, die nicht im ROM ausgeführt werden dürfen. Die Exchange Enterprise-Clientzugriffslizenz ist erforderlich, um die Werte dieser Einstellung zu ändern.</p></td>
</tr>
</tbody>
</table>

