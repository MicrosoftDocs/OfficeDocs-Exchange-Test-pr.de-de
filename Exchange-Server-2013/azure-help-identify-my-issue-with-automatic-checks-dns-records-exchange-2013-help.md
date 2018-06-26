---
title: 'Azure: Hilfe bei der Identifizierung meines Problems mit automatischen Tests - DNS-Einträge: Exchange 2013 Help'
TOCTitle: 'Azure: Hilfe bei der Identifizierung meines Problems mit automatischen Tests - DNS-Einträge'
ms:assetid: 1ef42cde-4df4-401a-b8f2-494630996ca8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn793619(v=EXCHG.150)
ms:contentKeyID: 62629985
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Azure: Hilfe bei der Identifizierung meines Problems mit automatischen Tests - DNS-Einträge

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Eines der häufigsten Konfigurationseinrichtungsprobleme ist die unkorrekte Konfiguration von DNS-Einträgen. Sie können die unten aufgelisteten automatischen Tests verwenden, um ihre Konfiguration zu überprüfen und Ihre Umgebung zu aktualisieren.

Wenn Sie bereits ein Office 365-Benutzerkonto besitzen, klicken Sie auf "Anmelden". Sie benötigen kein Azure-ID-Konto. Eventuell werden Sie erneut nach einem Benutzerkonto gefragt, während die Prüfungen laufen. Wenn dies der Fall ist, hat Ihr Benutzerkonto das Format Benutzername@youroffice365login.domain plus Ihr Kennwort.

## Voraussetzungen

Es wird geprüft, ob Azure Active Directory-Anmelde-Assistent und Azure Active Directory-Modul für Windows PowerShell installiert sind.

Die Azure Active Directory-Anmelde-Assistent gibt es in zwei Versionen: [32-Bit](https://go.microsoft.com/fwlink/?linkid=286261) und [64-Bit](https://go.microsoft.com/fwlink/?linkid=286262).

Die Azure Active Directory-Modul für Windows PowerShell gibt es in zwei Versionen: [32-Bit](https://go.microsoft.com/fwlink/?linkid=286258) und [64-Bit](https://go.microsoft.com/fwlink/?linkid=286259).

## Prüfungen von DNS-Einträgen


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
<td><p>Domänen</p></td>
<td><p>Meine benutzerdefinierte Domäne (z. B. &quot;contoso.com&quot;) scheint nicht mit Office 365 konfiguriert worden zu sein.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Domänen</p></td>
<td><p>Meine benutzerdefinierte Domäne (z. B. &quot;contoso.com&quot;) scheint mit Office 365 konfiguriert worden zu sein. (Ich habe einen CNAME-Eintrag verwendet)</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Domänen</p></td>
<td><p>Meine benutzerdefinierte Domäne (z. B. &quot;contoso.com&quot;) scheint mit Office 365 konfiguriert worden zu sein. (Ich habe einen TXT-Eintrag verwendet)</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834905">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Instant Messaging</p></td>
<td><p>Meine Benutzer haben Schwierigkeiten damit, den Lync-Client zu aktivieren.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834901">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Instant Messaging</p></td>
<td><p>Meine Benutzer haben Schwierigkeiten beim Einrichten des Lync-Clients für die Zusammenarbeit mit anderen Unternehmen</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834902">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>E-Mails</p></td>
<td><p>Ich kann Outlook nicht automatisch mit Office 365 konfigurieren</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834897">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>E-Mails</p></td>
<td><p>Meine E-Mail-Adresse wird anscheinend nicht an Office 365 weitergeleitet</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834898">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>E-Mails</p></td>
<td><p>Meine Organisation erhält viele Spam-Nachrichten.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834903">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>E-Mails</p></td>
<td><p>Ich kann anscheinend Exchange Hybrid nicht aktivieren</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834904">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
</tbody>
</table>

