---
title: 'Zuordnen von Empf. für Downloads v. Offlineadressbüchern: Exchange 2013-Hilfe'
TOCTitle: Zuordnen von Empfängern für Downloads von Offlineadressbüchern
ms:assetid: 141751ac-16d3-4e3c-b70c-004aeedcb5a0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996345(v=EXCHG.150)
ms:contentKeyID: 50475145
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zuordnen von Empfängern für Downloads von Offlineadressbüchern

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-15_

Wenn Sie in Ihrer Organisation mehrere Offlineadressbücher (OABs) verwenden, haben Sie mehrere Möglichkeiten anzugeben, welche Empfänger welche OABs herunterladen:

  - **Pro Postfachdatenbank**   Sie können bestimmte OAB-Downloads für Ihre Empfänger über die Exchange-Verwaltungskonsole oder die Shell festlegen, indem Sie eine Postfachdatenbank mit einem Standard-OAB für Office Outlook 2007-, Outlook 2010- und Outlook 2013-Clients verknüpfen.

  - **Pro Empfänger**   Sie können das Cmdlet **Set-Mailbox** in der Shell verwenden, um anzugeben, welches OAB heruntergeladen wird, indem Sie das OAB direkt mit dem Postfach eines Empfängers verknüpfen.

  - **Pro mehrere Empfänger**   Mit einem Pipelinebefehl in der Shell können Sie das OAB angeben, das mehrere Empfänger basierend auf gemeinsamen Attributen herunterladen.

  - **Pro Adressbuchrichtlinie**   Sie können dem Konto eines Postfachbenutzers eine Adressbuchrichtlinie zuweisen, um anzugeben, welches OAB in das Empfängerpostfach heruntergeladen wird. Wenn Sie einem Benutzerkonto eine Adressbuchrichtlinie zuweisen, dem bereits ein OAB zugewiesen ist, hat das dem Postfach explizit zugewiesene OAB Vorrang. Weitere Informationen finden Sie unter [Zuweisen einer Adressbuchrichtlinie zu E-Mail-Benutzern](https://review.docs.microsoft.com/de-de/exchange/address-books/address-book-policies/assign-an-address-book-policy-to-mail-users).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf OABs finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Diese Verfahren können nicht mit der Exchange-Verwaltungskonsole durchgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Festlegen von Empfängern für OAB-Downloads durch Verknüpfen der Postfachdatenbank mit einer Öffentliche Ordner-Datenbank oder einem Standard-OAB mithilfe der Shell

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Postfachdatenbanken" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

In diesem Beispiel wird die webbasierte Verteilung von "My OAB" für die standardmäßige Postfachdatenbank eingerichtet.

    Set-MailboxDatabase -Identity "Mailbox Database" -OfflineAddressBook "My OAB"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-MailboxDatabase](https://technet.microsoft.com/de-de/library/bb123971\(v=exchg.150\)).

## Verwenden der Shell zum Angeben des OAB, das heruntergeladen wird, durch Verknüpfen des OAB direkt mit dem Postfach eines Empfängers

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

Um anzugeben, welches OAB heruntergeladen wird, indem das OAB direkt mit dem Postfach eines Empfängers verknüpft wird, verwenden Sie die folgende Syntax.

    Set-Mailbox -Identity <MailboxIDParameter> -OfflineAddressBook <OfflineAddressBookIdParameter>


> [!NOTE]
> Der Parameter <EM>Identity</EM> gibt das Postfach an und kann die folgenden Werte annehmen: GUID, ADObjectID, DN (Distinguished Name), <EM>domain\account</EM>, Benutzerprinzipalname (User Principal Name, UPN), LegacyExchangeDN, SmtpAddress und Alias.



In diesem Beispiel wird angegeben, dass der Benutzer Kim das OAB "My OAB" herunterlädt.

    Set-Mailbox -Identity Kim -OfflineAddressBook "My OAB"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

## Verwenden der Shell zum Angeben des OAB, das mehrere Empfänger herunterladen

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Berechtigungen für die Empfängerbereitstellung" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

In diesem Beispiel wird angegeben, dass alle Benutzerpostfächer in den USA im Unternehmen Contoso das OAB "Contoso United States" herunterladen.

    Get-User -ResultSize Unlimited -Filter { Company -eq "Contoso" -and RecipientType -eq "UserMailbox" } | Where { $_.CountryOrRegion -eq "United States"} | Set-Mailbox -OfflineAddressBook "Contoso United States"

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-User](https://technet.microsoft.com/de-de/library/aa996896\(v=exchg.150\)) und [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\)).

