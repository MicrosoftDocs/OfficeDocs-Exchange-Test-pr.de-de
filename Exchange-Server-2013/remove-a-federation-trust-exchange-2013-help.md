---
title: 'Entfernen einer Verbundvertrauensstellung: Exchange 2013 Help'
TOCTitle: Entfernen einer Verbundvertrauensstellung
ms:assetid: dc4d126d-b567-470d-a5d0-e1402bf8f369
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657500(v=EXCHG.150)
ms:contentKeyID: 50476861
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Entfernen einer Verbundvertrauensstellung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-01-04_

Eine Verbundvertrauensstellung richtet eine Vertrauensstellung zwischen einer Microsoft Exchange 2013-Organisation und dem Azure Active Directory-Authentifizierungssystem ein und unterstützt eine Freigabe mit anderen Exchange-Organisationen im Partnerverbund. Durch das Entfernen einer Verbundvertrauensstellung aus Ihrer lokalen Exchange-Organisation wird die Verbundfreigabe mit anderen Exchange-Verbundorganisationen und Office 365-Organisationen deaktiviert, die im Rahmen einer Hybridbereitstellung mit Ihrer Organisation verbunden sind. Wägen Sie daher im Vorfeld alle Auswirkungen ab, die das Entfernen einer Verbundvertrauensstellung für Ihre Organisation hat.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Verbundvertrauensstellungen finden Sie unter [Verbundverfahren](federation-procedures-exchange-2013-help.md).


> [!IMPORTANT]
> Diese Funktion von Exchange Server 2013 ist nicht vollständig kompatibel mit dem von 21Vianet in China betriebenen Office 365. Möglicherweise sind einige Funktionseinschränkungen vorhanden. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=313640">Verwenden von Office 365 mit 21Vianet</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verbund- und Zertifikatberechtigungen" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Nachdem Sie eine Verbundvertrauensstellung entfernt haben, können Sie die TXT-Einträge für jede Verbunddomäne von Ihrem öffentlichen DNS-Server entfernen. Überprüfen Sie die Anforderungen für das Entfernen eines TXT-Eintrags mit der Organisation, die Ihre öffentlichen DNS-Einträge hostet.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Was möchten Sie machen?

## Entfernen einer Verbundvertrauensstellung mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie auf einem Exchange 2013-Server in Ihrer lokalen Organisation zu **Organisation** \> **Freigabe**.

2.  Klicken Sie im Abschnitt **Verbundvertrauensstellung** auf **Entfernen**.

3.  Klicken Sie in der Warnung auf **Ja**, um zu bestätigen, dass Sie die Verbundvertrauensstellung entfernen möchten.

4.  Klicken Sie auf **Schließen**, nachdem die Verbundvertrauensstellung entfernt wurde.

## Entfernen einer Verbundvertrauensstellung mithilfe der Shell

In diesem Beispiel wird die Verbundvertrauensstellung entfernt.

    Remove-FederationTrust

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Remove-FederationTrust](https://technet.microsoft.com/de-de/library/dd351153\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sich zu vergewissern, dass Sie die Verbundvertrauensstellung erfolgreich entfernt haben:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Organisation** \> **Freigabe**. Wenn Sie die Verbundvertrauensstellung erfolgreich entfernt haben, ist unter **Verbundvertrauensstellung** nur die Schaltfläche **Aktivieren** verfügbar.

  - Führen Sie in der Shell folgenden Befehl aus, um zu überprüfen, dass keine Informationen der Verbundvertrauensstellung für Ihre Exchange-Organisation zurückgegeben werden.
    
        Get-FederationTrust
    
    Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-FederationTrust](https://technet.microsoft.com/de-de/library/dd351262\(v=exchg.150\)).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

