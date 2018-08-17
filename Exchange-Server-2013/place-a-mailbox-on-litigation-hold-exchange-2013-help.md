---
title: 'Aktivieren des Beweissicherungsverfahrens für ein Postfach: Exchange 2013 Help'
TOCTitle: Aktivieren des Beweissicherungsverfahrens für ein Postfach
ms:assetid: adee4621-3626-4aec-aa53-00b35ff0d0b0
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn743673(v=EXCHG.150)
ms:contentKeyID: 62268979
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren des Beweissicherungsverfahrens für ein Postfach

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-10-18_

Durch die Aktivierung des Beweissicherungsverfahrens für ein Postfach werden auch alle Postfachinhalte aufbewahrt, einschließlich gelöschter Elemente und Originalversionen geänderter Elemente. Wenn Sie für das Postfach eines Benutzers das Beweissicherungsverfahren aktivieren, wird auch der Inhalt im Archivpostfach archiviert, wenn dieses aktiviert ist. Gelöschte und geänderte Elemente werden eine bestimmte Zeit lang aufbewahrt oder bis Sie das Beweissicherungsverfahren für das Postfach deaktivieren. Alle diese Postfachelemente werden bei einer [Compliance-eDiscovery](in-place-ediscovery-exchange-2013-help.md)-Suche zurückgegeben.


> [!IMPORTANT]
> Das Beweissicherungsverfahren behält Elemente im Ordner "Wiederherstellbare Elemente" im Postfach des Benutzers bei. In Abhängigkeit der Anzahl und Größe der gelöschten oder geänderten Elemente steigt die Größe des Ordners "Wiederherstellbare Elemente" des Postfachs möglicherweise rasant. Der Ordner "Wiederherstellbare Elemente" wird standardmäßig mit einem hohen Kontingent konfiguriert. In Exchange Online wird dieses Kontingent automatisch erhöht, wenn Sie für ein Postfach das Beweissicherungsverfahren aktivieren. In Exchange Server&nbsp;2013 sollten Sie Postfächer, für die die Beweissicherung aktiviert ist, auf wöchentlicher Basis überwachen, um sicherzustellen, dass sie nicht die Kontingente für "Wiederherstellbare Elemente" erreichen.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten

  - Es dauert bis zu 60 Minuten, bis die Einstellung für das Beweissicherungsverfahren in Kraft tritt.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „In-Situ-Archiv“ im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Um für ein Exchange Online-Postfach das Beweissicherungsverfahren zu aktivieren, muss ihm eine Exchange Online-Lizenz (Tarif 2) zugewiesen werden. Wenn einem Postfach eine Exchange Online-Lizenz (Tarif 1) zugewiesen ist, müssen Sie ihm eine separate Exchange Online-Archivierungslizenz zuweisen, um es anzuhalten.

  - Wie bereits erwähnt, wird der Inhalt im Archivpostfach des Benutzers auch ausgesetzt, wenn Sie für das Postfach eines Benutzers ein Beweissicherungsverfahren festlegen. Wenn Sie ein Beweissicherungsverfahren für ein lokales primäres Postfach in einer Exchange-Hybridbereitstellung festlegen, wird auch das cloudbasierte Archivpostfach (sofern aktiviert) ausgesetzt.

  - In Exchange Online wird das Kontingent für den Ordner "Wiederherstellbare Elemente" automatisch auf 100 GB erhöht, wenn Sie für ein Postfach das Beweissicherungsverfahren aktivieren. Die Standardgröße dieses Ordners beträgt 30 GB.

  - Das Beweissicherungsverfahren behält gelöschte Elemente und die ursprünglichen Versionen der geänderten Elemente bei, bis die Aufbewahrung entfernt wird. Sie können optional eine Aufbewahrungsdauer angeben, in der ein Postfachelement für eine angegebene Zeitdauer beibehalten wird. Wenn Sie eine Aufbewahrungsdauer angeben, wird sie vom Datum an berechnet, an dem eine Nachricht empfangen oder ein Postfachelement erstellt wurde. Verwenden Sie zum Beibehalten von Elementen, die Ihre angegeben Kriterien erfüllen, einen In-Situ-Speicher zum Erstellen einer *abfragebasierten* Aufbewahrung. Weitere Informationen finden Sie unter [Erstellen oder Entfernen eines Compliance-Archivs](create-or-remove-an-in-place-hold-exchange-2013-help.md).

  - Verwenden Sie die Exchange Online-PowerShell, um die Shell zum Ablegen eines Exchange Online-Postfachs in das Archiv zu verwenden Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Exchange Online mithilfe der Remote-PowerShell](https://technet.microsoft.com/de-de/library/jj984289\(v=exchg.150\)).

  - Das Festlegen eines Beweissicherungsverfahrens für ein Postfach für öffentliche Ordner wird nicht unterstützt. Sie müssen einen In-Situ-Speicher verwenden, um eine Speicherung für öffentliche Ordner festzulegen.

## Verwenden von EAC zum Aktivieren des Beweissicherungsverfahrens für ein Postfach

1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.

2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, für das Sie die Beweissicherungsverfahren aktivieren möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.

4.  Klicken Sie unter **Beweissicherungsverfahren: Deaktiviert** auf **Aktivieren**, um für das Postfach das Beweissicherungsverfahren zu aktivieren.

5.  Geben Sie auf der Seite **Beweissicherungsverfahren** die folgenden optionalen Informationen ein:
    
      - **Dauer des Beweissicherungsverfahrens (Tage)**   Verwenden Sie dieses Feld zum Angeben, wie lange Postfachelemente aufbewahrt werden, wenn für das Postfach das Beweissicherungsverfahren aktiviert wird. Der Zeitraum beginnt mit dem Datum, an dem das Postfachelement empfangen oder erstellt wurde. Wenn Sie dieses Feld leer lassen, werden Elemente unbegrenzt aufbewahrt oder bis die Aufbewahrung entfernt wird. Geben Sie die Dauer in Tagen an.
    
      - **Hinweis**   Verwenden Sie dieses Feld, um Benutzer darüber zu informieren, dass für ihr Postfach das Beweissicherungsverfahren aktiv ist. Der Hinweis wird im Postfach des Benutzers angezeigt, wenn er Outlook 2010 oder höher verwendet.
    
      - **URL**   Verwenden Sie dieses Feld, um den Benutzer an eine Website weiterzuleiten, auf der er weitere Informationen über das Beweissicherungsverfahren erhält. Diese URL wird im Postfach des Benutzers angezeigt, wenn er Outlook 2010 oder höher verwendet.

6.  Klicken Sie auf **Speichern** auf der Seite **Beweissicherungsverfahren**, und klicken Sie dann auf der Postfacheigenschaftsseite auf **Speichern**.

Zurück zum Seitenanfang

## Verwenden der Shell zum Aktivieren des unbegrenzten Beweissicherungsverfahrens für ein Postfach

In diesem Beispiel wird das Beweissicherungsverfahren für das Postfach "bsuneja@contoso.com" aktiviert. Elemente im Postfach werden unbegrenzt aufbewahrt oder bis die Aufbewahrung entfernt wird.

    Set-Mailbox bsuneja@contoso.com -LitigationHoldEnabled $true


> [!NOTE]
> Wenn Sie für ein Postfach das unbegrenzte Beweissicherungsverfahren aktivieren (indem Sie keine Dauer angeben), wird der Wert für die <EM>LitigationHoldDuration</EM>-Eigenschaft des Postfachs auf <CODE>Unlimited</CODE> festgelegt.



## Verwenden der Shell zum Aktivieren eines Postfachs für das Beweissicherungsverfahren und Beibehalten von Elementen für eine bestimmte Dauer

In diesem Beispiel wird das Beweissicherungsverfahren für das Postfach "mailbox bsuneja@contoso.com" aktiviert, und Elemente werden für 2.555 Tage (etwa 7 Jahre) beibehalten.

    Set-Mailbox bsuneja@contoso.com -LitigationHoldEnabled $true -LitigationHoldDuration 2555

## Verwenden der Shell zum Aktivieren des Beweissicherungsverfahrens für alle Postfächer für eine bestimmte Dauer

In Ihrer Organisation ist es möglicherweise erforderlich, dass alle Postfachdaten für einen bestimmten Zeitraum beibehalten werden. Bedenken Sie Folgendes, bevor Sie für alle Postfächer in einer Organisation das Beweissicherungsverfahren aktivieren:

In diesem Beispiel wird für alle Benutzerpostfächer in der Organisation für ein Jahr (365 Tage) das Beweissicherungsverfahren aktiviert.

    Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | Set-Mailbox -LitigationHoldEnabled $true -LitigationHoldDuration 365

Im Beispiel wird das Cmdlet [Get-Mailbox](https://technet.microsoft.com/de-de/library/bb123685\(v=exchg.150\)) verwendet, um alle Postfächer in der Organisation abzurufen. Es wird ein Empfängerfilter angegeben, um alle Benutzerpostfächer einzubeziehen. Anschließend wird die Liste der Postfächer an das [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))-Cmdlet umgeleitet, um das Beweissicherungsverfahren und die Aufbewahrungsdauer zu aktivieren.

Führen Sie den vorherigen Befehl ohne den Parameter *LitigationHoldDuration* aus, um alle Benutzerpostfächer unbegrenzt aufzubewahren.

Im Abschnitt Weitere Informationen finden Sie Beispiele für die Verwendung von anderen Empfängereigenschaften in einem Filter zum Einbeziehen oder Ausschließen von mindestens einem Postfach.

## Verwenden der Shell zum Aufheben des Beweissicherungsverfahrens für ein Postfach

In diesem Beispiel wird das Beweissicherungsverfahren für das Postfach "bsuneja@contoso.com" aufgehoben.

    Set-Mailbox bsuneja@contoso.com -LitigationHoldEnabled $false

Zurück zum Seitenanfang

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie eine der folgenden Aktionen aus, um sicherzustellen, dass Sie das Beweissicherungsverfahren für ein Postfach erfolgreich aktiviert haben:

  - In der Exchange-Verwaltungskonsole:
    
    1.  Navigieren Sie zu **Empfänger** \> **Postfächer**.
    
    2.  Klicken Sie in der Liste der Benutzerpostfächer auf das Postfach, dessen Einstellungen für das Beweissicherungsverfahren Sie überprüfen möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").
    
    3.  Klicken Sie auf der Eigenschaftenseite des Postfachs auf **Postfachfunktionen**.
    
    4.  Stellen Sie unter **Beweissicherungsverfahren** sicher, dass die Aufbewahrung aktiviert ist.
    
    5.  Klicken Sie auf **Details anzeigen**, um zu prüfen, wann und durch wen das Beweissicherungsverfahren für das Postfach aktiviert wurde. Sie können die Werte in den optionalen Feldern **Dauer des Beweissicherungsverfahrens (Tage)**, **Hinweis** und **URL** auch prüfen oder ändern.

  - Führen Sie in der Shell einen der folgenden Befehle aus:
    
        Get-Mailbox <name of mailbox> | FL LitigationHold*
    
    oder
    
        Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"} | FL Name,LitigationHold*
    
    Wenn das unbegrenzte Beweissicherungsverfahren für ein Postfach aktiviert ist, ist der Wert für die Eigenschaft *LitigationHoldDuration* des Postfachs auf `Unlimited` festgelegt.

## Weitere Informationen

  - Wenn Ihre Organisation verlangt, dass alle Postfachdaten für einen bestimmten Zeitraum beibehalten werden müssen, ziehen Sie Folgendes in Betracht, bevor Sie das Beweissicherungsverfahren für alle Postfächer in einer Organisation aktivieren.
    
      - Wenn Sie den vorherigen Befehl verwenden, um eine Aufbewahrung für alle Postfächer in einer Organisation (oder eine Teilmenge an Postfächern, die mit einem angegebenen Empfängerfilter übereinstimmen) zu aktivieren, wird die Aufbewahrung nur für die Postfächer aktiviert, die zum Zeitpunkt der Befehlsausführung vorhanden sind. Wenn Sie später neue Postfächer erstellen, müssen Sie den Befehl erneut ausführen, um die neuen Postfächer aufzubewahren. Wenn Sie oft neue Postfächer erstellen, können Sie den Befehl als geplante Aufgabe so oft wie erforderlich ausführen.
    
      - Die Aktivierung des Beweissicherungsverfahrens für alle Postfächer kann sich erheblich auf die Postfachgrößen auswirken. Planen Sie in einer Exchange Server 2013-Organisation ausreichend Speicherplatz ein, um die Aufbewahrungsanforderungen Ihrer Organisation zu erfüllen.
    
      - Für den Ordner "Wiederherstellbare Elemente" gilt eine eigene Speicherbegrenzung, sodass Elemente in diesem Ordner nicht zur Speicherbegrenzung des Postfachs zählen. Wie bereits erläutert, nimmt die Datenmenge im Postfach und Archiv eines Benutzers im Ordner "Wiederherstellbare Elemente" zu, wenn Sie Postfachdaten über einen langen Zeitraum aufbewahren. Um dieser Erhöhung Rechnung zu tragen, wird in Exchange Online das Kontingent für den Ordner "Wiederherstellbare Elemente" automatisch von 30 auf 100 GB erhöht, wenn Sie für ein Postfach das Beweissicherungsverfahren aktivieren.
        
        In Exchange Server 2013 beträgt die Speichergrenze für den Ordner "Wiederherstellbare Elemente" ebenfalls 30 GB. Wir empfehlen, die Größe des Ordners regelmäßig zu überprüfen, um sicherzustellen, dass die Grenze nicht erreicht wird. Weitere Informationen finden Sie unter [Ordner "Wiederherstellbare Elemente"](recoverable-items-folder-exchange-2013-help.md).

  - Der vorherige Befehl zum Platzieren aller Postfächer im Archiv verwendet einen Empfängerfilter, der alle Benutzerpostfächer zurückgibt. Sie können andere Empfängereigenschaften zum Zurückgeben einer Liste von bestimmten Postfächern verwenden, die Sie an das Cmdlet **Set-Mailbox** umleiten können, um für diese Postfächer ein Beweissicherungsverfahren zu aktivieren.
    
    Hier sind einige Beispiele dafür, wie mit den Cmdlets **Get-Mailbox** und **Get-Recipient** eine Teilmenge an Postfächern basierend auf allgemeinen Benutzer- oder Postfacheigenschaften zurückgegeben wird. In diesen Beispielen wird davon ausgegangen, dass entsprechende Postfacheigenschaften (wie *CustomAttributeN* oder *Department*) aufgefüllt wurden.
    
```
	Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'CustomAttribute15 -eq "OneYearLitigationHold"'
```

```
	Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'Department -eq "HR"'
```

```
	Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'PostalCode -eq "98052"'
```

```
	Get-Recipient -RecipientTypeDetails UserMailbox -ResultSize unlimited -Filter 'StateOrProvince -eq "WA"'
```

```
	Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -ne "DiscoveryMailbox"}
```    

Sie können andere Benutzerpostfacheigenschaften in einem Filter verwenden, um Postfächer einzubeziehen bzw. auszuschließen. Weitere Informationen finden Sie unter [Filterbare Eigenschaften für den Parameter „-Filter“](https://technet.microsoft.com/de-de/library/bb738155\(v=exchg.150\)).

Zurück zum Seitenanfang

