---
title: 'Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server: Exchange 2013 Help'
TOCTitle: Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server
ms:assetid: d12ea770-99ce-4ab4-a373-96f2554641fa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb738158(v=EXCHG.150)
ms:contentKeyID: 61180476
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Zum Einrichten der Internetnachrichtenübermittlung über einen Edge-Transport-Server abonnieren Sie den Edge-Transport-Server für einen Active Directory-Standort. Dabei werden die beiden erforderlichen Sendeconnectors für den Internetnachrichtenfluss automatisch erstellt.

  - Ein Sendeconnector, der zum Senden von ausgehenden E-Mails an alle Internetdomänen konfiguriert wird

  - Ein Sendeconnector, der zum Senden von eingehenden E-Mails vom Edge-Transport-Server zu einem Exchange 2013-Postfachserver konfiguriert wird

Wenn Sie kein Abonnement des Edge-Transport-Servers mit dem Active Directory-Standort herstellen möchten, können Sie die Sendeconnectors, die zum Einrichten der Nachrichtenübermittlung zwischen dem Postfach- und dem Edge-Transport-Server erforderlich sind, manuell erstellen. Weitere Informationen finden Sie unter [Konfigurieren der Internetnachrichtenflusses über einen Edge-Transport-Server ohne Verwendung von EdgeSync](configure-internet-mail-flow-through-an-edge-transport-server-without-using-edgesync-exchange-2013-help.md). Es wird jedoch empfohlen, wenn möglich ein Abonnement des Edge-Transport-Servers mit dem Active Directory-Standort herzustellen.

## Bevor Sie beginnen

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 20 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "EdgeSync" und "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Bevor Sie einen Edge-Transport-Server für Ihre Organisation abonnieren, müssen Sie zunächst die autorisierten Domänen und die E-Mail-Adressrichtlinien für Ihre Exchange-Organisation konfigurieren.

  - Aktivieren Sie den sicheren LDAP-Port 50636/TCP über die Firewall, die das Umkreisnetzwerk von der Exchange-Organisation trennt. Der Edge-Transport-Server muss in der Lage sein, mit allen Exchange 2013-Postfachservern am abonnierten Active Directory-Standort zu kommunizieren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der Internetnachrichtenübermittlung über einen abonnierten Edge-Transport-Server

1.  Erstellen Sie die Edge-Abonnementdatei auf dem Edge-Transport-Server mithilfe der folgenden Syntax.
    
        New-EdgeSubscription -FileName <FileName>.xml [-Force]
    
    Im folgenden Beispiel wird eine Edge-Abonnementdatei mit dem Namen "EdgeSubscriptionInfo.xml" im Ordner "C:\\My Documents" erstellt. Der Parameter *Force* unterdrückt Aufforderungen, in denen Sie die zu deaktivierenden Befehle und Warnungen, dass die Konfigurationsdaten auf dem Edge-Transport-Server überschrieben werden, bestätigen müssen.
    
        New-EdgeSubscription -FileName "C:\My Documents\EdgeSubscriptionInfo.xml" -Force

2.  Kopieren Sie die resultierende Edge-Abonnementdatei auf einen Postfachserver am Active Directory-Standort, für den der Edge-Transport-Server abonniert werden soll.

3.  Verwenden Sie zum Importieren der Edge-Abonnementdatei auf dem Postfachserver die folgende Syntax.
    
        New-EdgeSubscription -FileData ([byte[]]$(Get-Content -Path "<FileName>.xml" -Encoding Byte -ReadCount 0)) -Site <SiteName>
    
    In diesem Beispiel wird die Edge-Abonnementdatei mit dem Namen "EdgeSubscriptionInfo.xml" aus dem Ordner "D:\\Data" importiert. Der Edge-Transport-Server wird am Active Directory-Standort "Default-First-Site-Name" abonniert.
    
        New-EdgeSubscription -FileData ([byte[]]$(Get-Content -Path "D:\Data\EdgeSubscriptionInfo.xml" -Encoding Byte -ReadCount 0)) -Site "Default-First-Site-Name"
    

    > [!NOTE]
    > Sie können den Parameter <EM>CreateInternetSendConnector</EM> oder den Parameter <EM>CreateInboundSendConnector</EM> verwenden, um zu verhindern, dass einer der erforderlichen Sendeconnectors oder beide Sendeconnectors automatisch erstellt werden. Weitere Informationen finden Sie unter <A href="edge-subscriptions-exchange-2013-help.md">Edge-Abonnements</A>.



4.  Führen Sie auf dem Postfachserver den folgenden Befehl aus, um die EdgeSync-Synchronisierung zum ersten Mal zu starten.
    
        Start-EdgeSynchronization

5.  Wenn Sie den Vorgang abgeschlossen haben, wird dringend empfohlen, dass Sie die Edge-Abonnementdatei sowohl auf dem Edge-Transport-Server als auch auf dem Postfachserver löschen. Die Edge-Abonnementdatei enthält Informationen zu den Anmeldeinformationen, die während des LDAP-Kommunikationsvorgangs verwendet werden.

