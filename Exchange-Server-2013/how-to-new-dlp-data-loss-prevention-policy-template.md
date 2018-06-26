---
title: "So wird's gemacht: Neue DLP-Richtlinienvorlage (Data Loss Prevention, Verhinderung von Datenverlust)"
TOCTitle: Erstellen einer DLP-Richtlinie aus einer Vorlage
ms:assetid: 4432ef8b-6108-48d3-b2af-43ef5b40d2bc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150515(v=EXCHG.150)
ms:contentKeyID: 50474769
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer DLP-Richtlinie aus einer Vorlage

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-01-14_

In Microsoft Exchange Server 2013 können Sie Richtlinienvorlagen zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) verwenden, um den Anforderungen in Bezug auf Messagingrichtlinien und deren Einhaltung gerecht zu werden, die in Ihrer Organisation gelten. Diese Vorlagen enthalten vordefinierte Sätze an Regeln, mit denen Sie Nachrichtendaten verwalten können, für die verschiedene rechtliche und regulatorische Auflagen gelten. Eine Liste aller von Microsoft bereitgestellten Vorlagen finden Sie unter [In Exchange bereitgestellte DLP-Richtlinienvorlagen](dlp-policy-templates-supplied-in-exchange-exchange-2013-help.md). Die bereitgestellten DLP-Beispielvorlagen unterstützen Sie bei der Datenverwaltung in Bezug auf folgende Vorgaben und Standards:

  - Gramm-Leach-Bliley Act (GLBA)

  - Payment Card Industry Data Security Standard (PCI-DSS)

  - United States Personally Identifiable Information (U.S. PII)

Sie können jede dieser DLP-Vorlagen anpassen oder unverändert einsetzen. DLP-Richtlinienvorlagen setzen auf Transportregeln auf, die neue Bedingungen oder Prädikate und Aktionen enthalten. DLP-Richtlinien unterstützen sämtliche der traditionellen Transportregeln, und Sie können zusätzliche Regeln hinzufügen, nachdem eine DLP-Richtlinie eingerichtet wurde. Weitere Informationen zu Richtlinienvorlagen finden Sie unter [DLP-Richtlinienvorlagen](dlp-policy-templates-exchange-2013-help.md). Weitere Informationen zu Transportregelfunktionen finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange Server 2013) oder [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online). Wenn Sie mit dem Erzwingen einer Richtlinie begonnen haben, erfahren Sie in den folgenden Themen, wie Sie die Ergebnisse überwachen können:

Exchange 2013: [Anzeigen von DLP-Richtlinienerkennungsberichten](view-dlp-policy-detection-reports-exchange-2013-help.md)

Exchange Online: [Anzeigen von DLP-Richtlinienerkennungsberichten](https://technet.microsoft.com/de-de/library/dn904484\(v=exchg.150\))


> [!WARNING]
> Sie sollten Ihre DLP-Richtlinien im Testmodus aktivieren, bevor Sie sie in der Produktionsumgebung ausführen. Während dieser Tests wird empfohlen, dass Sie Beispielbenutzerpostfächer konfigurieren und Testnachrichten senden, die Ihre Testrichtlinien aufrufen, um die Ergebnisse zu bestätigen.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf die Erstellung einer DLP-Richtlinie aus einer Vorlage finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md)Exchange Server 2013 oder [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\))Exchange Online.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 30 Minuten

  - Stellen Sie sicher, dass Exchange 2013 wie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md) beschrieben eingerichtet wurde.

  - Konfigurieren Sie sowohl Administrator- als auch Benutzerkonten innerhalb Ihrer Organisation, und überprüfen Sie den grundlegenden E-Mail-Fluss.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verhinderung von Datenverlust (Data Loss Prevention, DLP)" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md)

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren einer DLP-Richtlinie aus einer Vorlage mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").
    

    > [!NOTE]
    > Sie können diese Aktion auch auswählen, wenn Sie auf den Pfeil neben dem Symbol <STRONG>Hinzufügen</STRONG><IMG title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif"> klicken und aus dem Dropdownmenü die Option <STRONG>Neue DLP-Richtlinie aus Vorlage</STRONG> auswählen.



2.  Füllen Sie auf der Seite **Erstellen einer neuen DLP-Richtlinie aus einer Vorlage** die folgenden Felder aus:
    
    1.  **Name**   Fügen Sie einen Namen ein, der diese Richtlinie von anderen unterscheidet.
    
    2.  **Beschreibung**   Fügen Sie eine optionale Beschreibung mit einer Zusammenfassung dieser Richtlinie ein.
    
    3.  **Vorlage auswählen**   Wählen Sie die geeignete Vorlage, um mit der Erstellung einer neuen Richtlinie zu beginnen.
    
    4.  **Weitere Optionen**   Wählen Sie den Modus oder Status. Die neue Richtlinie wird erst vollständig aktiviert, wenn Sie dies angeben. Der Standardmodus für eine Richtlinie sieht einen Test ohne Benachrichtigungen vor.
    
    5.  Klicken Sie auf **Speichern**, um die Richtlinie zu erstellen.


> [!NOTE]
> Zusätzlich zu den Regeln innerhalb einer spezifischen Vorlage hat Ihre Organisation möglicherweise weitere Erwartungen oder Unternehmensrichtlinien, die auf regulierte Daten innerhalb der Messagingumgebung angewendet werden müssen. In Exchange 2013 können Sie ganz einfach Aktionen zur Basisvorlage hinzufügen, um Ihre Exchange-Messagingumgebung an Ihre eigenen Anforderungen anzupassen.



Sie können Richtlinien ändern, indem Sie die Regeln in der Richtlinie bearbeiten, nachdem die Richtlinie in Ihrer Exchange 2013-Umgebung gespeichert wurde. Eine Regeländerung kann beispielsweise die Definition einer Ausnahme für bestimmte Personen oder das Senden eines Hinweises und die Blockierung der Nachrichtenzustellung sein, wenn in einer Nachricht vertrauliche Inhalte gefunden werden. Weitere Informationen zum Bearbeiten von Richtlinien und Regeln finden Sie unter [Verwalten von DLP-Richtlinien](manage-dlp-policies-exchange-2013-help.md).

Sie müssen auf der Seite **DLP-Richtlinie bearbeiten** zum Regelsatz der jeweiligen Richtlinie navigieren und die auf dieser Seite verfügbaren Tools verwenden, um eine DLP-Richtlinie zu ändern, die Sie bereits in Exchange 2013 erstellt haben.

Einige Richtlinien ermöglichen das Hinzufügen von Regeln, die RMS für Nachrichten aktivieren. Sie müssen RMS auf dem Exchange-Server konfigurieren, bevor Sie die Aktionen hinzufügen, um diese Art von Regeln zu verwenden.

Sie können für alle DLP-Richtlinien die Regeln, Aktionen, Ausnahmen und den Erzwingungszeitraum ändern und angeben, ob weitere Regeln innerhalb der Richtlinie aktiviert werden sollen. Ferner können Sie benutzerdefinierte Bedingungen erstellen.

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[DLP-Richtlinienvorlagen](dlp-policy-templates-exchange-2013-help.md)

