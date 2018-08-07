---
title: 'Hinzufügen o. Entfernen v. E-Mail-Adressen für Postfach: Exchange 2013-Hilfe'
TOCTitle: Hinzufügen oder Entfernen von E-Mail-Adressen für ein Postfach
ms:assetid: 93e2d9a4-7558-4509-8641-8381a7eb674f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123794(v=EXCHG.150)
ms:contentKeyID: 50554860
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinzufügen oder Entfernen von E-Mail-Adressen für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Sie können Sie können mehr als eine E-Mail-Adresse für dasselbe Postfach konfigurieren. Diese zusätzlichen Adressen werden als *Proxyadressen* bezeichnet. Eine Proxyadresse ermöglicht einem Benutzer das Empfangen von E-Mails, die an eine andere E-Mail-Adresse gesendet wurde. E-Mail-Nachrichten, die an die Proxyadresse des Betriebssystems gesendet wurden, werden der primären E-Mail-Adresse zugestellt, die auch als *primäre SMTP-Adresse* oder *Standardantwortadresse* bezeichnet wird.


> [!IMPORTANT]
> Wenn Sie Office 365 for Business verwenden, sollten Sie E-Mail-Adressen für Postfächer von Benutzern in der <A href="https://go.microsoft.com/fwlink/p/?linkid=8347775">Office 365-Verwaltungskonsole hinzufügen oder entfernen: Hinzufügen weiterer E-Mail-Aliase zu einem Benutzer in Office 365</A>



Zusätzliche Verwaltungsaufgaben im Zusammenhang mit dem Verwalten von Empfängern finden Sie in der Tabelle mit der Dokumentation zu Empfängern in [Empfänger](recipients-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

Anhand der Verfahren in diesem Thema wird das Hinzufügen und Entfernen von E-Mail-Adressen für ein Benutzerpostfach erläutert. Mithilfe ähnlicher Verfahren können Sie E-Mail-Adressen für andere Empfängertypen hinzufügen oder entfernen.

## Was möchten Sie machen?

## Hinzufügen einer E-Mail-Adresse zu einem Benutzerpostfach

## Hinzufügen einer E-Mail-Adresse mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dem Sie eine E-Mail-Adresse hinzufügen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **E-Mail-Adresse**.
    

    > [!NOTE]
    > Auf der Seite <STRONG>E-Mail-Adresse</STRONG> wird die primäre SMTP-Adresse fett gedruckt in der Adressenliste und dem groß geschriebenen Wert <STRONG>SMTP</STRONG> in der Spalte <STRONG>Typ</STRONG> angezeigt.



4.  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und anschließend auf **SMTP**, um diesem Postfach eine SMTP-Adresse hinzuzufügen.
    

    > [!NOTE]
    > SMTP ist der Standard-E-Mail-Adresstyp. Sie können einem Postfach auch Exchange Unified Messaging (EUM)- oder benutzerdefinierte Adressen hinzufügen. Weitere Informationen finden Sie unter "Ändern der Eigenschaften von Benutzerpostfächern" im Thema <A href="manage-user-mailboxes-exchange-2013-help.md">Verwalten von Benutzerpostfächern</A>.



5.  Geben Sie die neue SMTP-Adresse in das Feld **E-Mail-Adresse** ein, und klicken Sie dann auf **OK**.
    
    Die neue Adresse wird in der Liste der E-Mail-Adressen für das ausgewählte Postfach angezeigt.

6.  Klicken Sie zum Speichern der Änderung auf **Speichern**.

## Hinzufügen einer E-Mail-Adresse mithilfe der Shell

Die einem Postfach zugeordneten E-Mail-Adressen sind in der Eigenschaft *EmailAddresses* des Postfachs enthalten. Da mehrere E-Mail-Adressen enthalten sein können, ist die Eigenschaft *EmailAddresses* eine sog. *mehrwertige* Eigenschaft. Die folgenden Beispiele veranschaulichen verschiedene Möglichkeiten, eine mehrwertige Eigenschaft zu ändern.

Dieses Beispiel zeigt, wie eine SMTP-Adresse dem Postfach von Dan Jump hinzugefügt wird.

    Set-Mailbox "Dan Jump" -EmailAddresses @{add="dan.jump@northamerica.contoso.com"}

Dieses Beispiel zeigt, wie mehrere SMTP-Adressen einem Postfach hinzugefügt werden.

    Set-Mailbox "Dan Jump" -EmailAddresses @{add="dan.jump@northamerica.contoso.com","danj@tailspintoys.com"}

Weitere Informationen zu dieser Methode zum Hinzufügen oder Entfernen von Werten bei mehrwertigen Eigenschaften finden Sie unter [Ändern von mehrwertigen Eigenschaften](modifying-multivalued-properties-exchange-2013-help.md).

Dieses Beispiel zeigt eine andere Möglichkeit zum Hinzufügen von E-Mail-Adresse zu einem Postfach, indem alle dem Postfach zugeordneten Adressen angegeben werden. In diesem Beispiel ist "danj@tailspintoys.com" die neue E-Mail-Adresse, die Sie hinzufügen möchten. Die anderen beiden E-Mail-Adressen sind vorhandene Adressen. Die Adresse mit dem Kennzeichner `SMTP` mit Unterscheidung von Groß-/Kleinschreibung ist die primäre SMTP-Adresse. Bei Verwenden dieser Befehlssyntax müssen Sie alle E-Mail-Adressen für das Postfach einschließen. Falls nicht, überschreiben die im Befehl angegebenen Adressen die vorhandenen Adressen.

    Set-Mailbox "Dan Jump" -EmailAddresses SMTP:dan.jump@contoso.com,dan.jump@northamerica.contoso.com,danj@tailspintoys.com

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um das erfolgreiche Hinzufügen einer E-Mail-Adresse zu einem Postfach zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Klicken Sie auf das Postfach und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

  - Klicken Sie auf der Eigenschaftenseite des Postfachs auf **E-Mail-Adresse**.

  - Prüfen Sie in der Liste der E-Mail-Adressen für das Postfach, ob die neue E-Mail-Adresse enthalten ist.

– oder –

  - Führen Sie folgenden Befehl in der Shell aus.
    
        Get-Mailbox <identity> | fl EmailAddresses

  - Stellen Sie sicher, dass die neue E-Mail-Adresse in den Ergebnissen enthalten ist.

## Entfernen einer E-Mail-Adresse aus einem Benutzerpostfach

## Entfernen einer E-Mail-Adresse mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, aus dem Sie eine E-Mail-Adresse entfernen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **E-Mail-Adresse**.

4.  Wählen Sie in der Liste der E-Mail-Adressen die Adresse aus, die Sie entfernen möchten, und klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

5.  Klicken Sie zum Speichern der Änderung auf **Speichern**.

## Entfernen einer E-Mail-Adresse mithilfe der Shell

Dieses Beispiel zeigt, wie eine E-Mail-Adresse aus dem Postfach von Janet Schorr entfernt wird.

    Set-Mailbox "Janet Schorr" -EmailAddresses @{remove="janets@corp.contoso.com"}

Dieses Beispiel zeigt, wie mehrere Adressen aus einem Postfach entfernt werden.

    Set-Mailbox "Janet Schorr" -EmailAddresses @{remove="janet.schorr@corp.contoso.com","janets@tailspintoys.com"}

Weitere Informationen zu dieser Methode zum Hinzufügen oder Entfernen von Werten bei mehrwertigen Eigenschaften finden Sie unter [Ändern von mehrwertigen Eigenschaften](modifying-multivalued-properties-exchange-2013-help.md).

Sie können eine E-Mail-Adresse auch entfernen, indem Sie sie im Befehl zum Festlegen von E-Mail-Adressen für ein Postfach weglassen. Angenommen, das Postfach von Janet Schorr hat drei E-Mail-Adressen: janets@contoso.com (die primäre SMTP-Adresse), janets@corp.contoso.com und janets@tailspintoys.com. Um die Adresse janets@corp.contoso.com zu entfernen, müssen Sie den folgenden Befehl ausführen.

    Set-Mailbox "Janet Schorr" -EmailAddresses SMTP:janets@contoso.com,janets@tailspintoys.com

Da janets@corp.contoso.com im vorherigen Befehl weggelassen wurde, wird die Adresse aus dem Postfach entfernt.

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um das erfolgreiche Entfernen einer E-Mail-Adresse aus einem Postfach zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Klicken Sie auf das Postfach und dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

  - Klicken Sie auf der Eigenschaftenseite des Postfachs auf **E-Mail-Adresse**.

  - Prüfen Sie in der Liste der E-Mail-Adressen für das Postfach, ob die E-Mail-Adresse fehlt.

– oder –

  - Führen Sie folgenden Befehl in der Shell aus.
    
        Get-Mailbox <identity> | fl EmailAddresses

  - Stellen Sie sicher, dass die E-Mail-Adresse nicht in den Ergebnissen enthalten ist.

## Hinzufügen von E-Mail-Adressen zu mehreren Postfächern mithilfe der Shell

Mithilfe der Shell und einer CSV-Datei (mit Trennzeichen getrennte Werte) können Sie mehreren Postfächern gleichzeitig eine neue E-Mail-Adresse hinzufügen.

In diesem Beispiel werden Daten aus "C:\\Users\\Administrator\\Desktop\\AddEmailAddress.csv" importiert, die das folgende Format haben.

    Mailbox,NewEmailAddress
    Dan Jump,danj@northamerica.contoso.com
    David Pelton,davidp@northamerica.contoso.com
    Kim Akers,kima@northamerica.contoso.com
    Janet Schorr,janets@northamerica.contoso.com
    Jeffrey Zeng,jeffreyz@northamerica.contoso.com
    Spencer Low,spencerl@northamerica.contoso.com
    Toni Poe,tonip@northamerica.contoso.com
    ...

Führen Sie den folgenden Befehl aus, um mithilfe der Daten in der CSV-Datei die E-Mail-Adressen jedem in der CSV-Datei angegebenen Postfach hinzuzufügen.

    Import-CSV "C:\Users\Administrator\Desktop\AddEmailAddress.csv" | ForEach {Set-Mailbox $_.Mailbox -EmailAddresses @{add=$_.NewEmailAddress}}


> [!NOTE]
> Die Spaltennamen in der ersten Zeile dieser CSV-Datei (<CODE>Mailbox,NewEmailAddress</CODE>) können beliebig gewählt werden. Welche Namen auch immer Sie als Spaltennamen verwenden, stellen Sie sicher, dass Sie die gleichen Spaltennamen im Shell-Befehl verwenden.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um das erfolgreiche Hinzufügen einer E-Mail-Adresse zu mehreren Postfächern zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Klicken Sie auf das Postfach, dem Sie die Adresse hinzugefügt haben, und anschließend auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

  - Klicken Sie auf der Eigenschaftenseite des Postfachs auf **E-Mail-Adresse**.

  - Prüfen Sie in der Liste der E-Mail-Adressen für das Postfach, ob die neue E-Mail-Adresse enthalten ist.

– oder –

  - Führen Sie den folgenden Befehl in der Shell mit der CSV-Datei aus, die Sie auch zum Hinzufügen der neuen E-Mail-Adresse verwendet haben.
    
        Import-CSV "C:\Users\Administrator\Desktop\AddEmailAddress.csv" | ForEach {Get-Mailbox $_.Mailbox | fl Name,EmailAddresses}

  - Stellen Sie sicher, dass die neue E-Mail-Adresse in den Ergebnissen für jedes Postfach enthalten ist.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..


