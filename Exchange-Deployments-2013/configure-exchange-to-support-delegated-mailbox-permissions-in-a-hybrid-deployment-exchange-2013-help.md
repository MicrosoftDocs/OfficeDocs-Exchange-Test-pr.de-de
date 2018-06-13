---
title: 'Konfigurieren von Exchange für delegierte Postfachberechtigungen in einer Hybridbereitstellung: Exchange 2013 Help'
TOCTitle: Konfigurieren von Exchange für delegierte Postfachberechtigungen in einer Hybridbereitstellung
ms:assetid: a2a10cb3-4557-4ff5-8191-c653522f4512
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Mt784505(v=EXCHG.150)
ms:contentKeyID: 74447328
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Konfigurieren von Exchange für delegierte Postfachberechtigungen in einer Hybridbereitstellung

 

_**Letztes Änderungsdatum des Themas:**2018-01-30_

Mit delegierten Postfachberechtigungen wird Benutzern das Verwalten eines Teils eines anderen Benutzerpostfachs ermöglicht. Ein allgemeines Beispiel hierfür stellen Verwaltungsassistenten dar, die das Postfach und den Kalender einer Führungskraft verwalten müssen. Hybridbereitstellungen zwischen einer lokalen Exchange-Organisation und Office 365 unterstützen die delegierten Postfachberechtigungen **Vollzugriff** und **Senden im Auftrag von**. Je nach der installierten Exchange-Version in der lokalen Organisation müssen Sie möglicherweise zusätzliche Konfigurationsschritte ausführen, um delegierte Berechtigungen in einer Hybridbereitstellung zu verwenden. Im Folgenden werden die Versionen von Exchange aufgeführt, die delegierte Postfachberechtigungen in einer Hybridbereitstellung unterstützen, sowie die erforderlichen zusätzlichen Konfigurationsschritte für die jeweilige Version.

  - **Exchange 2016** Keine zusätzliche Konfiguration erforderlich.

  - **Exchange 2013** Ein unterstütztes kumulatives Update für Exchange 2013 und zusätzliche Konfigurationsschritte sind erforderlich.

  - **Exchange 2010** Ein unterstütztes Updaterollup für Exchange 2010 und zusätzliche Konfigurationsschritte sind erforderlich.

Weitere Informationen zu den Voraussetzungen für die Unterstützung von delegierten Berechtigungen in einer Hybridbereitstellung finden Sie unter [Berechtigungen in Exchange-Hybridbereitstellungen](permissions-in-exchange-hybrid-deployments-exchange-2013-help.md).

In den folgenden Abschnitten werden die einzelnen Konfigurationsschritte für lokale Exchange 2013- und Exchange 2010-Bereitstellungen für die Unterstützung von delegierten Postfachberechtigungen erläutert. Bevor Sie diese Schritte ausführen, müssen Sie sicherstellen, dass das neueste kumulative Update für Exchange 2013 und das Rollup für Exchange SP3 installiert ist. Weitere Informationen finden Sie unter [Voraussetzungen für die Hybridbereitstellung](hybrid-deployment-prerequisites-exchange-2013-help.md).

## Exchange 2013

Die für die Unterstützung von delegierten Postfachberechtigungen erforderlichen Schritte sind von einigen Faktoren abhängig. Wenn Sie Postfächer zu Office 365 verschoben haben und folgende Voraussetzungen zu diesem Zeitpunkt erfüllt waren:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Folgende Komponenten waren installiert...</th>
<th>Und die ACL-Objektsynchronisierung war in der Organisation...</th>
<th>Müssen folgende Voraussetzungen erfüllt sein...</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2013 mit kumulativem Update 9 oder älter</p></td>
<td><p>Dieses Feature ist in Exchange 2013 mit kumulativem Update 9 und älter nicht verfügbar.</p></td>
<td><p>Konfigurieren Sie jedes Postfach manuell für die Unterstützung von Zugriffssteuerungslisten.</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2013 mit kumulativem Update 10 oder höher</p></td>
<td><p>Deaktiviert</p></td>
<td><ol>
<li><p>Aktivieren Sie die ACL-Objektsynchronisierung auf Organisationsebene.</p></li>
<li><p>Aktivieren Sie die Zugriffssteuerungslisten für jedes Postfach, das vor der Aktivierung der ACL-Objektsynchronisierung auf Organisationsebene zu Office 365 verschoben wurde.</p></li>
</ol>
<p>Keine zusätzliche Konfiguration für Postfächer erforderlich, die nach der Aktivierung der ACL-Objektsynchronisierung auf Organisationsebene zu Office 365 verschoben wurden.</p></td>
</tr>
<tr class="odd">
<td><p>Exchange 2013 mit kumulativem Update 10 oder höher</p></td>
<td><p>Aktiviert</p></td>
<td><p>Keine zusätzliche Konfiguration erforderlich.</p></td>
</tr>
</tbody>
</table>


## Aktivieren der ACL-Objektsynchronisierung

So aktivieren Sie die ACL-Objektsynchronisierung auf Organisationsebene

1.  Installieren Sie die neueste Version von Azure Active Directory Connect (AAD Connect) auf allen AAD Connect-Servern. Dies ist erforderlich, damit AAD Connect die Attribute synchronisieren kann, die für die Unterstützung von Hybridberechtigungen erforderlich sind. Sie können AAD Connect unter [Microsoft Azure Active Directory Connect](http://go.microsoft.com/fwlink/p/?linkid=510956). herunterladen.

2.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Server mit der Exchange 2013-Version mit dem aktuellen verfügbaren kumulativen Update oder dem unmittelbar vorhergehenden kumulativem Update.

3.  Führen Sie den folgenden Befehl aus.
    
        Set-OrganizationConfig -ACLableSyncedObjectEnabled $True

Anschließen werden alle Postfächer, die zu Office 365 verschoben werden, ordnungsgemäß für die Unterstützung von delegierten Berechtigungen konfiguriert. Wenn die Postfächer vor Durchführung dieser Schritte zu Office 365 verschoben wurden, müssen Sie die Zugriffssteuerungslisten für diese Postfächer manuell mithilfe der Schritte unter Aktivieren von Zugriffssteuerungslisten für Remotepostfächer aktivieren.


> [!IMPORTANT]
> ACLs werden nicht auf remote in Office 365 erstellten Postfächer aktiviert. Wenn Sie ein Remotepostfach in Office 365 erstellen, müssen Sie die Schritte in der ACLs aktivieren auf remotepostfächer Abschnitt aus, um ACLs für dieses Postfach remote zu aktivieren. Um diese zusätzlichen Schritt zu vermeiden, wird empfohlen, dass das Postfach auf einem lokalen Exchange-Server zu erstellen und anschließend das Postfach in Office 365 verschieben.



## Aktivieren von Zugriffssteuerungslisten für Remotepostfächer

Führen Sie die folgenden Schritte durch, um die Zugriffssteuerungslisten für Postfächer zu aktivieren, die vor der Aktivierung der ACL-Objektsynchronisierung auf Organisationsebene zu Office 365 verschoben wurden:

1.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Server mit der Exchange 2013-Version mit dem aktuellen verfügbaren kumulativen Update oder dem unmittelbar vorhergehenden kumulativem Update.

2.  Führen Sie zum Aktivieren von Zugriffssteuerungslisten für ein einzelnes Postfach den folgenden Befehl aus:
    
        Get-AdUser <Identity> | Set-AdObject -Replace @{msExchRecipientDisplayType=-1073741818}

3.  Führen Sie zum Aktivieren von Zugriffssteuerungslisten für alle zu Office 365 verschobene Postfächer den folgenden Befehl aus:
    
        Get-RemoteMailbox | ForEach { Get-AdUser -Identity $_.Guid | Set-ADObject -Replace @{msExchRecipientDisplayType=-1073741818}}

4.  Führen Sie den folgenden Befehl aus, um sicherzustellen, dass die Postfächer erfolgreich aktualisiert wurden:
    
        Get-RemoteMailbox | ForEach { Get-AdUser -Identity $_.Guid -Properties msExchRecipientDisplayType | Format-Table -AutoSize DistinguishedName, msExchRecipientDisplayType}

## Exchange Server 2010

Exchange 2010 SP3-Server unterstützen die Konfiguration der Zugriffssteuerungslisten für Remotepostfächer. Diese Konfiguration muss jedoch für jedes Postfach manuell festgelegt werden. Im Gegensatz zu neueren Versionen von Exchange bietet Exchange 2010 keine Möglichkeit, dieses Feature auf Organisationsebene festzulegen. Sie müssen die folgenden Schritte für alle Postfächer durchführen, die zuvor zu Office 365 verschoben wurden, und für alle Postfächer, die in Zukunft von einem Exchange 2010 SP3-Server zu Office 365 verschoben werden.

## Aktivieren von Zugriffssteuerungslisten für Remotepostfächer

Führen Sie zum Aktivieren von Zugriffssteuerungslisten für zu Office 365 verschobene Postfächer folgende Schritte durch:

1.  Öffnen Sie die Exchange-Verwaltungsshell auf einem Server mit dem neuesten Exchange 2010 SP3-Updaterollup oder dem unmittelbar vorhergehenden Updaterollup.

2.  Führen Sie zum Aktivieren von Zugriffssteuerungslisten für ein einzelnes Postfach den folgenden Befehl aus:
    
        Get-AdUser <Identity> | Set-AdObject -Replace @{msExchRecipientDisplayType=-1073741818}

3.  Führen Sie zum Aktivieren von Zugriffssteuerungslisten für alle zu Office 365 verschobene Postfächer den folgenden Befehl aus:
    
        Get-RemoteMailbox | ForEach { Get-AdUser -Identity $_.Guid | Set-ADObject -Replace @{msExchRecipientDisplayType=-1073741818}}

4.  Führen Sie den folgenden Befehl aus, um sicherzustellen, dass die Postfächer erfolgreich aktualisiert wurden:
    
        Get-RemoteMailbox | ForEach { Get-AdUser -Identity $_.Guid -Properties msExchRecipientDisplayType | Format-Table -AutoSize DistinguishedName, msExchRecipientDisplayType}

