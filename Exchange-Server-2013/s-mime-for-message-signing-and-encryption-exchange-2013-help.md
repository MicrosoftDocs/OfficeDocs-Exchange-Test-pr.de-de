---
title: 'S/MIME für die Nachrichtensignierung und -verschlüsselung: Exchange 2013 Help'
TOCTitle: S/MIME für die Nachrichtensignierung und -verschlüsselung
ms:assetid: 887c710b-0ec6-4ff0-8065-5f05f74afef3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn626158(v=EXCHG.150)
ms:contentKeyID: 61212666
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# S/MIME für die Nachrichtensignierung und -verschlüsselung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

S/MIME (Secure/Multipurpose Internet Mail Extensions) ist eine weitgehend akzeptierte Methode, genauer gesagt ein Protokoll, zum Senden digital signierter und verschlüsselter Nachrichten. S/MIME ermöglicht Ihnen das Verschlüsseln und digitale Signieren von E-Mails. Wenn Sie S/MIME mit einer E-Mail verwenden, können die Empfänger sicher sein, dass sie genau die Nachricht im Postfach haben, die der Absender abgeschickt hat. Zudem können Empfänger von Nachrichten sicher sein, dass die Nachricht von dem spezifischen Absender stammt und nicht von jemanden, der vorgibt, der Absender zu sein. Dafür bietet S/MIME kryptografische Sicherheitsdienste, wie Authentifizierung, Nachrichtenintegrität und Ursprungszulassung (anhand von digitalen Signaturen). Es sorgt auch für mehr Datenschutz und -sicherheit (anhand von Verschlüsselung) für die elektronische Nachrichtenübermittlung. Genauere Hintergrundinformationen zur Geschichte und Architektur von S/MIME im Kontext von E-Mails finden Sie unter [Informationen zu S/MIME](https://go.microsoft.com/fwlink/?linkid=393948).

Als Administrator können Sie S/MIME-basierte Sicherheit für Ihre Organisation aktivieren, wenn Sie Postfächer in Exchange 2013 SP1 oder Exchange Online, einem Teil von Office 365, besitzen. Anhand der Anleitungen in den verknüpften Themen und der Exchange-Verwaltungsshell können Sie S/MIME einrichten. Damit sie S/MIME in unterstützten Versionen von Outlook oder ActiveSync mit Exchange 2013 SP1 oder Exchange Online verwenden können, müssen die Benutzer in Ihrer Organisation Zertifikate besitzen, die zu Signierungs- und Verschlüsselungszwecken ausgestellt werden, und über Daten verfügen, die über Ihren lokalen Active Directory-Domänendienst (Active Directory Domain Service, AD DS) veröffentlicht werden. Ihr AD DS muss sich auf Computern an einem von Ihnen gesteuerten physischen Ort befinden, und nicht an einem Remote-Standort oder in einem cloudbasierten Dienst irgendwo im Internet. Weitere Informationen über AD DS finden Sie unter [Active Directory-Domänendienste](https://go.microsoft.com/fwlink/?linkid=394064).

## Unterstützte Szenarien und technische Aspekte

Wenn Ihre Organisation Exchange 2013 SP1 oder Exchange Online nutzt, können Sie S/MIME für die folgenden Endpunkte einrichten:

  - Outlook 2010

  - Outlook 2013

  - Outlook Web App

  - Exchange ActiveSync (EAS)

Die Schritte für die Einrichtung von S/MIME für die verschiedenen Endpunkte unterscheiden sich je nach Endpunkt leicht. In der Regel müssen Sie die folgenden Aktionen ausführen:

  - Installieren eine Windows-basierte Zertifizierungsstelle, und richten Sie eine öffentliche Schlüsselinfrastruktur zum Ausstellen von S/MIME-Zertifikaten ein. Durch Drittanbieter-Zertifikatsanbieter ausgestellte Zertifikate werden nicht unterstützt. Details finden Sie unter [Active Directory-Zertifikatdienste: Übersicht](https://technet.microsoft.com/library/hh831740.aspx).

  - Veröffentlichen des Benutzerzertifikats in einem lokalen AD DS-Konto in den Attributen "UserSMIMECertificate" und/oder "UserCertificate".

  - Bei Exchange Online-Organisationen: Synchronisieren der Benutzerzertifikate aus AD DS nach Azure Active Directory unter Verwendung einer geeigneten Version von DirSync. Diese Zertifikate werden aus Azure Active Directory nach Exchange Online Directory synchronisiert und beim Verschlüsseln einer Nachricht an einen Empfänger verwendet.

  - Einrichten einer virtuellen Zertifikatauflistung zum Validieren von S/MIME. Diese Informationen verwendet OWA beim Validieren der Signatur einer E-Mail und Sicherstellen, dass sie von einem vertrauenswürdigen Zertifikat signiert wurde.

  - Einrichten des Outlook- oder EAS-Endpunkts für die Verwendung von S/MIME.

## Einrichten von S/MIME mit Outlook Web App

Das Einrichten von S/MIME für Exchange 2013 SP1 oder Exchange Online mit Outlook Web App umfasst die folgenden Schritte:

1.  [Konfigurieren von S/MIME-Einstellungen für Outlook Web App](configure-s-mime-settings-for-outlook-web-app-exchange-2013-help.md)

2.  [Einrichten einer virtuellen Zertifikatauflistung für die Überprüfung von S/MIME](set-up-virtual-certificate-collection-to-validate-s-mime-exchange-2013-help.md)

3.  [Synchronisierung von Benutzerzertifikaten nach Office 365 für S/MIME](https://technet.microsoft.com/de-de/library/dn626159\(v=exchg.150\)) Dieser Schritt gilt nur für Exchange Online.

## Zugehörige Nachrichten-Verschlüsselungstechnologien

Da die Nachrichtensicherheit einen immer größeren Stellenwert einnimmt, müssen Administratoren die Prinzipien und Konzepte eines sicheren Messaging verstehen. Dieses Verständnis ist aufgrund der zunehmenden Zahl an verfügbaren sicherheitsbezogenen Technologien, wie etwa S/MIME, von besonderer Wichtigkeit. Weitere Informationen zu S/MIME und seiner Funktionsweise im Kontext von E-Mails finden Sie unter [Informationen zu S/MIME](https://go.microsoft.com/fwlink/?linkid=393948). Eine Vielzahl von Verschlüsselungstechnologien arbeiten im Verbund zusammen, um sowohl im Postfach gespeicherte Nachrichten als auch Nachrichten während des Übertragungsvorgangs zu schützen. S/MIME kann gleichzeitig mit den folgenden Technologien zusammenarbeiten, ist aber nicht von diesen abhängig:

  -  
    **Transport Layer Security (TLS)** verschlüsselt den Tunnel oder die Route zwischen E-Mail-Servern, um ein Ausspionieren oder Ausspähen zu verhindern.

  -  
    **Secure Sockets Layer (SSL)** verschlüsselt die Verbindung zwischen E-Mail-Clients und Office 365-Servern.

  -  
    **BitLocker** verschlüsselt die Daten auf den Festplatten in einem Datacenter, so dass Personen, die sich unbefugt Zugang verschaffen, die Daten dennoch nicht lesen können.

## S/MIME-im Vergleich zur Office 365-Nachrichtenverschlüsselung

Für S/MIME ist eine Infrastruktur für Zertifikate und Veröffentlichungen erforderlich, die häufig in B2B(Business-to-Business)- und B2C(Business-to-Customer)-Situationen verwendet wird. Der Benutzer steuert die kryptografischen Schlüssel in S/MIME und kann wählen, ob sie für jede versendete Nachricht verwendet werden sollen. E-Mail-Programme wie Outlook suchen nach dem Ort einer vertrauenswürdigen Stammzertifizierungsstelle, um eine digitale Signatur vorzunehmen und diese Signatur zu überprüfen. Die Office 365-Nachrichtenverschlüsselung ist ein richtlinienbasierter Verschlüsselungsdienst, der von einem Administrator, und nicht von einem individuellen Benutzer, konfiguriert werden kann, um an Personen inner- und außerhalb des Unternehmens gesendete E-Mails zu verschlüsseln. Es handelt sich um einen Onlinedienst, der auf der Azure-Rechteverwaltung (RMS) basiert und nicht auf eine PKI angewiesen ist. Die Office 365-Nachrichtenverschlüsselung bietet auch zusätzliche Funktionen, wie beispielsweise die Möglichkeit zur Anpassung der E-Mail mit der Marke der Organisation. Weitere Informationen zur Office 365-Nachrichtenverschlüsselung finden Sie unter [Office 365-Nachrichtenverschlüsselung](https://go.microsoft.com/fwlink/?linkid=392525).

## Weitere Informationen

[Outlook Web App](outlook-web-app-exchange-2013-help.md)

[Secure Mail (2000)](https://technet.microsoft.com/de-de/library/cc962043.aspx)

