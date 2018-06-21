---
title: 'Transportoptionen in Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Transportoptionen in Exchange-Hybridbereitstellungen
ms:assetid: da605a78-5429-4de8-8b04-bc4c45a41ba1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ659055(v=EXCHG.150)
ms:contentKeyID: 50477193
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Transportoptionen in Exchange-Hybridbereitstellungen

 

_<strong>Gilt für:</strong>Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2016-12-09_

In Hybridbereitstellungen können Sie Postfächer verwenden, die sich in der lokalen Exchange-Organisation und auch in einer Exchange Online-Organisation befinden. Damit diese beiden separaten Organisationen als eine kombinierte Organisation für Benutzer und zwischen ihnen ausgetauschte Nachrichten angezeigt werden, ist der Hybridtransport unabdingbar. Der Hybridtransport ermöglicht es, dass zwischen Empfängern in den Organisationen gesendete Nachrichten mithilfe von TLS (Transport Layer Security) authentifiziert, verschlüsselt und übertragen werden. Diese Nachrichten werden gegenüber Exchange-Komponenten wie Transportregeln, Journaling und Antispamrichtlinien als „intern“ angezeigt werden. Der Hybridtransport wird vom Assistenten für die Hybridkonfiguration automatisch konfiguriert

Damit die Hybridtransportkonfiguration mit dem Assistenten für die Hybridkonfiguration funktioniert, muss es sich bei dem lokalen SMTP-Endpunkt, der Verbindungen von Exchange Online akzeptiert, um einen Postfachserver (Exchange 2016 und neuer), Clientzugriffsserver (Exchange 2013), Hub-Transport-Server (Exchange 2010 und älter) oder um einen Edge-Transport-Server (Exchange 2010 und neuer) handeln.


> [!IMPORTANT]
> Platzieren Sie keine Server, Dienste oder Geräte, die SMTP-Datenverkehr verarbeiten oder ändern, zwischen Ihren lokalen Exchange-Servern und Office 365. Das Sichern der E-Mail-Übertragung zwischen Ihrer lokalen Exchange-Organisation und Office 365 hängt von Informationen ab, die in Nachrichten, die innerhalb der Organisation gesendet werden, enthalten sind. Firewalls, die SMTP-Datenverkehr über TCP-Port 25 ohne Änderung zulassen, werden unterstützt. Wenn ein Server, Dienst oder Gerät eine Nachricht verarbeitet, die zwischen der lokalen Exchange-Organisation und Office 365 gesendet wird, werden diese Informationen entfernt. Wenn dies der Fall ist, wird die Nachricht nicht mehr als organisationsintern eingestuft und unterliegt Antispamfiltern, Transport- und Journalregeln sowie andere Richtlinien, die möglicherweise nicht für die Nachricht gelten.



Eingehende Nachrichten, die von externen Absendern im Internet an Empfänger in beiden Organisationen gesendet werden, verwenden eine allgemeine eingehende Route. Ausgehende Nachrichten, die von den Organisationen an externe Empfänger im Internet gesendet werden, können entweder eine allgemeine ausgehende Route verwenden oder über unabhängige Routen gesendet werden.

Wenn Sie die Hybridbereitstellung planen und konfigurieren, müssen Sie festlegen, wie eingehende und ausgehende Nachrichten weitergeleitet werden sollen. Die Route von eingehenden und ausgehenden Nachrichten, die an Empfänger und von Empfängern in der lokalen und der Exchange Online-Organisation gesendet werden, hängt von folgenden Bedingungen ab:

  - Möchten Sie, dass eingehende Internet-E-Mails sowohl für lokale als auch für Exchange Online-Postfächer über Exchange Online oder Ihre lokale Organisation weitergeleitet werden?
    
    Wohin eingehende Nachrichten für beide Organisationen weitergeleitet werden, hängt von verschiedenen Faktoren ab, u. a. davon, wo sich die Mehrheit Ihrer Postfächer befindet, ob Sie Ihre lokale Organisation mithilfe von Antimalware- und Antispamfiltern von Office 365 schützen möchten und ob Ihre Kompatibilitätsinfrastruktur konfiguriert ist.

  - Sollen ausgehende Nachrichten von Ihrer Exchange Online-Organisation an externe Empfänger über Ihre lokale Organisation (zentraler E-Mail-Transport) weitergeleitet werden, oder sollen sie direkt an das Internet weitergeleitet werden?
    
    Beim zentralen E-Mail-Transport können Sie alle E-Mails von Postfächern in der Exchange Online-Organisation über die lokale Organisation weiterleiten, bevor sie an das Internet zugestellt werden. Diese Methode ist hilfreich in Richtlinientreueszenarien, in denen alle Nachrichten an das und vom Internet von lokalen Servern verarbeitet werden müssen. Alternativ können Sie Exchange Online so konfigurieren, dass Nachrichten von externen Empfängern direkt an das Internet zugestellt werden.
    

    > [!NOTE]
    > Der zentrale E-Mail-Transport wird nur für Organisationen empfohlen, die aufgrund der Richtlinientreue spezielle Transportanforderungen haben. Für typische Exchange-Organisationen empfiehlt es sich, den zentralen E-Mail-Transport nicht aktivieren, da so möglicherweise die Menge der von Ihren lokalen Servern verarbeiteten Nachrichten erheblich erhöht, die verwendete Bandbreite erhöht und eine nicht benötigte Abhängigkeit auf Ihren lokalen Servern erstellt wird.



  - Möchten Sie in Ihrer lokalen Organisation einen Edge-Transport-Server bereitstellen?
    
    Wenn die der Domäne beigetretenen internen Exchange-Server nicht direkt für das Internet zugänglich sein sollen, können Sie im Umkreisnetzwerk Edge-Transport-Server bereitstellen. Weitere Informationen zum Hinzufügen eines Edge-Transport-Servers zu Ihrer Hybridbereitstellung finden Sie unter [Edge-Transport-Server in Hybridbereitstellungen](edge-transport-servers-with-hybrid-deployments-exchange-2013-help.md).

Unabhängig davon, wie Sie Nachrichten an das und vom Internet weiterleiten möchten, wird für alle Nachrichten, die zwischen der lokalen und der Exchange Online-Organisation gesendet werden, der sichere Transport verwendet. Weitere Informationen finden Sie weiter unten in diesem Thema im Abschnitt Vertrauenswürdige Kommunikation.

Weitere Informationen dazu, wie diese Optionen das Nachrichtenrouting in Ihrer Organisation beeinflussen, finden Sie unter [Transportweiterleitung in Exchange-Hybrid-Bereitstellungen](transport-routing-in-exchange-hybrid-deployments-exchange-2013-help.md).

## Exchange Online Protection in Hybridbereitstellungen

EOP ist ein von Microsoft bereitgestellter Onlinedienst, der von vielen Unternehmen zum Schutz ihrer lokalen Organisationen vor Viren, Spam, betrügerischen Phishing-Versuchen und Richtlinienverletzungen verwendet wird. In Office 365 wird EOP zum Schutz von Exchange Online-Organisationen vor eben diesen Bedrohungen verwendet. Wenn Sie sich für Office 365 registrieren, wird automatisch ein EOP-Unternehmen erstellt, das an Ihre Exchange Online-Organisation gebunden ist.

Ein EOP-Unternehmen enthält viele der E-Mail-Transporteinstellungen, die für Ihre Exchange Online-Organisation konfiguriert werden können. Sie können u. a. angeben, welche SMTP-Domänen von bestimmten IP-Adressen stammen müssen, ein TLS- und ein SSL-Zertifikat (Secure Sockets Layer) benötigen und Antispamfilterung oder Kompatibilitätsrichtlinien umgehen können. EOP fungiert quasi als Eingangstür zu Ihrer Exchange Online-Organisation. Alle Nachrichten, egal, woher sie stammen, müssen EOP durchlaufen, bevor sie die Postfächer in Ihrer Exchange Online-Organisation erreichen. Ebenso müssen alle Nachrichten, die von Ihrer Exchange Online-Organisation gesendet werden, EOP durchlaufen, bevor sie das Internet erreichen.

Wenn Sie eine Hybridbereitstellung mithilfe des Assistenten für die Hybridkonfiguration konfigurieren, werden alle Transporteinstellungen automatisch in Ihrer lokalen Organisation und im EOP-Unternehmen konfiguriert, das in Ihrer Exchange Online-Organisation enthalten ist. Der Assistent für die Hybridkonfiguration konfiguriert alle eingehenden und ausgehenden Connectors sowie andere Einstellungen in diesem EOP-Unternehmen, um zwischen der lokalen und der Exchange Online-Organisation gesendete Nachrichten zu sichern und Nachrichten an das richtige Ziel weiterzuleiten. Wenn Sie benutzerdefinierte Transporteinstellungen für Ihre Exchange Online-Organisation konfigurieren möchten, konfigurieren Sie diese auch in diesem EOP-Unternehmen.

## Vertrauenswürdige Kommunikation

Zum Schutz der Empfänger in der lokalen und der Exchange Online-Organisation und um sicherzustellen, dass zwischen diesen Organisationen gesendete Nachrichten nicht abgefangen und gelesen werden, wird TLS für den Transport zwischen der lokalen Organisation und EOP erzwungen. Der Sichere E-Mail-Transport verwendet TLS-/SSL-Zertifikate, die von einer vertrauenswürdigen externen Zertifizierungsstelle stammen. Für Nachrichten zwischen EOP und der Exchange Online-Organisation wird auch TLS verwendet.

Wenn der erzwungene TLS-Transport verwendet wird, prüfen der sendende und der empfangende Server das Zertifikat, das auf dem jeweils anderen Server konfiguriert ist. Der Antragstellername oder einer der alternativen Antragstellernamen, die für die Zertifikate konfiguriert sind, muss mit dem FQDN übereinstimmen, den ein Administrator explizit auf dem jeweils anderen Server angegeben hat. Wenn EOP beispielsweise so konfiguriert ist, dass Nachrichten akzeptiert und geschützt werden, die über den FQDN "mail.contoso.com" gesendet wurden, muss der sendende lokale Clientzugriffs- oder Edge-Transport-Server über ein SSL-Zertifikat mit "mail.contoso.com" im Feld für den Antragstellernamen oder den alternativen Antragstellernamen verfügen. Ist diese Voraussetzung nicht erfüllt, wird die Verbindung von EOP abgelehnt.


> [!NOTE]
> Der verwendete FQDN muss nicht mit dem E-Mail-Domänennamen der Empfänger übereinstimmen. Die einzige Bedingung ist, dass der FQDN im Antragstellernamen oder in einem alternativen Antragstellernamen mit dem FQDN übereinstimmt, den der empfangende oder sendende Server entsprechend der Konfiguration akzeptiert.



Zusätzlich zur Verwendung von TLS werden Nachrichten zwischen den Organisationen als "intern" behandelt Durch diese Vorgehensweise können Nachrichten Antispameinstellungen und andere Dienste umgehen.

Weitere Informationen zu SSL-Zertifikaten und der Domänensicherheit finden Sie unter [Zertifikatanforderungen für Hybridbereitstellungen](certificate-requirements-for-hybrid-deployments-exchange-2013-help.md) und [Grundlegendes zu TLS-Zertifikaten](http://go.microsoft.com/fwlink/p/?linkid=187237).

