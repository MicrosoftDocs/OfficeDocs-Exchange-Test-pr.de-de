---
title: 'Verwalten von Benutzerpostfächern: Exchange 2013 Help'
TOCTitle: Verwalten von Benutzerpostfächern
ms:assetid: 957ca61c-1fa1-42ab-a0e6-8488e4782566
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123809(v=EXCHG.150)
ms:contentKeyID: 50476288
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.NewMailboxWizardForm.NewMailboxIntroductionWizardPage
ms.translationtype: HT
---

# Verwalten von Benutzerpostfächern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-05-27_

Nachdem Sie ein Benutzerpostfach erstellt haben, können Sie in der Exchange-Verwaltungskonsole oder Shell Änderungen vornehmen und zusätzliche Eigenschaften festlegen.

Sie können auch Eigenschaften für mehrere Benutzerpostfächer gleichzeitig ändern. Weitere Informationen finden Sie unter Massenbearbeitung von Benutzerpostfächern.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe für jedes Benutzerpostfach: 2 bis 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ändern von Eigenschaften des Benutzerpostfachs

## Ändern von Benutzerpostfacheigenschaften mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Postfacheigenschaften auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Postfachnutzung
    
      - Kontaktinformationen
    
      - Organization (Organisation)
    
      - E-Mail-Adresse
    
      - Postfachfeatures
    
      - Mitglied von
    
      - E-Mail-Info
    
      - Stellvertretung für Postfächer

## Allgemein

Klicken Sie auf den Abschnitt **Allgemein**, um grundlegende Informationen zum Benutzer anzuzeigen oder zu ändern.

  - **Vorname**, **Initialen**, **Nachname**

  - **\* Name**   Das ist der Name, der in Active Directory aufgelistet wird. Wenn Sie diesen Namen ändern, darf er nicht länger als 64 Zeichen sein.

  - **\* Anzeigename** Dieser Name wird im Adressbuch Ihrer Organisation angezeigt, in "An:" und "Von:" in E-Mails sowie in der Postfachliste angezeigt. Dieser Name darf keine Leerzeichen vor oder nach dem Anzeigenamen enthalten.

  - **\* Alias** gibt den E-Mail-Alias des Benutzers an. Der Benutzeralias ist der Teil links vom @-Symbol in der E-Mail-Adresse. Er muss innerhalb der Gesamtstruktur eindeutig sein.

  - **\* Benutzeranmeldename**   Dies ist der Name, den der Benutzer zur Anmeldung beim Postfach und zur Anmeldung bei der Domäne verwendet. Im Allgemeinen besteht der Benutzeranmeldename aus dem Benutzeralias links vom @-Symbol und dem Namen der Domäne, in der sich der Benutzer befindet, rechts vom @-Symbol.
    

    > [!NOTE]
    > In Exchange Online heißt dieses Feld <STRONG>Benutzer-ID</STRONG>



  - **Bei nächster Anmeldung Kennwortänderung anfordern**   Aktivieren Sie dieses Kontrollkästchen, wenn der Benutzer das Kennwort bei der nächsten Anmeldung am Postfach zurücksetzen soll.
    

    > [!NOTE]
    > Dieses Kontrollkästchen ist nicht in Exchange Online verfügbar.



  - **Aus Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass der Empfänger im Adressbuch und anderen Adresslisten angezeigt wird, die in Ihrer Exchange-Organisation definiert sind. Nachdem Sie das Kontrollkästchen aktiviert haben, können Benutzer weiterhin unter Verwendung der E-Mail-Adresse Nachrichten an den Empfänger senden.

Klicken Sie auf **Weitere Optionen**, um diese zusätzlichen Eigenschaften anzuzeigen oder zu ändern:

  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit an, die das Benutzerkonto enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um das Benutzerkonten in eine andere Organisationseinheit zu verschieben.
    

    > [!NOTE]
    > Dieses Feld ist nicht in Exchange Online verfügbar.



  - **Postfachdatenbank**   Dieses schreibgeschützte Feld zeigt den Namen der Postfachdatenbank an, in der das Archivpostfach gehostet wird. Wenn Sie das Postfach in eine andere Datenbank verschieben möchten, wählen Sie es in der Postfachliste aus, und klicken Sie im Detailbereich auf **In eine andere Datenbank verschieben**.
    

    > [!NOTE]
    > Diese Option ist nicht in Exchange Online verfügbar.



  - **Benutzerdefinierte Attribute**   In diesem Abschnitt werden die benutzerdefinierten Attribute angezeigt, die für das Benutzerpostfach definiert sind. Klicken Sie auf **Bearbeiten**, um Werte für benutzerdefinierte Attribute anzugeben. Bis zu 15 benutzerdefinierte Attribute für den Empfänger können definiert werden.

## Postfachnutzung

Verwenden Sie den Abschnitt **Postfachnutzung**, um das Postfachspeicherkontingent und die Aufbewahrungseinstellungen für gelöschte Elemente für das Benutzerpostfach anzuzeigen und zu ändern. Diese Einstellungen werden standardmäßig bei der Erstellung des Postfachs konfiguriert. Dabei werden die Werte verwendet, die für die Postfachdatenbank konfiguriert sind und für alle Postfächer in der Datenbank gelten. Sie können diese Einstellungen für jedes Postfach anpassen, anstatt die Standardwerte der Postfachdatenbank zu verwenden.

  - **Letzte Anmeldung**   Dieses schreibgeschützte Feld zeigt die Uhrzeit der letzten Benutzeranmeldung beim Postfach an.

  - **Postfachnutzung**   In diesem Bereich wird die Gesamtgröße des Postfachs und der Prozentsatz des gesamten Postfachkontingents angezeigt, die bzw. der verwendet wurde.


> [!NOTE]
> Die Exchange-Verwaltungskonsole fragt die Postfachdatenbank ab, in der das Postfach gehostet wird, um die in diesem Feld angezeigten Informationen abzurufen. Wenn die Exchange-Verwaltungskonsole nicht mit dem Exchange-Speicher kommunizieren kann, der die Postfachdatenbank enthält, sind diese Felder leer. Eine Warnmeldung wird angezeigt, wenn sich der Benutzer noch nicht erstmalig beim Postfach angemeldet hat.



Klicken Sie auf **Weitere Optionen**, um das Speicherkontingent des Postfachs und die Einstellungen für die Aufbewahrungszeit für gelöschte Elemente für dieses Postfach anzuzeigen.


> [!NOTE]
> In Exchange Online sind diese Einstellungen in der Exchange-Verwaltungskonsole nicht verfügbar.



  - **Speicherkontingenteinstellungen**   Wenn Sie nicht die Standardeinstellungen der Postfachdatenbank verwenden, sondern diese Einstellungen für das Postfach selbst konfigurieren möchten, klicken Sie auf **Einstellungen für dieses Postfach anpassen**, geben Sie einen neuen Wert ein, und klicken Sie auf **Speichern**.
    
    Der Wertebereich für alle Einstellungen für Speicherkontingente liegt zwischen 0 und 2047 GB.
    
      - **Warnmeldung senden ab (GB)**   In diesem Feld wird der maximale Speichergrenzwert angezeigt, der erreicht werden muss, damit eine Warnung an den Benutzer ausgegeben wird. Wenn die Größe des Postfachs den angegebenen Wert erreicht oder übersteigt, sendet Exchange eine Warnmeldung an den Benutzer.
    
      - **Senden verbieten ab (GB)**   In diesem Feld wird der Grenzwert angezeigt, ab dem das *Sendeverbot* für das Postfach gilt. Wenn die Größe des Postfachs den angegebenen Grenzwert erreicht oder übersteigt, hindert Exchange den Postfachbenutzer am Senden neuer Nachrichten und zeigt eine Fehlermeldung mit weiteren Informationen an.
    
      - **Senden/Empfangen verbieten ab (GB)**   In diesem Feld wird der Grenzwert angezeigt, ab dem das *Sende- und Empfangsverbot* für das Postfach gilt. Wenn die Größe des Postfachs den angegebenen Grenzwert erreicht oder übersteigt, hindert Exchange den Postfachbenutzer am Senden neuer Nachrichten und stellt keine neuen Nachrichten mehr an das Postfach zu. Alle an das Postfach gesendeten Nachrichten werden zusammen mit einer Fehlermeldung und weiteren Informationen an den Absender zurückgeschickt.

  - **Aufbewahrungseinstellungen für gelöschte Elemente**   Wenn Sie nicht die Standardeinstellungen der Postfachdatenbank verwenden, sondern diese Einstellungen für das Postfach selbst konfigurieren möchten, klicken Sie auf **Einstellungen für dieses Postfach anpassen**, geben Sie einen neuen Wert ein, und klicken Sie auf **Speichern**.
    
      - **Gelöschte Elemente aufbewahren für (Tage)**   In diesem Feld wird der Zeitraum angezeigt, den gelöschte Elemente aufbewahrt werden, bevor sie endgültig gelöscht werden und vom Benutzer nicht mehr wiederhergestellt werden können. Beim Erstellen des Postfachs basiert dieser Wert auf den Aufbewahrungseinstellungen für gelöschte Elemente, die für die Postfachdatenbank konfiguriert wurden. Standardmäßig ist eine Postfachdatenbank für eine Aufbewahrung gelöschter Elemente für 14 Tage konfiguriert. Der Wertebereich für diese Einstellung liegt zwischen 0 und 24855 Tagen.
    
      - **Elemente nicht endgültig löschen, bevor die Datenbank gesichert ist**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Postfächer und E-Mails gelöscht werden, bevor die Postfachdatenbank, in der sich das Postfach befindet, gesichert wurde.

## Kontaktinformationen

Verwenden Sie den Abschnitt **Kontaktinformationen**, um die Kontaktinformationen des Benutzers anzuzeigen oder zu ändern. Die Informationen auf dieser Seite werden im Adressbuch angezeigt. Klicken Sie auf **Weitere Optionen**, um zusätzliche Felder anzuzeigen.


> [!TIP]
> Sie können das Feld <STRONG>Bundesland/Kanton</STRONG> verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.



Postfachbenutzer können ihre eigenen Kontaktinformationen mit Outlook oder Outlook Web App anzeigen und ändern. Sie können jedoch nicht die Informationen in den Feldern **Notizen** und **Webseite** ändern.

## Organization (Organisation)

Verwenden Sie den Abschnitt **Organisation**, um ausführliche Informationen zur Rolle des Benutzers in der Organisation aufzuzeichnen. Diese Informationen werden im Adressbuch angezeigt. Sie können auch ein virtuelles Organisationsdiagramm erstellen, auf das von E-Mail-Clients wie Outlook zugegriffen werden kann.

  - **Titel**   In diesem Feld kann der Titel des Empfängers angezeigt oder geändert werden.

  - **Abteilung**   Verwenden Sie dieses Feld, um die Abteilung, in der der Benutzer tätig ist, anzuzeigen oder zu ändern. Sie können dieses Feld verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.

  - **Firma**   Verwenden Sie dieses Feld, um das Unternehmen, in dem der Benutzer tätig ist, anzuzeigen oder zu ändern. Sie können dieses Feld verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.

  - **Vorgesetzter**   Um einen Vorgesetzten hinzuzufügen, klicken Sie auf **Durchsuchen**. Wählen Sie im Dialogfeld **Vorgesetzten auswählen** eine Person aus, und klicken Sie dann auf **OK**.

  - **Direkte Mitarbeiter**   Dieses Feld kann nicht geändert werden. Ein *direkt unterstellter Mitarbeiter* ist ein Benutzer, der einem bestimmten Vorgesetzten unterstellt ist. Wenn Sie einen Vorgesetzten für den Benutzer angegeben haben, wird dieser Benutzer als direkt unterstellter Mitarbeiter in den Postfachdetails des Vorgesetzten angezeigt. Beispielsweise ist Kari die Vorgesetzte von Chris und Kate. Dann ist das Postfach von Kari im Feld **Vorgesetzter** der Postfächer von Chris und Kate angegeben, und Chris und Kate werden in den Eigenschaften des Postfachs von Kari im Feld **Direkte Mitarbeiter** angezeigt.

## E-Mail-Adresse

Im Abschnitt **E-Mail-Adresse** können Sie die E-Mail-Adressen anzeigen und ändern, die dem Benutzerpostfach zugeordnet sind. Dazu gehören die primäre SMTP-Adresse des Benutzers sowie alle zugeordneten Proxyadressen. Die primäre SMTP-Adresse (auch als *Standardantwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben.

  - **Hinzufügen **  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue E-Mail-Adresse für dieses Postfach hinzuzufügen. Wählen Sie einen der folgenden Adresstypen aus:
    
      - **SMTP**   Dies ist der Standardadresstyp. Klicken Sie auf diese Schaltfläche, und geben Sie dann die neue SMTP-Adresse in das Feld **\* E-Mail-Adresse** ein.
    
      - **EUM**   Eine EUM-Adresse (Exchange Unified Messaging) wird von Microsoft Exchange Unified Messaging-Servern verwendet, um UM-aktivierte Benutzer innerhalb einer Exchange-Organisation zu finden. EUM-Adressen enthalten eine Durchwahlnummer und einen UM-Wählplan für den UM-aktivierten Benutzer. Klicken Sie auf diese Schaltfläche, und geben Sie die Durchwahlnummer im Feld **Adresse/Durchwahl** ein. Klicken Sie dann auf **Durchsuchen**, und wählen Sie einen Wählplan für den Benutzer aus.
    
      - **Benutzerdefinierter Adresstyp**   Klicken Sie auf diese Schaltfläche, und geben Sie einen der unterstützten Nicht-SMTP-E-Mail-Adresstypen in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Mit Ausnahme von X.400-Adressen überprüft Exchange benutzerdefinierte Adressen nicht auf ordnungsgemäße Formatierung. Sie müssen sicherstellen, dass die von Ihnen angegebene benutzerdefinierte Adresse die Formatanforderungen für den jeweiligen Adresstyp erfüllt.

    
      - **Diese Adresse als Antwortadresse verwenden**    In Exchange Online können Sie dieses Kontrollkästchen aktivieren, um die neue E-Mail-Adresse als primäre SMTP-Adresse für dieses Postfach zu verwenden. Dieses Kontrollkästchen ist in Exchange 2013 nicht in der Exchange-Verwaltungskonsole verfügbar.

  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden. Diese Option ist standardmäßig aktiviert.
    

    > [!NOTE]
    > Dieses Kontrollkästchen ist nicht in Exchange Online verfügbar.



  - **Diese Adresse als Antwortadresse verwenden**

## Postfachfeatures

Im Abschnitt **Postfachfeatures** können Sie die folgenden Postfachfeatures und -einstellungen anzeigen oder ändern:

  - **Freigaberichtlinie**   Dieses Feld zeigt die Freigaberichtlinie, die auf das Postfach angewendet wird. Mithilfe einer Freigaberichtlinie können Sie steuern, wie Benutzer in Ihrer Organisation Kalender- und Kontaktinformationen mit Benutzern außerhalb Ihrer Exchange-Organisation gemeinsam nutzen können. Beim Erstellen von Postfächern wird diesen die Standardfreigaberichtlinie zugewiesen. Wenn Sie die dem Benutzer zugewiesene Freigaberichtlinie ändern möchten, wählen Sie eine andere Richtlinie aus der Dropdownliste aus.

  - **Rollenzuweisungsrichtlinie**   Dieses Feld zeigt die Rollenzuweisungsrichtlinie, die dem Postfach zugewiesen ist. Die Rollenzuweisungsrichtlinie gibt die Rollen für die rollenbasierte Remotezugriffssteuerung (Remote Role-Based Access Control, RBAC) an, die dem Benutzer zugewiesen sind, und steuert die Konfigurationseinstellungen für Postfach und Verteilergruppe, die der Benutzer ändern darf. Wenn Sie die dem Benutzer zugewiesene Rollenzuweisungsrichtlinie ändern möchten, wählen Sie eine andere Richtlinie aus der Dropdownliste aus.

  - **Aufbewahrungsrichtlinie**   Dieses Feld zeigt die Aufbewahrungsrichtlinie, die auf das Postfach angewendet wird. Eine Aufbewahrungsrichtlinie ist eine Gruppe von Aufbewahrungstags, die auf das Benutzerpostfach angewendet werden. Damit können Sie steuern, wie lange Elemente in den Postfächern von Benutzern aufbewahrt werden, und die Aktionen definieren, die beim Erreichen eines bestimmten Alters für Elemente ausgeführt werden. Beim Erstellen von Postfächern wird diesen keine Aufbewahrungsrichtlinie zugewiesen. Wählen Sie eine Richtlinie aus der Dropdownliste aus, um dem Benutzer eine Aufbewahrungsrichtlinie zuzuweisen.

  - **Adressbuchrichtlinie**   Dieses Feld zeigt die Adressbuchrichtlinie, die auf das Postfach angewendet wird. Mit einer Adressbuchrichtlinie können Sie Benutzer in bestimmte Gruppen unterteilen, um angepasste Ansichten des Adressbuchs bereitzustellen. Zum Anwenden oder Ändern der Adressbuchrichtlinie, die für das Postfach gilt, wählen Sie eine Richtlinie aus der Dropdownliste aus.

  - **Unified Messaging**   Diese Funktion ist standardmäßig deaktiviert. Wenn Sie Unified Messaging (UM) aktivieren, kann der Benutzer die UM-Funktionen Ihrer Organisation nutzen, und es wird ein Standardsatz UM-Eigenschaften auf den Benutzer angewendet. Klicken Sie auf **Aktivieren**, um UM für das Postfach zu aktivieren. Weitere Informationen zum Aktivieren von UM finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/enable-a-user-for-voice-mail).
    

    > [!NOTE]
    > Bevor Sie UM aktivieren können, müssen ein UM-Wählplan und eine UM-Postfachrichtlinie vorhanden sein.



  - **Mobile Geräte**   Verwenden Sie diesen Abschnitt, um Einstellungen für Exchange ActiveSync anzuzeigen und zu ändern. Exchange ActiveSync ist standardmäßig aktiviert. Exchange ActiveSync ermöglicht auf mobilen Geräten den Zugriff auf ein Exchange-Postfach. Klicken Sie auf **Exchange ActiveSync deaktivieren**, um diese Funktion für das Postfach zu deaktivieren.

  - **Outlook Web App**   Diese Funktion ist standardmäßig aktiviert. Mit Outlook Web App können Sie über einen Webbrowser auf Ihr Exchange-Postfach zugreifen. Klicken Sie auf **Deaktivieren**, um Outlook Web App für das Postfach zu deaktivieren. Klicken Sie auf **Details bearbeiten**, um eine Outlook Web App-Postfachrichtlinie für das Postfach hinzuzufügen oder zu ändern.

  - **IMAP**   Diese Funktion ist standardmäßig aktiviert. Klicken Sie auf **Deaktivieren**, um IMAP für das Postfach zu deaktivieren.

  - **POP3**   Diese Funktion ist standardmäßig aktiviert. Klicken Sie auf **Deaktivieren**, um POP3 für das Postfach zu deaktivieren.

  - **MAPI**   Diese Funktion ist standardmäßig aktiviert. MAPI ermöglicht den Zugriff auf ein Exchange-Postfach über einen MAPI-Client wie Outlook. Klicken Sie auf **Deaktivieren**, um MAPI für das Postfach zu deaktivieren.

  - **Beweissicherungsverfahren**   Diese Funktion ist standardmäßig deaktiviert. Durch das Beweissicherungsverfahren bleiben gelöschte Postfachelemente erhalten und werden Änderungen an Postfachelementen erfasst. Gelöschte Elemente und alle Instanzen geänderter Elemente werden in einer Discoverysuche zurückgegeben. Klicken Sie auf **Aktivieren**, um das Beweissicherungsverfahren für das Postfach zu aktivieren. Wenn für das Postfach das Beweissicherungsverfahren aktiviert wurde, klicken Sie auf **Deaktivieren**, um das Beweissicherungsverfahren zu deaktivieren. Dem Beweissicherungsverfahren unterliegende Postfächer sind inaktive Postfächer und können nicht gelöscht werden. Deaktivieren Sie zum Löschen des Postfachs das Beweissicherungsverfahren. Wenn für das Postfach das Beweissicherungsverfahren aktiviert wurde, klicken Sie auf **Details bearbeiten**, um die folgenden Einstellungen für das Beweissicherungsverfahren anzuzeigen und zu ändern:
    
      - **Aufbewahrungsdatum**   Dieses schreibgeschützte Feld gibt mit Datum und Uhrzeit an, wann das Beweissicherungsverfahren für das Postfach aktiviert wurde.
    
      - **In den Haltenmodus gesetzt von:**    Dieses schreibgeschützte Feld gibt den Benutzer an, der das Beweissicherungsverfahren für das Postfach aktiviert hat.
    
      - **Hinweis**   Informieren Sie den Benutzer mithilfe dieses Felds über das Beweissicherungsverfahren, erläutern Sie, warum das Beweissicherungsverfahren für das Postfach aktiviert wurde, oder geben Sie ausführlichere Informationen für den Benutzer an. Teilen Sie dem Benutzer beispielsweise mit, dass die Verwendung von E-Mails durch das Beweissicherungsverfahren nicht beeinträchtigt wird.
    
      - **URL**   Geben Sie in diesem Feld eine URL zu einer Website mit Informationen zum Beweissicherungsverfahren für das Postfach an.
        

        > [!NOTE]
        > Der Text in diesen Feldern wird im Postfach des Benutzers nur angezeigt, wenn dieser Outlook&nbsp;2010 oder höher verwendet. In Outlook Web App oder anderen E-Mail-Clients wird die URL nicht angezeigt. Klicken Sie zum Anzeigen des Texts aus den Feldern <STRONG>Hinweis</STRONG> und <STRONG>URL</STRONG> in Outlook&nbsp;auf die Registerkarte <STRONG>Datei</STRONG>, und navigieren Sie auf der Seite Info zu Kontoeinstellungen.



  - **Archivierung**   Wenn für den Benutzer kein Archivpostfach vorhanden ist, ist diese Funktion deaktiviert. Um ein Archivpostfach zu aktivieren, klicken Sie auf **Aktivieren**. Wenn der Benutzer über ein Archivpostfach verfügt, werden die Größe und die Verwendungsstatistik für das Archivpostfach angezeigt. Klicken Sie auf **Details bearbeiten**, um die folgenden Einstellungen für Archivpostfächer anzuzeigen und zu ändern:
    
      - **Status**   Dieses schreibgeschützte Feld gibt an, ob ein Archivpostfach vorhanden ist.
    
      - **Datenbank**   Dieses schreibgeschützte Feld zeigt den Namen der Postfachdatenbank, die das Archivpostfach hostet. Dieses Feld ist nicht in Exchange Online verfügbar.
    
      - **Name**   Geben Sie in diesem Feld den Namen des Archivpostfachs ein. Dieser Name wird in Outlook oder Outlook Web App unterhalb der Ordnerliste angezeigt.
    
      - **Archivkontingent (GB)**   Dieses Feld zeigt die Gesamtgröße des Archivpostfachs an. Geben Sie einen neuen Wert in das Feld ein, oder wählen Sie einen Wert aus der Dropdownliste, um die Größe zu ändern.
    
      - **Warnmeldung senden ab (GB)**   Dieses Feld zeigt die maximale Speicherbegrenzung für das Archivpostfach, bevor eine Warnung an den Benutzer ausgegeben wird. Wenn die Größe des Archivpostfachs den angegebenen Wert erreicht oder übersteigt, sendet Exchange eine Warnmeldung an den Benutzer. Geben Sie einen neuen Wert in das Feld ein, oder wählen Sie einen Wert aus der Dropdownliste, um die Begrenzung zu ändern.
        

        > [!NOTE]
        > In Exchange Online können Sie das Archivkontingent und das Kontingent für "Warnmeldung senden" für das Archivpostfach nicht ändern.



  - **Zustellungsoptionen**   Verwenden Sie dieses Feld, um an den Benutzer gesendete E-Mail-Nachrichten an einen anderen Empfänger weiterzuleiten, und um die maximale Anzahl von Empfängern festzulegen, an die der Benutzer eine Nachricht senden kann. Klicken Sie auf **Details anzeigen**, um diese Einstellungen anzuzeigen und zu ändern.
    
      - **Weiterleitungsadresse**   Aktivieren Sie das Kontrollkästchen **Weiterleitung aktivieren**, und klicken Sie dann auf **Durchsuchen**, um die Seite **E-Mail-Benutzer und Postfach auswählen** anzuzeigen. Auf dieser Seite können Sie einen Empfänger auswählen, an den Sie sämtliche E-Mail-Nachrichten weiterleiten möchten, die an dieses Postfach gesendet werden.
    
      - **Nachricht an Weiterleitungsadresse und Postfach zustellen**   Aktivieren Sie dieses Kontrollkästchen, damit Nachrichten sowohl an die Weiterleitungsadresse als auch das Postfach des Benutzers zugestellt werden.
    
      - **Empfängergrenzwert**   Diese Einstellung steuert die maximale Anzahl von Empfängern, denen der Benutzer eine Nachricht senden kann. Aktivieren Sie das Kontrollkästchen **Maximale Anzahl Empfänger**, um die Anzahl von Empfängern zu begrenzen, die in den Zeilen "An:", "Cc:" und "Bcc:" einer E-Mail zulässig sind, und geben Sie die maximale Anzahl von Empfängern an.
        

        > [!NOTE]
        > Für lokale Exchange-Organisationen ist die Empfängeranzahl unbegrenzt. Für Exchange Online-Organisationen ist die Anzahl auf 500&nbsp;Empfänger begrenzt.



  - **Größeneinschränkungen für Nachrichten**   Diese Einstellungen steuern die Größe von Nachrichten, die vom Benutzer gesendet und empfangen werden können. Klicken Sie auf **Details anzeigen**, um die maximale Größe von gesendeten und empfangenen Nachrichten anzuzeigen und zu ändern.
    

    > [!NOTE]
    > Diese Einstellungen können in Exchange Online nicht geändert werden.

    
      - **Gesendete Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer gesendete Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht sendet, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Benutzer zurückgesendet.
    
      - **Empfangene Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer empfangene Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht empfängt, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Absender zurückgesendet.

  - **Einschränkungen für die Nachrichtenzustellung**   Diese Einstellungen steuern, welche Personen E-Mails an diesen Benutzer senden können. Klicken Sie auf **Details anzeigen**, um diese Einschränkungen anzuzeigen und zu ändern.
    
      - **Nachrichten annehmen von**   Verwenden Sie diesen Abschnitt, um anzugeben, wer Nachrichten an diesen Benutzer senden kann.
        
          - **Alle Absender**   Wählen Sie diese Option, um festzulegen, dass der Empfänger Nachrichten von allen Absendern akzeptieren kann. Dies schließt sowohl Absender innerhalb der Exchange-Organisation als auch externe Absender ein. Diese Option ist standardmäßig ausgewählt. Diese Option schließt externe Benutzer nur ein, wenn Sie das Kontrollkästchen **Authentifizierung aller Absender anfordern** deaktivieren. Wenn Sie dieses Kontrollkästchen aktivieren, werden Nachrichten von externen Benutzern zurückgewiesen.
        
          - **Nur Absender aus der folgenden Liste**   Wählen Sie diese Option, um festzulegen, dass der Benutzer nur Nachrichten einer bestimmten Gruppe von Absendern in der Exchange-Organisation empfangen kann. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Seite **Empfänger auswählen** aufzurufen, die eine Liste aller Empfänger in Ihrer Exchange-Organisation anzeigt. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.
        
          - **Authentifizierung aller Absender anfordern**   Wählen Sie diese Option, um zu verhindern, dass anonyme Benutzer Nachrichten an den Benutzer senden können.
    
      - **Nachrichten ablehnen von**   Verwenden Sie diesen Abschnitt, um Benutzer daran zu hindern, Nachrichten an diesen Benutzer zu senden.
        
          - **Keinem Absender**   Wählen Sie diese Option, um festzulegen, dass das Postfach keine Nachrichten von Absendern in der Exchange-Organisation zurückweist. Diese Option ist standardmäßig ausgewählt.
        
          - **Absendern aus der folgenden Liste**   Wählen Sie diese Option, um festzulegen, dass das Postfach Nachrichten von einer bestimmten Gruppe von Absendern in der Exchange-Organisation zurückweist. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Seite **Empfänger auswählen** aufzurufen, die eine Liste aller Empfänger in Ihrer Exchange-Organisation anzeigt. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.

## Mitglied von

Im Abschnitt **Mitglied von** können Sie eine Liste der Verteiler- oder Sicherheitsgruppen anzeigen, denen dieser Benutzer angehört. Informationen zur Mitgliedschaft können auf dieser Seite nicht geändert werden. Beachten Sie, dass der Benutzer möglicherweise den Kriterien für mindestens eine dynamische Verteilergruppe in Ihrer Organisation entspricht. Dynamische Verteilergruppen werden auf dieser Seite jedoch nicht angezeigt, da ihre Mitgliedschaft zum Zeitpunkt ihrer Verwendung stets neu berechnet wird.

## E-Mail-Info

Verwenden Sie den Abschnitt **E-Mail-Info**, um eine E-Mail-Info hinzuzufügen, mit der Benutzer auf potenzielle Probleme beim Senden einer Nachricht an diesen Empfänger hingewiesen werden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn dieser Empfänger dem Feld "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Stellvertretung für Postfächer

Verwenden Sie den Abschnitt **Stellvertretung für Postfächer**, um es anderen Benutzern (einer *Stellvertretung*) zu ermöglichen, sich im Namen eines Benutzers am Benutzerpostfach anzumelden oder Nachrichten zu senden. Sie können die folgenden Berechtigungen zuweisen:

  - **Senden als**   Diese Berechtigung ermöglicht es Benutzern, bei denen es sich nicht um den Postfachbesitzer handelt, das Postfach zum Senden von Nachrichten zu verwenden. Nachdem diese Berechtigung einer Stellvertretung zugewiesen wurde, werden alle Nachrichten, die eine Stellvertretung von diesem Postfach sendet, so angezeigt, als würden sie vom Postfachbesitzer gesendet. Diese Berechtigung ermöglicht es einer Stellvertretung jedoch nicht, sich am Benutzerpostfach anzumelden.

  - **Senden im Auftrag von**   Diese Berechtigung ermöglicht es einer Stellvertretung ebenfalls, das Postfach zum Senden von Nachrichten zu verwenden. Nachdem diese Berechtigung einer Stellvertretung zugewiesen wurde, zeigt die Zeile **Von:**  in allen von der Stellvertretung gesendeten Nachrichten an, dass die Nachricht im Auftrag des Postfachbesitzers von der Stellvertretung gesendet wurde.

  - **Vollzugriff**   Diese Berechtigung ermöglicht es einer Stellvertretung, sich am Postfach des Benutzers anzumelden und die Inhalte des Postfachs anzuzeigen. Nach der Zuweisung dieser Berechtigung kann die Stellvertretung jedoch keine Nachrichten von diesem Postfach aus senden. Wenn Sie einer Stellvertretung das Senden von E-Mails aus dem Benutzerpostfach erlauben möchten, müssen Sie der Stellvertretung die Berechtigung "Senden als" oder die Berechtigung "Senden im Auftrag von" zuweisen.

Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen** ![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Seite anzuzeigen, auf der eine Liste mit allen Empfängern in der Exchange-Organisation angezeigt wird, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.

## Ändern der Eigenschaften von Benutzerpostfächern mithilfe der Shell

Verwenden Sie die Cmdlets **Get-Mailbox** und **Set-Mailbox**, um Eigenschaften für Benutzerpostfächer anzuzeigen und zu ändern. Ein Vorteil der Shell liegt darin, dass Sie die Eigenschaften für mehrere Benutzerpoostfächer ändern können. Informationen dazu, welche Parameter den Postfacheigenschaften entsprechen, finden Sie in diesen Themen:

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

Im Folgenden finden Sie einige Beispiele, wie Sie Eigenschaften von Benutzerpostfächern mithilfe der Shell ändern können.

In diesem Beispiel wird gezeigt, wie die E-Mails für Pat Coleman an das Postfach von Sunil Koduri (sunilk@contoso.com) weitergeleitet werden können.

    Set-Mailbox -Identity patc -DeliverToMailboxAndForward $true -ForwardingAddress sunilk@contoso.com

In diesem Beispiel wird der Befehl **Get-Mailbox** verwendet, um alle Benutzerpostfächer in der Organisation zu finden, und dann wird mit dem Befehl **Set-Mailbox** der Empfängergrenzwert auf 500 zulässige Empfänger in den Zeilen "An:", "Cc:" und "Bcc:" einer E-Mail-Nachricht festgelegt.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -RecipientLimits 500

In diesem Beispiel wird mithilfe des Befehls **Get-Mailbox** nach allen Postfächern in der Organisationseinheit "Marketing" gesucht. Anschließend werden diese Postfächer mit dem Befehl **Set-Mailbox** konfiguriert. Die Grenzwerte für benutzerdefinierte Warnungen, Sendeverbote sowie Sende- und Empfangsverbote werden entsprechend auf 200 MB, 250 MB und 280 MB festgelegt. Die Standardgrenzwerte der Postfachdatenbank werden ignoriert. Mit diesem Befehl können Sie für eine bestimmte Gruppe von Postfächern höhere oder niedrigere Grenzwerte als für andere Postfächer in der Organisation festlegen.

    Get-Mailbox -OrganizationalUnit "Marketing" | Set-Mailbox -IssueWarningQuota 209715200 -ProhibitSendQuota 262144000 -ProhibitSendReceiveQuota 293601280 -UseDatabaseQuotaDefaults $false 

In diesem Beispiel werden mit dem Cmdlet **Get-Mailbox** alle Benutzer in der Kundendienstabteilung gesucht. Anschließend wird mit dem Cmdlet **Set-Mailbox** die maximale Nachrichtengröße für das Senden von Nachrichten auf 2 MB festgelegt.

    Get-Mailbox -Filter "Department -eq 'Customer Service'" | Set-Mailbox -MaxSendSize 2097152

In diesem Beispiel wird QuickInfo-Übersetzung auf Französisch und Chinesisch eingestellt.

    Set-Mailbox john@contoso.com -MailTipTranslations ("FR: C'est la langue française", "CHT: 這是漢語語言")

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Eigenschaften eines Benutzerpostfachs erfolgreich geändert wurden:

  - Wählen Sie in der Exchange-Verwaltungskonsole das Postfach aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder Funktion anzuzeigen, die Sie geändert haben. In Abhängigkeit von der geänderten Eigenschaft wird diese möglicherweise im Detailbereich für das ausgewählte Postfach angezeigt.

  - In der Shell verwenden Sie das Cmdlet **Get-Mailbox**, um die Änderungen zu überprüfen. Ein Vorteil der Shell liegt darin, dass Sie mehrere Eigenschaften für mehrere Postfächer anzeigen können. Führen Sie im oben stehenden Beispiel, in dem die Empfängergrenzwert geändert wurde, folgenden Befehl aus, um den neuen Wert zu überprüfen.
    
        Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | fl Name,RecipientLimits
    
    Führen Sie diesen Befehl für das vorherige Beispiel aus, in dem die Nachrichtengrenzwerte geändert wurden.
    
        Get-Mailbox -OrganizationalUnit "Marketing" | fl Name,IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults

## Massenbearbeitung von Benutzerpostfächern

Sie können mithilfe der Exchange-Verwaltungskonsole die Eigenschaften mehrerer Benutzerpostfächer ändern. Wenn Sie in der Exchange-Verwaltungskonsole mindestens zwei Benutzerpostfächer aus der Postfachliste auswählen, werden die Eigenschaften im Detailbereich angezeigt, die per Massenbearbeitung geändert werden können. Wenn Sie eine dieser Eigenschaften ändern, wird die Änderungen auf alle ausgewählten Postfächer angewendet.

Es folgt eine Liste der Eigenschaften und Funktionen von Benutzerpostfächern, für die eine Massenbearbeitung möglich ist. Beachten Sie, dass nicht alle Eigenschaften in jedem Bereich geändert werden können.

  - **Kontaktinformationen**   Ändern Sie freigegebene Eigenschaften wie Straße, PLZ und Ort.

  - **Organisation**   Ändern Sie freigegebene Eigenschaften wie Abteilungsname, Firmenname und den Vorgesetzten, an den die ausgewählten Benutzer berichten.

  - **Benutzerdefinierte Attribute**   Ändern Sie Werte für benutzerdefinierte Attribute 1–15, oder fügen Sie sie hinzu.

  - **Postfachkontingent**   Ändern Sie die Werte für Postfachkontingente und den Aufbewahrungszeitraum für gelöschte Elemente. Dieses Feld ist nicht in Exchange Online verfügbar.

  - **E-Mail-Konnektivität**   Aktivieren oder deaktivieren Sie Outlook Web App, POP3, IMAP, MAPI und Exchange ActiveSync.

  - **Archiv**   Aktivieren oder deaktivieren Sie das Archivpostfach.

  - **Aufbewahrungsrichtlinie, Rollenzuweisungsrichtlinie und Freigaberichtlinie**   Aktualisieren Sie die Einstellungen für jede dieser Postfachfunktionen.

  - **In eine andere Datenbank verschieben**   Verschieben Sie die ausgewählten Postfächer in eine andere Datenbank.

  - **Stellvertretungsberechtigungen**   Weisen Sie Benutzern oder Gruppen Berechtigungen zu, die diesen das Öffnen und Senden von Nachrichten aus anderen Postfächern erlauben. Sie können Benutzern und Gruppen die Berechtigungen "Vollständig", "Senden als" und "Senden im Auftrag von" zuweisen. Weitere Informationen finden Sie unter [Verwalten von Berechtigungen für Empfänger](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-permissions-for-recipients).


> [!NOTE]
> Die geschätzte Zeit bis zum Abschließen dieser Aufgabe sind 2&nbsp;Minuten, aber dies kann länger dauern, wenn Sie mehrere Eigenschaften oder Funktionen ändern.



## Massenbearbeitung von Benutzerpostfächern mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Liste der Postfächer mindestens zwei Postfächer aus.
    

    > [!TIP]
    > Sie können mehrere benachbarte Postfächer auswählen, indem Sie bei gedrückter UMSCHALTTASTE auf das erste und anschließend auf das letzte zu bearbeitende Postfach klicken. Sie können auch mehrere nicht benachbarte Postfächer auswählen, indem Sie bei gedrückter STRG-TASTE auf die gewünschten Postfächer klicken.



3.  Wählen Sie im Detailbereich unter **Massenbearbeitung** die Postfacheigenschaften oder -funktion aus, die Sie bearbeiten möchten.

4.  Nehmen Sie die Änderungen auf der Eigenschaftenseite vor, und speichern Sie Ihre Änderungen.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Massenbearbeitung von Benutzerpostfächern zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole jedes bearbeitete Postfach aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder Funktion anzuzeigen, die Sie geändert haben.

  - In der Exchange-Verwaltungsshell verwenden Sie das Cmdlet **Get-Mailbox**, um die Änderungen zu überprüfen. Ein Vorteil der Shell liegt darin, dass Sie mehrere Eigenschaften für mehrere Postfächer anzeigen können. Nehmen Sie beispielsweise an, Sie haben in der Exchange-Verwaltungskonsole mit der Massenbearbeitungsfunktion das Archivpostfach aktiviert und allen Benutzern in Ihrer Organisation eine Aufbewahrungsrichtlinie zugewiesen. Sie können den folgenden Befehl ausführen, um diese Änderungen zu überprüfen:
    
        Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | fl Name,ArchiveDatabase,RetentionPolicy
    
    Weitere Informationen zu den verfügbaren Parametern für das Cmdlet **Get-Mailbox** finden Sie unter [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

