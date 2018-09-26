---
title: 'Man. Konfig. d. Edge-Transport-Server-Nachrichtenüberm.: Exchange 2013-Hilfe'
TOCTitle: Manuelles Konfigurieren der Edge-Transport-Server-Nachrichtenübermittlung
ms:assetid: cb4cc165-6c09-44ab-a95f-167ae8ed2485
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn606261(v=EXCHG.150)
ms:contentKeyID: 61180474
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Manuelles Konfigurieren der Edge-Transport-Server-Nachrichtenübermittlung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-21_

In diesem Thema werden Verfahren zum Durchführen manueller Konfigurationsänderungen beschrieben, um die Art und Weise festzulegen, wie ein Edge-Transport-Server die Nachrichtenübermittlung verwaltet. Diese Verfahren beziehen sich auf bestimmte Szenarien. Falls Ihre Organisation keine spezifischen Anforderungen zum Durchführen manueller Konfigurationsänderungen hat, wird die Standardkonfiguration beim Abonnieren von Edge-Transport-Servern bevorzugt verwendet.

**Inhalt**

Manuelles Konfigurieren von Sendeconnectors

Organisationsinterne Sendeconnectors

Erstellen von zusätzlichen Sendeconnectors nach dem Edge-Abonnement

Gründe, um die automatische Erstellung von Sendeconnectors zu unterdrücken

Partitionieren der Nachrichtenübermittlung

Weiterleiten von ausgehenden E-Mails an einen Smarthost

Konfigurieren von Sendeconnectors für externe Relaydomänen

## Manuelles Konfigurieren von Sendeconnectors

Sie können die Konfiguration eines Sendeconnectors manuell ändern. Wenn Sie beispielsweise ausgehende E-Mails über einen Smarthost weiterleiten müssen, können Sie die automatische Erstellung eines Sendeconnectors unterdrücken und einen Sendeconnector in das Internet manuell konfigurieren.

## Organisationsinterne Sendeconnectors

Der organisationsinterne Sendeconnector ist ein impliziter und verborgener Sendeconnector, der von Exchange automatisch berechnet wird. Er aktiviert den Transportdienst auf Postfachservern in der gleichen Organisation für das Relay von Nachrichten zwischen diesen Servern, ohne dass explizite Sendeconnectors verwendet werden. Da ein Konfigurationsobjekt mit einer Active Directory-Standortzuordnung in Active Directory für ein Edge-Abonnement vorhanden ist, wird der organisationsinterne Sendeconnector auch für das Relay von Nachrichten an diesen Edge-Transport-Server verwendet.

Nur Postfachserver, die am abonnierten Active Directory-Standort vorhanden sind, können E-Mails direkt auf den oder von dem abonnierten Edge-Transport-Server übertragen. Wenn Sie eine Active Directory-Gesamtstruktur mit mehreren Standorten verwenden und Exchange an mehreren Standorten bereitgestellt wird, leiten die Postfachserver an nicht abonnierten Standorten ausgehende E-Mails an den abonnierten Standort weiter. Ein Postfachserver am abonnierten Standort leitet ausgehende E-Mails an den Edge-Transport-Server weiter.

## Erstellen von zusätzlichen Sendeconnectors nach dem Edge-Abonnement

Nachdem ein Edge-Transport-Server für einen Active Directory-Standort abonniert wurde, sind die Cmdlets zum Erstellen und Ändern von Sendeconnectors auf dem Edge-Transport-Server deaktiviert. Wenn Sie einen Sendeconnector erstellen möchten, dessen Quellserver der Edge-Transport-Server ist, können Sie den Sendeconnector innerhalb der Exchange-Organisation erstellen. Sie können mindestens ein Edge-Abonnement als Quellserver für einen Sendeconnector angeben. Sie können nicht sowohl Postfachserver als auch Edge-Abonnements als Quellserver für den gleichen Sendeconnector angeben. Der Sendeconnector wird bei der nächsten Synchronisierung der Konfigurationsdaten durch EdgeSync in die AD LDS-Instanz auf dem Edge-Transport-Server repliziert, der als Quellserver konfiguriert ist. Wenn Sie mehrere Edge-Abonnements als Quellserver angeben, wird für Verbindungen mit diesem Sendeconnector ein Lastenausgleich zwischen den abonnierten Edge-Transport-Servern durchgeführt. Die Edge-Transport-Server müssen den gleichen Active Directory-Standort abonniert haben, damit der Lastenausgleich eintritt. Wenn Edge-Abonnements an verschiedenen Active Directory-Standorten als Quellserver für den gleichen Sendeconnector konfiguriert sind, leiten die Edge-Transport-Server Nachrichten nur an den nächstgelegenen Quellserver weiter.

Unter den folgenden Umständen müssen Sie Sendeconnectors manuell erstellen:

  - Sie haben die automatische Erstellung der Internet- oder Sendeconnectors für eingehende Nachrichten unterdrückt.

  - Sie verwenden akzeptierte Domänen in Ihrer Organisation, die als externe Relaydomänen konfiguriert sind.

## Gründe, um die automatische Erstellung von Sendeconnectors zu unterdrücken

Abhängig von der Topologie Ihrer Exchange-Organisation können Sie wahlweise die automatische Erstellung von Sendeconnectors unterdrücken. Die folgenden Beispiele beschreiben Szenarien, in denen es erforderlich ist, die automatische Erstellung von Sendeconnectors zu unterdrücken.

## Partitionieren der Nachrichtenübermittlung

Wenn Sie die Verarbeitung eingehender und ausgehender Nachrichten zwischen zwei Edge-Transport-Servern partitionieren möchten, ist ein Edge-Transport-Server für die Verarbeitung der ausgehenden Nachrichtenübermittlung verantwortlich, und ein zweiter Edge-Transport-Server ist für die Verarbeitung der eingehenden Nachrichtenübermittlung verantwortlich. Konfigurieren Sie zu diesem Zweck die Edge-Abonnements wie folgt:

  - Für den Edge-Transport-Server, der für die Verarbeitung der ausgehenden Nachrichtenübermittlung zuständig ist, führen Sie den folgenden Befehl auf dem Postfachserver aus.
    
    ```powershell
        New-EdgeSubscription -FileData ([byte[]]$(Get-Content -Path "C:\EdgeServerSubscription.xml" -Encoding Byte -ReadCount 0)) -Site "Site-A" -CreateInboundSendConnector $false -CreateInternetSendConnector $true
    ```
    
  - Für den Edge-Transport-Server, der für die Verarbeitung der eingehenden Nachrichtenübermittlung zuständig ist, führen Sie den folgenden Befehl auf dem Postfachserver aus.
    
    ```powershell
        New-EdgeSubscription -FileData ([byte[]]$(Get-Content -Path "C:\EdgeServerSubscription.xml" -Encoding Byte -ReadCount 0)) -Site "Site-A" -CreateInboundSendConnector $true -CreateInternetSendConnector $false
    ```
    
## Weiterleiten von ausgehenden E-Mails an einen Smarthost

Wenn Ihre Exchange-Organisation die gesamten ausgehenden E-Mails über einen Smarthost weiterleitet, weist der automatisch erstellte Sendeconnector nicht die richtige Konfiguration auf.

Führen Sie den folgenden Befehl auf dem Postfachserver aus, um die automatische Erstellung des Sendeconnectors in das Internet zu unterdrücken.

```powershell
    New-EdgeSubscription -FileData ([byte[]]$(Get-Content -Path "C:\EdgeServerSubscription.xml" -Encoding Byte -ReadCount 0)) -Site "Site-A" -CreateInternetSendConnector $false
```

Nachdem der Edge-Abonnementprozess abgeschlossen ist, erstellen Sie manuell einen Sendeconnector in das Internet. Erstellen Sie den Sendeconnector innerhalb der Exchange-Organisation, und wählen Sie das Edge-Abonnement als Quellserver für den Connector aus. Wählen Sie den Verwendungstyp `Custom` (Benutzerdefiniert) aus, und konfigurieren Sie mindestens einen Smarthost. Dieser neue Sendeconnector wird bei der nächsten Synchronisierung der Konfigurationsdaten durch EdgeSync in die AD LDS-Instanz auf dem Edge-Transport-Server repliziert. Sie können die sofortige EdgeSync-Synchronisierung erzwingen, indem Sie das Cmdlet **Start-EdgeSynchronization** auf einem Postfachserver ausführen.

Beispiel: Das Verwenden der Shell zum Konfigurieren eines Sendeconnectors für einen abonnierten Edge-Transport-Server, der die Nachrichten für alle Internetadressräume durch einen Smarthost weiterleitet. Führen Sie diese Aufgabe auf einem Postfachserver innerhalb der Exchange-Organisation und nicht auf dem Edge-Transport-Server aus.

```powershell
    New-SendConnector -Name "EdgeSync - Site-A to Internet" -Usage Custom -AddressSpaces SMTP:*;100 -DNSRoutingEnabled $false -SmartHosts 192.168.10.1 -SmartHostAuthMechanism None -SourceTransportServers EdgeSubscriptionName
```


> [!IMPORTANT]
> In diesem Beispiel wird kein Smarthost-Authentifizierungsmechanismus angegeben. Stellen Sie sicher, dass Sie den richtigen Authentifizierungsmechanismus konfigurieren, und stellen Sie alle erforderlichen Anmeldeinformationen zur Verfügung, wenn Sie einen Smarthostconnector in Ihrer eigenen Exchange-Organisation erstellen.



## Konfigurieren von Sendeconnectors für externe Relaydomänen

Wenn Sie akzeptierte Domänen in Ihrer Exchange-Organisation verwenden, die als externe Relaydomänen konfiguriert sind, müssen Sie einen Sendeconnector für diese Adressräume manuell erstellen. Nachrichten, die externen Relaydomänen zugestellt werden, werden vom Edge-Transport-Server mittels Relay weitergeleitet. Der Edge-Abonnementprozess erstellt und konfiguriert Sendeconnectors für externe Relaydomänen nicht automatisch. Aus diesem Grund müssen Sie Sendeconnectors für diese Domänen konfigurieren und mindestens ein Edge-Abonnement als Quellserver für diese Sendeconnectors angeben.

Der DNS MX-Ressourcendatensatz für eine externe Relaydomäne wird in Ihren Edge-Transport-Server aufgelöst. Sie können einen Sendeconnector konfigurieren, der E-Mails mittels Relay an eine externe Relaydomäne weiterleitet, um einen Smarthost für das Routing zu verwenden. Wenn Sie den Sendeconnector für eine externe Relaydomäne für die Verwendung von DNS-Routing konfigurieren, tritt eine Routingschleife auf. Weitere Informationen zu externen Relaydomänen finden Sie unter [Akzeptierte Domänen](accepted-domains-exchange-2013-help.md).

Zurück zum Seitenanfang

