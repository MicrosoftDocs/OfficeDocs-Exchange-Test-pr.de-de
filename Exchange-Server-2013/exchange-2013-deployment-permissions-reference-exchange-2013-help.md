---
title: 'Berechtigungsreferenz für die Exchange 2013-Bereitstellung: Exchange 2013 Help'
TOCTitle: Berechtigungsreferenz für die Exchange 2013-Bereitstellung
ms:assetid: b13412d0-0cc4-4c1d-bf31-cae3d3e211a9
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee681663(v=EXCHG.150)
ms:contentKeyID: 59634168
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Berechtigungsreferenz für die Exchange 2013-Bereitstellung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema werden die Berechtigungen beschrieben, die zum Einrichten einer Microsoft Exchange Server 2013-Organisation erforderlich sind. Die Verwaltungsrollengruppen zugeordneten universellen Sicherheitsgruppen (Universal Security Groups, USGs) sowie andere Windows-Sicherheitsgruppen und -Sicherheitsprinzipale werden den Zugriffssteuerungslisten (Access Control Lists, ACLs) verschiedener Active Directory-Objekte hinzugefügt. Mit Zugriffssteuerungslisten wird gesteuert, welche Vorgänge für jedes Objekt ausgeführt werden können. Wenn Sie wissen, welche Berechtigungen den einzelnen Rollengruppen, Sicherheitsgruppen oder Sicherheitsprinzipalen zugewiesen werden, können Sie die zum Installieren von Exchange 2013 erforderlichen Mindestberechtigungen ermitteln.

In einigen Fällen wird die Zugriffssteuerungsliste nicht auf die Standardeigenschaft **ntSecurityDescriptor**, sondern auf eine andere Eigenschaft angewendet, z. B. auf **msExchMailboxSecurityDescriptor**. Der Verzeichnisdienst kann Sicherheit, die nicht in der Sicherheitsbeschreibung von Windows angegeben ist, nicht erzwingen. In den meisten Fällen werden diese ACLs vom Informationsspeicherdienst repliziert, um ACLs für geeignete Objekte zu speichern. Leider ist kein Tool verfügbar, mit dem diese ACLs angezeigt werden können. Es können nur die unformatierten Binärdaten eingesehen werden.

Die Spalten jeder Berechtigungstabelle enthalten die folgenden Informationen:

  - **Konto**   Der Sicherheitsprinzipal, dem die Berechtigungen gewährt oder verweigert werden.

  - **ACE-Typ**   Typ des Zugriffsteuerungseintrags (Access Control Entry, ACE)
    
      - **ALLOW-Zugriffssteuerungseintrag**   Durch einen ALLOW-Zugriffssteuerungseintrag wird den Benutzern oder Gruppen, die dem Zugriffsteuerungseintrag zugeordnet sind, der Zugriff auf ein Element gewährt.
    
      - **DENY-Zugriffssteuerungseintrag**   Durch einen DENY-Zugriffssteuerungseintrag wird den Benutzern oder Gruppen, die dem Zugriffsteuerungseintrag zugeordnet sind, der Zugriff auf ein Element verweigert.

  - **Vererbung**   Der Typ der Vererbung, der für untergeordnete Objekte verwendet wird.
    
      - **Alle** zeigt an, dass die Berechtigungen für das Objekt und alle Unterobjekte gelten.
    
      - **Beschr.** zeigt an, dass Berechtigungen für die Objektklasse gelten, die in der Zeile "Für Eigenschaft/Angewendet auf" aufgelistet werden.
    
      - **Keine** zeigt an, dass diese Berechtigungen nur für das Objekt gelten.

  - **Berechtigungen**   Die dem Konto erteilten Berechtigungen.

  - **Für Eigenschaft/Angewendet auf**   In einigen Fällen gelten Berechtigungen nur für eine bestimmte Eigenschaft, einen Eigenschaftensatz oder eine Objektklasse. Diese eingeschränkten Berechtigungen werden hier angegeben.

  - **Kommentare**   Diese Spalte erläutert ggf., warum die Berechtigungen erforderlich sind, oder stellt andere Informationen zu den Berechtigungen zur Verfügung.

Die Berechtigungen werden in der Tabelle im Allgemeinen unter den Namen aufgeführt, die auf der Eigenschaftenseite **Sicherheit** des ADSI-Editors (Active Directory Service Interfaces, **AdsiEdit.msc**) auf der Registerkarte **Anzeigen/Bearbeiten** in der Ansicht **Erweitert** angegeben sind. Auf der Eigenschaftenseite **Sicherheit** des ADSI-Editors werden die Berechtigungen nur in verkürzter Form angezeigt. Im LDP-Tool (**Ldp.exe**) wird die Zugriffsmaske direkt als numerischer Wert angezeigt. Bei den hier angegebenen Codes handelt es sich um Konstanten, die eindeutig die entsprechenden Berechtigungen definieren.

In der folgenden Tabelle werden die Beziehungen zwischen diesen Werten gezeigt.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Zusammenfassungsseite des ADSI-Editors</th>
<th>Ansicht &quot;ADSI-Editor, Erweitert&quot;, Registerkarte &quot;Anzeigen/Bearbeiten&quot;</th>
<th>Auf ein bestimmtes Objekt angewendete ACL-Einträge</th>
<th>Binärer Wert (Zugriffsmaske in LDP)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Vollzugriff</p></td>
<td><p>Vollzugriff</p></td>
<td><p><code>WRITE_OWNER | WRITE_DAC | READ_CONTROL | DELETE | ACTRL_DS_CONTROL_ACCESS | ACTRL_DS_LIST_OBJECT | ACTRL_DS_DELETE_TREE | ACTRL_DS_WRITE_PROP | ACTRL_DS_READ_PROP | ACTRL_DS_SELF | ACTRL_DS_LIST | ACTRL_DS_DELETE_CHILD | ACTRL_DS_CREATE_CHILD</code></p></td>
<td><p><code>0x000F01FF</code></p></td>
</tr>
<tr class="even">
<td><p>Lesen</p></td>
<td><p>Inhalt auflisten + Alle Eigenschaften lesen + Berechtigungen lesen</p></td>
<td><p><code>ACTRL_DS_LIST | ACTRL_DS_READ_PROP | READ_CONTROL</code></p></td>
<td><p><code>0x00020014</code></p></td>
</tr>
<tr class="odd">
<td><p>Schreiben</p></td>
<td><p>Alle Eigenschaften schreiben + Alle bestätigten Schreibvorgänge</p></td>
<td><p><code>ACTRL_DS_WRITE_PROP | ACTRL_DS_SELF</code></p></td>
<td><p><code>0x00000028</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Inhalt auflisten</p></td>
<td><p><code>ACTRL_DS_LIST</code></p></td>
<td><p><code>0x00000004</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Alle Eigenschaften lesen</p></td>
<td><p><code>ACTRL_DS_READ_PROP</code></p></td>
<td><p><code>0x00000010</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Alle Eigenschaften schreiben</p></td>
<td><p><code>ACTRL_DS_WRITE_PROP</code></p></td>
<td><p><code>0x00000020</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Löschen</p></td>
<td><p><code>DELETE</code></p></td>
<td><p><code>0x00010000</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Unterstruktur löschen</p></td>
<td><p><code>ACTRL_DS_DELETE_TREE</code></p></td>
<td><p><code>0x00000040</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Berechtigungen lesen</p></td>
<td><p><code>READ_CONTROL</code></p></td>
<td><p><code>0x00020000</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Berechtigungen ändern</p></td>
<td><p><code>WRITE_DAC</code></p></td>
<td><p><code>0x00040000</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Besitzer ändern</p></td>
<td><p><code>WRITE_OWNER</code></p></td>
<td><p><code>0x00080000</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Alle bestätigten Schreibvorgänge</p></td>
<td><p><code>ACTRL_DS_SELF</code></p></td>
<td><p><code>0x00000008</code></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Alle erweiterten Rechte</p></td>
<td><p><code>ACTRL_DS_CONTROL_ACCESS</code></p></td>
<td><p><code>0x00000100</code></p></td>
</tr>
<tr class="even">
<td><p>Alle untergeordneten Objekte erstellen</p></td>
<td><p>Alle untergeordneten Objekte erstellen</p></td>
<td><p><code>ACTRL_DS_CREATE_CHILD</code></p></td>
<td><p><code>0x00000001</code></p></td>
</tr>
<tr class="odd">
<td><p>Alle untergeordneten Objekte löschen</p></td>
<td><p>Alle untergeordneten Objekte löschen</p></td>
<td><p><code>ACTRL_DS_DELETE_CHILD</code></p></td>
<td><p><code>0x00000002</code></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p></p></td>
<td><p><code>ACTRL_DS_LIST_OBJECT</code></p></td>
<td><p><code>0x00000080</code></p></td>
</tr>
</tbody>
</table>


Bei erweiterten Rechten handelt es sich um benutzerdefinierte Rechte, die von bestimmten Anwendungen festgelegt werden. Sie werden in der ACL angegeben. Für Active Directory sind sie jedoch bedeutungslos. Die bestimmte Anwendung erzwingt alle erweiterten Rechte. Beispiele für erweiterte Rechte von Exchange sind "Öffentlichen Ordner erstellen" oder "Benannte Eigenschaften im Informationsspeicher erstellen".

Informationen zu Berechtigungen, die während der Installation von Microsoft Exchange Server 2010  festgelegt werden, finden Sie unter [Berechtigungsreferenz für die Exchange 2010-Bereitstellung](https://go.microsoft.com/fwlink/p/?linkid=402924).

## Vorbereiten der Active Directory-Berechtigungen

In den Berechtigungstabellen in diesem Abschnitt wird aufgezeigt, welche Berechtigungen festgelegt werden, wenn Sie den Befehl `Setup /PrepareAD` ausführen.


> [!NOTE]
> Die in diesem Abschnitt beschriebenen Berechtigungen sind die Standardberechtigungen, die konfiguriert werden, wenn Sie Exchange 2013 mithilfe des Modells mit gemeinsamen Berechtigungen bereitstellen. Wenn Sie Exchange 2013 mithilfe des Active Directory-Modells mit geteilten Berechtigungen bereitgestellt haben, sind die Standardberechtigungen andere. Weitere Informationen zu den Änderungen an den Standardberechtigungen, wenn Sie geteilte Active Directory-Berechtigungen verwenden, sowie allgemeine Infos zu den Modellen mit gemeinsamen und geteilten Berechtigungen finden Sie unter <A href="understanding-split-permissions-exchange-2013-help.md">Active Directory split permissions</A> in <A href="understanding-split-permissions-exchange-2013-help.md">Grundlegendes zu geteilten Berechtigungen</A>. Wenn Sie bei der Installation von Exchange keine geteilten Active Directory-Berechtigungen verwenden möchten, verwendet Exchange gemeinsame Berechtigungen.



## Microsoft Exchange-Containerberechtigungen

Die folgende Tabelle zeigt die Berechtigungen, die für den Microsoft Exchange-Container innerhalb der Konfigurationspartition festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<Domäne\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Account</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Installationskonto</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
<td><p>Hierbei handelt es sich um das zum Ausführen von <code>/PrepareAD</code> verwendete Konto.</p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Eigenschaft lesen</p>
<p>Inhalt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen ändern</p></td>
<td><p>msExchSmtpRceiveConnector</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Delegiertes Setup</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Containerberechtigungen der Microsoft Exchange-AutoErmittlung

In der folgenden Tabelle werden die Berechtigungen aufgeführt, die für den Container der Microsoft Exchange-AutoErmittlung innerhalb der Konfigurationspartition festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=Microsoft Exchange Autodiscover,CN=Services,CN=Configuration,DC=\<Domäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Containerberechtigungen der Microsoft Exchange-Organisation

In den Berechtigungstabellen in diesem Abschnitt wird aufgezeigt, welche Berechtigungen für die Microsoft Exchange-Organisation und die Untercontainer innerhalb der Konfigurationspartition festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=\<Organisation\>,CN=Microsoft Exchange,CN=Services,CN=Configuration,DC=\<Domäne\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konten</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisations-Admins</p>
<p>Stammdomänen-Admins</p>
<p>Installationskonto</p>
<p>Organisationsverwaltung</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Senden als</p>
<p>Empfangen als</p></td>
<td><p></p></td>
<td><p>Windows-Administratoren sind nicht berechtigt, Postfächer zu öffnen.</p></td>
</tr>
<tr class="even">
<td><p>Organisations-Admins</p>
<p>Schema-Admins</p>
<p>Stammdomänen-Admins</p>
<p>Installationskonto</p>
<p>Organisationsverwaltung</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Identitätswechsel für Exchange-Webdienste</p>
<p>Tokenserialisierung für Exchange-Webdienste</p></td>
<td><p></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
<tr class="odd">
<td><p>Organisations-Admins</p>
<p>Schema-Admins</p>
<p>Stammdomänen-Admins</p>
<p>Installationskonto</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Speicherübertragungszugriff</p>
<p>Eingeschränkte Delegierung für Speicher</p>
<p>Speicherlesezugriff</p>
<p>Speicherlese/-schreibzugriff</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Lokales System</p></td>
<td><p>Zulassen</p></td>
<td><p>Alle</p></td>
<td><p>Alle erweiterten Rechte</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>msExchAvailabilityUserPassword / msExchAvailabilityAddressSpace</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>Zulassen</p></td>
<td><p>Keine</p></td>
<td><p>Lesen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>NT-Autorität\Netzwerkdienst</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltete Verfügbarkeitsserver</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Alle erweiterten Rechte</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>groupType</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchOwningServer</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMailboxSecurityDescriptor</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMServerWritableFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchDatabaseCreated</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUserCulture</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMobileMailboxFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>siteFolderGUID</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>siteFolderServer</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchEDBOffline</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>userCertificate</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMDtmfMap</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchBlockedSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Public Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPatchMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>publicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMSpokenName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMPinChecksum</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchSafeSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>thumbnailPhoto</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Öffentliche Ordner der obersten Ebene erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Öffentliche Ordner der obersten Ebene erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Status des Informationsspeichers anzeigen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Status des Informationsspeichers anzeigen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Informationsspeicher verwalten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Informationsspeicher verwalten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Benannte Eigenschaften im Informationsspeicher erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Benannte Eigenschaften im Informationsspeicher erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>ACL für Öffentlichen Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>ACL für Öffentlichen Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Kontingente für Öffentliche Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Kontingente für Öffentliche Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Verwaltungs-ACL für Öffentlichen Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Verwaltungs-ACL für Öffentlichen Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Ablaufzeitraum für Öffentlichen Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Ablaufzeitraum für Öffentlichen Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Replikatlisten für Öffentliche Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Replikatlisten für Öffentliche Ordner ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Aufbewahrungszeit für gelöschte Objekte in Öffentlichen Ordnern ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Aufbewahrungszeit für gelöschte Objekte in Öffentlichen Ordnern ändern</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Öffentlichen Ordner erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Öffentlichen Ordner erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Öffentliche Ordner mailaktivieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Alle</p>
<p>NT-Autorität\Anonyme Anmeldung</p>
<p></p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Benannte Eigenschaften im Informationsspeicher erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Alle</p>
<p>NT-Autorität\Anonyme Anmeldung</p>
<p></p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Öffentlichen Ordner erstellen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Alle</p>
<p>NT-Autorität\Anonyme Anmeldung</p>
<p></p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p><code>/ msExchPrivateMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Alle</p>
<p>NT-Autorität\Anonyme Anmeldung</p>
<p></p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p><code>/ msExchPublicMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p><code>/ siteAddressing</code></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=All Address Lists,CN=Address Lists Container,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Offline Address Lists,CN=Address Lists Container, CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Download des Offlineadressbuchs</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Addressing,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Recipient Policies,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchLastAppliedRecipientFilter</code></p>
<p><code>msExchRecipientFilterFlags</code></p></td>
</tr>
</tbody>
</table>


## Containerberechtigungen der Konfigurationspartition

In den Berechtigungstabellen in diesem Abschnitt werden die Berechtigungen aufgeführt, die durch Ausführen des Befehls `Setup /PrepareAD` für die verschiedenen Container innerhalb der Konfigurationspartition festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=Sites,CN=Configuration,DC=\<Domäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchVersion / site</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchVersion / site-link</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPartnerId / site</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMinorPartnerId / site</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchResponsibleforSites / site</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p></p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchTransportSiteFlags / site</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchCost / site-link</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p>
<p>Lokales System</p>
<p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p><code>/ msExchEdgeSyncEHFConnector</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p>
<p>Lokales System</p>
<p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p><code>/ msExchEdgeSyncMservConnector</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Untergeordnete Objekte</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Struktur löschen</p></td>
<td><p><code>msExchEdgeSyncServiceConfig / site</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p>
<p>Lokales System</p>
<p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p><code>/ msExchEdgeSyncServiceConfig</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Untergeordnete Objekte</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Struktur löschen</p></td>
<td><p><code>msExchEdgeSyncMservConnector / msExchEdgeSyncServiceConfig</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p>
<p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Untergeordnete Objekte</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Struktur löschen</p></td>
<td><p><code>msExchEdgeSyncEHFConnector / msExchEdgeSyncServiceConfig</code></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Deleted Objects,CN=Configuration,DC=\<Domäne\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Installationskonto</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigung lesen</p>
<p>Berechtigung schreiben</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p>Hierbei handelt es sich um das zum Ausführen von <code>/PrepareAD</code> verwendete Konto.</p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Netzwerkdienst</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Berechtigungen der administrativen Gruppen von Exchange

Mit dem Befehl `Setup /PrepareAD` werden auch die folgenden Berechtigungen für die administrativen Gruppen innerhalb der Organisation konfiguriert.

### DN (Distinguished Name) des Objekts: CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Zugriff auf Empfängeraktualisierungsdienst</p></td>
<td><p><code>msExchExchangeServer</code></p></td>
<td><p>Ermöglicht Exchange-Empfängeradministratoren, Empfänger mit Proxyadressinformationen zu stempeln.</p></td>
</tr>
<tr class="even">
<td><p>Lokales System</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Zugriff auf Empfängeraktualisierungsdienst</p></td>
<td><p><code>msExchExchangeServer</code></p></td>
<td><p>Ermöglicht allen Servern, Empfänger mit Proxyadressinformationen zu stempeln.</p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Zugriff auf Empfängeraktualisierungsdienst</p></td>
<td><p><code>msExchExchangeServer</code></p></td>
<td><p>Ermöglicht Exchange-Administratoren für Öffentliche Ordner, Empfänger mit Proxyadressinformationen zu stempeln.</p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Advanced Security Settings,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Encryption,CN=Advanced Security Settings,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Arrays,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Database Availability Groups,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Databases,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Servers,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Empfangen als</p></td>
<td><p></p></td>
<td><p>Exchange-Server sind nicht berechtigt, Postfächer zu öffnen.</p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Containerberechtigungen der Microsoft Exchange-Sicherheitsgruppen

In den Berechtigungstabellen in diesem Abschnitt wird aufgezeigt, welche Berechtigungen für den Microsoft Exchange-Sicherheitsgruppencontainer innerhalb der Stammdomänenpartition festgelegt werden.

### DN (Distinguished Name) des Objekts: OU=Microsoft Exchange Security Groups,DC=\<Stammdomäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p></td>
<td><p><code>/ Group</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Löschen</p></td>
<td><p><code>/ group</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Member / group</code></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Organization Management,OU=Microsoft Exchange Security Groups,DC=\<Stammdomäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Public Folder Management,OU=Microsoft Exchange Security Groups,DC=\<Stammdomäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=ExchangeLegacyInterop,OU=Microsoft Exchange Security Groups,DC=\<Stammdomäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Exchange Servers,OU=Microsoft Exchange Security Groups,DC=\<Stammdomäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Stammdomänenadministratoren</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Mitglieder lesen</p>
<p>Mitglieder schreiben</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Administratoren untergeordneter Domänen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Mitglieder lesen</p>
<p>Mitglieder schreiben</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Domäne vorbereiten

In den folgenden Tabellen werden die Berechtigungen aufgeführt, die beim Ausführen des Befehls `Setup /PrepareDomain` festgelegt werden.


> [!NOTE]
> Die in diesem Abschnitt beschriebenen Berechtigungen sind die Standardberechtigungen, die konfiguriert werden, wenn Sie Exchange 2013 mithilfe des Modells mit gemeinsamen Berechtigungen bereitstellen. Wenn Sie Exchange 2013 mithilfe des Active Directory-Modells mit geteilten Berechtigungen bereitgestellt haben, sind die Standardberechtigungen andere. Weitere Informationen zu den Änderungen an den Standardberechtigungen, wenn Sie geteilte Active Directory-Berechtigungen verwenden, sowie allgemeine Infos zu den Modellen mit gemeinsamen und geteilten Berechtigungen finden Sie unter <A href="understanding-split-permissions-exchange-2013-help.md">Active Directory split permissions</A> in <A href="understanding-split-permissions-exchange-2013-help.md">Grundlegendes zu geteilten Berechtigungen</A>. Wenn Sie bei der Installation von Exchange keine geteilten Active Directory-Berechtigungen verwenden möchten, verwendet Exchange gemeinsame Berechtigungen.



### DN (Distinguished Name) des Objekts: DC=\<Domäne\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>NT-AUTORITÄT\NETZWERK</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p>Hiermit werden dem Transportdienst Leseberechtigungen erteilt.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>groupType</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMailboxSecurityDescriptor</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMServerWritableFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUserCultulre</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>memberOf</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>canonicalName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Replikationssynchronisierung</p></td>
<td><p></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Untergeordnete Objekte auflisten</p></td>
<td><p><code>msExchActiveSyncDevices / User</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Untergeordnete Objekte auflisten</p></td>
<td><p><code>msExchActiveSyncDevices / inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchSafeSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMobileMailboxFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchSafeRecipientsHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>userCertificate</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMDtmfMap</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchBlockedSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMSpokenName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMPinChecksum</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>thumbnailPhoto</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Public Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>pwdLastSet</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>WriteDACL</p></td>
<td><p><code>/ user</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>WriteDACL</p>
<p></p></td>
<td><p><code>/ inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Struktur löschen</p></td>
<td><p><code>/ user</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Struktur löschen</p>
<p></p></td>
<td><p><code>/ inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>sAMAccountName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Löschen</p></td>
<td><p><code>/ contact</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Löschen</p></td>
<td><p><code>/ inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Löschen</p></td>
<td><p><code>/ user</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Löschen</p></td>
<td><p><code>/ organizationUnit</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Löschen</p></td>
<td><p><code>/ group</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p></td>
<td><p><code>/ computer</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Member</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>wwwHomePage</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>countryCode</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>managedBy</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Bei der nächsten Anmeldung Kennwort zurücksetzen</p></td>
<td><p></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Kennwort ändern</p></td>
<td><p><code> / user</code></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
<tr class="odd">
<td><p>Delegiertes Setup</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>User Account Restrictions</code></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=AdminSDHolder,CN=System,DC=\<Domäne\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>NT-AUTORITÄT\NETZWERK</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p>Hiermit werden dem Transportdienst Leseberechtigungen erteilt.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>groupType</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMailboxSecurityDescriptor</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMServerWritableFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUserCultulre</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>memberOf</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>canonicalName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Replikationssynchronisierung</p></td>
<td><p></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Untergeordnete Objekte auflisten</p></td>
<td><p><code>msExchActiveSyncDevices / User</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p>
<p>Untergeordnete Objekte auflisten</p></td>
<td><p><code>msExchActiveSyncDevices / inetOrgPerson</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchSafeSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchMobileMailboxFlags</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchSafeRecipientsHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>userCertificate</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMDtmfMap</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchBlockedSendersHash</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMSpokenName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchUMPinChecksum</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>thumbnailPhoto</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Public Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>adminDisplayName</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p><code>/ msExchDynamicDistributionList</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Personal Information</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>mail</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>pwdLastSet</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>sAMAccountName</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>Member</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>wwwHomePage</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>countryCode</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>userAccountControl</code></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange Windows-Berechtigungen</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>managedBy</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Delegiertes Setup</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>User Account Restrictions</code></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Deleted Objects,DC=\<Domäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Inhalt auflisten</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Microsoft Exchange System Objects,DC=\<Domäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NT-AUTORITÄT\NETZWERK</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p>
<p>Inhalt auflisten</p>
<p>Berechtigungen lesen</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>garbageCollPeriod</code></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>adminDisplayName</code></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>modifyTimeStamp</code></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Struktur löschen</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>PropertyDelete-Struktur lesen</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p></p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p></td>
<td><p><code>/ publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p></p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt löschen</p>
<p></p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt löschen</p>
<p></p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>/ publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Kennwort ändern</p>
<p>Bei der nächsten Anmeldung Kennwort zurücksetzen</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p></td>
<td><p><code>/ msExchSystemMailbox</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p></td>
<td><p><code>/ user</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>mail / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>displayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>cn / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p>legacyExchangeDN / publicFolder</p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msDSPhoneticDisplayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPFContacts / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>name / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>mail / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>displayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>cn / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msDSPhoneticDisplayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPFContacts / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>name / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Verwaltung Öffentlicher Ordner</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>mail / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>displayNamePrintable / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>displayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>textEncodedORAddress / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>proxyAddresses / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>cn / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>showInAddressBook / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>legacyExchangeDN / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>Exchange Personal Information / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msDSPhoneticDisplayName / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPFContacts / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>garbageCollPeriod / publicFolder</code></p></td>
</tr>
<tr class="odd">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>name / publicFolder</code></p></td>
</tr>
<tr class="even">
<td><p>Vertrauenswürdiges Exchange-Teilsystem</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p>
<p>Eigenschaft schreiben</p></td>
<td><p><code>msExchPublicDelegates / publicFolder</code></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Exchange Install Domain Servers,CN=Microsoft Exchange System Objects,DC=\<Domäne\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Organisationsverwaltung</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Serverrolleninstallation

Während der Installation der Clientzugriffs- und Postfachserverrollen wird vom Setupprogramm der Sicherheitsgruppe "Administratoren" auf dem lokalen Computer die universelle Sicherheitsgruppe "Organisationsverwaltung" hinzugefügt, sodass Mitglieder der Verwaltungsrollengruppe "Organisationsverwaltung" den Server verwalten können.

In der folgenden Berechtigungstabelle werden die Berechtigungen aufgeführt, die beim Installieren der Clientzugriffs-, und Postfachserverrollen festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=\<Server\>,CN=Servers,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MACHINE$</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>MACHINE$</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p><code>msExchServerSite</code></p>
<p><code>msExchEdgeSyncCredential</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Speicherübertragungszugriff</p>
<p>Eingeschränkte Delegierung für Speicher</p>
<p>Schreibgeschützter Zugriff auf Speicher</p>
<p>Schreib-/Lesezugriff auf Speicher</p></td>
<td><p></p></td>
<td><p>Erweiterte Rechte</p></td>
</tr>
<tr class="even">
<td><p>NT-AUTORITÄT\NETZWERK</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Tokenserialisierung für Exchange-Webdienste</p></td>
<td><p></p></td>
<td><p>Erweitertes Recht</p>
<p>Wird nur für Objekte der Postfachserverrolle erteilt.</p></td>
</tr>
<tr class="odd">
<td><p>NT-AUTORITÄT\NETZWERK</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Lokales System</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Berechtigungen lesen</p>
<p>Inhalt auflisten</p>
<p>Eigenschaft lesen</p>
<p>Objekt auflisten</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Delegiertes Setup</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Vollzugriff</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Delegiertes Setup</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Untergeordnetes Objekt erstellen</p>
<p>Untergeordnetes Objekt löschen</p></td>
<td><p><code>/ msExchPublicMDB</code></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Delegiertes Setup</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Empfangen als</p>
<p>Senden als</p></td>
<td><p></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
</tbody>
</table>


## Database Availability Groups

In den Berechtigungstabellen in diesem Abschnitt werden die Berechtigungen aufgeführt, die im Zusammenhang mit Datenbankverfügbarkeitsgruppen und den jeweils zugehörigen Mitgliedern festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=\<Name der Datenbankverfügbarkeitsgruppe\>,CN=Database Availability Groups,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

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
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Edge-Transport

Wenn Sie einen Edge-Transport-Server installieren und ein Edge-Abonnement für die Exchange-Organisation einrichten, werden die in der folgenden Berechtigungstabelle angegebenen Berechtigungen festgelegt, wenn der Edge-Transport-Server in der Organisation instanziiert wird.

### DN (Distinguished Name) des Objekts: CN=\<Server\>,CN=Servers,CN=\<Administratorgruppe\>,CN=Administrative Groups,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Eigenschaft schreiben</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Keine</p></td>
<td><p>Eigenschaften lesen</p></td>
<td><p></p></td>
<td><p>Der Zugriffssteuerungseintrag ist im Schema für <code>msExchExchangeServer</code>-Klassenobjekte (<code>defaultSecurityDescriptor</code>) definiert.</p></td>
</tr>
</tbody>
</table>


## Postfachserver-Installation

Bei der Installation des ersten Postfachservers werden die folgenden Container angelegt, wenn sie noch nicht vorhanden sind. Die folgende Berechtigungstabelle zeigt die Berechtigungen, die angewendet werden.

### DN (Distinguished Name) des Objekts: CN=Availability Configuration,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Beschr.</p></td>
<td><p>Eigenschaft lesen</p></td>
<td><p><code>msExchAvailabilityUserPassword / msExchAvailabilityAddressSpaceObjects</code></p></td>
<td><p>Erweitertes Recht</p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Default \<Server\>,CN=SMTP Receive Connectors,CN=Protocols,CN=\<Server\>,CN=Servers,CN=\<Administratorgruppe\>,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>DENY-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte Sicherheits-ID (SID) für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>EXCH50 akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>EXCH50 akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>EXCH50 akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>EXCH50 akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>EXCH50 akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow annehmen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow annehmen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSessionParams übernehmen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSessionParams übernehmen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSessionParams übernehmen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XAttr akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XAttr akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XAttr akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Accept XProxyFrom</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XProxyFrom akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XProxyFrom akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSysProbe übernehmen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XSysProbe akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XSysProbe akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Erweiterte Eigenschaften von XMessageContext senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Erweiterte Eigenschaften von XMessageContext senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Erweiterte Eigenschaften von XMessageContext senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext Fast-Index senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext Fast-Index senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext Fast-Index senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext-AD-Empfängercache senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext-AD-Empfängercache senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext-AD-Empfängercache senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


### DN (Distinguished Name) des Objekts: CN=Client \<Server\>,CN=SMTP Receive Connectors,CN=Protocols,CN=\<Server\>,CN=Servers,CN=\<Administratorgruppe\>,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Benutzer</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSessionParams übernehmen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSessionParams übernehmen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSessionParams übernehmen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte Sicherheits-ID (SID) für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Jeden Absender akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an beliebige Empfänger übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow annehmen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow annehmen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>ExchangeLegacyInterop</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XAttr akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XAttr akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XAttr akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Accept XProxyFrom</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XProxyFrom akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XProxyFrom akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XSysProbe übernehmen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XSysProbe akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstruktur-XSysProbe akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Authentifizierungsflag akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Antispam umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Erweiterte Eigenschaften von XMessageContext senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Erweiterte Eigenschaften von XMessageContext senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Erweiterte Eigenschaften von XMessageContext senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext Fast-Index senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext Fast-Index senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext Fast-Index senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Beschränkung der Nachrichtengröße umgehen</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext-AD-Empfängercache senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext-AD-Empfängercache senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XMessageContext-AD-Empfängercache senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Nachrichten an Server übermitteln</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Absender aus autoritativer Domäne akzeptieren</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Erstellung der SMTP-Sendeconnectors

In der folgenden Tabelle werden die Berechtigungen aufgeführt, die beim Erstellen von Sendeconnectors festgelegt werden.

### DN (Distinguished Name) des Objekts: CN=\<Connectorname\>,CN=Connections,CN=\<Routinggruppe\>,CN=Routing Groups, CN=\<Administratorgruppe\>,CN=\<Organisation\>

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Konto</th>
<th>ACE-Typ</th>
<th>Vererbung</th>
<th>Berechtigungen</th>
<th>Für Eigenschaft/Angewendet auf</th>
<th>Kommentare</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NT-AUTORITÄT\ANONYME ANMELDUNG</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Organisationskopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Gesamtstrukturkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>XShadow senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-10</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Partnerserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-24</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Routingkopfzeilen senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Exchange-Legacyserver.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange-Server</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 senden</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-21</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Postfachserver.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-22</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Edge-Transport-Server.</p></td>
</tr>
<tr class="even">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-23</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für extern gesicherte Server.</p></td>
</tr>
<tr class="odd">
<td><p>S-1-9-1419165041-1139599005-3936102811-1022490595-24</p></td>
<td><p>ALLOW-Zugriffssteuerungseintrag</p></td>
<td><p>Alle</p></td>
<td><p>Exch50 senden</p></td>
<td><p></p></td>
<td><p>Dies ist die bekannte SID für Exchange-Legacyserver.</p></td>
</tr>
</tbody>
</table>

