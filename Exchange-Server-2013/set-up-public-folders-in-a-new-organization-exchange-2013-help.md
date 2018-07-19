---
title: 'Einrichten öffentlicher Ordner in einer neuen Organisation: Exchange 2013 Help'
TOCTitle: Einrichten öffentlicher Ordner in einer neuen Organisation
ms:assetid: 7b419906-8977-47f0-8687-a87911b5ebec
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ651147(v=EXCHG.150)
ms:contentKeyID: 50476003
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einrichten öffentlicher Ordner in einer neuen Organisation

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-11-09_

**Zusammenfassung:**  Informationen zum Einrichten öffentlicher Ordner, einschließlich Zuweisen von Berechtigungen für diese im Exchange Admin Center.

In diesem Thema wird erklärt, wie öffentliche Ordner in einer neuen Organisation oder einer Organisation ohne vorherige öffentliche Ordner konfiguriert und in Betrieb genommen werden.


> [!NOTE]
> Weitere Informationen zu den Speicherkontingenten und -grenzwerten bei öffentlichen Ordnern finden Sie unter den folgenden Themen: 
> <UL>
> <LI>
> <P>Informationen zu öffentlichen Ordnern bei Office 365 finden Sie unter <A href="https://go.microsoft.com/fwlink/?linkid=391188">Exchange Online-Begrenzungen</A>.</P>
> <LI>
> <P>Informationen zu öffentlichen Ordnern beim intern verwalteten Exchange Server 2013 finden Sie unter <A href="limits-for-public-folders-exchange-2013-help.md">Grenzwerte für öffentliche Ordner</A>.</P></LI></UL>



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner in Exchange Server 2013 finden Sie unter [Verfahren für öffentliche Ordner](public-folder-procedures-exchange-2013-help.md).

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf öffentliche Ordner in Exchange Online finden Sie unter [Öffentliche Ordnerprozeduren in Office 365 und Exchange Online](https://technet.microsoft.com/de-de/library/jj966272\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Öffentliche Ordner" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Erstellen des primären Postfachs für öffentliche Ordner

Das primäre Postfach für öffentliche Ordner enthält eine beschreibbare Kopie der Hierarchie öffentlicher Ordner samt Inhalt und ist das erste Postfach für öffentliche Ordner, das Sie für Ihre Organisation anlegen. Alle weiteren Postfächer für öffentliche Ordner werden sekundäre Postfächer für öffentliche Ordner, die eine schreibgeschützte Kopie der Hierarchie samt Inhalt enthalten.

Ausführliche Anleitungen finden Sie unter [Erstellen eines Postfachs für öffentliche Ordner](create-a-public-folder-mailbox-exchange-2013-help.md).

## Schritt 2: Erstellen des ersten öffentlichen Ordners

Ausführliche Anleitungen finden Sie unter [Erstellen eines öffentlichen Ordners](create-a-public-folder-exchange-2013-help.md).

## Schritt 3: Zuweisen von Berechtigungen zum öffentlichen Ordner

Nach dem Erstellen des öffentlichen Ordners müssen Sie die Berechtigungsstufe **Besitzer** festlegen, sodass mindestens ein Benutzer auf dem Client auf den öffentlichen Ordner zugreifen und Unterordner erstellen kann. Alle nachfolgend erstellten öffentlichen Ordner erben die Berechtigungen des übergeordneten öffentlichen Ordners.

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Öffentliche Ordner** \> **Öffentliche Ordner**.

2.  Wählen Sie in der Listenansicht den öffentlichen Ordner aus.

3.  Klicken Sie im Detailbereich unter **Ordnerberechtigungen** auf **Verwalten**.

4.  Klicken Sie in **Berechtigungen für öffentliche Ordner** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

5.  Klicken Sie auf **Durchsuchen**, um einen Benutzer auszuwählen.

6.  Wählen Sie in der Liste **Berechtigungsstufe** eine Stufe aus. Mindestens ein Benutzer sollte die Stufe **Besitzer** innehaben.

7.  Klicken Sie auf **Speichern**.

8.  Sie können mehrere Benutzer hinzufügen, indem Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") klicken und die oben genannten Schritte ausführen, um die geeigneten Berechtigungen zuzuweisen. Sie können die Berechtigungsstufe auch anpassen, indem Sie die entsprechenden Kontrollkästchen aktivieren oder deaktivieren. Wenn Sie eine vordefinierte Berechtigungsstufe wie z. B. **Besitzer** bearbeiten, ändert sich die Berechtigungsstufe zu **Benutzerdefiniert**.

Weitere Informationen zum Verwenden der Shell für das Zuweisen von Berechtigungen zu einem öffentlichen Ordner finden Sie unter [Add-PublicFolderClientPermission](https://technet.microsoft.com/de-de/library/bb124743\(v=exchg.150\)).

## Schritt 4 (optional): Aktivieren des öffentlichen Ordners für E-Mail

Wenn Sie möchten, dass Benutzer E-Mails an den öffentlichen Ordner senden können, müssen Sie den Ordner für E-Mail aktivieren. Dieser Schritt ist optional. Wenn Sie den öffentlichen Ordner nicht für E-Mail aktivieren, können Benutzer Nachrichten in diesem Ordner bereitstellen, indem sie Elemente aus Outlook in den Ordner ziehen.

1.  Wechseln Sie in der Exchange-Verwaltungskonsole zu **Öffentliche Ordner** \> **Öffentliche Ordner**.

2.  Wählen Sie in der Listenansicht den öffentlichen Ordner aus, den Sie für E-Mail aktivieren möchten.

3.  Klicken Sie im Detailbereich unter **E-Mail-Einstellungen – Deaktiviert** auf **Aktivieren**.
    
    Sie werden in einer Warnmeldung gefragt, ob Sie den öffentlichen Ordner tatsächlich für E-Mail aktivieren möchten. Klicken Sie auf **Ja**.

Der öffentliche Ordner ist nun für E-Mail aktiviert, und der Name des öffentlichen Ordners ist der Alias des öffentlichen Ordners. Wenn mehrere Empfänger den gleichen Namen aufweisen, wird eine Zahl an den Alias des öffentlichen Ordners angehängt. Wenn Sie beispielsweise über eine Verteilergruppe "Vertriebsteam" verfügen, einen öffentlichen Ordner namens "Vertriebsteam" erstellen und diesen für E-Mail aktivieren, erhält der öffentliche Ordner den Alias "Vertriebsteam1".

Weitere Informationen zum Verwenden der Shell für das Aktivieren eines öffentlichen Ordners für E-Mail finden Sie unter [Enable-MailPublicFolder](https://technet.microsoft.com/de-de/library/aa998824\(v=exchg.150\)).

