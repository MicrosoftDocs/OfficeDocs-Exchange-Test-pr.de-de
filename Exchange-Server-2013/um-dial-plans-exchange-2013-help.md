---
title: 'UM-Wählpläne: Exchange 2013 Help'
TOCTitle: UM-Wählpläne
ms:assetid: ed7afc03-94af-4b23-8745-6a61f203c149
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125151(v=EXCHG.150)
ms:contentKeyID: 50477003
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# UM-Wählpläne

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-21_

Unified Messaging-Wählpläne (UM) sind die wichtigste Komponente von Unified Messaging und für eine erfolgreiche Bereitstellung von Unified Messaging-Voicemail in Ihrem Netzwerk erforderlich. In den folgenden Abschnitten werden UM-Wählpläne und deren Verwendung in einer UM-Bereitstellung erläutert.

## UM-Wählpläne – Übersicht

Ein UM-Wählplan stellt eine Gruppe von Nebenstellenanlagen (Private Branch eXchange, PBX) oder IP-Nebenstellenanlagen dar, die bestimmte Benutzerdurchwahlnummern gemeinsam nutzen. Alle Benutzer-Durchwahlnummern, die auf Nebenstellenanlagen oder IP-Nebenstellenanlagen in einem Wählplan gehostet werden, müssen die gleich Anzahl von Stellen umfassen. Die Benutzer können die Durchwahlen der anderen Benutzer wählen, ohne eine Sondernummer an die Durchwahl anfügen oder eine vollständige Telefonnummer wählen zu müssen.

UM-Wählpläne entsprechen den Telefoniewählplänen. Telefoniewählpläne werden für PBX- oder -IP-PBX-Anlagen konfiguriert.

In Unified Messaging können die folgenden Topologien für UM-Wählpläne vorhanden sein:

  - Ein einzelner Wählplan, der eine Untermenge von Durchwahlen bzw. alle Durchwahlen einer Organisation mit einer PBX- oder IP-PBX-Anlage abbildet.

  - Ein einzelner Wählplan, der eine Untermenge von Durchwahlen bzw. alle Durchwahlen einer Organisation mit mehreren PBX- oder IP-PBX-Anlagen in einem Netzwerk abbildet.

  - Mehrere Wählpläne, die eine Untermenge von Durchwahlen bzw. alle Durchwahlen einer Organisation mit einer PBX- oder IP-PBX-Anlage abbilden.

  - Mehrere Wählpläne, die eine Untermenge von Durchwahlen bzw. alle Durchwahlen einer Organisation mit mehreren PBX- oder IP-PBX-Anlagen abbilden.

Benutzer, die demselben Wählplan angehören, besitzen folgende Merkmale:

  - Eine Durchwahlnummer, die das Benutzerpostfach in dem Wählplan eindeutig identifiziert.

  - Die Möglichkeit zum Anrufen oder zum Senden von Sprachmitteilungen an andere Mitglieder des Wählplans nur unter Verwendung der Durchwahlnummer.

Weitere Informationen zum Aktivieren eines Benutzers für Unified Messaging finden Sie unter [Aktivieren eines Benutzers für Voicemail](enable-a-user-for-voice-mail-exchange-2013-help.md).

UM-Wählpläne werden in Unified Messaging verwendet, um sicherzustellen, dass die Telefondurchwahlen der Benutzer eindeutig sind. In einigen Telefonnetzen sind mehrere Nebenstellenanlagen oder IP-Nebenstellenanlagen vorhanden. In solchen Telefonnetzen können theoretisch zwei Benutzer mit identischer Telefondurchwahlnummer vorhanden sein. Mithilfe von UM-Wählplänen kann dies vermieden werden. Indem Sie die beiden Benutzer zwei getrennten UM-Wählplänen zuordnen, werden ihre Durchwahlen eindeutig.

## Funktionsweise von Wählplänen

Wenn ein Telefonnetz in Unified Messaging integriert wird, muss mindestens ein VoIP-Gateway (Voice over IP) genanntes Hardwaregerät oder eine IP-Nebenstellenanlage vorhanden sein, das bzw. die Ihr Telefonnetz mit dem IP-basierten, paketvermittelten Netzwerk verbindet. VoIP-Gateways wandeln leitungsvermittelte Protokolle von einer Nebenstellenanlage in einem Telefonnetz in datenvermittelte Protokolle wie IP um. IP-Nebenstellenanlagen wandeln ebenfalls leitungsvermittelte Protokolle in ein datenvermitteltes Protokoll um. Mithilfe von Session Border Controllern (SBCs), die sich in UM-Hybrid- oder -Onlinebereitstellungen befinden, können Sie zwei IP-basierte Netzwerke über ein öffentliches oder privates WAN verbinden. Jedes VoIP-Gateway, jede IP-Nebenstellenanlage oder jeder Session Border Controller (SBC) in Ihrer Organisation wird durch ein UM-IP-Gateway dargestellt. Weitere Informationen zu UM-IP-Gateways finden Sie unter [UM-IP-Gateways](um-ip-gateways-exchange-2013-help.md).

Unified Messaging macht es erforderlich, mindestens einen UM-Wählplan zu erstellen. Es spielt keine Rolle, ob Sie einen oder mehrere Wählpläne erstellen – eingehende Anrufe werden von allen Exchange-Servern in Ihrer Organisation entgegengenommen. Außerdem muss mindestens ein UM-IP-Gateway dem Wählplan zugeordnet sein. In lokalen oder Hybridbereitstellungen werden eingehende Anrufe nach Installation der Exchange-Server und Zuordnung eines UM-IP-Gateways für alle Wählpläne von allen Exchange-Servern entgegengenommen. Allerdings müssen Sie in lokalen oder Hybridbereitstellungen bei der Integration von Exchange und Lync Server SIP-UIR-Wählpläne erstellen.


> [!IMPORTANT]
> Bei jeder Erstellung eines UM-Wählplans wird gleichzeitig eine standardmäßige UM-Postfachrichtlinie erstellt. Die UM-Postfachrichtlinie wird "&lt;<EM>Wählplanname</EM>&gt;-Standardrichtlinie" genannt. Diese UM-Postfachrichtlinie kann gelöscht oder anders konfiguriert werden.



Wenn Sie bei der Erstellung des ersten UM-IP-Gateways einen UM-Wählplan angeben, wird zudem ein UM-Standardsammelanschluss erstellt. Nach dem Erstellen dieser Komponenten können von den Exchange-Servern Anrufe von einem VoIP-Gateway, einer IP-Nebenstellenanlage oder einem SBC entgegengenommen und für die Benutzer verarbeitet werden, die dem UM-Wählplan zugeordnet sind. In lokalen oder Hybridbereitstellungen werden Anrufe, die beim VoIP-Gateway, der IP-Nebenstellenanlage oder dem SBC eingehen, an einen Clientzugriffsserver weitergeleitet. Der Clientzugriffsserver leitet den Anruf dann an einen Postfachserver weiter, der nach einer Übereinstimmung zwischen Durchwahl des Benutzers und zugeordnetem UM-Wählplan sucht.

## Typen von Wählplänen

Ein URI (Uniform Resource Identifier) ist eine Zeichenfolge (Zahlen oder Buchstaben) zur Identifizierung oder Benennung einer Ressource. Beim Unified Messaging besteht der Hauptzweck eines URIs darin, VoIP-Geräte mithilfe bestimmter Protokolle für die Kommunikation mit anderen Geräten zu aktivieren. Ein URI definiert das Namens- und das Zahlenformat oder -schema, das für die Informationen zum anrufenden und zum angerufenen Teilnehmer verwendet wird, die in einem SIP-Header (Session Initiation Protocol) für einen eingehenden oder ausgehenden Anruf enthalten sind.

Welche Arten von UM-Wählplänen Sie in Unified Messaging erstellen, hängt davon ab, welche URI-Typen von den VoIP-Gateways oder IP-Nebenstellenanlagen in Ihrer Organisation unterstützt werden. Der URI-Typ ist die Art von Zeichenfolge, die von der Nebenstellenanlage oder IP-Nebenstellenanlage gesendet wird. Für das Erstellen eines Wählplans sollten Ihnen die URI-Typen bekannt sein, die jeweils von Ihren PBX- oder IP-PBX-Anlagen unterstützt werden. Es gibt drei Formate oder URI-Typen, die für Unified Messaging-Wählpläne konfiguriert werden können:

  - Telefondurchwahl (TelExtn)

  - SIP-URI

  - E.164

Immer, wenn Sie in Unified Messaging einen Wählplan erstellen, wird der Wählplan standardmäßig für die Verwendung des URI-Typs "Telefondurchwahl" erstellt. Wenn Sie einen Wählplan erstellt haben, können Sie den URI-Typ nicht mehr ändern. Sie müssen den vorhandenen Wählplan löschen und einen anderen mit dem richtigen URI-Typ erstellen.

## URI-Typ "Telefondurchwahl"

Der URI-Typ "Telefondurchwahl" ist der gängigste UM-Wählplantyp, der für IP-Nebenstellenanlagen und Nebenstellenanlagen verwendet wird. Wenn Sie einen Telefondurchwahl-Wählplan (TelExtn) konfigurieren, müssen die VoIP-Gateways, Nebenstellenanlagen und IP-Nebenstellenanlagen den URI-Typ "TelExtn" unterstützen. Dieser URI-Typ wird heute von den meisten Nebenstellenanlagen und IP-Nebenstellenanlagen unterstützt.

Wenn ein Anruf an der Nebenstellenanlage eingeht und der UM-aktivierte Benutzer den Anruf nicht entgegennehmen kann, wird der Anruf von der Nebenstellenanlage an das VoIP-Gateway weitergeleitet. Das VoIP-Gateway (oder die IP-Nebenstellenanlage, falls verfügbar) wandelt den Anruf von einem leitungsvermittelten Protokoll in ein IP-basiertes Protokoll um. Im Header für das SIP-Paket (Session Initiation Protocol), das von dem VoIP-Gateway oder der IP-Nebenstellenanlage empfangen wird, werden die Informationen zum anrufenden und zum angerufenen Teilnehmer in einem der folgenden Formate aufgeführt:

  - Tel:512345

  - 512345@\<*IP-Adresse*\>

Das Format "Telefondurchwahl" (TelExtn) wird basierend auf der Konfiguration des VoIP-Gateways oder der IP-Nebenstellenanlage verwendet.

## SIP-URI-Typ

SIP (Session Initiation Protocol) ist ein Standardprotokoll zum Initiieren interaktiver Benutzersitzungen, die Multimediaelemente wie Video, Sprache, Chat und Spiele umfassen. SIP ist ein auf Anforderungen und Antworten basierendes Protokoll, das Anforderungen von Clients und Antworten von Servern beantwortet. Clients werden durch SIP-URIs identifiziert. Anforderungen können über ein beliebiges Transportprotokoll, z. B. UDP oder TCP, gesendet werden. SIP bestimmt den für die Sitzung zu verwendenden Endpunkt durch Auswahl des Kommunikationsmediums und der Medienparameter.

Wenn Sie einen neuen Wählplan erstellen, haben Sie die Möglichkeit, einen SIP-URI-Wählplan zu erstellen, wenn in Ihrer Umgebung Microsoft Office Communications Server 2007 R2 oder Microsoft Lync Server implementiert ist. Sie können einen SIP-URI-Wählplan auch erstellen, wenn in Ihrer Organisation IP-Nebenstellenanlagen oder SIP-aktivierte Nebenstellenanlagen verfügbar sind. In letzterem Fall muss Ihre Organisation auch SIP-URIs und das SIP-Routing unterstützen.

Ein SIP-URI ist die SIP-Telefonnummer eines Benutzers. Der SIP-URI ähnelt einer E-Mail-Adresse und weist folgendes Format auf: sip*:\<Benutzername\>@\<Domäne oder IP-Adresse\>*:*Port*. Wenn ein Anruf über eine SIP-aktivierte IP-Nebenstellenanlage oder eine Nebenstellenanlage an einen Exchange-Server gesendet wird, werden dabei die SIP-URI für den anrufenden und den angerufenen Teilnehmer übermittelt, und zwar ohne Durchwahlnummern.

## URI-Typ E.164

E.164 ist ein Standardformat für Telefonnummern, das den Nummerierungsplan für internationale öffentliche Fernmeldedienste (International Public Telecommunication Numbering Plan) definiert, der im PSTN (Public Switched Telephone Network) und einigen Datennetzwerken verwendet wird. E.164 definiert das Format von Telefonnummern. E.164-Nummern können bis zu 15 Ziffern enthalten und weisen in der Regel ein Pluszeichen (+) vor den Ziffern der Telefonnummer auf. Wenn Sie eine gemäß E.164 formatierte Telefonnummer von einem Telefon aus wählen möchten, muss die internationale Vorwahl in die gewählte Nummer einbezogen werden. In einem Nummerierungsplan für öffentliche Telefonsysteme nach E.164 enthält jede zugeordnete Nummer einen Ländercode, eine Bereichskennzahl und eine Teilnehmernummer.

Wenn Sie einen neuen Wählplan erstellen, können Sie einen E.164-Wählplan erstellen. Wenn Sie jedoch einen E.164-Wählplan erstellen und konfigurieren, müssen die PBX- und IP-PBX-Anlagen das E.164-Routing unterstützen. Der SIP-Header, der von einem E.164-Wählplan zugeordneten VoIP-Gateway empfangen wird, enthält die Telefonnummer im E.164-Format sowie Informationen zum anrufenden und zum angerufenen Teilnehmer. Das Format sieht wie folgt aus: Tel:+14255550123. Bei Exchange Online-Bereitstellungen mit Exchange Unified Messaging und Lync Server müssen Sie für Outlook Voice Access und die automatische Telefonzentrale richtig formatierte E.164-Nummern verwenden.

## VoIP-Sicherheit

Exchange-Server können je nach Konfiguration des UM-Wählplans mit VoIP-Gateways, IP-Nebenstellenanlagen und anderen Exchange-Computern im ungesicherten, SIP-gesicherten oder gesicherten Modus kommunizieren. In lokalen und Hybridbereitstellungen können Clientzugriffs- und Postfachserver in jedem für einen Wählplan konfigurierten Modus ausgeführt werden, da TCP-Port 5060 und TCP-Port 5061 von den Servern gleichzeitig auf ungesicherte bzw. gesicherte Anforderungen überwacht werden, sofern sie zum Starten im Dualmodus konfiguriert sind. Clientzugriffs- und Postfachserver beantworten alle eingehenden Anrufe für alle UM-Wählpläne, aber diese Wählpläne können unterschiedliche VoIP-Sicherheitseinstellungen aufweisen.

Wenn Sie in lokalen oder Hybridbereitstellungen einen UM-Wählplan erstellen, erfolgt die Kommunikation standardmäßig im ungesicherten Modus, und die Clientzugriffs- und Postfachserver senden unverschlüsselte Daten an VoIP-Gateways, IP-Nebenstellenanlagen und SBCs und empfangen Daten von diesen ebenfalls ohne Verschlüsselung. Im ungesicherten Modus werden weder der RTP-Medienkanal (Realtime Transport Protocol) noch die SIP-Signalinformationen verschlüsselt. Sie können das Cmdlet **Get-UMDialPlan** in der Shell verwenden, um die Sicherheitseinstellungen für einen bestimmten UM-Wählplan festzulegen.

In lokalen und Hybridbereitstellungen können Sie einen Clientzugriffs- und Postfachserver für die Verwendung von MTLS (Mutual TLS) zur Verschlüsselung des SIP- und RTP-Datenverkehrs konfigurieren, der von anderen Geräten und Servern gesendet und empfangen wird. Wenn Sie den Wählplan für den Modus "SIP-gesichert" konfigurieren, wird nur der SIP-Signalverkehr verschlüsselt, und die RTP-Medienkanäle verwenden weiterhin das unverschlüsselte TCP. Wenn Sie den Wählplan jedoch für den Modus "Gesichert" konfigurieren, werden sowohl der SIP-Signalverkehr als auch die RTP-Medienkanäle verschlüsselt. Ein verschlüsselter Signalmedienkanal, der SRTP (Secure Realtime Transport Protocol) einsetzt, verwendet außerdem MTLS (Mutual TLS) zum Verschlüsseln der VoIP-Daten.

Sie können den VoIP-Sicherheitsmodus entweder konfigurieren, wenn Sie einen neuen Wählplan erstellen oder nachdem Sie einen Wählplan mithilfe der Exchange-Verwaltungskonsole oder dem Cmdlet **Set-UMDialPlan** in der Shell erstellt haben. Wenn Sie in der Konfiguration des UM-Wählplans die Verwendung des SIP-gesicherten oder gesicherten Modus festgelegt haben, verschlüsseln die Clientzugriffs- und Postfachserver den SIP-Signalverkehr und/oder die RTP-Medienkanäle. Um jedoch verschlüsselte Daten an bzw. von Exchange-Servern zu senden, müssen Sie den UM-Wählplan richtig konfigurieren, und VoIP-Geräte wie VoIP-Gateways, IP-Nebenstellenanlagen oder SBCs müssen MTLS (Mutual TLS) unterstützen.

## Outlook Voice Access

Zwei Arten von Anrufern greifen mithilfe der Outlook Voice Access-Nummer, die für einen UM-Wählplan konfiguriert ist, auf das Voicemailsystem zu: nicht authentifizierte Anrufer und authentifizierte Anrufer. Wenn Anrufer die im Wählplan konfigurierte Outlook Voice Access-Nummer anrufen, gelten sie als anonym oder nicht authentifiziert, bis sie ihre Voicemaildurchwahl und PIN eingegeben haben. Die einzige Option, die anonymen oder nicht authentifizierten Anrufern zur Verfügung steht, ist das Verzeichnissuchfeature. Nachdem die Anrufer ihre Voicemaildurchwahl und PIN eingegeben haben, werden sie authentifiziert und erhalten Zugriff auf ihr Postfach. Nachdem der Zugang zum Voicemailsystem gewährt wurde, verwenden sie das Outlook Voice Access-Feature.

Outlook Voice Access besteht aus einer Reihe von Sprachansagen, mit denen der Anrufer auf E-Mail, Voicemail, Kalender und andere Informationen zugreifen kann. Outlook Voice Access ermöglicht authentifizierten Anrufern mithilfe von MFV-Tasten- oder Spracheingaben (auch als Tonwahl bezeichnet) die Navigation durch ihre persönlichen Informationen, das Tätigen von Anrufen oder Auffinden von Benutzern.

## Outlook Voice Access-Nummern

Nachdem Sie einen UM-Wählplan erstellt haben, müssen Sie mindestens eine Outlook Voice Access-Nummer hinzufügen. Outlook Voice Access-Nummern werden auch als Pilotnummern für Wählpläne bezeichnet. Diese Nummer wird von Outlook Voice Access-Benutzern für den Zugriff auf ihre Postfächer verwendet und ermöglichen ihnen die Verzeichnissuche.

Beim Erstellen eines UM-Wählplans werden standardmäßig keine Outlook Voice Access-Nummern konfiguriert. Sie müssen mindestens eine Telefon- oder Durchwahlnummer konfigurieren, damit die Benutzer das Outlook Voice Access-Feature verwenden können. Die Anzahl alphanumerischer Zeichen in der Outlook Voice Access-Nummer darf 20 nicht überschreiten. Nachdem Sie diese Nummer für den Wählplan konfiguriert haben, wird sie in den Voicemailoptionen in Microsoft Outlook sowie in Outlook Web App angezeigt.

Sie können eine Telefonnummer oder Durchwahl über das Feld **Outlook Voice Access-Nummern** zum UM-Wählplan hinzufügen, die ein Benutzer anrufen kann, um auf das Voicemailsystem mithilfe von Outlook Voice Access zuzugreifen. In den meisten Fällen wird eine Durchwahl oder eine externe Telefonnummer eingegeben. Da in diesem Feld jedoch alphanumerische Zeichen zulässig sind, kann ein SIP-URI angegeben werden, wenn eine IP-Nebenstellenanlage, Office Communications Server 2007 R2 oder Microsoft Lync Server verwendet wird.

In Abhängigkeit von den Anforderungen in Ihrer Organisation können Sie eine oder mehrere Outlook Voice Access-Nummern konfigurieren. Sie können eine einzige oder mehrere Outlook Voice Access-Nummern für einen einzelnen UM-Wählplan verwenden. Sie können jedoch keine einzelne Outlook Voice Access-Nummer verwenden, die mehrere UM-Wählpläne umfasst.

