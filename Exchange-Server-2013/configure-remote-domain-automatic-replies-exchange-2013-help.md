---
title: 'Konfigurieren von automatischen Antworten für die Remotedomäne: Exchange 2013 Help'
TOCTitle: Konfigurieren von automatischen Antworten für die Remotedomäne
ms:assetid: 3d88a1fb-4b62-419a-a50d-ffd868e229d0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657720(v=EXCHG.150)
ms:contentKeyID: 50475433
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von automatischen Antworten für die Remotedomäne

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können die Exchange-Verwaltungsshell verwenden, um zu konfigurieren, wie E-Mails über Remotedomänen gesendet und empfangen werden. Nachfolgend wird veranschaulicht, wie Sie mithilfe der Exchange-Verwaltungsshell konfigurieren, wie Exchange automatische Antworten verarbeitet.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 10 Minuten

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Remotedomänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren automatischer Antworten mithilfe der Shell

Sie können das Cmdlet **Set-RemoteDomain** verwenden, um die Eigenschaften einer Remotedomäne zu konfigurieren.

In diesem Beispiel werden automatische Antworten an die Remotedomäne "Contoso" zugelassen. Diese Einstellung ist standardmäßig deaktiviert.

    Set-RemoteDomain Contoso -AutoReplyEnabled $true

In diesem Beispiel werden automatische Weiterleitungen an die Remotedomäne zugelassen. Diese Einstellung ist standardmäßig deaktiviert.

    Set-RemoteDomain Contoso -AutoForwardEnabled $true

