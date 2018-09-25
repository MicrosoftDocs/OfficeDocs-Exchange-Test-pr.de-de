---
title: 'Konfigurieren von Kalenderoptionen für POP3: Exchange 2013 Help'
TOCTitle: Konfigurieren von Kalenderoptionen für POP3
ms:assetid: ac3d60a0-8697-4c06-9e93-f8d2c4b157b6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124133(v=EXCHG.150)
ms:contentKeyID: 50554894
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Kalenderoptionen für POP3

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-27_

Mithilfe der Shell können Sie Kalenderzugriffseinstellungen für Benutzer konfigurieren, die über POP3-Verbindungen eine Verbindung mit ihrem Postfach herstellen. Die festgelegten Einstellungen bestimmen, wie POP3-Benutzer auf ihren Kalender zugreifen und Kalenderinformationen mit anderen Benutzer austauschen können (z. B. beim Senden oder Beantworten einer Besprechungsanfrage).

Weitere Informationen zu POP3 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Festlegen von Kalenderoptionen für POP3 mithilfe der Shell

Dieses Beispiel ermöglicht POP3-Benutzern das Verwenden des iCalendar-Standards, der für den Austausch von Kalenderinformationen gilt.

```powershell
Set-PopSettings -Identity CAS01 -CalendarItemRetrievalOption iCalendar
```

In diesem Beispiel werden POP3-Benutzer für den Zugriff auf Kalenderinformationen über einen internen Server aktiviert.

```powershell
    Set-PopSettings -Identity CAS01 -CalendarItemRetrievalOption IntranetUrl 
```

In diesem Beispiel werden POP3-Benutzer für den Zugriff auf interne Kalenderinformationen über das Internet oder einen externen Server aktiviert.

```powershell
Set-PopSettings -CalendarItemRetrievalOption InternetUrl
```

In diesem Beispiel werden POP3-Benutzer für den Zugriff auf Kalenderinformationen mithilfe einer direkten Outlook Web App-URL aktiviert. Wenn Sie `Custom` verwenden, müssen Sie mithilfe des Parameters *OWAServerUrl* eine Outlook Web App-URL angeben.

```powershell
Set-PopSettings -CalendarItemRetrievalOption Custom -OwaServerUrl "https://OwaServer01"
```

Nachdem Sie die Kalenderoptionen für POP3 angegeben haben, müssen Sie die POP3-Dienste neu starten. Informationen zum Neustarten der POP3-Dienste finden Sie unter [Starten und Beenden des POP3-Diensts](start-and-stop-the-pop3-services-exchange-2013-help.md).

Weitere Informationen zu Syntax und Parametern finden Sie unter [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob Sie Kalenderoptionen erfolgreich festgelegt haben:

Führen Sie folgenden Befehl in der Shell aus.

```powershell
Get-PopSettings | format-list
```

Vergewissern Sie sich, dass die Kalendereinstellungen ordnungsgemäß sind.

## Weitere Informationen

Nachdem Sie die Kalenderoptionen für POP3 konfiguriert haben, können Sie die folgenden Aufgaben ausführen:

[Konfigurieren von Nachrichtenabrufformat-Optionen für POP3 und IMAP4](configure-pop3-and-imap4-message-retrieval-format-options-exchange-2013-help.md)

[Festlegen von Grenzwerten für Verbindungstimeouts für POP3](set-connection-time-out-limits-for-pop3-exchange-2013-help.md)

