---
title: 'Konfigurieren von Nachrichtenberichten für Remotedomänen: Exchange 2013 Help'
TOCTitle: Konfigurieren von Nachrichtenberichten für Remotedomänen
ms:assetid: 73dc686a-e7a3-44c7-b82f-f52ff9273199
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649325(v=EXCHG.150)
ms:contentKeyID: 50476009
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Nachrichtenberichten für Remotedomänen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Sie können die Exchange-Verwaltungsshell verwenden, um zu konfigurieren, wie E-Mails über Remotedomänen gesendet und empfangen werden. Nachfolgend wird veranschaulicht, wie Sie mithilfe der Exchange-Verwaltungsshell konfigurieren, auf welche Weise Exchange Zustellungs- und Unzustellbarkeitsberichte verarbeitet.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Remotedomänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren von Nachrichtenberichten mithilfe der Shell

Sie können das Cmdlet **Set-RemoteDomain** verwenden, um die Eigenschaften einer Remotedomäne zu konfigurieren.

In diesem Beispiel werden Zustellungsberichte an die Remotedomäne "Contoso" deaktiviert. Diese Einstellung ist standardmäßig aktiviert.

    Set-RemoteDomain Contoso -DeliveryReportEnabled $false

In diesem Beispiel werden Unzustellbarkeitsberichte an die Remotedomäne deaktiviert. Diese Einstellung ist standardmäßig aktiviert.

    Set-RemoteDomain Contoso -NDREnabled $false

