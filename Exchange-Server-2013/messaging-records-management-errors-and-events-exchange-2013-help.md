---
title: 'Verwalten von Fehlern und Ereignissen für Messagingdatensätzen: Exchange 2013 Help'
TOCTitle: Verwalten von Fehlern und Ereignissen für Messagingdatensätzen
ms:assetid: 8bc3f5ae-403b-45af-86c1-b2fccab34e63
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb310783(v=EXCHG.150)
ms:contentKeyID: 51409314
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von Fehlern und Ereignissen für Messagingdatensätzen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Die Messaging-Datensatzverwaltung (Messaging Records Management, MRM) generiert Ereignisse, die Sie in der Ereignisanzeige anzeigen können. Sie ermöglichen Ihnen die Problembehandlung und Leistungsüberprüfung für den Assistenten für verwaltete Ordner. Die Ereignisanzeige verfolgt die folgenden Arten von Ereignissen in der Reihenfolge ihrer Wichtigkeit:

1.  Fehlerereignisse

2.  Warnereignisse

3.  Informationsereignisse

## MRM-Fehler und -Ereignisse

In der folgenden Tabelle sind die Ereignisse aufgelistet, mit deren Hilfe Sie Probleme mit der MRM behandeln können. Folgende Protokollierungstypen gibt es:

  - Ereignisse, die als **LogAlways** gekennzeichnet sind, werden immer einzeln protokolliert.

  - Ereignisse, die als **LogPeriodic** gekennzeichnet sind, werden nicht bei jedem Auftreten, sondern nur einmal pro Fünf-Minuten-Intervall protokolliert. So werden übermäßige Protokolleinträge verhindert.

### MRM-Ereignisse in der Kategorie "Assistent für verwaltete Ordner"

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
<th><strong>Ereignis-ID</strong></th>
<th><strong>Kategorie</strong></th>
<th><strong>Ereignistyp</strong></th>
<th><strong>Protokollierung</strong></th>
<th><strong>Wert oder Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>10003</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogPeriodic</p></td>
<td><p>Das Serverkonfigurationsobjekt konnte nicht aus Active Directory abgerufen werden. &lt;<em>Ausnahmedetails</em>&gt;. Überprüfen Sie, ob Probleme mit der Netzwerkverbindung des Domänencontrollers vorliegen oder die DNS-Konfiguration falsch ist.</p></td>
</tr>
<tr class="even">
<td><p>10004</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Die Aufbewahrungsrichtlinie für den Ordner &lt;<em>Ordner</em>&gt; im Postfach &lt;<em>Postfach</em>&gt; wird nicht angewendet. Der Assistent für verwaltete Ordner kann die Einstellung für verwaltete Inhalte &lt;<em>Inhaltseinstellung</em>&gt; für den verwalteten Ordner &lt;<em>verwalteter Ordner</em>&gt; nicht verarbeiten. Die RetentionAction lautet MoveToFolder, es wurde aber kein Zielordner angegeben. Geben Sie einen Zielordner an.</p></td>
</tr>
<tr class="odd">
<td><p>10005</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Die Aufbewahrungsrichtlinie wird auf den Ordner &lt;<em>Ordner</em>&gt; im Postfach &lt;<em>Postfach</em>&gt; nicht angewendet. Die Einstellung für verwaltete Inhalte &lt;<em>Inhaltseinstellung</em>&gt; für den verwalteten Ordner &lt;<em>verwalteter Ordner</em>&gt; kann nicht verarbeitet werden. Die RetentionAction lautet MoveToFolder, Zielordner &lt;<em>Order</em>&gt; und Quellordner &lt;<em>Ordner</em>&gt; sind jedoch gleich. Geben Sie einen anderen Zielordner an.</p></td>
</tr>
<tr class="even">
<td><p>10009</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Der Assistent für verwaltete Ordner hat keine Datenbanken auf dem lokalen Server verarbeitet, weil er die Überwachungsprotokollparameter von Active Directory nicht lesen konnte. Der Vorgang wird zu einem späteren Zeitpunkt im Planfenster wiederholt. Aktuelle Datenbank: &lt;<em>Datenbank</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>10010</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Der Assistent für verwaltete Ordner hat keine Datenbanken auf dem lokalen Server verarbeitet, weil das Überwachungsprotokoll zwar aktiviert ist, der Pfad zum Überwachungsprotokoll in Active Directory jedoch fehlt. Der Vorgang wird zu einem späteren Zeitpunkt im Planfenster wiederholt. Aktuelle Datenbank: &lt;<em>Datenbank</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>10011</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Der Assistent für verwaltete Ordner konnte das Überwachungsprotokoll nicht konfigurieren. Die Verarbeitung der aktuellen Datenbank: '%1' wird beendet. '%1'. Der Vorgang wird zu einem späteren Zeitpunkt im Planfenster wiederholt. Ausnahmedetails: &lt;<em>Details</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>10012</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Der Assistent für verwaltete Ordner konnte nicht in das Überwachungsprotokoll schreiben. Die Verarbeitung der aktuellen Datenbank: '%1' wird beendet. &lt;<em>Datenbank</em>&gt;. Der Vorgang wird zu einem späteren Zeitpunkt im Planfenster wiederholt. Ausnahmedetails: &lt;<em>Details</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>10017</p></td>
<td><p>Assistent für verwaltete Ordner</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Der Assistent für verwaltete Ordner hat beim Verarbeiten des folgenden Postfachs eine Ausnahme ausgelöst: &lt;<em>Postfach</em> &gt; Ordner: Name: &lt;<em>Name des Ordners</em>&gt; ID: &lt;<em>Ordner-ID</em>&gt; Element: IDs: &lt;<em>IDs</em>&gt;. Ausnahme: &lt;<em>Ausnahme</em>&gt;.</p></td>
</tr>
</tbody>
</table>


### MRM-Ereignisse in der Kategorie "Assistenten"

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
<th><strong>Ereignis-ID</strong></th>
<th><strong>Kategorie</strong></th>
<th><strong>Ereignistyp</strong></th>
<th><strong>Protokollierung</strong></th>
<th><strong>Wert oder Beschreibung</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>9004</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; konnte das Postfach &lt;<em>Postfach</em>&gt; nicht verarbeiten. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>9014</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. Änderungen am Zeitplan konnten nicht verarbeitet werden. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>9017</p></td>
<td><p>Assistenten</p></td>
<td><p>Information</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; für Datenbank &lt;<em>Datenbank</em>&gt; tritt in ein geplantes Zeitfenster ein. Es sind &lt;<em>Anzahl</em>&gt; Postfächer zu verarbeiten.</p></td>
</tr>
<tr class="even">
<td><p>9018</p></td>
<td><p>Assistenten</p></td>
<td><p>Information</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; für die Datenbank &lt;<em>Datenbank</em>&gt; überschreitet ein geplantes Zeitfenster. &lt;<em>Anzahl</em>&gt; von &lt;<em>Anzahl</em>&gt; Postfächer wurden erfolgreich verarbeitet. &lt;<em>Anzahl</em>&gt; Postfächer wurden aufgrund von Fehlern übersprungen. &lt;<em>Anzahl</em>&gt; Postfächer wurden separat verarbeitet. &lt;<em>Anzahl</em>&gt; Postfächer wurden aufgrund nicht ausreichender Zeit nicht verarbeitet.</p>

> [!NOTE]
> Der Assistent für verwaltete Ordner nimmt die Verarbeitung bei der nächsten Ausführung an der Stelle der Unterbrechung wieder auf.


</td>
</tr>
<tr class="odd">
<td><p>9019</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogPeriodic</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. Fortschritt für &lt;<em>Dienst</em>&gt; für Datenbank &lt;<em>Datenbank</em>&gt; konnte nicht gespeichert werden. (Der Assistent konnte die Stelle der Unterbrechung nicht speichern, um dort beim erneuten Start fortzufahren.) Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>9020</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Name des Assistenten</em>&gt; konnte für Datenbank &lt;<em>Datenbank</em>&gt; nicht gestartet werden. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>9021</p></td>
<td><p>Assistenten</p></td>
<td><p>Information</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; für Datenbank &lt;<em>Datenbank</em>&gt; verarbeitet eine Bei-Bedarf-Anforderung. Es sind &lt;<em>Anzahl</em>&gt; Postfächer zu verarbeiten.</p></td>
</tr>
<tr class="even">
<td><p>9022</p></td>
<td><p>Assistenten</p></td>
<td><p>Information</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; für Datenbank &lt;<em>Datenbank</em>&gt; hat eine Bei-Bedarf-Anforderung fertig gestellt. &lt;<em>Anzahl</em>&gt; von &lt;<em>Anzahl</em>&gt; Postfächern wurden erfolgreich verarbeitet. &lt;<em>Anzahl</em>&gt; Postfächer wurden aufgrund von Fehlern ausgelassen.</p></td>
</tr>
<tr class="odd">
<td><p>9023</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; konnte die Zeitfensterverarbeitung für Datenbank &lt;<em>Datenbank</em>&gt; nicht starten. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>9025</p></td>
<td><p>Assistenten</p></td>
<td><p>Information</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; hat &lt;<em>Anzahl</em>&gt; Postfächer für Datenbank &lt;<em>Datenbank</em>&gt; ausgelassen. Postfächer: &lt;<em>Postfächer</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>9026</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; konnte die Bei-Bedarf-Verarbeitung für Datenbank &lt;<em>Datenbank</em>&gt; nicht starten. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>9027</p></td>
<td><p>Assistenten</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; hat bei der Verarbeitung von Postfach &lt;<em>Postfach</em>&gt; in Datenbank &lt;<em>Datenbank</em>&gt; &lt;<em>Anzahl</em>&gt; Mal zum Beenden des Prozesses geführt. Dieses Postfach wird während des angeforderten Zeitfensters bzw. der Bei-Bedarf-Anforderung nicht mehr verarbeitet. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="odd">
<td><p>9028</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; hat bei der Verarbeitung von Postfach &lt;<em>Postfach</em>&gt; in Datenbank &lt;<em>Datenbank</em>&gt; &lt;<em>Anzahl</em>&gt; Mal zum Beenden des Prozesses geführt. Die folgende Ausnahme hat den Fehler bewirkt: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>9033</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Dienst</em>&gt; für Datenbank &lt;<em>Datenbank</em>&gt; hat eine Bei-Bedarf-Anforderung empfangen. Es gibt jedoch keine zu verarbeitenden Postfächer.</p></td>
</tr>
<tr class="odd">
<td><p>9034</p></td>
<td><p>Assistenten</p></td>
<td><p>Information</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt; hat zeitbasierte Operationen für den Assistenten für verwaltete Ordner für Datenbank &lt;<em>Datenbank</em>&gt; angehalten.</p></td>
</tr>
<tr class="even">
<td><p>9035</p></td>
<td><p>Assistenten</p></td>
<td><p>Warnung</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. &lt;<em>Name des Assistenten</em>&gt; konnte &lt;<em>Anzahl</em>&gt; Postfächer aufgrund nicht ausreichender Zeit nicht verarbeiten.</p></td>
</tr>
<tr class="odd">
<td><p>9037</p></td>
<td><p>Assistenten</p></td>
<td><p>Fehler</p></td>
<td><p>LogAlways</p></td>
<td><p>Dienst &lt;<em>Dienst</em>&gt;. Bei der Verarbeitung eines Remoteprozeduraufrufs wurde eine Ausnahme erkannt. Methode: &lt;<em>Methode</em>&gt;, Ausnahme: &lt;<em>Ausnahme</em>&gt;</p></td>
</tr>
</tbody>
</table>

