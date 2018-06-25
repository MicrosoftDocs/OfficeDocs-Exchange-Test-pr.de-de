---
title: Übermitteln der Systemintegrität durch das Exchange Server 2013 Management Pack
TOCTitle: Übermitteln der Systemintegrität durch das Exchange Server 2013 Management Pack
ms:assetid: 6ca8847f-93fe-458d-bd43-7afad7fdd2f4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn195910(v=EXCHG.150)
ms:contentKeyID: 53181886
ms.author: dstrome
ms.date: 04/03/2015
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Übermitteln der Systemintegrität durch das Exchange Server 2013 Management Pack

 

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

In diesem Abschnitt finden Sie Informationen zur Art und Weise, wie das Exchange Server 2013 Management Pack die Systemintegrität von Exchange überwacht und meldet. Im Exchange 2013-Management Pack wird ein einfaches Rollup der Informationen zum Integritätsstatus durchgeführt. Immer dann, wenn ein Integritätssatz einen fehlerhaften Status meldet und der Antwortdienst für die Eskalation ausgelöst wird, wird folgendes Ereignis in die Windows-Ereignisanzeige geschrieben.

## Verwaltete Verfügbarkeit

In Exchange Server 2013 wurde einige Änderungen an der Architektur vorgenommen. Eine der wesentlichen Änderungen ist das neue Feature der *Verwalteten Verfügbarkeit*. Hierbei verfügen alle Exchange 2013-Komponenten über integrierte Monitore, die Probleme ermitteln und versuchen, die Dienstverfügbarkeit wiederherzustellen. Das Exchange 2013 Management Pack stützt sich auf dieses Feature. Alle Probleme, die nicht automatisch gelöst werden können, werden als Warnung an das Exchange 2013-Management Pack eskaliert. Jede Komponenten von Exchange 2013 überwacht sich mithilfe der drei grundlegenden Instrumente Test, Monitor und Antwortdienst selbst.

![Verwaltete Verfügbarkeit](images/Dn195910.dd5febae-d05e-4089-a3f5-1691b2d9a3d7(EXCHG.150).png "Verwaltete Verfügbarkeit")

  - **Tests**   Dies sind Datensammlersätze, die verschiedene Komponente messen. Es existieren drei wesentliche Testtypen:
    
      - Sie umfassen synthetische Transaktionen, die synthetische End-to-End-Benutzeroperationen messen, sowie Prüfungen, die den tatsächlichen Datenverkehr messen.
    
      - Prüfungen, die den tatsächlichen Kundenverkehr messen.
    
      - Benachrichtigungen, die es Exchange erlauben, unmittelbare Maßnahmen zu ergreifen. Ein gutes Beispiel dafür sind Benachrichtigungen, die ausgelöst werden, sobald ein Zertifikat erlischt.

  - **Monitore**   Die mithilfe von Tests erfassten Daten werden an Monitore weitergeleitet, welche die Daten auf spezifische Bedingungen analysieren und daraufhin entscheiden, ob die jeweilige Komponente sich in einem fehlerhaften oder fehlerfreien Zustand befindet.

  - **Antwortdienste**   Wenn ein Monitor ermittelt, dass sich eine Komponente in einem fehlerhaften Zustand befindet, wird ein Antwortdienst ausgelöst. Falls das Problem behoben werden kann, versucht der Antwortdienst, die Komponente mithilfe der integrierten Logik wiederherzustellen. Für jede Komponente stehen verschiedene Antwortdienste zur Verfügung, der für das Exchange 2013-Management Pack relevante Antwortdienst ist jedoch der *Antwortdienst für die Eskalation*. Wenn der Antwortdienst für die Eskalation ausgelöst wird, generiert er ein Ereignis, das das Exchange 2013-Management Pack erkennt und mit geeigneten Informationen für die Warnung füllt, die den Administratoren die erforderlichen Informationen zum Beheben des Problems an die Hand gibt.

Jede Komponente in Exchange 2013 verfügt über eine spezielle Gruppe von Tests, Monitoren und Antwortdiensten für die Selbstüberwachung. Die Sammlungen von Tests und Monitoren werden als *Integritätssätze* bezeichnet. Beispiel: Eine Reihe von Tests erfassen Daten zu unterschiedlichen Aspekten des ActiveSync-Diensts. Diese Daten werden einer bestimmten Gruppe von Monitoren verarbeitet, die die entsprechenden Antwortdienste auslösen, um Probleme zu beheben, die im ActiveSync-Dienst erkannt wurden. Zusammen bilden diese Komponenten den ActiveSync-Integritätssatz.

Diese Exchange-Integritätssätze lassen sich in die folgenden vier Kategorien unterteilen, die dem Management Pack Dashboard entsprechen:

  - Kontaktpunkte für Kunden

  - Dienstkomponenten

  - Serverressourcen

  - Schlüsselabhängigkeiten

Eine vollständige Liste der Exchange-Integritätssätze finden Sie unter [Appendix A: Exchange health sets](appendix-a-exchange-health-sets.md).

Weitere Informationen zur verwalteten Verfügbarkeit finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Funktionsweise des Integritätsrollups

In diesem Abschnitt finden Sie Informationen zur Art und Weise, wie das Exchange Server 2013 Management Pack die Systemintegrität von Exchange überwacht und meldet. Im Exchange 2013-Management Pack wird ein einfaches Rollup der Informationen zum Integritätsstatus durchgeführt. Immer dann, wenn ein Integritätssatz einen fehlerhaften Status meldet und der Antwortdienst für die Eskalation ausgelöst wird, wird folgendes Ereignis in die Windows-Ereignisanzeige geschrieben.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Protokollname</p></td>
<td><p>Microsoft-Exchange-ManagedAvailability/Monitoring</p></td>
</tr>
<tr class="even">
<td><p>Quelle</p></td>
<td><p>ManagedAvailability</p></td>
</tr>
<tr class="odd">
<td><p>Datum</p></td>
<td><p>&lt;<em>Datum und Uhrzeit des Ereignisses</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Ereignis-ID</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>Taskkategorie</p></td>
<td><p>Überwachung</p></td>
</tr>
<tr class="even">
<td><p>Stufe</p></td>
<td><p>Fehler</p></td>
</tr>
<tr class="odd">
<td><p>Schlüsselwörter</p></td>
<td><p>&lt;<em>Kein/e</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Benutzer</p></td>
<td><p>SYSTEM</p></td>
</tr>
<tr class="odd">
<td><p>Computer</p></td>
<td><p>&lt;<em>FQDN des Exchange-Servers</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Beschreibung</p></td>
<td><p>&lt;<em>vom Antwortdienst für die Eskalation dynamisch generiert</em>&gt;</p></td>
</tr>
</tbody>
</table>


Der Management Pack-Agent erkennt und verarbeitet dieses Ereignis. Mit diesem Ereignis können über die verwaltete Verfügbarkeit innerhalb von SCOM Warnungen generiert werden. Wurde das Problem behoben und der Integritätssatz kehrt zum Fehlerfreistatus zurück, wird das folgende Ereignis im Windows-Ereignisprotokoll protokolliert:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Protokollname</p></td>
<td><p>Microsoft-Exchange-ManagedAvailability/Monitoring</p></td>
</tr>
<tr class="even">
<td><p>Quelle</p></td>
<td><p>ManagedAvailability</p></td>
</tr>
<tr class="odd">
<td><p>Datum</p></td>
<td><p>&lt;<em>Datum und Uhrzeit des Ereignisses</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Ereignis-ID</p></td>
<td><p>1</p></td>
</tr>
<tr class="odd">
<td><p>Taskkategorie</p></td>
<td><p>Überwachung</p></td>
</tr>
<tr class="even">
<td><p>Stufe</p></td>
<td><p>Information</p></td>
</tr>
<tr class="odd">
<td><p>Schlüsselwörter</p></td>
<td><p>&lt;<em>Kein/e</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Benutzer</p></td>
<td><p>SYSTEM</p></td>
</tr>
<tr class="odd">
<td><p>Computer</p></td>
<td><p>&lt;<em>FQDN des Exchange-Servers</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Beschreibung</p></td>
<td><p>&lt;<em>vom Antwortdienst für die Eskalation dynamisch generiert</em>&gt;</p></td>
</tr>
</tbody>
</table>


Die Management Packs, die Vorgängerversionen von Exchange überwachten, wurden vollständig zentralisiert. Agents auf jedem Exchange-Server erfassten Daten, die anschließend von einem zentralen Korrelationsmodul verglichen und ausgewertet wurden, um die Dienstintegrität insgesamt zu ermitteln. In umfangreichen Umgebungen führte dieser Prozess zu komplexen Korrelationen, die wiederum zu Verzögerungen bei der Generierung von Warnungen führten. In Exchange 2013 kommt die Warnungskorrelation nicht länger zum Einsatz. Stattdessen führt jeder Server eine eigene Überwachung durch und gibt ggf. Warnungen an SCOM aus. Auf diese Weise wird eine hoch skalierbare Architektur unterstützt.

Je nach den Auswirkungen des Ereignisses und dem Integritätssatz, der es ausgelöst hat, wird das Problem auf der SCOM-Konsole in einer jeweils anderen Kategorie angezeigt. Falls das Ereignis zu Auswirkungen auf den Benutzer führt, zeigt der Kontaktpunktindikator des Kunden einen Fehler an. Führt das Ereignis zur Nichtverfügbarkeit einer kompletten Komponente, wie OWA, zeigt der Dienstkomponentenindikator einen Fehler an. Liegt das Problem bei einem bestimmten Server, zeigt der entsprechende Serverintegritätsindikator einen Fehler an. Liegt das Problem schließlich bei einer für Exchange unverzichtbaren Ressource, zeigt der Schlüsselabhängigkeitsindikator einen Fehler an. Weitere Informationen zu diesen Kategorien finden Sie unter [Erste Schritte mit Exchange Server 2013 Management Pack](getting-started-with-exchange-server-2013-management-pack.md).

