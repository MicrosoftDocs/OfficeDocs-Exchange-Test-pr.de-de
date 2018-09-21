---
title: 'Konfigurieren d. Exchange-Einstellungen f. E-Mail-Routing in Active Directory'
TOCTitle: Konfigurieren der Exchange-Einstellungen für E-Mail-Routing in Active Directory
ms:assetid: d01f8545-c201-4a96-be39-ed4c7008afcf
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ674705(v=EXCHG.150)
ms:contentKeyID: 50476765
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren der Exchange-Einstellungen für E-Mail-Routing in Active Directory

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Standardmäßig referenziert Microsoft Exchange Server 2013 die IP-Standortlinkobjekte in Active Directory, um den kostengünstigsten Routingpfad zu bestimmen. Wenn Sie jedoch feststellen, dass die IP-Standortverknüpfungskosten in Active Directory und die Datenverkehrsmuster nicht optimal für das Nachrichtenrouting in Exchange sind, können Sie Einstellungen in Active Directory konfigurieren, die nur von Exchange zur Optimierung des Nachrichtenflusses verwendet werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Active Directory-Standort und Standortlinkverwaltung" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Konfigurieren von Exchange-spezifischen Kosten für einen IP-Standortlink in Active Directory mit der Shell

Ermitteln Sie den Namen der IP-Standortverknüpfung in Active Directory, für den Exchange-Kosten festgelegt werden sollen. Ein geringerer Kostenwert kennzeichnet eine bevorzugte Route. Sie können den Inhalt der Routingtabellenprotokolle untersuchen und die Daten im Abschnitt **ADTopologyPath ID** anzeigen, um Einzelheiten zu dem berechneten kostengünstigsten Routingpfad zwischen zwei Active Directory-Standorten zu ermitteln.

Führen Sie folgenden Befehl aus, um die Exchange-spezifischen Kosten für einen Active Directory-Standortlink festzulegen:

``` 
 Set-AdSiteLink <ADSiteLinkIdentity> -ExchangeCost <Integer | $null>
```

In diesem Beispiel werden Exchange-spezifische Kosten mit dem Wert 10 dem IP-Standortlink "IPSiteLinkAB" hinzugefügt.

```powershell
Set-AdSiteLink IPSiteLinkAB -ExchangeCost 10
```

In diesem Beispiel werden die Exchange-Kosten des IP-Standortlinks "IPSiteLinkAB" gelöscht.

```powershell
Set-AdSiteLink IPSiteLinkAB -ExchangeCost $null
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie erfolgreich Exchange-Kosten für einen Active Directory-Standortlink festgelegt haben:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-AdSiteLink | Format-List Name,ExchangeCost
```

2.  Stellen Sie sicher, dass die Exchange-Kosten für den Active Directory-Standortlink konfiguriert sind.

## Konfigurieren eines Active Directory-Standorts als Hubstandort mithilfe der Shell

Wenn entlang des kostengünstigsten Routingpfads für eine Nachricht ein Hubstandort vorhanden ist, muss die Nachricht über den Hubstandort geleitet werden. Untersuchen Sie den Inhalt der Routingtabellenprotokolle, und zeigen Sie die Daten im Abschnitt **ADTopologyPath ID** an, um zu überprüfen, ob sich der ausgewählte Standort im kostengünstigsten Routingpfad zwischen zwei Active Directory-Standorten befindet. Falls dies nicht der Fall sein sollte, müssen Sie den IP-Standortlinks Exchange-spezifische Kosten hinzufügen, um die ausgewählten Standorte in den kostengünstigsten Routingpfad aufzunehmen.

Führen Sie folgenden Befehl aus, um einen Active Directory-Standort als Hubstandort zu konfigurieren:

```powershell
Set-AdSite <ADSiteIdentity> -HubSiteEnabled $true
```

In diesem Beispiel wird der Active Directory-Standort "Site A" als Hubstandort konfiguriert.

```powershell
Set-AdSite "Site A" -HubSiteEnabled $true
```

In diesem Beispiel wird das Hubstandortattribut vom Active Directory-Standort "Site B" entfernt.

```powershell
Set-AdSite "Site B" -HubSiteEnabled $false
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie folgende Schritte aus, um zu überprüfen, ob Sie erfolgreich einen Active Directory-Standort als Hubstandort konfiguriert haben:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-AdSite | Format-List Name,HubSiteEnabled
```

2.  Überprüfen Sie, ob der Wert *HubSiteEnabled* für den Active Directory-Standort `True` ist.

