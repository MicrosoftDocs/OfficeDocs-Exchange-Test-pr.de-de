---
title: 'Verwalten verknüpfter Postfächer: Exchange 2013 Help'
TOCTitle: Verwalten verknüpfter Postfächer
ms:assetid: 76e12d4a-1c3a-42e2-b64c-c09d36e81bd3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673532(v=EXCHG.150)
ms:contentKeyID: 50475971
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten verknüpfter Postfächer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-27_

Verknüpfte Postfächer sind Postfächer, auf die Benutzer in einer getrennten, vertrauenswürdigen Gesamtstruktur zugreifen. Verknüpfte Postfächer sind ggf. für Organisationen erforderlich, die Exchange in einer Ressourcengesamtstruktur bereitstellen. Mit dem Szenario für Ressourcengesamtstrukturen kann eine Organisation Exchange in einer Einzelgesamtstruktur zentralisieren und dabei den Zugriff auf die Exchange-Organisation mit Benutzerkonten in mindestens einer vertrauenswürdigen Gesamtstruktur (einer sogenannten *Kontogesamtstruktur*) zur Verfügung stellen. Das Benutzerpostfach, das auf das verknüpfte Postfach zugreift, ist nicht in der Gesamtstruktur vorhanden, in der Exchange bereitgestellt wird. Aus diesem Grund wird ein deaktiviertes Benutzerkonto, das in der gleichen Gesamtstruktur wie Exchange vorhanden ist, erstellt und jedem verknüpften Postfach zugeordnet.

Die folgende Abbildung zeigt die Beziehung zwischen dem verknüpften Benutzerkonto, das für den Zugriff auf das verknüpfte Postfach (in der Kontogesamtstruktur) verwendet wird, und dem deaktivierten Benutzerkonto in der Exchange-Ressourcengesamtstruktur, das dem verknüpften Postfach zugeordnet ist.

**Verknüpfte Postfächer**

![Komplexe Exchange-Organisation mit Ressourcengesamtstruktur](images/Aa998031.706725cf-e520-4b89-a275-acd8fb58943a(EXCHG.150).gif "Komplexe Exchange-Organisation mit Ressourcengesamtstruktur")


> [!NOTE]
> Vor dem Erstellen von verknüpften Postfächern muss eine Vertrauensstellung zwischen der Exchange-Gesamtstruktur und mindestens einer Kontogesamtstruktur eingerichtet werden. Es ist mindestens eine unidirektionale, ausgehende Vertrauensstellung erforderlich, damit die Exchange-Gesamtstruktur der Kontogesamtstruktur vertraut. Weitere Informationen finden Sie unter <A href="https://technet.microsoft.com/de-de/library/jj156983(v=exchg.150)">Weitere Informationen zum Einrichten einer Gesamtstruktur-Vertrauensstellung zur Unterstützung von verknüpften Postfächern</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 bis 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - In der Kontogesamtstruktur muss ein Benutzerkonto (das sogenannte *verknüpfte Hauptkonto*) vorhanden sein, bevor Sie ein verknüpftes Hauptkonto erstellen können. Der Grund dafür ist, dass das verknüpfte Hauptkonto einem Benutzer in der Kontogesamtstruktur zugeordnet ist.

  - Wenn Sie eine unidirektionale, ausgehende Vertrauensstellung erstellt haben, in der die Exchange-Gesamtstruktur der Kontogesamtstruktur vertraut, benötigen Sie Administratoranmeldeinformationen in der Kontogesamtstruktur, um ein verknüpftes Postfach zu erstellen.
    
    Sie müssen eine bidirektionale Vertrauensstellung oder eine weitere ausgehende unidirektionale Vertrauensstellung erstellen, in der die Kontogesamtstrukur auch der Exchange-Gesamtstruktur vertraut, um ein verknüpftes Postfach zu erstellen, ohne zur Eingabe der Administratoranmeldeinformationen in der Kontogesamtstruktur aufgefordert zu werden. Dieser Schritt erfordert auch Administratoranmeldeinformationen in der Kontogesamtstruktur.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines verknüpften Postfachs

## Erstellen eines verknüpften Postfachs mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Klicken Sie auf **Neu** \> **Verknüpftes Postfach**.

3.  Wählen Sie auf der Seite **Neues verknüpftes Postfach** im Feld **Vertrauenswürdige Gesamtstruktur oder Domäne** den Namen der Kontogesamtstruktur aus, die das Benutzerkonto enthält, für das Sie das verknüpfte Postfach erstellen möchten. Klicken Sie dann auf **Weiter**.

4.  Wenn in Ihrer Organisation eine unidirektionale, ausgehende Vertrauensstellung konfiguriert ist, in der die Exchange-Gesamtstruktur der Kontogesamtstruktur vertraut, werden Sie aufgefordert, Administratoranmeldeinformationen in der Kontogesamtstruktur einzugeben, um auf einen Domänencontroller in der vertrauenswürdigen Gesamtstruktur zuzugreifen. Geben Sie den Benutzernamen und das Kennwort für ein Administratorkonto in der Kontogesamtstruktur ein, und klicken Sie auf **Weiter**.
    

    > [!NOTE]
    > Wenn Sie eine bidirektionale Vertrauensstellung oder eine weitere unidirektionale, ausgehende Vertrauensstellung erstellt haben, in der die Kontogesamtstruktur der Exchange-Gesamtstruktur vertraut, werden Sie nicht zur Eingabe von Administratoranmeldeinformationen aufgefordert.



5.  Füllen Sie auf der Seite **Verknüpftes Hauptkonto auswählen** die folgenden Felder aus.
    
      - **Verknüpfte Domänencontroller** Wählen Sie einen Domänencontroller in der Kontogesamtstruktur aus. Exchange stellt eine Verbindung mit diesem Domänencontroller her, um die Liste der Benutzerkonten in der Kontogesamtstruktur abzurufen, sodass Sie das verknüpfte Hauptkonto auswählen können.
    
      - **Verknüpftes Hauptkonto**   Klicken Sie auf **Durchsuchen**, wählen Sie ein Benutzerkonto in der Kontogesamtstruktur aus, und klicken Sie auf **OK**. Das neue verknüpfte Postfach wird diesem Konto zugeordnet.

6.  Klicken Sie auf **Weiter**, und füllen Sie auf der Seite **Allgemeine Informationen eingeben** die folgenden Felder aus.
    
      - **\* Name**   Geben Sie in diesem Feld einen Namen für den Benutzer ein. Hierbei handelt es sich um den Namen, der als Anzeigename in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation verwendet und in Active Directory aufgeführt wird. Dieser Name ist erforderlich.
    
      - **Organisationseinheit**   Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container "Benutzer" in der Active Directory-Domäne festgelegt, in der sich der Computer befindet, auf dem die Exchange-Verwaltungskonsole ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container Benutzer ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten in der Exchange-Gesamtstruktur angezeigt, die sich im angegebenen Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie dann auf **OK**.
    
      - **\* Benutzeranmeldename**   Geben Sie in diesem Feld den Benutzeranmeldenamen ein, der zum Erstellen eines verknüpften Postfachs erforderlich ist. Geben Sie hier den Benutzernamen ein. Dieser Name wird im linken Teil der E-Mail-Adresse für das verknüpfte Postfach verwendet, wenn Sie keinen Alias angeben.
        

        > [!NOTE]
        > Da das Benutzerkonto, das in der Exchange-Gesamtstruktur erstellt wurde, beim Erstellen eines verknüpften Postfachs deaktiviert wird, verwendet der Benutzer nicht den Benutzeranmeldenamen, um sich beim verknüpften Postfach anzumelden. Der Benutzer verwendet stattdessen die Anmeldeinformationen aus der Kontogesamtstruktur.



7.  Klicken Sie auf **Weitere Optionen**, um die folgenden Felder zu konfigurieren. Fahren Sie andernfalls mit Schritt 8 fort, um das neue verknüpfte Postfach zu speichern.
    
      - **Alias**   Geben Sie einen Alias ein, der als E-Mail-Alias für das verknüpfte Postfach verwendet werden soll. Der Benutzeralias ist der Teil links vom @-Symbol in der E-Mail-Adresse. Er muss innerhalb der Gesamtstruktur eindeutig sein.
        

        > [!NOTE]
        > Wenn Sie dieses Feld leer lassen, wird der Wert des Benutzernamens im <STRONG>Benutzeranmeldenamen</STRONG> als E-Mail-Alias verwendet.

    
      - **Vorname**, **Initialen**, **Nachname**
    
      - **Postfachdatenbank**   Verwenden Sie diese Option, um selbst eine Postfachdatenbank anzugeben, anstatt Exchange die Auswahl einer Datenbank zu überlassen. Klicken Sie auf **Durchsuchen**, um das Dialogfeld **Postfachdatenbank auswählen** zu öffnen. In diesem Dialogfeld werden alle Postfachdatenbanken in Ihrer Exchange-Organisation aufgelistet. Standardmäßig werden die Postfachdatenbanken nach dem Namen sortiert. Sie können auch auf den Titel der entsprechenden Spalte klicken, um die Datenbanken nach Servernamen oder Version zu sortieren. Wählen Sie die gewünschte Postfachdatenbank aus, und klicken Sie dann auf **OK**.
    
      - **Adressbuchrichtlinie**   Verwenden Sie diese Option, um eine Adressbuchrichtlinie für das verknüpfte Postfach anzugeben. Adressbuchrichtlinien enthalten eine globale Adressbuchline (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine Gruppe von Adresslisten. Wenn Postfachbenutzern eine Adressbuchrichtlinie zugewiesen ist, stellt diese den Benutzern Zugriff auf eine benutzerdefinierte GAL in Outlook und Outlook Web App bereit. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).
        
        Wählen Sie in der Dropdownliste die Richtlinie aus, die diesem Postfach zugeordnet werden soll.

8.  Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um das neue verknüpfte Postfach zu erstellen.

## Erstellen eines verknüpften Postfachs mithilfe der Shell

In diese Beispiel wird ein verknüpftes Postfach für Ayla Kol in der Exchange-Ressourcengesamtstruktur CONTOSO erstellt. Die Domäne FABRIKAM befindet sich in der Kontogesamtstruktur. Das Administratorkonto "FABRIKAM \\administrator" wird für den Zugriff auf den verknüpften Domänencontroller verwendet.

    New-Mailbox -Name "Ayla Kol" -LinkedDomainController "DC1_FABRIKAM" -LinkedMasterAccount " FABRIKAM\aylak" -OrganizationalUnit Users -UserPrincipalName aylak@contoso.com -LinkedCredential:(Get-Credential FABRIKAM\administrator)

Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines verknüpften Postfachs zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**. Das neue verknüpfte Postfach wird in der Postfachliste angezeigt. Unter **Postfachtyp** lautet der Typ **Verknüpft**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen verknüpften Postfach anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,RecipientTypeDetails,IsLinked,LinkedMasterAccount

## Ändern der Eigenschaften eines verknüpften Postfachs

Nachdem Sie ein verknüpftes Postfach erstellt haben, können Sie dieses über die Exchange-Verwaltungskonsole oder die Exchange-Verwaltungsshell ändern oder zusätzliche Eigenschaften konfigurieren.

Sie können auch Eigenschaften für mehrere verknüpfte Postfächer gleichzeitig ändern. Weitere Informationen finden Sie im Abschnitt "Massenbearbeitung von Benutzerpostfächern" im Thema [Verwalten von Benutzerpostfächern](manage-user-mailboxes-exchange-2013-help.md).


> [!IMPORTANT]
> Die geschätzte Zeit bis zum Abschließen des Vorgangs variiert je nach der Anzahl von Eigenschaften, die Sie anzeigen oder ändern möchten.



## Ändern von Eigenschaften verknüpfter Postfächer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Klicken Sie in der Liste der Postfächer auf das verknüpfte Postfach, dessen Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Postfacheigenschaften auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Postfachnutzung
    
      - E-Mail-Adresse
    
      - Postfachfeatures
    
      - Mitglied von
    
      - E-Mail-Info
    
      - Stellvertretung für Postfächer

## Allgemein

Klicken Sie auf den Abschnitt **Allgemein**, um grundlegende Informationen zum Benutzer anzuzeigen oder zu ändern.

  - **\* Name des verknüpften Postfachs**   Dies ist der Name, der in Active Directory aufgelistet wird. Wenn Sie diesen Namen ändern, darf er nicht länger als 64 Zeichen sein.

  - **\* Anzeigename**   Dieser Name wird im Adressbuch Ihrer Organisation angezeigt, in den Zeilen "An:" und "Von:" in E-Mails sowie in der Postfachliste in der Exchange-Verwaltungskonsole. Dieser Name darf keine Leerzeichen vor oder nach dem Anzeigenamen enthalten.

  - **\* Benutzeranmeldename**   Bei Benutzerpostfächern ist dies der Name, den der Benutzer zur Anmeldung beim Postfach und zur Anmeldung bei der Domäne verwendet. Bei verknüpften Postfächern wird das entsprechende Benutzerpostfach, das beim Erstellen des verknüpften Postfachs in der Exchange-Gesamtstruktur erstellt wurde, deaktiviert. Der Benutzer verwendet die Anmeldeinformationen aus der Kontogesamtstruktur, um sich beim verknüpften Postfach anzumelden.
    
    Wenn Sie diesen Namen ändern, beachten Sie, dass er in der Organisation eindeutig sein muss.

  - **Verknüpftes Hauptkonto**   Dieses schreibgeschützte Feld zeigt den Benutzer (im Format "Domäne\\Benutzername") aus der Kontogesamtstruktur, der dem verknüpften Postfach zugeordnet ist. Zum Ändern des verknüpften Hauptkontos, das dem verknüpften Postfach zugeordnet ist, müssen Sie das Cmdlet **Set-Mailbox** in der Shell verwenden. Wenn Sie das verknüpfte Hauptkonto ändern, müssen Benutzer die Anmeldeinformationen für das neue verknüpfte Hauptkonto verwenden, um sich beim verknüpften Postfach anzumelden. Die Befehlssyntax zum Ändern des verknüpften Hauptkontos finden Sie unter Ändern von Eigenschaften verknüpfter Postfächer mithilfe der Shell.

  - **Aus Adresslisten ausblenden** Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass das verknüpfte Postfach im Adressbuch und anderen Adresslisten angezeigt wird, die in Ihrer Exchange-Organisation definiert sind. Nachdem Sie das Kontrollkästchen aktiviert haben, können Benutzer weiterhin unter Verwendung der E-Mail-Adresse Nachrichten an diesen Benutzer senden.

Klicken Sie auf **Weitere Optionen**, um diese zusätzlichen Eigenschaften anzuzeigen oder zu ändern:

  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit an, die das Benutzerkonto enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um das Benutzerkonten in eine andere Organisationseinheit zu verschieben.

  - **Postfachdatenbank**   Dieses schreibgeschützte Feld zeigt den Namen der Postfachdatenbank an, in der das Archivpostfach gehostet wird. Wenn Sie das Postfach in eine andere Datenbank verschieben möchten, wählen Sie es in der Postfachliste aus, und klicken Sie im Detailbereich auf **In eine andere Datenbank verschieben**.

  - **\* Alias** Dies gibt den E-Mail-Alias für das verknüpfte Postfach an. Der Alias ist der Teil links vom @-Symbol in der E-Mail-Adresse. Er muss innerhalb der Gesamtstruktur eindeutig sein.

  - **Vorname**, **Initialen**, **Nachname**

  - **Benutzerdefinierte Attribute**   In diesem Abschnitt werden die benutzerdefinierten Attribute angezeigt, die für das verknüpfte Postfach definiert sind. Klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um benutzerdefinierte Attributwerte anzugeben. Bis zu 15 benutzerdefinierte Attribute für den Empfänger können definiert werden.

## Postfachnutzung

Verwenden Sie den Abschnitt **Postfachnutzung**, um das Postfachspeicherkontingent und die Aufbewahrungseinstellungen für gelöschte Elemente für das verknüpfte Postfach anzuzeigen und zu ändern. Diese Einstellungen werden standardmäßig bei der Erstellung des verknüpften Postfachs konfiguriert. Dabei werden die Werte verwendet, die für die Postfachdatenbank konfiguriert sind und für alle Postfächer in der Datenbank gelten. Sie können diese Einstellungen für jedes Postfach anpassen, anstatt die Standardwerte der Postfachdatenbank zu verwenden.

  - **Letzte Anmeldung**   Dieses schreibgeschützte Feld zeigt die Uhrzeit der letzten Benutzeranmeldung beim Postfach an.

  - **Postfachnutzung**   In diesem Bereich wird die Gesamtgröße des Postfachs und der Prozentsatz des gesamten Postfachkontingents angezeigt, die bzw. der verwendet wurde.


> [!NOTE]
> Die Exchange-Verwaltungskonsole fragt die Postfachdatenbank ab, in der das Postfach gehostet wird, um die in diesem Feld angezeigten Informationen abzurufen. Wenn die Exchange-Verwaltungskonsole nicht mit dem Exchange-Speicher kommunizieren kann, der die Postfachdatenbank enthält, sind diese Felder leer. Eine Warnmeldung wird angezeigt, wenn sich der Benutzer noch nicht erstmalig beim Postfach angemeldet hat.



Klicken Sie auf **Weitere Optionen**, um das Speicherkontingent des Postfachs und die Einstellungen für die Aufbewahrungszeit für gelöschte Elemente für dieses Postfach anzuzeigen.

  - **Speicherkontingenteinstellungen**   Wenn Sie nicht die Standardeinstellungen der Postfachdatenbank verwenden, sondern diese Einstellungen für das Postfach selbst konfigurieren möchten, klicken Sie auf **Einstellungen für dieses Postfach anpassen**, geben Sie einen neuen Wert ein, und klicken Sie auf **Speichern**.
    
    Der Wertebereich für alle Einstellungen für Speicherkontingente liegt zwischen 0 und 2047 GB.
    
      - **Warnmeldung senden ab (GB)**   In diesem Feld wird der maximale Speichergrenzwert angezeigt, der erreicht werden muss, damit eine Warnung an den Benutzer ausgegeben wird. Wenn die Größe des Postfachs den angegebenen Wert erreicht oder übersteigt, sendet Exchange eine Warnmeldung an den Benutzer.
    
      - **Senden verbieten ab (GB)**   In diesem Feld wird der Grenzwert angezeigt, ab dem das *Sendeverbot* für das Postfach gilt. Wenn die Größe des Postfachs den angegebenen Grenzwert erreicht oder übersteigt, hindert Exchange den Postfachbenutzer am Senden neuer Nachrichten und zeigt eine Fehlermeldung mit weiteren Informationen an.
    
      - **Senden/Empfangen verbieten ab (GB)**   In diesem Feld wird der Grenzwert angezeigt, ab dem das *Sende- und Empfangsverbot* für das Postfach gilt. Wenn die Größe des Postfachs den angegebenen Grenzwert erreicht oder übersteigt, hindert Exchange den Postfachbenutzer am Senden neuer Nachrichten und stellt keine neuen Nachrichten mehr an das Postfach zu. Alle an das Postfach gesendeten Nachrichten werden zusammen mit einer Fehlermeldung und weiteren Informationen an den Absender zurückgeschickt.

  - **Aufbewahrungseinstellungen für gelöschte Elemente**   Wenn Sie nicht die Standardeinstellungen der Postfachdatenbank verwenden, sondern diese Einstellungen für das Postfach selbst konfigurieren möchten, klicken Sie auf **Einstellungen für dieses Postfach anpassen**, geben Sie einen neuen Wert ein, und klicken Sie auf **Speichern**.
    
      - **Gelöschte Elemente aufbewahren für (Tage)**   In diesem Feld wird der Zeitraum angezeigt, den gelöschte Elemente aufbewahrt werden, bevor sie endgültig gelöscht werden und vom Benutzer nicht mehr wiederhergestellt werden können. Beim Erstellen des Postfachs basiert dieser Zeitraum auf den Aufbewahrungseinstellungen für gelöschte Elemente, die für die Postfachdatenbank konfiguriert wurden. Standardmäßig ist eine Postfachdatenbank für eine Aufbewahrung gelöschter Elemente für 14 Tage konfiguriert. Der Wertebereich für diese Einstellung liegt zwischen 0 und 24855 Tagen.
    
      - **Elemente nicht endgültig löschen, bevor die Datenbank gesichert ist**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass Postfächer und E-Mails gelöscht werden, bevor die Postfachdatenbank, in der sich das Postfach befindet, gesichert wurde.

## E-Mail-Adresse

Im Abschnitt **E-Mail-Adresse** können Sie die E-Mail-Adressen anzeigen und ändern, die dem verknüpften Postfach zugeordnet sind. Dazu gehören die primären SMTP-Adressen des Benutzers sowie alle zugeordneten Proxyadressen. Die primäre SMTP-Adresse (auch als *Standardantwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben.

  - **Hinzufügen **  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue E-Mail-Adresse für dieses Postfach hinzuzufügen. Wählen Sie einen der folgenden Adresstypen aus:
    
      - **SMTP**   Dies ist der Standardadresstyp. Klicken Sie auf dieses Optionsfeld, und geben Sie die neue SMTP-Adresse im Feld **\* E-Mail-Adresse** ein.
    
      - **EUM**   Eine EUM-Adresse (Exchange Unified Messaging) wird von Microsoft Exchange Unified Messaging-Servern verwendet, um UM-aktivierte Benutzer innerhalb einer Exchange-Organisation zu finden. EUM-Adressen enthalten eine Durchwahlnummer und einen UM-Wählplan für den UM-aktivierten Benutzer. Klicken Sie auf dieses Optionsfeld, und geben Sie die Durchwahlnummer im Feld **Adresse/Durchwahl** ein. Klicken Sie dann auf **Durchsuchen**, und wählen Sie einen Wählplan für den Benutzer aus.
    
      - **Benutzerdefinierter Adresstyp**   Klicken Sie auf diese Schaltfläche, und geben Sie einen der unterstützten Nicht-SMTP-E-Mail-Adresstypen in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Mit Ausnahme von X.400-Adressen überprüft Exchange benutzerdefinierte Adressen nicht auf ordnungsgemäße Formatierung. Sie müssen sicherstellen, dass die von Ihnen angegebene benutzerdefinierte Adresse die Formatanforderungen für den jeweiligen Adresstyp erfüllt.



  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden. Diese Option ist standardmäßig aktiviert.

## Postfachfeatures

Im Abschnitt **Postfachfeatures** können Sie die folgenden Postfachfeatures und -einstellungen anzeigen oder ändern:

  - **Freigaberichtlinie**   Dieses Feld zeigt die Freigaberichtlinie, die auf das Postfach angewendet wird. Mithilfe einer Freigaberichtlinie können Sie steuern, wie Benutzer in Ihrer Organisation Kalender- und Kontaktinformationen mit Benutzern außerhalb Ihrer Exchange-Organisation gemeinsam nutzen können. Beim Erstellen von Postfächern wird diesen die Standardfreigaberichtlinie zugewiesen. Wenn Sie die dem Benutzer zugewiesene Freigaberichtlinie ändern möchten, wählen Sie eine andere Richtlinie aus der Dropdownliste aus.

  - **Rollenzuweisungsrichtlinie**   Dieses Feld zeigt die Rollenzuweisungsrichtlinie, die dem Postfach zugewiesen ist. Die Rollenzuweisungsrichtlinie gibt die Rollen für die rollenbasierte Remotezugriffssteuerung (Remote Role-Based Access Control, RBAC) an, die dem Benutzer zugewiesen sind, und steuert die Konfigurationseinstellungen für Postfach und Verteilergruppe, die der Benutzer ändern darf. Wenn Sie die dem Benutzer zugewiesene Rollenzuweisungsrichtlinie ändern möchten, wählen Sie eine andere Richtlinie aus der Dropdownliste aus.

  - **Aufbewahrungsrichtlinie**   Dieses Feld zeigt die Aufbewahrungsrichtlinie, die auf das Postfach angewendet wird. Eine Aufbewahrungsrichtlinie ist eine Gruppe von Aufbewahrungstags, die auf das Benutzerpostfach angewendet werden. Mit Tags können Sie steuern, wie lange Elemente in den Postfächern von Benutzern aufbewahrt werden, und die Aktionen definieren, die beim Erreichen eines bestimmten Alters für Elemente ausgeführt werden. Beim Erstellen von Postfächern wird diesen keine Aufbewahrungsrichtlinie zugewiesen. Wählen Sie eine Richtlinie aus der Dropdownliste aus, um dem Benutzer eine Aufbewahrungsrichtlinie zuzuweisen.

  - **Adressbuchrichtlinie**   Dieses Feld zeigt die Adressbuchrichtlinie, die auf das Postfach angewendet wird. Mit einer Adressbuchrichtlinie können Sie Benutzer in bestimmte Gruppen unterteilen, um angepasste Ansichten des Adressbuchs bereitzustellen. Zum Anwenden oder Ändern der Adressbuchrichtlinie, die für das Postfach gilt, wählen Sie eine Richtlinie aus der Dropdownliste aus.

  - **Unified Messaging**   Diese Funktion ist standardmäßig deaktiviert. Wenn Sie Unified Messaging (UM) aktivieren, kann der Benutzer die UM-Funktionen Ihrer Organisation nutzen, und es wird ein Standardsatz UM-Eigenschaften auf den Benutzer angewendet. Klicken Sie auf **Aktivieren**, um UM für das Postfach zu aktivieren. Weitere Informationen zum Aktivieren von UM finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).
    

    > [!NOTE]
    > Bevor Sie UM aktivieren können, müssen ein UM-Wählplan und eine UM-Postfachrichtlinie vorhanden sein.



  - **Mobile Geräte**   Verwenden Sie diesen Abschnitt, um Einstellungen für Exchange ActiveSync anzuzeigen und zu ändern. Exchange ActiveSync ist standardmäßig aktiviert. Exchange ActiveSync ermöglicht auf mobilen Geräten den Zugriff auf ein Exchange-Postfach. Klicken Sie auf **Exchange ActiveSync deaktivieren**, um diese Funktion für das Postfach zu deaktivieren.

  - **Outlook Web App**   Diese Funktion ist standardmäßig aktiviert. Outlook Web App bietet Zugriff auf ein Exchange-Postfach über einen Webbrowser. Klicken Sie auf **Deaktivieren**, um Outlook Web App für das Postfach zu deaktivieren. Klicken Sie auf **Details bearbeiten**, um eine Outlook Web App-Postfachrichtlinie für das Postfach hinzuzufügen oder zu ändern.

  - **IMAP**   Diese Funktion ist standardmäßig aktiviert. Klicken Sie auf **Deaktivieren**, um IMAP für das Postfach zu deaktivieren.

  - **POP3**   Diese Funktion ist standardmäßig aktiviert. Klicken Sie auf **Deaktivieren**, um POP3 für das Postfach zu deaktivieren.

  - **MAPI**   Diese Funktion ist standardmäßig aktiviert. MAPI ermöglicht den Zugriff auf ein Exchange-Postfach über einen MAPI-Client wie Outlook. Klicken Sie auf **Deaktivieren**, um MAPI für das Postfach zu deaktivieren.

  - **Beweissicherungsverfahren**   Diese Funktion ist standardmäßig deaktiviert. Durch das Beweissicherungsverfahren bleiben gelöschte Postfachelemente erhalten und werden Änderungen an Postfachelementen erfasst. Gelöschte Elemente und alle Instanzen geänderter Elemente werden in einer Discoverysuche zurückgegeben. Klicken Sie auf **Aktivieren**, um das Beweissicherungsverfahren für das Postfach zu aktivieren. Wenn für das Postfach das Beweissicherungsverfahren aktiviert wurde, klicken Sie auf **Deaktivieren**, um das Beweissicherungsverfahren zu deaktivieren. Wenn für das Postfach das Beweissicherungsverfahren aktiviert wurde, klicken Sie auf **Details bearbeiten**, um die folgenden Einstellungen für das Beweissicherungsverfahren anzuzeigen und zu ändern:
    
      - **Aufbewahrungsdatum**   Dieses schreibgeschützte Feld gibt mit Datum und Uhrzeit an, wann das Beweissicherungsverfahren für das Postfach aktiviert wurde.
    
      - **In den Haltenmodus gesetzt von:**    Dieses schreibgeschützte Feld gibt den Benutzer an, der das Beweissicherungsverfahren für das Postfach aktiviert hat.
    
      - **Hinweis**   Informieren Sie den Benutzer mithilfe dieses Felds über das Beweissicherungsverfahren, erläutern Sie, warum das Beweissicherungsverfahren für das Postfach aktiviert wurde, oder geben Sie ausführlichere Informationen für den Benutzer an. Teilen Sie dem Benutzer beispielsweise mit, dass die Verwendung von E-Mails durch das Beweissicherungsverfahren nicht beeinträchtigt wird.
    
      - **URL**   Geben Sie in diesem Feld eine URL zu einer Website mit Informationen zum Beweissicherungsverfahren für das Postfach an.
        

        > [!NOTE]
        > Der Text in diesen Feldern wird im Postfach des Benutzers nur angezeigt, wenn dieser Outlook&nbsp;2010 oder höher verwendet. In Outlook Web App oder anderen E-Mail-Clients wird die URL nicht angezeigt. Klicken Sie zum Anzeigen des Texts aus den Feldern Hinweis und URL in Outlook&nbsp;auf die Registerkarte <STRONG>Datei</STRONG>, und navigieren Sie auf der Seite <STRONG>Info</STRONG> zu <STRONG>Kontoeinstellungen</STRONG>.



  - **Archivierung**   Wenn für den Benutzer kein Archivpostfach vorhanden ist, ist diese Funktion deaktiviert. Klicken Sie auf **Aktivieren**, um ein Archivpostfach zu aktivieren. Wenn der Benutzer über ein Archivpostfach verfügt, werden die Größe und die Verwendungsstatistik für das Archivpostfach angezeigt. Klicken Sie auf **Details bearbeiten**, um die folgenden Einstellungen für Archivpostfächer anzuzeigen und zu ändern:
    
      - **Status**   Dieses schreibgeschützte Feld gibt an, ob ein Archivpostfach vorhanden ist.
    
      - **Datenbank**   Dieses schreibgeschützte Feld zeigt den Namen der Postfachdatenbank, die das Archivpostfach hostet.
    
      - **Name**   Geben Sie in diesem Feld den Namen des Archivpostfachs ein. Dieser Name wird in Outlook oder Outlook Web App unterhalb der Ordnerliste angezeigt.
    
      - **Kontingentbedarf**   Dieser schreibgeschützte Bereich zeigt die Gesamtgröße des Archivpostfachs und den Prozentsatz am Gesamtkontingent für das Archivpostfach an, der belegt wurde.
    
      - **Kontingentwert (GB)**   Dieses Feld zeigt die Gesamtgröße des Archivpostfachs an. Geben Sie einen neuen Wert in das Feld ein, oder wählen Sie einen Wert aus der Dropdownliste, um die Größe zu ändern.
    
      - **Warnmeldung senden ab (GB)**   Dieses Feld zeigt die maximale Speicherbegrenzung für das Archivpostfach, bevor eine Warnung an den Benutzer ausgegeben wird. Wenn die Größe des Archivpostfachs den angegebenen Wert erreicht oder übersteigt, sendet Exchange eine Warnmeldung an den Benutzer. Geben Sie einen neuen Wert in das Feld ein, oder wählen Sie einen Wert aus der Dropdownliste, um die Begrenzung zu ändern.

  - **Zustellungsoptionen**   Verwenden Sie Zustellungsoptionen, um an den Benutzer gesendete E-Mail-Nachrichten an einen anderen Empfänger weiterzuleiten, und um die maximale Anzahl von Empfängern festzulegen, an die der Benutzer eine Nachricht senden kann. Klicken Sie auf **Details bearbeiten**, um diese Einstellungen anzuzeigen und zu ändern.
    
      - **Weiterleitungsadresse**   Aktivieren Sie das Kontrollkästchen **Weiterleitung aktivieren**, und klicken Sie dann auf **Durchsuchen**, um die Seite **E-Mail-Benutzer und Postfach auswählen** anzuzeigen. Auf dieser Seite können Sie einen Empfänger auswählen, an den Sie sämtliche E-Mail-Nachrichten weiterleiten möchten, die an dieses Postfach gesendet werden. Nachrichten werden sowohl an das verknüpfte Postfach als auch an die Weiterleitungsadresse gesendet.
    
      - **Empfängergrenzwert**   Diese Einstellung steuert die maximale Anzahl von Empfängern, denen der Benutzer eine Nachricht senden kann. Aktivieren Sie das Kontrollkästchen **Maximale Anzahl Empfänger**, um die Anzahl von Empfängern zu begrenzen, die in den Zeilen "An:", "Cc:" und "Bcc:" einer E-Mail zulässig sind, und geben Sie die maximale Anzahl von Empfängern an.
        

        > [!NOTE]
        > Für lokale Exchange-Organisationen ist die Empfängeranzahl unbegrenzt. Für Exchange Online-Organisationen ist die Anzahl auf 500&nbsp;Empfänger begrenzt.



  - **Größeneinschränkungen für Nachrichten**   Diese Einstellungen steuern die Größe von Nachrichten, die vom Benutzer gesendet und empfangen werden können. Klicken Sie auf **Details bearbeiten**, um die maximale Größe von gesendeten und empfangenen Nachrichten anzuzeigen und zu ändern.
    
      - **Gesendete Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer gesendete Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht sendet, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Benutzer zurückgesendet.
    
      - **Empfangene Nachrichten**   Aktivieren Sie das Kontrollkästchen **Maximale Nachrichtengröße (KB)**, und geben Sie einen Wert in das Feld ein, um eine maximale Größe für von diesem Benutzer empfangene Nachrichten festzulegen. Die Nachrichtengröße muss zwischen 0 und 2.097.151 KB liegen. Wenn der Benutzer eine Nachricht empfängt, die die angegebene Größe überschreitet, wird die Nachricht mit einer beschreibenden Fehlermeldung an den Absender zurückgesendet.

  - **Einschränkungen für die Nachrichtenzustellung**   Diese Einstellungen steuern, welche Personen E-Mails an diesen Benutzer senden können. Klicken Sie auf **Details bearbeiten**, um diese Einschränkungen anzuzeigen und zu ändern.
    
      - **Nachrichten annehmen von**   Verwenden Sie diesen Abschnitt, um anzugeben, wer Nachrichten an diesen Benutzer senden kann.
        
          - **Alle Absender**   Wählen Sie diese Option, um festzulegen, dass der Empfänger Nachrichten von allen Absendern akzeptieren kann. Dies schließt sowohl Absender innerhalb der Exchange-Organisation als auch externe Absender ein. Diese Option ist standardmäßig ausgewählt. Diese Option schließt externe Benutzer nur ein, wenn Sie das Kontrollkästchen **Authentifizierung aller Absender anfordern** deaktivieren. Wenn Sie dieses Kontrollkästchen aktivieren, werden Nachrichten von externen Benutzern zurückgewiesen.
        
          - **Nur Absender aus der folgenden Liste**   Wählen Sie diese Option, um festzulegen, dass der Benutzer nur Nachrichten einer bestimmten Gruppe von Absendern in der Exchange-Organisation empfangen kann. Klicken Sie auf **Hinzufügen**, um die Seite **Empfänger auswählen** aufzurufen, die eine Liste aller Empfänger in Ihrer Exchange-Organisation anzeigt. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie seinen Namen in das Suchfeld eingeben und dann auf **Suchen** klicken.
        
          - **Authentifizierung aller Absender anfordern**   Wählen Sie diese Option, um zu verhindern, dass anonyme Benutzer Nachrichten an den Benutzer senden können.
    
      - **Nachrichten ablehnen von**   Verwenden Sie diesen Abschnitt, um Benutzer daran zu hindern, Nachrichten an diesen Benutzer zu senden.
        
          - **Keinem Absender**   Wählen Sie diese Option, um festzulegen, dass das Postfach keine Nachrichten von Absendern in der Exchange-Organisation zurückweist. Diese Option ist standardmäßig ausgewählt.
        
          - **Absendern aus der folgenden Liste**   Wählen Sie diese Option, um festzulegen, dass das Postfach Nachrichten von einer bestimmten Gruppe von Absendern in der Exchange-Organisation zurückweist. Klicken Sie auf **Hinzufügen**, um die Seite **Empfänger auswählen** aufzurufen, die eine Liste aller Empfänger in Ihrer Exchange-Organisation anzeigt. Wählen Sie die Empfänger aus, deren Nachrichten zurückgewiesen werden sollen, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie seinen Namen in das Suchfeld eingeben und dann auf **Suchen** klicken.

## Mitglied von

Im Abschnitt **Mitglied von** können Sie eine Liste der Verteiler- oder Sicherheitsgruppen anzeigen, denen dieser Benutzer angehört. Informationen zur Mitgliedschaft können auf dieser Seite nicht geändert werden. Beachten Sie, dass der Benutzer möglicherweise den Kriterien für mindestens eine dynamische Verteilergruppe in Ihrer Organisation entspricht. Dynamische Verteilergruppen werden auf dieser Seite jedoch nicht angezeigt, da ihre Mitgliedschaft zum Zeitpunkt ihrer Verwendung stets neu berechnet wird.

## E-Mail-Info

Verwenden Sie den Abschnitt **E-Mail-Info**, um eine E-Mail-Info hinzuzufügen, mit der Benutzer auf potenzielle Probleme beim Senden einer Nachricht an diesen Empfänger hingewiesen werden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn dieser Empfänger den Zeilen "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Stellvertretung für Postfächer

Verwenden Sie den Abschnitt **Stellvertretung für Postfächer**, um es anderen Benutzern (einer *Stellvertretung*) zu ermöglichen, sich im Namen eines Benutzers am Benutzerpostfach anzumelden oder Nachrichten zu senden. Sie können die folgenden Berechtigungen zuweisen:

  - **Senden als**   Diese Berechtigung ermöglicht es Benutzern, bei denen es sich nicht um den Postfachbesitzer handelt, das Postfach zum Senden von Nachrichten zu verwenden. Nachdem diese Berechtigung einer Stellvertretung zugewiesen wurde, werden alle Nachrichten, die eine Stellvertretung von diesem Postfach sendet, so angezeigt, als würden sie vom Postfachbesitzer gesendet. Diese Berechtigung ermöglicht es einer Stellvertretung jedoch nicht, sich am Benutzerpostfach anzumelden.

  - **Senden im Auftrag von**   Diese Berechtigung ermöglicht es einer Stellvertretung ebenfalls, das Postfach zum Senden von Nachrichten zu verwenden. Nachdem diese Berechtigung einer Stellvertretung zugewiesen wurde, zeigt die Zeile **Von:**  in allen von der Stellvertretung gesendeten Nachrichten an, dass die Nachricht im Auftrag des Postfachbesitzers von der Stellvertretung gesendet wurde.

  - **Vollzugriff**   Diese Berechtigung ermöglicht es einer Stellvertretung, sich am Postfach des Benutzers anzumelden und die Inhalte des Postfachs anzuzeigen. Nach der Zuweisung dieser Berechtigung kann die Stellvertretung jedoch keine Nachrichten von diesem Postfach aus senden. Wenn Sie einer Stellvertretung das Senden von E-Mails aus dem Benutzerpostfach erlauben möchten, müssen Sie der Stellvertretung die Berechtigung Senden als oder die Berechtigung Senden im Auftrag von zuweisen.

Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen**, um die Seite **Empfänger auswählen** anzuzeigen, auf der eine Liste mit allen Empfängern in der Exchange-Organisation angezeigt wird, denen die Berechtigung zugewiesen werden kann. Wählen Sie die Empfänger aus, denen Sie Stellvertretungsberechtigungen zuweisen möchten, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie seinen Namen in das Suchfeld eingeben und dann auf **Suchen** klicken.

## Ändern von Eigenschaften verknüpfter Postfächer mithilfe der Shell

Verwenden Sie die Cmdlets **Get-Mailbox** und **Set-Mailbox**, um Eigenschaften für verknüpfte Postfächer anzuzeigen und zu ändern. Ein Vorteil der Shell liegt darin, dass Sie die Eigenschaften für mehrere verknüpfte Postfächer ändern können. Informationen dazu, welche Parameter den Postfacheigenschaften entsprechen, finden Sie in diesen Themen:

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

Im Folgenden finden Sie einige Beispiele, wie Sie Eigenschaften von verknüpften Postfächern mithilfe der Shell ändern können.

In diesem Beispiel wird der Befehl **Get-Mailbox** verwendet, um alle verknüpften Postfächer in der Organisation zu finden.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'LinkedMailbox')}

In diesem Beispiel wird der Befehl **Set-Mailbox** verwendet, um die Anzahl von Empfängern in den Zeilen "An:", "Cc:" und "Bcc:" einer E-Mail auf 500 zu begrenzen. Diese Beschränkung gilt für alle verknüpften Postfächer in der Organisation.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'LinkedMailbox')} | Set-Mailbox -RecipientLimits 500

In diesem Beispiel wird das verknüpfte Hauptkonto in der Kontogesamtstruktur "fabrikam.com" geändert, das einem verknüpften Postfach in einer Exchange-Gesamtstruktur zugeordnet ist.

    Set-Mailbox -Identity "Ayla Kol" -LinkedDomainController DC1.fabrikam.com -LinkedMasterAccount "fabrikam\robinw" -LinkedCredential:(Get-Credential fabrikam\administrator)

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Eigenschaften eines verknüpften Postfachs erfolgreich geändert wurden:

  - Wählen Sie in der Exchange-Verwaltungskonsole das verknüpfte Postfach aus, und klicken Sie auf **Bearbeiten**, um die Eigenschaft oder Funktion anzuzeigen, die Sie geändert haben. In Abhängigkeit von der geänderten Eigenschaft wird diese möglicherweise im Detailbereich für das ausgewählte Postfach angezeigt.

  - In der Shell verwenden Sie das Cmdlet **Get-Mailbox**, um die Änderungen zu überprüfen. Ein Vorteil der Shell liegt darin, dass Sie mehrere Eigenschaften für mehrere verknüpfte Postfächer anzeigen können. Im oben stehenden Beispiel, in dem die Empfängergrenzwert geändert wurde, können Sie den neuen Wert mit folgenden Befehl überprüfen:
    
        Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'LinkedMailbox')} | fl Name,RecipientLimits
    
    Im oben stehenden Beispiel, in dem das verknüpfte Hauptkonto geändert wurde, können Sie den neuen Wert mit folgenden Befehl überprüfen.
    
        Get-Mailbox "Ayla Kol" | fl LinkedMasterAccount

