---
title: 'Offlineadressbücher: Exchange 2013 Help'
TOCTitle: Offlineadressbücher
ms:assetid: a6bcb072-4ab9-400e-a5d0-c05264629097
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232155(v=EXCHG.150)
ms:contentKeyID: 50476395
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Offlineadressbücher

 

_**Gilt für:** Exchange Server 2010, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-11-16_

Ein Offlineadressbuch (OAB) ist die Kopie einer Adresslistensammlung, die heruntergeladen wurde, damit ein Benutzer von Microsoft Outlook auf das Adressbuch zugreifen kann, wenn keine Verbindung zum Server besteht. Microsoft Exchange generiert die neuen OAB-Dateien, komprimiert die Dateien und speichert die Dateien dann auf einer lokalen Freigabe. Sie können entscheiden, welche Adresslisten Benutzern zur Verfügung gestellt werden, die offline arbeiten, und auch die Methode konfigurieren, mit der die Adressbücher verteilt werden.

Weitere Informationen zu Adresslisten finden Sie unter [Adresslisten](address-lists-exchange-2013-help.md).


> [!IMPORTANT]
> OAB-Daten werden durch den Microsoft Exchange OABGen-Dienst generiert, einen Postfach-Assistenten. Wenn Sie die Sicherheitsbeschreibung verwenden, um zu verhindern, dass Benutzer bestimmte Empfänger in Active Directory sehen, können Benutzer, die das OAB herunterladen, diese verborgenen Empfänger anzeigen. Um also einen Empfänger in einer Adressliste auszublenden, legen Sie in den Cmdlets <A href="https://technet.microsoft.com/de-de/library/aa998596(v=exchg.150)">Set-PublicFolder</A>, <A href="https://technet.microsoft.com/de-de/library/aa995950(v=exchg.150)">Set-MailContact</A>, <A href="https://technet.microsoft.com/de-de/library/aa995971(v=exchg.150)">Set-MailUser</A>, <A href="https://technet.microsoft.com/de-de/library/bb123796(v=exchg.150)">Set-DynamicDistributionGroup</A>, <A href="https://technet.microsoft.com/de-de/library/bb123981(v=exchg.150)">Set-Mailbox</A> und <A href="https://technet.microsoft.com/de-de/library/bb124955(v=exchg.150)">Set-DistributionGroup</A> den Parameter <EM>HiddenFromAddressListsEnabled</EM> fest. Alternativ können Sie ein neues Standard-OAB erstellen, das den verborgenen Empfänger nicht enthält. Weitere Details zum Hinzufügen oder Entfernen von Adresslisten aus einem OAB finden Sie unter <A href="https://docs.microsoft.com/de-de/exchange/address-books/offline-address-books/add-or-remove-an-address-list">Hinzufügen einer Adressliste zu oder Entfernen einer Adressliste aus einem Offlineadressbuch</A>.



Möchten Sie wissen, welche Verwaltungsaufgaben es im Zusammenhang mit Offlineadressbüchern gibt? Weitere Informationen finden Sie unter [Verfahren für Offlineadressbücher](offline-address-book-procedures-exchange-2013-help.md).

**Inhalt**

Verschieben von OABs zwischen Exchange-Versionen

OAB Version 4 und Outlook-Clients

Webbasierte Verteilung

Überlegungen zu OABs

## Verschieben von OABs zwischen Exchange-Versionen

In Exchange 2007 und Exchange 2010 wurde das Cmdlet **Move-OfflineAddressBook** verwendet, um die OAB-Generierung auf einen anderen Postfachserver zu verlagern. Exchange 2013 unterstützt nur OAB (Version 4). Dies ist die gleiche OAB-Version, die standardmäßig in Exchange 2010 verwendet wurde. In Exchange 2013 können keine anderen OAB-Versionen generiert werden, und die OAB-Generierung erfolgt auf dem Postfachserver, auf dem sich das Organisationspostfach befindet. Daher müssen Sie in Exchange 2013 das Organisationspostfach verschieben, um die OAB-Generierung zu verlagern. Sie können die OAB-Generierung nur in eine andere Exchange 2013-Postfachdatenbank verlagern. Die OAB-Generierung kann nicht in eine Version von Exchange verlagert werden. Führen Sie folgenden Shell-Befehl aus, um das Exchange 2013-Organisationspostfach zu finden:

    Get-Mailbox -Arbitration | where {$_.PersistedCapabilities -like "*oab*"}

Anschließend können Sie das Cmdlet **MoveRequest**, verwenden, um das Postfach zu verschieben.

## OAB Version 4 und Outlook-Clients

Exchange 2013 unterstützt nur OAB Version 4. Diese Version wurde in Exchange 2003 Service Pack 2 (SP2) eingeführt und wird von Outlook 2007, Outlook 2010 und Outlook 2013 unterstützt. Dieses OAB im Unicode-Format ermöglicht Clientcomputern den Empfang von differenziellen Updates anstelle von vollständigen OABs und somit eine geringere Dateigröße.

## Outlook-Clients, die OAB Version 4 verwenden

Für Outlook 2013-, Outlook 2010- und Outlook 2007-Clients, die OAB Version 4 verwenden, löst Outlook einen vollständigen OAB-Download aus, falls die Größe der Datei **Changes.oab** mindestens der Hälfte der Größe der gesamten OAB-Dateien entspricht.

## Webbasierte Verteilung

Die *webbasierte Verteilung* ist die Verteilungsmethode, mit deren Hilfe Outlook 2013-, Outlook 2010- oder Outlook 2007-Benutzer, die offline arbeiten, auf das OAB zugreifen können.

Die Verwendung der webbasierten Verteilung weist verschiedene Vorteile auf, einschließlich:

  - Unterstützung einer größeren Anzahl gleichzeitiger Clientcomputer.

  - Verringerung der Bandbreitennutzung.

  - Umfassendere Kontrolle über die OAB-Verteilungspunkte. Bei der webbasierten Verteilung ist der Verteilungspunkt die HTTPS-Webadresse, an der die Clientcomputer das OAB herunterladen können.

Damit die webbasierte Verteilung optimal genutzt werden kann, muss auf den Clientcomputern Outlook 2013, Outlook 2010 oder Outlook 2007 ausgeführt werden.

Die ordnungsgemäße Funktion der webbasierten Verteilung ist von den folgenden Komponenten abhängig:

  - **OAB-Generierung**   Dies ist der Prozess, durch den das OAB von Exchange erstellt und aktualisiert wird. Zum Erstellen und Aktualisieren des OAB wird der OABGen-Dienst auf dem Postfachserver ausgeführt, auf dem sich auch das Organisationspostfach befindet. Damit die OAB-Verteilung unterstützt wird, muss der Server ein Exchange-Postfachserver sein.

  - **OAB-Verteilung**   Wenn ein Client die OAB-Verteilungsanforderung auslöst, wird diese Anforderung durch einen Clientzugriffsserver geleitet. Der Clientzugriffsserver leitet die Anforderung an den Postfachserver weiter, der die OAB-Dateien hostet. Die OAB-Dateien werden anschließend direkt vom Postfachserver an den Client verteilt.

  - **Virtuelles OAB-Verzeichnis**   Das virtuelle OAB-Verzeichnis ist der Verteilungspunkt, der von der webbasierten Verteilungsmethode verwendet wird. Bei der Installation von Exchange wird standardmäßig ein neues virtuelles Verzeichnis mit dem Namen **OAB** in der internen Standardwebsite von IIS (Internetinformationsdienste) erstellt. Wenn clientseitige Benutzer außerhalb der Firewall Ihrer Organisation eine Verbindung mit Outlook herstellen, können Sie eine externe Website hinzufügen. Alternativ dazu wird ein neues virtuelles Verzeichnis mit dem Namen "OAB" auf der IIS-Standardwebsite auf dem lokalen Exchange-Clientzugriffsserver erstellt, wenn Sie das Cmdlet **New-OABVirtualDirectory** in der Shell ausführen. Informationen finden Sie unter [Erstellen eines virtuellen Offlineadressbuch-Verzeichnisses](create-an-offline-address-book-virtual-directory-exchange-2013-help.md).

  - **AutoErmittlungsdienst**   Dies ist eine Funktion, die in Outlook 2013, Outlook 2010 oder Outlook 2007 sowie einigen mobilen Geräten zur Verfügung steht und Clients automatisch für den Zugriff auf Exchange konfiguriert. Der Dienst wird auf einem Clientzugriffsserver ausgeführt und gibt die richtige OAB URL für eine bestimmte Clientverbindung zurück.

## Überlegungen zu OABs

Berücksichtigen Sie als bewährte Methode die folgenden Faktoren beim Planen und Implementieren der OAB-Strategie, unabhängig davon, ob Sie ein einzelnes oder mehrere OABs verwenden:

  - Die Größe der einzelnen OABs im Unternehmen. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt Überlegungen zur OAB-Größe.

  - Die Anzahl der OAB-Downloads.

  - Die Anzahl und die Häufigkeit von übergeordneten DN-Änderungen (Distinguished Name).

  - SMTP-Adressenkonflikte.

  - Die Gesamtanzahl von Änderungen, die am Verzeichnis vorgenommen wurden.

## Überlegungen zur OAB-Größe

Bei einigen Unternehmen ist das OAB eine kleine Datei, die gelegentlich von Remotebenutzern heruntergeladen wird. Für diese Unternehmen ist das Herunterladen des OABs normalerweise nicht von Bedeutung. Für einige große Unternehmen mit umfassenden Verzeichnissen oder für Unternehmen, die Outlook 2003 im Exchange-Cachemodus bereitgestellt haben, kann dies von Bedeutung sein, insbesondere, wenn die Unternehmen Exchange-Server in einem regionalen Datencenter zusammengefasst haben.

Die Größe der OABs kann zwischen einigen Megabyte und mehreren hundert Megabyte variieren. Folgende Faktoren können die Größe des OABs beeinflussen:

  - Die Verwendung von Zertifikaten im Unternehmen. Je mehr PKI-Zertifikate (Public-Key-Infrastruktur) verwendet werden, desto größer ist das OAB. PKI-Zertifikate sind zwischen 1 KB und 3 KB groß. Sie haben den größten Einzelanteil an der Größe des OABs.

  - Die Anzahl der E-Mail-Empfänger in Active Directory.

  - Die Anzahl der Verteilergruppen in Active Directory.

  - Die Informationen, die ein Unternehmen für jedes postfachaktivierte oder E-Mail-aktivierte Objekt zu Active Directory hinzufügt. Einige Organisationen füllen beispielsweise die Adresseigenschaften für jeden Benutzer aus, während andere diese auslassen.

