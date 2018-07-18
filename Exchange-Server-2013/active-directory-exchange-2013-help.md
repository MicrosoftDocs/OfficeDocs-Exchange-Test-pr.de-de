---
title: 'Active Directory: Exchange 2013 Help'
TOCTitle: Active Directory
ms:assetid: 8e8464df-2d1d-4d68-82de-b0c158c549c3
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123715(v=EXCHG.150)
ms:contentKeyID: 50476149
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Active Directory

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Exchange Server 2013 verwendet Active Directory zum Speichern und Freigeben von Verzeichnisinformationen für Windows. Das Active Directory-Gesamtstrukturdesign für Exchange 2013 ähnelt Exchange Server 2010 mit wenigen Ausnahmen, die im Folgenden erläutert werden.

## Active Directory-Treiber

Der Active Directory-Treiber ist die Microsoft Exchange-Kernkomponente, die es den Exchange-Diensten ermöglicht, Daten der Active Directory-Domänendienste zu erstellen, zu ändern, zu löschen und abzufragen. In Exchange 2013 erfolgt der gesamte Zugriff auf Active Directory über den Active Directory-Treiber selbst. In Exchange 2010 stellt DSAccess Verzeichnissuchdienste für Komponenten wie SMTP, den Nachrichtenübermittlungs-Agent (MTA) und den Exchange-Speicher bereit.

Der Active Directory-Treiber verwendet zudem die Microsoft ExchangeActive Directory-Topologie (MSExchangeADTopology), die es dem Active Directory-Treiber ermöglicht, die DSAccess-Topologiedaten (Directory Service Access) zu nutzen. Zu diesen Daten gehört eine Liste der verfügbaren Domänencontroller und globalen Katalogserver, die für die Verarbeitung von Exchange-Anforderungen zur Verfügung stehen. Weitere Informationen über den Active Directory-Treiber finden Sie unter [Active Directory-Domänendienste](https://go.microsoft.com/fwlink/p/?linkid=110942) .

## Active Directory-Schemaänderungen

Exchange 2013 fügt dem Active Directory-Domänendienstschema neue Attribute hinzu und nimmt weitere Änderungen an vorhandenen Klassen und Attributen vor. Weitere Informationen zu Active Directory-Änderungen bei der Installation von Exchange 2013 finden Sie unter [Änderungen des Active Directory-Schemas in Exchange 2013](exchange-2013-active-directory-schema-changes-exchange-2013-help.md).

## Weitere Informationen

Weitere Informationen dazu, wie Exchange 2013 Daten in Active Directory speichert und daraus abruft, erhalten Sie unter [Zugriff auf Active Directory](access-to-active-directory-exchange-2013-help.md).

Weitere Informationen über das Design der Active Directory-Gesamtstruktur finden Sie unter [AD DS-Entwurfsleitfaden](https://go.microsoft.com/fwlink/p/?linkid=264957) .

Weitere Informationen zu Computern, die Windows in einer Active Directory-Domäne ausführen und Exchange 2013 in einer Domäne mit einem nicht zusammenhängenden Namespace bereitstellen, finden Sie unter [Szenarien mit nicht zusammenhängenden Namespaces](disjoint-namespace-scenarios-exchange-2013-help.md).

