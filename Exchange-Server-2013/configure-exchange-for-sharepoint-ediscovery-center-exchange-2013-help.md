---
title: 'Konfig. v. Exchange f. SharePoint eDiscovery Center: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von Exchange für SharePoint eDiscovery Center
ms:assetid: 795c1a3b-295c-4ee5-ade9-52cf3fda3f19
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ218665(v=EXCHG.150)
ms:contentKeyID: 50475985
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Exchange für SharePoint eDiscovery Center

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Microsoft Exchange Server 2013 umfasst Funktionen für die Arbeit mit Microsoft SharePoint Server 2013 und Microsoft Lync Server 2013, diese werden als *Partneranwendungen* bezeichnet. Damit diese Partneranwendungen gegenseitig auf Ressourcen zugreifen können, müssen Sie die Server-zu-Server-Authentifizierung konfigurieren.

In diesem Thema wird erläutert, wie Sie die Server-zu-Server-Authentifizierung zwischen Exchange 2013 und SharePoint 2013 konfigurieren, sodass Benutzer ihre Exchange Server 2013-Postfachinhalte über das eDiscovery Center in SharePoint 2013 durchsuchen können. Sie müssen zusätzliche Schritte in SharePoint 2013 ausführen, um diese Funktionalität vollständig zu aktivieren. Ausführliche Informationen hierzu finden Sie unter [Konfigurieren von eDiscovery in SharePoint 2013](https://go.microsoft.com/fwlink/?linkid=257727).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 30 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Die Funktion wird unterstützt, um Exchange 2013 und SharePoint 2013 in verschiedenen Domänen oder Gesamtstrukturen zu installieren. Es ist keine vertrauenswürdige Windows-Beziehung zwischen den Exchange- und SharePoint-Gesamtstrukturen erforderlich, da sich Exchange und SharePoint in diesem Fall durch das OAuth 2.0-Protokoll gegenseitig vertrauen.

  - Die SharePoint 2013-Website muss zur Verwendung von Secure Sockets Layer (SSL) konfiguriert sein.

  - Die [Verwaltete API für Exchange-Webdienste](https://go.microsoft.com/fwlink/?linkid=257726) muss auf jedem Server installiert sein, auf dem SharePoint 2013 ausgeführt wird. Setzen Sie Internet Information Server (IIS) nach der Installation zurück.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Konfigurieren der Server-zu-Server-Authentifizierung für Exchange 2013 auf einem Server mit SharePoint Server 2013

Führen Sie folgenden Befehl aus, um Exchange 2013 als vertrauenswürdigen Aussteller von Sicherheitstoken in SharePoint 2013 zu erstellen:

```powershell
    New-SPTrustedSecurityTokenIssuer -Name Exchange -MetadataEndPoint https://<Exchange Server Name or FQDN>/autodiscover/metadata/json/1
```

## Schritt 2: Konfigurieren der Server-zu-Server-Authentifizierung für SharePoint 2013 auf einem Server mit Exchange 2013

Führen Sie diesen Schritt auf einem Exchange 2013-Server aus. Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Partneranwendungen – Konfiguration" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

Führen Sie diesen Befehl aus, um die SharePoint-Partneranwendung zu konfigurieren.

```powershell
    cd c:\'Program Files'\Microsoft\'Exchange Server'\V15\Scripts
    .\Configure-EnterprisePartnerApplication.ps1 -AuthMetadataUrl <path to SharePoint AuthMetadataUrl> -ApplicationType SharePoint
```

## Schritt 3: Hinzufügen von autorisierten Benutzern zur Rollengruppe "Discoveryverwaltung"

Fügen Sie der Rollengruppe "Discoveryverwaltung" in Exchange 2013 Benutzer hinzu, die SharePoint 2013 verwenden müssen, um eDiscovery-Suchen durchzuführen. Weitere Informationen finden Sie unter [Zuweisen von eDiscovery-Berechtigungen in Exchange](https://technet.microsoft.com/de-de/library/Dd298059(v=EXCHG.150)).


> [!WARNING]
> Indem Sie Benutzer der Rollengruppe "Discoveryverwaltung" hinzufügen, ermöglichen Sie ihnen, die Compliance-eDiscovery zu verwenden, um alle Exchange 2013-Postfächer zu durchsuchen und auf möglicherweise vertrauliche E-Mail-Inhalte in den Benutzerpostfächern zuzugreifen. Diese Berechtigung ist standardmäßig keinem Benutzer zugewiesen, einschließlich der Mitglieder der Rollengruppe "Organisationsverwaltung". Setzen Sie sich mit der Rechts- oder Personalabteilung Ihrer Organisation in Verbindung, bevor Sie diese Berechtigung einem Benutzer zuweisen.


