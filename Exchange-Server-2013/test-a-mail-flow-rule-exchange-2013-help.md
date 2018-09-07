---
title: 'Testen einer Nachrichtenflussregel: Exchange 2013 Help'
TOCTitle: Testen einer Nachrichtenflussregel
ms:assetid: 3d949e2a-8ba4-4261-8cfb-736fd2446ea1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn831862(v=EXCHG.150)
ms:contentKeyID: 63145419
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Testen einer Nachrichtenflussregel

 

_**Gilt für:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Immer wenn Sie eine Exchange-E-Mail-Flussregel erstellen, die auch als Transportregel bezeichnet wird, sollten Sie sie zunächst testen, bevor Sie sie aktivieren. Wenn Sie versehentlich eine Bedingung erstellen, die nicht exakt das Gewünschte macht oder mit anderen Regeln auf unerwartete Weise interagiert, vermeiden Sie dadurch unvorhersehbare Folgen.


> [!IMPORTANT]
> Warten Sie nach dem Erstellen einer Regel 30 Minuten, ehe Sie sie testen. Wenn Sie die Regel sofort nach dem Erstellen testen, ist das Verhalten möglicherweise inkonsistent. Bei Verwendung von Exchange Server und mehrerer Exchange-Server kann es sogar länger dauern, bis alle Server die Regel empfangen haben.



## Schritt 1: Erstellen einer Regel im Testmodus

Sie können die Bedingungen für eine Regel auswerten, ohne Aktionen auszuführen, die die Nachrichtenübermittlung beeinträchtigen, indem Sie einen Testmodus auswählen. Sie können eine Regel so einrichten, dass Sie jedes Mal eine E-Mail-Benachrichtigung erhalten, wenn es eine Regelübereinstimmung gibt. Oder Sie können die Untersuchen der Nachrichtenablaufverfolgung auf Nachrichten untersuchen, die ggf. mit der Regel übereinstimmen. Es gibt zwei Testmodi:

  - **Test ohne Richtlinientipps**   Verwenden Sie diesen Modus zusammen mit einer Schadensberichtsaktion, damit Sie eine E-Mail-Nachricht erhalten, sobald eine E-Mail mit der Regel übereinstimmt.

  - **Test mit Richtlinientipps**   Dieser Modus ist nur verfügbar, wenn Sie [Verhinderung von Datenverlust](https://review.docs.microsoft.com/de-de/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) (DLP) einsetzen. Dieses Feature ist in verschiedenen Exchange Online- und Exchange Online Protection-Abonnementplänen (EOP) verfügbar. Bei diesem Modus wird dem Absender eine Meldung angezeigt, wenn eine Nachricht, die er senden möchte, mit einer Richtlinie übereinstimmt, ohne dass E-Mail-Flussaktionen erfolgen.

Nachstehend sehen Sie die Meldung bei einer Regelübereinstimmung, wenn Sie die Schadensberichtsaktion hinzufügen:

![Nachricht, die gesendet wird, wenn Regel erkannt wird](images/Dn831862.c1a2db60-3fb9-4ddc-86d5-1757e2250f59(EXCHG.150).png "Nachricht, die gesendet wird, wenn Regel erkannt wird")

**Verwenden eines Testmodus mit einer Schadensberichtsaktion**

1.  Navigieren Sie im Exchange-Verwaltungskonsole (EAC) zu **Nachrichtenfluss** \> **Regeln**.

2.  Erstellen Sie eine neue Regel, oder wählen Sie eine vorhandene Regel und dann **Bearbeiten** aus.

3.  Führen Sie einen Bildlauf nach unten zum Abschnitt **Modus für diese Regel auswählen** durch, und wählen Sie dann **Test ohne Richtlinientipps** oder **Test mit Richtlinientipps** aus.

4.  Fügen Sie eine Schadensberichtsaktion hinzu:
    
    1.  Wählen Sie **Aktion hinzufügen**, oder, falls nicht angezeigt, **Weitere Optionen**, und dann **Aktion hinzufügen** aus.
    
    2.  Wählen Sie **Schadensbericht erstellen und senden an** aus.
    
    3.  Klicken Sie auf **Eine(n) auswählen**... , und wählen Sie sich selbst oder eine andere Person.
    
    4.  Wählen Sie **Nachrichteneigenschaften einbeziehen** und dann alle Eigenschaften aus, die die E-Mail enthalten soll, die Sie empfangen. Wenn Sie keine auswählen, erhalten Sie dennoch eine E-Mail, falls die Regel erfüllt ist.

5.  Klicken Sie auf **Speichern**.

## Schritt 2: Prüfen, ob die Regel wie gewünscht funktioniert

Zum Testen einer Regel können Sie entweder genügend Testnachrichten senden, um zu bestätigen, dass das Erwartete passiert, oder die Nachrichtenablaufverfolgung auf Nachrichten überprüfen, die Personen in Ihrer Organisation senden. Überprüfen Sie auf jeden Fall die folgenden Arten von Nachrichten:

  - Nachrichten, von denen Sie erwarten, dass sie der Regel entsprechen

  - Nachrichten, von denen Sie nicht erwarten, dass sie der Regel entsprechen

  - Nachrichten, die von und an Personen in Ihrer Organisation gesendet wurden

  - Nachrichten, die von und an Personen außerhalb Ihrer Organisation gesendet wurden

  - Antworten auf Nachrichten, die der Regel entsprechen

  - Nachrichten, die zu Interaktionen zwischen mehreren Regeln führen können

## Tipps für das Senden von Testnachrichten

Eine Möglichkeit zum Testen ist, sich als Absender und Empfänger einer Testnachricht anzumelden.

  - Wenn Sie über keinen Zugriff auf mehrere Konten in Ihrer Organisation verfügen, können Sie den Test mit einem [Office 365-Testkonto](https://go.microsoft.com/fwlink/p/?linkid=402791) durchführen oder temporär einige gefälschte Benutzer in Ihrer Organisation erstellen.

  - Da es ein Webbrowser in der Regel nicht zulässt, dass Sie auf dem gleichen Computer bei mehreren Konten gleichzeitig angemeldet sind, können Sie für jeden Benutzer das [Internet Explorer InPrivate-Browsen](https://go.microsoft.com/fwlink/p/?linkid=402784) oder einen anderen Computer, Webbrowser oder ein anderes Gerät verwenden.

## Untersuchen der Nachrichtenablaufverfolgung

Die Nachrichtenablaufverfolgung enthält einen Eintrag für jede Regel, die für die Nachricht gefunden wird, und einen Eintrag für jede von der Regel ausgeführte Aktion. Dies ist nützlich zum Nachverfolgen, was mit Testnachrichten geschieht, und auch zum Nachverfolgen, was mit tatsächlichen Nachrichten passiert, die Ihre Organisation durchlaufen.

![Nachrichtenablaufverfolgung, die Transportregelaktionen zeigt](images/Dn831862.64179f28-5c8c-421b-b630-cc1f7de9a34f(EXCHG.150).png "Nachrichtenablaufverfolgung, die Transportregelaktionen zeigt")

1.  Wechseln Sie im EAC zu **Nachrichtenfluss** \> **Nachrichtenablaufverfolgung**.

2.  Suchen Sie die Nachrichten, die Sie nachverfolgen möchten, mithilfe von Kriterien wie z. B. Absender und Sendedatum. Hilfe beim Angeben von Kriterien finden Sie unter [Ausführen einer Nachrichtenablaufverfolgung und Anzeigen der Ergebnisse](https://technet.microsoft.com/de-de/library/jj200712\(v=exchg.150\)).

3.  Nach dem Auffinden der Nachricht, die Sie nachverfolgen möchten, doppelklicken Sie darauf, um Details zur Nachricht anzeigen.

4.  Suchen Sie in der Spalte **Ereignis** nach **Transportregel**. In der Spalte **Aktion** wird die spezifisch erfolgte Aktion angezeigt.

## Schritt 3: Festlegen der zu erzwingenden Regel im Anschluss an den Test

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Regeln**.

2.  Wählen Sie eine Regel aus, und klicken Sie dann auf **Bearbeiten**.

3.  Klicken Sie auf **Erzwingen**.

4.  Wenn Sie eine Aktion zum Generieren eines Schadensberichts verwendet haben, wählen Sie die Aktion aus, und klicken Sie dann auf **Entfernen**.

5.  Klicken Sie auf **Speichern**.


> [!TIP]
> Um Überraschungen zu vermeiden, informieren Sie die Benutzer über neue Regeln.



## Vorschläge zur Problembehandlung

Hier nun einige gängige Probleme und Lösungen:

  - **Alles sieht wie gewünscht aus, doch die Regel funktioniert nicht.**
    
    Gelegentlich dauert es länger als 15 Minuten, bis ein neuer E-Mail-Fluss zur Verfügung steht. Warten Sie ein paar Stunden, und wiederholen Sie den Test. Überprüfen Sie auch, ob ggf. eine andere Regel störend wirkt. Versuchen Sie, die Priorität dieser Regel in 0 zu ändern, indem Sie sie an den Anfang der Liste verschieben.

  - **Der Haftungsausschluss wird an die ursprüngliche Nachricht und alle Antworten und nicht nur an die ursprüngliche Nachricht angefügt.**
    
    Um dies zu vermeiden, können Sie eine Ausnahme für die Haftungsausschlussregel hinzufügen, dass nach einem eindeutigen Ausdruck im Haftungsausschluss gesucht werden soll.

  - **Meine Regel enthält zwei Bedingungen, und ich möchte, dass die Aktion erfolgt, wenn eine der Bedingungen erfüllt ist. Sie erfolgt aber nur, wenn beide Bedingungen zutreffen.**
    
    Sie müssen zwei Regeln erstellen, eine für jede Bedingung. Sie können die Regel problemlos kopieren, indem Sie **Kopieren** auswählen und eine Bedingung aus dem Original und die andere Bedingung aus der Kopie entfernen.

  - **Ich arbeite mit Verteilergruppen, doch der** **Absender** (**SentTo**) **scheint nicht zu funktionieren.**
    
    **SentTo** entspricht Nachrichten, bei denen einer der Empfänger ein Postfach, E-Mail-aktivierter Benutzer oder Kontakt ist. Sie können jedoch keine Verteilergruppe mit dieser Bedingung angeben. Verwenden Sie stattdessen **Feld „An“ enthält ein Mitglied dieser Gruppe** (**SentToMemberOf**).

## Weitere Testoptionen

Wenn Sie Exchange Online oder Exchange Online Protection verwenden, können Sie mithilfe eines Regelberichts prüfen, wie oft jede Regel erfüllt wird. Damit eine Regel in den Berichten eingeschlossen wird, muss bei der Regel das Kontrollkästchen **Diese Regel mit Schweregrad überwachen** aktiviert sein. Dank dieser Berichte können Sie Trends bei der Verwendung von Regeln ausmachen und Regeln bestimmen, die nicht erfüllt werden.

Wählen Sie zum Anzeigen eines Regelberichts im Office 365 Admin Center die Option **Berichte** aus.


> [!NOTE]
> Die meisten Daten werden innerhalb von 24&nbsp;Stunden im Bericht erfasst. Bei einigen Daten kann es bis zu 5&nbsp;Tage dauern, bis sie angezeigt werden.



![Bericht, der Regelnutzung zeigt](images/Dn831862.df5bf202-741d-432a-b71d-b37143f0ec0a(EXCHG.150).png "Bericht, der Regelnutzung zeigt")

Weitere Informationen finden Sie unter [Anzeigen von Berichten zum E-Mail-Schutz](https://go.microsoft.com/fwlink/p/?linkid=402958).

## Benötigen Sie weitere Hilfe?

[Verwalten von Nachrichtenflussregeln](manage-mail-flow-rules-exchange-2013-help.md)

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\)) (Exchange Online)

[Nachrichtenflussregeln (Transportregeln) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/dn271424\(v=exchg.150\)) (Exchange Online Protection)

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md) (Exchange Server)

