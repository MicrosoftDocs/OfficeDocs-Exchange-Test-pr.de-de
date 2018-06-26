---
title: 'Adressbuchrichtlinien: Exchange 2013 Help'
TOCTitle: Adressbuchrichtlinien
ms:assetid: d0a916a1-e3ed-49ae-b116-a559be0dcce6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh529948(v=EXCHG.150)
ms:contentKeyID: 50476760
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Adressbuchrichtlinien

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Erfahren Sie, wie Sie Ihre globale Adressliste in bestimmte Gruppen unterteilen können, um benutzerdefinierte globale Adresslisten in Outlook und Outlook Web App zu erstellen.

Die Segmentierung der globalen Adressliste (*GAL*) ist das Verfahren, mit dem Administratoren Benutzer in bestimmte Gruppen einteilen können, um benutzerdefinierte Ansichten der GAL der Organisation bereitzustellen. Adressbuchrichtlinien ermöglichen Ihnen die Einteilung von Benutzern in bestimmte Gruppen, um benutzerdefinierte Ansichten der globalen Adressliste Ihrer Organisation bereitzustellen. Bei der Erstellung einer Adressbuchrichtlinie weisen Sie der Richtlinie eine globale Adressliste (GAL), ein Offlineadressbuch (OAB), eine Raumliste und eine oder mehrere Adresslisten zu. Anschließend können Sie die Adressbuchrichtlinie Postfachbenutzern zuweisen und diesen den Zugriff auf eine benutzerdefinierte GAL in Outlook und Outlook Web App bereitstellen. Das Ziel besteht darin, einen einfacheren Mechanismus zum Durchführen der GAL-Segmentierung für lokale Organisationen bereitzustellen, die mehrere GALs benötigen.


> [!NOTE]
> Adressbuchrichtlinien dienen dazu, die GAL und Adresslisten für jede Benutzergruppe zu optimieren. Sie sollen es Benutzern nicht erschweren, andere Benutzer anzuzeigen oder mit anderen Benutzern in Ihrer Organisation zu kommunizieren. Adressbuchrichtlinien trennen Benutzer nur virtuell in der Form von Verzeichnissen, nicht in rechtlichem Sinn.



**Inhalt**

Funktionsweise von Adressbuchrichtlinien

Adressbuchrichtlinie - Beispiel

Entourage, Outlook für Mac und Adressbuchrichtlinien

## Funktionsweise von Adressbuchrichtlinien

Adressbuchrichtlinien enthalten die folgenden Listen:

  - Eine GAL

  - Ein OAB

  - Eine Raumliste (für Buchungszwecke)

  - Mindestens eine Adressliste

In der folgenden Abbildung besteht die Adressbuchrichtlinie A aus einer Teilmenge der verschiedenen Adressobjekte, die in der Organisation vorhanden sind (wie im unteren Teil der Abbildung dargestellt). Der daraus resultierende Bereich einer Adressbuchrichtlinie entspricht dem Bereich der in der Richtlinie enthaltenen GAL, in diesem Fall GAL1. Wenn die Adressbuchrichtlinie erstellt und einem Benutzer zugewiesen wird, werden die Adressobjekte in der Adressbuchrichtlinie als der Objektbereich definiert, den der Benutzer anzeigen kann.

![Übersicht über Adressbuchrichtlinien](images/Hh529948.68084064-7319-431b-be3b-0cce761258b1(EXCHG.150).gif "Übersicht über Adressbuchrichtlinien")

Sie können folgende Methoden verwenden, um einzelnen Postfachbenutzern Adressbuchrichtlinien zuzuweisen:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Neues oder vorhandenes Postfach?</th>
<th>Shell</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Neu</p></td>
<td><p><a href="https://technet.microsoft.com/de-de/library/aa997663(v=exchg.150)">New-Mailbox</a>-Cmdlet mit dem Parameter <em>AddressBookPolicy</em></p></td>
</tr>
<tr class="even">
<td><p>Vorhanden</p></td>
<td><p><a href="https://technet.microsoft.com/de-de/library/bb123981(v=exchg.150)">Set-Mailbox</a>-Cmdlet mit dem Parameter <em>AddressBookPolicy</em></p>
<p></p></td>
</tr>
</tbody>
</table>


Adressbuchrichtlinien treten in Kraft, wenn sich die Clientanwendung eines Benutzers in Exchange 2013 mit einem Clientzugriffsserver verbindet. Wenn Sie die Adressbuchrichtlinie ändern, wird die aktualisierte Adressbuchrichtlinie erst wirksam, nachdem der Benutzer seinen Client neu gestartet oder verbunden hat oder Sie die RPC-Clientzugriffsserver auf dem Exchange 2013-Postfachserver neu gestartet haben.

## Routing-Agent für Adressbuchrichtlinien

In einer Exchange-Organisation ohne Adressbuchrichtlinien passiert Folgendes, wenn eine E-Mail in Outlook oder Outlook Web App erstellt und an einen anderen Empfänger in Ihrer Exchange-Organisation gesendet wird:

1.  Die E-Mail-Adresse wird aufgelöst. Wenn Sie z. B. **kweku@contoso.com** in das Feld **An** eingeben, wird die SMTP-E-Mail-Adresse in den Anzeigenamen des Benutzers **Kweku Ako-Adjei** aufgelöst.

2.  Sie können die Kontaktkarte der anderen Person anzeigen. Nach der Auflösung des Namens können Sie auf den Namen des Benutzers doppelklicken und Kontaktinformationen wie Büro und Telefonnummer anzeigen.

Wenn Sie Adressbuchrichtlinien verwenden und nicht möchten, dass Benutzer in getrennten virtuellen Organisationen sich gegenseitig ihre möglicherweise vertraulichen Informationen anzeigen, können Sie den Agent für das Routing von Adressbuchrichtlinien aktivieren. Der Agent für das Routing von Adressbuchrichtlinien ist ein Transport-Agent, der steuert, wie Empfänger in Ihrer Organisation aufgelöst werden. Nachdem der Agent für das Routing von Adressbuchrichtlinien installiert und konfiguriert wurde, werden Benutzer, die verschiedenen globalen Adresslisten zugewiesen sind, insofern als externe Empfänger angezeigt, da sie die Kontaktkarten externer Empfänger nicht anzeigen können.

Informationen zum Aktivieren des Agents für das Routing von Adressbuchrichtlinien in Exchange Online finden Sie unter [Aktivieren des Adressbuchrichtlinien-Routings](https://technet.microsoft.com/de-de/library/jj891095\(v=exchg.150\)).

Informationen zum Aktivieren des Agents für das Routing von Adressbuchrichtlinien in Exchange Server finden Sie unter [Installieren und Konfigurieren des Agents für das Routing von Adressbuchrichtlinien](install-and-configure-the-address-book-policy-routing-agent-exchange-2013-help.md).

## Adressbuchrichtlinie - Beispiel

In der folgenden Abbildung haben Fabrikam und Tailspin Toys eine gemeinsame Exchange-Organisation und denselben CEO. Der CEO ist der einzige Mitarbeiter, der zu beiden Unternehmen gehört.

![Zwei Unternehmen, ein CEO](images/JJ657455.c87a5654-d456-4688-acb2-0be15ba1cda6(EXCHG.150).gif "Zwei Unternehmen, ein CEO")

Diese Konfiguration enthält drei Adressbuchrichtlinien:

  - Eine enthält die Fabrikam-Mitarbeiter und den CEO

  - Eine enthält die Tailspin Toys-Mitarbeiter und den CEO

  - Eine enthält nur den CEO

Für die Adressbuchrichtlinien gelten folgende Regeln:

  - Die Benutzer bei Tailspin Toys können nur die Tailspin Toys-Mitarbeiter und den CEO anzeigen, wenn sie die GAL durchsuchen.

  - Die Benutzer bei Fabrikam können nur die Fabrikam-Mitarbeiter und den CEO anzeigen, wenn sie die GAL durchsuchen.

  - Der CEO kann alle Fabrikam- und Tailspin Toys-Mitarbeiter anzeigen, wenn er die GAL durchsucht.

  - Benutzer, die die Mitgliedschaft des CEO in Gruppen anzeigen, sehen nur Gruppen, die zum Unternehmen der Benutzer gehören. Sie sehen nicht die Gruppen, die im anderen Unternehmen vorhanden sind.

## Entourage, Outlook für Mac und Adressbuchrichtlinien

Adressbuchrichtlinien funktionieren nicht für Entourage-Benutzer oder Outlook für Mac-Benutzer, die mit ihrem Unternehmensnetzwerk verbunden sind. Entourage- und Outlook für Mac-Clients innerhalb eines Unternehmensnetzwerks verwenden nicht den Clientzugriffsserver, sondern verbinden sich direkt mit dem globalen Katalogserver und fragen Active Directory direkt ab. Outlook für Mac 2011-Clients jedoch, die eine Verbindung über das Internet herstellen, können ein OAB oder die Exchange-Webdienste verwenden. Aus diesem Grund können diese Clients die GAL basierend auf der ihnen zugewiesenen Adressbuchrichtlinie durchsuchen. Weitere Informationen zur Verwaltung von Outlook für Mac 2011 finden Sie unter [Planen von Outlook für Mac 2011](https://go.microsoft.com/fwlink/p/?linkid=231878)

## Weitere Informationen

[Szenario: Bereitstellen von Adressbuchrichtlinien](scenario-deploying-address-book-policies-exchange-2013-help.md)

[Verfahren für Adressbuchrichtlinien](https://technet.microsoft.com/de-de/library/jj891096\(v=exchg.150\)) in Exchange Online

