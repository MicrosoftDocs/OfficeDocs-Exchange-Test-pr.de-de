---
title: 'Verwalten von E-Mail-Kontakten: Exchange 2013 Help'
TOCTitle: Verwalten von E-Mail-Kontakten
ms:assetid: 74c72aed-e9ff-4927-8eb7-c08a86e79ae0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998858(v=EXCHG.150)
ms:contentKeyID: 50474798
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.NewMailContactWizardForm.NewMailContactIntroductionWizardPage
ms.translationtype: HT
---

# Verwalten von E-Mail-Kontakten

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-10-04_

E-Mail-Kontakte sind E-Mail-aktivierte Verzeichnisdienstobjekte, die Informationen über Personen oder Organisationen außerhalb der Exchange- oder Exchange Online-Organisation enthalten. Jeder E-Mail-Kontakt verfügt über eine externe E-Mail-Adresse. Weitere Informationen zu E-Mail-Kontakten finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines E-Mail-Kontakts

## Erstellen eines E-Mail-Kontakts mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Klicken Sie auf **Neu** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") \> **E-Mail-Kontakt**.

3.  Füllen Sie auf der Seite **Neuer E-Mail-Kontakt** folgende Felder aus:
    
      - **Vorname**   Geben Sie in diesem Feld den Vornamen des Kontakts ein.
    
      - **Initialen**   Geben Sie in diesem Feld die Initialen des Empfängers ein.
    
      - **Nachname**   Geben Sie in diesem Feld den Nachnamen des Kontakts ein.
    
      - **\* Anzeigename**   Geben Sie in diesem Feld einen Anzeigenamen für den Kontakt ein. Dies ist der Name, der in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation in der Kontaktliste angegeben wird. Dieses Feld wird automatisch mit den Namen aufgefüllt, die Sie in den Feldern **Vorname**, **Initialen** und **Nachname** eingegeben haben. Wenn Sie diese Felder nicht verwendet haben, müssen Sie in diesem Feld einen Namen eingeben, da die Eingabe erforderlich ist. Der Name darf nicht länger als 64 Zeichen sein.
    
      - **\* Name**   Geben Sie in diesem Feld einen Namen für den Kontakt ein. Dabei handelt es sich um den im Verzeichnisdienst aufgeführten Namen. Genau wie beim Anzeigenamen wird dieses Feld automatisch mit den Namen aufgefüllt, die Sie in den Feldern **Vorname**, **Initialen** und **Nachname** eingegeben haben. Wenn Sie diese Felder nicht verwendet haben, müssen Sie in diesem Feld einen Namen eingeben, da die Eingabe erforderlich ist. Der Name darf nicht länger als 64 Zeichen sein.
    
      - **\* Alias**   Geben Sie in diesem Feld einen Alias (maximal 64 Zeichen) für den Kontakt ein. Dieses Feld ist erforderlich.
    
      - **\* Externe E-Mail-Adresse**   Geben Sie in diesem Feld das externe E-Mail-Konto des Kontakts ein. Dieses Feld ist erforderlich. An diesen Kontakt gesendete E-Mails werden an diese E-Mail-Adresse weitergeleitet.
    
      - **Organisationseinheit**   Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container "Benutzer" in der Domäne festgelegt, in der sich der Computer befindet, auf dem das EAC ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container Benutzer ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten der Gesamtstruktur angezeigt, die sich in einem bestimmten Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie dann auf **OK**.
        

        > [!NOTE]
        > Das Feld <STRONG>Organisationseinheit</STRONG> ist nur in Exchange Server&nbsp;2013 verfügbar. In Exchange Online ist es nicht verfügbar.



4.  Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Erstellen eines E-Mail-Kontakts mithilfe der Shell

In diesem Beispiel wird ein E-Mail-Kontakt für Debra Garcia in Exchange Server 2013 erstellt.

    New-MailContact -Name "Debra Garcia" -ExternalEmailAddress dgarcia@tailspintoys.com -OrganizationalUnit Users

In diesem Beispiel wird ein E-Mail-Kontakt für Alan Shen in Exchange Online erstellt.

    New-MailContact -Name "Alan Shen" -ExternalEmailAddress alans@fourthcoffee.com

In diesem Beispiel wird der vorhandener Kontakt "Karen Toh" in Exchange Server 2013 für E-Mail aktiviert.

    Enable-MailContact -Identity "Karen Toh" -ExternalEmailAddress ktoh@tailspintoys.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines E-Mail-Kontakts zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**. Der neue E-Mail-Kontakt wird in der Kontaktliste angezeigt. Unter **Kontakttyp** lautet der Typ **E-Mail-Kontakt**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen E-Mail-Kontakt anzuzeigen.
    
        Get-MailContact <Name> | FL Name,RecipientTypeDetails,ExternalEmailAddress

## Ändern von E-Mail-Kontakt-Eigenschaften

## Ändern von E-Mail-Kontakt-Eigenschaften mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Klicken Sie in der Liste der E-Mail-Kontakte und E-Mail-Benutzer auf den E-Mail-Kontakt, dessen Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den E-Mail-Kontakt-Eigenschaften auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Kontaktinformationen
    
      - Organization (Organisation)
    
      - E-Mail-Optionen (in Exchange Online nicht verfügbar)
    
      - E-Mail-Info

## Allgemein

Verwenden Sie den Abschnitt **Allgemein**, um grundlegende Informationen zum E-Mail-Kontakt anzuzeigen oder zu ändern.

  - **Vorname**, **Initialen**, **Nachname**

  - **\* Name**   Das ist der Name, der in Active Directory aufgelistet wird. Wenn Sie diesen Namen ändern, darf er nicht länger als 64 Zeichen sein.

  - **\* Anzeigename**   Dieser Name wird im Adressbuch Ihrer Organisation, in den Zeilen "An" und "Von" in E-Mails sowie in der Postfachliste angezeigt. Dieser Name darf keine Leerzeichen vor oder nach dem Anzeigenamen enthalten.

  - **\* Alias**   Dies ist der Alias des E-Mail-Kontakts. Wenn Sie diesen ändern, beachten Sie, dass er in der Organisation eindeutig sein muss und höchstens 64 Zeichen lang sein darf.

  - **\* Externe E-Mail-Adresse**   Dies ist die primäre SMTP-Adresse und das externe E-Mail-Konto des E-Mail-Kontakts. An diesen Kontakt gesendete E-Mails werden an diese E-Mail-Adresse weitergeleitet.

  - Klicken Sie auf **Weitere Optionen**, um die Organisationseinheit anzuzeigen, die das Konto des E-Mail-Kontakts enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um den Kontakt in eine andere Organisationseinheit zu verschieben.

## Kontaktinformationen

Verwenden Sie den Abschnitt **Kontaktinformationen**, um die Kontaktinformationen des Empfängers wie z. B. E-Mail-Adresse und Telefonnummern anzuzeigen oder zu ändern. Diese Informationen werden im Adressbuch angezeigt.

## Organization (Organisation)

Verwenden Sie den Abschnitt **Organisation**, um detaillierte Informationen zur Rolle des E-Mail-Kontakts in der Organisation aufzuzeichnen. Diese Informationen werden im Adressbuch angezeigt. Sie können auch ein virtuelles Organisationsdiagramm erstellen, auf das von E-Mail-Clients wie Outlook zugegriffen werden kann.

  - **Titel**   In diesem Feld kann der Titel des E-Mail-Kontakts angezeigt oder geändert werden.

  - **Abteilung**   In diesem Feld kann die Abteilung, in der der E-Mail-Kontakt tätig ist, angezeigt oder geändert werden. Sie können dieses Feld verwenden, um Empfängerbedingungen für dynamische Verteilergruppen und Adresslisten zu erstellen.

  - **Firma**   Verwenden Sie dieses Feld, um das Unternehmen, in dem der E-Mail-Kontakt tätig ist, anzuzeigen oder zu ändern. Sie können dieses Feld auch verwenden, um Empfängerbedingungen für dynamische Verteilergruppen zu erstellen.

  - **Vorgesetzter**   Um einen Vorgesetzten hinzuzufügen, klicken Sie auf **Durchsuchen**. Wählen Sie im Dialogfeld **Vorgesetzten auswählen** eine Person aus, und klicken Sie dann auf **OK**.

  - **Direkte Mitarbeiter**   Dieses Feld kann nicht geändert werden. Ein *direkt unterstellter Mitarbeiter* ist ein Empfänger, der einem bestimmten Vorgesetzten unterstellt ist. Wenn Sie einen Vorgesetzten für den Empfänger angegeben haben, wird dieser Empfänger als direkter Mitarbeiter in den Postfachdetails des Vorgesetzten angezeigt. Ein Beispiel: Toby ist Vorgesetzter von Ann und Spencer, die E-Mail-Kontakte sind. Toby ist also in den Organisationseigenschaften für Ann und Spencer als **Vorgesetzter** angegeben, und Ann und Spencer werden in den Eigenschaften von Tobys Postfach als **Direkte Mitarbeiter** angezeigt.

## E-Mail-Optionen

Verwenden Sie den Abschnitt **E-Mail-Optionen**, um Proxyadressen für einen E-Mail-Kontakt hinzuzufügen oder daraus zu entfernen oder um vorhandene Proxyadresse zu bearbeiten. Die primäre SMTP-Adresse des E-Mail-Kontakts wird in diesem Abschnitt ebenfalls angezeigt, kann aber nicht geändert werden. Zum Ändern dieser Adresse müssen Sie die externe E-Mail-Adresse des Kontakts im Abschnitt **Allgemein** ändern.


> [!NOTE]
> Der Abschnitt <STRONG>E-Mail-Optionen</STRONG> ist nur in Exchange Server&nbsp;2013 verfügbar. In Exchange Online ist er nicht vorhanden.



## E-Mail-Info

Verwenden Sie den Abschnitt **E-Mail-Info**, um eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, bevor sie eine Nachricht an diesen Empfänger senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn dieser Empfänger dem Feld "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Ändern von Eigenschaften von E-Mail-Kontakten mithilfe der Shell

Die Eigenschaften eines E-Mail-Kontakts werden sowohl in Active Directory als auch in Exchange gespeichert. Im Allgemeinen verwenden Sie die Cmdlets **Get-Contact** und **Set-Contact**, um Eigenschaften von Organisations- und Kontaktinformationen zu ändern. Verwenden Sie die Cmdlets **Get-MailContact** und **Set-MailContact**, um E-Mail-bezogene Eigenschaften wie E-Mail-Adressen, E-Mail-Infos und benutzerdefinierte Attribute anzuzeigen oder zu ändern und um anzugeben, ob der Kontakt in Adresslisten ausgeblendet werden soll.

Weitere Informationen hierzu finden Sie in den folgenden Themen:

  - [Get-Contact](https://technet.microsoft.com/de-de/library/aa998258\(v=exchg.150\))

  - [Set-Contact](https://technet.microsoft.com/de-de/library/bb124535\(v=exchg.150\))

  - [Get-MailContact](https://technet.microsoft.com/de-de/library/bb124717\(v=exchg.150\))

  - [Set-MailContact](https://technet.microsoft.com/de-de/library/aa995950\(v=exchg.150\))

Im Folgenden finden Sie einige Beispiele, wie Sie Eigenschaften von E-Mail-Kontakten mithilfe der Shell ändern können.

In diesem Beispiel werden die Eigenschaften für Titel, Abteilung, Unternehmen und Vorgesetzter für den E-Mail-Kontakt Kai Axford konfiguriert.

    Set-Contact "Kai Axford" _-Title Consultant -Department "Public Relations" -Company Fabrikam -Manager "Karen Toh"

In diesem Beispiel wird die Eigenschaft "CustomAttribute1" für alle E-Mail-Kontakte auf den Wert "PartTime" festgelegt, und alle Kontakte werden im Organisationsadressbuch ausgeblendet.

    Get-MailContact | Set-MailContact -CustomAttribute1 PartTime -HiddenFromAddressListsEnabled $true

In diesem Beispiel wird die Eigenschaft "CustomAttribute15" für alle E-Mail-Kontakte in der Abteilung "Public Relations" auf den Wert "TemporaryEmployee" festgelegt.

    Get-Contact -Filter "Department -eq 'Public Relations'" | Set-MailContact -CustomAttribute15 TemporaryEmployee

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Eigenschaften eines E-Mail-Kontakts erfolgreich geändert wurden:

  - Wählen Sie in der Exchange-Verwaltungskonsole den E-Mail-Kontakt aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft anzuzeigen, die Sie geändert haben.

  - Verwenden Sie in der Shell die Cmdlets **Get-Contact** und **Get-MailContact**, um die Änderungen zu überprüfen. Ein Vorteil bei der Verwendung der Shell besteht darin, dass Sie mehrere Eigenschaften für mehrere E-Mail-Kontakte anzeigen können. Im oben stehenden Beispiel, in dem die Eigenschaft "CustomAttribute1" für alle E-Mail-Kontakte auf "PartTime" festgelegt wurde und alle Kontakte im Adressbuch ausgeblendet wurden, führen Sie folgenden Befehl aus, um die Änderungen zu überprüfen.
    
        Get-MailContact | Fl Name,CustomAttribute1,HiddenFromAddressListsEnabled
    
    Im oben stehenden Beispiel, in dem die Eigenschaft "CustomAttribute15" für alle E-Mail-Kontakte in der Abteilung "Public Relations" festgelegt wurde, führen Sie folgenden Befehl aus, um die Änderungen zu überprüfen.
    
        Get-Contact -Filter "Department -eq 'Public Relations'" | Get-MailContact | FL Name,CustomAttribute15

## Massenbearbeitung von E-Mail-Kontakten

Sie können in der Exchange-Verwaltungskonsole ausgewählte Eigenschaften für mehrere E-Mail-Kontakte ändern. Wenn Sie in der Exchange-Verwaltungskonsole mindestens zwei E-Mail-Kontakte aus der Kontaktliste auswählen, werden die Eigenschaften im Detailbereich angezeigt, die per Massenbearbeitung geändert werden können. Wenn Sie eine dieser Eigenschaften ändern, wird die Änderungen auf alle ausgewählten Empfänger angewandt.

Bei der Massenbearbeitung von E-Mail-Kontakten können Sie folgende Eigenschaftsbereiche ändern:

  - **Kontaktinformationen**   Ändern Sie freigegebene Eigenschaften wie Straße, PLZ und Ort.

  - **Organisation**   Ändern Sie freigegebene Eigenschaften wie Abteilungsname, Firmenname und den Vorgesetzten, an den die ausgewählten E-Mail-Kontakte oder E-Mail-Benutzer berichten.

## Ändern von E-Mail-Kontakten per Massenbearbeitung

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Wählen Sie in der Kontaktliste mindestens zwei E-Mail-Kontakte aus. Für Kombinationen aus E-Mail-Kontakten und E-Mail-Benutzern ist keine Massenbearbeitung möglich.
    

    > [!TIP]
    > Sie können mehrere benachbarte E-Mail-Kontakte auswählen, indem Sie bei gedrückter UMSCHALTTASTE auf den ersten und anschließend auf den letzten Kontakt klicken. Sie können auch mehrere nicht benachbarte E-Mail-Kontakte auswählen, indem Sie bei gedrückter STRG-TASTE auf die gewünschten Kontakte klicken.



3.  Klicken Sie im Detailbereich unter **Massenbearbeitung** unter **Kontaktinformationen** oder **Organisation** auf **Aktualisieren**.

4.  Nehmen Sie die Änderungen auf der Eigenschaftenseite vor, und speichern Sie Ihre Änderungen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Massenbearbeitung von E-Mail-Kontakten zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole jeden der E-Mail-Kontakte aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaften anzuzeigen, die Sie geändert haben.

  - In der Shell verwenden Sie das Cmdlet **Get-Contact**, um die Änderungen zu überprüfen. Ein Beispiel: Sie haben die Massenbearbeitungsfunktion in der Exchange-Verwaltungskonsole verwendet, um den Vorgesetzten und das Büro für alle E-Mail-Kontakte eines Lieferantenunternehmens namens "A. Datum Corporation" zu ändern. Sie können den folgenden Befehl in der Shell ausführen, um diese Änderungen zu überprüfen.
    
        Get-Contact -ResultSize unlimited -Filter {(Company -eq 'Adatum')} | fl Name,Office,Manager


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Bb123521.eac8a413-9498-4220-8544-1e37d1aaea13(EXCHG.150).png" title="Das Kurzsymbol für LinkedIn Learning" alt="Das Kurzsymbol für LinkedIn Learning" /> <strong>Neu bei Office 365?</strong><br />
Entdecken Sie die kostenlosen Videokurse für <a href="https://support.office.com/de-de/article/office-365-admin-and-it-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5">Office 365 admins and IT pros</a>, präsentiert von LinkedIn Learning.</p></td>
</tr>
</tbody>
</table>

