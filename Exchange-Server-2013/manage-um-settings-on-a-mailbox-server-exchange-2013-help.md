---
title: 'Verwalten von UM-Einstellungen auf einem Postfachserver: Exchange 2013 Help'
TOCTitle: Verwalten von UM-Einstellungen auf einem Postfachserver
ms:assetid: 6df4853d-21d2-473f-b0ca-ebc996d8794a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998815(v=EXCHG.150)
ms:contentKeyID: 50554844
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.UnifiedMessaging.UMServerPropertiesPropertyPage
ms.translationtype: MT
---

# Verwalten von UM-Einstellungen auf einem Postfachserver

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-11_

Nach der Installation eines Postfachservers, auf dem Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, können Sie mehrere Optionen, einschließlich der Anzahl gleichzeitiger Anrufe, die TCP und Sicherheit TLS (Transport Layer) überwacht Ports, den Status und der UM-Startmodus konfigurieren.


> [!IMPORTANT]
> Es ist nicht erforderlich, dass Postfachserver zu einem um-Wählplan hinzugefügt werden, bevor er Anrufe für Unified Messaging (UM), mit Ausnahme von verarbeiten kann bei der Integration von UM und Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server. Standardmäßig stehen allen Postfachservern in einer Organisation, die eingehende Anrufe entgegennehmen.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit Unified Messaging und Postfachservern finden Sie unter [UM-Dienste – Verfahren](um-services-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachserver (UM-Dienst)" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Stellen Sie sicher, dass der Postfachserver installiert ist, entweder auf demselben Computer wie der Clientzugriffsserver oder auf einem anderen Computer.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Shell zum Konfigurieren von Unified Messaging-Eigenschaften auf einem Postfachserver

Dieses Beispiel entfernt einen Postfachserver mit dem Namen `MyMailboxServer` aus allen Wählplänen von Session Initiation Protocol (SIP).

```powershell
Set-UMService -Identity MyMailboxServer -DialPlans $null
```

Dieses Beispiel fügt den Postfachserver namens `MyMailboxServer` zu einem UM-SIP-Wählplan mit dem Namen `MySIPDialPlanName` und wird auch die maximale Anzahl der eingehenden Sprachanrufe.

```powershell
    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlanName -MaxCalls 150 
```

In diesem Beispiel wird den Startmodus Dualmodus auf einem Postfachserver mit dem Namen `MyUMServer`.

```powershell
    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlanName -UMStartUpMode -Dual 
```

## Verwenden der Shell zum Anzeigen der Postfach-Servereigenschaften

In diesem Beispiel wird eine Liste aller Postfachserver.

```powershell
Get-UMService
```

In diesem Beispiel wird eine formatierte Liste der Eigenschaften für den Postfachserver mit dem Namen `MyMailboxServer`.

```powershell
Get-UMService -Identity MyMailboxServer | Format-List
```

