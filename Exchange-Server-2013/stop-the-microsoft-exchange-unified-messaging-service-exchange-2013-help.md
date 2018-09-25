---
title: 'Beenden des Microsoft Exchange Unified Messaging-Diensts: Exchange 2013 Help'
TOCTitle: Beenden des Microsoft Exchange Unified Messaging-Diensts
ms:assetid: 64fa5535-8150-45c6-82e6-d2346892a031
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998595(v=EXCHG.150)
ms:contentKeyID: 50554827
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Beenden des Microsoft Exchange Unified Messaging-Diensts

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-16_

Zum Beenden des MicrosoftExchange Unified Messaging-Diensts auf einem Postfachserver können Sie das Dienste-Snap-In in Microsoft Management Console (MMC) oder den Befehl "cmd.exe" an einer Eingabeaufforderung verwenden. Mitunter kann es notwendig sein, diesen Dienst zu beenden, z. B. wenn Sie den Postfachserver offline schalten. Wenn Sie den MicrosoftExchange Unified Messaging-Dienst beenden, kann der Postfachserver eingehende Anrufe nicht annehmen und verarbeiten.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Postfachservern finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Um die folgenden Verfahren ausführen zu können, müssen Sie sich beim Postfachserver mit einem Konto anmelden, das ein Mitglied der lokalen Administratorgruppe ist.

  - Stellen Sie sicher, dass der Postfachserver auf dem gleichen Computer wie der Clientzugriffsserver oder auf einem gesonderten Computer installiert ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]  
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden des MMC-Snap-Ins "Dienste", um den Microsoft Exchange Unified Messaging-Dienst zu beenden

1.  Klicken Sie auf **Start** und dann auf **Systemsteuerung**.

2.  Doppelklicken Sie in der Systemsteuerung auf **Verwaltung**.

3.  Doppelklicken Sie in **Verwaltung** auf **Dienste**.

4.  Klicken Sie im Detailbereich **Dienste** mit der rechten Maustaste auf **Microsoft Exchange Unified Messaging**, und klicken Sie dann auf **Beenden**.

## Verwenden der Befehlszeile, um den Microsoft Exchange Unified Messaging-Dienst zu beenden

1.  Klicken Sie auf **Start**, und klicken Sie dann auf **Ausführen**.

2.  Geben Sie im Textfeld **Öffnen** den folgenden Befehl ein, und drücken Sie dann die EINGABETASTE.
    
    ```powershell
    net stop MSExchangeUM
    ```

