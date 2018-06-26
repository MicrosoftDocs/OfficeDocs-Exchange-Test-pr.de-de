---
title: 'Verwalten von Gerätepostfächern: Exchange 2013 Help'
TOCTitle: Verwalten von Gerätepostfächern
ms:assetid: e5f58b3a-83e1-4742-8846-85103a44ee18
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ215770(v=EXCHG.150)
ms:contentKeyID: 50474911
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Gerätepostfächern

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-10-09_

Ein *Gerätepostfach* ist ein Ressourcenpostfach, das einer ortsunabhängigen Ressource zugewiesen wird, wie z. B. einem Laptop, einem Projektor, einem Mikrofon oder einem Firmenwagen. Nachdem ein Administrator ein Gerätepostfach erstellt hat, können die Benutzer das Gerät einfach reservieren, indem sie das entsprechende Gerätepostfach in eine Besprechungsanfrage einschließen. Sie können die Exchange-Verwaltungskonsole und die Shell verwenden, um ein Gerätepostfach zu erstellen oder die Eigenschaften von Gerätepostfächern zu ändern. Weitere Informationen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

Informationen zu anderen Ressourcenpostfachtyp, einem Raumpostfach, finden Sie unter [Erstellen und Verwalten von Raumpostfächern](create-and-manage-room-mailboxes-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 bis 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen eines Gerätepostfachs

## Erstellen eines Gerätepostfachs mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Ressourcen**.

2.  Zum Erstellen des Gerätepostfachs klicken Sie auf **Neu** \> **Gerätepostfach**. Zum Erstellen eines Raumpostfachs klicken Sie auf **Neu** \> **Raumpostfach**.

3.  Verwenden Sie die Optionen auf der Seite, um die Einstellungen für das neue Ressourcenpostfach festzulegen.
    
      - **\* Gerätename**   Geben Sie in diesem Feld einen Namen für das Gerätepostfach ein. Dies ist der Name, der in der Ressourcenpostfachliste in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation verwendet wird. Dieser Name ist erforderlich und darf höchstens 64 Zeichen umfassen.
        

        > [!TIP]
        > Zwar enthalten auch andere Felder Details zum Raum (z.&nbsp;B. die Kapazität), es empfiehlt sich jedoch, die wichtigsten Details unter Verwendung einer konsistenten Benennungskonvention im Gerätenamen zusammenzufassen. Der Grund: Benutzer erhalten so auf einfache Weise Informationen zu dem Gerät, wenn sie es in einer Besprechungsanfrage im Adressbuch auswählen.

    
      - **\* E-Mail-Adresse**   Ein Gerätepostfach verfügt über eine E-Mail-Adresse, daher kann es Buchungsanfragen empfangen. Die E-Mail-Adresse besteht aus einem Alias vor dem @-Symbol, der in der Gesamtstruktur eindeutig sein muss, und dem Namen Ihrer Domäne hinter dem Symbol. Die E-Mail-Adresse ist erforderlich.

4.  Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um das Gerätepostfach zu erstellen.

Nachdem Sie Ihr Gerätepostfach erstellt haben, können Sie Ihr Gerätepostfach so ändern, dass es Informationen zu Buchungsoptionen, E-Mails und Stellvertretern aktualisiert. Lesen Sie den den unten aufgeführten Abschnitt zum Ändern von Gerätepostfacheigenschaften, wenn Sie Raumpostfacheigenschaften ändern möchten.

## Erstellen eines Gerätepostfachs mithilfe der Shell

In diesem Beispiel wird ein Gerätepostfach mit der folgenden Konfiguration erstellt:

  - Das Gerätepostfach befindet sich in der Postfachdatenbank "Mailbox Database 1".

  - Der Name des Geräts lautet "MotorVehicle2", und er wird in der globalen Adressliste als "Motor Vehicle 2" angezeigt.

  - Die E-Mail-Adresse lautet "MotorVehicle2@contoso.com".

  - Das Postfach befindet sich in der Organisationseinheit "Equipment".

  - Der Parameter *Equipment* gibt an, dass dieses Postfach als Gerätepostfach erstellt wird.

<!-- end list -->

    New-Mailbox -Database "Mailbox Database 1" -Name MotorVehicle2 -OrganizationalUnit Equipment -DisplayName "Motor Vehicle 2" -Equipment

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-Mailbox](https://technet.microsoft.com/de-de/library/aa997663\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung eines Benutzerpostfachs zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Ressourcen**. Das neue Benutzerpostfach wird in der Postfachliste angezeigt. Unter **Postfachtyp** lautet der Typ **Gerät**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zum neuen Gerätepostfach anzuzeigen.
    
        Get-Mailbox <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress

## Ändern der Gerätepostfacheigenschaften

Nachdem Sie ein Gerätepostfach erstellt haben, können Sie Änderungen vornehmen und zusätzliche Eigenschaften über die Exchange-Verwaltungskonsole oder über die Shell festlegen.

## Ändern der Gerätepostfacheigenschaften mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Ressourcen**.

2.  Klicken Sie in der Liste der Ressourcenpostfächer auf das Gerätepostfach, dessen Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite mit den Gerätepostfacheigenschaften auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Stellvertretungen
    
      - Buchungsoptionen
    
      - Kontaktinformationen
    
      - E-Mail-Adresse
    
      - E-Mail-Info

## Allgemein

Verwenden Sie den Abschnitt **Allgemein**, um grundlegende Informationen zur Ressource anzuzeigen oder zu ändern.

  - **\* Gerätename**   Dies ist der Name, der in der Ressourcenpostfachliste in der Exchange-Verwaltungskonsole und im Adressbuch Ihrer Organisation angezeigt wird. Der Name darf höchstens 64 Zeichen umfassen, wenn Sie ihn ändern.

  - **\* E-Mail-Adresse**   Dieses schreibgeschützte Feld zeigt die E-Mail-Adresse für das Gerätepostfach an. Sie können die Adresse im Abschnitt E-Mail-Adresse ändern.

  - **Kapazität**   Geben Sie über dieses Feld die maximale Anzahl von Personen ein, die diese Ressource ggf. verwenden können. Wenn das Gerätepostfach z. B. einem Kompaktwagen entspricht, könnten Sie **4** eingeben.

Klicken Sie auf **Weitere Optionen**, um diese zusätzlichen Eigenschaften anzuzeigen oder zu ändern:

  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit an, die das Konto für das Gerätepostfach enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um das Konto in eine andere Organisationseinheit zu verschieben.

  - **Postfachdatenbank**   Dieses schreibgeschützte Feld zeigt den Namen der Postfachdatenbank an, in der das Gerätepostfach gehostet wird. Verwenden Sie die Seite **Migration** in der Exchange-Verwaltungskonsole, um das Postfach in eine andere Datenbank zu verschieben.

  - **\* Alias**   Verwenden Sie dieses Feld, um den Alias für das Gerätepostfach zu ändern.

  - **Aus Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, um zu verhindern, dass das Gerätepostfach im Adressbuch und anderen Adresslisten angezeigt wird, die in Ihrer Exchange-Organisation definiert sind. Nachdem Sie dieses Kontrollkästchen aktiviert haben, können Benutzer weiterhin unter Verwendung der E-Mail-Adresse Buchungsnachrichten an das Gerätepostfach senden.

  - **Abteilung**   In diesem Feld können Sie einen Abteilungsnamen angeben, dem die Ressource zugeordnet ist. Sie können diese Eigenschaft verwenden, um Empfängerbedingungen für dynamische Verteilergruppen und Adresslisten zu erstellen.

  - **Firma**   In diesem Feld können Sie eine Firma angeben, der die Ressource zugeordnet ist. Sie können diese Eigenschaft genauso wie die Eigenschaft "Abteilung" verwenden, um Empfängerbedingungen für dynamische Verteilergruppen und Adresslisten zu erstellen.

  - **Adressbuchrichtlinie**   Verwenden Sie diese Option, um eine Adressbuchrichtlinie für die Ressource anzugeben. Adressbuchrichtlinien enthalten eine globale Adressliste (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine Gruppe von Adresslisten. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).
    
    Wählen Sie in der Dropdownliste die Richtlinie aus, die diesem Postfach zugeordnet werden soll.

  - **Benutzerdefinierte Attribute**   In diesem Abschnitt werden die benutzerdefinierten Attribute angezeigt, die für das Gerätepostfach definiert sind. Klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um benutzerdefinierte Attributwerte anzugeben. Bis zu 15 benutzerdefinierte Attribute für den Empfänger können definiert werden.

## Stellvertretungen

Mithilfe dieses Abschnitts können Sie anzeigen oder ändern, wie Reservierungsanfragen vom Gerätepostfach verarbeitet werden. Außerdem können Sie festlegen, wer Buchungsanfragen annehmen oder ablehnen darf, sofern dieser Vorgang nicht automatisch ausgeführt wird.

  - **Buchungsanfragen**   Wählen Sie eine der folgenden Optionen aus, um Buchungsanfragen zu verarbeiten.
    
      - **Buchungsanfragen automatisch annehmen oder ablehnen**   Bei einer gültigen Besprechungsanfrage wird die Ressource automatisch reserviert. Bei einem Planungskonflikt mit einer vorhandenen Reservierung oder bei einem Verstoß gegen die Zeitplanungseinschränkungen der Ressource (beispielsweise bei zu langer Reservierungsdauer) wird die Besprechungsanfrage automatisch abgelehnt.
    
      - **Stellvertretungen auswählen, die Buchungsanfragen annehmen oder ablehnen können**   Ressourcenstellvertretungen sind für das Annehmen oder Ablehnen von Besprechungsanfragen zuständig, die an das Gerätepostfach gesendet werden. Wenn Sie mehr als eine Stellvertretung für die Ressource zuweisen, muss nur eine davon bei einer bestimmten Besprechungsanfrage tätig werden.

  - **Stellvertretungen**   Wenn Sie die Option ausgewählt haben, dass Buchungsanfragen an Stellvertretungen gesendet werden sollen, werden die angegebenen Stellvertretungen aufgeführt. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") oder **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um Stellvertretungen zu dieser Liste hinzuzufügen oder daraus zu entfernen.

## Buchungsoptionen

Über den Abschnitt **Buchungsoptionen** können Sie die Einstellungen für die Buchungsrichtlinie anzeigen oder ändern, die festlegt, wann die Ressource geplant werden kann, für welchen Zeitraum und wie weit im Voraus sie reserviert werden kann.

  - **Besprechungsserien zulassen**   Mit dieser Einstellung werden Besprechungsserien für die Ressource zugelassen oder verhindert. Diese Einstellung ist standardmäßig aktiviert, sodass Besprechungsserien zulässig sind.

  - **Terminplanung nur während der Arbeitszeit zulassen**   Mit dieser Einstellung werden Besprechungsanfragen, die nicht innerhalb der für die Ressource definierten Arbeitszeit liegen, angenommen oder abgelehnt. Diese Einstellung ist standardmäßig deaktiviert, sodass Besprechungsanfragen außerhalb der Arbeitszeit zulässig sind. Die Arbeitszeit ist standardmäßig auf Montag bis Freitag, 8:00 Uhr bis 17:00 Uhr festgelegt. Die Arbeitszeit für das Gerätepostfach kann auf der Seite "Kalender" im Abschnitt "Darstellung" konfiguriert werden.

  - **Immer ablehnen, wenn das Enddatum hinter diesem Grenzwert liegt**   Diese Einstellung steuert das Verhalten für Besprechungsserien, deren Enddatum nach dem Datum liegt, das in der Einstellung für die maximale Vorlaufzeit für Buchungen angegeben ist.
    
      - Wenn Sie diese Einstellung aktivieren, wird eine Serienbuchungsanfrage automatisch abgelehnt, wenn die Buchung an oder vor dem Datum beginnt, das durch den Wert im Feld **Maximale Vorlaufzeit für Buchungen** angegeben ist, und über das angegebene Datum hinausgeht. Dies ist die Standardeinstellung.
    
      - Wenn Sie diese Einstellung deaktivieren, wird eine Serienbuchungsanfrage automatisch angenommen, wenn die Buchungsanfrage an oder vor dem Datum beginnt, das durch den Wert im Feld **Maximale Buchungsvorlaufzeit** angegeben ist, und über das angegebene Datum hinausgeht. Allerdings wird die Anzahl von Buchungen reduziert, sodass nach dem angegebenen Datum keine Buchungen möglich sind.

  - **Maximale Buchungsvorlaufzeit (Tage)**   Diese Einstellung gibt die maximale Anzahl von Tagen an, die die Ressource im Voraus gebucht werden kann. Eine gültige Eingabe ist eine ganze Zahl zwischen 0 und 1080. Der Standardwert beträgt 180 Tage.

  - **Maximale Dauer (Stunden)**   Diese Einstellung gibt die maximale Dauer an, die die Ressource in einer Buchungsanfrage reserviert werden kann. Der Standardwert ist 24 Stunden.
    
    Bei Serienbuchungsanfragen gilt die maximale Buchungsdauer für die Länge jeder einzelnen Instanz der Serienbuchungsanfrage.

Auf dieser Seite ist auch ein Feld enthalten, in das Sie eine Nachricht eingeben können, die an Benutzer gesendet wird, die Besprechungsanfragen senden, um die Ressource zu reservieren.

## Kontaktinformationen

Verwenden Sie den Abschnitt **Kontaktinformationen**, um die Kontaktinformationen für die Ressource anzuzeigen oder zu ändern. Die Informationen auf dieser Seite werden im Adressbuch angezeigt.


> [!TIP]
> Sie können das Feld <STRONG>Bundesland/Kanton</STRONG> verwenden, um Empfängerbedingungen für dynamische Verteilergruppen, Richtlinien für E-Mail-Adressen oder Adresslisten zu erstellen.



## E-Mail-Adresse

In dem Abschnitt **E-Mail-Adresse** können Sie die E-Mail-Adressen anzeigen und ändern, die dem Gerätepostfach zugeordnet sind. Dazu gehören die primäre SMTP-Adresse des Postfachs und alle zugehörigen Proxyadressen. Die primäre SMTP-Adresse (auch als *Antwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben.

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

Verwenden Sie den Abschnitt **E-Mail-Info**, um eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, bevor sie eine Buchungsanfrage an das Gerätepostfach senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn dieser Empfänger dem Feld "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Ändern der Gerätepostfacheigenschaften mithilfe der Shell

Verwenden Sie die folgenden Cmdlets, um die Eigenschaften des Gerätepostfachs anzuzeigen oder zu ändern: **Get-Mailbox** und **Set-Mailbox**, um allgemeine Eigenschaften und E-Mail-Adressen für Gerätepostfächer anzuzeigen oder zu ändern. Verwenden Sie die Cmdlets **Get-CalendarProcessing** und **Set-CalendarProcessing**, um Stellvertretungen und Buchungsoptionen anzuzeigen und zu ändern.

  - **Get-User** und **Set-User**   Mit diesen Cmdlets können Sie allgemeine Eigenschaften wie Abteilungs- und Firmennamen anzeigen und festlegen.

  - **Get-Mailbox** und **Set-Mailbox**   Verwenden Sie diese Cmdlets, um Postfacheigenschaften wie z. B. E-Mail-Adressen und die Postfachdatenbank anzuzeigen und festzulegen.

  - **Get-CalendarProcessing** und **Set-CalendarProcessing**   Verwenden Sie diese Cmdlets, um Buchungsoptionen und Stellvertretungen anzuzeigen und festzulegen.

Weitere Informationen über diese Cmdlets finden Sie in de folgenden Themen:

  - [Get-User](https://technet.microsoft.com/de-de/library/aa996896\(v=exchg.150\))

  - [Set-User](https://technet.microsoft.com/de-de/library/aa998221\(v=exchg.150\))

  - [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\))

  - [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))

  - [Get-CalendarProcessing](https://technet.microsoft.com/de-de/library/dd298137\(v=exchg.150\))

  - [Set-CalendarProcessing](https://technet.microsoft.com/de-de/library/dd335046\(v=exchg.150\))

Hier folgen einige Beispiele zum Ändern der Eigenschaften des Gerätepostfachs mithilfe der Shell.

In diesem Beispiel werden der Anzeigename und die primäre SMTP-Adresse (auch als Standardantwortadresse bezeichnet) für das Gerätepostfach "MotorPool 1" geändert. Die vorherige Antwortadresse wird als Proxyadresse beibehalten.

    Set-Mailbox "MotorPool 1" -DisplayName "Motor Pool 1 - Compact" -EmailAddresses SMTP:MP1.compact@contoso.com,smtp:MP.1@contoso.com

In diesem Beispiel werden Gerätepostfächer so konfiguriert, dass sie das Planen von Buchungsanfragen nur während der Arbeitszeiten gestatten.

    Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'EquipmentMailbox')} | Set-CalendarProcessing -ScheduleOnlyDuringWorkHours $true

In diesem Beispiel wird das Cmdlet **Get-User** verwendet, um alle Gerätepostfächer in der Abteilung "Audio Visual" zu finden. Dann werden mit dem Cmdlet **Set-CalendarProcessing** Buchungsanfragen an eine Stellvertretung namens "Ann Beebe" gesendet, um diese anzunehmen oder abzulehnen.

    Get-User -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'EquipmentMailbox') -and (Department -eq 'Audio Visual')} | Set-CalendarProcessing -AllBookInPolicy $false -AllRequestInPolicy $true -ResourceDelegates "Ann Beebe"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um die erfolgreiche Änderung von Gerätepostfacheigenschaften zu überprüfen:

  - Wählen Sie in der Exchange-Verwaltungskonsole das Postfach aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder das Feature anzuzeigen, die bzw. das Sie geändert haben. In Abhängigkeit von der geänderten Eigenschaft wird diese möglicherweise im Detailbereich für das ausgewählte Postfach angezeigt.

  - In der Shell verwenden Sie das Cmdlet **Get-Mailbox**, um die Änderungen zu überprüfen. Ein Vorteil der Shell liegt darin, dass Sie mehrere Eigenschaften für mehrere Postfächer anzeigen können. Führen Sie im obigen Beispiel, in dem die Buchungsanfragen nur während der Arbeitszeiten geplant werden konnten, folgenden Befehl aus, um den neuen Wert zu überprüfen.
    
        Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'EquipmentMailbox')} | Get-CalendarProcessing | fl Identity,ScheduleOnlyDuringWorkHours

