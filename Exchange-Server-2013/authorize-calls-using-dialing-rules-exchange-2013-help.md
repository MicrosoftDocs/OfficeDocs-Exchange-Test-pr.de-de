---
title: 'Autorisieren von Anrufen mit Wählregeln: Exchange Online Help'
TOCTitle: Autorisieren von Anrufen mit Wählregeln
ms:assetid: 4c18bc07-f55c-42b7-81c1-729878aa93aa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ898499(v=EXCHG.150)
ms:contentKeyID: 51409292
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Autorisieren von Anrufen mit Wählregeln

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Benutzer können standardmäßig keine ausgehenden Anrufe tätigen. Um die Arten von Anrufen festzulegen, die von Benutzern getätigt werden können, erstellen Sie zunächst Wählregeln, und autorisieren Sie dann Gruppen dieser Wählregeln in UM-Wählplänen, UM-Postfachrichtlinien oder automatischen UM-Telefonzentralen. Damit Sie Wählregelgruppen autorisieren können, müssen Wählregeln in einem UM-Wählplan definiert werden. Weitere Informationen finden Sie unter [Erstellen von Wählregeln für Benutzer](https://technet.microsoft.com/de-de/library/JJ898502(v=EXCHG.150)).

Jede von Ihnen erstellte Wählregel enthält die Anruftypen oder Nummernmuster, für die Sie den Benutzern Zugriff erteilen möchten. Sie können verschiedenen Typen von Benutzern das Tätigen verschiedener Anruftypen erlauben. Die von Ihnen zugelassenen Anrufe können innerhalb eines Landes oder einer Region oder auch im Ausland liegen.

Zum Autorisieren oder Einschränken der Wählfunktion müssen die folgenden Einstellungen richtig konfiguriert werden:

  - **Wählregeln**   Wählregeln definieren die Nummer, die UM-aktivierte Benutzer wählen, und die Nummer, die von Unified Messaging aus gesendet und von der Nebenstellenanlage (Private Branch eXchange, PBX) bzw. IP-Nebenstellenanlage gewählt wird. Sie erstellen eine Wählregelgruppe, indem Sie eine Wählregel hinzufügen. Nach der Erstellung einer Wählregelgruppe fügen Sie diese der Liste autorisierter Anrufe für eine inländische/regionale oder internationale Wählregelgruppe hinzu.

  - **Wählregelgruppen**   Wählregelgruppen bestimmen die Art der Anrufe, die Benutzer innerhalb einer Wählgruppe tätigen können.

  - **Wählautorisierungen**   Wählautorisierungen bestimmen die Einschränkungen, die angewendet werden, um zu verhindern, dass Benutzer unnötige Telefongebühren verursachen oder Ferngespräche führen.

## Wie autorisiere ich eine Wählregelgruppe?

An welcher Stelle Sie Wählregelgruppen autorisieren, hängt von den Anrufertypen ab, denen Sie ausgehende Anrufe erlauben möchten. Wenn Sie beispielsweise nur Outlook Voice Access-Benutzern das Tätigen ausgehender Anrufe erlauben möchten, erstellen Sie die Wählregeln und autorisieren anschließend diese Wählregelgruppen bei der UM-Postfachrichtlinie, mit der die Outlook Voice Access-Benutzer verknüpft sind. Die folgende Tabelle zeigt, wie Anrufe für verschiedene Typen von Anrufern autorisiert werden.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Anrufertyp</th>
<th>Wählregelgruppen hier autorisieren</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nicht authentifizierte Anrufer, die sich bei einer Outlook Voice Access-Nummer einwählen und keine PIN eingeben</p></td>
<td><p>UM-Wählplan. Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/authorize-calls-for-users-in-a-dial-plan">Autorisieren von Anrufen für Benutzer in einem Wählplan</a>.</p></td>
</tr>
<tr class="even">
<td><p>Authentifizierte Anrufer, die sich bei einer Outlook Voice Access-Nummer einwählen und eine PIN eingeben</p></td>
<td><p>UM-Postfachrichtlinie für den Anrufer. Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/authorize-calls-for-a-group-of-users">Autorisieren von Anrufen für eine Gruppe von Benutzern</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Nicht authentifizierte Anrufer, die sich bei einer Telefonnummer einwählen, die für eine automatische UM-Telefonzentrale konfiguriert ist</p></td>
<td><p>Automatische UM-Telefonzentrale. Weitere Informationen finden Sie unter <a href="https://docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/authorize-calls-for-auto-attendant-callers">Autorisieren von Aufrufen für automatische Telefonzentralen Anrufer</a>.</p></td>
</tr>
</tbody>
</table>


Je nachdem, welche Benutzer Sie für das tätigen ausgehender Anrufe autorisieren, verwenden Sie die Seite **Wählautorisierung** in der Exchange-Verwaltungskonsole für den Wählplan, die automatische Telefonzentrale oder die UM-Postfachrichtlinie.

