---
title: 'Aktivieren oder Deaktivieren der Transportentschlüsselung: Exchange 2013 Help'
TOCTitle: Aktivieren oder Deaktivieren der Transportentschlüsselung
ms:assetid: 4663f54e-dd0a-4a42-983e-8765e2adc412
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638126(v=EXCHG.150)
ms:contentKeyID: 50475515
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Aktivieren oder Deaktivieren der Transportentschlüsselung

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Aktivieren transportentschlüsselung ermöglicht Transportregel-Agent auf Microsoft Exchange Server 2013 Postfachservern Zugriff auf die Inhalte in Nachrichten von Information Rights Management (IRM) geschützt. Daher andere Transport-Agents Nachrichteninhalt zugreifen und möglicherweise ändern Sie es. Transportregel-Agent müssen möglicherweise zum Prüfen der Nachrichteninhalt und Anwenden von Transportregeln (wie Regeln, die einen Haftungsausschluss auf die Nachricht angewendet). Zum Entschlüsseln von IRM-geschützte Nachrichten müssen Sie der Administratorengruppe auf dem [Active Directory-Rechteverwaltungsdienste (AD RMS)](https://technet.microsoft.com/en-us/library/hh831364.aspx) Server konfiguriert das Zustellung Federated Postfach hinzufügen.


> [!IMPORTANT]
> Mitgliedern der Administratorengruppe wird beim Anfordern einer Lizenz vom AD&nbsp;RMS-Cluster eine Besitzernutzungslizenz gewährt. Damit können sie sämtliche von diesem AD RMS-Cluster erstellten Inhalte, die durch den Rechteverwaltungsdienst geschützt sind, entschlüsseln.



Beim Aktivieren der Transportentschlüsselung können Sie die folgenden Einstellungen angeben:

  - **Verbindlich**   Nachrichten, die nicht entschlüsselt werden können, werden zurückgewiesen, und an den Absender wird ein Unzustellbarkeitsbericht (Non-Delivery Report, NDR) gesendet.

  - **Optional**   Für die Entschlüsselung wird der "Best-Effort-Ansatz" verwendet. Nachrichten werden nach Möglichkeit entschlüsselt und selbst dann zugestellt, wenn die Entschlüsselung fehlschlägt. Dies ist die Standardeinstellung.

Weitere Informationen zur Transportentschlüsselung finden Sie unter [Transportentschlüsselung](transport-decryption-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf IRM finden Sie unter [Verfahren zur Verwaltung von Informationsrechten](information-rights-management-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rechteschutz" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Ein AD RMS-Server ist in der Active Directory-Gesamtstruktur vorhanden, und Sie können darauf zugreifen.

  - Das Verbundzustellungspostfach wurde der AD RMS-Administratorengruppe hinzugefügt. Weitere Informationen finden Sie unter [Hinzufügen des Verbundpostfachs zur AD RMS-Administratorengruppe](add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md).

  - Die Transportentschlüsselung kann nicht in der Exchange-Verwaltungskonsole aktiviert werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Aktivieren der Transportentschlüsselung

In diesem Beispiel wird die Transportentschlüsselung für die Exchange 2013-Organisation aktiviert. Nachrichten, die nicht entschlüsselt werden können, werden zurückgewiesen, und an den Absender wird ein Unzustellbarkeitsbericht gesendet.

    Set-IRMConfiguration -TransportDecryptionSetting Mandatory

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Verwenden der Shell zum Deaktivieren der Transportentschlüsselung

In diesem Beispiel wird die Transportentschlüsselung für die Microsoft Exchange 2013-Organisation deaktiviert.

    Set-IRMConfiguration -TransportDecryptionSetting Disabled

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-IRMConfiguration](https://technet.microsoft.com/de-de/library/dd979792\(v=exchg.150\)).

## Woher weiß ich, dass der Vorgang erfolgreich war?

Verwenden Sie das Cmdlet **Get-IRMConfiguration**, und überprüfen Sie den Wert der Eigenschaft *JournalDecryptionEnabled*, um die erfolgreiche Aktivierung oder Deaktivierung der Transportentschlüsselung zu überprüfen.

Ein Beispiel für das Überprüfen der IRM-Konfiguration finden Sie im Abschnitt [Examples](https://technet.microsoft.com/de-de/e1821219-fe18-4642-a9c2-58eb0aadd61a\(exchg.150\)#examples) zu **Get-IRMConfiguration**.

