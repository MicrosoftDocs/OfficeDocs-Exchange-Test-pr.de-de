---
title: 'Hilfe bei der Identifizierung meines Problems mit automatischen Tests – Verzeichnissynchronisierung: Exchange 2013 Help'
TOCTitle: Hilfe bei der Identifizierung meines Problems mit automatischen Tests – Verzeichnissynchronisierung
ms:assetid: e6ea900a-c382-444c-a8ce-54d392bfeca3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn793977(v=EXCHG.150)
ms:contentKeyID: 62633030
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Hilfe bei der Identifizierung meines Problems mit automatischen Tests – Verzeichnissynchronisierung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Sie können die unten aufgelisteten automatischen Tests verwenden, um ihre Konfiguration zu überprüfen und Ihre Umgebung zu aktualisieren.

Wenn Sie bereits ein Office 365-Benutzerkonto besitzen, klicken Sie auf "Anmelden". Sie benötigen kein Azure-ID-Konto. Eventuell werden Sie erneut nach einem Benutzerkonto gefragt, während die Prüfungen laufen. Wenn dies der Fall ist, hat Ihr Benutzerkonto das Format Benutzername@youroffice365login.domain plus Ihr Kennwort.


> [!NOTE]
> Wenn Sie in der Office 365-Portal, Fehler in der Synchronisierung-Server-Ereignisprotokollen oder fehlerhaft Directory Synchronization Benachrichtigung-e-Mails von Microsoft Online Services Sync Warnung Nachrichten erhalten, können Sie verschiedenste Directory Synchronisierungsproblem treten. Der <A href="https://aka.ms/dsup">Directory Synchronization Ratgeber</A> ist ein webbasierter Diagnosetool, identifizieren gängige Typen von Synchronisierungsfehler und vorschreiben gezielt bereitgestellten Lösungen zu gefundene Probleme unterstützen. Die Directory-Synchronisierung Problembehandlung muss auf dem Dirsync-Server ausgeführt werden.



## Voraussetzungen

Es wird geprüft, ob Azure Active Directory-Anmelde-Assistent und Azure Active Directory-Modul für Windows PowerShell installiert sind.

Die Azure Active Directory-Anmelde-Assistent gibt es in zwei Versionen: [32-Bit](https://go.microsoft.com/fwlink/?linkid=286261) und [64-Bit](https://go.microsoft.com/fwlink/?linkid=286262).

Die Azure Active Directory-Modul für Windows PowerShell gibt es in zwei Versionen: [32-Bit](https://go.microsoft.com/fwlink/?linkid=286258) und [64-Bit](https://go.microsoft.com/fwlink/?linkid=286259).

## Überprüfungen der Verzeichnissynchronisierung


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Anwendung</p></td>
<td><p>Symptom</p></td>
<td><p>Prüfung</p></td>
</tr>
<tr class="even">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob alle meine Active Directory-Benutzerkonten die Anforderungen für die Verzeichnissynchronisierung erfüllen.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834884">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob meine Active Directory-Funktionsebenen korrekt auf Windows Server 2003 oder höher eingestellt sind.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834876">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob in den letzten drei Stunden eine Verzeichnissynchronisierung durchgeführt wurde.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834887">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob mein Active Directory doppelte Benutzerattribute aufweist, die die Verzeichnissynchronisierung blockieren.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834883">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob die Verzeichnissynchronisierung in Office 365 aktiviert ist.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834887">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob ich Office 365-Kontingentbegrenzungen einsetzen kann.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834920">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob ich Office 365 einsetzen und das Standard-Setup für die Verzeichnissynchronisierung verwenden kann.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834876">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob ich Active Directory verwenden und die Verzeichnissynchronisierung unterstützen kann.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834886">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Verzeichnissynchronisierung</p></td>
<td><p>Ich bin nicht sicher, ob alle meine Active Directory-Gruppen die Anforderungen für die Verzeichnissynchronisierung erfüllen.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834913">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
</tbody>
</table>

