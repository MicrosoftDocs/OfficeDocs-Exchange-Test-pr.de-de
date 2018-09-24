---
title: 'Konfig. v. Exchange f. Annehmen v. Nachr. f. mehrere autoritative Domänen'
TOCTitle: Konfigurieren von Exchange für das Annehmen von Nachrichten für mehrere autoritative Domänen
ms:assetid: 11801f73-4934-4025-a1c1-3935dada7e9b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996314(v=EXCHG.150)
ms:contentKeyID: 51409266
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von Exchange für das Annehmen von Nachrichten für mehrere autoritative Domänen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-06-15_

In Microsoft Exchange Server 2013 können Ihrer Organisation ganz leicht mehrere autoritative Domänen hinzugefügt werden. Nach dem Hinzufügen der autoritativen Domäne müssen Sie jedoch entscheiden, wie diese in Ihrer Organisation verwendet werden soll. Beispiel:

  - Wenn Sie für Empfänger in Ihrer Organisation eine E-Mail-Adresse in der neuen autoritativen Domäne hinzufügen möchten: Soll die vorhandene primäre Antwortadresse für die Empfänger ersetzt werden, oder soll die neue E-Mail-Adresse als (sekundäre) Proxyadresse hinzugefügt werden?

  - Möchten Sie, dass die E-Mail-Adresse in der neuen autoritativen Domäne für alle Empfänger und alle Empfängertypen gilt? Oder soll die neue E-Mail-Adresse auf bestimmte Empfängertypen oder, je nach ihren Benutzereigenschaften, auf bestimmte Empfänger angewendet werden, beispielsweise nur auf Benutzer in der Finanzabteilung?

Die folgenden Beispiele beschreiben Szenarien, in denen Ihre Exchange-Organisation möglicherweise E-Mail für mehr als eine autorisierende SMTP-Domäne empfangen und verarbeiten muss:

  - Sie ändern den Namen Ihrer SMTP-Domäne, müssen jedoch für eine Zeitlang weiterhin E-Mail für den alten Domänennamen akzeptieren, da Kunden möglicherweise E-Mail-Nachrichten an die früheren E-Mail-Adressen senden. Sie können die neue E-Mail-Adresse als primäre Adresse (Antwortadresse) festlegen. Dies bedeutet, dass die neue Adresse als Standard-E-Mail-Adresse verwendet wird, die auf allen vom Empfänger gesendeten E-Mail-Nachrichten angezeigt wird. Sie können die alte E-Mail-Adresse als sekundäre Adresse festlegen. Dadurch kann der Empfänger weiterhin E-Mail empfangen, die an die alte E-Mail-Adresse gesendet wird.

  - Sie möchten verschiedene E-Mail-Adressen für Unternehmenseinheiten innerhalb Ihrer Organisation bereitstellen. Wenn z. B. die Active Directory-Gesamtstruktur "contoso.com" Unterdomänen für die Tochterunternehmen "Tailspin Toys" und "Fourth Coffee" enthält, kann es sinnvoll sein, den Empfängern in diesen jeweiligen Unternehmenseinheiten die SMTP-Domänennamen "contoso.com", "tailspintoys.com" und "fourthcoffee.com" zuzuweisen.

  - Sie bieten E-Mail-Hostdienste an und müssen E-Mail für mehrere SMTP-Domänennamen akzeptieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Akzeptierte Domänen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md) und "E-Mail-Adressrichtlinien" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Besteht in Ihrem Umkreisnetzwerk ein Edge-Transport-Serverabonnement, konfigurieren Sie akzeptierte Domänen auf einem Postfachserver in Ihrer Exchange-Organisation. Während der EdgeSync-Synchronisierung wird die Konfiguration der akzeptierten Domänen auf dem Edge-Transport-Server repliziert. Weitere Informationen finden Sie unter [Edge-Abonnements](edge-subscriptions-exchange-2013-help.md).

  - Beim Erstellen einer akzeptierten Domäne können Platzhalterzeichen (\*) im Adressraum verwendet werden, um anzugeben, dass alle Unterdomänen des SMTP-Adressraums ebenfalls von der Exchange-Organisation akzeptiert werden. Wenn Sie z. B. "contoso.com" und sämtliche Unterdomänen als akzeptierte Domänen konfigurieren möchten, geben Sie **\*.contoso.com** als SMTP-Adressraum an. Wenn die Namen der Unterdomänen jedoch in einer Richtlinie für E-Mail-Adressen verwendet werden, muss jede Unterdomäne explizit als akzeptierte Domäne eingetragen sein.

  - Ein MX-Eintrag im öffentlichen DNS ist für jede SMTP-Domäne erforderlich, für die Sie E-Mail aus dem Internet annehmen. Jeder MX-Eintrag muss sich in den für das Internet verwendeten Server auflösen, der E-Mails für Ihre Organisation empfängt.

  - Sie müssen Sendeconnectors and Empfangsconnectors konfigurieren, damit Ihre Exchange-Organisation E-Mail an das Internet senden und daraus empfangen kann. Die Konfiguration der Internetsendeconnectors und -empfangsconnectors wird durch Ihre Exchange-Topologie bestimmt. Weitere Informationen zum Konfigurieren von Connectors finden Sie unter [Connectors](connectors-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen einer autoritativen Domäne

## Erstellen einer autoritativen Domäne mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Akzeptierte Domänen**, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie im Feld **Name** den Anzeigenamen für die akzeptierte Domäne ein. Jede akzeptierte Domäne für Ihre Organisation muss über einen eindeutigen Anzeigenamen verfügen. Dieser Name kann von der akzeptierten Domäne abweichen. Beispielsweise könnte die Domäne "contoso.com" über den Anzeigenamen "Lokale akzeptierte Contoso-Domäne" verfügen.

3.  Geben Sie im Feld **Akzeptierte Domäne** einen SMTP-Namensraum an, für den Ihre Organisation E-Mails annimmt. Beispiel: "contoso.com".

4.  Wählen Sie **Autoritative Domäne** aus.

5.  Klicken Sie auf **Speichern**.

## Erstellen einer autoritativen Domäne mithilfe der Shell

Verwenden Sie folgende Syntax, um eine neue autoritative Domäne zu erstellen.

    New-AcceptedDomain -Name "<Unique Name>" -DomainName <SMTP domain> -DomainType Authoritative

Beispielsweise erstellen Sie eine neue autoritative Domäne namens "Fourth Coffee subsidiary" für die Domäne "fourthcoffee.com" mithilfe des folgenden Befehls:

    New-AcceptedDomain -Name "Fourth Coffee subsidiary" -DomainName fourthcoffee.com -DomainType Authoritative

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine autoritative Domäne erfolgreich erstellt wurde:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Akzeptierte Domänen**. Stellen Sie sicher, dass die von Ihnen erstellte akzeptierte Domäne angezeigt wird und **Domänentyp** den Wert **Autoritativ** aufweist.

  - Führen Sie in der Shell den Befehl **Get-AcceptedDomain** aus. Stellen Sie sicher, dass die von Ihnen erstellte Domäne angezeigt wird und **DomainType** den Wert `Authoritative` aufweist.

## Schritt 2: Konfigurieren einer E-Mail-Adressrichtlinie für die autoritative Domäne

Damit Sie die von Ihnen erstellte autoritative akzeptierte Domäne verwenden können, müssen Sie eine E-Mail-Adressrichtlinie für die autoritative Domäne konfigurieren, die den Zielen Ihres Szenarios entspricht. Möglicherweise müssen Sie eine neue E-Mail-Adressrichtlinie erstellen oder eine vorhandene Richtlinie ändern. Sie können wählen, ob Sie die primäre E-Mail-Adresse für einige oder alle Empfänger ersetzen möchten oder ob die alte primäre E-Mail-Adresse beibehalten oder entfernt werden soll. In diesem Abschnitt werden zwei Beispielszenarien vorgestellt.

## Ändern der bestehenden primären E-Mail-Adresse

Führen Sie die folgenden Schritte aus, um die den Empfängern zugeordnete primäre E-Mail-Adresse (Antwortadresse) zu ändern und die alte primäre E-Mail-Adresse als sekundäre Proxy-E-Mail-Adresse beizubehalten:

## Ändern der bestehenden primären E-Mail-Adresse mithilfe der Exchange-Verwaltungskonsole

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **E-Mail-Adressrichtlinien**. Wählen Sie die E-Mail-Adressrichtlinie aus, die Sie ändern möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **E-Mail-Adressrichtlinie** auf die Registerkarte **E-Mail-Adressformat**. Klicken Sie im Abschnitt **E-Mail-Adressformat** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Treffen Sie auf der daraufhin angezeigten Seite **E-Mail-Adressformat** die folgende Auswahl:
    
      - **Akzeptierte Domäne auswählen**   Klicken Sie auf die Dropdownliste, und wählen Sie die neue autoritative Domäne aus.
    
      - Wählen Sie **Dieses Format für Adresse der Antwort-E-Mail verwenden**.
    
    Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

4.  Klicken Sie auf der Seite **E-Mail-Adressrichtlinie** auf **Speichern**, um Ihre Änderungen an der Richtlinie zu speichern.

5.  Es wird eine Warnung angezeigt, dass die E-Mail-Adressrichtlinie nicht angewendet wird, bevor sie aktualisiert wurde. Nach der Erstellung wählen Sie sie aus und klicken anschließend im Detailbereich auf **Anwenden**.

## Ändern der vorhandenen primären E-Mail-Adresse mithilfe der Shell

In der Shell verwenden Sie zwei separate Befehle: einen Befehl zum Ändern der vorhandenen E-Mail-Adressrichtlinie und einen weiteren Befehl zum Anwenden der aktualisierten E-Mail-Adressrichtlinie auf die Empfänger in Ihrer Organisation.

Führen Sie den folgenden Befehl aus, um die vorhandene primäre E-Mail-Adresse zu ändern und die alte primäre E-Mail-Adresse als Proxyadresse beizubehalten:

    Set-EmailAddressPolicy <EmailAddressPolicyIdentity> -EnabledEmailAddressTemplates SMTP:<NewPrimaryEmailAddress>,smtp:<OldPrimaryEmailAddress>

Nehmen Sie beispielsweise an, die E-Mail-Adressrichtlinie in Ihrer Organisation verwendet das E-Mail-Adressformat *useralias*`@contoso.com`. In diesem Beispiel wird die Domäne der primären Adresse (Antwortadresse) in der E-Mail-Adressrichtlinie namens "Default Policy" in `@fourthcoffee.com` geändert und die alte primäre Antwortadresse in der Domäne `@contoso.com` als (sekundäre) Proxyadresse beibehalten.

    Set-EmailAddressPolicy "Default Policy" -EnabledEmailAddressTemplates SMTP:@fourthcoffee.com,smtp:@contoso.com


> [!NOTE]
> Der <CODE>SMTP</CODE>-Qualifizierer in Großbuchstaben gibt die primäre Adresse (Antwortadresse) an. Der <CODE>smtp</CODE>-Qualifizierer in Kleinbuchstaben gibt eine (sekundäre) Proxyadresse an.



Verwenden Sie folgende Syntax, um die aktualisierte E-Mail-Adressrichtlinie auf Empfänger anzuwenden.

    Update-EmailAddressPolicy <EamilAddressPolicyIdentity>

Führen Sie beispielsweise den folgenden Befehl aus, um eine aktualisierte E-Mail-Adressrichtlinie namens "Default Policy" anzuwenden:

    Update-EmailAddressPolicy "Default Policy"

## Ersetzen der vorhandenen primären E-Mail-Adresse für eine gefilterte Auswahl von Empfängern

Die E-Mail-Standardadressrichtlinie kann nicht so geändert werden, dass sie für eine gefilterte Auswahl von Empfängern gilt. Sie müssen eine neue E-Mail-Adressrichtlinie erstellen oder eine vorhandene benutzerdefinierte E-Mail-Adressrichtlinie ändern. In den Beispielen in diesem Abschnitt wird eine neue E-Mail-Adressrichtlinie erstellt. In diesen Beispielen ersetzt die primäre Adresse (Antwortadresse) in der neuen akzeptierten Domäne die alte primäre Adresse für die angegebenen Empfänger, ohne dass die alte primäre Adresse als (sekundäre) Proxy-E-Mail-Adresse beibehalten wird. Daher können die betroffenen Empfänger unter ihrer alten primären E-Mail-Adresse keine weitere E-Mail empfangen.

Außerdem soll den E-Mail-Adressrichtlinien, die für bestimmte Benutzer gelten, eine höhere Priorität eingeräumt werden (niedrigerer Ganzzahlwert) als anderen E-Mail-Adressrichtlinien, einschließlich der Standardrichtlinie, damit die spezifische Richtlinie als Erste angewendet wird. Da zwei Richtlinien nicht denselben Prioritätswert besitzen können, müssen Sie zunächst die Priorität der E-Mail-Standardadressrichtlinie Ihrer Organisation verringern.

## Ersetzen der vorhandenen primären E-Mail-Adresse für eine gefilterte Auswahl von Empfängern mithilfe der Exchange-Verwaltungskonsole

Führen Sie diese Schritte aus, um weitere E-Mail-Adressen zu erstellen, die als primäre E-Mail-Adresse für eine gefilterte Auswahl von Empfängern verwendet werden sollen:

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **E-Mail-Adressrichtlinien**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Füllen Sie auf der Seite **E-Mail-Adressrichtlinie** die folgenden Felder aus:
    
    1.  **Richtlinienname**   Geben Sie einen eindeutigen, beschreibenden Namen ein.
    
    2.  **E-Mail-Adressformat**   Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Treffen Sie auf der daraufhin angezeigten Seite **E-Mail-Adressformat** die folgende Auswahl:
        
          - **Akzeptierte Domäne auswählen**   Klicken Sie auf die Dropdownliste, und wählen Sie die neue autoritative Domäne aus.
        
          - **E-Mail-Adressformat**   Wählen Sie das geeignete E-Mail-Adressformat für Ihre Organisation aus.
        
          - Wählen Sie **Dieses Format für Adresse der Antwort-E-Mail verwenden**.
        
        Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

3.  **Diese Richtlinie in dieser Reihenfolge mit anderen Richtlinien ausführen**   Normalerweise sollte Richtlinien, die für bestimmte Benutzer gelten, eine höhere Priorität eingeräumt werden (niedrigerer Ganzzahlwert) als anderen E-Mail-Adressrichtlinien, einschließlich der Standardrichtlinie.

4.  **Geben Sie die Empfängertypen an, auf die diese E-Mail-Adressrichtlinie angewendet wird**   Wählen Sie die Empfängertypen aus, auf die die E-Mail-Adressrichtlinie angewendet werden soll.

5.  **Erstellen Sie Regeln, um die Empfänger, auf die diese E-Mail-Adressrichtlinie angewendet wird, weiter zu definieren**   Klicken Sie auf **Regeln hinzufügen**, um die Empfänger einzuschränken, auf die diese Richtlinie angewendet werden soll. Dadurch wird eine boolesche **AND**-Anweisung erstellt. Wiederholen Sie diesen Schritt so oft wie nötig.
    

    > [!WARNING]
    > Wenn Sie zu viele Regeln anwenden, kann es passieren, dass die E-Mail-Adressrichtlinie so weit eingeschränkt wird, dass keine Benutzer mehr enthalten sind.



6.  Klicken Sie auf **Vorschau auf Empfänger anzeigen, für die die Richtlinie gilt**, um die Empfänger anzuzeigen, auf die diese Richtlinie angewendet wird.

7.  Klicken Sie auf **OK**, um Ihre Änderungen zu speichern und die Richtlinie zu erstellen.

8.  Es wird eine Warnung angezeigt, dass die E-Mail-Adressrichtlinie nicht angewendet wird, bevor sie aktualisiert wurde. Nach der Erstellung wählen Sie sie aus und klicken anschließend im Detailbereich auf **Anwenden**.

## Ersetzen der vorhandenen primären E-Mail-Adresse für eine gefilterte Auswahl von Empfängern mithilfe der Shell

Verwenden Sie den folgenden Befehl, um die primäre E-Mail-Adresse für eine gefilterte Auswahl von Empfängern zu ersetzen:

    New-EmailAddressPolicy -Name <Policy Name> -Priority <Integer> -IncludedRecipients <RecipientTypes> <Conditional Recipient Properties> -EnabledEmailAddressTemplates SMTP:@<NewPrimaryEmailAddress>

In diesem Beispiel wird eine E-Mail-Adressrichtlinie namens "Fourth Coffee Recipients" erstellt und Postfachbenutzern in der Abteilung "Fourth Coffee" zugewiesen. Ferner wird für diese E-Mail-Adressrichtlinie die höchste Priorität festgelegt, sodass die Richtlinie als Erste angewendet wird. Beachten Sie, dass die alte primäre E-Mail-Adresse für diese Empfänger nicht beibehalten wird, sodass sie unter ihrer alten primären E-Mail-Adresse keine weitere E-Mail empfangen können.

    New-EmailAddressPolicy -Name "Fourth Coffee Recipients" -Priority 1 -IncludedRecipients MailboxUsers -ConditionalDepartment "Fourth Coffee" -EnabledEmailAddressTemplates SMTP:@fourthcoffee.com

Führen Sie den folgenden Befehl aus, um die neue E-Mail-Adressrichtlinie auf die betreffenden Empfänger anzuwenden:

    Update-EmailAddressPolicy "Fourth Coffee Recipients"

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um sicherzustellen, dass für die autoritative Domäne erfolgreich eine E-Mail-Adressrichtlinie konfiguriert wurde:

  - Wechseln Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **E-Mail-Adressrichtlinien**. Überprüfen Sie, ob die Richtlinien in der richtigen Reihenfolge angewendet werden. Wählen Sie außerdem neue oder aktualisierte Richtlinien aus, und überprüfen Sie im Detailbereich das E-Mail-Adressformat, die eingeschlossenen Empfänger und, ob die Richtlinie angewendet wurde.

  - Führen Sie in der Shell die Befehle **Get-EmailAddressPolicy** und `Get-EmailAddressPolicy "<Policy Name>"| Format-List` aus, um die Details der Richtlinien zu überprüfen.

## Woher wissen Sie, dass diese Aufgabe erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass Exchange für die Annahme von E-Mail für mehrerer autoritative Domänen konfiguriert wurde:

1.  Senden Sie Testnachrichten von einem Postfach außerhalb Ihrer Exchange-Organisation aus an einen betroffenen Empfänger. Überprüfen Sie die E-Mail-Adressen, die E-Mail erfolgreich akzeptieren.

2.  Senden Sie Testnachrichten von einem betroffenen Empfängerpostfach aus an einen externen Empfänger, und überprüfen Sie die Von-Adresse der Nachricht.

