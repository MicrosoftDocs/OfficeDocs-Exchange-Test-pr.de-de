---
title: 'Automatische Postfachverteilung: Exchange 2013 Help'
TOCTitle: Automatische Postfachverteilung
ms:assetid: f4db4636-948c-466b-839c-300c1a3a9544
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ff477621(v=EXCHG.150)
ms:contentKeyID: 59634175
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Automatische Postfachverteilung

 

_**Gilt für:** Exchange Server 2010 Service Pack 2 (SP2), Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-08-13_

Beim Erstellen oder Verschieben eines Postfachs oder Aktivieren eines vorhandenen Benutzers für E-Mail muss das Postfach in einer Postfachdatenbank gespeichert werden. In Microsoft Exchange Server 2013 können Sie festlegen, dass Exchange die Datenbank mithilfe der automatischen Postfachverteilung ausgewählt wird.

Bei Verwendung der automatischen Postfachverteilung prüft Exchange die Postfachdatenbanken in Ihrer Organisation, schließt nicht geeignete Datenbanken basierend auf Kriterien aus, die weiter unten in diesem Thema erläutert werden, und wählt nach dem Zufallsprinzip eine Datenbank zum Speichern des Postfachs aus. Bei diesem Vorgang werden Postfächer nach dem Zufallsprinzip auf alle geeigneten Postfachdatenbanken in Ihrer Organisation verteilt.

Die automatische Verteilung wird verwendet, wenn der Parameter *Database* der Cmdlets **New-Mailbox** und **Enable-Mailbox** oder der Parameter *TargetDatabase* des Cmdlets **New-MoveRequest** nicht angegeben wird.


> [!NOTE]
> Die automatische Postfachverteilung wird nur ausgeführt, wenn ein Postfach auf einem Exchange 2013-Server erstellt oder auf einen Exchange 2013-Server verschoben bzw. wenn ein Benutzer für E-Mail aktiviert wird. Die Cmdlets <STRONG>Neues Postfach</STRONG>, <STRONG>Neue MoveRequest</STRONG> und <STRONG>Postfach aktivieren</STRONG> müssen auf einem Server mit Exchange 2013 ausgeführt werden. Exchange verteilt Postfächer nicht neu, um die Last basierend auf der Serverauslastung automatisch zu verteilen.



Zur Ermittlung einer geeigneten Postfachdatenbank für ein neues oder verschobenes Postfach wird der folgende Vorgang ausgeführt:

1.  Exchange ruft eine Liste aller Postfachdatenbanken in der Exchange 2013-Organisation ab.

2.  Postfachdatenbanken, die für den Ausschluss aus dem Verteilungsvorgang gekennzeichnet sind, werden aus der Liste der verfügbaren Datenbanken entfernt. Sie können steuern, welche Datenbanken ausgeschlossen werden. Weitere Informationen finden Sie später in diesem Thema im Abschnitt Ausschließen von Datenbanken aus der automatischen Verteilung.

3.  Postfachdatenbanken, die nicht zu den Datenbankverwaltungsbereichen des Administrators gehören, der den Vorgang ausführt, werden aus der Liste der verfügbaren Datenbanken entfernt. Weitere Informationen finden Sie später in diesem Thema im Abschnitt Datenbankbereiche.

4.  Postfachdatenbanken außerhalb des lokalen Active Directory-Standorts, an dem der Vorgang ausgeführt wird, werden aus der Liste der verfügbaren Datenbanken entfernt.

5.  Aus der Liste der verbleibenden Postfachdatenbanken wählt Exchange nach dem Zufallsprinzip eine Datenbank aus. Wenn die Datenbank verfügbar ist und einen fehlerfreien Zustand aufweist, wird sie von Exchange verwendet. Wenn die Datenbank nicht verfügbar ist oder keinen fehlerfreien Zustand aufweist, wird nach dem Zufallsprinzip eine andere Datenbank ausgewählt. Wenn keine Datenbanken ermittelt werden, die verfügbar sind oder einen fehlerfreien Zustand aufweisen, wird der Vorgang mit einem Fehler abgebrochen.

Der Vorgang zur Auswahl einer Postfachdatenbank wird vom Cmdlet-Erweiterung-Agent für die Verwaltung von Postfachressourcen ausgeführt. Der `Mailbox Resources Management Agent` ist einer von mehreren Cmdlet-Erweiterungs-Agents, mit denen die Funktionen ausgeführter Cmdlets erweitert werden können. Weitere Informationen zu Cmdlet-Erweiterungs-Agents finden Sie unter [Cmdlet-Erweiterungs-Agents](cmdlet-extension-agents-exchange-2013-help.md).

Wenn Postfächer nie automatisch verteilt werden sollen, kann der `Mailbox Resources Management Agent` deaktiviert werden. Beim Deaktivieren des Agents wird diese Änderung für die gesamte Exchange-Organisation übernommen. Weitere Informationen zum Deaktivieren von Cmdlet-Erweiterungs-Agents finden Sie unter [Verwalten von Cmdlet-Erweiterungs-Agents](manage-cmdlet-extension-agents-exchange-2013-help.md).

## Ausschließen von Datenbanken aus der automatischen Verteilung

Standardmäßig können alle Postfachdatenbanken auf Exchange 2013-Servern im lokalen Active Directory-Standort, die verfügbar sind und einen fehlerfreien Zustand aufweisen, bei der automatischen Postfachverteilung zum Speichern eines neuen oder verschobenen Postfachs ausgewählt werden. Aus verschiedenen Gründen kann es jedoch sinnvoll sein, einige Datenbanken aus dem Verteilungsvorgang auszuschließen. Sie können z. B. eine Postfachdatenbank als Journaldatenbank festlegen, in der nur manuell angegebene Postfächer gespeichert werden sollen. Oder Sie entfernen eine Datenbank möglicherweise vorübergehend aus einer Rotation, um geplante Wartungsaufgaben auszuführen. In Exchange 2013 können Datenbanken dauerhaft oder vorübergehend mithilfe des *IsExcludedFromProvisioning*-Parameters, das über den **Set-MailboxDatabase**-Cmdlet festgelegt werden kann, aus dem Ausschlussvorgang ausgeschlossen werden.


> [!NOTE]
> Über den <STRONG>Set-MailboxDatabase</STRONG>-Cmdlet sind zwei weitere Parameter verfügbar: <EM>IsSuspendedFromProvisioning</EM> und <EM>IsExcludedFromInitialProvisioning</EM>. Diese Parameter werden in einer zukünftigen Version von Exchange entfernt und ihre Nutzung nicht mehr unterstützt.



Der *IsExcludedFromProvisioning*-Parameter verfügt über zwei gültige Werte, `$True` und `$False`. Wenn Sie diese Eigenschaft auf `$True` festlegen, wird die Postfachdatenbank aus der automatischen Verteilung ausgeschlossen. Wenn Sie diese Eigenschaft auf `$False` festlegen, wird die Postfachdatenbank bei der automatischen Verteilung berücksichtigt. Der Standardwert lautet `$False`.

Verwenden Sie den folgenden Befehl, um eine Postfachdatenbank aus der automatischen Verteilung auszuschließen:

    Set-MailboxDatabase <database name> -IsExcludedFromProvisioning $True

Wenn eine Postfachdatenbank aus der automatischen Verteilung ausgeschlossen ist, muss der Parameter *Database* mit den Cmdlets **New-Mailbox** und **Enable-Mailbox** oder der Parameter *TargetDatabase* mit dem Cmdlet **New-MoveRequest** verwendet werden, um eine Postfach in der Datenbank zu erstellen bzw. in diese zu verschieben.

## Datenbankbereiche

Datenbankverwaltungsbereiche ermöglichen eine zusätzliche Steuerung der automatischen Postfachverteilung und sind in Exchange 2013 verfügbar. Wenn eine Postfachdatenbank verfügbar ist, einen fehlerfreien Zustand aufweist, sich im lokalen Active Directory-Standort befindet und nicht aus der automatischen Verteilung ausgeschlossen wurde, prüft Exchange 2013, ob die Postfachdatenbank zum Datenbankbereich des Administrators gehört, der das Cmdlet ausführt. Wenn die Datenbank zu diesem Datenbankbereich gehört, wird sie in die Liste der verfügbaren Datenbanken für diesen Administrator aufgenommen.

Datenbankbereiche sind Teil des Berechtigungsmodells für die rollenbasierten Zugriffssteuerung (Role Based Access Control, RBAC). Weitere Informationen zu RBAC und Datenbankbereichen finden Sie unter den folgenden Themen:

  - [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md)

  - [Grundlegendes zu Verwaltungsrollenbereichen](understanding-management-role-scopes-exchange-2013-help.md)

Datenbankbereiche können nützlich sein, wenn Sie über eine Vielzahl von Postfächern in Ihrem lokalen Active Directory-Standort verfügen, die für die automatische Verteilung verfügbar sind, und Sie einschränken möchten, welche Datenbanken von bestimmten Administratoren verwendet werden können. Beispiel: Ihre Exchange 2013-Server werden für mehrere Agenturen eingesetzt, die einzelnen Agenturen sollen jedoch lediglich in der Lage sein, Postfächer in Postfachdatenbanken zu erstellen bzw. in diese zu verschieben, die der jeweiligen Agentur zugewiesen sind.

Standardmäßig können sämtliche Administratoren in einer Exchange 2013-Organisation alle Postfachdatenbanken innerhalb der Organisation anzeigen. Um einzuschränken, welche Datenbanken angezeigt und damit in welchen Datenbanken Postfächer platziert werden können, führen Sie die folgenden Schritte aus:

1.  Erstellen Sie mithilfe des Cmdlets **New-ManagementScope** einen benutzerdefinierten Datenbankverwaltungsbereich mit den Postfachdatenbanken, deren Verwendung durch einen bestimmten Administrator zulässig sein soll.

2.  Ordnen Sie den neuen Datenbankbereich über eine der folgenden Methoden einer Verwaltungsrollenzuweisung zu:
    
      - Fügen Sie den neuen Datenbankbereich über den Parameter *CustomConfigWriteScope* des Cmdlets **Set-ManagementRoleAssignment** zu einer vorhandenen Verwaltungsrollenzuweisung hinzu. Der Datenbankbereich wird nun auf die Verwaltungsrollengruppe, die universelle Sicherheitsgruppe oder den der Rollenzuweisung zugewiesenen Benutzer angewendet.
    
      - Erstellen Sie mithilfe des Cmdlets **New-ManagementRoleAssignment** eine Verwaltungsrollenzuweisung, und geben Sie den neuen Datenbankbereich über den Parameter *CustomConfigWriteScope* an. Eine Rollenzuweisung kann zwischen einer Verwaltungsrolle und einer Rollengruppe, einer universellen Sicherheitsgruppe oder einem Benutzer erstellt werden.

3.  Wenn Sie eine Rollenzuweisung für eine Rollengruppe oder universelle Sicherheitsgruppe erstellt haben, fügen Sie der Rollengruppe oder universellen Sicherheitsgruppe Benutzer hinzu, sodass die Rollenzuweisung und der Datenbankbereich auf die Benutzer angewendet werden.

4.  Entfernen Sie den der neuen Rollenzuweisung zugewiesenen Benutzer (oder die Benutzer, die Mitglieder der in den vorherigen Schritten erstellten Rollengruppen oder universellen Sicherheitsgruppen sind) gegebenenfalls aus anderen Rollengruppen oder universellen Sicherheitsgruppen, wenn diesen Gruppen ein Datenbankbereich mit Datenbanken zugewiesen ist, auf die diese Benutzer nicht zugreifen sollen.

5.  Stellen Sie sicher, dass die Administratoren lediglich auf die von Ihnen festgelegten Datenbanken zugreifen können.

Nach Abschluss dieses Vorgangs können Administratoren mit Rollenzuweisungen, welche die erstellten Datenbankbereiche umfassen, lediglich in den angegebenen Datenbanken Postfächer erstellen bzw. Postfächer lediglich in diese Datenbanken verschieben.

Weitere Informationen zur Verwendung von Datenbankbereichen, um die für Administratoren verfügbaren Postfachdatenbanken einzuschränken, finden Sie unter [Steuern der automatischen Postfachverteilung mithilfe von Datenbankbereichen](control-automatic-mailbox-distribution-using-database-scopes-exchange-2013-help.md).

