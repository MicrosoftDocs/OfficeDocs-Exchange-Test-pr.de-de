---
title: 'Grundlegendes zu Verwaltungsrollenbereichs-Filtern: Exchange 2013 Help'
TOCTitle: Grundlegendes zu Verwaltungsrollenbereichs-Filtern
ms:assetid: 6acc2922-ee9c-41f1-8a0f-10a541e8c273
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298043(v=EXCHG.150)
ms:contentKeyID: 50475907
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Verwaltungsrollenbereichs-Filtern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Mit den Filtern für Verwaltungsrollenbereiche können in hohem Maße anpassbare Verwaltungsbereiche definiert werden. Mithilfe von Bereichsfiltern können Sie einen Bereich erstellen, der die Segmentierung Ihrer Empfänger, Datenbanken und Server widerspiegelt. Auf diese Weise können Administratoren nur die Objekte verwalten, auf die sie auch Zugriff haben sollen. Bereichsfilter können nahezu alle Empfänger-, Datenbank-, oder Serverobjekteigenschaften verwenden.

Wenn Sie Filter für Verwaltungsrollenbereiche einsetzen möchten, müssen Sie mit Verwaltungsrollenbereichen vertraut sein. Weitere Informationen zu Verwaltungsrollenbereichen finden Sie unter [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md).

Gefilterte benutzerdefinierte Bereiche werden in Microsoft Exchange Server 2013 mithilfe des Cmdlets **New-ManagementScope** erstellt. Die beiden Arten gefilterter Bereiche, Empfänger und Konfiguration (bestehend aus Server- und Datenbankbereichen), werden in reguläre und exklusive Bereiche unterteilt. Aus der folgenden Liste geht hervor, welcher Parameter mit dem Cmdlet **New-ManagementScope** zu verwenden ist, um die jeweilige Art des gefilterten Bereichs zu erstellen:

  - **Regulärer gefilterter Empfängerbereich**   Diese Art gefilterter Bereich wird mit dem Parameter *RecipientRestrictionFilter* erstellt.

  - **Exklusiver gefilterter Empfängerbereich**   Diese Art gefilterter Bereich wird mit dem Parameter *RecipientRestrictionFilter* und der Option *Exclusive* erstellt.

  - **Regulärer gefilterter serverbasierter Konfigurationsbereich**   Diese Art gefilterter Bereich wird mit dem Parameter *ServerRestrictionFilter* erstellt.

  - **Exklusiver gefilterter serverbasierter Konfigurationsbereich**   Diese Art gefilterter Bereich wird mit dem Parameter *ServerRestrictionFilter* und der Option *Exclusive* erstellt.

  - **Regulärer gefilterter datenbankbasierter Konfigurationsbereich**   Diese Art gefilterter Bereich wird mit dem Parameter *DatabaseRestrictionFilter* erstellt.

  - **Exklusiver gefilterter datenbankbasierter Konfigurationsbereich**   Diese Art gefilterter Bereich wird mit dem Parameter *DatabaseRestrictionFilter* und der Option *Exclusive* erstellt.

Wenn Sie einen gefilterten benutzerdefinierten Bereich erstellen, sucht der Bereich nach Übereinstimmungen des Filters mit Objekten, die innerhalb des impliziten Lesebereichs der Verwaltungsrolle zugänglich sind. Wird ein Objekt gefunden, wird es in die vom Filter zurückgegebenen Ergebnisse einbezogen, und das Objekt wird der Verwaltungsrolle durch den benutzerdefinierten Bereich zur Verfügung gestellt. Ein Filter kann keine Ergebnisse zurückgeben, die sich außerhalb des impliziten Lesebereichs der Verwaltungsrolle befinden.

Wenn Sie mit dem Parameter *RecipientRestrictionFilter* einen Empfängerfilter angeben, können Sie mithilfe des Parameters *RecipientRoot* eine Organisationseinheit angeben, auf die sich der Filter beschränken soll. Wenn Sie mit dem Parameter *RecipientRoot* eine Organisationseinheit angeben, sucht der Empfängerfilter nur nach Übereinstimmungen mit Empfängern innerhalb dieser Organisationseinheit und nicht im gesamten impliziten Lesebereich.

Informationen zum Erstellen eines Verwaltungsbereichs mithilfe der in diesem Thema enthaltenen filterbaren Eigenschaften finden Sie unter [Erstellen eines regulären oder exklusiven Bereichs](create-a-regular-or-exclusive-scope-exchange-2013-help.md).

## Filtersyntax

Sowohl für Empfänger- als auch für Konfigurationsfilter wird zum Erstellen einer Filterabfrage die gleiche Syntax verwendet. Alle Filterabfragen müssen mindestens die folgenden Bestandteile enthalten:

  - **Öffnende Klammer**   Die öffnende geschweifte Klammer ({) gibt den Start der Filterabfrage an.

  - **Zu untersuchende Eigenschaft**   Die Eigenschaft ist der Wert eines Objekts, der geprüft werden soll. Dabei kann es sich beispielsweise um die Stadt oder Abteilung eines Empfängerobjekts handeln, den Active Directory-Standortnamen oder Servernamen eines Serverkonfigurationsobjekts oder den Datenbanknamen eines Datenbankkonfigurationsobjekts.

  - **Vergleichsoperator**   Der Vergleichsoperator gibt vor, wie die Abfrage den von Ihnen angegebenen Wert mit dem in der Eigenschaft gespeicherten Wert abgleichen soll. Vergleichsoperatoren sind beispielsweise **Eq**, was "gleich" bedeutet, **Ne**, was "nicht gleich" bedeutet, oder **Like**, was "ähnlich" bedeutet. Eine Liste aller Operatoren, die Sie in der Exchange-Verwaltungsshell verwenden können, finden Sie unter [Vergleichsoperatoren](https://technet.microsoft.com/de-de/library/bb125229\(v=exchg.150\)).

  - **Vergleichswert**   Der Wert, den Sie in der Filterabfrage angeben, wird mit dem Wert verglichen, der in der angegebenen Eigenschaft gespeichert ist. Der angegebene Wert muss in Anführungszeichen (") eingeschlossen werden. Wenn Sie eine Teilzeichenfolge angeben möchten, können Sie die Zeichenfolge in Platzhalterzeichen (\*) einschließen und einen Vergleichsoperator verwenden, der Platzhalterzeichen unterstützt (z. B. **Like**). Jede Zeichenfolge, die die Teilzeichenfolge enthält, stimmt mit der Filterabfrage überein.

  - **Schließende Klammer**   Die schließende geschweifte Klammer (}) gibt das Ende der Filterabfrage an.

Die folgenden Bestandteile sind optional und erlauben das Erstellen komplexerer Filterabfragen:

  - **Klammern**   Wie in der Mathematik können Sie auch in einer Filterabfrage mithilfe von Klammern die Reihenfolge vorgeben, in der eine Operation erfolgen soll. Die Werte in den innersten Klammern werden zuerst gewertet, d. h. die Filterabfrage arbeitet die Klammern von innen nach außen ab.

  - **Logische Operatoren**   Mit logischen Operatoren werden ein oder mehrere Vergleichsoperationen miteinander verknüpft, sodass die Filterabfrage die gesamte Anweisung auswerten muss. Zu den logischen Operatoren zählen beispielsweise **And**, **Or** und **Not**.

Bei einer Verknüpfung sieht eine einfache Abfrage z. B. wie `{ City -Eq "Vancouver" }` aus. Mit diesem Filter wird nach einer Übereinstimmung mit Empfängern gesucht, deren Eigenschaftswert **City** der Zeichenfolge "Vancouver" entspricht.

Eine andere, komplexere Abfrage lautet `{ ((City -Eq "Vancouver") -And (Department -Eq "Sales")) -Or (Title -Like "*Manager*") }`. Die Filterabfrage wird in der folgenden Reihenfolge ausgewertet:

1.  Die Eigenschaften **City** und **Department** werden ausgewertet. Jede Eigenschaft wird in Abhängigkeit von dem jeweils gespeicherten Wert auf `True` oder `False` gesetzt.

2.  Anschließend werden die Ergebnisse der Anweisungen **City** und **Department** ausgewertet. Wenn beide Eigenschaften `True` lauten, wird die gesamte **And**-Anweisung mit `True` gewertet. Wenn eine oder beide Eigenschaften den Wert `False` haben, wird die gesamte **And**-Anweisung mit `False` gewertet. Folgendes gilt:
    
      - Lautet die **And**-Anweisung `True`, wird die gesamte Filterabfrage als `True` gewertet, da der **Or**-Operator vorgibt, dass mindestens ein Teil der Abfrage den Wert `True` aufweisen muss. Das Objekt wird für die Rollenzuweisung verfügbar gemacht.
    
      - Wurde für die **And**-Anweisung der Wert `False` ermittelt, wird die Filterabfrage fortgesetzt, um die Eigenschaft **Title** auszuwerten.

3.  Dann wird die Eigenschaft **Title** ausgewertet. Sie wird in Abhängigkeit von dem in der Eigenschaft **Title** gespeicherten Wert auf `True` oder `False` gesetzt. Folgendes gilt:
    
      - Wurde die Eigenschaft **Title** mit `True` gewertet, erhält die gesamte Filterabfrage den Wert `True`, da der **Or**-Operator vorgibt, dass mindestens ein Teil der Abfrage den Wert `True` aufweisen muss. Das Objekt wird für die Rollenzuweisung verfügbar gemacht.
    
      - Wurde die Eigenschaft **Title** als `False` gewertet, erhält die gesamte Filterabfrage den Wert `False`, und das Objekt wird nicht für die Rollenzuweisung verfügbar gemacht.

Die folgende Tabelle enthält ein Beispiel mit Werten, aus dem hervorgeht, wann die komplexe Abfrage als `True` bzw. `False` gewertet wird.

### Komplexe Abfrage

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>City</th>
<th>Department</th>
<th>Title</th>
<th>Ergebnis</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Vancouver (True)</p></td>
<td><p>Sales (True)</p></td>
<td><p>CEO (False)</p></td>
<td><p>&quot;True&quot;, da sowohl <strong>City</strong> als auch <strong>Department</strong> den Wert &quot;True&quot; aufweisen. <strong>Title</strong> wird nicht ausgewertet, da die Bedingungen der Filterabfrage bereits erfüllt sind.</p></td>
</tr>
<tr class="even">
<td><p>Seattle (False)</p></td>
<td><p>Sales (True)</p></td>
<td><p>IT Manager (True)</p></td>
<td><p>&quot;True&quot;, da <strong>Title</strong> den Wert &quot;True&quot; aufweist. Die Ergebnisse des Vergleichs von <strong>City</strong> und <strong>Department</strong> werden verworfen, da <strong>Title</strong> den Wert &quot;True&quot; aufweist und somit die Bedingungen der Filterabfrage erfüllt sind.</p>

> [!NOTE]
> "IT Manager" stimmt mit der Filterabfrage überein, da der Vergleichsoperator <STRONG>Like</STRONG> verwendet wurde, der bei der Verwendung von Platzhalterzeichen (*) in der Abfrage nach einer Übereinstimmung mit Teilzeichenfolgen sucht.


</td>
</tr>
<tr class="odd">
<td><p>Vancouver (True)</p></td>
<td><p>Marketing (False)</p></td>
<td><p>Writer (False)</p></td>
<td><p>&quot;False&quot;, da sowohl <strong>City</strong> als auch <strong>Department</strong> nicht als &quot;True&quot; gewertet wurden und auch <strong>Title</strong> nicht den Wert &quot;True&quot; aufweist.</p></td>
</tr>
</tbody>
</table>


## Filterbare Empfängereigenschaften

Beim Erstellen eines Empfängerfilters kann nahezu jede Eigenschaft eines Empfängerobjekts verwendet werden. Eine Liste filterbarer Eigenschaften finden Sie unter [Filterbare Eigenschaften für den Parameter „-RecipientFilter“](https://technet.microsoft.com/de-de/library/bb738157\(v=exchg.150\)). Die meisten Eigenschaften funktionieren auch mit dem Parameter *RecipientRestrictionFilter* des Cmdlets **New-ManagementScope**, auch wenn in diesem Thema die Eigenschaften behandelt werden, die mit dem Parameter *RecipientFilter* anderer Cmdlets verwendet werden.

## Filterbare Servereigenschaften

Beim Erstellen eines Verwaltungsbereichs mit dem Parameter *ServerRestrictionFilter* können Sie die folgenden Servereigenschaften verwenden:

  - **CurrentServerRole**

  - **CustomerFeedbackEnabled**

  - **DataPath**

  - **DistinguishedName**

  - **ExchangeLegacyDN**

  - **ExchangeLegacyServerRole**

  - **ExchangeVersion**

  - **Fqdn**

  - **Guid**

  - **InternetWebProxy**

  - **Name**

  - **NetworkAddress**

  - **ObjectCategory**

  - **ObjectClass**

  - **ProductID**

  - **ServerRole**

  - **ServerSite**

  - **WhenChanged**

  - **WhenChangedUTC**

  - **WhenCreated**

  - **WhenCreatedUTC**

## Filterbare Datenbankeigenschaften

Sie können beim Erstellen eines Verwaltungsbereichs mithilfe des Parameters *DatabaseRestrictionFilter* die folgenden Datenbankeigenschaften verwenden:

  - **AdminDisplayName**

  - **AllowFileRestore**

  - **BackgroundDatabaseMaintenance**

  - **CircularLoggingEnabled**

  - **DatabaseCreated**

  - **DeletedItemRetention**

  - **Description**

  - **DistinguishedName**

  - **EdbFilePath**

  - **EventHistoryRetentionPeriod**

  - **ExchangeLegacyDN**

  - **ExchangeVersion**

  - **Guid**

  - **IssueWarningQuota**

  - **LogFilePrefix**

  - **LogFileSize**

  - **LogFolderPath**

  - **MasterServerOrAvailabilityGroup**

  - **MountAtStartup**

  - **Name**

  - **ObjectCategory**

  - **ObjectClass**

  - **RetainDeletedItemsUntilBackup**

  - **Server**

  - **WhenChanged**

  - **WhenChangedUTC**

  - **WhenCreated**

  - **WhenCreatedUTC**

