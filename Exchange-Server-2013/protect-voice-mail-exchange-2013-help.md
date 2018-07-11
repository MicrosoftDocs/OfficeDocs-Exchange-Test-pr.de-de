---
title: 'Schützen von Voicemail: Exchange 2013 Help'
TOCTitle: Schützen von Voicemail
ms:assetid: a88d41d5-2e70-4193-bcd3-dec50dff412b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd351041(v=EXCHG.150)
ms:contentKeyID: 52062798
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Schützen von Voicemail

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Einige ältere Nebenstellenanlagen und IP-Nebenstellenanlagen ermöglichen dem Anrufer, eine Voicemailnachricht als privat zu kennzeichnen, wodurch der vorgesehene Empfänger der Nachricht daran gehindert wird, die Nachricht beim Abhören an andere Personen weiterzuleiten. In integrierten Voicemailsystemen kann auf eine Sprachnachricht in verschiedener Weise zugegriffen werden. Dies erschwert es, als privat gekennzeichnete Sprachnachrichten vor einem Zugriff durch nicht autorisierte Personen zu schützen.

Unified Messaging (UM) kann zur Verwendung der Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS) konfiguriert werden, um Sprachnachrichten für eine Organisation zu schützen. Diese Funktion wird als geschützte Voicemail bezeichnet.

Wenn eine Sprachnachricht geschützt ist, kann der Empfänger die Nachricht nicht weiterleiten. Darüber hinaus wird über Unified Messaging (UM) sichergestellt, dass nur der vorgesehene Empfänger der Nachricht auf deren Inhalte zugreifen kann. Auf geschützte Sprachnachrichten kann mithilfe von MicrosoftOutlook 2010 oder höher, Outlook Web App und Outlook Voice Access zugegriffen werden.

**Inhalt**

Übersicht über geschützte Voicemail

Übersicht über die Active Directory-Rechteverwaltungsdienste

Clientunterstützung und Endbenutzerfunktionen

Struktur einer geschützten Sprachnachricht

Verfassen einer geschützten Voicemailnachricht

UM-Postfachrichtlinien

SMS-Benachrichtigungen und geschützte Voicemail

## Übersicht über geschützte Voicemail

Die Funktion für geschützte Voicemail ist mit Exchange 2010 Unified Messaging (UM) und höheren Versionen verfügbar. Die Funktion kann für eine UM-Postfachrichtlinie konfiguriert werden. Alle Einstellungen für geschützte Voicemail können über die Exchange-Verwaltungskonsole oder Shell in Exchange 2010 oder über die Exchange-Verwaltungskonsole oder Cmdlets in der Shell von Exchange 2013 konfiguriert werden.

Die Funktionalität für geschützte Voicemail wird durch Aktivierung von IRM (Information Rights Management, Verwaltung von Informationsrechten) für Sprachnachrichten implementiert. Für UM-geschützte Sprachnachrichten gilt Folgendes:

  - Benutzer können auf geschützte Sprachnachrichten antworten.

  - Empfänger einer Sprachnachricht können diese nicht weiterleiten.

  - Benutzer können keine Kopie der Sprachnachricht speichern.

  - Benutzer können die angehängte Audiodatei der Sprachnachricht weder speichern noch kopieren.

  - Eine Sprachnachricht kann nur von den vorgesehen Empfängern geöffnet werden.

Sowohl Sprachnachrichten für Mailboxansagen als auch Sprachnachrichten zwischen Benutzern (Sprachnachrichten, die über Outlook Voice Access an einen Benutzer gesendet werden) können von UM geschützt werden. Der Schutz erstreckt sich jedoch nicht auf folgende Nachrichtentypen:

  - Faxnachrichten.

  - Nicht-Sprachnachrichten. Hierzu gehören beispielsweise E-Mail-Nachrichten oder Besprechungsanfragen, selbst wenn diese mit Outlook Voice Access erstellt werden (Sprachantworten).

Zurück zum Seitenanfang

## Übersicht über die Active Directory-Rechteverwaltungsdienste

Die Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS) sind eine Komponente von Windows Server 2008 und höheren Versionen. Mithilfe von AD RMS können Dateien geschützt werden, sodass sie nur von den Benutzern angezeigt werden können, für die sie bestimmt sind. AD RMS schützt eine Datei, indem die Rechte festgelegt werden, die ein Benutzer für den Zugriff auf die Datei benötigt. Rechte können so konfiguriert werden, dass ein Benutzer die durch Rechte verwalteten Informationen öffnen, ändern, drucken oder weiterleiten bzw. andere Aktionen ausführen kann. Mit AD RMS können Sie Daten schützen, die außerhalb Ihres Netzwerks verteilt werden.

Ein AD RMS-System verfügt über eine Server- und eine Clientkomponente, darunter:

  - Ein Server, auf dem Windows Server 2008 R2 oder eine höhere Version installiert ist und auf dem die Active Directory-Serverrolle "Rechteverwaltungsdienste" ausgeführt wird, die für Zertifikate und Lizenzierung zuständig ist.

  - Ein Datenbankserver.

  - Der AD RMS-Client. Die neueste Version des AD RMS-Clients gehört zum Lieferumfang der Betriebssysteme Windows 7 und Windows 8.

Die Serverkomponente umfasst verschiedene Webdienste, die auf einem Microsoft-Server mit beispielsweise Windows Server 2008 oder höher ausgeführt werden. Die Clientkomponente kann entweder auf einem Client- oder auf einem Serverbetriebssystem ausgeführt werden und umfasst Funktionen, die einer Anwendung das Ver- und Entschlüsseln von Inhalten, das Abrufen von Vorlagen und Sperrlisten sowie das Anfordern von Lizenzen und Zertifikaten von einem Server ermöglichen.

Durch Verwendung von AD RMS und dem AD RMS-Client können Sie die Sicherheit in einer Organisation verbessern, indem Informationen dauerhaft mit Verwendungsrichtlinien verknüpft werden – unabhängig davon, wohin die Daten verschoben werden. Mithilfe von AD RMS können Sie verhindern, dass vertrauliche Informationen – z. B. Finanzberichte, Produktspezifikationen, Kundendaten sowie vertrauliche E-Mail- und Voicemailnachrichten – absichtlich oder versehentlich in die falschen Hände gelangen. Ausführliche Informationen finden Sie unter [Übersicht über AD RMS](https://go.microsoft.com/fwlink/p/?linkid=199436).

In Exchange UM können Sie mithilfe der Funktionen zur Verwaltung von Informationsrechten (IRM) Nachrichten und Anlagen dauerhaft schützen.

Durch Einsatz der IRM-Funktionen und Verwendung von geschützter Voicemail können Ihre Organisation und Benutzer die Rechte steuern, die Empfänger in Bezug auf den Zugriff auf E-Mail- und Voicemailnachrichten gewährt werden. Mit IRM können außerdem Aktionen der Empfänger, wie beispielsweise das Weiterleiten einer Nachricht an andere Empfänger, das Drucken einer Nachricht oder einer Anlage oder das Extrahieren von Nachrichteninhalten oder Anlagen mittels Kopieren und Einfügen, zugelassen oder eingeschränkt werden.

## IRM-Anforderungen

Bevor Sie IRM in Exchange implementieren können, müssen Sie zunächst Ihre AD RMS-Infrastruktur bereitstellen und konfigurieren. Ausführliche Informationen finden Sie unter [Active Directory-Rechteverwaltungsdienste](https://go.microsoft.com/fwlink/p/?linkid=199439). Damit IRM so implementiert werden kann, dass geschützte Voicemail in Ihrer Exchange-Organisation unterstützt wird, muss Ihre Bereitstellung die folgenden Anforderungen erfüllen.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Server</th>
<th>Anforderung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AD RMS-Cluster</p></td>
<td><ul>
<li><p>Windows Server 2008 R2 Standard oder Enterprise mit SP1 oder Windows Server 2012 Standard oder Datacenter. Weitere Informationen zu den Systemvoraussetzungen finden Sie unter <a href="exchange-2013-system-requirements-exchange-2013-help.md">Exchange 2013 – Systemanforderungen</a>.</p></li>
<li><p><strong>Dienstverbindungspunkt (Service Connection Point, SCP)</strong>   Exchange 2013 und AD RMS-fähige Anwendungen verwenden für die Erkennung von AD RMS-Clustern und URLs den in Active Directory registrierten Dienstverbindungspunkt. AD RMS ermöglicht die Registrierung der Dienstverbindungspunkte während des AD RMS-Setups. Wenn das zum Einrichten von AD RMS verwendete Konto nicht zur Sicherheitsgruppe <strong>Organisations-Admins</strong> gehört, kann die Registrierung des Dienstverbindungspunkts nach dem Setup vorgenommen werden. Es gibt nur einen Dienstverbindungspunkt für AD RMS in einer Active Directory-Gesamtstruktur.</p></li>
<li><p><strong>Berechtigungen</strong>   Servern in den Exchange-Servergruppen oder einzelne Exchange-Server müssen für die AD RMS-Serverzertifizierungspipeline die Berechtigungen <strong>Lesen</strong> und <strong>Ausführen</strong> zugewiesen werden. Der Standardpfad auf AD RMS-Servern ist <strong>\inetpub\wwwroot\_wmcs\certification\ServerCertification.asmx</strong>.</p></li>
<li><p><strong>AD RMS-Administratoren</strong>   Wenn Sie die Transportentschlüsselung, die Journalberichtentschlüsselung, IRM in Outlook Web App und IRM für Exchange-Suche aktivieren möchten, müssen Sie der Administratorengruppe des AD RMS-Clusters das Verbundzustellungspostfach (Federated Delivery Mailbox) hinzufügen. Dabei handelt es sich um ein Systempostfach, das von Exchange Setup erstellt wird. Ausführliche Informationen finden Sie unter <a href="add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md">Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe</a>.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Konfigurieren und Testen von IRM

Zum Konfigurieren der IRM-Funktionen müssen Sie die Shell verwenden. Mit dem Cmdlet [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)) können Sie einzelne IRM-Funktionen konfigurieren. Weitere Informationen zum Konfigurieren von IRM-Funktionen finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

Nach dem Einrichten eines Exchange-Servers können Sie mithilfe des Cmdlets [Test-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979798\(v=exchg.150\)) umfassende Tests Ihrer IRM-Bereitstellung ausführen. Dieses Cmdlet überprüft die IRM-Konfiguration für eine Organisation und sollte ausgeführt werden, bevor Sie die Funktion für geschützte Voicemail aktivieren. Mit dem Cmdlet **Test-IRMConfiguration** werden die folgenden Tests durchgeführt:

  - Überprüfen der IRM-Konfiguration für Ihre Exchange-Organisation.

  - Überprüfen des AD RMS-Servers auf Versions- und Hotfixinformationen.

  - Abrufen eines Rechtekontozertifikats (RAC) und eines Client-Lizenzgeberzertifikats (CLC), um zu prüfen, ob für RMS ein Exchange-Server aktiviert werden kann.

  - Abrufen von AD RMS-Vorlagen für Benutzerrechterichtlinien vom AD RMS-Server.

  - Überprüfen, ob der angegebene Absender IRM-geschützte Nachrichten senden kann.

  - Abrufen einer Administratornutzungslizenz für den angegebenen Empfänger.

  - Abrufen einer Vorlizenz für den angegebenen Empfänger.

Zurück zum Seitenanfang

## Clientunterstützung und Endbenutzerfunktionen

Die E-Mail-Clientsoftware, die zum Abhören einer geschützten Voicemailnachricht verwendet wird, muss IRM unterstützen und eine UM-geschützte Sprachnachricht lesen können. Zu den unterstützten E-Mail-Clients gehören beispielsweise MicrosoftOutlook 2010 und höhere Versionen, Outlook Web App und Outlook Voice Access. Die folgende Tabelle enthält eine Liste von E-Mail-Clients sowie Informationen dazu, ob diese unterstützt werden oder nicht.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>E-Mail-Client</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook</p></td>
<td><ul>
<li><p>Geschützte Sprachnachrichten werden nur in Outlook 2010 und späteren Versionen unterstützt.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook Web App</p></td>
<td><ul>
<li><p>Outlook Web App in Exchange 2010 und späteren Versionen unterstützt geschützte Voicemailnachrichten. Frühere Versionen von Outlook Web App mit dem Namen Outlook Web Access bieten keine Unterstützung.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook Voice Access</p></td>
<td><ul>
<li><p>Outlook Voice Access in Exchange 2010 und späteren Versionen unterstützt geschützte Voicemail. Die in Exchange 2007 enthaltene Version von Outlook Voice Access bietet keine Unterstützung für geschützte Voicemail.</p></li>
<li><p>Das Benutzerpostfach muss sich auf einem Postfachserver in Exchange 2010 oder einer späteren Version befinden.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Windows Mobile oder Windows Phone</p></td>
<td><ul>
<li><p>Windows Mobile bietet keine Unterstützung für geschützte Voicemail. Allerdings unterstützen Windows Phone 7 und Windows Phone 8 geschützte Voicemail.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange ActiveSync</p></td>
<td><ul>
<li><p>Geschützte Voicemail wird in Exchange 2010 SP1 und höheren Versionen unterstützt.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Andere E-Mail-Clients</p></td>
<td><ul>
<li><p>Keine Unterstützung für geschützte Voicemail.</p></li>
</ul></td>
</tr>
</tbody>
</table>


Zurück zum Seitenanfang

## Struktur einer geschützten Sprachnachricht

Jede geschützte Voicemailnachricht umfasst tatsächlich zwei Nachrichten. Die erste ist die äußere Nachricht, diese ist nicht verschlüsselt. Sie enthält eine Anlage namens "message.rpmsg". Die Anlage enthält die IRM-geschützte Sprachnachricht sowie Daten zur Steuerung der internen Rechteverwaltung. Die Daten zur Steuerung der Rechteverwaltung umfassen einen Inhaltsschlüssel sowie Rechteinformationen. Diese geben an, welche Benutzer auf die Sprachnachricht zugreifen können und in welcher Weise der Zugriff erfolgen kann.

Geschützte Sprachnachrichten werden im Suchordner **Voicemail** im Posteingang des Benutzers angezeigt. Der Benutzer kann die Sprachnachrichten mit dem eingebetteten Audioplayer abhören, ebenso wie eine reguläre Sprachnachricht abgehört wird. Bei der Wiedergabe einer geschützten Sprachnachricht ist allerdings die Schaltfläche zum Weiterleiten deaktiviert, und es wird im oberen Bereich der Nachricht ein Hinweis angezeigt, dass die Nachricht geschützt ist und nicht weitergeleitet werden kann.

Bei E-Mail-Clients, die geschützte Voicemail nicht unterstützen, wird der Text der äußeren Nachricht angezeigt. Administratoren können mithilfe von UM-Postfachrichtlinien Text hinzufügen, wenn die Software des Clients geschützte Voicemail nicht unterstützt. Sie können den Standardtext in der E-Mail-Nachricht durch Konfigurieren einer UM-Postfachrichtlinie anpassen. Beispielsweise können Sie die UM-Postfachrichtlinie mit dem folgenden angepassten Text konfigurieren: *"Sie können diese Sprachnachricht nicht öffnen, da sie geschützt ist. Melden Sie sich zum Abhören dieser Sprachnachricht bei Ihrem Postfach unter "https://mail.contoso.com" an, oder wählen Sie +1 (425) 555-1234, um sich bei Outlook Voice Access anzumelden."*

Zurück zum Seitenanfang

## Verfassen einer geschützten Voicemailnachricht

Es gibt zwei Situationen, in denen geschützte Sprachnachrichten erstellt werden können:

  - **Mailboxansage**   Eine Mailboxansage tritt auf, wenn ein Anrufer einen UM-aktivierten Benutzer anruft, dieser den Anruf jedoch nicht entgegennehmen kann und der Anruf direkt an die zugehörige Mailbox weitergeleitet wird. In einem solchen Szenario spielt das Voicemailsystem verschiedene Ansagen ab, nachdem der Anrufer eine Sprachnachricht aufgezeichnet hat.
    
    Der Anrufer kann aus verschiedenen zusätzlichen Nachrichtenoptionen wählen und die Sprachnachricht beispielsweise durch Drücken der Rautetaste (\#) als privat kennzeichnen. Wenn der Anrufer die Rautetaste (\#) betätigt, kann die Nachricht gemäß den UM-Anweisungen als privat gekennzeichnet, eine solche Kennzeichnung aufgehoben oder die Sprachnachricht als wichtig gekennzeichnet werden. Das folgende Diagramm zeigt die Menüoptionen, die Anrufern zur Verfügung stehen, wenn sie eine private Sprachnachricht für einen Benutzer hinterlassen.
    

    > [!NOTE]
    > Bei Mailboxansagen werden von Unified Messaging die in der UM-Postfachrichtlinie des vorgesehenen Empfängers festgelegten Einstellungen für geschützte Voicemail verwendet, da der Anrufer nicht authentifiziert ist.

    
    **Erstellen einer geschützten Voicemail über eine Mailboxansage**
    
    ![Erstellen geschützter Voicemail unter Verwendung von Mailboxansagen](images/Dd351041.4e9f50bf-5066-4d0a-b3eb-0515a2fc4560(EXCHG.150).jpg "Erstellen geschützter Voicemail unter Verwendung von Mailboxansagen")  

  - **Outlook Voice Access**   Outlook Voice Access ermöglicht UM-aktivierten Benutzern den Zugriff auf ihr Postfach über analoge, digitale oder Mobiltelefone, indem sie ihre Outlook Voice Access-Nummer wählen. UM-aktivierten Benutzern stehen zwei Unified Messaging-Schnittstellen zur Verfügung: die Benutzerschnittstelle für Telefoneingabe (Telephone User Interface, TUI) und die Benutzerschnittstelle für Spracheingabe (Voice User Interface, VUI).
    
    Outlook Voice Access-Benutzer können im Verzeichnis nach Kontakten suchen und diesen Kontakten Sprachnachrichten senden. Wenn für die UM-aktivierten Empfänger die Funktion für geschützte Voicemail aktiviert wurde, können Anrufer die Nachrichten nach der Aufzeichnung als privat kennzeichnen. Alternativ können Administratoren eine UM-Postfachrichtlinie konfigurieren um sicherzustellen, dass alle Sprachnachrichten, die von authentifizierten Benutzern gesendet werden, UM-geschützt sind.
    

    > [!NOTE]
    > Wenn es sich um einen authentifizierten Anrufer handelt, werden die in der UM-Postfachrichtlinie festgelegten Einstellungen für geschützte Voicemail angewendet, die mit dem Anrufer verknüpft sind. Dies gilt unabhängig von den UM-Postfachrichtlinieneinstellungen für den vorgesehenen Empfänger der Sprachnachricht.

    
    **Erstellen einer geschützten Voicemailnachricht über die Benutzerschnittstelle für Spracheingabe**
    
    ![Erstellen geschützter Voicemail unter Verwendung der Sprachbenutzerschnittstelle](images/Dd351041.6b425ee4-5171-4a63-961f-bdbc6c79e1be(EXCHG.150).jpg "Erstellen geschützter Voicemail unter Verwendung der Sprachbenutzerschnittstelle")  
    
    **Erstellen einer geschützten Voicemailnachricht über die Benutzerschnittstelle für Telefoneingabe**
    
    ![Erstellen geschützter Voicemail unter Verwendung der Tonwahleingabe](images/Dd351041.dd58fd38-c4c3-437c-adc1-497deb3c8a9f(EXCHG.150).jpg "Erstellen geschützter Voicemail unter Verwendung der Tonwahleingabe")  

Zurück zum Seitenanfang

## UM-Postfachrichtlinien

Sie können eine Unified Messaging-Postfachrichtlinie erstellen, um einen allgemeinen Satz von UM-Richtlinieneinstellungen, z. B. PIN-Richtlinieneinstellungen oder Wähleinschränkungen, auf eine Sammlung von UM-aktivierten Postfächern anzuwenden. Weitere Informationen zu UM-Postfachrichtlinien finden Sie unter [Verwalten einer UM-Postfachrichtlinie](manage-a-um-mailbox-policy-exchange-2013-help.md).

Zum Konfigurieren der Optionen für geschützte Voicemail können Sie die Exchange-Verwaltungskonsole oder das Cmdlet **Set-UMMailboxPolicy** verwenden. In der folgenden Tabelle sind die Einstellungen aufgeführt, die für geschützte Voicemail konfiguriert werden können.

**Einstellungen für geschützte Voicemail**


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Shell-Parameter</th>
<th>Einstellung in der Exchange-Verwaltungskonsole verfügbar?</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ProtectAuthenticatedVoiceMail</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>ProtectAuthenticatedVoiceMail</em> gibt an, ob UM-aktivierte Benutzer geschützte Sprachnachrichten senden können, wenn sie über Outlook Voice Access auf ihr Postfach zugreifen. Die Standardeinstellung lautet <code>None</code>. Dies bedeutet, dass Sprachnachrichten beim Verfassen nicht geschützt werden und Anrufer keine Möglichkeit haben, die Sprachnachrichten als privat zu kennzeichnen. Wenn der Wert auf <code>Private</code> festgelegt ist, werden nur durch den Anrufer als privat gekennzeichnete Nachrichten geschützt. Ist der Wert auf <code>All</code> festgelegt, wird jede Sprachnachricht geschützt – unabhängig von der vom Anrufer gewählten Option.</p></td>
</tr>
<tr class="even">
<td><p><em>ProtectUnauthenticatedVoiceMail</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>ProtectUnauthenticatedVoiceMail</em> gibt an, ob über die Postfachserver, die Anrufe für UM-aktivierte Benutzer mit einer zugeordneten UM-Postfachrichtlinie beantworten, geschützte Sprachnachrichten erstellt werden. Diese Einstellung wird auch angewendet, wenn eine Nachricht von einer automatischen UM-Telefonzentrale an einen UM-aktivierten Benutzer gesendet wird. Die Standardeinstellung lautet <code>None</code>. Dies bedeutet, dass Sprachnachrichten nicht geschützt werden und Anrufer keine Möglichkeit haben, die Nachricht als privat zu kennzeichnen. Wenn der Wert auf <code>Private</code> festgelegt ist, werden nur durch den Anrufer als privat gekennzeichnete Nachrichten geschützt. Ist der Wert auf <code>All</code> festgelegt, wird jede Sprachnachricht geschützt – unabhängig davon, ob die Nachricht vom Anrufer als privat gekennzeichnet wurde.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProtectedVoiceMailText</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>ProtectedVoiceMailText</em> gibt den Text an, der in den Nachrichtenteil der äußeren Nachricht einer geschützten Voicemailnachricht eingeschlossen werden soll. Dieser Text wird in allen E-Mail-Clientanwendungen angezeigt, die keine Unterstützung für geschützte Voicemailnachrichten bieten. Beachten Sie, dass Unified Messaging immer eine Standardnachricht bereitstellt, wenn diese Eigenschaft auf <code>Null</code> festgelegt wurde oder leer ist.</p></td>
</tr>
<tr class="even">
<td><p><em>RequireProtectedPlayOnPhone</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>RequireProtectedPlayOnPhone</em> gibt an, ob der UM-Postfachrichtlinie zugeordnete Benutzer die geschützte Sprachnachricht über das Telefon (mittels Wiedergabe über Telefon) abhören müssen. Der Standardwert lautet <code>$false.</code>. Wenn der Wert auf <code>$true</code> festgelegt ist, wird der Audioplayer in geschützten Voicemailformularen in Outlook oder Outlook Web App als deaktiviert angezeigt. Beachten Sie, dass auf den Vorschautext für die Sprachnachricht immer zugegriffen werden kann. Der Benutzer kann weder die Audiodatei mit einer Media Player-Software abspielen noch den eingebetteten Media Player zum Abhören der Sprachnachricht verwenden.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowVoiceResponseToOtherMessageTypes</em></p></td>
<td><p>Ja</p></td>
<td><p>Der Parameter <em>AllowVoiceResponseToOtherMessageTypes</em> gibt an, ob Anrufer, die sich für den E-Mail-Zugriff bei Outlook Voice Access authentifiziert haben, eine Sprachantwort auf E-Mail-Nachrichten und Besprechungsanfragen verfassen können.</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zum Verwalten von Einstellungen für geschützte Voicemail finden Sie unter [Geschützte Voicemail-Prozeduren](protected-voice-mail-procedures-exchange-2013-help.md) oder [Set-UMMailboxPolicy](https://technet.microsoft.com/de-de/library/bb124903\(v=exchg.150\)).

Zurück zum Seitenanfang

## SMS-Benachrichtigungen und geschützte Voicemail

Benutzer, die ihr UM-Konto so konfiguriert haben, dass beim Empfang von Sprachnachrichten eine Textnachricht (SMS-Benachrichtigung) an ihr Mobiltelefon gesendet wird, empfangen im Nachrichtenteil der Textnachricht zusätzlich eine Audiotranskription (Voicemailvorschau) des Texts. Für geschützte Sprachnachrichten stellt dies jedoch ein Sicherheitsrisiko dar, da der Inhalt von Sprachnachrichten immer geschützt werden sollte.

Wenn Unified Messaging eine Textbenachrichtigung für eine Sprachnachricht erstellt, wird überprüft, ob die Sprachnachricht als privat markiert wurde. In diesem Fall wird der transkribierte Audiotext nicht der Textnachricht hinzugefügt, die an das Mobiltelefon gesendet wird. Stattdessen wird der folgende Text in die Textnachricht eingefügt: "Greifen Sie auf diese geschützte Voicemailnachricht mithilfe von Outlook Voice Access zu."

Zurück zum Seitenanfang

