---
title: 'Neue Voicemailfeatures: Exchange 2013 Help'
TOCTitle: Neue Voicemailfeatures
ms:assetid: 89faaa97-3485-4704-a56c-d13632f01e2a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649002(v=EXCHG.150)
ms:contentKeyID: 50476125
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Neue Voicemailfeatures

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Unified Messaging (UM) umfasst in Microsoft Exchange Server 2013 den gleichen Funktionssatz wie Exchange 2010 und Exchange 2007, jedoch mit einigen Erweiterungen und Architekturänderungen. Bei Unified Messaging handelt es sich allerdings nicht länger um eine separate Serverrolle. Es handelt sich hierbei nun um eine Komponente der sprachbezogenen Funktionen in Exchange 2013.

## Änderungen in der Architektur für Voicefunktionen

Die Architektur für Voicefunktionen unterscheidet sich in Exchange 2013 von der Architektur in Exchange 2010 und Exchange 2007. In Vorgängerversionen von Exchange UM befanden sich alle Komponenten für Unified Messaging auf einem Server mit der UM-Serverrolle. In Exchange 2013 sind die Unified Messaging-Komponenten aufgeteilt zwischen einem Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Call-Router-Dienst ausgeführt wird, und einem Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird. Der Großteil der Funktionalität, einschließlich der Dienste und Arbeitsprozesse für Unified Messaging, befindet sich auf den einzelnen Postfachservern. Der Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Call-Router-Dienst ausgeführt wird, leitet eingehende Anrufe per Proxy an den Postfachserver weiter. Weitere Informationen finden Sie unter [Änderungen an der Spracharchitektur](voice-architecture-changes-exchange-2013-help.md).

## Unterstützung für IPv6

Internetprotokoll, Version 6, (IPv6) ist die aktuelle Version des Internetprotokolls (IP). Mit IPv6 sollen zahlreiche der Defizite von IPv4, der vorherigen IP-Version, korrigiert werden. Ebenso wie Exchange 2010 bieten Exchange 2013-Clientzugriffs- und Postfachserver vollständige Unterstützung für IPv6-Netzwerke. Weitere Informationen finden Sie unter [IPv6-Unterstützung in Unified Messaging](ipv6-support-in-unified-messaging-exchange-2013-help.md).

## Unterstützung für die UCMA 4.0-API

Seit Exchange 2010 Service Pack 1 (SP1) stützt sich die Unified Messaging-Rolle in Bezug auf Signal- und Mediendatenverkehr auf die Unified Communications Managed API v2.0 (UCMA). UCMA 2.0 war daher eine Voraussetzung für die Installation von Exchange 2010 UM. UCMA 2.0 kann von Administratoren auf UM-Servern mit Exchange 2010 SP1 oder höher separat heruntergeladen und manuell bereitgestellt werden.

UCMA 2.0 weist jedoch einige Einschränkungen auf. Viele dieser Einschränkungen wurden durch UCMA 4.0 korrigiert, welches für Exchange 2013 erforderlich ist. Da der UM-Server jetzt keine separate Serverrolle mehr ist, benötigen die Clientzugriffs- und Postfachserver UCMA 4.0.

UCMA 4.0 unterstützt neue Funktionen in Unified Messaging, beispielsweise wird dieselbe Version des Sprachmoduls sowohl für das TTS-Modul (Text-to-Speech) als auch für die automatische Spracherkennung (ASR) verwendet. Die für Exchange 2013 verwendete Plattform, .NET 4.0, umfasst eine einzelne Installationsdatei und bietet Abwärtskompatibilität mit UM-Servern für Exchange 2010 und Exchange 2007.

In Exchange 2010 SP2 und SP1 ist vor der Installation des Service Packs auf einem Unified Messaging-Server die Installation von UCMA 2.0 erforderlich.

Die Verwendung von UCMA 4.0 bietet mehrere Vorteile:

  - Es enthält Hotfixes und Patches.

  - Es unterstützt IPv6.

  - Die Bereitstellung von UCMA 4.0 wurde automatisiert und vereinfacht.

  - Mit dem UCMA 4.0-Setup werden alle Voraussetzungen für Exchange 2013 erfüllt.

  - UCMA 4.0 bietet genauere Sprachmodulübersetzungen und eine besser skalierbare Sprachplattform-Unterstützung über mehrere Produkte.


> [!NOTE]
> UCMA&nbsp;4.0 wird bei der Installation von Exchange 2013 installiert. Ausführliche Informationen über UCMA&nbsp;4.0 und die Anforderungen für das Setup finden Sie unter <A href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</A>. Wenn Sie ein Upgrade auf die neueste Version von UCMA durchführen möchten, müssen Sie zunächst über Software alle vorherigen UCMA-Versionen deinstallieren.



## Verbesserungen an der Voicemailvorschau

Einige Erweiterungen der sprachbezogenen Dienste werden in Exchange Server 2013 UM über das Sprachmodul, Version 11.0, und UCMA 4.0 bereitgestellt. Es wurden Verbesserungen an der Grammatikgenerierung, an wichtigen Sprachdiensten und an der Unterstützung für mehrere Sprachen vorgenommen. Exchange Server 2013 UM bietet außerdem mehrere Verbesserungen an Transkriptionsdiensten, die den Endbenutzern bereitgestellt werden, sowie eine größere Zuverlässigkeit und Genauigkeit für die Voicemailvorschau. Weitere Informationen finden Sie unter [Voicemail-Vorschau Erweiterungen](voice-mail-preview-enhancements-exchange-2013-help.md).

## Verbesserte Anrufer-ID-Unterstützung

In früheren Versionen von Exchange Unified Messaging verwendet ein UM-Server, der einen Anruf entgegennimmt, die Anrufer-ID, um die mögliche Identität des Anrufers zu ermitteln. Die Suche erfolgt in Active Directory und den persönlichen Kontakten, die UM-Benutzer in ihren Postfächern speichern.

In der Vergangenheit war es für Benutzer häufig ein Ärgernis, dass das Voicemailsystem Exchange- oder persönliche Kontakte nicht anhand der Anrufer-ID identifizieren konnte. Bis jetzt wurde nur der Standardkontaktordner im Exchange-Postfach eines Benutzers für diese Suche verwendet. Exchange Server 2013-Benutzer verfügen jedoch wahrscheinlich über Kontakte aus externen sozialen Netzwerken oder über Kontaktdaten, die sie beim Organisieren ihrer Kontakte speziellen Ordnern hinzugefügt haben. In Exchange 2013 erweitert UM den Suchbereich auf die anderen Exchange- und persönlichen Kontaktordner des Benutzers, die manuell erstellt wurden. Exchange 2013 unterstützt außerdem die Aggregation von Kontakten aus externen sozialen Netzwerken, stellt intelligente Funktionen zur Verknüpfung mehrerer Kontaktdaten zu derselben Person bereit und verwendet diese Daten, um personenbezogene (nicht kontaktbezogene) Ansichten bereitzustellen. Somit können Kontakte aus externen sozialen Netzwerken in dem Kontaktordner abgelegt werden, der im Postfach des Benutzers in Microsoft Outlook Web App und Outlook gespeichert ist. Diese Kontakte können jetzt auch allen weiteren von Benutzern erstellten Kontaktordnern hinzugefügt werden.

Die Suche nach Anrufer-IDs ist in die Kontaktaggregation integriert, sodass Suchläufe auch in externen Kontakten durchgeführt werden. Die Eigenschaft **PersonID**, sofern sie vorhanden und auf einen Wert ungleich Null eingestellt ist, verbessert die Auflösung von Anrufer-IDs, indem doppelte Treffer für Kontakte, die derselben Person zugeordnet sind, unterdrückt werden. Da die PersonID-Eigenschaft bei beiden Ergebnissen identisch ist, betrachtet UM das Ergebnis als Treffer für einen einzelnen Kontakt.

## Verbesserungen an Sprachplattform und Spracherkennung

Mit Exchange Server 2013 UM werden einige Verbesserungen an Sprachplattform und Spracherkennung eingeführt, darunter die folgenden:

  - Erweiterungen und verbesserte Genauigkeit für die Voicemailvorschau.

  - Unterstützung für die [Microsoft Speech Platform – Runtime (Version 11.0)](https://go.microsoft.com/fwlink/p/?linkid=253196).

  - Sprachgrammatikgenerierung unter Verwendung des Systempostfachs für eine Organisation.

Exchange Unified Messaging verwendet statische und dynamische Sprachgrammatikdaten, um Befehle, Kontaktnamen in der globalen Adressliste (GAL) und Namen persönlicher Kontakte im Benutzerpostfach zu erkennen. In Exchange Server 2013 generiert jeder Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, Grammatikdaten für alle installierten UM-Sprachen und speichert diese in Verzeichnissen. Jeder Postfachserver speichert sämtliche mögliche Grammatikdaten, deren Generierung auf der Anzahl von Wählplänen, den automatischen Telefonzentralen und den installierten UM-Sprachen basiert.

UM verwendet Grammatikdateien, damit Anrufer über die Sprachfunktion Benutzer in Ihrer Organisation auffinden können. Die Dateien werden alle 24 Stunden vom Postfach-Assistenten aktualisiert. Der Befehl "GGG.exe" in Exchange 2007 und Exchange 2010 ermöglicht Ihnen, die Grammatikdateien manuell zu aktualisieren, ohne auf das geplante Update warten zu müssen. Zum Lösen von Skalierbarkeitsproblemen mit der Grammatikgenerierung für die automatische Spracherkennung in UM wird die Sprachgrammatik für die GAL in Exchange Server 2013 nicht mehr auf dem Server generiert, auf dem die Unified Messaging-Serverrolle installiert ist. Stattdessen erfolgt die Generierung unter Verwendung des Postfach-Assistenten und wird regelmäßig auf dem Postfachserver durchgeführt, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird und der das Vermittlungspostfach der Organisation hostet. Die Sprachgrammatikdatei für die GAL wird im Vermittlungspostfach einer Organisation gespeichert und später auf alle Postfachserver in dieser Exchange-Organisation heruntergeladen. Standardmäßig wird der Postfach-Assistent alle 24 Stunden ausgeführt. Sie können die Häufigkeit mithilfe des Cmdlets **Set-MailboxServer** anpassen.

## Cmdlet-Aktualisierungen

Für Exchange 2013 wurden viele UM-Cmdlets aus Exchange 2010 übernommen. Einige dieser Cmdlets wurden jedoch geändert, und für neue Funktionen wurden weitere Cmdlets hinzugefügt. Weitere Informationen finden Sie unter [Updates für Unified Messaging-Cmdlets](unified-messaging-cmdlet-updates-exchange-2013-help.md).

