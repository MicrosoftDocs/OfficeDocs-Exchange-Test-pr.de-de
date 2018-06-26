---
title: 'Bereitstellen von Exchange 2013 UM: Exchange 2013 Help'
TOCTitle: Bereitstellen von Exchange 2013 UM
ms:assetid: d147d4b1-32d7-476b-b76f-ee3c0b35ba49
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ673564(v=EXCHG.150)
ms:contentKeyID: 50476770
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Exchange 2013 UM

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Für Unified Messaging (UM) muss Ihre Exchange Server-Bereitstellung in das vorhandene Telefoniesystem für Ihre Organisation integriert werden. Für eine erfolgreiche Bereitstellung und die Durchführung der richtigen Planungsschritte für die Bereitstellung und Verwaltung von Voicemail in Unified Messaging ist eine sorgfältige Analyse Ihrer vorhandenen Telefonieinfrastruktur erforderlich.

**Inhalt**

Vor der Bereitstellung

Bereitstellen von Unified Messaging

Nach der Bereitstellung auszuführende Aufgaben für Unified Messaging

## Vor der Bereitstellung

Bevor Sie Unified Messaging bereitstellen, sollten Sie sich mit den Konzepten in folgenden Themen vertraut machen:

  - [UM-Wählpläne](um-dial-plans-exchange-2013-help.md)

  - [UM-IP-Gateways](um-ip-gateways-exchange-2013-help.md)

  - [UM-Dienste](um-services-exchange-2013-help.md)

  - [UM-Sammelanschlüsse](um-hunt-groups-exchange-2013-help.md)

  - [Automatisches Beantworten und Weiterleiten eingehender Anrufe](automatically-answer-and-route-incoming-calls-exchange-2013-help.md)

  - [UM-Postfachrichtlinien](um-mailbox-policies-exchange-2013-help.md)

  - [Voicemail für Benutzer](voice-mail-for-users-exchange-2013-help.md)

## Bereitstellen von Unified Messaging

Unabhängig davon, ob Sie UM mithilfe von IP-Nebenstellenanlagen, VoIP-Gateways oder Microsoft Lync Server bereitstellen, weisen alle Bereitstellungsoptionen für Unified Messaging einige identische Schritte auf. Diese Schritte müssen ausgeführt werden, um ein skalierbares System mit hoher Verfügbarkeit zur Unterstützung einer großen Anzahl von Unified Messaging-Benutzern zu erstellen. Diese Schritte lauten wie folgt:

1.  Stellen Sie die Telefoniekomponenten für Unified Messaging bereit, und konfigurieren Sie diese.

2.  Vergewissern Sie sich, dass der Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung, und der Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, korrekt installiert wurden.

3.  Erstellen Sie die erforderlichen Unified Messaging-Komponenten, und konfigurieren Sie diese.

4.  Führen Sie alle nach der Bereitstellung auszuführenden Aufgaben für Unified Messaging aus.

## Bereitstellen und Konfigurieren der Telefoniekomponenten

Damit Unified Messaging in einer Exchange-Organisation erfolgreich bereitgestellt werden kann, muss sich der Exchange-Administrator über Datennetzwerkkonzepte sowie Telefonieterminologie und -konzepte informieren. Zudem muss er in der Lage sein, die für UM erforderlichen Telefoniekomponenten ordnungsgemäß zu konfigurieren. Für die Ausführung einer neuen Bereitstellung oder das Upgrade eines Legacy-Voicemailsystems sind umfassende Kenntnisse von Telefonienetzwerken und Unified Messaging erforderlich.

Im Allgemeinen müssen drei Aufgaben erledigt werden, um die für UM erforderlichen Telefoniekomponenten erfolgreich zu konfigurieren:

1.  **Bereitstellen von PBX-Leitungen**   Der erste Schritt zum Bereitstellen einer skalierbaren UM-Lösung besteht im Bereitstellen von PBX-Leitungen.

2.  **Organisieren von Kanälen**   Im Anschluss an die Bereitstellung von auf Nebenstellenanlagen basierten Sprachkanälen können Sie diese in Sammelanschlüssen organisieren.

3.  **Bereitstellen von VoIP-Gateways**   Im Anschluss an die Organisation der Sprachkanäle in Sammelanschlüssen müssen Sie am Ende der Kanäle VoIP-Gateways erstellen. VoIP-Gateways werden zusammen mit einer Legacy-Nebenstellenanlage verwendet, um die leitungsvermittelten Protokolle des Telefonienetzwerks in IP-basierte, paketvermittelte Protokolle zu konvertieren.

Wenn Sie die Telefonie- und Datennetzwerke der Organisation im Rahmen der Bereitstellung von Unified Messaging integrieren, müssen die Telefonie- und Datennetzwerkkomponenten ordnungsgemäß konfiguriert werden. Außerdem müssen Sie für eine erfolgreiche Bereitstellung von Unified Messaging die folgenden Komponenten oder Schnittstellen konfigurieren:

  - **Konfigurieren der Verbindung zwischen den Nebenstellenanlagen in Ihrer Organisation für die Kommunikation mit den VoIP-Gateways.**   Einzelheiten finden Sie unter [Anschließen eines VoIP-Gateways zur Kommunikation mit einer Nebenstellenanlage](connect-a-voip-gateway-to-communicate-with-a-pbx-exchange-2013-help.md).

  - **Konfigurieren der Verbindung zwischen der VoIP-Gateway-Schnittstelle und der Nebenstellenanlage.**   Weitere Informationen zum Konfigurieren der Nebenstellenanlagen-Schnittstelle für die Kommunikation mit dem unterstützten VoIP-Gateway finden Sie in der Produktdokumentation der Nebenstellenanlage oder unter [Anschließen eines VoIP-Gateways zur Kommunikation mit einer Nebenstellenanlage](connect-a-voip-gateway-to-communicate-with-a-pbx-exchange-2013-help.md).

  - **Konfigurieren der Verbindung zwischen der VoIP-Gatewayschnittstelle und den Clientzugriffs- und Postfachservern.**   Einzelheiten finden Sie unter [Verbinden eines VoIP-Gateways, einer IP-Nebenstellenanlage oder eines Session Border Controllers mit UM](connect-a-voip-gateway-ip-pbx-or-session-border-controller-to-um-exchange-2013-help.md).

  - **Konfigurieren der Verbindung zwischen den Clientzugriffs- und Postfachservern und der VoIP-Gatewayschnittstelle.**   Einzelheiten finden Sie unter [Verbinden von UM mit einem unterstützten VoIP-Gateway](connect-um-to-a-supported-voip-gateway-exchange-2013-help.md).

Vor der Bereitstellung

## Installieren der Postfach- und Clientzugriffsserver

Organisationen, die die Bereitstellung von Exchange Unified Messaging planen, stehen unterschiedliche Bereitstellungspfade zur Verfügung. Obgleich alle Pfade zum selben Ergebnis führen, nämlich einer erfolgreichen Bereitstellung von Unified Messaging, weichen die verschiedenen Pfade leicht voneinander ab, da die Anforderungen und Ausgangssituationen der einzelnen Kunden unterschiedlich sind. Generell sind jedoch gängige Ausgangspunkte und Pfade vorhanden, die alle unterstützten Bereitstellungsszenarien abdecken, zu denen auch Neuinstallationen und Upgrades zählen. Führen Sie diese Schritte aus, um die Clientzugriffs- und Postfachserver bereitzustellen:

1.  Vergewissern Sie sich, dass die vorhandene Infrastruktur die erforderlichen Voraussetzungen erfüllt. Weitere Informationen finden Sie unter [Voraussetzungen für Exchange 2013](exchange-2013-prerequisites-exchange-2013-help.md).

2.  Stellen Sie die neue Exchange 2013-Organisation bereit. Weitere Informationen finden Sie unter [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md).
    

    > [!WARNING]
    > Sie müssen mindestens einen Exchange 2013 Postfachserver in Ihrer Organisation bereitstellen, bevor Sie Ihre VoIP-Gateways oder IP PBX konfigurieren, um UM-SIP und RTP-Meldungen an die Exchange 2013 Clientzugriffsserver zu senden.



3.  Vergewissern Sie sich, dass die Clientzugriffs- und Postfachserver korrekt installiert wurden. Es empfiehlt sich, nach der Installation der Server die Installation und die Setupprotokolldateien zu überprüfen. Weitere Informationen finden Sie unter [Überprüfen einer Exchange 2013-Installation](verify-an-exchange-2013-installation-exchange-2013-help.md).

## Hinzufügen der erforderlichen UM-Sprachpakete

UM-Sprachpakete ermöglichen Anrufern und Outlook Voice Access-Benutzern die Interaktion mit dem Voicemailsystem in mehreren Sprachen. Nachdem Sie ein zusätzliches Sprachpaket auf einem Postfachserver installiert haben, können Anrufer und Outlook Voice Access-Benutzer E-Mail-Nachrichten in dieser Sprache wiedergeben und mit dem Voicemailsystem in dieser Sprache interagieren.

Bei der anfänglichen Installation von Exchange ist US-amerikanisches Englisch die Standardsprache und die einzige verfügbare Sprachoption für Ihren Wählplan. Nachdem Sie ein UM-Sprachpaket auf einem Postfachserver installiert haben, wird die dem Sprachpaket zugeordnete Sprache als verfügbare Option aufgelistet, wenn Sie die Standardsprache für den Wählplan konfigurieren. Da automatische UM-Telefonzentralen bei der Erstellung einem UM-Wählplan zugeordnet werden, wird standardmäßig die Standardspracheinstellung des zugehörigen UM-Wählplans verwendet. Diese Einstellung kann jedoch geändert werden, nachdem die automatische UM-Telefonzentrale erstellt wurde.

Nach dem Herunterladen eines UM-Sprachpakets von [Exchange Server 2013 UM Language Packs – Deutsch](https://go.microsoft.com/fwlink/p/?linkid=266542) kann dieses über den Befehl "Setup.exe" oder über das Installationsprogramm "*\<UMLanguagePack\>*.exe" installiert werden. Zum Entfernen eines UM-Sprachpakets müssen Sie jedoch den Befehl "Setup.exe" verwenden. Es gibt kein Cmdlet in der Exchange-Verwaltungsshell, mit dem Sprachen zu einem Postfachserver hinzugefügt oder von diesem entfernt werden können. Weitere Informationen zum Installieren eines UM-Sprachpakets finden Sie unter [Installieren eines Sprachpakets](install-a-um-language-pack-exchange-2013-help.md).


> [!NOTE]
> Bei der Installation eines Postfachservers wird standardmäßig die US-englische Version (en-US) installiert. Eine Entfernung ist nur möglich, indem Sie den Postfachserver vom Computer entfernen.



Vor der Bereitstellung

## Erstellen und Konfigurieren der UM-Komponenten

Mehrere UM-Komponenten sind für die Bereitstellung und den Betrieb von Unified Messaging erforderlich. Unified Messaging-Komponenten verbinden die Telefonieinfrastruktur mit der Unified Messaging-Umgebung. Führen Sie folgende Schritte aus, nachdem Sie die Clientzugriffs- und Postfachserver erfolgreich installiert haben.

## Schritt 1: Erstellen und Konfigurieren von UM-Wähleinstellungen

UM-Wählpläne sind für den Betrieb von Unified Messaging wichtig und für eine erfolgreiche Bereitstellung von Unified Messaging in Ihrem Netzwerk unerlässlich. Nach der erfolgreichen Installation der Clientzugriffs- und Postfachserver erstellen Sie als erste Komponente einen UM-Wählplan.

Standardmäßig senden und empfangen UM-Wählpläne und einem Wählplan zugeordnete Clientzugriffs- und Postfachserver Daten ohne Verschlüsselung. VoIP- und SIP-Datenverkehr werden im ungesicherten Modus nicht verschlüsselt. Wenn Sie die Wähleinstellungen erstellen bzw. erstellt haben, können Sie diese so konfigurieren, dass der VoIP- und SIP-Datenverkehr mithilfe von MTLS (Mutual Transport Layer Security) verschlüsselt wird. Wenn Sie MTLS verwenden, müssen Sie den Wählplan auf "SIP-gesichert" oder "Gesichert" und den UM-Startmodus auf "TLS" oder "Dual" festlegen. Außerdem müssen Sie ein vertrauenswürdiges Zertifikat für die Exchange-Server und VoIP-Gateways, IP-Nebenstellenanlagen oder Session Border Controller (SBCs) erstellen und verteilen. Wenn Sie die VoIP-Sicherheitseinstellung konfiguriert haben, konfigurieren Sie den Startmodus für die Clientzugriffs- und Postfachserver. Weitere Informationen finden Sie unter [Konfigurieren des Startmodus auf einem Postfachserver](configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md) oder [Konfigurieren des Startmodus auf einem Clientzugriffsserver](configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md).

Führen Sie zum Erstellen eines neuen UM-Wählplans das folgende Verfahren aus.

## Erstellen eines UM-Wählplans

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Füllen Sie auf der Seite **Neuer UM-Wählplan** folgende Felder aus:
    
      - **Name**   Geben Sie den Namen für die Wähleinstellungen ein. Ein Name für die UM-Wähleinstellungen ist erforderlich und muss eindeutig sein. Der eingegebene Name dient nur zu Anzeigezwecken in der Exchange-Verwaltungskonsole und der Shell. Der Name der UM-Wähleinstellungen kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
        

        > [!IMPORTANT]
        > Das Feld für den Wählplannamen kann zwar 64&nbsp;Zeichen aufnehmen, der Wählplanname darf jedoch höchstens 49&nbsp;Zeichen umfassen. Das liegt daran, dass bei der Erstellung der Wähleinstellungen auch eine UM-Standardpostfachrichtlinie mit dem Namen "<EM>&lt;Wähleinstellungenname&gt;</EM>-Standardrichtlinie" erstellt wird. Der Parameter <EM>name</EM> für die UM-Wähleinstellungen und die UM-Postfachrichtlinie kann eine Länge von 64 Zeichen haben.

    
      - **Durchwahllänge (Ziffern)**   Geben Sie die Anzahl von Ziffern für Durchwahlnummern im Wählplan ein. Die Anzahl der Stellen für Durchwahlnummern basiert auf den Telefoniewähleinstellungen, die auf einer PBX (Nebenstellenanlage) eingerichtet werden. Wenn beispielsweise ein Benutzer, der bestimmten Telefoniewähleinstellungen zugeordnet ist, eine 4-stellige Durchwahl wählt, um einen anderen Benutzer mit den gleichen Telefoniewähleinstellungen anzurufen, dann wählen Sie 4 als die Anzahl der Stellen in der Durchwahl aus.
        
        Dies ist ein erforderliches Feld mit Werten von 1 bis 20. Die typische Durchwahllänge beträgt 3 bis 7 Ziffern. Wenn die vorhandene Telefonieumgebung Durchwahlnummern verwendet, müssen Sie eine Anzahl für die Stellen festlegen, die mit der Anzahl der Stellen in diesen Durchwahlnummern übereinstimmt.
        
        Wenn Sie einen Wählplan für die Telefondurchwahl erstellen, müssen Sie eine Durchwahlnummer für den Benutzer eingeben, wenn dieser mit einem Wählplan für die Telefondurchwahl verknüpft ist. Eine Durchwahlnummer ist auch bei SIP-Wählplänen (Session Initiation-Protokoll) oder E.164-Wählplänen erforderlich, wenn ein UM-aktivierter Benutzer mit einem SIP-URI- oder einem E.164-Wählplan verknüpft ist. Die Durchwahlnummer wird von Outlook Voice Access-Benutzern verwendet, wenn sie auf ihr Exchange-Postfach zugreifen.
    
      - UNRESOLVED\_TOKENBLOCK\_VAL(UI\_URI-Typ)
    
      - UNRESOLVED\_TOKENBLOCK\_VAL(UI\_VoIP-Sicherheit)
    
      - **Länder-/Regionscode**   Verwenden Sie dieses Feld zur Eingabe des Länder-/Regionscodes für ausgehende Anrufe. Diese Nummer wird automatisch vor der zu wählenden Telefonnummer eingefügt. In diesem Feld werden nur 1 bis 4 Ziffern akzeptiert. In den USA wird beispielsweise als Landes-/Regionscode 1, in Großbritannien 44 verwendet.

3.  Klicken Sie auf **Speichern**.
    

    > [!IMPORTANT]
    > In früheren Versionen von Exchange musste der Unified Messaging-Server einem UM-Wählplan hinzugefügt werden. In Exchange 2013 können die Clientzugriffs- und Postfachserver weder einem Wählplan für die Telefondurchwahl noch einem E.164-Wählplan zugeordnet werden. Clientzugriffs- und Postfachserver beantworten alle eingehenden Anrufe für alle Typen von Wählplänen. Wenn Sie jedoch UM mit Microsoft Lync Server integrieren, müssen Sie alle Clientzugriffs- und Postfachserver allen SIP-URI-Wählplänen hinzufügen, damit die Anrufweiterleitung mit Lync Server korrekt funktioniert.



Vor der Bereitstellung

## Schritt 2: Erstellen und Konfigurieren der UM-IP-Gateways

Bei einem UM-IP-Gateway handelt es sich entweder um ein VoIP-Gatewayhardwaregerät oder eine IP-Nebenstellenanlage. Durch die Kombination des UM-IP-Gateways mit einem UM-Sammelanschluss wird eine Verknüpfung zwischen einem VoIP-Gateway oder einer IP-Nebenstellenanlage und einem UM-Wählplan eingerichtet.

Wenn Sie die VoIP-Sicherheit für einen UM-Wählplan erstellt oder aktiviert haben, wird das UM-IP-Gateway, das Sie mithilfe eines der folgenden Verfahren erstellen, einem UM-Wählplan zugeordnet, der VoIP-Sicherheit verwendet. In diesem Fall müssen Sie zum Erstellen des UM-IP-Gateways statt einer IP-Adresse einen vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) verwenden. Außerdem müssen Sie das UM-IP-Gateway für die Überwachung von TCP-Port 5061 konfigurieren. Führen Sie dazu den folgenden Befehl aus: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`. Sie müssen zudem sicherstellen, dass alle VoIP-Gateways oder IP-Nebenstellenanlagen für die Überwachung von Port 5061 für MTLS konfiguriert sind.

Führen Sie zum Erstellen eines neuen UM-IP-Gateways das folgende Verfahren aus.

## Erstellen eines UM-IP-Gateways

1.  
    
    Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-IP-Gateways**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie auf der Seite **Neues UM-IP-Gateway** die folgenden Informationen ein:
    
      - **Name**   Geben Sie in diesem Feld einen eindeutigen Namen für das UM-IP-Gateway ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Namen des UM-IP-Gateways nach dem Erstellen ändern müssen, muss zuerst das vorhandene UM-IP-Gateway gelöscht und dann ein anderes UM-IP-Gateway mit dem entsprechenden Namen erstellt werden. Der UM-IP-Gatewayname ist erforderlich, wird aber nur zur Anzeige verwendet. Da in Ihrer Organisation unter Umständen mehrere UM-IP-Gateways verwendet werden, sollten Sie aussagekräftige Namen für Ihre UM-IP-Gateways verwenden. Die maximale Länge eines UM-IP-Gatewaynamens beträgt 64 Zeichen, wobei Leerzeichen enthalten sein dürfen. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Adresse**   Ein UM-IP-Gateway kann entweder mit einer IP-Adresse oder mit einem vollqualifizierten Domänennamen (FDQN) konfiguriert werden. Verwenden Sie dieses Feld, um die auf VoIP-Gateway, SIP-aktivierter Nebenstellenanlage, IP-Nebenstellenanlage oder SBC konfigurierte IP-Adresse oder einen vollqualifizierten Domänennamen (FQDN) anzugeben. In dieses Textfeld können nur gültige FQDNs eingegeben werden, die ordnungsgemäß formatiert sind.
        
        Sie können in diesem Feld Buchstaben und Zahlen eingeben. Es werden IPv4-Adressen, IPv6-Adressen und FQDNs unterstützt. Um MTLS zwischen einem UM-IP-Gateway und einem Wählplan zu verwenden, die im SIP-gesicherten oder gesicherten Modus betrieben werden, müssen Sie das UM-IP-Gateway mit einem FQDN konfigurieren. Außerdem müssen Sie das Gateway für die Überwachung von Port 5061 konfigurieren und sicherstellen, dass VoIP-Gateways oder IP-Nebenstellenanlagen ebenfalls für die Überwachung von Port 5061 auf Mutual TLS-Anforderungen konfiguriert wurden. Führen Sie zum Konfigurieren eines UM-IP-Gateways den folgenden Befehl aus: `Set-UMIPGateway -identity MyUMIPGateway -Port 5061`.
        
        Wenn Sie einen FQDN verwenden, müssen Sie außerdem sicherstellen, dass Sie für das VoIP-Gateway einen gültigen DNS-Hosteintrag konfiguriert haben, sodass der Hostname fehlerfrei in eine IP-Adresse aufgelöst werden kann. Auch wenn Sie anstelle einer IP-Adresse einen FQDN verwenden und die DNS-Konfiguration für das UM-IP-Gateway ändern, müssen Sie das UM-IP-Gateway deaktivieren und erneut aktivieren, um sicherzustellen, dass die Konfigurationsinformationen für das UM-IP-Gateway ordnungsgemäß aktualisiert werden
    
      - **UM-Wählplan**   Klicken Sie auf **Durchsuchen**, um den UM-Wählplan auszuwählen, den Sie dem UM-IP-Gateway zuordnen möchten. Wenn Sie UM-Wähleinstellungen für die Zuordnung zu einem UM-IP-Gateway auswählen, wird außerdem ein UM-Sammelanschluss erstellt und diesen UM-Wähleinstellungen zugeordnet. Wenn Sie keine UM-Wähleinstellungen auswählen, müssen Sie einen UM-Sammelanschluss manuell erstellen und diesen dann dem erstellten UM-IP-Gateway zuordnen.

3.  
    
    Klicken Sie auf **Speichern**.

## Schritt 3: Erstellen und Konfigurieren der UM-Sammelanschlüsse (optional)

Der Begriff *Sammelanschluss* dient der Bezeichnung einer Gruppe von Nebenstellenanlagen, IP-Nebenstellenanlagen bzw. Durchwahlnummern, die von Benutzern gemeinsam verwendet werden. Sammelanschlüsse werden für das effiziente Verteilen der eingehenden und ausgehenden Anrufe einer bestimmten Geschäftseinheit verwendet.

Wenn Sie ein UM-IP-Gateway erstellen und dieses einem UM-Wählplan zuordnen, wird ein UM-Standardsammelanschluss erstellt. Je nach Anzahl der erstellten UM-IP-Gateways können Sie einen anderen UM-Sammelanschluss demselben oder einem anderen UM-IP-Gateway zuordnen.

Wenn Sie einen UM-Sammelanschluss erstellen, aktivieren Sie alle Postfachserver, die im UM-Wählplan angegeben sind, für die Kommunikation mit einem VoIP-Gateway. Weitere Informationen finden Sie unter [UM-Sammelanschlüsse](um-hunt-groups-exchange-2013-help.md).

## Erstellen eines UM-Sammelanschlusses

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unter **UM-Sammelanschlüsse** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Füllen Sie auf der Seite **Neuer UM-Sammelanschluss** die folgenden Felder aus:
    
      - **Zugeordnetes UM-IP-Gateway**   Dieses reine Anzeigefeld zeigt den Namen des UM-IP-Gateways an, das dem UM-Sammelanschluss zugeordnet wird.
    
      - **Name**   Verwenden Sie dieses Feld, um den Anzeigenamen für den UM-Sammelanschluss zu erstellen. Ein UM-Sammelanschlussname ist erforderlich, und er muss eindeutig sein, wobei er jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell verwendet wird. Wenn Sie den Anzeigenamen des Sammelanschlusses nach dem Erstellen ändern müssen, müssen Sie zuerst den vorhandenen Sammelanschluss löschen und können dann einen anderen Sammelanschluss mit dem entsprechenden Namen erstellen.
        
        Wenn in Ihrer Organisation mehrere Sammelanschlüsse verwendet werden, empfiehlt sich die Verwendung aussagekräftiger Namen für die Sammelanschlüsse. Der Name eines UM-Sammelanschlusses kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.
    
      - **Wählplan**   Klicken Sie auf **Durchsuchen**, um den Wählplan auszuwählen, der dem UM-Sammelanschluss zugeordnet wird. Die Zuordnung eines Sammelanschlusses zu Wähleinstellungen ist erforderlich. Ein UM-Sammelanschluss kann nur einem bestimmten UM-IP-Gateway und bestimmten Wähleinstellungen zugeordnet werden.
    
      - **Pilot-ID**   Verwenden Sie dieses Feld, um eine Zeichenfolge anzugeben, die die Pilot-ID eindeutig kennzeichnet, die auf der Nebenstellenanlage oder der IP-Nebenstellenanlage konfiguriert ist.
        
        In diesem Feld können eine Durchwahlnummer oder ein SIP-URI (Session Initiation-Protokoll - Uniform Resource Identifier) verwendet werden. Alphanumerische Zeichen sind in diesem Feld zulässig. Für ältere Nebenstellenanlagen wird ein numerischer Wert als Pilot-ID verwendet. Einige IP-Nebenstellenanlagen können jedoch SIP-URIs verwenden.

4.  Klicken Sie auf **Speichern**.

Vor der Bereitstellung

## Schritt 4: Erstellen und Konfigurieren einer UM-Postfachrichtlinie

UM-Postfachrichtlinien sind erforderlich, wenn Sie Benutzer für Unified Messaging aktivieren. Das Postfach jedes UM-aktivierten Benutzers muss mit einer einzelnen UM-Postfachrichtlinie verknüpft sein. Nachdem Sie eine UM-Postfachrichtlinie erstellt haben, ordnen Sie ihr eines oder mehrere UM-aktivierte Postfächer zu. Dadurch können Sie PIN-Sicherheitseinstellungen steuern, z. B. die Mindestanzahl an Stellen einer PIN oder die Höchstanzahl an fehlerhaften Anmeldeversuchen für UM-aktivierte Benutzer, die der UM-Postfachrichtlinie zugeordnet sind.

Jedes Mal wenn UM-Wähleinstellungen erstellt werden, wird gleichzeitig eine UM-Postfachrichtlinie erstellt. Die UM-Postfachrichtlinie wird als \<*Name\_Wähleinstellungen*\>-Standardrichtlinie bezeichnet. Führen Sie das folgende Verfahren aus, wenn Sie dennoch eine neue UM-Postfachrichtlinie erstellen müssen.

## Erstellen einer UM-Postfachrichtlinie

1.  
    
    Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**. Wählen Sie in der Listenansicht den UM-Wählplan aus, den Sie ändern möchten, und klicken Sie dann auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unter **UM-Postfachrichtlinien** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Geben Sie auf der Seite **Neue UM-Postfachrichtlinie** im Textfeld **Name** den Namen der neuen UM-Postfachrichtlinie ein.
    
    Geben Sie in dieses Feld einen eindeutigen Namen für die UM-Postfachrichtlinie ein. Hierbei handelt es sich um den Anzeigenamen, der in der Exchange-Verwaltungskonsole angezeigt wird. Wenn Sie den Anzeigenamen der UM-Postfachrichtlinie nach dem Erstellen ändern müssen, muss zuerst die vorhandene UM-Postfachrichtlinie gelöscht und dann eine andere UM-Postfachrichtlinie mit dem entsprechenden Namen erstellt werden. Sie können eine UM-Postfachrichtlinie nur löschen, wenn dieser keine UM-aktivierten Benutzer zugeordnet sind.
    
    Der UM-Postfachrichtlinienname ist erforderlich, wird aber nur zur Anzeige verwendet. Wenn in Ihrer Organisation mehrere UM-Postfachrichtlinien verwendet werden, empfiehlt sich die Verwendung aussagekräftiger Namen für die UM-Postfachrichtlinien. Der Name einer UM-Postfachrichtlinie kann eine Länge von maximal 64 Zeichen haben und Leerzeichen enthalten. Die folgenden Zeichen dürfen jedoch nicht enthalten sein: " / \\ \[ \] : ; | = , + \* ? \< \>.

4.  Klicken Sie auf **Speichern**, um die neue UM-Postfachrichtlinie zu speichern. Wenn Sie die UM-Postfachrichtlinie speichern, werden alle Standardeinstellungen einschließlich PIN-Richtlinien, Voicemailfeatures und Einstellungen für geschützte Voicemail aktiviert. Wenn Sie Standardeinstellungen anpassen oder ändern möchten, verwenden Sie das Cmdlet **Set-UMMailbox**, um die Einstellungen für die UM-Postfachrichtlinie zu ändern, die Sie gerade erstellt haben.

## Schritt 5: Erstellen und Konfigurieren automatischer UM-Telefonzentralen (optional)

Unified Messaging ermöglicht je nach den Anforderungen Ihrer Organisation die Einrichtung einer oder mehrerer automatischer UM-Telefonzentralen. Beim Erstellen einer automatischen UM-Telefonzentrale wird ein sprachgesteuertes Menüsystem für die Organisation erstellt. Anrufer von außer- oder innerhalb der Organisation können durch das Menüsystem navigieren, um Benutzer oder Abteilungen in der Organisation aufzufinden sowie Anrufe an diese zu tätigen oder zu vermitteln.

Anrufer können mithilfe des Tonwahlverfahrens (Dual Tone Multi-Frequency, DTMF) oder mithilfe von Spracheingaben durch das Menüsystem navigieren. Damit die automatische Spracherkennung (Automatic Speech Recognition, ASR) funktioniert, sodass die Benutzer die Spracheingabe verwenden können, müssen Sie die automatische UM-Telefonzentrale für die Spracheingabe aktivieren.

Das Erstellen und Verwenden von automatischen Telefonzentralen in Unified Messaging ist optional. Führen Sie das folgende Verfahren aus, wenn Sie eine neue automatische UM-Telefonzentrale erstellen möchten.

## Erstellen einer automatischen UM-Telefonzentrale

1.  
    
    Navigieren Sie in der Exchange-Verwaltungskonsole zu **Unified Messaging** \> **UM-Wählpläne**, wählen Sie den UM-Wählplan aus, für den Sie eine automatische Telefonzentrale hinzufügen möchten, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol").

2.  Klicken Sie auf der Seite **UM-Wählplan** unterhalb von **Automatische UM-Telefonzentralen** auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

3.  Füllen Sie auf der Seite **Neue automatische UM-Telefonzentrale** die folgenden Felder aus:
    
      - **Name**   Geben Sie in dieses Feld den Anzeigenamen für die automatische UM-Telefonzentrale ein. Ein Name für die automatische UM-Telefonzentrale ist erforderlich und muss eindeutig sein. Er dient jedoch nur zur Anzeige in der Exchange-Verwaltungskonsole und der Shell.
        
        Falls Sie den Namen für die automatische Telefonzentrale nach ihrer Erstellung ändern möchten, müssen Sie zunächst die vorhandene automatische UM-Telefonzentrale löschen und anschließend eine andere automatische Telefonzentrale mit dem gewünschten Namen erstellen. Wenn in Ihrer Organisation mehrere automatische UM-Telefonzentralen eingesetzt werden, sollten Sie aussagekräftige Namen für Ihre automatischen UM-Telefonzentralen verwenden. Die maximale Länge für den Namen einer automatischen UM-Telefonzentrale beträgt 64 Zeichen inklusive Leerzeichen.
        
        Wenngleich der Name einer neuen UM-Telefonzentrale Leerzeichen enthalten darf, ist bei der Integration von Unified Messaging in Office Communications Server 2007 R2 oder Microsoft Lync Server die Verwendung von Leerzeichen im Namen von automatischen Telefonzentralen nicht zulässig. Wenn Sie daher eine automatische Telefonzentrale mit Leerzeichen im Anzeigenamen erstellt haben und Sie eine Integration in Office Communications Server 2007 R2 oder Lync Server durchführen, müssen Sie diese automatische Telefonzentrale zunächst löschen und dann eine andere automatische Telefonzentrale erstellen, die keine Leerzeichen im Anzeigenamen enthält.
    
      - **Diese automatische Telefonzentrale als aktiviert erstellen**   Aktivieren Sie dieses Kontrollkästchen, wenn nach Abschluss der Erstellung der automatischen UM-Telefonzentrale die automatische Telefonzentrale eingehende Anrufe beantworten soll. Standardmäßig wird eine neue automatische Telefonzentrale als deaktiviert erstellt.
        
        Wenn Sie die automatische UM-Telefonzentrale als deaktiviert erstellen, können Sie sie nach Abschluss der Erstellung der automatischen Telefonzentrale in der Exchange-Verwaltungskonsole oder in der Shell aktivieren.
    
      - **Automatische Telefonzentrale zur Antwort auf Sprachbefehle einrichten**   Aktivieren Sie dieses Kontrollkästchen, um die automatische Telefonzentrale für die Spracherkennung zu aktivieren. Bei Sprachaktivierung der automatischen Telefonzentrale können Anrufer auf Systemansagen oder benutzerdefinierte Ansagen der automatischen UM-Telefonzentrale mit Tonwahl- oder Spracheingaben antworten. Standardmäßig wird die automatische Telefonzentrale bei ihrer Erstellung nicht sprachaktiviert.
        
        Damit Anrufern eine sprachaktivierte automatische Telefonzentrale in einer anderen Sprache als US-Englisch (en-US) zur Verfügung steht, müssen Sie das entsprechende UM-Sprachpaket installieren und die Eigenschaften der automatischen Telefonzentrale für die Verwendung dieser Sprache konfigurieren. Bei der Installation eines Postfachservers wird standardmäßig die US-englische Version (en-US) des UM-Sprachpakets installiert.
    
      - **Zugriffsnummern**   Verwenden Sie dieses Feld, um die Durchwahl- bzw. Telefonnummern einzugeben, die Anrufer zum Erreichen der automatischen Telefonzentrale verwenden. Geben Sie eine Durchwahlnummer in das Feld ein, und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"), um die Nummer der Liste hinzuzufügen. Die Anzahl von Ziffern der eingegebenen Durchwahl- oder Telefonnummer muss nicht mit der Anzahl von Ziffern einer Durchwahlnummer übereinstimmen, die im zugeordneten Satz UM-Wähleinstellungen konfiguriert ist. Der Grund dafür ist, dass direkte Anrufe bei automatischen UM-Telefonzentralen zulässig sind.
        
        Die Anzahl von Durchwahlnummern oder Pilot-IDs, die Sie eingeben können, ist unbegrenzt. Sie können die neue automatische Telefonzentrale jedoch auch ohne Durchwahl- oder Telefonnummer erstellen. Eine Durchwahl- oder Telefonnummer ist nicht erforderlich.
        
        Sie können eine vorhandene Durchwahlnummer oder Pilot-ID bearbeiten und löschen. Klicken Sie zum Bearbeiten einer vorhandenen Durchwahl- oder Telefonnummer auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"). Klicken Sie zum Entfernen einer vorhandenen Durchwahl- oder Telefonnummer aus der Liste auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

4.  Klicken Sie auf **Speichern**.

Vor der Bereitstellung

## Nach der Bereitstellung auszuführende Aufgaben für Unified Messaging

Nach Abschluss einer neuen Installation der Clientzugriffs- und Postfachserver und der erfolgreichen Bereitstellung von Unified Messaging sollten Sie die nach der Bereitstellung vorzunehmenden Aufgaben ausführen. Durch das Ausführen dieser Aufgaben können Sie Benutzer für Unified Messaging aktivieren, die UM-Bereitstellung sichern sowie Funktionen für den Faxempfang für UM-aktivierte Benutzer bereitstellen.

## Aktivieren von Benutzern für Voicemail

Nachdem Sie die VoIP-Gateways oder IP-Nebenstellenanlagen bereitgestellt, die Clientzugriffs- und Postfachserver installiert und die für Unified Messaging erforderlichen Komponenten erstellt haben, müssen Sie die Benutzer für Unified Messaging aktivieren. Weitere Informationen finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

## Schützen von Voicemail

Unified Messaging kann zur Verwendung der Active Directory-Rechteverwaltungsdienste (Active Directory Rights Management Services, AD RMS) konfiguriert werden, um Sprachnachrichten für eine Organisation zu schützen. Diese Funktion wird als geschützte Voicemail bezeichnet. Wenn eine Sprachnachricht geschützt ist, kann der Empfänger die Nachricht nicht weiterleiten. Darüber hinaus wird über Unified Messaging (UM) sichergestellt, dass nur der vorgesehene Empfänger der Nachricht auf deren Inhalte zugreifen kann. Auf geschützte Sprachnachrichten kann mithilfe von Microsoft Outlook 2010 oder höher, Outlook Web App und Outlook Voice Access zugegriffen werden. Weitere Informationen finden Sie unter [Schützen von Voicemail](protect-voice-mail-exchange-2013-help.md).

## MTLS für UM

Führen Sie folgende Aufgaben aus, um mithilfe von MTLS den SIP- und RTP-Datenverkehr (Real-Time Transport-Protokoll) zu verschlüsseln, der von den Clientzugriffs- und Postfachservern gesendet und empfangen wird:

  - Führen Sie den Assistenten für Exchange-Zertifikate aus. Weitere Informationen finden Sie unter [Bereitstellen von Zertifikaten für Unified Messaging](deploying-certificates-for-um-exchange-2013-help.md).

  - Importieren Sie das Zertifikat auf die Clientzugriffs- und Postfachserver.

  - Importieren Sie die erforderlichen Zertifikate auf die VoIP-Gateways sowie die IP-Nebenstellenanlagen und Clientzugriffs- und Postfachserver in Ihrer Organisation.

  - Konfigurieren Sie die VoIP-Sicherheit für die UM-Wähleinstellungen. Weitere Informationen finden Sie unter [Konfigurieren der VoIP-Sicherheitseinstellung](configure-the-voip-security-setting-exchange-2013-help.md).

  - Konfigurieren Sie den Startmodus auf den Clientzugriffs- und Postfachservern. Ausführliche Informationen finden Sie unter [Konfigurieren des Startmodus auf einem Postfachserver](configure-the-startup-mode-on-a-mailbox-server-exchange-2013-help.md) und [Konfigurieren des Startmodus auf einem Clientzugriffsserver](configure-the-startup-mode-on-a-client-access-server-exchange-2013-help.md).

  - Konfigurieren Sie die UM-IP-Gateways für die Überwachung von Port 5061. Weitere Informationen finden Sie unter [Konfigurieren Sie den Überwachungsport](configure-the-listening-port-exchange-2013-help.md).

## PIN-Richtlinien für UM-aktivierte Benutzer

In Unified Messaging werden PIN-Richtlinien in einer UM-Postfachrichtlinie festgelegt und konfiguriert. Wenn Sie einen Benutzer für Unified Messaging aktivieren, ordnen Sie den Benutzer einer vorhandenen UM-Postfachrichtlinie zu. Die UM-PIN-Richtlinien, die in der UM-Postfachrichtlinie konfiguriert werden, müssen auf den Sicherheitsanforderungen Ihrer Organisation basieren. Weitere Informationen zum Konfigurieren der PIN-Einstellungen für UM-aktivierte Benutzer finden Sie unter [Festlegen von Outlook Voice Access-PIN-Sicherheit](set-outlook-voice-access-pin-security-exchange-2013-help.md).

## Einrichten von Client-Voicemailfunktionen

Nachdem Sie Ihre Server und die benötigten UM-Komponenten bereitgestellt haben, können Sie optional weitere voicemailbezogene Funktionen konfigurieren. Weitere Informationen hierzu finden Sie unter folgenden Themen:

  - [Einrichten von Outlook Voice Access](setting-up-outlook-voice-access-exchange-2013-help.md)

  - [Zulassen, dass Voice Mailbenutzer Anrufe weitergeleitet werden sollen](allow-voice-mail-users-to-forward-calls-exchange-2013-help.md)

  - [Zulassen der Anzeige von Voicemailtranskriptionen für Benutzer](allow-users-to-see-a-voice-mail-transcript-exchange-2013-help.md)

  - [Aktivieren von Voicemailbenutzern für den Faxempfang](enable-voice-mail-users-to-receive-faxes-exchange-2013-help.md)


> [!IMPORTANT]
> Wenn Sie Ihre Unified Messaging-Umgebung in Microsoft Lync Server integrieren, sind weitere Planungsaspekte zu beachten. Weitere Informationen finden Sie unter <A href="deploying-exchange-2013-um-and-lync-server-overview-exchange-2013-help.md">Bereitstellen von Exchange 2013 UM und Lync-Server (Übersicht)</A>.



Vor der Bereitstellung

