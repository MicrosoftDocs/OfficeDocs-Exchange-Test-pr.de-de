---
title: 'Aktiv. d. Unterst. für Transport-Agents einer Vorversion: Exchange 2013-Hilfe'
TOCTitle: Aktivieren der Unterstützung für Transport-Agents einer Vorversion
ms:assetid: 00617e87-7199-406e-b4a3-94378f657f1f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ591524(v=EXCHG.150)
ms:contentKeyID: 50474926
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren der Unterstützung für Transport-Agents einer Vorversion

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In Microsoft Exchange Server 2013 werden Transport-Agents, die unter Verwendung von Microsoft .NET Framework 4.0 erstellt wurden, standardmäßig unterstützt. Exchange 2013 unterstützt auch Transport-Agents, die unter Verwendung früherer Versionen von .NET Framework erstellt wurden, diese Unterstützung ist jedoch nicht standardmäßig aktiviert. Zum Aktivieren der Unterstützung älterer Transport-Agents muss die entsprechende XML-Anwendungskonfigurationsdatei geändert werden. Welche Dateien geändert werden müssen, hängt vom Installationsort des Transport-Agents ab:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Server</th>
<th>Anwendungskonfigurationsdateien</th>
<th>Microsoft Windows-Dienst</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientzugriffsserver</p></td>
<td><p>%ExchangeInstallPath%Bin\MSExchangeFrontendTransport.exe.config</p></td>
<td><p>Microsoft Exchange-Front-End-Transport (MSExchangeFrontendTransport)</p></td>
</tr>
<tr class="even">
<td><p>Postfachserver</p></td>
<td><ul>
<li><p>%ExchangeInstallPath%Bin\EdgeTransport.exe.config</p></li>
<li><p>%ExchangeInstallPath%Bin\MSExchangeTransport.exe.config</p></li>
</ul></td>
<td><p>Microsoft Exchange-Transport (MSExchangeTransport)</p></td>
</tr>
</tbody>
</table>


Die Unterstützung für ältere Transport-Agents wird über Schlüssel in den Anwendungskonfigurationsdateien gesteuert. Standardmäßig sind keine der erforderlichen Schlüssel in den Anwendungskonfigurationsdateien vorhanden. Die Schlüssel müssen manuell hinzugefügt werden. In der folgenden Tabelle werden die einzelnen Schlüssel ausführlicher beschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Taste</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>useLegacyV2RuntimeActivationPolicy</em></p></td>
<td><p>Dieser Schlüssel aktiviert oder deaktiviert die Unterstützung für ältere Transport-Agents. Gültige Werte für diesen Schlüssel sind <code>true</code> oder <code>false</code>. Wenn dieser Schlüssel nicht angegeben wird, lautet der Standardwert <code>false</code>.</p></td>
</tr>
<tr class="even">
<td><p><em>supportedRuntime version</em></p></td>
<td><p>Dieser Schlüssel gibt die Version von Microsoft .NET Framework an, die für den Agent erforderlich ist. Folgende Werte fÜr diesen SchlÜssel sind gÜltig:</p>
<ul>
<li><p><code>v4.0</code> oder <code>v4.0.30319</code></p></li>
<li><p><code>v3.5</code> oder <code>v3.5.21022</code></p></li>
<li><p><code>v3.0</code> oder <code>v3.0.4506</code></p></li>
<li><p><code>v2.0</code> oder <code>v2.0.50727</code></p></li>
</ul>
<p>Wenn Sie mehrere Werte angeben möchten, verwenden Sie separate Instanzen des Schlüssels <em>supportedRuntime version</em>.</p>
<p>Bei Aktivierung der Unterstützung älterer Transport-Agents mithilfe des Schlüssels <em>useLegacyV2RuntimeActivationPolicy</em> sollten Sie zusätzlich zu den für den älteren Transport-Agent erforderlichen Werten immer den Wert <code>v4.0</code> angeben.</p></td>
</tr>
</tbody>
</table>


## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Exchange-Berechtigungen gelten nicht für die Verfahren in diesem Thema. Diese Verfahren werden im Betriebssystem des Exchange Server-Computers ausgeführt.

  - Änderungen an Anwendungskonfigurationsdateien werden nach dem Neustart des entsprechenden Diensts angewendet.

  - Beim Neustart der mit den Anwendungskonfigurationsdateien verknüpften Dienste wird die Nachrichtenübermittlung auf dem Server vorübergehend unterbrochen.

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config\&quot;-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config\&quot; auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]  
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der Unterstützung für ältere Transport-Agents über eine Eingabeaufforderung

Gehen Sie folgendermaßen vor, um die Unterstützung für ältere Transport-Agents zu aktivieren:

1.  Führen Sie auf dem Exchange 2013-Server, auf dem die Unterstützung älterer Transport-Agents konfiguriert werden soll, an einer Eingabeaufforderung den folgenden Befehl aus, um die entsprechende Anwendungskonfigurationsdatei im Editor zu öffnen:
    
       ```powershell
       Notepad %ExchangeInstallPath%Bin\<AppConfigFile>
       ```
    
    Zum Öffnen der Datei "EdgeTransport.exe.config" auf einem Postfachserver führen Sie z. B. den folgenden Befehl aus:
    
       ```powershell
       Notepad %ExchangeInstallPath%Bin\EdgeTransport.exe.config
       ```

2.  Navigieren Sie zum Schlüssel *\</configuration\>* am Ende der Datei, und fügen Sie vor dem Schlüssel *\</configuration\>* die folgenden Schlüssel ein:
    
      ```xml
       <startup useLegacyV2RuntimeActivationPolicy="true">
               <supportedRuntime version="v4.0" />
               <supportedRuntime version="v3.5" />
               <supportedRuntime version="v3.0" />
               <supportedRuntime version="v2.0" />
       </startup>
      ```

3.  Speichern und schließen Sie die Anwendungskonfigurationsdatei nach Abschluss des Vorgangs.

4.  Wiederholen Sie die Schritte 1 bis 3, um die anderen Anwendungskonfigurationsdateien zu ändern.

5.  Führen Sie den folgenden Befehl aus, um den zugehörigen Windows-Dienst zu starten:
    
     ```powershell
     net stop <service> && net start <service>
     ```
    
    Wenn Sie z. B. die Datei "EdgeTransport.exe.config" geändert haben, müssen Sie den Microsoft Exchange-Transportdienst über den folgenden Befehl neu starten:
    
     ```powershell
     net stop MSExchangeTransport && net start MSExchangeTransport
     ```

6.  Wiederholen Sie Schritt 5, um Dienste neu zu starten, die den anderen geänderten Anwendungskonfigurationsdateien zugeordnet sind.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Diese Schritte waren erfolgreich, wenn der ältere Transport-Agent erfolgreich installiert werden kann. Wenn Sie versuchen, einen älteren Transport-Agent zu installieren, ohne zuvor die in diesem Thema beschriebenen Schritte auszuführen, wird ein Fehler angezeigt, der mit der folgenden Meldung vergleichbar ist:

```powershell
Mixed mode assembly is built against version '<version>' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.
```

