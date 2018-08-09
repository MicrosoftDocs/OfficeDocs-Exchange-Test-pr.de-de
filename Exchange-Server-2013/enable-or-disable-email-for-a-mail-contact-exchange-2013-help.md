---
title: 'Aktivieren o. Deaktivieren von E-Mail für E-Mail-Kontakt: Exchange 2013-Hilfe'
TOCTitle: Aktivieren oder Deaktivieren von E-Mail für einen E-Mail-Kontakt
ms:assetid: ca47441f-1aa4-4958-aba5-18d51e59837e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124552(v=EXCHG.150)
ms:contentKeyID: 50554924
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren von E-Mail für einen E-Mail-Kontakt

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-12-05_

Sie können E-Mail für einen vorhandenen E-Mail-Kontakt in Ihrer Exchange-Organisation deaktivieren. Wenn Sie E-Mail für einen vorhandenen E-Mail-Kontakt deaktivieren, wird dieser aus Exchange und dem Adressbuch Ihrer Organisation entfernt. Wenn der E-Mail-Kontakt Mitglied einer Verteilergruppe ist, erhält der Kontakt keine an die Gruppe gesendeten E-Mails mehr. Darüber hinaus werden die Exchange-Attribute vom für E-Mail aktivierten Kontaktobjekt in Active Directory entfernt. Der Kontakt selbst und seine nicht auf Exchange bezogenen Attribute (z. B. Kontakt- und Organisationsinformationen) bleiben in Active Directory erhalten.

Nachdem Sie E-Mail für einen E-Mail-Kontakt deaktiviert haben, können Sie den Kontakt mithilfe des Shell-Cmdlets **Enable-MailContact** wieder für E-Mail aktivieren. Mit diesem Cmdlet können Sie auch beliebige Active Directory-Kontakte für E-Mail aktivieren.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf E-Mail-Kontakte finden Sie unter [Verwalten von E-Mail-Kontakten](manage-mail-contacts-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Kontakte" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren von E-Mail für einen E-Mail-Kontakt

Wenn Sie, wie zuvor erwähnt, E-Mail für einen E-Mail-Kontakt deaktivieren, werden die Exchange-Attribute zwar aus dem entsprechenden Active Directory-Kontaktobjekt entfernt, doch der Kontakt bleibt erhalten. Der E-Mail-Kontakt wird aus der Liste der E-Mail-Kontakte in der Exchange-Verwaltungskonsole entfernt. Sie können jedoch das dazugehörige Active Directory-Kontaktobjekt mithilfe von **Active Directory-Benutzer und -Computer** oder in der Shell mit den Cmdlets **Get-Contact** und **Set-Contact** anzeigen und verwalten.

## Deaktivieren von E-Mail für einen E-Mail-Kontakt mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Klicken Sie in der Liste der Kontakte auf den E-Mail-Kontakt, für den Sie E-Mail deaktivieren möchten.

3.  Klicken Sie auf **Mehr**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") und dann auf **Deaktivieren**.

4.  Es wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie den ausgewählten E-Mail-Kontakt wirklich deaktivieren möchten. Klicken Sie auf **Ja**, um ihn zu deaktivieren.

Der E-Mail-Kontakt wird aus der Kontaktliste entfernt.

## Deaktivieren von E-Mail für einen E-Mail-Kontakt mithilfe der Shell

In diesem Beispiel wird E-Mail für den E-Mail-Kontakt Neil Black deaktiviert.

    Disable-MailContact -Identity "Neil Black"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Disable-MailContact](https://technet.microsoft.com/de-de/library/aa997465\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um die erfolgreiche Deaktivierung von E-Mail für einen E-Mail-Kontakt zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Kontakte**, und prüfen Sie, ob der E-Mail-Kontakt nicht mehr aufgeführt ist.

2.  Klicken Sie in **Active Directory-Benutzer und -Computer** mit der rechten Maustaste auf den Kontakt und anschließend auf **Eigenschaften**. Auf der Registerkarte **Allgemein** sehen Sie, dass das Feld **E-Mail** leer ist. Dadurch wird bestätigt, dass der Kontakt nicht für E-Mail aktiviert ist.

3.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-MailContact
    
    Der Kontakt, für den Sie E-Mail deaktiviert haben, wird in den Ergebnissen nicht zurückgegeben, da dieses Cmdlet nur für E-Mail aktivierte Kontakte zurückgibt.

4.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-Contact
    
    Der Kontakt, für den Sie E-Mail deaktiviert haben, wird in den Ergebnissen zurückgegeben, da dieses Cmdlet alle Active Directory-Kontaktobjekte zurückgibt.

## Aktivieren von Kontakten für E-Mail mithilfe der Shell

Verwenden Sie das Cmdlet **Enable-MailContact**, um vorhandene Active Directory-Kontakte für E-Mail zu aktivieren. Sie können einen einzelnen Kontakt für E-Mail aktivieren oder mithilfe einer CSV-Datei mehrere Kontakte für E-Mail aktivieren.

## Aktivieren eines einzelnen Kontakts für E-Mail mithilfe der Shell

In diesem Beispiel wird der Kontakt Rene Valdes für E-Mail aktiviert. Sie müssen eine externe E-Mail-Adresse angeben.

    Enable-MailContact -Identity "Rene Valdes" -ExternalEmailAddress renev@tailspintoys.com

## Aktivieren mehrerer Kontakte für E-Mail mithilfe der Shell und einer CSV-Datei

Wenn Sie zahlreiche Kontakte für E-Mail aktivieren möchten, müssen Sie zunächst die Liste der nicht für E-Mail aktivierten Kontakte in eine CSV-Datei (mit Trennzeichen getrennte Werte) exportieren. Fügen Sie anschließend mithilfe eines Texteditors wie Windows Editor oder einer Tabellenkalkulationsanwendung wie Microsoft Excel die externen E-Mail-Adressen der CSV-Datei hinzu. Geben Sie danach die aktualisierte CSV-Datei im Shell-Befehl zum Aktivieren der Kontakte in der CSV-Datei für E-Mail an.

1.  Führen Sie den folgenden Befehl aus, um eine Liste vorhandener nicht für E-Mail aktivierter Kontakte in eine Datei auf dem Desktop des Administrators mit dem Namen **Contacts.csv** zu exportieren.
    
        Get-Contact | Where { $_.RecipientType -eq "Contact" } | Out-File "C:\Users\Administrator\Desktop\Contacts.csv"
    
    Die resultierende Datei ähnelt der folgenden Datei:
    
        Name
        Walter Harp
        James Alvord
        Rainer Witt
        Susan Burk
        Ian Tien
        ...

2.  Fügen Sie die Spaltenüberschrift **E-Mail-Adresse** und anschließend eine E-Mail-Adresse für jeden Kontakt in der Datei hinzu. Der Name und die externe E-Mail-Adresse jedes Kontakts müssen durch ein Komma getrennt werden. Die aktualisierte CSV-Datei sollte nun ungefähr so aussehen:
    
        Name,EmailAddress
        James Alvord,james@contoso.com
        Susan Burk,sburk@tailspintoys.com
        Walter Harp,wharp@tailspintoys.com
        Ian Tien,iant@tailspintoys.com
        Rainer Witt,rainerw@fourthcoffee.com
        ...

3.  Führen Sie den folgenden Befehl aus, um mithilfe der Daten in der CSV-Datei die Kontakte in der Datei für E-Mail zu aktivieren.
    
        Import-CSV C:\Users\Administrator\Desktop\Contacts.csv | ForEach-Object {Enable-MailContact -Identity $_.Name -ExternalEmailAddress $_.EmailAddress}
    
    Die Befehlsergebnisse zeigen Informationen zu den neu für E-Mail aktivierten Kontakten.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um die erfolgreiche Aktivierung von Active Directory-Kontakten für E-Mail zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**. Neue E-Mail-Kontakte werden in der Kontaktliste angezeigt. Unter **Kontakttyp** lautet der Typ **E-Mail-Kontakt**.
    

    > [!NOTE]
    > Sie müssen ggf. auf <STRONG>Aktualisieren</STRONG><IMG title="Aktualisieren (Symbol)" alt="Aktualisieren (Symbol)" src="images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif"> klicken, um die neuen E-Mail-Kontakte anzuzeigen.



  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zu neuen E-Mail-Kontakten anzuzeigen.
    
        Get-MailContact | Format-Table Name,RecipientTypeDetails,ExternalEmailAddress

