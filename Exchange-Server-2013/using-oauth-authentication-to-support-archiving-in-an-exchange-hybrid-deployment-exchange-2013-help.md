---
title: 'Verwenden der OAuth-Authentifizierung zur Unterstützung der Archivierung in einer Exchange-Hybridbereitstellung: Exchange 2013 Help'
TOCTitle: Verwenden der OAuth-Authentifizierung zur Unterstützung der Archivierung in einer Exchange-Hybridbereitstellung
ms:assetid: deb882b1-1ae2-40f3-a71c-423fafe3d66a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn689104(v=EXCHG.150)
ms:contentKeyID: 62248371
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden der OAuth-Authentifizierung zur Unterstützung der Archivierung in einer Exchange-Hybridbereitstellung

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Wenn Sie in einer Exchange 2013-Hybridbereitstellung die Exchange Online-Archivierung (EOA) für Exchange Server verwenden, müssen Sie nach dem Aktualisieren auf das kumulative Update 5 (CU5) Exchange 2013 die OAuth-Authentifizierung zwischen Ihren lokalen und Exchange Online-Organisationen konfigurieren. Dank der EOA können Sie ein cloudbasiertes Archiv für Ihre Benutzer mit lokalen Postfächern haben. In diesem Szenario wendet der Assistent für die Verwaltung von Nachrichtendatensätzen (Messaging Records Management, MRM) Archivierungsrichtlinien auf Ihrem lokalen Postfachserver an und verschiebt die Nachrichten automatisch von einem Postfach eines Benutzers in dessen cloudbasiertes Archiv. In Exchange 2013 CU5 wird die OAuth-Authentifizierung verwendet.

Schrittweise Anleitungen zum Konfigurieren der OAuth-Authentifizierung finden Sie unter [Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen](configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help.md).

## Was ist die OAuth-Authentifizierung?

Die OAuth-Authentifizierung ist ein Server-zu-Server-Authentifizierungsprotokoll, das es Anwendungen ermöglicht, sich gegenseitig zu authentifizieren. Bei der OAuth-Authentifizierung werden Anmeldeinformationen von Benutzern und Kennwörter nicht von einem Computer an einen anderen weitergegeben. Stattdessen basieren Authentifizierung und Autorisierung auf dem Austausch von Sicherheitstoken, die für einen bestimmten Zeitraum den Zugriff auf einen bestimmten Satz an Ressourcen gewähren.

OAuth-Authentifizierung umfasst normalerweise drei Komponenten: einen Server mit Einzelanmeldung und zwei Bereiche, die miteinander kommunizieren müssen. Sicherheitstoken werden vom Autorisierungsserver (auch als Sicherheitstokenserver bezeichnet) an die zwei Bereiche ausgegeben, die kommunizieren müssen; diese Token prüfen, ob die Kommunikation des einen Bereichs für den anderen Bereich vertrauenswürdig ist. Bei der Verwendung der OAuth-Authentifizierung zwischen einer lokalen Exchange-Organisation und Exchange Online wird die Funktion des Autorisierungsservers von Azure Active Directory-Zugriffssteuerungsdienste (Access Control Services, ACS) in Ihrer Office 365-Organisation bereitgestellt. Beispielsweise stellt Azure Active Directory ACS während einer standortübergreifenden eDiscovery-Suche Token aus, die überprüfen, ob ein Administrator oder Compliance Officer aus der lokalen Exchange-Organisation auf Postfächer in der Exchange Online-Organisation zugreifen kann und umgekehrt.

## Konfigurieren der OAuth-Authentifizierung zur Unterstützung der Archiverung

Wie zuvor erwähnt, finden Sie unter [Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen](configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help.md) Anweisungen zur Konfiguration der OAuth-Authentifizierung zur Unterstützung der Archivierung in einer Exchange-Hybridbereitstellung.

Wenn OAuth für Ihre Exchange-Hybridbereitstellung nicht konfiguriert ist, können Sie keine Archivierungsrichtlinien verwenden, um Elemente automatisch von einem primären Postfach eines Benutzers in Ihrer lokalen Organisation in das cloudbasierte Archiv des Benutzers in Exchange Online zu verschieben.

## Weitere Informationen

  - Sie müssen die OAuth-Authentifizierung außerdem so konfigurieren, dass standortübergreifende eDiscovery-Suchen in Ihren lokalen und cloudbasierten Postfächern in einer einzelnen eDiscovery-Suche durchgeführt werden. Weitere Informationen finden Sie unter [Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung](using-oauth-authentication-to-support-ediscovery-in-an-exchange-hybrid-deployment-exchange-2013-help.md).

  - Sie können die OAuth-Authentifizierung auch so konfigurieren, dass andere Anwendungen, z. B. SharePoint 2013 und Lync Server 2013 sich bei Exchange 2013 authentifizieren können. Weitere Informationen finden Sie unter [Konfigurieren der OAuth-Authentifizierung mit SharePoint 2013 und Lync 2013](configure-oauth-authentication-with-sharepoint-2013-and-lync-2013-exchange-2013-help.md).

  - Sie können die Server-zu-Server-Authentifizierung zwischen Exchange 2013 und SharePoint 2013 so konfigurieren, dass Administratoren und Compliance Officer das eDiscovery Center in SharePoint 2013 verwenden können, um Exchange 2013-Postfächer zu durchsuchen. Weitere Informationen finden Sie unter [Konfigurieren von Exchange für SharePoint eDiscovery Center](configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md).

  - Sie können eine Exchange-Hybridbereitstellung mithilfe des Assistenten für die Hybridkonfiguration in Exchange 2013 konfigurieren. Eine benutzerdefinierte schrittweise Konfigurationsprüfliste für die Hybridbereitstellung finden Sie im [Bereitstellungs-Assistenten für Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=277105).

