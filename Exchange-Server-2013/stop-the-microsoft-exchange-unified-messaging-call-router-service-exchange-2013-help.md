---
title: 'Beenden des Microsoft Exchange Unified Messaging-Anrufrouterdiensts: Exchange 2013 Help'
TOCTitle: Beenden des Microsoft Exchange Unified Messaging-Anrufrouterdiensts
ms:assetid: 79935528-1a8c-4f22-826c-8f9a60f4f6f4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673535(v=EXCHG.150)
ms:contentKeyID: 50554846
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Beenden des Microsoft Exchange Unified Messaging-Anrufrouterdiensts

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-16_

Zum Beenden des MicrosoftExchange Unified Messaging-Anrufrouterdiensts auf einem Clientzugriffsserver können Sie das Snap-In "Dienste" in Microsoft Management Console (MMC) oder den Befehl "cmd.exe" an einer Eingabeaufforderung verwenden. Mitunter kann es notwendig sein, diesen Dienst zu beenden, z. B. wenn Sie den Clientzugriffsserver offline schalten müssen. Wenn Sie den Microsoft Exchange Unified Messaging-Anrufrouterdienst beenden, kann der Clientzugriffsserver eingehende Anrufe nicht annehmen und verarbeiten.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Clientzugriffsserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Um die folgenden Verfahren ausführen zu können, müssen Sie sich beim Clientzugriffsserver mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" ist.

  - Stellen Sie sicher, dass der Clientzugriffsserver installiert ist, entweder auf demselben Computer wie der Postfachserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden des MMC-Snap-Ins "Dienste", um den Microsoft Exchange Unified Messaging-Anrufrouterdienst zu beenden

1.  Klicken Sie auf **Start** und dann auf **Systemsteuerung**.

2.  Doppelklicken Sie in der Systemsteuerung auf **Verwaltung**.

3.  Doppelklicken Sie in **Verwaltung** auf **Dienste**.

4.  Klicken Sie im Detailbereich **Dienste** mit der rechten Maustaste auf **Microsoft Exchange Unified Messaging-Anrufrouter**, und klicken Sie dann auf **Beenden**.

## Beenden des Microsoft Exchange Unified Messaging-Anrufrouterdiensts über eine Befehlszeile

1.  Klicken Sie auf **Start**, und klicken Sie dann auf **Ausführen**.

2.  Geben Sie im Textfeld **Öffnen** die folgende Zeichenfolge ein, und drücken Sie dann die EINGABETASTE.
    
        net stop MSExchangeUMCR

