---
title: 'Erstellen von Benutzerpostfächern: Exchange 2013 Help'
TOCTitle: Erstellen von Benutzerpostfächern
ms:assetid: 51a8b4c6-a53e-41c5-8bb1-ea4c0eaa0174
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ991919(v=EXCHG.150)
ms:contentKeyID: 52062856
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen von Benutzerpostfächern

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-04-12_

Postfächer sind der häufigste Empfängertyp, der von Information-Workern in einer Exchange-Organisation verwendet wird. Jedem Postfach ist ein Active Directory-Benutzerkonto zugeordnet. Der Benutzer kann das Postfach zum Senden und Empfangen von Nachrichten sowie zum Speichern von Nachrichten, Terminen, Aufgaben, Notizen und Dokumenten verwenden. Erstellen von Benutzerpostfächern mithilfe der Exchange-Verwaltungskonsole oder der Shell.

Sie können außerdem Benutzerpostfächer für vorhandene Benutzer erstellen, die über ein Active Directory-Benutzerkonto verfügen, aber kein entsprechendes Postfach besitzen. Dieser Vorgang wird als *Postfachaktivierung* vorhandener Benutzer bezeichnet.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe für jedes Benutzerpostfach: 2 bis 5 Minuten.

  - Bei der Erstellung eines neuen Benutzerpostfachs dürfen im Alias oder Benutzeranmeldenamen kein Apostroph (') oder Anführungszeichen (") verwendet werden, da diese Zeichen nicht unterstützt werden. Auch wenn Sie bei der Erstellung eines neuen Postfachs mit nicht unterstützten Zeichen möglicherweise keine Fehlermeldung erhalten, können diese Zeichen später Probleme verursachen. So können beispielsweise Benutzer, denen Zugriffsrechte für ein Postfach zugewiesen wurden, das mit nicht unterstützten Zeichen erstellt wurde, auf Probleme oder unerwartetes Verhalten stoßen.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines Benutzerpostfachs

## Erstellen eines Benutzerpostfachs mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie auf **Neu** \> **Benutzerpostfach**.

3.  Geben Sie auf der Seite **Neues Benutzerpostfach** im Feld **Alias** den Alias des Benutzers ein, der den E-Mail-Alias für den Benutzer angibt. Der Benutzeralias ist der Teil links vom @-Symbol in der E-Mail-Adresse. Er muss innerhalb der Gesamtstruktur eindeutig sein.
    

    > [!NOTE]
    > Wenn Sie dieses Feld leer lassen, wird der Wert des Benutzernamens im <STRONG>Benutzeranmeldenamen</STRONG> als E-Mail-Alias verwendet.



4.  
    
    Wählen Sie eine der folgenden Optionen aus:
    
      - **Vorhandener Benutzer**   Wählen Sie diese Option aus, um für einen vorhandenen Benutzer E-Mail zu aktivieren und ein Postfach zu erstellen.
        
        Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Benutzer auswählen - Vollständige Gesamtstruktur** zu öffnen. Dieses Dialogfeld enthält eine Liste mit Active Directory-Benutzerkonten in der Gesamtstruktur, die nicht E-Mail-aktiviert sind bzw. nicht über Exchange-Postfächer verfügen. Wählen Sie das Benutzerkonto aus, das für E-Mail aktiviert werden soll, und klicken Sie auf **OK**. Wenn Sie diese Option auswählen, brauchen Sie keine Informationen zum Benutzerkonto anzugeben, da diese Informationen bereits in Active Directory vorhanden sind.
    
      - **Neuer Benutzer**   Wählen Sie diese Option aus, um ein neues Benutzerkonto in Active Directory und ein Postfach für diesen Benutzer zu erstellen. Wenn Sie diese Option auswählen, müssen Sie die erforderlichen Informationen zum Benutzerkonto angeben.
    

    > [!NOTE]
    > Das Active Directory-Konto, das Benutzerpostfächern zugeordnet ist, muss sich in derselben Gesamtstruktur wie der Exchange-Server befinden. Sie müssen ein verknüpftes Postfach erstellen, um ein Postfach für ein Benutzerkonto zu erstellen, das sich in einer vertrauenswürdigen Gesamtstruktur befindet. Weitere Informationen finden Sie unter <A href="manage-linked-mailboxes-exchange-2013-help.md">Verwalten verknüpfter Postfächer</A>.



5.  
    
    Wenn Sie in Schritt 4 **Neuer Benutzer** ausgewählt haben, füllen Sie die folgenden Felder auf der Seite **Neues Benutzerpostfach** aus. Fahren Sie andernfalls mit Schritt 7 fort.
    
      - **Vorname** Verwenden Sie dieses Feld, um den Vornamen des Benutzers einzugeben.
    
      - **Initialen** Verwenden Sie dieses Textfeld, um die Initialen des Benutzers einzugeben.
    
      - **Nachname** Verwenden Sie dieses Feld, um den Nachnamen des Benutzers einzugeben.
    
      - **\* Anzeigename**   Geben Sie in diesem Feld einen Anzeigenamen für den Benutzer ein. Dies ist der Name, der in der Exchange-Verwaltungskonsole und im freigegebenen Adressbuch in der Postfachliste angegeben wird. Dieses Feld wird automatisch mit den Namen aufgefüllt, die Sie in den Feldern **Vorname**, **Initialen** und **Nachname** eingegeben haben. Wenn Sie diese Felder nicht verwendet haben, müssen Sie in diesem Feld einen Namen eingeben, da die Eingabe erforderlich ist. Der Name darf nicht länger als 64 Zeichen sein.
    
      - **\* Name**   Geben Sie in diesem Feld einen Namen für den Benutzer ein. Das ist der Name, der in Active Directory aufgeführt wird. Dieses Feld wird ebenfalls mit den Namen aufgefüllt, die Sie in den Feldern **Vorname**, **Initialen** und **Nachname** eingegeben haben. Wenn Sie diese Felder nicht verwendet haben, müssen Sie in diesem Feld einen Namen eingeben, da die Eingabe erforderlich ist. Dieser Name darf ebenfalls nicht länger als 64 Zeichen sein.
    
      - **Organisationseinheit**   Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container "Benutzer" in der Active Directory-Domäne festgelegt, in der sich der Computer befindet, auf dem die Exchange-Verwaltungskonsole ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container "Benutzer" ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten der Gesamtstruktur angezeigt, die sich in einem bestimmten Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie auf **OK**.
    
      - **\* Benutzeranmeldename**   Verwenden Sie dieses Feld, um den Namen einzugeben, den der Benutzer zur Anmeldung beim Postfach und zur Anmeldung bei der Domäne verwendet. Der Anmeldename des Benutzers setzt sich aus einem Benutzernamen auf der linken Seite des at-Zeichens (@) und einem Suffix auf der rechten Seite zusammen. Normalerweise ist das Suffix der Name der Domäne, in der sich das Benutzerkonto befindet. Beachten Sie, dass im Benutzeranmeldenamen ein Apostroph (') oder ein Anführungszeichen (") nicht unterstützt werden.
        

        > [!NOTE]
        > Wenn sich der Wert für den Benutzernamen von dem im Feld <STRONG>Alias</STRONG> verwendeten Wert unterscheidet, dann unterscheiden sich auch die E-Mail-Adresse und der Anmeldename des Benutzers.

    
      - **\* Neues Kennwort**   Verwenden Sie dieses Feld, um das Kennwort einzugeben, das der Benutzer für die Anmeldung beim Postfach verwenden muss.
        

        > [!NOTE]
        > Stellen Sie sicher, dass das angegebene Kennwort den Anforderungen hinsichtlich Länge, Komplexität und Verlauf der Domäne entspricht, in der Sie das Benutzerkonto erstellen.

    
      - **\* Kennwort bestätigen**   Verwenden Sie dieses Feld zum Bestätigen des Kennworts, das Sie im Feld **Kennwort** eingegeben haben.
    
      - **Bei nächster Anmeldung Kennwortänderung anfordern**   Aktivieren Sie dieses Kontrollkästchen, wenn der Benutzer das Kennwort bei der ersten Anmeldung beim Postfach zurücksetzen soll.
        
        Wenn Sie dieses Kontrollkästchen aktivieren, wird der neue Benutzer bei der ersten Anmeldung über ein Dialogfeld aufgefordert, das Kennwort zu ändern. Der Benutzer kann erst dann Aufgaben ausführen, wenn das Kennwort erfolgreich geändert wurde.

6.  
    
    Klicken Sie auf **Weitere Optionen**, um die folgenden Felder zu konfigurieren. Fahren Sie andernfalls mit Schritt 7 fort, um das neue Benutzerpostfach zu speichern.
    
      - **Postfachdatenbank angeben**   Verwenden Sie diese Option, um selbst eine Postfachdatenbank anzugeben, anstatt Exchange die Auswahl einer Datenbank zu überlassen. Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Postfachdatenbank auswählen** zu öffnen. In diesem Dialogfeld werden alle Postfachdatenbanken in Ihrer Exchange-Organisation aufgelistet. Standardmäßig werden die Postfachdatenbanken nach dem Namen sortiert. Sie können auch auf den Titel der entsprechenden Spalte klicken, um die Datenbanken nach Servernamen oder Version zu sortieren. Wählen Sie die gewünschte Postfachdatenbank aus, und klicken Sie dann auf **OK**.
    
      - **Lokalen Archivspeicher für diesen Benutzer erstellen**   Aktivieren Sie dieses Kontrollkästchen, um ein Archivpostfach für das Postfach zu erstellen. Wenn Sie ein Archivpostfach erstellen, werden Postfachelemente automatisch entsprechend den standardmäßigen oder von Ihnen definierten Aufbewahrungsrichtlinien aus dem primären Postfach in das Archiv verschoben.
        
        Klicken Sie auf **Durchsuchen**, um zum Speichern des Archivpostfachs eine Datenbank auszuwählen, die sich in der lokalen Gesamtstruktur befindet.
        
        Weitere Informationen finden Sie unter [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md).
    
      - **Adressbuchrichtlinie**   Verwenden Sie diese Option, um eine Adressbuchrichtlinie für das Postfach anzugeben. Adressbuchrichtlinien enthalten eine globale Adressbuchline (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine Gruppe von Adresslisten. Wenn sie Postfachbenutzern zugewiesen wird, kann diesen über die Adressbuchrichtlinie Zugriff auf eine angepasste GAL in Outlook und Outlook Web App bereitgestellt werden. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).
        
        Wählen Sie in der Dropdownliste die Richtlinie aus, die diesem Postfach zugeordnet werden soll.

7.  
    
    Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um das Postfach zu erstellen.

## Erstellen eines Benutzerpostfachs mithilfe der Shell

In diesem Beispiel werden ein neues Benutzerkonto und Postfach mit den folgenden Details für Pilar Pinilla erstellt:

  - Der Alias lautet "pilarp"

  - Der Vorname lautet "Pilar", und der Nachname lautet "Pinilla"

  - Der Name und Anzeigename lautet "Pilar Pinilla"

  - Der Benutzeranmeldename lautet "pilarp@contoso.com"

  - Das Kennwort lautet "Pa$$word1"

  - Das Postfach wird in der Standard-OU erstellt. Wenn Sie eine andere OU angeben möchten, verwenden Sie den Parameter *OrganizationalUnit*.

<!-- end list -->

    New-Mailbox -Alias pilarp -Name "Pilar Pinilla" -FirstName Pilar -LastName Pinilla -DisplayName "Pilar Pinilla" -UserPrincipalName pilarp@contoso.com -Password (ConvertTo-SecureString -String 'Pa$$word1' -AsPlainText -Force)

Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines Benutzerpostfachs zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Das neue Benutzerpostfach wird in der Postfachliste angezeigt. Unter **Postfachtyp** lautet der Typ **Benutzer**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen Benutzerpostfach anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress

## Erstellen eines Postfachs für einen vorhandenen Benutzer

Sie können außerdem Benutzerpostfächer für vorhandene Benutzer erstellen, die über ein Active Directory-Benutzerkonto verfügen, aber kein entsprechendes Postfach besitzen. Dieser Vorgang wird als *Postfachaktivierung* vorhandener Benutzer bezeichnet. Nach der Postfachaktivierung für einen vorhandenen Benutzer kann der Benutzer Nachrichten senden und empfangen.

## Erstellen eines Postfachs für einen vorhandenen Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie auf **Neu** \> **Benutzerpostfach**.

3.  Geben Sie auf der Seite **Neues Benutzerpostfach** im Feld **Alias** den Alias des Benutzers ein, der den E-Mail-Alias für den Benutzer angibt. Der Benutzeralias ist der Teil links vom @-Symbol in der E-Mail-Adresse. Er muss innerhalb der Gesamtstruktur eindeutig sein.
    

    > [!NOTE]
    > Wenn Sie dieses Feld leer lassen, wird der Wert des Benutzernamens im <STRONG>Benutzeranmeldenamen</STRONG> als E-Mail-Alias verwendet.



4.  Klicken Sie auf **Vorhandener Benutzer**.

5.  Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Benutzer auswählen - Vollständige Gesamtstruktur** zu öffnen. Dieses Dialogfeld enthält eine Liste mit Active Directory-Benutzerkonten in der Gesamtstruktur, die nicht E-Mail-aktiviert sind bzw. nicht über Exchange-Postfächer verfügen. Wählen Sie das Benutzerkonto aus, das für E-Mail aktiviert werden soll, und klicken Sie auf **OK**.
    
    Beim Erstellen eines Postfachs für einen vorhandenen Benutzer brauchen Sie keine Kontoinformationen anzugeben, da diese Informationen bereits in Active Directory vorhanden sind.
    

    > [!NOTE]
    > Das Active Directory-Konto, das Benutzerpostfächern zugeordnet ist, muss sich in derselben Gesamtstruktur wie der Exchange-Server befinden. Sie müssen ein verknüpftes Postfach erstellen, um ein Postfach für ein Benutzerkonto zu erstellen, das sich in einer vertrauenswürdigen Gesamtstruktur befindet. Weitere Informationen finden Sie unter <A href="manage-linked-mailboxes-exchange-2013-help.md">Verwalten verknüpfter Postfächer</A>.



6.  Klicken Sie auf **Weitere Optionen**, um die folgenden Felder zu konfigurieren. Fahren Sie andernfalls mit Schritt 7 fort, um das neue Benutzerpostfach zu speichern.
    
      - **Postfachdatenbank angeben**   Verwenden Sie diese Option, um selbst eine Postfachdatenbank anzugeben, anstatt Exchange die Auswahl einer Datenbank zu überlassen. Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Postfachdatenbank auswählen** zu öffnen. In diesem Dialogfeld werden alle Postfachdatenbanken in Ihrer Exchange-Organisation aufgelistet. Standardmäßig werden die Postfachdatenbanken nach dem Namen sortiert. Sie können auch auf den Titel der entsprechenden Spalte klicken, um die Datenbanken nach Servernamen oder Version zu sortieren. Wählen Sie die gewünschte Postfachdatenbank aus, und klicken Sie dann auf **OK**.
    
      - **Lokalen Archivspeicher für diesen Benutzer erstellen**   Aktivieren Sie dieses Kontrollkästchen, um ein Archivpostfach für das Postfach zu erstellen. Wenn Sie ein Archivpostfach erstellen, werden Postfachelemente automatisch entsprechend den standardmäßigen oder von Ihnen definierten Aufbewahrungsrichtlinien aus dem primären Postfach in das Archiv verschoben.
        
        Klicken Sie auf **Durchsuchen**, um zum Speichern des Archivpostfachs eine Datenbank auszuwählen, die sich in der lokalen Gesamtstruktur befindet.
        
        Weitere Informationen finden Sie unter [In-Situ-Archivierung in Exchange 2013](in-place-archiving-in-exchange-2013-exchange-2013-help.md).
    
      - **Adressbuchrichtlinie**   Verwenden Sie diese Option, um eine Adressbuchrichtlinie für das Postfach anzugeben. Adressbuchrichtlinien enthalten eine globale Adressbuchline (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine Gruppe von Adresslisten. Wenn sie Postfachbenutzern zugewiesen wird, kann diesen über die Adressbuchrichtlinie Zugriff auf eine angepasste GAL in Outlook und Outlook Web App bereitgestellt werden. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).
        
        Wählen Sie in der Dropdownliste die Richtlinie aus, die diesem Postfach zugeordnet werden soll.

7.  Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um das Postfach zu erstellen.

## Verwenden der Shell zum Erstellen eines Postfachs für einen vorhandenen Benutzer

In diesem Beispiel wird ein Postfach für den vorhandenen Benutzer "estherv@contoso.com" in der Exchange-Datenbank "UsersMailboxDatabase" erstellt.

    Enable-Mailbox estherv@contoso.com -Database UsersMailboxDatabase

Sie können auch das Cmdlet **Enable-Mailbox** verwenden, um mehrere Benutzer gleichzeitig für E-Mail zu aktivieren. Dazu werden die Ergebnisse des Cmdlets **Get-User** per Pipelining an das Cmdlet **Enable-Mailbox** umgeleitet. Wenn Sie das Cmdlet **Get-User** ausführen, dürfen nur Benutzer zurückgegeben werden, die noch nicht für E-Mail aktiviert wurden. Dazu müssen Sie für den Parameter *RecipientTypeDetails* den Wert "User" angeben. Sie können den Umfang der zurückgegebenen Ergebnisse auch begrenzen, indem Sie den Parameter *Filter* verwenden, damit nur Benutzer zurückgegeben werden, die die von Ihnen angegebenen Kriterien erfüllen. Anschließend können Sie das Ergebnis per Pipelining an das Cmdlet **Enable-Mailbox** übermitteln.

Beispielsweise wird mit dem folgenden Befehl die Postfachaktivierung für Benutzer durchgeführt, die noch nicht über eine Postfachaktivierung verfügen und für die in der Eigenschaft **UserPrincipalName** ein Wert enthalten ist. Hiermit kann sichergestellt werden, dass Sie nicht versehentlich ein Systemkonto in ein Postfach konvertieren.

    Get-User -RecipientTypeDetails User -Filter { UserPrincipalName -ne $Null } | Enable-Mailbox

Informationen zu Syntax und Parametern finden Sie unter [Enable-Mailbox](https://technet.microsoft.com/de-de/library/aa998251\(v=exchg.150\)) und [Get-User](https://technet.microsoft.com/de-de/library/aa996896\(v=exchg.150\)).

Weitere Informationen zum Pipelining finden Sie unter [Pipelining](https://technet.microsoft.com/de-de/library/aa998260\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines Postfachs für einen vorhandenen Benutzer zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**. Der neue Benutzer mit Postfachaktivierung wird in der Postfachliste angezeigt. Unter **Postfachtyp** lautet der Typ **Benutzer**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen Benutzer mit Postfachaktivierung anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress
    
    Beachten Sie, dass die Eigenschaft *RecipientTypeDetails* den Wert `UserMailbox` aufweist.

