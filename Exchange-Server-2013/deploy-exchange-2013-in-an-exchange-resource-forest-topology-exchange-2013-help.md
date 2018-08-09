---
title: 'Bereitstellen v. Exchange 2013 in Exchange-Ressourcengesamtstruktur-Topologie'
TOCTitle: Bereitstellen von Exchange 5.113,02 cm einer Exchange-Ressourcengesamtstruktur-Topologie
ms:assetid: 537a7b2b-d002-40a6-84ae-fd02635f9e23
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998031(v=EXCHG.150)
ms:contentKeyID: 51409303
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Bereitstellen von Exchange 5.113,02 cm einer Exchange-Ressourcengesamtstruktur-Topologie

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

In diesem Thema wird erläutert, wie Microsoft Exchange 2013 in einer Exchange-Ressourcengesamtstruktur-Topologie bereitgestellt wird. Eine Exchange-Ressourcengesamtstruktur wird auch als dedizierte Exchange-Gesamtstruktur bezeichnet. In diesem Thema wird davon ausgegangen, dass Sie nicht über eine vorhandene Exchange 2013-Topologie verfügen.

Die folgende Abbildung zeigt eine Exchange-Organisation mit einer Ressourcengesamtstruktur.

**Beispiel für eine Exchange-Organisation mit einer Exchange-Ressourcengesamtstruktur**

![Komplexe Exchange-Organisation mit Ressourcengesamtstruktur](images/Aa998031.706725cf-e520-4b89-a275-acd8fb58943a(EXCHG.150).gif "Komplexe Exchange-Organisation mit Ressourcengesamtstruktur")

## Was sollten Sie wissen, bevor Sie beginnen?

Es müssen die folgenden Voraussetzungen erfüllt sein, um das nachstehende Verfahren in Exchange 2013 auszuführen:

  - Sie verfügen über die folgenden zwei Active Directory-Gesamtstrukturen:
    
      - Eine Gesamtstruktur enthält die Benutzerkonten für Ihre Organisation. In diesem Verfahren wird diese Gesamtstruktur als *Kontengesamtstruktur* bezeichnet.
    
      - Eine Gesamtstruktur enthält keine Benutzerkonten, und in ihr ist Exchange noch nicht installiert. In diesem Verfahren wird diese Gesamtstruktur als *Exchange-Gesamtstruktur* bezeichnet. Sie verwenden das Verfahren zum Installieren von Exchange 2013 in dieser Gesamtstruktur.

  - Sie haben DNS (Domain Name System) für die gesamtstrukturübergreifende Namensauflösung in Ihrer Organisation ordnungsgemäß konfiguriert. Führen Sie einen Verbindungstest mithilfe von Ping für jede Gesamtstruktur von der/den anderen Gesamtstruktur(en) in Ihrer Organisation durch, um zu prüfen, ob DNS ordnungsgemäß konfiguriert ist. Weitere Informationen zum Konfigurieren von DNS finden Sie im [DNS-Server-Betriebshandbuch](https://go.microsoft.com/fwlink/p/?linkid=282295).

## Bereitstellen von Exchange 5.113,02 cm einer Exchange-Ressourcengesamtstruktur-Topologie

1.  Erstellen Sie auf einem Domänencontroller in der Exchange-Gesamtstruktur eine unidirektionale ausgehende Vertrauensstellung, damit die Exchange-Gesamtstruktur der Kontengesamtstruktur vertraut. Ausführliche Anleitungen finden Sie unter [Erstellen einer unidirektionalen, ausgehenden Gesamtstruktur-Vertrauensstellung für beide Seiten der Vertrauensstellung](https://go.microsoft.com/fwlink/p/?linkid=69130).
    

    > [!NOTE]
    > Zwar wird empfohlen, eine Gesamtstruktur-Vertrauensstellung zu erstellen, Sie können jedoch entweder eine Gesamtstruktur-Vertrauensstellung oder eine externe Vertrauensstellung erstellen. Wenn Sie beim Erstellen verknüpfter Postfächer in Schritt&nbsp;3 eine externe Vertrauensstellung erstellen, müssen Sie auf der Seite <STRONG>Hauptkonto</STRONG> des Assistenten für neue Postfächer ein Benutzerkonto angeben, das auf den Domänencontroller in der vertrauenswürdigen Gesamtstruktur zugreifen kann. Sie können nicht die Anmeldeinformationen verwenden, mit denen Sie zurzeit angemeldet sind. Wenn Sie verknüpfte Postfächer mithilfe des Cmdlets <STRONG>New-Mailbox</STRONG> erstellen, müssen Sie ein Benutzerkonto angeben, das auf den Domänencontroller in der vertrauenswürdigen Gesamtstruktur mithilfe des Parameters <EM>LinkedCredential</EM> zugreifen kann.



2.  Installieren Sie Exchange in der Exchange 2013-Gesamtstruktur. Installieren Sie Exchange auf dieselbe Weise wie in einem Szenario mit einer einzelnen Gesamtstruktur. Genaue Anweisungen zum Installieren von Exchange 2013 finden Sie unter einem der folgenden Themen:
    
      - [Bereitstellen einer Neuinstallation von Exchange 2013](deploy-a-new-installation-of-exchange-2013-exchange-2013-help.md)
    
      - [Installieren von Exchange 2013 mithilfe des Setup-Assistenten](install-exchange-2013-using-the-setup-wizard-exchange-2013-help.md)

3.  Erstellen Sie in der Exchange-Gesamtstruktur für jedes Benutzerkonto in der Kontengesamtstruktur, das in der Exchange-Gesamtstruktur ein Postfach aufweisen soll, ein Postfach, das einem externen Konto zugeordnet ist. Ausführliche Anleitungen finden Sie unter [Verwalten verknüpfter Postfächer](manage-linked-mailboxes-exchange-2013-help.md).

