---
title: 'Löschen und Neuerstellen des Standarddiscoverypostfachs in Exchange'
TOCTitle: Löschen und Neuerstellen des Standarddiscoverypostfachs in Exchange
ms:assetid: 4bde0b00-bdf7-44b4-ba64-aa062bc10ca2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn750894(v=EXCHG.150)
ms:contentKeyID: 62371359
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Löschen und Neuerstellen des Standarddiscoverypostfachs in Exchange

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-05-04_

Mithilfe der Exchange-Verwaltungsshell können Sie das Standarddiscoverypostfach löschen und neu erstellen und dem Postfach Berechtigungen zuweisen.

## Aus welchen Gründen kann dies nötig sein?

In Exchange Server 2013 und Exchange Online beträgt die maximale Größe des Standarddiscoverypostfachs 50 GB. Es dienst zum Speichern von Compliance-eDiscovery-Suchergebnissen. Bevor das Größenlimit geändert wurden, konnten Organisationen das Speicherkontingent auf mehr als 50 GB erhöhen. Discoverypostfächer konnten also auf mehr als 50 GB anwachsen. Es bestehen drei Probleme im Zusammenhang mit einem Standarddiscoverypostfach mit mehr als 50 GB:

  - Es wird nicht unterstützt.

  - Es kann nicht zu Office 365 migriert werden.

  - Wenn es das Standarddiscoverypostfach in Exchange Server 2010 ist, kann es nicht auf Exchange Server 2013 aktualisiert werden.

Wie Sie diese Probleme beheben, richtet sich danach, ob Sie die Suchergebnisse aus einem Standarddiscoverypostfach mit mehr als 50 GB speichern möchten.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Möchten Sie die Suchergebnisse speichern?</th>
<th>Aktion...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nein</p></td>
<td><p>Führen Sie die Schritte in diesem Abschnitt aus, um das Standarddiscoverypostfach zu löschen und anschließend neu zu erstellen.</p></td>
</tr>
<tr class="even">
<td><p>Ja</p></td>
<td><p>Führen Sie die unter <a href="reduce-the-size-of-a-discovery-mailbox-in-exchange-exchange-2013-help.md">Verkleinern eines Discoverypostfachs in Exchange</a> beschriebenen Schritte aus.</p></td>
</tr>
</tbody>
</table>


## Verwenden der Exchange-Verwaltungsshell zum Löschen und Neuerstellen des Standarddiscoverypostfachs


> [!NOTE]
> Sie können das Exchange-Verwaltungskonsole (EAC) nicht verwenden, da Discoverypostfächer im EAC nicht angezeigt werden.



1.  Führen Sie den folgenden Befehl aus, um das Standarddiscoverypostfach zu löschen.
    
        Remove-Mailbox "DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}"

2.  Geben Sie in der Meldung, in der aufgefordert werden, zu bestätigen, dass Sie das Postfach und das entsprechende Active Directory-Benutzerobjekt löschen möchten, **Y** ein, und drücken Sie die EINGABETASTE.
    
    Wenn Sie im nächsten Schritt das Discoverypostfach erstellen, wird ein neues Benutzerobjekt in Active Directory erstellt.

3.  Führen Sie den folgenden Befehl aus, um das Standarddiscoverypostfach neu zu erstellen.
    
        New-Mailbox -Name "DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}" -Alias "DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}" -DisplayName "Discovery Search Mailbox" -Discovery

4.  Führen Sie den folgenden Befehl aus, um die Berechtigungen der Rollengruppe "Discoveryverwaltung" zum Öffnen des Standarddiscoverypostfachs und Anzeigen der Suchergebnisse zuzuweisen.
    
        Add-MailboxPermission "DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}" -User "Discovery Management" -AccessRights FullAccess -InheritanceType all

