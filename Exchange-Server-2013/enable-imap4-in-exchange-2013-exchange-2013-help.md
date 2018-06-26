---
title: 'Aktivieren von IMAP4 in Exchange 2016: Exchange 2013 Help'
TOCTitle: Aktivieren von IMAP4 in Exchange 2016
ms:assetid: c1ae10dd-14da-4400-b38d-2aeafde8abe6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124489(v=EXCHG.150)
ms:contentKeyID: 50476643
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren von IMAP4 in Exchange 2016

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-06-02_

Informationen zum Aktivieren von IMAP4-Clientverbindungen in Exchange 2016 mithilfe von Microsoft Management Console (MMC) oder Exchange-Verwaltungsshell (EMS)

Nach der Installation von Exchange Server 2016 sind IMAP4-Clientverbindungen nicht aktiviert. Zum Aktivieren der IMAP4-Clientverbindungen müssen Sie zwei IMAP-Dienste starten, den Microsoft Exchange-IMAP4-Dienst und den Microsoft Exchange IMAP4-Back-End-Dienst. Wenn Sie IMAP4 aktivieren, akzeptiert Exchange 2016 ungesicherte IMAP4-Clientkommunikationen an Port 143 und über Port 993 mithilfe von SSL (Secure Sockets Layer).

IMAP4- und IMAP4-Back-End-Dienste werden auf dem gleichen Exchange 2016-Computer mit der Postfachserverrolle verwaltet. Clientzugriffsdienste sind in Exchange 2016 Teil der Postfachserverrolle, sodass diese Dienste nicht mehr getrennt verwaltet werden müssen

Weitere Informationen zum Einrichten von POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „POP3- und IMAP4-Berechtigungen“ im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Microsoft Management Console (MMC) zum Aktivieren von IMAP4

Auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird:

1.  Klicken Sie im Snap-In **Dienste** in der Konsolenstruktur auf **Dienste (Lokal)**.

2.  Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf **Microsoft Exchange IMAP4**, und klicken Sie dann auf **Eigenschaften**.

3.  Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf **Microsoft Exchange IMAP4-Back-End**, und klicken Sie dann auf **Eigenschaften**.

4.  Wählen Sie auf der Registerkarte **Allgemein** unter **Starttyp** die Option **Automatisch** aus, und klicken Sie dann auf **Übernehmen**.

5.  Klicken Sie unter **Dienststatus** auf **Starten**, und klicken Sie anschließend auf **OK**.

## Verwenden von Exchange-Verwaltungsshell zum Aktivieren von IMAP4

Auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird:

1.  Geben Sie an, dass der Microsoft Exchange-IMAP4-Dienst automatisch gestartet wird.
    
        Set-service msExchangeIMAP4 -startuptype automatic

2.  Starten Sie den Microsoft Exchange-IMAP4-Dienst.
    
        Start-service msExchangeIMAP4

3.  Geben Sie an, dass der Microsoft Exchange-IMAP4-Back-End-Dienst automatisch gestartet werden soll.
    
        Set-service msExchangeIMAP4BE -startuptype automatic

4.  Starten Sie den Microsoft Exchange-IMAP4-Back-End-Dienst.
    
        Start-service msExchangeIMAP4BE

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Öffnen Sie auf dem Exchange 2016-Postfachserver den Windows Task-Manager. Auf der Registerkarte **Dienste** wird als Status von **MSExchangeIMAP4** und **MSExchangeIMAP4BE** der Eintrag **Wird ausgeführt** angezeigt, wenn IMAP4 aktiviert ist.

