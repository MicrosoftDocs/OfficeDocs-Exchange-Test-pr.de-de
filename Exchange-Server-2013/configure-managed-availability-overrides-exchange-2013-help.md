---
title: 'Konfig. von Überschreibungen für verw. Verfügbarkeit: Exchange 2013-Hilfe'
TOCTitle: Konfigurieren von Überschreibungen für die verwaltete Verfügbarkeit
ms:assetid: c8f315b3-1d5e-4ad9-8bea-9c3a4a13ebfc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn482055(v=EXCHG.150)
ms:contentKeyID: 59889668
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Überschreibungen für die verwaltete Verfügbarkeit

 

_**Gilt für:** Exchange Online, Exchange Server 2013 SP1_

_**Letztes Änderungsdatum des Themas:** 2015-11-30_

Die verwaltete Verfügbarkeit führt fortlaufend Messungen durch, um mögliche Probleme mit Exchange-Komponenten oder deren Abhängigkeiten zu erkennen. Außerdem führt sie Wiederherstellungsaktionen durch, um so sicherzustellen, dass die Anwenderfreundlichkeit aufgrund von Problemen mit einer dieser Komponenten nicht beeinträchtigt wird. Es können jedoch Szenarien auftreten, in denen die vorgegebenen Einstellungen für Ihre Umgebung möglicherweise nicht geeignet sind. Tastköpfe, Monitore und Antwortsender für die verwaltete Verfügbarkeit können durch die Erstellung von Überschreibungen angepasst werden.

Es werden zwei Arten von Überschreibungen unterschieden: lokal und global. Die Bezeichnung weist bereits darauf hin, dass eine lokale Überschreibung nur auf dem Server verfügbar ist, auf dem sie erstellt wurde. Eine globale Überschreibung dient dazu, eine Überschreibung auf mehrere Server anzuwenden. Beide Überschreibungsarten können für eine bestimmte Dauer oder für eine bestimmte Version von Exchange erstellt werden, jedoch nicht beide gleichzeitig.


> [!NOTE]
> Eine erstellte Überschreibung tritt nicht sofort in Kraft. Der Microsoft Exchange Health Management-Dienst prüft alle zehn Minuten, ob Konfigurationsänderungen vorgenommen wurden, und lädt die erkannten Konfigurationsänderungen. Wenn Sie nicht warten möchten, können Sie den Dienst auch neu starten.



Informationen zu weiteren Verwaltungsaufgaben im Zusammenhang mit verwalteter Verfügbarkeit finden Sie unter [Verwalten von Integritätssätzen und Serverintegrität](manage-health-sets-and-server-health-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Die Shell kann nur für diesen Vorgang verwendet werden.Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Exchange-Verwaltungsshell zum Erstellen einer lokalen Überschreibung

Verwenden Sie zu Erstellen einer lokalen Überschreibung die folgende Syntax.

    Add-ServerMonitoringOverride -Server <ServerName> -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertyName> -PropertyValue <Value> -Duration <dd.hh:mm:ss>

Verwenden Sie zu Erstellen einer lokalen Überschreibung für eine bestimmte Version von Exchange die folgende Syntax.

    Add-ServerMonitoringOverride -Server <ServerName> -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertyName> -PropertyValue <Value> -Version <15.01.xxxx.xxx>


> [!NOTE]
> Beachten Sie beim Erstellen der Überschreibung die Groß-/Kleinschreibung in den im <EM>Identity</EM>-Parameter verwendeten Werten.



In diesem Beispiel wird eine lokale Überschreibung hinzugefügt, die den `ActiveDirectoryConnectivityConfigDCServerReboot`-Antwortdienst auf dem Server mit dem Namen „EXCH03“ für 20 Tage deaktiviert.

    Add-ServerMonitoringOverride -Server EXCH03 -Identity "AD\ActiveDirectoryConnectivityConfigDCServerReboot" -ItemType Responder -PropertyName Enabled -PropertyValue 0 -Duration 20.00:00:00

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um zu überprüfen, ob die lokale Überschreibung erfolgreich erstellt wurde, verwenden Sie das **Get-ServerMonitoringOverride**-Cmdlet zum Anzeigen der Liste mit lokalen Überschreibungen:

    Get-ServerMonitoringOverride  -Server <ServerIdentity> | Format-List

Die Überschreibung sollte in der Liste angezeigt werden.

## Verwenden der Exchange-Verwaltungsshell zum Entfernen von lokalen Überschreibungen

Verwenden Sie die folgende Syntax, um eine lokale Überschreibung zu entfernen.

    Remove-ServerMonitoringOverride -Server <ServerName> -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <ExistingItemTypeValue> -PropertyName <PropertytoRemove>

In diesem Beispiel wird die vorhandene lokale Überschreibung des `ActiveDirectoryConnectivityConfigDCServerReboot`-Antwortdiensts im Exchange-Integritätssatz vom Server „EXCH01“ entfernt.

    Remove-ServerMonitoringOverride -Server EXCH01 -Identity Exchange\ActiveDirectoryConnectivityConfigDCServerReboot -ItemType Responder -PropertyName Enabled

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um zu überprüfen, ob die lokale Überschreibung erfolgreich entfernt wurde, verwenden Sie das **Get-ServerMonitoringOverride**-Cmdlet zum Anzeigen der Liste mit lokalen Überschreibungen:

    Get-ServerMonitoringOverride  -Server <ServerIdentity> | Format-List

Die entfernte Überschreibung sollte nicht mehr in der Liste angezeigt werden.

## Verwenden der Exchange-Verwaltungsshell zum Erstellen von globalen Überschreibungen

Verwenden Sie zu Erstellen einer globalen Überschreibung die folgende Syntax.

    Add-GlobalMonitoringOverride -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertytoOverride> -PropertyValue <NewPropertyValue> -Duration <dd.hh:mm:ss>

Verwenden Sie zu Erstellen einer globalen Überschreibung für eine bestimmte Version von Exchange die folgende Syntax.

    Add-GlobalMonitoringOverride -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <Probe | Monitor | Responder | Maintenance> -PropertyName <PropertytoOverride> -PropertyValue <NewPropertyValue> -ApplyVersion <15.01.xxxx.xxx>


> [!NOTE]
> Beachten Sie beim Erstellen der Überschreibung die Groß-/Kleinschreibung in den im <EM>Identity</EM>-Parameter verwendeten Werten.



In diesem Beispiel wird eine globale Überschreibung hinzugefügt, die den `OnPremisesInboundProxy`-Test für 30 Tage deaktiviert.

    Add-GlobalMonitoringOverride -Identity "FrontendTransport\OnPremisesInboundProxy" -ItemType Probe -PropertyName Enabled -PropertyValue 0 -Duration 30.00:00:00

In diesem Beispiel wird eine globale Überschreibung hinzugefügt, die den `StorageLogicalDriveSpaceEscalate`-Antwortdienst für alle Server mit Exchange Version 15.01.0225.042 deaktiviert.

    Add-GlobalMonitoringOverride -Identity "MailboxSpace\StorageLogicalDriveSpaceEscalate" -PropertyName Enabled -PropertyValue 0 -ItemType Responder -ApplyVersion "15.01.0225.042"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um zu überprüfen, ob die globale Serverüberschreibung erfolgreich erstellt wurde, verwenden Sie das Cmdlet **Get-GlobalMonitoringOverride** zum Anzeigen der Liste mit globalen Überschreibungen:

    Get-GlobalMonitoringOverride

Die Überschreibung sollte in der Liste angezeigt werden.

## Verwenden der Exchange-Verwaltungsshell zum Entfernen von globalen Überschreibungen

Verwenden Sie die folgende Syntax, um eine globale Überschreibung zu entfernen.

    Remove-GlobalMonitoringOverride -Identity <HealthSetName>\<MonitoringItemName>[\<TargetResource>] -ItemType <ExistingItemTypeValue> -PropertyName <OverriddenProperty>

In diesem Beispiel wird die vorhandene globale Überschreibung der `ExtensionAttributes`-Eigenschaft des `OnPremisesInboundProxy`-Tests im `FrontEndTransport`-Integritätssatz entfernt.

    Remove-GlobalMonitoringOverride -Identity FrontEndTransport\OnPremisesInboundProxy -ItemType Probe -PropertyName ExtensionAttributes

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Um zu überprüfen, ob die globale Serverüberschreibung erfolgreich entfernt wurde, verwenden Sie das Cmdlet **Get-GlobalMonitoringOverride** zum Anzeigen der Liste mit globalen Überschreibungen:

    Get-GlobalMonitoringOverride

Die entfernte Überschreibung sollte nicht mehr in der Liste angezeigt werden.

