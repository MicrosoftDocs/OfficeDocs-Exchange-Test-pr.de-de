---
title: 'Änd. v. Einträgen f. Rollen oberst. Eb. o. Ber.einschr.: Exchange 2013-Hilfe'
TOCTitle: Ändern Sie einen rolleneintrag für eine auf oberster Ebene ohne bereichseinschränkung
ms:assetid: 65c0bfb3-aafd-4c64-8429-7616c57adf1c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876896(v=EXCHG.150)
ms:contentKeyID: 50475841
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern Sie einen rolleneintrag für eine auf oberster Ebene ohne bereichseinschränkung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Verwaltungsrolleneinträge für Verwaltungsrollen oberster Ebene ohne Bereichseinschränkung verweisen auf die Skripts und Exchange-fremden Cmdlets sowie deren Parameter, die Sie für diejenigen verfügbar machen möchten, denen die Rolle zugewiesen ist. Durch die Änderung der Parameter, die für einen Rolleneintrag verfügbar sind, steuern Sie, wozu diejenigen, denen die Rolle zugewiesen ist, das Skript oder das Exchange-fremde Cmdlet verwenden können. Weitere Informationen zu Rolleneinträgen ohne Bereichseinschränkung finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).


> [!NOTE]
> Informationen zum Ändern eines Rolleneintrags für eine Verwaltungsrolle, die Exchange-Cmdlets enthält, finden Sie unter <A href="change-a-role-entry-exchange-2013-help.md">Ändern Sie einen rolleneintrag</A>.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie unter [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Die Fähigkeit, einen Rolleneintrag für eine Rolle oberster Ebene ohne Bereichseinschränkung zu ändern, ist in keiner Verwaltungsrollengruppe standardmäßig verfügbar. Bevor ein Benutzer einen Rolleneintrag oberster Ebene ohne Bereichseinschränkung hinzufügen oder ändern kann, müssen Sie zuerst die Rolle "Rollenverwaltung ohne Bereichseinschränkung" dem Benutzer oder einer universellen Sicherheitsgruppe (universal security group, USG) oder Rollengruppe zuweisen, der der Benutzer angehört. Weitere Informationen zum Hinzufügen einer Rolle zu einem Benutzer, zu einer universellen Sicherheitsgruppe oder zu einer Rollengruppe finden Sie unter den folgenden Themen:
    
      - [Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)
    
      - [Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden Sie die Shell, um mindestens einen Parameter zu einem Rolleneintrag hinzuzufügen

Zum Hinzufügen von Parametern zu einem Rolleneintrag oberster Ebene ohne Bereichseinschränkung benötigen Sie Folgendes:

  - Geben Sie die hinzuzufügenden Parameter mit dem Parameter *Parameters* an.

  - Geben Sie den Parameter *AddParameter* an, um anzuzeigen, dass Sie einen Hinzufügevorgang ausführen möchten.

  - Geben Sie den Parameter *UnscopedTopLevel* an, um anzuzeigen, dass Sie einen Rolleneintrag für eine Rolle auf oberster Ebene ohne Bereichseinschränkung ändern. Wenn Sie diesen Parameter beim Ändern eines Rolleneintrags für eine Rolle ohne Bereichseinschränkung nicht angeben, tritt ein Fehler auf.

Verwenden Sie zum Hinzufügen von Parametern zu einem Rolleneintrag die folgende Syntax.

    Set-ManagementRoleEntry <role name>\<script or non-Exchange cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -AddParameter -UnscopedTopLevel

In diesem Beispiel werden für die Rolle "Recipient Administrators" ohne Bereichseinschränkung die Parameter *EmailAddress* und *City* zum Skript **CreateUsers.ps1** hinzugefügt.

    Set-ManagementRoleEntry "Recipient Administrators\CreateUsers.ps1" -Parameters EmailAddress, City -AddParameter -UnscopedTopLevel

Ausführliche Informationen zur Syntax und zu den Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Verwenden Sie die Shell, um mindestens einen Parameter aus einem Rolleneintrag zu entfernen

Zum Entfernen von Parametern aus einem Rolleneintrag benötigen Sie Folgendes:

  - Geben Sie die zu entfernenden Parameter mit dem Parameter *Parameters* an.

  - Geben Sie den Parameter *RemoveParameter* an, um anzuzeigen, dass Sie einen Entfernvorgang ausführen möchten.

  - Geben Sie den Parameter *UnscopedTopLevel* an, um anzuzeigen, dass Sie einen Rolleneintrag für eine Rolle auf oberster Ebene ohne Bereichseinschränkung ändern. Wenn Sie diesen Parameter beim Ändern eines Rolleneintrags für eine Rolle ohne Bereichseinschränkung nicht angeben, tritt ein Fehler auf.


> [!WARNING]
> Löschvorgänge können nicht rückgängig gemacht werden. Wenn Sie einen Parameter versehentlich aus einem Rolleneintrag entfernen, müssen Sie ihn manuell erneut hinzufügen.



Verwenden Sie zum Entfernen von Parametern aus einem Rolleneintrag die folgende Syntax.

    Set-ManagementRoleEntry <role name>\<script or non-Exchange cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -RemoveParameter -UnscopedTopLevel

In diesem Beispiel werden für die Rolle "Tier 1 Server Administrators" die Parameter *Delay*, *Force* und *Credential* aus dem Exchange-fremden Cmdlet **Start-Widget** entfernt.

    Set-ManagementRoleEntry "Tier 1 Server Administrators\Start-Widget" -Parameters Delay, Force, Credential -RemoveParameter -UnscopedTopLevel

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Verwenden Sie die Shell, um alle Parameter aus einem Rolleneintrag zu entfernen

Zum Entfernen aller Parameter aus einem Rolleneintrag benötigen Sie Folgendes:

  - Geben Sie den Wert `$Null` für den Parameter *Parameters* an. Sie müssen den Parameter *RemoveParameter* nicht einbeziehen.

  - Geben Sie den Parameter *UnscopedTopLevel* an, um anzuzeigen, dass Sie einen Rolleneintrag für eine Rolle auf oberster Ebene ohne Bereichseinschränkung ändern. Wenn Sie diesen Parameter beim Ändern eines Rolleneintrags für eine Rolle ohne Bereichseinschränkung nicht angeben, tritt ein Fehler auf.

Das Entfernen aller Parameter aus einem Rolleneintrag ist insbesondere dann hilfreich, wenn Sie für ein Skript oder Exchange-fremdes Cmdlet nur wenige Parameter verfügbar machen möchten und alle anderen Parameter ausgeschlossen werden sollen.

Wenn die Rolle keinen Zugriff auf ein Skript oder Exchange-fremdes Cmdlet erhalten soll, sollten Sie den entsprechenden Rolleneintrag vollständig aus der Rolle entfernen, anstatt nur die Parameter zu entfernen. Weitere Informationen zum Entfernen eines Rolleneintrags aus einer Rolle finden Sie unter [Entfernen eines Rolleneintrags aus einer Rolle](remove-a-role-entry-from-a-role-exchange-2013-help.md).


> [!WARNING]
> Löschvorgänge können nicht rückgängig gemacht werden. Wenn Sie versehentlich alle Parameter aus einem Rolleneintrag entfernen, müssen Sie diese manuell erneut hinzufügen.



Verwenden Sie zum Entfernen aller Parameter aus einem Rolleneintrag die folgende Syntax.

    Set-ManagementRoleEntry <role name>\<script or non-Exchange cmdlet> -Parameters $Null -UnscopedTopLevel

In diesem Beispiel werden für die Rolle "Recipient Administrators" alle Parameter aus dem Skript "FindMailboxesOverQuota.ps1" entfernt.

    Set-ManagementRoleEntry "Recipient Administrators\FindMailboxesOverQuota.ps1" -Parameters $Null -UnscopedTopLevel

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Verwenden der Shell zum Anwenden einer bestimmten Gruppe von Parametern

Wenn nur bestimmte Parameter in einen Rolleneintrag eingeschlossen werden sollen, müssen Sie folgende Schritte ausführen:

  - Geben Sie nur den Parameter *Parameters* an. Schließen Sie nicht die Parameter *AddParameter* oder *RemoveParameter* ein.

  - Geben Sie den Parameter *UnscopedTopLevel* an, um anzuzeigen, dass Sie einen Rolleneintrag für eine Rolle ohne Bereichseinschränkung ändern. Wenn Sie diesen Parameter beim Ändern eines Rolleneintrags für eine Rolle oberster Ebene ohne Bereichseinschränkung nicht angeben, tritt ein Fehler auf.


> [!WARNING]
> Wenn Sie nur den Parameter <EM>Parameters</EM> angeben, werden nur die von Ihnen angegebenen Parameter in den Rolleneintrag einbezogen. Alle anderen Parameter werden entfernt.



Verwenden Sie zum Festlegen einer bestimmten Gruppe von Parametern die folgende Syntax.

    Set-ManagementRoleEntry <role name>\<script or non-Exchange cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -UnscopedTopLevel

In diesem Beispiel werden für die Rolle "Seattle Mail Recipient Admins" nur die Parameter *Alias*, *DisplayName*, *WidgetConfig* und *Enabled* für das Cmdlet **Set-Widget** eingeschlossen.

    Set-ManagementRoleEntry "Seattle Mail Recipient Admins\Set-UMMailbox" -Parameters Alias, DisplayName, WidgetConfig, Enabled -UnscopedTopLevel

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Weitere Aufgaben

Nachdem Sie einen Rolleintrag für eine Rolle oberster Ebene ohne Bereichseinschränkung geändert haben, können Sie die folgenden Aufgaben ausführen:

[Hinzufügen eines Rolleneintrags zu einer Rolle](add-a-role-entry-to-a-role-exchange-2013-help.md)

[Verwalten von Rollengruppen](manage-role-groups-exchange-2013-help.md)

[Verwalten von Rollengruppenmitgliedern](manage-role-group-members-exchange-2013-help.md)

[Hinzufügen einer Rolle zu einem Benutzer oder einer universellen Sicherheitsgruppe](add-a-role-to-a-user-or-usg-exchange-2013-help.md)

[Entfernen einer Rolle von einem Benutzer oder einer universellen Sicherheitsgruppe](remove-a-role-from-a-user-or-usg-exchange-2013-help.md)

