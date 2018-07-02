---
title: 'Erstellen und Verwalten von Verteilergruppen: Exchange 2013 Help'
TOCTitle: Erstellen und Verwalten von Verteilergruppen
ms:assetid: c4c43493-55e1-46d2-bd4b-d6f6cecd747f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124513(v=EXCHG.150)
ms:contentKeyID: 50476661
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.CreateDistributionGroupWizardForm.CreateDistributionGroupIntroductionWizardPage
ms.translationtype: HT
---

# Erstellen und Verwalten von Verteilergruppen

 

_**Gilt für:** Exchange Online, Exchange Server 2016, Office 365_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Verwenden Sie das Exchange Admin Center (EAC) oder die Exchange-Verwaltungsshell, um in der Exchange-Organisation eine neue Verteilergruppe zu erstellen oder in Active Directory eine vorhandene Gruppe für E-Mails zu aktivieren.

Es gibt zwei Arten von Gruppen, die zum Verteilen von Nachrichten verwendet werden können:

  - *E-Mail-aktivierte universelle Verteilergruppen* (werden auch als *Verteilergruppen* bezeichnet) können ausschließlich zum Verteilen von Nachrichten verwendet werden.

  - *E-Mail-aktivierte universelle Sicherheitsgruppen* (werden auch als *Sicherheitsgruppen* bezeichnet) können zum Verteilen von Nachrichten sowie zur Erteilung von Zugriffsberechtigungen für Ressourcen in Active Directory verwendet werden. Weitere Informationen finden Sie unter [Verwalten von E-Mail-aktivierten Sicherheitsgruppen](manage-mail-enabled-security-groups-exchange-2013-help.md).

Beachten Sie, dass sich die Terminologie zwischen Active Directory und Exchange unterscheidet. In Active Directory verweist eine Verteilergruppe auf eine beliebige Gruppe ohne Sicherheitskontext, unabhängig davon, ob diese E-Mail-aktiviert ist oder nicht. Im Gegensatz dazu werden alle E-Mail-aktivierten Gruppen in Exchange Verteilergruppen genannt, unabhängig davon, ob sie in einen Sicherheitskontext eingebunden sind oder nicht.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 2 bis 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verteilergruppen" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Wenn in Ihrer Organisation eine Gruppenbenennungsrichtlinie konfiguriert wurde, wird sie nur auf Gruppen angewendet, die von Benutzern erstellt werden. Wenn Sie oder andere Administratoren mithilfe der Exchange-Verwaltungskonsole Verteilergruppen erstellen, wird die Gruppenbenennungsrichtlinie ignoriert und nicht auf den Gruppennamen angewendet. Wenn Sie jedoch mit der Shell eine Verteilergruppe erstellen oder umbenennen, wird die Richtlinie angewendet, sofern Sie nicht mit dem Parameter *IgnoreNamingPolicy* die Gruppenbenennungsrichtlinie außer Kraft setzen. Weitere Informationen finden Sie unter:
    
      - [Erstellen einer Benennungsrichtlinie für Verteilergruppen](create-a-distribution-group-naming-policy-exchange-2013-help.md)
    
      - [Außerkraftsetzen der Benennungsrichtlinie für Verteilergruppen](override-the-distribution-group-naming-policy-exchange-2013-help.md)

## Was möchten Sie machen?

## Erstellen einer Verteilergruppe

## Erstellen einer Verteilergruppe mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Gruppen**.

2.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") \> **Verteilergruppe**.

3.  
    

    > [!TIP]
    > <IMG title="Neue Office 365-Testgruppen" alt="Neue Office 365-Testgruppen" src="images/Bb124513.3ea82c95-9dda-450f-823b-cd0772249d81(EXCHG.150).png"><BR>Sie können nun eine Office 365-Gruppe statt einer Verteilergruppe erstellen, wenn Sie über einen Office 365-Plan für Unternehmen oder ein Exchange Online-Plan verfügen. Office 365-Gruppen verfügen über die Features von Verteilergruppen und vieles mehr. Mit Office 365-Gruppen können Sie E-Mails an eine Gruppe senden, einen gemeinsamen Kalender freigeben, eine Bibliothek zum Speichern und Bearbeiten von Gruppendateien und -Ordnern verwenden. Klicken Sie zum Einstieg auf <STRONG>Neu</STRONG><IMG title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif">&nbsp;&gt;&nbsp;<STRONG>Office 365-Gruppe</STRONG>, und lesen Sie die Informationen unter <A href="https://go.microsoft.com/fwlink/p/?linkid=800653">Administratorhilfe zu Office 365-Gruppen</A>.<BR>Wenn Sie vorhandene Verteilergruppen haben, die Sie zu Office 365-Gruppen migrieren möchten, lesen Sie <A href="https://go.microsoft.com/fwlink/p/?linkid=824756">Migrieren von Verteilerlisten zu Office 365-Gruppen – Administratorhilfe</A>.<BR>Wenn Sie weiterhin eine Verteilergruppe erstellen möchten, klicken oder tippen Sie auf den Assistenten für <STRONG>Neue Verteilergruppe</STRONG>.



4.  
    
    Füllen Sie auf der Seite **Neue Verteilergruppe** die folgenden Felder aus:
    
      - **\* Anzeigename**   Verwenden Sie dieses Feld, um den Anzeigenamen einzugeben. Dieser Name wird im Adressbuch der Organisation in der Zeile "An:" angezeigt, wenn eine E-Mail an diese Gruppe gesendet wird. Außerdem wird er in der Gruppenliste in der Exchange-Verwaltungskonsole angezeigt. Der Anzeigename ist erforderlich und muss aussagekräftig sein, damit andere Personen den Zweck der Gruppe erkennen können. Dieser Name muss auch in der Gesamtstruktur eindeutig sein.
    
      - **\* Alias**   Verwenden Sie dieses Feld, um den Aliasnamen der Gruppe einzugeben. Der Alias darf höchstens 64 Zeichen umfassen und muss in der Gesamtstruktur eindeutig sein. Wenn ein Benutzer den Alias in der Zeile "An:" einer E-Mail eingibt, wird er in den Anzeigenamen der Gruppe aufgelöst.
    
      - **Organisationseinheit**   (Diese Option wird nur lokal in Exchange 2013 angezeigt) Sie können eine andere Organisationseinheit (OU) als die Standardeinheit auswählen (die dem Empfängerbereich entspricht). Wenn für den Empfängerbereich die Gesamtstruktur festgelegt ist, wird der Standardwert auf den Container "Benutzer" in der Active Directory-Domäne festgelegt, in der sich der Computer befindet, auf dem die Exchange-Verwaltungskonsole ausgeführt wird. Wenn der Empfängerbereich auf eine bestimmte Domäne festgelegt ist, wird standardmäßig der in dieser Domäne vorhandene Container „Benutzer“ ausgewählt. Wenn der Empfängerbereich auf eine bestimmte Organisationseinheit festgelegt ist, wird diese standardmäßig ausgewählt.
        
        Um eine andere Organisationseinheit auszuwählen, klicken Sie auf **Durchsuchen**. In diesem Dialogfeld werden alle Organisationseinheiten der Gesamtstruktur angezeigt, die sich in einem bestimmten Bereich befinden. Wählen Sie die gewünschte Organisationseinheit aus, und klicken Sie dann auf **OK**.
    
      - **\* Besitzer**   Standardmäßig ist die Person, die eine Gruppe erstellt, der Besitzer. Jede Gruppe muss mindestens einen Besitzer aufweisen. Sie können Besitzer hinzufügen, indem Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken.
    
      - **Mitglieder**   Verwenden Sie diesen Abschnitt zum Hinzufügen von Mitglieder und um anzugeben, ob eine Genehmigung erforderlich ist, damit Personen der Gruppe beitreten bzw. diese verlassen können.
        
        Besitzer von Gruppen müssen nicht Mitglied der Gruppe sein. Verwenden Sie die Option **Gruppenbesitzer als Mitglieder hinzufügen**, um die Besitzer als Mitglieder hinzuzufügen bzw. zu entfernen.
        
        Klicken Sie zum Hinzufügen von Mitgliedern zur Gruppe auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wenn Sie mit dem Hinzufügen von Mitgliedern fertig sind, klicken Sie auf **OK**, um zur Seite **Neue Verteilergruppe** zurückzukehren.
        
        Geben Sie unter **Wählen Sie aus, ob für den Beitritt zur Gruppe eine Besitzergenehmigung erforderlich ist** an, ob eine Genehmigung erforderlich ist, damit Benutzer der Gruppe beitreten können. Wählen Sie eine der folgenden Einstellungen aus:
        
          - **Offen: Jeder kann dieser Gruppe ohne Genehmigung durch die Gruppenbesitzer beitreten**   Dies ist die Standardeinstellung.
        
          - **Geschlossen: Mitglieder können nur von den Gruppenbesitzern hinzugefügt werden. Alle Beitrittsanforderungen werden automatisch zurückgewiesen**
        
          - **Genehmigung durch Besitzer: Alle Anforderungen werden von den Gruppenbesitzern manuell genehmigt oder abgelehnt**   Wenn Sie diese Option auswählen, erhalten die Gruppenbesitzer eine E-Mail, in der die Genehmigung für den Beitritt zur Gruppe angefordert wird.
        
        Geben Sie unter **Wählen Sie aus, ob die Gruppe zum Verlassen geöffnet ist** an, ob eine Genehmigung erforderlich ist, wenn Benutzer die Gruppe verlassen möchten. Wählen Sie eine der folgenden Einstellungen aus:
        
          - **Offen: Jeder kann diese Gruppe ohne Genehmigung durch die Gruppenbesitzer verlassen**   Dies ist die Standardeinstellung.
        
          - **Geschlossen: Mitglieder können nur von den Gruppenbesitzern entfernt werden. Alle Anforderungen zum Verlassen werden automatisch zurückgewiesen   **

5.  Wenn Sie fertig sind, klicken Sie auf **Speichern**, um die Verteilergruppe erstellen.


> [!NOTE]
> Standardmäßig ist für neue Verteilergruppen die Authentifizierung aller Absender erforderlich. Auf diese Weise wird verhindert, dass externe Absender Nachrichten an Verteilergruppen senden können. Um eine Verteilergruppe für das Annehmen von Nachrichten von allen Absendern zu konfigurieren, müssen Sie die Einstellungen für die Einschränkungen der Nachrichtenübermittlung für die betreffende Verteilergruppe ändern.



## Erstellen einer Verteilergruppe mithilfe der Shell

In diesem Beispiel wird eine Verteilergruppe mit dem Alias **itadmin** und dem Namen **IT Administrators** erstellt. Die Verteilergruppe wird in der Standardorganisationseinheit erstellt, und jeder kann ohne Genehmigung der Gruppenbesitzer dieser Gruppe beitreten.

    New-DistributionGroup -Name "IT Administrators" -Alias itadmin -MemberJoinRestriction open

Weitere Informationen zur Verwendung der Shell zum Erstellen von Verteilergruppen finden Sie unter [New-DistributionGroup](https://technet.microsoft.com/de-de/library/aa998856\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Erstellung einer Verteilergruppe zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Gruppen**. Die neue Verteilergruppe wird in der Gruppenliste angezeigt. Unter **Gruppentyp** lautet der Typ **Verteilergruppe**.

  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zur neuen Verteilergruppe anzuzeigen.
    
        Get-DistributionGroup <Name> | FL Name,RecipientTypeDetails,PrimarySmtpAddress


> [!NOTE]
> Sie können nur universelle Verteilergruppen erstellen bzw. für E-Mail aktivieren. Zum Konvertieren einer lokalen Gruppe der Domäne oder einer globalen Gruppe in eine universelle Gruppe können Sie das Cmdlet <A href="https://technet.microsoft.com/de-de/library/bb123770(v=exchg.150)">Set-Group</A> in der Shell verwenden. Möglicherweise verfügen Sie über E-Mail-aktivierte Gruppen, die aus früheren Versionen von Exchange migriert wurden und bei denen es sich nicht um universelle Gruppen handelt. Sie können diese Gruppen mithilfe der Exchange-Verwaltungskonsole oder der Shell verwalten



## Ändern von Verteilergruppeneigenschaften

## Ändern von Verteilergruppeneigenschaften mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Gruppen**.

2.  Klicken Sie in der Liste der Gruppen auf die Verteilergruppe, die Sie anzeigen oder ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

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
    
    Wenn Sie eine Gruppenbenennungsrichtlinie implementiert haben, muss der Anzeigename dem von der Richtlinie definierten Namensformat entsprechen.

  - **\* Alias**   Dies ist der Teil der E-Mail-Adresse, der link neben dem @-Symbol´angezeigt wird. Wenn Sie den Alias ändern, wird die primäre SMTP-Adresse für die Gruppe ebenfalls geändert, die dann den neuen Alias enthält. Zusätzlich bleibt die E-Mail-Adresse mit dem vorherigen Alias als Proxyadresse für die Gruppe erhalten.

  - **Beschreibung**   Verwenden Sie dieses Feld, um die Gruppe zu beschreiben, damit der Zweck der Gruppe ersichtlich wird. Diese Beschreibung wird im Adressbuch und im Detailbereich der Exchange-Verwaltungskonsole angezeigt.

  - **Diese Gruppe in Adresslisten ausblenden**   Aktivieren Sie dieses Kontrollkästchen, wenn diese Gruppe den Benutzern im Adressbuch nicht angezeigt werden soll. Ein Absender muss den Alias oder die E-Mail-Adresse der Gruppe in die Zeile "An:" oder "Cc:" eingeben, um eine E-Mail an diese Gruppe senden zu können.
    

    > [!TIP]
    > Blenden Sie ggf. Sicherheitsgruppen aus, da sie normalerweise zum Zuweisen von Berechtigungen zu Gruppenmitgliedern und nicht zum Senden von E-Mails verwendet werden.



  - **Organisationseinheit**   Dieses schreibgeschützte Feld zeigt die Organisationseinheit (Organizational Unit, OU) an, die die Verteilergruppe enthält. Sie müssen "Active Directory-Benutzer und -Computer" verwenden, um die Gruppe in eine andere Organisationseinheit zu verschieben.

## Besitz

Verwenden Sie diesen Abschnitt, um Gruppenbesitzer zuzuweisen. Der Gruppenbesitzer kann der Gruppe Mitglieder hinzufügen, Beitritts- oder Austrittsanfragen genehmigen oder ablehnen sowie an die Gruppe gesendete Nachrichten genehmigen oder ablehnen. Standardmäßig ist die Person, die eine Gruppe erstellt, deren Besitzer. Jede Gruppe muss mindestens einen Besitzer aufweisen.

Sie können Besitzer hinzufügen, indem Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken. Sie können einen Besitzer entfernen, indem Sie ihn auswählen und auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)") klicken.

## Mitgliedschaft

Verwenden Sie diesen Abschnitt, um Mitglieder hinzuzufügen oder zu entfernen. Besitzer von Gruppen müssen nicht Mitglied der Gruppe sein. Unterhalb von **Mitglieder** können Sie Mitglieder hinzufügen, indem Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken. Sie können ein Mitglied entfernen, indem Sie einen Benutzer in der Mitgliederliste auswählen und anschließend auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)") klicken.

## Genehmigung der Mitgliedschaft

In diesem Abschnitt können Sie angeben, ob eine Genehmigung erforderlich ist, damit Benutzer der Gruppe beitreten bzw. diese verlassen können.

  - **Wählen Sie aus, ob für den Beitritt zur Gruppe eine Besitzergenehmigung erforderlich ist**   Wählen Sie eine der folgenden Einstellungen aus:
    
      - **Offen: Jeder Benutzer kann dieser Gruppe ohne Genehmigung durch die Gruppenbesitzer beitreten**
    
      - **Geschlossen: Mitglieder können nur von den Gruppenbesitzern hinzugefügt werden. Alle Beitrittsanforderungen werden automatisch zurückgewiesen**
    
      - **Genehmigung durch Besitzer: Alle Anforderungen werden von den Gruppenbesitzern genehmigt oder abgelehnt**   Wenn Sie diese Option auswählen, erhalten die Gruppenbesitzer eine E-Mail, in der die Genehmigung für den Beitritt zur Gruppe angefordert wird.

  - **Wählen Sie aus, ob die Gruppe zum Verlassen geöffnet ist   **Wählen Sie eine der folgenden Einstellungen aus:
    
      - **Offen: Jeder Benutzer kann die Gruppe ohne Genehmigung durch die Gruppenbesitzer verlassen   **
    
      - **Geschlossen: Mitglieder können nur von den Gruppenbesitzern entfernt werden. Alle Anforderungen zum Verlassen werden automatisch zurückgewiesen   **

## Zustellungsverwaltung

In diesem Abschnitt können Sie verwalten, von wem E-Mails an diese Gruppe gesendet werden können.

  - **Nur Absender innerhalb meiner Organisation**   Wählen Sie diese Option aus, damit nur Absender in der eigenen Organisation Nachrichten an die Gruppe senden können. Wenn also ein Benutzer außerhalb der Organisation eine E-Mail an diese Gruppe sendet, wird diese abgelehnt. Dies ist die Standardeinstellung.

  - **Absender innerhalb und außerhalb meiner Organisation**   Wählen Sie diese Option aus, damit alle Benutzer Nachrichten an die Gruppe senden können.
    
    Sie können den Kreis der Personen, die Nachrichten an die Gruppe senden können, weiter einschränken, indem Sie es nur bestimmten Absendern gestatten, Nachrichten an diese Gruppe zu senden. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie dann mindestens einen Empfänger aus. Wenn Sie dieser Liste Absender hinzufügen, sind diese die einzigen, die E-Mails an die Gruppe senden können. E-Mails, die von Personen gesendet werden, die sich nicht in der Liste befinden, werden abgelehnt.
    
    Um eine Person oder eine Gruppe aus der Liste zu entfernen, wählen Sie sie aus und klicken dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").
    

    > [!IMPORTANT]
    > Wenn Sie die Gruppe so konfiguriert haben, dass nur Absender in der Organisation Nachrichten an die Gruppe senden dürfen, werden von E-Mail-Kontakten gesendete E-Mails abgelehnt, auch wenn sie dieser Liste hinzugefügt werden.



## Nachrichtenbestätigung

In diesem Abschnitt können Sie Optionen zum Moderieren der Gruppe festlegen. Moderatoren genehmigen Nachrichten, die an die Gruppe gesendet werden, oder weisen sie zurück, bevor diese die Gruppenmitglieder erreichen.

  - **An diese Gruppe gesendete Nachrichten müssen von einem Moderator genehmigt werden**   Dieses Kontrollkästchen ist nicht standardmäßig aktiviert. Wenn Sie dieses Kontrollkästchen aktivieren, werden eingehende Nachrichten vor der Zustellung von den Gruppenmoderatoren geprüft. Gruppenmoderatoren können eingehende Nachrichten genehmigen oder zurückweisen.

  - **Gruppenmoderatoren**   Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um Gruppenmoderatoren hinzuzufügen. Wenn Sie einen Moderator entfernen möchten, wählen Sie ihn aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"). Wenn Sie das Kontrollkästchen "An diese Gruppe gesendete Nachrichten müssen von einem Moderator genehmigt werden" aktiviert haben und keinen Moderator auswählen, werden Nachrichten an die Gruppe zur Genehmigung an die Besitzer der Gruppe gesendet.

  - **Absender, die keine Nachrichtengenehmigung benötigen**    Klicken Sie zum Hinzufügen von Personen oder Gruppen, die die Moderation dieser Gruppe umgehen können, auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Um eine Person oder Gruppe zu entfernen, wählen Sie das Element aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

  - **Moderationsbenachrichtigungen auswählen   **In diesem Abschnitt können Sie festlegen, wie Benutzer über Nachrichtengenehmigungen benachrichtigt werden.
    
      - **Alle Absender bei Nichtgenehmigung ihrer Nachrichten benachrichtigen**   Dies ist die Standardeinstellung. Mit dieser Option werden alle Absender innerhalb und außerhalb der Organisation benachrichtigt, wenn ihre Nachricht nicht genehmigt wurde.
    
      - **Absender innerhalb Ihrer Organisation benachrichtigen, wenn ihre Nachrichten nicht genehmigt wurden**   Wenn Sie diese Option wählen, werden nur Personen oder Gruppen in Ihrer Organisation benachrichtigt, wenn eine von diesen an die Gruppe gesendete Nachricht von einem Moderator nicht genehmigt wurde.
    
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



  - **Bearbeiten**   Wenn Sie eine der Gruppe zugeordnete E-Mail-Adresse ändern möchten, markieren Sie diese in der Liste, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    

    > [!NOTE]
    > Damit eine vorhandene Adresse die primäre SMTP-Adresse der Gruppe wird, aktivieren Sie das Kontrollkästchen <STRONG>Diese Adresse als Antwortadresse verwenden</STRONG>.



  - **Entfernen**   Wenn Sie eine der Gruppe zugeordnete E-Mail-Adresse löschen möchten, markieren Sie diese in der Liste, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

  - **E-Mail-Adressen basierend auf der E-Mail-Adressrichtlinie für diesen Empfänger automatisch aktualisieren**   Aktivieren Sie dieses Kontrollkästchen, damit die E-Mail-Adressen des Empfängers automatisch aktualisiert werden, wenn Änderungen an den E-Mail-Adressrichtlinien in Ihrer Organisation vorgenommen wurden. Diese Option ist standardmäßig aktiviert.

## MailTip

Verwenden Sie diesen Abschnitt, um eine E-Mail-Info hinzuzufügen, in der Benutzer vor möglichen Problemen gewarnt werden, wenn sie eine Nachricht an diese Gruppe senden. Eine E-Mail-Info ist Text, der in der Infoleiste angezeigt wird, wenn diese Gruppe der Zeile "An", "Cc" oder "Bcc" einer neuen E-Mail hinzugefügt wird. Sie könnten z. B. großen Gruppen eine E-Mail-Info hinzufügen, um potenzielle Absender zu warnen, dass ihre Nachricht an viele Personen gesendet wird.


> [!NOTE]
> Eine E-Mail-Info kann HTML-Tags enthalten, Skripts sind jedoch nicht zulässig. Die Länge einer benutzerdefinierten E-Mail-Info darf 175&nbsp;angezeigte Zeichen nicht überschreiten. HTML-Tags werden bei diesem Zeichenlimit nicht mitgezählt.



## Gruppendelegierung

In diesem Abschnitt können Sie einem Benutzer (der als *Stellvertretung* bezeichnet wird) Berechtigungen zuweisen, sodass der Benutzer Nachrichten als die Gruppe oder im Namen der Gruppe senden kann. Sie können die folgenden Berechtigungen zuweisen:

  - **Senden als**   Diese Berechtigung ermöglicht es der Stellvertretung, Nachrichten als die Gruppe zu senden. Sobald diese Berechtigung zugewiesen ist, kann die Stellvertretung die Gruppe in die Zeile **Von** einfügen, um anzugeben, dass die Nachricht von der Gruppe gesendet wurde.

  - **Senden im Auftrag von**   Diese Berechtigung ermöglicht es der Stellvertretung zusätzlich, Nachrichten im Auftrag der Gruppe zu senden. Nach der Zuweisung dieser Berechtigung kann die Stellvertretung die Gruppe in der Zeile **Von** hinzufügen. Für die Nachricht wird angezeigt, dass sie von der Gruppe gesendet wurde, und der Nachricht ist zu entnehmen, dass sie von der Stellvertretung im Auftrag der Gruppe gesendet wurde.

Wenn Sie einer Stellvertretung eine Berechtigung zuweisen möchten, klicken Sie unter der entsprechenden Berechtigung auf **Hinzufügen**, um die Seite **Empfänger auswählen** anzuzeigen, auf der eine Liste mit allen Empfängern in der Exchange-Organisation angezeigt wird, denen die Berechtigung zugewiesen werden kann. Wählen Sie die gewünschten Empfänger aus, fügen Sie diese der Liste hinzu, und klicken Sie dann auf **OK**. Sie können auch nach einem bestimmten Empfänger suchen, indem Sie seinen Namen in das Suchfeld eingeben und dann auf **Suchen** klicken.

## Ändern von Verteilergruppeneigenschaften mithilfe der Shell

Verwenden Sie die Cmdlets **Get-DistributionGroup** und **Set-DistributionGroup**, um Eigenschaften für Verteilergruppen anzuzeigen und zu ändern. Die Vorteile der Verwendung der Shell sind die Möglichkeit, Eigenschaften, die in der Exchange-Verwaltungskonsole nicht verfügbar sind, und Eigenschaften für mehrere Gruppen zu ändern. Informationen dazu, welche Parameter den Verteilergruppeneigenschaften entsprechen, finden Sie in den folgenden Themen:

  - [Get-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124755\(v=exchg.150\))

  - [Set-DistributionGroup](https://technet.microsoft.com/de-de/library/bb124955\(v=exchg.150\))

Hier finden Sie einige Beispiele dafür, wie Sie mit der Shell Verteilergruppeneigenschaften ändern können.

In diesem Beispiel wird die primäre SMTP-Adresse (wird auch als Antwortadresse bezeichnet) für die Verteilergruppe "Seattle Employees" von "employees@contoso.com" in "sea.employees@contoso.com" geändert. Zudem wird die vorherige Adresse als Proxyadresse beibehalten.

    Set-DistributionGroup "Seattle Employees" -EmailAddresses SMTP:sea.employees@contoso.com,smtp:employees@contoso.com

In diesem Beispiel wird die maximale Größe von Nachrichten, die an alle Verteilergruppen in der Organisation gesendet werden können, auf 10 Megabytes (MB) beschränkt.

    Get-DistributionGroup -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailUniversalDistributionGroup')} | Set-DistributionGroup -MaxReceiveSize 10MB

In diesem Beispiel wird die Moderation für die Verteilergruppe "Customer Support" aktiviert und der Moderator auf "Amy" festgelegt. Zusätzlich werden für diese moderierte Verteilergruppe Absender, die Mail aus der Organisation senden, darüber benachrichtigt, wenn ihre Nachrichten nicht genehmigt werden.

    Set-DistributionGroup -Identity "Customer Support" -ModeratedBy "Amy" -ModerationEnabled $true -SendModerationNotifications 'Internal'

In diesem Beispiel wird die durch einen Benutzer erstellte Verteilergruppe "Dog Lovers" so geändert, dass der Gruppenleiter Benutzeranforderungen zum Gruppenbeitritt genehmigen muss. Zusätzlich wird durch Verwendung des Parameters *BypassSecurityGroupManagerCheck* der Gruppenleiter nicht über Änderungen benachrichtigt, die an den Einstellungen der Verteilergruppe vorgenommen wurden.

    Set-DistributionGroup -Identity "Dog Lovers" -MemberJoinRestriction 'ApprovalRequired' -BypassSecurityGroupManagerCheck

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Schritte aus, um die erfolgreiche Änderung von Verteilergruppeneigenschaften zu überprüfen:

  - Wählen Sie die Gruppe in der Exchange-Verwaltungskonsole aus, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um die Eigenschaft oder das Feature anzuzeigen, die oder das Sie geändert haben. Je nachdem, welche Eigenschaft Sie geändert haben, wird diese möglicherweise im Detailbereich für die ausgewählte Gruppe angezeigt.

  - In der Shell verwenden Sie das Cmdlet **Get-DistributionGroup**, um die Änderungen zu überprüfen. Ein Vorteil bei der Verwendung der Shell besteht darin, dass Sie mehrere Eigenschaften für mehrere Gruppen anzeigen können. Führen Sie im oben stehenden Beispiel, in dem die Empfängergrenzwert geändert wurde, folgenden Befehl aus, um den neuen Wert zu überprüfen.
    
        Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | fl Name,RecipientLimits
    
    Führen Sie diesen Befehl für das vorherige Beispiel aus, in dem die Nachrichtengrenzwerte geändert wurden.
    
        Get-Mailbox -OrganizationalUnit "Marketing" | fl Name,IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults

