---
title: 'Konfig. von clientspezif. Nachrichtengrößenbegrenzungen: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von clientspezifischen Nachrichtengrößenbegrenzungen
ms:assetid: fef9ca78-b68f-4342-ada0-881ab985ce3c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529949(v=EXCHG.150)
ms:contentKeyID: 52062930
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von clientspezifischen Nachrichtengrößenbegrenzungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-01-26_

In Microsoft Exchange Server 2013 gelten für die Übertragung von Nachrichten über die Exchange-Organisation verschiedene Größenbeschränkungen. Weitere Informationen finden Sie unter [Beschränkungen der Nachrichtengröße](message-size-limits-exchange-2013-help.md).

Es gibt jedoch clientspezifische Nachrichtengrößenbeschränkungen, die für Outlook Web App und E-Mail-Clients, die ActiveSync oder ActiveSync (EWS) verwenden, konfiguriert werden können. Wenn Sie die Exchange-organisationsweiten Größenbeschränkungen für Nachrichten ändern, müssen Sie sich vergewissern, dass die Nachrichtengrößenbeschränkungen für Exchange-Webdienste, Outlook Web App und Exchange-Webdienste entsprechend festgelegt werden. Sie können diese Werte in „web.config“-Dateien auf Clientzugriffs- und Postfachservern konfigurieren. Diese Beschränkungen werden in den folgenden Tabellen beschrieben:

### ActiveSync

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Serverrolle</th>
<th>Konfigurationsdatei</th>
<th>Schlüssel und Standardwerte</th>
<th>Größe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientzugriff</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;30000000 bytes&quot;</code> ist standardmäßig nicht vorhanden (siehe Kommentare).</p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="even">
<td><p>Clientzugriff</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;10240&quot;</code></p></td>
<td><p>Kilobyte</p></td>
</tr>
<tr class="odd">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Sync\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;30000000 bytes&quot;</code> ist standardmäßig nicht vorhanden (siehe Kommentare).</p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="even">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Sync\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;10240&quot;</code></p></td>
<td><p>Kilobyte</p></td>
</tr>
<tr class="odd">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Sync\web.config</code></p></td>
<td><p><code>&lt;add key=&quot;MaxDocumentDataSize&quot; value=&quot;10240000&quot;&gt;</code></p></td>
<td><p>Bytes</p></td>
</tr>
</tbody>
</table>


**Kommentare in Bezug auf ActiveSync-Beschränkungen**

Standardmäßig ist kein *maxAllowedContentLength*-Schlüssel in den `web.config`-Dateien für ActiveSync vorhanden. Die maximale Nachrichtengröße für ActiveSync wird jedoch durch den Wert **maxAllowedContentLength** beeinflusst, der für alle Websites auf dem Server übernommen wird. Der Standardwert beträgt 30000000 Bytes (30 MB). Führen Sie die folgenden Schritte aus, um diese Werte für ActiveSync auf Clientzugriffs- und Postfachservern im IIS-Manager anzuzeigen:

1.  Führen Sie einen der folgenden Schritte aus:
    
      - Öffnen Sie auf Clientzugriffsservern **IIS-Manager**, wechseln Sie zu **Websites** \> **Standardwebsite**, und wählen Sie **Microsoft-Server-ActiveSync** aus.
    
      - Öffnen Sie auf Postfachservern **IIS-Manager**, wechseln Sie zu **Websites** \> **Exchange Back End**, und wählen Sie **Microsoft-Server-ActiveSync** aus.

2.  Stellen Sie sicher, dass die Ansicht **Features** ausgewählt ist, und doppelklicken Sie im Abschnitt für die Verwaltung auf **Konfigurations-Editor**.

3.  Klicken Sie im Feld **Abschnitt** auf den Dropdownpfeil, navigieren Sie zu **system.webServer** \> **Sicherheit**, und wählen Sie **requestFiltering** aus.

4.  Erweitern Sie in den Ergebnissen **requestLimits**, sodass **maxAllowedContentLength** und der Standardwert "30000000" (Byte" angezeigt werden.

Geben Sie zum Ändern des Werts **maxAllowedContentLength** einen neuen Wert in "Bytes" ein, und klicken Sie auf die Option zum Übernehmen. Sie müssen den Wert auf Clientzugriffs- und Postfachservern ändern. Nachdem Sie den Wert im IIS-Manager geändert haben, wird ein neuer *maxAllowedContentLength*-Schlüssel in die entsprechende `web.config`-Datei (`%ExchangeInstallPath%FrontEnd\HttpProxy\Sync\web.config` auf Clientzugriffs- und `%ExchangeInstallPath%ClientAccess\Sync\web.config` auf Postfachservern) geschrieben.

Zum Ändern der maximal zulässigen Nachrichtengröße für ActiveSync-Clients müssen Sie den Wert von *maxRequestLength* in der `web.config`-Datei auf Clientzugriffs- und Postfachservern, *MaxDocumentDataSize* in der `web.config`-Datei auf Postfachservern und *maxAllowedContentLength* im IIS-Manager auf Clientzugriffs- und Postfachservern ändern.

### Exchange-Webdienste

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Rolle „Verarbeiten“</th>
<th>Konfigurationsdatei</th>
<th>Schlüssel und Standardwerte</th>
<th>Größe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientzugriff</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\ews\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;67108864&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="even">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\exchweb\ews\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;67108864&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="odd">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\exchweb\ews\web.config</code></p></td>
<td><p>14 Instanzen von <code>maxReceivedMessageSize=&quot;67108864&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
</tbody>
</table>


**Kommentare in Bezug auf Begrenzungen bei Exchange-Webdiensten**

  - Für den Wert `maxReceivedMessageSize="67108864"` gibt es 14 separate Instanzen, die verschiedenen Kombinationen von Bindungen (HTTP und HTTPS) und Authentifizierungsmethoden entsprechen.

  - Zum Ändern der maximal zulässigen Nachrichtengröße für Exchange-Webdienstclients müssen Sie den Wert von *maxAllowedContentLength* in beiden `web.config`-Dateien und alle 14 Instanzen von `maxReceivedMessageSize="67108864"` in der `web.config`-Datei auf Postfachservern ändern.

  - In der `web.config`-Datei auf Postfachservern gibt es zudem zwei Instanzen des Werts `maxReceivedMessageSize="1048576"` für **UMLegacyMessageEncoderSoap11Element**-Bindungen, die Sie nicht ändern müssen.

  - *maxRequestLength* ist eine ASP.NET-Einstellung, die in beiden "web.config"-Dateien vorhanden ist. Sie wird jedoch durch die Exchange-Webdienste nicht verwendet und muss daher nicht geändert werden.

### Outlook Web App

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Serverrolle</th>
<th>Konfigurationsdatei</th>
<th>Schlüssel und Standardwerte</th>
<th>Größe</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Clientzugriff</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\owa\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;35000000&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="even">
<td><p>Clientzugriff</p></td>
<td><p><code>%ExchangeInstallPath%FrontEnd\HttpProxy\owa\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;35000&quot;</code></p></td>
<td><p>Kilobyte</p></td>
</tr>
<tr class="odd">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p><code>maxAllowedContentLength=&quot;35000000&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="even">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p><code>maxRequestLength=&quot;35000&quot;</code></p></td>
<td><p>Kilobyte</p></td>
</tr>
<tr class="odd">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p>2 Instanzen von <code>maxReceivedMessageSize=&quot;35000000&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
<tr class="even">
<td><p>Postfach</p></td>
<td><p><code>%ExchangeInstallPath%ClientAccess\Owa\web.config</code></p></td>
<td><p>2 Instanzen von <code>maxStringContentLength=&quot;35000000&quot;</code></p></td>
<td><p>Bytes</p></td>
</tr>
</tbody>
</table>


**Kommentare in Bezug auf Outlook Web App-Beschränkungen**

  - In der `web.config`-Datei auf Postfachservern gibt es zwei separate Instanzen der Werte `maxReceivedMessageSize="35000000"` und `maxStringContentLength="35000000"`, die HTTP- und HTTPS-Bindungen entsprechen.

  - Zum Ändern der maximal zulässigen Nachrichtengröße für Outlook Web App-Clients müssen Sie all diese Werte in beiden Dateien, einschließlich beider Instanzen von *maxReceivedMessageSize* und *maxStringContentLength* in der `web.config`-Datei auf Postfachservern, ändern.

  - In der `web.config`-Datei auf Postfachservern gibt es zudem eine Instanz des Werts `maxStringContentLength="102400"` für die Bindung **MsOnlineShellService**, die Sie nicht ändern müssen.

Sie müssen für alle Nachrichtengrößenbeschränkungen Werte festlegen, die größer als die tatsächlich zu erzwingenden Größen sind. Diese Werterhöhung ist notwendig, um der Vergrößerung der Nachricht gerecht zu werden, die nach der Base64-Verschlüsselung der Nachrichtenanlagen und eventueller binärer Daten unvermeidlich ist. Durch Base64-Verschlüsselung vergrößert sich die Nachricht um ca. 33 % – daher müssen die von Ihnen angegebenen Werte für Nachrichtengrößenbeschränkungen ca. 33 % größer sein als die tatsächlich nutzbare Nachrichtengröße. Wenn Sie beispielsweise für Nachrichten eine maximale Größenbeschränkung von 64 MB angeben, können Sie erwarten, dass die maximale Größe der Nachricht in Wirklichkeit ca. 48 MB beträgt.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Exchange-Berechtigungen gelten nicht für die Verfahren in diesem Thema. Diese Verfahren werden im Betriebssystem des Exchange Server-Computers ausgeführt.

  - In der Konfigurationsdatei "web.config" gespeicherte Änderungen werden nach einem Neustart von IIS wirksam.

  - Multiplizieren Sie den gewünschten neuen maximalen Größenwert in Megabyte mit 4/3, um eine durch Base64-Verschlüsselung bedingte Vergrößerung um 33 % einzukalkulieren. Zum Umrechnen des Werts in Kilobyte multiplizieren Sie ihn mit 1024. Zum Konvertieren des Werts in Byte multiplizieren Sie ihn mit 1048756 (1024\*1024). Beachten Sie, dass die durch Base64-Verschlüsselung verursachte Vergrößerung mehr als 33 % betragen kann und von verschiedenen Faktoren abhängt, wie Größe, Typ und Komprimierung der Anlagendatei sowie dem E-Mail-Client, der zum Erstellen und Senden der Nachricht verwendet wird.

  - Alle benutzerdefinierten Einstellungen auf Serverbasis, die Sie an Exchange-XML-Anwendungskonfigurationsdateien vornehmen (z. B. an „web.config“-Dateien auf Clientzugriffsservern bzw. an der Datei „EdgeTransport.exe.config“ auf Postfachservern), werden bei der Installation eines kumulativen Exchange-Updates überschrieben. Stellen Sie sicher, dass diese Informationen gespeichert werden, damit Sie Ihren Server nach der Installation leicht erneut konfigurieren können. Nach der Installation eines kumulativen Exchange-Updates müssen Sie diese Einstellungen neu konfigurieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden von Editor zum Konfigurieren einer clientspezifischen Nachrichtengrößenbegrenzung

1.  Öffnen Sie die entsprechenden „web.config“-Dateien in Editor: Führen Sie beispielsweise zum Öffnen der „web.config“-Dateien für Exchange-Webdienste-Clients die folgenden Befehle aus:
    
        Notepad %ExchangeInstallPath%ClientAccess\exchweb\ews\web.config
        Notepad %ExchangeInstallPath%FrontEnd\HttpProxy\ews\web.config

2.  Suchen Sie in den „web.config“-Dateien der entsprechenden Komponente nach den relevanten Schlüsseln (siehe obige Tabellen in diesem Thema). Suchen Sie beispielsweise für Exchange-Webdienste-Clients den *maxAllowedContentLength*-Schlüssel in beiden Dateien und allen 14 Instanzen des Werts `maxReceivedMessageSize="67108864"` in der `web.config`-Datei auf Postfachservern.
    
        <requestLimits maxAllowedContentLength="67108864" />
        ...maxReceivedMessageSize="67108864"...
    
    Wenn Sie beispielsweise eine Base64-verschlüsselte maximale Nachrichtengröße von ca. 64 MB erlauben möchten, ändern Sie alle Instanzen von `67108864` in `89478486` (64\*4/3\*1048756):
    
        <requestLimits maxAllowedContentLength="89478486" />
        ...maxReceivedMessageSize="89478486"...

3.  Speichern und schließen Sie die "web.config"-Dateien nach Abschluss des Vorgangs.

4.  Starten Sie IIS neu, indem Sie den folgenden Befehl ausführen:
    
    ```powershell
IISReset /noforce
```

## Konfigurieren von clientspezifischen Nachrichtengrößenbegrenzungen über die Befehlszeile

Statt mit dem Editor können Sie die clientspezifischen Nachrichtengrößenbegrenzungen über die Befehlszeile konfigurieren. Öffnen Sie die Eingabeaufforderung mit erhöhten Rechten auf dem Exchange-Server (ein Eingabeaufforderungsfenster, das Sie durch Auswählen von **Als Administrator ausführen** öffnen), und führen Sie die entsprechenden Befehle für die Grenzwerte aus, die Sie konfigurieren möchten.

**Hinweise:** 

  - Die Größenwerte in den Befehlen sind die Standardwerte, daher müssen Sie diese ändern.

  - Achten Sie unbedingt darauf, ob der Wert in Bytes oder KB angegeben wird.

**ActiveSync**

    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/Microsoft-Server-ActiveSync/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:30000000
    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/Microsoft-Server-ActiveSync/" -section:system.web/httpRuntime /maxRequestLength:10240
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/Microsoft-Server-ActiveSync/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:30000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/Microsoft-Server-ActiveSync/" -section:system.web/httpRuntime /maxRequestLength:10240
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/Microsoft-Server-ActiveSync/" -section:appSettings /[key='MaxDocumentDataSize'].value:10240000

**Exchange-Webdienste**

    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/ews/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSAnonymousHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSAnonymousHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSBasicHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSBasicHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSNegotiateHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSNegotiateHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecuritySymmetricKeyHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecuritySymmetricKeyHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityX509CertHttpsBinding'].httpsTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /customBinding.[name='EWSWSSecurityX509CertHttpBinding'].httpTransport.maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /webHttpBinding.[name='EWSStreamingNegotiateHttpsBinding'].maxReceivedMessageSize:67108864
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/ews/" -section:system.serviceModel/bindings /webHttpBinding.[name='EWSStreamingNegotiateHttpBinding'].maxReceivedMessageSize:67108864

**Outlook Web App**

    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/owa/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Default Web Site/owa/" -section:system.web/httpRuntime /maxRequestLength:35000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.webServer/security/requestFiltering /requestLimits.maxAllowedContentLength:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.web/httpRuntime /maxRequestLength:35000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpsBinding'].maxReceivedMessageSize:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpBinding'].maxReceivedMessageSize:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpsBinding'].readerQuotas.maxStringContentLength:35000000
    %windir%\system32\inetsrv\appcmd.exe set config "Exchange Back End/owa/" -section:system.serviceModel/bindings /webHttpBinding.[name='httpBinding'].readerQuotas.maxStringContentLength:35000000

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie müssen eine Testnachricht an ein und von einem Postfach senden, auf das durch den betroffenen Client zugegriffen wird, um sicherzustellen, dass Sie die clientspezifische Nachrichtengrößenbegrenzung erfolgreich konfiguriert haben. Sie können versuchen, einige kleinere Anlagen oder eine große Anlage anzuhängen, sodass die Größe der Testnachricht ca. 33 % unter dem konfigurierten Wert liegt. Wenn der konfigurierte Wert beispielsweise 85 MB beträgt, liegt die maximale Nachrichtengröße in Wirklichkeit bei ca. 64 MB.

