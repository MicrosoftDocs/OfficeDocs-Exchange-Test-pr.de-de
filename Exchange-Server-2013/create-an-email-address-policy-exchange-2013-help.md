---
title: 'Erstellen einer E-Mail-Adressrichtlinie: Exchange 2013 Help'
TOCTitle: Erstellen einer E-Mail-Adressrichtlinie
ms:assetid: eb2bf42e-2058-4e17-85d5-97546433b40a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125137(v=EXCHG.150)
ms:contentKeyID: 50476991
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.NewEmailAddressPolicyWizardForm.EmailAddressPolicyIntroductionPage
ms.translationtype: HT
---

# Erstellen einer E-Mail-Adressrichtlinie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-12-10_

Ein Empfänger muss über eine E-Mail-Adresse verfügen, um E-Mails empfangen oder senden zu können. E-Mail-Adressrichtlinien generieren die primären und sekundären E-Mail-Adressen für Ihre Empfänger (einschließlich Benutzern, Kontakten und Gruppen), damit diese E-Mails empfangen und senden können.

Wenn Sie eine neue E-Mail-Adressrichtlinie erstellen, können Sie die folgenden E-Mail-Adresstypen verwenden:

  - **SMTP-E-Mail-Musteradressen**. SMTP-E-Mail-*Muster*adressen sind häufig verwendete E-Mail-Adresstypen, die für Sie bereitgestellt werden.

  - **Benutzerdefinierte SMTP-E-Mail-Adressen**. Wenn Sie keine der SMTP-E-Mail-Musteradressen verwenden möchten, können Sie eine benutzerdefinierte SMTP-E-Mail-Adresse angeben.
    
    Wenn Sie eine benutzerdefinierte SMTP-E-Mail-Adresse erstellen, können Sie die Variablen in der folgenden Tabelle zum Angeben von Alternativwerten für den lokalen Teil der E-Mail-Adresse verwenden.
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Variable</th>
    <th>Wert</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>%g</p></td>
    <td><p>Vorname</p></td>
    </tr>
    <tr class="even">
    <td><p>%i</p></td>
    <td><p>Mittelinitial</p></td>
    </tr>
    <tr class="odd">
    <td><p>%s</p></td>
    <td><p>Nachname</p></td>
    </tr>
    <tr class="even">
    <td><p>%d</p></td>
    <td><p>Anzeigename</p></td>
    </tr>
    <tr class="odd">
    <td><p>%m</p></td>
    <td><p>Exchange-Alias</p></td>
    </tr>
    <tr class="even">
    <td><p>%<em>x</em>s</p></td>
    <td><p>Verwendet die ersten <em>x</em> Buchstaben des Nachnamens. Wenn z. B. <em>x</em> =2 ist, werden die ersten zwei Buchstaben des Nachnamens verwendet.</p></td>
    </tr>
    <tr class="odd">
    <td><p>%<em>x</em>g</p></td>
    <td><p>Verwendet die ersten <em>x</em> Buchstaben des Vornamens. Wenn z. B. <em>x</em> =2 ist, werden die ersten zwei Buchstaben des Vornamens verwendet.</p></td>
    </tr>
    </tbody>
    </table>


  - **Nicht-SMTP-E-Mail-Adressen**. Die folgenden Nicht-SMTP-E-Mail-Adresstypen werden unterstützt:
    
      - EX (Anzeigename des Präfixes der Legacy-DN-Proxyadresse)
    
      - X.500
    
      - X.400
    
      - MSMail
    
      - CcMail
    
      - Lotus Notes
    
      - Novell GroupWise
    
      - Exchange Unified Messaging-Proxyadresse (EUM-Proxyadresse)
    

    > [!IMPORTANT]
    > In Exchange werden alle Nicht-SMTP-E-Mail-Adressen als benutzerdefinierte Adressen angesehen. Exchange bietet für die E-Mail-Adresstypen X.400, GroupWise oder Lotus Notes keine eigenen Dialogfelder oder Eigenschaften an. Beim Hinzufügen einer benutzerdefinierten Nicht-SMTP-E-Mail-Adresse müssen Sie über die entsprechenden DLL-Dateien (Dynamic Link Library) verfügen. Wenn Sie die entsprechenden DLL-Dateien nicht bereitstellen, können Sie keine benutzerdefinierte E-Mail-Adressrichtlinie erstellen. Der folgende Fehler wird in der Ereignisanzeige protokolliert: "Das Beschreibungsobjekt für E-Mail-Adressen im Microsoft Exchange-Verzeichnis für den Adresstyp 'SADF' auf 'i386' Computern fehlt."



Ausführliche Anweisungen zum Erstellen einer E-Mail-Adressrichtlinie finden Sie in den folgenden Themen:

[Erstellen einer E-Mail-Adressrichtlinie](create-an-email-address-policy-exchange-2013-help.md)

[Erstellen einer E-Mail-Adressrichtlinie mithilfe der Empfängerfilterung](create-an-email-address-policy-by-using-recipient-filters-exchange-2013-help.md)

## Was müssen Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "E-Mail-Adressrichtlinien" im Thema [E-Mail-Adressen und Adressbücher](email-addresses-and-address-books-exchange-2013-help.md).

  - Bevor eine SMTP-Adressendomäne in einer E-Mail-Adressrichtlinie verwendet werden kann, müssen Sie eine akzeptierte Domäne konfigurieren. Weitere Informationen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!WARNING]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer E-Mail-Adressrichtlinie mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Nachrichtenfluss** \> **E-Mail-Adressrichtlinien**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Füllen Sie unter **E-Mail-Adressrichtlinie** die folgenden Felder aus:
    
      - **Name der Richtlinie**
    
      - **E-Mail-Adressformat**
    
      - **Empfängertypen angeben, auf die diese E-Mail-Adressrichtlinie angewendet wird**

3.  Klicken Sie auf **Regel hinzufügen**, um die Auswahl der Empfänger weiter einzuschränken, auf die diese Richtlinie angewendet wird. Dadurch wird eine boolesche **AND**-Anweisung erstellt.
    

    > [!WARNING]
    > Wenn Sie zu viele Regeln anwenden, kann es passieren, dass die E-Mail-Adressrichtlinie so weit eingeschränkt wird, dass keine Benutzer mehr enthalten sind.



4.  Klicken Sie auf **Vorschau auf Empfänger anzeigen, für die die Richtlinie gilt**, um die Empfänger anzuzeigen, auf die diese Richtlinie angewendet wird.

5.  Klicken Sie auf **OK**, um Ihre Änderungen zu speichern und die Richtlinie zu erstellen.

6.  Es wird eine Warnung angezeigt, dass die E-Mail-Adressrichtlinie nicht angewendet wird, bevor sie aktualisiert wurde. Nach der Erstellung wählen Sie sie aus und klicken anschließend im Detailbereich auf **Anwenden**.

## Erstellen einer E-Mail-Adressrichtlinie mithilfe der Shell

In diesem Beispiel wird eine E-Mail-Adressrichtlinie erstellt, die Postfachbenutzer in Niederlassungen im Südosten einschließt, die E-Mail-Adressen verwenden, die aus ihrem Nachnamen und den ersten beiden Buchstaben ihres Vornamens bestehen.

```powershell
    New-EmailAddressPolicy -Name "southeast offices" -IncludedRecipients MailboxUsers -ConditionalStateorProvince "Georgia","Alabama","Louisiana" -EnabledEmailAddressTemplates "SMTP:%s%2g@southeast.contoso.com"
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-EmailAddressPolicy](https://technet.microsoft.com/de-de/library/aa996800\(v=exchg.150\)).

