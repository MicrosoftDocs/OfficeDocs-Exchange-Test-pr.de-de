---
title: 'Anzeigen von Eigenschaften in der Warteschlange befindlicher Nachrichten in der Warteschlangenanzeige: Exchange 2013 Help'
TOCTitle: Anzeigen von Eigenschaften in der Warteschlange befindlicher Nachrichten in der Warteschlangenanzeige
ms:assetid: 9d15d8b8-e061-4288-9354-df58e282fb6b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123934(v=EXCHG.150)
ms:contentKeyID: 50476310
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.Edge.SystemManager.MessagePropertyPage
ms.translationtype: HT
---

# Anzeigen von Eigenschaften in der Warteschlange befindlicher Nachrichten in der Warteschlangenanzeige

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2013-01-17_

Verwenden Sie die Warteschlangenanzeige in der Exchange Toolbox, um die Eigenschaften einer Nachricht anzuzeigen, die sich zurzeit in der Warteschlange für die Zustellung befindet.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Warteschlangen" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Sie können auch das Cmdlet Get-Message in der Exchange-Verwaltungsshell verwenden, um weitere Nachrichteneigenschaften anzuzeigen, die in der Warteschlangenanzeige nicht gezeigt werden. Weitere Informationen finden Sie unter [Nachrichtenfilter](message-filters-exchange-2013-help.md) und [Verwenden der Exchange-Verwaltungsshell zum Verwalten von Warteschlangen](use-the-exchange-management-shell-to-manage-queues-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen der Eigenschaften einer Nachricht mithilfe der Warteschlangenanzeige in der Exchange-Toolbox

1.  Klicken Sie auf **Start** \> **Alle Programme** \> **Microsoft Exchange 2013** \> **Exchange Toolbox**.

2.  Doppelklicken Sie im Abschnitt **Nachrichtenflusstools** auf **Warteschlangenanzeige**, um das Tool in einem neuen Fenster zu öffnen.

3.  Wählen Sie in der Warteschlangenanzeige die Registerkarte **Nachrichten** aus, um eine Liste mit den Nachrichten anzuzeigen, die sich zurzeit in der Warteschlange für die Zustellung befinden.

4.  Klicken Sie mit der rechten Maustaste auf die Nachricht, deren Eigenschaften angezeigt werden sollen, und wählen Sie dann **Eigenschaften** aus.

5.  
    
    Auf der Registerkarte **Allgemein** werden die folgenden Angaben zu dieser Nachricht angezeigt:
    
      - **Identität**   Dieses Feld zeigt die ganze Zahl an, die für eine bestimmte Nachricht steht. Die Nachrichtenidentität wird von der Warteschlangendatenbank zugewiesen, wenn die Nachricht zur Verarbeitung empfangen wird. Sie können eine optionale Server- und Warteschlangenidentität mit aufnehmen, um eine Instanz der Nachricht eindeutig zu identifizieren.
    
      - **Betreff**   Dieses Feld zeigt den Betreff einer Nachricht in Form einer Textzeichenfolge an. Der Wert wird aus dem Kopfzeilenfeld `Subject:` übernommen.
    
      - **Internetnachrichten-ID**   Dieses Feld zeigt den Wert des Kopfzeilenfelds `MessageID:` an. Der Wert dieser Eigenschaft wird als GUID, gefolgt von der SMTP-Adresse des sendenden Servers, ausgedrückt; siehe folgendes Beispiel: 67D754D6103DC4FB3BA6BC7205DACABA61231@exchange.contoso.com
    
      - **Von Adresse**   Dieses Feld zeigt die SMTP-Adresse des Nachrichtenabsenders an. Dieser Wert wird dem Feld MAIL FROM: im Nachrichtenumschlag entnommen.
    
      - **Status** In diesem Feld wird der aktuelle Status der Nachricht angezeigt. Eine Nachricht kann einen der folgenden Statuswerte aufweisen:
        
          - **Aktiv**   Wenn die Nachricht sich in einer Zustellungswarteschlange befindet, wird die Nachricht an ihr Ziel zugestellt. Wenn die Nachricht sich in der Übermittlungswarteschlange befindet, wird sie vom Kategorisierungsmodul verarbeitet.
        
          - **Entfernen ausstehend**   Die Nachricht wurde vom Administrator gelöscht, befand sich aber bereits in der Zustellung. Die Nachricht wird gelöscht, wenn die Zustellung mit einem Fehler endet, der ein erneutes Eintreten der Nachricht in die Wartschlange bewirkt. Andernfalls wird die Zustellung fortgesetzt.
        
          - **Anhaltevorgang ausstehend**   Die Nachricht wurde vom Administrator angehalten, befand sich aber bereits in der Zustellung. Die Nachricht wird angehalten, wenn die Zustellung mit einem Fehler endet, der ein erneutes Eintreten der Nachricht in die Wartschlange bewirkt. Andernfalls wird die Zustellung fortgesetzt.
        
          - **Bereit**   Die Nachricht wartet in der Warteschlange und ist zur Verarbeitung bereit.
        
          - **Wiederholen**   Fehler beim letzten Verbindungsversuch für die Warteschlange, in der sich diese Nachricht befindet. Die Nachricht wartet auf den nächsten Wiederholungsversuch der Warteschlange.
        
          - **Angehalten**   Die Nachricht wurde vom Administrator angehalten.
    
      - **Größe (KB)**   Dieses Feld zeigt die Größe der Nachricht an, aufgerundet auf das nächste KB.
    
      - **Name der Nachrichtenquelle**   Dieses Feld zeigt den Namen der Komponente an, die diese Nachricht an die Warteschlange übermittelt hat.
    
      - **Quell-IP**   Dieses Feld zeigt die IP-Adresse des externen Servers an, der die Nachricht an die Exchange-Organisation übermittelt hat.
    
      - **SCL (Spam Confidence Level)** Dieses Feld zeigt die SCL-Bewertung (Spam Confidence Level) der Nachricht an. Gültige SCL-Einträge sind die ganzen Zahlen von 0 bis 9 oder -1. Ein leerer SCL-Eintrag zeigt an, dass die Nachricht nicht vom Inhaltsfilter-Agent verarbeitet wurde.
    
      - **Empfangsdatum** Dieses Feld zeigt das Datum und die Uhrzeit des Empfangs der Nachricht durch den Server an, auf dem die Warteschlange ausgeführt wird, in der sich die Nachricht befindet.
    
      - **Ablaufzeit** Dieses Feld zeigt den Zeitpunkt (Datum und Uhrzeit) an, zu dem die Nachricht abläuft und aus der Warteschlange gelöscht wird, wenn sie nicht zugestellt werden kann.
    
      - **Letzter Fehler** Dieses Feld zeigt den letzten für eine Nachricht aufgezeichneten Fehler.
    
      - **Warteschlangen-ID** Dieses Feld zeigt die Identität der Warteschlange an, in der sich die Nachricht befindet. Die Warteschlangenidentität wird in der Form *Server\\Ziel* ausgedrückt, wobei *Ziel* für eine Zustellungsgruppe, ein Routingziel, den Namen einer beständigen Warteschlange oder die ID der Warteschlangendatenbank steht. Die Warteschlangendatenbank-ID wird als ganze Zahl dargestellt und kann durch Anzeigen der Nachrichteneigenschaften bestimmt werden.
    
      - **Empfänger**   Dieses Feld zeigt die Liste der Empfänger an, an die die Nachricht gesendet werden soll.
    
      - **Anzahl von Wiederholungen** Dieses Feld zeigt die Anzahl der Zustellungsversuche für eine Nachricht an ein Ziel an.

6.  
    
    Auf der Registerkarte **Empfängerinformationen** werden die folgenden Angaben zu den Empfängern dieser Nachricht angezeigt:
    
      - **Adresse**   Dieses Feld zeigt die SMTP-Adresse des Nachrichtenempfängers an. Dieser Wert wird dem Feld `RCPT TO:` im Nachrichtenumschlag entnommen.
    
      - **Status** In diesem Feld wird der aktuelle Status der Nachricht angezeigt. Eine Nachricht kann einen der folgenden Statuswerte aufweisen:
        
          - **Aktiv   **Wenn die Nachricht sich in einer Zustellungswarteschlange befindet, wird die Nachricht an ihr Ziel zugestellt. Wenn die Nachricht sich in der Übermittlungswarteschlange befindet, wird sie vom Kategorisierungsmodul verarbeitet.
        
          - **Entfernen ausstehend**   Die Nachricht wurde vom Administrator gelöscht, befand sich aber bereits in der Zustellung. Die Nachricht wird gelöscht, wenn die Zustellung mit einem Fehler endet, der ein erneutes Eintreten der Nachricht in die Wartschlange bewirkt. Andernfalls wird die Zustellung fortgesetzt.
        
          - **Anhaltevorgang ausstehend**   Die Nachricht wurde vom Administrator angehalten, befand sich aber bereits in der Zustellung. Die Nachricht wird angehalten, wenn die Zustellung mit einem Fehler endet, der ein erneutes Eintreten der Nachricht in die Wartschlange bewirkt. Andernfalls wird die Zustellung fortgesetzt.
        
          - **Bereit**   Die Nachricht befindet sich in der Warteschlange und ist zur Verarbeitung bereit.
        
          - **Wiederholen**   Fehler beim letzten Verbindungsversuch für die Warteschlange, in der sich diese Nachricht befindet. Die Nachricht wartet auf den nächsten Wiederholungsversuch der Warteschlange.
        
          - **Angehalten**   Die Nachricht wurde vom Administrator angehalten.
    
      - **Letzter Fehler** Dieses Feld zeigt den letzten für eine Nachricht aufgezeichneten Fehler.

## Anzeigen der Eigenschaften einer Nachricht mithilfe der Shell

Mit dem Cmdlet **Get-Message** können Sie die Eigenschaften einer Nachricht anzeigen, die sich zurzeit in der Warteschlange für die Zustellung befindet. Im folgenden Beispiel wird für alle Nachrichten mit dem Status "Wiederholen" eine Tabelle mit der Absenderadresse, den Empfängern, dem Betreff und dem Empfangsdatum erstellt:

    Get-Message -IncludeRecipientInfo -Filter {Status -eq "Retry"} | Format-Table FromAddress,Recipients,Subject,DateReceived

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Get-Message](https://technet.microsoft.com/de-de/library/bb124738\(v=exchg.150\)).

