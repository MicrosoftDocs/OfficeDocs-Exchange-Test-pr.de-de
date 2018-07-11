---
title: 'Exchange Admin Center in Exchange 2013: Exchange 2013 Help'
TOCTitle: Exchange Admin Center in Exchange 2013
ms:assetid: a9aea11a-6ba3-4f4a-a76e-79072e7cfc7d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150562(v=EXCHG.150)
ms:contentKeyID: 50476410
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange Admin Center in Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-17_

Die Exchange-Verwaltungskonsole (Exchange Administration Center, EAC) ist die webbasierte Verwaltungskonsole in Microsoft Exchange Server 2013, die für lokale, Online- oder Hybridbereitstellungen von Exchange optimiert ist. Die EAC ersetzt die bisherige Exchange-Verwaltungskonsole (Exchange Management Console, EMC) und Exchange-Systemsteuerung (Exchange Control Panel, ECP), die zur Verwaltung von Exchange Server 2010 verwendet wurden.

Ein Vorteil einer webbasierte Exchange-Verwaltungskonsole ist, dass Sie im virtuellen IIS-Verzeichnis der ECP den Internet- und Intranetzugriff voneinander trennen können. Dank dieser Möglichkeit können Sie steuern, ob Benutzer von außerhalb der Organisation Zugriff auf die Exchange-Verwaltungskonsole haben dürfen, und zugleich Endbenutzern Zugriff auf Outlook Web App-Optionen bieten. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf das EAC](turn-off-access-to-the-exchange-admin-center-exchange-2013-help.md).

Suchen Sie die Exchange Online-Version dieses Themas? Weitere Informationen finden Sie unter [Exchange Admin Center in Exchange Online](https://technet.microsoft.com/de-de/library/jj200743\(v=exchg.150\)).

Suchen Sie die Exchange Online Protection-Version dieses Themas? Weitere Informationen finden Sie unter [Exchange Admin Center in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj723141\(v=exchg.150\)).

Inhalt

Zugreifen auf die Exchange-Verwaltungskonsole

Allgemeine Elemente der Benutzeroberfläche in der Exchange-Verwaltungskonsole

Unterstützte Browser

## Zugreifen auf die Exchange-Verwaltungskonsole

Weil die Exchange-Verwaltungskonsole jetzt eine webbasierte Verwaltungskonsole ist, können Sie auf diese nur zugreifen, indem Sie in Ihrem Webbrowser die URL des virtuellen ECP-Verzeichnisses verwenden. In den meisten Fällen sieht die URL der Exchange-Verwaltungskonsole wie folgt aus:

  - **Interne URL: `https://<CASServerName>/ecp`**   Die interne URL dient für den Zugriff auf die Exchange-Verwaltungskonsole von innerhalb der Firewall der Organisation.

  - **Externe URL: `https://mail.contoso.com/ecp`**   Die externe URL dient für den Zugriff auf die Exchange-Verwaltungskonsole von außerhalb der Firewall der Organisation. Einige Organisationen ziehen es möglicherweise vor, den externen Zugriff auf die Exchange-Verwaltungskonsole zu deaktivieren. Weitere Informationen finden Sie unter [Deaktivieren des Zugriffs auf das EAC](turn-off-access-to-the-exchange-admin-center-exchange-2013-help.md).

Mithilfe des Cmdlets [Get-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd351058\(v=exchg.150\)) können Sie die interne und externe URL der Exchange-Verwaltungskonsole bestimmen. Weitere Informationen finden Sie unter [Ermitteln der internen und externen URLs für die Exchange-Verwaltungskonsole](find-the-internal-and-external-urls-for-the-exchange-admin-center-exchange-2013-help.md).

Wenn in Ihrer Organisation ein Koexistenzszenario von Exchange Server 2010 und Exchange Server 2013 vorliegt und sich Ihr Postfach weiterhin auf dem Exchange 2010-Postfachserver befindet, navigiert Ihr Browser standardmäßig zur Exchange-Systemsteuerung von Exchange Server 2010. Sie können auf die Exchange-Verwaltungskonsole zugreifen, indem Sie die Exchange-Version der URL hinzufügen. Wenn Sie beispielsweise auf die Exchange-Verwaltungskonsole zugreifen möchten, deren virtuelles Verzeichnis sich auf dem Clientzugriffsserver CAS15-NA befindet, verwenden Sie die folgende URL: `https://CAS15-NA/ecp/?ExchClientVer=15`. Umgekehrt verwenden Sie, wenn Sie auf die Exchange-Systemsteuerung von Exchange 2010 zugreifen möchten und sich Ihr Postfach auf einem Exchange 2013-Postfachserver befindet, die folgende URL: `https://CAS14-NA/ecp/?ExchClientVer=14`.

## Allgemeine Elemente der Benutzeroberfläche in der Exchange-Verwaltungskonsole

In diesem Abschnitt werden die Elemente der Benutzeroberfläche beschrieben, die in der gesamten Exchange-Verwaltungskonsole verwendet werden.

![Exchange-Verwaltungskonsole](images/JJ150562.cd617bc0-19ef-47d2-bba1-4e9546b12e0c(EXCHG.150).gif "Exchange-Verwaltungskonsole")

## Standortübergreifende Navigation

Mithilfe der standortübergreifenden Navigation können Sie schnell zwischen Ihrer Exchange Online- und lokalen Exchange-Bereitstellung wechseln. Wenn Sie keine Exchange Online-Organisation haben, werden Sie vom Link zur Anmeldeseite von Office 365 geführt. Weitere Informationen finden Sie unter [Hybridbereitstellungen in Exchange Server](https://technet.microsoft.com/de-de/library/jj200581\(v=exchg.150\)).

## Featurebereich

Dies ist die erste Navigationsebene für die meisten Aufgaben, die Sie in der Exchange-Verwaltungskonsole ausführen. Der Featurebereich ist mit der Konsolenstruktur in der Exchange-Verwaltungskonsole in Exchange 2010 vergleichbar. Allerdings ist der Featurebereich in Exchange 2013 nach Featureteilbereichen statt nach Serverrollen organisiert, und es sind weniger Klicks erforderlich, um das jeweils benötigte Element zu finden.

  - **Empfänger   **Mit diesem Feature können Sie Postfächer, Gruppen, Ressourcenpostfächer, Kontakte, freigegebene Postfächer sowie Postfachmigrationen und -verschiebungen verwalten.

  - **Berechtigungen   **Mit diesem Feature können Sie Administrator- und Benutzerrollen sowie Outlook Web App-Richtlinien verwalten.

  - **Verwaltung der Richtlinientreue   **Mit diesem Feature können Sie die Compliance-eDiscovery, Compliance-Archive, Überwachung, Verhinderung von Datenverlust, Aufbewahrungsrichtlinien, Aufbewahrungstags und Journalregeln verwalten.

  - **Organisation   **Mit diesem Feature können Sie die Aufgaben verwalten, die Ihre Exchange-Organisation betreffen. Dazu gehören Verbundfreigaben, Outlook-Apps und Adresslisten.

  - **Schutz   **Mit diesem Feature können Sie den Antischadsoftwareschutz für Ihre Organisation verwalten.

  - **Nachrichtenfluss   **Mit diesem Feature können Sie Regeln, Zustellungsberichte, akzeptierte Domänen, E-Mail-Adressrichtlinien sowie Sende- und Empfangsconnectors verwalten.

  - **Mobil   **Mit diesem Feature können Sie die mobilen Geräte verwalten, über die Sie Verbindungen mit Ihrer Organisation zulassen. Sie können den Zugriff auf und die Richtlinien für mobile Geräte verwalten.

  - **Öffentliche Ordner   **In Exchange 2010 mussten Sie öffentliche Ordner mit der Verwaltungskonsole für öffentliche Ordner verwalten, die sich außerhalb der Exchange-Verwaltungskonsole in der Toolbox befindet. In Exchange 2013 können öffentliche Ordner im Featurebereich **Öffentliche Ordner** verwaltet werden.

  - **Unified Messaging   **Mit diesem Feature können Sie UM-Wählpläne und UM-IP-Gateways verwalten.

  - **Server   **Mit diesem Feature können Sie Ihre Postfach- und Clientzugriffsserver, Datenbanken, Database Availability Groups, virtuellen Verzeichnisse und Zertifikate verwalten.

  - **Hybrid   **Mit diesem Feature können Sie eine Hybridorganisation einrichten und konfigurieren.

## Registerkarten

Die Registerkarten sind Ihre zweite Ebene der Navigation. Alle Featurebereiche enthalten verschiedene Registerkarten, die jeweils ein vollständiges Feature repräsentieren. Die einzige Ausnahme zu dieser Regel ist der Featurebereich Hybrid. Sie müssen zunächst Ihre Organisation mit dem Assistenten für Hybridkonfigurationen für eine Hybridbereitstellung aktivieren.

## Symbolleiste

Für die meisten Registerkarten wird eine Symbolleiste angezeigt, nachdem Sie auf sie geklickt haben. Die Symbolleiste enthält Symbole, die jeweils eine bestimmte Aktion auslösen. In der folgenden Tabelle werden die gängigsten Symbole und ihre Aktionen beschrieben. Um die Aktion einzublenden, die einem Symbol zugeordnet ist, bewegen Sie den Mauszeiger über dem Symbol.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Symbol</th>
<th>Name</th>
<th>Aktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><img src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif" title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" /></p></td>
<td><p>Hinzufügen, Neu</p></td>
<td><p>Über dieses Symbol können Sie ein neues Objekt erstellen. Bei einigen dieser Symbole gibt es einen dazugehörigen nach unten zeigenden Pfeil, auf den Sie klicken können, um weitere Objekte anzuzeigen, die Sie erstellen können. In <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> werden beispielsweise durch Klicken auf den nach unten zeigenden Pfeil die zusätzlichen Optionen <strong>Benutzerpostfach</strong> und <strong>Verknüpftes Postfach</strong> angezeigt.</p></td>
</tr>
<tr class="even">
<td><p><img src="images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif" title="Bearbeitungssymbol" alt="Bearbeitungssymbol" /></p></td>
<td><p>Bearbeiten</p></td>
<td><p>Über dieses Symbol können Sie ein Objekt bearbeiten.</p></td>
</tr>
<tr class="odd">
<td><p><img src="images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif" title="Löschen (Symbol)" alt="Löschen (Symbol)" /></p></td>
<td><p>Löschen</p></td>
<td><p>Über dieses Symbol können Sie ein Objekt löschen. Bei einigen Löschsymbolen gibt es einen nach unten zeigenden Pfeil, auf den Sie zum Einblenden weiterer Optionen klicken können.</p></td>
</tr>
<tr class="even">
<td><p><img src="images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif" title="Suchen (Symbol)" alt="Suchen (Symbol)" /></p></td>
<td><p>Suche</p></td>
<td><p>Über dieses Symbol können Sie ein Suchfeld öffnen, in das Sie den Suchbegriff für ein zu suchendes Objekt eingeben können. Weitere Suchoptionen finden Sie unter <a href="https://technet.microsoft.com/de-de/library/jj156853(v=exchg.150)">Empfänger &gt; Erweiterte Suche</a>.</p></td>
</tr>
<tr class="odd">
<td><p><img src="images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif" title="Aktualisieren (Symbol)" alt="Aktualisieren (Symbol)" /></p></td>
<td><p>Aktualisieren</p></td>
<td><p>Über dieses Symbol können Sie die Listenansicht aktualisieren.</p></td>
</tr>
<tr class="even">
<td><p><img src="images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif" title="Weitere Optionen (Symbol)" alt="Weitere Optionen (Symbol)" /></p></td>
<td><p>Weitere Optionen</p></td>
<td><p>Über dieses Symbol können Sie mehrere Aktionen anzeigen, die Sie auf die Objekte dieser Registerkarte anwenden können. Unter <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> werden durch Klicken auf dieses Symbol die folgenden Optionen angezeigt: <strong>Deaktivieren</strong>, <strong>Spalten hinzufügen/entfernen</strong>, <strong>Daten in eine CSV-Datei exportieren</strong>, <strong>Postfach verbinden</strong> und <strong>Erweiterte Suche</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><img src="images/JJ150576.1732c727-328b-4a1a-b84d-6d7252c7dcab(EXCHG.150).gif" title="NACH-OBEN-TASTE (Symbol)" alt="NACH-OBEN-TASTE (Symbol)" />   <img src="images/JJ150576.ef5ca57d-a033-457b-bd92-6361877c33d0(EXCHG.150).gif" title="NACH-UNTEN-TASTE (Symbol)" alt="NACH-UNTEN-TASTE (Symbol)" /></p></td>
<td><p>Pfeil nach oben und Pfeil nach unten</p></td>
<td><p>Mithilfe dieser Symbole können Sie die Priorität eines Objekts nach oben oder unten verschieben. Klicken Sie beispielsweise in <strong>Nachrichtenfluss</strong> &gt; <strong>E-Mail-Adressrichtlinien</strong> auf den nach oben zeigenden Pfeil, um die Priorität einer E-Mail-Adressrichtlinie zu erhöhen. Sie können auch mithilfe dieser Pfeile durch die Hierarchie öffentlicher Ordner navigieren und Regeln in der Listenansicht nach oben oder unten verschieben.</p></td>
</tr>
<tr class="even">
<td><p><img src="images/JJ657480.ed7f7abf-39d8-4f43-a918-ccb3bff87ef5(EXCHG.150).gif" title="Kopieren (Symbol)" alt="Kopieren (Symbol)" /></p></td>
<td><p>Kopieren</p></td>
<td><p>Über dieses Symbol können Sie ein Objekt kopieren, damit Sie es ändern können, ohne das ursprüngliche Objekt zu ändern. Wählen Sie beispielsweise in <strong>Berechtigungen</strong> &gt; <strong>Administratorrollen</strong> in der Listenansicht eine Rolle aus, und klicken Sie auf dieses Symbol. Nun können Sie eine neue Rollengruppe erstellen, die auf einer vorhandenen Rollengruppe basiert.</p></td>
</tr>
<tr class="odd">
<td><p><img src="images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif" title="Entfernen (Symbol)" alt="Entfernen (Symbol)" /></p></td>
<td><p>Entfernen</p></td>
<td><p>Über dieses Symbol können Sie ein Element aus einer Liste entfernen. Im Dialogfeld <strong>Berechtigungen für Öffentliche Ordner</strong> können Sie beispielsweise Benutzer aus der Liste der Benutzer entfernen, die auf den öffentlichen Ordner zugreifen dürfen, indem Sie den Benutzer auswählen und auf dieses Symbol klicken.</p></td>
</tr>
</tbody>
</table>


## Listenansicht

Wenn Sie auf eine Registerkarte klicken, sehen Sie in den meisten Fällen eine Listenansicht. Die Listenansicht in der Exchange-Verwaltungskonsole wurde umgestaltet, sodass es einige Einschränkungen nicht mehr gibt, die für die Exchange-Systemsteuerung galten. In der Exchange-Systemsteuerung konnten nur bis zu 500 Objekte angezeigt werden, und um Objekte anzuzeigen, die im Detailbereich nicht aufgeführt wurden, mussten Sie mithilfe von Such- und Filterfunktionen nach diesen Objekten suchen. In Exchange 2013 ist die Listenansicht in der Exchange-Verwaltungskonsole auf etwa 20.000 Objekte in lokalen Bereitstellungen und 10.000 Objekte in Exchange Online begrenzt. Darüber hinaus können Sie die Ergebnisse seitenweise anzeigen. In der Listenansicht **Empfänger** können Sie außerdem die Seitengröße konfigurieren und die Daten in eine CSV-Datei exportieren.

## Detailbereich

Wenn Sie in der Listenansicht ein Objekt auswählen, werden Informationen zu diesem Objekt im Detailbereich angezeigt. In einigen Fällen (z. B. bei Empfängerobjekten) enthält der Detailbereich Schnellverwaltungsaufgaben. Wenn Sie z. B. zu **Empfänger** \> **Postfächer** navigieren und ein Postfach in der Listenansicht auswählen, wird im Detailbereich eine Option angezeigt, über die Sie das Archiv für dieses Postfach aktivieren oder deaktivieren können. Der Detailbereich kann auch für die Massenbearbeitung mehrerer Objekte genutzt werden. Klicken Sie bei gedrückter STRG-TASTE auf die für die Massenbearbeitung gewünschten Objekte, und wählen Sie anschließend im Detailbereich die Optionen aus. Durch Auswählen mehrerer Postfächer können Sie beispielsweise eine Massenaktualisierung u. a. der Kontakt- und Organisationsinformationen, benutzerdefinierten Attribute, Postfachkontingente und Outlook Web App-Einstellungen durchführen.

## Benachrichtigungen

Die Exchange-Verwaltungskonsole weist eine Benachrichtigungsanzeige auf, sodass Sie den Status lang dauernder Prozesse anzeigen und Benachrichtigungen erhalten, sobald ein Prozess abgeschlossen ist. Für besonders lang dauernde Prozesse (beispielsweise Verschiebungsanforderungen) können Sie außerdem E-Mail-Benachrichtigungen anfordern.

## Ich-Kachel und Hilfe

Über die *Ich-Kachel* können Sie sich von der Exchange-Verwaltungskonsole abmelden und als ein anderer Benutzer anmelden. Über das Dropdownmenü der Hilfe ![Hilfe (Symbol)](images/JJ150562.a32eac4e-345d-4236-a284-204390aff4ee(EXCHG.150).gif "Hilfe (Symbol)") können Sie folgende Aktionen ausführen:

  - **Hilfe**   Klicken Sie auf ![Hilfe (Symbol)](images/JJ150562.a32eac4e-345d-4236-a284-204390aff4ee(EXCHG.150).gif "Hilfe (Symbol)"), damit der Inhalt der Onlinehilfe angezeigt wird.

  - **Hilfe-Sprechblase deaktivieren**   In der Hilfe-Sprechblase wird Kontexthilfe für Felder angezeigt, wenn Sie ein Objekt erstellen oder bearbeiten. Sie können die Hilfe-Sprechblase deaktivieren oder aktivieren, wenn sie deaktiviert ist.

  - **Copyright und Datenschutz   **Klicken Sie auf den entsprechenden Link, um die Copyright- und Datenschutzinformationen zu Exchange 2013 zu lesen.

## Unterstützte Browser

Für die beste Benutzererfahrung mit der Exchange-Verwaltungskonsole sollten Sie eine Kombination aus Betriebssystem und Browser mit der Bezeichnung "Premium" verwenden.


> [!NOTE]
> Weitere Kombinationen aus Betriebssystemen und Browsern, die nicht aufgelistet werden, werden nicht unterstützt.



  - **Premium:**  Alle Funktionalitäten werden unterstützt und wurden umfassend getestet.

  - **Unterstützt:**  Bietet dieselbe Unterstützung der Funktionalitäten wie "Premium". Unterstützte Browser enthalten jedoch die Features nicht, die von der Kombination aus Browser und Betriebssystem nicht unterstützt werden.

  - **Nicht unterstützt:**  Der Browser und das Betriebssystem werden nicht unterstützt oder wurden nicht getestet.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Webbrowser</p></td>
<td><p>Windows XP und Windows Server 2003</p></td>
<td><p>Windows Vista</p></td>
<td><p>Windows 7 und Windows Server 2008</p></td>
<td><p>Windows 8 und Windows Server 2012</p></td>
<td><p>Mac OS X</p></td>
<td><p>Linux</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 8</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Premium</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="odd">
<td><p>Internet Explorer 9</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Premium</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Internet Explorer 10 oder höher</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Premium</p></td>
<td><p>Premium</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="odd">
<td><p>Firefox 11 oder höher</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Premium</p></td>
<td><p>Premium</p></td>
<td><p>Premium</p></td>
<td><p>Unterstützt</p></td>
</tr>
<tr class="even">
<td><p>Safari 5,1 oder höher</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Nicht unterstützt</p></td>
<td><p>Premium</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
<tr class="odd">
<td><p>Chrome 18 oder höher</p></td>
<td><p>Unterstützt</p></td>
<td><p>Unterstützt</p></td>
<td><p>Premium</p></td>
<td><p>Premium</p></td>
<td><p>Premium</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
</tbody>
</table>

