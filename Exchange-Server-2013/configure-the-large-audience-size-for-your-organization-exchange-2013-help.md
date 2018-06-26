---
title: 'Konfigurieren einer großen Benutzergruppe für Ihre Organisation: Exchange 2013 Help'
TOCTitle: Konfigurieren einer großen Benutzergruppe für Ihre Organisation
ms:assetid: 8a37911c-4339-4921-b5d3-0a5a774d4517
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659068(v=EXCHG.150)
ms:contentKeyID: 50476213
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren einer großen Benutzergruppe für Ihre Organisation

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Mithilfe der Exchange-Verwaltungsshell können Sie verschiedene Einstellungen konfigurieren, die festlegen, wie Sie E-Mail-Infos in Ihrer Organisation verwenden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Infos" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Konfigurieren der Größe einer großen Benutzergruppe für Ihre Organisation

Sie verwenden das Cmdlet **Set-OrganizationConfig**, um die Größe einer großen Benutzergruppe für Ihre Organisation zu konfigurieren. Wenn Absender Nachrichten an eine größere Gruppe von Empfängern senden, als Sie konfiguriert haben, werden diese in der E-Mail-Info zu einer großen Benutzergruppe angezeigt. Die Größe einer großen Benutzergruppe ist standardmäßig auf 25 festgelegt. In diesem Beispiel wird die Größe einer großen Benutzergruppe in Ihrer Organisation auf 50 konfiguriert.

    Set-OrganizationConfig -MailTipsLargeAudienceThreshold 50

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-OrganizationConfig](https://technet.microsoft.com/de-de/library/aa997443\(v=exchg.150\)).

