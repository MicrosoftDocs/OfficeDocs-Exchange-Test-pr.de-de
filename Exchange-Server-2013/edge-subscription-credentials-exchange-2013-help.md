---
title: 'Edge-Abonnementanmeldeinformationen: Exchange 2013 Help'
TOCTitle: Edge-Abonnementanmeldeinformationen
ms:assetid: 1d291bc1-9c00-4d1b-8da0-cb81f63d8305
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb266959(v=EXCHG.150)
ms:contentKeyID: 61180464
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Edge-Abonnementanmeldeinformationen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In diesem Thema wird erläutert, wie der Edge-Abonnementprozess die Anmeldeinformationen bereitstellt, die zum Sichern des EdgeSync-Synchronisierungsprozesses verwendet werden, und wie der EdgeSync-Dienst diese Anmeldeinformationen zum Herstellen einer sicheren LDAP-Verbindung zwischen einem Exchange 2013-Postfachserver und einem Edge-Transport-Server verwendet Weitere Informationen zum Edge-Abonnementprozess finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

**Inhalt**

Edge-Abonnementprozess

EdgeSync-Replikationskonten

Authentifizieren der ersten Replikation

Authentifizieren geplanter Synchronisierungssitzungen

Erneuern der EdgeSync-Replikationskonten

## Edge-Abonnementprozess

Ein Active Directory-Standort wird von einem Edge-Transport-Server abonniert, um eine Synchronisierungsbeziehung zwischen den Postfachservern an einem Active Directory-Standort und dem abonnierten Edge-Transport-Server einzurichten. Die Anmeldeinformationen, die während des Edge-Abonnementprozesses bereitgestellt werden, werden zum Sichern der LDAP-Verbindung zwischen einem Postfachserver und einem Edge-Transport-Server im Umkreisnetzwerk verwendet.

Wenn Sie das Cmdlet **New-EdgeSubscription** auf einem Edge-Transport-Server ausführen, werden die ESBRA-Anmeldeinformationen (EdgeSync Bootstrap Replication Account) im AD LDS (Active Directory Lightweight Directory Services)-Verzeichnis auf dem lokalen Server erstellt und dann in die Edge-Abonnementdatei geschrieben. Diese Anmeldeinformationen werden nur zum Einrichten der anfänglichen Synchronisierung verwendet und laufen 24 Stunden nach Erstellung der Edge-Abonnementdatei ab. Wenn der Edge-Abonnementprozess nicht innerhalb von 24 Stunden abgeschlossen ist, müssen Sie das Cmdlet **New-EdgeSubscription** erneut ausführen, um eine neue Edge-Abonnementdatei zu erstellen. Die Daten des Edge-Abonnements werden in der XML-Datei für das Edge-Abonnement gespeichert.

In der folgenden Tabelle werden die in der XML-Datei für das Edge-Abonnement enthaltenen Daten aufgeführt.

### Inhalt der Edge-Abonnementdatei

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Abonnementdaten</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>EdgeServerName</strong></p></td>
<td><p>Der NetBIOS-Name des Edge-Transport-Servers. Der Active Directory-Name des Edge-Abonnements ist mit diesem Namen identisch.</p></td>
</tr>
<tr class="even">
<td><p><strong>EdgeServerFQDN</strong></p></td>
<td><p>Der vollqualifizierte Domänenname (FQDN, Fully Qualified Domain Name) des Edge-Transport-Servers. Die Postfachserver am abonnierten Active Directory-Standort müssen in der Lage sein, den Edge-Transport-Server mithilfe von DNS zum Auflösen des FQDNs zu ermitteln.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EdgeCertificateBlob</strong></p></td>
<td><p>Der öffentliche Schlüssel des selbstsignierten Zertifikats des Edge-Transport-Servers.</p></td>
</tr>
<tr class="even">
<td><p><strong>ESRAUsername</strong></p></td>
<td><p>Der dem ESBRA-Konto zugewiesene Name. Das ESBRA-Konto weist folgendes Format auf: ESRA.<em>Edge-Transport-Server-Name</em>. ESRA bedeutet EdgeSync Replication Account (Replikationskonto); beachten Sie den Unterschied zwischen den Abkürzungen ESBRA (EdgeSync Bootstrap Replication Account) und ESRA.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ESRAPassword</strong></p></td>
<td><p>Das dem ESBRA-Konto zugewiesene Kennwort. Das Kennwort wird mithilfe eines Zufallszahlengenerators generiert und in der Edge-Abonnementdatei als unverschlüsselter Klartext gespeichert.</p></td>
</tr>
<tr class="even">
<td><p><strong>EffectiveDate</strong></p></td>
<td><p>Das Erstellungsdatum der Edge-Abonnementdatei.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Gültigkeitsdauer</strong></p></td>
<td><p>Die Zeitspanne, für die diese Anmeldeinformationen gültig sind, bevor sie ablaufen. Das ESBRA-Konto ist nur 24 Stunden gültig.</p></td>
</tr>
<tr class="even">
<td><p><strong>AdamSslPort</strong></p></td>
<td><p>Der sichere LDAP-Port, an den EdgeSync bei der Synchronisation von Daten von Active Directory zu AD LDS gebunden wird. Standardmäßig ist dies der TCP-Port 50636.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProductID</strong></p></td>
<td><p>Die Lizenzierungsinformationen für den Edge-Transport-Server. Sie müssen den Edge-Transport-Server lizenzieren, bevor Sie das Edge-Abonnement erstellen.</p></td>
</tr>
<tr class="even">
<td><p><strong>VersionNumber</strong></p></td>
<td><p>Die Versionsnummer der Edge-Abonnementdatei.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SerialNumber</strong></p></td>
<td><p>Die Exchange-Version des Edge-Transport-Servers.</p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> Die ESBRA-Anmeldeinformationen werden als unverschlüsselter Klartext in die Edge-Abonnementdatei geschrieben. Diese Datei muss während des gesamten Abonnementprozesses geschützt werden. Nach dem Importieren der Edge-Abonnementdatei in Ihre Exchange-Organisation sollten Sie die Edge-Abonnementdatei sofort vom Edge Transport-Server, aus dem Netzwerkfreigabeordner, den Sie für den Import der Datei in Ihre Exchange-Organisation verwendet haben, und von allen Wechselmedien löschen.



Zurück zum Seitenanfang

## EdgeSync-Replikationskonten

Die EdgeSync-Replikationskonten (ESRA) sind ein wichtiger Teil der EdgeSync-Sicherheit. Die Authentifizierung und Autorisierung der ESRA-Konten ist ein Mechanismus, mit dem die Verbindung zwischen einem Edge-Transport-Server und einem Postfachserver gesichert wird.

Das ESBRA-Konto, das in der Edge-Abonnementdatei enthalten ist, wird während der anfänglichen Synchronisierung zum Herstellen einer sicheren LDAP-Verbindung verwendet. Nachdem die Edge-Abonnementdatei auf einen Postfachserver am Active Directory-Standort importiert wurde, den der Edge-Transport-Server abonniert hat, werden in Active Directory weitere ESRA-Konten für jedes Paar aus Edge-Transport- und Postfachservern erstellt. Während der anfänglichen Synchronisierung werden die neu erstellten ESRA-Anmeldeinformationen nach AD LDS repliziert. Diese ESRA-Anmeldeinformationen sichern spätere Synchronisierungssitzungen.

Jedem EdgeSync-Replikationskonto werden die in der folgenden Tabelle aufgeführten Eigenschaften zugewiesen.

### Ms-Exch-EdgeSyncCredential-Eigenschaften

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Eigenschaftenname</th>
<th>Typ</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>TargetServerFQDN</strong></p></td>
<td><p>String</p></td>
<td><p>Der Edge-Transport-Server, der diese Anmeldeinformationen akzeptiert.</p></td>
</tr>
<tr class="even">
<td><p><strong>SourceServerFQDN</strong></p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Der Postfachserver, der diese Anmeldeinformationen bereitstellt. Dieser Wert ist leer, wenn es sich bei den Anmeldeinformationen um die Bootstrapanmeldeinformationen handelt.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EffectiveTime</strong></p></td>
<td><p>DateTime (UTC)</p></td>
<td><p>Datum und Uhrzeit des Gültigkeitsbeginns dieser Anmeldeinformationen.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExpirationTime</strong></p></td>
<td><p>DateTime (UTC)</p></td>
<td><p>Datum und Uhrzeit des Gültigkeitsablaufs dieser Anmeldeinformationen.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserName</strong></p></td>
<td><p>Zeichenfolge</p></td>
<td><p>Der zur Authentifizierung verwendete Benutzername.</p></td>
</tr>
<tr class="even">
<td><p><strong>Password</strong></p></td>
<td><p>Byte</p></td>
<td><p>Das zur Authentifizierung verwendete Kennwort. Das Kennwort wird mithilfe von <strong>ms-Exch-EdgeSync-Certificate</strong> verschlüsselt.</p></td>
</tr>
</tbody>
</table>


In den folgenden Abschnitten wird beschrieben, wie die ESRA-Anmeldeinformationen während des EdgeSync-Synchronisierungsprozesses bereitgestellt und verwendet werden.

## Bereitstellen des ESBRA-Kontos (EdgeSync Bootstrap Replication Account)

Wenn das Cmdlet **New-EdgeSubscription** auf dem Edge-Transport-Server ausgeführt wird, wird das ESBRA-Konto folgendermaßen bereitgestellt:

  - Ein selbstsigniertes Zertifikat ("Edge-Cert") wird auf dem Edge-Transport-Server erstellt. Der private Schlüssel wird im Informationsspeicher des lokalen Computers gespeichert, und der öffentliche Schlüssel wird in die Edge-Abonnementdatei geschrieben.

  - Das ESBRA-Konto wird in AD LDS erstellt, und seine Anmeldeinformationen werden in die Edge-Abonnementdatei geschrieben.

  - Die Edge-Abonnementdatei wird durch Kopieren auf Wechselmedien exportiert. (Da sich der Edge-Server nicht in Ihrem Active Directory befindet, können Sie zum Exportieren der Datei keinen freigegebenen Ordner verwenden.) Die Datei ist nun für den Import auf einen Postfachserver bereit.

## Bereitstellen von EdgeSync-Replikationskonten in Active Directory

Wenn die Edge-Abonnementdatei auf einen Postfachserver importiert wird, werden die folgenden Schritte ausgeführt, um einen Datensatz des Edge-Abonnements in Active Directory einzurichten und zusätzliche ESRA-Anmeldeinformationen zur Verfügung zu stellen:

1.  Ein Edge-Transport-Server-Konfigurationsobjekt wird in Active Directory erstellt. Das Zertifikat "Edge-Cert" wird als Attribut in dieses Objekt geschrieben.

2.  Jeder Postfachserver am abonnierten Active Directory-Standort empfängt eine Active Directory-Benachrichtigung, dass das neue Edge-Abonnement registriert wurde. Sobald diese Benachrichtigung empfangen wurde, ruft jeder Postfachserver das ESRA.Edge-Konto ab und verschlüsselt dieses Konto mithilfe des öffentlichen Schlüssels Edge-Cert. Das verschlüsselte ESRA.Edge-Konto wird in das Edge-Transport-Server-Konfigurationsobjekt geschrieben.

3.  Jeder Postfachserver erstellt ein selbstsigniertes Zertifikat (TransportService-Cert). Der private Schlüssel wird im Informationsspeicher des lokalen Computers gespeichert, und der öffentliche Schlüssel wird im Postfachserver-Konfigurationsobjekt in Active Directory gespeichert.

4.  Jeder Postfachserver verschlüsselt das ESRA.Edge-Konto mithilfe des öffentlichen Schlüssels seines eigenen TransportService-Zertifikats und speichert es dann in seinem eigenen Konfigurationsobjekt.

5.  Jeder Postfachserver generiert ein ESRA-Konto für jedes vorhandene Edge-Transport-Server-Konfigurationsobjekt in Active Directory (ESRA.Edge. *Postfachname.Nr.*).
    
    Beispiel: ESRA.Edge.Beispiel.0
    
    Das Kennwort für ESRA.Edge wird mithilfe eines Zufallszahlengenerators generiert und mithilfe des öffentlichen Schlüssels des Zertifikats TransportService-Cert verschlüsselt. Das generierte Kennwort besitzt die maximale Länge, die für Windows Server zulässig ist.

6.  Jedes Konto mit dem Namen ESRA.Edge.*Postfachname.Nr.* wird mithilfe des öffentlichen Schlüssels des Zertifikats Edge-Cert und dann im Edge-Transport-Server-Konfigurationsobjekt in Active Directory gespeichert.

Im folgenden Abschnitt wird erläutert, wie diese Konten während der EdgeSync-Synchronisierung verwendet werden.

Zurück zum Seitenanfang

## Authentifizieren der ersten Replikation

Das erste ESBRA-Konto wird nur zum Einrichten der anfänglichen Synchronisierung verwendet. Während der ersten EdgeSync-Synchronisierungssitzung werden die weiteren ESRA-Konten (ESRA.Edge.*Postfachname.Nr.*) nach AD LDS repliziert. Diese Konten werden zum Authentifizieren nachfolgender EdgeSync-Synchronisierungssitzungen verwendet.

Der Postfachserver, der die anfängliche Replikation durchführt, wird nach dem Zufallsprinzip bestimmt. Der erste Postfachserver am Active Directory-Standort, der einen Topologiescan durchführt und das neue Edge-Abonnement erkennt, führt die anfängliche Replikation durch. Da diese Erkennung auf dem Zeitpunkt des Topologiescans basiert, kann jeder Postfachserver am Standort die anfängliche Replikation durchführen.

EdgeSync leitet eine sichere LDAP-Sitzung vom Postfach- zum Edge-Transport-Server ein.. Der Edge-Transport-Server reicht sein selbstsigniertes Zertifikat ein, und der Postfachserver stellt sicher, dass das Zertifikat dem Zertifikat entspricht, das im Edge-Transport-Server-Konfigurationsobjekt in Active Directory gespeichert ist. Nachdem die Identität des Edge-Transport-Servers überprüft wurde, stellt der Postfachserver dem Edge-Transport-Server die Anmeldeinformationen des Kontos ESRA.Edge.*Postfachname.Nr.* zur Verfügung. Der Edge-Transport-Server überprüft die Anmeldeinformationen, indem er sie mit dem Konto vergleicht, das in AD LDS gespeichert ist.

Der EdgeSync-Dienst auf dem Postfachserver übermittelt die Topologie-, Konfigurations- und Empfängerdaten dann mittels Push aus Active Directory an AD LDS. Die Änderung des Edge-Transport-Server-Konfigurationsobjekts in Active Directory wird nach AD LDS repliziert. AD LDS empfängt die neu hinzugefügten Einträge für ESRA.Edge*Postfachname.\#*, und der Microsoft Exchange-Anmeldeinformationsdienst erstellt das entsprechende AD LDS-Konto.. Diese Konten stehen nun zum Authentifizieren nachfolgender EdgeSync-Synchronisierungssitzungen zur Verfügung.

## Microsoft Exchange-Anmeldeinformationsdienst

Der Microsoft Exchange-Anmeldeinformationsdienst ist Teil des Edge-Abonnementprozesses. Der Anmeldeinformationsdienst wird nur auf dem Edge-Transport-Server ausgeführt. Dieser Dienst erstellt die bidirektionalen ESRA-Konten in AD LDS, damit sich ein Postfachserver bei einem Edge-Transport-Server zum Durchführen der EdgeSync-Synchronisierung authentifizieren kann. EdgeSync kommuniziert nicht direkt mit dem Microsoft Exchange-Anmeldeinformationsdienst. Der Microsoft Exchange-Anmeldeinformationsdienst kommuniziert mit AD LDS und installiert die ESRA-Anmeldeinformationen immer dann, wenn der Postfachserver sie aktualisiert.

Zurück zum Seitenanfang

## Authentifizieren geplanter Synchronisierungssitzungen

Nachdem die anfängliche EdgeSync-Synchronisierung abgeschlossen ist, wird der Zeitplan für die EdgeSync-Synchronisierung festgelegt, und Active Directory-Daten, die sich geändert haben, werden regelmäßig in AD LDS aktualisiert. Ein Postfachserver leitet eine sichere LDAP-Sitzung mit der AD LDS-Instanz auf dem Edge-Transport-Server ein. AD LDS beweist diesem Postfachserver seine Identität, indem das selbstsignierte Zertifikat vorgelegt wird. Der Postfachserver legt AD LDS seine ESRA.Edge-Anmeldeinformationen vor. Das ESRA.Edge-Kennwort wird mithilfe des öffentlichen Schlüssels des selbstsignierten Zertifikats des Postfachservers verschlüsselt. Nur dieser bestimmte Postfachserver kann diese Anmeldeinformationen für die Authentifizierung bei AD LDS verwenden

Zurück zum Seitenanfang

## Erneuern der EdgeSync-Replikationskonten

Das Kennwort für das ESRA-Konto muss der Kennwortrichtlinie des lokalen Servers genügen. Um zu verhindern, dass der Kennworterneuerungsprozess zu einem temporären Authentifizierungsfehler führt, wird ein zweites ESRA.Edge-Konto mit einer Gültigkeitsdauer von drei Tagen vor dem Ablaufzeitpunkt des ersten ESRA-Kontos sieben Tage vor Ablauf des ersten ESRA.Edge-Kontos erstellt. Sobald das zweite ESRA.Edge-Konto gültig wird, verwendet EdgeSync das erste Konto nicht mehr und beginnt mit der Verwendung des zweiten Kontos. Wenn der Ablaufzeitpunkt für das erste Konto erreicht wird, werden diese ESRA-Anmeldeinformationen gelöscht. Dieser Erneuerungsprozess wird fortgesetzt, bis das Edge-Abonnement entfernt wird.

Zurück zum Seitenanfang

