---
title: 'Aktiv. o. Deaktiv. d. IRM-Protokollierung: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder deaktivieren Informationen Rights Management-Protokollierung
ms:assetid: 6933bc65-4d98-4878-9167-0e9eaac68b6b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff686962(v=EXCHG.150)
ms:contentKeyID: 50475864
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder deaktivieren Informationen Rights Management-Protokollierung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

In Exchange Server 2013 können Sie die Protokolle der Verwaltung von Informationsrechten (Information Rights Management, IRM) verwenden, um IRM-Vorgänge zu überwachen und Probleme zu beheben. Die IRM-Protokollierung ist standardmäßig aktiviert.

IRM-Protokolle arbeiten mit den folgenden allgemeinen Parametern:

  - *IrmLogEnabled*   Dient zum Aktivieren bzw. Deaktivieren der IRM-Protokollierung. Standardwert: `$true`.

  - *IrmLogMaxAge*   Gibt das maximal zulässige Alter von IRM-Protokolldateien an. Dateien, die älter als der angegebene Wert sind, werden gelöscht. Standardwert: 30 Tage.

  - *IrmLogMaxDirectorySize*   Gibt die maximale Größe des Verzeichnisses an, in dem die IRM-Protokolle enthalten sind. Wenn die maximale Größe eines Verzeichnisses erreicht ist, löscht der Server zuerst die ältesten Protokolldateien. Standardwert: 250 MB.

  - *IrmLogMaxFileSize*   Gibt die maximale Größe der einzelnen IRM-Protokolldateien an. Wenn eine Protokolldatei die angegebene Größe erreicht, wird eine neue Protokolldatei erstellt. Standardwert: 10 MB.

  - *IrmLogPath*   Gibt den Speicherort des IRM-Protokollverzeichnisses an. Standardwert: `%ExchangeInstallPath%Logging\IRMLogs`.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2-5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Konfigurieren der IRM-Protokollierung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Die Exchange-Verwaltungskonsole kann nicht zum Aktivieren oder Deaktivieren der IRM-Protokollierung auf einem Server verwendet werden. Sie müssen die Shell verwenden

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Aktivieren der IRM-Protokollierung auf einem Server mithilfe der Verwaltungsshell

In diesem Beispiel wird die IRM-Protokollierung auf einem Postfachserver aktiviert.

```powershell
Set-TransportService -Identity EXCH01 -IRMLogEnabled $true
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-TransportService](https://technet.microsoft.com/de-de/library/jj215682\(v=exchg.150\)).

## Deaktivieren der IRM-Protokollierung auf einem Server mithilfe der Verwaltungsshell

In diesem Beispiel wird die IRM-Protokollierung auf einem Postfachserver deaktiviert.

```powershell
Set-TransportService -Identity EXCH01 -IRMLogEnabled $false
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-TransportService](https://technet.microsoft.com/de-de/library/jj215682\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Rufen Sie mithilfe des Cmdlets [Get-TransportService](https://technet.microsoft.com/de-de/library/jj215746\(v=exchg.150\)) die IRM-Einstellungen ab, um zu überprüfen, ob die IRM-Protokollierung auf einem Server erfolgreich aktiviert bzw. deaktiviert wurde.

In diesem Beispiel werden alle IRM-Protokollierungseigenschaften auf dem Server EXCH01 abgerufen.

    Get-TransportService -Identity EXCH01 | Format-List IRMLog*

