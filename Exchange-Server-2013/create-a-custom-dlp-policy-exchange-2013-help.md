---
title: 'Erstellen einer benutzerdefinierten DLP-Richtlinie: Exchange 2013 Help'
TOCTitle: Erstellen einer benutzerdefinierten DLP-Richtlinie
ms:assetid: b3299a39-9663-41e4-b76e-9d2f7879d486
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150550(v=EXCHG.150)
ms:contentKeyID: 50474896
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen einer benutzerdefinierten DLP-Richtlinie

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-03-18_

Mit einer benutzerdefinierten Richtlinie zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) können Sie Bedingungen, Regeln und Aktionen einrichten, mit denen Sie bestimmte Anforderungen Ihrer Organisation erfüllen können, die von keiner der vorhandenen DLP-Vorlagen abgedeckt werden.

Die für Sie in einer einzelnen Richtlinie verfügbaren Regelbedingungen enthalten zusätzlich zu allen herkömmlichen Transportregeln die neuen Typen vertraulicher Informationen, die unter [Wonach die Typen von vertraulichen Informationen in Exchange suchen](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md) vorgestellt werden. Weitere Informationen zu Transportregeln finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange 2013) oder [Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online).


> [!WARNING]
> Sie sollten Ihre DLP-Richtlinien im Testmodus aktivieren, bevor Sie sie in der Produktionsumgebung ausführen. Während dieser Tests wird empfohlen, dass Sie Beispielbenutzerpostfächer konfigurieren und Testnachrichten senden, die Ihre Testrichtlinien aufrufen, um die Ergebnisse zu bestätigen. Weitere Informationen zu Tests finden Sie unter <A href="test-a-mail-flow-rule-exchange-2013-help.md">Testen einer Nachrichtenflussregel</A>.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit der Erstellung einer benutzerdefinierten DLP-Richtlinie finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md)(Exchange 2013) oder [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\)) (Exchange Online).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 60 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verhinderung von Datenverlust (Data Loss Prevention, DLP)" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Damit Sie neue benutzerdefinierte DLP-Richtlinien erstellen können, müssen Sie die Installationsanweisungen für Exchange 2013 beachten. Weitere Informationen zur Bereitstellung finden Sie unter [Planung und Bereitstellung](planning-and-deployment-for-exchange-2013-installation-instructions.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!NOTE]
> Aufgrund der unterschiedlichen Kundenumgebungen kann Microsoft Customer Support Services (CSS) nicht an der Entwicklung oder an Tests benutzerdefinierter Regular Expression-Skripts (RegEx-Skripts) teilnehmen. Die Entwicklung, Tests und das Debuggen benutzerdefinierter RegEx-Skripts muss für Office&nbsp;365-Kunden von der internen IT-Abteilung übernommen werden. Alternativ können Office&nbsp;365-Kunden einen externen Beratungsservice wie z.&nbsp;B. Microsoft Consulting Services (MCS) nutzen. Unabhängig davon, wo das Skript entwickelt wurde, können CSS EXO- und EOP-Supporttechniker nicht für Anfragen bezüglich benutzerdefinierter RegEx-Skripts zur Verfügung stehen.




> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Erstellen einer benutzerdefinierten DLP-Richtlinie ohne vorhandene Regeln mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**. Alle vorhandenen Richtlinien, die Sie konfiguriert haben, werden in einer Liste angezeigt.

2.  Klicken Sie auf den Pfeil neben dem Symbol **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie **Neue benutzerdefinierte Richtlinie** aus.
    

    > [!IMPORTANT]
    > Wenn Sie nicht auf den Pfeil, sondern auf <STRONG>Hinzufügen</STRONG><IMG title="Hinzufügen (Symbol)" alt="Hinzufügen (Symbol)" src="images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif"> klicken, erstellen Sie eine neue Richtlinie, die auf einer Vorlage basiert. Weitere Informationen zum Verwenden von Vorlagen finden Sie unter <A href="how-to-new-dlp-data-loss-prevention-policy-template.md">Erstellen einer DLP-Richtlinie aus einer Vorlage</A>.



3.  Füllen Sie auf der Seite **Neue benutzerdefinierte Richtlinie** die folgenden Felder aus:
    
    1.  **Name**   Fügen Sie einen Namen ein, der diese Richtlinie von anderen unterscheidet.
    
    2.  **Beschreibung**   Fügen Sie eine optionale Beschreibung mit einer Zusammenfassung dieser Richtlinie hinzu.
    
    3.  **Status auswählen**   Wählen Sie den Status oder Modus für diese Richtlinie aus. Die neue Richtlinie wird erst vollständig aktiviert, wenn Sie dies angeben. Der Standardmodus für eine Richtlinie sieht einen Test ohne Benachrichtigungen vor.

4.  Klicken Sie auf **Speichern**, um das Erstellen der Referenzinformationen der neuen Richtlinie zu beenden. Die Richtlinie wird der Liste der von Ihnen konfigurierten Richtlinien hinzugefügt, obwohl es noch keine Regeln oder Aktionen gibt, die mit dieser neuen benutzerdefinierten Richtlinie verknüpft sind.

5.  Doppelklicken Sie auf die soeben erstellte Richtlinie, oder wählen Sie sie aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

6.  Klicken Sie auf der Seite **DLP-Richtlinie bearbeiten** auf **Regeln**.
    
    Klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue leere Regel hinzufügen. Sie können Bedingungen mit allen herkömmlichen Transportregeln sowie den Typen vertraulicher Informationen einrichten.
    
    Damit Sie die Übersicht behalten, sollten Sie jedem Bestandteil Ihrer Richtlinie oder Regel einen eindeutigen Namen geben, wenn Sie eine eigene Zeichenfolge bereitstellen können. Es stehen Ihnen mehrere zusätzliche Optionen zur Verfügung:
    
    1.  Klicken Sie auf den Pfeil neben dem Symbol **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Regel zur Absenderbenachrichtigung oder zum Zulassen von Außerkraftsetzungen hinzuzufügen.
    
    2.  Um eine Regel zu entfernen, markieren Sie die Regel und klicken auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").
    
    3.  Klicken Sie auf **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)"), um weitere Bedingungen und Aktionen für diese Regel hinzuzufügen, etwa zeitgebundene Beschränkungen für eine Erzwingung oder Effekte für andere Regeln in dieser Richtlinie.

7.  Klicken Sie auf **Speichern**, um die Bearbeitung der Richtlinie zu beenden und Ihre Änderungen zu speichern.

DLP-Richtlinienvorlagen sind ein Feature von Microsoft Exchange, das es Ihnen ermöglicht, ein robustes Richtlinien- und Einhaltungssystem für Ihre Messagingumgebung zu entwerfen und anzuwenden. Weitere Informationen zu Kompatibilitätsfunktionen finden Sie unter [Messagingrichtlinie und -kompatibilität](messaging-policy-and-compliance-exchange-2013-help.md) (Exchange 2013) oder [Sicherheit und Richtlinientreue für Exchange Online](https://technet.microsoft.com/de-de/library/jj200706\(v=exchg.150\)).

## Weitere Informationen

[Verhinderung von Datenverlust](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)Exchange 2013

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))Exchange Online

[Integrieren von Regeln für vertrauliche Informationen in Transportregeln](integrating-sensitive-information-rules-with-transport-rules-exchange-2013-help.md)

