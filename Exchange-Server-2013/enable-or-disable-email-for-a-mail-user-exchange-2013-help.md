---
title: 'Aktivieren oder Deaktivieren von E-Mail für einen E-Mail-Benutzer: Exchange 2013 Help'
TOCTitle: Aktivieren oder Deaktivieren von E-Mail für einen E-Mail-Benutzer
ms:assetid: 1e2571d4-ff84-4fda-bb1d-825e96e1bd26
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996598(v=EXCHG.150)
ms:contentKeyID: 50554794
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren oder Deaktivieren von E-Mail für einen E-Mail-Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-14_

Sie können E-Mails für einen vorhandenen E-Mail-Benutzer in der Exchange-Organisation deaktivieren. Wenn Sie E-Mails für einen E-Mail-Benutzer deaktivieren, wird er aus Exchange und dem Adressbuch der Organisation entfernt. Wenn der E-Mail-Benutzer Mitglied einer Verteilergruppe ist, erhält der Benutzer keine E-Mails mehr, die an die Gruppe gesendet werden. Zudem werden die Exchange-Attribute vom Benutzerobjekt in Active Directory entfernt, aber das Benutzerobjekt und seine Attribute, die sich nicht auf Exchange beziehen (wie Kontakt- und Organisationsinformationen), bleiben in Active Directory erhalten.

Nach der Deaktivierung von E-Mails für einen E-Mail-Benutzer können Sie den Benutzer wieder für E-Mails aktivieren, indem Sie das Cmdlet **Enable-MailUser** in der Shell verwenden. Mit diesem Cmdlet können Sie auch beliebige Active Directory-Benutzer für E-Mails aktivieren.


> [!NOTE]
> E-Mail-Benutzer (oder auch <EM>E-Mail-aktivierte Benutzer</EM>) unterscheiden sich von den Benutzern in der Organisation, die über ein Postfach verfügen. Der wichtigste Unterschied ist, dass E-Mail-Benutzer Benutzer außerhalb Ihrer Exchange-Organisation darstellen, die eine externe E-Mail-Adresse haben. Sie besitzen kein Postfach in Ihrer Organisation. Weitere Informationen zu den Unterschieden zwischen Benutzern, die über Postfächer in Ihrer Organisation verfügen, und E-Mail-Benutzern finden Sie unter <A href="recipients-exchange-2013-help.md">Empfänger</A>.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit E-Mail-Benutzern finden Sie unter [Verwalten von E-Mail-Benutzern](manage-mail-users-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 2 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachbenutzer" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Deaktivieren von E-Mails für einen E-Mail-Benutzer

Wie bereits dargestellt, werden bei der Deaktivierung von E-Mails für einen E-Mail-Benutzer die Exchange-Attribute vom entsprechenden E-Mail-Benutzerobjekt in Active Directory entfernt, der Benutzer bleibt aber erhalten. Der E-Mail-Benutzer wird aus der Liste der E-Mail-Benutzer in der Exchange-Verwaltungskonsole entfernt, Sie können aber das entsprechende Active Directory-Kontaktobjekt über Active Directory-Benutzer und -Computer oder mit den Cmdlets **Get-MailUser** und **Set-Set-MailUser** in der Shell anzeigen und verwalten.

## Deaktivieren von E-Mails für einen E-Mail-Benutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**.

2.  Klicken Sie in der Liste der Kontakte auf den E-Mail-Benutzer, für den Sie E-Mails deaktivieren möchten.

3.  Klicken Sie auf **Mehr**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)"), und klicken Sie dann auf **Deaktivieren**.

4.  Es wird eine Warnung angezeigt, in der Sie gefragt werden, ob Sie den E-Mail-Benutzer wirklich deaktivieren möchten. Klicken Sie auf **Ja**, um ihn zu deaktivieren.

Der E-Mail-Benutzer wird aus der Kontaktliste entfernt.

## Deaktivieren von E-Mails für einen E-Mail-Benutzer mithilfe der Shell

In diesem Beispiel werden E-Mails für den E-Mail-Benutzer Yan Li deaktiviert.

    Disable-MailUser -Identity "Yan Li"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Disable-MailUser](https://technet.microsoft.com/de-de/library/aa998578\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche Deaktivierung von E-Mails für einen E-Mail-Benutzer zu überprüfen:

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger** \> **Kontakte**, und vergewissern Sie sich, dass der E-Mail-Benutzer nicht mehr aufgeführt wird.

2.  Klicken Sie in Active Directory-Benutzer und -Computer mit der rechten Maustaste auf den Benutzer und anschließend auf **Eigenschaften**. Auf der Registerkarte **Allgemein** ist das Feld **E-Mail** leer. Dadurch wird deutlich, dass der E-Mail-Benutzer nicht E-Mail-aktiviert ist.

3.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-MailUser
    
    Der E-Mail-Benutzer, für den Sie E-Mails deaktiviert haben, wird nicht in den Ergebnissen zurückgegeben, da mit diesem Cmdlet nur E-Mail-aktivierte Benutzer zurückgegeben werden.

4.  Führen Sie in der Shell den folgenden Befehl aus.
    
        Get-User
    
    Der E-Mail-Benutzer, für den Sie E-Mails deaktiviert haben, wird in den Ergebnissen zurückgegeben, da mit diesem Cmdlet alle Active Directory-Benutzerobjekte zurückgegeben werden.

## Aktivieren von Benutzern für E-Mails mithilfe der Shell

Sie können das Cmdlet **Enable-MailUser** verwenden, um einen vorhandenen Active Directory-Benutzer für E-Mails zu aktivieren. Sie können einen einzelnen Benutzer für E-Mails aktivieren, Sie können aber auch eine CSV-Datei verwenden, um mehrere Benutzer für E-Mails zu aktivieren.

## Aktivieren eines einzelnen Benutzers für E-Mails mithilfe der Shell

In diesem Beispiel wird der Benutzer Sanjay Shah für E-Mails aktiviert. Sie müssen eine externe E-Mail-Adresse angeben.

    Enable-MailUser -Identity "Sanjay Shah" -ExternalEmailAddress renev@tailspintoys.com

## Aktivieren mehrerer Benutzer für E-Mails mithilfe der Shell und einer CSV-Datei

Wenn Sie mehrere Benutzer gleichzeitig für E-Mails aktivieren, exportieren Sie zuerst die Liste der nicht E-Mail-aktivierten Benutzer in eine CSV-Datei (durch Trennzeichen getrennte Datei). Dann fügen Sie mit einem Text-Editor wie Editor oder einer Tabellenkalkulationsanwendung wie Microsoft Excel der CSV-Datei die externen E-Mail-Adressen hinzu. Anschließend verwenden Sie die aktualisierte CSV-Datei im Shell-Befehl, um die in der CSV-Datei aufgeführten Benutzer für E-Mails zu aktivieren.

1.  Führen Sie den folgenden Befehl aus, um eine Liste vorhandener Benutzer, die nicht E-Mail-aktiviert sind oder die nicht über ein Postfach in Ihrer Organisation verfügen, in eine Datei namens "UsersToMailEnable.csv" auf dem Desktop des Administrators zu exportieren.
    
        Get-User | Where { $_.RecipientType -eq "User" } | Out-File "C:\Users\Administrator\Desktop\UsersToMailEnable.csv"
    
    Die resultierende Datei gleicht der folgenden Datei.
    
        Name            RecipientType
        ----            -------------
        Guest           User
        krbtgt          User
        RMS_SERVICE     User
        David Pelton    User
        Kim Akers       User
        Janet Schorr    User
        Jeffrey Zang    User
        Spencer Low     User
        Toni Poe        User
        ...

2.  Nehmen Sie in der CSV-Datei die folgenden Änderungen vor:
    
      - Löschen Sie alle Benutzer, die Sie nicht für E-Mails aktivieren möchten, in der CSV-Datei. Sie würden beispielsweise die ersten drei Einträge im vorherigen Beispiel löschen, da es sich dabei im Standardsystemkonten handelt.
    
      - Löschen Sie die Spalte **RecipientType** und alle Instanzen von `User`.
    
      - Fügen Sie die Spaltenüberschrift **EmailAddress** hinzu, und ergänzen Sie dann die E-Mail-Adresse für jeden Benutzer in der Datei. Der Name und die externe E-Mail-Adresse der einzelnen Benutzer müssen durch ein Komma getrennt werden.
    
    Die aktualisierte CSV-Datei sollte nun wie die folgende Datei aussehen.
    
        Name,EmailAddress
        David Pelton,davidp@contoso.com
        Kim Akers,kakers@tailspintoys.com
        Janet Schorr,janet.schorr@adatum.com
        Jeffrey Zang,jzang@tailspintoys.com
        Spencer Low,spencerl@fouthcoffee.com
        Toni Poe,tonip@contoso.com
        ...

3.  Führen Sie den folgenden Befehl aus, um mit den Daten in der CSV-Datei die in der Datei aufgeführten Benutzer für E-Mails zu aktivieren.
    
        Import-CSV "C:\Users\Administrator\Desktop\UsersToMailEnable.csv" | ForEach-Object {Enable-MailUser -Identity $_.Name -ExternalEmailAddress $_.EmailAddress}
    
    In den Ergebnissen des Befehls werden Informationen über die neuen E-Mail-aktivierten Benutzer angezeigt.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um die erfolgreiche E-Mail-Aktivierung von Active Directory-Benutzern zu überprüfen:

  - Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Kontakte**. Neue E-Mail-Benutzer werden in der Kontaktliste angezeigt. Unter **Kontakttyp** lautet der Typ **E-Mail-Benutzer**.
    

    > [!NOTE]
    > Möglicherweise müssen Sie auf <STRONG>Aktualisieren</STRONG><IMG title="Aktualisieren (Symbol)" alt="Aktualisieren (Symbol)" src="images/Dn624163.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif"> klicken, um neue E-Mail-Benutzer anzuzeigen.



  - Führen Sie in der Shell den folgenden Befehl aus, um Informationen zu neuen E-Mail-Benutzern anzuzeigen.
    
        Get-MailUser | Format-Table Name,RecipientTypeDetails,ExternalEmailAddress

