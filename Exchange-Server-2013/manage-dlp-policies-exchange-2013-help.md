---
title: 'Verwalten von DLP-Richtlinien: Exchange 2013 Help'
TOCTitle: Verwalten von DLP-Richtlinien
ms:assetid: ba81fabd-7f7f-4ef7-968f-ce851ada9d70
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673559(v=EXCHG.150)
ms:contentKeyID: 50476565
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von DLP-Richtlinien

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-01-14_

Mit der Exchange-Verwaltungskonsole oder der Exchange-Verwaltungsshell können Sie vorhandene Richtlinien zur Verhinderung von Datenverlusten (Data Loss Prevention, DLP) in Microsoft Exchange anzeigen, ändern oder entfernen.

Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit DLP finden Sie unter [DLP-Verfahren](dlp-procedures-exchange-2013-help.md) (Exchange Server 2013) oder [DLP-Verfahren](https://technet.microsoft.com/de-de/library/jj938003\(v=exchg.150\)) (Exchange Online).

Weitere Informationen zur Exchange-Verwaltungsshell finden Sie unter [Verwenden von Powershell mit Exchange 2013 (Exchange-Verwaltungsshell)](https://technet.microsoft.com/de-de/library/bb123778\(v=exchg.150\)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15-60 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Verhinderung von Datenverlust (Data Loss Prevention, DLP)" im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Für jede DLP-Richtlinie können Sie einen von drei Modi auswählen:
    
      -    **Erzwingen**   Regeln in der Richtlinie werden für alle Nachrichten und unterstützten Dateitypen ausgewertet. Der Nachrichtfluss kann unterbrochen werden, wenn Daten gefunden werden, die die Bedingungen der Richtlinie erfüllen. Alle in der Richtlinie beschriebenen Aktionen werden ausgeführt.
    
      -    **DLP-Richtlinie mit Richtlinientipps testen**   Regeln in der Richtlinie werden für alle Nachrichten und unterstützten Dateitypen ausgewertet. Der Nachrichtfluss wird nicht unterbrochen, wenn Daten gefunden werden, die die Bedingungen der Richtlinie erfüllen. Das heißt, Nachrichten werden nicht blockiert. Wenn Richtlinientipps konfiguriert sind, werden sie den Benutzern angezeigt.
    
      -    **DLP-Richtlinie ohne Richtlinientipps testen**   Regeln in der Richtlinie werden für alle Nachrichten und unterstützten Dateitypen ausgewertet. Der Nachrichtfluss wird nicht unterbrochen, wenn Daten gefunden werden, die die Bedingungen der Richtlinie erfüllen. Das heißt, Nachrichten werden nicht blockiert. Wenn Richtlinientipps konfiguriert sind, werden sie den Benutzern nicht angezeigt.

  - Eine einzelne Regel in einer DLP-Richtlinie kann eigene Moduseinstellungen haben. Wenn der Modus einer Richtlinie und der Modus einer Regel in dieser Richtlinie unterschiedlich sind, hat die Regeleinstellung Vorrang und wird entsprechend ihrem Modus ausgewertet.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen der Details einer vorhandenen DLP-Richtlinie

Möglicherweise müssen Sie die Regeln und Aktionen einer vorhandenen DLP-Richtlinie anzeigen, die Sie bereits für Ihre Organisation eingerichtet haben. Dies kann erforderlich sein, wenn es unerwartete Nachrichtenflussprobleme gibt oder wenn in Ihrer Organisation die Vorschriften geändert wurden, wie vertrauliche Informationen zu überwachen sind.

## Anzeigen der Details einer vorhandenen DLP-Richtlinie mit der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Doppelklicken Sie auf eine der Richtlinien in der Richtlinienliste, oder markieren Sie ein Element, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **DLP-Richtlinie bearbeiten** auf **Regeln**.


> [!TIP]
> Sie können eine DLP-Richtlinie erstellen und im deaktivierten Modus belassen. In diesem Modus wird die Richtlinie nicht erzwungen, und Sie können, bevor Sie die Richtlinie testen oder aktivieren, alle Prädikate, Aktionen oder Werte ändern, die ihr zugewiesen sind.



## Anzeigen der Details einer vorhandenen DLP-Richtlinie mit der Shell

In diesem Beispiel werden Informationen zur fiktiven DLP-Richtlinie "Employee Numbers" zurückgegeben. Der Befehl wird mittels Pipe zum Cmdlet **Format-List** umgeleitet, um die Detailkonfiguration der angegebenen DLP-Richtlinie anzuzeigen.

    Get-DlpPolicy "Employee Numbers" | Format-List

Informationen zu Syntax und Parametern finden Sie unter [Get-DlpPolicy](https://technet.microsoft.com/de-de/library/jj215752\(v=exchg.150\)).

## Ändern einer DLP-Richtlinie

Sie können eine vorhandene DLP-Richtlinie ändern, indem Sie entweder den Namen der Richtlinie oder die Regeln ändern, die die Auswirkungen der Richtlinie bestimmen. Eine Regeländerung kann beispielsweise darin bestehen, benutzerdefinierten Text für den Haftungsausschluss an einen Nachrichtentext anzufügen sowie Rechteverwaltungsdienste-Schutz für Nachrichten hinzuzufügen, die in einer bestimmten Domäne gesendet wurden und für die festgestellt wurde, dass sie vertrauliche Informationen enthalten. Wenn Sie DLP-Richtlinienvorlagen verwenden, sollten Sie daran denken, dass diese nur eines der Features in Exchange 2013 sind, die es Ihnen ermöglichen, ein robustes Richtlinien- und Einhaltungssystem für Ihre Messagingumgebung zu entwerfen und anzuwenden.

## Ändern einer vorhandenen DLP-Richtlinie mit der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Doppelklicken Sie auf eine der vorlagenbasierten Richtlinien in der Richtlinienliste, oder markieren Sie ein Element, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Seite **DLP-Richtlinie bearbeiten** auf **Regeln**.

4.  Markieren Sie die Regel, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um eine vorhandene Regel zu ändern.

5.  Klicken Sie auf **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine neue leere Regel hinzuzufügen, die Sie vollständig anpassen können.

6.  Klicken Sie auf den Pfeil neben dem Symbol **Neu**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um eine Regel für eine Absenderbenachrichtigung, für ein Blockieren von Nachrichten oder für ein Zulassen von Außerkraftsetzungen hinzuzufügen.

7.  Um eine Regel zu entfernen, markieren Sie die Regel und klicken auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

8.  Klicken Sie auf **Speichern**, um die Bearbeitung der Richtlinie zu beenden und Ihre Änderungen zu speichern.

## Ändern einer vorhandenen DLP-Richtlinie mit der Shell

Mit der Exchange-Verwaltungsshell können Sie die Aktions- und die Benachrichtigungsebene einer Richtlinie angeben. In diesem Beispiel wird der Modus einer fiktiven DLP-Richtlinie namens "Employee Numbers" so festgelegt, dass die Aktionen nicht erzwungen und die Benachrichtigungsnachrichten nicht angezeigt werden.

    Set-DlpPolicy "Employee Numbers" -Mode Audit

Informationen zu Syntax und Parametern finden Sie unter [Set-DlpPolicy](https://technet.microsoft.com/de-de/library/jj215778\(v=exchg.150\)).

## Löschen einer DLP-Richtlinie

Mit der Exchange-Verwaltungskonsole können Sie eine DLP-Richtlinie endgültig entfernen. Sobald Sie eine Richtlinie gelöscht haben, wird sie nicht länger erzwungen, und keine der Regeln und Aktionen wird gespeichert.

Alternativ können Sie den Betriebsstatus oder -modus einer Richtlinie auf **DLP-Richtlinie ohne Richtlinientipps testen** festlegen. Dies bewirkt, dass die Richtlinie nicht länger in Ihrer Messagingumgebung erzwungen wird, die ausführlichen Konfigurationseinstellungen der Richtlinie aber erhalten bleiben. Dies kann nützlich sein, wenn die Möglichkeit besteht, dass Sie die Richtlinie später erneut erzwingen müssen.

## Löschen einer vorhandenen DLP-Richtlinie mit der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Verwaltung der Richtlinientreue** \> **Verhinderung von Datenverlust**.

2.  Wählen Sie in der Liste der Richtlinien die Richtlinie aus, die Sie entfernen möchten, und klicken Sie dann auf **Entfernen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Löschen einer vorhandenen DLP-Richtlinie mit der Shell

In diesem Beispiel wird die fiktive DLP-Richtlinie "Employee Numbers" entfernt.

    Remove-DlpPolicy "Employee Numbers"

Informationen zu Syntax und Parametern finden Sie unter [Remove-DlpPolicy](https://technet.microsoft.com/de-de/library/jj215677\(v=exchg.150\)).

## Weitere Informationen

[Verhinderung von Datenverlust](https://technet.microsoft.com/de-de/library/JJ150527(v=EXCHG.150))

[Richtlinientipps](https://technet.microsoft.com/de-de/library/JJ150512(v=EXCHG.150))

