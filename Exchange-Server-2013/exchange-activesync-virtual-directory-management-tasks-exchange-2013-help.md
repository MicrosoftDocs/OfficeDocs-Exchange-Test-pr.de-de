---
title: 'Exchange ActiveSync virtual Directory Management-Aufgaben: Exchange 2013 Help'
TOCTitle: Exchange ActiveSync virtual Directory Management-Aufgaben
ms:assetid: f0b339b7-e184-4392-a133-20523183459d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125170(v=EXCHG.150)
ms:contentKeyID: 50477036
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Exchange ActiveSync virtual Directory Management-Aufgaben

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2012-10-05_

Sie können verschiedene Anwendungseinstellungen von Exchange ActiveSync in Exchange Server 2013 über das virtuelle Exchange ActiveSync-Verzeichnis verwalten. Die Internetinformationsdienste (Internet Information Services, IIS) verwenden ein virtuelles Verzeichnis, um den Zugriff auf eine Webanwendung wie Exchange ActiveSync zu gestatten. Einige Einstellungen des virtuellen Verzeichnisses, die Sie für Exchange ActiveSync verwalten können, umfassen die Authentifizierung, Sicherheit und Berichterstellung.

## Einstellungen der virtuellen Verzeichnisse in Exchange ActiveSync

Folgende Eigenschaften und Einstellungen können für ein virtuelles Exchange ActiveSync-Verzeichnis geändert werden:

  - **InternalURL**   "InternalURL" gibt die URL an, mit der interne Clients auf das virtuelle Verzeichnis zugreifen können. Sie besitzt in der Regel das Format "https://servername/Microsoft-Server-ActiveSync". Wenn der NetBIOS-Name für den Server z. B. "Sequoia" lautet, entspricht "InternalURL" dem Wert "https://sequoia/Microsoft-Server-ActiveSync".

  - **ExternalURL**   "ExternalURL" gibt die URL an, mit der externe Clients auf das virtuelle Verzeichnis zugreifen können. Diese URL sollte von außerhalb des internen Netzwerks zugänglich sein. "ExternalURL" könnte z. B. "https://www.contoso.com/" lauten.

  - **Authentifizierungseinstellungen**   Die beiden Authentifizierungsmethoden, die Sie für das virtuelle Exchange ActiveSync-Verzeichnis konfigurieren können, sind die Standardauthentifizierung und die Clientzertifikatsauthentifizierung.

