---
title: 'Aktiv. o. Deaktiv. von Journalberichtentschlüsselung: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren von Journalberichtentschlüsselung
ms:assetid: 1dedbe73-2c1a-4b14-8799-5091aaec7965
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638092(v=EXCHG.150)
ms:contentKeyID: 50475163
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren von Journalberichtentschlüsselung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Aktivieren journalberichtentschlüsselung ermöglicht den Journal-Agent So fügen Sie eine verschlüsselte Kopie einer durch Rechte geschützten Nachricht an den Journalbericht an. Bevor Sie journalberichtentschlüsselung aktiviert haben, müssen Sie der Administratorengruppe auf dem [Active Directory-Rechteverwaltungsdienste (AD RMS)](https://technet.microsoft.com/en-us/library/hh831364.aspx) Server konfiguriert das Zustellung Federated Postfach hinzufügen.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Verwaltung von Informationsrechten (Information Rights Management, IRM) finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rechteschutz" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Mitgliedern der Administratorengruppe wird eine Nutzungslizenz für Besitzer erteilt, wenn sie eine Lizenz vom AD RMS-Cluster anfordern. Damit können sie alle RMS-geschützten Inhalte entschlüsseln, die von diesem AD RMS-Cluster erstellt werden.

  - In der Active Directory-Gesamtstruktur muss ein AD RMS-Cluster installiert werden.

  - Das Verbundzustellungspostfach wurde einer Administratorengruppe der Active Directory-Rechteverwaltungsdienste hinzugefügt. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

  - Die Journalberichtentschlüsselung kann nicht in der Exchange-Verwaltungskonsole aktiviert werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Aktivieren der Journalberichtentschlüsselung

In diesem Beispiel wird die Journalberichtentschlüsselung für die Exchange-Organisation aktiviert.

```powershell
Set-IRMConfiguration -JournalReportDecryptionEnabled $true
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Verwenden der Shell zum Deaktivieren der Journalberichtentschlüsselung

In diesem Beispiel wird die Journalberichtentschlüsselung für die Exchange-Organisation deaktiviert.

```powershell
Set-IRMConfiguration -JournalReportDecryptionEnabled $false
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie das Cmdlet **Get-IRMConfiguration** aus, und überprüfen Sie den Wert der Eigenschaft *JournalDecryptionEnabled*, um die erfolgreiche Aktivierung oder Deaktivierung der Journalberichtentschlüsselung zu überprüfen.

Ein Beispiel für das Überprüfen der IRM-Konfiguration finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/e1821219-fe18-4642-a9c2-58eb0aadd61a\(exchg.150\)#examples) zu **Get-IRMConfiguration**.

