---
title: 'Hilfe bei der Identifizierung meines Problems mit automatischen Tests - Migration: Exchange 2013 Help'
TOCTitle: Hilfe bei der Identifizierung meines Problems mit automatischen Tests - Migration
ms:assetid: c1cd235d-8e8b-44a8-862d-9d36dc3a44c3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn793980(v=EXCHG.150)
ms:contentKeyID: 62633028
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Hilfe bei der Identifizierung meines Problems mit automatischen Tests - Migration

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Die Tests auf dieser Seite helfen bei der Identifikation einiger der häufigsten Konnektivitätsprobleme. Sie können die unten aufgelisteten automatischen Tests verwenden, um ihre Konfiguration zu überprüfen und Ihre Umgebung zu aktualisieren.

Wenn Sie bereits ein Office 365-Benutzerkonto besitzen, klicken Sie auf **Anmelden**. Ein Azure-ID-Konto ist nicht erforderlich. Eventuell werden Sie erneut nach einem Benutzerkonto gefragt, während die Prüfungen laufen. Wenn dies der Fall ist, hat Ihr Benutzerkonto das Format Benutzername@youroffice365login.domain plus Ihr Kennwort.

## Voraussetzungen

Es wird geprüft, ob Azure Active Directory-Anmelde-Assistent und Azure Active Directory-Modul für Windows PowerShell installiert sind.

Die Azure Active Directory-Anmelde-Assistent gibt es in zwei Versionen: [32-Bit](https://go.microsoft.com/fwlink/?linkid=286261) und [64-Bit](https://go.microsoft.com/fwlink/?linkid=286262).

Die Azure Active Directory-Modul für Windows PowerShell gibt es in zwei Versionen: [32-Bit](https://go.microsoft.com/fwlink/?linkid=286258) und [64-Bit](https://go.microsoft.com/fwlink/?linkid=286259).

## Hinzufügen von Domänenprüfungen


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
<td><p>Postfachgrößen</p></td>
<td><p>Ich möchte feststellen, ob meine Benutzer die Standardpostfachgrößen meiner Organisation verwenden, sodass ich meine Migration möglichst gut planen kann.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834877">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Einzelne Gesamtstruktur</p></td>
<td><p>Ich möchte feststellen, ob ich die Konten meiner Benutzer mit der Verzeichnissynchronisation kopieren kann.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834875">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="even">
<td><p>Domänenfunktionsmodus</p></td>
<td><p>Ich bin nicht sicher, ob ich für die Integration von ADFS 2.0 mit einmaliger Anmeldung bereit bin</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834876">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
<tr class="odd">
<td><p>Öffentliche Ordner</p></td>
<td><p>Ich bin nicht sicher, ob ich öffentliche Ordner habe, die nach Office 365 migriert werden müssen.</p></td>
<td><p><a href="https://go.microsoft.com/?linkid=9834896">Führen Sie dieses Kontrollkästchen</a></p></td>
</tr>
</tbody>
</table>

