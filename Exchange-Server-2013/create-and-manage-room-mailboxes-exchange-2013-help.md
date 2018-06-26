---
title: 'Erstellen und Verwalten von Raumpostfächern: Exchange 2013 Help'
TOCTitle: Erstellen und Verwalten von Raumpostfächern
ms:assetid: f70752ad-fce0-4e14-8428-fc5ac63f6c54
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ215781(v=EXCHG.150)
ms:contentKeyID: 50474857
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen und Verwalten von Raumpostfächern

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2017-02-02_

Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

Ein Raumpostfach ist ein Ressourcenpostfach, das einem physischen Standort, z. B. einem Konferenzraum, einem Hörsaal oder einem Schulungsraum, zugeordnet ist. Nachdem ein Administrator Raumpostfächer erstellt hat, können die Benutzer auf einfache Weise Räume reservieren, indem sie Raumpostfächer in Besprechungsanfragen aufnehmen. Weitere Details finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

Weitere Informationen zu anderen Ressourcenpostfachtypen finden Sie unter [Verwalten von Gerätepostfächern](manage-equipment-mailboxes-exchange-2013-help.md).

## Was möchten Sie machen?

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).


> [!IMPORTANT]
> Wenn Sie Exchange 2013 in einem Hybridszenario verwenden, müssen Sie sicherstellen, dass Sie die Raumpostfächer am richtigen Ort erstellen. Erstellen Sie Raumpostfächer für Ihre Organisation im lokalen Netzwerk und Raumpostfächer für Exchange Online in der Cloud.




## Erstellen eines Raumpostfachs

## Verwenden der Exchange-Verwaltungskonsole zum Erstellen eines Raumpostfachs

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Ressourcen**.

2.  Zum Erstellen eines Raumpostfachs klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") \> **Raumpostfach**

3.  Verwenden Sie die Optionen auf der Seite, um die Einstellungen für das neue Ressourcenpostfach festzulegen.
    
      - **\* Raumname**   Geben Sie in diesem Feld einen Namen für das Raumpostfach ein. Dies ist der Name, der in der Ressourcenpostfachliste in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation aufgeführt ist. Dieser Name ist erforderlich und darf höchstens 64 Zeichen umfassen.
        

        > [!TIP]
        > Zwar enthalten auch andere Felder Details zum Raum (beispielsweise "Ort" und "Kapazität"), es empfiehlt sich jedoch, die wichtigsten Details unter Verwendung einer konsistenten Benennungskonvention im Raumnamen zusammenzufassen. Der Grund: Benutzer erhalten so auf einfache Weise Informationen zu dem Raum, wenn sie ihn in der Besprechungsanfrage aus dem Adressbuch auswählen.

    
      - **\* E-Mail-Adresse**   Ein Raumpostfach hat eine E-Mail-Adresse, damit Buchungsanfragen empfangen werden können. Die E-Mail-Adresse besteht aus einem Alias vor dem @-Symbol, der in der Gesamtstruktur eindeutig sein muss, und dem Namen Ihrer Domäne hinter dem Symbol. Die E-Mail-Adresse ist erforderlich.
    
      - **Ort**, **Telefon**, **Kapazität**   Diese Felder dienen zum Eingeben von Raumdetails. Wie bereits erwähnt, können Sie diese Informationen auch in den Raumnamen integrieren, um sie den Benutzern zur Verfügung zu stellen.

4.  Wenn Sie alle Felder ausgefüllt haben, klicken Sie auf **Speichern**, um das Raumpostfach zu erstellen.

Nachdem Sie Ihr Gerätepostfach erstellt haben, können Sie Ihr Gerätepostfach so ändern, dass es Informationen zu Buchungsoptionen, E-Mails und Stellvertretern aktualisiert. Lesen Sie den unten aufgeführten Abschnitt zur Exchange-Verwaltungskonsole, wenn Sie Raumpostfacheigenschaften ändern möchten.

## Verwenden Sie der Exchange PowerShell zum Erstellen eines Raumpostfachs

In diesem Beispiel wird ein Raumpostfach mit der folgenden Konfiguration erstellt:

  - Das Raumpostfach befindet sich in der Postfachdatenbank "Mailbox Database 1".

  - Der Postfachname lautet "ConfRoom1". Dieser Name wird auch für die E-Mail-Adresse des Raums verwendet.

  - Der Anzeigename in der Exchange-Verwaltungskonsole und im Adressbuch lautet "Besprechungsraum 1".

  - Die Option *Room* gibt an, dass dieses Postfach als Raumpostfach erstellt wird.

<!-- end list -->

    New-Mailbox -Database "Mailbox Database 1" -Name ConfRoom1 - -DisplayName "Conference Room 1" -Room

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie haben mehrere Möglichkeiten, sich zu vergewissern, dass das Raumpostfach ordnungsgemäß erstellt wurde:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Ressourcen**. Das neue Raumpostfach wird in der Postfachliste angezeigt. Unter **Postfachtyp** lautet der Typ **Raum**.

  - Führen Sie in der Exchange PowerShell den folgenden Befehl aus, um Informationen über das neue Raumpostfach anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress

## Erstellen einer Raumliste

Wenn Sie mehr als 100 Räume planen oder bereits mehr als 100 Räume erstellt haben, sollten Sie eine Raumliste erstellen, um die Räume zu verwalten. Wenn Ihr Unternehmen über mehrere Gebäude mit Räumen verfügt, die für Besprechungen gebucht werden können, können Sie Raumbelegungspläne für jedes Gebäude erstellen. Raumbelegungspläne sind speziell markierte Verteilungsgruppen, die Sie auf dieselbe Weise wie Verteilungsgruppen verwenden können. Sie können Raumbelegungspläne allerdings nur mit der Exchange-Verwaltungsshell erstellen.

## Verwenden der Exchange PowerShell zum Erstellen einer Raumliste

In diesem Beispiel erstellen wir eine Raumliste für Gebäude 32.

    New-DistributionGroup -Name "Building 32 Conference Rooms" -OrganizationalUnit "contoso.com/rooms" -RoomList

## Verwenden der Exchange PowerShell zum Hinzufügen eines Raumes zu einer Raumliste

In diesem Beispiel fügen wir confroom3223 zur Raumliste von Gebäude 32 hinzu.

    Add-DistributionGroupMember -Identity "Building 32 Conference Rooms" -Member confroom3223@contoso.com

## Verwenden der Exchange PowerShell zum Konvertieren eine Verteilergruppe in eine Raumliste

Sie haben möglicherweise bereits in der Vergangenheit Verteilergruppen erstellt, in denen Ihre Konferenzräume enthalten sind. Sie müssen sie nicht neu erstellen. Wir können sie schnell in eine Raumliste konvertieren.

In diesem Beispiel konvertieren wir die Verteilergruppe für die Konferenzräume von Gebäude 34 in eine Raumliste.

    Set-DistributionGroup -Identity "Building 34 Conference Rooms" -RoomList

## Ändern von Raumpostfacheigenschaften

Nachdem Sie ein Raumpostfach erstellt haben, können Sie in der Exchange-Verwaltungskonsole oder der Exchange PowerShell Änderungen vornehmen und zusätzliche Eigenschaften festlegen.

## Verwenden der Exchange-Verwaltungskonsole zum Ändern von Raumpostfacheigenschaften

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Ressourcen**.

2.  Klicken Sie in der Liste mit den Ressourcenpostfächern auf das Raumpostfach, dessen Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Raumpostfacheigenschaften auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Stellvertretungen
    
      - Buchungsoptionen
    
      - Kontaktinformationen
    
      - E-Mail-Adresse
    
      - E-Mail-Info

## Allgemein

Verwenden Sie den Abschnitt **Allgemein**, um grundlegende Informationen zur Ressource anzuzeigen oder zu ändern.

  - **\* Raumname**   Dieser Name wird in der Ressourcenpostfachliste in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation angezeigt. Der Name darf höchstens 64 Zeichen umfassen, wenn Sie ihn ändern.

  - **\* E-Mail-Adresse**   Dieses schreibgeschützte Feld zeigt die E-Mail-Adresse für das Raumpostfach an. Sie können die Adresse im Abschnitt E-Mail-Adresse ändern.

  - **Kapazität**   Geben Sie in diesem Feld die maximale Anzahl an Personen ein, mit der der Raum belegt werden kann.

Klicken Sie auf **Weitere Optionen**, um diese zusätzlichen Eigenschaften anzuzeigen oder zu ändern:

  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit an, die das Konto für das Raumpostfach enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um das Konto in eine andere Organisationseinheit zu verschieben.

  - **Postfachdatenbank**   Dieses schreibgeschützte Feld zeigt den Namen der Postfachdatenbank an, in der das Raumpostfach gehostet wird. Verwenden Sie die Seite **Migration** in der Exchange-Verwaltungskonsole, um das Postfach in eine andere Datenbank zu verschieben.

  - **\* Alias** In diesem Feld können Sie den Alias für das Raumpostfach ändern.

  - **Aus Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass das Raumpostfach im Adressbuch und in anderen Adresslisten angezeigt wird, die in Ihrer Exchange-Organisation definiert sind. Nach dem Aktivieren dieses Kontrollkästchens können Benutzer weiterhin mit der E-Mail-Adresse Buchungsnachrichten an das Raumpostfach senden.

  - **Abteilung**   Geben Sie in diesem Feld den Namen einer Abteilung ein, der der Raum zugeordnet ist. Sie können diese Eigenschaft verwenden, um Empfängerbedingungen für dynamische Verteilergruppen und Adresslisten zu erstellen.

  - **Firma**   Geben Sie in diesem Feld eine Firma ein, der der Raum gegebenenfalls zugeordnet ist. Sie können diese Eigenschaft genauso wie die Eigenschaft "Abteilung" verwenden, um Empfängerbedingungen für dynamische Verteilergruppen und Adresslisten zu erstellen.

  - **Adressbuchrichtlinie**   Verwenden Sie diese Option, um eine Adressbuchrichtlinie für das Raumpostfach anzugeben. Adressbuchrichtlinien enthalten eine globale Adressliste (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine Gruppe von Adresslisten. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).
    
    Wählen Sie in der Dropdownliste die Richtlinie aus, die diesem Postfach zugeordnet werden soll.

  - **Benutzerdefinierte Attribute**   Dieser Abschnitt zeigt die für das Raumpostfach festgelegten benutzerdefinierten Attribute an. Klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um benutzerdefinierte Attributwerte anzugeben. Bis zu 15 benutzerdefinierte Attribute für den Empfänger können definiert werden.

## Stellvertretungen

In diesem Abschnitt können Sie anzeigen oder ändern, wie Reservierungsanfragen vom Raumpostfach behandelt werden, und festlegen, wer Buchungsanfragen annehmen oder ablehnen kann, falls dies nicht automatisch erfolgt.

  - **Buchungsanfragen**   Wählen Sie eine der folgenden Optionen aus, um Buchungsanfragen zu verarbeiten.
    
      - **Buchungsanfragen automatisch annehmen oder ablehnen**   Bei einer gültigen Besprechungsanfrage wird der Raum automatisch reserviert. Bei einem Planungskonflikt mit einer vorhandenen Reservierung oder bei einem Verstoß gegen die Zeitplanungseinschränkungen der Ressource (beispielsweise bei zu langer Reservierungsdauer) wird die Besprechungsanfrage automatisch abgelehnt.
    
      - **Stellvertretungen auswählen, die Buchungsanfragen annehmen oder ablehnen können**   Ressourcenstellvertretungen sind für das Annehmen oder Ablehnen von Besprechungsanfragen zuständig, die an das Raumpostfach gesendet werden. Wenn Sie mehr als eine Stellvertretung für die Ressource zuweisen, muss nur eine davon bei einer bestimmten Besprechungsanfrage tätig werden.

  - **Stellvertretungen**   Wenn Sie die Option ausgewählt haben, dass Buchungsanfragen an Stellvertretungen gesendet werden sollen, werden die angegebenen Stellvertretungen aufgeführt. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") oder **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um Stellvertretungen zu dieser Liste hinzuzufügen oder daraus zu entfernen.

## Buchungsoptionen

Im Abschnitt **Buchungsoptionen** können Sie die Einstellungen für die Buchungsrichtlinien anzeigen oder ändern. Diese Buchungsrichtlinien legen fest, wann der Raum eingeplant, wie lange er reserviert und wie weit im Voraus er reserviert werden kann.

  - **Besprechungsserien zulassen**   Diese Einstellung erlaubt oder verhindert Besprechungsserien für den Raum. Diese Einstellung ist standardmäßig aktiviert, sodass Besprechungsserien zulässig sind.

  - **Terminplanung nur während der Arbeitszeit zulassen**   Diese Einstellung nimmt Anfragen für Besprechungen an, die nicht in der für den Raum festgelegten Arbeitszeit stattfinden sollen, oder lehnt diese ab. Diese Einstellung ist standardmäßig deaktiviert, sodass Besprechungsanfragen außerhalb der Arbeitszeit zulässig sind. Die Arbeitszeit ist standardmäßig auf Montag bis Freitag, 8:00 Uhr bis 17:00 Uhr festgelegt. Die Arbeitszeit für das Raumpostfach kann auf der Seite "Kalender" im Abschnitt "Darstellung" konfiguriert werden.

  - **Immer ablehnen, wenn das Enddatum hinter diesem Grenzwert liegt**   Diese Einstellung steuert das Verhalten für Besprechungsserien, deren Enddatum nach dem Datum liegt, das in der Einstellung für die maximale Vorlaufzeit für Buchungen angegeben ist.
    
      - Wenn Sie diese Einstellung aktivieren, wird eine Serienbuchungsanfrage automatisch abgelehnt, wenn die Buchung an oder vor dem Datum beginnt, das durch den Wert im Feld **Maximale Vorlaufzeit für Buchungen** angegeben ist, und über das angegebene Datum hinausgeht. Dies ist die Standardeinstellung.
    
      - Wenn Sie diese Einstellung deaktivieren, wird eine Serienbuchungsanfrage automatisch angenommen, wenn Buchungsanfragen an oder vor dem Datum beginnen, das durch den Wert im Feld **Maximale Buchungsvorlaufzeit** angegeben ist, und über das angegebene Datum hinausgehen. Allerdings wird die Anzahl von Buchungen reduziert, sodass nach dem angegebenen Datum keine Buchungen möglich sind.

  - **Maximale Buchungsvorlaufzeit (Tage)**   Diese Einstellung gibt die maximale Anzahl an Tagen an, die der Raum im Voraus gebucht werden kann. Eine gültige Eingabe ist eine ganze Zahl zwischen 0 und 1080. Der Standardwert beträgt 180 Tage.

  - **Maximale Dauer (Stunden)**   Diese Einstellung gibt die maximale Dauer an, die der Raum in einer Buchungsanfrage reserviert werden kann. Der Standardwert ist 24 Stunden.
    
    Bei Serienbuchungsanfragen gilt die maximale Buchungsdauer für die Länge jeder einzelnen Exchange-Verwaltungskonsoleninstanz der Serienbuchungsanfrage.

Auf dieser Seite befindet sich auch ein Feld, in dem Sie eine Nachricht eingeben können, die an Benutzer gesendet wird, die Buchungsanfragen für die Reservierung des Raums senden.

## Kontaktinformationen

Im Abschnitt **Kontaktinformationen** können Sie Kontaktinformationen anzeigen oder ändern. Die Informationen auf dieser Seite werden im Adressbuch angezeigt.


> [!TIP]
> Sie können das Feld <STRONG>Bundesland/Kanton</STRONG> verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.



## E-Mail-Adresse

Im Abschnitt **E-Mail-Adresse** können Sie die E-Mail-Adressen anzeigen und ändern, die dem Raumpostfach zugeordnet sind. Dazu gehören die primäre SMTP-Adresse des Postfachs und alle zugehörigen Proxyadressen. Die primäre SMTP-Adresse (auch als *Antwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben.

  - **Hinzufügen **  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue E-Mail-Adresse für dieses Postfach hinzuzufügen. Wählen Sie einen der folgenden Adresstypen aus:
    
      - **SMTP**   Dies ist der Standardadresstyp. Klicken Sie auf diese Schaltfläche, und geben Sie dann die neue SMTP-Adresse in das Feld **\* E-Mail-Adresse** ein.
    
      - **EUM**   Eine EUM-Adresse (Exchange Unified Messaging) wird vom Microsoft Exchange Unified Messaging-Dienst verwendet, um UM-aktivierte Empfänger innerhalb einer Exchange-Organisation zu finden. EUM-Adressen enthalten eine Durchwahlnummer und einen UM-Wählplan für den UM-aktivierten Benutzer. Klicken Sie auf diese Schaltfläche, und geben Sie die Durchwahlnummer im Feld **Adresse/Durchwahl** ein. Klicken Sie dann auf **Durchsuchen**, und wählen Sie einen Wählplan für das Postfach aus.
    
      - **Benutzerdefinierter Adresstyp**   Klicken Sie auf diese Schaltfläche, und geben Sie einen der unterstützten Nicht-SMTP-E-Mail-Adresstypen in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Mit Ausnahme von X.400-Adressen überprüft Exchange benutzerdefinierte Adressen nicht auf ordnungsgemäße Formatierung. Sie müssen sicherstellen, dass die von Ihnen angegebene benutzerdefinierte Adresse die Formatanforderungen für den jeweiligen Adresstyp erfüllt.

    

    > [!NOTE]
    > Wenn Sie eine neue E-Mail-Adresse hinzufügen, können Sie diese als primäre SMTP-Adresse festlegen.



  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden.

## E-Mail-Info

Im Abschnitt **E-Mail-Info** können Sie eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, bevor sie eine Buchungsanfrage an das Raumpostfach senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn dieser Empfänger dem Feld "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Verwenden der Exchange Powershell zum Ändern von Raumpostfacheigenschaften

Mit den folgenden Cmdlets können Sie die Eigenschaften des Raumpostfachs anzeigen und ändern: **Get-Mailbox** und **Set-Mailbox** zum Anzeigen und Ändern von allgemeinen Eigenschaften und E-Mail-Adressen für Raumpostfächer. Verwenden Sie die Cmdlets **Get-CalendarProcessing** und **Set-CalendarProcessing**, um Stellvertretungen und Buchungsoptionen anzuzeigen und zu ändern.

  - **Get-User** und **Set-User**   Verwenden Sie diese Cmdlets zum Anzeigen und Ändern von allgemeinen Eigenschaften, wie Standort, Abteilungs- und Firmenname.

  - **Get-Mailbox** und **Set-Mailbox**   Verwenden Sie diese Cmdlets, um Postfacheigenschaften wie z. B. E-Mail-Adressen und die Postfachdatenbank anzuzeigen und festzulegen.

  - **Get-CalendarProcessing** und **Set-CalendarProcessing**   Verwenden Sie diese Cmdlets, um Buchungsoptionen und Stellvertretungen anzuzeigen und festzulegen.

Weitere Informationen über diese Cmdlets finden Sie in de folgenden Themen:

  - [Get-User](https://technet.microsoft.com/de-de/library/aa996896\(v=exchg.150\))

  - [Set-User](https://technet.microsoft.com/de-de/library/aa998221\(v=exchg.150\))

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

  - [Get-CalendarProcessing](https://technet.microsoft.com/de-de/library/dd298137\(v=exchg.150\))

  - [Set-CalendarProcessing](https://technet.microsoft.com/de-de/library/dd335046\(v=exchg.150\))

Hier finden Sie einige Beispiele dafür, wie Sie mit der Exchange PowerShell Raumpostfacheigenschaften ändern können.

In diesem Beispiel werden der Anzeigename, die primäre SMTP-Adresse (auch als Standardantwortadresse bezeichnet) und die Raumkapazität geändert. Außerdem wird die vorherige Antwortadresse als Proxyadresse gespeichert.

    Set-Mailbox "Conf Room 123" -DisplayName "Conf Room 31/123 (12)" -EmailAddresses SMTP:Rm33.123@contoso.com,smtp:rm123@contoso.com -ResourceCapacity 12

In diesem Beispiel werden Raumpostfächer so konfiguriert, dass Buchungsanfragen nur während der Arbeitszeit eingeplant werden können und auf maximal neun Stunden ausgelegt sind.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'RoomMailbox')} | Set-CalendarProcessing -ScheduleOnlyDuringWorkHours $true -MaximumDurationInMinutes 540

In diesem Beispiel werden mit dem Cmdlet **Get-User** alle Raumpostfächer gesucht, die privaten Konferenzräumen entsprechen, und dann werden mit dem Cmdlet **Set-CalendarProcessing** Buchungsanfragen zur Annahme oder Ablehnung an einen Stellvertreter namens "Robin Wood" gesendet.

    Get-User -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'RoomMailbox') -and (DisplayName -like 'Private*')} | Set-CalendarProcessing -AllBookInPolicy $false -AllRequestInPolicy $true -ResourceDelegates "Robin Wood"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob Sie die Eigenschaften für ein Raumpostfach erfolgreich geändert haben:

  - Wählen Sie in der Exchange-Verwaltungskonsole das Postfach aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder das Feature anzuzeigen, die bzw. das Sie geändert haben. In Abhängigkeit von der geänderten Eigenschaft wird diese möglicherweise im Detailbereich für das ausgewählte Postfach angezeigt.

  - Verwenden Sie in der Exchange PowerShell das Cmdlet **Get-Mailbox**, um die Änderungen zu überprüfen. Ein Vorteil der Verwendung von Exchange PowerShell besteht darin, dass Sie mehrere Eigenschaften für mehrere Postfächer anzeigen können. Führen Sie im obigen Beispiel, in dem Buchungsanfragen nur während der Arbeitszeit eingeplant werden konnten und für eine maximale Dauer von neun Stunden ausgelegt waren, den folgenden Befehl aus, um die neuen Werte zu überprüfen.
    
        Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'RoomMailbox')} | Get-CalendarProcessing | fl Identity,ScheduleOnlyDuringWorkHours,MaximumDurationInMinutes

Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..


