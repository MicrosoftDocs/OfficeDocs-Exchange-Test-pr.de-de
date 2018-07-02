---
title: 'Verwalten von E-Mail-Benutzern: Exchange 2013 Help'
TOCTitle: Verwalten von E-Mail-Benutzern
ms:assetid: bb8b8804-f730-4ad7-9173-896a4965b90f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124381(v=EXCHG.150)
ms:contentKeyID: 50474834
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.NewMailUserWizardForm.NewMailUserIntroductionWizardPage
ms.translationtype: HT
---

# Verwalten von E-Mail-Benutzern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

E-Mail-Benutzer ähneln E-Mail-Kontakten. Beide verfügen über externe E-Mail-Adressen und können Informationen zu Personen außerhalb Ihrer Exchange- oder Exchange Online-Organisation enthalten, und beide können im freigegebenen Adressbuch und in anderen Adresslisten angezeigt werden. Im Gegensatz zu E-Mail-Kontakten verfügen E-Mail-Benutzer jedoch über Anmeldeinformationen in Ihrer Exchange- oder Office 365-Organisation und können auf Ressourcen zugreifen. Weitere Informationen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines E-Mail-Benutzers

## Erstellen eines E-Mail-Benutzers mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Kontakte** \> **Neu** \> **E-Mail-Benutzer**.

2.  Geben Sie auf der Seite **Neuer E-Mail-Benutzer** im Feld **\* Alias** einen Alias für den E-Mail-Benutzer ein. Der Alias darf höchstens 64 Zeichen enthalten und muss in der Gesamtstruktur eindeutig sein. Dieses Feld ist erforderlich.

3.  Führen Sie einen der folgenden Schritte durch, um den E-Mail-Adresstyp für den E-Mail-Benutzer anzugeben:
    
      - Um für die externe E-Mail-Adresse des Benutzers eine SMTP-E-Mail-Adresse anzugeben, klicken Sie auf **SMTP**.
        

        > [!NOTE]
        > Exchange überprüft SMTP-Adressen auf ordnungsgemäße Formatierung. Entspricht Ihr Eintrag nicht dem SMTP-Format, wird eine Fehlermeldung angezeigt, wenn Sie auf <STRONG>Speichern</STRONG> klicken, um den E-Mail-Benutzer zu erstellen.

    
      - Um einen benutzerdefinierten Adresstyp anzugeben, aktivieren Sie das Optionsfeld, und geben Sie dann den benutzerdefinierten Adresstyp an. Sie können beispielsweise eine Adresse vom Typ X.500, GroupWise oder Lotus Notes angeben.

4.  Geben Sie im Feld **\* Externe E-Mail-Adresse** die externe E-Mail-Adresse des Benutzers ein. An diesen E-Mal-Benutzer gesendete E-Mails werden an diese E-Mail-Adresse weitergeleitet. Dieses Feld ist erforderlich.

5.  
    
    Wählen Sie eine der folgenden Optionen aus:
    
      - **Vorhandener Benutzer**   Wählen Sie diese Option aus, um einen vorhandenen Benutzer für E-Mail zu aktivieren.
        
        Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Benutzer auswählen - Vollständige Gesamtstruktur** zu öffnen. Dieses Dialogfeld enthält eine Liste mit Benutzerkonten in der Organisation, die nicht E-Mail-aktiviert sind bzw. nicht über Postfächer verfügen. Wählen Sie das Benutzerkonto aus, das für E-Mail aktiviert werden soll, und klicken Sie auf **OK**. Wenn Sie diese Option auswählen, brauchen Sie keine Informationen zum Benutzerkonto anzugeben, da diese Informationen bereits in Active Directory vorhanden sind.
    
      - **Neuer Benutzer**   Wählen Sie diese Option aus, um in Active Directory ein neues Benutzerkonto zu erstellen und den Benutzer für E-Mail zu aktivieren. Wenn Sie diese Option auswählen, müssen Sie die erforderlichen Informationen zum Benutzerkonto angeben.

6.  
    
    Wenn Sie in Schritt 5 **Neuer Benutzer** ausgewählt haben, füllen Sie die folgenden Felder auf der Seite **Neuer E-Mail-Benutzer** aus. Fahren Sie andernfalls mit Schritt 7 fort.
    
      - **Vorname**   Geben Sie in diesem Feld den Vornamen des E-Mail-Benutzers ein.
    
      - **Initialen**   Geben Sie in diesem Feld die Initialen des E-Mail-Benutzers ein.
    
      - **Nachname**   Geben Sie in diesem Feld den Nachnamen des E-Mail-Benutzers ein.
    
      - **\* Anzeigename**   Geben Sie in diesem Feld einen Anzeigenamen für den Benutzer ein. Dies ist der Name, der in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation in der Kontaktliste angegeben wird. Dieses Feld wird automatisch mit den Namen aufgefüllt, die Sie in den Feldern **Vorname**, **Initialen** und **Nachname** eingegeben haben. Wenn Sie diese Felder nicht verwendet haben, müssen Sie in diesem Feld einen Namen eingeben, da die Eingabe erforderlich ist. Der Name darf nicht länger als 64 Zeichen sein.
    
      - **\* Name**   Geben Sie in diesem Feld einen Namen für den E-Mail-Benutzer ein. Dabei handelt es sich um den im Verzeichnisdienst aufgeführten Namen. Dieses Feld wird ebenfalls mit den Namen aufgefüllt, die Sie in den Feldern **Vorname**, **Initialen** und **Nachname** eingegeben haben. Wenn Sie diese Felder nicht verwendet haben, müssen Sie in diesem Feld einen Namen eingeben, da die Eingabe erforderlich ist. Dieser Name darf ebenfalls nicht länger als 64 Zeichen sein.
        

        > [!NOTE]
        > Das Feld <STRONG>Name</STRONG> ist nur in Exchange Server&nbsp;2013 verfügbar. In Exchange Online ist es nicht verfügbar.

    
      - **Organisationseinheit**   Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container **Benutzer** in der Domäne festgelegt, in der sich der Computer befindet, auf dem die Exchange-Verwaltungskonsole ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container **Benutzer** ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten der Gesamtstruktur angezeigt, die sich in einem bestimmten Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie dann auf **OK**.
        

        > [!NOTE]
        > Das Feld <STRONG>Organisationseinheit</STRONG> ist nur in Exchange Server&nbsp;2013 verfügbar. In Exchange Online ist es nicht verfügbar.

    
      - **\* Benutzeranmeldename**   Geben Sie in diesem Feld den Namen ein, den der E-Mail-Benutzer zum Anmelden bei der Domäne verwendet. Der Anmeldename des Benutzers setzt sich aus einem Benutzernamen auf der linken Seite des at-Zeichens (@) und einem Suffix auf der rechten Seite zusammen. Normalerweise ist das Suffix der Name der Domäne, in der sich das Benutzerkonto befindet.
        

        > [!NOTE]
        > In Exchange Online heißt dieses Feld <STRONG>Benutzer-ID</STRONG>.

    
      - **\* Neues Kennwort**   Geben Sie in diesem Feld das Kennwort ein, mit dem sich der E-Mail-Benutzer bei der Domäne anmelden muss.
        

        > [!NOTE]
        > Stellen Sie sicher, dass das angegebene Kennwort den Anforderungen hinsichtlich Länge, Komplexität und Verlauf der Domäne entspricht, in der Sie das Benutzerkonto erstellen.

    
      - **\* Kennwort bestätigen**   Verwenden Sie dieses Feld zum Bestätigen des Kennworts, das Sie im Feld **Kennwort** eingegeben haben.
    
      - **Bei nächster Anmeldung Kennwortänderung anfordern**   Aktivieren Sie dieses Kontrollkästchen, wenn der E-Mail-Benutzer das Kennwort bei der ersten Anmeldung bei der Domäne zurücksetzen soll.
        
        Wenn Sie dieses Kontrollkästchen aktivieren, wird der neue E-Mail-Benutzer bei der erstmaligen Anmeldung über ein Dialogfeld aufgefordert, das Kennwort zu ändern. Der E-Mail-Benutzer kann erst dann Aufgaben ausführen, wenn das Kennwort erfolgreich geändert wurde.

7.  
    
    Wenn Sie fertig sind, klicken Sie auf **Speichern**, um den E-Mail-Benutzer zu erstellen.

## Erstellen eines E-Mail-Benutzers mithilfe der Shell

In diesem Beispiel wird in Exchange Server 2013 für Jeffrey Zeng ein E-Mail-aktiviertes Benutzerkonto mit den folgenden Angaben erstellt:

  - Der Name und Anzeigename lautet "Jeffrey Zeng".

  - Der Alias ist "jeffreyz".

  - Die externe E-Mail-Adresse ist "jzeng@tailspintoys.com".

  - Der Vorname ist "Jeffrey" und der Nachname ist "Zeng".

  - Der Anmeldename ist "jeffreyz@contoso.com".

  - Das Kennwort lautet "Pa$$word1".

  - Der E-Mail-Benutzer wird in der Standard-OU erstellt. Wenn Sie eine andere OU angeben möchten, verwenden Sie den Parameter *OrganizationalUnit*.

<!-- end list -->

    New-MailUser -Name "Jeffrey Zeng" -Alias jeffreyz -ExternalEmailAddress jzeng@tailspintoys.com -FirstName Jeffrey -LastName Zeng -UserPrincipalName jeffreyz@contoso.com -Password (ConvertTo-SecureString -String 'Pa$$word1' -AsPlainText -Force)

In diesem Beispiel wird in Exchange Online für Rene Valdes ein E-Mail-aktiviertes Benutzerkonto.

    New-MailUser -Name "Rene Valdes" -Alias renev -ExternalEmailAddress renevaldes@fineartschool.edu -FirstName Rene -LastName Valdes -MicrosoftOnlineServicesID renev@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force)

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Erstellung eines E-Mail-Benutzers zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**. Der neue E-Mail-Benutzer wird in der Liste der Kontakte angezeigt. Unter **Kontakttyp** lautet der Typ **E-Mail-Benutzer**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen E-Mail-Benutzer anzuzeigen.
    
        Get-MailUser <Name> | FL Name,RecipientTypeDetails,ExternalEmailAddress

## Ändern von E-Mail-Benutzereigenschaften

Nachdem Sie einen E-Mail-Benutzer erstellt haben, können Sie in der Exchange-Verwaltungskonsole oder in der Shell Änderungen vornehmen und zusätzliche Eigenschaften festlegen.

Sie können auch Eigenschaften für mehrere Benutzerpostfächer gleichzeitig ändern. Weitere Informationen finden Sie unter Massenbearbeitung von E-Mail-Benutzern Verwenden mithilfe der Exchange-Verwaltungskonsole.

Die geschätzte Zeit bis zum Abschließen des Vorgangs variiert je nach der Anzahl von Eigenschaften, die Sie anzeigen oder ändern möchten.

## Ändern von Benutzerpostfacheigenschaften mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Klicken Sie in der Liste der Kontakte auf den E-Mail-Benutzer, dessen Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Eigenschaften des E-Mail-Benutzers auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Kontaktinformationen
    
      - Organization (Organisation)
    
      - E-Mail-Adressen
    
      - Nachrichtenflusseinstellungen
    
      - Mitglied von
    
      - E-Mail-Info

## Allgemein

Klicken Sie auf den Abschnitt **Allgemein**, um grundlegende Informationen zum E-Mail-Benutzer anzuzeigen oder zu ändern.

  - **Vorname**, **Initialen**, **Nachname**

  - **\* Name**   Das ist der Name, der in Active Directory aufgelistet wird. Wenn Sie diesen Namen ändern, darf er nicht länger als 64 Zeichen sein.

  - **\* Anzeigename**    Dieser Name wird im Adressbuch der Organisation in der Zeile "An:" und "Von:" in einer E-Mail und in der Liste der Kontakte in der Exchange-Verwaltungskonsole angezeigt. Dieser Name darf keine Leerzeichen vor oder nach dem Anzeigenamen enthalten.

  - **\* Benutzeranmeldename**   Dies ist der Name, mit dem sich der Benutzer bei der Domäne anmeldet. In Exchange Online ist dies die Benutzer-ID, mit der sich der Benutzer an Office 365 anmeldet.

  - **Aus Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass der E-Mail-Benutzer im Adressbuch und anderen Adresslisten angezeigt wird, die in Ihrer Exchange-Organisation definiert sind. Nachdem Sie das Kontrollkästchen aktiviert haben, können Benutzer weiterhin unter Verwendung der E-Mail-Adresse Nachrichten an den Empfänger senden.

  - **Bei nächster Anmeldung Kennwortänderung anfordern**   Aktivieren Sie dieses Kontrollkästchen, wenn der Benutzer das Kennwort bei der nächsten Anmeldung bei der Domäne zurücksetzen soll.
    

    > [!NOTE]
    > Dieses Feld ist nicht in Exchange Online verfügbar.



Klicken Sie auf **Weitere Optionen**, um diese zusätzlichen Eigenschaften anzuzeigen oder zu ändern:

  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit (OU) an, die das E-Mail-Benutzerkonto enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um das Konto in eine andere Organisationseinheit zu verschieben.
    

    > [!NOTE]
    > Dieses Feld ist nicht in Exchange Online verfügbar.



  - **Benutzerdefinierte Attribute**   In diesem Abschnitt werden die für den E-Mail-Benutzer festgelegten benutzerdefinierten Attribute angezeigt. Klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um benutzerdefinierte Attributwerte anzugeben. Bis zu 15 benutzerdefinierte Attribute für den Empfänger können definiert werden.

## Kontaktinformationen

Verwenden Sie den Abschnitt **Kontaktinformationen**, um die Kontaktinformationen des Benutzers anzuzeigen oder zu ändern. Die Informationen auf dieser Seite werden im Adressbuch angezeigt. Klicken Sie auf **Weitere Optionen**, um zusätzliche Felder anzuzeigen.


> [!TIP]
> Sie können das Feld <STRONG>Bundesland/Kanton</STRONG> verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.



## Organization (Organisation)

Verwenden Sie den Abschnitt **Organisation**, um ausführliche Informationen zur Rolle des Benutzers in der Organisation aufzuzeichnen. Diese Informationen werden im Adressbuch angezeigt. Sie können auch ein virtuelles Organisationsdiagramm erstellen, auf das von E-Mail-Clients wie Outlook zugegriffen werden kann.

  - **Titel**   In diesem Feld kann der Titel des Empfängers angezeigt oder geändert werden.

  - **Abteilung**   Verwenden Sie dieses Feld, um die Abteilung, in der der Benutzer tätig ist, anzuzeigen oder zu ändern. Sie können dieses Feld verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.

  - **Firma**   Verwenden Sie dieses Feld, um das Unternehmen, in dem der Benutzer tätig ist, anzuzeigen oder zu ändern. Sie können dieses Feld verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.

  - **Vorgesetzter**   Um einen Vorgesetzten hinzuzufügen, klicken Sie auf **Durchsuchen**. Wählen Sie im Dialogfeld **Vorgesetzten auswählen** eine Person aus, und klicken Sie dann auf **OK**.

  - **Direkte Mitarbeiter**   Dieses Feld kann nicht geändert werden. Ein *direkt unterstellter Mitarbeiter* ist ein Benutzer, der einem bestimmten Vorgesetzten unterstellt ist. Wenn Sie einen Vorgesetzten für den Benutzer angegeben haben, wird dieser Benutzer als direkt unterstellter Mitarbeiter in den Postfachdetails des Vorgesetzten angezeigt. So sind Chris und Kate beispielsweise Kari unterstellt, also wurde Kari im Feld **Vorgesetzter** von Chris und Kate angegeben, und Chris und Kate werden im Feld **Direkter Mitarbeiter** in den Eigenschaften von Karis Konto angezeigt.

## E-Mail-Adressen

Im Abschnitt **E-Mail-Adressen** können Sie die E-Mail-Adressen anzeigen und ändern, die dem E-Mail-Benutzer zugeordnet sind. Dazu gehören die primäre SMTP-Adresse des E-Mail-Benutzers, alle externen E-Mail-Adressen und alle zugehörigen Proxyadressen. Die primäre SMTP-Adresse (auch als *Standardantwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben. Nachdem der E-Mail-Benutzer erstellt wurde, sind die primäre SMTP-Adresse und externe E-Mail-Adresse standardmäßig gleich.

  - **Hinzufügen **  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue E-Mail-Adresse für dieses Postfach hinzuzufügen. Wählen Sie einen der folgenden Adresstypen aus:
    
      - **SMTP**   Dies ist der Standardadresstyp. Klicken Sie auf diese Schaltfläche, und geben Sie dann die neue SMTP-Adresse in das Feld **\* E-Mail-Adresse** ein.
    
      - **Benutzerdefinierter Adresstyp**   Klicken Sie auf diese Schaltfläche, und geben Sie einen der unterstützten Nicht-SMTP-E-Mail-Adresstypen in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Mit Ausnahme von X.400-Adressen überprüft Exchange benutzerdefinierte Adressen nicht auf ordnungsgemäße Formatierung. Sie müssen sicherstellen, dass die von Ihnen angegebene benutzerdefinierte Adresse die Formatanforderungen für den jeweiligen Adresstyp erfüllt.



  - **Legen Sie die externe E-Mail-Adresse fest**   In diesem Feld können Sie die externe Adresse des E-Mail-Benutzers ändern. An diesen E-Mal-Benutzer gesendete E-Mails werden an diese E-Mail-Adresse weitergeleitet.

  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden. Diese Option ist standardmäßig aktiviert.
    

    > [!NOTE]
    > Dieses Kontrollkästchen ist nicht in Exchange Online verfügbar.



## Nachrichtenflusseinstellungen

Im Abschnitt **Nachrichtenübermittlungseinstellungen** können Sie die folgenden Einstellungen anzeigen oder ändern:

  - **Größenbeschränkungen für Nachrichten**   Diese Einstellungen steuern die Größe von Nachrichten, die vom E-Mail-Benutzer gesendet und empfangen werden können. Klicken Sie auf **Details anzeigen**, um die maximale Größe für gesendete und empfangene Nachrichten anzuzeigen und zu ändern.
    
      - **Gesendete Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer gesendete Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht sendet, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Benutzer zurückgesendet.
    
      - **Empfangene Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer empfangene Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht empfängt, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Absender zurückgesendet.

  - **Einschränkungen für die Nachrichtenzustellung**   Diese Einstellungen steuern, welche Personen E-Mails an diesen E-Mail-Benutzer senden können. Klicken Sie auf **Details anzeigen**, um diese Einschränkungen anzuzeigen und zu ändern.
    
      - **Nachrichten annehmen von**   Verwenden Sie diesen Abschnitt, um anzugeben, wer Nachrichten an diesen Benutzer senden kann.
        
          - **Alle Absender**   Wählen Sie diese Option, um festzulegen, dass der Empfänger Nachrichten von allen Absendern akzeptieren kann. Dies schließt sowohl Absender innerhalb der Exchange-Organisation als auch externe Absender ein. Diese Option ist standardmäßig ausgewählt. Diese Option schließt externe Benutzer nur ein, wenn Sie das Kontrollkästchen **Authentifizierung aller Absender anfordern** deaktivieren. Wenn Sie dieses Kontrollkästchen aktivieren, werden Nachrichten von externen Benutzern zurückgewiesen.
        
          - **Nur Absender aus der folgenden Liste**   Wählen Sie diese Option aus, um festzulegen, dass der Benutzer nur Nachrichten einer bestimmten Gruppe von Absendern in der Exchange-Organisation empfangen kann. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Seite **Empfänger auswählen** aufzurufen, die eine Liste aller Empfänger in Ihrer Exchange-Organisation anzeigt. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
        
          - **Authentifizierung aller Absender anfordern**   Wählen Sie diese Option, um zu verhindern, dass anonyme Benutzer Nachrichten an den Benutzer senden können.
    
      - **Nachrichten ablehnen von**   Verwenden Sie diesen Abschnitt, um Benutzer daran zu hindern, Nachrichten an diesen Benutzer zu senden.
        
          - **Keinem Absender**   Wählen Sie diese Option, um festzulegen, dass das Postfach keine Nachrichten von Absendern in der Exchange-Organisation zurückweist. Diese Option ist standardmäßig ausgewählt.
        
          - **Absendern aus der folgenden Liste**   Wählen Sie diese Option, um festzulegen, dass das Postfach Nachrichten von einer bestimmten Gruppe von Absendern in der Exchange-Organisation zurückweist. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Seite **Empfänger auswählen** aufzurufen, die eine Liste aller Empfänger in Ihrer Exchange-Organisation anzeigt. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.

## Mitglied von

Im Abschnitt **Mitglied von** können Sie eine Liste der Verteiler- oder Sicherheitsgruppen anzeigen, denen dieser Benutzer angehört. Informationen zur Mitgliedschaft können auf dieser Seite nicht geändert werden. Beachten Sie, dass der Benutzer möglicherweise den Kriterien für mindestens eine dynamische Verteilergruppe in Ihrer Organisation entspricht. Dynamische Verteilergruppen werden auf dieser Seite jedoch nicht angezeigt, da ihre Mitgliedschaft zum Zeitpunkt ihrer Verwendung stets neu berechnet wird.

## E-Mail-Info

Verwenden Sie den Abschnitt **E-Mail-Info**, um eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, bevor sie eine Nachricht an diesen Empfänger senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn dieser Empfänger dem Feld "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Ändern von E-Mail-Benutzereigenschaften mit der Shell

Die Eigenschaften eines E-Mail-Benutzers sind in Active Directory und in Exchange gespeichert. Im Allgemeinen verwenden Sie die Cmdlets **Get-User** und **Set-User**, um Organisations- und Kontaktinformationseigenschaften zu ändern. Sie verwenden die Cmdlets **Get-MailUser** und **Set-MailUser**, um E-Mail-bezogene Eigenschaften wie E-Mail-Adressen, E-Mail-Infos und benutzerdefinierte Attribute anzuzeigen und zu ändern. Hier können Sie auch festlegen, ob der E-Mail-Benutzer in Adresslisten ausgeblendet werden soll.

Mit den Cmdlets **Get-MailUser** und **Set-MailUser** können Sie die Eigenschaften von E-Mail-Benutzern anzeigen und ändern. Weitere Informationen finden Sie unter den folgenden Themen:

  - [Get-User](https://technet.microsoft.com/de-de/library/aa996896\(v=exchg.150\))

  - [Set-User](https://technet.microsoft.com/de-de/library/aa998221\(v=exchg.150\))

  - [Get-MailUser](https://technet.microsoft.com/de-de/library/aa997254\(v=exchg.150\))

  - [Set-MailUser](https://technet.microsoft.com/de-de/library/aa995971\(v=exchg.150\))

Hier finden Sie einige Beispiele dafür, wie Sie mit der Shell Eigenschaften für E-Mail-Benutzer ändern können.

In diesem Beispiel wird die externe E-Mail-Adresse für Pilar Pinilla festgelegt.

    Set-MailUser "Pilar Pinilla" -ExternalEmailAddress pilarp@tailspintoys.com

In diesem Beispiel werden alle E-Mail-Benutzer im Adressbuch der Organisation ausgeblendet.

    Get-MailUser | Set-MailUser -HiddenFromAddressListsEnabled $true

In diesem Beispiel wird die Eigenschaft "Company" für alle E-Mail-Benutzer in "Contoso" geändert.

    Get-User -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'mailuser')} | Set-User -Company Contoso

In diesem Beispiel wird die Eigenschaft "CustomAttribute1" für alle E-Mail-Benutzer, deren Eigenschaft "Company" den Wert "Contoso" aufweist, in den Wert "ContosoEmployee" geändert.

    Get-User -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'mailuser') -and (Company -eq 'Contoso')}| Set-MailUser -CustomAttribute1 ContosoEmployee

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Änderung der Eigenschaften von E-Mail-Benutzern zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole den E-Mail-Benutzer aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft anzuzeigen, die Sie geändert haben.

  - In der Shell verwenden Sie die Cmdlets **Get-User** und **Get-MailUser**, um die Änderungen zu überprüfen. Ein Vorteil bei der Verwendung der Shell besteht darin, dass Sie mehrere Eigenschaften für mehrere E-Mail-Kontakte anzeigen können.
    
        Get-MailUser | Fl Name,CustomAttribute1 
    
    Führen Sie für das Beispiel oben, in dem die Eigenschaft "Company" für alle E-Mail-Kontakte auf "Contoso" festgelegt wurde, den folgenden Befehl aus, um die Änderungen zu überprüfen:
    
        Get-User -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'mailuser')} | FL Name,Company
    
    Führen Sie im Beispiel oben, in dem die Eigenschaft "CustomAttribute1" auf "ContosoEmployee" festgelegt wurde, den folgenden Befehl aus, um die Änderungen zu überprüfen.
    
        Get-MailUser | Fl Name,CustomAttribute1 

## Massenbearbeitung von E-Mail-Benutzern

Sie können mithilfe der Exchange-Verwaltungskonsole auch ausgewählte Eigenschaften für mehrere E-Mail-Benutzer ändern. Wenn Sie in der Kontaktliste in der Exchange-Verwaltungskonsole zwei oder mehr Benutzer auswählen, werden die Eigenschaften, für die eine Massenbearbeitung möglich ist, im Detailbereich angezeigt. Wenn Sie eine dieser Eigenschaften ändern, wird die Änderungen auf alle ausgewählten Empfänger angewandt.

Bei der Massenbearbeitung von E-Mail-Benutzern können Sie die folgenden Eigenschaftenbereiche ändern:

  - **Kontaktinformationen**   Ändern Sie freigegebene Eigenschaften wie Straße, PLZ und Ort.

  - **Organisation**   Ändern Sie freigegebene Eigenschaften wie Abteilungsname, Firmenname und den Vorgesetzten, an den die ausgewählten E-Mail-Kontakte oder E-Mail-Benutzer berichten.

## Massenbearbeitung von E-Mail-Benutzern Verwenden mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Wählen Sie in der Liste der Kontakte mindestens zwei E-Mail-Benutzer aus. Für Kombinationen aus E-Mail-Kontakten und E-Mail-Benutzern ist keine Massenbearbeitung möglich.
    

    > [!TIP]
    > Sie können mehrere benachbarte E-Mail-Benutzer auswählen, indem Sie bei gedrückter UMSCHALTTASTE auf den ersten und anschließend auf den letzten E-Mail-Benutzer klicken, den Sie bearbeiten möchten. Sie können auch mehrere nicht benachbarte E-Mail-Benutzer auswählen, indem Sie bei gedrückter STRG-TASTE auf die Einträge klicken, die Sie bearbeiten möchten.



3.  Klicken Sie im Detailbereich unter **Massenbearbeitung** unter **Kontaktinformationen** oder **Organisation** auf **Aktualisieren**.

4.  Nehmen Sie die Änderungen auf der Eigenschaftenseite vor, und speichern Sie Ihre Änderungen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Massenbearbeitung von E-Mail-Benutzern zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole jeden der E-Mail-Benutzer aus, die in die Massenbearbeitung einbezogen waren, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaften anzuzeigen, die Sie geändert haben.

  - Verwenden Sie in der Shell das Cmdlet **Get-User**, um die Änderungen zu überprüfen. Beispiel: Sie haben das Massenbearbeitungsfeature der Exchange-Verwaltungskonsole verwendet, um den Vorgesetzten und die Büros aller E-Mail-Benutzer eines Lieferanten mit Namen A. Datum Corporation zu ändern. Sie können den folgenden Befehl in der Shell ausführen, um diese Änderungen zu überprüfen:
    
        Get-User -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'mailuser') -and (Company -eq 'Adatum')} | fl Name,Office,Manager

## Verwenden der Verzeichnissynchronisierung zum Verwalten von E-Mail-Benutzern in Exchange Online

In diesem Abschnitt finden Sie weitere Informationen zum Verwalten von E-Mail-Benutzern mithilfe der Verzeichnissynchronisierung in Exchange Online. Die Verzeichnissynchronisierung steht für Kunden mit einer Hybridbereitstellung (lokale und cloudgehostete Postfächer) sowie für vollständig gehostete Exchange Online-Kunden zur Verfügung, die über ein lokales Active Directory verfügen.


> [!NOTE]
> Wenn Sie Verzeichnissynchronisierung zur Verwaltung der Empfänger verwenden, können Sie Benutzer dennoch im Office 365 Admin Center hinzufügen und verwalten. Sie werden dann jedoch nicht mit dem lokalen Active Directory synchronisiert. Dies liegt daran, dass bei der Verzeichnissynchronisierung nur Empfänger aus dem lokalen Active Directory mit der Cloud synchronisiert werden.




> [!NOTE]
> Für die folgenden Funktionen wird empfohlen, Verzeichnissynchronisierung zu verwenden: 
> <UL>
> <LI>
> <P><STRONG>Outlook-Listen sicherer und blockierter Absender</STRONG> Wenn diese Listen mit dem Dienst synchronisiert werden, haben sie in diesem Dienst Vorrang vor der Spamfilterung. Dadurch können Benutzer ihre eigene Liste sicherer und blockierter Absender auf Benutzer- oder Domänenbasis verwalten.</P>
> <LI>
> <P><STRONG>Verzeichnisbasierte Edge-Blockierung</STRONG> Weitere Informationen zu verzeichnisbasierter Edge-Blockierung finden Sie unter <A href="https://technet.microsoft.com/de-de/library/dn600322(v=exchg.150)">Verwenden von verzeichnisbasierter Edge-Blockierung zum Ablehnen von Nachrichten, die an ungültige Empfänger gesendet wurden</A>.</P>
> <LI>
> <P><STRONG>Spam-Quarantäne von Endbenutzern</STRONG> Für den Zugriff auf die Spam-Quarantäne von Endbenutzern benötigen Endbenutzer eine gültige Office&nbsp;365-Benutzer-ID samt Kennwort. Kunden mit lokalen Postfächern müssen gültige E-Mail-Benutzer sein.</P>
> <LI>
> <P><STRONG>Transportregeln</STRONG> - Wenn Sie mit Verzeichnissynchronisierung arbeiten, werden Ihre vorhandenen Active Directory-Benutzer und -Gruppen automatisch in der Cloud aktualisiert, und Sie können Transportregeln erstellen, die für bestimmte Benutzer und/oder Gruppen gelten, ohne dass Sie sie über die EAC oder die remote Windows-PowerShell manuell hinzufügen müssen. Bitte beachten Sie, dass <A href="https://go.microsoft.com/fwlink/?linkid=507569">dynamische Verteilungsgruppen</A> nicht über die Verzeichnissynchronisierung synchronisiert werden können.</P></LI></UL>



**Bevor Sie beginnen**

Rufen Sie die erforderlichen Berechtigungen ab, und bereiten Sie die Verzeichnissynchronisierung vor, wie unter [Vorbereiten der Verzeichnissynchronisierung](https://go.microsoft.com/fwlink/p/?linkid=308908) beschrieben.

**So synchronisieren Sie Benutzerverzeichnisse**

1.  Aktivieren Sie die Verzeichnissynchronisierung, wie unter [Aktivieren der Verzeichnissynchronisierung](https://go.microsoft.com/fwlink/p/?linkid=308909) beschrieben.

2.  Richten Sie den Computer für die Verzeichnissynchronisierung ein, wie unter [Einrichten des Computers für die Verzeichnissynchronisierung](http://go.microsoft.com/fwlink/p/?linkid=308911) beschrieben.

3.  Synchronisieren Sie die Verzeichnisse, wie unter [Synchronisieren der Verzeichnisse mithilfe des Konfigurations-Assistenten](http://go.microsoft.com/fwlink/p/?linkid=308912) beschrieben.
    

    > [!IMPORTANT]
    > Wenn Sie den Konfigurationsassistent für Azure Active Directory-Synchronisierungstool abschließen, wird in Ihrer Active Directory-Gesamtstruktur das Konto <STRONG>MSOL_AD_SYNC</STRONG> erstellt. Dieses Konto wird zum Lesen und Synchronisieren der lokalen Active Directory-Informationen verwendet. Damit die Verzeichnissynchronisierung ordnungsgemäß ausgeführt wird, müssen Sie sicherstellen, dass TCP 443 auf dem lokalen Verzeichnissynchronisierungsserver geöffnet ist.



4.  Aktivieren Sie die synchronisierten Benutzer, wie unter [Aktivieren synchronisierter Benutzer](http://go.microsoft.com/fwlink/p/?linkid=308913) beschrieben.

5.  Verwalten Sie die Verzeichnissynchronisierung, wie unter [Verwalten der Verzeichnissynchronisierung](http://go.microsoft.com/fwlink/p/?linkid=308915) beschrieben.

6.  Überprüfen Sie, ob Exchange Online korrekt synchronisiert. Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Kontakte**, und vergewissern Sie sich, dass die Liste der Benutzer in Ihrer lokalen Umgebung korrekt synchronisiert wird.

