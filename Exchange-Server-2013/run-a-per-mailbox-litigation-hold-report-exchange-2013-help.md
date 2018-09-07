---
title: 'Ausf. e. Berichts zu Beweissicherungsverf. pro Postfach: Exchange 2013-Hilfe'
TOCTitle: Ausführen eines Berichts zu Beweissicherungsverfahren pro Postfach
ms:assetid: 98c46226-2f48-42c6-a741-34bb5944f519
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150542(v=EXCHG.150)
ms:contentKeyID: 50474878
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ausführen eines Berichts zu Beweissicherungsverfahren pro Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-13_

Wenn Ihre Organisation in ein Rechtsverfahren involviert ist, müssen Sie möglicherweise Schritte unternehmen, um relevante Daten zu sichern – beispielsweise E-Mails, die als Beweis dienen können. In einer solchen Situation können Sie alle von bestimmten Personen gesendeten und empfangenen E-Mails bzw. alle in Ihrer Organisation gesendeten und empfangenen E-Mails mithilfe der Beweissicherung für einen bestimmten Zeitraum aufbewahren. Weitere Informationen dazu, was passiert, wenn ein Postfach einem Beweissicherungsverfahren unterliegt, sowie zur Aktivierung und Deaktivierung der Beweissicherung für ein Postfach finden Sie im Abschnitt "Postfachfunktionen "unter [Verwalten von Benutzerpostfächern](https://review.docs.microsoft.com/de-de/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes).

Verwenden Sie den Bericht für die Beweissicherung, um die folgenden Typen von Änderungen nachzuverfolgen, die innerhalb eines bestimmten Zeitraums an einem Postfach vorgenommen wurden:

  - Das Beweissicherungsverfahren wurde aktiviert.

  - Das Beweissicherungsverfahren wurde deaktiviert.

Der Bericht enthält für jede dieser Änderungen den Benutzer, der die Änderung vorgenommen hat, und die Zeit (Uhrzeit und Datum), zu der die Änderung vorgenommen wurde.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Überwachungsprotokollierung durch Administratoren mit Leserechten" im Thema [Exchange- und Shellinfrastrukturberechtigungen](exchange-and-shell-infrastructure-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Erstellen eines Berichts für die Beweissicherung über die Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Überwachung**.

2.  Klicken Sie auf **Bericht zu Beweissicherungsverfahren pro Postfach ausführen**.
    
    Microsoft Exchange führt den Bericht für alle für die Beweissicherung relevanten Änderungen aus, die in den vergangenen zwei Wochen an allen Postfächern vorgenommen wurden.

3.  Um die Änderungen für ein bestimmtes Postfach anzuzeigen, wählen Sie im Suchergebnisbereich das Postfach aus. Sehen Sie sich die Suchergebnisse im Detailbereich an.


> [!TIP]
> Eingrenzen der Suchergebnisse? Wählen Sie das Startdatum und/oder das Enddatum sowie bestimmte Postfächer aus, die durchsucht werden sollen. Klicken Sie auf <STRONG>Suchen</STRONG>, um den Bericht erneut auszuführen.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen Bericht zur Beweissicherung erfolgreich erstellt haben, werden Postfächer, bei denen im Datumsbereich für die Beweissicherung relevante Änderungen erfolgt sind, im Suchergebnisbereich angezeigt. Wenn es keine Ergebnisse gibt, sind im Datumsbereich keine für die Beweissicherung relevante Änderungen erfolgt oder neueste Änderungen noch nicht wirksam.


> [!NOTE]
> Wenn ein Postfach der Beweissicherung unterliegt, kann es bis zu 60&nbsp;Minuten dauern, bis diese wirksam wird.


