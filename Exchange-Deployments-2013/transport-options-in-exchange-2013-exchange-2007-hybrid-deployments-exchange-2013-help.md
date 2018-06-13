---
title: 'Transportoptionen in Exchange 2013-/Exchange 2007-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Transportoptionen in Exchange 2013-/Exchange 2007-Hybridbereitstellungen
ms:assetid: 92d9e3ca-8d79-4872-9ff7-0067fcdbd434
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn151301(v=EXCHG.150)
ms:contentKeyID: 54651521
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportoptionen in Exchange 2013-/Exchange 2007-Hybridbereitstellungen

Dieses Thema ist in Bearbeitung.  

_**Gilt für:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

In Hybridbereitstellungen können Sie Postfächer verwenden, die sich in der lokalen Exchange-Organisation und auch in einer Exchange Online-Organisation befinden. Damit diese beiden separaten Organisationen als eine kombinierte Organisation für Benutzer und zwischen ihnen ausgetauschte Nachrichten angezeigt werden, ist der Hybridtransport unabdingbar. Der Hybridtransport ermöglicht es, dass zwischen Empfängern in den Organisationen gesendete Nachrichten mithilfe von TLS (Transport Layer Security) authentifiziert, verschlüsselt und übertragen sowie gegenüber Exchange-Komponenten wie Transportregeln, Journaling und Antispamrichtlinien als "intern" angezeigt werden. Der Hybridtransport wird vom Assistenten für die Hybridkonfiguration in Exchange 2013 automatisch konfiguriert

Damit die Hybridtransportkonfiguration mit dem Assistenten für die Hybridkonfiguration funktioniert, muss es sich bei dem lokalen SMTP-Endpunkt, der Verbindungen von Microsoft Exchange Online Protection (EOP) akzeptiert und den Transport für die Exchange Online-Organisation übernimmt, um einen Exchange 2013-Clientzugriffsserver, einen Exchange 2013-Edge-Transport-Server oder einen Exchange Server 2010-Edge-Transport-Server mit Service Pack 3 (SP3) handeln.


> [!IMPORTANT]
> Es dürfen keine weiteren SMTP-Hosts oder Dienste zwischen dem lokalen Exchange 2013-Clientzugriffsserver oder einem Exchange 2013-/Exchange 2010&nbsp;SP3-Edge-Transport-Server und EOP vorhanden sein. Nachrichten hinzugefügte Informationen, die Hybridtransportfunktionen aktivieren, werden entfernt, wenn die Nachrichten einen Nicht-Exchange 2013-Server, einen Server vor Exchange 2010 SP3 oder einen SMTP-Host durchlaufen. Wenn Sie in Ihrer Organisation Exchange 2010&nbsp;SP2-Edge-Transport-Server bereitgestellt haben und diese für den Hybridtransport verwendet werden sollen, müssen sie auf Exchange 2010&nbsp;SP3 aktualisiert werden.



Eingehende Nachrichten, die von externen Absendern im Internet an Empfänger in beiden Organisationen gesendet werden, verwenden eine allgemeine eingehende Route. Ausgehende Nachrichten, die von den Organisationen an externe Empfänger im Internet gesendet werden, können entweder eine allgemeine ausgehende Route verwenden oder über unabhängige Routen gesendet werden.

Wenn Sie die Hybridbereitstellung planen und konfigurieren, müssen Sie festlegen, wie eingehende und ausgehende Nachrichten weitergeleitet werden sollen. Die Route von eingehenden und ausgehenden Nachrichten, die an Empfänger und von Empfängern in der lokalen und der Exchange Online-Organisation gesendet werden, hängt von folgenden Bedingungen ab:

  - Möchten Sie, dass eingehende Internet-E-Mails sowohl für lokale als auch für Exchange Online-Postfächer über Microsoft Office 365 und EOP oder Ihre lokale Organisation weitergeleitet werden?
    
    Sie können auswählen, ob eingehende Internet-E-Mails für beide Organisationen über die lokale Organisation oder über EOP und die Exchange Online-Organisation weitergeleitet werden. Eingehende Nachrichten für beide Organisationen werden abhängig davon, ob der zentrale E-Mail-Transport in der Hybridbereitstellung aktiviert ist, weitergeleitet.

  - Sollen ausgehende Nachrichten von Ihrer Exchange Online-Organisation an externe Empfänger über Ihre lokale Organisation (zentraler E-Mail-Transport) weitergeleitet werden, oder sollen sie direkt an das Internet weitergeleitet werden?
    
    Beim zentralen E-Mail-Transport können Sie alle E-Mails von Postfächern in der Exchange Online-Organisation über die lokale Organisation weiterleiten, bevor sie an das Internet zugestellt werden. Diese Methode ist hilfreich in Richtlinientreueszenarien, in denen alle Nachrichten an das und vom Internet von lokalen Servern verarbeitet werden müssen. Alternativ können Sie Exchange Online so konfigurieren, dass Nachrichten von externen Empfängern direkt an das Internet zugestellt werden.
    

    > [!NOTE]
    > Der zentrale E-Mail-Transport wird nur für Organisationen empfohlen, die aufgrund der Richtlinientreue spezielle Transportanforderungen haben. Für typische Exchange-Organisationen empfiehlt es sich, den zentralen E-Mail-Transport nicht zu aktivieren.



  - Möchten Sie in Ihrer lokalen Organisation einen Edge-Transport-Server bereitstellen?
    
    Wenn die der Domäne beigetretenen internen Exchange 2013-Server nicht direkt für das Internet zugänglich sein soll, können Sie im Umkreisnetzwerk Exchange 2013-Edge-Transport-Server oder Exchange 2010 SP3-Edge-Transport-Server bereitstellen. Weitere Informationen zum Hinzufügen eines Edge-Transport-Servers zu Ihrer Hybridbereitstellung finden Sie unter [Edge-Transport-Server in Exchange 2013/Exchange 2007-Hybrid-Bereitstellungen](edge-transport-servers-in-exchange-2013-exchange-2007-hybrid-deployments-exchange-2013-help.md).

Unabhängig davon, wie Sie Nachrichten an das und vom Internet weiterleiten möchten, wird für alle Nachrichten, die zwischen der lokalen und der Exchange Online-Organisation gesendet werden, der sichere Transport verwendet. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt [Trusted communication](transport-options-in-exchange-hybrid-deployments-exchange-2013-help.md).

Weitere Informationen dazu, wie diese Optionen das Nachrichtenrouting in Ihrer Organisation beeinflussen, finden Sie unter [Transportweiterleitung in Exchange 2013-/Exchange 2007-Hybridbereitstellungen](transport-routing-in-exchange-2013-exchange-2007-hybrid-deployments-exchange-2013-help.md).

## Exchange Online Protection in Hybridbereitstellungen

EOP ist ein von Microsoft bereitgestellter Onlinedienst, der von vielen Unternehmen zum Schutz ihrer lokalen Organisationen vor Viren, Spam, betrügerischen Phishing-Versuchen und Richtlinienverletzungen verwendet wird. In Office 365 wird EOP zum Schutz von Exchange Online-Organisationen vor eben diesen Bedrohungen verwendet. Wenn Sie sich für Office 365 registrieren, wird automatisch ein EOP-Unternehmen erstellt, das an Ihre Exchange Online-Organisation gebunden ist.

Ein EOP-Unternehmen enthält viele der E-Mail-Transporteinstellungen, die für Ihre Exchange Online-Organisation konfiguriert werden können. Sie können u. a. angeben, welche SMTP-Domänen von bestimmten IP-Adressen stammen müssen, ein TLS- und ein SSL-Zertifikat (Secure Sockets Layer) benötigen und Kompatibilitätsrichtlinien umgehen können. EOP fungiert quasi als Eingangstür zu Ihrer Exchange Online-Organisation. Alle Nachrichten, egal, woher sie stammen, müssen EOP durchlaufen, bevor sie die Postfächer in Ihrer Exchange Online-Organisation erreichen. Ebenso müssen alle Nachrichten, die von Ihrer Exchange Online-Organisation gesendet werden, EOP durchlaufen, bevor sie das Internet erreichen.

Wenn Sie eine Hybridbereitstellung mithilfe des Assistenten für die Hybridkonfiguration konfigurieren, werden alle Transporteinstellungen automatisch in Ihrer lokalen Organisation und im EOP-Unternehmen konfiguriert, das in Ihrer Exchange Online-Organisation enthalten ist. Der Assistent für die Hybridkonfiguration konfiguriert alle eingehenden und ausgehenden Connectors sowie andere Einstellungen in diesem EOP-Unternehmen, um zwischen der lokalen und der Exchange Online-Organisation gesendete Nachrichten zu sichern und Nachrichten an das richtige Ziel weiterzuleiten. Wenn Sie benutzerdefinierte Transporteinstellungen für Ihre Exchange Online-Organisation konfigurieren möchten, konfigurieren Sie diese auch in diesem EOP-Unternehmen.

## Vertrauenswürdige Kommunikation

Zum Schutz der Empfänger in der lokalen und der Exchange Online-Organisation und um sicherzustellen, dass zwischen diesen Organisationen gesendete Nachrichten nicht abgefangen und gelesen werden, wird TLS für den Transport zwischen der lokalen Organisation und EOP erzwungen. Der TLS-Transport verwendet SSL-Zertifikate (Secure Sockets Layer), die von einer vertrauenswürdigen externen Zertifizierungsstelle stammen. Für Nachrichten zwischen EOP und der Exchange Online-Organisation wird auch TLS verwendet.

Wenn der erzwungene TLS-Transport verwendet wird, prüfen der sendende und der empfangende Server das Zertifikat, das auf dem jeweils anderen Server konfiguriert ist. Der Antragstellername oder einer der alternativen Antragstellernamen, die für die Zertifikate konfiguriert sind, muss mit dem FQDN übereinstimmen, den ein Administrator explizit auf dem jeweils anderen Server angegeben hat. Wenn EOP beispielsweise so konfiguriert ist, dass Nachrichten akzeptiert und geschützt werden, die über den FQDN "mail.contoso.com" gesendet wurden, muss der sendende lokale Clientzugriffs- oder Edge-Transport-Server über ein SSL-Zertifikat mit "mail.contoso.com" im Feld für den Antragstellernamen oder den alternativen Antragstellernamen verfügen. Ist diese Voraussetzung nicht erfüllt, wird die Verbindung von EOP abgelehnt.


> [!NOTE]
> Der verwendete FQDN muss nicht mit dem E-Mail-Domänennamen der Empfänger übereinstimmen. Die einzige Bedingung ist, dass der FQDN im Antragstellernamen oder in einem alternativen Antragstellernamen mit dem FQDN übereinstimmt, den der empfangende oder sendende Server entsprechend der Konfiguration akzeptiert.



Zusätzlich zur Verwendung von TLS werden Nachrichten zwischen den Organisationen als "intern" behandelt Durch diese Vorgehensweise können Nachrichten Antispameinstellungen und andere Dienste umgehen.

Weitere Informationen zu SSL-Zertifikaten und der Domänensicherheit finden Sie unter [Zertifikatanforderungen für Hybridbereitstellungen](certificate-requirements-for-hybrid-deployments-exchange-2013-help.md) und [Grundlegendes zu TLS-Zertifikaten](http://go.microsoft.com/fwlink/p/?linkid=187237).

