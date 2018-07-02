---
title: 'Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer: Exchange 2013 Help'
TOCTitle: Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer
ms:assetid: dbbef170-e726-4735-abf1-2857db9bb52d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150575(v=EXCHG.150)
ms:contentKeyID: 50474908
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer

 

_**Gilt für:** Exchange Online_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Im Bericht zum Postfachzugriff durch Nichtbesitzer werden in der Exchange-Verwaltungskonsole die Postfächer aufgeführt, auf die von irgendeiner Person zugegriffen wurde, die nicht der Besitzer des Postfachs ist. Wenn auf ein Postfach von einem Nicht-Besitzer zugegriffen wird, werden Informationen zu dieser Aktion in einem Postfachüberwachungsprotokoll protokolliert, das als E-Mail in einem ausgeblendeten Ordner des überwachten Postfachs gespeichert wird. Die Einträge aus diesem Protokoll werden als Suchergebnisse angezeigt und enthalten eine Liste mit Postfächern, auf die von einem Nicht-Besitzer zugegriffen wurde, sowie Angaben zur zugreifenden Person und zur Zugriffszeit, zu den Aktionen, die der Nicht-Besitzer ausgeführt hat, sowie zum Status der Aktion. Einträge im Postfachüberwachungsprotokoll werden standardmäßig für 90 Tage aufbewahrt.

Wenn Sie die Postfachüberwachungsprotokollierung für ein Postfach aktivieren, werden bestimmte Aktionen von Nicht-Besitzern protokolliert. Zu diesen Nicht-Besitzern zählen neben Administratoren auch so genannte *delegierte Benutzer*, denen Berechtigungen für ein Postfach zugewiesen wurden. Die Suche kann auch auf Benutzer innerhalb oder außerhalb der Organisation eingegrenzt werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachüberwachungsprotokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Aktivieren der Postfachüberwachungsprotokollierung

Die Postfachüberwachungsprotokollierung muss für jedes Postfach aktiviert werden, für das ein Bericht zum Postfachzugriff durch Nicht-Besitzer ausgeführt werden soll. Ist die Postfachüberwachungsprotokollierung nicht aktiviert, erhalten Sie beim Ausführen eines Berichts keine Ergebnisse.

Führen Sie den folgenden Shell-Befehl aus, um die Postfachüberwachungsprotokollierung für ein einzelnes Postfach zu aktivieren.

    Set-Mailbox <Identity> -AuditEnabled $true

Führen Sie beispielsweise den folgenden Befehl aus, um die Postfachüberwachung für einen Benutzer mit dem Namen Florence Flipo zu aktivieren.

    Set-Mailbox "Florence Flipo" -AuditEnabled $true

Führen Sie folgende Befehle aus, um die Postfachüberwachung für alle Benutzerpostfächer in Ihrer Organisation zu aktivieren.

    $UserMailboxes = Get-mailbox -Filter {(RecipientTypeDetails -eq 'UserMailbox')}

    $UserMailboxes | ForEach {Set-Mailbox $_.Identity -AuditEnabled $true}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie den folgenden Befehl aus, um sich zu vergewissern, dass Sie die Postfachüberwachungsprotokollierung erfolgreich konfiguriert haben.

    Get-Mailbox | FL Name,AuditEnabled

Durch Festlegen der Eigenschaft *AuditEnabled* auf `True` wird sichergestellt, dass die Überwachungsprotokollierung aktiviert ist.

Zurück zum Seitenanfang

## Ausführen eines Berichts zum Postfachzugriff durch Nicht-Besitzer

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Überwachung**.

2.  Klicken Sie auf **Bericht für Nicht-Besitzer-Postfachzugriff ausführen**.
    
    Standardmäßig wird der Bericht zu Nicht-Besitzer-Zugriffen auf Postfächer in der Organisation für den Zeitraum der letzten zwei Wochen ausgeführt. Für die in den Suchergebnissen aufgeführten Postfächer wurde die Postfachüberwachungsprotokollierung aktiviert.

3.  Wählen Sie zum Anzeigen von Nicht-Besitzer-Zugriffen für ein bestimmtes Postfach das Postfach in der Liste der Postfächer aus. Sehen Sie sich die Suchergebnisse im Detailbereich an.


> [!TIP]
> Eingrenzen der Suchergebnisse? Wählen Sie das Startdatum und/oder das Enddatum sowie bestimmte Postfächer aus, die durchsucht werden sollen. Klicken Sie auf <STRONG>Suchen</STRONG>, um den Bericht erneut auszuführen.



## Suchen nach bestimmten Typen von Nicht-Besitzer-Zugriff

Sie können auch den Typ des Nicht-Besitzer-Zugriffs (auch Anmeldetyp genannt) angeben, nach dem gesucht werden soll. Sie haben folgende Möglichkeiten:

  - **Alle Nicht-Besitzer**   Dient zum Suchen nach Zugriffen durch Administratoren und delegierte Benutzer in der Organisation. Umfasst außerdem Zugriffe durch Benutzer außerhalb Ihrer Organisation.

  - **Externe Benutzer** Dient zum Suchen nach Zugriffen durch Benutzer außerhalb Ihrer Organisation.

  - **Administratoren und delegierte Benutzer**   Dient zum Suchen nach Zugriffen durch Administratoren und delegierte Benutzer in der Organisation.

  - **Administratoren**   Dient zum Suchen nach Zugriffen durch Administratoren in der Organisation.

Zurück zum Seitenanfang

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Überprüfen Sie den Bereich mit den Suchergebnissen, um sich zu vergewissern, dass Sie erfolgreich einen Bericht für Nicht-Besitzer-Postfachzugriff ausgeführt haben. Postfächer, für die Sie den Bericht ausgeführt haben, werden in diesem Bereich angezeigt. Wenn für ein bestimmtes Postfach keine Ergebnisse angezeigt werden, liegt möglicherweise kein Zugriff durch einen Nicht-Besitzer vor, oder der Nicht-Besitzer-Zugriff hat nicht im angegebenen Datumsbereich stattgefunden. Wie zuvor beschrieben, sollten Sie sich auf jeden Fall vergewissern, dass die Überwachungsprotokollierung für die Postfächer aktiviert wurde, die Sie nach Zugriff durch Nicht-Besitzer durchsuchen möchten.

Zurück zum Seitenanfang

## Was wird im Postfachüberwachungsprotokoll protokolliert?

Wenn Sie einen Bericht für Nicht-Besitzer-Postfachzugriff ausführen, werden Einträge aus dem Postfachüberwachungsprotokoll in den Suchergebnissen der Exchange-Verwaltungskonsole angezeigt. Jeder Berichtseintrag enthält folgende Informationen:

  - Angaben zur zugreifenden Person und zur Zugriffszeit

  - Die Aktionen, die durch den Nicht-Besitzer ausgeführt wurden

  - Die betroffene Nachricht und der Speicherort des entsprechenden Ordners

  - Den Status der Aktion

In der folgenden Tabelle sind die von Nicht-Besitzern ausgeführten Aktionen aufgelistet, die mit der Postfachüberwachungsprotokollierung protokolliert werden können. Ein **Ja** bedeutet, dass die Aktion für diesen Anmeldetyp protokolliert werden kann. Ein **Nein** bedeutet, dass eine Aktion nicht protokolliert werden kann. Ein Sternchen (**\***) gibt an, dass die Aktion standardmäßig protokolliert wird, wenn die Überwachungsprotokollierung für das Postfach aktiviert ist. Wenn Sie Aktionen nachverfolgen möchten, die standardmäßig nicht protokolliert werden, müssen Sie die Protokollierung dieser Aktionen mit PowerShell aktivieren.


> [!NOTE]
> Ein Administrator, dem Vollzugriff für ein Benutzerpostfach gewährt wurde, gilt als delegierter Benutzer.




<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Aktion</th>
<th>Beschreibung</th>
<th>Administrator</th>
<th>Delegierter Benutzer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Kopieren</strong></p></td>
<td><p>Eine Nachricht wurde in einen anderen Ordner kopiert.</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p><strong>Erstellen</strong></p></td>
<td><p>Ein Element wird im Postfachordner „Kalender“, „Kontakte“, „Aufgaben“ oder „Notizen“ erstellt. Beispielsweise wird eine neue Besprechungsanfrage erstellt. Die Erstellung von Nachrichten oder Ordnern wird nicht überwacht.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
</tr>
<tr class="odd">
<td><p><strong>FolderBind</strong></p></td>
<td><p>Auf einen Postfachordner wurde zugegriffen.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>Dauerhaft löschen</strong></p></td>
<td><p>Eine Nachricht wurde endgültig aus dem Ordner &quot;Wiederherstellbare Elemente&quot; gelöscht.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
</tr>
<tr class="odd">
<td><p><strong>MessageBind</strong></p></td>
<td><p>Eine Nachricht wurde im Vorschaufenster angezeigt oder geöffnet.</p></td>
<td><p>Ja</p></td>
<td><p>Nein</p></td>
</tr>
<tr class="even">
<td><p><strong>Verschieben</strong></p></td>
<td><p>Eine Nachricht wurde in einen anderen Ordner verschoben.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p><strong>In Ordner &quot;Gelöschte Objekte&quot; verschieben</strong></p></td>
<td><p>Eine Nachricht wurde in den Ordner &quot;Gelöschte Objekte&quot; verschoben.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>Senden als</strong></p></td>
<td><p>Eine Nachricht wurde mithilfe der SendAs-Berechtigung gesendet. Das bedeutet, dass ein anderer Benutzer die Nachricht so gesendet hat, dass sie vom Postfachbesitzer zu kommen scheint.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
</tr>
<tr class="odd">
<td><p><strong>Senden im Auftrag von</strong></p></td>
<td><p>Eine Nachricht wurde mithilfe der SendOnBehalf-Berechtigung gesendet. Das bedeutet, dass ein anderer Benutzer die Nachricht im Namen des Postfachbesitzers gesendet hat. Für den Empfänger ist in der Nachricht angegeben, in wessen Namen die Nachricht gesendet wurde und wer die Nachricht tatsächlich gesendet hat.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p><strong>Vorläufig löschen</strong></p></td>
<td><p>Eine Nachricht wurde aus dem Ordner &quot;Gelöschte Objekte&quot; gelöscht.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
</tr>
<tr class="odd">
<td><p><strong>Aktualisieren</strong></p></td>
<td><p>Eine Nachricht wurde geändert.</p></td>
<td><p>Ja*</p></td>
<td><p>Ja*</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> *&nbsp; Wird standardmäßig überwacht, wenn die Überwachung für ein Postfach aktiviert wurde.



Zurück zum Seitenanfang

