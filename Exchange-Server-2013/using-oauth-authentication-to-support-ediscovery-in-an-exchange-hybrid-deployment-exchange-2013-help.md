---
title: 'OAuth-Auth. zur Unterstützung von eDiscovery in Exchange-Hybridbereitstellung'
TOCTitle: Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung
ms:assetid: b069f8db-fbe1-4047-ad97-d00172ee6a12
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn497703(v=EXCHG.150)
ms:contentKeyID: 61292111
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwenden der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Um in einer Exchange 2013-Hybridorganisation eine erfolgreiche standortübergreifende eDiscovery-Suche durchführen zu können, müssen Sie die OAuth-Authentifizierung (Open Authorization) zwischen Ihrer lokalen Exchange-Organisation und der Exchange Online-Organisation einrichten, damit Sie Compliance-eDiscovery zum Durchsuchen der lokalen und cloudbasierten Postfächer verwenden können. Die OAuth-Authentifizierung wird in den folgenden eDiscovery-Szenarien in einer Exchange-Hybridbereitstellung unterstützt:

  - Durchsuchen lokaler Postfächer, für die die Exchange Online-Archivierung für cloudbasierte Archivpostfächer verwendet wird

  - Durchsuchen lokaler und cloudbasierter Postfächer in derselben eDiscovery-Suche

Schrittweise Anleitungen zum Konfigurieren der OAuth-Authentifizierung zur Unterstützung von eDiscovery finden Sie unter [Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen](configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help.md).

## Was ist die OAuth-Authentifizierung?

Die OAuth-Authentifizierung ist ein Server-zu-Server-Authentifizierungsprotokoll, das es Anwendungen ermöglicht, sich gegenseitig zu authentifizieren. Bei Verwendung der OAuth-Authentifizierung werden Benutzeranmeldeinformationen und Kennwörter nicht von einem Computer an einen anderen übergeben. Stattdessen basieren Authentifizierung und Autorisierung auf dem Austausch von Sicherheitstoken, die für einen bestimmten Zeitraum den Zugriff auf bestimmte Ressourcen gewähren.

An der OAuth-Authentifizierung sind normalerweise drei Parteien beteiligt: ein Server mit Einzelanmeldung und zwei Bereiche, die miteinander kommunizieren müssen. Sicherheitstoken werden vom Autorisierungsserver (auch als Sicherheitstokenserver bezeichnet) an die zwei Bereiche ausgegeben, die kommunizieren müssen. Diese Token prüfen, ob die Kommunikation des einen Bereichs für den anderen Bereich vertrauenswürdig ist. Wenn die OAuth-Authentifizierung zwischen einer lokalen Exchange-Organisation und Exchange Online verwendet wird, wird die Funktion des Autorisierungsservers von Microsoft Azure Active Directory-Zugriffssteuerungsdiensten (Access Control Services, ACS) in Ihrer Office 365-Organisation bereitgestellt. Beispielsweise stellt Azure ACS während einer standortübergreifenden eDiscovery-Suche Token aus, die überprüfen, ob ein Administrator oder Compliance Officer aus der lokalen Exchange-Organisation auf Postfächer in der Exchange Online-Organisation zugreifen kann und umgekehrt.

## eDiscovery-Szenarien in einer Hybridbereitstellung

In der folgenden Tabelle sind die eDiscovery-Szenarien in einer Exchange-Hybridbereitstellung aufgeführt, bei denen OAuth-Authentifizierung benötigt wird.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>eDiscovery-Szenario</th>
<th>Erfordert OAuth-Authentifizierung?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Durchsuchen von lokalen Exchange-Postfächern und Exchange Online-Postfächern in derselben eDiscovery-Suche, die von der lokalen Exchange-Organisation initiiert wurde. Beispielsweise das Durchsuchen sämtlicher Postfächer in der Organisation in einer einzelnen eDiscovery-Suche.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Durchsuchen lokaler Exchange-Postfächer, bei denen die Exchange Online-Archivierung für cloudbasierte Archivpostfächer verwendet wird. Wenn Sie Compliance-eDiscovery verwenden, werden sowohl primäre Postfächer als auch Archivpostfächer durchsucht.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="odd">
<td><p>Durchsuchen von Exchange Online-Postfächern in einer eDiscovery-Suche, die von einem Administrator oder Compliance Officer in der lokalen Exchange-Organisation initiiert wurde.</p></td>
<td><p>Ja</p></td>
</tr>
<tr class="even">
<td><p>Durchsuchen lokaler Postfächer in einer eDiscovery-Suche, die von einem Administrator oder Compliance Officer in der lokalen Exchange-Organisation initiiert wurde.</p></td>
<td><p>Nein</p>

> [!NOTE]
> Wie bereits erläutert, ist die OAuth-Authentifizierung erforderlich, wenn die lokalen Postfächer mit cloudbasierten Archivpostfächern konfiguriert wurden.


</td>
</tr>
<tr class="odd">
<td><p>Durchsuchen von Exchange Online-Postfächern in einer eDiscovery-Suche, die von einem Office 365-Mandantenadministrator oder einem Compliance Officer, der an einem Office 365-Benutzerkonto angemeldet ist, in Exchange Online oder dem eDiscovery Center in SharePoint Online initiiert wurde.</p></td>
<td><p>Nein</p></td>
</tr>
</tbody>
</table>


## Konfigurieren der OAuth-Authentifizierung zur Unterstützung von eDiscovery

Wie bereits zuvor erwähnt, finden Sie unter [Konfigurieren der OAuth-Authentifizierung zwischen Exchange- und Exchange Online-Organisationen](configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help.md) Anweisungen zum Konfigurieren der OAuth-Authentifizierung zur Unterstützung von eDiscovery in einer Exchange-Hybridbereitstellung.

Wenn OAuth für Ihre Exchange-Hybridbereitstellung nicht konfiguriert ist, können Sie eDiscovery nicht verwenden, um lokale Exchange-Postfächer und Exchange Online-Postfächer in derselben eDiscovery-Suche zu durchsuchen. Sie müssen lokale Postfächer in einer eDiscovery-Suche durchsuchen, die in Ihrer lokalen Organisation initiiert wurde. Ebenso können Sie Exchange Online-Postfächer nur in einer eDiscovery-Suche durchsuchen, die in Ihrer Exchange Online-Organisation initiiert wurde, oder im eDiscovery Center in SharePoint Online. Außerdem können Sie keine primären lokalen Postfächer durchsuchen, wenn sich das entsprechende Archivpostfach in Exchange Online oder in einer Exchange Online-Archivierungsorganisation befindet.

## Weitere Informationen

  - Mithilfe der OAuth-Authentifizierung kann auch anderen Anwendungen, wie beispielsweise SharePoint 2013 und Lync Server 2013 die Authentifizierung bei Exchange 2013 ermöglicht werden. Weitere Informationen finden Sie unter [Konfigurieren der OAuth-Authentifizierung mit SharePoint 2013 und Lync 2013](configure-oauth-authentication-with-sharepoint-2013-and-lync-2013-exchange-2013-help.md).

  - Sie können die Server-zu-Server-Authentifizierung zwischen Exchange 2013 und SharePoint 2013 konfigurieren, sodass Administratoren und Compliance Officer das eDiscovery Center in SharePoint 2013 zum Durchsuchen von Exchange 2013-Postfächern verwenden können. Weitere Informationen finden Sie unter [Konfigurieren von Exchange für SharePoint eDiscovery Center](configure-exchange-for-sharepoint-ediscovery-center-exchange-2013-help.md).

  - Sie können eine Exchange-Hybridbereitstellung mithilfe des Assistenten für die Hybridkonfiguration in Exchange 2013 konfigurieren. Eine benutzerdefinierte schrittweise Konfigurationsprüfliste für die Hybridbereitstellung finden Sie im [Bereitstellungs-Assistenten für Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=277105).

