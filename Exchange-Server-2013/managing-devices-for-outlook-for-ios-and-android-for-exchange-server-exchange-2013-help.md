---
title: 'Verwalten von Geräten für Outlook für iOS und Android für Exchange Server'
TOCTitle: Managing devices for Outlook for iOS and Android for Exchange Server
ms:assetid: 16ce7d24-be74-4466-b126-828a67f69b6e
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt465748(v=EXCHG.150)
ms:contentKeyID: 70086932
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Managing devices for Outlook for iOS and Android for Exchange Server

 

_**Gilt für:** Exchange Server 2010, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2018-04-01_

**Zusammenfassung:**  In diesem Artikel erfahren Sie, wie Sie mit Exchange Aktive Sync Mobilgeräte mit Outlook für iOS und Android in Ihrer lokalen Exchange-Organisation mithilfe der Standardauthentifizierung über das Exchange ActiveSync-Protokoll verwalten können.

Microsoft empfiehlt Exchange ActiveSync für die Verwaltung von Mobilgeräten, mit denen auf Exchange-Postfächer in Ihrer lokalen Umgebung zugegriffen wird. Exchange ActiveSync ist ein Microsoft Exchange-Synchronisierungsprotokoll, über das Mobiltelefone auf organisationsinterne Informationen zugreifen können, die auf Microsoft Exchange-Servern gespeichert sind.

Dieser Artikel konzentriert sich auf spezifische Exchange ActiveSync-Funktionen und -Szenarien für Mobilgeräte mit Outlook für Android und iOS bei Verwendung der Standardauthentifizierung. Alle Details zum Microsoft Exchange-Synchronisierungsprotokoll finden Sie unter [Exchange ActiveSync](exchange-activesync-exchange-2013-help.md). Im [Office-Blog](https://go.microsoft.com/fwlink/p/?linkid=623922) finden Sie darüber hinaus detaillierte Informationen zum Thema Kennworterzwingung sowie zu den weiteren Vorteilen einer Verwendung von Exchange ActiveSync mit Geräten, auf denen Outlook für iOS und Android ausgeführt wird.

## PIN-Sperre und Geräteverschlüsselung

Verlangt die Exchange ActiveSync-Richtlinie Ihrer Organisation, dass Benutzer zur Synchronisierung ihrer E-Mails ein Kennwort auf ihrem Mobilgerät eingeben, erzwingt Outlook diese Richtlinie auf Geräteebene. Die konkrete Umsetzung ist dabei auf iOS-Geräten und Android-Geräten jeweils unterschiedlich und basiert auf den von Apple und Google jeweils zur Verfügung gestellten Steuerelementen.

Auf iOS-Geräten überprüft Outlook, ob der Benutzer einen Code oder eine PIN festgelegt hat. Ist kein Code festgelegt, fordert Outlook den Benutzer auf, einen Code in den iOS-Einstellungen festzulegen. Der Benutzer kann erst auf Outlook für iOS zugreifen, wenn er einen Code festgelegt hat.

Outlook für iOS wird erst ab iOS 10.0 unterstützt. Geräte mit dieser Betriebssystemversion verfügen über eine integrierte Verschlüsselungsfunktion. Mit dieser Verschlüsselungsfunktion verschlüsselt Outlook nach Aktivierung des Codes alle Outlook-Datenspeicher auf dem iOS-Gerät lokal. iOS-Geräte mit einer PIN werden also immer verschlüsselt, unabhängig davon, ob es eine entsprechende ActiveSync-Richtlinie gibt.

Auf Android-Geräten erzwingt Outlook Regeln für die Bildschirmsperre. Darüber hinaus stellt Google Steuerelemente bereit, mit deren Hilfe Outlook für Android Exchange-Richtlinien bezüglich der Kennwortlänge, der Kennwortkomplexität und der Anzahl von zulässigen Entsperrversuchen vor Zurücksetzung des Telefons einhalten kann. Outlook für Android empfiehlt dem Benutzer auch die Verschlüsselung des Gerätespeichers, falls diese Funktion noch nicht aktiviert ist, und führt ihn Schritt für Schritt durch den Prozess.

iOS- und Android-Geräte, die diese Einstellungen für Kennwortsicherheit nicht unterstützen, können keine Verbindung zu Exchange-Postfächern herstellen.

## Remotezurücksetzung mit Exchange ActiveSync

Administratoren können Geräte mithilfe von Exchange ActiveSync remote zurücksetzen, beispielsweise aufgrund einer Kompromittierung der Geräte. Bei Outlook für iOS und Android wird die Remotezurücksetzung auf die Outlook-App angewendet. Es wird keine vollständige Gerätezurücksetzung durchgeführt.

Gibt der Administrator den Befehl zur Remotezurücksetzung aus, wird die Zurücksetzung durchgeführt, sobald die Outlook-App wieder eine Verbindung mit Exchange herstellt. Der eigentliche Prozess dauert dann nur wenige Sekunden. Die Outlook-App wird zurückgesetzt, und alle Outlook-E-Mails, -Kalender, -Kontakte und -Dateien werden vom Gerät und aus dem Outlook-Dienst entfernt. Persönliche Apps und Informationen außerhalb von Outlook bleiben von der Zurücksetzung unberührt.

Da Outlook für iOS und Android in Exchange unter den Mobilgeräten des Benutzers als eine einzige Mobilgerätezuordnung angezeigt wird, werden Remotezurücksetzungen auf alle Geräte mit Outlook (iPhone, iPad, Android) angewendet, die dem Benutzer zugeordnet sind. Das heißt: Es werden auf allen Geräten die entsprechenden Daten entfernt, und es werden auf allen Geräten sämtliche Synchronisierungsbeziehungen gelöscht.


> [!NOTE]
> Aufgrund der Cloudarchitektur von Outlook&nbsp;für&nbsp;iOS&nbsp;und&nbsp;Android wird das Ergebnis einer Remotegerätezurücksetzung nicht an Exchange gemeldet. Selbst bei erfolgreicher Zurücksetzung wird der Status weiterhin als <STRONG>Ausstehend</STRONG> angezeigt. Dieses Problem ist uns bekannt, und wir arbeiten bereits an einer Lösung.



## Gerätebezeichner und Zugriffssteuerung

Aufgrund der cloudbasierten Architektur von Outlook für iOS und Android erscheinen sämtliche Outlook-Verbindungen eines Exchange-Benutzers unter einem einzigen Mobilgerätebezeichner (ID). Alle für den Benutzer geltenden Zugriffssteuerungsregeln für den Zugriff über Mobilgeräte werden auf alle Geräte angewendet, die dieser Geräte-ID zugeordnet sind. Diese Implementierung bedingt zwei Unterschiede zur Funktionsweise der herkömmlichen Exchange ActiveSync-Gerätezugriffssteuerung:

  - **Blockierung:**  Eine Blockierungsregel blockiert Outlook auf allen Geräten und unter allen unterstützten Betriebssystemen. Die Blockierung lässt sich nicht auf einzelne Geräte oder Betriebssysteme beschränken.

  - **Quarantäne:**  Der Quarantäneprozess arbeitet auf Benutzerbasis, nicht auf Gerätebasis. Wurde ein Gerät eines Benutzers aus der Quarantäne entlassen, kann der Benutzer Outlook auf beliebig vielen weiteren Geräten installieren und konfigurieren. Da der Benutzer aus der Quarantäne entlassen wurde, werden neue ihm zugewiesene Geräte nicht unter Quarantäne gestellt.

Existieren Mobilgeräte-Postfachrichtlinien, gelten sie für alle Geräte, die einem Benutzer zugeordnet sind. Wenn Sie also beispielsweise für ein bestimmtes Postfach eine PIN-Sperre erzwingen, ist auf allen Geräten, die sich mit dem Postfach verbinden, die Eingabe einer PIN erforderlich.


> [!NOTE]
> Da Geräte-IDs nicht von der ID eines <EM>physischen Geräts</EM> abhängen, können sie sich ohne Vorankündigung ändern. Das kann unerwartete Konsequenzen haben, falls Geräte-IDs zur Verwaltung der Benutzergeräte verwendet werden. Bereits zugelassene Geräte könnten unerwarteterweise von Exchange blockiert oder unter Quarantäne gestellt werden. Aus diesem Grund empfehlen wir Administratoren, ausschließlich Mobilgeräterichtlinien zu implementieren, die Geräte auf Basis des Gerätetyps oder des Gerätemodells zulassen/blockieren.



## Blockieren von Outlook für iOS und Android

In diesem Abschnitt erfahren Sie, wie Sie die App blockieren können, wenn Sie nicht möchten, dass die Benutzer in Ihrer lokalen Exchange-Organisation mit Outlook für iOS und Android mithilfe der Standardauthentifizierung auf Daten zugreifen.

Jede Exchange-Organisation definiert eigene Richtlinien für Sicherheit und Geräteverwaltung. Kommt eine Organisation zu dem Schluss, dass Outlook für iOS und Android ihren Anforderungen nicht entspricht oder aus irgendeinem Grund nicht die beste Lösung für ihren Anwendungsfall ist, können Administratoren die App mithilfe von Exchange ActiveSync-Geräteverwaltungsrichtlinien blockieren. Alle Informationen zur Konfiguration von Exchange ActiveSync finden Sie unter [Steuern des Gerätezugriffs](https://go.microsoft.com/fwlink/p/?linkid=62400). In den Exchange ActiveSync-Verwaltungsbildschirmen wird die Outlook-App als **DeviceModel: 'Outlook for iOS and Android'** oder **DeviceType: 'Outook'** aufgeführt.


> [!NOTE]
> Da Geräte-IDs nicht von der ID eines <EM>physischen Geräts</EM> abhängen, können sie sich ohne Vorankündigung ändern. Das kann unerwartete Konsequenzen haben, falls Geräte-IDs zur Verwaltung der Benutzergeräte verwendet werden. Bereits zugelassene Geräte könnten unerwarteterweise von Exchange blockiert oder unter Quarantäne gestellt werden. Aus diesem Grund empfehlen wir Administratoren, ausschließlich Mobilgeräterichtlinien zu implementieren, die Geräte auf Basis des Gerätetyps oder des Gerätemodells zulassen/blockieren.



Die Exchange-Benutzer in Ihrer Organisation können weiterhin die Apps Outlook im Web für iPhone, Outlook im Web für iPad und Outlook im Web für Android oder die nativen Mail-Apps von iOS und Android verwenden, um auf ihre Exchange-Postfächer zuzugreifen.

Unten sehen Sie, wie eine im Exchange Admin Center erstellte Geräteregel in der PowerShell aussieht:

![Beispiel für eine Geräteregel in PowerShell.](images/Mt465748.d1418996-ff8b-4ddb-a3d9-7a80d808e677(EXCHG.150).png "Beispiel für eine Geräteregel in PowerShell.")

## Geräteverwaltung mit Exchange ActiveSync: häufig gestellte Fragen

In diesem Abschnitt finden Sie häufig gestellte Fragen zu Kennwörtern, PINs und Verschlüsselungsrichtlinien für Geräte mit Outlook für iOS und Android.

## Die native Mail-App unter iOS erzwingt Exchange ActiveSync-Richtlinien zu Kennwortlänge und Kennwortkomplexität. Warum werden die Richtlinien nicht von Outlook erzwungen?

Outlook nutzt die Drittanbieter-Entwicklersteuerelemente, die Microsoft zur Verfügung stehen. Wir werden diese Funktion weiter verbessern, sollte Apple weitere Steuerelemente für Entwickler bereitstellen.

## Warum erzwingt Outlook für iOS und Android PINs auf Geräteebene und nicht auf App-Ebene?

Nach einer Analyse der unter iOS und Android verfügbaren Funktionen ist Microsoft zu dem Schluss gekommen, dass eine PIN auf Geräteebene für unsere Kunden benutzerfreundlicher ist, sowohl mit Blick auf den Komfort als auch mit Blick auf die Sicherheit. Bei einer PIN auf App-Ebene müssten Benutzer zwei verschiedene PINs eingeben, um auf ihre E-Mails zugreifen zu können. Das scheint uns nicht wünschenswert. Darüber hinaus können wir mit einer PIN auf Geräteebene Funktionen wie die native Geräteverschlüsselung, Touch ID unter iOS und Smart Lock unter Android nutzen. Die Remotezurücksetzung allerdings wird auf App-Ebene implementiert, sodass die persönlichen Anwendungen und Daten des Benutzers von einer Outlook-Zurücksetzung unberührt bleiben.

## Unterstützt Outlook für Android die Geräteverschlüsselung?

Ja, Outlook für Android unterstützt die Geräteverschlüsselung über Postfachrichtlinien für mobile Geräte. Vor Android 7.0 variiert die Verfügbarkeit und die Implementierung dieses Prozesses jedoch je nach Android-Version und Gerätehersteller, sodass Benutzer die Möglichkeit haben, den Verschlüsselungsprozess abzubrechen. Aufgrund von Änderungen, die Google in Android 7.0 einführte, kann Outlook für Android nun die Verschlüsselung auf Geräten erzwingen, auf denen Android 7.0 oder höher ausgeführt wird. Benutzer mit Geräten, auf denen diese Betriebssysteme ausgeführt werden, können den Verschlüsselungsprozess nicht abbrechen.

Doch selbst wenn das Android-Gerät unverschlüsselt ist: Ist eine Geräte-PIN festgelegt, können Angreifer nicht auf die Outlook-Datenbank zugreifen, wenn sie es in ihren Besitz bringen. Das ist sogar dann der Fall, wenn USB-Debugging aktiviert ist und sie das Android-SDK installiert haben. Sollte ein Angreifer versuchen, das Gerät zu rooten, um die PIN zu umgehen und sich Zugang zu den Daten zu verschaffen, wird dadurch die Zurücksetzung des Gerätespeichers angestoßen. Zusätzlich werden alle Outlook-Daten entfernt. Rootet der Benutzer sein unverschlüsseltes Gerät selbst und es wird anschließend entwendet, kann ein Angreifer sich möglicherweise Zugriff auf die Outlook-Datenbank verschaffen, indem er das USB-Debugging aktiviert und das Gerät an einen Computer mit installiertem Android-SDK anschließt.

