---
title: 'SCL-Schwellenwert: Exchange 2013 Help'
TOCTitle: SCL-Schwellenwert
ms:assetid: 0009b4af-be6d-41d2-98bc-b5487272c74a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995744(v=EXCHG.150)
ms:contentKeyID: 50474919
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# SCL-Schwellenwert

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-11-17_


> [!NOTE]
> Am 1. November 2016 hat Microsoft die Generierung von Spamdefinitionsupdates für die SmartScreen-Filter in Exchange und Outlook eingestellt. Die vorhandenen SmartScreen-Spamdefinitionen bleiben bestehen, ihre Effektivität wird aber im Laufe der Zeit wahrscheinlich abnehmen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=835894">Deprecating support for SmartScreen in Outlook and Exchange</A>.



In Microsoft Exchange Server 2013 können Sie bestimmte Aktionen gemäß den Schwellenwerten der SCL-Bewertung (Spam Confidence Level) definieren. Sie können z. B. verschiedene Schwellenwerte für das Zurückweisen, Löschen oder Verschieben von Nachrichten in den Quarantäneordner auf einem Exchange-Server definieren, auf dem der Inhaltsfilter-Agent ausgeführt wird.

Die Kombination dieser SCL-Schwellenwertkonfiguration im Inhaltsfilter-Agent und in der Konfiguration des SCL-Junk-E-Mail-Ordners für das Benutzerpostfach unterstützt Sie beim Implementieren einer umfassenderen und genaueren Antispamstrategie. Diese genauere und ausführlichere SCL-Schwellenwertanpassungsfunktion in Exchange 2013 kann Sie dabei unterstützen, die Gesamtkosten der Bereitstellung und Verwaltung einer Antispamlösung innerhalb der gesamten Exchange-Organisation zu verringern.

Der Inhaltsfilter-Agent weist zu einem späten Zeitpunkt im Antispamzyklus eine SCL-Bewertung für Nachrichten zu, nachdem andere Antispam-Agents eingehende Nachrichten verarbeitet haben. Viele der anderen Antispam-Agents, die eingehende Nachrichten verarbeiten, bevor diese vom Inhaltsfilter-Agent verarbeitet werden, sind deterministisch hinsichtlich der Aktionen für eine Nachricht. Der Verbindungsfilter-Agent auf einem Edge-Transport-Server weist z. B. alle Nachrichten zurück, die von einer in einer Echtzeit-Sperrliste enthaltenen IP-Adresse gesendet wurden. Der Absenderfilter-Agent und der Empfängerfilter-Agent verarbeiten Nachrichten auf eine ähnlich deterministische Weise.

In Exchange 2013 verarbeiten diese deterministischen Antispam-Agents Nachrichten zuerst und verringern so die Anzahl der Nachrichten erheblich, die vom Inhaltsfilter-Agent verarbeitet werden müssen. Weitere Informationen zur Reihenfolge, in der Antispam-Agents Nachrichten verarbeiten, finden Sie unter [Antispamschutz](anti-spam-protection-exchange-2013-help.md).

Da es sich bei der Inhaltsfilterung nicht um einen genauen, deterministischen Vorgang handelt, ist die Möglichkeit, die vom Inhaltsfilter-Agent für verschiedene SCL-Werte ausgeführte Aktion anpassen zu können, von großer Bedeutung. Durch sorgfältiges Anpassen der SCL-Schwellenwertkonfiguration können Sie Folgendes minimieren:

  - Die Größe des Speicherorts für Spamquarantäne

  - Die Anzahl von legitimen E-Mails, die fälschlicherweise unter Quarantäne gestellt werden

  - Die Anzahl von legitimen E-Mails, die in den Junk-E-Mail-Ordner des Benutzers in Microsoft Outlook verschoben wurden

  - Die Anzahl von unerwünschten Spam-E-Mails, die im Outlook-Posteingang des Benutzers eingehen oder in den Junk-E-Mail-Ordner verschoben wurden

  - Die Anzahl von unerwünschten Spam-E-Mails, die im Outlook-Posteingang des Benutzers eingehen

## SCL-Schwellenwertaktionen

Durch Anpassen der SCL-Schwellenwertaktionen können Sie die Inhaltsfilteraktion eskalieren, die für Nachrichten ausgeführt wird, bei denen ein höheres Risiko besteht, dass es sich um Spam handelt. Zum Verständnis dieser Funktion ist es hilfreich, die verschiedenen SCL-Schwellenwertaktionen sowie deren Implementierung zu verstehen:

  - **SCL-Schwellenwert zum Löschen**   Wenn der SCL-Wert für eine bestimmte Nachricht größer oder gleich dem SCL-Schwellenwert zum Löschen ist, löscht der Inhaltsfilter-Agent die Nachricht. Es findet keine Kommunikation auf Protokollebene statt, die das sendende System oder den Absender informiert, dass die Nachricht gelöscht wurde. Wenn der SCL-Wert für eine Nachricht kleiner als der SCL-Schwellenwert zum Löschen ist, löscht der Inhaltsfilter-Agent die Nachricht nicht. In diesem Fall vergleicht der Inhaltsfilter-Agent den SCL-Wert mit dem SCL-Zurückweisungsschwellenwert.

  - **SCL-Zurückweisungsschwellenwert**   Wenn der SCL-Wert für eine bestimmte Nachricht größer oder gleich dem SCL-Zurückweisungsschwellenwert ist, löscht der Inhaltsfilter-Agent die Nachricht und sendet eine Zurückweisungsantwort an das sendende System. Sie können die Zurückweisungsantwort anpassen. In einigen Fällen wird ein Unzustellbarkeitsbericht an den ursprünglichen Absender der Nachricht gesendet. Wenn der SCL-Wert für eine Nachricht kleiner ist als die SCL-Schwellenwerte zum Löschen und zum Zurückweisen, wird die Nachricht nicht vom Inhaltsfilter-Agent gelöscht oder zurückgewiesen. In diesem Fall vergleicht der Inhaltsfilter-Agent den SCL-Wert mit dem SCL-Quarantäneschwellenwert.

  - **SCL-Quarantäneschwellenwert**   Wenn der SCL-Wert für eine bestimmte Nachricht größer oder gleich dem SCL-Quarantäneschwellenwert ist, sendet der Inhaltsfilter-Agent die Nachricht an ein Quarantänepostfach. E-Mail-Administratoren müssen das Quarantänepostfach regelmäßig überprüfen. Wenn der SCL-Wert für eine Nachricht kleiner ist als die SCL-Schwellenwerte zum Löschen, zum Zurückweisen und zum unter Quarantäne stellen, wird die Nachricht vom Inhaltsfilter-Agent weder gelöscht, noch zurückgewiesen oder unter Quarantäne gestellt. In diesem Fall sendet der Inhaltsfilter-Agent die Nachricht an den entsprechenden Postfachserver, auf dem der pro Empfänger geltende SCL-Schwellenwert des Junk-E-Mail-Ordners für die Nachricht ausgewertet wird.

  - **SCL-Schwellenwert des Junk-E-Mail-Ordners**   Wenn der SCL-Wert für eine bestimmte Nachricht den SCL-Schwellenwert des Junk-E-Mail-Ordners überschreitet, wird die Nachricht in den Junk-E-Mail-Ordner des Benutzers verschoben. Wenn der SCL-Wert für eine Nachricht kleiner als die SCL-Schwellenwerte für das Löschen, Zurückweisen und Verschieben von Nachrichten in den Quarantäneordner oder in den Junk-E-Mail-Ordner ist, geht die Nachricht im Posteingang des Benutzers ein.

Der Inhaltsfilter-Agent und der Junk-E-Mail-Ordner verarbeiten den SCL-Schwellenwert auf unterschiedliche Weise. Der Inhaltsfilter-Agent verarbeitet den von Ihnen konfigurierten Wert für den SCL-Schwellenwert. Im Junk-E-Mail-Ordner wird der von Ihnen konfigurierte Wert für den SCL-Schwellenwert plus 1 verarbeitet. Wenn Sie beispielsweise für den Löschvorgang im Inhaltsfilter-Agent einen SCL von 8 konfigurieren, werden alle Nachrichten mit einem SCL von 8 oder höher gelöscht. Wenn Sie den Junk-E-Mail-Ordner jedoch mit einem SCL-Schwellenwert von 4 konfigurieren, werden alle Nachrichten mit einem SCL von 5 oder höher in den Junk-E-Mail-Ordner verschoben.

Wenn Sie den SCL-Schwellenwert zum Löschen z. B. auf 8, den SCL-Zurückweisungsschwellenwert auf 7, den SCL-Quarantäneschwellenwert auf 6 und den SCL-Schwellenwert des Junk-E-Mail-Ordners auf 4 festlegen, werden alle E-Mails mit einem SCL-Wert von 5 oder niedriger an das Benutzerpostfach übermittelt. Nachrichten mit einem SCL-Wert von 5 werden in den Junk-E-Mail-Ordner des Benutzers verschoben. Nachrichten mit einem SCL-Wert von 4 oder niedriger gehen im Posteingang des Benutzers ein.

Die SLC-Einstellungen für das Löschen, Zurückweisen und Verschieben von Nachrichten in den Quarantäneordner oder in den Junk-E-Mail-Ordner können an den folgenden Stellen konfiguriert werden:

  - **In der Konfiguration des Inhaltsfilter-Agent (SCL-Konfiguration pro Transportserver)**   Verwenden Sie das Cmdlet **Set-ContentFilterConfig**, um die SCL-Schwellenwerte für das Löschen, Zurückweisen und Verschieben von Nachrichten in den Quarantäneordner auf dem Exchange-Server, auf dem der Inhaltsfilter-Agent ausgeführt wird, zu aktivieren, zu deaktivieren oder festzulegen. Nachdem Sie die Spamfunktionen und -messgrößen analysiert haben, die von den Antispamprotokollierungs- und -Berichtsfunktionen bereitgestellt werden, können Sie nach Bedarf weitere Anpassungen an diesen SCL-Schwellenwertkonfigurationen vornehmen.
    
    In der folgenden Tabelle sind die SCL-Parameter beschrieben, die mit dem Cmdlet **Set-ContentFilterConfig** verwendet werden können.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Parameter</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><em>SCLDeleteEnabled</em></p></td>
    <td><p>Mit diesem Parameter wird das Löschen einer Nachricht ohne Unzustellbarkeitsbericht aktiviert oder deaktiviert, wenn der SCL-Wert größer ist als der über den Parameter <em>SCLDeleteThreshold</em> angegebene Wert bzw. diesem Wert entspricht. Gültige Eingaben für diesen Parameter sind <code>$true</code> oder <code>$false</code>.</p></td>
    </tr>
    <tr class="even">
    <td><p><em>SCLDeleteThreshold</em></p></td>
    <td><p>Eine gültige Eingabe für diesen Parameter ist eine ganze Zahl von 0 bis einschließlich 9. Der Wert dieses Parameters sollte größer sein als die anderen SCL-Schwellenwertparameter. Dieser Parameter kann nur dann verwendet werden, wenn der Parameter <em>SCLDeleteEnabled</em> den Wert <code>$true</code> aufweist.</p></td>
    </tr>
    <tr class="odd">
    <td><p><em>SCLRejectEnabled</em></p></td>
    <td><p>Mit diesem Parameter wird das Zurückweisen einer Nachricht mit Unzustellbarkeitsbericht aktiviert oder deaktiviert, wenn der SCL-Wert größer ist als der über den Parameter <em>SCLRejectThreshold</em> angegebene Wert bzw. diesem Wert entspricht. Gültige Eingaben für diesen Parameter sind <code>$true</code> oder <code>$false</code>.</p></td>
    </tr>
    <tr class="even">
    <td><p><em>SCLRejectThreshold</em></p></td>
    <td><p>Eine gültige Eingabe für diesen Parameter ist eine ganze Zahl von 0 bis einschließlich 9. Der Wert dieses Parameters sollte geringer sein als der Wert des Parameters <em>SCLDeleteThreshold</em>, jedoch größer als die anderen SCL-Schwellenwertparameter. Dieser Parameter ist nur von Bedeutung, wenn der Parameter <em>SCLRejectEnabled</em> auf <code>$true</code> festgelegt ist.</p></td>
    </tr>
    <tr class="odd">
    <td><p><em>SCLQuarantineEnabled</em></p></td>
    <td><p>Mit diesem Parameter wird das Senden von Nachrichten an das Quarantänepostfach für Spam aktiviert oder deaktiviert, wenn der SCL-Wert größer ist als der über den Parameter <em>SCLQuarantineThreshold</em> angegebene Wert bzw. diesem Wert entspricht. Gültige Eingaben für diesen Parameter sind <code>$true</code> oder <code>$false</code>.</p>
    <p>Weitere Informationen zum Spam-Quarantänepostfach finden Sie unter <a href="spam-quarantine-exchange-2013-help.md">Quarantänepostfach für Spam</a>.</p></td>
    </tr>
    <tr class="even">
    <td><p><em>SCLQuarantineThreshold</em></p></td>
    <td><p>Eine gültige Eingabe für diesen Parameter ist eine ganze Zahl von 0 bis einschließlich 9. Der Wert dieses Parameters sollte geringer sein als der Wert des Parameters <em>SCLRejectThreshold</em>, jedoch größer als der Parameter <em>SCLJunkThreshold</em> für das Cmdlet <strong>Set-OrganizationConfig</strong> oder <strong>Set-Mailbox</strong>. Dieser Parameter kann nur dann verwendet werden, wenn der Parameter <em>SCLQuarantineThreshold</em> den Wert <code>$true</code> aufweist.</p></td>
    </tr>
    </tbody>
    </table>


  - **In den Konfigurationseinstellungen der Organisation (organisationsweite SCL-Konfiguration)**   Verwenden Sie das Cmdlet **Set-OrganizationConfig**, um den SCL-Schwellenwert des Junk-E-Mail-Ordners für alle Postfächer in der Organisation festzulegen.
    
    In der folgenden Tabelle ist der SCL-Parameter beschrieben, der mit dem Cmdlet **Set-OrganizationConfig** verwendet werden kann. Weitere Informationen zur Verwendung von SCLJunkThreshold finden Sie unter [Konfigurieren von Antispameinstellungen für Postfächer](configure-anti-spam-settings-on-mailboxes-exchange-2013-help.md).
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Parameter</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><em>SCLJunkThreshold</em></p></td>
    <td><p>Dieser Parameter gibt den SCL-Wert an, den eine Nachricht überschreiten muss, um in den Junk-E-Mail-Ordner des Empfängerpostfachs verschoben zu werden. Eine gültige Eingabe für diesen Parameter ist eine ganze Zahl von 0 bis einschließlich 9. Der Wert dieses Parameters sollte geringer sein als die anderen SCL-Schwellenwertparameter. Wenn Sie z. B. den Wert 4 festlegen, werden Nachrichten mit einem SCL-Wert von 5 oder mehr in den Junk-E-Mail-Ordner des Benutzers verschoben.</p></td>
    </tr>
    </tbody>
    </table>


  - **Für Benutzerpostfächer (SCL-Konfiguration pro Empfänger)**   Verwenden Sie das Cmdlet **Set-Mailbox**, um SCL-Schwellenwerte für das Löschen, Zurückweisen und Verschieben von Nachrichten in den Quarantäneordner oder in den Junk-E-Mail-Ordner für einzelne Benutzer zu aktivieren, zu deaktivieren und festzulegen. Mit dem Cmdlet **Set-Mailbox** kann der SCL-Schwellenwert des Junk-E-Mail-Ordners nur für einzelne Postfächer aktiviert oder deaktiviert werden. Die pro Empfänger festgelegten SCL-Schwellenwerte für das Löschen, Zurückweisen und Verschieben von Nachrichten in den Quarantäneordner werden in Active Directory gespeichert und durch den Microsoft Exchange EdgeSync-Dienst auf die abonnierten Edge-Transport-Server repliziert. Die pro Empfänger vorgenommenen SCL-Schwellenwertkonfigurationen werden vom Inhaltsfilter-Agent selbst dann verwendet, wenn Sie SCL-Konfigurationen pro Transport-Servercomputer festgelegt haben. Wenn Sie SCL-Schwellenwerte pro Empfänger festgelegt haben, verwendet der Inhaltsfilter-Agent daher die pro Empfänger festgelegten SCL-Schwellenwerte für bestimmte Benutzer statt der SCL-Konfiguration für den Inhaltsfilter-Agent. Beispiele finden Sie unter [Konfigurieren von Antispameinstellungen für Postfächer](configure-anti-spam-settings-on-mailboxes-exchange-2013-help.md).
    

    > [!NOTE]
    > SCL-Schwellenwerte pro Empfänger werden nicht für E-Mail-Nachrichten erzwungen, die über Verteilergruppen empfangen wurden.

    
    Für das Cmdlet **Set-Mailbox** können dieselben SCL-Parameter verwendet werden wie für das Cmdlet **Set-ContentFilterConfig** und **Set-OrganizationConfig**:
    
      - *SCLDeleteEnabled*
    
      - *SCLDeleteThreshold*
    
      - *SCLRejectEnabled*
    
      - *SCLRejectThreshold*
    
      - *SCLQuarantineEnabled*
    
      - *SCLQuarantineThreshold*
    
      - *SCLJunkThreshold*
    
    Für alle SCL-Parameter des Cmdlets **Set-Mailbox** kann jedoch auch der Wert `$null` angegeben werden. Wenn eine SCL-Einstellung für ein Postfach leer ist (`$null`), wird die entsprechende Einstellung des Inhaltsfilter-Agents oder die Konfigurationseinstellung der Organisation auf das Postfach angewendet. Wenn für die SCL-Einstellung eines Postfachs der Wert `$true` oder `$false` festgelegt ist, setzt die Postfacheinstellung die entsprechende organisationsweite Einstellung für den Inhaltsfilter-Agent oder die Organisationskonfiguration außer Kraft.
    
    In der folgenden Tabelle ist der SCL-Parameter beschrieben, der ausschließlich mit dem Cmdlet **Set-Mailbox** verwendet werden kann.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Parameter</th>
    <th>Beschreibung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><em>SCLJunkEnabled</em></p></td>
    <td><p>Mit diesem Parameter wird die Zustellung einer Nachricht an den Junk-E-Mail-Ordner eines Benutzers aktiviert oder deaktiviert, wenn der SCL-Wert der Nachricht größer ist als der über den Parameter <em>SCLQuarantineThreshold</em> angegebene Wert. Die gültige Eingabe für diesen Parameter ist <code>$true</code>, <code>$false</code> oder <code>$null</code>.</p>
    <p>Beachten Sie, dass die Junk-E-Mail-Filterung standardmäßig für alle Postfächer in der Organisation aktiviert ist. Der Parameter <em>Enabled</em> des Cmdlets <strong>Set-MailboxJunkEmailConfiguration</strong> ist standardmäßig für alle Benutzerpostfächer auf <code>$true</code> festgelegt.</p></td>
    </tr>
    </tbody>
    </table>
    
    Weitere Informationen zur Konfiguration der SCL-Schwellenwerte für ein Postfach finden Sie unter [Konfigurieren von Antispameinstellungen für Postfächer](configure-anti-spam-settings-on-mailboxes-exchange-2013-help.md).

## Überwachen der SCL-Schwellenwerte

Zum Erfassen von Filterergebnisdaten können Sie verschiedene integrierte Skripts verwenden, die sich im Ordner `%ExchangeInstallPath%Scripts` befinden (z. B. **get-AntispamSCLHistogram.ps1**). Wenn die Daten anzeigen, dass sofortige Anpassungen erforderlich sind, konfigurieren Sie die SCL-Schwellenwerte erneut. Erfassen Sie andernfalls die Daten, und analysieren Sie die Spamberichte, damit Sie bestimmen können, ob Anpassungen erforderlich sind.

