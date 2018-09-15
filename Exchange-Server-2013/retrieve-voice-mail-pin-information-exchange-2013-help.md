---
title: 'Abrufen von PIN-Informationen für Voicemail: Exchange Online Help'
TOCTitle: Abrufen von PIN-Informationen für Voicemail
ms:assetid: 01517cca-99fe-46b2-b586-19e8d2707728
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa995900(v=EXCHG.150)
ms:contentKeyID: 54651492
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Abrufen von PIN-Informationen für Voicemail

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-04-03_

Sie können PIN-Informationen für einen Benutzer abrufen, der für Unified Messaging (UM) aktiviert ist. Nachdem ein Benutzer für UM aktiviert wurde und eine PIN generiert oder erstellt wurde, wird die PIN verschlüsselt und im Postfach des Benutzers gespeichert.

Wenn Sie PIN-Informationen für einen UM-aktivierten Benutzer abrufen, werden die Informationen, die an Sie zurückgegeben werden, mithilfe der verschlüsselten PIN-Daten im Postfach des Benutzers berechnet. Mit diesem Task können Sie Informationen aus dem Postfach des Benutzers anzeigen. Er gibt außerdem an, ob der Benutzer für sein Postfach gesperrt wurde.

Weitere Aufgaben im Zusammenhang mit PIN-Sicherheit finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wähleinstellungen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Genaue Anweisungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass das Postfach des Benutzers UM-aktiviert wurde. Genaue Anweisungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Abrufen von PIN-Informationen für einen UM-aktivierten Benutzer

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**. Wählen Sie in der Listenansicht das Benutzerpostfach aus, das angezeigt werden soll.

2.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** auf **Details anzeigen**.

3.  Lassen Sie auf der Seite **UM-Postfach** \> **UM-Postfacheinstellungen** den **PIN-Status** für den Benutzer anzeigen. Auf dieser Seite können Sie außerdem die Voicemail-PIN für den Benutzer zurücksetzen.

## Verwenden der Shell zum Abrufen von PIN-Informationen für einen UM-aktivierten Benutzer

In diesem Beispiel wird die Benutzer-ID angezeigt sowie die Information, ob eine PIN abgelaufen ist, ob das UM-Postfach gesperrt wurde und ob Thorsten zum ersten Mal als Benutzer auftritt.

    Get-UMMailboxPIN -identity tony@contoso.com

