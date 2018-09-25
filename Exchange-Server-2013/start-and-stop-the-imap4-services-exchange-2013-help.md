---
title: 'Starten und Stoppen der IMAP4-Dienste: Exchange 2013 Help'
TOCTitle: Starten und Stoppen der IMAP4-Dienste
ms:assetid: a52db4bd-69a6-47b2-acf3-d9d8571c7a87
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124022(v=EXCHG.150)
ms:contentKeyID: 50476384
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Starten und Stoppen der IMAP4-Dienste

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-05_

Standardmäßig werden die beiden IMAP4 -Dienste, der Microsoft Exchange-IMAP4-Dienst und der Microsoft Exchange-IMAP4-Back-End-Dienst, auf Computern mit MicrosoftExchange Server 2013 nicht gestartet. Sie müssen diese zwei Dienste starten, damit Ihre E-Mail-Clients über IMAP4 eine Verbindung mit Exchange herstellen können. Wenn diese Dienste ausgeführt werden, akzeptiert Exchange 2013 ungesicherte IMAP4-Clientverbindungen auf Port 143 und über Port 993 mithilfe von SSL (Secure Sockets Layer).

Der Microsoft Exchange IMAP4-Dienst wird auf Exchange 2013-Computern ausgeführt, auf denen die Clientzugriffs-Serverrolle ausgeführt wird. Der Microsoft Exchange IMAP4-Back-End-Dienst wird auf dem Exchange 2013-Computer ausgeführt, auf dem die Postfachserverrolle ausgeführt wird. In Umgebungen, in denen die Clientzugriffs-Serverrolle und die Postfachserverrolle auf dem gleichen Computer ausgeführt werden, verwalten Sie beide Dienste auf dem gleichen Computer.

Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3- und IMAP4-Berechtigungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Starten oder Beenden der IMAP4-Dienste mithilfe des Snap-ins "Dienste" der Microsoft-Verwaltungskonsole

So starten Sie die IMAP4-Dienste:

1.  Klicken Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf **Microsoft Exchange-IMAP4**, und klicken Sie dann auf **Start**.

2.  Klicken Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf **Microsoft Exchange-IMAP4-Back-End**, und klicken Sie dann auf **Start**.

So halten Sie die IMAP4-Dienste an:

1.  Klicken Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf **Microsoft Exchange-IMAP4**, und klicken Sie dann auf **Beenden**.

2.  Klicken Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf **Microsoft Exchange-IMAP4-Back-End**, und klicken Sie dann auf **Beenden**.

## Starten oder Beenden der IMAP4-Dienste mithilfe der Shell

So starten Sie die IMAP4-Dienste:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Dienst zu starten.
    
    ```powershell
    Start-service msExchangeIMAP4
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Back-End-Dienst zu starten.
    
    ```powershell
    Start-service msExchangeIMAP4BE
    ```

So halten Sie die IMAP4-Dienste an:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Dienst zu beenden.
    
    ```powershell
    Stop-service msExchangeIMAP4
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Back-End-Dienst zu beenden.
    
    ```powershell
    Stop-service msExchangeIMAP4BE
    ```

## Starten und Beenden der IMAP4-Dienste mithilfe von "net start"

So starten Sie die IMAP4-Dienste:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Dienst zu starten.
    
    ```powershell
    net start msExchangeIMAP4
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Back-End-Dienst zu starten.
    
    ```powershell
    net start msExchangeIMAP4BE
    ```

So halten Sie die IMAP4-Dienste an:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Dienst zu beenden.
    
    ```powershell
    Net Stop MSExchangeIMAP4
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-IMAP4-Back-End-Dienst zu beenden.
    
    ```powershell
    Net Stop MSExchangeIMAP4BE
    ```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

1.  Öffnen Sie auf dem Exchange-Clientzugriffsserver den Windows-Task-Manager. Auf der Registerkarte **Dienste** wird der Status für **MSExchangeIMAP4** als **Wird ausgeführt** angezeigt, wenn der Microsoft Exchange-IMAP4-Dienst ausgeführt wird.

2.  Öffnen Sie auf dem Exchange-Postfachserver den Windows-Task-Manager. Auf der Registerkarte **Dienste** wird der Status für **MSExchangeIMAP4BE** als **Wird ausgeführt** angezeigt, wenn der Microsoft Exchange-IMAP4-Dienst ausgeführt wird.

