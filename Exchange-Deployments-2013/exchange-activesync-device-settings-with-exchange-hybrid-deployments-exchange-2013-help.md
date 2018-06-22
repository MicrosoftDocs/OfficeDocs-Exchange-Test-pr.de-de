---
title: 'Exchange ActiveSync-Geräteeinstellungen mit Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Exchange ActiveSync-Geräteeinstellungen mit Exchange-Hybridbereitstellungen
ms:assetid: 77f7cd72-2a8a-467e-9ffd-b93f5eeb2f69
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn931281(v=EXCHG.150)
ms:contentKeyID: 64965198
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Exchange ActiveSync-Geräteeinstellungen mit Exchange-Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-01-27_

Exchange ActiveSync-Geräte werden automatisch erneut konfiguriert, wenn ein Postfach von einer lokalen Exchange-Organisation zu Office 365 verschoben wird. Exchange ActiveSync sucht nach dem neuen Postfachort in Office 365 und aktualisiert seine Konfiguration, um direkt mit Office 365 zu kommunizieren. Das Exchange ActiveSync-Gerät versucht keine Verbindung zum lokalen Exchange-Server herzustellen, nachdem es erfolgreich an Office 365 umgeleitet wurde. Abgesehen von einigen wenigen Ausnahmen (im Folgenden dazu mehr) muss der Benutzer sein Gerät nicht mehr manuell einrichten, damit die E-Mails funktionieren.

Informationen über das Verschieben eines Postfachs zu Office 365 finden Sie unter [Verschieben von Postfächern zwischen lokalen und Exchange Online-Organisationen in Hybridbereitstellungen](move-mailboxes-between-on-premises-and-exchange-online-organizations-in-hybrid-deployments-exchange-2013-help.md).

Weitere Informationen zu Hybridbereitstellungen finden Sie unter [Hybridbereitstellungen in Exchange Server](exchange-server-hybrid-deployments-exchange-2013-help.md).

Zum Verwenden der automatischen Umleitung müssen auf Ihren lokalen Servern die neuesten Versionen von Exchange 2010, Exchange 2013, Exchange 2016 oder höher ausgeführt werden. Sie müssen zudem [Assistent für die Hybridkonfiguration](hybrid-configuration-wizard-exchange-2013-help.md) verwendet haben, um Ihre Hybridbereitstellung einzurichten. Die Exchange ActiveSync-Umleitungsfunktion verwendet die Outlook im Web-Ziel-URL, die im Organisationsbeziehungsobjekt festgelegt ist. Dieses Objekt wird konfiguriert, wenn der Assistent für die Hybridkonfiguration ausgeführt wird.

Wenn Ihre Organisation die oben aufgeführten Anforderungen erfüllt, sollten Mobilgeräte automatisch ohne zusätzlich Konfiguration an Office 365 umgeleitet werden, wenn das Postfach eines Benutzers verschoben wird. Stellen Sie für eine optimale Verwendung sicher, dass auf den Mobilgeräten Ihrer Benutzer die neuesten Versionen der Betriebssysteme und E-Mail-Clients ausgeführt werden. Bei einigen Mobilgeräten, beispielsweise jene, auf denen das Android-Betriebssystem ausgeführt wird, dauert die Umleitung länger als erwartet. Zudem interpretieren einige Geräte möglicherweise die durch Exchange gesendeten Exchange ActiveSync 451-Umleitungsanweisungen nicht richtig. Bei diesen Geräten müssen Benutzer weiterhin ihre E-Mail-Konten auf den entsprechenden Geräten erneut konfigurieren und erneut erstellen. Wenn Sie Fragen haben, ob ein Gerät die Exchange ActiveSync 451-Umleitung unterstützt, wenden Sie sich an den Geräteherstellen.

Die automatische Exchange ActiveSync-Umleitung wird in den folgenden Szenarien nicht unterstützt:

  - Verschieben von Postfächern von Office 365 zu einer lokalen Exchange-Organisation.

  - Verschieben von Postfächern zwischen lokalen Exchange-Organisationen.

  - Verschieben von Postfächern von Exchange 2007-Servern zu Office 365.

