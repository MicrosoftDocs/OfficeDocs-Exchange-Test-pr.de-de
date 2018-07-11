---
title: 'Outlook Web App-Postfachrichtlinien: Exchange 2013 Help'
TOCTitle: Outlook Web App-Postfachrichtlinien
ms:assetid: 213b8b7a-1c29-49ee-8c98-d0364ddf4f9d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd335142(v=EXCHG.150)
ms:contentKeyID: 50475208
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Outlook Web App-Postfachrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-05_

Verwenden Sie MicrosoftOutlook Web App-Postfachrichtlinien, um Richtlinien auf Organisationsebene zur Verwaltung des Zugriffs auf Funktionen in Outlook Web App zu erstellen.

**Inhalt**

Outlook Web App-Postfachrichtlinien

Erstellen oder Löschen von Outlook Web App-Postfachrichtlinien

Konfigurieren von Outlook Web App-Postfachrichtlinien

Anwenden von Outlook Web App-Postfachrichtlinien

## Outlook Web App-Postfachrichtlinien

Sie können in Exchange 2013 mehrere Outlook Web App-Postfachrichtlinien erstellen und auf einzelne Postfächer anwenden. Wird eine Outlook Web App-Postfachrichtlinie auf ein Postfach angewendet, setzt diese die Einstellungen des virtuellen Verzeichnisses außer Kraft.

Zur Verwaltung von Outlook Web App-Funktionen können auch die virtuellen Outlook Web App-Verzeichnisse konfiguriert werden. Die Einstellungen virtueller Verzeichnisse werden für sämtliche Postfächer verwendet, auf die keine Postfachrichtlinie angewendet wurde.

## Erstellen oder Löschen von Outlook Web App-Postfachrichtlinien

Bei der Installation von Exchange wird automatisch eine Outlook Web App-Postfachrichtlinie erstellt. Standardmäßig sind alle Optionen für die Outlook Web App-Standardpostfachrichtlinie aktiviert. Sie können so viele Outlook Web App-Postfachrichtlinien erstellen, wie es Ihre Organisation erfordert.


> [!NOTE]
> Die standardmäßige Outlook Web App-Postfachrichtlinie wird nicht automatisch auf Postfächer angewendet.



Informationen zum Erstellen oder Entfernen von Postfachrichtlinien finden Sie unter [Erstellen einer Outlook Web App-Postfachrichtlinie](create-an-outlook-web-app-mailbox-policy-exchange-2013-help.md) und [Entfernen einer Outlook Web App-Postfachrichtlinie aus Exchange](remove-an-outlook-web-app-mailbox-policy-from-exchange-exchange-2013-help.md).

## Konfigurieren von Outlook Web App-Postfachrichtlinien

In der Outlook Web App-Standardpostfachrichtlinie sind standardmäßig alle Optionen aktiviert. Weitere Informationen zum Konfigurieren von Outlook Web App-Postfachrichtlinien finden Sie unter [Anzeigen oder Konfigurieren der Eigenschaften von Outlook Web App-Postfachrichtlinien](view-or-configure-outlook-web-app-mailbox-policy-properties-exchange-2013-help.md).

## Anwenden von Outlook Web App-Postfachrichtlinien

Auf ein Postfach kann nur eine Outlook Web App-Postfachrichtlinie angewendet werden.

Wenn keine Outlook Web App-Postfachrichtlinie auf ein Postfach angewendet ist, werden die im virtuellen Verzeichnis definierten Einstellungen angewendet.

Eine Outlook Web App-Postfachrichtlinie kann auf ein Postfach angewendet werden, indem Sie ein vorhandenes Postfach über die Exchange-Verwaltungskonsole ändern, oder indem Sie die Postfachrichtlinie mithilfe des Cmdlets [Set-CASMailbox](https://technet.microsoft.com/de-de/library/bb125264\(v=exchg.150\)) über die Shell anwenden. Weitere Informationen finden Sie unter [Anwenden oder Entfernen einer Outlook Web App-Postfachrichtlinie auf ein Postfach bzw. von einem Postfach](apply-or-remove-an-outlook-web-app-mailbox-policy-on-a-mailbox-exchange-2013-help.md).

