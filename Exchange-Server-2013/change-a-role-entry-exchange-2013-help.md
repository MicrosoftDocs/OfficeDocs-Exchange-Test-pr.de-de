---
title: 'Ändern Sie einen rolleneintrag: Exchange 2013 Help'
TOCTitle: Ändern Sie einen rolleneintrag
ms:assetid: 5aa4f39c-16a4-4815-ac4f-2cdcfa2b3ee1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd298005(v=EXCHG.150)
ms:contentKeyID: 50475745
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Ändern Sie einen rolleneintrag

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-03_

Jeder Verwaltungsrolleneintrag für eine Verwaltungsrolle repräsentiert ein einzelnes Cmdlet. Durch das Hinzufügen oder Entfernen von Parametern zu bzw. aus einem Rolleintrag, der anschließend einer Verwaltungsrolle hinzugefügt wird, steuern Sie, ob diese Parameter für dieses Cmdlet verfügbar sind. Weitere Informationen zu Verwaltungsrolleneinträgen in Microsoft Exchange Server 2013 finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

Es ist nicht möglich, Rolleneinträge für integrierte Verwaltungsrollen zu ändern.


> [!NOTE]
> In diesem Thema wird nicht erläutert, wie Sie Verwaltungsrolleneinträge ohne Bereichseinschränkung für eine Verwaltungsrolle ohne Bereichseinschränkung ändern. Weitere Informationen zum Ändern von Rolleneinträgen ohne Bereichseinschränkung finden Sie unter <A href="create-a-role-exchange-2013-help.md">Erstellen einer Rolle</A>.




> [!WARNING]
> Zum Hinzufügen oder Entfernen von Parametern zu bzw. aus einem Rolleneintrag müssen Sie den Parameter <EM>AddParameter</EM> bzw. <EM>RemoveParameter</EM> verwenden. Wenn Sie den Parameter <EM>AddParameter</EM> oder <EM>RemoveParameter</EM> beim Ausführen des Cmdlets <STRONG>Set-ManagementRoleEntry</STRONG> nicht angeben, werden nur die mit dem Parameter <EM>Parameters</EM> angegebenen Parameter in den Rolleneintrag einbezogen. Alle anderen Parameter für den Rolleneintrag werden entfernt.



Möchten Sie wissen, welche anderen Verwaltungsaufgaben es im Zusammenhang mit Rollen gibt? Weitere Informationen finden Sie unter [Erweiterte Berechtigungen](advanced-permissions-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verwaltungsrollen" im Thema [Berechtigungen für die Rollenverwaltung](role-management-permissions-exchange-2013-help.md).

  - Sie müssen diese Verfahren mithilfe der Shell ausführen.

  - Wenn Sie Parameter zu einem Rolleneintrag hinzufügen möchten, müssen die hinzuzufügenden Parameter im Rolleneintrag der übergeordneten Rolle vorhanden sein. Die Parameter müssen auch für das angegebene Cmdlet vorhanden sein.

  - Wenn Sie Parameter aus einem Rolleneintrag entfernen möchten, können die Parameter, die Sie entfernen, nicht in Rolleneinträgen untergeordneter Rollen enthalten sein. Sie müssen die Parameter aus den Rolleneinträgen der untergeordneten Rollen entfernen. Verwenden Sie das Verfahren unter "Verwenden Sie die Shell, um mindestens einen Parameter aus einem Rolleneintrag zu entfernen" weiter unten in diesem Thema, um die Parameter aus den Rolleinträgen aller untergeordneten Rollen zu entfernen.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden Sie die Shell, um mindestens einen Parameter zu einem Rolleneintrag hinzuzufügen

Zum Hinzufügen von Parametern zu einem Rolleneintrag müssen Sie die hinzuzufügenden Parameter mithilfe des Parameters *Parameters* angeben. Anschließend müssen Sie den Parameter *AddParameter* angeben, um anzuzeigen, dass Sie einen Hinzufügevorgang ausführen möchten.

Verwenden Sie zum Hinzufügen von Parametern zu einem Rolleneintrag die folgende Syntax.

```powershell
    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -AddParameter
```

In diesem Beispiel werden die Parameter *EmailAddresses* und *Type* zum Cmdlet **Set-Mailbox** für die Rolle "Recipient Administrators" hinzugefügt.

```powershell
    Set-ManagementRoleEntry "Recipient Administrators\Set-Mailbox" -Parameters EmailAddresses, Type -AddParameter
```

Ausführliche Informationen zur Syntax und zu den Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Verwenden Sie die Shell, um mindestens einen Parameter aus einem Rolleneintrag zu entfernen

Zum Entfernen von Parametern aus einem Rolleneintrag müssen Sie die zu entfernenden Parameter mithilfe des Parameters *Parameters* angeben. Anschließend müssen Sie den Parameter *RemoveParameter* angeben, um anzuzeigen, dass Sie einen Entfernvorgang ausführen möchten.

Verwenden Sie zum Entfernen von Parametern aus einem Rolleneintrag die folgende Syntax.

```powershell
    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...> -RemoveParameter
```

In diesem Beispiel werden für die Rolle "Tier 1 Server Administrators" die Parameter *Port*, *ProtocolLoggingLevel* und *SmartHostAuthMechanism* aus dem Cmdlet **Set-SendConnector** entfernt.

```powershell
    Set-ManagementRoleEntry "Tier 1 Server Administrators\Set-SendConnector" -Parameters Port, ProtocolLoggingLevel, SmartHostAuthMechanism -RemoveParameter
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Verwenden Sie die Shell, um alle Parameter aus einem Rolleneintrag zu entfernen

Zum Entfernen aller Parametern aus einem Rolleneintrag müssen Sie den Wert `$Null` für den Parameter *Parameters* angeben. Sie müssen den Parameter *RemoveParameters* nicht einbeziehen.

Das Entfernen aller Parameter aus einem Rolleneintrag ist insbesondere dann hilfreich, wenn Sie für ein Cmdlet nur wenige Parameter verfügbar machen möchten und alle anderen Parameter ausgeschlossen werden sollen. Wenn die Rolle keinen Zugriff auf ein Cmdlet erhalten soll, sollten Sie den entsprechenden Rolleneintrag vollständig aus der Rolle entfernen, anstatt nur die Parameter zu entfernen. Weitere Informationen zum Entfernen eines Rolleneintrags aus einer Rolle finden Sie unter [Entfernen eines Rolleneintrags aus einer Rolle](remove-a-role-entry-from-a-role-exchange-2013-help.md).


> [!WARNING]
> Löschvorgänge können nicht rückgängig gemacht werden. Wenn Sie versehentlich alle Parameter aus einem Rolleneintrag entfernen, müssen Sie diese manuell erneut hinzufügen.



Verwenden Sie zum Entfernen aller Parameter aus einem Rolleneintrag die folgende Syntax.

```powershell
    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters $Null 
```

In diesem Beispiel werden für die Rolle "Recipient Administrators" alle Parameter aus dem Cmdlet **Set-CASMailbox** entfernt.

```powershell
    Set-ManagementRoleEntry "Recipient Administrators\Set-CASMailbox" -Parameters $Null 
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

## Verwenden der Shell zum Anwenden einer bestimmten Gruppe von Parametern

Wenn nur bestimmte Parameter in einen Rolleneintrag eingeschlossen werden sollen, geben Sie nur den Parameter *Parameters* an. Schließen Sie nicht die Parameter *AddParameter* oder *RemoveParameter* ein. Wenn Sie nur den Parameter *Parameters* angeben, werden nur die von Ihnen angegebenen Parameter in den Rolleneintrag einbezogen. Alle anderen Parameter werden entfernt.

Verwenden Sie zum Festlegen einer bestimmten Gruppe von Parametern die folgende Syntax.

```powershell
    Set-ManagementRoleEntry <role name>\<cmdlet> -Parameters <parameter 1>, <parameter 2>, <parameter...>
```

In diesem Beispiel werden für die Rolle "Seattle Mail Recipients" nur die Parameter *Identity*, *DisplayName*, *MissedCallNotificationEnabled* und *PersonalAuthAttendantEnabled* für das Cmdlet **Set-UMMailbox** eingeschlossen.

```powershell
    Set-ManagementRoleEntry "Seattle Mail Recipients\Set-UMMailbox" -Parameters Identity, DisplayName, MissedCallNotificationEnabled, PersonalAutoAttendantEnabled
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ManagementRoleEntry](https://technet.microsoft.com/de-de/library/dd351162\(v=exchg.150\)).

