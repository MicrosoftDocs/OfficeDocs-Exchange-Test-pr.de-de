---
title: 'Exchange 2013-Benutzeroberfläche zur Zertifikatsverwaltung: Exchange 2013 Help'
TOCTitle: Exchange 2013-Benutzeroberfläche zur Zertifikatsverwaltung
ms:assetid: 8975848d-07f0-4643-9eac-20aece69945f
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ984582(v=EXCHG.150)
ms:contentKeyID: 52062874
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Exchange 2013-Benutzeroberfläche zur Zertifikatsverwaltung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-04-21_

Die Verwaltung von Zertifikaten in einer Exchange Server-Bereitstellung ist eine der wichtigsten Verwaltungsaufgaben. Die Sicherstellung, dass Zertifikate ordnungsgemäß eingerichtet und konfiguriert sind, ist der Schlüssel zu einer sicheren Messaginginfrastruktur für das Unternehmen. In Exchange 2010 war die Exchange-Verwaltungskonsole das Hauptinstrument zum Verwalten von Zertifikaten. In Exchange 2013 erfolgt die Zertifikatverwaltung über die Exchange-Verwaltungskonsole, die neue Exchange 2013-Benutzeroberfläche für die Verwaltung. In Exchange 2013 liegt der Fokus auf der Minimierung der Anzahl von Zertifikaten, die ein Administrator verwalten muss, und der Interaktion des Administrators mit Zertifikaten sowie dem Ermöglichen einer zentralen Zertifikatverwaltung.

## Zertifikate für Clientzugriffsserver

Der Clientzugriffsserver in Exchange 2013 ist ein zustandsloser Thin-Server mit dem Zweck, eingehende Clientverbindungen zu akzeptieren und als Proxy an den ordnungsgemäßen Postfachserver weiterzuleiten. Die Exchange-Benutzeroberfläche für die Zertifikatverwaltung auf dem Clientzugriffsserver dient zum Ausführen einer Vielzahl von Aufgaben, einschließlich Anfordern neuer Zertifikate und Verlängern abgelaufener oder bald ablaufender Zertifikate.

## Grundlegendes zur Benutzeroberfläche für die Zertifikatverwaltung

Sie können in der Exchange-Verwaltungskonsole durch Auswählen von **Server** \> **Zertifikate** auf die Benutzeroberfläche für die Zertifikatverwaltung zugreifen. Auf dieser Verwaltungsoberfläche können Sie die folgenden Aufgaben ausführen:

  - **Erstellen eines neuen Zertifikats**   Durch Klicken auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)") wird der Assistent für neue Exchange-Zertifikate gestartet.

  - **Bearbeiten eines vorhandenen Zertifikats**   Durch Klicken auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol") bei einem gültigen Zertifikat wird die Eigenschaftsseite des Zertifikats angezeigt.

  - **Löschen eines Zertifikats**   Durch Klicken auf **Löschen**![Löschen (Symbol)](images/JJ657511.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Löschen (Symbol)"), wenn ein Zertifikat ausgewählt ist, wird das Dialogfeld zum Bestätigen des Löschens angezeigt.

  - **Ausführen weiterer Aktionen**   Durch Klicken auf **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") können Sie ein Zertifikat ex- oder importieren. Wenn Sie ein Zertifikat exportieren möchten, muss es gültig sein.

## Zertifikatablauf

In früheren Microsoft Exchange-Versionen war es schwierig zu erkennen, wann sich ein digitales Zertifikat dem Ablauf näherte. In Exchange 2013 zeigt das Benachrichtigungscenter Warnungen an, wenn ein auf einem Server mit Exchange 2013 gespeichertes Zertifikat vor dem Ablauf steht.

## Zertifikate für Postfachserver

Ein wesentlicher Unterschied zwischen Exchange 2010 und Exchange 2013 besteht darin, dass die Zertifikate, die auf dem Exchange 2013-Postfachserver verwendet werden, selbstsignierte Zertifikate sind. Da sich alle Clients über einen Exchange 2013-Clientzugriffsserver mit einem Exchange 2013-Postfachserver verbinden, müssen Sie lediglich die Zertifikate auf den Clientzugriffsservern verwalten. Der Clientzugriffsserver vertraut dem selbstsignierten Zertifikat auf dem Postfachserver automatisch, weshalb Clients keine Warnungen zu einem selbstsignierten Zertifikat erhalten, dem nicht vertraut wird. Voraussetzung ist allerdings, dass der Clientzugriffsserver über ein nicht selbstsigniertes Zertifikat von entweder einer Windows-Zertifizierungsstelle oder einem vertrauenswürdigen Drittanbieter verfügt. Es stehen keine Tools oder Cmdlets zur Verfügung, um selbstsignierte Zertifikate auf dem Postfachserver zu verwalten. Nach der ordnungsgemäßen Installation des Servers müssen Sie sich um die Zertifikate auf dem Postfachserver keine Gedanken mehr machen.

## Ablauf selbstsignierter Zertifikate

Standardmäßig läuft das selbstsignierte Zertifikat, das auf dem Exchange 2013-Postfachserver installiert ist, fünf Jahre nach dem Datum der Installation ab.

## Zertifikat-Cmdlets

Mit den folgenden Cmdlets können Sie die digitalen Zertifikate auf einem Exchange-Clientzugriffsserver verwalten:

  - Import-ExchangeCertificate   Dieses Cmdlet dient zum Importieren von Zertifikaten auf einen Server. Sie können ein von einer Zertifizierungsstelle signiertes Zertifikat (zum Erfüllen einer ausstehenden Zertifikatsignieranforderung) oder ein Zertifikat mit einem privaten Schlüssel importieren (PCS \#12-Dateien, zumeist mit der Erweiterung PFX, die zuvor von einem Server zusammen mit dem privaten Schlüssel exportiert wurden).

  - Remove-ExchangeCertificate   Dieses Cmdlet dient zum Entfernen von Zertifikaten von einem Server.

  - Enable-ExchangeCertificate   Dieses Cmdlet dient zum Zuweisen von Diensten zu einem Zertifikat.

  - Get-ExchangeCertificate   Dieses Cmdlet dient zum Abrufen eines Exchange-Zertifikats basierend auf verschiedenen Kriterien.

  - New-ExchangeCertificate   Dieses Cmdlet dient zum Erstellen eines neuen selbstsignierten Zertifikats oder einer Zertifikatsignieranforderung.

