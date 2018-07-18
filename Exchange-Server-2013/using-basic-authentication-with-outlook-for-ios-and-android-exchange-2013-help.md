---
title: 'Outlook for iOS and Android: Exchange 2013 Help'
TOCTitle: Outlook for iOS and Android
ms:assetid: 3a66817c-30da-4965-a6db-2955b5365b0f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt465744(v=EXCHG.150)
ms:contentKeyID: 70061270
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Outlook for iOS and Android

 

_**Gilt für:** Exchange Server 2010, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-04-02_

**Zusammenfassung:**  Dieser Artikel richtet sich an Administratoren und enthält Architektur- sowie Sicherheitsinformationen zu Outlook für iOS und Android in einer lokalen Exchange 2013-Umgebung, wenn die App die Standardauthentifizierung verwendet.

Die Outlook-App für iOS und Android ermöglicht den Zugriff auf E-Mails, Kalender, Kontakte und andere Dateien, sodass die Benutzer in Ihrer Organisation mehr Aufgaben über ihre Mobilgeräte erledigen können. Dieser Artikel gibt einen Überblick über die Architektur und das Speicherdesign der App. Mit diesen Informationen können Exchange-Administratoren Outlook für iOS und Android in ihren Exchange-Organisationen bereitstellen und warten.

Beachten Sie, dass sich dieser Artikel auf die Verwendung der App in einer Exchange 2013-Umgebung bezieht. Weitere Informationen zur Verwendung der modernen Hybridauthentifizierung für lokale Postfächer für die App finden Sie unter [Using hybrid Modern Authentication with Outlook for iOS and Android](using-hybrid-modern-authentication-with-outlook-for-ios-and-android-exchange-2013-help.md). Informationen zur Verwendung der App mit Exchange Online finden Sie unter [Outlook für iOS und Android in Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=845477).

## Architektur von Outlook für iOS und Android

Outlook für iOS und Android besteht aus einer Front-End-App zur Installation auf Mobilgeräten sowie einem sicheren und skalierbaren Clouddienst im Back-End, genannt *Outlook-Dienst*. Dank der Auslagerung der Informationsverarbeitung an den Outlook-Dienst können erweiterte Features und Funktionen bereitgestellt werden. Damit sorgt die Architektur für eine bessere Outlook-Benutzererfahrung sowie höhere Leistung und Stabilität. Daneben reduziert die Auslagerung verarbeitungsintensiver Aufgaben an den Outlook-Dienst den Ressourcenbedarf auf den Benutzergeräten auf ein Minimum.

![Architektur der Standardauthentifizierung in Outlook für iOS und Android](images/Mt465744.f42e5af5-92fa-4d12-bf8c-994925c6084a(EXCHG.150).png "Architektur der Standardauthentifizierung in Outlook für iOS und Android")

Hier einige Vorteile, von denen Benutzer dank des Outlook-Diensts profitieren:

  - Kategorisierung für die Funktion „Posteingang mit Relevanz“

  - 1-Klick-Abmeldung von Verteilern

  - Verbesserung von Suchgeschwindigkeit und Sucheffektivität

  - Möglichkeit zur Weiterleitung und Versendung großer Dateien ohne vorherigen Download auf ein Mobilgerät

Diese Architektur unterstützt keine Features von Enterprise Mobility + Security, wie bedingter Azure Active Directory-Zugriff und Intune-App-Schutzrichtlinien.

## Zwischenspeicherung von Daten

Zur Steigerung der Leistung werden einige E-Mail-, Kalender- und Dateidaten aus den Postfächern der einzelnen Benutzer im Outlook-Dienst synchronisiert. Für lokale Postfächer, die die Standardauthentifizierung verwenden, wird dieser Dienst derzeit auf Microsoft Azure ausgeführt.

Momentan werden alle Daten im Outlook-Dienst abhängig von der IP-Adresse des verbindenden Clients in den USA oder in Europa zwischengespeichert. Im Zuge der Migration des Outlook-Diensts zu Office 365 werden wir das Angebot jedoch an die Prinzipien des Office 365 Trust Center anpassen und regionale Rechenzentren nutzen. Der primäre Speicherort der Kundendaten in Office 365 hängt davon ab, welches Land bzw. welche Region der Administrator des Kunden bei der Ersteinrichtung der Dienste angibt. Weitere Informationen finden Sie im [Office 365 Trust Center](https://go.microsoft.com/fwlink/p/?linkid=525776).

## Zwischenspeicherung von Daten: häufig gestellte Fragen

In diesem Abschnitt finden Sie häufig gestellte Fragen zur Datenspeicherung in Outlook für iOS und Android, wenn die Standardauthentifizierung verwendet wird.

## Wie viele Postfachdaten eines Benutzers werden im Outlook-Dienst synchronisiert?

Es werden in etwa die E-Mail-, Kalender- und Kontaktdaten eines Monats zwischengespeichert. Gesteuert wird die Zwischenspeicherung von einem Algorithmus, der verschiedene Faktoren berücksichtigt, unter anderem die Größe eines Postfachs, die relative Wichtigkeit eines Ordners in dem Postfach (z. B. die des Standardordners „Posteingang“ relativ zu der eines vom Benutzer erstellten Ordners) und die Häufigkeit, mit der ein Benutzer auf einen Ordner zugreift.

Für die Speicherung von Anlagendaten im Outlook-Dienst gilt: Will der Benutzer eine E-Mail-Anlage in Outlook öffnen, ruft der Dienst die Anlage vom Exchange-Server ab und speichert sie vorübergehend. Zu diesem Zeitpunkt wird die Anlage an die App auf dem Mobilgerät des Benutzers ausgeliefert. Daten, die älter als einen Monat sind, werden regelmäßig aus dem Dienst gelöscht. Die betreffenden Anlagen sind dann nur noch auf dem Exchange-Server verfügbar.

## Wie entferne ich meine Daten aus dem Outlook-Dienst?

Es gibt drei Möglichkeiten, wie Sie Ihre Daten aus dem Outlook-Dienst entfernen können.

  - Option 1: Sie initiieren eine Remotezurücksetzung für jeden Benutzer, der mit der Outlook-App für iOS und Android eine Verbindung zu Office 365 oder Exchange hergestellt hat.

  - Option 2: Sie weisen alle Benutzer an, die Outlook-App zu löschen. Dann werden innerhalb von etwa 3 bis 7 Tagen sämtliche Daten entfernt.

  - Option 3: Sie weisen alle Benutzer an, ihr Konto aus der Outlook-App zu entfernen und anschließend die App von ihrem Mobilgerät zu löschen. Benutzeranleitung zur Entfernung eines Kontos:
    
    1.  Tippen Sie in der Outlook-App unter **Einstellungen** auf **Kontoeinstellungen**.
    
    2.  Tippen Sie auf **Konto auswählen**. Ist das Konto ausgewählt, tippen Sie auf **Konto entfernen**.
    
    3.  Tippen Sie auf **Device & Remote Data**.

## Wie werden die vorübergehend im Outlook-Dienst zwischengespeicherten Postfachdaten geschützt?

Informationen dazu, wie unsere Daten aktuell geschützt werden, finden Sie im [Azure Trust Center](https://azure.microsoft.com/support/trust-center/). Wie bereits erwähnt, migrieren wir derzeit von Azure zu Office 365. Informationen zur Sicherheit dieser Dienste finden Sie im [Office 365 Trust Center](https://go.microsoft.com/fwlink/p/?linkid=525776).

