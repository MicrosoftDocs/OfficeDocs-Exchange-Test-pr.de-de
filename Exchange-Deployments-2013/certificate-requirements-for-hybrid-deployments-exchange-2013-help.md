---
title: 'Zertifikatanforderungen für Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Zertifikatanforderungen für Hybridbereitstellungen
ms:assetid: 48d532cc-29f9-4009-9d2d-f19a9c13c320
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Hh563848(v=EXCHG.150)
ms:contentKeyID: 50477181
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zertifikatanforderungen für Hybridbereitstellungen

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In einer Hybridbereitstellung sind digitale Zertifikate ein wichtiger Bestandteil zur Gewährleistung einer sicheren Kommunikation zwischen der lokalen Exchange-Organisation und Office 365. Zertifikate machen es möglich, dass eine Exchange-Organisation der Identität einer anderen Organisation vertrauen kann. Zertifikate können auch sicherstellen, dass jede Exchange-Organisation mit der richtigen Quelle kommuniziert.

In einer Hybridbereitstellung werden Zertifikate von vielen Diensten verwendet:

  - **Azure Active Directory Connect (Azure AD Connect) mit Active Directory-Verbunddiensten (Active Directory Federation Services, AD FS)**   Wenn Sie Azure AD Connect mit AD FS als Bestandteil der Hybridbereitstellung einrichten, wird zum Einrichten einer Vertrauensstellung zwischen Webclients und Verbundserverproxys ein von einer vertrauenswürdigen externen Zertifizierungsstelle ausgegebenes Zertifikat verwendet, mit dem Sicherheitstokens signiert und entschlüsselt werden.
    
    Weitere Informationen finden Sie unter [Zertifikate](http://go.microsoft.com/fwlink/p/?linkid=205993).

  - **Exchange-Partnerverbund**   Ein selbstsigniertes Zertifikat, das zum Erstellen einer sicheren Verbindung zwischen den lokalen Exchange-Servern und dem Azure Active Directory-Authentifizierungssystem verwendet wird.
    
    Weitere Informationen finden Sie unter [Freigabe](https://technet.microsoft.com/de-de/library/dd638083\(v=exchg.150\)).

  - **Exchange-Dienste**   Von einer vertrauenswürdigen Zertifizierungsstelle eines Drittanbieters ausgegebene Zertifikate zum Herstellen einer sicheren SSL-Verbindung (Secure Sockets Layer) zwischen den Exchange-Servern und -Clients. Zu den Diensten, die Zertifikate verwenden, gehören Outlook im Web, Exchange ActiveSync, Outlook Anywhere und die sichere Nachrichtenübermittlung.

  - **Vorhandene Exchange-Server**   Ihre vorhandenen Exchange-Server verwenden möglicherweise Zertifikate, um die Sicherheit der Outlook im Web-Kommunikation, der Nachrichtenübermittlung usw. zu verbessern. In Abhängigkeit von der Art und Weise, wie Sie Zertifikate auf Ihren Exchange-Servern nutzen, werden wahrscheinlich selbstsignierte oder von einer vertrauenswürdigen Zertifizierungsstelle eines Drittanbieters ausgegebene Zertifikate verwendet.

## Zertifikatanforderungen für eine Hybridbereitstellung

Bei der Konfiguration einer Hybridbereitstellung müssen Sie Zertifikate verwenden und konfigurieren, die Sie von einer vertrauenswürdigen externen Zertifizierungsstelle erworben haben. Das für die sichere Hybrid-Nachrichtenübermittlung verwendete Zertifikat muss auf allen lokalen Postfach- (Exchange 2016 und neuer) und Postfach- und Clientzugriffsservern (Exchange 2013 und früher) installiert werden.


> [!IMPORTANT]
> Wenn Sie eine Hybridbereitstellung in einer Organisation konfigurieren, die Exchange-Server in mehreren Active Directory-Gesamtstrukturen bereitgestellt hat, müssen Sie ein separates Zertifizierungsstellenzertifikat eines Drittanbieters für <EM>jede</EM> Active Directory-Gesamtstruktur verwenden.




> [!NOTE]
> Wenn Exchange-Edge-Transport-Server in einer lokalen Organisationen bereitgestellt sind, muss dieses Zertifikat auch auf allen Edge-Transport-Servern installiert werden. Jeder Transportserver muss für eine ordnungsgemäße Funktion ein Zertifikat verwenden, das dieselbe ausgebende Zertifizierungsstelle und denselben Antragsteller für sichere Hybrid-E-Mails nutzt.



Mehrere Dienste wie AD FS, Exchange-Partnerverbund, -Dienste und Exchange selbst erfordern Zertifikate. In Abhängigkeit von Ihrer Organisation sollten Sie sich für eine der folgenden Lösungen entscheiden:

  - Verwenden eines Drittanbieterzertifikats, das serverübergreifend von allen Diensten genutzt wird.

  - Verwenden eines Drittanbieterzertifikats für jeden Server, der Dienste bereitstellt.

Die Entscheidung, ob das gleiche Zertifikat für alle Dienste verwendet oder jedem Dienst ein eigenes Zertifikat zugewiesen werden soll, hängt von Ihrer Organisation und dem zu implementierenden Dienst ab. Nachstehend einige Punkte, die bei den einzelnen Möglichkeiten zu berücksichtigen sind:

  - **Serverübergreifend verwendetes Drittanbieterzertifikat**   Drittanbieterzertifikate, die serverübergreifend von den Diensten verwendet werden, sind wahrscheinlich etwas preiswerter, jedoch schwieriger zu erneuern und zu ersetzen. Das liegt daran, weil Sie das Zertifikat zum Zeitpunkt der Erneuerung auf jedem Server, auf dem es installiert ist, ersetzen müssen.

  - **Drittanbieterzertifikat für jeden Server**   Wenn Sie für jeden Server, auf dem Dienste verwaltet werden, ein dediziertes Zertifikat verwenden, können Sie das Zertifikat speziell für die Dienste auf diesem Server konfigurieren. Wenn das Zertifikat erneuert oder ersetzt werden muss, braucht es nur auf dem Server, auf dem die Dienste installiert sind, ersetzt zu werden. Andere Server sind nicht betroffen.

Es wird empfohlen, für jeden optionalen AD FS-Server ein dediziertes Drittanbieterzertifikat, ein weiteres Zertifikat für die Exchange-Dienste für Ihre Hybridbereitstellung und bei Bedarf ein weiteres Zertifikat für Ihre Exchange-Server für andere benötigte Dienste und Features zu verwenden. Für die lokale Verbundvertrauensstellung, die im Rahmen der Verbundfreigabe in einer Hybridbereitstellung konfiguriert ist, wird standardmäßig ein selbstsigniertes Zertifikat verwendet. Sofern keine besonderen Anforderungen gelten, ist für die im Rahmen der Hybridbereitstellung konfigurierte Verbundvertrauensstellung kein Zertifikat eines Drittanbieters erforderlich.

Voraussetzung für die auf einem einzelnen Server installierten Dienste ist die Konfiguration mehrerer vollqualifizierter Domänennamen (Fully Qualified Domain Names, FQDNs) für den Server. Erwerben Sie ein Zertifikat, das die maximal erforderliche Anzahl von FQDNs zulässt. Zertifikate bestehen aus dem Antragstellernamen (auch Prinzipalname genannt) und einem oder mehreren alternativen Antragstellernamen (Subject Alternative Names, SANs). Der Antragstellername ist der FQDN, auf den das Zertifikat ausgestellt wurde, und er verwendet die primäre SMTP-Domäne, die von der lokalen und der Exchange Online-Organisationen gemeinsam genutzt wird. Alternative Antragstellernamen sind die FQDNs, die dem Zertifikat neben dem Antragstellernamen hinzugefügt werden können. Wenn Sie ein Zertifikat für die Unterstützung von fünf FQDNs benötigen, sollten Sie ein Zertifikat erwerben, dem fünf Domänen hinzugefügt werden können: ein Antragstellername und vier alternative Antragstellernamen.

In der folgenden Tabelle wird die minimale vorgeschlagene Anzahl an FQDNs beschrieben, die in Zertifikaten enthalten sein soll, die für die Verwendung in einer Hybridbereitstellung konfiguriert werden.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Dienst</th>
<th>Vorgeschlagener FQDN</th>
<th>Feld</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Primäre gemeinsam genutzte SMTP-Domäne</p></td>
<td><p>contoso.com</p></td>
<td><p>Antragstellername</p></td>
</tr>
<tr class="even">
<td><p>AutoErmittlung</p></td>
<td><p>Bezeichnung, die dem externen FQDN für die AutoErmittlung Ihres vorhandenen Exchange 2013-Clientzugriffsservers entspricht, z. B. &quot;autodiscover.contoso.com&quot;</p></td>
<td><p>Alternativer Antragstellername</p></td>
</tr>
<tr class="odd">
<td><p>Transport</p></td>
<td><p>Bezeichnung, die dem externen FQDN Ihrer Edge-Transport-Server entspricht, z. B. &quot;edge.contoso.com&quot;</p></td>
<td><p>Alternativer Antragstellername</p></td>
</tr>
</tbody>
</table>

