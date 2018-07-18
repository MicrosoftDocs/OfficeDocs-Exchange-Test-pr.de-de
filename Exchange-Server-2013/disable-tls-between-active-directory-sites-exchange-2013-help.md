---
title: 'Deaktivieren von TLS zwischen Active Directory-Standorten: Exchange 2013 Help'
TOCTitle: Deaktivieren von TLS zwischen Active Directory-Standorten
ms:assetid: 1e1a0acf-24e7-4f94-9b33-603a4e0a812c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dd876856(v=EXCHG.150)
ms:contentKeyID: 52062838
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Deaktivieren von TLS zwischen Active Directory-Standorten

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-19_

Microsoft Exchange Server 2013 unterstützt das Deaktivieren von TLS für die SMTP-Kommunikation zwischen Postfachservern in bestimmten Topologien, in denen WOC-Geräte (WAN Optimization Controller) verwendet werden, die den SMTP-Datenverkehr komprimieren.

Diese Thema stellt Schrittanleitungen zum Konfigurieren des Transportdiensts in Ihren betreffenden Postfachservern bereit, sodass TLS deaktiviert und sichergestellt wird, dass Ihre Active Directory-Routingtopologie für die ordnungsgemäße Weiterleitung von Nachrichten konfiguriert ist. Weitere Informationen zu diesem Szenario finden Sie unter [Szenario: Konfigurieren von Exchange zur Unterstützung von WOC-Geräten (WAN Optimization Controller)](scenario-configure-exchange-to-support-wan-optimization-controllers-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 60 Minuten.

  - Einzelne Konfigurationsschritte in diesem Szenario können auch mit geringeren Berechtigungen durchgeführt werden. Um alle Aufgaben des End-to-End-Szenarios durchzuführen, muss Ihr Konto jedoch Mitglied der Rollengruppe "Organisationsverwaltung" sein.

  - Stellen Sie sicher, dass Sie TLS nur für Verbindungen deaktivieren, die WOC-Geräte durchlaufen.

  - Für dieses Verfahren ist es erforderlich, dass Exchange 2013 an mehreren Active Directory-Standorten bereitgestellt wird und mindestens ein Standort mit anderen Standorten über eine WAN-Verbindung verbunden ist.

  - Für dieses Verfahren ist es erforderlich, dass WOC-Geräte bereitgestellt werden, um den SMTP-Datenverkehr über die WAN-Verbindung zu komprimieren.

  - Für dieses Verfahren ist es erforderlich, dass ein Pfad für den logischen Meldungsfluss für Exchange vorhanden ist, welcher die WAN-Verbindung durchläuft, für die die WOC-Geräte bereitgestellt wurden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Schritt 1: Konfigurieren des Transportdiensts auf dem Postfachserver für die Verwendung der heruntergestuften Exchange Server-Authentifizierung mithilfe der Shell

Führen Sie den folgenden Befehl aus, um den Transportdienst auf einem Postfachserver für die Verwendung der heruntergestuften Exchange Server-Authentifizierung zu konfigurieren:

    Set-TransportService <ServerIdentity> -UseDowngradedExchangeServerAuth $true

In diesem Beispiel wird diese Konfigurationsänderung auf dem Server "Mailbox01" vorgenommen.

    Set-TransportService Mailbox01 -UseDowngradedExchangeServerAuth $true

## Schritt 2: Erstellen eines dedizierten Empfangsconnectors auf dem Postfachserver für den Active Directory-Zielstandort

## Erstellen des Empfangsconnectors mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Nachrichtenfluss** \> **Empfangsconnectors**, und klicken Sie dann auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)").

2.  Geben Sie auf der ersten Seite des Assistenten **Neuer Empfangsconnector** die folgenden Werte ein
    
      - **Name**   Geben Sie einen beschreibenden Wert ein.
    
      - **Typ**   Intern
    
    Klicken Sie nach Abschluss des Vorgangs auf **Weiter**.

3.  Geben Sie auf der zweiten Seite des Assistenten **Neuer Empfangsconnector** im Abschnitt **Remoteeinstellungen** die IP-Adressen oder IP-Adressbereiche für den Active Directory-Zielstandort ein. Klicken Sie nach Abschluss des Vorgangs auf **Fertig stellen**.

## Erstellen des Empfangsconnectors mithilfe der Shell

Führen Sie zum Erstellen eines Empfangsconnectors auf dem Postfachserver den folgenden Befehl aus:

    New-ReceiveConnector -Name <Name> -Server <ServerIdentity> -RemoteIPRanges <IPAddressRange> -Internal

In diesem Beispiel wird der Empfangsconnector namens "WAN" auf dem Server "Mailbox01" mit folgenden Einstellungen erstellt:

  - Der Parameter *RemoteIPRanges* wird auf "10.0.2.0/24" festgelegt. Dieser IP-Adressbereich sollte dem Active Directory-Remotestandort entsprechen, von dem der Empfangsconnector unverschlüsselte Verbindungen empfängt. Wenn der Remotestandort mehrere IP-Subnetze aufweist, können Sie diese sämtlich durch Komma getrennt eingeben.

  - Der Verwendungstyp wird auf "Internal" festgelegt.

<!-- end list -->

    New-ReceiveConnector -Name WAN -Server Hub01 -RemoteIPRanges 10.0.2.0/24 -Internal

## Schritt 3: Deaktivieren von TLS auf dem dedizierten Empfangsconnector mithilfe der Shell

Führen Sie zum Deaktivieren von TLS auf dem Empfangsconnector den folgenden Befehl aus:

    Set-ReceiveConnector <ReceiveConnectorIdentity> -SuppressXAnonymousTLS $true

In diesem Beispiel wird TLS auf dem Empfangsconnector "WAN" auf dem Postfachserver "Mailbox01" deaktiviert.

    Set-ReceiveConnector Mailbox01\WAN -SuppressXAnonymousTLS $true

## Schritt 4: Festlegen der Active Directory-Standorte als Hubstandorte mithilfe der Shell

Führen Sie folgenden Befehl aus, um einen Active Directory-Standort als Hubstandort festzulegen:

    Set-AdSite <ADSiteIdentity> -HubSiteEnabled $true

Diesen Vorgang müssen Sie einmal für jeden Active Directory-Standort ausführen, der über Postfachserver verfügt, die für unverschlüsselten Datenverkehr verwendet werden.

In diesem Beispiel wird der Active Directory-Standort "Central Office Site 1" als Hubstandort konfiguriert.

    Set-AdSite "Central Office Site 1" -HubSiteEnabled $true

## Schritt 5: Konfigurieren des kostengünstigsten Routingpfads über die WAN-Verbindung mithilfe der Shell

Je nach Konfiguration der Kosten für IP-Standortverknüpfungen in Active Directory kann dieser Schritt ggf. ausgelassen werden. Sie müssen sicherstellen, dass die Netzwerkverbindung mit den bereitgestellten WOC-Geräten sich auf dem kostengünstigsten Routingpfad befindet. Führen Sie den folgenden Befehl aus, um die Kosten für Active Directory-Standortverknüpfungen und die Exchange-spezifischen Kosten für Standortverknüpfungen anzuzeigen:

    Get-AdSiteLink

Wenn die Netzwerkverknüpfung mit den bereitgestellten WOC-Geräten sich nicht auf dem kostengünstigsten Routingpfad befindet, müssen Sie der jeweiligen IP-Standortverknüpfung Exchange-spezifische Kosten zuweisen, um eine ordnungsgemäße Weiterleitung der Nachrichten zu gewährleisten. Informationen zu diesem speziellen Aspekt finden Sie im Abschnitt "Konfigurieren Exchange-spezifischer Active Directory-Standortverknüpfungskosten" unter [Szenario: Konfigurieren von Exchange zur Unterstützung von WOC-Geräten (WAN Optimization Controller)](scenario-configure-exchange-to-support-wan-optimization-controllers-exchange-2013-help.md).

In diesem Beispiel werden Exchange-spezifische Kosten von 15 für die IP-Standortverknüpfung "Branch Office 2-Branch Office 1" konfiguriert.

    Set-AdSiteLink "Branch Office 2-Branch Office 1" -ExchangeCost 15

