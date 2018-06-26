---
title: 'Limits für den verwalteten Speicher: Exchange 2013 Help'
TOCTitle: Limits für den verwalteten Speicher
ms:assetid: bea9ec15-bfb5-4716-b14e-010e389c9f9e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt741981(v=EXCHG.150)
ms:contentKeyID: 73226018
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Limits für den verwalteten Speicher

 

_**Letztes Änderungsdatum des Themas:**2016-09-15_

**Zusammenfassung:** In diesem Artikel erfahren Sie Details zu den Verbindungslimits für den verwalteten Speicher sowie zu deren Konfiguration.

In MicrosoftExchange Server 2013 wurden Verbindungs- und Nutzungslimits für den verwalteten Speicher von Exchange festgelegt, um zu verhindern, dass eine einzelne Anwendung oder ein einzelner Benutzer alle verfügbaren Verbindungen zum verwalteten Speicher belegt. Wenn ein einzelner Benutzer oder eine einzelne Anwendung alle Verbindungen verwenden darf, können andere Benutzer oder Anwendungen nicht auf den verwalteten Speicher zugreifen. Das kann zu Downtime führen.


> [!NOTE]
> Für Verbindungen von Konten mit Administratorrechten wurden die maximalen Sitzungslimits auf 64.000 erhöht.



## Begrifflichkeiten

Sie sollten die folgenden Begriffe kennen, um die Arten von Verbindungen zu verstehen, die in diesem Artikel vorkommen.

  - Sitzungen  
    Sitzungen repräsentieren die Verbindungen, über die Dienste und Clientanwendungen wie Microsoft Outlook sich mit dem verwalteten Speicher verbinden. Dienste und Clients können zu einem bestimmten Zeitpunkt über mehrere Sitzungen verfügen. Die Begriffe *Verbindungen* und *Sitzungen* können synonym verwendet werden.

<!-- end list -->

  - Threads  
    Threads sind gleichzeitig ausgeführte Anforderungen an den verwalteten Speicher. Wenn beispielsweise ein Benutzer einen Ordner in Outlook öffnet, führt Outlook im Auftrag des Benutzers eine Anforderung an den verwalteten Speicher aus. Die Ausführung dieser Anforderung entspricht einem einzelnen Thread.
    
    In Exchange Server 2013 gibt es keine Thread-Limits auf Basis des Clienttyps mehr. Stattdessen wurde die maximale Anzahl an Threads **pro Postfachdatenbank** für alle Clients auf 50 festgelegt. Die einzige Ausnahme ist der Verfügbarkeitsdienst, für den ein maximales Limit von 16 Threads pro Benutzer gilt.

Zurück zum Seitenanfang

## Sitzungslimits

In der folgenden Tabelle sind die Arten von Clientverbindungen zum verwalteten Speicher sowie die für sie geltenden Limits aufgeführt. Wenn Sie die Sitzungslimits ändern möchten, lesen Sie den Abschnitt "Konfigurieren von Sitzungslimits" unmittelbar nach der Tabelle.

In früheren Exchange-Versionen wurden die Limits für Verbindungen zum verwalteten Speicher auf Basis der Anzahl an Verbindungen pro Server festgelegt. In Exchange 2013 werden die Sitzungslimits auf Basis der Anzahl an Verbindungen pro Postfachdatenbank festgelegt.

Es gibt die folgenden Typen von Verbindungslimits in Exchange 2013:

  - **Maximale Anzahl von Sitzungen pro Prozess:** Gibt die maximale Anzahl Sitzungen an, die ein Exchange-Dienst gleichzeitig zu einer Postfachdatenbank haben darf.

  - **Maximale Anzahl von Benutzersitzungen pro Prozess:** Gibt die maximale Anzahl von Sitzungen mit einem bestimmten Protokoll für einen einzelnen Benutzer an.

Im Abschnitt "Konfigurieren von Sitzungslimits" unten wird beschrieben, wie diese Limits angepasst werden können.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Clienttyp</th>
<th></th>
<th>Maximale Anzahl von Sitzungen pro Postfachdatenbank</th>
<th>Standardanzahl von Benutzersitzungen pro Postfachdatenbank</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Administrator</p></td>
<td></td>
<td><p>10,000</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>Verfügbarkeitsdienst</p></td>
<td></td>
<td><p>10,000</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Inhaltsindizierung</p></td>
<td></td>
<td><p>10,000</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>Exchange ActiveSync</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Webdienste</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="even">
<td><p>Verwaltung</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>MAPI on the Middle Tier (MoMT)</p></td>
<td></td>
<td><p>–</p></td>
<td><p>32</p></td>
</tr>
<tr class="even">
<td><p>MSExchangeMailboxAssistants: Ereignisse</p></td>
<td></td>
<td><p>10,000</p></td>
<td><p>–</p></td>
</tr>
<tr class="odd">
<td><p>MSExchangeMailboxAssistants: mit Zeitgeber</p></td>
<td></td>
<td><p>10,000</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>MSExchange-Remoteprozeduraufruf</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft OfficeOutlook Web App</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="even">
<td><p>POP3 und IMAP4</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Transport</p></td>
<td></td>
<td><p>10,000</p></td>
<td><p>–</p></td>
</tr>
<tr class="even">
<td><p>Unified Messaging</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Sonstige</p></td>
<td></td>
<td><p>–</p></td>
<td><p>16</p></td>
</tr>
</tbody>
</table>


## Konfigurieren von Sitzungslimits

Sie können die Standardwerte für die Sitzungslimits ändern.


> [!NOTE]
> Wenn Sie die Sitzungslimits ändern möchten, müssen Sie sie auf allen Postfachservern in allen Database Availability Groups (DAGs) ändern. Wenn Sie nicht auf allen Servern die gleichen Änderungen vornehmen, erhalten Sie ein inkonsistentes Ergebnis. Zur Erhöhung des Sitzungslimits auf dem Clientzugriffsserver muss der Wert <CODE>RCAMaxConcurrency</CODE> der Einschränkungsrichtlinie heraufgesetzt werden. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/dd298094(v=exchg.150)">Set-ThrottlingPolicy</A>.




> [!WARNING]
> Eine fehlerhafte Bearbeitung der Registrierung kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen kann. Durch fehlerhafte Bearbeitung der Registrierung verursachte Probleme können unter Umständen nicht mehr behoben werden. Sichern Sie alle wichtigen Daten, bevor Sie die Registrierung bearbeiten.



1.  Starten Sie den Registrierungs-Editor (**regedit**).

2.  Navigieren Sie zum folgenden Registrierungsunterschlüssel:
    
    **\\\\HKEY\_LOCAL\_MACHINE \\SYSTEM\\CurrentControlSet\\Services\\MSExchangeIS\\ParametersSystem**.

3.  Klicken Sie mit der rechten Maustaste auf **ParametersSystem**, wählen Sie **Neu** aus, und klicken Sie dann auf **DWORD-Wert (32-Bit)**.
    
    Der neue Wert wird im Ergebnisbereich erstellt.

4.  Benennen Sie den Schlüssel in einen der folgenden Werte um, und drücken Sie dann die EINGABETASTE:
    
      - **Maximum Allowed Sessions Per User**   Dieses Limit gibt die maximal zulässige Anzahl von Sitzungen pro Benutzer an.
    
      - **Maximum Allowed Service Sessions Per User**   Dieses Limit gibt die maximal zulässige Anzahl von Dienstsitzungen pro Benutzer an.
    
      - **Maximum Allowed Exchange Sessions Per Service**   Dieses Limit gibt die maximal zulässige Anzahl von Exchange-Sitzungen pro Dienst an. Der Standardwert ist 10.000.

5.  Klicken Sie mit der rechten Maustaste auf den gerade erstellten Schlüssel, und klicken Sie dann auf **Ändern**.

6.  Geben Sie in das Feld **Wert** die Anzahl von Objekten ein, auf die Sie diesen Eintrag beschränken möchten, und klicken Sie dann auf **OK**. Die Standardeinstellungen sehen Sie in der vorstehenden Tabelle.

Zurück zum Seitenanfang

## Limits für geöffnete Elemente

Limits für geöffnete Elemente begrenzen die Anzahl von Elementen, die ein einzelnes Postfach in einer einzelnen Sitzung öffnen kann. Ein Benutzer kann jedoch mehrere Sitzungen gleichzeitig öffnen. Er kann also beispielsweise mit zwei geöffneten Sitzungen 1.000 Ordner öffnen.

Wenn Sie diese Limits ändern möchten, lesen Sie den Abschnitt "Konfigurieren von Limits für geöffnete Elemente" unmittelbar nach der Tabelle.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Elementtyp</th>
<th>Registrierungsobjekttyp</th>
<th>Max. geöffnet pro Sitzung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ACL-Ansicht</p></td>
<td><p>objtACLView</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>Anhang</p></td>
<td><p>objtAttachment</p></td>
<td><p>500</p></td>
</tr>
<tr class="odd">
<td><p>Anlagenansicht</p></td>
<td><p>objtAttachmentView</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>CStream</p></td>
<td><p>objtCStream</p></td>
<td><p>–</p></td>
</tr>
<tr class="odd">
<td><p>Ordner</p></td>
<td><p>objtFolder</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>Ordneransicht</p></td>
<td><p>objtFolderView</p></td>
<td><p>500</p></td>
</tr>
<tr class="odd">
<td><p>FX-Zielstream</p></td>
<td><p>objtFXDstStrm</p></td>
<td><p>500</p></td>
</tr>
<tr class="even">
<td><p>FX-Quellstream</p></td>
<td><p>objtFXSrcStrm</p></td>
<td><p>500</p></td>
</tr>
<tr class="odd">
<td><p>Meldung</p></td>
<td><p>objtMessage</p></td>
<td><p>250</p></td>
</tr>
<tr class="even">
<td><p>Nachrichtenansicht</p></td>
<td><p>objtMessageView</p></td>
<td><p>500</p></td>
</tr>
<tr class="odd">
<td><p>Benachrichtigung</p></td>
<td><p>objtNotify</p></td>
<td><p>500,000</p></td>
</tr>
<tr class="even">
<td><p>Regelansicht</p></td>
<td><p>objtRulesView</p></td>
<td><p>–</p></td>
</tr>
<tr class="odd">
<td><p>Stream</p></td>
<td><p>objtStream</p></td>
<td><p>250</p></td>
</tr>
</tbody>
</table>


## Konfigurieren von Limits für geöffnete Elemente

Sie können die maximale Anzahl von Ressourcen begrenzen, die ein MAPI-Client gleichzeitig verwenden kann.


> [!NOTE]
> Wenn Sie die Limits für geöffnete Elemente ändern möchten, müssen Sie sie auf allen Postfachservern in allen DAGs und Clientzugriffsarrays ändern. Wenn Sie nicht auf allen Servern die gleichen Änderungen vornehmen, erhalten Sie ein inkonsistentes Ergebnis.




> [!WARNING]
> Eine fehlerhafte Bearbeitung der Registrierung kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen kann. Durch fehlerhafte Bearbeitung der Registrierung verursachte Probleme können unter Umständen nicht mehr behoben werden. Sichern Sie alle wichtigen Daten, bevor Sie die Registrierung bearbeiten.



1.  Starten Sie den Registrierungs-Editor (**regedit**).

2.  Navigieren Sie zum folgenden Registrierungsunterschlüssel:
    
    **\\\\HKEY\_LOCAL\_MACHINE \\SYSTEM\\CurrentControlSet\\Services\\MSExchangeIS\\ParametersSystem**

3.  Klicken Sie mit der rechten Maustaste auf **ParametersSystem**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Schlüssel**.
    
    In der Konsolenstruktur wird ein neuer Schlüssel erstellt.

4.  Benennen Sie den Schlüssel in **MaxObjsPerMapiSession** um, und drücken Sie dann die Eingabetaste.

5.  Klicken Sie mit der rechten Maustaste auf **MaxObjsPerMapiSession**, wählen Sie **Neu** aus, und klicken Sie dann auf **DWORD-Wert (32-Bit)**.
    
    Der neue Wert wird im Ergebnisbereich erstellt.

6.  Benennen Sie den Schlüssel in *\<Object\_type\>* um. Tragen Sie für *\<Object\_type\>* den Namen des Registrierungsobjekttyps ein, den Sie ändern möchten. Wenn Sie beispielsweise die Anzahl der Nachrichten ändern möchten, die geöffnet werden können, verwenden Sie *objtMessage*. Drücken Sie die EINGABETASTE.

7.  Klicken Sie mit der rechten Maustaste auf den gerade erstellten Schlüssel, und klicken Sie dann auf **Ändern**.

8.  Geben Sie in das Feld **Wert** die Anzahl an Objekten ein, auf die Sie diesen Eintrag begrenzen möchten, und klicken Sie dann auf **OK**. Geben Sie z. B. **350** ein, um den Wert für das Objekt zu erhöhen.

9.  Starten Sie den Microsoft Exchange-Informationsspeicherdienst neu.

Zurück zum Seitenanfang

## Größenlimit für Elemente

Größenlimits für Elemente gelten für Elemente in einem Benutzerpostfach. Sie können mithilfe der Parameter *MaxSendSize* und *MaxReceiveSize* im Cmdlet [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) konfiguriert werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Elementtyp</th>
<th>Grenze</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nachricht (gespeichert)</p></td>
<td><p>Maximale Größe von &quot;SendLimit&quot;, &quot;ReceiveLimit&quot;</p></td>
</tr>
<tr class="even">
<td><p>Nachricht (gesendet)</p></td>
<td><p>Maximale Größe von &quot;SendLimit&quot;</p></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

