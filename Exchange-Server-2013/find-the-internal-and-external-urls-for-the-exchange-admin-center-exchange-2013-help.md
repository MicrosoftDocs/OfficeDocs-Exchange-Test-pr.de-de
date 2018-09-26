---
title: 'Ermitteln der internen und externen URLs für das Exchange Admin Center'
TOCTitle: Ermitteln der internen und externen URLs für die Exchange-Verwaltungskonsole
ms:assetid: 3ddb30ff-a405-4b9d-8d77-2d7a3a5ab8fa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ680108(v=EXCHG.150)
ms:contentKeyID: 50475438
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ermitteln der internen und externen URLs für die Exchange-Verwaltungskonsole

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-04_

Da es sich bei der Exchange-Verwaltungskonsole um eine webbasierte Verwaltungskonsole in Exchange Server 2013 handelt, greifen Sie darauf zu, indem Sie die URL des virtuellen ECP-Verzeichnisses in einem Webbrowser eingeben. In diesem Thema wird gezeigt, wie Sie die URL des virtuellen ECP-Verzeichnisses ermitteln.


> [!NOTE]
> Die Exchange-Systemsteuerung (Exchange Control Panel, ECP) ist die webbasierte Benutzerschnittstelle, die für Exchange Server 2010 entwickelt wurde. Die Cmdlets der Exchange-Verwaltungskonsole für virtuelle Verzeichnisse verwenden weiterhin "ECP" im Namen, und diese Cmdlets können zur Verwaltung von virtuellen Verzeichnissen für Exchange 2010 und Exchange 2013 verwendet werden.



Weitere Informationen zur Exchange-Verwaltungskonsole finden Sie unter [Exchange Admin Center in Exchange 2013](exchange-admin-center-in-exchange-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Dieses Verfahren kann nicht mit der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Konnektivität der Exchange-Verwaltungskonsole" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Ermitteln der internen und externen URLs für die virtuellen ECP-Verzeichnisse mithilfe der Shell

In diesem Beispiel werden der Name des virtuellen ECP-Verzeichnisses, die interne URL und die externe URL in einer formatierten Liste zurückgegeben.

```powershell
Get-ECPVirtualDirectory | Format-List Name,InternalURL,ExternalURL
```

Verwenden Sie nach Ausführung des Befehls die Werte von *InternalURL* oder *ExternalURL* im Webbrowser, um die Exchange-Verwaltungskonsole zu starten.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd351058\(v=exchg.150\)).

