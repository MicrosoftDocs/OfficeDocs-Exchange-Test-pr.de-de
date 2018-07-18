---
title: 'Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien: Exchange 2013 Help'
TOCTitle: Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien
ms:assetid: 25913e43-326a-4371-90b5-021a35f100fe
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd638100(v=EXCHG.150)
ms:contentKeyID: 50475361
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Grundlegendes zu Verwaltungsrollen-Zuweisungsrichtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Eine *Richtlinie für die Verwaltungsrollenzuweisung* ist eine Sammlung aus einer oder mehreren Endbenutzerverwaltungsrollen, mit denen Endbenutzer ihre eigene Microsoft Exchange Server 2013-Postfach- und Verteilergruppenkonfiguration verwalten können. Mit Rollenzuweisungsrichtlinien, die Teil des rollenbasierten Zugriffssteuerungsmodells (Role Based Access Control, RBAC) in Exchange 2013 sind, können Sie steuern, welche spezifischen Konfigurationseinstellungen Endbenutzer für Postfächer und Verteilergruppen ändern können. Rollenzuweisungsrichtlinien können auf unterschiedliche Benutzergruppen abgestimmt sein.


> [!NOTE]
> Inhalt dieses Themas ist die erweiterte RBAC-Funktionalität. Informationen zum Verwalten grundlegender Exchange 2013-Berechtigungen finden Sie unter <A href="permissions-exchange-2013-help.md">Berechtigungen</A>. In diesem Thema wird z.&nbsp;B. beschrieben, wie Sie das Exchange Admin Center (EAC) verwenden, um Mitglieder zu Rollengruppen hinzuzufügen oder aus diesen zu entfernen oder um Rollengruppen und Rollenzuweisungsrichtlinien zu erstellen oder zu ändern.



Weitere Informationen zu RBAC finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

**Inhalt**

Ebenen von Rollenzuweisungsrichtlinien

Standard- und explizite Rollenzuweisungsrichtlinien

Verwenden von Rollenzuweisungsrichtlinien

Verwalten von Rollenzuweisungsrichtlinien

## Ebenen von Rollenzuweisungsrichtlinien

Im Folgenden werden die Ebenen beschrieben, aus denen das Modell für Rollenzuweisungsrichtlinien besteht:

  - **Postfach**   Postfächern wird eine einzelne Rollenzuweisungsrichtlinie zugewiesen. Wird einem Postfach eine Rollenzuweisungsrichtlinie zugewiesen, werden die Zuweisungen zwischen Verwaltungsrollen und einer Rollenzuweisungsrichtlinie auf das Postfach angewendet. Dadurch werden dem Postfach alle von den Verwaltungsrollen bereitgestellten Berechtigungen erteilt.

  - **Richtlinie für die Verwaltungsrollenzuweisung**   Die *Richtlinie für die Verwaltungsrollenzuweisung* ist ein spezielles Objekt in Exchange 2013. Benutzern wird eine Rollenzuweisungsrichtlinie zugeordnet, wenn ihr Postfach erstellt wird oder Sie die Rollenzuweisungsrichtlinie für ein Postfach ändern. Dieser weisen Sie auch Endbenutzerverwaltungsrollen zu. Die Kombination aller Rollen in einer Rollenzuweisungsrichtlinie definiert all das, was der Benutzer in seinem Postfach oder in Verteilergruppen verwalten kann.

  - **Verwaltungsrollenzuweisung**   Eine *Verwaltungsrollenzuweisung* ist die Verknüpfung zwischen einer Verwaltungsrolle und eine Rollenzuweisungsrichtlinie. Durch das Zuweisen einer Verwaltungsrolle zu einer Rollenzuweisungsrichtlinie wird die Möglichkeit gegeben, die in der Verwaltungsrolle definierten Cmdlets und Parameter zu verwenden. Beim Erstellen einer Rollenzuweisung zwischen einer Rollenzuweisungsrichtlinie und einer Verwaltungsrolle können Sie keinen Bereich angeben. Der von der Zuweisung angewendete Bereich basiert auf der Verwaltungsrolle und ist entweder `Self` oder `MyGAL`. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollenzuweisungen](understanding-management-role-assignments-exchange-2013-help.md).

  - **Verwaltungsrolle**   Eine *Verwaltungsrolle* ist ein Container für eine Gruppierung von Verwaltungsrolleneinträgen. Rollen werden zum Definieren der spezifischen Aufgaben verwendet, die Benutzer mit ihrem Postfach oder Verteilergruppen ausführen können. Ein *Verwaltungsrolleneintrag* ist ein Cmdlet, Skript oder eine spezielle Berechtigung zur Ausführung der einzelnen spezifischen Aufgaben in einer Verwaltungsrolle. Sie können nur Endbenutzerverwaltungsrollen mit Rollenzuweisungsrichtlinien verwenden. Weitere Informationen finden Sie unter [Grundlegendes zu Verwaltungsrollen](understanding-management-roles-exchange-2013-help.md).

  - **Verwaltungsrolleneintrag**   Verwaltungsrolleneinträge sind die einzelnen Einträge in einer Verwaltungsrolle, die bestimmen, welche Cmdlets und Parameter für die Verwaltungsrolle und die Rollengruppe zur Verfügung stehen. Jeder Rolleneintrag besteht aus einem Cmdlet und den Parametern, auf die über die Verwaltungsrolle zugegriffen werden kann.

Die folgende Abbildung zeigt die einzelnen Ebenen für die in der vorhergehenden Liste aufgeführten Rollenzuweisungsrichtlinien und die Beziehung der einzelnen Ebenen zueinander.

**Modell der Richtlinien für die Verwaltungsrollenzuweisung**

![Rollenzuweisungen – Modellbeziehungen](images/Dd638100.7f7c11ca-0d61-464d-98a3-a9991ec811b5(EXCHG.150).jpg "Rollenzuweisungen – Modellbeziehungen")

Weitere Informationen zu Verwaltungsrollen, Rollenzuweisungen und Bereichen finden Sie unter [Grundlegendes zur rollenbasierten Zugriffssteuerung](understanding-role-based-access-control-exchange-2013-help.md).

## Standard- und explizite Rollenzuweisungsrichtlinien

Die folgenden Abschnitte beschreiben die beiden Arten von Rollenzuweisungsrichtlinien in Exchange 2013.

## Standard-Rollenzuweisungsrichtlinie

Eine Standard-Rollenzuweisungsrichtlinie ist eine Rollenzuweisungsrichtlinie, die einem Postfach zugewiesen wird, wenn dieses erstellt oder auf einen Server, auf dem Exchange 2013 ausgeführt wird, verschoben wird und keine Rollenzuweisungsrichtlinie mithilfe des Parameters *RoleAssignmentPolicy* in den Cmdlets **New-Mailbox** oder **Enable-Mailbox** bereitgestellt wurde.

Exchange 2013 beinhaltet eine Standard-Rollenzuweisungsrichtlinie, die Endbenutzern die am häufigsten verwendeten Berechtigungen zur Verfügung stellt. Sie können die Standardberechtigungen in der Standard-Rollenzuweisungsrichtlinie ändern, indem Sie Verwaltungsrollen hinzufügen oder entfernen.

Wenn Sie die Standard-Rollenzuweisungsrichtlinie durch eine eigene Standard-Rollenzuweisungsrichtlinie ersetzen möchten, können Sie mithilfe des Cmdlets **Set-RoleAssignmentPolicy** einen neuen Standard auswählen. Wenn Sie dies tun, werden alle neuen Postfächer der Rollenzuweisungsrichtlinie zugewiesen, die Sie standardmäßig angegeben haben, sofern Sie keine explizite Rollenzuweisungsrichtlinie angeben.

Wenn Sie die Standard-Rollenzuweisungsrichtlinie ändern, wird Postfächern, denen die Standard-Rollenzuweisungsrichtlinie zugewiesen wurde, nicht automatisch die neue Standard-Rollenzuweisungsrichtlinie zugewiesen. Wenn Sie vorher erstellte Postfächer so aktualisieren möchten, dass diese die von Ihnen als Standard festgelegten Rollenzuweisungsrichtlinien verwenden, müssen Sie dazu das Cmdlet **Set-Mailbox** verwenden.

## Explizite Rollenzuweisungsrichtlinie

Eine explizite Rollenzuweisungsrichtlinie ist eine Richtlinie, die Sie einem Postfach mithilfe des Parameters *RoleAssignmentPolicy* in den Cmdlets **New-Mailbox**, **Set-Mailbox** oder **Enable-Mailbox** manuell zuweisen. Wenn Sie eine explizite Rollenzuweisungsrichtlinie zuweisen, wird die neue Richtlinie sofort wirksam und ersetzt die vorher zugewiesene explizite Rollenzuweisungsrichtlinie.

## Verwenden von Rollenzuweisungsrichtlinien

Mithilfe von Rollenzuweisungsrichtlinien können Sie Berechtigungen auf der Grundlage dessen erteilen, welche Einstellungen zum Erfüllen von Geschäftsanforderungen Ihre Benutzer konfigurieren können sollten. Wenn die Standard-Rollenzuweisungsrichtlinie Ihren Anforderungen genügt, müssen Sie keine Anpassung vornehmen. Wenn Sie jedoch über viele verschiedene Benutzergruppen mit unterschiedlichen Anforderungen verfügen, können Sie für diese Rollenzuweisungsrichtlinien erstellen.

Die von Ihnen verwendete Standard-Rollenzuweisungsrichtlinie sollte die Berechtigungen enthalten, die für die größte Benutzergruppe gelten. Erstellen Sie dann Rollenzuweisungsrichtlinien für die jeweiligen speziellen Benutzergruppen, und passen Sie diese Rollenzuweisungsrichtlinien an, um mehr oder weniger eingeschränkte oder Berechtigungen zu erteilen. Wenn Sie Ihre Rollenzuweisungsrichtlinien auf diese Weise organisieren, reduzieren Sie die Komplexität, indem Sie nur spezialisierten Benutzern explizite Rollenzuweisungsrichtlinien zuweisen, während die Mehrzahl der Benutzer die gängigen Berechtigungen erhält, die von der Standard-Rollenzuweisungsrichtlinie bereitgestellt werden.

Ein Postfach kann nur eine Rollenzuweisungrichtlinie haben. Allen Benutzern, auch Administratoren und spezialisierten Benutzern, wird eine Rollenzuweisungsrichtlinie zugewiesen. Wenn Sie möchten, dass ein Benutzer über andere Berechtigungen verfügt, müssen Sie dem Postfach dieses Benutzers eine andere Rollenzuweisungsrichtlinie mit den erforderlichen Berechtigungen zuweisen.

## Verwalten von Rollenzuweisungsrichtlinien

Um eine neue Rollenzuweisungsrichtlinie hinzuzufügen, müssen Sie diese zunächst erstellen und festlegen, ob es sich dabei um die Standard-Rollenzuweisungsrichtlinie handeln soll. Nachdem Sie eine Rollenzuweisungsrichtlinie erstellt haben, weisen Sie der Rollenzuweisungsrichtlinie Verwaltungsrollen zu. Anschließend weisen Sie die Rollenzuweisungsrichtlinie wiederum Postfächern zu. Sie können Verwaltungsrollen später nach Bedarf hinzufügen oder entfernen oder eine andere Rollenzuweisungsrichtlinie als Standard auswählen.

Die folgende Tabelle enthält eine Liste der Ebenen der Rollenzuweisungsrichtlinien und Links zu den Vorgehensweisen beim Verwalten der einzelnen Ebenen.

### Verwaltung von Rollenzuweisungsrichtlinien

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Ebene des Modells für Rollenzuweisungsrichtlinien</th>
<th>Verwaltungsthemen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Postfach</p></td>
<td><p><a href="manage-user-mailboxes-exchange-2013-help.md">Verwalten von Benutzerpostfächern</a></p>
<p><a href="change-the-assignment-policy-on-a-mailbox-exchange-2013-help.md">Ändern der Zuweisungsrichtlinie für ein Postfach</a></p></td>
</tr>
<tr class="even">
<td><p>Rollenzuweisungsrichtlinie</p></td>
<td><p><a href="manage-role-assignment-policies-exchange-2013-help.md">Verwalten von Rollenzuweisungsrichtlinien</a></p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Verwaltungsrollen und -zuweisungen</p></td>
<td><p><a href="manage-role-assignment-policies-exchange-2013-help.md">Verwalten von Rollenzuweisungsrichtlinien</a></p>
<p></p></td>
</tr>
<tr class="even">
<td><p>Verwaltungsrolleneinträge</p></td>
<td><p><a href="add-a-role-entry-to-a-role-exchange-2013-help.md">Hinzufügen eines Rolleneintrags zu einer Rolle</a></p>
<p><a href="change-a-role-entry-exchange-2013-help.md">Ändern Sie einen rolleneintrag</a></p>
<p><a href="remove-a-role-entry-from-a-role-exchange-2013-help.md">Entfernen eines Rolleneintrags aus einer Rolle</a></p>

> [!NOTE]
> Beim Ändern der Verwaltungsrolleneinträge in Verwaltungsrollen einer Rollenzuweisungsrichtlinie handelt es sich um eine fortgeschrittene Aufgabe, die in den meisten Fällen nicht erforderlich ist. Sie können stattdessen möglicherweise eine vorher bestehende Verwaltungsrolle verwenden, die Ihren Anforderungen entspricht. Weitere Informationen finden Sie unter <A href="built-in-role-groups-exchange-2013-help.md">Integrierte Rollengruppen</A>.


</td>
</tr>
</tbody>
</table>

