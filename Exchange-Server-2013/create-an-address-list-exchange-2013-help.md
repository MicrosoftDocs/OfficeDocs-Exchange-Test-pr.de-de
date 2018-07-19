---
title: 'Erstellen einer Adressliste: Exchange 2013 Help'
TOCTitle: Erstellen einer Adressliste
ms:assetid: e86ba1b7-c41c-4050-bc29-13996cf53c59
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125036(v=EXCHG.150)
ms:contentKeyID: 50477007
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.OrganizationConfiguration.Mailbox.NewAddressListWizardForm.AddressListIntroductionPage
ms.translationtype: MT
---

# Erstellen einer Adressliste

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-12_

Adresslisten sind eine Sammlung von Empfänger- und anderen Active Directory-Objekten. Jede Adressliste kann einen oder mehrere Objekttypen beinhalten (z. B. Benutzer, Kontakte, Gruppen, Öffentliche Ordner, Konferenz- und andere Ressourcen). Adresslisten bieten außerdem einen Mechanismus, mit dem E-Mail-aktivierte Objekte in Active Directory für bestimmte Gruppen von Benutzern aufgeteilt werden können.

Informationen zu anderen Verwaltungsaufgaben, die sich auf Adresslisten beziehen, finden Sie unter [Verfahren für die Adressliste](address-list-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adresslisten" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Adressliste mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Organisation** \> **Adresslisten**, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie in **Adressliste** einen Namen ein, und geben Sie dann die Empfängertypen an, die in die Liste einbezogen werden sollen.

3.  Exchange erstellt standardmäßig Adresslisten, die alle Mitglieder Ihrer Organisation enthalten. Klicken Sie auf **Regel hinzufügen**, um eine eindeutige benutzerdefinierte Adressliste zu erstellen.
    

    > [!IMPORTANT]
    > Wenn Sie keine Regel hinzufügen, erstellen Sie eine Adressliste, die zu einer der Standardadresslisten redundant ist.



4.  Wählen Sie in der Liste eine Filteroption aus (z. B. **Benutzerdefiniertes Attribut 1**).

5.  Geben Sie in **Wörter oder Ausdrücke angeben** Wörter oder Ausdrücke ein, nach denen gefiltert wird. Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und anschließend auf **OK**.
    
    Sie können weiterhin verschiedene Ausdrücke oder Wörter hinzufügen, indem Sie Schritt 4 wiederholen. Der Filter ist eine boolesche **OR**-Anweisung. Sie können z. B. einen Filter erstellen, der die Adressliste auf Benutzer anwendet, deren "Benutzerdefiniertes Attribut 1" **Oregon**, **Idaho** oder **Washington** entspricht.

6.  (Optional) Klicken Sie erneut auf **Regel hinzufügen**, um weitere Filter hinzuzufügen. Zusätzliche Filter erstellen eine boolesche **AND**-Anweisung. Je mehr Filter Sie hinzufügen, desto geringer die Anzahl der Benutzer, auf die die Adressliste angewendet wird.

7.  Klicken Sie auf **Vorschau der in der Adressliste enthaltenen Empfänger anzeigen**, um die Empfänger anzuzeigen, auf die diese Adressliste angewendet wird.

8.  Klicken Sie auf **Speichern**.

9.  Es wird eine Warnung angezeigt, dass die Adressliste nicht angewendet wird, bevor sie aktualisiert wurde. In Abhängigkeit von der Größe Ihrer Organisation und der zur Adressliste hinzugefügten Filter können einige Adresslisten Tausende oder Zehntausende Empfänger enthalten. Das Aktualisieren von Adresslisten kann sich auf Ihre Ressourcen auswirken, daher sollten Sie die Adressen außerhalb der Hauptnutzungszeiten aktualisieren.
    
    Weitere Informationen zum Aktualisieren einer Adressliste finden Sie unter [Aktualisieren einer Adressliste](update-an-address-list-exchange-2013-help.md).

## Erstellen einer Adressliste mithilfe der Shell

In diesem Beispiel wird die Adressliste "MyAddressList" erstellt. Hierzu wird der Parameter *RecipientFilter* verwendet und es werden Empfänger eingeschlossen, bei denen es sich um Postfachbenutzer handelt, für die `StateOrProvince` auf `Washington` oder `Oregon` festgelegt wurde.

    New-AddressList -Name MyAddressList -RecipientFilter {((RecipientType -eq 'UserMailbox') -and ((StateOrProvince -eq 'Washington') -or (StateOrProvince -eq 'Oregon')))}

In diesem Beispiel wird durch die Verwendung vordefinierter Bedingungen eine untergeordnete Adressliste mit dem Namen "Building 34 Meeting Rooms" im übergeordneten Container "All Rooms" erstellt.

    New-AddressList -Name "Building 34 Meeting Rooms" -Container "\All Rooms" -IncludedRecipients Resources -ConditionalCustomAttribute1 "Building 34"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-AddressList](https://technet.microsoft.com/de-de/library/aa996912\(v=exchg.150\)).

