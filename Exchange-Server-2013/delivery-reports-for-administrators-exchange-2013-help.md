---
title: 'Übermittlungsberichte für Administratoren: Exchange 2013 Help'
TOCTitle: Übermittlungsberichte für Administratoren
ms:assetid: d98623d3-e0b7-4cb9-93fb-6351b4a06137
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ919241(v=EXCHG.150)
ms:contentKeyID: 51409349
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Übermittlungsberichte für Administratoren

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mit Zustellungsberichten für Administratoren können Sie Übermittlungsinformationen zu Nachrichten nachverfolgen, die von einem bestimmten Postfach in Ihrer Organisation gesendet oder empfangen wurden. Für Zustellungsberichte für Administratoren wird insbesondere die Exchange-Verwaltungskonsole genutzt, um eine zielgerichtete Durchsuchung der Nachrichtenverfolgungsprotokolle durchzuführen. Die Suche ist immer auf ein bestimmtes Postfach beschränkt. Sie können Nachrichten suchen, die vom oder an das Postfach gesendet wurden, und Suchergebnisse nach dem Nachrichtenbetreff filtern.

Der Inhalt des Nachrichtentexts wird im Zustellungsbericht nicht zurückgegeben, die Betreffzeile wird in den Ergebnissen jedoch angezeigt. Informationen zum Durchsuchen der Postfächer Ihrer Organisation nach bestimmten E-Mail-Nachrichten basierend auf dem Nachrichteninhalt finden Sie unter [Compliance-eDiscovery](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery).

Sie finden Zustellungsberichtssuchen möglicherweise in den folgenden Situationen nützlich:

  - Ein Vorgesetzter stellt einem Praktikanten ein schlechtes Zeugnis aus, weil der Praktikant eine Aufgabe nicht rechtzeitig erledigt hat. Der Praktikant besteht darauf, dass er eine E-Mail mit der Aufgabe als Anlage gesendet hat. Der Vorgesetzte bittet Sie, den Status der Nachricht zu überprüfen.

  - Ein Sicherheitsbulletin wurde an Benutzer gesendet, mit der Aufforderung zur sofortigen Antwort. Niemand hat geantwortet. Wird die E-Mail ignoriert, oder haben sie sie einfach nicht empfangen?

  - Benutzer klagen darüber, dass niemand ihre Nachrichten empfängt. Sie überprüfen den Zustellungsstatus ihrer E-Mails, können jedoch nicht erkennen, was vor sich geht. Möglicherweise wird eine Regel auf Organisationsebene auf Nachrichten angewendet.

Nach dem Erstellen einer Zustellungsberichtssuche enthält der resultierende Zustellungsbericht die folgenden Informationen: den Absender und Empfänger der Nachricht, die Betreffzeile und den Sendezeitpunkt der Nachricht. Der Zustellungsbericht zeigt auch den Zustellungsstatus der Nachrichten und die Gründe an, warum die Übermittlung möglicherweise verzögert wird oder fehlerhaft ist.

## Weitere Informationen zu Zustellungsberichten

  - Hier finden Sie Informationen, wie ein neuer Zustellungsbericht erstellt wird: [Nachverfolgen von Nachrichten mit Zustellungsberichten](track-messages-with-delivery-reports-exchange-2013-help.md).

  - Lokale Exchange-Organisationen können über die Exchange-Verwaltungsshell die Nachrichtenverfolgungsprotokolle direkt abfragen. Weitere Informationen finden Sie unter [Durchsuchen von Nachrichtenverfolgungsprotokollen](search-message-tracking-logs-exchange-2013-help.md).

  - Benutzer können ihre eigenen Nachrichten nachverfolgen. Weitere Informationen finden Sie unter [Zustellungsberichte für Benutzer](https://go.microsoft.com/fwlink/?linkid=279920).

  - Falls Ihre Organisation eine Vorversion von Exchange aufweist, müssen Sie prüfen, wie die Zustellungsberichtsfunktion in Exchange 2013 in älteren Exchange-Versionen funktioniert.
    
      - Exchange 2013-Zustellungsberichte dienen zum Nachverfolgen von Nachrichten auf Servern mit Exchange 2010 am selben Active Directory-Standort.
    
      - Exchange 2013-Zustellungsberichte dienen nicht zum Nachverfolgen von Nachrichten auf Servern mit Exchange 2007 am selben Active Directory-Standort. Die Zustellungsberichtsfunktion verwendet einen Remoteprozeduraufruf (RPC) und eine Webdienst-Schnittstelle, die in Exchange 2007 nicht vorhanden ist.

