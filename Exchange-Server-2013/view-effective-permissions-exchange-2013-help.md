---
title: 'Anzeigen geltender Berechtigungen: Exchange 2013 Help'
TOCTitle: Anzeigen geltender Berechtigungen
ms:assetid: ae6cb7cf-f998-44a6-a69a-02ad736c8260
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638167(v=EXCHG.150)
ms:contentKeyID: 50476477
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Anzeigen geltender Berechtigungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-09_

Berechtigungen werden in Microsoft Exchange Server 2013 unter Verwendung von Verwaltungsrollen gewährt, die Verwaltungsrollengruppen, Zuweisungsrichtlinien für Verwaltungsrollen, universellen Sicherheitsgruppen oder Benutzern direkt zugewiesen werden. Benutzern werden Berechtigungen erteilt, wenn sie Mitglieder der entsprechenden Rollengruppen oder universellen Sicherheitsgruppen sind oder ihnen Rollenzuweisungsrichtlinien zugewiesen wurden.

Die meisten Berechtigungen werden basierend auf Rollengruppenmitgliedschaften oder durch das Zuordnen von Zuweisungsrichtlinien zu Endbenutzern gewährt. Wenngleich die Verwendung von Rollengruppen und Zuweisungsrichtlinien das Gewähren von Berechtigungen für eine Vielzahl von Benutzern erleichtert, wissen Sie möglicherweise nicht, wer Mitglied einer Rollengruppe ist oder wem eine Zuweisungsrichtlinie zugewiesen wurde. In diesen Fällen ist die Option *GetEffectiveUsers* des Cmdlets **Get-ManagementRoleAssignment** sehr nützlich. Sie zeigt, welchen Benutzern die Berechtigungen einer Verwaltungsrolle gewährt wurden, entweder über Rollengruppen, Verwaltungsrichtlinien oder universelle Sicherheitsgruppen, denen sie zugeordnet sind.

Die Option *GetEffectiveUsers* wird mit dem Cmdlet **Get-ManagementRoleAssignment** verwendet, wenn der Parameter *Role* zum Einsatz kommt. Durch das Angeben dieser Option mit einer bestimmten Rolle untersucht das Cmdlet **Get-ManagementRoleAssignment** alle der Rolle zugeordneten Objekte, z. B. Rollengruppen, Zuweisungsrichtlinien und universelle Sicherheitsgruppen, und listet die Mitglieder dieser Objekte auf.


> [!NOTE]
> Die Option <EM>GetEffectiveUser</EM> listet keine Benutzer auf, die Mitglieder einer verknüpften fremden Rollengruppe sind. Wird eine verknüpfte Rollengruppe ermittelt, werden anstelle einer Benutzerliste alle verknüpften Gruppenmitglieder angezeigt. Weitere Informationen zu Berechtigungen in mehreren Gesamtstrukturen finden Sie unter <A href="understanding-multiple-forest-permissions-exchange-2013-help.md">Grundlegendes zu Berechtigungen für mehrere Gesamtstrukturen</A>.



Weitere Informationen zu Verwaltungsrollen, Rollengruppen und Zuweisungsrichtlinien finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md). Weitere Informationen zu Verwaltungsrollenzuweisungen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit der Verwaltung von Berechtigungen gibt? Weitere Informationen finden Sie hier: [Berechtigungen](permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Rollengruppen" und "Rollenzuweisungsrichtlinie" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Die Verfahren in diesem Thema können nur in der Shell ausgeführt werden. Die jeweils wirksamen Berechtigungen können nicht in der Exchange-Verwaltungskonsole angezeigt werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Auflisten aller effektiven Benutzer mithilfe der Shell

Verwenden Sie die folgende Syntax, um alle Benutzer aufzulisten, denen die Berechtigungen erteilt sind, die von einer Verwaltungsrolle bereitgestellt werden.

```powershell
Get-ManagementRoleAssignment -Role <role name> -GetEffectiveUsers
```

In diesem Beispiel werden alle Benutzer aufgelistet, denen die Berechtigungen der Rolle "E-Mail-Empfänger" gewährt wurden.

```powershell
Get-ManagementRoleAssignment -Role "Mail Recipients" -GetEffectiveUsers
```

Wenn Sie die in der Liste zurückgegebenen Eigenschaften ändern oder die Liste in eine durch Trennzeichen getrennte Datei (Comma-Separated Value, CSV) exportieren möchten, finden Sie weitere Informationen im Abschnitt Anpassen und Anzeigen der Ausgabe mithilfe der Shell weiter unten in diesem Thema.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Ermitteln eines spezifischen Benutzers für eine Rolle mithilfe der Shell

Um einen bestimmten Benutzer zu ermitteln, dem über eine Verwaltungsrolle Berechtigungen gewährt wurden, müssen Sie das Cmdlet **Get-ManagementRoleAssignment** zum Abrufen einer Liste aller effektiven Benutzer verwenden und die Ausgabe des Cmdlets mittels Pipelining an das Cmdlet **Where** umleiten. Das Cmdlet **Where** filtert die Ausgabe und gibt nur die angegebenen Benutzer zurück. Verwenden Sie die folgende Syntax.

```powershell
    Get-ManagementRoleAssignment -Role <role name> -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "<name of user>" }
```

In diesem Beispiel wird der Benutzer David Strome für die Journal-Rolle ermittelt.

```powershell
    Get-ManagementRoleAssignment -Role Journaling -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "David Strome" }
```

Weitere Informationen zum Ändern, welche Eigenschaften in der Liste zurückgegeben werden, oder zum Exportieren der Liste in eine CSV-Datei finden Sie unter Anpassen und Anzeigen der Ausgabe mithilfe der Shell weiter unten in diesem Thema.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Ermitteln eines bestimmten Benutzers für alle Rollen mithilfe der Shell

Um alle Rollen zu ermitteln, über die einem Benutzer Berechtigungen gewährt werden, müssen Sie das Cmdlet **Get-ManagementRoleAssignment** zum Abrufen aller effektiven Benutzer für alle Verwaltungsrollen verwenden und anschließend die Ausgabe des Cmdlets mittels Pipelining an das Cmdlet **Where** umleiten. Das Cmdlet **Where** filtert die Ausgabe und gibt nur die Rollenzuweisungen zurück, die dem Benutzer Berechtigungen gewähren.

```powershell
    Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "<name of user>" }
```

In diesem Beispiel werden alle Rollenzuweisungen ermittelt, die dem Benutzer Kim Akers Berechtigungen gewähren.

```powershell
Get-ManagementRoleAssignment -GetEffectiveUsers | Where {     Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "Kim Akers" }.EffectiveUserName -Eq "Kim Akers" }
```

Weitere Informationen zum Ändern, welche Eigenschaften in der Liste zurückgegeben werden, oder zum Exportieren der Liste in eine CSV-Datei finden Sie unter Anpassen und Anzeigen der Ausgabe mithilfe der Shell weiter unten in diesem Thema.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Anpassen und Anzeigen der Ausgabe mithilfe der Shell

Die Standardausgabe des Cmdlets **Get-ManagementRoleAssignment** enthält möglicherweise nicht die gewünschten Informationen. Die Ausgabe des Cmdlets umfasst jedoch viele weitere Eigenschaften, auf die Sie zugreifen können. Im folgenden werden einige der Eigenschaften aufgeführt, die nützlich sein können:

  - **EffectiveUserName**   Der Name des Benutzers.

  - **Role**   Die Rolle, die die Berechtigungen erteilt.

  - **RoleAssigneeName**   Die Rollengruppe, Zuweisungsrichtlinie oder universelle Sicherheitsgruppe, die der Rolle zugewiesen ist und den Benutzer in der Eigenschaft `EffectiveUserName` enthält.

  - **RoleAssigneeType**   Gibt an, ob die Rollenzuweisung für eine Rollengruppe, eine Zuweisungsrichtlinie, eine universellen Sicherheitsgruppe oder einen Benutzer gilt.

  - **AssignmentMethod**   Gibt an, ob es sich um eine direkte oder indirekte Zuweisung zwischen der Rolle und dem Rollenempfänger handelt.

  - **CustomRecipientWriteScope**   Gibt den benutzerdefinierten Empfängerschreibbereich an, der der Rollenzuweisung bei deren Erstellung zugewiesen wurde (sofern vorhanden). Der in dieser Eigenschaft angegebene Bereich setzt den impliziten Empfängerschreibbereich außer Kraft, der in der Eigenschaft `RecipientWriteScope` angegeben ist.

  - **CustomConfigWriteScope**   Gibt den benutzerdefinierten Konfigurationsschreibbereich an, der der Rollenzuweisung bei deren Erstellung zugewiesen wurde (sofern vorhanden). Der in dieser Eigenschaft angegebene Bereich setzt den impliziten Konfigurationsschreibbereich außer Kraft, der in der Eigenschaft `ConfigWriteScope` angegeben ist.

  - **RecipientReadScope**   Gibt den impliziten Empfängerlesebereich an, der auf die Rolle angewendet wird.

  - **RecipientReadScope**   Gibt den impliziten Empfängerschreibbereich an, der auf die Rolle angewendet wird.

  - **ConfigReadScope**   Gibt den impliziten Konfigurationslesebereich an, der auf die Rolle angewendet wird.

  - **ConfigReadScope**   Gibt den impliziten Konfigurationsschreibbereich an, der auf die Rolle angewendet wird.

Zum Auswählen der Eigenschaften, die Sie in der Liste anzeigen möchten, verwenden Sie Befehle ähnlich denen, die in den Abschnitten Auflisten aller effektiven Benutzer mithilfe der Shell, Ermitteln eines spezifischen Benutzers für eine Rolle mithilfe der Shell und Ermitteln eines bestimmten Benutzers für alle Rollen mithilfe der Shell verwendet werden. Der Unterschied besteht darin, dass Sie die Ausgabe dieser Befehle mittels Pipelining an die Cmdlets **Format-Table** oder **Select-Object** umleiten. Das Cmdlet **Format-Table** ist nützlich, um die Liste der Ergebnisse auf dem Bildschirm auszugeben. Mit dem Cmdlet **Select-Object** können Sie die Ergebnisliste in eine CSV-Datei ausgeben.

Beide Cmdlets ermöglichen die Festlegung der Eigenschaften, die Sie anzeigen möchten. Es ist ebenfalls möglich, eine Anzeigereihenfolge anzugeben. Das Cmdlet **Format-Table** stellt Ihnen weitere Optionen bereit, wenn Sie die Ergebnisse auf dem Bildschirm ausgeben. Das Cmdlet **Select-Object** ändert die Ausgabe dagegen nicht, was bei einem Weiterreichen der Liste in eine CSV-Datei nützlich ist.

Weitere Informationen zu den Cmdlets **Format-Table** und **Select-Object** finden Sie unter [Arbeiten mit Ausgaben von Befehlen](working-with-command-output-exchange-2013-help.md).

## Ausgabe einer benutzerdefinierten Liste auf dem Bildschirm

1.  Wählen Sie mit einem der folgenden Verfahren die Informationen aus, die angezeigt werden sollen, und suchen Sie nach dem zugehörigen Befehl:
    
      - Auflisten aller effektiven Benutzer mithilfe der Shell
    
      - Ermitteln eines spezifischen Benutzers für eine Rolle mithilfe der Shell
    
      - Ermitteln eines bestimmten Benutzers für alle Rollen mithilfe der Shell

2.  Wählen Sie die Eigenschaften aus, die in der Liste angezeigt werden sollen.

3.  Verwenden Sie die folgende Syntax, um die Liste anzuzeigen.
    
    ```powershell
        <command to retrieve list > | Format-Table <property 1>, <property 2>, <property ...>
    ```
    
In diesem Beispiel wird der Benutzer David Strome in allen Rollen gefunden, und es werden die Eigenschaften `EffectiveUserName`, `Role`, `CustomRecipientWriteScope` und `CustomConfigWriteScope` angezeigt.

```powershell
    Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "David Strome" } | Format-Table EffectiveUserName, Role, CustomRecipientWriteScope, CustomConfigWriteScope
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

## Ausgeben einer benutzerdefinierten Liste in eine CSV-Datei

Um eine Liste in eine CSV-Datei zu exportieren, müssen Sie die Ergebnisse des Befehls **Get-ManagementRoleAssignment** wie im entsprechenden Verfahren weiter oben beschrieben an das Cmdlet **Select-Object** weiterreichen. Die Ausgabe des Cmdlets **Select-Object** wird dann an das Cmdlet **Export-CSV** weitergereicht, das die CSV-Ausgabe in einer von Ihnen angegebenen Datei speichert.

1.  Wählen Sie mit einem der folgenden Verfahren die Informationen aus, die angezeigt werden sollen, und suchen Sie nach dem zugehörigen Befehl:
    
      - Auflisten aller effektiven Benutzer mithilfe der Shell
    
      - Ermitteln eines spezifischen Benutzers für eine Rolle mithilfe der Shell
    
      - Ermitteln eines bestimmten Benutzers für alle Rollen mithilfe der Shell

2.  Wählen Sie die Eigenschaften aus, die in der Liste angezeigt werden sollen.

3.  Verwenden Sie die folgende Syntax, um die Liste in eine CSV-Datei zu exportieren.
    
    ```powershell
        <command to retrieve list > | Select-Object <property 1>, <property 2>, <property ...> | Export-CSV <filename>
    ```
    
In diesem Beispiel wird der Benutzer David Strome in allen Rollen gefunden, und es werden die Eigenschaften `EffectiveUserName`, `Role`, `CustomRecipientWriteScope` und `CustomConfigWriteScope` angezeigt.

```powershell
    Get-ManagementRoleAssignment -GetEffectiveUsers | Where { $_.EffectiveUserName -Eq "David Strome" } | Select-Object EffectiveUserName, Role, CustomRecipientWriteScope, CustomConfigWriteScope | Export-CSV c:\output.csv
```

Sie können die CSV-Datei nun in einem Viewer Ihrer Wahl anzeigen.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-ManagementRoleAssignment](https://technet.microsoft.com/de-de/library/dd351024\(v=exchg.150\)).

