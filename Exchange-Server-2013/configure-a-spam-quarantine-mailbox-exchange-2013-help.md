---
title: 'Konfigurieren eines Spamquarantänepostfachs: Exchange 2013 Help'
TOCTitle: Konfigurieren eines Spamquarantänepostfachs
ms:assetid: 907d2f90-2a62-4d59-a4cf-945fef2e963f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123746(v=EXCHG.150)
ms:contentKeyID: 50476238
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren eines Spamquarantänepostfachs

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-19_

Nachrichten, die vom Inhaltsfilter-Agent als Spam erkannt werden, können in ein Spam-Quarantänepostfach umgeleitet werden. Wenn der SCL-Isolierungsschwellenwert (Spam Confidence Level) aktiviert ist, werden alle isolierten Nachrichten als Unzustellbarkeitsberichte (NDR) zusammengefasst und an die SMTP-Adresse gesendet, die von Ihnen als Quarantänepostfach für Spam angegeben wurde. Sie können isolierte Nachrichten überprüfen und an die Empfänger senden, für die sie gedacht waren, indem Sie die Funktion "Erneut Senden" in Microsoft Outlook verwenden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 45 Minuten.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Der für das Quarantänepostfach für Spam verantwortliche Benutzer kann möglicherweise private und vertrauliche Nachrichten anzeigen und im Namen jedes Benutzers in der Exchange-Organisation E-Mails senden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Überprüfen, ob die Inhaltsfilterung aktiviert ist

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

1.  Führen Sie den folgenden Befehl aus, um zu überprüfen, ob der Inhaltsfilter-Agent auf dem Exchange-Server installiert und aktiviert ist:
    
        Get-TransportAgent "Content Filter Agent"

2.  Führen Sie den folgenden Befehl, um sicherzustellen, dass Content-Filterung aktiviert ist:
    
        Get-ContentFilterConfig | Format-List Enabled

Weitere Informationen finden Sie unter [Verwalten der Inhaltsfilterung](manage-content-filtering-exchange-2013-help.md).

## Schritt 2: Erstellen eines dedizierten Postfach für die Spamquarantäne

Gehen Sie folgendermaßen Sie vor, um ein dediziertes Postfach für die Spamquarantäne zu erstellen:

  - **Erstellen einer dedizierten Exchange-Datenbank**   Es wird empfohlen, eine dedizierte Datenbank für das Quarantänepostfach für Spam zu erstellen. Das Quarantänepostfach für Spam sollte eine große Datenbank besitzen, weil Nachrichten verloren gehen, wenn das Speicherkontingent erreicht wird. Weitere Informationen finden Sie unter [Verwalten von Postfachdatenbanken in Exchange 2013](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).

  - **Erstellen eines dedizierten Postfachs und Benutzerkontos**   Es wird empfohlen, ein dediziertes Postfach und Active Directory-Benutzerkonto für das Spam-Quarantänepostfach zu erstellen. Weitere Informationen finden Sie unter [Erstellen von Benutzerpostfächern](create-user-mailboxes-exchange-2013-help.md).
    
    Sie können gemäß den Unternehmensrichtlinien und -anforderungen Ihrer Organisation Empfängerrichtlinien anwenden, z. B. Verwaltung von Nachrichtendatensätzen und Postfachkontingente sowie Delegierungsrechte. Weitere Informationen finden Sie unter [Messaging-Datensatzverwaltung](messaging-records-management-exchange-2013-help.md).
    

    > [!NOTE]
    > Wenn eine Nachricht isoliert werden soll, aber aufgrund eines Speicherkontingents abgelehnt wird, geht die Nachricht verloren. Exchange generiert keine Unzustellbarkeitsberichte für isolierte Nachrichten, da isolierte Nachrichten in Unzustellbarkeitsberichte eingeschlossen sind.



  - **Konfigurieren von Outlook**   Sie müssen die Berechtigungen für das Delegieren des Zugriffs in Outlook gemäß den Anforderungen Ihrer Organisation konfigurieren. Außerdem wird empfohlen, das Outlook-Profil so zu konfigurieren, dass die ursprünglichen Felder `Sender[#0x0069001E]`, `Recipient[#0x0E04001E]` und `Bcc[#0x0E02001E]` in der Ansicht **Nachricht** angezeigt werden. Weitere Informationen finden Sie unter [Freigeben von Nachrichten unter Quarantäne aus dem Quarantänepostfach für Spam](release-quarantined-messages-from-the-spam-quarantine-mailbox-exchange-2013-help.md).

## Schritt 3: Festlegen des Quarantänepostfachs für Spam

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

Führen Sie den folgenden Befehl aus:

    Set-ContentFilterConfig -QuarantineMailbox <SmtpAddress>

In diesem Beispiel werden alle Nachrichten, die den Isolierungsschwellenwert für Spam überschreiten, an "spamQ@contoso.com" gesendet.

    Set-ContentFilterConfig -QuarantineMailbox spamQ@contoso.com

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass das Quarantänepostfach für Spam erfolgreich festgelegt wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-ContentFilterConfig | Format-List QuarantineMailbox

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Schritt 4: Konfigurieren des SCL-Isolierungsschwellenwerts

Der SCL-Isolierungsschwellenwert ist der Wert, bei dem eine bestimmte, als möglicher Spam klassifizierte Nachricht dem Quarantänepostfach für Spam zugestellt wird. Sie können den SCL-Isolierungsschwellenwert auf einen Wert zwischen 0 und 9 festlegen, wobei 0 mit geringerer Wahrscheinlichkeit und 9 mit hoher Wahrscheinlichkeit als Spam angesehen wird.

Weitere Informationen zum Anpassen von SCL-Schwellenwerten an die Anforderungen Ihrer Organisation und zum Anpassen von SCL-Schwellenwerten auf Empfängerbasis finden Sie unter [Verwalten der Inhaltsfilterung](manage-content-filtering-exchange-2013-help.md).

## Schritt 5: Verwalten des Spam-Quarantänepostfachs

Wenn Sie das Quarantänepostfach für Spam verwalten, sollten Sie die folgenden Richtlinien befolgen:

  - Geben Sie Elemente frei, die an das Quarantänepostfach für Spam gesendet wurden, indem Sie das Feature "Erneut senden" in Outlook verwenden, um die ursprüngliche Nachricht erneut zu senden.
    
    Weitere Informationen finden Sie unter [Freigeben von Nachrichten unter Quarantäne aus dem Quarantänepostfach für Spam](release-quarantined-messages-from-the-spam-quarantine-mailbox-exchange-2013-help.md).

  - Überwachen Sie das Quarantänepostfach für Spam, damit die Größe des Quarantänepostfachs für Spam in einem akzeptablen Rahmen bleibt. Der Umfang der E-Mail-Nachrichten kann sich durch eine größere Anzahl von Empfängern, den natürlichen Trend zu größeren Nachrichten oder den Schwellenwert für die SCL-Isolierungsaktion ändern.

  - Überwachen Sie das Quarantänepostfachs für Spam auf falsch positive Ergebnisse. Wenn Ihr Quarantänepostfach für Spam viele fälschlicherweise als Spam bewertete Nachrichten enthält, passen Sie den SCL-Isolierungsschwellenwert an. Weitere Informationen zum Ermitteln der Ursache, warum falsch positive Ergebnisse dem Quarantänepostfach für Spam zugestellt werden, finden Sie unter [Antispamstempel](anti-spam-stamps-exchange-2013-help.md).

  - Verwenden Sie dasselbe Outlook-Profil, um isolierte Nachrichten aus dem Quarantänepostfach für Spam wiederherzustellen. Einem anderen Outlook-Profil die Berechtigung zum Wiederherstellen von Nachrichten zuzuweisen, wird nicht unterstützt. Sie können kein anderes Outlook-Profil zum Wiederherstellen oder Freigeben von Nachrichten aus dem Quarantänepostfach für Spam verwenden.


> [!IMPORTANT]
> Unzustellbarkeitsberichte, die als Spam klassifiziert werden, werden selbst dann gelöscht, wenn ihre SCL-Bewertung angibt, dass sie isoliert werden sollten. Unzustellbarkeitsberichte werden nicht dem Quarantänepostfach für Spam zugestellt. Um solche Nachrichten nachzuverfolgen, verwenden Sie das Agent-Protokoll oder das Nachrichtenverfolgungsprotokoll. Weitere Informationen finden Sie unter <A href="anti-spam-agent-logging-exchange-2013-help.md">Antispam-Agent-Protokollierung</A>.



## Schritt 6: Anpassen des SCL-Isolierungsschwellenwerts

Nachdem Sie den SCL-Isolierungsschwellenwert konfiguriert haben, sollten Sie die Einstellungen regelmäßig überwachen und basierend auf den Anforderungen Ihrer Organisation anpassen. Wenn z. B. zu viele falsch positive Ergebnisse in das Quarantänepostfach für Spam gefiltert werden, erhöhen Sie den SCL-Isolierungsschwellenwert auf einen höheren Wert. Weitere Informationen zum Anpassen des SQL-Isolierungsschwellenwerts finden Sie unter [SCL-Schwellenwert](spam-confidence-level-threshold-exchange-2013-help.md).

