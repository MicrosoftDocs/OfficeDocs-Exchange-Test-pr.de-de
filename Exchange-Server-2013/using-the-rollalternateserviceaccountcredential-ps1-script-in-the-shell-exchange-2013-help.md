---
title: 'Verwenden des Skripts "RollAlternateserviceAccountCredential.ps1" in der Shell: Exchange 2013 Help'
TOCTitle: Verwenden des Skripts "RollAlternateserviceAccountCredential.ps1" in der Shell
ms:assetid: 6ac55aae-472a-4ed6-83df-2d0e7b48e05c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff808311(v=EXCHG.150)
ms:contentKeyID: 63915382
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden des Skripts \"RollAlternateserviceAccountCredential.ps1\" in der Shell

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-09_

Sie können das Skript „RollAlternateserviceAccountCredential.ps1“ in Exchange Server 2013 verwenden, um die Anmeldeinformationen für das alternative Dienstkonto (ASA-Anmeldeinformationen) zu aktualisieren und das Update an bestimmte Clientzugriffsserver zu verteilen.


> [!NOTE]
> Skripts werden in der Exchange-Verwaltungshell nicht automatisch geladen. Sie müssen allen Skripts die Zeichen „<STRONG>.\</STRONG>“ voranstellen. Geben Sie z.&nbsp;B. <CODE>.\RollAlternateServiceAccountPassword.ps1</CODE> ein, um das Skript „RollAlternateserviceAccountCredential.ps1“ auszuführen.




> [!NOTE]
> Dieses Skript wird ausschließlich auf Englisch bereitgestellt.



Weitere Informationen zum Verwenden und Schreiben von Skripts finden Sie unter [Skripterstellung mit der Exchange-Verwaltungsshell](https://technet.microsoft.com/de-de/library/bb123798\(v=exchg.150\)).

## Syntax

    RollAlternateServiceAccountPassword.ps1 -Scope <Object> -Identity <Object> -Source <Object> -

## Detaillierte Beschreibung

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Clientzugriffssicherheit" im Thema "Clientzugriffsberechtigungen".

## Technische Details des Skripts für Anmeldeinformationen für das alternative Dienstkonto

Dieses Skript vereinfacht die Einrichtung und Wartung der ASA-Anmeldeinformationen. Wenn Sie die ASA-Anmeldeinformationen erstellt und die entsprechenden Dienstprinzipalnamen festgelegt haben, können Sie die Anmeldeinformationen mithilfe des Skripts an die Ziel-Clientzugriffsserver verteilen.

Wenn Sie das Skript verwenden möchten, müssen Sie die Zielserver identifizieren und angeben, welche Anmeldeinformationen Sie als ASA-Anmeldeinformationen verwenden möchten.

## Serverbereich

Sie können mithilfe des Skripts alle Clientzugriffsserver in der Gesamtstruktur, alle Mitglieder eines bestimmten Clientzugriffsserver-Arrays oder bestimmte Server als Ziel vorgeben. Die verfügbaren Parameter sind *ToEntireForest*, *ToArraryMembers* und *ToSpecificServers*. Wenn Sie im Skript bestimmte Server oder Mitglieder eines bestimmten Serverarrays als Ziel vorgeben, muss der Parameter *Identity* mit den Zielservern bzw. den entsprechenden Serverarraynamen angegeben werden.

## Quelle der Anmeldeinformationen

Das Skript kann das Kennwort des alternativen Dienstkontos von einem vorhandenen Server kopieren. Sie können aber auch das zu verwendende Konto angeben und das Skript ein neues Kennwort für das Konto generieren lassen. Die verfügbaren Parameter sind *GenerateNewPasswordFor* und *CopyFrom*. Der Parameter *GenerateNewPasswordFor* erfordert die Angabe einer Kontozeichenfolge im folgenden Format: DOMÄNE\\Kontoname. Wenn Sie ein Computerkonto verwenden, müssen Sie am Ende des Kontonamens das Zeichen „$“ anhängen. Beispiel: CONTOSO\\ClientServerAcct$. Der Parameter *CopyFrom* verwendet den Namen eines vorhandenen Clientzugriffsservers als Quelle der Anmeldeinformationen.

## Generieren ein neues Kennworts für Anmeldeinformationen

Das Kennwort wird vom Skript erstellt. Es ist keine Benutzereingabe erforderlich. Das Skript versucht, das Kennwort an alle Zielcomputer zu verteilen und dann die Active Directory-Anmeldeinformationen anhand des neu generierten Kennworts zu aktualisieren.

Das neu generierte Kennwort ist 73 Zeichen lang und erfüllt die Standardanforderungen für sichere Kennwörter. Wenn Ihre Kennwortanforderungen abweichen, müssen Sie das Kennwort u. U. manuell festlegen und dann auf die Zielserver kopieren.

Das Skript untersucht alle Clientzugriffsserver, um Dienstunterbrechungen zu verhindern, und bewahrt zusätzlich zum neuen Kennwort das aktuelle Kennwort auf. Nach dem Ausführen des Skripts können die freigegebenen ASA-Anmeldeinformationen eines von zwei Kennwörtern verwenden: das aktuelle Kennwort, das in Active Directory gespeichert ist, oder das neue Kennwort, das bisher noch nicht in Active Directory festgelegt wurde.

Alle Kennwörter, die nicht mehr gültig sind, z. B. abgelaufene Kennwörter, werden von den Zielservern entfernt. Wenn das Kennwort in Active Directory nicht geändert werden kann, weil es möglicherweise abgelaufen ist, versucht das Skript, das Kennwort zurückzusetzen. Dafür muss das Konto, unter dem das Skript ausgeführt wird, Berechtigungen zum Zurücksetzen von Active Directory-Computerkontokennwörtern oder -Benutzerkontokennwörtern besitzen, je nachdem, ob es sich bei dem alternativen Dienstkonto um ein Computerkonto oder ein Benutzerkonto handelt.

Wenn die Kennwörter nicht für alle Ziel-Clientzugriffsserver erfolgreich geändert werden, kann das Aktualisieren des Active Directory-Kennworts einen Authentifizierungsfehler verursachen. Wenn das Skript im unbeaufsichtigten Modus ausgeführt wird, wird das Active Directory-Kennwort nicht in das neue Kennwort geändert, solange die Ziel-Clientzugriffsserver nicht erfolgreich aktualisiert wurden. Wenn das Skript im unbeaufsichtigten Modus ausgeführt wird, werden Sie gefragt, ob Sie das Kennwort in Active Directory aktualisieren wollen.

## Erstellen eines geplanten Tasks zum Automatisieren der Kennwortwartung

Wenn das Skript einen geplanten Task für die fortlaufende Wartung des Kennworts erstellen soll, verwenden Sie den Parameter *CreateScheduledTask*. Dieser Parameter erfordert eine Zeichenfolge für den Namen des zu erstellenden Tasks.


> [!NOTE]
> Führen Sie das Skript aus, und stellen Sie sicher, dass es im beaufsichtigten Modus richtig ausgeführt wird, bevor Sie den unbeaufsichtigten geplanten Task erstellen.



Das Skript erstellt eine CMD-Datei in dem Ordner, in dem sich das Skript befindet. Dann erstellt es einen Task, um die CMD-Datei alle drei Wochen auszuführen. Sie können den geplanten Task mithilfe des Windows-Taskplaners ändern, z. B. damit dieser häufiger oder seltener ausgeführt wird. In der Standardeinstellung wird der Task als aktuell angemeldeter Benutzer ausgeführt. Darüber hinaus wird das Skript nur ausgeführt, wenn der Benutzer am Computer angemeldet ist. Sie sollten den geplanten Task so ändern, dass er unabhängig davon ausgeführt wird, ob der Benutzer angemeldet ist. Sie können den Task wahlweise auch unter einem anderen Konto ausführen, sofern das Konto Active Directory-Berechtigungen zum Zurücksetzen von Kennwörtern sowie die Exchange-Rolle "Organisationsadministrator" aufweist. Wenn Sie einen geplanten Task erstellen, wird das Skript automatisch im unbeaufsichtigten Modus ausgeführt.

## Tasks außerhalb des Skriptbereichs

Mit dem Skript können keine Sicherheitsprinzipalnamen der ASA-Anmeldeinformationen verwaltet und auch kein alternatives Dienstkonto von einem Server entfernt werden. Informationen zum Entfernen eines alternativen Dienstkontos von einem Server finden Sie im Abschnitt [Turn Kerberos authentication off](configuring-kerberos-authentication-for-load-balanced-client-access-servers-exchange-2013-help.md) unter [Konfigurieren der Kerberos-Authentifizierung für Clientzugriffsserver mit Lastenausgleich](configuring-kerberos-authentication-for-load-balanced-client-access-servers-exchange-2013-help.md).

## Problembehandlung für das Skript

Sie sollten das Skript ausführen und sicherstellen, dass es im beaufsichtigten Modus richtig ausgeführt wird, bevor Sie den unbeaufsichtigten geplanten Task erstellen. Informationen zur Problembehandlung finden Sie unter [Problembehandlung für das Skript "RollAlternateServiceAccountCredential.ps1"](troubleshooting-the-rollalternateserviceaccountcredential-ps1-script-exchange-2013-help.md).

## Überprüfen des Skripts

Wenn Sie das Skript interaktiv mit dem Flag "-verbose" ausführen, sollte die Ausgabe angeben, welche Skriptoperationen erfolgreich waren. Zur Bestätigung, dass die Clientzugriffsserver aktualisiert wurden, können Sie den letzten geänderten Zeitstempel in den ASA-Anmeldeinformationen überprüfen. Im folgenden Beispiel wird eine Liste mit Clientzugriffsservern und dem letzten Zeitpunkt generiert, an dem das alternative Dienstkonto aktualisiert wurde.

    Get-ClientAccessServer -IncludeAlternateServiceAccountCredentialstatus |Fl Name, AlternateServiceAccountConfiguration

Sie können auch das Ereignisprotokoll auf dem Computer prüfen, auf dem das Skript ausgeführt wird. Die Ereignisprotokolleinträge für das Skript befinden sich im Anwendungsereignisprotokoll und stammen aus der Quell-*MSExchange Management Application*.In der folgenden Tabelle sind die protokollierten Ereignisse und ihre Bedeutung aufgelistet.

### Skriptereignis-IDs und ihre Erläuterung

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ereignis</th>
<th>Erläuterung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>14001</p></td>
<td><p>Start</p></td>
</tr>
<tr class="even">
<td><p>14002</p></td>
<td><p>Erfolg (Information)</p></td>
</tr>
<tr class="odd">
<td><p>14003</p></td>
<td><p>Erfolgreich, aber mit Warnungen.</p>
<p>Das Skript ist auf einige Fehler gestoßen, konnte diese jedoch zunächst außer Acht lassen oder erhielt durch eine Benutzereingabe die Bestätigung, dass sie nicht von Bedeutung sind. Wird das Skript im interaktiven Modus ausgeführt, finden Sie in der Skriptausgabe weitere Details zu den Warnungen.</p></td>
</tr>
<tr class="even">
<td><p>14004</p></td>
<td><p>Fehler</p></td>
</tr>
</tbody>
</table>


Wenn das Skript als geplanter Task ausgeführt wird, werden seine Ergebnisse im Ordner **Protokollierung** des Exchange-Servers in dem Unterordner **RollAlternateServiceAccountPassword** protokolliert.

Sie können anhand des Protokolls erkennen, dass der Task erfolgreich ausgeführt wurde.

## Parameter


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Erforderlich</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ToEntireForest</em></p></td>
<td><p>Optional</p></td>
<td><p>Mit dem Parameter <em>ToEntireForest</em> gibt das Skript alle Clientzugriffsserver in der Gesamtstruktur als Ziel vor.</p></td>
</tr>
<tr class="even">
<td><p><em>ToArrayMembers</em></p></td>
<td><p>Optional</p></td>
<td><p>Mit dem Parameter <em>ToArrayMembers</em> gibt das Skript alle Mitglieder eines bestimmten Clientzugriffsserver-Arrays als Ziel vor.</p>

> [!NOTE]
> Wenn Sie den Parameter <EM>ToArrayMembers</EM> oder <EM>ToSpecificServers</EM> verwenden, müssen Sie die Servernamen oder die Serverarraynamen mithilfe des Parameters <EM>Identity</EM> angeben.


</td>
</tr>
<tr class="odd">
<td><p><em>ToSpecificServers</em></p></td>
<td><p>Optional</p></td>
<td><p>Mit dem Parameter <em>ToSpecificServers</em> gibt das Skript bestimmte Zielserver vor.</p>

> [!NOTE]
> Wenn Sie den Parameter <EM>ToArrayMembers</EM> oder <EM>ToSpecificServers</EM> verwenden, müssen Sie die Servernamen oder die Serverarraynamen mithilfe des Parameters <EM>Identity</EM> angeben.


</td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Erforderlich</p></td>
<td><p>Der Parameter <em>Identity</em> gibt den Namen des Clientzugriffsserver-Arrays oder die Namen der bestimmten Server an, die als Ziel vorgegeben werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>GenerateNewPasswordFor&lt;String&gt;</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>GenerateNewPasswordFor</em> gibt an, dass das Skript ein neues Kennwort für das alternative Dienstkonto generieren soll. Der Zeichenfolgenwert muss dem alternativen Dienstkonto im folgenden Format entsprechen: DOMÄNE\Kontoname. Wenn Sie ein Computerkonto verwenden, müssen Sie am Ende des Kontonamens das Zeichen „$“ anhängen.</p></td>
</tr>
<tr class="even">
<td><p><em>CopyFrom&lt;String&gt;</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>CopyFrom</em> gibt an, dass die Anmeldeinformationen von einem anderen Clientzugriffsserver kopiert werden. Der angegebene Zeichenfolgenwert ist der Name des Clientzugriffsservers.</p></td>
</tr>
<tr class="odd">
<td><p><em>Mode</em></p></td>
<td><p>Optional</p></td>
<td><p>Die Option <em>Mode</em> gibt an, ob das Skript im beaufsichtigten oder unbeaufsichtigten Modus ausgeführt wird. Der unbeaufsichtigte Modus erfordert keine Benutzereingabe und wählt ggf. automatisch eher konservativere Optionen.</p></td>
</tr>
<tr class="even">
<td><p><em>CreateScheduledTask&lt;String&gt;</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>CreateScheduledTask</em> weist das Skript an, einen geplanten Task für die Durchführung des Updates der ASA-Anmeldeinformationen zu erstellen. Der Zeichenfolgenwert ist der Name des zu erstellenden geplanten Tasks.</p>

> [!NOTE]
> Das Skript erstellt eine CMD-Datei in dem Ordner, in dem sich das Skript befindet. Der geplante Task führt die CMD-Datei einmal alle drei Wochen aus. Sie können den Task direkt im Windows-Taskplaner bearbeiten, wenn Sie die Häufigkeit ändern wollen, mit der der Task ausgeführt wird.


</td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>Die Option <em>WhatIf</em> weist den Befehl an, die für das Objekt auszuführenden Aktionen zu simulieren. Durch Verwendung der Option <em>WhatIf</em> können Sie eine Vorschau der Änderungen anzeigen, ohne diese Änderungen wirklich übernehmen zu müssen. Für die<em>WhatIf</em>-Option muss kein Wert angegeben werden.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>Die Option <em>Confirm</em> bewirkt eine Unterbrechung der Befehlsausführung und zwingt Sie, die Aktion des Befehls zu bestätigen, bevor die Verarbeitung fortgesetzt wird. Für die Option <em>Confirm</em> muss kein Wert angegeben werden.</p></td>
</tr>
<tr class="odd">
<td><p><em>Verbose</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>Verbose</em> weist das Skript an, die ausführliche Protokollierung zu verwenden, sodass zusätzliche Informationen zu den Aktionen des Skripts in die Protokolldatei geschrieben werden.</p></td>
</tr>
<tr class="even">
<td><p><em>Debug</em></p></td>
<td><p>Optional</p></td>
<td><p>Der Parameter <em>Debug</em> weist das Skript an, im Debugmodus zu starten. Dieser Parameter sollte verwendet werden, um zu ermitteln, warum das Skript einen Fehler verursacht.</p></td>
</tr>
</tbody>
</table>


## Beispiele

## Beispiel 1

In diesem Beispiel wird das Skript verwendet, um die Anmeldeinformationen für das erste Setup per Push an alle Clientzugriffsserver in der Gesamtstruktur zu verteilen.

    .\RollAlternateserviceAccountPassword.ps1 -ToEntireForest -GenerateNewPasswordFor "Contoso\ComputerAccount$" -Verbose

## Beispiel 2

In diesem Beispiel wird ein neues Kennwort für ASA-Anmeldeinformationen eines Benutzerkontos generiert und das Kennwort an alle Mitglieder des Clientzugriffsserver-Arrays verteilt, bei deren Namen eine Übereinstimmung mit \*mailbox\* erkannt wird.

    .\RollAlternateserviceAccountPassword.ps1 -ToArrayMembers *mailbox* -GenerateNewPasswordFor "Contoso\UserAccount" -Verbose

## Beispiel 3

In diesem Beispiel wird ein einmal pro Monat geplanter automatischer Task namens "Exchange-RollAsa" geplant. Er aktualisiert die ASA-Anmeldeinformationen für alle Clientzugriffsserver in der Gesamtstruktur anhand eines neuen, skriptgenerierten Kennworts. Der geplante Task wird erstellt, aber das Skript wird nicht ausgeführt. Wenn der geplante Task ausgeführt wird, wird das Skript im unbeaufsichtigten Modus ausgeführt.

    .\RollAlternateServiceAccountPassword.ps1 -CreateScheduledTask "Exchange-RollAsa" -ToEntireForest -GenerateNewPasswordFor 'contoso\computerAccount$'

## Beispiel 4

In diesem Beispiel werden die ASA-Anmeldeinformationen für alle Clientzugriffsserver im Clientzugriffsserver-Array "CAS01" aktualisiert. Die Anmeldeinformationen werden vom Active Directory-Computerkonto "ServiceAc1" in der Domäne "Contoso" abgerufen.

    .\RollAlternateserviceAccountPassword.ps1 -ToArrayMembers "CAS01" -GenerateNewPasswordFor "CONTOSO\ServiceAc1$" 

## Beispiel 5

In diesem Beispiel wird gezeigt, wie Sie das Skript verwenden können, um ASA-Anmeldeinformationen an einen neuen Computer zu verteilen oder an einen Computer, der wieder in Dienst genommen wird, wenn Sie beispielsweise Ihr Serverarray vergrößert haben oder Arraymitglieder nach der Wartung wieder zum Array hinzufügen.

Sie müssen die ASA-Anmeldeinformationen aktualisieren, bevor der Clientzugriffsserver Datenverkehr empfängt. Kopieren Sie die freigegebenen ASA-Anmeldeinformationen von einem bereits richtig konfigurierten Clientzugriffsserver. Wenn Server A beispielsweise aktuell über funktionierende ASA-Anmeldeinformationen verfügt und Sie Server B gerade dem Array hinzugefügt haben, können Sie die Anmeldeinformationen (einschließlich Kennwort) mithilfe des Skripts von Server A nach Server B kopieren. Dies ist hilfreich, wenn Server B heruntergefahren oder bei der letzten Änderung des Kennworts noch kein Mitglied des Arrays war.

    .\RollAlternateServiceAccountPassword.ps1 -CopyFrom ServerA -ToSpecificServers ServerB -Verbose

