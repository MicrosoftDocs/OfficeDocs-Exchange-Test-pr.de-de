---
title: 'Mobile Geräte: Exchange 2013 Help'
TOCTitle: Mobile Geräte
ms:assetid: 93a949e7-b3ef-43ea-ae0c-6698826fc8d2
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232129(v=EXCHG.150)
ms:contentKeyID: 50476255
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Mobile Geräte

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-09-24_

Mit mobilen Geräten, die für MicrosoftExchange ActiveSync aktiviert sind, können Benutzer jederzeit und von jedem beliebigen Ort aus auf einen Großteil ihrer Microsoft Exchange-Postfachdaten zugreifen. Es gibt viele verschiedene Mobiltelefone und mobile Geräte, die für Exchange ActiveSync aktiviert sind. Hierzu gehören Windows Phone, Mobiltelefone von Nokia, Android-Mobiltelefone und -Tablets sowie Apple iPhone, iPod und iPad.

Während sowohl Mobiltelefone als auch andere mobile Geräte Exchange ActiveSync unterstützen, verwenden wir in der Dokumentation zu Exchange ActiveSync meist den Begriff *mobiles Gerät*. Sofern die erläuterte Funktion kein Mobiltelefonsignal erfordert, z. B. eine SMS-Benachrichtigung, bezeichnet der Begriff "mobiles Gerät" sowohl Mobiltelefone als auch sonstige mobile Geräte, wie Tablets.

## Exchange ActiveSync

Exchange ActiveSync ist ein Kommunikationsprotokoll, das drahtlosen mobilen Zugriff auf E-Mail-Nachrichten, Zeitplanungsdaten, Kontakte und Aufgaben ermöglicht. Exchange ActiveSync ist für Windows Phone sowie für Mobiltelefone von Drittanbietern verfügbar, die für Exchange ActiveSync aktiviert sind.

Exchange ActiveSync bietet Direct Push-Technologie. Direct Push verwendet eine verschlüsselte HTTPS-Verbindung, die von dem mobilen Gerät zum Server hergestellt und aufrechterhalten wird, sodass neue E-Mail-Nachrichten und sonstige Exchange-Daten mithilfe der Push-Funktion auf das Mobiltelefon übertragen werden können.

Um Direct Push mit MicrosoftExchange Server 2013 verwenden zu können, müssen die Benutzer über ein mobiles Gerät verfügen, dessen Entwurf Direct Push unterstützt.

## Exchange ActiveSync-Funktionen

Exchange ActiveSync bietet Zugriff auf viele unterschiedliche Funktionen, mit denen Sie Sicherheitsrichtlinien für mobile Geräte erzwingen können. Mithilfe von Exchange 2013 können Sie mehrere Postfachrichtlinien für mobile Geräte konfigurieren und steuern, welche mobilen Geräte mit dem Exchange-Server synchronisiert werden können. Exchange ActiveSync ermöglicht es, einen Befehl zur Remotegerätzurücksetzung zu senden, der sämtliche Daten von einem mobilen Gerät entfernt, falls das mobile Geräte verloren geht oder gestohlen wird. Benutzer können eine Remotegerätzurücksetzung auch über Outlook Web App initiieren.

Exchange ActiveSync ermöglicht es Benutzern, ein Wiederherstellungskennwort zu generieren. Dieses Wiederherstellungskennwort wird auf dem mobilen Gerät gespeichert und verwendet, wenn ein Benutzer sein Kennwort vergessen hat. Der Benutzer generiert das Wiederherstellungskennwort zu dem Zeitpunkt, zu dem er auch das Gerätekennwort oder die PIN generiert. Dieses Wiederherstellungskennwort kann zum Entsperren des mobilen Geräts verwendet werden. Unmittelbar nachdem dieses Wiederherstellungskennwort verwendet wurde, muss der Benutzer eine neue PIN erstellen.

## POP3 und IMAP4

Wenn Ihr mobiles Gerät Exchange ActiveSync nicht unterstützt oder wenn Sie die umfangreichen Funktionen von Exchange ActiveSync nicht benötigen, können Sie über POP3 oder IMAP4 auf Ihre E-Mails auf dem mobilen Gerät zugreifen. Weitere Informationen zum Zugriff auf Ihr Postfach über POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

