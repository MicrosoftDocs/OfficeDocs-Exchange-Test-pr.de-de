---
title: 'Durchsuchen von Nachrichtenverfolgungsprotokollen: Exchange 2013 Help'
TOCTitle: Durchsuchen von Nachrichtenverfolgungsprotokollen
ms:assetid: e1678327-bcd5-42d4-a363-67f33067fe9a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124926(v=EXCHG.150)
ms:contentKeyID: 51409354
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Durchsuchen von Nachrichtenverfolgungsprotokollen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-02-25_

In Microsoft Exchange Server 2013 ist das Nachrichtenverfolgungsprotokoll eine detaillierte Aufzeichnung aller Nachrichtenaktivitäten, d. h. Übertragungen in und aus dem Transportdienst auf Postfachservern, Postfächern auf Postfachservern und Edge-Transport-Servern.

Über das Cmdlet **Get-MessageTrackingLog** in der Exchange-Verwaltungsshell können Sie anhand bestimmter Suchkriterien nach Einträgen im Nachrichtenverfolgungsprotokoll suchen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Nachrichtenverfolgung" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Zum Durchsuchen der Nachrichtenverfolgungsprotokolle muss der Microsoft Exchange Transportprotokoll-Suchdienst ausgeführt werden. Wenn Sie diesen Dienst deaktivieren oder anhalten, können die Protokolldateien der Nachrichtenverfolgung nicht durchsucht und keine Zustellungsberichte erstellt werden. Das Anhalten dieses Diensts hat jedoch keine Auswirkungen auf andere Funktionen in Exchange.

  - Die in den Ergebnissen des Cmdlets **Get-MessageTrackingLog** angezeigten Feldnamen ähneln den tatsächlichen Feldnamen, die in den Nachrichtenverfolgungsprotokollen verwendet werden. Die größten Unterschiede:
    
      - Die Striche werden aus den Feldnamen entfernt. Beispiel: **internal-message-id** wird angezeigt als `InternalMessageId`.
    
      - Das Feld **date-time** wird angezeigt als `Timestamp`.
    
      - Das Feld **recipient-address** wird als `Recipients` angezeigt.
    
      - Das Feld **sender-address** wird als `Sender` angezeigt.

  - Das **date-time**-Feld im Nachrichtenverfolgungsprotokoll speichert Informationen im UTC-Format (Coordinated Universal Time). Sie sollten die Suchkriterien für Datum und Uhrzeit für die Parameter *Start* oder *End* jedoch im regionalen Datums- und Uhrzeitformat des Computers eingeben, den Sie zum Durchführen des Suchvorgangs verwenden.

  - Sie können nicht die Nachrichtenverfolgungsprotokoll-Dateien von einem anderen Exchange-Server kopieren und diese anschließend mit dem Cmdlet **Get-MessageTrackingLog** durchsuchen. Wenn Sie außerdem eine vorhandene Nachrichtenverfolgungsprotokoll-Datei manuell speichern, unterbricht die Änderung am Datum-/Uhrzeitstempel die Abfragelogik, die Exchange zum Durchsuchen der Nachrichtenverfolgungsprotokolle nutzt.

  - Das Cmdlet Exchange 2013**Get-MessageTrackingLog** dient zum Durchsuchen der Nachrichtenverfolgungsprotokolle auf Exchange 2007- und Exchange 2010-Servern am selben Active Directory-Standort.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Durchsuchen der Nachrichtenverfolgungsprotokolle

Wählen Sie zum Durchsuchen der Einträge in den Nachrichtenverfolgungsprotokollen auf bestimmte Ereignisse die folgende Syntax.

    Get-MessageTrackingLog [-Server <ServerIdentity.] [-ResultSize <Integer> | Unlimited] [-Start <DateTime>] [-End <DateTime>] [-EventId <EventId>] [-InternalMessageId <InternalMessageId>] [-MessageId <MessageId>] [-MessageSubject <Subject>] [-Recipients <RecipientAddress1,RecipientAddress2...>] [-Reference <Reference>] [-Sender <SenderAddress>]

Führen Sie den folgenden Befehl aus, um die 1000 neuesten Nachrichtenverfolgungsprotokoll-Einträge auf dem Server anzuzeigen:

    Get-MessageTrackingLog

Dieses Beispiel durchsucht die Nachrichtenverfolgungsprotokolle auf dem lokalen Server nach allen Einträgen vom 28.03.2013 8:00 Uhr bis 28.03.2013 17:00 Uhr nach Ereignissen vom Typ **FAIL**, bei denen der Absender der Nachricht "pat@contoso.com" war.

    Get-MessageTrackingLog -ResultSize Unlimited -Start "3/28/2013 8:00AM" -End "3/28/2013 5:00PM" -EventId "Fail" -Sender "pat@contoso.com"

## Verwenden der Shell zum Steuern der Ausgabe der Suche in einem Nachrichtenverfolgungsprotokoll

Verwenden Sie die folgende Syntax.

    Get-MessageTrackingLog <SearchFilters> | <Format-Table | Format-List> [<FieldNames>] [<OutputFileOptions>]

In diesem Beispiel werden die Nachrichtenverfolgungsprotokolle mithilfe der folgenden Suchkriterien durchsucht:

  - Ergebnisse für die ersten 1000 **Send**-Ereignisse zurückgeben.

  - Die Ergebnisse im Listenformat anzeigen.

  - Nur die Feldnamen anzeigen, die mit `Send` oder `Recipient` beginnen.

  - Die Ausgabe in eine neue Datei namens `D:\Send Search.txt` schreiben

<!-- end list -->

    Get-MessageTrackingLog -EventId Send | Format-List Send*,Recipient* > "D:\Send Search.txt"

## Verwenden der Shell zum Durchsuchen der Nachrichtenverfolgungsprotokolle nach Nachrichteneinträgen auf mehreren Servern

In der Regel bleibt der Wert im Kopfzeilenfeld **MessageID:** unverändert, während die Nachricht die Exchange-Organisation durchläuft. Diese Eigenschaft heißt **InternetMessageId** in Hilfsprogrammen zum Anzeigen von Warteschlagen und **MessageId** in Hilfsprogrammen zum Anzeigen von Nachrichtenverfolgungsprotokollen. Nachdem Sie den `MessageID:`-Wert einer bestimmten Nachricht ermittelt haben, können Sie Informationen zu dieser Nachricht in den Nachrichtenverfolgungsprotokollen auf allen Postfachservern in Ihrer Exchange-Produkt suchen.

Wählen Sie zum Durchsuchen aller Einträge in den Nachrichtenverfolgungsprotokollen nach einer bestimmten Nachricht auf allen Postfachservern die folgende Syntax.

    Get-ExchangeServer | where {$_.isHubTransportServer -eq $true -or $_.isMailboxServer -eq $true} | Get-MessageTrackingLog -MessageId <MessageID> | Select-Object <CommaSeparatedFieldNames> | Sort-Object -Property <FieldName>

In diesem Beispiel werden die Nachrichtenverfolgungsprotokolle auf allen Exchange 2013-Postfachservern mithilfe der folgenden Suchkriterien durchsucht:

  - Einträge in Bezug auf eine Nachricht finden, die den **MessageID:** -Wert `<ba18339e-8151-4ff3-aeea-87ccf5fc9796@mailbox01.contoso.com>` hat. Sie können die eckigen Klammern weglassen (`<``>`). Falls nicht, müssen Sie den gesamten **MessageID:**-Wert in Anführungszeichen setzen. -Wert in Anführungszeichen setzen.

  - Für jeden Eintrag die Felder **date-time**, **server-hostname**, **client-hostname**, **source**, **event-id** und **recipient-address** anzeigen.

  - Die Ergebnisse nach dem **date-time**-Feld sortieren.

<!-- end list -->

    Get-ExchangeServer | where {$_.isHubTransportServer -eq $true -or $_.isMailboxServer -eq $true} | Get-MessageTrackingLog -MessageId ba18339e-8151-4ff3-aeea-87ccf5fc9796@mailbox01.contoso.com | Select-Object Timestamp,ServerHostname,ClientHostname,Source,EventId,Recipients | Sort-Object -Property Timestamp

## Durchsuchen der Nachrichtenverfolgungsprotokolle mithilfe der Exchange-Verwaltungskonsole

Sie können über die Funktion "Zustellungsberichte für Administratoren" in der Exchange-Verwaltungskonsole die Nachrichtenverfolgungsprotokolle nach Informationen zu Nachrichten durchsuchen, die von einem bestimmten Postfach in Ihrer Organisation gesendet oder empfangen wurden. Weitere Informationen finden Sie unter [Nachverfolgen von Nachrichten mit Zustellungsberichten](track-messages-with-delivery-reports-exchange-2013-help.md).

