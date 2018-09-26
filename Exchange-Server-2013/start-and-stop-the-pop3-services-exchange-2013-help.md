---
title: 'Starten und Beenden des POP3-Diensts: Exchange 2013 Help'
TOCTitle: Starten und Beenden des POP3-Diensts
ms:assetid: 3d543921-d8c9-4d4b-99a1-82446b585ceb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997475(v=EXCHG.150)
ms:contentKeyID: 50475426
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Starten und Beenden des POP3-Diensts

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-03-13_

Standardmäßig werden die zwei POP3-Dienste, der Microsoft Exchange-POP3-Dienst und der Microsoft Exchange-POP3-Back-End-Dienst, auf Computern mit MicrosoftExchange Server 2013 nicht gestartet. Sie müssen diese zwei Dienste starten, damit Ihre E-Mail-Clients über POP3 eine Verbindung mit Exchange herstellen können. Wenn diese Dienste ausgeführt werden, akzeptiert Exchange 2013 ungesicherte POP3-Clientverbindungen an Port 110 und über Port 995 mithilfe von SSL (Secure Sockets Layer).

Der Microsoft Exchange POP3-Dienst wird auf Exchange 2013-Computern ausgeführt, auf denen die Clientzugriffs-Serverrolle ausgeführt wird. Der Microsoft Exchange POP3-Back-End-Dienst wird auf dem Exchange 2013-Computer ausgeführt, auf dem die Postfachserverrolle ausgeführt wird. In Umgebungen, in denen die Clientzugriffsrolle und die Postfachrolle auf dem gleichen Computer ausgeführt werden, verwalten Sie beide Dienste auf dem gleichen Computer.

Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3- und IMAP4-Berechtigungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Starten oder Beenden der POP3-Dienste mithilfe des Snap-ins Dienste der Microsoft-Verwaltungskonsole

So starten Sie die POP3-Dienste:

1.  Klicken Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf den Dienst **Microsoft Exchange-POP3**, und klicken Sie dann auf **Start**.

2.  Klicken Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie im Ergebnisbereich mit der rechten Maustaste auf **Microsoft Exchange-POP3-Back-End**, und klicken Sie dann auf **Start**.

So beenden Sie die POP3-Dienste:

1.  Klicken Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf den Dienst **Microsoft Exchange-POP3**, und klicken Sie dann auf **Beenden**.

2.  Klicken Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Verwaltung**, und klicken Sie anschließend auf **Dienste**. Klicken Sie mit der rechten Maustaste auf **Microsoft Exchange-POP3-Back-End**, und klicken Sie dann auf **Beenden**.

## Starten oder Beenden der POP3-Dienste mithilfe der Shell

So starten Sie die POP3-Dienste:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-POP3-Dienst zu starten.
    
    ```powershell
    Start-service MSExchangePOP3
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-POP3-Back-End-Dienst zu starten.
    
    ```powershell
    Start-service MSExchangePOP3BE
    ```

So beenden Sie die POP3-Dienste:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-POP3-Dienst zu beenden.
    
    ```powershell
    Stop-service MSExchangePOP3
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, in der Shell den folgenden Befehl aus, um den Microsoft Exchange-POP3-Back-End-Dienst zu beenden.
    
    ```powershell
    Stop-service MSExchangePOP3BE
    ```

## Starten oder Beenden der POP3-Dienste mithilfe von "net start"

So starten Sie die POP3-Dienste:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-POP3-Dienst zu starten.
    
    ```powershell
    Net Start msExchangePOP3
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-POP3-Back-End-Dienst zu starten.
    
    ```powershell
    Net Start msExchangePOP3BE
    ```

So beenden Sie die POP3-Dienste:

1.  Führen Sie auf dem Computer, auf dem die Clientzugriffs-Serverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-POP3-Dienst zu beenden.
    
    ```powershell
    Net Stop MSExchangePOP3
    ```

2.  Führen Sie auf dem Computer, auf dem die Postfachserverrolle ausgeführt wird, an der Eingabeaufforderung den folgenden Befehl aus, um den Microsoft Exchange-POP3-Back-End-Dienst zu beenden.
    
    ```powershell
    Net Stop MSExchangePOP3BE
    ```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

1.  Öffnen Sie auf dem Exchange-Clientzugriffsserver den Windows-Task-Manager. Auf der Registerkarte **Dienste** wird der Status für **MSExchangePOP3** als **Wird ausgeführt** angezeigt, wenn der Microsoft Exchange-POP3-Dienst ausgeführt wird.

2.  Öffnen Sie auf dem Exchange-Postfachserver den Windows-Task-Manager. Auf der Registerkarte **Dienste** wird der Status für **MSExchangePOP3BE** als **Wird ausgeführt** angezeigt, wenn der Microsoft Exchange-POP3-Back-End-Dienst ausgeführt wird.

