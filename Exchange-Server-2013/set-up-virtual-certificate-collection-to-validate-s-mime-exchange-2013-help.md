---
title: 'Einricht. virt. Zert.auflistung für Überpr. von S/MIME: Exchange 2013-Hilfe'
TOCTitle: Einrichten einer virtuellen Zertifikatauflistung für die Überprüfung von S/MIME
ms:assetid: 04a616e6-197c-490c-ae8c-c8d5f0f0b3dd
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn626155(v=EXCHG.150)
ms:contentKeyID: 61212664
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Einrichten einer virtuellen Zertifikatauflistung für die Überprüfung von S/MIME

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-12-09_

Als Mandantenadministrator müssen Sie eine virtuelle Zertifikatauflistung konfigurieren, die zur Überprüfung von S/MIME-Zertifikaten verwendet wird. Die virtuelle Zertifikatauflistung wird als Datei vom Typ Zertifikatspeicher mit der Dateinamenerweiterung SST eingerichtet. Die SST-Datei enthält alle Stamm- und Zwischenzertifikate, die bei der Überprüfung eines S/MIME-Zertifikats verwendet werden.

## Erstellen und Speichern einer SST-Datei

Die Shell kann nur für diesen Vorgang verwendet werden.Wie eine Exchange-Verwaltungsshell in Ihrer lokalen Exchange-Organisation geöffnet wird, erfahren Sie unter [Öffnen der Shell](https://technet.microsoft.com/de-de/library/dd638134\(v=exchg.150\)).Wie Sie mit Windows PowerShell eine Verbindung mit Exchange Online herstellen, können Sie unter [Herstellen einer Verbindung mit Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554) nachlesen.

Als Administrator können Sie diese SST-Datei erstellen, indem Sie die Zertifikate mit dem Cmdlet `Export-Certificate` von einem vertrauenswürdigen Computer exportieren und den Typ als SST angeben. Weitere Informationen zum Cmdlet `Export-Certificate` finden Sie im Referenzthema zu [Export-Certificate](https://technet.microsoft.com/de-de/library/hh848628.aspx).

Nachdem die SST-Datei generiert wurde, speichern Sie sie mit dem Cmdlet `Set-Smimeconfig` mit dem Parameter *-SMIMECertificateIssuingCA* im virtuellen Zertifikatspeicher. Beispiel: `Set-SmimeConfig -SMIMECertificateIssuingCA (Get-Content filename.sst -Encoding Byte)`

## Sicherstellen der Gültigkeit eines Zertifikats

Zunächst sucht Exchange 2013 SP1 nach der SST-Datei und überprüft das Zertifikat. Liefert die Überprüfung einen Fehler, wird im Zertifikatspeicher des lokalen Computers gesucht, um das Zertifikat zu überprüfen. Dieses Verhalten ist neu in Exchange 2013 SP1 und unterscheidet sich von früheren Versionen von Exchange. In Exchange Online wird nur die SST-Datei zur Überprüfung verwendet.

## Weitere Informationen

[S/MIME für die Nachrichtensignierung und -verschlüsselung](s-mime-for-message-signing-and-encryption-exchange-2013-help.md)

[Get-SmimeConfig](https://technet.microsoft.com/de-de/library/dn554257\(v=exchg.150\))

