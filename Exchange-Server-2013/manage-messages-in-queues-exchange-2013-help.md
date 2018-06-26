---
title: 'Verwalten von Nachrichten in Warteschlangen: Exchange 2013 Help'
TOCTitle: Verwalten von Nachrichten in Warteschlangen
ms:assetid: 83358884-6036-4e91-87a8-35200541874d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123535(v=EXCHG.150)
ms:contentKeyID: 51409318
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von Nachrichten in Warteschlangen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-05-07_

In Microsoft Exchange Server 2013 können Sie die Warteschlangenanzeige in der Exchange Toolbox oder Exchange-Verwaltungsshell zum Verwalten von Nachrichten in Warteschlangen verwenden. Weitere Informationen zu den Cmdlets zur Nachrichtenverwaltung in der Exchange-Verwaltungsshell finden Sie unter [Verwenden der Exchange-Verwaltungsshell zum Verwalten von Warteschlangen](use-the-exchange-management-shell-to-manage-queues-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Warteschlangen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Nachrichten aus Warteschlangen entfernen

Eine Nachricht, die an mehrere Empfänger gesendet wird, kann sich in mehreren Warteschlangen befinden. Zum Entfernen einer Nachricht aus mehreren Warteschlangen in einem einzelnen Vorgang muss ein Filter verwendet werden. Sie können auswählen, ob beim Entfernen von Nachrichten aus einer Warteschlange ein Unzustellbarkeitsbericht (Non-Delivery Report, NDR) gesendet werden soll. Sie können keine Nachrichten aus einer Übermittlungswarteschlange entfernen.

## Entfernen von Nachrichten mithilfe der Warteschlangenanzeige in der Exchange Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Nachrichten**. Es wird eine Liste aller Nachrichten auf dem Server angezeigt, mit dem eine Verbindung besteht. Um die Aktion an eine einzelne Warteschlange anzupassen, klicken Sie auf die Registerkarte **Warteschlangen**, doppelklicken Sie auf den Warteschlangennamen, und klicken Sie anschließend auf die angezeigte Registerkarte *Server\\Warteschlange*.

4.  Wählen Sie eine oder mehrere Nachrichten aus der Liste aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Nachrichten entfernen (mit Unzustellbarkeitsbericht)** oder **Nachrichten entfernen (ohne Unzustellbarkeitsbericht)** aus. Es wird ein Dialogfeld angezeigt, das die ausgewählte Aktion bestätigt und die Meldung **Möchten Sie fortfahren** anzeigt. Klicken Sie auf **Ja**.

5.  Zum Entfernen aller Nachrichten aus einer bestimmten Warteschlange klicken Sie auf die Registerkarte **Warteschlangen**. Wählen Sie eine Wartschlange aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Nachrichten entfernen (mit Unzustellbarkeitsbericht)** oder **Nachrichten entfernen (ohne Unzustellbarkeitsbericht)** aus. Es wird ein Dialogfeld angezeigt, das die ausgewählte Aktion bestätigt und die Meldung **Möchten Sie fortfahren** anzeigt. Klicken Sie auf **Ja**.
    

    > [!NOTE]
    > Wenn Sie mit einer gefilterten Liste arbeiten, enthält die angezeigte Seite möglicherweise nicht alle Elemente im Filter. In diesem Fall wird eine Eingabeaufforderung mit folgendem Wortlaut angezeigt: <STRONG>Diese Aktion wirkt sich auf alle Elemente auf dieser Seite aus. Um den Bereich dieser Aktion so zu erweitern, dass alle Elemente von diesem Filter berücksichtigt werden, aktivieren Sie das folgende Kontrollkästchen, bevor Sie auf 'OK' klicken.</STRONG>



## Entfernen von Nachrichten mithilfe der Shell

Verwenden Sie die folgende Syntax, um Nachrichten aus Warteschlangen zu entfernen.

    Remove-Message <-Identity MessageIdentity | -Filter {MessageFilter}> -WithNDR <$true | $false>

In diesem Beispiel werden Nachrichten in den Warteschlangen entfernt, die den Betreff "Win Big" aufweisen, ohne dass ein Unzustellbarkeitsbericht gesendet wird.

    Remove-Message -Filter {Subject -eq "Win Big"} -WithNDR $false

In diesem Beispiel wird die Nachricht mit der Nachrichten-ID 3 in der Nicht-erreichbar-Warteschlange auf dem Server "Mailbox01" angehalten und ein Unzustellbarkeitsbericht gesendet.

    Remove-Message -Identity Mailbox01\Unreachable\3 -WithNDR $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um sich zu vergewissern, dass Sie Nachrichten erfolgreich aus Warteschlangen entfernt haben:

  - Wählen Sie in der Warteschlangenanzeige die Warteschlange aus, oder erstellen Sie einen Filter, um sich zu vergewissern, dass die Nachrichten nicht mehr vorhanden sind.

  - Mit dem Cmdlet **Get-Message** und dem Parameter *Queue* oder *Filter* können Sie sicherstellen, dass die Nachrichten nicht mehr vorhanden sind. Weitere Informationen finden Sie unter [Get-Message](https://technet.microsoft.com/de-de/library/bb124738\(v=exchg.150\)).

## Nachrichten in Warteschlangen fortsetzen

Eine Nachricht, die aktuell den Status Angehalten aufweist, kann fortgesetzt werden. Durch das Fortsetzen einer Nachricht aktivieren Sie die Zustellung der Nachricht. Wenn Sie eine Nachricht fortsetzen, die sich in der Warteschlange für potenziell schädliche Nachrichten befindet, wird die betreffende Nachricht für die Verarbeitung an das Kategorisierungsmodul gesendet. Eine Nachricht, die an mehrere Empfänger gesendet wird, kann sich in mehreren Warteschlangen befinden. Wenn Sie eine Nachricht in einem Vorgang in mehreren Warteschlangen fortsetzen möchten, müssen Sie einen Filter verwenden.

## Fortsetzen von Nachrichten mithilfe der Warteschlangenanzeige in Exchange Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Nachrichten**. Es wird eine Liste aller Nachrichten auf dem Server angezeigt, mit dem eine Verbindung besteht. Klicken Sie auf die Registerkarte **Warteschlangen**, doppelklicken Sie auf den Warteschlangennamen, und klicken Sie anschließend auf die angezeigte Registerkarte *Server\\Warteschlange*, um den Schwerpunkt der Aktion auf eine einzelne Warteschlange festzulegen.

4.  Klicken Sie auf **Filter erstellen**, und geben Sie den gewünschten Filterausdruck wie folgt ein:
    
    1.  Wählen Sie **Status** in der Dropdownliste der Nachrichteneigenschaften aus.
    
    2.  Wählen Sie den Operator **Gleich** aus der Dropdownliste der Vergleichsoperatoren aus.
    
    3.  Wählen Sie **Angehalten** in der Werte-Dropdownliste aus.

5.  Klicken Sie auf **Filter anwenden**. Alle Nachrichten, die den Status Angehalten aufweisen, werden angezeigt.

6.  Wählen Sie mindestens eine Nachricht aus der Liste aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Fortsetzen** aus.

## Fortsetzen von Nachrichten mithilfe der Shell

Verwenden Sie die folgende Syntax, um Nachrichten fortzusetzen:

    Resume-Message <-Identity MessageIdentity | -Filter {MessageFilter}>

In diesem Beispiel werden alle Nachrichten fortgesetzt, die von beliebigen Absendern in der Domäne "Contoso.com" gesendet wurden.

    Resume-Message -Filter {FromAddress -eq "*contoso.com"}

In diesem Beispiel wird die Nachricht mit der Nachrichten-ID 3 in der Nicht-erreichbar-Warteschlange auf dem Server "Hub01" fortgesetzt.

    Resume-Message -Identity Hub01\Unreachable\3

Um Nachrichten aus der Warteschlange für nicht verarbeitbare Nachrichten erneut zu übermitteln, führen Sie die folgenden Schritte aus:

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um sich zu vergewissern, dass Sie Nachrichten erfolgreich in Warteschlangen fortgesetzt haben:

  - Wählen Sie in der Warteschlangenanzeige die Warteschlange aus, oder erstellen Sie einen Filter, um sich zu vergewissern, dass die Nachrichten nicht mehr angehalten sind.

  - Mit dem Cmdlet **Get-Message** und dem Parameter *Queue* oder *Filter* können Sie prüfen, ob die Nachrichten nicht mehr angehalten sind. Weitere Informationen finden Sie unter [Get-Message](https://technet.microsoft.com/de-de/library/bb124738\(v=exchg.150\)).

Wenn Sie die Nachricht in keiner Warteschlange auf dem Server finden können, bedeutet dies zumeist, dass die Nachricht erfolgreich an den nächsten Hop übermittelt wurde.

## Nachrichten in Warteschlangen anhalten

Wenn Sie eine Nachricht anhalten, verhindern Sie die Zustellung der Nachricht. Eine Nachricht, die in der Warteschlange angezeigt wird, sich jedoch bereits in Zustellung befindet, wird nicht angehalten. Die Zustellung wird fortgesetzt, und der Nachrichtenstatus lautet **PendingSuspend**. Wenn ein Fehler bei der Zustellung auftritt, wird die Nachricht erneut in die Warteschlange eingereiht und dann angehalten. Sie können keine Nachricht anhalten, die sich in der Übermittlungswarteschlange oder der Warteschlange für potenziell schädliche Nachrichten befindet.

Eine Nachricht, die an mehrere Empfänger gesendet wird, kann sich in mehreren Warteschlangen befinden. Wenn Sie eine Nachricht in einem Vorgang in mehreren Warteschlangen anhalten möchten, müssen Sie einen Filter verwenden.

## Anhalten von Nachrichten mithilfe der Warteschlangenanzeige in Exchange Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Nachrichten**. Es wird eine Liste aller Nachrichten auf dem Server angezeigt, mit dem eine Verbindung besteht. Um die Ansicht auf eine einzelne Warteschlange einzuschränken, klicken Sie auf die Registerkarte **Warteschlangen**, klicken Sie doppelt auf den Warteschlangennamen, und klicken Sie anschließend auf die angezeigte Registerkarte *Server\\Warteschlange*.

4.  Wählen Sie mindestens eine Nachricht aus, klicken Sie dann mit der rechten Maustaste, und wählen Sie anschließend **Anhalten** aus.

## Anhalten von Nachrichten mithilfe der Shell

Verwenden Sie die folgende Syntax, um Nachrichten anzuhalten:

    Suspend-Message <-Identity MessageIdentity | -Filter {MessageFilter}>

Im folgenden Beispiel werden alle Nachrichten in der Warteschlange angehalten, die von einem beliebigen Absender in der Domäne "contoso.com" stammen:

    Suspend-Message -Filter {FromAddress -eq "*contoso.com"}

In diesem Beispiel wird die Nachricht mit der Nachrichten-ID 3 in der Nicht-erreichbar-Warteschlange auf dem Server "Mailbox01" angehalten:

    Suspend-Message -Identity Mailbox01\Unreachable\3

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie einen der folgenden Schritte aus, um sich zu vergewissern, dass Sie Nachrichten erfolgreich in Warteschlangen angehalten haben:

  - Wählen Sie in der Warteschlangenanzeige die Warteschlange aus, oder erstellen Sie einen Filter, um sich zu vergewissern, dass die Nachrichten angehalten sind.

  - Mit dem Cmdlet **Get-Message** und dem Parameter *Queue* oder *Filter* können Sie prüfen, ob die Nachrichten angehalten sind. Weitere Informationen finden Sie unter [Get-Message](https://technet.microsoft.com/de-de/library/bb124738\(v=exchg.150\)).

