---
title: 'Verwalten von Nachrichtenflussregeln: Exchange 2013 Help'
TOCTitle: Verwalten von Nachrichtenflussregeln
ms:assetid: e7a81372-b6d7-4d1f-bc9e-a845a7facac2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657505(v=EXCHG.150)
ms:contentKeyID: 50476964
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Nachrichtenflussregeln

 

_**Gilt für:** Exchange Online, Exchange Online Protection, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Mithilfe von E-Mail-Flussregeln, die auch als Transportregeln bezeichnet werden, können Sie Nachrichten, die Ihre Organisation durchlaufen, auf bestimmte Bedingungen prüfen und entsprechende Aktionen ausführen. In diesem Thema wird gezeigt, wie Sie Regeln erstellen, kopieren, aktivieren bzw. deaktivieren, löschen oder importieren bzw. exportieren, deren Reihenfolge ändern, und wie Sie die Regelnutzung überwachen.


> [!TIP]
> Damit Ihre Regeln Ihren Erwartungen entsprechend funktionieren, sollten Sie alle Regeln sowie alle Interaktionen zwischen Regeln sorgfältig testen.



Sie interessieren sich für Szenarien, in denen dieses Verfahren verwendet wird? Siehe die folgenden Themen:

  - [Organisationsweite Haftungsausschlüsse, Signaturen, Fußzeilen oder Kopfzeilen](organization-wide-disclaimers-signatures-footers-or-headers-exchange-online-help.md)

  - [Überprüfen von Nachrichtenanlagen mithilfe von Transportregeln](use-transport-rules-to-inspect-message-attachments-exchange-2013-help.md)

  - [Standardszenarien für Anlagensperre](https://technet.microsoft.com/de-de/library/Dn950026(v=EXCHG.150))

  - [Verwenden von Nachrichtenflussregeln zum Routen von E-Mails basierend auf einer Liste von Wörtern, Begriffen oder Mustern](https://technet.microsoft.com/de-de/library/Dn951131(v=EXCHG.150))

  - [Gängige Szenarien der Nachrichtengenehmigung](common-message-approval-scenarios-exchange-2013-help.md)

  - [Verwenden von Nachrichtenflussregeln zum Umgehen von unwichtigen Elementen durch Nachrichten](https://technet.microsoft.com/de-de/library/Dn896639(v=EXCHG.150))

  - [Bewährte Methoden für die Konfiguration von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/Dn960147(v=EXCHG.150))

  - [Überprüfen von Nachrichtenanlagen mithilfe von Nachrichtenflussregeln](https://technet.microsoft.com/de-de/library/jj919236\(v=exchg.150\))

  - [Verwenden von Transportregeln zum Konfigurieren von Massen-e-Mail-Filterung](https://technet.microsoft.com/de-de/library/dn720438\(v=exchg.150\))

  - [Definieren von Regeln zum Verschlüsseln oder Entschlüsseln von Nachrichten](https://go.microsoft.com/fwlink/p/?linkid=402846)

  - [Erstellen von organisationsweiten sicherer Absender oder gesperrter Absenderlisten in Office 365](https://technet.microsoft.com/de-de/library/dn198251\(v=exchg.150\))

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unterEintrag "Transportregeln" in [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md) (Exchange Server) oder in [Featureberechtigungen in Exchange Online](https://technet.microsoft.com/de-de/library/jj200673\(v=exchg.150\)).

  - Wenn eine Regel als **Version 14** aufgeführt ist, bedeutet dies, dass die Regel auf einem Exchange Server 2010-E-Mail-Flussregelformat basiert. Für diese Regeln sind alle Optionen verfügbar.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer E-Mail-Flussregel

Sie können eine E-Mail-Flussregel erstellen, indem Sie eine DLP-Richtlinie (Data Loss Prevention, Verhinderung von Datenverlust) einrichten, eine neue Regel erstellen oder eine Regel kopieren. Sie können dasExchange-Verwaltungskonsole (EAC) oder die Exchange-Verwaltungsshell verwenden.


> [!NOTE]
> Nach dem Erstellen oder Ändern einer E-Mail-Flussregel kann es bis zu 30&nbsp;Minuten dauern, bis die neue oder aktualisierte Regel auf E-Mails angewendet wird.



## Verwenden einer DLP-Richtlinie zum Erstellen von E-Mail-Flussregeln

Jede DLP-Richtlinie ist eine Sammlung von E-Mail-Flussregeln. Nachdem Sie die DLP-Richtlinie erstellt haben, können Sie die Regeln anhand der unten genannten Verfahren verfeinern.

1.  Erstellen Sie eine DLP-Richtlinie. Weitere Anweisungen finden Sie in:
    
      - [DLP-Verfahren für Exchange Server 2013](dlp-procedures-exchange-2013-help.md)
    
      - [DLP-Verfahren für Exchange Online](dlp-procedures-exchange-2013-help.md)

2.  Ändern Sie die mit der DLP-Richtlinie erstellten E-Mail-Flussregeln. Weitere Informationen finden Sie unter Anzeigen oder Ändern einer E-Mail-Flussregel.

## Verwenden des EAC zum Erstellen einer E-Mail-Flussregel

Im EAC können Sie E-Mail-Flussregeln erstellen, indem Sie eine Vorlage verwenden, eine vorhandene Regel kopieren oder eine Regel von Grund auf neu erstellen.

1.  Wechseln Sie zu **Nachrichtenfluss** \> **Regeln**.

2.  Erstellen Sie die Regel mithilfe einer der folgenden Optionen:
    
      - Um eine Regel von einer Vorlage zu erstellen, klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), und wählen Sie eine Vorlage aus.
    
      - Um eine Regel zu kopieren, wählen Sie die Regel aus, und wählen Sie dann **Kopieren**![Kopieren (Symbol)](images/JJ657480.ed7f7abf-39d8-4f43-a918-ccb3bff87ef5(EXCHG.150).gif "Kopieren (Symbol)") aus.
    
      - Um eine Regel von Grund auf neu zu erstellen, wählen Sie **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") und dann **Neue Regel erstellen** aus.

3.  Geben Sie im Dialogfeld **Neue Regel** einen Namen für die Regel ein, und wählen Sie dann die Bedingungen und Aktionen für diese Regel aus:
    
    1.  Wählen Sie in **Diese Regel anwenden, wenn…** aus der Liste verfügbarer Bedingungen die gewünschte Bedingung aus.
        
          - Für einige Bedingungen müssen Werte angegeben werden. Wenn Sie z. B. die Bedingung **Der Absender ist…** auswählen, müssen Sie eine Absenderadresse angeben. Beim Hinzufügen eines Worts oder Ausdrucks müssen Sie beachten, dass nachfolgende Leerzeichen nicht zulässig sind.
        
          - Wenn die gewünschte Bedingung nicht aufgeführt wird, oder wenn Sie Ausnahmen hinzufügen müssen, wählen Sie **Weitere Optionen** aus. Zusätzliche Bedingungen und Ausnahmen werden aufgelistet.
        
          - Wenn Sie keine Bedingung angeben möchten und diese Regel auf alle Nachrichten in Ihrer Organisation angewendet werden soll, wählen Sie die Bedingung **\[Auf alle Nachrichten anwenden\]** aus.
    
    2.  Wählen Sie in **Gehen Sie folgendermaßen vor...** die Aktion aus, die von der Regel auf Nachrichten angewendet werden soll, die den Kriterien aus der Liste der verfügbaren Aktionen entsprechen.
        
          - Für einige der Aktionen müssen Sie Werte angeben. Wenn Sie z. B. die Bedingung **Nachricht zur Genehmigung weiterleiten an…** auswählen, müssen Sie einen Empfänger in Ihrer Organisation auswählen.
        
          - Wenn die gewünschte Bedingung nicht aufgeführt ist, wählen Sie **Weitere Optionen** aus. Zusätzliche Bedingungen werden aufgelistet.
    
    3.  Geben Sie an, wie Regelübereinstimmungsdaten für diese Regel in den [DLP-Berichten](https://go.microsoft.com/fwlink/p/?linkid=402768) und den [Transportregelberichten](https://go.microsoft.com/fwlink/p/?linkid=402769) angezeigt werden.
        
          - Wählen Sie unter **Diese Regel mit Schweregrad überwachen** einen Grad aus, um den Schweregrad für diese Regel anzugeben. Die Office 365-Aktivitätsberichte für E-Mail-Flussregelgruppen werden nach Schweregrad abgeglichen. Der Schweregrad ist nur ein Filter zum Vereinfachen der Verwendung von Berichten. Der Schweregrad hat keine Auswirkung auf die Priorität, mit der die Regel verarbeitet wird.
            

            > [!NOTE]
            > Wenn Sie das Kontrollkästchen <STRONG>Diese Regel mit Schweregrad überwachen</STRONG> deaktivieren, werden Regelübereinstimmungen in den Regelberichten nicht angezeigt.

    
    4.  Legen Sie den Modus für die Regel fest. Sie können einen von zwei Testmodi verwenden, um die Regel zu testen, ohne den E-Mail-Fluss zu beeinträchtigen. In beiden Testmodi wird der Nachrichtenablaufverfolgung ein Eintrag hinzugefügt, wenn die Bedingungen erfüllt werden.
        
          - **Erzwingen**   Diese Option aktiviert die Regel, die unmittelbar mit der Verarbeitung von Nachrichten beginnt. Alle Aktionen für die Regel werden ausgeführt.
        
          - **Test mit Richtlinientipps**   Damit wird die Regel aktiviert, und alle Richtlinientippaktionen (**Absender mit Richtlinientipp benachrichtigen**) werden gesendet. Es erfolgen keine Aktionen im Zusammenhang mit der Nachrichtenübermittlung. Zur Verwendung dieses Modus ist DLP (Data Loss Prevention, Verhinderung von Datenverlust) erforderlich. Weitere Informationen finden Sie unter [Richtlinientipps](https://technet.microsoft.com/de-de/library/JJ150512(v=EXCHG.150)).
        
          - **Test mit Richtlinientipps**   Nur die Aktion "Schadensbericht generieren" wird durchgeführt. Es erfolgen keine Aktionen im Zusammenhang mit der Nachrichtenübermittlung.

4.  Wenn Sie mit der Regel zufrieden sind, wechseln Sie zu Schritt 5. Klicken Sie auf **Weitere Optionen**, um weitere Bedingungen oder Aktionen hinzuzufügen, Ausnahmen anzugeben oder zusätzliche Eigenschaften festzulegen. Nachdem Sie auf **Weitere Optionen** geklickt haben, füllen Sie die folgenden Felder aus, um Ihre Regel zu erstellen:
    
    1.  Klicken Sie auf **Bedingung hinzufügen**, um weitere Bedingungen hinzuzufügen. Wenn Sie über mehrere Bedingungen verfügen, können Sie eine beliebige Bedingung entfernen, indem Sie daneben auf **X entfernen** klicken. Beachten Sie, dass eine größere Auswahl an Bedingungen zur Verfügung steht, nachdem Sie auf **Weitere Optionen** geklickt haben.
    
    2.  Klicken Sie auf **Aktion hinzufügen**, um weitere Aktionen hinzuzufügen. Wenn Sie über mehrere Aktionen verfügen, können Sie eine beliebige Aktion entfernen, indem Sie daneben auf **X entfernen** klicken. Beachten Sie, dass eine größere Auswahl an Aktionen zur Verfügung steht, nachdem Sie auf **Weitere Optionen** geklickt haben.
    
    3.  Klicken Sie zum Angeben von Ausnahmen auf **Ausnahme hinzufügen**, und wählen Sie anschließend die Ausnahmen in der Dropdownliste **Außer wenn...** aus. Sie können beliebige Ausnahmen aus der Regel entfernen, indem Sie neben der jeweiligen Ausnahme auf **X entfernen** klicken.
    
    4.  Wenn diese Regel nach einem bestimmten Datum wirksam werden soll, klicken Sie auf **Diese Regel an folgendem Datum aktivieren:**  Geben Sie anschließend ein Datum an. Beachten Sie, dass die Regel vor diesem Datum weiterhin aktiviert ist, aber nicht verarbeitet wird.
        
        Ebenso können Sie festlegen, dass die Regel an einem bestimmten Datum nicht verarbeitet wird. Klicken Sie hierzu auf **Diese Regel an folgendem Datum deaktivieren:**  Geben Sie anschließend ein Datum an. Beachten Sie, dass die Regel aktiviert bleibt, aber nicht verarbeitet wird.
    
    5.  Sie können auswählen, dass keine weiteren Regeln angewendet werden, nachdem diese Regel auf eine Nachricht angewendet wurde. Klicken Sie hierzu auf **Keine weiteren Regeln anwenden**. Wenn Sie diese Option aktivieren und eine Nachricht von dieser Regel verarbeitet wird, werden auf diese Nachricht keine nachfolgenden Regeln angewendet.
    
    6.  Sie können angeben, wie die Nachricht behandelt werden soll, wenn die Regelverarbeitung nicht abgeschlossen werden kann. Standardmäßig wird die Regel ignoriert, und die Nachricht wird normal verarbeitet. Sie können jedoch die Nachricht zur Verarbeitung erneut senden. Aktivieren Sie hierfür das Kontrollkästchen **Nachricht zurückstellen, wenn die Regelverarbeitung nicht abgeschlossen wird**.
    
    7.  Wenn Ihre Regel die Absenderadresse analysiert, wird standardmäßig nur der Nachrichtkopf untersucht. Sie können die Regel jedoch so konfigurieren, dass auch der SMTP-Nachrichtenumschlag untersucht wird. Um anzugeben, was untersucht wird, klicken Sie für **Absenderadresse in Nachricht untersuchen** auf einen der folgenden Werte:
        
          - **Kopf**   Nur der Nachrichtenkopf wird untersucht.
        
          - **Umschlag**   Nur der SMTP-Nachrichtenumschlag wird untersucht.
        
          - **Kopf und Umschlag**   Sowohl der Nachrichtenkopf als auch der SMTP-Nachrichtenumschlag werden untersucht.
    
    8.  Im Feld **Kommentare** können Sie Kommentare zu dieser Regel hinzufügen.

5.  Klicken Sie auf **Speichern**, um die Erstellung der Regel abzuschließen.

## Verwenden des Exchange-Verwaltungsshell zum Erstellen einer E-Mail-Flussregel

In diesem Beispiel wird mithilfe des Cmdlets [New-TransportRule](https://technet.microsoft.com/de-de/library/bb125138\(v=exchg.150\)) eine neue E-Mail-Flussregel erstellt, um Nachrichten, die von außerhalb der Organisation an die Verteilergruppe "Sales Department" gesendet werden, die Zeichenfolge "`External message to Sales DG:`" voranzustellen.

    New-TransportRule -Name "Mark messages from the Internet to Sales DG" -FromScope NotInOrganization -SentTo "Sales Department" -PrependSubject "External message to Sales DG:"

Die Regelparameter und -aktionen, die in den oben stehenden Schritten verwendet werden, dienen nur zu Demonstrationszwecken. Prüfen Sie alle verfügbaren E-Mail-Flussregelbedingungen und -aktionen, um die für Ihre Anforderungen geeigneten Prädikate und Aktionen zu ermitteln.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie erfolgreich eine neue E-Mail-Flussregel erstellt haben:

  - Überprüfen Sie im EAC, ob die von Ihnen neu erstellte E-Mail-Flussregel in der Liste **Regeln** aufgeführt ist.

  - Überprüfen Sie über die Exchange-Verwaltungsshell, dass Sie die neue E-Mail-Flussregel erfolgreich erstellt haben, indem Sie den folgenden Befehl (das Beispiel unten überprüft die im oben genannten Exchange-Verwaltungsshell-Beispiel erstellte Regel) ausführen:
    
        Get-TransportRule "Mark messages from the Internet to Sales DG"

## Anzeigen oder Ändern einer E-Mail-Flussregel


> [!NOTE]
> Nach dem Erstellen oder Ändern einer E-Mail-Flussregel kann es bis zu 30&nbsp;Minuten dauern, bis die neue oder aktualisierte Regel auf E-Mails angewendet wird.



## Anzeigen oder Ändern einer E-Mail-Flussregel mithilfe des EAC

1.  Navigieren Sie im EAC zu **Nachrichtenfluss** \> **Regeln**.

2.  Wenn Sie eine Regel in der Liste auswählen, werden die Bedingungen, Aktionen, Ausnahmen und ausgewählten Eigenschaften dieser Regel im Detailbereich angezeigt. Doppelklicken Sie auf eine bestimmte Regel, um ihre gesamten Eigenschaften anzuzeigen. Dadurch wird das Regel-Editor-Fenster geöffnet, in dem Sie Änderungen an der Regel vornehmen können. Weitere Informationen zu Regeleigenschaften finden Sie im Abschnitt Verwenden des EAC zum Erstellen einer E-Mail-Flussregel weiter oben in diesem Thema.

## Anzeigen oder Ändern einer E-Mail-Flussregel mithilfe des Exchange-Verwaltungsshell

Das folgende Beispiel bietet Ihnen eine Liste aller in Ihrer Organisation konfigurierten Regeln:

    Get-TransportRule

Wenn Sie die Eigenschaften einer bestimmten E-Mail-Flussregel anzeigen möchten, geben Sie den Namen der Regel oder ihre GUID ein. Es ist in der Regel hilfreich, die Ausgabe an das Cmdlet **Format-List** zu senden, um die Eigenschaften zu formatieren. Das folgende Beispiel gibt alle Eigenschaften der E-Mail-Flussregel namens **Sender is a member of Marketing** zurück:

    Get-TransportRule "Sender is a member of marketing" | Format-List

Um die Eigenschaften einer bestehenden Regel zu ändern, verwenden Sie das Cmdlet [Set-TransportRule](https://technet.microsoft.com/de-de/library/bb123534\(v=exchg.150\)). Mit diesem Cmdlet können Sie beliebige Eigenschaften, Bedingungen, Aktionen oder Ausnahmen ändern, die einer Regel zugeordnet sind. Im folgenden Beispiel wird der Regel "Sender is a member of marketing" eine Ausnahme hinzugefügt, damit sie nicht auf Nachrichten angewendet wird, die vom Benutzer "Kelly Rollin" gesendet werden:

    Set-TransportRule "Sender is a member of marketing" -ExceptIfFrom "Kelly Rollin"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um die erfolgreiche Änderung einer E-Mail-Flussregel zu überprüfen, gehen Sie wie folgt vor:

  - Klicken Sie im EAC in der Liste **Regeln** auf die von Ihnen geänderte Regel, und zeigen Sie den Detailbereich an.

  - Überprüfen Sie mithilfe der Exchange-Verwaltungsshell durch Ausführen des folgenden Befehls, der die von Ihnen geänderten Eigenschaften zusammen mit dem Namen der Regel auflistet, ob Sie die E-Mail-Flussregel erfolgreich geändert haben (im Beispiel unten wird die im obigen Exchange-Verwaltungsshell-Beispiel geänderte Regel überprüft):
    
        Get-TransportRule "Sender is a member of marketing" | Format-List Name,ExceptIfFrom

## Eigenschaften von Nachrichtenflussregeln

Sie können auch das Set-TransportRule-Cmdlet verwenden, um vorhandene Transportregeln in Ihrer Organisation zu ändern. Es folgt eine Liste mit Eigenschaften, die Sie ändern können, die aber nicht im EAC verfügbar sind. Weitere Informationen zur Verwendung des Set-TransportRule-Cmdlets zum Vornehmen dieser Änderungen finden Sie unter [Set-TransportRule](https://technet.microsoft.com/de-de/library/bb123534\(v=exchg.150\))


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Name der Bedingung im EAC</th>
<th>Name der Bedingung im Exchange-Verwaltungsshell</th>
<th>Eigenschaften</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Verarbeiten von Regeln beenden</strong></p></td>
<td><p><code>StopRuleProcessing </code></p></td>
<td><p><code> Not applicable</code></p></td>
<td><p>Ermöglicht es Ihnen, die Verarbeitung zusätzlicher Regeln zu beenden</p></td>
</tr>
<tr class="even">
<td><p><strong>Kopf/Umschlag stimmen überein</strong></p></td>
<td><p><code>SenderAddressLocation </code></p></td>
<td><p>Nicht zutreffend</p></td>
<td><p>Ermöglicht es Ihnen, den SMTP-Nachrichtenumschlag zu untersuchen, um sicherzustellen, dass der Kopf und der Umschlag übereinstimmen</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Schweregrad überwachen</strong></p></td>
<td><p><code>SetAuditSeverity </code></p></td>
<td><p><code>Not applicable</code></p></td>
<td><p>Ermöglicht es Ihnen, einen Schweregrad für die Überwachung auszuwählen</p></td>
</tr>
<tr class="even">
<td><p><strong>Regelmodi</strong></p></td>
<td><p><code>Mode</code></p></td>
<td><p><code>Not applicable</code></p></td>
<td><p>Ermöglicht es Ihnen, den Modus für die Regel festzulegen</p></td>
</tr>
</tbody>
</table>


## Festlegen der Priorität einer E-Mail-Flussregel

Die Regel oben in der Liste wird zuerst verarbeitet. Diese Regel weist die **Priorität** 0 auf.

## Festlegen der Priorität einer Regel im EAC

1.  Navigieren Sie im EAC zu **Nachrichtenfluss** \> **Regeln**. Die Regeln werden in der Reihenfolge angezeigt, in der sie verarbeitet werden.

2.  Wählen Sie eine Regel aus, und verschieben Sie die Regeln mithilfe der Pfeile in der Liste nach oben oder unten.

## Festlegen der Priorität einer Regel im Exchange-Verwaltungsshell

Im folgenden Beispiel wird die Priorität von "Sender is a member of marketing" auf 2 festgelegt:

    Set-TransportRule "Sender is a member of marketing" priority "2"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um die erfolgreiche Änderung einer E-Mail-Flussregel zu überprüfen, gehen Sie wie folgt vor:

  - Prüfen Sie im EAC in der Regelliste die Reihenfolge der Regeln.

  - Überprüfen Sie in der Exchange-Verwaltungsshell die Priorität der Regeln (mit dem folgenden Beispiel wird die im Exchange-Verwaltungsshell-Beispiel oben geänderte Regel überprüft):
    
        Get-TransportRule * | Format-List Name,Priority

## Aktivieren oder Deaktivieren einer E-Mail-Flussregel

Regeln werden bei ihrer Erstellung aktiviert. Sie können eine E-Mail-Flussregel deaktivieren.

## Aktivieren oder Deaktivieren einer E-Mail-Flussregel mithilfe des EAC

1.  Navigieren Sie im EAC zu **Nachrichtenfluss** \> **Regeln**.

2.  Deaktivieren Sie das Kontrollkästchen neben dem Namen einer Regel, um diese Regel zu deaktivieren.

3.  Aktivieren Sie das Kontrollkästchen neben dem Namen einer Regel, um die deaktivierte Regel zu aktivieren.

## Aktivieren oder Deaktivieren einer E-Mail-Flussregel mithilfe des Exchange-Verwaltungsshell

Im folgenden Beispiel wird die E-Mail-Flussregel "Sender is a member of marketing" deaktiviert:

    Disable-TransportRule "Sender is a member of marketing"

Im folgenden Beispiel wird die E-Mail-Flussregel "Sender is a member of marketing" aktiviert:

    Enable-TransportRule "Sender is a member of marketing"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie erfolgreich eine E-Mail-Flussregel aktiviert oder deaktiviert haben:

  - Zeigen Sie im EAC die Liste **Regeln** an, und überprüfen Sie den Status des Kontrollkästchens in der Spalte **EIN**.

  - Führen Sie in der Exchange-Verwaltungsshell folgenden Befehl aus, um eine Liste aller Regeln in Ihrer Organisation einschließlich Status zurückzugeben:
    
        Get-TransportRule | Format-Table Name,State

## Entfernen einer E-Mail-Flussregel

## Verwenden des EAC zum Entfernen einer E-Mail-Flussregel

1.  Navigieren Sie im EAC zu **Nachrichtenfluss** \> **Regeln**.

2.  Wählen Sie die Regel aus, die Sie entfernen möchten, und klicken Sie dann auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)").

## Verwenden des Exchange-Verwaltungsshell zum Entfernen einer E-Mail-Flussregel

Im folgenden Beispiel wird die E-Mail-Flussregel "Sender is a member of marketing" entfernt:

    Remove-TransportRule "Sender is a member of marketing"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um sich zu vergewissern, dass Sie die E-Mail-Flussregel erfolgreich entfernt haben:

  - Zeigen Sie im EAC die Liste **Regeln** an und überprüfen Sie, dass die von Ihnen entfernte Regel nicht länger angezeigt wird.

  - Führen Sie in der Exchange-Verwaltungsshell folgenden Befehl aus, um zu überprüfen, ob die Regel, die Sie entfernt haben, nicht mehr aufgeführt wird:
    
        Get-TransportRule

## Überwachung der Regelnutzung

Wenn Sie Exchange Online oder Exchange Online Protection verwenden, können Sie durch die Verwendung eines Regelberichts prüfen, wie oft jede Regel erfüllt wird. Damit eine Regel in den Berichten eingeschlossen wird, muss bei der Regel das Kontrollkästchen **Diese Regel mit Schweregrad überwachen** aktiviert sein. Sie können einen Bericht online anzeigen oder eine Excel-Version aller E-Mail-Schutzberichte herunterladen.


> [!NOTE]
> Die meisten Daten werden innerhalb von 24&nbsp;Stunden im Bericht erfasst. Bei einigen Daten kann es bis zu 5&nbsp;Tage dauern, bis sie angezeigt werden.



## Generieren eines Regelberichts mithilfe des Office 365 Admin Center

1.  Wählen Sie im Office 365 Admin Center **Berichte** aus.

2.  Wählen Sie im Abschnitt **RegelnHäufigste Regelübereinstimmungen bei E-Mails** oder **Regelübereinstimmungen bei E-Mails** aus.

Weitere Informationen finden Sie unter [Anzeigen von Berichten zum E-Mail-Schutz](https://go.microsoft.com/fwlink/p/?linkid=402958).

## Herunterladen einer Excel-Version der Berichte

1.  Wählen Sie im Office 365 Admin Center auf der Berichtsseite **Berichte zum E-Mail-Schutz (Excel)** aus.

2.  Wenn Sie die Excel-Berichte zum E-Mail-Schutz zum ersten Mal verwenden, wird eine Registerkarte mit der Downloadseite geöffnet.
    
    1.  Wählen Sie **Download** aus, um das Microsoft Office-365-Excel-Plug-In für Exchange Online-Berichte herunterzuladen.
    
    2.  Öffnen Sie den Download.
    
    3.  Wählen Sie im Dialogfeld **Mail Protection reports for Office 365 Setup** (Einrichtung für Berichte zum E-Mail-Schutz für Office 365) **Weiter** aus, stimmen Sie den Bedingungen des Lizenzvertrags zu, und wählen Sie dann **Weiter** aus.
    
    4.  Wählen Sie den Dienst aus, den Sie verwenden, und wählen Sie dann **Weiter** aus.
    
    5.  Überprüfen Sie die Voraussetzungen, und klicken Sie auf **Weiter**.
    
    6.  Wählen Sie **Installieren** aus. Auf Ihrem Desktop wird eine Verknüpfung zu den Berichten erstellt.

3.  Wählen Sie auf dem Desktop **Berichte zum E-Mail-Schutz für Office 365** aus.

4.  Wählen Sie im Bericht die Registerkarte **Regeln** aus.

## Importieren oder Exportieren von E-Mail-Flussregelsammlungen

Verwenden Sie die Exchange-Verwaltungsshell, um eine E-Mail-Flussregelsammlung zu im- bzw. exportieren. Informationen zum Importieren einer E-Mail-Flussregelsammlung aus einer XML-Datei finden Sie unter [Import-TransportRuleCollection](https://technet.microsoft.com/de-de/library/bb123582\(v=exchg.150\)). Informationen zum Exportieren einer E-Mail-Flussregelsammlung in eine XML-Datei finden Sie unter [Export-TransportRuleCollection](https://technet.microsoft.com/de-de/library/bb124410\(v=exchg.150\)).

## Benötigen Sie weitere Hilfe?

Ressourcen für Exchange Online:

[Nachrichtenflussregeln (Transportregeln) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919238\(v=exchg.150\))

[Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online](https://technet.microsoft.com/de-de/library/jj919235\(v=exchg.150\))

[Aktionen für Nachrichtenflussregeln in Exchange Online](https://technet.microsoft.com/de-de/library/jj919237\(v=exchg.150\))

[Transport- und Postfachregelgrenzen](https://go.microsoft.com/fwlink/p/?linkid=324584)

Ressourcen für Exchange Online Protection:

[Nachrichtenflussregeln (Transportregeln) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/dn271424\(v=exchg.150\))

[Nachrichtenflussregel-Bedingungen und -Ausnahmen (Prädikate) in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj919234\(v=exchg.150\))

[Aktionen für Nachrichtenflussregeln in Exchange Online Protection](https://technet.microsoft.com/de-de/library/jj920117\(v=exchg.150\))

[Transport- und Postfachregelgrenzen](https://go.microsoft.com/fwlink/p/?linkid=324584)

Ressourcen für Exchange Server 2013:

[Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)

[Transportregelbedingungen (Prädikate)](mail-flow-rule-conditions-and-exceptions-predicates-in-exchange-2013-exchange-2013-help.md)

[Transportregelaktionen](mail-flow-rule-actions-in-exchange-2013-exchange-2013-help.md)

