---
title: 'Verwaltung von Edge-Abonnements: Exchange 2013 Help'
TOCTitle: Verwaltung von Edge-Abonnements
ms:assetid: 27de4104-fb8e-4eab-9ad2-a64f81a4fb69
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996865(v=EXCHG.150)
ms:contentKeyID: 61180465
ms.date: 04/27/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwaltung von Edge-Abonnements

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2018-04-16_

In diesem Thema erhalten Sie detaillierte Informationen über verschiedene Aufgaben zur Verwaltung von Edge-Abonnements.

**Inhalt**

Abonnieren eines Edge-Transport-Servers

Entfernen eines Edge-Abonnements

Erneutes Abonnieren eines Edge-Transport-Servers

Hinzufügen oder Entfernen eines Postfachservers

Manuelle Ausführung von EdgeSync

Überprüfen der EdgeSync-Ergebnisse

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter Eintrag "EdgeSync" und Abschnitt "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Sie müssen über einen Edge-Server verfügen, der Ihren mit dem Internet verbundenen Active Directory-Standort abonniert hat. Weitere Informationen finden Sie unter [Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server](configure-internet-mail-flow-through-a-subscribed-edge-transport-server-exchange-2013-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Abonnieren eines Edge-Transport-Servers

Sie können einen oder mehrere Edge-Transport-Server an einem einzelnen Active Directory-Standort abonnieren. Wenn Sie zusätzliche Edge-Transport-Server in Ihrem Umkreisnetzwerk bereitstellen und diese für den gleichen Active Directory-Standort abonnieren, für den ein Edge-Abonnement bereits vorhanden ist, bewirkt dies Folgendes:

  - Ein neues Edge-Abonnementobjekt wird in Active Directory erstellt.

  - Für jeden Postfachserver am Active Directory-Standort wird ein zusätzliches ESRA-Konto erstellt. Diese Konten werden nach Active Directory Lightweight Directory Services (AD LDS) repliziert und von EdgeSync-Synchronisierungsprozess während der Synchronisierung mit dem neuen Server verwendet.

  - Das neue Edge-Abonnement wird der Quellserverliste der automatischen Sendeconnector in das Internet hinzugefügt. Für Nachrichten, die an diesen Connector zur Verarbeitung übermittelt werden, wird ein Lastenausgleich zwischen den abonnierten Edge-Transport-Servern durchgeführt.

  - Der eingehende Sendeconnector vom Edge-Transport-Server zur Exchange-Organisation wird automatisch erstellt.

  - Die EdgeSync-Synchronisierung auf den Edge-Transport-Server beginnt.

## Entfernen eines Edge-Abonnements

Gelegentlich könnten Sie ein Edge-Abonnement aus der Exchange-Organisation oder sowohl aus der Exchange-Organisation als auch vom Edge-Transport-Server entfernen wollen. Wenn Sie planen, diesen Edge-Transport-Server später wieder für die Exchange-Organisation zu abonnieren, löschen Sie das Edge-Abonnement nicht vom Edge-Transport-Server Wenn Sie das Edge-Abonnement von einem Edge-Transport-Server entfernen, werden alle replizierten Daten aus AD LDS gelöscht. Dieser Vorgang kann sehr viel Zeit in Anspruch nehmen, wenn eine große Menge von Empfängerdaten vorhanden ist.

Um ein Edge-Abonnement komplett zu entfernen, müssen Sie dieses Verfahren auf dem Edge-Transport-Server, den Sie entfernen möchten, und auf einem Exchange 2013-Postfachserver an dem Active Directory-Standort, für den der Edge-Transport-Server abonniert wurde, ausführen.

Nach dem Entfernen des Edge-Abonnements wird die Synchronisierung der Informationen von AD LDS gestoppt. Alle Konten, die in AD LDS gespeichert sind, werden entfernt, und der Edge-Transport-Server wird aus der Quellserverliste aller Sendeconnectors entfernt. Die Edge-Transport-Serverfunktionen, die von Active Directory-Daten abhängen, können anschließend nicht mehr verwendet werden.

1.  Verwenden Sie die folgende Syntax, um das Edge-Abonnement vom Edge-Transport-Server zu entfernen.
    
        Remove-EdgeSubscription <EdgeTransportServerIdentity>
    
    Führen Sie z. B. den folgenden Befehl aus, wenn Sie das Edge-Abonnement vom Edge-Transport-Server namens Edge01 löschen möchten.
    
        Remove-EdgeSubscription Edge01

2.  Verwenden Sie die folgende Syntax, um das Edge-Abonnement vom Postfachserver zu entfernen.
    
        Remove-EdgeSubscription <MailboxServerIdentity>
    
    Führen Sie z. B. den folgenden Befehl aus, wenn Sie das Edge-Abonnement vom Postfachserver namens Mailbox01 löschen möchten.
    
        Remove-EdgeSubscription Mailbox01

Sie müssen das Edge-Abonnement entfernen, wenn:

  - Der Edge-Transport-Server nicht mehr an der EdgeSync-Synchronisierung teilnehmen soll. Sie müssen das Edge-Abonnement sowohl vom Edge-Transport-Server als auch aus der Exchange-Organisation entfernen.

  - Ein Edge-Transport-Server wird außer Betrieb gesetzt. In diesem Szenario müssen Sie nur das Edge-Abonnement aus der Exchange-Organisation entfernen. Wenn Sie die Edge-Transport-Serverrolle vom Computer deinstallieren, werden auch die AD LDS-Instanz und alle in AD LDS gespeicherten Active Directory-Daten entfernt.

  - Sie möchten die Active Directory-Standortzuordnung für das Edge-Abonnement ändern. Sie müssen nur das Edge-Abonnement aus der Exchange-Organisation entfernen. Nachdem das Edge-Abonnement aus der Exchange-Organisation entfernt wurde, können Sie den Edge-Transport-Server für einen anderen Active Directory-Standort erneut abonnieren.

Wenn Sie ein Edge-Abonnement aus der Exchange-Organisation entfernen:

  - Die Synchronisierung von Informationen aus Active Directory in AD LDS wird beendet.

  - Die ESRA-Konten werden aus Active Directory und AD LDS entfernt.

  - Der Edge-Transport-Server wird aus der Eigenschaft *SourceTransportServers* aller Sendeconnectors entfernt.

  - Der automatische eingehende Sendeconnector vom Edge-Transport-Server zur Exchange-Organisation wird aus AD LDS entfernt.

Wenn Sie das Edge-Abonnement von einem Edge-Transport-Server entfernen:

  - Sie können die Edge-Transport-Server-Features nicht mehr verwenden, die von Active Directory-Daten abhängen.

  - Die replizierten Daten werden aus AD LDS entfernt.

  - Die Tasks, die bei der Erstellung des Edge-Abonnements deaktiviert wurden, werden erneut aktiviert, um die lokale Konfiguration zu ermöglichen.

## Erneutes Abonnieren eines Edge-Transport-Servers

Es kann vorkommen, dass Sie einen Edge-Transport-Server wieder für einen Active Directory-Standort abonnieren möchten. Wenn das Edge-Abonnement wiederhergestellt wird, werden neue Anmeldeinformationen erstellt, und Sie müssen das komplette Edge-Abonnementsverfahren ausführen. Sie müssen einen Edge-Transport-Server erneut abonnieren, wenn:

  - Sie neue Postfachserver zum abonnierten Active Directory-Standort hinzufügen und möchten, dass der neue Postfachserver an der EdgeSync-Synchronisierung teilnimmt.

  - Sie nach dem Erstellen des Edge-Abonnements den Lizenzschlüssel für den Edge-Transport-Server übernommen haben. Die Lizenzierungsinformationen für den Edge-Transport-Server werden bei der Erstellung des Edge-Abonnements erfasst. Abonnierte Edge-Transport-Server werden nur dann als lizenziert angezeigt, wenn sie für die Exchange-Organisation abonniert wurden, nachdem der Lizenzschlüssel bereits für den Edge-Transport-Server übernommen wurde. Wird der Lizenzschlüssel auf dem Edge-Transport-Server angewendet, nachdem das Edge-Abonnementverfahren durchgeführt wurde, werden die Lizenzierungsinformationen in der Exchange-Organisation nicht aktualisiert, und Sie müssen den Edge-Transport-Server erneut abonnieren.

  - Die ESRA-Anmeldeinformationen sind beschädigt.
    

    > [!IMPORTANT]
    > Um einen Edge-Transport-Server erneut zu abonnieren, exportieren Sie eine neue Edge-Abonnementdatei auf den Edge-Transport-Server, und importieren Sie dann die XML-Datei auf einen Postfachserver. Sie müssen den Edge-Transport-Server am gleichen Active&nbsp;Directory-Standort erneut abonnieren, für den er ursprünglich abonniert war. Das ursprüngliche Edge-Abonnement muss nicht entfernt werden. Durch den Prozess des erneuten Abonnierens wird das vorhandene Edge-Abonnement außer Kraft gesetzt.



## Hinzufügen oder Entfernen eines Postfachservers

Wenn Sie einen Postfachserver für einen Active Directory-Standort abonnieren, für den bereits ein Edge-Transport-Server abonniert ist, nimmt der neue Postfachserver nicht automatisch an der EdgeSync-Synchronisierung teil. Um die Teilnahme eines neu eingesetzten Postfachservers an der EdgeSync-Synchronisierung zu aktivieren, müssen Sie jeden Edge-Transport-Server für den Active Directory-Standort abonnieren.

Wenn ein Postfachserver von einem Active Directory-Standort entfernt wird, für den ein Edge-Transport-Server abonniert wurde, wirkt sich dies nicht auf die EdgeSync-Synchronisierung aus, außer wenn dieser Postfachserver der einzige Postfachserver an diesem Standort ist. Wenn Sie alle Postfachserver aus dem Active Directory-Standort entfernen, für den ein Edge-Transport-Server abonniert wurde, sind die für diesen Standort abonnierten Edge-Transport-Server verwaist.

## Manuelle Ausführung von EdgeSync

Es kann angebracht sein, EdgeSync manuell auszuführen, wenn Sie größere Änderungen an der Konfiguration oder an Empfängern in Active Directory durchgeführt haben und diese Änderungen sofort synchronisiert werden sollen. Sie können eine vollständige Synchronisierung durchführen oder nur die seit der letzten Replikation durchgeführten Änderungen synchronisieren.

Eine manuelle EdgeSync setzt den EdgeSync-Synchronisierungszeitplan zurück. Die nächste automatische Synchronisierung richtig sich danach, wann die letzte manuelle Synchronisierung stattgefunden hat,

Verwenden Sie die folgende Syntax, um die EdgeSync manuell auszuführen:

    Start-EdgeSynchronization [-Server <MailboxServerIdentity>] [-TargetServer <EdgeTransportServerIdentity> [-ForceFullSync]

Das folgende Beispiel startet EdgeSync mit den folgenden Optionen:

  - Die Synchronisierung wird durch den Exchange 2013-Postfachserver mit dem Namen Mailbox01 initiiert.

  - Alle Edge-Transport-Server werden synchronisiert.

  - Nur die Änderungen seit der letzten Replikation werden synchronisiert.

<!-- end list -->

    Start-EdgeSynchronization -Server Mailbox01

In diesem Beispiel startet die EdgeSync-Synchronisierung mit den folgenden Optionen:

  - Die Synchronisierung wird vom lokalen Postfachserver initiiert.

  - Nur der Edge-Transport-Server mit dem Namen Edge03 wird synchronisiert.

  - Alle Empfänger- und Konfigurationsdaten werden vollständig synchronisiert.

<!-- end list -->

    Start-EdgeSynchronization -TargetServer Edge03 -ForceFullSync

## Überprüfen der EdgeSync-Ergebnisse

Sie können das Cmdlet **Test-EdgeSynchronization** verwenden, um den ordnungsgemäßen Ablauf der Edge-Synchronisierung zu überprüfen. Dieses Cmdlet meldet den Synchronisierungsstatus der abonnierten Edge-Transport-Server.

Die Ausgabe dieses Cmdlets zeigt an, welche Objekte nicht mit dem Edge-Transport-Server synchronisiert wurden. Der Task vergleicht die in Active Directory gespeicherten Daten mit den in AD LDS gespeicherten Daten und meldet alle Dateninkonsistenzen.

Verwenden Sie den Parameter *ExcludeRecipientTest* auf dem Cmdlet **Test-EdgeSynchronization**, um die Prüfung der Synchronisierung von Empfängerdaten auszuschließen. Wenn Sie diesen Parameter einbeziehen, wird nur die Synchronisation von Konfigurationsobjekten überprüft. Die Überprüfung von Empfängerdaten dauert länger als die reine Prüfung von Konfigurationsdaten.

## Überprüfen der EdgeSync-Ergebnisse für einen einzelnen Empfänger

Verwenden Sie die folgende Syntax auf einem Postfachserver am Active Directory-Standort, wenn Sie die EdgeSync-Ergebnisse für einen einzelnen Empfänger überprüfen möchten:

    Test-EdgeSynchronization -VerifyRecipient <emailaddress>

Dieses Beispiel überprüft die EdgeSync-Ergebnisse für den Benutzer kate@contoso.com.

    Test-EdgeSynchronization -VerifyRecipient kate@contoso.com

Zurück zum Seitenanfang

