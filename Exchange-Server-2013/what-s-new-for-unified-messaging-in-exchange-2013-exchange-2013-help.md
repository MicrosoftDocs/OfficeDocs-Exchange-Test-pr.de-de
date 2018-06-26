---
title: 'Neues in Exchange 2013 Unified Messaging: Exchange 2013 Help'
TOCTitle: Neues in Exchange 2013 Unified Messaging
ms:assetid: a444ef2d-d893-408e-adf9-c9d8a8b07593
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150545(v=EXCHG.150)
ms:contentKeyID: 50476359
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Neues in Exchange 2013 Unified Messaging

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In Microsoft Exchange Server 2013 wurden neue Funktionen hinzugefügt und Änderungen an der Architektur vorgenommen, um frühere Exchange-Versionen zu erweitern. Unified Messaging (UM) in Exchange 2013 umfasst den gleichen Funktionssatz wie in Exchange 2010 und Exchange 2007, ist jedoch keine separate Serverrolle mehr. Es handelt sich hierbei nun um eine Komponente der sprachbezogenen Funktionen in Exchange 2013.

## Änderungen in der Architektur für Voicefunktionen

Die Exchange 2013-Architektur unterscheidet sich von der Architektur in Exchange 2010 und Exchange 2007. In Vorgängerversionen von Exchange UM befanden sich alle Komponenten für Unified Messaging auf einem Server mit der UM-Serverrolle. In Exchange 2013 sind alle Unified Messaging-Komponenten aufgeteilt zwischen einem Clientzugriffsserver, auf dem der Microsoft Exchange Unified Messaging-Call-Router-Dienst ausgeführt wird, und einem Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird. Sämtliche Funktionen, einschließlich der Dienste und Arbeitsprozesse für Unified Messaging, befinden sich auf allen Postfachservern, mit Ausnahme des Clientzugriffsservers mit dem Microsoft Exchange Unified Messaging-Call-Router-Dienst, der eingehende Anrufe per Proxy an den Postfachserver weiterleitet. Weitere Informationen finden Sie unter [Änderungen an der Spracharchitektur](voice-architecture-changes-exchange-2013-help.md).

## Unterstützung für IPv6

Internetprotokoll, Version 6, (IPv6) ist die aktuelle Version des Internetprotokolls. Mit IPv6 sollen zahlreiche der Defizite von IPv4, der vorherigen IP-Version, korrigiert werden. Ebenso wie Exchange 2010 bieten Exchange 2013-Clientzugriffs- und Postfachserver vollständige Unterstützung für IPv6-Netzwerke. Weitere Informationen finden Sie unter [IPv6-Unterstützung in Unified Messaging](ipv6-support-in-unified-messaging-exchange-2013-help.md).

## Unterstützung für die UCMA 4.0-API

Seit Exchange 2010 Service Pack 1 stützt sich die Unified Messaging-Rolle in Bezug auf Signal- und Mediendatenverkehr auf die Unified Communications Managed API v2.0 (UCMA). UCMA 2.0 ist daher eine Voraussetzung für die Installation von Exchange 2010 UM. UCMA 2.0 kann von Administratoren auf Unified Messaging-Servern mit Exchange 2010 SP1 oder höher separat heruntergeladen und manuell bereitgestellt werden. Für Exchange 2013 ist UCMA 4.0 erforderlich. Angesichts der Tatsache, dass der UM-Server in Exchange 2013 keine separate Serverrolle mehr ist, benötigen nun die Clientzugriffs- und Postfachserver UCMA 4.0.

UCMA 4.0 unterstützt neue Funktionen in Unified Messaging, beispielsweise wird dieselbe Version des Sprachmoduls sowohl für das TTS-Modul (Text-to-Speech) als auch für die automatische Spracherkennung (ASR) verwendet. Die für Exchange 2013 verwendete Plattform, .NET 4.0, umfasst eine einzelne Installationsdatei und bietet Abwärtskompatibilität mit UM-Servern für Exchange 2010 und Exchange 2007.

In Exchange 2010 SP2 und SP1 ist vor der Installation des Service Packs auf einem Unified Messaging-Server die Installation von UCMA 2.0 erforderlich. UCMA 2.0 weist jedoch einige Einschränkungen auf. In UCMA 4.0 wurden viele dieser Defizite korrigiert. In Exchange Server 2013 wird für das Unified Messaging weiterhin UCMA verwendet. Eine Umstellung auf die neueste UCMA-Version bietet jedoch eine Reihe von Vorteilen:

  - Der neueste UCMA-Build enthält Hotfixes und Patches.

  - UCMA erfordert .NET 4.0, die Plattform, die von Exchange Server 2013 verwendet wird. (UCMA 2.0 unterstützt .NET 4.0. nicht)

  - UCMA 4.0 unterstützt IPv6.

  - Vereinfachte und automatisierte Bereitstellung von UCMA 4.0. Das Exchange 2013-Setup führt eine einzige Prüfung für UCMA 4.0 durch.

  - Mit dem UCMA 4.0-Setup werden alle Voraussetzungen für Exchange 2013 erfüllt.


> [!NOTE]
> UCMA&nbsp;4.0 wird bei der Installation von Exchange 2013 installiert. Ausführliche Informationen über UCMA&nbsp;4.0 und die Anforderungen für das Setup finden Sie unter <A href="exchange-2013-prerequisites-exchange-2013-help.md">Voraussetzungen für Exchange 2013</A>. Wenn Sie ein Upgrade auf die neueste Version von UCMA durchführen möchten, müssen Sie zunächst über <STRONG>Software</STRONG> alle vorherigen UCMA-Versionen deinstallieren.



## Verbesserungen an der Voicemailvorschau

Einige Erweiterungen der sprachbezogenen Dienste werden in Exchange Server 2013 UM über das Sprachmodul, Version 11.0, und UCMA 4.0 bereitgestellt. Verbesserungen der Grammatikgenerierung und Spracherkennung sind im Lieferumfang enthalten. Darüber hinaus bietet Exchange Server 2013 UM verschiedene Erweiterungen der Benutzeroberfläche sowie eine verbesserte Zuverlässigkeit und Genauigkeit für die Voicemailvorschau. Weitere Informationen finden Sie unter [Voicemail-Vorschau Erweiterungen](voice-mail-preview-enhancements-exchange-2013-help.md).

## Verbesserte Anrufer-ID-Unterstützung

In früheren Versionen von Exchange Unified Messaging verwendet ein UM-Server, der einen Anruf entgegennimmt, die Anrufer-ID, um die Identität des Anrufers zu ermitteln. Die Suche erfolgt in Active Directory und den persönlichen Kontakten, die UM-Benutzer in ihren Postfächern speichern.

Exchange-Benutzer haben zuweilen damit zu kämpfen, dass bei der Ermittlung von Kontaktdaten aus Anrufer-IDs Fehler auftreten. Bis jetzt wurde nur der Standardkontaktordner in Exchange UM für die Suche verwendet. Exchange Server 2013-Benutzer verfügen jedoch wahrscheinlich über Kontaktdaten aus externen sozialen Netzwerken oder in Ordnern, die die Benutzer manuell erstellt haben. Exchange 2013 unterstützt die Aggregation von Kontakten aus sozialen Netzwerken, stellt intelligente Funktionen zur Verknüpfung mehrerer Kontaktinformationen zur gleichen Person bereit und verwendet diese Daten, um personenbezogene (statt kontaktbezogene) Ansichten bereitzustellen. Die aus externen Netzwerken aggregierten Kontakte werden ebenso wie von den Benutzern erstellte zusätzliche Kontaktordner in Kontaktordnern gespeichert. Die Exchange 2013 UM-Funktionen erweitern den Suchbereich, sodass nun auch andere Exchange-Kontaktordner und persönliche, manuell erstellte Kontaktordner einbezogen werden.

Die Suche nach Anrufer-IDs ist in die Kontaktaggregation integriert, sodass Suchläufe auch in externen Kontakten durchgeführt werden. Die Eigenschaft "PersonID", sofern vorhanden und mit einem Wert ungleich Null, verbessert die Auflösung von Anrufer-IDs, indem doppelte Treffer für Kontakte, die der gleichen Person zugeordnet sind, unterdrückt werden. Da die PersonID-Eigenschaft bei beiden Ergebnissen identisch ist, betrachtet UM das Ergebnis als Treffer für einen einzelnen Kontakt.

## Verbesserungen an Sprachplattform und Spracherkennung

Mit Exchange Server 2013 UM werden einige Verbesserungen an Sprachplattform und Spracherkennung eingeführt, darunter die folgenden:

  - Erweiterungen und verbesserte Genauigkeit für die Voicemailvorschau.

  - Unterstützung für die [Microsoft Speech Platform – Runtime (Version 11.0)](https://go.microsoft.com/fwlink/p/?linkid=253196).

  - Sprachgrammatikgenerierung unter Verwendung des Systempostfachs für eine Organisation.

Exchange Unified Messaging verwendet statische und dynamische Sprachgrammatikdaten, um Befehle, Kontaktnamen in der globalen Adressliste und Namen persönlicher Kontakte im Benutzerpostfach zu erkennen. In Exchange Server 2013 generiert jeder Postfachserver, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird, Grammatikdaten für alle installierten UM-Sprachen und speichert diese in Verzeichnissen. Jeder Postfachserver speichert sämtliche mögliche Grammatikdaten, deren Generierung auf der Anzahl von Wählplänen, den automatischen Telefonzentralen und den installierten UM-Sprachen basiert.

Grammatikdateien werden als Eingaben für den Spracherkennungsprozess verwendet und regelmäßig generiert. Der Befehl "GGG.exe" in Exchange 2007 und Exchange 2010 ermöglicht Ihnen, die Grammatikdateien manuell zu aktualisieren, ohne auf das geplante Update warten zu müssen. Zum Lösen von Skalierbarkeitsproblemen mit der Grammatikgenerierung für die automatische Spracherkennung in UM wird die Sprachgrammatik für die GAL in Exchange Server 2013 nicht mehr auf dem Server generiert, auf dem die Unified Messaging-Serverrolle installiert ist. Stattdessen erfolgt die Generierung unter Verwendung des Postfach-Assistenten und wird regelmäßig auf dem Postfachserver durchgeführt, auf dem der Microsoft Exchange Unified Messaging-Dienst ausgeführt wird und der das Vermittlungspostfach der Organisation hostet. Die Sprachgrammatikdatei für die GAL wird im Vermittlungspostfach einer Organisation gespeichert und später auf alle Postfachserver in dieser Exchange-Organisation heruntergeladen. Standardmäßig wird der Postfach-Assistent alle 24 Stunden ausgeführt. Sie können die Häufigkeit mithilfe des Cmdlets **Set-MailboxServer** anpassen.

## Cmdlet-Aktualisierungen

In Exchange 2013 wurden viele UM-Cmdlets aus Exchange 2010 übernommen, es wurden jedoch einige dieser Cmdlets geändert, und es wurden neue Cmdlets hinzugefügt. Weitere Informationen finden Sie unter [Updates für Unified Messaging-Cmdlets](unified-messaging-cmdlet-updates-exchange-2013-help.md).

