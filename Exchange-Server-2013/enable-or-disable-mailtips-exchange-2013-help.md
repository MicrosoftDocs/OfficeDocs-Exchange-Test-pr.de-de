---
title: 'Aktivieren oder Deaktivieren von E-Mail-Infos: Exchange 2013 Help'
TOCTitle: Aktivieren oder Deaktivieren von E-Mail-Infos
ms:assetid: 11ad3848-f303-4ad5-a21d-9b0883db4bda
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649321(v=EXCHG.150)
ms:contentKeyID: 50475132
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren von E-Mail-Infos

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Mithilfe der Exchange-Verwaltungsshell können Sie verschiedene Einstellungen konfigurieren, die festlegen, wie Sie E-Mail-Infos in Ihrer Organisation verwenden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Infos" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Aktivieren oder Deaktivieren von E-Mail-Infos

Sie können das Cmdlet **Set-OrganizationConfig** zum Aktivieren oder Deaktivieren von E-Mail-Infos in Ihrer Organisation verwenden. E-Mail-Infos sind standardmäßig aktiviert, wenn Sie eine neue Exchange-Organisation installieren. In diesem Beispiel wird veranschaulicht, wie Sie E-Mail-Infos in Ihrer Organisation aktivieren.

    Set-OrganizationConfig -MailTipsAllTipsEnabled $true

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)).

