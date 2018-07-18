---
title: 'Erstellen eines virtuellen Offlineadressbuch-Verzeichnisses: Exchange 2013 Help'
TOCTitle: Erstellen eines virtuellen Offlineadressbuch-Verzeichnisses
ms:assetid: 2c70e21f-2b12-414a-9e8c-65634a767c72
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996917(v=EXCHG.150)
ms:contentKeyID: 50475254
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Erstellen eines virtuellen Offlineadressbuch-Verzeichnisses

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-10-16_

Das virtuelle OAB-Verzeichnis ist der Verteilungspunkt für das OAB. Bei der Installation von Microsoft Exchange Server 2013 wird standardmäßig ein neues virtuelles Verzeichnis mit dem Namen "OAB" auf der internen Standardwebsite von IIS (Internet Information Services, Internetinformationsdienste) erstellt. Wenn clientseitige Benutzer außerhalb der Firewall Ihrer Organisation eine Verbindung mit MicrosoftOutlook herstellen, können Sie eine externe Website hinzufügen. Alternativ dazu wird ein neues virtuelles Verzeichnis mit dem Namen "OAB" auf der IIS-Standardwebsite auf dem lokalen Exchange-Server erstellt, wenn Sie das Cmdlet **New-OABVirtualDirectory** in der Shell ausführen.

Das Erstellen eines virtuellen OAB-Verzeichnisses ist keine Aufgabe, die häufig ausgeführt werden muss. In Exchange ist ein virtuelles OAB-Verzeichnis namens "OAB" zulässig, und Sie sollten nur dann ein virtuelles OAB-Verzeichnis erstellen, wenn ein Problem mit dem vorhandenen virtuellen OAB-Verzeichnis vorliegt und das vorherige virtuelle OAB-Verzeichnis entfernt wurde.

Informationen zu weiteren Verwaltungsaufgaben in Bezug auf OABs finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).


> [!IMPORTANT]
> Stellen Sie sicher, dass die Benutzer über die ausgeführten Änderungen informiert sind, bevor Sie ein virtuelles OAB-Verzeichnis erstellen. Möglicherweise unterbrechen Sie den OAB-Downloadvorgang für Ihre Benutzer.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Offlineadressbücher" im Thema [Berechtigungen für E-Mail-Adressen und Adressbücher](email-address-and-address-book-permissions-exchange-2013-help.md).

  - Auf dem lokalen Exchange-Server muss die Clientzugriffs-Serverrolle installiert sein.

  - Es ist eine IIS-Standardwebsite vorhanden, z. B. /w3svc/1/root.

  - Es ist noch kein virtuelles Verzeichnis mit dem Namen "OAB" vorhanden.

  - Die webbasierte Verteilung ist zwar standardmäßig aktiviert und erfordert keine weitere Konfiguration, es wird jedoch empfohlen, SSL (Secure Sockets Layer) für den OAB-Verteilungspunkt zu aktivieren.

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden der Shell zum Erstellen eines virtuellen OAB-Verzeichnisses

Um ein virtuelles OAB-Verzeichnis mit allen Standardeinstellungen zu erstellen, können Sie das Cmdlet **New-OABVirtualDirectory** ohne Parameter ausführen. Verwenden Sie das folgende Verfahren, um ein virtuelles OAB-Verzeichnis mit benutzerdefinierten Einstellungen zu erstellen.


> [!NOTE]
> Es wird empfohlen, SSL zu aktivieren, wenn Sie ein virtuelles OAB-Verzeichnis erstellen.



In diesem Beispiel wird ein virtuelles OAB-Verzeichnis auf dem Clientzugriffsserver mit dem Namen "CASServer01" erstellt, für das SSL aktiviert ist und das über eine externe URL verfügt.

    New-OABVirtualDirectory -Server CASServer01 -RequireSSL $true -ExternalURL "https://www.contoso.com/OAB"

Nachdem Sie ein neues virtuelles OAB-Verzeichnis erstellt haben, müssen Sie die Einstellungen für jedes OAB bearbeiten, das webbasierte Verteilung verwendet, um erneut eine Verbindung mit dem virtuellen OAB-Verzeichnis herzustellen. Weitere Informationen finden Sie unter [Ändern des Zeitplans für die Generierung des Offlineadressbuchs](change-the-offline-address-book-generation-schedule-exchange-2013-help.md).

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [New-OabVirtualDirectory](https://technet.microsoft.com/de-de/library/bb123735\(v=exchg.150\)).

