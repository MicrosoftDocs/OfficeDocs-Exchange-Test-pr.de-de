---
title: 'Ratgeber für Voicemailvorschau: Exchange 2013 Help'
TOCTitle: Ratgeber für Voicemailvorschau
ms:assetid: 0957dd54-df6d-4b50-9db5-4757f548b899
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Ee364730(v=EXCHG.150)
ms:contentKeyID: 51409263
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ratgeber für Voicemailvorschau

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Exchange Unified Messaging (UM) umfasst ein Feature namens Voicemailvorschau, das Voicemailnachrichten mithilfe der automatischen Spracherkennung eine Textversion der Voicemailaudiodatei hinzufügt. Die automatische Spracherkennung ist nicht immer exakt, insbesondere wenn sie für die Aufzeichnung von Ton mit unbekannten Stimmen und Geräuschen über ein Telefon verwendet wird. Einige Organisationen benötigen konsistent fehlerfreie (oder nahezu fehlerfreie) Abschriften von Sprachnachrichten. Das Voicemailvorschau-Partnerprogramm unterstützt diese Organisationen bei der Erfüllung dieser Anforderungen.

Die Voicemailvorschau verwendet [Sprachtechnologie von Microsoft](http://go.microsoft.com/fwlink/p/?linkid=187348) für die Bereitstellung einer Textversion von Audioaufzeichnungen. Der Voicemailtext wird in E-Mails innerhalb von MicrosoftOutlook Web App, Outlook 2010 oder höheren Versionen und in anderen E-Mail-Programmen angezeigt.

Wenn Sie einen Benutzer in einer lokalen oder einer Hybridbereitstellung für UM aktivieren, wird standardmäßig eine Voicemailvorschau gesendet, wenn ein unterstütztes UM-Sprachpaket installiert ist. Wenn Sie einen Benutzer in Exchange Online für UM aktivieren, werden alle UM-Sprachpakete installiert. Voicemailvorschau wird jedoch nicht in allen installierten Sprachen unterstützt.

Manche Voicemailvorschau-Partner bieten erweiterte Unterstützung und Dienste für die Transkription der Voicemailvorschau an. Diese Partner beschäftigen Mitarbeiter für die Korrektur von Voicemail-Transkriptionen, die mithilfe von ASR erstellt wurden. Jeder Voicemailvorschau-Partner muss bestimmte Anforderungen erfüllen, um für die Zusammenarbeit mit Exchange UM zertifiziert zu werden.

Wenn Sie feststellen, dass die an Ihre Benutzer gesendete Voicemailvorschau nicht präzise genug ist, können Sie sich an einen der zertifizierten Voicemailvorschau-Partner wenden, die unter [Microsoft Pinpoint](https://go.microsoft.com/fwlink/p/?linkid=281966) aufgeführt sind, und sich gegen zusätzliche Kosten bei diesen anmelden.

**Inhalt**

Übersicht

Voicemail-Partnerprogramm für Exchange Unified Messaging

Für Exchange Unified Messaging zertifizierte Voicemailvorschau-Partner

Konfigurieren von Voicemailvorschau-Partnern

Unterstützung für VoIP- oder Mediengateways und IP-PBX

## Übersicht

Wenn Unified Messaging den Ton einer Sprachnachricht aufzeichnet, wird die automatische Spracherkennung verwendet, um eine Vorschau des Texts in der Audiodatei zu erstellen und die gesamte Sprachnachricht zur Zustellung an den Benutzer zu übermitteln. Für jede erstellte Sprachnachricht legt Unified Messaging eine Zuverlässigkeitsstufe für die Voicemailvorschau in jeder Nachricht fest. Diese gibt an, wie genau der Ton in der Aufzeichnung den Wörtern, Zahlen und Phrasen in der Nachricht entspricht. Wenn das System problemlos Übereinstimmungen findet, ist die Zuverlässigkeitsstufe hoch. Einer höheren Zuverlässigkeitsstufe ist im Allgemeinen eine höhere Genauigkeit zugeordnet.

Die Genauigkeit des Voicemailvorschautexts hängt von vielen Faktoren ab, und manchmal können diese Faktoren nicht gesteuert werden. Der Text ist jedoch wahrscheinlich genauer, wenn:

  - Es wird eine einfache Sprachnachricht hinterlassen, in der der Anrufer keine umgangssprachlichen Begriffe, technischen Jargon oder seltenen Wörter oder Ausdrücke verwendet.

  - der Benutzer eine einfach zu erkennende und vom Voicemailsystem zu konvertierende Sprache verwendet. Im Allgemeinen enthalten die Sprachnachrichten von Benutzern, die nicht zu schnell oder weich sprechen und keinen starken Akzent haben, genauere Sätze und Ausdrücke.

  - Die Sprachnachricht enthält keine Hintergrundgeräusche, Echos oder Tonaussetzer.

Viele Kunden, die Unified Messaging verwenden, bestätigen, dass die Voicemailvorschau ausreichend exakt für ihre Benutzer ist. Wenn die automatische Spracherkennung jedoch auf Aufzeichnungen von unbekannten Stimmen oder Hintergrundgeräuschen am Telefon verwendet wird, ist der Voicemailvorschau-Text nicht vollständig exakt. Wenn die Zuverlässigkeitsstufe konstant niedrig ist oder die empfangene Voicemailvorschau nicht exakt ist, können Sie die Genauigkeit der vom Benutzer empfangenen Voicemailvorschauen wie folgt erhöhen:

  - Melden Sie sich für einen Sprachtranskriptionsdienst eines Voicemailvorschau-Partners an.

  - Nachdem Sie sich bei einem Voicemailvorschau-Partner angemeldet haben, richten Sie den Partner für die Arbeit mit UM ein. Weitere Informationen zum Konfigurieren von UM für einen Voicemailvorschau-Partner finden Sie unter [Voicemailvorschau Partnerdienste für Benutzer konfigurieren](configure-voice-mail-preview-partner-services-for-users-exchange-2013-help.md).

Wenn Sie sich bei einem Voicemailvorschau-Partner anmelden, leiten die Exchange-Server in Ihrer Organisation Voicemailnachrichten mit angehängter Audiodatei an den Voicemailvorschau-Partner weiter, anstatt einen Voicemailvorschautext für Sprachnachrichten zu erstellen und die Sprachnachrichten an das Postfach des Benutzers weiterzuleiten. Die E-Mail mit dem vom Voicemailvorschau-Partner erstellten Voicemailvorschautext wird anschließend an die Exchange-Server in Ihrer Organisation übermittelt, um an das Postfach des Empfängers zugestellt zu werden.


> [!IMPORTANT]
> Alle Kunden, die eine Bereitstellung von Unified Messaging planen, sollten einen UM-Spezialisten zu Rate ziehen. Ein UM-Spezialist unterstützt Sie dabei sicherzustellen, dass der Übergang von einem älteren Voicemailsystem zu UM reibungslos verläuft. Für die Durchführung einer neuen Bereitstellung oder für das Upgrade eines älteren Voicemailsystems sind umfassende Kenntnisse über VoIP-Gateways, IP-Nebenstellenanlagen, Nebenstellenanlagen, Session Border Controller (SBCs) und Unified Messaging erforderlich. Weitere Informationen zur Kontaktaufnahme mit einem UM-Spezialisten finden Sie unter <A href="http://go.microsoft.com/fwlink/p/?linkid=262708">Spezialisten für Microsoft Exchange Server 2013 Unified Messaging (UM)</A> oder unter <A href="https://go.microsoft.com/fwlink/p/?linkid=261951">Microsoft Pinpoint für Unified Messaging</A>.



Übersicht

## Voicemail-Partnerprogramm für Exchange Unified Messaging

Um zertifizierter Voicemailpartner für die Interoperabilität mit Exchange UM zu werden, muss der Partner die in der Interoperabilitätsspezifikation für Voicemailpartner (Voice Mail Preview Interoperability Specification) enthaltenen Anforderungen implementieren, und die Partnerlösung muss von einem unabhängigen Zertifikatanbieter zertifiziert werden. Wenn Sie sich für eine Zertifizierung Ihres Transkriptionsdiensts für die Interoperabilität mit Exchange UM interessieren, können Sie eine Anfrage an [Voicemailvorschau-Partner für Exchange Unified Messaging](mailto:vmppp@microsoft.com) richten.

## Für Exchange Unified Messaging zertifizierte Voicemailvorschau-Partner

Wenn Sie Unified Messaging bereits in Ihrer Organisation bereitgestellt haben und einen zertifizierten Voicemailvorschau-Partner für Transkriptionsdienste suchen, finden Sie weitere Informationen unter [Microsoft PinPoint](https://go.microsoft.com/fwlink/p/?linkid=281966). Diese Softwareanbieter wurden für die Interoperabilität mit Exchange UM zertifiziert.

## Konfigurieren von Voicemailvorschau-Partnern

Nach der Konfiguration von UM werden Sprachnachrichten mit Ton an dedizierte Voicemailvorschau-Partner weitergeleitet, die dann aus der Audiodatei den Voicemailvorschautext erstellen. Damit Benutzer die Voicemailvorschau mit ihrer Sprachnachricht im Postfach erhalten können, müssen Sie jedoch eine UM-Postfachrichtlinie konfigurieren, Benutzer der UM-Postfachrichtlinie zuordnen und die Benutzer bestätigen lassen, dass sie Voicemailvorschauen in ihren Sprachnachrichten in Outlook 2010 oder höher bzw. in Outlook Web App empfangen kann. Weitere Informationen zum Konfigurieren von UM für einen Voicemailvorschau-Partner finden Sie unter [Voicemailvorschau Partnerdienste für Benutzer konfigurieren](configure-voice-mail-preview-partner-services-for-users-exchange-2013-help.md).

## Unterstützung für VoIP- oder Mediengateways und IP-PBX

Das Konfigurieren von VoIP-Gateways und IP-Nebenstellenanlagen für die Organisation ist eine schwierige Bereitstellungsaufgabe, die ordnungsgemäß durchgeführt werden muss, damit Unified Messaging für einen Voicemailvorschau-Partner erfolgreich bereitgestellt wird. Weitere Informationen zur Konfiguration von VoIP-Gateways und IP-Nebenstellenanlagen finden Sie unter [Telefonieratgeber für Exchange 2013](telephony-advisor-for-exchange-2013-exchange-2013-help.md) oder unter [Konfigurationshinweise zu unterstützten VoIP-Gateways, IP-Nebenstellenanlagen und Nebenstellenanlagen](configuration-notes-for-supported-voip-gateways-ip-pbxs-and-pbxs-exchange-2013-help.md).

Das Testen der Interoperabilität von Exchange UM mit VoIP-Gateways wurde in das Microsoft Unified Communications Open Interoperability Program integriert. Weitere Informationen hierzu finden Sie unter [Microsoft Unified Communications Open Interoperability Program](https://go.microsoft.com/fwlink/p/?linkid=132071).

Übersicht

