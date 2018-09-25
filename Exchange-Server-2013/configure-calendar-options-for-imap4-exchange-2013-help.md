---
title: 'Konfigurieren von Kalenderoptionen für IMAP4: Exchange 2013 Help'
TOCTitle: Konfigurieren von Kalenderoptionen für IMAP4
ms:assetid: 6679c8b2-3f0f-449a-a17c-a7b30001538c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998606(v=EXCHG.150)
ms:contentKeyID: 50554829
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Kalenderoptionen für IMAP4

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-27_

Mithilfe der Shell können Sie die Einstellungen für den Kalenderzugriff der Benutzer konfigurieren, die sich unter Verwendung von IMAP4 mit ihren Postfächern verbinden. Mit den von Ihnen angegebenen Einstellungen bestimmen Sie, wie Ihre IMAP4-Benutzer auf ihre Kalender zugreifen und Kalenderinformationen mit anderen Benutzern austauschen können (z. B. das Versenden und Beantworten von Besprechungsanfragen).

Weitere Informationen zu IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Verwenden der Shell zum Festlegen der Kalenderoptionen für IMAP4

In diesem Beispiel wird IMAP4-Benutzern die Verwendung des iCalendar-Standards ermöglicht, ein Standard für den Austausch von Kalenderinformationen.

```powershell
Set-ImapSettings -Identity CAS01 -CalendarItemRetrievalOption iCalendar
```

In diesem Beispiel wird IMAP4-Benutzern der Zugriff auf Kalenderinformationen von einem internen Server ermöglicht.

```powershell
    Set-ImapSettings -Identity CAS01 -CalendarItemRetrievalOption IntranetUrl 
```

In diesem Beispiel wird IMAP4-Benutzern der Zugriff auf Kalenderinformationen aus dem Internet oder von einem externen Server ermöglicht.

```powershell
Set-ImapSettings -CalendarItemRetrievalOption InternetUrl
```

In diesem Beispiel wird IMAP4-Benutzern der Zugriff auf Kalenderinformationen mithilfe einer direkten Outlook Web App-URL ermöglicht. Wenn Sie `Custom` verwenden, müssen Sie eine Outlook Web App-URL unter Verwendung des Parameters *OWAServerUrl* angeben.

```powershell
Set-Imap4Settings -CalendarItemRetrievalOption Custom -OwaServerUrl "https://OwaServer01"
```

Nach dem Festlegen der Kalenderoptionen für IMAP4 müssen die IMAP4-Dienste neu gestartet werden. Informationen zum Neustarten der IMAP4-Dienste finden Sie unter [Starten und Stoppen der IMAP4-Dienste](start-and-stop-the-imap4-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um das erfolgreiche Einstellen der Kalenderoptionen zu überprüfen:

Führen Sie folgenden Befehl in der Shell aus.

```powershell
Get-ImapSettings | format-list
```

Überprüfen Sie, ob die Kalendereinstellungen korrekt sind.

## Weitere Informationen

Nachdem Sie die Kalenderoptionen für IMAP4 festgelegt haben, können Sie die folgenden Aufgaben ausführen:

[Konfigurieren von Nachrichtenabrufformat-Optionen für POP3 und IMAP4](configure-pop3-and-imap4-message-retrieval-format-options-exchange-2013-help.md)

[Festlegen von Verbindungstimeout-Einschränkungen für IMAP4](set-connection-time-out-limits-for-imap4-exchange-2013-help.md)

