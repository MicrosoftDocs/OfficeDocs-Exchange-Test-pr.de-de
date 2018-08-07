---
title: 'Konfig. d. PICKUP-Verzeich. und d. Wiedergabeverzeichn.: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren des PICKUP-Verzeichnisses und des Wiedergabeverzeichnisses
ms:assetid: c9ca7358-9a08-4f57-89d0-910e4438df8a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124549(v=EXCHG.150)
ms:contentKeyID: 50476684
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren des PICKUP-Verzeichnisses und des Wiedergabeverzeichnisses

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die PICKUP- und Wiedergabeverzeichnisse werden vom Transportdienst auf Postfachservern und Edge-Transport-Servern verwendet, um Nachrichten direkt in die Transportpipeline einzufügen. Ordnungsgemäß formatierte E-Mails, die in das PICKUP- oder Wiedergabeverzeichnis kopiert werden, werden zur Zustellung übermittelt. Das PICKUP-Verzeichnis wird von Administratoren zum Testen der Nachrichtenübermittlung oder von Anwendungen verwendet, die ihre eigenen Nachrichten erstellen und senden müssen. Das Wiedergabeverzeichnis empfängt Nachrichten von fremden Gatewayservern, die kein SMTP verwenden, und übermittelt Nachrichten erneut, die Sie aus den Warteschlangen der Microsoft Exchange-Server exportiert haben.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportdienst" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Der Wert des Parameters *PickupDirectoryMaxMessagesPerMinute* im Cmdlet **Set-TransportService** wird von den PICKUP- und Wiedergabeverzeichnissen verwendet.

  - Durch das Ändern des Speicherorts für die PICKUP- oder Wiedergabeverzeichnisse werden keine vorhandenen Nachrichtendateien aus dem alten Speicherort in den neuen Speicherort kopiert. Der neue Speicherort für das PICKUP- oder Wiedergabeverzeichnis gilt unmittelbar nach der Konfigurationsänderung, vorhandene Nachrichtendateien werden jedoch am alten Speicherort belassen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie tun?

## Konfigurieren des PICKUP-Verzeichnisses mithilfe der Shell

Verwenden Sie folgende Syntax, um das PICKUP-Verzeichnis zu konfigurieren.

    Set-TransportService <ServerIdentity> -PickupDirectoryPath <LocalFilePath> -PickupDirectoryMaxHeaderSize <Size> -PickupDirectoryMaxRecipientsPerMessage <Integer> -PickupDirectoryMaxMessagesPerMinute <Integer>

In diesem Beispiel werden die folgenden Änderungen am PICKUP-Verzeichnis auf dem Postfachserver "Exchange01" vorgenommen:

  - Der Speicherort des PICKUP-Verzeichnisses wird auf "D:\\Pickup Directory" festgelegt.

  - Die maximal zulässige Größe für Nachrichtenköpfe in einer Nachrichtendatei wird auf 96 KB erweitert.

  - Die maximal zulässige Anzahl von Empfängern in einer Nachrichtendatei wird auf 250 erhöht.

  - Die maximale Anzahl von Nachrichten, die für das PICKUP- und das Wiedergabeverzeichnis verarbeitet werden dürfen, wurde auf 200 Nachrichten pro Minute angehoben.

<!-- end list -->

    Set-TransportService Exchange01 -PickupDirectoryPath "D:\Pickup Directory" -PickupDirectoryMaxHeaderSize 96KB -PickupDirectoryMaxRecipientsPerMessage 250 -PickupDirectoryMaxMessagesPerMinute 200


> [!NOTE]
> <UL>
> <LI>
> <P>Wenn Sie den Parameter <EM>PickupDirectoryPath</EM> auf den Wert <CODE>$null</CODE> festlegen, wird das PICKUP-Verzeichnis deaktiviert.</P>
> <LI>
> <P>Die von den Parametern <EM>PickupDirectoryPath</EM> und <EM>ReplayDirectoryPath</EM> angegebenen Verzeichnisse dürfen nicht identisch sein.</P></LI></UL>



## Konfigurieren des Wiedergabeverzeichnisses mithilfe der Shell

Verwenden Sie folgende Syntax, um das Wiedergabeverzeichnis zu konfigurieren.

    Set-TransportService <ServerIdentity> -ReplayDirectoryPath "C:\Replay Directory" <LocalFilePath> -PickupDirectoryMaxMessagesPerMinute <Integer>

In diesem Beispiel werden die folgenden Änderungen am Wiedergabeverzeichnis auf dem Postfachserver "Exchange01" vorgenommen:

  - Der Speicherort des Wiedergabeverzeichnisses wird auf "D:\\Replay Directory" festgelegt.

  - Die maximale Anzahl von Nachrichten, die für das PICKUP- und das Wiedergabeverzeichnis verarbeitet werden dürfen, wurde auf 200 Nachrichten pro Minute angehoben.

<!-- end list -->

    Set-TransportService Exchange01 -ReplayDirectoryPath "D:\Replay Directory" -PickupDirectoryMaxMessagesPerMinute 200


> [!NOTE]
> <UL>
> <LI>
> <P>Wenn Sie den Parameter <EM>ReplayDirectoryPath</EM> auf den Wert <CODE>$null</CODE> festlegen, wird das Wiedergabeverzeichnis deaktiviert.</P>
> <LI>
> <P>Die von den Parametern <EM>PickupDirectoryPath</EM> und <EM>ReplayDirectoryPath</EM> angegebenen Verzeichnisse dürfen nicht identisch sein.</P></LI></UL>



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie die PICKUP- und Wiedergabeverzeichnisse erfolgreich konfiguriert haben:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-TransportService <ServerIdentity> | Format-List Pickup*,Replay*

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

