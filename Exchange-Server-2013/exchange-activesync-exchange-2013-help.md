---
title: 'Exchange ActiveSync: Exchange 2013 Help'
TOCTitle: Exchange ActiveSync
ms:assetid: 5fafaff3-eb37-4fdb-95f0-e56c45ea5884
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998357(v=EXCHG.150)
ms:contentKeyID: 50475762
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange ActiveSync

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Informationen zum Exchange ActiveSync-Clientprotokoll für Exchange Server 2013. Hier erhalten Sie Informationen zu den Features von Exchange ActiveSync, u. a. zu Sicherheitsfeatures, über Dinge, die Sie verwalten können, zum Schutz von diesen und zum Vermeiden von Problemen beim Synchronisieren mit Windows Phone 7.


> [!TIP]
> Dieses Thema ist für Administratoren bestimmt. Sie möchten Ihr Windows Phone-, iOS- oder Android-Gerät einrichten, um mit diesem auf das Office 365- oder Exchange Server-Postfach zugreifen zu können? Informationen hierzu finden Sie in den folgenden Themen: 
> <UL>
> <LI>
> <P><A href="https://go.microsoft.com/fwlink/p/?linkid=615415">Einrichten von E-Mail auf einem Windows Phone</A></P>
> <LI>
> <P><A href="https://go.microsoft.com/fwlink/p/?linkid=615414">Einrichten von E-Mail auf einem iPhone, iPad oder iPod touch</A></P>
> <LI>
> <P><A href="https://go.microsoft.com/fwlink/?linkid=615417">Einrichten von E-Mail auf einem Android-Smartphone oder -Tablet</A></P></LI></UL>



Exchange ActiveSync ist ein Clientprotokoll, mit dem Sie ein mobiles Gerät mit Ihrem Exchange-Postfach synchronisieren können. Exchange ActiveSync wird bei der Installation von Microsoft Exchange 2013 standardmäßig aktiviert.

**Inhalt**

Exchange ActiveSync - Übersicht

Funktionen in Exchange ActiveSync

Verwalten von Exchange ActiveSync

Synchronisieren von Windows Phone 7-Mobiltelefonen

## Exchange ActiveSync - Übersicht

Exchange ActiveSync ist ein Microsoft Exchange-Synchronisierungsprotokoll, das für die Zusammenarbeit mit Netzwerken mit langer Wartezeit und niedriger Bandbreite optimiert ist. Mithilfe des Protokolls, das auf HTTP und XML basiert, können Mobiltelefone auf die Informationen einer Organisation auf einem Server zugreifen, auf dem Microsoft Exchange ausgeführt wird. Exchange ActiveSync ermöglicht Benutzern von Mobiltelefonen den Zugriff auf ihre E-Mail-Nachrichten, ihren Kalender, ihre Kontakte und Aufgaben sowie den Zugriff auf diese Informationen während des Offlinearbeitens.


> [!NOTE]
> Exchange ActiveSync unterstützt weder freigegebene Postfächer noch Stellvertretungszugriff.




> [!IMPORTANT]
> Mobiltelefone mit Windows Phone 7 unterstützen die Einstellungen für Exchange ActiveSync-Postfachrichtlinien nur teilweise. Eine vollständige Liste finden Sie unter Synchronisieren von Windows Phone 7-Mobiltelefonen.



## Funktionen in Exchange ActiveSync

Exchange ActiveSync stellt die folgenden Funktionen bereit:

  - Unterstützung für HTML-Nachrichten

  - Unterstützung für Nachverfolgungsflag

  - Gruppierung von E-Mails nach Unterhaltung

  - Möglichkeit zum Synchronisieren einer gesamten Unterhaltung

  - Synchronisierung von SMS-Nachrichten (Short Message Service) mit dem Exchange-Postfach eines Benutzers

  - Unterstützung für das Anzeigen des Antwortstatus von Nachrichten

  - Unterstützung für schnellen Nachrichtenabruf

  - Informationen zu Besprechungsteilnehmern

  - Erweiterte Exchange-Suche

  - PIN-Zurücksetzung

  - Optimierte Gerätesicherheit durch Kennwortrichtlinien

  - AutoErmittlung für drahtlose Bereitstellung

  - Unterstützung für die Einstellung der automatischen Antwortfunktion, wenn Benutzer nicht verfügbar (abwesend, auf Reisen oder nicht im Büro) sind

  - Unterstützung für Aufgabensynchronisierung

  - Direct Push

  - Unterstützung für Verfügbarkeitsinformationen für Kontakte

## Verwalten von Exchange ActiveSync

Standardmäßig ist Exchange ActiveSync aktiviert. Alle Benutzer, die über ein Exchange-Postfach verfügen, können ihre mobilen Geräte mit dem Microsoft Exchange-Server synchronisieren.

Sie können die folgenden Exchange ActiveSync Aufgaben ausführen:

  - Aktivieren und Deaktivieren von Exchange ActiveSync für Benutzer

  - Festlegen von Richtlinien, wie minimale Kennwortlänge, Gerätesperre und maximale Fehleingaben des Kennworts

  - Einleiten eines Remotezurücksetzungsvorgangs zum Löschen aller Daten von einem verlorenen oder gestohlenen Mobiltelefon

  - Ausführen einer Vielzahl von Berichten zur Anzeige oder zum Export in verschiedenen Formaten

  - Steuerung der mobilen Gerätetypen, die über Gerätezugriffsregeln eine Synchronisierung mit Ihrer Organisation durchführen können

## Sicherheit in Exchange ActiveSync

Sie können Exchange ActiveSync für die Verwendung von SSL-Verschlüsselung (Secure Sockets Layer) für die Kommunikation zwischen dem Exchange-Server und dem mobilen Gerät konfigurieren.

## Verwalten des Zugriffs über mobile Geräte in Exchange ActiveSync

Sie können steuern, welche mobilen Geräte eine Synchronisierung durchführen können. Hierzu überwachen Sie neue mobile Geräte bei der Verbindungsherstellung mit Ihrer Organisation, oder Sie richten Regeln ein, mit denen die mobilen Gerätetypen festgelegt werden, die eine Verbindung herstellen dürfen. Unabhängig von der gewählten Methode zur Festlegung der mobilen Geräte, für die eine Synchronisierung zulässig ist, können Sie den Zugriff durch ein spezifisches mobiles Gerät für einen bestimmten Benutzer jederzeit gewähren oder verweigern

## Funktionen zur Gerätesicherheit in Exchange ActiveSync

Über die Möglichkeit hinaus, Sicherheitsoptionen für die Kommunikation zwischen dem Exchange-Server und Ihren mobilen Geräten zu konfigurieren, bietet Exchange ActiveSync die folgenden Features zum Steigern der Sicherheit mobiler Geräte:

  - **Remotezurücksetzung**   Wenn ein mobiles Gerät verloren geht, gestohlen oder in anderer Weise beschädigt wird, können Sie auf dem Exchange Server-Computer oder aus einem beliebigen Webbrowser mithilfe von Outlook Web App einen Befehl zur Remotezurücksetzung ausgeben. Mit diesem Befehl werden alle Daten vom mobilen Gerät gelöscht.

  - **Richtlinien für Gerätekennwörter**   Exchange ActiveSync ermöglicht das Konfigurieren verschiedener Optionen für Gerätekennwörter.
    

    > [!WARNING]
    > Die Fingerabdruck-Lesegerättechnologie von iOS7 kann nicht als Gerätekennwort verwendet werden. Wenn Sie sich für die Verwendung des iOS7-Fingerabdruck-Lesegeräts entscheiden, müssen Sie trotzdem noch ein Gerätekennwort erstellen und eingeben, wenn die Postfachrichtlinie für mobile Geräte in Ihrer Organisation ein Gerätekennwort vorschreibt.

    
    Folgende Optionen für Gerätekennwörter sind verfügbar:
    
      - **Minimale Kennwortlänge (Zeichen)**   Mit dieser Option wird die Länge des Kennworts für das mobile Gerät angegeben. Die Standardlänge beträgt vier Zeichen, es können jedoch bis zu 18 Zeichen vorgeschrieben werden.
    
      - **Minimale Anzahl von Zeichensätzen**   Mithilfe dieses Textfelds legen Sie die Komplexität des alphanumerischen Kennworts fest und zwingen die Benutzer, verschiedene Zeichensätze zu verwenden, die Folgendes einbeziehen: Kleinbuchstaben, Großbuchstaben, Symbole und Zahlen.
    
      - **Alphanumerisches Kennwort anfordern**   Mit dieser Option wird die Sicherheit des Kennworts bestimmt. Sie können die Verwendung eines Buchstabens oder Sonderzeichens im Kennwort zusätzlich zu Ziffern erzwingen.
    
      - **Leerlaufzeit (Sekunden)**   Diese Option bestimmt, wie lange das mobile Gerät inaktiv sein muss, bevor der Benutzer zur Eingabe eines Kennworts aufgefordert wird, um die Sperre für das mobile Gerät aufzuheben.
    
      - **Kennwortverlauf erzwingen**   Aktivieren Sie dieses Kontrollkästchen, um den Benutzer daran zu hindern, frühere Kennwörter erneut zu verwenden. Die von Ihnen angegebene Anzahl bestimmt die Anzahl früherer Kennwörter, die der Benutzer nicht erneut verwenden darf.
    
      - **Kennwortwiederherstellung aktivieren**   Aktivieren Sie dieses Kontrollkästchen, um die Kennwortwiederherstellung für das Mobilgerät zu aktivieren. Administratoren können das Cmdlet **Get-ActiveSyncDeviceStatistics** verwenden, um nach dem Wiederherstellungskennwort des Benutzers zu suchen.
    
      - **Gerät nach Fehlversuchen entfernen (Versuche)**  Diese Option gibt an, ob der Speicher des Mobiltelefons nach mehreren fehlgeschlagenen Kennworteingaben gelöscht werden soll.

  - **Richtlinien zur Geräteverschlüsselung**   Es gibt eine Reihe von Verschlüsselungsrichtlinien für mobile Geräte, die Sie für eine Gruppe von Benutzern erzwingen können. Hierzu zählen folgende Richtlinien:
    
      - **Verschlüsselung auf dem Gerät anfordern**   Aktivieren Sie dieses Kontrollkästchen, um die Verschlüsselung auf dem mobilen Gerät anzufordern. Auf diese Weise wird die Sicherheit erhöht, da alle Informationen auf dem mobilen Gerät verschlüsselt werden.
    
      - **Verschlüsselung auf der Speicherkarte vorschreiben**   Aktivieren Sie dieses Kontrollkästchen, um für die austauschbare Speicherkarte des mobilen Geräts eine Verschlüsselung anzufordern. Auf diese Weise wird die Sicherheit erhöht, da alle Informationen auf Speicherkarten des mobilen Geräts verschlüsselt werden.

## Synchronisieren von Windows Phone 7-Mobiltelefonen

Wenn Ihre Organisation über mobile Geräte mit Windows Phone 7 verfügt und bestimmte Richtlinieneigenschaften für mobile Gerätepostfächer konfiguriert sind, treten Synchronisierungsprobleme auf. Um die Synchronisierung von Mobiltelefonen mit Windows Phone 7 mit einem Exchange-Postfach zu ermöglichen, legen Sie die Eigenschaft **AllowNonProvisionableDevices** auf "True" fest, oder konfigurieren Sie nur die folgenden Richtlinieneigenschaften für mobile Gerätepostfächer:

  - PasswordRequired

  - MinPasswordLength

  - IdleTimeoutFrequencyValue

  - DeviceWipeThreshold

  - AllowSimplePassword

  - PasswordExpiration

  - PasswordHistory

  - DisableRemovableStorage

  - DisableIrDA

  - DisableDesktopSync

  - BlockRemoteDesktop

  - BlockInternetSharing

