---
title: 'Verwalten von E-Mail-aktivierten Sicherheitsgruppen: Exchange 2013 Help'
TOCTitle: Verwalten von E-Mail-aktivierten Sicherheitsgruppen
ms:assetid: 80b3b537-4786-4d02-9202-44e373811a25
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123521(v=EXCHG.150)
ms:contentKeyID: 50474805
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von E-Mail-aktivierten Sicherheitsgruppen

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-10-04_

Eine E-Mail-aktivierte Sicherheitsgruppe kann zum Verteilen von Nachrichten sowie zur Erteilung von Zugriffsberechtigungen für Ressourcen in Active Directory verwendet werden. Weitere Informationen finden Sie unter [Empfänger](recipients-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 bis 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Erstellen einer E-Mail-aktivierten Sicherheitsgruppe

## Erstellen einer Sicherheitsgruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Gruppen**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") \> **Sicherheitsgruppe**.

3.  Füllen Sie auf der Seite **Neue Sicherheitsgruppe** die folgenden Felder aus:
    
      - **\* Anzeigename**   Verwenden Sie dieses Feld, um den Anzeigenamen einzugeben. Dieser Name wird im freigegebenen Adressbuch in der Zeile "An:" angezeigt, wenn eine E-Mail an diese Gruppe gesendet wird. Außerdem wird er in der Gruppenliste in der Exchange-Verwaltungskonsole angezeigt. Der Anzeigename ist erforderlich und muss aussagekräftig sein, damit andere Personen den Zweck der Gruppe erkennen können. Dieser Name muss auch in der Gesamtstruktur eindeutig sein.
        

        > [!NOTE]
        > Wenn eine Gruppenbenennungsrichtlinie angewendet wird, müssen die für Ihre Organisation erzwungenen Benennungseinschränkungen beachtet werden. Weitere Informationen finden Sie unter <A href="create-a-distribution-group-naming-policy-exchange-2013-help.md">Erstellen einer Benennungsrichtlinie für Verteilergruppen</A>. Informationen zum Außerkraftsetzen der Gruppenbenennungsrichtlinie Ihrer Organisation finden Sie unter <A href="override-the-distribution-group-naming-policy-exchange-2013-help.md">Außerkraftsetzen der Benennungsrichtlinie für Verteilergruppen</A>.

    
      - **\* Alias**   Verwenden Sie dieses Feld, um den Alias für die Sicherheitsgruppe einzugeben. Der Alias darf höchstens 64 Zeichen umfassen und muss in der Gesamtstruktur eindeutig sein. Wenn ein Benutzer den Alias in der Zeile "An:" einer E-Mail eingibt, wird er in den Anzeigenamen der Gruppe aufgelöst.
    
      - **Beschreibung**   Verwenden Sie dieses Feld, um die Sicherheitsgruppe zu beschreiben, damit der Zweck der Gruppe ersichtlich wird.
    
      - **Organisationseinheit**   Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container "Benutzer" in der Active Directory-Domäne festgelegt, in der sich der Computer befindet, auf dem die Exchange-Verwaltungskonsole ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container Benutzer ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten der Gesamtstruktur angezeigt, die sich in einem bestimmten Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie auf **OK**.
    
      - **\* Besitzer**   Standardmäßig ist die Person, die eine Gruppe erstellt, der Besitzer. Jede Gruppe muss mindestens einen Besitzer aufweisen. Sie können Besitzer hinzufügen, indem Sie auf **Hinzufügen** klicken.
    
      - **Mitglieder**   Verwenden Sie diesen Abschnitt zum Hinzufügen von Mitglieder und um anzugeben, ob eine Genehmigung erforderlich ist, damit Personen der Gruppe beitreten bzw. diese verlassen können.
        
        Besitzer von Gruppen müssen nicht Mitglied der Gruppe sein. Verwenden Sie die Option **Gruppenbesitzer als Mitglieder hinzufügen**, um die Besitzer als Mitglieder hinzuzufügen bzw. zu entfernen.
        
        Klicken Sie zum Hinzufügen von Mitgliedern zur Gruppe auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wenn Sie mit dem Hinzufügen von Mitgliedern fertig sind, klicken Sie auf **OK**, um zur Seite **Neue Sicherheitsgruppe** zurückzukehren.
        
        Aktivieren Sie das Kontrollkästchen **Genehmigung durch Besitzer erforderlich**, wenn Gruppenbesitzer Benutzeranforderungen zum Beitritt zur Gruppe erhalten sollen. Wenn Sie diese Option auswählen, können Mitglieder nur durch die Gruppenbesitzer entfernt werden.

4.  Klicken Sie nach Abschluss dieses Vorgangs auf **Speichern**, um die Sicherheitsgruppe zu erstellen.


> [!NOTE]
> Standardmäßig ist für alle neuen E-Mail-aktivierten Sicherheitsgruppen die Authentifizierung aller Absender erforderlich. Auf diese Weise wird verhindert, dass externe Absender Nachrichten an E-Mail-aktivierte Sicherheitsgruppen senden können. Um eine E-Mail-aktivierte Sicherheitsgruppe für das Annehmen von Nachrichten von allen Absendern zu konfigurieren, müssen Sie die Einstellungen für die Einschränkungen der Nachrichtenübermittlung für die betreffende Gruppe ändern.



## Verwenden der Shell zum Erstellen einer Sicherheitsgruppe

In diesem Beispiel wird eine Sicherheitsgruppe mit dem Alias "fsadmin" und dem Namen "File Server Managers" erstellt. Die Sicherheitsgruppe wird in der Standardorganisationseinheit erstellt, und jeder kann dieser Gruppe mit Genehmigung durch die Gruppenbesitzer beitreten.

    New-DistributionGroup -Name "File Server Managers" -Alias fsadmin -Type security

Weitere Informationen dazu, wie Sie E-Mail-aktivierte Sicherheitsgruppen mithilfe der Shell erstellen, finden Sie unter [New-DistributionGroup](https://technet.microsoft.com/de-de/library/aa998856\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung einer E-Mail-aktivierten Sicherheitsgruppe zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Gruppen**. Die neue E-Mail-aktivierte Sicherheitsgruppe wird in der Gruppenliste angezeigt. Unter **Gruppentyp** lautet der Typ **Sicherheitsgruppe**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zur neuen E-Mail-aktivierten Sicherheitsgruppe anzuzeigen.
    
        Get-DistributionGroup <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress

## Ändern der Eigenschaften von E-Mail-aktivierten Sicherheitsgruppen

## Ändern der Eigenschaften von E-Mail-aktivierten Sicherheitsgruppen mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Gruppen**.

2.  Klicken Sie in der Gruppenliste auf die E-Mail-aktivierte Sicherheitsgruppe, deren Eigenschaften Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite für die Gruppe auf einen der folgenden Abschnitte, um Eigenschaften anzuzeigen oder zu ändern.
    
      - Allgemein
    
      - Besitz
    
      - Mitgliedschaft
    
      - Genehmigung der Mitgliedschaft
    
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

  - **Diese Gruppe in Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, wenn diese Gruppe den Benutzern im Adressbuch nicht angezeigt werden soll. Wenn dieses Kontrollkästchen aktiviert ist, muss ein Absender den Alias oder die E-Mail-Adresse der Gruppe in die Zeile "An:" oder "Cc:" eingeben, um eine E-Mail an die Gruppe zu senden.
    

    > [!TIP]
    > Blenden Sie ggf. Sicherheitsgruppen aus, da sie normalerweise zum Zuweisen von Berechtigungen zu Gruppenmitgliedern und nicht zum Senden von E-Mails verwendet werden.



  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit an, die die Sicherheitsgruppe enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um die Gruppe in eine andere Organisationseinheit zu verschieben.

## Besitz

Verwenden Sie diesen Abschnitt, um Gruppenbesitzer zuzuweisen. Der Gruppenbesitzer kann der Gruppe Mitglieder hinzufügen und Beitrittsanforderungen genehmigen oder ablehnen. Standardmäßig ist die Person, die eine Gruppe erstellt, deren Besitzer. Jede Gruppe muss mindestens einen Besitzer aufweisen.

Sie können Besitzer hinzufügen, indem Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken. Sie können einen Besitzer entfernen, indem Sie ihn auswählen und auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)") klicken.

## Mitgliedschaft

Verwenden Sie diesen Abschnitt, um Mitglieder hinzuzufügen oder zu entfernen. Besitzer von Gruppen müssen nicht Mitglied der Gruppe sein. Unterhalb von **Mitglieder** können Sie Mitglieder hinzufügen, indem Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken. Sie können ein Mitglied entfernen, indem Sie einen Benutzer in der Mitgliederliste auswählen und anschließend auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)") klicken.

## Genehmigung der Mitgliedschaft

In diesem Abschnitt können Sie angeben, ob eine Genehmigung durch den oder die Besitzer erforderlich ist, damit Benutzer der Gruppe beitreten können. Wenn Sie das Kontrollkästchen **Genehmigung durch Besitzer erforderlich** aktivieren, wird eine E-Mail an den oder die Gruppenbesitzer gesendet, in der die Genehmigung zum Beitritt angefordert wird. Wie bereits erwähnt, können nur Besitzer Mitglieder aus der Gruppe entfernen.


> [!NOTE]
> Diese Option funktioniert aufgrund von Sicherheitseinschränkungen nicht mit E-Mail-aktivierten Sicherheitsgruppen.



## Zustellungsverwaltung

In diesem Abschnitt können Sie verwalten, von wem E-Mails an diese Gruppe gesendet werden können.

  - **Nur Absender innerhalb meiner Organisation**   Wählen Sie diese Option aus, damit nur Absender in der eigenen Organisation Nachrichten an die Gruppe senden können. Wenn also ein Benutzer außerhalb der Organisation eine E-Mail an diese Gruppe sendet, wird diese abgelehnt. Dies ist die Standardeinstellung.

  - **Absender innerhalb und außerhalb meiner Organisation**   Wählen Sie diese Option aus, damit alle Benutzer Nachrichten an die Gruppe senden können.
    
    Sie können den Kreis der Personen, die Nachrichten an die Gruppe senden können, weiter einschränken, indem Sie es nur bestimmten Absendern gestatten, Nachrichten an diese Gruppe zu senden. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann mindestens einen Empfänger aus. Wenn Sie dieser Liste Absender hinzufügen, sind diese die einzigen, die E-Mails an die Gruppe senden können. E-Mails, die von Personen gesendet werden, die sich nicht in der Liste befinden, werden abgelehnt.
    
    Um eine Person oder eine Gruppe aus der Liste zu entfernen, wählen Sie sie aus und klicken dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").
    

    > [!IMPORTANT]
    > Wenn Sie die Gruppe so konfiguriert haben, dass nur Absender innerhalb Ihrer Organisation Nachrichten an die Gruppe senden dürfen, werden von externen Kontakten gesendete E-Mails abgelehnt, auch wenn sie dieser Liste hinzugefügt werden.



## Nachrichtenbestätigung

In diesem Abschnitt können Sie Optionen zum Moderieren der Gruppe festlegen. Moderatoren genehmigen Nachrichten, die an die Gruppe gesendet werden, oder weisen sie zurück, bevor diese die Gruppenmitglieder erreichen.

  - **An diese Gruppe gesendete Nachrichten müssen von einem Moderator genehmigt werden**   Dieses Kontrollkästchen ist nicht standardmäßig aktiviert. Wenn Sie dieses Kontrollkästchen aktivieren, werden eingehende Nachrichten vor der Zustellung von den Gruppenmoderatoren geprüft. Gruppenmoderatoren können eingehende Nachrichten genehmigen oder zurückweisen.

  - **Gruppenmoderatoren**   Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um Gruppenmoderatoren hinzuzufügen. Wenn Sie einen Moderator entfernen möchten, wählen Sie ihn aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"). Wenn Sie das Kontrollkästchen An diese Gruppe gesendete Nachrichten müssen von einem Moderator genehmigt werden aktiviert haben und keinen Moderator auswählen, werden Nachrichten an die Gruppe zur Genehmigung an die Besitzer der Gruppe gesendet.

  - **Absender, die keine Nachrichtengenehmigung benötigen**   Klicken Sie zum Hinzufügen von Personen oder Gruppen, die die Moderation dieser Gruppe umgehen können, auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Um eine Person oder Gruppe zu entfernen, wählen Sie das Element aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

  - **Moderationsbenachrichtigungen auswählen   **In diesem Abschnitt können Sie festlegen, wie Benutzer über Nachrichtengenehmigungen benachrichtigt werden.
    
      - **Alle Absender bei Nichtgenehmigung ihrer Nachrichten benachrichtigen**   Dies ist die Standardeinstellung. Absender innerhalb und außerhalb Ihrer Organisation werden benachrichtig, wenn ihre Nachrichten nicht genehmigt werden.
    
      - **Absender innerhalb Ihrer Organisation benachrichtigen, wenn ihre Nachrichten nicht genehmigt wurden**   Wenn Sie diese Option wählen, werden nur Personen oder Gruppen in Ihrer Organisation benachrichtigt, wenn eine von diesen an die Gruppe gesendete Nachricht von einem Moderator nicht genehmigt wurde.
    
      - **Niemanden benachrichtigen, wenn eine Nachricht nicht genehmigt wird**   Wenn Sie diese Option auswählen, erhalten Nachrichtenabsender, deren Nachrichten von den Gruppenmoderatoren nicht genehmigt wurden, keine Benachrichtigungen.

## E-Mail-Optionen

In diesem Abschnitt können Sie die E-Mail-Adressen anzeigen und ändern, die der Gruppe zugeordnet sind. Dazu gehören die primären SMTP-Adressen der Gruppe sowie alle zugeordneten Proxyadressen. Die primäre SMTP-Adresse (auch als *Antwortadresse* bezeichnet) wird fettgedruckt in der Adressliste angezeigt. Der Wert **SMTP** in der Spalte **Typ** wird dabei in Großbuchstaben angegeben.

  - **Hinzufügen **  Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue E-Mail-Adresse für dieses Postfach hinzuzufügen. Wählen Sie einen der folgenden Adresstypen aus:
    
      - **SMTP**   Dies ist der Standardadresstyp. Klicken Sie auf diese Schaltfläche, und geben Sie dann die neue SMTP-Adresse in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Damit die neue Adresse die primäre SMTP-Adresse der Gruppe wird, aktivieren Sie das Kontrollkästchen <STRONG>Diese Adresse als Antwortadresse verwenden</STRONG>. Dieses Kontrollkästchen wird nur angezeigt, wenn das Kontrollkästchen <STRONG>E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren</STRONG> deaktiviert ist.

    
      - **Benutzerdefinierter Adresstyp**   Klicken Sie auf diese Schaltfläche, und geben Sie einen der unterstützten Nicht-SMTP-E-Mail-Adresstypen in das Feld **\* E-Mail-Adresse** ein.
        

        > [!NOTE]
        > Mit Ausnahme von X.400-Adressen überprüft Exchange benutzerdefinierte Adressen nicht auf ordnungsgemäße Formatierung. Sie müssen sicherstellen, dass die von Ihnen angegebene benutzerdefinierte Adresse die Formatanforderungen für den jeweiligen Adresstyp erfüllt.



  - **Bearbeiten**   Wenn Sie eine der Gruppe zugeordnete E-Mail-Adresse ändern möchten, markieren Sie diese in der Liste, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    

    > [!NOTE]
    > Damit eine vorhandene Adresse die primäre SMTP-Adresse der Gruppe wird, aktivieren Sie das Kontrollkästchen <STRONG>Diese Adresse als Antwortadresse verwenden</STRONG>. Wie bereits erwähnt, wird dieses Kontrollkästchen nur angezeigt, wenn das Kontrollkästchen <STRONG>E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren</STRONG> deaktiviert ist.



  - **Entfernen**   Wenn Sie eine der Gruppe zugeordnete E-Mail-Adresse löschen möchten, markieren Sie diese in der Liste, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## MailTip

Verwenden Sie diesen Abschnitt, um eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, bevor sie eine Nachricht an diese Gruppe senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn diese Gruppe der Zeile "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird. Sie könnten z. B. großen Gruppen eine E-Mail-Info hinzufügen, um potenzielle Absender zu warnen, dass ihre Nachricht an viele Personen gesendet wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Gruppendelegierung

In diesem Abschnitt können Sie einem Benutzer (der als *Stellvertretung* bezeichnet wird) Berechtigungen zuweisen, sodass der Benutzer Nachrichten als die Gruppe oder im Namen der Gruppe senden kann. Sie können die folgenden Berechtigungen zuweisen:

  - **Senden als**   Diese Berechtigung ermöglicht es der Stellvertretung, Nachrichten als die Gruppe zu senden. Sobald diese Berechtigung zugewiesen ist, kann die Stellvertretung die Gruppe in die Zeile **Von** einfügen, um anzugeben, dass die Nachricht von der Gruppe gesendet wurde.

  - **Senden im Auftrag von**   Diese Berechtigung ermöglicht es der Stellvertretung zusätzlich, Nachrichten im Auftrag der Gruppe zu senden. Nach der Zuweisung dieser Berechtigung kann die Stellvertretung die Gruppe in der Zeile **Von** hinzufügen. Für die Nachricht wird angezeigt, dass sie von der Gruppe gesendet wurde, und der Nachricht ist zu entnehmen, dass sie von der Stellvertretung im Auftrag der Gruppe gesendet wurde.

Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen**, um die Seite **Empfänger auswählen** anzuzeigen, auf der eine Liste mit allen Empfängern in der Exchange-Organisation angezeigt wird, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie den Empfängernamen in das Suchfeld eingeben und dann auf **Suchen**![Suchen (Symbol)](images/Dn624163.773574d0-9b92-4cab-9f6b-81532c7418b9(EXCHG.150).gif "Suchen (Symbol)") klicken.

## Ändern der Eigenschaften von Sicherheitsgruppen mithilfe der Shell

Verwenden Sie die Cmdlets **Get-DistributionGroup** und **Set-DistributionGroup**, um Eigenschaften für Sicherheitsgruppen anzuzeigen und zu ändern. Der Vorteil der Shell liegt darin, dass Sie Eigenschaften ändern können, die in der Exchange-Verwaltungskonsole nicht verfügbar sind, und dass Sie die Eigenschaften mehrerer Sicherheitsgruppen ändern können. Informationen dazu, welche Parameter welchen Verteilergruppeneigenschaften entsprechen, finden Sie in diesen Themen:

  - [Get-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124755\(v=exchg.150\))

  - [Set-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124955\(v=exchg.150\))

Im Folgenden finden Sie einige Beispiele, wie Sie Eigenschaften von Sicherheitsgruppen mithilfe der Shell ändern können.

In diesem Beispiel wird eine Liste aller Sicherheitsgruppen in der Organisation angezeigt.

    Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalSecurityGroup')}

In diesem Beispiel wird die primäre SMTP-Adresse (auch als Antwortadresse bezeichnet) für die Sicherheitsgruppe "Seattle Administrators" von "admins@contoso.com" zu "seattle.admins@contoso.com" geändert. Die vorherige Antwortadresse wird als Proxyadresse beibehalten.

    Set-DistributionGroup "Seattle Employees" -EmailAddresses SMTP:sea.admins@contoso.com,smtp:admins@contoso.com

In diesem Beispiel werden alle Sicherheitsgruppen in der Organisation aus dem Adressbuch ausgeblendet.

    Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalSecurityGroup')} | Set-DistributionGroup -HiddenFromAddressListsEnabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Eigenschaften einer Sicherheitsgruppe erfolgreich geändert wurden:

  - Wählen Sie die Gruppe in der Exchange-Verwaltungskonsole aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder das Feature anzuzeigen, die oder das Sie geändert haben. Je nachdem, welche Eigenschaft Sie geändert haben, wird diese möglicherweise im Detailbereich für die ausgewählte Gruppe angezeigt.

  - In der Shell verwenden Sie das Cmdlet **Get-DistributionGroup**, um die Änderungen zu überprüfen. Ein Vorteil bei der Verwendung der Shell besteht darin, dass Sie mehrere Eigenschaften für mehrere Gruppen anzeigen können. Führen Sie im oben stehenden Beispiel, in dem alle Sicherheitsgruppen aus dem Adressbuch ausgeblendet wurden, folgenden Befehl aus, um den neuen Wert zu überprüfen.
    
        Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalSecurityGroup')} |
         fl Name,HiddenFromAddressListsEnabled


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

