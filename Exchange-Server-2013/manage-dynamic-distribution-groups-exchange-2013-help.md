---
title: 'Verwalten dynamischer Verteilergruppen: Exchange 2013 Help'
TOCTitle: Verwalten dynamischer Verteilergruppen
ms:assetid: 8ef85d0a-41df-4b5c-b8e7-ca8d09c048ca
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123722(v=EXCHG.150)
ms:contentKeyID: 50474877
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.CreateDynamicGroupWizardForm.CreateDynamicGroupInformationWizardPage
ms.translationtype: HT
---

# Verwalten dynamischer Verteilergruppen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Dynamische Verteilergruppen sind E-Mail-aktivierte Active Directory-Gruppenobjekte, die erstellt werden, um den Massenversand von E-Mail-Nachrichten und sonstigen Informationen innerhalb einer Microsoft Exchange-Organisation zu beschleunigen.

Im Gegensatz zu normalen Verteilergruppen mit einer festgelegten Anzahl an Mitgliedern wird die Mitgliederliste für dynamische Verteilergruppen basierend auf den von Ihnen festgelegten Filtern und Bedingungen jedes Mal berechnet, wenn eine Nachricht an die Gruppe übermittelt wird. Wenn eine E-Mail an eine dynamische Verteilergruppe gesendet wird, wird sie an alle Empfänger in der Organisation zugestellt, die mit den für die Gruppe festgelegten Kriterien übereinstimmen.


> [!IMPORTANT]
> Eine dynamische Verteilergruppe enthält alle Empfänger in Active Directory, deren Attributwerte dem jeweiligen Filter entsprechen. Werden die Eigenschaften eines Empfängers geändert, damit sie dem Filter entsprechen, kann dieser Empfänger ggf. versehentlich ein Gruppenmitglied werden und Nachrichten erhalten, die an die Gruppe gesendet werden. Ordnungsgemäße und konsistente Kontobereitstellungsverfahren verringern das Risiko solcher Vorkommnisse.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 bis 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Dynamische Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer dynamischen Verteilergruppe

## Erstellen einer dynamischen Verteilergruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Gruppen** \> **Neu** \> **Dynamische Verteilergruppe**.

2.  Füllen Sie auf der Seite **Neue dynamische Verteilergruppe** die folgenden Felder aus:
    
      - **\* Anzeigename**   Verwenden Sie dieses Feld, um den Anzeigenamen einzugeben. Dieser Name wird im freigegebenen Adressbuch in der Zeile "An:" angezeigt, wenn eine E-Mail an diese Gruppe gesendet wird. Außerdem wird er in der Gruppenliste in der Exchange-Verwaltungskonsole angezeigt. Der Anzeigename ist erforderlich und muss aussagekräftig sein, damit andere Personen den Zweck der Gruppe erkennen können. Dieser Name muss auch in der Gesamtstruktur eindeutig sein.
        

        > [!NOTE]
        > Die Gruppenbenennungsrichtlinie wird auf dynamische Verteilergruppen nicht angewendet.

    
      - **\* Alias**   Verwenden Sie dieses Feld, um den Aliasnamen der Gruppe einzugeben. Der Alias darf höchstens 64 Zeichen enthalten und muss in der Gesamtstruktur eindeutig sein. Wenn ein Benutzer den Alias in der Zeile "An:" einer E-Mail eingibt, wird er in den Anzeigenamen der Gruppe aufgelöst.
    
      - **Beschreibung**   Verwenden Sie dieses Feld, um die Gruppe zu beschreiben, damit der Zweck der Gruppe ersichtlich wird. Diese Beschreibung wird im freigegebenen Adressbuch angezeigt.
    
      - **Organisationseinheit**   Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container "Benutzer" in der Active Directory-Domäne festgelegt, in der sich der Computer befindet, auf dem die Exchange-Verwaltungskonsole ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container Benutzer ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten der Gesamtstruktur angezeigt, die sich in einem bestimmten Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie dann auf **OK**.
    
      - **Besitzer**  Ein Besitzer für eine dynamische Verteilergruppe ist optional. Sie können Besitzer hinzufügen, indem Sie auf **Durchsuchen** klicken und anschließend Benutzer aus der Liste auswählen.

3.  Im Abschnitt **Mitglieder** geben Sie die Empfängertypen für die Gruppe an und richten Regeln zum Festlegen der Mitgliedschaft ein. Wählen Sie eines der folgenden Felder aus:
    
      - **Alle Empfängertypen**   Wählen Sie diese Option, um Nachrichten, die den für diese Gruppe definierten Kriterien entsprechen, an alle Empfängertypen zu senden.
    
      - **Nur die folgenden Empfängertypen**   Nachrichten, die den für diese Gruppe definierten Kriterien entsprechen, werden an einen oder mehrere der folgenden Empfängertypen gesendet:
        
          - **Benutzer mit Exchange-Postfächern**   Aktivieren Sie dieses Kontrollkästchen, um Benutzer mit Exchange-Postfächern einzubeziehen. Benutzer mit Exchange-Postfächern haben ein Benutzerdomänenkonto und ein Postfach in der Exchange-Organisation.
        
          - **Benutzer mit externen E-Mail-Adressen**   Aktivieren Sie dieses Kontrollkästchen, um Benutzer mit externen E-Mail-Adressen einzubeziehen. Benutzer mit externen E-Mail-Konten besitzen Benutzerdomänenkonten in Active Directory, verwenden jedoch E-Mail-Konten außerhalb der Organisation. So können diese in die globale Adressliste (Global Address List, GAL) eingebunden und Verteilerlisten hinzugefügt werden.
        
          - **Ressourcenpostfächer**   Aktivieren Sie dieses Kontrollkästchen, um Exchange-Ressourcenpostfächer einzubeziehen. Ressourcenpostfächer ermöglichen das Verwalten der Unternehmensressourcen (z. B. eines Konferenzraums oder eines Firmenfahrzeugs) über ein Postfach.
        
          - **Kontakte mit externen E-Mail-Adressen**   Aktivieren Sie dieses Kontrollkästchen, um Kontakte mit externen E-Mail-Adressen einzubeziehen. Kontakte mit externen E-Mail-Adressen haben in Active Directory keine Benutzerdomänenkonten, die externe E-Mail-Adresse steht jedoch in der GAL zur Verfügung.
        
          - **E-Mail-aktivierte Gruppen**   Aktivieren Sie dieses Kontrollkästchen, um E-Mail-aktivierte Sicherheitsgruppen oder Verteilergruppen einzubeziehen. E-Mail-aktivierte Gruppen ähneln Verteilergruppen. E-Mail-Nachrichten, die an ein E-Mail-aktiviertes Gruppenkonto gesendet werden, werden an mehrere Empfänger geschickt.

4.  Klicken Sie auf **Regel hinzufügen**, um die Kriterien für die Mitgliedschaft in dieser Gruppe zu definieren.

5.  Wählen Sie eines der folgenden Empfängerattribute aus der Dropdownliste aus, und geben Sie einen Wert an. Wenn der Wert für das ausgewählte Attribut dem von Ihnen definierten Wert entspricht, erhält der Empfänger eine Nachricht, die an diese Gruppe gesendet wird.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Attribut</th>
    <th>Nachricht in folgenden Fällen an einen Empfänger senden...</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Empfängercontainer</strong></p></td>
    <td><p>Das Empfängerobjekt befindet sich in der angegebenen Domäne oder Organisationseinheit.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Bundesland oder Kanton</strong></p></td>
    <td><p>Der angegebene Wert entspricht der Eigenschaft Bundesland/Kanton des Empfängers.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Company</strong></p></td>
    <td><p>Der angegebene Wert entspricht der Eigenschaft Firma des Empfängers.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Department</strong></p></td>
    <td><p>Der angegebene Wert entspricht der Eigenschaft Abteilung des Empfängers.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Benutzerdefiniertes AttributN</strong> (wobei N für eine Zahl zwischen 1 und 15 steht)</p></td>
    <td><p>Der angegebene Wert entspricht der Eigenschaft CustomAttributeN des Empfängers.</p></td>
    </tr>
    </tbody>
    </table>
    

    > [!IMPORTANT]
    > Die für das ausgewählte Attribut eingegebenen Werte müssen den Werten auf der Eigenschaftenseite des Empfängers genau entsprechen. Wenn Sie beispielsweise <STRONG>Nordrhein-Westfalen</STRONG> für <STRONG>Bundesland/Kanton</STRONG> eingeben, der Wert für die Empfängereigenschaft jedoch <STRONG>NRW</STRONG> lautet, wird die Bedingung nicht erfüllt. Bei den von Ihnen angegebenen Werten wird zudem keine Groß- und Kleinschreibung unterschieden. Wenn Sie beispielsweise <STRONG>Contoso</STRONG> für das Attribut <STRONG>Firma</STRONG> angeben, werden Nachrichten an einen Empfänger gesendet, wenn dieser Wert <STRONG>contoso</STRONG> lautet.



6.  Geben Sie im Fenster **Wörter oder Ausdrücke angeben** den Wert im Textfeld ein. Klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **OK**.

7.  Wenn Sie eine weitere Regel zum Definieren der Kriterien für die Mitgliedschaft hinzufügen möchten, klicken Sie unter der zuvor erstellten Regel auf **Regel hinzufügen**.
    

    > [!IMPORTANT]
    > Wenn Sie mehrere Regeln zum Definieren der Mitgliedschaft hinzufügen, muss ein Empfänger die Kriterien aller Regeln erfüllen, um eine an die Gruppe gesendete Nachricht zu erhalten. Anders ausgedrückt: Jede Regel ist über den Booleschen Operator <STRONG>UND</STRONG> verbunden.



8.  Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um die dynamische Verteilergruppe zu erstellen.


> [!NOTE]
> Wenn Sie Regeln für andere Attribute angeben möchten, die nicht in der Exchange-Verwaltungskonsole verfügbar sind, müssen Sie die Shell zum Erstellen einer dynamischen Verteilergruppe verwenden. Berücksichtigen Sie, dass die Filter- und Bedingungseinstellungen für dynamische Verteilergruppen mit benutzerdefinierten Empfängerfiltern nur über die Shell verwaltet werden können. Ein Beispiel für die Erstellung einer dynamischen Verteilergruppe anhand einer benutzerdefinierten Abfrage finden Sie im nächsten Abschnitt über die Erstellung einer dynamischen Verteilergruppe mithilfe der Shell.



## Erstellen einer dynamischen Verteilgruppe mithilfe der Shell

In diesem Beispiel wird die dynamische Verteilergruppe "Mailbox Users DDG" erstellt, die nur Postfachbenutzer enthält.

    New-DynamicDistributionGroup -IncludedRecipients MailboxUsers -Name "Mailbox Users DDG" -OrganizationalUnit Users

In diesem Beispiel wird eine dynamische Verteilergruppe mit einem benutzerdefinierten Empfängerfilter erstellt. Die dynamische Verteilergruppe enthält alle Postfachbenutzer auf dem Server "Server1".

    New-DynamicDistributionGroup -Name "Mailbox Users on Server1" -OrganizationalUnit Users -RecipientFilter {((RecipientTypeDetails -eq 'UserMailbox' -and ServerName -eq 'Server1'))}

In diesem Beispiel wird eine dynamische Verteilergruppe mit einem benutzerdefinierten Empfängerfilter erstellt. Die dynamische Verteilergruppe enthält alle Postfachbenutzer, deren Eigenschaft **CustomAttribute10** den Wert "FullTimeEmployee" aufweist.

    New-DynamicDistributionGroup -Name "Full Time Employees" -RecipientFilter {(RecipientTypeDetails -eq 'UserMailbox') -and (CustomAttribute10 -eq 'FullTimeEmployee')}

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb125127\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung einer dynamischen Verteilergruppe zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Gruppen**. Die neue dynamische Verteilergruppe wird in der Gruppenliste angezeigt. Unter **Gruppentyp** lautet der Typ **Dynamische Verteilergruppe**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zur neuen dynamischen Verteilergruppe anzuzeigen.
    
        Get-DynamicDistributionGroup | FL Name,RecipientTypeDetails,RecipientFilter,PrimarySmtpAddress

## Ändern der Eigenschaften für dynamische Verteilergruppen

## Ändern der Eigenschaften einer dynamischen Verteilergruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Gruppen**.

2.  Klicken Sie in der Gruppenliste auf die dynamische Verteilergruppe, die Sie anzeigen oder ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite für die Gruppe auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Besitz
    
      - Mitgliedschaft
    
      - Zustellungsverwaltung
    
      - Nachrichtenbestätigung
    
      - E-Mail-Optionen
    
      - MailTip
    
      - Gruppendelegierung

## Allgemein

Verwenden Sie diesen Abschnitt, um grundlegende Informationen zur Gruppe anzuzeigen oder zu ändern.

  - **\* Anzeigename**   Dieser Name wird im Adressbuch, in E-Mails in den Zeilen "An:" angezeigt, wenn eine E-Mail an diese Gruppe gesendet wird. Außerdem wird er in der Gruppenliste angezeigt. Der Anzeigename ist erforderlich und muss aussagekräftig sein, damit andere Personen den Zweck der Gruppe erkennen können. Er muss außerdem innerhalb der Domäne eindeutig sein.

  - **\* Alias**   Dies ist der Teil der E-Mail-Adresse, der links neben dem @-Symbol angezeigt wird. Wenn Sie den Alias ändern, wird die primäre SMTP-Adresse für die Gruppe ebenfalls geändert, die dann den neuen Alias enthält. Zusätzlich bleibt die E-Mail-Adresse mit dem vorherigen Alias als Proxyadresse für die Gruppe erhalten.

  - **Beschreibung**   Verwenden Sie dieses Feld, um die Gruppe zu beschreiben, damit der Zweck der Gruppe ersichtlich wird. Diese Beschreibung wird im Adressbuch und im Detailbereich der Exchange-Verwaltungskonsole angezeigt.

  - **Diese Gruppe in Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, wenn diese Gruppe den Benutzern im Adressbuch nicht angezeigt werden soll. Ein Absender muss den Alias oder die E-Mail-Adresse der Gruppe in die Zeile "An:" oder "Cc:" eingeben, um eine E-Mail an diese Gruppe senden zu können.

  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit an, die die dynamische Verteilergruppe enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um die Gruppe in eine andere Organisationseinheit zu verschieben.

## Besitz

Verwenden Sie diesen Abschnitt, um einen Gruppenbesitzer zuzuweisen. Eine dynamische Verteilergruppe kann nur einen Besitzer haben. Der Gruppenbesitzer wird auf der Registerkarte **Verwaltet von** des Objekts in Active Directory-Benutzer und -Computer angezeigt.

Sie können Besitzer hinzufügen, indem Sie auf **Durchsuchen** klicken und den Besitzer aus der Liste auswählen. Klicken Sie zum Entfernen des Benutzers auf **Löschen**, und klicken Sie anschließend auf **Speichern**.![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

## Mitgliedschaft

In diesem Abschnitt ändern Sie die Kriterien, die zum Festlegen der Gruppenmitgliedschaft verwendet werden. Sie können vorhandene Mitgliedschaftsregeln löschen oder ändern und neue Regeln hinzufügen. Verfahren hierzu finden Sie unter Erstellen einer dynamischen Verteilergruppe mithilfe der Exchange-Verwaltungskonsole in den Verfahren zum Konfigurieren der Mitgliedschaft, wenn Sie eine neue dynamische Verteilergruppe mithilfe der Exchange-Verwaltungskonsole erstellen.

## Zustellungsverwaltung

In diesem Abschnitt können Sie verwalten, von wem E-Mails an diese Gruppe gesendet werden können.

  - **Nur Absender innerhalb meiner Organisation**   Wählen Sie diese Option aus, damit nur Absender in der eigenen Organisation Nachrichten an die Gruppe senden können. Wenn also ein Benutzer außerhalb der Organisation eine E-Mail an diese Gruppe sendet, wird diese abgelehnt. Dies ist die Standardeinstellung.

  - **Absender innerhalb und außerhalb meiner Organisation**   Wählen Sie diese Option aus, damit alle Benutzer Nachrichten an die Gruppe senden können.
    
    Sie können den Kreis der Personen, die Nachrichten an die Gruppe senden können, weiter einschränken, indem Sie es nur bestimmten Absendern gestatten, Nachrichten an diese Gruppe zu senden. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann mindestens einen Empfänger aus. Wenn Sie dieser Liste Absender hinzufügen, sind diese die einzigen, die E-Mails an die Gruppe senden können. E-Mails, die von Personen gesendet werden, die sich nicht in der Liste befinden, werden abgelehnt.
    
    Um eine Person oder eine Gruppe aus der Liste zu entfernen, wählen Sie sie aus und klicken dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").
    

    > [!IMPORTANT]
    > Wenn Sie die Gruppe so konfiguriert haben, dass nur Absender innerhalb Ihrer Organisation Nachrichten an die Gruppe senden dürfen, werden von externen Kontakten gesendete E-Mails auch dann abgelehnt, wenn sie dieser Liste hinzugefügt werden.



## Nachrichtenbestätigung

In diesem Abschnitt können Sie Optionen zum Moderieren der Gruppe festlegen. Moderatoren genehmigen Nachrichten, die an die Gruppe gesendet werden, oder weisen sie zurück, bevor diese die Gruppenmitglieder erreichen.

  - **An diese Gruppe gesendete Nachrichten müssen von einem Moderator genehmigt werden**   Dieses Kontrollkästchen ist nicht standardmäßig aktiviert. Wenn Sie dieses Kontrollkästchen aktivieren, werden eingehende Nachrichten vor der Zustellung von den Gruppenmoderatoren geprüft. Gruppenmoderatoren können eingehende Nachrichten genehmigen oder zurückweisen.

  - **Gruppenmoderatoren**   Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um Gruppenmoderatoren hinzuzufügen. Wenn Sie einen Moderator entfernen möchten, wählen Sie ihn aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"). Wenn Sie das Kontrollkästchen "An diese Gruppe gesendete Nachrichten müssen von einem Moderator genehmigt werden" aktiviert haben und keinen Moderator auswählen, werden Nachrichten an die Gruppe zur Genehmigung an die Besitzer der Gruppe gesendet.

  - **Absender, die keine Nachrichtengenehmigung benötigen**    Klicken Sie zum Hinzufügen von Personen oder Gruppen, die die Moderation dieser Gruppe umgehen können, auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Um eine Person oder Gruppe zu entfernen, wählen Sie das Element aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

  - **Moderationsbenachrichtigungen auswählen   **In diesem Abschnitt können Sie festlegen, wie Benutzer über Nachrichtengenehmigungen benachrichtigt werden.
    
      - **Alle Absender bei Nichtgenehmigung ihrer Nachrichten benachrichtigen**   Dies ist die Standardeinstellung. Mit dieser Option werden alle Absender innerhalb und außerhalb der Organisation benachrichtigt, wenn ihre Nachricht nicht genehmigt wurde.
    
      - **Absender in der Organisation nur bei Nichtgenehmigung ihrer Nachrichten benachrichtigen**   Wenn Sie diese Option wählen, werden nur Personen oder Gruppen in Ihrer Organisation benachrichtigt, wenn eine von ihnen an die Gruppe gesendete Nachricht von einem Moderator nicht genehmigt wurde.
    
      - **Niemanden benachrichtigen, wenn eine Nachricht nicht genehmigt wird**   Wenn Sie diese Option auswählen, erhalten Nachrichtenabsender, deren Nachrichten von den Gruppenmoderatoren nicht genehmigt wurden, keine Benachrichtigungen.

## E-Mail-Optionen

In diesem Abschnitt können Sie die E-Mail-Adressen anzeigen und ändern, die der Gruppe zugeordnet sind. Dazu gehören die primären SMTP-Adressen der Gruppe sowie alle zugeordneten Proxyadressen. Die primäre SMTP-Adresse (auch als *Antwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben.

  - **Hinzufügen **  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue E-Mail-Adresse für dieses Postfach hinzuzufügen. Wählen Sie einen der folgenden Adresstypen aus:
    
      - **SMTP**   Dies ist der Standardadresstyp. Klicken Sie auf diese Schaltfläche, und geben Sie dann die neue SMTP-Adresse in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Damit die neue Adresse die primäre SMTP-Adresse der Gruppe wird, aktivieren Sie das Kontrollkästchen <STRONG>Diese Adresse als Antwortadresse verwenden</STRONG>.

    
      - **Benutzerdefinierter Adresstyp**   Klicken Sie auf diese Schaltfläche, und geben Sie einen der unterstützten Nicht-SMTP-E-Mail-Adresstypen in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Mit Ausnahme von X.400-Adressen überprüft Exchange benutzerdefinierte Adressen nicht auf ordnungsgemäße Formatierung. Sie müssen sicherstellen, dass die von Ihnen angegebene benutzerdefinierte Adresse die Formatanforderungen für den jeweiligen Adresstyp erfüllt.



  - **Bearbeiten**   Wenn Sie eine der Gruppe zugeordnete E-Mail-Adresse ändern möchten, wählen Sie diese in der Liste aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    

    > [!NOTE]
    > Damit eine vorhandene Adresse die primäre SMTP-Adresse der Gruppe wird, aktivieren Sie das Kontrollkästchen <STRONG>Diese Adresse als Antwortadresse verwenden</STRONG>.



  - **Entfernen**   Wenn Sie eine der Gruppe zugeordnete E-Mail-Adresse löschen möchten, wählen Sie diese in der Liste aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden. Diese Option ist standardmäßig aktiviert.

## MailTip

Verwenden Sie diesen Abschnitt, um eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, bevor sie eine Nachricht an diese Gruppe senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn diese Gruppe der Zeile "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird. Sie könnten z. B. großen Gruppen eine E-Mail-Info hinzufügen, um potenzielle Absender zu warnen, dass ihre Nachricht an viele Personen gesendet wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Gruppendelegierung

In diesem Abschnitt können Sie einem Benutzer (der als *Stellvertretung* bezeichnet wird) Berechtigungen zuweisen, sodass der Benutzer Nachrichten als die Gruppe oder im Namen der Gruppe senden kann. Sie können die folgenden Berechtigungen zuweisen:

  - **Senden als**   Diese Berechtigung ermöglicht es der Stellvertretung, Nachrichten als die Gruppe zu senden. Sobald diese Berechtigung zugewiesen ist, kann die Stellvertretung die Gruppe in die Zeile **Von** einfügen, um anzugeben, dass die Nachricht von der Gruppe gesendet wurde.

  - **Senden im Auftrag von**   Diese Berechtigung ermöglicht es der Stellvertretung zusätzlich, Nachrichten im Auftrag der Gruppe zu senden. Nach der Zuweisung dieser Berechtigung kann die Stellvertretung die Gruppe in der Zeile **Von** hinzufügen. Für die Nachricht wird angezeigt, dass sie von der Gruppe gesendet wurde, und der Nachricht ist zu entnehmen, dass sie von der Stellvertretung im Auftrag der Gruppe gesendet wurde.

Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen**, um die Seite **Empfänger auswählen** anzuzeigen, auf der eine Liste mit allen Empfängern in der Exchange-Organisation angezeigt wird, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie seinen Namen in das Suchfeld eingeben und dann auf **Suchen** klicken.

## Ändern der Eigenschaften einer dynamischen Verteilergruppe mithilfe der Shell

Verwenden Sie die Cmdlets **Get-DynamicDistributionGroup** und **Set-DynamicDistributionGroup**, um Eigenschaften für dynamische Verteilergruppen anzuzeigen und zu ändern. Der Vorteil der Shell liegt darin, dass Sie Eigenschaften ändern können, die in der Exchange-Verwaltungskonsole nicht verfügbar sind, und dass Sie die Eigenschaften mehrerer Gruppen ändern können. Informationen dazu, welche Parameter den Eigenschaften der Verteilergruppen entsprechen, finden Sie in diesen Themen:

  - [Get-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb124762\(v=exchg.150\))

  - [Set-DynamicDistributionGroup](https://technet.microsoft.com/de-de/library/bb123796\(v=exchg.150\))

Im Folgenden finden Sie einige Beispiele für das Ändern der Eigenschaften dynamischer Verteilergruppen mithilfe der Shell.

In diesem Beispiel werden die folgenden Parameter für alle dynamischen Verteilergruppen in der Organisation geändert:

  - Ausblenden aller dynamischen Verteilergruppen aus dem Adressbuch

  - Festlegen der maximalen Nachrichtengröße, die an die Gruppe gesendet werden kann, auf 5 MB

  - Aktivieren der Moderation

  - Zuweisen des Administrators als Moderator der Gruppe

<!-- end list -->

    Get-DynamicDistributionGroup -ResultSize unlimited | Set-DynamicDistributionGroup -HiddenFromAddressListsEnabled $true -MaxReceiveSize 5MB -ModerationEnabled $true -ModeratedBy administrator

In diesem Beispiel wird die Proxy-SMTP-E-Mail-Adresse "Seattle.Employees@contoso.com" der Gruppe "Alle Mitarbeiter" hinzugefügt.

    Set-DynamicDistributionGroup -Identity "All Employees" -EmailAddresses SMTP:All.Employees@contoso.com, smtp:Seattle.Employees@contoso.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Eigenschaften einer dynamischen Verteilergruppe erfolgreich geändert wurden:

  - Wählen Sie die Gruppe in der Exchange-Verwaltungskonsole aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder das Feature anzuzeigen, die oder das Sie geändert haben. Je nachdem, welche Eigenschaft Sie geändert haben, wird diese möglicherweise im Detailbereich für die ausgewählte Gruppe angezeigt.

  - In der Shell verwenden Sie das Cmdlet **Get-DynamicDistributionGroup**, um die Änderungen zu überprüfen. Ein Vorteil bei der Verwendung der Shell besteht darin, dass Sie mehrere Eigenschaften für mehrere Gruppen anzeigen können. Im ersten Beispiel führen Sie den folgenden Befehl aus, um die neuen Werte zu überprüfen.
    
        Get-DynamicDistributionGroup -ResultSize unlimited | fl Name,HiddenFromAddressListsEnabled,MaxReceiveSize,ModerationEnabled,ModeratedBy
    
    Führen Sie diesen Befehl für das vorherige Beispiel aus, in dem die Nachrichtengrenzwerte geändert wurden.
    
        Get-Mailbox -OrganizationalUnit "Marketing" | fl Name,IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults

