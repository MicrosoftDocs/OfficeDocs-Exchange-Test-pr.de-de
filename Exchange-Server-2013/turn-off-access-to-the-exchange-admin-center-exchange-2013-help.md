---
title: 'Deaktivieren des Zugriffs auf das EAC: Exchange 2013 Help'
TOCTitle: Deaktivieren des Zugriffs auf das EAC
ms:assetid: 49f4fa77-1722-4703-81c9-8724ae0334fb
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218639(v=EXCHG.150)
ms:contentKeyID: 50475575
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Deaktivieren des Zugriffs auf das EAC

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-05-20_

Aus Sicherheitsgründen möchten einige Organisation den Zugriff auf die Exchange-Verwaltungskonsole für Benutzer einschränken, die über das Internet zugreifen. Das vorliegende Verfahren zeigt, wie Sie den Zugriff auf die Exchange-Verwaltungskonsole deaktivieren. Das hier vorgestellte Verfahren hindert Benutzer nicht daran, in Outlook Web App auf die Optionen zuzugreifen.


> [!NOTE]
> Mit dieser Vorgehensweise wird der Zugriff des Administrators der Exchange-Verwaltungskonsole auf den CAS-Server deaktiviert, auf den die Schritte angewendet werden. Aktivieren Sie den Administrator der Exchange-Verwaltungskonsole für interne Benutzer, müssen Se einen eigenen CAS-Server installieren und diesen mit dem folgenden Befehl so konfigurieren, dass nur interne Anforderungen verarbeitet werden.<BR><CODE>Set-ECPVirtualDirectory -Identity "InternalCAS\ecp (default web site)" -AdminEnabled $True</CODE>




> [!WARNING]
> Das Verfahren gilt nur für lokalen Bereitstellungen von Exchange Server&nbsp;2013.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Konnektivität der Exchange-Verwaltungskonsole" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Dieses Verfahren kann nicht mit der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Deaktivieren des Internetzugriffs auf die Exchange-Verwaltungskonsole mithilfe der Shell

In diesem Beispiel wird der Zugriff auf die Exchange-Verwaltungskonsole auf dem Server "CAS01" deaktiviert.

```powershell
    Set-ECPVirtualDirectory -Identity "CAS01\ecp (default web site)" -AdminEnabled $false
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-EcpVirtualDirectory](https://technet.microsoft.com/de-de/library/dd297991\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Deaktivierung des Zugriffs auf die Exchange-Verwaltungskonsole zu überprüfen:

1.  Geben Sie in Ihrem Internetbrowser die interne oder externe URL für den Zugriff auf Outlook Web App ein, ersetzen Sie jedoch die Kennung **/owa** durch **/ecp**. Wenn die externe URL für den Zugriff auf Outlook Web App beispielsweise "https://primary.tailspintoys.com/owa" lautet, verwenden Sie "https://primary.tailspintoys.com/ecp".

2.  Wenn der Zugriff deaktiviert ist, erhalten Sie eine Meldung vom Typ **404 – Website nicht gefunden**.

