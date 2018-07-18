---
title: 'Archivieren von Lync-Unterhaltungen und Besprechungsinhalten in Exchange: Exchange 2013 Help'
TOCTitle: Archivieren von Lync-Unterhaltungen und Besprechungsinhalten in Exchange
ms:assetid: 3cff970e-e5ed-4a54-88e6-3665d84b5ed7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn508399(v=EXCHG.150)
ms:contentKeyID: 59678841
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Archivieren von Lync-Unterhaltungen und Besprechungsinhalten in Exchange

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können Lync Online-Inhalte wie Chatunterhaltungen im Exchange Online-Postfach eines Benutzers archivieren. In lokalen Bereitstellungen können Sie Lync 2013-Inhalte in Exchange 2013-Postfächern archivieren. Sowohl in Onlineumgebungen als auch in lokalen Umgebungen müssen Sie dazu das betreffende Benutzerpostfach in ein Beweissicherungsverfahren einbinden oder einen In-Situ-Speicher für das Postfach einrichten. Löscht ein Benutzer, dessen Postfach in ein Beweissicherungsverfahren eingebunden oder mit einem In-Situ-Speicher konfiguriert wurde, Lync-Inhalte endgültig, werden die archivierten Lync-Inhalte im Ordner „Wiederherstellbare Elemente“ in seinem Postfach aufbewahrt. Dieser Ordner ist für den Benutzer unsichtbar, wird aber in eDiscovery-Suchen einbezogen.

Wenn Sie ein Postfach in ein Beweissicherungsverfahren einbinden, werden alle Inhaltstypen aufbewahrt, einschließlich Lync-Elementen. Standardmäßig ist dies ebenfalls der Fall, wenn Sie einen In-Situ-Speicher erstellen. Wenn Sie in einem In-Situ-Speicher ausschließlich Lync-Elemente aufbewahren möchten, können Sie unter der Option **Nachrichtentypen auswählen** im Assistenten **In-Situ-eDiscovery und -Speicher** das Kontrollkästchen **Lync items** aktivieren (siehe Screenshot unten).

![Lync-Elemente in Archivpostfächern platzieren](images/Dn508399.691d2324-9fac-4689-8527-c78d387e0e3e(EXCHG.150).jpg "Lync-Elemente in Archivpostfächern platzieren")


> [!NOTE]
> Sie können einen In-Situ-Speicher auch so konfigurieren, dass Lync-Elemente ausgenommen werden. So könnte es beispielsweise sein, dass eine Organisation Chatnachrichten und Voicemails nicht so lange aufbewahren möchte wie andere Inhaltstypen. Zur Einrichtung einer entsprechenden Richtlinie würden Sie einen In-Situ-Speicher erstellen, in dem Inhalte über einen langen Zeitraum hinweg aufbewahrt werden (z.&nbsp;B. 7&nbsp;Jahre), und Lync-Elemente von der Aufbewahrung ausnehmen. Anschließend würden Sie einen weiteren In-Situ-Speicher mit einer kürzeren Aufbewahrungszeit erstellen, in dem nur Lync-Elemente aufbewahrt werden. Sie können auch festlegen, wie lange die Inhalte aufbewahrt werden sollen. Weitere Informationen dazu, wie Sie einen In-Situ-Speicher oder ein Beweissicherungsverfahren mit einer bestimmten Aufbewahrungsdauer erstellen, finden Sie unter <A href="in-place-hold-and-litigation-hold-exchange-2013-help.md">In-Place Hold and Litigation Hold</A>.



Schritt-für-Schritt-Anleitungen für die Erstellung eines In-Situ-Speichers und die Einbindung in ein Beweissicherungsverfahren finden Sie in den folgenden Artikeln:

  - [Erstellen oder Entfernen eines Compliance-Archivs](create-or-remove-an-in-place-hold-exchange-2013-help.md)

  - [Aktivieren des Beweissicherungsverfahrens für ein Postfach](place-a-mailbox-on-litigation-hold-exchange-2013-help.md)

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Archivierung finden Sie unter:

  - [Aktivieren oder Deaktivieren eines Archivpostfachs in Exchange Online](https://technet.microsoft.com/de-de/library/jj984357\(v=exchg.150\))

  - [Verwalten von In-Situ-Archiven in Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md)

## Weitere Informationen

  - Die Lync-Inhalte werden auf dem Server archiviert, und zwar unabhängig davon, ob der Benutzer den Lync-Client so konfiguriert hat, dass [Lync-Chatunterhaltungen im Ordner „Aufgezeichnete Unterhaltungen“ gespeichert werden](https://go.microsoft.com/fwlink/p/?linkid=400589).

  - Die Archivierung der Lync-Inhalte beginnt, sobald der Benutzer in ein Beweissicherungsverfahren eingebunden wurde bzw. sobald ein In-Situ-Speicher erstellt wurde. Soll die gesamte Lync-Kommunikation eines Benutzers ab dem Zeitpunkt der Kontoerstellung archiviert werden, müssen Sie das Konto unmittelbar nach seiner Erstellung in ein Beweissicherungsverfahren einbinden bzw. unmittelbar nach der Kontoerstellung einen In-Situ-Speicher einrichten.

Folgendes gilt zusätzlich in lokalen Exchange 2013- und Lync 2013-Bereitstellungen:

  - Sie müssen die OAuth-Authentifizierung zwischen Lync 2013 und Exchange 2013 konfigurieren. Details hierzu finden Sie unter [Integration in SharePoint und Lync](integration-with-sharepoint-and-lync-exchange-2013-help.md).

  - Sie können Lync 2013-Inhalte auch in Exchange 2013 archivieren, ohne den betreffenden Benutzer in ein Beweissicherungsverfahren einzubinden oder einen In-Situ-Speicher zu erstellen. Dazu müssen Sie die Exchange-Archivierungsrichtlinie für den Benutzer konfigurieren. Verwenden Sie das Cmdlet `Set-CsUser` auf dem Lync 2013-Server, um die Eigenschaft *ExchangeArchivingPolicy* des Lync-Benutzers auf `ArchivingToExchange` zu setzen.

  - Weitere Details zur Archivierung von Lync-Inhalten in lokalen Bereitstellungen finden Sie im Artikel zum Thema [Planen der Archivierung](https://go.microsoft.com/fwlink/p/?linkid=400590) in der Lync 2013-Dokumentation.

