---
title: 'Konfigurieren von Nachrichtenübermittlungseinschränkungen für ein Postfach: Exchange 2013 Help'
TOCTitle: Konfigurieren von Nachrichtenübermittlungseinschränkungen für ein Postfach
ms:assetid: c4b8b89f-3dbe-4cb8-8839-9a4e8067e00c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb397214(v=EXCHG.150)
ms:contentKeyID: 50554923
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Nachrichtenübermittlungseinschränkungen für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-29_

Sie können Einschränkungen mithilfe der Exchange-Verwaltungskonsole oder Shell dahingehend einrichten, ob Nachrichten einzelnen Empfängern zugestellt werden. Einschränkungen für die Nachrichtenzustellung eignen sich zum Bestimmen, wer an Benutzer in Ihrer Organisation Nachrichten senden darf. Sie können beispielsweise ein Postfach so konfigurieren, dass von bestimmten Benutzern gesendete Nachrichten akzeptiert oder abgelehnt oder nur Nachrichten von Benutzern in Ihrer Exchange-Organisation akzeptiert werden.

Die in diesem Thema behandelten Nachrichtenübermittlungseinschränkungen gelten für alle Empfängertypen. Weitere Informationen zu den verschiedenen Empfängertypen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit Empfängern finden Sie in den folgenden Themen:

  - [Verwalten von Benutzerpostfächern](manage-user-mailboxes-exchange-2013-help.md)

  - [Erstellen und Verwalten von Verteilergruppen](create-and-manage-distribution-groups-exchange-2013-help.md)

  - [Verwalten dynamischer Verteilergruppen](manage-dynamic-distribution-groups-exchange-2013-help.md)

  - [Verwalten von E-Mail-Benutzern](manage-mail-users-exchange-2013-help.md)

  - [Verwalten von E-Mail-Kontakten](manage-mail-contacts-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole zum Konfigurieren von Einschränkungen für die Nachrichtenzustellung

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, für das Sie Einschränkungen für die Nachrichtenzustellung konfigurieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Klicken Sie unter **Einschränkungen für die Nachrichtenzustellung** auf **Details anzeigen**, um die folgenden Zustellungseinschränkungen anzuzeigen und zu ändern:
    
      - **Nachrichten annehmen von**   Verwenden Sie diesen Abschnitt, um anzugeben, wer Nachrichten an diesen Benutzer senden kann.
        
          - **Alle Absender**   Diese Option legt fest, dass der Empfänger Nachrichten von allen Absendern akzeptieren kann. Dies schließt sowohl Absender innerhalb der Exchange-Organisation als auch externe Absender ein. Hierbei handelt es sich um die Standardeinstellung. Diese Option schließt externe Benutzer nur ein, wenn Sie das Kontrollkästchen **Authentifizierung aller Absender anfordern** deaktivieren. Wenn Sie dieses Kontrollkästchen aktivieren, werden Nachrichten von externen Benutzern zurückgewiesen.
        
          - **Nur Absender aus der folgenden Liste**   Diese Option legt fest, dass der Benutzer nur Nachrichten einer bestimmten Gruppe von Absendern in der Exchange-Organisation empfangen kann. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Liste aller Empfänger in der Exchange-Organisation anzuzeigen. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
        
          - **Authentifizierung aller Absender anfordern**   Diese Option verhindert, dass anonyme Benutzer Nachrichten an den Benutzer senden können. Dazu gehören externe Benutzer, die sich außerhalb der Exchange-Organisation befinden.
    
      - **Nachrichten ablehnen von**   Verwenden Sie diesen Abschnitt, um Benutzer daran zu hindern, Nachrichten an diesen Benutzer zu senden.
        
          - **Keinem Absender**   Diese Option bestimmt, dass das Postfach keine Nachrichten von Absendern in der Exchange-Organisation zurückweist. Hierbei handelt es sich um die Standardeinstellung.
        
          - **Absendern aus der folgenden Liste**   Diese Option legt fest, dass das Postfach Nachrichten von einer bestimmten Gruppe von Absendern in der Exchange-Organisation zurückweist. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Liste aller Empfänger in der Exchange-Organisation anzuzeigen. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.

5.  Klicken Sie auf **OK**, um die Seite **Einschränkungen für die Nachrichtenzustellung** zu schließen, und dann auf **Speichern**, um die Änderungen zu speichern.

## Verwenden der Shell zum Konfigurieren von Nachrichtenübermittlungseinschränkungen

In den folgenden Beispielen wird gezeigt, wie die Shell zum Konfigurieren von Einschränkungen für die Nachrichtenzustellung für ein Postfach verwendet wird. Verwenden Sie für andere Empfängertypen das entsprechende **Set-**Cmdlet mit den gleichen Parametern.

In diesem Beispiel wird das Postfach von Robin Wood so konfiguriert, dass nur Nachrichten der Benutzer Lori Penor, Jens Phillips und von Mitgliedern der Verteilergruppe "Legal Team 1" akzeptiert werden.

    Set-Mailbox -Identity "Robin Wood" -AcceptMessagesOnlyFrom "Lori Penor","Jeff Phillips" -AcceptMessagesOnlyFromDLMembers "Legal Team 1"


> [!NOTE]
> Wenn Sie ein Postfach so konfigurieren möchten, dass nur Nachrichten einzelner Absender angenommen werden, müssen Sie den Parameter <EM>AcceptMessagesOnlyFrom</EM> verwenden. Wenn Sie ein Postfach so konfigurieren möchten, dass nur Nachrichten von Absendern angenommen werden, die Mitglied einer bestimmten Verteilergruppe sind, verwenden Sie den Parameter <EM>AcceptMessagesOnlyFromDLMembers</EM>.



In diesem Beispiel wird der Benutzer David Pelton der Liste der Benutzer hinzugefügt, deren Nachrichten vom Postfach von Robin Wood akzeptiert werden.

    Set-Mailbox -Identity "Robin Wood" -AcceptMessagesOnlyFrom @{add="David Pelton"}

In diesem Beispiel wird das Postfach von Robin Wood so konfiguriert, dass nur authentifizierte Absender zugelassen werden. Dies bedeutet, dass das Postfach nur Nachrichten akzeptiert, die von anderen Benutzern in Ihrer Exchange-Organisation gesendet wurden.

    Set-Mailbox -Identity "Robin Wood" -RequireSenderAuthenticationEnabled $true

In diesem Beispiel wird das Postfach von Robin Wood so konfiguriert, dass Nachrichten der Benutzer Joe Healy, Terry Adams und von Mitgliedern der Verteilergruppe "Legal Team 2" zurückgewiesen werden.

    Set-Mailbox -Identity "Robin Wood" -RejectMessagesFrom "Joe Healy","Terry Adams" -RejectMessagesFromDLMembers "Legal Team 2"

In diesem Beispiel wird das Postfach von Robin Wood so konfiguriert, dass auch Nachrichten von Mitgliedern der Gruppe "Legal Team 3" zurückgewiesen werden.

    Set-Mailbox -Identity "Robin Wood" -RejectMessagesFromDLMembers @{add="Legal Team 3"}


> [!NOTE]
> Wenn Sie ein Postfach so konfigurieren möchten, dass nur Nachrichten einzelner Absender zurückgewiesen werden, müssen Sie den Parameter <EM>RejectMessagesFrom</EM> verwenden. Wenn Sie ein Postfach so konfigurieren möchten, dass nur Nachrichten von Absendern zurückgewiesen werden, die Mitglied einer bestimmten Verteilergruppe sind, verwenden Sie den Parameter <EM>RejectMessagesFromDLMembers</EM>.



In den folgenden Themen finden Sie detaillierte Informationen zu Syntax und Parametern im Zusammenhang mit der Konfiguration von Zustellungseinschränkungen für verschiedene Empfängertypen:

  - [Set-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124955\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb123796\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

  - [Set-MailContact](https://technet.microsoft.com/de-de/library/aa995950\(v=exchg.150\))

  - [Set-MailUser](https://technet.microsoft.com/de-de/library/aa995971\(v=exchg.150\))

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Konfiguration von Einschränkungen für die Nachrichtenzustellung für ein Benutzerpostfach zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Einschränkungen für die Nachrichtenzustellung Sie überprüfen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Klicken Sie unter **Einschränkungen für die Nachrichtenzustellung** auf **Details anzeigen**, um die Einschränkungen für die Nachrichtenzustellung für das Postfach zu überprüfen.

– oder –

Führen Sie folgenden Befehl in der Shell aus.

    Get-Mailbox <identity> | fl AcceptMessagesOnlyFrom,AcceptMessagesOnlyFromDLMembers,RejectMessagesFrom,RejectMessagesFromDLMembers,RequireSenderAuthenticationEnabled

