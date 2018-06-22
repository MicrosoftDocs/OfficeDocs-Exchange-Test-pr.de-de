---
title: 'Berechtigungen in Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Berechtigungen in Exchange-Hybridbereitstellungen
ms:assetid: 58b46b2c-a6b2-424a-8fc2-0f1fe1ad8e18
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ906433(v=EXCHG.150)
ms:contentKeyID: 51406941
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Berechtigungen in Exchange-Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2018-05-02_

Die Organisation mit Exchange Online in Office 365 basiert auf Exchange Server und verwendet, ähnlich wie lokale Organisationen, ebenfalls die rollenbasierte Zugriffssteuerung (Role Based Access Control, RBAC), um Berechtigungen zu steuern. Administratoren werden Berechtigungen über Verwaltungsrollengruppen erteilt, während Endbenutzern Berechtigungen über Zuweisungsrichtlinien für Verwaltungsrollen erteilt werden.

Weitere Informationen zu Berechtigungen in Exchange Online und lokalen Exchange-Bereitstellung finden Sie unter: [Berechtigungen](https://technet.microsoft.com/de-de/library/dd351175\(v=exchg.150\))

## Administratorberechtigungen

Der Benutzer, der zum Erstellen des Office 365-Mandanten verwendet wurde, wird in der Exchange Online-Organisation standardmäßig als Mitglied der Rollengruppe „Organisationsverwaltung\&quot; festgelegt. Dieser Benutzer kann die gesamte Exchange Online-Organisation verwalten, wozu auch die Konfiguration von Einstellungen auf Organisationebene sowie die Verwaltung von Exchange Online-Empfängern gehören.

Abhängig von den anfallenden Verwaltungsaufgaben können Sie der Exchange Online-Organisation weitere Administratoren hinzufügen. Sie können beispielsweise weitere Organisationsadministratoren und Empfängeradministratoren hinzufügen, speziellen Benutzern das Ausführen von Einhaltungsaufgaben z. B. Ermittlung, Konfigurieren von benutzerdefinierten Berechtigungen usw. ermöglichen. Die gesamte Exchange Online-Berechtigungsverwaltung für Office 365-Administratoren muss in der Exchange Online-Organisation über die Exchange-Verwaltungskonsole oder über Remote-PowerShell ausgeführt werden.


> [!IMPORTANT]
> Es findet keine Übertragung von Berechtigungen zwischen der lokalen Organisation und der Office&nbsp;365-Organisation statt. Berechtigungen, die Sie in der lokalen Organisation definiert haben, müssen in der Office&nbsp;365-Organisation neu erstellt werden.



Weitere Informationen finden Sie unter [Verwalten von Rollengruppen](https://technet.microsoft.com/de-de/library/jj657480\(v=exchg.150\)) und [Verwalten von Rollengruppenmitgliedern](https://technet.microsoft.com/de-de/library/jj657492\(v=exchg.150\)).

## Delegieren von Berechtigungen für Postfächer

In der lokalen Exchange-Bereitstellungen können Benutzer eine Vielzahl von Berechtigungen für Postfächer anderer Benutzer erteilt werden. Delegierte Postfachberechtigungen und seine wird nützlich aufgerufen, wenn ein Verwaltungsmitarbeiter einen Teil des Postfachs für einen anderen Benutzer verwalten muss; Verwalten von beispielsweise eine Führungskraft Kalender. Hybridbereitstellungen in Exchange unterstützt die Verwendung von manchen, jedoch nicht alle Postfachberechtigungen zwischen befindet sich in einer lokalen Exchange-Organisation und Postfächer befindet sich im Office 365. Die folgenden Abschnitte beschreiben, welche Berechtigung werden und werden nicht unterstützt. zusätzliche Konfigurationsschritte zur Unterstützung von Hybriden Postfachberechtigungen erforderlich; und wie Postfachberechtigungen zwischen Ihrer lokalen Organisation und Office 365 synchronisiert werden.

## In Hybridumgebungen unterstützte Postfachberechtigungen

Folgende Berechtigungen **werden unterstützt**:

  - **Vollzugriff** Einem Postfach auf einem lokalen Exchange-Server kann die Berechtigung **Vollzugriff** für ein Office 365-Postfach gewährt werden und umgekehrt. So kann beispielsweise einem Office 365-Postfach die Berechtigung **Vollzugriff** auf ein lokales freigegebenes Postfach gewährt werden. Benutzer müssen das Postfach mithilfe des Outlook-Desktopclients öffnen. Standortübergreifende Postfachberechtigungen werden in Outlook im Web nicht unterstützt.
    

    > [!NOTE]
    > Benutzer werden möglicherweise zusätzlich aufgefordert, ihre Anmeldeinformationen einzugeben, wenn sie erstmals auf ein in der anderen Organisation befindliches Postfach zugreifen, und es zu ihrem Outlook-Profil hinzuzufügen.



  - **Senden im Auftrag von** Einem Postfach auf einem lokalen Exchange-Server kann die Berechtigung **Senden im Auftrag von** für ein Office 365-Postfach gewährt werden und umgekehrt. So kann beispielsweise einem Office 365-Postfach die Berechtigung **Senden im Auftrag von** auf ein lokales freigegebenes Postfach gewährt werden. Benutzer müssen das Postfach mithilfe des Outlook-Desktopclients öffnen. Standortübergreifende Postfachberechtigungen werden in Outlook im Web nicht unterstützt.
    
    Einige Änderungen müssen auf dem Azure Active Directory Connect-Server vorgenommen werden, damit die Berechtigungen „Senden im Auftrag von\&quot; zwischen den lokalen Exchange-Servern und Exchange Online synchronisiert werden. Weitere Informationen hierzu finden Sie unter Aktivieren der Unterstützung für Hybridpostfachberechtigungen in Azure Active Directory Connect weiter unten in diesem Thema.

  - **Folder permissions** Grants access to the contents of a particular folder.

  - **Private Elemente** Beim Hinzufügen einer stellvertretungs kann die Option für die Benutzer mit Berechtigungen für Ordner privaten Kalenderelementen finden Sie unter zulassen konfiguriert werden.


> [!NOTE]
> Ab Februar 2018 das Feature unterstützen Vollzugriff, Senden im Auftrag und Ordner Rechte gesamtstrukturübergreifende ist eingeführt wird und voraussichtlich April 2018 abgeschlossen sein.



Die folgenden Berechtigungen oder Funktionen **werden nicht** unterstützt:

  - **Send-As**Ermöglicht es einem Benutzer, E-Mails aus dem Postfach eines anderen Benutzers zu senden.

  - **Automatische Zuordnung** Ermöglicht es Outlook, alle Postfächer beim Start automatisch zu öffnen, für die dem Benutzer **Vollzugriff** gewährt wurde.

Postfächer, die diese Berechtigungen von einem anderen Postfach empfangen, müssen gleichzeitig mit diesem Postfach verschoben werden. Wenn ein Postfach Berechtigungen von mehreren Postfächern empfängt, müssen dieses Postfach und alle Postfächer, die Berechtigungen dafür gewähren, gleichzeitig verschoben werden.

## Konfigurieren der lokalen Exchange-Server zur Unterstützung von Hybridpostfachberechtigungen

Um in einer Hybridbereitstellung die Berechtigung „Vollzugriff\&quot; und „Senden im Auftrag von\&quot; zu gewähren, sind je nach der installierten Exchange-Version möglicherweise zusätzliche Konfigurationsschritte erforderlich. Die folgende Tabelle zeigt, welche Versionen von Exchange in einer Hybridbereitstellung mit Office 365 delegierte Postfachberechtigungen unterstützen und welche zusätzliche Konfiguration erforderlich ist. Schritte zum Konfigurieren von Exchange 2013- und 2010-Servern und Postfächern für die Unterstützung von Zugriffssteuerungslisten finden Sie unter [Konfigurieren von Exchange für delegierte Postfachberechtigungen in einer Hybridbereitstellung](configure-exchange-to-support-delegated-mailbox-permissions-in-a-hybrid-deployment-exchange-2013-help.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exchange-Version</th>
<th>Voraussetzungen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2016</p></td>
<td><p>Keine zusätzliche Konfiguration erforderlich.</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2013</p></td>
<td><p>Für Exchange 2013-Server müssen folgende Voraussetzungen erfüllt sein:</p>
<ul>
<li><p>Das neueste kumulative Update (KU) oder das unmittelbar vorhergehende kumulative Update muss installiert sein. Exchange 2013-Server mit älteren kumulativen Updates werden nicht unterstützt und funktionieren möglicherweise nicht mit delegierten Postfachberechtigungen in einer Hybridbereitstellung.</p></li>
<li><p>Die Exchange-Organisation ist so konfiguriert, dass E-Mail-Objekte mit Zugriffssteuerungslisten gekennzeichnet werden und mit Office 365 synchronisiert werden.</p></li>
<li><p>Lokale Remotepostfächer, denen zu Office 365 vor Exchange 2013 mit kumulativem Update 10 verschobene Postfächer zugewiesen sind, müssen manuell für die Unterstützung von Zugriffssteuerungslisten konfiguriert werden. Auf Servern mit Exchange 2013 mit kumulativem Update 10 oder höher erstellte Remotepostfächer werden automatisch konfiguriert, nachdem die Exchange-Organisation für das Zulassen von Zugriffssteuerungslisten konfiguriert wurde.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange Server 2010</p></td>
<td><p>Für Exchange 2010 SP3-Server müssen folgende Voraussetzungen erfüllt sein:</p>
<ul>
<li><p>Das neueste Updaterollup oder das unmittelbar vorhergehende Updaterollup muss installiert sein. Exchange 2010 SP3-Server mit älteren Updaterollups werden nicht unterstützt und funktionieren möglicherweise nicht mit delegierten Postfachberechtigungen in einer Hybridbereitstellung.</p></li>
<li><p>Lokale Remotepostfächer, denen Office 365-Postfächer zugeordnet sind, müssen für die Unterstützung von Zugriffssteuerungslisten konfiguriert werden. Dies muss für jedes lokale Remotepostfach erfolgen, dem ein Office 365-Postfach zugeordnet ist.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Exchange 2007 oder älter</p></td>
<td><p>Nicht unterstützt</p></td>
</tr>
</tbody>
</table>


## Aktivieren der Unterstützung für Hybridpostfachberechtigungen in Azure Active Directory Connect

Neben der Konfiguration der lokalen Exchange-Server müssen Sie auch sicherstellen, dass der Azure Active Directory Connect-Server (AAD Connect) für die Synchronisierung von Hybridpostfachberechtigungen eingerichtet ist. Führen Sie die folgenden Schritte durch, um sicherzustellen, dass der AAD Connect-Server für die Unterstützung dieser Berechtigungen konfiguriert ist:

  - **Upgrade AAD verbinden** AAD verbinden auf mindestens aktualisiert werden muss Version 1.1.553.0. Sie können die neueste Version von AAD Verbinden von [Microsoft Azure Active Directory verbinden](http://go.microsoft.com/fwlink/p/?linkid=510956)herunterladen.

  - **Aktivieren von Exchange Hybrid in AAD Connect** Um Attribute für das Aktivieren der Hybridpostfachberechtigungen (insbesondere der Berechtigung „Senden im Auftrag von\&quot;) zu synchronisieren, müssen Sie sicherstellen, dass die Konfigurationsoption für die **Exchange-Hybridbereitstellung** in AAD Connect aktiviert ist. Informationen zum erneuten Ausführen des AAD Connect-Installations-Assistenten, um die Konfiguration zu aktualisieren, finden Sie unter [Azure AD Connect-Synchronisierung: Erneutes Ausführen des Installations-Assistenten](https://docs.microsoft.com/de-de/azure/active-directory/connect/active-directory-aadconnectsync-installation-wizard).

## Synchronisieren von Postfachberechtigungen zwischen der lokalen und der Office 365-Organisationen

## Endbenutzerberechtigungen

Ähnlich wie bei Administratorberechtigungen können Endbenutzern in Exchange Online Berechtigungen erteilt werden. Standardmäßig werden Endbenutzern Berechtigungen über die Standardrichtlinie für die Rollenzuweisung erteilt. Diese Richtlinie wird auf jedes Postfach in der Exchange Online-Organisation angewendet. Wenn die standardmäßig erteilten Berechtigungen ausreichen, sind keine weiteren Schritte erforderlich.

Wenn Sie Endbenutzerberechtigungen anpassen möchten, können Sie entweder die vorhandene Standardrichtlinie für die Rollenzuweisung ändern oder neue Zuweisungsrichtlinien erstellen. Wenn Sie mehrere Zuweisungsrichtlinien erstellen, können Sie unterschiedlichen Gruppen von Postfächern unterschiedliche Richtlinien zuweisen, sodass Sie die Berechtigungen, die jeder Gruppe erteilt werden, entsprechend deren Anforderungen einrichten können. Die gesamte Berechtigungsverwaltung für Exchange Online-Endbenutzer muss in der Exchange Online-Organisation über die Exchange-Verwaltungskonsole oder über Remote-PowerShell ausgeführt werden.

Analog zu Administratorberechtigungen werden Endbenutzerberechtigungen nicht zwischen der lokalen Organisation und der Exchange Online-Organisation übertragen. Alle Berechtigungen, die Sie in der lokalen Organisation definiert haben, müssen in der Exchange Online-Organisation neu erstellt werden.

Weitere Informationen finden Sie unter [Verwalten von Rollenzuweisungsrichtlinien](https://technet.microsoft.com/de-de/library/jj657511\(v=exchg.150\)) und [Ändern der Zuweisungsrichtlinie für ein Postfach](https://technet.microsoft.com/de-de/library/dd638076\(v=exchg.150\)).

In der folgenden Tabelle sind die Berechtigungen aufgelistet, die von den Standardrichtlinien für die Rollenzuweisung in der Exchange Online-Organisation erteilt werden.

### Berechtigungen der Standardrichtlinien für die Rollenzuweisung

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Verwaltungsrolle</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MyTeamMailboxes</p></td>
<td><p>Mit der Verwaltungsrolle <code>MyTeamMailboxes</code> können einzelne Benutzer Websitepostfächer erstellen und mit Microsoft SharePoint-Websites verbinden.</p></td>
</tr>
<tr class="even">
<td><p>Eigene Marketplace-Apps</p></td>
<td><p>Die Verwaltungsrolle <code>My Marketplace Apps</code> ermöglicht einzelnen Benutzern das Anzeigen und Ändern ihrer Microsoft Office Marketplace-Apps.</p></td>
</tr>
<tr class="odd">
<td><p>MyBaseOptions</p></td>
<td><p>Die Verwaltungsrolle <code>MyBaseOptions</code> ermöglicht einzelnen Benutzern, die grundlegende Konfiguration ihres eigenen Postfachs und der zugeordneten Einstellungen anzuzeigen und zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>MyContactInformation</p></td>
<td><p>Mithilfe der Verwaltungsrolle <code>MyContactInformation</code> können einzelne Benutzer ihre Kontaktinformationen einschließlich Adresse und Telefonnummern ändern.</p></td>
</tr>
<tr class="odd">
<td><p>MyDistributionGroupMembership</p></td>
<td><p>Die Verwaltungsrolle <code>MyDistributionGroupMembership</code> berechtigt einzelne Benutzer, ihre Mitgliedschaften in Verteilergruppen innerhalb einer Organisation anzuzeigen und zu bearbeiten, sofern in diesen Verteilergruppen Änderungen an der Gruppenmitgliedschaft zulässig sind.</p></td>
</tr>
<tr class="even">
<td><p>MyDistributionGroups</p></td>
<td><p>Mithilfe der Verwaltungsrolle <code>MyDistributionGroups</code> können einzelne Benutzer Verteilergruppen erstellen, ändern und anzeigen sowie in Verteilergruppen, deren Besitzer sie sind, Mitglieder ändern, anzeigen, entfernen und hinzufügen.</p></td>
</tr>
<tr class="odd">
<td><p>MyMailSubscription</p></td>
<td><p>Die Rolle <code>MyMailSubscription</code> ermöglicht es einzelnen Benutzern, die Einstellungen ihrer E-Mail-Abonnements (z. B. die Standardeinstellungen für Nachrichtenformate und Protokollierung) anzuzeigen und zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>MyProfileInformation</p></td>
<td><p>Die Verwaltungsrolle <code>MyProfileInformation</code> ermöglicht einzelnen Benutzern das Ändern ihres Namens.</p></td>
</tr>
<tr class="odd">
<td><p>MyRetentionPolicies</p></td>
<td><p>Die Verwaltungsrolle <code>MyRetentionPolicies</code> ermöglicht es den einzelnen Benutzern, ihre Aufbewahrungstags anzuzeigen und die Einstellungen und Standardwerte für die Aufbewahrungstags anzuzeigen und zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>MyTextMessaging</p></td>
<td><p>Die Verwaltungsrolle <code>MyTextMessaging</code> ermöglicht einzelnen Benutzern das Erstellen, Anzeigen und Ändern ihrer Textnachrichteneinstellungen.</p></td>
</tr>
<tr class="odd">
<td><p>MyVoiceMail</p></td>
<td><p>Die Verwaltungsrolle <code>MyVoiceMail</code> ermöglicht es den einzelnen Benutzern, ihre Voicemaileinstellungen anzuzeigen und zu ändern.</p></td>
</tr>
<tr class="even">
<td><p>Eigene ReadWriteMailbox-Apps</p></td>
<td><p>Die Verwaltungsrolle <code>My ReadWriteMailbox Apps</code> ermöglicht Benutzern das Installieren von Apps mit ReadWriteMailbox-Berechtigungen.</p></td>
</tr>
<tr class="odd">
<td><p>Eigene benutzerdefinierte Apps</p></td>
<td><p>Die Verwaltungsrolle <code>My Custom Apps</code> ermöglicht Benutzern das Anzeigen und Ändern ihrer benutzerdefinierten Apps.</p></td>
</tr>
</tbody>
</table>

