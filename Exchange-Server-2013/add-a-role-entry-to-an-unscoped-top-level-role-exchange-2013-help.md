---
title: 'Hinz. d. Roll.eintr. z. Rolle obrst. Eb. o. Ber.einschr.: Exchange 2013-Hilfe'
TOCTitle: Hinzufügen eines Eintrags Rolle zu einem oberster Ebene ohne bereichseinschränkung
ms:assetid: 52fd3f20-c348-49d5-9bdb-f2cbf780cf2d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd979789(v=EXCHG.150)
ms:contentKeyID: 50475668
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Hinzufügen eines Eintrags Rolle zu einem oberster Ebene ohne bereichseinschränkung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Sie können Skripts und Exchange-fremde Cmdlets zu Verwaltungsrollen oberster Ebene ohne Bereichseinschränkung hinzufügen, wenn Sie neue Skripts oder Exchange-fremde Cmdlets für vorhandene Rollen ohne Bereichseinschränkung verfügbar machen möchten. Diese Skripts und Exchange-fremden Cmdlets werden in Form von Verwaltungsrolleneinträgen zu Verwaltungsrollen oberster Ebene ohne Bereichseinschränkung hinzugefügt. Anschließend können sie von diesen Rolleinträgen oberster Ebene ohne Bereichseinschränkung oder von allen Rollen ohne Bereichseinschränkung verwendet werden, die von den Rollen oberster Ebene abgeleitet werden. Weitere Informationen zu Rolleneinträgen ohne Bereichseinschränkung finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).


> [!NOTE]
> Informationen zum Ändern eines Rolleneintrags für eine Verwaltungsrolle, die Exchange-Cmdlets enthält, finden Sie unter <A href="change-a-role-entry-exchange-2013-help.md">Ändern Sie einen rolleneintrag</A>.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie unter [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Die Fähigkeit, einen Rolleneintrag für eine Rolle oberster Ebene ohne Bereichseinschränkung hinzuzufügen, ist in keiner Verwaltungsrollengruppe standardmäßig verfügbar. Bevor ein Benutzer einen Rolleneintrag oberster Ebene ohne Bereichseinschränkung hinzufügen kann, müssen Sie zuerst die Rolle "Rollenverwaltung ohne Bereichseinschränkung" dem Benutzer oder einer universellen Sicherheitsgruppe (universal security group, USG) oder Rollengruppe zuweisen, der der Benutzer angehört. Weitere Informationen zum Hinzufügen einer Rolle zu einer Rollengruppe, einem Benutzer oder einer USG finden Sie unter den folgenden Themen:
    
      - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)
    
      - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Hinzufügen eines Skriptrolleneintrags zu einer Rolle oberster Ebene ohne Bereichseinschränkung

Verwenden Sie dieses Verfahren, wenn Sie ein Skript zu einer vorhandenen Rolle ohne Bereichseinschränkung hinzufügen möchten. Wenn Sie ein Exchange-fremdes Cmdlet zu einer vorhandenen Rolle ohne Bereichseinschränkung hinzufügen möchten, finden Sie weitere Informationen im Folgenden unter "Hinzufügen eines Rolleneintrags für Exchange-fremde Cmdlets zu einer Rolle oberster Ebene ohne Bereichseinschränkung".

Zum Hinzufügen eines Windows PowerShell-Skripts zu einer Rolle der obersten Ebene ohne Bereichseinschränkung müssen Sie der Rolle einen Verwaltungsrolleneintrag hinzufügen. Der Rolleneintrag enthält den Skriptnamen und die Parameter des Skripts, das der Rolle zur Verfügung gestellt werden soll.

Das Skript muss sich im Microsoft Exchange Server 2013-Installationspfad im Verzeichnis "Scripts" auf jedem Exchange 2013 ausführenden Server befinden, mit dem die Benutzer möglicherweise die Verbindung herstellen, um das Skript auszuführen. Wenn ein Benutzer über den Zugriff zum Ausführen eines Skripts verfügt, sich das Skript aber nicht auf dem Exchange 2013-Server befindet, mit dem der Benutzer verbunden ist, dann tritt ein Fehler auf. Standardmäßig lautet der Pfad zum Skriptverzeichnis "C:\\Programme\\Microsoft\\Exchange Server\\V15\\Scripts".

Nachdem Sie das Skript auf die entsprechenden Exchange 2013-Server kopiert und entschieden haben, welche Parameter verwendet werden sollen, erstellen Sie den Rolleneintrag mithilfe der folgenden Syntax.

```powershell
    Add-ManagementRoleEntry <unscoped top-level role name>\<script filename> -Parameters <parameter 1, parameter 2, parameter...> -Type Script -UnscopedTopLevel
```

In diesem Beispiel wird das Skript "BulkProvisionUsers.ps1" mit den Parametern *Name* und *Location* zur Rolle "IT Scripts" hinzugefügt.

```powershell
    Add-ManagementRoleEntry "IT Scripts\BulkProvisionUsers.ps1" -Parameters Name, Location -Type Script -UnscopedTopLevel
```


> [!NOTE]
> Das Cmdlet <STRONG>Add-ManagementRoleEntry</STRONG> führt die Standardüberprüfung aus, um sicherzustellen, dass Sie nur die Parameter hinzufügen, die im Skript vorhanden sind. Es erfolgt jedoch keine weitere Überprüfung, nachdem der Rolleneintrag hinzugefügt wurde. Wenn später Parameter hinzugefügt oder entfernt werden, müssen Sie die Rolleneinträge manuell aktualisieren, die das Skript enthalten.



## Hinzufügen eines Rolleneintrags für Exchange-fremde Cmdlets zu einer Rolle oberster Ebene ohne Bereichseinschränkung

Verwenden Sie dieses Verfahren, wenn Sie ein Exchange-fremdes Cmdlet zu einer vorhandenen Rolle ohne Bereichseinschränkung hinzufügen möchten. Wenn Sie ein Skript-Cmdlet zu einer vorhandenen Rolle ohne Bereichseinschränkung hinzufügen möchten, finden Sie weitere Informationen weiter oben in diesem Thema unter "Hinzufügen eines Skriptrolleneintrags zu einer Rolle oberster Ebene ohne Bereichseinschränkung".

Zum Hinzufügen eines Nicht-Exchange-Cmdlets zu einer Rolle der obersten Ebene ohne Bereichseinschränkung müssen Sie der Rolle einen Verwaltungsrolleneintrag hinzufügen. Der Rolleneintrag enthält das Cmdlet-Snap-In, den Cmdlet-Namen und die Parameter des Cmdlets, das der Rolle zur Verfügung gestellt werden soll.

Wenn Sie der neuen Rolle Nicht-Exchange-Cmdlets hinzufügen, müssen die Cmdlets auf jedem Exchange 2013-Server installiert werden, zu dem die Benutzer möglicherweise eine Verbindung herstellen, um die Cmdlets auszuführen. Informationen zum ordnungsgemäßen Installieren und Registrieren der Windows PowerShell-Snap-Ins, die die zu verwendenden Cmdlets enthalten, finden Sie in der Dokumentation Ihres Produkts.

Nachdem Sie das Windows PowerShell-Snap-In, das die Cmdlets enthält, auf den entsprechenden Servern mit Exchange 2013 installiert haben und nun entscheiden, welche Cmdlet-Parameter verwendet werden sollen, können Sie den Rolleneintrag mithilfe der folgenden Syntax erstellen.

```powershell
    Add-ManagementRoleEntry <unscoped top-level role name>\<cmdlet name> -PSSnapinName <snap-in name> -Parameters <parameter 1, parameter 2, parameter...> -Type Cmdlet -UnscopedTopLevel
```

In diesem Beispiel wird das Cmdlet **Set-WidgetConfiguration** zum Snap-In "Contoso.Admin.Cmdlets" zur Rolle "Widget Cmdlets" mit den Parametern *Database* und *Size* hinzugefügt.

```powershell
    Add-ManagementRoleEntry "Widget Cmdlets\Set-WidgetConfiguration" -PSSnapinName Contoso.Admin.Cmdlets -Parameters Database, Size -Type Cmdlet -UnscopedTopLevel
```

> [!NOTE]
> Das Cmdlet <STRONG>Add-ManagementRoleEntry</STRONG> führt die Standardüberprüfung aus, um sicherzustellen, dass Sie nur die Parameter hinzufügen, die im Cmdlet vorhanden sind. Es erfolgt jedoch keine weitere Überprüfung, nachdem der Rolleneintrag hinzugefügt wurde. Wenn das Cmdlet später geändert wird und Parameter hinzugefügt oder entfernt werden, müssen Sie die Rolleneinträge manuell aktualisieren, die das Cmdlet enthalten.



## Weitere Aufgaben

Nachdem Sie einen Rolleneintrag oder eine Rolle oberster Ebene ohne Bereichseinschränkung hinzugefügt haben, können Sie die folgenden Aufgaben ausführen:

[Hinzufügen eines Rolleneintrags zu einer Rolle](add-a-role-entry-to-a-role-exchange-2013-help.md)

[Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

[Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md)

[Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

[Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)

