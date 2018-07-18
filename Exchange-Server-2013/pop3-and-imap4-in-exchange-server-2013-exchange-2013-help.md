---
title: 'POP3 und IMAP4 in Exchange Server 2013: Exchange 2013 Help'
TOCTitle: POP3 und IMAP4
ms:assetid: a7dc91ee-2919-4db3-ae9c-cd665d2e09ea
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657728(v=EXCHG.150)
ms:contentKeyID: 50476393
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# POP3 und IMAP4 in Exchange Server 2013

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-08-16_

Dieser Artikel enthält Informationen zu Unterschieden zwischen POP3- und IMAP4-Protokollen in Exchange Server 2013 und zum Konfigurieren von Optionen für den Zugriff auf Exchange 2013-Postfächer über verschiedene E-Mail-Programme.

Standardmäßig sind POP3 und IMAP4 in Exchange Server 2013 deaktiviert. Zur Unterstützung von POP3-Clients, die weiterhin diese Protokolle voraussetzen, müssen Sie zwei POP3-Dienste starten: den Microsoft Exchange-POP3-Dienst und den Microsoft Exchange-POP3-Back-End-Dienst. Zur Unterstützung von IMAP4-Clients, die weiterhin diese Protokolle voraussetzen, müssen Sie zwei IMAP4-Dienste starten: den Microsoft Exchange-IMAP4-Dienst und den Microsoft Exchange-IMAP4-Back-End-Dienst.

Genaue Anweisungen zum Aktivieren des POP3- und IMAP4-Diensts finden Sie unter [Aktivieren von POP3 in Exchange 2013](enable-pop3-in-exchange-2013-exchange-2013-help.md) und [Aktivieren von IMAP4 in Exchange 2016](enable-imap4-in-exchange-2013-exchange-2013-help.md).

Standardmäßig können Benutzer, die Postfächer auf Computern mit Exchange 2013 haben, über Outlook oder Outlook Web App, Exchange ActiveSync oder Outlook Voice Access auf ihre Postfächer zugreifen. Outlook, Outlook Web App und Outlook Voice Access ermöglichen Ihren E-Mail-Benutzern das Verwenden der umfassenden Features, die Benutzern bereitstehen, die über Postfächer auf Exchange 2016-Servern verfügen.

**Inhalt**

Übersicht über die Funktionalität von POP3 und IMAP4

Standortübergreifende Konnektivität mit POP3 und IMAP4

Verwenden nicht standardmäßiger Konten mit POP3 und IMAP4

Grundlegendes zu den Unterschieden zwischen POP3 und IMAP4

Sende- und Empfangsoptionen für POP3- und IMAP4-E-Mail-Anwendungen

POP3- und IMAP4-Anwendungen

Benutzereinstellungen zum Konfigurieren des POP3- oder IMAP4-Zugriffs auf Exchange 2013-Postfächer

## Übersicht über die Funktionalität von POP3 und IMAP4

In diesem Abschnitt wird die Funktionalität von POP3 und IMAP4 für Exchange 2013 beschrieben.

Das POP3- und das IMAP4-Protokoll weisen folgende Vorteile und Einschränkungen auf:

  - **POP3**   POP3 wurde entwickelt, um die Offlineverarbeitung von E-Mails zu unterstützen. Mit POP3 werden E-Mails vom Server entfernt und auf dem lokalen POP3-Client gespeichert, sofern der Client nicht so konfiguriert wurde, dass Nachrichten auf dem Server verbleiben. Dadurch wird die Verantwortung für die Datenverwaltung und Sicherheit auf den Benutzer übertragen. POP3 bietet keine erweiterten Funktionen für die Zusammenarbeit, wie z. B. Kalender, Kontakte und Aufgaben.

  - **IMAP4**   IMAP4 bietet sowohl Offline- als auch Onlinezugriff, doch wie POP3 bietet auch IMAP4 keine erweiterten Features für die Zusammenarbeit, wie Kalenderfunktionen, Kontakte und Aufgaben.

POP3- und IMAP4-E-Mail-Anwendungen verwenden zum Versenden von Nachrichten an den E-Mail-Server weder POP3 noch IMAP4. Sie versenden Nachrichten mit dem SMTP-Protokoll. Der Connector zum Empfangen von E-Mail-Übermittlungen von Clientanwendungen, die POP3 oder IMAP4 verwenden, wird bei der Installation von Exchange automatisch erstellt. Weitere Informationen zu Connectors finden Sie unter [Empfangsconnectors](receive-connectors-exchange-2013-help.md).


> [!NOTE]
> Immer wenn ein Benutzer ein POP- oder IMAP-basiertes E-Mail-Programm zum Öffnen seiner Office 365-E-Mail nutzt, kommt es zu einer mehrsekündigen Verzögerung. Deren Ursache ist die Verwenden eines Proxyservers, der einen weiteren Hop für die Authentifizierung hinzufügt. Der Proxyserver untersucht zunächst den zugewiesenen PoD-Sever (Clientzugriffsserver), bei dem eine Authentifizierung erfolgt.



## Standortübergreifende Konnektivität mit POP3 und IMAP4

In früheren Versionen von Exchange mussten Sie Ihre POP3- und IMAP4-Clients manuell konfigurieren, um eine Verbindungsherstellung von einem Standort in Ihrer Organisation zu ermöglichen, wenn sich die Postfächer an einem anderen Standort in Ihrer Organisation befanden. Exchange 2013 führt standardmäßig eine Proxyweiterleitung von einem Clientzugriffsserver in einem Standort an den richtigen Server aus.

## Verwenden nicht standardmäßiger Konten mit POP3 und IMAP4

Sie können sich nicht mithilfe des anonymen Kontos oder des Kontos „Gast“ über POP3 oder IMAP4 bei einem Exchange 2016-Postfach anmelden. Anonyme Konten werden aufgrund von Sicherheitsrisiken bei der Verwendung nicht standardmäßiger Konten für den POP3- und IMAP4-Zugriff blockiert. Darüber hinaus können Sie über POP3 oder IMAP4 keine Verbindung mit dem Administratorpostfach herstellen. Diese Einschränkung wurde in Exchange 2013 eingeführt, um die Sicherheit für das Administratorpostfach zu erhöhen. Um auf das Administratorpostfach zuzugreifen, müssen Sie Outlook oder Outlook Web App verwenden.

## Grundlegendes zu den Unterschieden zwischen POP3 und IMAP4

**POP3** POP3 ist ein häufig verwendetes E-Mail-Internetprotokoll. Wenn POP3-E-Mail-Anwendungen E-Mails auf einen Clientcomputer herunterladen, werden die heruntergeladenen Nachrichten standardmäßig vom Server entfernt. Wenn keine Kopien der E-Mails des Benutzers auf dem E-Mail-Server gespeichert werden, kann der Benutzer nicht von mehreren Computern aus auf diese E-Mails zugreifen. Einige POP3-E-Mail-Anwendungen können jedoch so konfiguriert werden, dass Kopien der Nachrichten auf dem Server gespeichert werden, damit von anderen Computern aus der Zugriff auf die E-Mails möglich ist. POP3-Clientanwendungen können nur zum Herunterladen von Nachrichten vom E-Mail-Server in einen einzigen Ordner (in der Regel in den Ordner "Posteingang") auf dem Clientcomputer verwendet werden. Das POP3-Protokoll kann nicht mehrere Ordner auf dem E-Mail-Server mit mehreren Ordnern auf dem Clientcomputer synchronisieren.

**IMAP4** E-Mail-Clientanwendungen, die IMAP4 verwenden, sind flexibler und bieten im Allgemeinen eine größere Anzahl von Features als E-Mail-Clientanwendungen, die POP3 verwenden. Wenn IMAP4-E-Mail-Anwendungen E-Mails auf einen Clientcomputer herunterladen, verbleibt standardmäßig eine Kopie der heruntergeladenen Nachrichten auf dem E-Mail-Server. Da eine Kopie der E-Mails des Benutzers auf dem E-Mail-Server gespeichert wird, kann der Benutzer von mehreren Computern aus auf diese E-Mails zugreifen. Bei Verwendung von IMAP4 kann der Benutzer auf mehrere E-Mail-Ordner auf dem E-Mail-Server zugreifen bzw. mehrere dieser Ordner erstellen. Die Benutzer können dann auf alle Nachrichten auf dem Server von Computern an mehreren Standorten aus zugreifen. Die meisten IMAP4-Anwendungen können z. B. so konfiguriert werden, dass eine Kopie der gesendeten Elemente des Benutzers auf dem Server verbleibt, damit die gesendeten Elemente auf einem beliebigen anderen Computer angezeigt werden können. IMAP4 unterstützt zusätzliche Funktionen, die von den meisten IMAP4-Anwendungen unterstützt werden. Einige IMAP4-Anwendungen enthalten z. B. ein Feature, mithilfe dessen Benutzer nur die Kopfzeilen ihrer E-Mails (Absender und Betreff der Nachricht) auf dem Server anzeigen und anschließend nur die Nachrichten herunterladen können, die sie lesen möchten. IMAP4 unterstützt außerdem keinen Zugriff auf öffentliche Ordner.


> [!NOTE]
> IMAP4- und POP3-Clients haben eingeschränkten Zugriff auf Kalenderinformationen für Exchange. Weitere Informationen finden Sie unter <A href="configure-calendar-options-for-pop3-exchange-2013-help.md">Konfigurieren von Kalenderoptionen für POP3</A> und <A href="configure-calendar-options-for-imap4-exchange-2013-help.md">Konfigurieren von Kalenderoptionen für IMAP4</A>.



## Sende- und Empfangsoptionen für POP3- und IMAP4-E-Mail-Anwendungen

Mit POP3- und IMAP4-E-Mail-Anwendungen können Benutzer auswählen, wann eine Verbindung mit dem Server zum Senden und Empfangen von E-Mails hergestellt werden soll. In diesem Abschnitt werden einige der gängigsten Konnektivitätsoptionen behandelt. Außerdem werden einige Aspekte erläutert, die Ihre Benutzer beim Auswählen der Verbindungsoptionen in ihren POP3- und IMAP4-E-Mail-Anwendungen berücksichtigen sollten.

## Allgemeine Konfigurationseinstellungen

Drei der am häufigsten verwendeten Verbindungseinstellungen können wie folgt für eine POP3- oder IMAP4-Clientanwendung festgelegt werden:

  - Bei jedem Start der E-Mail-Anwendung Nachrichten senden und empfangen. Bei Verwendung dieser Option werden Nachrichten nur beim Start der E-Mail-Anwendung gesendet und empfangen.

  - Nachrichten manuell senden und empfangen. Bei Verwendung dieser Option werden Nachrichten nur dann gesendet und empfangen, wenn der Benutzer auf den Befehl „Senden und Empfangen“ in der Clientbenutzeroberfläche klickt.

  - Nachrichten immer nach einer festgelegten Anzahl von Minuten senden und empfangen. Bei Verwendung dieser Option stellt die Clientanwendung immer nach Ablauf eines in Minuten festgelegten Zeitraums eine Verbindung mit dem Server her, um Nachrichten zu senden und neue Nachrichten herunterzuladen.

Informationen zum Konfigurieren dieser Einstellungen für die von Ihnen verwendete E-Mail-Anwendung finden Sie in der Hilfedokumentation zur jeweiligen E-Mail-Anwendung.

## Überlegungen bei der Auswahl von Sende- und Empfangsoptionen

Wenn das Gerät oder der Computer, auf dem eine POP3- oder IMAP4-E-Mail-Anwendung ausgeführt wird, immer mit dem Internet verbunden ist, möchten Benutzer ihre E-Mail-Anwendung ggf. so konfigurieren, dass Nachrichten in einem festgelegten Minutenintervall gesendet und empfangen werden. Durch regelmäßige Verbindungen mit dem Server wird sichergestellt, dass die E-Mail-Anwendung des Benutzers mit den neuen Informationen auf dem Server aktualisiert wird. Wenn das Gerät oder der Computer, auf dem eine POP3- oder IMAP4-E-Mail-Anwendung ausgeführt wird, nicht immer mit dem Internet verbunden ist, möchten Benutzer ihre E-Mail-Anwendung ggf. so konfigurieren, dass Nachrichten manuell gesendet und abgerufen werden.


> [!NOTE]
> Wenn der Benutzer eine mit IMAP4 kompatible E-Mail-Anwendung verwendet, die den Befehl "IMAP4 IDLE" unterstützt, ist er ggf. in der Lage, E-Mails nahezu in Echtzeit an das Exchange-Postfach zu senden und von diesem zu empfangen. Damit diese Verbindungsmethode funktioniert, müssen sowohl die E-Mail-Server- als auch die Clientanwendung den Befehl "IMAP4 IDLE" unterstützen. In den meisten Fällen müssen Benutzer keine Einstellungen in ihrer IMAP4-Anwendung konfigurieren, um diese Verbindungsmethode verwenden zu können.



## POP3- und IMAP4-Anwendungen

Da Exchange 2013 POP3 und IMAP4 unterstützt, können Benutzer jede Anwendung, die POP3- und IMAP4-Clientanwendungen unterstützt, dazu verwenden, eine Verbindung mit Exchange 2013 herzustellen. Zu diesen Anwendungen zählen Outlook, Outlook Web App, Windows Live Mail, Outlook Express, Entourage und zahlreiche Anwendungen von Drittanbietern, wie Google Mail, Mozilla Thunderbird und Eudora. Die von den einzelnen E-Mail-Clientanwendungen unterstützten Features variieren. Informationen zu den jeweiligen Funktionen, die von bestimmten POP3- und IMAP4-Clientanwendungen zur Verfügung gestellt werden, finden Sie in der jeweiligen Dokumentation zur betreffenden Anwendung.

## Benutzereinstellungen zum Konfigurieren des POP3- oder IMAP4-Zugriffs auf Exchange 2013-Postfächer

Nachdem Sie den POP3- und IMAP4-Clientzugriff aktiviert haben, müssen Sie die Benutzer darüber informieren, wie sie sich über die von ihnen verwendeten E-Mail-Programme mit ihrem Exchange 2016-Postfach verbinden können.

Soll eine Verbindung aus dem Unternehmensnetzwerk hergestellt werden, benötigen Benutzer die folgenden Informationen:

  - Interner Name des POP3- oder IMAP4-Servers

  - Interne Nummer des POP3- oder IMAP4-Ports

  - Interne POP3- oder IMAP4-Verschlüsselungsmethode

  - Interner SMTP-Name (Ausgangsserver)

  - Interne SMTP-Portnummer (Ausgangsserver)

  - Interne SMTP-Verschlüsselungsmethode (Ausgangsserver)

Soll eine Verbindung aus dem Internet hergestellt werden, benötigen Benutzer die folgenden Informationen:

  - Externer Name des POP3- oder IMAP4-Servers

  - Externe Nummer des POP3- oder IMAP4-Ports

  - Externe POP3- oder IMAP4-Verschlüsselungsmethode

  - Externer SMTP-Name (Ausgangsserver)

  - Externe SMTP-Portnummer (Ausgangsserver)

  - Externe SMTP-Verschlüsselungsmethode (Ausgangsserver)

Diese Einstellungen können Sie den Benutzern über E-Mail oder andere manuelle Kommunikationsmethoden bereitstellen. Sie können außerdem Exchange so konfigurieren, dass Benutzer mithilfe von Outlook Web App ihre eigenen Einstellungen nachschlagen können.

**Konfigurieren von Exchange, sodass Benutzer ihre POP3-, IMAP4- und SMTP-Servereinstellungen nachschlagen können**

Standardmäßig ist es Benutzern nicht möglich, über Outlook Web App ihre POP3-, IMAP4- und SMTP-Servereinstellungen nachzuschlagen. Damit Benutzer diese nachschlagen können, müssen die **Set-PopSettings**- und **Set-ImapSettings**-Cmdlets verwendet werden. Damit Benutzer ihre (ausgehenden) SMTP-Servereinstellungen nachschlagen können, muss das **Set-ReceiveConnector**-Cmdlet verwendet werden.

Gehen Sie wie folgt vor, damit es Benutzern möglich ist, ihre POP3-, IMAP4- und SMTP-Einstellungen nachzuschlagen:

  - **POP3-Einstellungen**   Führen Sie das **Set-POPSettings**-Cmdlet mit dem *ExternalConnectionSettings*-Parameter aus. Verwenden Sie das Format `Set-POPSettings -ExternalConnectionSetting {<FQDN>:995:SSL}`. Führen Sie beispielsweise `Set-PopSettings -ExternalConnectionSetting {Dublin01.Contoso.com:995:SSL}` aus, wenn Clients, die sich mit dem FQDN „Dublin01.Contoso.com“ mit dem Server verbinden, das Nachschlagen ihrer POP-Einstellungen möglich sein soll.
    
    Sie müssen IIS nach dem Anwenden dieser Einstellung neu starten.

  - **IMAP4-Einstellungen**   Führen Sie das **Set-IMAPSettings**-Cmdlet mit dem *ExternalConnectionSettings*-Parameter aus. Verwenden Sie das Format `Set-ImapSettings -ExternalConnectionSetting {<FQDN>:993:SSL}`. Führen Sie beispielsweise `Set-IMAPSettings -ExternalConnectionSetting {Dublin01.Contoso.com:993:SSL}` aus, wenn Clients, die sich mit dem FQDN „Dublin01.Contoso.com“ mit dem Server verbinden, das Nachschlagen ihrer IMAP-Einstellungen möglich sein soll.
    
    Sie müssen IIS nach dem Anwenden dieser Einstellung neu starten.

  - **SMTP-Einstellungen**   Führen Sie das **Set-ReceiveConnector**-Cmdlet mit dem *AdvertiseClientSettings*-Parameter aus. Verwenden Sie das Format `Set-ReceiveConnector "Client Frontend <Server Name>" -AdvertiseClientSettings $True -FQDN <FQDN>`. Führen Sie beispielsweise `Set-ReceiveConnector "Client Frontend <Server Name>" -AdvertiseClientSettings $True -FQDN Dublin01.Contoso.com` aus, wenn Clients, die sich mit dem FQDN „Dublin01.Contoso.com“ mit dem Server verbinden, das Nachschlagen ihrer SMTP-Einstellungen möglich sein soll.
    
    Sie müssen IIS nach dem Anwenden dieser Einstellung neu starten.

Nachdem die Standardeinstellungen durch Ausführen der Cmdlets **Set-POPSettings**, **Set-IMAPSettings** und **Set-ReceiveConnector** geändert wurden, können Benutzer ihre externen POP-, IMAP- und SMTP-Servereinstellungen in Outlook Web App durch Klicken auf **Einstellungen** \> **Optionen** \> **Konto** \> **Mein Konto** \> **Einstellungen für den Zugriff über POP oder IMAP** nachschlagen.

**Beibehalten von Nachrichtenkopien auf dem Server**

Einige E-Mail-Programme sind standardmäßig so eingestellt, dass sie nach dem Abrufen von Nachrichten die Nachrichten auf dem Server löschen. Sie sollten Ihren Benutzern unbedingt empfehlen, ihr jeweiliges E-Mail-Programm so zu konfigurieren, dass Kopien aller Nachrichten, die der Client abgerufen hat, auf dem Server beibehalten werden. Werden Nachrichtenkopien auf dem Server beibehalten, können die Benutzer aus anderen E-Mail-Programmen auf ihre Nachrichten zugreifen.

