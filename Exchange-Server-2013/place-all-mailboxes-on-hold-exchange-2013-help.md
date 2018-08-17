---
title: 'Platzieren aller Postfächer im Archiv: Exchange 2013 Help'
TOCTitle: Platzieren aller Postfächer im Archiv
ms:assetid: 4c141604-3210-44cc-b98e-f3e0f15613b8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn767952(v=EXCHG.150)
ms:contentKeyID: 62486283
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Platzieren aller Postfächer im Archiv

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-01-18_


> [!NOTE]
> Wir haben den Stichtag (1. Juli 2017) für das Erstellen neuer In-Situ-Speicher in Exchange Online (in Office 365 und eigenständigen Exchange Online-Plänen) verschoben. Im späteren Verlauf dieses Jahres oder Anfang des nächsten Jahres können Sie keine neuen In-Situ-Speicher mehr in Exchange Online erstellen. Als Alternative zur Verwendung von In-Situ-Speichern können Sie <A href="https://go.microsoft.com/fwlink/?linkid=780738">eDiscovery-Fälle</A> oder <A href="https://go.microsoft.com/fwlink/?linkid=827811">Aufbewahrungsrichtlinien</A> im Office 365-Sicherheit &amp; Compliance Center verwenden. Sobald die Erstellung neuer In-Situ-Speicher eingestellt ist, können vorhandene In-Situ-Speicher weiterhin geändert werden, und das Erstellen neuer In-Situ-Speicher in Exchange Server&nbsp;2013- und Exchange-Hybridbereitstellungen wird weiterhin unterstützt. Und Sie können weiterhin Postfächer im Beweissicherungsverfahren platzieren.



In Ihrer Organisation kann es erforderlich sein, alle Postfachdaten eine bestimmte Zeit lang aufzubewahren. Sie können dazu ein Beweissicherungsverfahren oder Compliance-Archiv aktivieren. Nachdem Sie für ein Postfach ein Beweissicherungsverfahren oder einen In-Situ-Speicher aktiviert haben, werden Postfachelemente, die verändert oder gelöscht werden, dauerhaft im Ordner "Wiederherstellbare Elemente" beibehalten. Weitere Informationen finden Sie unter [In-Place Hold and Litigation Hold](in-place-hold-and-litigation-hold-exchange-2013-help.md).

Berücksichtigen Sie Folgendes, bevor Sie für alle Postfächer in einer Organisation ein Beweissicherungsverfahren oder Compliance-Archiv aktivieren:

  - Wenn Sie Postfächer archivieren, wird auch der Inhalt im Archivpostfach des Benutzers archiviert, wenn dieses aktiviert ist.

  - Alle Postfächer in einer Organisation im Archiv zu platzieren, kann die Postfachgröße erheblich erhöhen. Planen Sie in einer Exchange Server 2013-Bereitstellung ausreichend Speicherplatz ein, um die Aufbewahrungsanforderungen Ihrer Organisation zu erfüllen. In Exchange Online hängen [Postfachspeicherbegrenzungen](https://go.microsoft.com/fwlink/?linkid=403645) für Ihre Benutzer von der Abonnementlizenz des Benutzers ab.

  - Wenn Sie Postfachdaten über einen langen Zeitraum aufbewahren, nimmt die Datenmenge im Postfach und Archiv eines Benutzers im Ordner "Wiederherstellbare Elemente" zu. Für den Ordner "Wiederherstellbare Elemente" gilt eine eigene Speicherbegrenzung, sodass Elemente in diesem Ordner nicht zur Speicherbegrenzung des Postfachs zählen. In Exchange Server 2013 und Exchange Online beträgt die standardmäßige Speichergrenze für den Ordner "Wiederherstellbare Elemente" 30 GB.
    
      - In Exchange Online wird das Kontingent für den Ordner "Wiederherstellbare Elemente" automatisch auf 100 GB erhöht, wenn Sie ein Postfach archivieren.
    
      - In Exchange Server 2013 empfehlen wir, die Größe des Ordners regelmäßig zu überprüfen, um sicherzustellen, dass die Grenze nicht erreicht wird. Weitere Informationen finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

## Auswahl zwischen Compliance-Archiv und Beweissicherungsverfahren

Im Folgenden finden Sie einige Informationen, die berücksichtigt werden sollten, wenn es darum geht, welche Aufbewahrungsfunktion Sie verwenden sollten, um alle Ihre Postfächer in Ihrer Organisation archivieren zu können.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Sie möchten...</th>
<th>Beweissicherungsverfahren verwenden</th>
<th>Compliance-Archiv verwenden</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Das EAC verwenden</p></td>
<td><p>Ja</p>
<p>Um Compliance-Archivierung festzulegen, ist das EAC am besten für schnelle einmalige Aktionen bei einigen wenigen Postfächern geeignet. Wir empfehlen, die Shell zu verwenden, um für alle Benutzer in Ihrer Organisation ein Beweissicherungsverfahren zu aktivieren.</p></td>
<td><p>Ja</p>
<p>Sie können im EAC allerdings nicht mehr als 500 Quellpostfächer auswählen.</p></td>
</tr>
<tr class="even">
<td><p>Die Shell verwenden</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Mehr als 10.000 Postfächer im Archiv platzieren</p></td>
<td><p>Ja</p>
<p>Das Beweissicherungsverfahren ist eine Postfacheigenschaft. Sie können alle Postfächer in einer Organisation mithilfe des Cmdlets <strong>Set-Mailbox</strong> archivieren.</p></td>
<td><p>Ja, über die Aktivierung mehrerer In-Situ-Speicher.</p>
<p>Sie können Verteilergruppen zum Angeben von maximal 10.000 Postfächern in einem einzelnen In-Situ-Speicher verwenden. Um zusätzliche Postfächer im Archiv zu platzieren, müssen Sie zusätzliche Compliance-Archive erstellen. Dadurch erhöht sich der Verwaltungsaufwand. Die Verwendung des Beweissicherungsverfahrens zum Archivieren einer Vielzahl an Postfächern ist einfacher.</p></td>
</tr>
<tr class="even">
<td><p>Platzieren Sie viele verschiedene Postfächer für verschiedene Zeiträume im Archiv.</p></td>
<td><p>Ja</p>
<p>Das Beweissicherungsverfahren ist eine Postfacheigenschaft. Sie können jedes Postfach (oder Sätze von Postfächern) unterschiedliche Zeit lang im Archiv platzieren.</p>
<p>Beispiele über die Verwendung der Empfängereigenschaften in einem Filter für das Archivieren eines Beweissicherungsverfahrens für eine Teilmenge an Postfächern finden Sie im Abschnitt Weitere Informationen.</p></td>
<td><p>Ja</p>
<p>Wenn Sie Tausende von Postfächern einzeln archivieren, empfehlen wir, das Beweissicherungsverfahren zu verwenden. Wenn Sie Archive für bestimmte Ergebnisse erstellen, die mehrere Benutzer betreffen, aktivieren Sie für die Gruppe von Benutzern ein einzelnes Compliance-Archiv.</p>
<p>Es wird nicht empfohlen, einzelne In-Situ-Speicher für jedes Postfach zu erstellen, da dies zu vielen In-Situ-Speicherabfragen führt, die schwieriger zu verwalten sind als Beweissicherungsverfahren. Eine große Anzahl von In-Situ-Speicherobjekten kann auch zu Leistungseinbußen in EAC führen, wenn Sie Archivobjekte aktualisieren, erstellen oder ändern.</p></td>
</tr>
<tr class="odd">
<td><p>Neue Postfächer automatisch archivieren</p></td>
<td><p>Nein</p>
<p>Sie müssen für ein neues Postfach ein Beweissicherungsverfahren aktivieren, nachdem Sie es erstellt haben. Sie können den Befehl oder das Skript so planen, dass es so häufig wie erforderlich ausgeführt wird, um den gleichen Effekt zu erzielen.</p></td>
<td><p>Nein</p>
<p>Sie müssen ein neues Postfach zu einem In-Situ-Speicher hinzufügen, selbst wenn Sie eine Verteilergruppe beim Erstellen des In-Situ-Speichers angegeben haben. Sie können den Befehl oder das Skript auch so planen, dass es so häufig wie erforderlich ausgeführt wird, um den gleichen Effekt zu erzielen. Wir empfehlen, dass das Skript überprüft, ob ein bestehender In-Situ-Speicher bereits die Postfachgrenze von 10.000 erreicht hat. Bei Bedarf sollten Sie einen neuen In-Situ-Speicher erstellen.</p></td>
</tr>
<tr class="even">
<td><p>Alle öffentlichen Ordner im Archiv platzieren</p></td>
<td><p>Nein</p>
<p>Das Festlegen eines Beweissicherungsverfahrens für ein Postfach für öffentliche Ordner wird in Exchange Online nicht unterstützt. Sie müssen den In-Situ-Speicher verwenden.</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


## Aktivierung eines Beweissicherungsverfahrens für alle Postfächer

Sie können mithilfe der Shell alle Postfächer schnell und einfach für einen bestimmten oder unbestimmten Zeitraum im Archiv platzieren. Mit diesem Befehl werden alle Postfächer für 2.555 Tage (etwa 7 Jahre) im Archiv platziert.

    Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Set-Mailbox -LitigationHoldEnabled $true -LitigationHoldDuration 2555

Im Beispiel werden das Cmdlet [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) und ein Empfängerfilter zum Abrufen sämtlicher Benutzerpostfächer in der Organisation verwendet. Anschließend wird die Liste der Postfächer an das Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) umgeleitet, um das Beweissicherungsverfahren zu aktivieren und um eine Dauer des Beweissicherungsverfahrens anzugeben. Weitere Informationen finden Sie unter [Aktivieren des Beweissicherungsverfahrens für ein Postfach](place-a-mailbox-on-litigation-hold-exchange-2013-help.md).

## Aktivierung eines Compliance-Archivs für alle Postfächer

Sie können mithilfe des EAC bis 500 Postfächer auswählen und im Archiv platzieren. Weitere Informationen finden Sie unter [Erstellen oder Entfernen eines Compliance-Archivs](create-or-remove-an-in-place-hold-exchange-2013-help.md).


> [!TIP]
> Wenn Sie für mehr als 500 Benutzer ein Compliance-Archiv aktivieren möchten, verwenden Sie die Shell. Siehe <A href="https://technet.microsoft.com/de-de/library/dd298064(v=exchg.150)">New-MailboxSearch</A>.



## Weitere Informationen

  - Wenn Sie alle Postfächer in Ihrer Organisation archivieren, werden nur die Postfächer archiviert, die zum Zeitpunkt, an dem Sie den Befehl ausführen, vorhanden sind. Wenn Sie später neue Postfächer erstellen, führen Sie den Befehl erneut aus, um sie im Archiv zu platzieren. Wenn Sie häufig neue Postfächer erstellen, können Sie den Befehl als geplante Aufgabe so oft wie erforderlich ausführen.

  - Das Platzieren von Postfächern im Archiv bewahrt die Daten, indem verhindert wird, dass Sie vor einem angegebenen Zeitraum gelöscht werden, und durch Speicherung der ursprünglichen Version einer Nachricht, bevor sie geändert wird. Dadurch werden Nachrichten nach Ablauf des angegebenen Zeitraums nicht automatisch gelöscht. Sie können das Beweissicherungsverfahren oder die Archivierung mit einer Aufbewahrungsrichtlinie kombinieren, wodurch Nachrichten nach Ablauf des angegebenen Zeitraums automatisch gelöscht werden, um die Anforderungen an die Nachrichtenaufbewahrung in Ihrer Organisation zu erfüllen. Weitere Informationen finden Sie unter [Aufbewahrungstags und Aufbewahrungsrichtlinien](retention-tags-and-retention-policies-exchange-2013-help.md).

  - Der in diesem Thema zum Aktivieren des Beweissicherungsverfahrens für alle Postfächer verwendete PowerShell-Befehl verwendet einen Empfängerfilter, der alle Benutzerpostfächer zurückgibt. Sie können andere Empfängereigenschaften zum Zurückgeben einer Liste von bestimmten Postfächern verwenden, die Sie an das Cmdlet **Set-Mailbox** umleiten können, um für diese Postfächer ein Beweissicherungsverfahren zu aktivieren.
    
    Hier sind einige Beispiele dafür, wie mit den Cmdlets **Get-Mailbox** und **Get-Recipient** eine Teilmenge an Postfächern basierend auf allgemeinen Benutzer- oder Postfacheigenschaften zurückgegeben wird. In diesen Beispielen wird davon ausgegangen, dass entsprechende Postfacheigenschaften (wie *CustomAttributeN* oder *Department*) aufgefüllt wurden.
    
    ```
        Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'CustomAttribute15 -eq "OneYearLitigationHold"'
    ```

    ```
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'Department -eq "HR"'
    ```
    
    ```
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'PostalCode -eq "98052"'
    ```
    
    ```
        Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'StateOrProvince -eq "WA"'
    ```

    ```
        Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -ne "DiscoveryMailbox"}
    ```

    <p>Sie können andere Benutzerpostfacheigenschaften in einem Filter verwenden, um Postfächer einzubeziehen bzw. auszuschließen. Weitere Informationen finden Sie unter [Filterbare Eigenschaften für den Parameter „-Filter“](https://technet.microsoft.com/de-de/library/bb738155\(v=exchg.150\)).</p>
