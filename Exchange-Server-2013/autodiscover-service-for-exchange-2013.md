---
title: 'AutoErmittlungsdienst: Exchange 2013 Help'
TOCTitle: AutoErmittlungsdienst
ms:assetid: b03c0f21-cbc2-4be8-ad03-73a7dac16ffc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124251(v=EXCHG.150)
ms:contentKeyID: 50554877
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# AutoErmittlungsdienst

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Informationen zum Exchange-AutoErmittlungsdienst für Microsoft Exchange 2013. Erfahren Sie, wie der Exchange-AutoErmittlungsdienst funktioniert und welche Bereitstellungsoptionen es gibt.

MicrosoftExchange 2013 bietet einen neuen Dienst, den AutoErmittlungsdienst. Dieses Thema bietet eine Übersicht über den Dienst und Erläuterungen seiner Funktionsweise, seiner Konfiguration von Outlook-Clients und der Optionen zum Bereitstellung des AutoErmittlungsdiensts in Ihrer Nachrichtenumgebung.

Der AutoErmittlungsdienst führt die folgenden Aktionen aus:

  - Automatische Konfiguration von Benutzerprofileinstellungen für Clients mit MicrosoftOffice Outlook 2007, Outlook 2010 und Outlook 2013 sowie unterstützte Mobiltelefone. Telefone mit Windows Mobile 6.1 oder höher werden unterstützt. Wenn Ihr Telefon kein Windows Mobile-Telefon ist, prüfen Sie in der Dokumentation Ihres Mobiltelefons, ob es unterstützt wird.

  - Bereitstellung des Zugriffs auf Exchange-Funktionen für Outlook 2007-, Outlook 2010- oder Outlook 2013-Clients, die mit Ihrer Exchange-Nachrichtenumgebung verbunden sind.

  - Verwendung der E-Mail-Adresse und des Kennworts eines Benutzer, um Outlook 2007-, Outlook 2010- oder Outlook 2013-Clients und unterstützten Mobiltelefonen Profileinstellungen bereitzustellen. Wenn der Outlook-Client einer Domäne beitritt, wird das Domänenkonto des Benutzers verwendet.

**Inhalt**

Übersicht über den AutoErmittlungsdienst

Funktionsweise des AutoErmittlungsdiensts

Bereitstellungsoptionen für den AutoErmittlungsdienst

Konfigurieren der AutoErmittlung für gesamtstrukturübergreifende Verschiebevorgänge

## Übersicht über den AutoErmittlungsdienst

Der AutoErmittlungsdienst vereinfacht die Konfiguration von Outlook 2007, Outlook 2010 und Outlook 2013 sowie einiger Mobiltelefone. Der AutoErmittlungsdienst kann nicht mit Versionen von Outlook vor Office Outlook 2007 verwendet werden. In früheren Versionen von Microsoft Exchange (Exchange 2003 SP2 oder früher) und Outlook (Outlook 2003 oder früher) mussten alle Benutzerprofile manuell für den Zugriff Exchange konfiguriert werden. Die Verwaltung dieser Profile verursachte zusätzlichen Arbeitsaufwand, wenn Änderungen an der Messagingumgebung vorgenommen wurden. Andernfalls wurden die Outlook-Clients nicht mehr ordnungsgemäß ausgeführt.

Mithilfe des AutoErmittlungsdienst findet Outlook einen neuen Verbindungspunkt, der sich aus der Benutzerpostfach-GUID + @ + dem Domänenanteil der primären SMTP-Adresse des Benutzers zusammensetzt. Der AutoErmittlungsdienst gibt die folgende Informationen an den Client zurück:

  - Den Anzeigenamen des Benutzers

  - Gesonderte Verbindungseinstellungen für interne und externe Verbindungen

  - Den Speicherort des Postfachservers des Benutzers

  - Die URLs für verschiedene Outlook-Funktionen, die Funktionen wie Frei/Gebucht-Informationen, Unified Messaging und das Offlineadressbuch regeln

  - Servereinstellungen von Outlook Anywhere

Wenn die Exchange-Informationen eines Benutzers geändert werden, konfiguriert Outlook das Benutzerprofil mit dem AutoErmittlungsdienst automatisch neu. Wird beispielsweise das Postfach eines Benutzers verschoben oder kann der Client keine Verbindung zum Postfach des Benutzers bzw. zu verfügbaren Exchange-Funktionen herstellen, ruft Outlook den AutoErmittlungsdienst auf und aktualisiert das Benutzerprofil automatisch mit den Informationen, die für die Verbindung zum Postfach und zu den Exchange-Funktionen benötigt werden.

Zurück zum Seitenanfang

## Funktionsweise des AutoErmittlungsdiensts

Bei der Installation eines Clientzugriffsservers in Exchange 2013 wird standardmäßig ein virtuelles Verzeichnis mit dem Namen **Autodiscover** in der internen Standardwebsite von IIS (Internetinformationsdienste) erstellt. Dieses virtuelle Verzeichnis verarbeitet unter den folgenden Umständen Anforderungen des AutoErmittlungsdiensts von Outlook 2007-, Outlook 2010- und Outlook 2013-Clients sowie unterstützter Mobiltelefone:

  - Ein Benutzerkonto wird konfiguriert oder aktualisiert

  - Ein Outlook-Client überprüft regelmäßig, ob Änderungen der Exchange-Webdienste-URLs vorliegen

  - In Ihrer Exchange-Messagingumgebung treten Änderungen der zugrunde liegenden Netzwerkverbindung auf

Außerdem wird ein neues Active Directory-Objekt (das Dienstverbindungspunkt-Objekt) auf dem Server erstellt, auf dem Sie den Clientzugriffsserver installieren.

Das Dienstverbindungspunkt-Objekt enthält die autoritative Liste der URLs des AutoErmittlungsdiensts für die Gesamtstruktur. Sie können das Dienstverbindungspunkt-Objekt mithilfe des Cmdlets **Set-ClientAccessServer** aktualisieren. Weitere Informationen finden Sie unter [Set-ClientAccessServer](https://technet.microsoft.com/de-de/library/bb125157\(v=exchg.150\)).


> [!IMPORTANT]
> Stellen Sie vor dem Ausführen des Cmdlets <STRONG>Set-ClientAccessServer</STRONG> sicher, dass das Konto <STRONG>Authentifizierte Benutzer</STRONG> auf dem Clientzugriffsserver über Leseberechtigungen für das Dienstverbindungspunkt-Objekt verfügt. Verfügen Benutzer nicht über die ordnungsgemäßen Berechtigungen, können sie Elemente weder suchen noch lesen.



Weitere Informationen über Dienstverbindungspunkt-Objekte finden Sie auf der Website zur [Veröffentlichung mit Dienstverbindungspunkten](https://go.microsoft.com/fwlink/p/?linkid=72744).

Für den externen Zugriff oder das Verwenden von DNS nutzt der Client die primäre SMTP-Domänenadresse in der E-Mail-Adresse des Benutzers, um den AutoErmittlungsdienst im Internet zu suchen.


> [!NOTE]
> Sie müssen in DNS einen Hostservice-Ressourceneintrag (SRV) für Outlook-Clients angeben, damit der AutoErmittlungsdienst mithilfe von DNS ermittelt wird. Weitere Informationen finden Sie in Ihrer Windows-Dokumentation zur Konfiguration von DNS sowie in folgendem <A href="https://go.microsoft.com/fwlink/p/?linkid=85214">Whitepaper: AutoErmittlungsdienst in Exchange 2007</A> .



Abhängig davon, ob der AutoErmittlungsdienst auf einer separaten Website konfiguriert wurde, lautet die URL des AutoErmittlungsdiensts entweder "https://\<*SMTP-Adresse-Domäne*\>/autodiscover/autodiscover.xml" oder "https://autodiscover.\<*SMTP-Adresse-Domäne*\>/autodiscover/autodiscover.xml". Dabei ist "://\<*SMTP-Adresse-Domäne*\>" die primäre SMTP-Domänenadresse. Wenn die E-Mail-Adresse des Benutzers "tony@contoso.com" lautet, ist die primäre SMTP-Domänenadresse "contoso.com". Wenn sich der Client mit Active Directory verbindet, sucht der Client das während des Setups erstellte Dienstverbindungspunkt-Objekt. In Bereitstellungen mit mehreren Clientzugriffsservern wird für jeden Clientzugriffsserver ein Dienstverbindungspunkt-Objekt der AutoErmittlung erstellt. Das Dienstverbindungspunkt-Objekt beinhaltet das Attribut *ServiceBindingInfo*, das den vollqualifizierten Domänennamen (FQDN) des Clientzugriffsservers im Format **https://CAS01/autodiscover/autodiscover.xml** enthält. Dabei ist **CAS01** der vollqualifizierte Domänenname des Clientzugriffsservers. Mithilfe der Anmeldeinformationen führt der Outlook 2007-, Outlook 2010- oder Outlook 2013-Client die Authentifizierung bei Active Directory durch und sucht die Dienstverbindungspunkt-Objekte der AutoErmittlung. Nachdem der Client die Instanzen des AutoErmittlungsdiensts abgerufen und aufgelistet hat, stellt er eine Verbindung zum ersten Clientzugriffsserver in der Liste her und ruft die Profilinformationen als XML-Daten ab, die für die Verbindung zum Benutzerpostfach sowie zu verfügbaren Exchange-Funktionen benötigt werden.

Zurück zum Seitenanfang

## Bereitstellungsoptionen für den AutoErmittlungsdienst

Der AutoErmittlungsdienst muss ordnungsgemäß bereitgestellt und konfiguriert werden, damit Outlook 2007-, Outlook 2010- und Outlook 2013-Clients automatisch eine Verbindung mit Exchange-Funktionen wie dem Offlineadressbuch, dem Verfügbarkeitsdienst und Unified Messaging (UM) herstellen können. Das Bereitstellen des AutoErmittlungsdiensts ist nur ein Schritt, mit dem sichergestellt wird, dass Outlook 2007-, Outlook 2010- oder Outlook 2013-Clients auf Exchange-Dienste wie etwa den Verfügbarkeitsdienst zugreifen können.

## Konfigurieren der AutoErmittlung für gesamtstrukturübergreifende Verschiebevorgänge

Der AutoErmittlungsdienst kann Benutzerprofilinformationen bereitstellen, um Outlook-Clients für Postfächer zu verbinden, die aus einer Exchange-Gesamtstruktur in eine andere verschoben wurden. Hierfür müssen Sie einen für E-Mail aktivierten Benutzer sowohl in der Quellgesamtstruktur, in der sich das Postfach des Benutzers befindet, als auch in der Zielgesamtstruktur mithilfe des Cmdlets **New-MailUser** konfigurieren. In der Quellgesamtstruktur müssen Sie den Parameter *ExternalEmailAddress* im Cmdlet angeben, um die neue E-Mail-Adresse des Postfachs in der Zielgesamtstruktur anzugeben. Weitere Informationen finden Sie unter [New-MailUser](https://technet.microsoft.com/de-de/library/aa996335\(v=exchg.150\)).

Wenn Sie einen für E-Mail aktivierten Benutzer konfigurieren, leitet der AutoErmittlungsdienst in der Quellgesamtstruktur den sich authentifizierenden Benutzer an die neue E-Mail-Adresse in der Zielgesamtstruktur um. Der sich verbindende Outlook-Client wird zum Clientzugriffsserver in der Zielgesamtstruktur umgeleitet, in die das Postfach verschoben wurde.

Zurück zum Seitenanfang

