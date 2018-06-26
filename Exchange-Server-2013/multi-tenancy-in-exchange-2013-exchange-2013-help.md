---
title: 'Mandantenfähigkeit in Exchange 2013: Exchange 2013 Help'
TOCTitle: Mandantenfähigkeit in Exchange 2013
ms:assetid: df09257d-dd98-4f59-b830-1818cedda15c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ862352(v=EXCHG.150)
ms:contentKeyID: 50554927
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Mandantenfähigkeit in Exchange 2013

 

_**Gilt für:**Exchange Online, Exchange Server, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-12-09_

Eine mehrmandantenfähige (gehostete) Exchange 2013-Bereitstellung ist als eine Bereitstellung definiert, bei der die Exchange-Organisation für das Hosten mehrerer, voneinander unabhängiger Organisationen oder Geschäftsbereiche (Mandanten) konfiguriert wurde, die in der Regel weder E-Mails, Daten, Benutzer, globale Adresslisten (GALs) noch andere häufig verwendete Exchange-Objekte gemeinsam nutzen. Diese gemeinsame Nutzung von Hardware, Software und Ressourcen (bei gleichzeitiger logischer Trennung der Mandanten) ermöglicht Organisationen die Ausnutzung der Einfachheit einer Exchange-Standardbereitstellung und zugleich die Bereitstellung von Funktionalität und Dienste für mehrere Mandanten zum Erfüllen ihrer Hostinganforderungen.

## Mandantenfähigkeit in Exchange 2013-Organisationen

In Exchange 2013 unterstützen wir weiter das Hosten mittels einer standardmäßigen lokalen Exchange-Installation ähnlich dem Ansatz in Exchange 2010 Service Pack 2 (SP2). Wir haben die Modusoption `/hosting` entfernt und empfehlen die Nutzung von Adressbuchrichtlinien in Kombination mit Hostingmanagementlösungen und Automatisierungstools, die von genehmigten unabhängigen Softwareanbietern (ISVs) angeboten werden. Diese Lösungen basieren auf einem Rahmenwerk aus von Microsoft genehmigten Konfigurationsrichtlinien und -methoden und bieten Exchange-Organisationen eine einfachere, zuverlässigere Möglichkeit, Services und Funktionen zu hosten.

Exchange 2013 unterstützt Mandantenfähigkeit, indem Sie die folgenden primären Komponenten und Funktionen genutzt werden:

  - **Active Directory**   Anstatt getrennte *ExchangeOrganization*-Active Directory-Container für jeden Geschäftsbereich in einer Exchange-Organisation mit mehreren Mandanten zu verwenden, wird die Mandantenfähigkeit von Exchange 2013 mithilfe eines einzelnen *ExchangeOrganization*-Active Directory-Containers unterstützt. Dies ermöglicht eine einfachere Active Directory-Struktur und verringert die Wahrscheinlichkeit von sich Active Directory beziehender Berechtigungsprobleme.
    
    Weitere Informationen zu Active Directory-Änderungen in Exchange 2013 finden Sie unter [Active Directory](active-directory-exchange-2013-help.md).

  - **Adressbuchrichtlinien**   Die in Exchange 2010 SP2 eingeführten Adressbuchrichtlinien in Exchange 2013 dienen zum Steuern des Benutzerzugriffs auf eine Adressenliste, die globale Adressenliste und Offlineadressbücher in der Exchange-Organisation. Mithilfe von Adressbuchrichtlinien werden diese verschiedenen Active Directory-Objekte in einem einzelnen, virtuellen Objekt gruppiert, das einzelnen Benutzern zugewiesen werden kann, und sie dienen zum Erstellen einer logischen Gruppierung dieser Ressourcen in einer Organisationsstruktur für mehrere Mandanten. Die Funktionalität von Adressbuchrichtlinien in Exchange 2013 ähnelt der in Exchange 2010 SP2.
    
    Weitere Informationen zu Adressbuchrichtlinien in Exchange 2013 finden Sie unter [Adressbuchrichtlinien](address-book-policies-exchange-2013-help.md).

  - **Managementlösungen für das Hosting**   Einige Administratoren, die Exchange 2013 zum Bereitstellen einer gehosteten Exchange-Lösung verwenden, profitieren vom Befolgen eines angepassten Managementansatzes für das Hosting. Aufgrund verschiedener Einschränkungen der Exchange-Verwaltungskonsole arbeitet Microsoft mit anderen Anbietern zusammen, um diese bei der Entwicklung von Systemsteuerungs- und Automatisierungslösungen zu unterstützen, die im Einklang mit den Richtlinien und dem genehmigten Rahmenwerk für gehostete Exchange 2013-Organisationen sind. Organisationen, die eine gehostete Exchange-Lösung konfigurieren, wird zum Verwalten ihrer gehosteten Organisationen der Einsatz dieser Tools entsprechend den jeweiligen Umständen empfohlen.
    
    Weitere Informationen zu gehosteten Managementlösungen und zugelassenen Lösungsanbietern finden Sie unter [Lösungen und Hilfestellung zu Exchange Server 2013-Hosting und -Mehrinstanzenfähigkeit](https://go.microsoft.com/fwlink/?linkid=275036)

