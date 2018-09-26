---
title: 'Pipelineablaufverfolgung: Exchange 2013 Help'
TOCTitle: Pipelineablaufverfolgung
ms:assetid: e7780499-9a6f-48b1-aea8-df88ecd8b18a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125018(v=EXCHG.150)
ms:contentKeyID: 52062922
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Pipelineablaufverfolgung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Für die Pipelineablaufverfolgung werden Kopien von E-Mail-Nachrichten eines bestimmten Absenders erfasst, während diese den Transportdienst auf Postfachservern, den Postfachtransport-Zustellungsdienst auf Postfachservern und Edge-Transport-Server durchlaufen. Die Pipelineablaufverfolgung erfasst ausführliche Informationen zu den Änderungen, die von jedem Transport-Agent an Nachrichten in der Transportpipeline vorgenommen werden, in Nachrichten-Snapshotdateien. Durch Untersuchen des Inhalts der Nachrichten-Snapshotdateien können Sie herausfinden, ob die Transport-Agents die Änderungen an den Nachrichten in der Transportpipeline erwartungsgemäß vorgenommen haben. Bei der Behandlung eines Problems müssen Sie herausfinden, welcher Transport-Agent fehlerhaft ist. Erst dann können Sie sich auf die Behandlung der Problematik dieses Agents konzentrieren, um das Problem zu beheben. Anschließend können Sie erneut Nachrichten-Snapshotdateien anzeigen, um sicherzustellen, dass Ihre Lösung erfolgreich war.


> [!WARNING]
> <UL>
> <LI>
> <P>Die Pipelineablaufverfolgung kopiert den vollständigen Inhalt von E-Mail-Nachrichten, die von der E-Mail-Adresse des Absenders gesendet werden. Um die unerwünschte Preisgabe vertraulicher Informationen zu vermeiden, müssen Sie für den Ordner der Pipelineablaufverfolgung geeignete Sicherheitsberechtigungen festlegen.</P>
> <LI>
> <P>Aktivieren Sie die Pipelineablaufverfolgung nicht für längere Zeiträume. Bei der Pipelineablaufverfolgung werden Dateien erstellt, die schnell sehr groß werden können. Überwachen Sie bei aktivierter Pipelineablaufverfolgung immer den auf dem Datenträger verfügbaren Speicherplatz.</P></LI></UL>



## Konfigurieren der Pipelineablaufverfolgung

Bevor Sie die Pipelineablaufverfolgung aktivieren, müssen Sie die zu überwachende E-Mail-Adresse des Absenders angeben. Die Pipelineablaufverfolgung dient zum Protokollieren von Nachrichten, die von einer bestimmten E-Mail-Adresse gesendet werden. Die E-Mail-Adresse des Absenders kann für Ihre Exchange-Organisation intern oder extern sein. Alternativ können Sie die Pipelineablaufverfolgung für Systemnachrichten aktivieren, die vom Transportdienst auf dem angegebenen Postfach- oder Edge-Transport-Server generiert werden, z. B. automatische Antworten, Benachrichtigungen über den Zustellungsstatus, Journalberichte und andere vom System generierte Nachrichten. Sie können auch den Speicherort des Ordners für die Pipelineablaufverfolgung ändern.

Die Parameter, mit deren Hilfe Sie die Pipelineablaufverfolgung konfigurieren, finden Sie in der folgenden Tabelle


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Parameter</th>
<th>Standardwert</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-TransportService</strong></p>
<p><strong>Set-MailboxTransportService</strong></p></td>
<td><p><em>PipelineTracingSenderAddress</em></p></td>
<td><p>Leer (<code>$null</code>)</p></td>
<td><p>Geben Sie die E-Mail-Adresse des Absenders an, die Sie überwachen möchten.</p>
<p>Geben Sie den Wert &quot;&lt;&gt;&quot; zum Überwachen vom System generierter Nachrichten an, die vom angegebenen Transportdienst auf dem Server gesendet werden.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-TransportService</strong></p>
<p><strong>Set-MailboxTransportService</strong></p></td>
<td><p><em>PipelineTracingPath</em></p></td>
<td><p><strong>Transportdienst</strong> <code>%ExchangeInstallPath%TransportRoles\Logs\Hub\PipelineTracing</code></p>
<p><strong>Postfachtransportdienst</strong> <code>%ExchangeInstallPath%TransportRoles\Logs\Mailbox\PipelineTracing</code></p></td>
<td><p>Der Pfad muss sich auf dem lokalen Server befinden. UNC-Pfade werden nicht unterstützt.</p>
<p>Der angegebene Pfad enthält den Ordner <code>MessageSnapshots</code>, in dem die Pipelineablaufverfolgungsdateien gespeichert werden.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-TransportService</strong></p>
<p><strong>Set-MailboxTransportService</strong></p></td>
<td><p><em>PipelineTracingEnabled</em></p></td>
<td><p><code>$false</code></p></td>
<td><p>Sie können die Pipelineablaufverfolgung nur für den angegebenen Transportdienst auf dem Server aktivieren, nachdem Sie die zu überwachende Absenderadresse konfiguriert haben.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Aktivieren der Pipelineablaufverfolgung sowie zum Konfigurieren der Absenderadresse für die Pipelineablaufverfolgung finden Sie unter [Konfigurieren der Pipelineablaufverfolgung](configure-pipeline-tracing-exchange-2013-help.md).

## Nachrichten-Snapshotdateien

Nachrichtensnapshots sind Dateien zum Erfassen von Änderungen an einer Nachricht durch Transport-Agents im Transportdienst oder Postfachtransport-Übermittlungsdienst. Diese Dateien werden im Ordner `MessageSnapshots` im dazugehörigen Pipelineablaufverfolgungs-Pfad für den Transportdienst gespeichert.

Im Ordner `MessageSnapshots` legt Exchange einen Ordner für jede vom überwachten Absender überwachte Nachricht an, die den angegebenen Transportdienst durchläuft. Jeder Ordner ist gemäß einer GUID benannt, die der Nachricht zugewiesen ist. Wenn Sie die Pipelineablaufverfolgung für den Transportdienst oder Postfachtransportdienst auf demselben Postfachserver aktivieren, wird derselben Nachricht von jedem Transportdienst eine andere GUID zugewiesen. Deshalb unterscheidet sich der Ordnername einer Nachricht im Ordner `MessageSnapshots` für den Transportdienst vom Ordnernamen für dieselbe Nachricht im Ordner `MessageSnapshots` für den Postfachtransportdienst. Wenn Sie die Pipelineablaufverfolgung auf mehreren Exchange-Servern aktivieren, wird der Nachricht beim Durchlaufen des angegebenen Transportdiensts auf den einzelnen Exchange-Servern eine andere GUID zugewiesen.

In jedem Nachrichtenordner erstellt Exchange mehrere Nachrichten-Snapshotdateien mit der Erweiterung "EML". Diese Nachrichten-Snapshotdateien enthalten den Inhalt der Nachricht, wenn sie mit dem jeweiligen SMTP-Ereignis und Transport-Agent in Kontakt kommt.

Wenn ein Transport-Agent für ein SMTP-Ereignis registriert ist, erstellt Exchange einen Nachrichtensnapshot der Nachricht, bevor die Nachricht mit einem Transport-Agent in Kontakt kommt. Auf diese Weise erhalten Sie eine Kopie der Nachricht, bevor diese mit Transport-Agents in Kontakt kommt, die für dieses Ereignis registriert sind. Danach wird für jeden Transport-Agent, mit dem die Nachricht in Kontakt kommt, ein neuer Nachrichtensnapshot erstellt, unabhängig davon, ob ein Transport-Agent den Inhalt der Nachricht verändert. Wenn jedoch keine Agents für ein Ereignis registriert sind, erstellt Exchange keine Nachrichtensnapshots für das Ereignis.

Wenn beispielsweise drei Agents für das Ereignis **OnEndofData** registriert sind, aber nur zwei der Transport-Agents eine Nachricht ändern, werden vier Nachrichtensnapshots erstellt. Der erste Nachrichtensnapshot erfasst die Nachricht, wenn sie mit dem **OnEndofData**-Ereignis in Kontakt kommt, bevor eine Änderung von den Transport-Agents vorgenommen wurde, die für dieses Ereignis registriert sind. Danach wird für jeden Transport-Agent ein Nachrichtensnapshot erstellt, unabhängig davon, ob ein Transport-Agent die Nachricht verändert.

Die erstellten Nachrichten-Snapshotdateien werden in der folgenden Liste beschrieben:

  - **Original.eml**   Diese Datei enthält den ursprünglichen, unveränderten Inhalt der E-Mail-Nachricht, bevor diese mit einem SMTP-Ereignis oder Transport-Agent in Kontakt kommt.

  - **Routingnnnn.eml**   Diese Dateien enthalten den Inhalt der E-Mail-Nachricht, wenn sie mit den SMTP-Ereignissen und Transport-Agents, die für diese Ereignisse registriert sind, im Kategorisierungsteil des Transportdiensts in Kontakt kommt. Der Platzhalter *nnnn* ist ein mit `0001` beginnender Ganzzahlwert. Der Wert wird bei allen SMTP-Ereignissen und Transport-Agents, die für diese Ereignisse registriert sind, in der Reihenfolge erhöht, in der die Ereignisse und Agents auf die Nachricht einwirken. Der Postfachtransport-Zustellungsdienst generiert diese **Routing**-Snapshotdateien nicht.

  - **Routingnnnn.eml**   Diese Dateien enthalten den Inhalt der E-Mail-Nachricht, wenn sie mit den SMTP-Ereignissen **OnEndofData** und **OnEndOfHeaders** und Transport-Agents, die für diese Ereignisse registriert sind, im SMTP-Empfangsteil des Transportdiensts oder des Postfachtransport-Zustellungsdiensts in Kontakt kommt. Der Platzhalter *nnnn* ist ein mit `0001` beginnender Ganzzahlwert. Der Wert wird bei allen SMTP-Ereignissen und Transport-Agents, die für diese Ereignisse registriert sind, in der Reihenfolge erhöht, in der die Ereignisse und Agents auf die Nachricht einwirken.

Die Nachrichten-Snapshotdateien können mithilfe eines Text-Editors wie Editor geöffnet werden.

Jede Nachrichten-Snapshotdatei beginnt mit Kopfzeilen, die dem Nachrichteninhalt hinzugefügt werden, und listet das SMTP-Ereignis zusammen mit dem Transport-Agent auf, auf die sich die Nachrichtensnapshotdatei bezieht. Diese Kopfzeilen beginnen mit `X-CreatedBy: MessageSnapshot-Begin injected headers` und enden mit `X-EndOfInjectedXHeaders: MessageSnapshot-End injected headers`. Sie werden in jeder Nachrichten-Snapshotdatei durch die des nachfolgenden Transport-Agents und SMTP-Ereignisses ersetzt. Es folgt ein Beispiel der Kopfzeilen, die einer E-Mail-Nachrichtendatei hinzugefügt werden:

```powershell
    X-CreatedBy: MessageSnapshot-Begin injected headers
    X-MessageSnapshot-UTC-Time: 2013-01-23T23:20:18.138Z
    X-MessageSnapshot-Record-Id: 21474836486
    X-MessageSnapshot-Source: OnSubmittedMessageX-Sender: michelle@nwtraders.com
    X-Receiver: chris@contoso.com
    X-EndOfInjectedXHeaders: MessageSnapshot-End injected headers
```

Hinter den Nachrichtensnapshot-Kopfzeilen befindet sich der Inhalt der Nachricht, einschließlich aller ursprünglichen Nachrichtenkopfzeilen. Wenn ein Transport-Agent den Inhalt der Nachricht ändert, werden die Änderungen in die Nachricht integriert angezeigt. Während die Nachricht von jedem Transport-Agent verarbeitet wird, werden die Änderungen des jeweiligen Agents an dem Nachrichteninhalt vorgenommen. Wenn ein Transport-Agent keine Änderungen am Nachrichteninhalt vornimmt, ist der Nachrichtensnapshot, der von diesem Agent erstellt wird, mit dem Nachrichtensnapshot identisch, der von dem vorangehenden Transport-Agent erstellt wurde.

