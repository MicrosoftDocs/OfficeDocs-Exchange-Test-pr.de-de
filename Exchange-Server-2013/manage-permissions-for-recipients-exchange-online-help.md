---
title: 'Verwalten von Berechtigungen für Empfänger: Exchange 2013 Help'
TOCTitle: Verwalten von Berechtigungen für Empfänger
ms:assetid: 749cdfe3-496b-453f-96eb-20a0bf28fd52
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ919240(v=EXCHG.150)
ms:contentKeyID: 51407063
ms.date: 05/05/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Berechtigungen für Empfänger

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-04-20_

Sie können mithilfe der Exchange-Verwaltungskonsole oder Shell Benutzern oder Gruppen (*Stellvertretungen* genannte) Berechtigungen zuweisen, die diesen das Öffnen und Senden von Nachrichten aus anderen Postfächern erlauben. Berechtigungen können Benutzerpostfächern, verknüpften Postfächern, Ressourcenpostfächern und freigegebenen Postfächern zugewiesen werden. Sie können Berechtigungen auch Verteilergruppen, dynamischen Verteilergruppen und für E-Mail aktivierten Sicherheitsgruppen zuweisen, damit Stellvertretungen Nachrichten im Auftrag der Gruppe senden können. Sie können Stellvertretungen die folgenden Berechtigungen für den Zugriff auf Postfächer und das Senden von Nachrichten im Auftrag von Postfächern oder Gruppen zuweisen:

  - **Vollzugriff**   Diese Berechtigung ermöglicht es einer Stellvertretung, das Postfach eines Benutzers zu öffnen und auf die Inhalte des Postfachs zuzugreifen. Durch Zuweisen der Berechtigung "Vollzugriff" kann die Stellvertretung jedoch keine E-Mail aus dem Postfach senden. Sie müssen der Stellvertretung die Berechtigung "Senden als" oder "Senden im Auftrag von" zuweisen, damit sie E-Mail senden kann.
    
    Die Berechtigung "Vollzugriff" steht nicht zur Verfügung, wenn Berechtigungen für Gruppen konfiguriert werden.

  - **Senden als**   Diese Berechtigung ermöglicht es einer Stellvertretung, Nachrichten zu senden. Nachdem diese Berechtigung einer Stellvertretung zugewiesen wurde, werden alle Nachrichten, die eine Stellvertretung aus dem Postfach sendet, so angezeigt, als wären sie vom Postfachbesitzer gesendet worden. Diese Berechtigung ermöglicht es einer Stellvertretung jedoch nicht, sich am Benutzerpostfach anzumelden. Die Berechtigung erlaubt allerdings nur Benutzern das Öffnen des Postfachs. Wenn diese Berechtigung einer Gruppe zugewiesen ist, wird eine von der Stellvertretung gesendete Nachricht so angezeigt, als wäre sie von der Gruppe gesendet worden.

  - **Senden im Auftrag von**   Diese Berechtigung ermöglicht es einer Stellvertretung ebenfalls, das Postfach zum Senden von Nachrichten zu verwenden. Nachdem diese Berechtigung der Stellvertretung zugewiesen wurde, gibt die Adresse **Von** in allen von der Stellvertretung gesendeten Nachrichten an, dass die Nachricht im Auftrag des Postfachbesitzers von der Stellvertretung gesendet wurde.


> [!NOTE]
> Wenn Sie die Berechtigung „Vollzugriff“, „Senden als“ oder „Senden im Auftrag von“ für den Zugriff auf ein Postfach zuweisen, das aus Adresslisten ausgeblendet ist, kann die Stellvertretung das Postfach nicht öffnen und keine Nachrichten senden.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zuweisen von Berechtigungen zu einem Postfach

Wie bereits erwähnt, können Sie Benutzerpostfächern, verknüpften Postfächern, Ressourcenpostfächern und freigegebenen Postfächern Stellvertretungsberechtigungen zuweisen. Über die Shell können Sie auch Stellvertretungsberechtigungen für den Zugriff auf ein Discoverypostfach zuweisen.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen und Stellvertretung" im Abschnitt "Empfängerbereitstellungsberechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

## Zuweisen von Berechtigungen mithilfe der Exchange-Verwaltungskonsole

Das folgende Verfahren veranschaulicht, wie einem Benutzerpostfach Berechtigungen zugewiesen werden. Das Verfahren zum Zuweisen von Berechtigungen zu Ressourcen- und freigegebenen Postfächern ist ähnlich. Sie navigieren in der Exchange-Verwaltungskonsole zur Seite **Ressourcen** oder **Freigegeben** und wählen das Postfach aus, dem die Berechtigungen zugewiesen werden sollen.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Postfächer auf das Postfach, dem Sie Berechtigungen zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachstellvertretung**.

4.  Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Seite mit der eine Liste aller Empfänger in der Exchange-Organisation anzuzeigen, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
    
    Um eine Berechtigung für einen Empfänger zu entfernen, wählen Sie die gewünschte Berechtigung aus und klicken dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Massenzuweisung von Berechtigungen mithilfe der Exchange-Verwaltungskonsole

Verwenden Sie die folgenden Schritte für die Massenzuweisung von Berechtigungen

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie die Postfächer aus, denen Sie Berechtigungen zuweisen möchten.

3.  Klicken oder tippen Sie auf **Weitere Optionen** im rechten Bereich, und klicken Sie unter **Stellvertretung für Postfächer** auf **Hinzufügen**.

4.  Klicken oder tippen Sie auf der Seite **Massenhinzufügen Stellvertretung** auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") unter der entsprechenden Berechtigung zum Anzeigen einer Seite, die alle Empfänger in der Exchange-Organisation auflistet, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie sie der Liste hinzu, und klicken Sie dann auf **OK**.
    
    Um eine Berechtigung für Empfänger zu entfernen, wählen Sie die Empfänger unter der entsprechenden Berechtigung aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

## Zuweisen von Benutzerberechtigungen für das Senden von E-Mails aus dem Postfach eines anderen Benutzers mithilfe der Exchange-Verwaltungskonsole

Das folgende Verfahren beschreibt, wie Sie eine Benutzerberechtigung für das Senden von E-Mails aus dem Postfach eines anderen Benutzers zuweisen.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Postfächer auf das Postfach, dem Sie die Berechtigung zum "Senden im Auftrag von" zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachstellvertretung**.

4.  Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter **Senden als** oder **Senden im Auftrag von** auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Seite mit einer Liste aller Empfänger in der Exchange-Organisation anzuzeigen, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
    
    Die Berechtigung **Senden als** ermöglicht es der Stellvertretung, Nachrichten von diesem Postfach zu senden.
    
    Die Berechtigung **Senden im Auftrag von** ermöglicht es der Stellvertretung, Nachrichten im Auftrag von diesem Postfach zu senden. Die Zeile **Von** gibt in allen von der Stellvertretung gesendeten Nachrichten an, dass die Nachricht im Auftrag des Postfachbesitzers von der Stellvertretung gesendet wurde.
    

    > [!NOTE]
    > Falls der Benutzer außerdem den Inhalt des Postfachs öffnen und anzeigen soll, müssen Sie dem Benutzer die Berechtigung <STRONG>Vollzugriff</STRONG> zuweisen.



5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Zuweisen von Benutzerberechtigungen für das Senden von E-Mails von einer Gruppe mithilfe der Exchange-Verwaltungskonsole

Das folgende Verfahren beschreibt, wie Sie eine Benutzerberechtigung für das Senden von E-Mails von einer Gruppe zuweisen.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Gruppen**.

2.  Klicken Sie in der Liste der Gruppen auf die Gruppe, der Sie die Berechtigung "Senden als" zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite der Gruppe auf **Gruppendelegierung**.

4.  Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter **Senden als** oder **Senden im Auftrag von** auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Seite mit einer Liste aller Empfänger in der Exchange-Organisation anzuzeigen, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
    
    Die Berechtigung **Senden als** ermöglicht es der Stellvertretung, Nachrichten von dieser Gruppe zu senden.
    
    Die Berechtigung **Senden im Auftrag von** ermöglicht es der Stellvertretung, Nachrichten im Auftrag von dieser Gruppe zu senden. Die Zeile **Von** gibt in allen von der Stellvertretung gesendeten Nachrichten an, dass die Nachricht im Auftrag der Gruppe von der Stellvertretung gesendet wurde.

5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Zuweisen von Vollzugriffsberechtigungen über die Exchange-Verwaltungskonsole

Das folgende Verfahren veranschaulicht, wie einem Benutzerpostfach Vollzugriffsberechtigungen zugewiesen werden.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Postfächer auf das Postfach, dem Sie Vollzugriffsberechtigungen zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachstellvertretung**.

4.  Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter **Vollzugriff** auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Seite mit einer Liste aller Empfänger in der Exchange-Organisation anzuzeigen, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
    
    Die Berechtigung **Vollzugriff** ermöglicht es einer Stellvertretung, das Postfach eines Benutzers zu öffnen und auf die Inhalte des Postfachs zuzugreifen.
    

    > [!NOTE]
    > Durch Zuweisen der Berechtigung <STRONG>Vollzugriff</STRONG> kann die Stellvertretung jedoch keine E-Mail aus dem Postfach senden. Sie müssen der Stellvertretung die Berechtigung <STRONG>Senden als</STRONG> oder <STRONG>Senden im Auftrag von</STRONG> zuweisen, damit sie E-Mails senden kann.



5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Zuweisen von Berechtigungen mithilfe der Shell

In den folgenden Abschnitten wird erklärt, wie Sie mithilfe der Shell die Berechtigungen "Vollzugriff", "Senden als" und "Senden im Auftrag von" für Postfächer verwalten.

## Verwalten der Berechtigung "Vollzugriff"

Die folgenden Beispiele zeigen, wie Sie mit den Cmdlets **Add-MailboxPermission** und **Remove-MailboxPermission** die Berechtigung "Vollzugriff" verwalten.

Bei diesem Beispiel wird der Stellvertretung Raymond Sam die Berechtigung "Vollzugriff" für das Postfach von Terry Adams zugewiesen.

    Add-MailboxPermission -Identity "Terry Adams" -User raymonds -AccessRights FullAccess -InheritanceType all

Bei diesem Beispiel wird Esther Valle die Berechtigung "Vollzugriff" für das Standardpostfach für die Discoverysuche der Organisation zugewiesen.

    Add-MailboxPermission -Identity "DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}" -User estherv -AccessRights FullAccess -InheritanceType all

Bei diesem Beispiel wird Mitgliedern der Verteilergruppe "Helpdesk" die Berechtigung "Vollzugriff" für das freigegebene Postfach "Helpdesk Tickets" zugewiesen.

    Add-MailboxPermission "HelpdeskTickets" -User helpdesk -AccessRights FullAccess -InheritanceType all

In diesem Beispiel wird die Berechtigung "Vollzugriff" von Jim Hance für das Postfach von Ayla Kol aufgehoben.

    Remove-MailboxPermission -Identity ayla -User "Jim Hance" -AccessRights FullAccess -Inheritance

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

  - [Add-MailboxPermission](https://technet.microsoft.com/de-de/library/bb124097\(v=exchg.150\))

  - [Remove-MailboxPermission](https://technet.microsoft.com/de-de/library/bb125153\(v=exchg.150\))

## Verwalten der Berechtigung "Senden als"

In den folgenden Beispielen wird gezeigt, wie die Berechtigung "Senden als" in Exchange Server 2013 und Exchange Online verwaltet wird. In Exchange 2013 müssen Sie die Cmdlets **Add-ADPermission** und **Remove-ADPermission** und in Exchange Online die Cmdlets **Add-RecipientPermission** und **Remove-RecipientPermission** verwenden. In beiden Fällen verwenden Sie den Parameter *Identity* zum Angeben des Namens des Postfachs, für das die Berechtigung "Senden als" hinzugefügt oder entfernt werden soll, und den Parameter *User* oder *Trustee*, um die Stellvertretung (z. B. einen Benutzer oder eine Gruppe) anzugeben, der die Berechtigung "Senden als" zugewiesen oder entzogen wird.


> [!TIP]
> Verwenden Sie das Cmdlet <STRONG>Get-Recipient</STRONG>, um die Eigenschaft <EM>Name</EM> für das Postfach und die Stellvertretung abzurufen. Verwenden Sie diese Werte, um die Berechtigung "Senden als" zuzuweisen.



## Exchange Server 2013

Bei diesem Beispiel wird die Berechtigung "Senden als" der Gruppe "Helpdesk" für das freigegebene Postfach "Helpdesk Support Team" zugewiesen.

    Add-ADPermission -Identity helpdesksupport -User helpdeskgroup -ExtendedRights "Send As"

Bei diesem Beispiel wird die Berechtigung "Senden als" der Benutzerin Pilar Pinilla für das Postfach von James Alvord entzogen.

    Remove-ADPermission -Identity "James Alvord" -User pilarp -ExtendedRights "Send As"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter:

  - [Add-ADPermission](https://technet.microsoft.com/de-de/library/bb124403\(v=exchg.150\))

  - [Remove-ADPermission](https://technet.microsoft.com/de-de/library/aa996048\(v=exchg.150\))

## Exchange Online

Bei diesem Beispiel wird die Berechtigung "Senden als" der Gruppe "Printer Support" für das freigegebene Postfach "Contoso Printer Support" zugewiesen.

    Add-RecipientPermission -Identity "Contoso Printer Support" -Trustee "Printer Support" -AccessRights SendAs

Bei diesem Beispiel wird die Berechtigung "Senden als" der Benutzerin Karen Toh für das Postfach von Yan Li entzogen.

    Remove-RecipientPermission -Identity "Yan Li" -Trustee "Karen Toh" -ExtendedRights SendAs

Ausführliche Informationen zu Syntax und Parametern finden Sie unter:

  - [Add-RecipientPermission](https://technet.microsoft.com/de-de/library/ff935839\(v=exchg.150\))

  - [Remove-RecipientPermission](https://technet.microsoft.com/de-de/library/ff945794\(v=exchg.150\))

## Verwalten der Berechtigung "Senden im Auftrag von"

Die folgenden Beispiele zeigen, wie Sie mit dem Cmdlet **Set-Mailbox** die Berechtigung "Senden im Auftrag von" verwalten.

Bei diesem Beispiel wird der Stellvertretung Holly Holt die Berechtigung "Senden im Auftrag von" für das Postfach von Sean Chai zugewiesen.

    Set-Mailbox -Identity seanc@contoso.com -GrantSendOnBehalfTo hollyh

Bei diesem Beispiel wird die Berechtigung "Senden im Auftrag von" für das freigegebene Postfach "Contoso Executives" der Gruppe "Temporary Executive Assistants" entzogen.

    Set-Mailbox "Contoso Executives" -GrantSendOnBehalfTo @{remove="tempassistants@contoso.com"}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Zuweisung von Berechtigungen zu einem Postfach bzw. einem freigegebenen Postfach zu überprüfen:

  - In der Exchange-Verwaltungskonsole:
    
    1.  Navigieren Sie zu **Empfänger** \> **Postfach** oder **Freigegeben**. Klicken Sie auf das Postfach und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    2.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachstellvertretung**.
    
    3.  Wenn Sie einem Empfänger Berechtigungen zugewiesen haben, prüfen Sie, ob der Benutzer oder die Gruppe unter der entsprechenden Berechtigung angegeben ist. Wenn Sie Berechtigungen entzogen haben, stellen Sie sicher, dass der Benutzer oder die Gruppe nicht unter der entsprechenden Berechtigung angegeben ist.

– oder –

  - Führen Sie in der Shell abhängig von der verwalteten Berechtigung einen der folgenden Befehle aus.
    
      - **Vollzugriff**
        
            Get-MailboxPermission -Identity <mailbox>
        
        Um zu prüfen, ob einer bestimmten Stellvertretung die Berechtigung "Vollzugriff" für ein Postfach zugewiesen ist, führen Sie den folgenden Befehl aus.
        
            Get-MailboxPermission -Identity <mailbox> -User <delegate>
    
      - **Senden als**
        
        Führen Sie in Exchange Server 2013 den folgenden Befehl aus.
        
            Get-ADPermission -Identity <name of mailbox> -User <delegate>
        
        Führen Sie in Exchange Online den folgenden Befehl aus.
        
            Get-RecipientPermission -Identity <mailbox> -Trustee <delegate>
    
      - **Senden im Auftrag von**
        
            Get-Mailbox -Identity <mailbox> | FL GrantSendOnBehalfTo

## Zuweisen von Berechtigungen zu einer Gruppe

Wie bereits erwähnt, können Sie die Berechtigungen "Senden als" und "Senden im Auftrag von" Verteilergruppen, dynamischen Verteilergruppen und für E-Mail aktivierten Sicherheitsgruppen zuweisen, damit Stellvertretungen Nachrichten als Gruppe oder im Auftrag der Gruppe senden können.

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" und "Dynamische Verteilergruppen" im Abschnitt "Empfängerbereitstellungsberechtigungen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

## Zuweisen von Berechtigungen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Gruppen**.

2.  Klicken Sie in der Liste der Gruppen auf die Gruppe, der Sie Berechtigungen zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite der Gruppe auf **Gruppendelegierung**.

4.  Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Seite anzuzeigen, auf der eine Liste mit allen Empfängern in der Exchange-Organisation angezeigt wird, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
    
    Um eine Berechtigung für einen Empfänger zu entfernen, wählen Sie die gewünschte Berechtigung aus und klicken dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

5.  Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Zuweisen von Berechtigungen mithilfe der Shell

In den folgenden Abschnitten wird erklärt, wie Sie mithilfe der Shell die Berechtigungen "Senden als" und "Senden im Auftrag von" für Gruppen verwalten.

## Verwalten der Berechtigung "Senden als"

In den folgenden Beispielen wird gezeigt, wie die Berechtigung "Senden als" für Gruppen in Exchange Server 2013 und Exchange Online verwaltet wird. In Exchange 2013 müssen Sie die Cmdlets **Add-ADPermission** und **Remove-ADPermission** verwenden. In Exchange Online müssen Sie die Cmdlets **Add-RecipientPermission** und **Remove-RecipientPermission** verwenden. In beiden Fällen verwenden Sie den Parameter *Identity* zum Angeben des Namens der Gruppe, für die die Berechtigung "Senden als" hinzugefügt oder entfernt werden soll, und den Parameter *User* oder *Trustee*, um die Stellvertretung (z. B. einen Benutzer oder eine Gruppe) anzugeben, der die Berechtigung "Senden als" zugewiesen oder entzogen wird.


> [!TIP]
> Verwenden Sie das Cmdlet <STRONG>Get-Recipient</STRONG>, um die Eigenschaft <EM>Name</EM> für die Gruppe und die Stellvertretung abzurufen. Verwenden Sie diese Werte, um die Berechtigung "Senden als" zuzuweisen.



## Exchange Server 2013

Bei diesem Beispiel wird die Berechtigung "Senden als" der Gruppe "Sales Admins" für die Gruppe "Contoso Sales" zugewiesen. Dadurch können Mitglieder der Gruppe "Sales Admins" Nachrichten als Gruppe "Contoso Sales Information" senden.

    Add-ADPermission -Identity "Contoso Sales Info" -User "Sales Admins" -ExtendedRights "Send As"

Bei diesem Beispiel wird die Berechtigung "Senden als" dem Benutzer Alan Shen für die Gruppe "Corporate IT Admins" entzogen.

    Remove-ADPermission -Identity "Corporate IT Admins" -User contoso\alans -ExtendedRights "Send As"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter:

  - [Add-ADPermission](https://technet.microsoft.com/de-de/library/bb124403\(v=exchg.150\))

  - [Remove-ADPermission](https://technet.microsoft.com/de-de/library/aa996048\(v=exchg.150\))

## Exchange Online

Bei diesem Beispiel wird die Berechtigung "Senden als" der Gruppe "Contoso Admins" für die dynamische Verteilergruppe "Emergency Broadcast Messages" zugewiesen.

    Add-RecipientPermission -Identity emergencybroadcast@contoso.com -Trustee "Contoso Admins" -AccessRights SendAs

Bei diesem Beispiel wird die Berechtigung "Senden als" dem Benutzer Walter Harp für die Sicherheitsgruppe "Printer Resources" entzogen.

    Remove-RecipientPermission -Identity "Printer Resources" -Trustee walterh@contoso.com ExtendedRights SendAs

Ausführliche Informationen zu Syntax und Parametern finden Sie unter:

  - [Add-RecipientPermission](https://technet.microsoft.com/de-de/library/ff935839\(v=exchg.150\))

  - [Remove-RecipientPermission](https://technet.microsoft.com/de-de/library/ff945794\(v=exchg.150\))

## Verwalten der Berechtigung "Senden im Auftrag von"

Die folgenden Beispiele zeigen, wie Sie mit den Cmdlets **Set-DistributionGroup** und **Set-DynamicDistributionGroup** die Berechtigung "Senden im Auftrag von " für Gruppen verwalten.

Bei diesem Beispiel wird der Stellvertretung Sara Davis die Berechtigung "Senden im Auftrag von" für die Verteilergruppe "Printer Support" zugewiesen.

    Set-DistributionGroup -Identity printersupport@contoso.com -GrantSendOnBehalfTo sarad

Bei diesem Beispiel wird der Stellvertretung "Administrator" die Berechtigung "Senden im Auftrag von" für die dynamische Verteilergruppe "All Employees" zugewiesen.

    Set-DynamicDistributionGroup -Identity "All Employees" -GrantSendOnBehalfTo administrator

Bei diesem Beispiel wird die Berechtigung "Senden im Auftrag von" für die dynamische Verteilergruppe "All Employees" dem Administrator entzogen.

    Set-DynamicDistributionGroup "All Employees" -GrantSendOnBehalfTo @{remove="administrator"}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter:

  - [Set-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124955\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb123796\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Zuweisung von Berechtigungen zu einer Gruppe zu überprüfen:

  - In der Exchange-Verwaltungskonsole:
    
    1.  Navigieren Sie zu **Empfänger** \> **Gruppen**, klicken Sie auf die Gruppe und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    2.  Klicken Sie auf der Eigenschaftenseite der Gruppe auf **Gruppendelegierung**.
    
    3.  Wenn Sie einem Empfänger Berechtigungen zugewiesen haben, prüfen Sie, ob der Benutzer oder die Gruppe unter der entsprechenden Berechtigung angegeben ist. Wenn Sie Berechtigungen entzogen haben, stellen Sie sicher, dass der Benutzer oder die Gruppe nicht unter der entsprechenden Berechtigung angegeben ist.

– oder –

  - Führen Sie in der Shell abhängig von der verwalteten Berechtigung einen der folgenden Befehle aus.
    
      - **Senden als**
        
        Führen Sie in Exchange Server 2013 den folgenden Befehl aus.
        
            Get-ADPermission -Identity <name of group> -User <delegate>
        
        Führen Sie in Exchange Online den folgenden Befehl aus.
        
            Get-RecipientPermission -Identity <group> -Trustee <delegate>
    
      - **Senden im Auftrag von**
        
            Get-DistributionGroup -Identity <group> | FL GrantSendOnBehalfTo
        
        – oder –
        
            Get-DynamicDistributionGroup -Identity <group> | FL GrantSendOnBehalfTo

