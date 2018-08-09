---
title: 'Versch. d. Exchange 2010-Systempostf. zu Exchange 2013: Exchange 2013-Hilfe'
TOCTitle: Verschieben des Exchange 2010-Systempostfachs nach Exchange 2013
ms:assetid: a3b03c4e-0bc7-41a2-885c-e9cac37566c8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn249849(v=EXCHG.150)
ms:contentKeyID: 54915045
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verschieben des Exchange 2010-Systempostfachs nach Exchange 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

In Exchange 2010 ist das Microsoft Exchange-Systempostfach ein Vermittlungspostfach, das zum Speichern von organisationsweiten Daten verwendet wird, wie Administrator-Überwachungsprotokollen, eDiscovery-Suchmetadaten und Unified Messaging-Daten wie Menüs, Wähleinstellungen und benutzerdefinierten Begrüßungen. Das Microsoft Exchange-Systempostfach hat den Namen **SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}**; der Anzeigename ist **Microsoft Exchange**.

Wenn Sie Ihre vorhandene Exchange 2010-Organisation auf Exchange 2013 aktualisieren, müssen Sie das Microsoft Exchange-Systempostfach in eine Postfachdatenbank auf einem Exchange 2013-Postfachserver verschieben. Sie sollten dieses Postfach verschieben, nachdem Sie Exchange 2013 installiert und überprüft haben. Wenn Sie dieses Systempostfach nicht nach Exchange 2013 verschieben, treten folgende Probleme auf, weil Exchange 2010 und Exchange 2013 gleichzeitig in Ihrer Exchange-Organisation vorhanden sind:

  - Exchange 2013-Aufgaben werden nicht im Administrator-Überwachungsprotokoll gespeichert. Wenn Sie das Cmdlet **Search-AdminAuditLog** ausführen oder versuchen, das Administrator-Überwachungsprotokoll in die Exchange-Verwaltungskonsole zu exportieren, wird ein Fehler angezeigt, der besagt, dass Sie keine Administrator-Überwachungsprotokollsuche erstellen können, da das Systempostfach "SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}" sich auf einem Server befindet, auf dem nicht Exchange 2013 ausgeführt wird. Außerdem wird bei jeder Befehlsausführung ein Microsoft Exchange-Fehler mit der Ereignis-ID 5000 im Windows-Anwendungsprotokoll vermerkt.

  - Sie können keine eDiscovery-Suchen mithilfe der Verwaltungskonsole oder der Shell in Exchange 2013 ausführen. Postfachsuchen können erstellt und in die Warteschlange gestellt, aber nicht gestartet werden. Im MsExchange Management-Protokoll wird ein Fehler mit der Ereignis-ID 6 protokolliert, der besagt, dass das Cmdlet **Start-MailboxSearch** fehlgeschlagen ist. Sie können jedoch Postfächer mithilfe der Shell und der Exchange-Systemsteuerung (ECP) in Exchange 2010 durchsuchen.

Sie müssen das Microsoft Exchange-Systempostfach auch nach Exchange 2013 verschieben, wenn Sie ein Upgrade von Exchange 2010 Unified Messaging auf Exchange 2013 durchführen.

Weitere Informationen zum Upgrade auf Exchange 2013 finden Sie in den folgenden Themen:

  - [Aktualisieren von Exchange 2010 auf Exchange 2013](upgrade-from-exchange-2010-to-exchange-2013-exchange-2013-help.md)

  - [Aktualisierung von Exchange 2010 Unified Messaging auf Exchange 2013 Unified Messaging](upgrade-exchange-2010-um-to-exchange-2013-um-exchange-2013-help.md)

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 20 Minuten. Die tatsächliche Zeit hängt von der Größe des Systempostfachs ab.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für Postfachverschiebung und -migration" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Führen Sie den folgenden Befehl in Exchange 2013 aus, um die Identität und Version des Exchange-Servers und der Postfachdatenbanken abzufragen, welche die Systempostfächer in Ihrer Organisation enthalten.
    
        Get-Mailbox -Arbitration | FL Name,DisplayName,ServerName,Database,AdminDisplayVersion
    
    Die Eigenschaft **AdminDisplayVersion** gibt die Exchange-Version an, die auf dem Server ausgeführt wird. Der Wert `Version 14.x` gibt Exchange 2010 an; der Wert `Version 15.x` gibt Exchange 2013 an.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungskonsole, um das Systempostfach zu verschieben

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Migration**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und anschließend auf **In andere Datenbank verschieben**.

3.  Klicken Sie auf der Seite **Neues lokales Postfach verschieben** auf **Zu verschiebende Benutzer auswählen**. Klicken Sie anschließend auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

4.  Fügen Sie das Postfach, das die folgenden Eigenschaften erfüllt, auf der Seite **Postfach auswählen** hinzu:
    
      - Der Anzeigename lautet **Microsoft Exchange**.
    
      - Der Alias der E-Mail-Adresse des Postfachs lautet **SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}**.

5.  Klicken Sie auf **OK** und dann auf **Weiter**.

6.  Geben Sie auf der Seite **Konfiguration verschieben** den Namen des Migrationsbatches ein, und klicken Sie auf **Durchsuchen** neben dem Feld **Zieldatenbank**.

7.  Fügen Sie die Postfachdatenbank auf der Seite **Postfachdatenbank auswählen** dem Systempostfach hinzu. Stellen Sie sicher, dass die Version der ausgewählten Postfachdatenbank Version 15. x entspricht. Dies bedeutet, dass sich die Datenbank auf einem Exchange 2013-Server befindet.

8.  Klicken Sie auf **OK** und dann auf **Weiter**.

9.  Wählen Sie auf der Seite **Batch starten** die Optionen für den automatischen Start und das Abschließen der Migrationsanforderung aus. Klicken Sie anschließend auf **Neu**.

## Verwenden der Shell, um das Systempostfach zu verschieben

Führen Sie zuerst den folgenden Befehl in Exchange 2013 aus, um die Namen und Versionen aller Postfachdatenbanken in Ihrer Organisation abzurufen.

    Get-MailboxDatabase -IncludePreExchange2013 | FL Name,Server,AdminDisplayVersion

Nachdem Sie die Namen der Postfachdatenbanken in Ihrer Organisation bestimmt haben, führen Sie den folgenden Befehl in Exchange 2013 aus, um das Microsoft Exchange-Systempostfach in eine Postfachdatenbank auf einem Exchange 2013-Server zu verschieben.

    Get-Mailbox -Arbitration -Identity "SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}" | New-MoveRequest -TargetDatabase <name of Exchange 2013 database>

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um sicherzustellen, dass Sie das Microsoft Exchange-Systempostfach erfolgreich in eine Postfachdatenbank auf einem Exchange 2013-Server verschoben haben, führen Sie den folgenden Befehl in der Shell aus.

    Get-Mailbox -Arbitration -Identity "SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}" | FL Database,ServerName,AdminDisplayVersion

Entspricht der Wert der **AdminDisplayVersion**-Eigenschaft **Version 15.x (Build xxx.x)**, ist sichergestellt, dass sich das Systempostfach in einer Postfachdatenbank auf einem Exchange 2013-Server befindet.

Nachdem Sie das Microsoft Exchange-Systempostfach nach Exchange 2013 verschoben haben, können Sie die folgenden Verwaltungsaufgaben erfolgreich ausführen:

  - Führen Sie das Cmdlet **Search-AdminAuditLog** aus.

  - Exportieren Sie das Administrator-Überwachungsprotokoll in die Exchange-Verwaltungskonsole (EAC).

  - Erstellen und starten Sie die eDiscovery-Suche mithilfe der Verwaltungskonsole oder der Shell in Exchange 2013.

