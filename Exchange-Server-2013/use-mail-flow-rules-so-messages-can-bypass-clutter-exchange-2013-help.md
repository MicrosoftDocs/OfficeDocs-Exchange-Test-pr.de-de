---
title: 'Verwenden von Nachrichtenflussregeln zum Umgehen von unwichtigen Elementen durch Nachrichten: Exchange 2013 Help'
TOCTitle: Verwenden von Nachrichtenflussregeln zum Umgehen von unwichtigen Elementen durch Nachrichten
ms:assetid: 58e413f0-aa27-4307-bffd-4df03090a15e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn896639(v=EXCHG.150)
ms:contentKeyID: 64141278
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden von Nachrichtenflussregeln zum Umgehen von unwichtigen Elementen durch Nachrichten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Wenn Sie sicherstellen möchten, dass Sie bestimmte Nachrichten erhalten, können Sie eine Exchange-Transportregel erstellen, die sicherstellt, dass diese Nachrichten Ihren Ordner für unwichtige Elemente umgehen. Weitere Informationen über unwichtige Elemente finden Sie unter [Verwenden der Funktion „Unwichtige Elemente“ zum Sortieren von Nachrichten mit niedriger Priorität in Outlook Web App](https://go.microsoft.com/fwlink/p/?linkid=528411).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Transportregeln finden Sie unter [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) und im [New-TransportRule](https://technet.microsoft.com/de-de/library/bb125138\(v=exchg.150\))-PowerShell-Thema. Wenn Sie mit der PowerShell nicht vertraut sind, lesen Sie die folgenden Themen, um Hilfe in Bezug auf die Verwendung der PowerShell zu erhalten:

  - [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\))

  - [Herstellen einer Verbindung mit Exchange mithilfe der Remoteshell](https://technet.microsoft.com/de-de/library/dd335083\(v=exchg.150\))

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportregeln" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Verwenden der Benutzeroberfläche zum Erstellen einer Transportregel zum Umgehen des Ordners für unwichtige Elemente

In diesem Beispiel sind alle Nachrichten mit dem Titel „Meeting“ zulässig, um die unwichtigen Elemente zu umgehen.

1.  Navigieren Sie im Exchange Admin Center zu **Nachrichtenfluss** \> **Regeln**. Klicken Sie auf ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann **Neue Regel erstellen...** aus.

2.  Nachdem Sie die neue Regel erstellt haben, klicken Sie auf **Speichern**, um die Regel zu starten.

![Grafikbeispiel: Wenn Betreff „Besprechung“ enthält, Clutter umgehen](images/Dn896639.75957aa4-4b2a-4142-92ff-07f8ccc64d82(EXCHG.150).png "Grafikbeispiel: Wenn Betreff „Besprechung“ enthält, Clutter umgehen")

## Verwenden der Shell zum Erstellen einer Transportregel zum Umgehen des Ordners für unwichtige Elemente

In diesem Beispiel sind alle Nachrichten mit dem Titel „Meeting“ zulässig, um die unwichtigen Elemente zu umgehen.

    New-TransportRule -Name <name_of_the_rule> -SubjectContainsWords "Meeting" -SetHeaderName "X-MS-Exchange-Organization-BypassClutter" -SetHeaderValue "true"


> [!IMPORTANT]
> In diesem Beispiel wird die Groß-/Kleinschreibung bei „X-MS-Exchange-Organization-BypassClutter“ und „true“ beachtet.



Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-TransportRule](https://technet.microsoft.com/de-de/library/bb125138\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie können die Kopfzeilen von E-Mail-Nachrichten überprüfen, um zu sehen, ob E-Mails aufgrund der Transportregel zum Umgehen von Clutter im Posteingang landen. Wählen Sie eine E-Mail-Nachricht aus dem Postfach in Ihrer Organisation aus, auf die die Transportregel zum Umgehen von Clutter angewendet wurde. Sehen Sie sich die Kopfzeilen in der Nachricht an. Sie sollten die Kopfzeile **X-MS-Exchange-Organization-BypassClutter: true** sehen. Dies bedeutet, dass die Umgehung funktioniert. Im Thema [Anzeigen der Informationen in Internetkopfzeilen für eine E-Mail-Nachricht](https://go.microsoft.com/fwlink/p/?linkid=822530) finden Sie Informationen zum Suchen der Kopfzeileninformationen.


> [!NOTE]
> Elemente im Kalender, z. B. akzeptierte, gesendete oder abgelehnte Besprechungen, weisen diese Kopfzeilen nicht auf. Wir arbeiten daran, die Clutterfunktionen bald um diese Kalenderelemente zu erweitern.


