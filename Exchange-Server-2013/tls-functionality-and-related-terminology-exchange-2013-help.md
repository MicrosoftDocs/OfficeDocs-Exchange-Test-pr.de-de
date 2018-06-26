---
title: 'TLS-Funktionalität und die zugehörige Terminologie: Exchange 2013 Help'
TOCTitle: TLS-Funktionalität und die zugehörige Terminologie
ms:assetid: 294ba2a9-892d-4a90-beec-9d298426b5f4
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb430753(v=EXCHG.150)
ms:contentKeyID: 52062848
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# TLS-Funktionalität und die zugehörige Terminologie

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2014-06-18_

Microsoft Exchange Server 2013 stellt zusätzliche Verwaltungsfunktionen und andere Verbesserungen zur Verfügung, die die Gesamtverwaltung von TLS (Transport Layer Security) optimieren. Wenn Sie mit dieser Funktionalität arbeiten, müssen Sie einiges über TLS-bezogene Funktionen und über die Funktionalität erfahren. Einige Begriffe und Konzepte beziehen sich auf mehrere TLS-spezifische Funktionen. In diesem Thema finden Sie eine kurze Erläuterung der einzelnen Funktionen, die Sie dabei unterstützen soll, einige Unterschiede sowie die allgemeine Terminologie zu verstehen, die sich auf TLS und die Funktionssammlung "Domänensicherheit" bezieht.

  - **Transport Layer Security   **TLS ist ein Standardprotokoll, das zum Bereitstellen sicherer Webkommunikationsverbindungen im Internet oder in Intranets verwendet wird. Es ermöglicht Clients das Authentifizieren von Servern oder, optional, Servern das Authentifizieren von Clients. Es stellt ferner durch Verschlüsseln der Kommunikation einen sicheren Kanal bereit. TLS ist die aktuellste Version des SSL-Protokolls (Secure Sockets Layer).

  - **Mutual TLS**   Die Mutual TLS-Authentifizierung (MTLS) unterscheidet sich in der Bereitstellung von TLS. Bei der Bereitstellung von TLS wird das Protokoll normalerweise nur dazu verwendet, Vertraulichkeit in Form von Verschlüsselung zu bieten. Zwischen dem Absender und dem Empfänger findet keine Authentifizierung statt. Darüber hinaus wird bei Bereitstellung von TLS manchmal nur der empfangende Server authentifiziert. Diese Bereitstellung von TLS ist für die HTTP-Implementierung von TLS typisch. Diese Implementierung, bei der nur der empfangende Server authentifiziert wird, ist SSL.
    
    Bei der MTLS-Authentifizierung prüft jeder Server die Identität des jeweils anderen Servers, indem er dessen Zertifikat überprüft. In diesem Szenario, in dem Nachrichten von externen Domänen über überprüfte Verbindungen in einer Exchange 2013-Umgebung eingehen, zeigt Microsoft Outlook das Symbol für eine gesicherte Domäne an.

  - **Domänensicherheit**   Domänensicherheit ist eine Funktionssammlung, die z. B. aus Zertifikatverwaltung, Connectorfunktionen und Outlook-Clientverhalten besteht. Sie ermöglicht MTLS als verwaltbare und sinnvolle Technologie. Domänensicherheit wird nicht unterstützt, wenn ausgehende E-Mail über einen Exchange 2013-Clientzugriffsserver geleitet wird.

  - **Opportunistisches TLS**   In Exchange 2013 erstellt das Setup ein selbstsigniertes Zertifikat. TLS ist standardmäßig aktiviert. Dadurch kann jedes sendende System die bei Exchange eingehende SMTP-Sitzung verschlüsseln. Standardmäßig versucht Exchange 2013, TLS auch für alle Remoteverbindungen zu verwenden.

  - **Direkte Vertrauensstellung**   Der gesamte Verkehr zwischen Edge-Transport-Servern und Postfachservern wird standardmäßig authentifiziert und verschlüsselt. Der zugrundeliegende Mechanismus für Authentifizierung und Verschlüsselung ist auch hier MTLS. Statt die X.509-Gültigkeitsprüfung zu verwenden, verwenden Exchange 2013-Benutzer direkte Vertrauensstellungen zum Authentifizieren der Zertifikate. Direkte Vertrauensstellung bedeutet, dass das Zertifikat durch sein Vorhandensein in Active Directory oder Active Directory Lightweight Directory Services (AD LDS) bestätigt wird. Active Directory wird als vertrauenswürdiger Speichermechanismus betrachtet. Wenn die direkte Vertrauensstellung verwendet wird, ist es nicht von Bedeutung, ob das Zertifikat selbstsigniert oder von einer Zertifizierungsstelle signiert ist. Wenn Sie einen Edge-Transport-Server für eine Exchange-Organisation abonnieren, veröffentlicht das Edge-Abonnement das Edge-Transport-Serverzertifikat für die Überprüfung durch die Postfachserver in Active Directory. Der Microsoft Exchange EdgeSync-Dienst aktualisiert AD LDS mit dem Satz von Postfachserverzertifikaten, damit diese vom Edge-Transport-Server überprüft werden können.

