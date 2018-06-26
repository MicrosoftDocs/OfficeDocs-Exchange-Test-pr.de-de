---
title: 'Konfigurieren der OAuth-Authentifizierung mit SharePoint 2013 und Lync 2013: Exchange 2013 Help'
TOCTitle: Konfigurieren der OAuth-Authentifizierung mit SharePoint 2013 und Lync 2013
ms:assetid: ca3c78a3-80cc-4df2-859f-0106bbd57a07
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ649094(v=EXCHG.150)
ms:contentKeyID: 50476685
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der OAuth-Authentifizierung mit SharePoint 2013 und Lync 2013

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-03-03_

In Exchange Server 2013 können andere Anwendungen OAuth für die Authentifizierung bei Exchange verwenden. Die Anwendungen müssen als Partneranwendungen in Exchange 2013 konfiguriert werden.

In Exchange 2013 wird die OAuth-Konfiguration mit Partneranwendungen wie SharePoint 2013 und Lync Server 2013 nur durch die Verwendung des Skripts `Configure-EnterpriseApplication.ps1` unterstützt. Durch die Automatisierung der Aufgabe vereinfacht das Skript die Konfiguration der Authentifizierung mit Partneranwendungen und reduziert Konfigurationsfehler. Mit dem Skript werden die folgenden Aufgaben ausgeführt:

1.  Konfiguration einer Unternehmenspartneranwendung, die selbst OAuth-Token für die erfolgreiche Authentifizierung bei Exchange ausgibt.

2.  Zuweisung von RBAC-Rollen (Role Based Access Control, rollenbasierte Zugriffssteuerung) zur Partneranwendung, um das Aufrufen bestimmter Exchange-Webdienste-APIs durch die Anwendung zu autorisieren.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Die Partneranwendung muss ein Dokument mit Autorisierungsmetadaten für Exchange 2013 veröffentlichen, um eine direkte Vertrauensstellung mit dieser Anwendung herzustellen und Authentifizierungsanforderungen zu akzeptieren.

  - In den Beispielen in diesem Thema wird der folgende Standardspeicherort des Verzeichnisses `\Scripts` verwendet: `C:\Program Files\Microsoft\Exchange Server\V15\Scripts`.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Partneranwendungen – Konfiguration" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Konfigurieren der OAuth-Authentifizierung mit einer Partneranwendung

In diesem Verfahren wird das Skript `Configure-EntepririseApplication.ps1` verwendet, um die OAuth-Authentifizierung mit Partneranwendungen zu konfigurieren. Der Zugriff auf Ressourcen hängt von den Berechtigungen, die der Partneranwendung zugewiesen sind, und/oder dem Benutzer, dessen Identität mit RBAC angenommen wird, ab.

Nach der Konfiguration der OAuth-Authentifizierung mit Exchange kann die Partneranwendung Exchange 2013-Ressourcen verwenden. Wenn Exchange 2013 auch Zugriff auf Ressourcen der Partneranwendung benötigt, müssen Sie die OAuth-Authentifizierung auch in der Partneranwendung konfigurieren.

In diesem Beispiel wird die OAuth-Authentifizierung für SharePoint 2013 konfiguriert.

    Cd C:\Program Files\Microsoft\Exchange Server\V15\Scripts
    Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl https://sharepoint.contoso.com/_layouts/15/metadata/json/1 -ApplicationType SharePoint

In diesem Beispiel wird die OAuth-Authentifizierung für Lync Server 2013 konfiguriert.

    Cd C:\Program Files\Microsoft\Exchange Server\V15\Scripts
    Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl https://lync.contoso.com/metadata/json/1 -ApplicationType Lync

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Sie können überprüfen, ob Sie eine Unternehmenspartneranwendung erfolgreich für die Authentifizierung bei Exchange 2013 konfiguriert haben, indem Sie das Cmdlet [Get-PartnerApplication](https://technet.microsoft.com/de-de/library/jj218721\(v=exchg.150\)) in der Shell ausführen, um die Konfiguration abzurufen. Sie können auch das Cmdlet [Test-OAuthConnectivity](https://technet.microsoft.com/de-de/library/jj218623\(v=exchg.150\)) ausführen, um die OAuth-Verbindung mit einer Partneranwendung für einen Benutzer zu testen.

## Weitere Informationen

  - In einer Hybridbereitstellung können Sie die OAuth-Authentifizierung zwischen der lokalen Exchange 2013-Organisation und der Exchange Online-Organisation verwenden. Weitere Informationen finden Sie unter [Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung](using-oauth-authentication-to-support-ediscovery-in-an-exchange-hybrid-deployment-exchange-2013-help.md).

  - In lokalen Bereitstellungen können Sie die serverbezogene Authentifizierung zwischen Exchange 2013 und SharePoint 2013 konfigurieren, sodass Administratoren und Compliance-Beauftragte das eDiscovery Center in SharePoint 2013 zum Durchsuchen von Exchange 2013-Postfächern verwenden können. Weitere Informationen finden Sie unter [Konfigurieren von Exchange für SharePoint eDiscovery Center](configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md).

