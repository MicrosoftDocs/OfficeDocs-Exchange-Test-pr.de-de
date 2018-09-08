---
title: 'Aktivieren von Voicemailbenutzern für den Faxempfang: Exchange 2013 Help'
TOCTitle: Aktivieren von Voicemailbenutzern für den Faxempfang
ms:assetid: 451ab0ea-21e1-4c1f-ae62-4ba7cdfd1e4d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb232022(v=EXCHG.150)
ms:contentKeyID: 52062869
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren von Voicemailbenutzern für den Faxempfang

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2015-04-07_

Microsoft Exchange Unified Messaging (UM) ermöglicht die Zustellung von Voicemailnachrichten an das Postfach eines Benutzers sowie den Empfang von Faxnachrichten im Benutzerpostfach. Bei UM wird ein Fax in Form einer E-Mail-Nachricht an das Postfach des Benutzers geschickt, an die eine Bilddatei mit der Endung TIF angefügt ist. Der Benutzer kann die angefügte Datei mit einer Software öffnen, die Bilddateien mit der Erweiterung TIF verarbeiten kann. In diesem Thema wird die Faxfunktion und deren Funktionsweise in UM behandelt.


> [!NOTE]
> Unified Messaging ermöglicht Benutzern nicht das Senden ausgehender Faxnachrichten. Es gibt jedoch eine Reihe von Drittanbieterlösungen wie Internetfaxdienste, E-Mail-Faxdienste oder Faxserveranwendungen von Drittanbietern, mit denen ausgehende Faxnachrichten gesendet werden können.



**Inhalt**

Übersicht über die Faxübermittlung

Faxübermittlungsmethoden

T.38

Übersicht über die Faxkommunikation mit Unified Messaging

Empfangen eingehender Faxe

Verweismethoden für Faxanrufe

Konfigurieren der Faxübermittlung

Telefonnummern und Faxübermittlung

Journalfunktion bei UM-Faxnachrichten

## Übersicht über die Faxübermittlung

"Fax" ist eine Abkürzung für das Wort "Faksimile". Es handelt sich dabei um eine Technologie für die elektronische Übergabe von Dokumenten. Im Allgemeinen werden Faxnachrichten von Faxgeräten oder Computerfaxmodems über das Public Switched Telephone Network (PSTN), einem telefon- oder leitungsvermittelten Netzwerk, gesendet und empfangen. Allerdings können auch andere Optionen zum Senden und Empfangen von Faxnachrichten verwendet werden.

In den meisten Organisationen sollen Benutzer in der Lage sein, Faxnachrichten zu senden und zu empfangen. Organisationen verwenden für das Versenden und Empfangen von Faxnachrichten über das PSTN oder über das Internet eine oder mehrere der in der folgenden Liste aufgeführten Methoden. Jede dieser Methoden hat Vor- und Nachteile.

  - Herkömmliche Faxgeräte und computerbasierte Faxübermittlung

  - Faxübermittlung mit Faxservern oder Faxgateways

  - Faxübermittlung über ein VoIP-Netzwerk (Voice over IP)

  - Faxübermittlung mit einer E-Mail-Clientanwendung

Zum Senden einer Faxnachricht müssen Benutzer in einer Organisation möglicherweise folgende Schritte ausführen:

  - Ausdrucken einer Kopie des zu faxenden Dokuments und Senden der Faxnachricht mit einem Faxgerät.

  - Speichern des Dokuments auf ihrem Computer und Verwenden eines Faxmodems zum Senden der Faxnachricht. Dazu muss allerdings eine Telefonleitung am Computer angeschlossen sein.

  - Verwenden eines Internetfaxdiensts zum Faxen eines Dokuments über eine herstellerspezifische Softwareanwendung.

  - Senden einer ausgehenden Faxnachricht an einen Faxserver mithilfe einer Softwareanwendung, die den Faxserver nutzt.

Zum Empfangen einer Faxnachricht müssen Benutzer in einer Organisation möglicherweise folgende Schritte ausführen:

  - Empfangen einer Faxnachricht auf einem Faxgerät in der Organisation.

  - Empfangen einer Faxnachricht über ein auf dem Computer installiertes Faxmodem.

  - Empfangen einer Faxnachricht über einen Internetfaxdienst.

  - Empfangen einer Faxnachricht über einen Faxserver, der in einem Netzwerk konfiguriert ist.

  - Empfangen einer Faxnachricht vom Server eines Faxpartners, der Unified Messaging zum Zustellen der Faxnachricht über ein VoIP-Netzwerk verwendet.

Übersicht über die Faxübermittlung

## Faxübermittlungsmethoden

Es gibt unterschiedliche Möglichkeiten, Faxnachrichten zu senden und zu empfangen:

**Herkömmliche Faxgeräte und computerbasierte Faxübermittlung**   Ein Scanner, ein Faxmodem in einem Computer, ein Drucker mit integrierter Faxfunktion oder ein spezielles Faxgerät können zum Senden und Empfangen von Faxnachrichten verwendet werden. Alle diese Geräte übertragen Daten in Form von Impulsen über eine Telefonleitung an ein anderes Faxmedium, meist ein anderes Faxgerät oder einen Computer mit einem Faxmodem. Die Impulse werden dann in Bilder umgewandelt oder zum Drucken des Bildes auf Papier verwendet.

Für die herkömmliche Faxmethode ist mindestens eine Telefonleitung am Sende- und am Empfangsgerät erforderlich. Es kann jeweils nur ein Fax gesendet oder empfangen werden. Ein Nachteil beim Senden und Empfangen von Faxnachrichten über ein Faxmodem besteht darin, dass der Computer eingeschaltet sein und eine Faxsoftware oder einen Faxdienst ausführen muss. Bei dieser computerbasierten Art der Faxübermittlung wird weder für das Senden noch das Empfangen das Internet verwendet.

**Herkömmliche und computerbasierte Faxübermittlung**

![Konventioneller Faxversand](images/Bb232022.7bdc1cab-9504-4314-a6e0-eccdfe2a9cd6(EXCHG.150).gif "Konventioneller Faxversand")

**Faxserver oder Faxgateways und Internetfaxdienste**   Es gibt mehrere Methoden, Faxnachrichten über das Internet zu senden und zu empfangen. Dazu gehört auch die Verwendung einer Softwareanwendung auf einem Computer oder eines E-Mail-Clients zum Empfangen von Faxnachrichten. In den meisten Fällen ist bei dieser Faxmethode ein Faxserver oder Faxgateway für die Umwandlung von Fax zu E-Mail erforderlich. Diese Methode wird immer häufiger eingesetzt, da Organisationen auf zusätzliche Faxgeräte verzichten können. Außerdem müssen keine zusätzlichen Telefonleitungen installiert werden. Bei dieser Art der Faxübermittlung muss das Dokument, einschließlich eines Deckblatts mit den korrekten ID-Informationen, erstellt und an ein herkömmliches Faxgerät gesendet werden. Der Benutzer verwendet beispielsweise eine Softwareanwendung wie Microsoft Word oder Microsoft Outlook, um das Fax zu erstellen und an den Faxserver oder an das Faxgateway zu senden. Der Faxserver oder das Faxgateway empfängt das Fax und sendet es über eine herkömmliche Telefonleitung an ein Faxgerät oder ein Faxmodem, das auf einem Computer installiert ist.

**Faxübermittlung mit Faxservern oder Faxgateways**

![Versenden von Faxnachrichten mit Faxservern/-gateways](images/Bb232022.d6fa2402-b4ca-4313-956c-62e5fe7731ad(EXCHG.150).gif "Versenden von Faxnachrichten mit Faxservern/-gateways")

Mit Internetfaxdiensten können Benutzer Faxnachrichten von einem Computer über das Internet versenden. Mithilfe einer Softwareanwendung wie Word oder Outlook können Faxnachrichten erstellt und an den Internetfaxdienst gesendet werden. Viele Unternehmen bieten Internetfaxdienste in Form eines Abonnements oder mit separater Abrechnung pro gesendetem Fax an. Die Verwendung von Internetfaxdiensten bietet folgende Vorteile:

  - Es ist kein Faxgerät erforderlich.

  - Es muss keine Software oder Hardware installiert werden.

  - Es sind keine speziellen Telefonleitungen erforderlich.

  - Die Vertraulichkeit ist gewahrt.

  - Gleichzeitiges Senden mehrerer Faxnachrichten ist möglich.

  - Der Empfang von Faxnachrichten bei ausgeschaltetem Computer ist möglich.

Die folgende Abbildung zeigt die Verwendung von Internetfaxdiensten zum Senden und Empfangen von Faxnachrichten.

**Internetfaxdienste**

![Internetfaxdienste](images/Bb232022.5d0fb3d6-95f4-4fbf-80e5-64f5de553e65(EXCHG.150).gif "Internetfaxdienste")

**Faxübermittlung mit einer E-Mail-Clientanwendung**   Faxnachrichten können mithilfe eines Faxgeräts über das Internet gesendet und empfangen und dann von einem E-Mail-Client wie Outlook empfangen werden.

Mithilfe des T.37-Protokolls können Faxgeräte Faxnachrichten über das Internet an einen E-Mail-Client senden. Ein Fax wird dabei über das Internet als E-Mail-Anlagen, üblicherweise als TIF- oder PDF-Dateien, gesendet. Bei dieser Faxmethode sind Faxgeräte mit iFax- oder T.37-Unterstützung erforderlich sowie eine E-Mail-Adresse für die Sende- und Empfangsfaxgeräte. Damit herkömmliche Faxgeräte und Faxmodems weiterhin verwendet werden können, unterstützen alle T.37-Faxgeräte die Standardfaxübermittlung per Telefonleitung. In einigen Fällen können T.37-Faxgeräte auch genutzt werden, wenn ein Faxgateway verwendet wird. Die folgende Abbildung zeigt die Verwendung von Faxgeräten mit T.37-Unterstützung und E-Mail-Clients zum Senden und Empfangen von Faxnachrichten.

**Versenden einer Faxnachricht per E-Mail**

![Versenden einer Faxnachricht per E-Mail](images/Bb232022.086f086b-dc39-4439-a694-7a98e03e65d1(EXCHG.150).gif "Versenden einer Faxnachricht per E-Mail")

**Faxübertragung mithilfe eines VoIP-Netzwerks**   VoIP (Voice over IP) ist eine Technologie, die Hard- und Software bereitstellt, sodass ein IP-basiertes Netzwerk als Übertragungsmedium für Telefonate verwendet werden kann. In einem VoIP-Netzwerk werden Sprach- und Faxdaten in Form von Paketen über das Internetprotokoll (IP) gesendet, statt konventioneller Leitungsübertragungen bzw. leitungsvermittelter Telefonleitungen des PSTN. Ein VoIP-Gateway, das Sie mit Ihrem IP-Netzwerk verbinden, verwendet VoIP zum Senden von Sprachdatenpaketen zwischen einem Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Dienst für die Anrufweiterleitung ausgeführt wird, und einem Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, sowie einem Nebenstellenanlagensystem (Private Branch eXchange, PBX). Sie können auch eine IP-Nebenstellenanlage verwenden, die die Funktionen eines VoIP-Gateways und einer Nebenstellenanlage übernimmt.

Es gibt zwei grundlegende Typen von leitungsvermittelten Netzwerken: Ein leitungsvermitteltes Netzwerk ist ein Netzwerk, in dem eine dedizierte Verbindung besteht. Eine dedizierte Verbindung ist ein Schaltkreis oder eine Leitung, der bzw. die zwischen zwei Knoten eingerichtet wird, um diesen die Kommunikation untereinander zu ermöglichen. Nachdem ein Anruf zwischen zwei Knoten aufgebaut wurde, kann die Verbindung nur von diesen beiden Knoten verwendet werden. Wenn der Anruf von einem der beiden Knoten beendet wird, wird auch die Verbindung unterbrochen. In leitungsvermittelten Netzwerken, wie z. B. PSTN, werden mehrere Anrufe über dasselbe Übertragungsmedium übermittelt. Häufig handelt es sich bei dem im PSTN verwendeten Medium um Kupferkabel. Es können aber auch Glasfaserkabel verwendet werden.

In paketvermittelten Netzwerken wie dem Internet oder einem LAN (Local Area Network) werden Pakete über die zweckmäßigste Route an ihr Ziel geleitet, wobei aber nicht alle Pakete zwischen zwei Hosts dieselbe Route nehmen, auch nicht, wenn sie von einer einzigen Nachricht stammen. Bei dieser Vorgehensweise kann man davon ausgehen, dass die Pakete zu unterschiedlichen Zeiten und nicht in der richtigen Reihenfolge ankommen. In einem paketvermittelten Netzwerk werden Pakete (Nachrichten oder Fragmente von Nachrichten) einzeln zwischen Knoten über Datenverbindungen geroutet, die für andere Knoten freigegeben werden können. Bei der Paketvermittlung wird die verfügbare Bandbreite im Gegensatz zur Leitungsvermittlung für mehrere Verbindungen mit Knoten im Netzwerk freigegeben. Paketvermittelte Netzwerke haben das Internet erst ermöglicht und gleichzeitig die Verfügbarkeit von Datennetzwerken, insbesondere LAN-basierten IP- und VoIP-Netzwerken, wesentlich erhöht und diese verbreitet.

Übersicht über die Faxübermittlung

## T.38

T.38 ist ein Faxübermittlungsstandard und -protokoll, der die Faxübermittlung in einem IP-basierten Netzwerk ermöglicht. Ein IP-basiertes Netzwerk, das das T.38-Protokoll einsetzt, verwendet zum Senden einer Nachricht an das Empfängerpostfach SMTP (Simple Mail Transfer Protocol) und MIME (Multipurpose Internet Mail Extension). T.38 ermöglicht IP-Faxübertragungen für IP-fähige Faxgeräte und Faxgateways. Die Geräte können auf IP-Netzwerken basierende Hosts umfassen, wie etwa Clientcomputer und Drucker. In Exchange Unified Messaging stellen die Faxdateien separate Dokumente dar, die als TIF-Dateien codiert und einer E-Mail-Nachricht als Anlage beigefügt sind. Sowohl die E-Mail-Nachricht als auch die TIF-Dateianlage werden an das UM-aktivierte Postfach des Benutzers gesendet.

Unified Messaging basiert auf der Fähigkeit des Gateways, TDM-Protokolle (Time Division Multiplex) oder leitungsvermittelte Telefonieprotokolle, wie etwa ISDN (Integrated Services Digital Network) oder QSIG, von einer Nebenstellenanlage in IP- oder VoIP-basierte Protokolle, wie beispielsweise SIP (Session Initiation Protocol), RTP (Real-Time Transport Protocol) oder T.38 für den Empfang von Faxnachrichten, zu übersetzen bzw. umzuwandeln. Das VoIP-Gateway ist ein integraler Bestandteil und Voraussetzung für die Funktionalität und den Betrieb von Unified Messaging. Das VoIP-Gateway ist zuständig für das Abtasten von Faxsignalen. Clientzugriffs- und Postfachserver benötigen das VoIP-Gateway zum Senden einer Benachrichtigung, wenn eine Faxnachricht erkannt wurde. Die Clientzugriffs- und Postfachserver handeln dann die Mediensitzung neu aus und verwendet das T.38-Protokoll.

Übersicht über die Faxübermittlung

## Übersicht über die Faxkommunikation mit Unified Messaging

In Unified Messaging erhält der Benutzer Faxdateien als separate Dokumente, die als TIF-Bilddateien codiert und einer E-Mail-Nachricht als Anlage beigefügt sind. Sowohl die E-Mail-Nachricht als auch die TIF-Dateianlage werden an das UM-aktivierte Postfach des Benutzers gesendet.

Das Senden einer Faxnachricht an das Postfach des Benutzers besitzt mehrere Vorteile. Hierzu gehören die folgenden Vorteile:

  - Die Anzahl der physischen oder herkömmlichen Faxgeräte kann reduziert werden.

  - Die Anzahl von für die Faxübermittlung genutzten Telefonleitungen in einer Organisation kann verringert werden, da der Postfachserver in der Lage ist, mehrere Faxnachrichten in eine Warteschlange zu verschieben und die einzelnen Faxnachrichten zu senden, sobald die Telefonleitung frei ist.

  - Faxe, die als TIF-Bilddatei empfangen werden, weisen eine bessere Qualität als herkömmliche Faxe auf. Eingehende Faxe können von einem lokalen oder freigegebenen Drucker gedruckt werden.

  - An ein Benutzerpostfach gesendete Faxnachrichten sind sicherer, da die Gefahr, dass eine andere Person als der Empfänger das Fax an sich nimmt, wesentlich geringer ist.

  - Benutzer können Faxnachrichten direkt an ihrem Schreibtisch empfangen.

  - Eingehende Faxnachrichten können auf die Einhaltung der Sicherheitsrichtlinien einer Organisation geprüft werden.

Eine Faxnachricht kann nur an einen einzelnen UM-aktivierten Benutzer gesendet werden. Die Weiterleitung von Faxnachrichten an eine Verteilerliste ist bei Unified Messaging nicht möglich. Wenn Sie diese Funktionalität benötigen, müssen Sie die folgenden Schritte ausführen:

1.  Erstellen Sie ein Postfach, das den Faxanruf entgegennimmt. Dieses wird als Postfach für die Verteilerliste verwendet.

2.  Aktivieren Sie das Postfach der Verteilerliste für UM.

3.  Erstellen Sie eine Regel für dieses UM-aktivierte Postfach. Legen Sie in der Regel fest, dass alle Nachrichten an die ausgewählte Verteilerliste weitergeleitet werden.

Übersicht über die Faxübermittlung

## Empfangen eingehender Faxe

Der Empfang von Faxnachrichten in einem VoIP-Netzwerk unterscheidet sich von dem Empfang mit einem standardmäßigen Faxgerät oder über einen Faxserver in einem IP-basierten Netzwerk. Damit Faxnachrichten über ein VoIP-Netzwerk gesendet und empfangen werden können, müssen Sie über ein VoIP-Gateway oder eine IP-Nebenstellenanlage mit T.38-Protokollunterstützung sowie über einen Server verfügen, der ebenfalls T.38 unterstützt. T.38 ermöglicht IP-basierte Faxübermittlung bei IP-netzwerkbasierten Hosts, z. B. Clientcomputer sowie Drucker mit integrierter Faxfunktion und Server wie einem Postfachserver.


> [!IMPORTANT]
> Das Senden und Empfangen von Faxen mithilfe von T.38 oder G.711 wird in einer Umgebung, in der Unified Messaging und Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server integriert sind, nicht unterstützt.



Wenn eine Nebenstellenanlage einen Anruf empfängt, wird dieser Anruf an die entsprechende Durchwahl weitergeleitet. Wird der Anruf an der Durchwahlnummer des Benutzers nicht entgegengenommen, leitet die Nebenstellenanlage ihn an ein VoIP-Gateway weiter. Dieses wiederum leitet den Anruf an den entsprechenden Postfachserver weiter. Der Postfachserver ermittelt über das für den Anruf genutzte Protokoll, ob es sich um einen Sprachanruf oder um einen Faxanruf handelt. Bei Verwendung des SIP-Protokolls verarbeitet der Postfachserver den Anruf als Sprachnachricht. Wenn jedoch das VoIP-Gateway das T.38-Protokoll verwendet, erkennt der Postfachserver, dass es sich um einen Faxanruf handelt und verarbeitet diesen wie im folgenden Absatz beschrieben. Ein Postfachserver leitet eingehende Faxanrufe an einen dafür vorgesehenen Faxpartnerserver weiter, der dann die Faxverbindung mit dem Faxabsender aufbaut und die Nachricht für den UM-aktivierten Benutzer empfängt. Der Server des Faxpartners sendet das Fax, das als TIF-Anlage in die SMTP-Nachricht eingeschlossen ist, dann an das Postfach des Empfängers.

Wenn ein eingehendes T.38-Faxsignal vom VoIP-Gateway an einen Postfachserver gesendet wird, fragt der Postfachserver das Verzeichnis mittels LDAP (Lightweight Directory Access Protocol) ab, um festzustellen, ob der vorgesehene Empfänger des eingehenden Faxanrufs eingehende Faxnachrichten empfangen darf, und um die SIP-Adresse des Faxpartnerservers zu ermitteln. Nach Überprüfung dieser Informationen sendet der Postfachserver eine Verweisanforderung für den Faxanruf an das VoIP-Gateway oder den SIP-Peer, das bzw. der die Faxanforderung dann an den Faxpartnerserver weiterleitet. Nachdem der Faxanruf erfolgreich hergestellt wurde, sendet der Faxabsender das Faxmedium und die Faxdaten an den Faxpartnerserver. Sobald der Faxpartnerserver die Faxmedien und -daten erhalten hat, sendet er über SMTP eine E-Mail-Nachricht an einen Postfachserver. Diese Nachricht enthält eine TIF-Datei der Faxnachricht und besondere X-Kopfzeilen für den vorgesehenen Faxempfänger.

Nachdem die Faxnachricht authentifiziert und von einem gültigen Faxpartnerserver gesendet wurde, gibt der UM-Postfach-Assistent auf dem Postfachserver einen RPC-Aufruf an den Microsoft Exchange Unified Messaging-Dienst aus. Auf diese Weise wird sichergestellt, dass die Eigenschaften der Faxnachricht denjenigen von Faxnachrichten entsprechen, die von einem Postfachserver erstellt werden. Der Postfachserver übermittelt dann die endgültige Faxnachricht, die die E-Mail-Nachricht und die TIF-Anlage für das eingehende Fax enthält. Danach wird die vollständige und formatierte Version der Faxnachricht mittels MAPI RPC dem Postfachserver zugestellt, der das Postfach des vorgesehenen Empfängers enthält.

Übersicht über die Faxübermittlung

## Verweismethoden für Faxanrufe

Ein eingehender Faxanruf kann einem Postfachserver entweder mittels erneuter SIP-INVITE-Anforderung vom VoIP-Gateway oder vom SIP-Peer (Mediengateway), mittels CNG-Benachrichtigung (anrufender Faxton) durch den SIP-Peer oder mittels CNG-Erkennung durch den Postfachserver signalisiert werden. In den folgenden Unterabschnitten wird der Faxanrufverweis für jeden einzelnen Fall ausführlich beschrieben.

## REINVITE von einem SIP-Peer

Ein für eine UM-Pilotnummer eingehender Anruf wird als INVITE mit einem SDP-Voiceprofil (RTP/Audio) an UM geleitet

1.  UM nimmt die Einladung an, und Mediendatenströme werden eingerichtet. Nach der Einrichtung des Anrufs initiiert der Anrufer die Faxübertragung.

2.  Der SIP-Peer erkennt den anrufenden Faxton (CNG). Der SIP-Peer gibt eine REINVITE-Anforderung an den Postfachserver aus und gibt nunmehr ein Faxprofil (T.38 oder G.711) im SDP an.

3.  UM antwortet auf die REINVITE-Anforderung mit dem Signal "200 OK", das den SIP-Peer in den Zustand "Gehalten" versetzt.

4.  UM gibt einen REFER-Befehl aus, mit dem der SIP-Peer (CNG) an einen Endpunkt einer Faxpartnerlösung verwiesen wird, der aus den Konfigurationsdaten abgerufen wurde.

5.  Der SIP-Peer sendet den INVITE-Befehl für die Faxsitzung an die Partnerlösung.

6.  Die Faxpartnerlösung akzeptiert den INVITE-Befehl, und eine Mediensitzung mit dem SIP-Peer wird eingerichtet.

## CNG-Benachrichtigung von einem SIP-Peer

Ein für eine UM-Pilotnummer eingehender Anruf wird als INVITE mit einem SDP-Voiceprofil (RTP/Audio) an UM geleitet.

1.  UM nimmt die Einladung an, und Mediendatenströme werden eingerichtet. Nach der Einrichtung des Anrufs initiiert der Anrufer die Faxübertragung.

2.  Der SIP-Peer erkennt den anrufenden Faxton (CNG). Der SIP-Peer benachrichtigt den UM-Server über die Faxnachricht, indem er eine CNG-Benachrichtigung im RFC 4733-Format über den RTP-Datenstrom sendet.

3.  UM gibt als Antwort auf die Benachrichtigung unmittelbar einen REFER-Befehl aus, sodass der SIP-Peer an einen Endpunkt einer Faxpartnerlösung verwiesen wird, der aus den Konfigurationsdaten abgerufen wurde.

4.  Der SIP-Peer sendet den INVITE-Befehl für die Faxsitzung an die Partnerlösung.

5.  Die Faxpartnerlösung nimmt die Einladung an.

6.  Eine Mediensitzung mit dem SIP-Peer wird eingerichtet.

## CNG-Erkennung durch einen Postfachserver

Ein für eine UM-Pilotnummer eingehender Anruf wird als INVITE mit einem SDP-Voiceprofil (RTP/Audio) an UM geleitet. UM nimmt die Einladung an, und Mediendatenströme werden eingerichtet.

1.  Nach der Einrichtung des Anrufs initiiert der Anrufer die Faxübertragung.

2.  Der Postfachserver erkennt den Faxton (CNG) im RTP-Audiodatenstrom.

3.  UM gibt als Antwort auf die Benachrichtigung unmittelbar einen REFER-Befehl aus, sodass der SIP-Peer an einen Endpunkt einer Faxpartnerlösung verwiesen wird, der aus den Konfigurationsdaten abgerufen wurde.

4.  Der SIP-Peer sendet den INVITE-Befehl für die Faxsitzung an die Partnerlösung.

5.  Die Faxpartnerlösung nimmt die Einladung an.

6.  Eine Mediensitzung mit dem SIP-Peer wird eingerichtet.

Übersicht über die Faxübermittlung

## Konfigurieren der Faxübermittlung

Beim Installieren des Postfachservers wird der Server nicht standardmäßig für die Verarbeitung eingehender Faxanrufe und die anschließende Zustellung an einen UM-aktivierten Benutzer konfiguriert. Zur Konfiguration von UM mit einem Faxpartnerserver müssen Sie die UM-Postfachrichtlinie sowie die Authentifizierung zwischen dem Postfachserver und dem Faxpartnerserver konfigurieren. Weitere Informationen finden Sie unter [Einrichten von eingehenden Faxen](setting-up-incoming-faxing-exchange-2013-help.md).

Übersicht über die Faxübermittlung

## Telefonnummern und Faxübermittlung

In Exchange Unified Messaging stehen folgende Optionen zur Verfügung, wenn Sie den Faxempfang für UM-aktivierte Benutzer konfigurieren:

  - Eine DID-Telefonnummer (Direct Inward Dial) für einen einzelnen Benutzer, die sowohl für Faxnachrichten als auch für Voicemail verwendet wird.

  - Eine separate DID-Telefonnummer, die für einen einzelnen Benutzer für den Empfang von Faxnachrichten verwendet wird.

  - Eine zentrale Faxnummer für alle Benutzer, auf der alle Faxnachrichten eingehen.

## Eine einzelne DID-Telefonnummer

Wenn Sie einen Benutzer für Unified Messaging über die Seite **UM-Postfach aktivieren** oder über das Cmdlet **Enable-UMMailbox** aktivieren, müssen Sie mindestens eine Durchwahlnummer für den Benutzer angeben. Diese Durchwahlnummer gilt nur für einen Benutzer und darf in einem bestimmten Satz Wähleinstellungen nur einmal vorkommen. Unified Messaging verwendet diese Durchwahl zum Suchen des richtigen Benutzers. Zudem wird sie für die Zustellung von Sprach- und Faxnachrichten an das Postfach des Benutzers verwendet. Weitere Informationen finden Sie unter [Enable-UMMailbox](https://technet.microsoft.com/de-de/library/aa998033\(v=exchg.150\)).

Mit einer einzelnen DID-Nummer können Sie die Faxübermittlung so konfigurieren, dass ein Benutzer eine einzelne DID-Nummer sowohl für Sprach- als auch für Faxnachrichten verwendet. Diese Konfiguration ist einfach zu verwalten, und es werden keine zusätzlichen DID-Nummern verschwendet. Wenn bei Eingang eines Faxanrufs der Benutzer abwesend ist oder gerade telefoniert, nimmt UM den Anruf an, erkennt das Faxsignal, erstellt eine Faxnachricht und sendet diese an den Benutzer.

Wenn ein Benutzer, dessen Faxübermittlung mit einer einzigen DID-Telefonnummer konfiguriert ist, einen Anruf von einem Faxgerät erhält, während er anwesend und nicht im Telefongespräch ist, stehen folgende Möglichkeiten zur Verfügung:

  - Wenn es klingelt, nimmt er den Anruf nicht entgegen, sodass der Faxanruf von einem Postfachserver angenommen und weitergeleitet wird. Die Faxnachricht wird erstellt und an das Postfach des Benutzers weitergeleitet.

  - Er nimmt den Faxanruf entgegen und leitet ihn an sich selbst weiter, sodass ein Postfachserver den Anruf annimmt und weiterleitet. Die Faxnachricht wird erstellt und an das Postfach des Benutzers weitergeleitet.

  - Er wartet darauf, dass der Anrufer einen erneuten Faxsendeversuch startet, und lässt den Faxanruf an einen Postfachserver weiterleiten.

Bei Verwendung einer einzelnen DID-Nummer muss der Benutzer zusätzliche Aktionen ausführen, um Faxnachrichten zu empfangen.

Übersicht über die Faxübermittlung

## Mehrere DID-Telefonnummern

Wenn Sie einen Benutzer für Unified Messaging aktivieren, müssen Sie mindestens eine Durchwahlnummer für diesen Benutzer eingeben. Mithilfe der Exchange-Verwaltungskonsole können Sie mehrere Durchwahlnummern für einen UM-aktivierten Benutzer hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen einer Durchwahlnummer](https://technet.microsoft.com/de-de/library/Dd335124(v=EXCHG.150)).

Das Hinzufügen mehrerer Durchwahlnummern ist für einen UM-aktivierten Benutzer in folgenden Fällen nützlich:

  - Beim Empfang vieler Faxnachrichten.

  - Wenn zum Empfangen von Faxnachrichten kein Anruf entgegengenommen werden soll.

  - Wenn beim Entgegennehmen von Telefonaten kein Faxsignal ertönen soll.

Das Hinzufügen mehrerer Durchwahlnummern ist im Vergleich zu einer einzelnen Durchwahlnummer komplexer und erfordert unter Umständen zusätzliche Konfigurationseinstellungen auf einer PBX- oder IP-PBX-Anlage. Zum Konfigurieren mehrerer Durchwahlnummern für einen UM-aktivierten Benutzer müssen DID-Durchwahlnummern verfügbar sein, die in der Organisation noch nicht genutzt werden. Die Verwendung mehrerer Nummern für einen UM-aktivierten Benutzer ist nicht empfehlenswert, wenn die Organisation nur über eine begrenzte Anzahl von DID-Durchwahlnummern verfügt.

Der Vorteil mehrerer DID-Durchwahlnummern besteht darin, dass ein UM-aktivierter Benutzer Sprachanrufe auf der einen DID-Durchwahlnummer und Faxanrufe auf der anderen empfängt. Die Verwendung separater DID-Nummern für Voicemail und Faxanrufe ist für den Benutzer einfacher.

Wenn Sie zwei DID-Durchwahlnummern für einen bestimmten Benutzer konfigurieren, können diese aus unterschiedlichen UM-Wähleinstellungen stammen. Für die Verwendung von zwei DID-Nummern können Sie einen Wählplan erstellen und einen Postfachserver als dedizierten Server für den Empfang von Faxanrufen und die Weiterleitung von Faxnachrichten an die Benutzer verwenden. Weitere Informationen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

Bei der Konfiguration mehrerer DID-Durchwahlnummern für UM-aktivierte Benutzer stehen folgende Optionen zur Verfügung:

  - **Eine Durchwahl für Fax ohne Unified Messaging und eine für Voicemail**   Dieser Konfigurationstyp wird für jeden Benutzer einzeln aktiviert. Er wird verwendet, wenn zusätzliche oder nicht verwendete DID-Durchwahlnummern zur Verfügung stehen. Eine DID-Durchwahlnummer wird als Voicemailnummer und die andere als Faxnummer des Benutzers veröffentlicht. Sprachanrufe, die angenommen werden, weil der Benutzer den Anruf nicht entgegennimmt oder ein Besetztzeichen ertönt, werden an einen Postfachserver weitergeleitet. Eine Sprachnachricht wird erstellt und an das Postfach des UM-aktivierten Benutzers gesendet. Die andere Durchwahlnummer kann einem Faxgerät oder einem anderen Computer mit Faxmodem zugewiesen werden. Bei dieser Konfiguration verarbeitet ein Postfachserver keine Faxanrufe, und Faxnachrichten werden nicht an das Postfach des UM-aktivierten Benutzers gesendet.

  - **Eine Durchwahl für Fax und eine für Voicemail**   Dieser Konfigurationstyp wird für jeden Benutzer einzeln aktiviert. Er wird verwendet, wenn die Organisation über viele DID-Durchwahlnummern verfügt. In dieser Konfiguration werden beide DID-Durchwahlnummern an einen Postfachserver weitergeleitet, wenn der Anruf nicht entgegengenommen wird oder das Besetztzeichen ertönt. Dieser erstellt dann abhängig von der gewählten DID-Durchwahlnummer eine Sprach- oder eine Faxnachricht. Auch wenn der Benutzer eine Nummer für Voicemail und eine andere für Faxanrufe angibt, erkennt der Postfachserver den Anruftyp, der auf der DID-Durchwahlnummer eingeht, und kann eine Sprach- oder Faxnachricht für beide DID-Durchwahlnummern erstellen. Dies ist besonders hilfreich, wenn ein Benutzer kein separates Faxgerät bzw. keinen dedizierten Computer mit Faxmodem für eingehende Faxanrufe besitzt.

  - **Eine "Phantomdurchwahlnummer" für Faxnachrichten und eine für Voicemail**   Dieser Konfigurationstyp wird für jeden Benutzer einzeln aktiviert. Im Grunde handelt es sich hierbei um die gleiche Konfiguration wie bei zwei DID-Nummern (eine für Fax- und eine für Sprachanrufe). In dieser Konfiguration jedoch wird die für Faxanrufe verwendete Nummer des UM-aktivierten Benutzers in der PBX-Anlage als "Phantomdurchwahlnummer �" konfiguriert. Auf dieser "Phantom"-DID-Durchwahlnummer eingehende Anrufe werden immer an einen Postfachserver weitergeleitet.
    
    Der Vorteil dieser Konfigurationsart besteht darin, dass eingehende Faxanrufe von einem Postfachserver angenommen werden. Wenn das Telefon klingelt, der Anruf jedoch nicht entgegengenommen wird, erstellt der Postfachserver ein Fax und leitet es an das Postfach des UM-aktivierten Benutzers weiter, ohne diesen zu stören. Dies ist automatisch möglich, weil sich kein Telefon- oder Faxgerät in der Nähe des Benutzers befindet und er deshalb kein Klingeln bei eingehenden Anrufen hört.
    
    Der Nachteil bei dieser Konfiguration ist, dass Sie über zusätzliche DID-Durchwahlnummern verfügen müssen. Außerdem muss die PBX- oder IP-PBX-Anlage für die Weiterleitung des Anrufs an einen Postfachserver konfiguriert werden.

## Zentrale Faxnummer

Wenn Sie einen Benutzer über die Seite **UM-Postfach aktivieren** oder über das Cmdlet **Enable-UMMailbox** aktivieren, müssen Sie mindestens eine Durchwahlnummer für den Benutzer angeben. Wenn Sie jedoch eine zentrale Faxnummer für eingehende Faxnachrichten konfigurieren möchten, müssen Sie ein separates UM-aktiviertes Postfach zum Empfangen aller Faxanrufe einrichten.

Bei einigen Organisationen, insbesondere wenn diese täglich viele Faxnachrichten erhalten, muss möglicherweise eine Faxnummer für die gesamte Organisation veröffentlicht werden. Diese Faxnummer wird dann von sämtlichen Anrufern verwendet, die Faxnachrichten an Benutzer der Organisation senden.

Wenn eine Faxnummer für die gesamte Organisation veröffentlicht wird, kann die Organisation steuern, welche Faxtypen von Benutzern empfangen werden. Der Vorteil dieser Konfiguration besteht darin, dass nur eine einzelne DID-Durchwahlnummer oder eine externe Telefonnummer erforderlich ist. Außerdem ist keine separate DID-Nummer für die Faxübermittlung für die einzelnen UM-aktivierten Benutzer erforderlich. Allerdings ist entsprechendes Personal erforderlich, das eingehende Faxnachrichten anhand der Informationen auf dem Deckblatt oder der Nachricht selbst an die Benutzer verteilt.


> [!NOTE]
> In Exchange Unified Messaging ist die Verwendung einer zentralen Faxnummer mit OCR (Optical Character Recognition, optische Zeichenerkennung) nicht verfügbar. Diese Art der Konfiguration kann eine zentrale Faxnummer verwenden. Statt einer Weiterleitung an den Empfänger durch entsprechendes Personal empfängt die Faxsoftware das Fax, führt OCR durch und versucht den Empfänger anhand der Informationen auf dem Deckblatt oder in der Faxnachricht zu ermitteln.



Die Verwendung einer einzigen Faxnummer für die gesamte Organisation ist in folgenden Situationen nützlich:

  - Ein Benutzer innerhalb der Organisation empfängt für eine effektive Verwaltung zu viele Faxnachrichten in seinem Postfach.

  - Ein Benutzer empfängt zu viele Spam-Faxnachrichten in seinem Postfach.

  - Die Unternehmensanforderungen sind zu komplex, um die Erstellung einer Transportregel zu gewährleisten, durch die eingehende Faxnachrichten angenommen und an das beabsichtigte Postfach weitergeleitet werden. Dies ist möglicherweise der Fall, wenn in Ihrer Organisation bestimmte Faxnachrichten an eine Gruppe und andere an eine andere Gruppe geleitet werden soll. Weitere Informationen finden Sie unter [Nachrichtenfluss- oder Transportregeln](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md).

  - Das Filtern von Faxnachrichten mit Outlook ist nicht effektiv.

Übersicht über die Faxübermittlung

## Journalfunktion bei UM-Faxnachrichten

Viele Organisationen, die die Journalfunktion implementieren, verwenden möglicherweise auch Unified Messaging, um ihre E-Mail-, Voicemail- und Faxinfrastruktur zu konsolidieren. Möglicherweise wünschen Sie jedoch nicht, dass der Journalvorgang Journalberichte für Nachrichten generiert, die von Unified Messaging generiert werden. In diesem Fall können Sie entscheiden, ob Voicemailnachrichten und Benachrichtigungen über verpasste Anrufe, die von einem Postfachserver verarbeitet werden, erfasst oder übersprungen werden sollen. Wenn in Ihrer Organisation die Erfassung von Voicemail und Benachrichtigungen über verpasste Anrufe nicht erforderlich ist, können Sie den Speicherplatz, der zum Speichern von Journalberichten benötigt wird, verringern, indem Sie diese Nachrichten nicht berücksichtigen. Wenn Sie den Journalvorgang für Voicemailnachrichten und Benachrichtigungen über verpasste Anrufe aktivieren bzw. deaktivieren, wird diese Änderung auf alle Transportdienste in Ihrer Organisation angewendet. Weitere Informationen finden Sie unter [Journale](journaling-exchange-2013-help.md).


> [!NOTE]
> Nachrichten, die von einem Postfachserver generierte Faxe enthalten, werden immer erfasst, selbst wenn Sie eine Journalregel konfigurieren, die keine Erfassung von Unified Messaging-Voicemailnachrichten und Benachrichtigungen über verpasste Anrufe festlegt.



Übersicht über die Faxübermittlung

