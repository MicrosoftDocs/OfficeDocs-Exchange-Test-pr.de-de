---
title: 'Zuweisen einer Adressbuchrichtlinie zu E-Mail-Benutzern: Exchange 2013 Help'
TOCTitle: Zuweisen einer Adressbuchrichtlinie zu E-Mail-Benutzern
ms:assetid: bdfe6575-24c0-47d0-9cfb-ece910db248b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529942(v=EXCHG.150)
ms:contentKeyID: 50476594
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zuweisen einer Adressbuchrichtlinie zu E-Mail-Benutzern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-11_

Nach dem Erstellen einer Adressbuchrichtlinie (Address Book Policy, ABP) müssen Sie diese Postfachbenutzern zuweisen. Beim Erstellen von Benutzerkonten wird den Benutzern keine Standard-ABP zugewiesen. Wenn Sie einem Benutzer keine ABP zuweisen, kann der Benutzer über Outlook und Outlook Web App auf die globale Adressliste (Global Address List, GAL) für Ihre gesamte Organisation zugreifen. Weitere Informationen finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf Adressbuchrichtlinien finden Sie unter [Verfahren für Adressbuchrichtlinien](address-book-policy-procedures-exchange-2013-help.md).

Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet werden? Weitere Informationen finden Sie unter [Szenario: Bereitstellen von Adressbuchrichtlinien](scenario-deploying-address-book-policies-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Adressbuchrichtlinien" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Zuweisen einer ABP zu einem Postfachbenutzer mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Wählen Sie in der Listenansicht den Benutzer aus, dem Sie eine Richtlinie zuweisen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf **Postfachfunktionen**.

4.  Wählen Sie in der Liste **Adressbuchrichtlinie** eine ABP aus, die Sie auf diesen Benutzer anwenden möchten.

5.  Klicken Sie auf **Speichern**.

## Zuweisen einer ABP zu mehreren Postfachbenutzern mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Drücken Sie in der Listenansicht die STRG-Taste, um mehrere Benutzer auszuwählen.

3.  Klicken Sie im Detailbereich auf **Weitere Optionen**.

4.  Klicken Sie unter **Adressbuchrichtlinie** auf **Aktualisieren** .

5.  Wählen Sie in der Liste **Adressbuchrichtlinie auswählen** eine ABP aus, die Sie auf diese Benutzer anwenden möchten.

6.  Klicken Sie auf **Speichern**.

## Verwenden der Shell zum Zuweisen einer ABP zu Postfachbenutzern

In diesem Beispiel wird die Adressbuchrichtlinie namens "All Fabrikam" dem vorhandenen Postfachbenutzer "joe@fabrikam.com" zugewiesen.

    Set-Mailbox -Identity joe@fabrikam.com -AddressBookPolicy "All Fabrikam"

In diesem Beispiel wird die Adressbuchrichtlinie namens "ABP\_EngineeringDepartment" allen Postfachbenutzern zugewiesen, deren `CustomAttribute11`-Wert die Zeichenfolge "Engineering Department" enthält.

    Get-Mailbox -Filter {(CustomAttribute11 -like "Engineering Department")} | Set-Mailbox -AddressBookPolicy ABP_EngineeringDepartment

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)) und [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)).

