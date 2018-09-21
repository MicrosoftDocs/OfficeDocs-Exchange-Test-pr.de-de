---
title: 'Erstellen einer Rolle ohne Bereichseinschränkung: Exchange 2013 Help'
TOCTitle: Erstellen einer Rolle ohne Bereichseinschränkung
ms:assetid: 5a042ccf-4d5f-4609-a91b-21c20d1e6459
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876886(v=EXCHG.150)
ms:contentKeyID: 50475718
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Erstellen einer Rolle ohne Bereichseinschränkung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-06-09_

Mithilfe einer Verwaltungsrolle ohne Bereichseinschränkung können Sie Administratoren und Benutzern mit besonderen Aufgaben den Zugriff auf Windows PowerShell-Skripts und Exchange-fremde Cmdlets ermöglichen. Sie können entweder eine Rolle oberster Ebene ohne Bereichseinschränkung erstellen und dieser Rolle dann Skripts oder Exchange-fremde Cmdlets hinzufügen oder eine Rolle erstellen, die auf einer vorhandenen Rolle oberster Ebene ohne Bereichseinschränkung basiert. Nachdem eine Rolle ohne Bereichseinschränkung erstellt und angepasst wurde, kann die Rolle Verwaltungsrollengruppen, Benutzern und universellen Sicherheitsgruppen (universal security groups, USGs) zugewiesen werden. Es ist nicht möglich, Rollen ohne Bereichseinschränkung zu Verwaltungsrollen-Zuweisungsrichtlinien zuzuweisen. Weitere Informationen zu Rollen ohne Bereichseinschränkung finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).


> [!WARNING]
> Rollen ohne Bereichseinschränkung können sehr einflussreich sein, da, wie der Name schon sagt, kein Verwaltungsbereich auf sie angewendet ist. Das bedeutet, dass Skripts und Exchange-fremde Cmdlets, die in diesen Rollen enthalten sind, auf jedem Objekt in der Exchange-Organisation ausgeführt werden können. Sie sollten dies berücksichtigen, wenn Sie Skripts und Exchange-fremde Cmdlets zu einer Rolle ohne Bereichseinschränkung hinzufügen und die Rolle ohne Bereichseinschränkung zuweisen.




> [!NOTE]
> Wenn Sie eine Rolle erstellen möchten, die Exchange-Cmdlets enthält, müssen Sie eine Rolle erstellen, die auf einer vorhandenen Verwaltungsrolle basiert. Weitere Informationen zum Erstellen von Rollen mit Exchange-Cmdlets finden Sie unter <A href="create-a-role-exchange-2013-help.md">Erstellen einer Rolle</A>.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie unter [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Die Fähigkeit, Rollen ohne Bereichseinschränkung zu erstellen, ist in keiner Verwaltungsrollengruppe standardmäßig verfügbar. Bevor ein Benutzer eine Rollengruppe erstellen kann, müssen Sie zuerst die Rolle "Rollenverwaltung ohne Bereichseinschränkung" dem Benutzer, einer USG oder Rollengruppe zuweisen, der der Benutzer angehört. Weitere Informationen zum Hinzufügen einer Rolle zu einem Benutzer, zu einer universellen Sicherheitsgruppe oder zu einer Rollengruppe finden Sie in den folgenden Themen:
    
      - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)
    
      - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Verwaltungsrolle oberster Ebene ohne Bereichseinschränkung

Wenn Sie Skripts oder Exchange-fremde Cmdlets für Administratoren oder Benutzer mit besonderen Aufgaben in der Organisation verfügbar machen möchten, müssen Sie eine Rolle oberster Ebene ohne Bereichseinschränkung erstellen. Skripts und Exchange-fremde Cmdlets können nur zu einer Rolle ohne Bereichseinschränkung hinzugefügt werden, die als Rolle oberster Ebene erstellt wurde, da die Ausgangsrolle ohne Bereichseinschränkung nicht die Eigenschaften anderer Rollen erbt. Anschließend kann die neue Rolle oberster Ebene ohne Bereichseinschränkung als übergeordnete Rolle für weitere Rollen ohne Bereichseinschränkung fungieren, die ebenfalls die hinzugefügten Skripts und Exchange-fremden Cmdlets verwenden können.

Zum Erstellen einer Rolle oberster Ebene ohne Bereichseinschränkung sind folgende Schritte erforderlich:

## Schritt 1: Erstellen der Rolle oberster Ebene ohne Bereichseinschränkung

Rollen oberster Ebene ohne Bereichseinschränkung haben keine übergeordnete Rolle. Zum Erstellen einer Rolle ohne übergeordnete Rolle müssen Sie die Option *UnscopedTopLevel* angeben. Verwenden Sie die folgende Syntax, um eine neue Rolle zu erstellen.

```powershell
New-ManagementRole <name of new role> -UnscopedTopLevel
```

In diesem Beispiel wird eine Rolle oberster Ebene ohne Bereichseinschränkung erstellt, die den Namen "IT Scripts" erhält.

```powershell
New-ManagementRole "IT Scripts" -UnscopedTopLevel
```

Nachdem die Rolle erstellt wurde, ist sie leer, bis Sie ihr Skripts oder Exchange-fremde Cmdlets hinzufügen.

Ausführliche Informationen zur Syntax und zu den Parametern finden Sie unter [New-ManagementRole](https://technet.microsoft.com/de-de/library/dd298073\(v=exchg.150\)).

## Schritt 2a: Hinzufügen von Skript-Verwaltungsrolleneinträgen

Führen Sie diesen Schritt aus, wenn Sie ein Skript zu einer neuen Rolle ohne Bereichseinschränkung hinzufügen möchten. Wenn Sie ein Exchange-fremdes Cmdlet zu einer neuen Rolle ohne Bereichseinschränkung hinzufügen möchten, müssen Sie Step 2b ausführen.

Zum Hinzufügen eines Windows PowerShell-Skripts zu einer Rolle der obersten Ebene ohne Bereichseinschränkung müssen Sie der Rolle einen Verwaltungsrolleneintrag hinzufügen. Der Rolleneintrag enthält den Skriptnamen und die Parameter des Skripts, das der Rolle zur Verfügung gestellt werden soll.

Das Skript muss sich im Microsoft Exchange Server 2013-Installationspfad im Verzeichnis `RemoteScripts` auf jedem Exchange 2013 ausführenden Server befinden, mit dem die Benutzer möglicherweise die Verbindung herstellen, um das Skript auszuführen. Wenn ein Benutzer über den Zugriff zum Ausführen eines Skripts verfügt, sich das Skript aber nicht auf dem Exchange 2013-Server befindet, mit dem der Benutzer verbunden ist, dann tritt ein Fehler auf. Standardmäßig lautet der Pfad zum `RemoteScripts`-Verzeichnis "C:\\Programme\\Microsoft\\Exchange Server\\V15\\RemoteScripts".

Nachdem Sie das Skript auf die entsprechenden Exchange 2013-Server kopiert und entschieden haben, welche Parameter verwendet werden sollen, erstellen Sie den Rolleneintrag mithilfe der folgenden Syntax.

    Add-ManagementRoleEntry <unscoped top-level role name>\<script filename> -Parameters <parameter 1, parameter 2, parameter...> -Type Script -UnscopedTopLevel

In diesem Beispiel wird das Skript "BulkProvisionUsers.ps1" mit den Parametern *Name* und *Location* zur Rolle "IT Scripts" hinzugefügt.

    Add-ManagementRoleEntry "IT Scripts\BulkProvisionUsers.ps1" -Parameters Name, Location -Type Script -UnscopedTopLevel


> [!NOTE]
> Das Cmdlet <STRONG>Add-ManagementRoleEntry</STRONG> führt die Standardüberprüfung aus, um sicherzustellen, dass Sie nur die Parameter hinzufügen, die im Skript vorhanden sind. Es erfolgt jedoch keine weitere Überprüfung, nachdem der Rolleneintrag hinzugefügt wurde. Wenn später Parameter hinzugefügt oder entfernt werden, müssen Sie die Rolleneinträge manuell aktualisieren, die das Skript enthalten.



## Schritt 2 b: Hinzufügen von Rolleneinträgen für Exchange-fremde Cmdlets

Führen Sie diesen Schritt aus, wenn Sie ein Exchange-fremdes Cmdlet zu einer neuen Rolle ohne Bereichseinschränkung hinzufügen möchten. Wenn Sie ein Skript zu einer neuen Rolle ohne Bereichseinschränkung hinzufügen möchten, müssen Sie Step 2a ausführen.

Zum Hinzufügen eines Nicht-Exchange-Cmdlets zu einer Rolle der obersten Ebene ohne Bereichseinschränkung müssen Sie der Rolle einen Verwaltungsrolleneintrag hinzufügen. Der Rolleneintrag enthält das Cmdlet-Snap-In, den Cmdlet-Namen und die Parameter des Cmdlets, das der Rolle zur Verfügung gestellt werden soll.

Wenn Sie der neuen Rolle Nicht-Exchange-Cmdlets hinzufügen, müssen die Cmdlets auf jedem Exchange 2013-Server installiert werden, zu dem die Benutzer möglicherweise eine Verbindung herstellen, um die Cmdlets auszuführen. Informationen zum ordnungsgemäßen Installieren und Registrieren der Windows PowerShell-Snap-Ins, die die zu verwendenden Cmdlets enthalten, finden Sie in der Dokumentation Ihres Produkts.

Nachdem Sie das Windows PowerShell-Snap-In, das die Cmdlets enthält, auf den entsprechenden Servern mit Exchange 2013 installiert haben und nun entscheiden, welche Cmdlet-Parameter verwendet werden sollen, können Sie den Rolleneintrag mithilfe der folgenden Syntax erstellen.

    Add-ManagementRoleEntry <unscoped top-level role name>\<cmdlet name> -PSSnapinName <snap-in name> -Parameters <parameter 1, parameter 2, parameter...> -Type Cmdlet -UnscopedTopLevel

In diesem Beispiel wird das Cmdlet **Set-WidgetConfiguration** zum Snap-In "Contoso.Admin.Cmdlets" zur Rolle "Widget Cmdlets" mit den Parametern *Database* und *Size* hinzugefügt.

    Add-ManagementRoleEntry "Widget Cmdlets\Set-WidgetConfiguration" -PSSnapinName Contoso.Admin.Cmdlets -Parameters Database, Size -Type Cmdlet -UnscopedTopLevel


> [!NOTE]
> Das Cmdlet <STRONG>Add-ManagementRoleEntry</STRONG> führt die Standardüberprüfung aus, um sicherzustellen, dass Sie nur die Parameter hinzufügen, die im Cmdlet vorhanden sind. Es erfolgt jedoch keine weitere Überprüfung, nachdem der Rolleneintrag hinzugefügt wurde. Wenn das Cmdlet später geändert wird und Parameter hinzugefügt oder entfernt werden, müssen Sie die Rolleneinträge manuell aktualisieren, die das Cmdlet enthalten.



## Schritt 3: Zuweisen der Verwaltungsrolle

Der abschließende Schritt beim Erstellen und Konfigurieren einer Rolle ist deren Zuweisung an einen Rollenempfänger.


> [!IMPORTANT]
> Verwaltungsbereiche können nicht für Rollenzuweisungen konfiguriert werden, die eine Rolle ohne Bereichseinschränkung zuweisen. Unabhängig davon, ob Sie eine Rollenzuweisung für eine Rollengruppe, einen Benutzer oder eine universelle Sicherheitsgruppe erstellen, müssen Sie die Option zum Erstellen einer Rollenzuweisung ohne Verwaltungsbereich auswählen.



Sie können die neue Rolle zu einer Rollengruppe, zu einem Benutzer oder zu einer universellen Sicherheitsgruppe zuweisen. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

## Erstellen einer Rolle ohne Bereichseinschränkung basierend auf einer anderen Rolle ohne Bereichseinschränkung

Wenn Sie über eine vorhandene Rolle oberster Ebene ohne Bereichseinschränkung oder andere Rollen ohne Bereichseinschränkung verfügen, die Sie als Grundlage für neue Rollen ohne Bereichseinschränkung verwenden möchten, können Sie untergeordnete Rollen ohne Bereichseinschränkung erstellen. Die untergeordneten Rollen ohne Bereichseinschränkung können eine Teilmenge der Skripts und Cmdlets enthalten, die für die übergeordneten Rollen ohne Bereichseinschränkung verfügbar sind. Dies ist z. B. hilfreich, wenn Sie einem weniger erfahrenen Administrator nur eine Teilmenge der Skripts oder Cmdlets bereitstellen möchten, die in einer übergeordneten Rolle ohne Bereichseinschränkung verfügbar sind.

Zum Erstellen einer untergeordneten Rolle ohne Bereichseinschränkung sind folgende Schritte erforderlich:

## Schritt 1: Erstellen der untergeordneten Rolle ohne Bereichseinschränkung

Neue untergeordnete Rollen ohne Bereichseinschränkung können auf vorhandenen Rollen ohne Bereichseinschränkung basieren. Wenn Sie eine Rolle erstellen, werden eine vorhandene Rolle und ihre Verwaltungsrolleneinträge in die neue Rolle kopiert. Die vorhandene Rolle wird zur übergeordneten Rolle der neuen untergeordneten Rolle. Wenn Sie eine Rolle ohne Bereichseinschränkung erstellen, die auf einer anderen Rolle ohne Bereichseinschränkung basiert, müssen Sie eine Rolle auswählen, die alle erforderlichen Cmdlets und Parameter enthält, und dann die nicht gewünschten Cmdlets und Parameter entfernen. Für untergeordnete Rollen ohne Bereichseinschränkung kann es keine Verwaltungsrolleneinträge geben, die nicht in der übergeordneten Rolle vorhanden sind.


> [!NOTE]
> Wenn Sie eine Rolle ohne Bereichseinschränkung erstellen müssen, die Skripts oder Exchange-fremde Cmdlets enthält, die in keiner anderen Rollen ohne Bereichseinschränkung verfügbar sind, müssen Sie eine Rolle oberster Ebene ohne Bereichseinschränkung erstellen. Weitere Informationen finden Sie unter Create an unscoped top-level management role weiter oben in diesem Thema.



Verwenden Sie die folgende Syntax, um eine neue Rolle zu erstellen.

    New-ManagementRole -Parent <existing unscoped role to copy> -Name <name of new unscoped role>

Im folgenden Beispiel werden die Rolle "IT Global Scripts" und die zugehörigen Verwaltungsrolleneinträge in die Rolle "Diagnostic IT Scripts" kopiert.

```powershell
New-ManagementRole -Parent "IT Global Scripts" -Name "Diagnostic IT Scripts"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-ManagementRole](https://technet.microsoft.com/de-de/library/dd298073\(v=exchg.150\)).

## Schritt 2: Ändern der Verwaltungsrolleneinträge der Rolle

Nachdem Sie die Rolle erstellt haben, müssen Sie die Einträge der Rolle ändern. Sie können einen kompletten Rolleneintrag entfernen, was dazu führt, dass der Zugriff auf das zugeordnete Skript oder Exchange-fremde Cmdlet vollständig aufgehoben wird. Sie können jedoch auch einzelne Parameter aus einem Rolleneintrag entfernen, um nur den Zugriff auf diese speziellen Parameter des zugeordneten Skripts oder Exchange-fremden Cmdlets aufzuheben.

Das Hinzufügen von Rolleneinträgen oder Parametern für Rolleneinträge ist nur möglich, wenn diese bereits in der übergeordneten Rolle vorhanden sind. Da Sie gerade in Schritt 1 eine Rolle aus einer übergeordneten Rolle erstellt haben, können Sie keine weiteren Rolleneinträge oder Parameter für Rolleneinträge hinzufügen, da diese in der übergeordneten Rolle nicht vorhanden sind.

Nachdem Sie einen Rolleneintrag für eine Rolle geändert haben, können Sie die folgenden Aufgaben ausführen:

  - Einen einzelnen vollständigen Rolleneintrag entfernen.

  - Mehrere vollständige Rolleneinträge entfernen.

  - Parameter eines Rolleneintrags entfernen.

Informationen zum Entfernen von Rolleneinträgen aus der neuen Rolle finden Sie unter [Entfernen eines Rolleneintrags aus einer Rolle](remove-a-role-entry-from-a-role-exchange-2013-help.md).

## Schritt 3: Zuweisen der Verwaltungsrolle

Der abschließende Schritt beim Erstellen und Konfigurieren einer Rolle ist deren Zuweisung an einen Rollenempfänger.


> [!IMPORTANT]
> Verwaltungsbereiche können nicht für Rollenzuweisungen konfiguriert werden, die eine Rolle ohne Bereichseinschränkung zuweisen. Unabhängig davon, ob Sie eine Rollenzuweisung für eine Rollengruppe, einen Benutzer oder eine universelle Sicherheitsgruppe erstellen, müssen Sie die Option zum Erstellen einer Rollenzuweisung ohne Verwaltungsbereich auswählen.



Sie können die neue Rolle zu einer Rollengruppe, zu einem Benutzer oder zu einer universellen Sicherheitsgruppe zuweisen. Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

  - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

