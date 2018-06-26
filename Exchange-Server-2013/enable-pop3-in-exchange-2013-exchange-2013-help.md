---
title: 'Aktivieren von POP3 in Exchange 2013: Exchange 2013 Help'
TOCTitle: Aktivieren von POP3
ms:assetid: e226a5f1-429d-4046-b925-da6cc151709e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124934(v=EXCHG.150)
ms:contentKeyID: 50476933
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren von POP3 in Exchange 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-03-28_

Informationen zum Aktivieren von POP3-Clientverbindungen in Exchange 2016 mithilfe von Microsoft Management Console (MMC) oder Exchange-Verwaltungsshell (EMS)

Wenn Sie Exchange Server 2016 installieren, werden die POP3-Clientverbindungen nicht aktiviert. Sie müssen zwei POP3-Dienste starten, den Microsoft Exchange POP3-Dienst und den Microsoft Exchange POP3-Back-End-Dienst, um die POP3-Clientverbindungen zu aktivieren. Wenn Sie POP3 aktivieren, akzeptiert Exchange 2016 ungesicherte POP3-Clientverbindungen an Port 110 und über Port 995 bei Verwendung von SSL (Secure Sockets Layer).

POP3- und POP3-Back-End-Dienste werden auf dem gleichen Exchange 2016-Computer mit der Postfachserverrolle verwaltet. Clientzugriffsdienste sind in Exchange 2016 Teil der Postfachserverrolle, sodass diese Dienste nicht mehr getrennt verwaltet werden müssen

Weitere Informationen zum Einrichten von POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „POP3- und IMAP4-Berechtigungen“ im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Microsoft Management Console (MMC) zum Aktivieren von POP3

Auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird:

1.  Klicken Sie im Snap-In **Dienste** in der Konsolenstruktur auf **Dienste (Lokal)**.

2.  Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf **Microsoft Exchange POP3**, und klicken Sie dann auf **Eigenschaften**.

3.  Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf **Microsoft Exchange POP3-Back-End**, und klicken Sie dann auf **Eigenschaften**.

4.  Wählen Sie auf der Registerkarte **Allgemein** unter **Starttyp** die Option **Automatisch** aus, und klicken Sie dann auf **Übernehmen**.

5.  Klicken Sie unter **Dienststatus** auf **Starten**, und klicken Sie anschließend auf **OK**.

## Verwenden von Exchange-Verwaltungsshell zum Aktivieren von POP3

Auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird:

1.  Legen Sie fest, dass der Microsoft Exchange POP3-Dienst automatisch gestartet werden soll.
    
        Set-service msExchangePOP3 -startuptype automatic

2.  Starten Sie den Microsoft Exchange POP3-Dienst.
    
        Start-service msExchangePOP3

3.  Legen Sie fest, dass der Microsoft Exchange POP3-Back-End-Dienst automatisch gestartet werden soll.
    
        Set-service msExchangePOP3BE -startuptype automatic

4.  Starten Sie den Microsoft Exchange POP3-Back-End-Dienst.
    
        Start-service msExchangePOP3BE

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Öffnen Sie auf dem Exchange 2016-Postfachserver den Windows Task-Manager. Auf der Registerkarte **Dienste** wird als Status für **MSExchangePOP3**und für **MSExchangePOP3BE** der Wert **Wird ausgeführt** angezeigt, wenn POP3 aktiviert ist.

