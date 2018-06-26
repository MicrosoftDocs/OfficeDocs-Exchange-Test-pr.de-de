---
title: 'Verwalten von Warteschlangen: Exchange 2013 Help'
TOCTitle: Verwalten von Warteschlangen
ms:assetid: 37f11378-a884-4aff-ab55-689f40a46321
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997263(v=EXCHG.150)
ms:contentKeyID: 51409279
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Warteschlangen

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-01-31_

In Microsoft Exchange Server 2013 können Sie die Warteschlangenanzeige in der Exchange-Toolbox oder in der Exchange-Verwaltungsshell zur Verwaltung von Warteschlangen verwenden. Weitere Informationen zur Verwendung der Cmdlets zur Warteschlangenverwaltung in der Exchange-Verwaltungsshell finden Sie unter [Verwenden der Exchange-Verwaltungsshell zum Verwalten von Warteschlangen](use-the-exchange-management-shell-to-manage-queues-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Warteschlangen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Warteschlangen anzeigen

## Anzeigen von Warteschlangen mithilfe der Warteschlangenanzeige in der Exchange-Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Warteschlangen**. Es wird eine Liste aller Warteschlangen auf dem Server angezeigt, mit dem die Verbindung besteht.

4.  Im Aktionsbereich können Sie den Link **Liste exportieren** verwenden, um die Liste der Warteschlangen zu exportieren. Weitere Informationen finden Sie unter [Exportieren von Listen aus der Warteschlangenanzeige](export-lists-from-queue-viewer-exchange-2013-help.md).

## Anzeigen von Warteschlangen mithilfe der Shell

Verwenden Sie die folgende Syntax, um Warteschlangen anzuzeigen.

    Get-Queue [-Filter <Filter> -Server <ServerIdentity> -Include <Internal | External | Empty | DeliveryType> -Exclude <Internal | External | Empty | DeliveryType>]

In diesem Beispiel werden grundlegende Informationen zu allen nicht leeren Warteschlangen auf dem Exchange 2013-Postfachserver namens "Mailbox01" angezeigt.

    Get-Queue -Server Mailbox01 -Exclude Empty

In diesem Beispiel werden detaillierte Informationen zu allen Warteschlangen mit mehr als 100 Nachrichten auf dem Postfachserver angezeigt, auf dem der Befehl ausgeführt wird.

    Get-Queue -Filter {MessageCount -gt 100} | Format-List

## Anzeigen zusammenfassender Warteschlangeninformationen auf mehreren Exchange-Servern mithilfe der Shell

Das Cmdlet **Get-QueueDigest** bietet eine aggregierte Übersicht der Warteschlangenstatus auf allen Servern innerhalb eines bestimmten Bereichs, z. B. in einer DAG, an einem Active Directory-Standort, in einer Serverliste oder innerhalb der Active Directory-Gesamtstruktur. Beachten Sie, dass Warteschlangen auf einem abonnierten Edge-Transport-Server im Umkreisnetzwerk nicht in den Ergebnissen enthalten sind. **Get-QueueDigest** ist zwar auf einem Edge-Transport-Server verfügbar, aber die Ergebnisse beschränken sich auf Warteschlangen auf dem Edge-Transport-Server.


> [!NOTE]
> Standardmäßig zeigt das <STRONG>Get-QueueDigest</STRONG>-Cmdlet Zustellungswarteschlangen an, die zehn oder mehr Nachrichten enthalten und deren Ergebnisse zwischen ein und zwei Minuten alt sind. Anweisungen zum Ändern der Standardwerte finden Sie unter <A href="configure-get-queuedigest-exchange-2013-help.md">Konfigurieren von Get-QueueDigest</A>.



Führen Sie den folgenden Befehl aus, um zusammenfassende Informationen zu Warteschlangen auf mehreren Exchange-Servern anzuzeigen:

    Get-QueueDigest <-Server <ServerIdentity1,ServerIdentity2,..> | -Dag <DagIdentity1,DagIdentity2...> | -Site <ADSiteIdentity1,ADSiteIdentity2...> | -Forest> [-Filter <Filter>]

In diesem Beispiel werden zusammenfassende Informationen zu den Warteschlangen auf allen Exchange 2013-Postfachservern am Active Directory-Standort "FirstSite" angezeigt, in denen die Anzahl der Nachrichten 100 übersteigt.

    Get-QueueDigest -Site FirstSite -Filter {MessageCount -gt 100}

In diesem Beispiel werden zusammenfassende Informationen zu den Warteschlangen auf allen Exchange 2013-Postfachservern in der Database Availability Group (DAG) namens "DAG01" angezeigt, deren Warteschlangenstatus den Wert **Retry** aufweist.

    Get-QueueDigest -Dag DAG01 -Filter {Status -eq "Retry"}

## Fortsetzen von Warteschlangen

Durch das Fortsetzen einer Warteschlange werden ausgehende Aktivitäten in einer Warteschlange, die den Status "Angehalten" aufweist, erneut gestartet. Die Warteschlange muss den Status "Angehalten" aufweisen, damit sich diese Aktion auf die Warteschlange auswirkt. Beim Fortsetzen einer Warteschlange ändert sich der Status der Nachrichten in der Warteschlange nicht. Nachrichten mit dem Status "Angehalten" bleiben weiterhin angehalten und verlassen die Warteschlange nicht.

## Fortsetzen von Warteschlangen mithilfe der Warteschlangenanzeige in der Exchange-Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Warteschlangen**. Es wird eine Liste aller Warteschlangen auf dem Server angezeigt, mit dem die Verbindung besteht.

4.  Klicken Sie auf **Filter erstellen**, und geben Sie den gewünschten Filterausdruck wie folgt ein:
    
    1.  Wählen Sie **Status** in der Dropdownliste der Warteschlangeneigenschaften aus.
    
    2.  Wählen Sie den Operator **Gleich** aus der Dropdownliste der Vergleichsoperatoren aus.
    
    3.  Wählen Sie **Angehalten** in der Werte-Dropdownliste aus.

5.  Klicken Sie auf **Filter anwenden**. Alle derzeit auf dem Server angehaltenen Warteschlangen werden angezeigt.

6.  Wählen Sie mindestens eine Warteschlange aus der Liste aus, klicken Sie mit der rechten Maustaste auf die Warteschlange(n), und wählen Sie dann **Fortsetzen** aus.

## Verwenden der Shell zum Fortsetzen von Warteschlangen

Verwenden Sie die folgende Syntax, um Warteschlangen fortzusetzen.

    Resume-Queue <-Identity QueueIdentity | -Filter {QueueFilter} [-Server ServerIdentity]>

In diesem Beispiel werden alle Warteschlangen auf dem lokalen Server fortgesetzt, die den Status "Angehalten" aufweisen.

    Resume-Queue -Filter {Status -eq "Suspended"}

In diesem Beispiel wird die angehaltene Zustellungswarteschlange "contoso.com" auf dem Server "Mailbox01" fortgesetzt.

    Resume-Queue -Identity Mailbox01\contoso.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine Warteschlange erfolgreich fortgesetzt wurde:

1.  Suchen Sie die Warteschlange, die fortgesetzt werden soll, mithilfe der Warteschlangenanzeige oder über das Cmdlet **Get-Queue**.

2.  Stellen Sie sicher, dass die Eigenschaft **Status** der Warteschlange nicht den Wert `Suspended` aufweist.

## Wiederholen von Warteschlangen

Wenn ein Transportserver keine Verbindung mit dem nächsten Hop herstellen kann, wird die Zustellungswarteschlange in den Status Wiederholen versetzt. Wenn für eine Zustellungswarteschlange mithilfe der Warteschlangenanzeige oder der Shell ein Wiederholungsversuch ausgeführt wird, wird ein sofortiger Verbindungsversuch erzwungen, wodurch der nächste geplante Wiederholungszeitpunkt außer Kraft gesetzt wird. Kommt keine Verbindung zustande, wird der nächste Wiederholungszeitpunkt zurückgesetzt. Die Zustellungswarteschlange muss den Status Wiederholen aufweisen, damit diese Aktion wirksam ist.

## Wiederholen einer Warteschlange mithilfe der Warteschlangenanzeige in der Exchange-Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Warteschlangen**. Es wird eine Liste aller Warteschlangen auf dem Server angezeigt, mit dem die Verbindung besteht.

4.  Klicken Sie auf **Filter erstellen**, und geben Sie den gewünschten Filterausdruck wie folgt ein:
    
    1.  Wählen Sie **Status** in der Dropdownliste der Warteschlangeneigenschaften aus.
    
    2.  Wählen Sie den Operator **Gleich** aus der Dropdownliste der Vergleichsoperatoren aus.
    
    3.  Wählen Sie den Wert **Wiederholen** aus der Dropdownliste aus.

5.  Klicken Sie auf **Filter anwenden**. Alle Warteschlangen, die zurzeit den Status **Wiederholen** aufweisen, werden angezeigt.

6.  Wählen Sie mindestens eine Warteschlange aus der Liste aus. Klicken Sie mit der rechten Maustaste, und wählen Sie dann **Wiederholungsversuch für Warteschlange**. Kommt eine Verbindung zustande, wird der Warteschlangenstatus in **Aktiv** geändert. Kann keine Verbindung hergestellt werden, bleibt die Warteschlange im Status **Wiederholen**, und der nächste Wiederholungszeitpunkt wird aktualisiert.

## Ausführen eines Wiederholungsversuchs für eine Warteschlange mithilfe der Shell

Verwenden Sie die folgende Syntax, um Warteschlangen zu wiederholen.

    Retry-Queue <-Identity QueueIdentity | -Filter QueueFilter [-Server ServerIdentity]>

In diesem Beispiel wird für alle Warteschlangen auf dem lokalen Server, die den Status "Wiederholen" aufweisen, ein Wiederholungsversuch ausgeführt.

    Retry-Queue -Filter {status -eq "retry"}

In diesem Beispiel wird für die Warteschlange "contoso.com", die sich auf dem Server "Mailbox01" im Zustand `Retry` befindet, ein Wiederholungsversuch durchgeführt.

    Retry-Queue -Identity Mailbox01\contoso.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine Warteschlange erfolgreich wiederholt wurde:

1.  Suchen Sie die Warteschlange, für die Sie einen Wiederholungsversuch gestartet haben, mithilfe der Warteschlangenanzeige oder über das Cmdlet **Get-Queue**.

2.  Stellen Sie sicher, dass die Eigenschaft **LastRetryTime** der Warteschlange mit dem Zeitpunkt übereinstimmt, zu dem Sie einen Wiederholungsversuch für die Warteschlange unternommen haben.

## Erneutes Übermitteln von Nachrichten in Warteschlangen

Die erneute Übermittlung einer Warteschlange ähnelt der Wiederholung einer Warteschlange, außer dass die Nachrichten an die Übermittlungswarteschlange zurückgesendet werden, um vom Kategorisierungsmodul erneut verarbeitet zu werden. Sie können Nachrichten, die den folgenden Status besitzen, erneut übermitteln:

  - Zustellungswarteschlangen mit dem Status "Wiederholen". Die Nachrichten in den Warteschlangen können nicht den Status "Angehalten" aufweisen.

  - Nachrichten in der Nicht-erreichbar-Warteschlange, die nicht den Status "Angehalten" aufweisen.

  - Nachrichten in der Warteschlange für potenziell schädliche Nachrichten.

## Erneutes Übermitteln von Nachrichten mithilfe der Shell

Verwenden Sie die folgende Syntax, um Nachrichten erneut zu übermitteln.

    Retry-Queue <-Identity QueueIdentity | -Filter {Status -eq "Retry"} -Server ServerIdentity> -Resubmit $true

In diesem Beispiel werden alle Nachrichten erneut übermittelt, die sich in einer beliebigen Zustellungswarteschlange mit dem Status "Wiederholen" auf dem Server "Mailbox01" befinden.

    Retry-Queue -Filter {Status -eq "Retry"} -Server Mailbox01 -Resubmit $true

In diesem Beispiel werden alle Nachrichten erneut übermittelt, die sich in der Nicht-erreichbar-Warteschlange auf dem Server "Mailbox01" befinden.

    Retry-Queue -Identity Mailbox01\Unreachable -Resubmit $true

## Erneutes Übermitteln von Nachrichten in der Warteschlange für nicht verarbeitbare Nachrichten

Nachrichten in der Warteschlange für nicht verarbeitbare Nachrichten werden erneut übermittelt, indem Sie die Nachricht fortsetzen. Sie können die Warteschlangenanzeige oder die Shell zum erneuten Übermitteln von Nachrichten verwenden, die sich in der Warteschlange für nicht verarbeitbare Nachrichten befinden. Beachten Sie, dass die Warteschlange für nicht verarbeitbare Nachrichten in der Warteschlangenanzeige nur dann angezeigt wird, wenn sie Nachrichten enthält.


> [!NOTE]
> Die Warteschlange für nicht verarbeitbare Nachrichten enthält Nachrichten, die nach einem Serverausfall als schädlich für das Exchange-System erkannt werden. Die Nachrichten können hinsichtlich ihres Inhalts oder Formats tatsächlich schädlich sein. Alternativ können sie jedoch auch das Opfer eines schlecht programmierten Agents sein, der während der Verarbeitung vermeintlich fehlerhafter Nachrichten zu einem Absturz des Exchange-Servers geführt hat. Wenn Sie nicht von der Sicherheit der Nachrichten in der Warteschlange für nicht verarbeitbare Nachrichten überzeugt sind, sollten Sie die Nachrichten in Dateien exportieren, sodass sie überprüft werden können. Weitere Informationen finden Sie unter <A href="export-messages-from-queues-exchange-2013-help.md">Nachrichten aus Warteschlangen exportieren</A>.



## Erneutes Übermitteln von Nachrichten in der Warteschlange für nicht verarbeitbare Nachrichten mithilfe der Warteschlangenanzeige in der Exchange-Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Warteschlangen**. Es wird eine Liste aller Warteschlangen auf dem Server angezeigt, mit dem die Verbindung besteht.

4.  Klicken Sie auf die Warteschlange für potenziell schädliche Nachrichten. Wählen Sie im Aktionsbereich **Nachrichten anzeigen** aus.

5.  Wählen Sie mindestens eine Nachricht aus der Liste aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Fortsetzen** aus.

## Erneutes Übermitteln von Nachrichten in der Warteschlange für nicht verarbeitbare Nachrichten mithilfe der Shell

Führen Sie die folgenden Schritte durch, um eine Nachricht aus der Warteschlange für nicht verarbeitbare Nachrichten erneut zu übermitteln.

1.  Finden Sie die Identität der Nachricht, indem Sie den folgenden Befehl ausführen.
    
        Get-Message -Queue Poison | Format-Table Identity

2.  Verwenden Sie die Identität der Nachricht aus dem vorherigen Schritt im folgenden Befehl.
    
        Resume-Message <PoisonMessageIdentity>
    
    In diesem Beispiel wird die Nachricht mit dem Identitätswert 222 aus der Warteschlange für potenziell schädliche Nachrichten fortgesetzt.
    
        Resume-Message 222

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine Nachricht aus der Warteschlange für nicht verarbeitbare Nachrichten erneut übermittelt wurde:

1.  Zeigen Sie die Warteschlange für nicht verarbeitbare Nachrichten, aus der Sie die Nachricht erneut übermittelt haben, mithilfe der Warteschlangenanzeige oder über das Cmdlet **Get-Queue** an.

2.  Stellen Sie sicher, dass die Nachricht nicht mehr in die Warteschlange für nicht verarbeitbare Nachrichten enthalten ist. Beachten Sie, dass eine leere Warteschlange für nicht verarbeitbare Nachrichten in der Warteschlangenanzeige und im Cmdlet **Get-Queue** nicht angezeigt wird. Wenn die Nachricht, die Sie erneut übermittelt haben, die einzige Nachricht in der Warteschlange für nicht verarbeitbare Nachrichten war und die Warteschlange für nicht verarbeitbare Nachrichten nicht mehr angezeigt wird, ist dies daher ein Indiz dafür, dass die Nachricht erfolgreich übermittelt wurde.

## Anhalten von Warteschlangen

Durch das Anhalten einer Warteschlange wird verhindert, dass Nachrichten die Warteschlange verlassen. Der Status von Nachrichten in der Warteschlange ändert sich jedoch nicht. In Verarbeitung befindliche SMTP-Sendevorgänge von Nachrichten werden zunächst fertig gestellt. Sie können eine Warteschlange anhalten, um die Nachrichtenübermittlung zu beenden, und anschließend eine oder mehrere Nachrichten in der Warteschlange anhalten. Beim Fortsetzen der Warteschlange verlassen die angehaltenen Nachrichten nicht die Warteschlange.

Sie können eine Warteschlange anhalten, die den Status Aktiv oder Wiederholen aufweist. Auch die Nicht-erreichbar-Warteschlange und die Übermittlungswarteschlange können angehalten werden.

Wenn die Nicht-erreichbar-Warteschlange angehalten wird, werden bei Eingang von Konfigurationsupdates über den Transportserver Elemente erst wieder an das Kategorisierungsmodul übermittelt, wenn die Warteschlange fortgesetzt wird. Wenn die Übermittlungswarteschlange angehalten wird, werden vom Kategorisierungsmodul erst wieder Nachrichten abgeholt, wenn die Warteschlange fortgesetzt wird.

## Anhalten einer Warteschlange mithilfe der Warteschlangenanzeige in der Exchange-Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Klicken Sie in der Warteschlangenanzeige auf die Registerkarte **Warteschlangen**. Es wird eine Liste aller Warteschlangen auf dem Server angezeigt, mit dem die Verbindung besteht. Sie können einen Filter erstellen, um nur die Warteschlangen anzuzeigen, die bestimmten Kriterien entsprechen.

4.  Wählen Sie mindestens eine Warteschlangen aus, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Anhalten** aus.

## Anhalten einer Warteschlange mithilfe der Shell

Verwenden Sie die folgende Syntax, um eine Warteschlange anzuhalten.

    Suspend-Queue <-Identity QueueIdentity | -Filter {QueueFilter} [-Server ServerIdentity]>

In diesem Beispiel werden alle Warteschlangen auf dem lokalen Server angehalten, die 1.000 oder mehr Nachrichten enthalten und den Status "Wiederholen" aufweisen.

    Suspend-Queue -Filter {MessageCount -ge 1000 -and Status -eq "Retry"}

In diesem Beispiel wird die Warteschlange "contoso.com" auf dem Server "Mailbox01" angehalten.

    Suspend-Queue -Identity Mailbox01\contoso.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine Warteschlange erfolgreich angehalten wurde:

1.  Suchen Sie die Warteschlange, die angehalten werden soll, mithilfe der Warteschlangenanzeige oder über das Cmdlet **Get-Queue**.

2.  Stellen Sie sicher, dass die Eigenschaft **Status** der Warteschlange den Wert `Suspended` aufweist.

