---
title: 'Getrennte Postfächer: Exchange 2013 Help'
TOCTitle: Getrennte Postfächer
ms:assetid: 508ebe2b-387d-4867-bdb0-028ef351ce56
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232039(v=EXCHG.150)
ms:contentKeyID: 50554820
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Getrennte Postfächer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Jedes Microsoft Exchange-Postfach besteht aus einem Active Directory-Benutzerkonto und den Postfachdaten, die in der Exchange-Postfachdatenbank gespeichert sind. Sämtliche Konfigurationsdaten für ein Postfach werden in den Exchange-Attributen des Active Directory-Benutzerobjekts gespeichert. Die Postfachdatenbank enthält die E-Mail-Daten, die sich in dem Postfach befinden, das dem Benutzerkonto zugeordnet ist. Die folgende Abbildung zeigt die Komponenten eines Postfachs.

**Postfachkomponenten**

![Bestandteile eines Postfachs](images/Bb201680.5fcb5e6d-656e-42ae-871f-0eef8aea456b(EXCHG.150).gif "Bestandteile eines Postfachs")

Bei einem *getrennten Postfach* handelt es sich um ein Postfachobjekt in der Postfachdatenbank, das keinem Active Directory-Benutzerkonto zugeordnet ist. Es gibt zwei Typen von getrennten Postfächern:

  - **Deaktivierte Postfächer**   Wenn ein Postfach in der Exchange-Verwaltungskonsole oder mithilfe des Cmdlets **Disable-Mailbox** oder **Remove-Mailbox** in der Exchange-Verwaltungsshell deaktiviert oder gelöscht wird, bewahrt Exchange das gelöschte Postfach in der Postfachdatenbank auf und deaktiviert das Postfach. Aus diesem Grund werden deaktivierte bzw. gelöschte Postfächer als *deaktivierte Postfächer* bezeichnet. Der Unterschied ist, dass beim Deaktivieren eines Postfachs die Exchange-Attribute aus dem entsprechenden Active Directory-Benutzerkonto entfernt werden, das Benutzerkonto jedoch aufbewahrt wird. Beim Löschen eines Postfachs werden sowohl die Exchange-Attribute als auch das Active Directory-Benutzerkonto gelöscht.
    
    Deaktivierte und gelöschte Postfächer werden in der Postfachdatenbank bis zum Ablauf des Aufbewahrungszeitraum für gelöschte Postfächer aufbewahrt, also standardmäßig 30 Tage. Nach Ablauf des Aufbewahrungszeitraums wird das Postfach *endgültig gelöscht*. Wird ein Postfach mithilfe des Cmdlets **Remove-Mailbox** gelöscht, erfolgt ebenfalls eine Aufbewahrung bis zum Ablauf des Aufbewahrungszeitraums.
    

    > [!IMPORTANT]  
    > Wird ein Postfach mithilfe des Cmdlets <STRONG>Remove-Mailbox</STRONG> und mit dem Parameter <EM>Permanent</EM> oder <EM>StoreMailboxIdentity</EM> gelöscht, dann wird das Postfach umgehend aus der Postfachdatenbank gelöscht.

    
    Führen Sie zum Ermitteln der deaktivierten Postfächer in Ihrer Organisation den folgenden Befehl in der Shell aus:
    
      ```powershell
      Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisconnectReason -eq "Disabled" } | ft DisplayName,Database,DisconnectDate
      ```

  - **Vorläufig gelöschte Postfächer**   Wenn ein Postfach in eine andere Postfachdatenbank verschoben wird, löscht Exchange das Postfach nach Abschluss des Vorgangs nicht vollständig aus der Quelldatenbank. Stattdessen wird das Postfach in der Quellpostfachdatenbank in einen Zustand *vorläufiger Löschung* versetzt. Wie deaktivierte Postfächer werden vorläufig gelöschte Postfächer in der Quelldatenbank aufbewahrt, bis der Aufbewahrungszeitraum für gelöschte Postfächer abgelaufen ist oder das Postfach mit dem Cmdlet **Remove-StoreMailbox** endgültig gelöscht wird.
    
    Führen Sie den folgenden Befehl aus, um die in Ihrer Organisation vorläufig gelöschten Postfächer zu ermitteln:
    
      ```powershell
      Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisconnectReason -eq "SoftDeleted" } | ft DisplayName,Database,DisconnectDate
      ```

**Inhalt**

Arbeiten mit deaktivierten Postfächern

Arbeiten mit deaktivierten Archivpostfächern

Arbeiten mit vorläufig gelöschten Postfächern

Zusammenfassung – Arbeiten mit getrennten Postfächern

Dokumentation zu getrennten Postfächern

## Arbeiten mit deaktivierten Postfächern

Sie können mehrere Vorgänge für ein deaktiviertes Postfach ausführen, bevor es endgültig aus der Postfachdatenbank gelöscht wird:

  - Verbinden Sie es wieder mit demselben Benutzerkonto.

  - Verbinden Sie es mit einem anderen Benutzerkonto, das nicht E-Mail-aktiviert ist und entsprechend nicht über ein Postfach verfügt.

  - Stellen Sie es in einem Benutzerkonto wieder her, das ein vorhandenes Postfach hat. Wenn ein Benutzer, dessen Postfach gelöscht wurde, ein neues Postfach hat, können Sie beispielsweise das deaktivierte Postfach im neuen Postfach wiederherstellen.

  - Löschen Sie das Postfach endgültig aus der Exchange-Postfachdatenbank.

## Verbinden oder Wiederherstellen eines deaktivierten Postfachs

Nachstehend werden Szenarien beschrieben, in denen es sich empfiehlt, ein deaktiviertes Postfach vor Ablauf des Aufbewahrungszeitraums für gelöschte Postfächer bzw. vor dem endgültigen Löschen zu verbinden oder wiederherzustellen:

  - Sie haben ein Postfach deaktiviert und möchten nun erneut eine Verbindung des Postfachs mit demselben Active Directory-Benutzerkonto herstellen.

  - Sie haben ein Postfach mithilfe der Exchange-Verwaltungskonsole oder des Cmdlets [Remove-Mailbox](https://technet.microsoft.com/de-de/library/aa995948\(v=exchg.150\)) gelöscht und möchten das Postfach jetzt mit einem anderen Active Directory-Benutzerkonto neu verbinden.

  - Sie haben ein Postfach gelöscht und möchten es jetzt in einem vorhandenen Postfach wiederherstellen. Wenn ein Benutzer, dessen Postfach gelöscht wurde, ein neues Postfach hat, können Sie beispielsweise das deaktivierte Postfach im neuen Postfach wiederherstellen.

  - Sie möchten ein Benutzerportfach in ein verknüpftes Postfach konvertieren, das einem (externen) Benutzerkonto außerhalb der Gesamtstruktur zugeordnet ist, in der sich die Exchange-Organisation befindet. Im Szenario einer Ressourcengesamtstruktur ist es beispielsweise erforderlich, ein Postfach einem externen Konto zuzuordnen. In diesem Szenario verfügen Benutzerobjekte in der Exchange-Gesamtstruktur über Postfächer, aber die Benutzerobjekte sind deaktiviert und können nicht für Anmeldezwecke verwendet werden. Sie müssen ein Postfach in der Exchange-Gesamtstruktur einem Benutzerkonto in der externen Kontengesamtstruktur zuordnen.

Es gibt zwei Möglichkeiten zum Verbinden oder Wiederherstellen eines deaktivierten Postfachs. Eine Möglichkeit ist die Verwendung der Exchange-Verwaltungskonsole oder des Cmdlets **Connect-Mailbox**, um das Postfach mit einem Benutzerkonto zu verbinden. Vorgehensweisen zum erneuten Verbinden deaktivierter Postfächer finden Sie unter [Verbinden eines deaktivierten Postfachs](connect-a-disabled-mailbox-exchange-2013-help.md).

Eine zweite Möglichkeit ist die Verwendung des Cmdlets **New-MailboxRestoreRequest**, um die Inhalte des deaktivierten Postfachs mit denen eines vorhandenen Postfachs zusammenzuführen. Dieses Cmdlet verwendet zum erneuten Verbinden des Postfachs den Postfachreplikationsdienst (Mailbox Replication Service, MRS). Vorgehensweisen zum Wiederherstellen deaktivierter Postfächer finden Sie unter [Verbinden oder Wiederherstellen eines gelöschten Postfachs](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md).

## Endgültiges Löschen eines deaktivierten Postfachs

Wie zuvor erwähnt, werden deaktivierte Postfächer in Exchange in der Postfachdatenbank basierend auf den für die Postfachdatenbank konfigurierten Aufbewahrungseinstellungen für gelöschte Postfächer aufbewahrt. Nach Ablauf des festgelegten Aufbewahrungszeitraums wird ein deaktiviertes Postfach endgültig aus der Exchange-Postfachdatenbank gelöscht. Sie können ein deaktiviertes Postfach und alle darin enthaltenen Nachrichten mithilfe des Cmdlets **Remove-StoreMailbox** endgültig aus der Postfachdatenbank löschen. Sobald ein deaktiviertes Postfach entweder automatisch oder durch einen Administrator endgültig gelöscht wurde, ist der Datenverlust dauerhaft und das Postfach kann nicht wiederhergestellt werden.

Weitere Informationen finden Sie unter [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md).

Arbeiten mit deaktivierten Postfächern

## Arbeiten mit deaktivierten Archivpostfächern

Archivpostfächer werden getrennt, wenn sie deaktiviert werden. Ein getrenntes Archivpostfach kann auf ähnliche Weise wie deaktivierte primäre Postfächer mithilfe des Cmdlets **Connect-Mailbox** mit dem Parameter *Archive* verbunden werden.

Das primäre Postfach und das Archivpostfach verwenden denselben Legacy-DN (Distinguished Name). Daher müssen Sie das Archivpostfach mit demselben Benutzerpostfach verbinden, mit dem es zuvor verbunden war. Das Archivpostfach kann nicht mit einem anderen Benutzerpostfach verbunden werden.

Sie können zwei Vorgänge für ein deaktiviertes Archivpostfach ausführen:

  - **Verbinden mit einem vorhandenen Postfach**   Wie getrennte primäre Postfächer werden getrennte Archivpostfächer in der Postfachdatenbank aufbewahrt, bis der Aufbewahrungszeitraum für gelöschte Postfächer abgelaufen ist. Der Standardaufbewahrungszeitraum beträgt 30 Tage. Während dieses Zeitraums können Sie das Archivpostfach wiederherstellen, indem Sie es mit demselben Benutzerkonto verbinden, mit dem es vor der Deaktivierung verbunden war.
    

    > [!NOTE]  
    > Wenn Sie ein Archivpostfach für ein Benutzerpostfach deaktivieren und anschließend ein Archivpostfach für denselben Benutzer aktivieren, erhält das Benutzerpostfach ein neues Archivpostfach. Während Sie das Cmdlet <STRONG>Connect-Mailbox</STRONG> zum Verbinden eines primären Postfachs mit einem Benutzer verwenden können, müssen Sie das Cmdlet <STRONG>Enable-Mailbox</STRONG> verwenden, um ein deaktiviertes Archivpostfach mit einem vorhandenen Postfach zu verbinden.

    
    Weitere Informationen finden Sie unter [Verwalten von In-Situ-Archiven in Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md).

  - **Endgültiges Löschen aus der Exchange-Postfachdatenbank**    Deaktivierte Postfächer werden in Exchange in der Postfachdatenbank basierend auf den für die Postfachdatenbank konfigurierten Aufbewahrungseinstellungen für gelöschte Postfächer aufbewahrt. Der Standardaufbewahrungszeitraum beträgt 30 Tage. Nach Ablauf des festgelegten Aufbewahrungszeitraums wird ein getrenntes Archivpostfach endgültig aus der Exchange-Postfachdatenbank gelöscht.
    
    Ein deaktiviertes Archivpostfach kann auf ähnliche Weise wie deaktivierte primäre Postfächer mithilfe des Cmdlets **Remove-StoreMailbox** gelöscht werden. Weitere Informationen finden Sie unter [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md).

Arbeiten mit deaktivierten Postfächern

## Arbeiten mit vorläufig gelöschten Postfächern

Ein vorläufig gelöschtes Postfach wird erstellt, wenn das Postfach aus einer Exchange-Postfachdatenbank in eine andere Postfachdatenbank verschoben wird. Für den Fall, dass das Postfach durch einen während der Verschiebung aufgetretenen Fehler nicht in der Zieldatenbank verwendet werden kann, wird das Postfach in Exchange nach dem Verschieben nicht vollständig aus der Quelldatenbank gelöscht. Sie können das Quellpostfach immer wiederherstellen und den Vorgang wiederholen. Das vorläufig gelöschte Postfach wird in Exchange bis zum Ablauf des Aufbewahrungszeitraums aufbewahrt.

Sie können zwei Vorgänge für ein vorläufig gelöschtes Postfach ausführen:

  - Stellen Sie das Postfach in einem vorhandenen Postfach wieder her.

  - Löschen Sie das Postfach endgültig aus der Exchange-Postfachdatenbank.

Diese Verfahren zum Wiederherstellen und endgültigen Löschen eines vorläufig gelöschten Postfachs ähneln denen Verfahren für ein deaktiviertes Postfach. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Wiederherstellen eines vorläufig gelöschten Postfachs](restore-a-soft-deleted-mailbox-exchange-2013-help.md)

  - [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md)

Arbeiten mit deaktivierten Postfächern

## Zusammenfassung – Arbeiten mit getrennten Postfächern

In der folgenden Tabelle sind die Informationen über getrennte Postfächer aufgeführt, einschließlich Informationen darüber, wie das Postfach getrennt wurde, was mit dem entsprechenden Active Directory-Benutzerkonto geschieht, wenn ein Postfach getrennt wird, sowie die Optionen und Tools, die zum Verbinden oder Wiederherstellen getrennter Postfächer zur Verfügung stehen.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Wie das Postfach deaktiviert wurde</th>
<th>Wert der Eigenschaft <em>DisconnectReason</em></th>
<th>Wird das Active Directory-Benutzerkonto beibehalten?</th>
<th>Optionen zum Verbinden oder Wiederherstellen</th>
<th>Tools</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>Die Exchange-Verwaltungskonsole: <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Deaktivieren</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>Disable-Mailbox</strong></p></li>
</ul></td>
<td><p>Deaktiviert</p></td>
<td><p>Ja</p></td>
<td><p>Verbinden mit demselben Benutzerkonto</p></td>
<td><ul>
<li><p>Die Exchange-Verwaltungskonsole: <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Postfach verbinden</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>Connect-Mailbox</strong></p></li>
</ul></td>
</tr>
<tr class="even">
<td><ul>
<li><p>Die Exchange-Verwaltungskonsole: <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Löschen</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>Remove-Mailbox</strong></p></li>
</ul></td>
<td><p>Deaktiviert</p></td>
<td><p>Nein</p></td>
<td><ul>
<li><p>Verbinden mit einem anderen Benutzerkonto</p></li>
<li><p>Wiederherstellen in einem anderen Postfach</p></li>
</ul></td>
<td><ul>
<li><p>Die Exchange-Verwaltungskonsole: <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Postfach verbinden</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>Connect-Mailbox</strong></p></li>
<li><p><strong>Enable-Mailbox</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>New-MailboxRestore</strong></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Verschoben in eine andere Postfachdatenbank</p></td>
<td><p>SoftDeleted</p></td>
<td><p>Ja</p></td>
<td><ul>
<li><p>Verbinden mit einem anderen Benutzerkonto</p></li>
<li><p>Wiederherstellen in einem anderen Postfach</p></li>
</ul></td>
<td><ul>
<li><p>Die Exchange-Verwaltungskonsole: <strong>Empfänger</strong> &gt; <strong>Postfächer</strong> &gt; <strong>Postfach verbinden</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>Connect-Mailbox</strong></p></li>
<li><p><strong>Enable-Mailbox</strong></p></li>
<li><p>Die Shell: Cmdlet <strong>New-MailboxRestore</strong></p></li>
</ul></td>
</tr>
</tbody>
</table>


Arbeiten mit deaktivierten Postfächern

## Dokumentation zu getrennten Postfächern

Die folgende Tabelle enthält Links zu Themen, die Sie beim Verwalten getrennter Postfächer unterstützen. Dies umfasst das Verwalten getrennter Benutzerpostfächer, verknüpfter Postfächer, Ressourcenpostfächer und freigegebener Postfächer.


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
<td><p><a href="disable-or-delete-a-mailbox-exchange-2013-help.md">Deaktivieren oder Löschen eines Postfachs</a></p></td>
<td><p>Informationen zum Deaktivieren oder Löschen von Postfächern.</p></td>
</tr>
<tr class="even">
<td><p><a href="connect-a-disabled-mailbox-exchange-2013-help.md">Verbinden eines deaktivierten Postfachs</a></p></td>
<td><p>Informationen zum Verbinden eines deaktivierten Postfachs mit einem vorhandenen Benutzerkonto.</p></td>
</tr>
<tr class="odd">
<td><p><a href="connect-or-restore-a-deleted-mailbox-exchange-2013-help.md">Verbinden oder Wiederherstellen eines gelöschten Postfachs</a></p></td>
<td><p>Informationen zum Verbinden eines gelöschten Postfachs mit einem Benutzerkonto oder zum Wiederherstellen der Inhalte eines gelöschten Postfachs in einem vorhandenen Postfach.</p></td>
</tr>
<tr class="even">
<td><p><a href="restore-a-soft-deleted-mailbox-exchange-2013-help.md">Wiederherstellen eines vorläufig gelöschten Postfachs</a></p></td>
<td><p>Informationen zum Verbinden eines vorläufig gelöschten Postfachs mit einem Benutzerkonto oder zum Wiederherstellen eines vorläufig gelöschten Postfachs in einem vorhandenen Postfach.</p></td>
</tr>
<tr class="odd">
<td><p><a href="manage-mailbox-restore-requests-exchange-2013-help.md">Verwalten von Postfachwiederherstellungsanforderungen</a></p></td>
<td><p>Informationen zum Verwalten von Postfachwiederherstellungsanforderungen mithilfe der Shell.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><a href="permanently-delete-a-mailbox-exchange-2013-help.md">Endgültiges Löschen eines Postfachs</a></p></td>
<td><p>Informationen zum endgültigen Löschen eines Postfachs.</p></td>
</tr>
</tbody>
</table>


Arbeiten mit deaktivierten Postfächern