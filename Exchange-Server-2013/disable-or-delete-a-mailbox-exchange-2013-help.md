---
title: 'Deaktivieren oder Löschen eines Postfachs: Exchange 2013 Help'
TOCTitle: Deaktivieren oder Löschen eines Postfachs
ms:assetid: 31ad25d6-2942-4fd9-aecb-cdf9654163d2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ863434(v=EXCHG.150)
ms:contentKeyID: 50554788
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren oder Löschen eines Postfachs

 

_**Gilt für:** Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Sie können EAC oder die Shell zum Deaktivieren oder Löschen eines Postfachs in Exchange 2013 verwenden. Wenn ein Postfach deaktiviert oder gelöscht wird, behält Exchange das Postfach in der Postfachdatenbank bei und wechselt den Status des Postfachs zu deaktiviert. Deaktivierte und gelöschte Postfächer verbleiben in der Postfachdatenbank, bis der Aufbewahrungszeitraum für gelöschte Postfächer abläuft. Das ist standardmäßig nach 30 Tagen der Fall. Nach Ablauf des Aufbewahrungszeitraums wird das Postfach endgültig gelöscht*gespülten*.

Informationen zum Löschen eines Postfachs in Exchange Online finden Sie unter [Löschen oder Wiederherstellen von Benutzerpostfächern in Exchange Online](https://technet.microsoft.com/de-de/library/dn186233\(v=exchg.150\)).


> [!NOTE]
> Deaktivierte oder gelöschte Postfächer werden als <EM>getrennte Postfächer</EM> bezeichnet.



Der wichtigste Unterschied zwischen dem Löschen und dem Deaktivieren eines Postfachs ist, dass beim Deaktivieren eines Postfachs die Exchange-Attribute vom entsprechenden Active Directory-Benutzerkonto entfernt werden, das Benutzerkonto aber erhalten bleibt. Wenn Sie ein Postfach löschen, werden die Exchange-Attribute und das Active Directory-Benutzerkonto gelöscht. Dieser Unterschied bestimmt zudem Ihre Optionen bei der erneuten Verbindung oder Wiederherstellung deaktivierter oder gelöschter Postfächer.

In der folgenden Tabelle wird gezeigt, welche Arten von Exchange-Postfächern deaktiviert und gelöscht werden können.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Postfachtyp</th>
<th>Deaktivieren</th>
<th>Löschen</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Archivpostfach</p></td>
<td><p>Ja</p></td>
<td><p>Nein *</p></td>
</tr>
<tr class="even">
<td><p>Verknüpftes Postfach</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Ressourcenpostfach (Raum oder Gerät)</p></td>
<td><p>Nein</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Freigegebenes Postfach</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Benutzerpostfach</p></td>
<td><p>Ja</p></td>
<td><p>Ja</p></td>
</tr>
</tbody>
</table>


\* Wenn ein Archivpostfach aktiviert ist, wird es gelöscht, wenn das primäre Postfach gelöscht wird. Informationen zum Deaktivieren von Archivpostfächern finden Sie unter [Verwalten von In-Situ-Archiven in Exchange 2013](manage-in-place-archives-in-exchange-2013-exchange-2013-help.md).

Wenn ein Administrator ein Benutzerkonto mit einem Postfach löscht, erkennt der Exchange-Informationsspeicher nach einiger Zeit, dass das Postfach nicht mehr mit einem Benutzerkonto verbunden ist, und markiert dieses Postfach zur Löschung, auch wenn es archiviert ist. Wenn Sie das Postfach beibehalten möchten, gehen Sie wie folgt vor:

1.  Deaktivieren Sie das Benutzerkonto, anstatt es zu löschen.

2.  Ändern Sie die Eigenschaften des Postfachs, um seine Verwendung und den Zugriff darauf einzuschränken. Setzen Sie z. B. das Sende- und das Empfangskontingent gleich 1, blockieren Sie die Sendung von Nachrichten an das Postfach, und begrenzen sie den Zugriff auf die Mailbox.

3.  Behalten Sie das Postfach bei, bis alle Daten entfernt sind oder die Archivierung nicht mehr notwendig ist.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit getrennten Postfächern finden Sie in den folgenden Themen:

  - [Getrennte Postfächer](disconnected-mailboxes-exchange-2013-help.md)

  - [Verbinden eines deaktivierten Postfachs](connect-a-disabled-mailbox-exchange-2013-help.md)

  - [Verbinden oder Wiederherstellen eines gelöschten Postfachs](connect-or-restore-a-deleted-mailbox-exchange-2013-help.md)

  - [Endgültiges Löschen eines Postfachs](permanently-delete-a-mailbox-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren eines Postfachs

Wie bereits dargestellt, werden bei der Deaktivierung eines Postfachs die Exchange-Attribute vom entsprechenden Active Directory-Benutzerkonto entfernt, das Benutzerkonto bleibt aber erhalten.

## Deaktivieren eines Postfachs mithilfe der Exchange-Verwaltungskonsole

Das folgende Verfahren veranschaulicht, wie ein Benutzerpostfach deaktiviert wird. Mit diesem Verfahren können Sie auch andere Postfachtypen deaktivieren, nachdem Sie die entsprechende Seite in der Exchange-Verwaltungskonsole aufgerufen haben.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, das Sie deaktivieren möchten.

3.  Klicken Sie auf **Mehr**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)"), und klicken Sie dann auf **Deaktivieren**.

4.  Es wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie das Postfach wirklich deaktivieren möchten. Klicken Sie auf **Ja**, um das Postfach zu deaktivieren.

Das Postfach wird aus der Postfachliste entfernt.

## Verwenden der Shell zum Deaktivieren eines Postfachs

Verwenden Sie den folgenden Befehl, um Benutzerpostfächer, verknüpfte Postfächer, Ressourcenpostfächer und freigegebene Postfächer zu deaktivieren.

    Disable-Mailbox <identity>

Wenn Sie diesen Befehl ausführen, müssen Sie in einer Meldung bestätigen, dass Sie das Postfach deaktivieren möchten.

Im Folgenden finden Sie einige Beispiele für Befehle zum Deaktivieren von Postfächern.

    Disable-Mailbox danj

    Disable-Mailbox "Conf Room 31/1234 (12)"

    Disable-Mailbox sharedmbx@contoso.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Sie ein Postfach erfolgreich deaktiviert haben:

  - Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger**, navigieren Sie zur entsprechenden Seite für den deaktivierten Postfachtyp, und vergewissern Sie sich, dass das Postfach nicht mehr aufgeführt wird.

  - Klicken Sie in Active Directory-Benutzer und -Computer mit der rechten Maustaste auf das Benutzerkonto, dessen Postfach Sie deaktiviert haben, und anschließend auf **Eigenschaften**. Auf der Registerkarte **Allgemein** ist das Feld **E-Mail** leer. Dadurch wird bestätigt, dass das Postfach deaktiviert wurde, das Benutzerkonto aber noch vorhanden ist.

  - Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisconnectReason,DisconnectDate
    
    Mit dem Wert `Disabled` der Eigenschaft *DisconnectReason* wird angegeben, dass das Postfach deaktiviert wurde.
    

    > [!NOTE]
    > Wenn Sie ein Postfach löschen, ist der Wert der Eigenschaft <EM>DisconnectReason</EM> auch <CODE>Disabled</CODE>. Jedoch wird das entsprechende Active Directory-Benutzerkonto gelöscht.



  - Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-User <identity>
    
    Beachten Sie, dass die Eigenschaft *RecipientType* den Wert `User` aufweist, und nicht `UserMailbox`, dem Wert für Benutzer mit aktivierten Postfächern. Dadurch wird auch bestätigt, dass das Postfach deaktiviert wurde, das Benutzerkonto aber erhalten bleibt.

## Löschen eines Postfachs

Wie bereits erläutert, werden beim Löschen eines Postfachs die Exchange-Attribute und das Active Directory-Benutzerkonto gelöscht. Das Postfach (und das Archivpostfach, sofern aktiviert) werden endgültig aus der Postfachdatenbank gelöscht, nachdem der Aufbewahrungszeitraum abgelaufen ist.

## Löschen eines Postfachs mithilfe der Exchange-Verwaltungskonsole

Das folgende Verfahren veranschaulicht, wie ein Benutzerpostfach gelöscht wird. Mit diesem Verfahren können Sie auch andere Postfachtypen löschen, nachdem Sie die entsprechende Seite in der Exchange-Verwaltungskonsole aufgerufen haben.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, das Sie löschen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

3.  Es wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie das Postfach wirklich löschen möchten. Klicken Sie auf **Ja**, um das Postfach zu löschen.

Das Postfach wird aus der Postfachliste entfernt.

## Löschen eines Postfachs mithilfe der Shell

Verwenden Sie den folgenden Befehl, um Benutzerpostfächer, verknüpfte Postfächer, Ressourcenpostfächer und freigegebene Postfächer zu löschen.

    Remove-Mailbox <identity>

Wenn Sie diesen Befehl ausführen, müssen Sie in einer Meldung bestätigen, dass Sie das Postfach und das entsprechende Active Directory-Benutzerkonto entfernen möchten.

Im Folgenden finden Sie einige Beispiele für Befehle zum Löschen von Postfächern.

    Remove-Mailbox pilarp@contoso.com

    Remove-Mailbox "Fleet Van (16)"

    Remove-Mailbox corpprint

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eines der folgenden Verfahren aus, um das erfolgreiche Löschen eines Postfachs zu überprüfen.

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger**, navigieren Sie dann zur entsprechenden Seite für den deaktivierten Postfachtyp, und vergewissern Sie sich, dass das Postfach nicht mehr aufgeführt wird.

2.  Vergewissern Sie sich in Active Directory-Benutzer und -Computer, dass das entsprechende Benutzerkonto nicht mehr aufgeführt wird.

– oder –

1.  Führen Sie den folgenden Befehl aus, um zu überprüfen, ob das Postfach gelöscht wurde.
    
        Get-MailboxDatabase | Get-MailboxStatistics | Where { $_.DisplayName -eq "<display name>" } | fl DisconnectReason,DisconnectDate
    
    Mit dem Wert `Disabled` der Eigenschaft *DisconnectReason* wird angegeben, dass das Postfach gelöscht wurde.
    

    > [!NOTE]
    > Wenn Sie ein Postfach deaktivieren, ist der Wert der Eigenschaft <EM>DisconnectReason</EM> auch <CODE>Disabled</CODE>. Jedoch wird das entsprechende Active Directory-Benutzerkonto beibehalten.



2.  Führen Sie den folgenden Befehl aus, um zu überprüfen, ob das Active Directory-Benutzerkonto gelöscht wurde.
    
        Get-User <identity>
    
    Der Befehl gibt einen Fehler zurück, der angibt, dass der Benutzer nicht gefunden wurde. So wird bestätigt, dass das Konto gelöscht wurde.

