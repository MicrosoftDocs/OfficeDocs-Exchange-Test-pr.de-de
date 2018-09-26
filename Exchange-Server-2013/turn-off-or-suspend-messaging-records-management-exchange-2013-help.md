---
title: 'Deaktiv. o. Anhalten der Messaging-Datensatzverwaltung: Exchange 2013-Hilfe'
TOCTitle: Deaktivieren oder Anhalten der Messaging-Datensatzverwaltung
ms:assetid: 631191aa-3bba-4ebf-a727-c48ed2ebe176
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998580(v=EXCHG.150)
ms:contentKeyID: 52062860
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren oder Anhalten der Messaging-Datensatzverwaltung

 

_**Gilt für:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-14_

Bei einzelnen, informationstechnischen oder geschäftlichen Anforderungen muss möglicherweise die Messaging-Datensatzverwaltung (Messaging Records Management, MRM) für einen einzelnen Benutzer oder einen Postfachserver deaktiviert bzw. vorübergehend angehalten werden. Die Messaging-Datensatzverwaltung wird u. a. aus den folgenden Gründen deaktiviert bzw. angehalten:

  - Wenn ein Postfachbenutzer nicht im Büro ist oder aus anderen Gründen nicht auf seine E-Mail-Nachrichten zugreifen kann, können Sie die Messaging-Datensatzverwaltung für das Postfach vorübergehend deaktivieren, indem Sie die Aufbewahrungszeit anhalten. Wenn die Aufbewahrungszeit für ein Postfach angehalten ist, wird das Postfach nicht mehr vom Assistenten für verwaltete Ordner verarbeitet. Wenn der Postfachbenutzer wieder im Büro ist bzw. auf sein Postfach zugreifen kann, können Sie das Anhalten der Aufbewahrungszeit für das Postfach aufheben.

  - Wenn Sie bei Leistungsproblemen Tests oder Fehlerbehebungsmaßnamen durchführen müssen, können Sie die Messaging-Datensatzverwaltung auf dem entsprechenden Server vorübergehend anhalten, indem Sie den Terminplan des Assistenten für verwaltete Ordner löschen.

  - Wenn Sie aus Postfächern ein Aufbewahrungstag (mit dem den jeweiligen Postfächern eine Aufbewahrungsrichtlinie zugewiesen wurde) entfernen müssen, entfernen Sie das Tag aus der Richtlinie.

  - Wenn eine Aufbewahrungsrichtlinie oder eine Postfachrichtlinie für verwalteten Ordner nicht mehr für ein Postfach gelten soll, entfernen Sie die Richtlinie aus dem Postfach.

  - Wenn sich Ihre Organisation entschließt, die MRM-Funktionen nicht mehr zu verwenden, können Sie die Messaging-Datensatzverwaltung dauerhaft für die gesamte Organisation deaktivieren. MRM kann bei Bedarf zu einem späteren Zeitpunkt wieder aktiviert werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 1 Minute

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

## Was möchten Sie machen?

## Anhalten der Aufbewahrungszeit für Postfächer

Sie können für Postfächer die Aufbewahrungszeit anhalten, um die Messaging-Datensatzverwaltung (beispielsweise während des Urlaubs der jeweiligen Benutzer) zu deaktivieren. Dadurch wird die Verarbeitung von Aufbewahrungsrichtlinien für das Postfach so lange unterbrochen, bis das Anhalten der Aufbewahrungszeit wieder aufgehoben wird. Dies unterscheidet sich von der Compliance-Archivierung oder dem Beweissicherungsverfahren für Postfächer.

Ausführliche Informationen zum Anhalten der Aufbewahrungszeit für ein Postfach finden Sie unter [Anhalten der Aufbewahrungszeit für ein Postfach](https://technet.microsoft.com/de-de/library/Dd335168(v=EXCHG.150)).

Weitere Informationen zu Compliance-Archiv und Beweissicherungsverfahren finden Sie unter [In-Place Hold and Litigation Hold](https://docs.microsoft.com/de-de/exchange/security-and-compliance/in-place-and-litigation-holds).

## Entfernen von Aufbewahrungstags aus Postfächern

Zum Entfernen eines Aufbewahrungstags aus einem Postfach heben Sie die Verknüpfung des Tags mit der Aufbewahrungsrichtlinie auf. Wenn Sie die Verknüpfung des Tags mit einer Aufbewahrungsrichtlinie für einen Standardordner aufheben, gilt das Tag des Standardpostfachs für alle Elemente in diesem Ordner. Wenn Sie die Verknüpfung mit einem persönlichen Tag aufheben, steht das Tag für den Benutzer nicht mehr zur Verfügung. Tags, die auf vorhandene Nachrichten angewendet wurden, werden nach wie vor verarbeitet, bis Sie das Tag aus der Exchange-Organisation entfernen.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

Im folgenden Beispiel mit der Shell wird das Aufbewahrungstag "Delete - 3 Days" aus der Aufbewahrungsrichtlinie "Corp-Users" entfernt.

```powershell
    $tags = (Get-RetentionPolicy "Corp-Users").RetentionPolicyTagLinks
    $tags -= "Deleted Items - 3 Days"
    Set-RetentionPolicy "Corp-Users" -RetentionPolicyTagLinks $tags
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd298086\(v=exchg.150\)) und [Set-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd335196\(v=exchg.150\)).

## Entfernen von Aufbewahrungsrichtlinien aus Postfächern

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Anwenden von Aufbewahrungsrichtlinien" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

Sie können das Anwenden einer Aufbewahrungsrichtlinie auf ein Postfach beenden, indem Sie die Richtlinie aus den Eigenschaften des Postfachbenutzers entfernen.

Im folgenden Beispiel mit der Shell wird die Aufbewahrungsrichtlinie aus dem Postfach "jpeoples" entfernt.

```powershell
Set-Mailbox jpeoples -RetentionPolicy $null.
```

Im folgenden Beispiel mit der Shell wird die Aufbewahrungsrichtlinie aus allen Postfächern in der Exchange-Organisation entfernt.

```powershell
    Get-Mailbox -ResultSize unlimited -Filter {RetentionPolicy -ne $null} | Set-Mailbox -RetentionPolicy $null
```

Im folgenden Beispiel mit der Shell wird die Aufbewahrungsrichtlinie "Corp-Finance" von allen Postfachbenutzern entfernt, bei denen die Richtlinie angewendet wurde.

```powershell
    Get-Mailbox -ResultSize unlimited -Filter {RetentionPolicy -eq "Corp-Finance"} | Set-Mailbox -RetentionPolicy $null
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) und [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

## Endgültiges Deaktivieren der Messaging-Datensatzverwaltung für eine ganze Organisation

Zum Deaktivieren der Messaging-Datensatzverwaltung für eine Organisation löschen Sie alle Aufbewahrungstags und Aufbewahrungsrichtlinien außer der Richtlinie "ArbitrationMailbox", die vom Exchange-Setupprogramm erstellt wird. Nachdem dieser Vorgang abgeschlossen wurde, werden Aufbewahrungsrichtlinien nicht durchgesetzt.


> [!WARNING]
> Aufbewahrungsrichtlinien umfassen außerdem "In Archiv verschieben"-Tags, durch welche Nachrichten in das Archivpostfach des Benutzers verschoben werden. Wenn Sie eine Aufbewahrungsrichtlinie entfernen, die ein "In Archiv verschieben"-Tag aufweist, werden Nachrichten von Benutzern, auf die die Richtlinie angewendet wurde, nicht länger vom Assistenten für verwaltete Ordner in das Archiv verschoben.<BR>Um dies zu vermeiden, entfernen Sie nur die Tags "Löschen und Wiederherstellung zulassen" und "Endgültig löschen" aus Ihrer Organisation, und behalten Sie die Richtlinien bei, für die die "In Archiv verschieben"-Tags gelten. Alternativ dazu können Benutzer mit aktiviertem Archiv Elemente manuell mithilfe von Outlook oder Outlook Web App in ihr Archivpostfach verschieben.<BR>Vor dem Entfernen von Aufbewahrungstags oder Aufbewahrungsrichtlinien empfiehlt es sich, die Einstellungen der zu entfernenden Tags zu überprüfen. Löschen Sie keine Tags mit der Aufbewahrungsaktion "In Archiv verschieben".



Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Messaging-Datensatzverwaltung" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).


> [!NOTE]
> Schließen Sie die Option <EM>WhatIf</EM> in die folgenden Befehle ein, um die von einem Befehl durchgeführte Aktion zu simulieren.



In diesem Beispiel werden alle Löschen-Tags aus einer Exchange-Organisation entfernt mit Ausnahme des Tags "Nie löschen", welches in der vom Exchange-Setupprogramm erstellten Richtlinie "ArbitrationMailbox" verwendet wird.

```powershell
    Get-RetentionPolicyTag | ? {$_.RetentionAction -ne "MoveToArchive" -and $_.Name -ne "Never Delete"} | Remove-RetentionPolicyTag
```

In diesem Beispiel werden alle Aufbewahrungstags außer dem Tag "Nie löschen" entfernt.

```powershell
    Get-RetentionPolicyTag | ? {$_.Name -ne "Never Delete"} | Remove-RetentionPolicyTag
```

Dieser Befehl entfernt die Aufbewahrungsrichtlinie "Corp-Benutzer" aus einer Exchange-Organisation.

```powershell
Remove-RetentionPolicy Corp-Users
```

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Get-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd298009\(v=exchg.150\))

  - [Remove-RetentionPolicyTag](https://technet.microsoft.com/de-de/library/dd335092\(v=exchg.150\))

  - [Remove-RetentionPolicy](https://technet.microsoft.com/de-de/library/dd297962\(v=exchg.150\))

