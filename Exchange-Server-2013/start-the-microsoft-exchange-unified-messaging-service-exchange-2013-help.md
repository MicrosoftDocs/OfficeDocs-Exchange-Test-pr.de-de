---
title: 'Starten des Microsoft Exchange Unified Messaging-Diensts: Exchange 2013 Help'
TOCTitle: Starten des Microsoft Exchange Unified Messaging-Diensts
ms:assetid: b54008e6-172e-4435-8516-57cff740e89c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124330(v=EXCHG.150)
ms:contentKeyID: 50554909
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Starten des Microsoft Exchange Unified Messaging-Diensts

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2012-11-16_

Zum Starten des MicrosoftExchange Unified Messaging-Diensts auf einem Postfachserver können Sie das Snap-In **Dienste** in Microsoft Management Console (MMC) oder den Befehl **cmd.exe** an einer Eingabeaufforderung verwenden. Standardmäßig wird der MicrosoftExchange Unified Messaging-Dienst gestartet, nachdem ein Postfachserver installiert wurde. Es kann jedoch vorkommen, dass der Microsoft Exchange Unified Messaging-Dienst manuell neu gestartet werden muss, z. B. wenn der Postfachserver offline geschaltet wurde und nun wieder online geschaltet werden soll.

Wenn der MicrosoftExchange Unified Messaging-Dienst auf einem Postfachserver gestartet wird, steht der Postfachserver für die Verarbeitung eingehender UM-Anrufe zur Verfügung.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Postfachserver finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Um die folgenden Verfahren ausführen zu können, müssen Sie sich beim Postfachserver mit einem Konto anmelden, das Mitglied der lokalen Gruppe "Administratoren" ist.

  - Stellen Sie sicher, dass der Postfachserver installiert ist, entweder auf demselben Computer wie der Clientzugriffsserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Starten des Microsoft Exchange Unified Messaging-Diensts mithilfe des MMC-Snap-Ins "Dienste"

1.  Klicken Sie auf **Start** und dann auf **Systemsteuerung**.

2.  Doppelklicken Sie in der Systemsteuerung auf **Verwaltung**.

3.  Doppelklicken Sie in **Verwaltung** auf **Dienste**.

4.  Klicken Sie im Detailbereich **Dienste** mit der rechten Maustaste auf **Microsoft Exchange Unified Messaging**, und klicken Sie dann auf **Starten**.

## Starten des Microsoft Exchange Unified Messaging-Diensts mithilfe einer Eingabeaufforderung

1.  Klicken Sie auf **Start**, und klicken Sie dann auf **Ausführen**.

2.  Geben Sie im Textfeld **Öffnen** die folgende Zeichenfolge ein, und drücken Sie dann die EINGABETASTE.
    
        net start MSExchangeUM

