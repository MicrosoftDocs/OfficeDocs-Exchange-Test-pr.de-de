---
title: 'Konfigurieren von Mobiltelefonen für den E-Mail-Zugriff: Exchange 2013 Help'
TOCTitle: Konfigurieren von Mobiltelefonen für den E-Mail-Zugriff
ms:assetid: 8d6e2cea-265a-43d9-a074-076f35658436
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123704(v=EXCHG.150)
ms:contentKeyID: 52062738
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Mobiltelefonen für den E-Mail-Zugriff

 

_**Gilt für:**Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-03-12_

Sie können ein Mobiltelefon (z. B. ein Windows Phone) für die Verwendung von Microsoft Exchange ActiveSync konfigurieren. Diese Schritte müssen Sie auf jedem Mobiltelefon in Ihrer Organisation ausführen.

## Voraussetzungen

  - Sie haben die Herstellerdokumentation für das Mobiltelefon gelesen, das Sie konfigurieren möchten.

  - Exchange ActiveSync ist in Ihrer Organisation aktiviert.


> [!NOTE]
> Gerätespezifische Informationen über das Einrichten von Microsoft Exchange-basierten E-Mails auf einem Telefon oder Tablet finden Sie unter <A href="https://support.office.com/de-de/article/set-up-a-mobile-device-using-office-365-for-business-7dabb6cb-0046-40b6-81fe-767e0b1f014f">Einrichten eines mobilen Geräts mit Office 365 Business</A>.



## Konfigurieren eines Mobiltelefons für die Verwendung von Exchange ActiveSync

Die meisten Mobiltelefone und Geräte können mithilfe der AutoErmittlung den mobilen E-Mail-Client für die Verwendung von Exchange ActiveSync konfigurieren. Für die Konfiguration eines E-Mail-Kontos benötigen Sie auf den meisten Mobiltelefonen zwei Informationen.

  - Die E-Mail-Adresse des Benutzers

  - Das Kennwort des Benutzers

Wenn das Mobiltelefon den Exchange-Server nicht automatisch über AutoErmittlung kontaktieren kann, müssen Sie das Mobiltelefon manuell einrichten. Für die manuelle Einrichtung werden die E-Mail-Adresse und das Kennwort des Benutzers sowie der Name des Exchange ActiveSync-Servers benötigt. In vielen Organisationen entspricht der Exchange ActiveSync-Servername dem Outlook Web App-Servernamen ohne "/owa". Beispiel: mail.contoso.com.

## Windows Phone-Synchronisierung

Wenn Sie ein Windows Phone-Mobiltelefon für die Synchronisierung mit einem Exchange-Postfach mithilfe von Exchange ActiveSync konfigurieren, wird nur eine Untermenge der Postfachrichtlinieneinstellungen für mobile Geräte unterstützt. Diese Richtlinieneinstellungen werden unter [Unterstützte Postfachrichtlinien für mobile Geräte für Windows-Telefone und -Geräte](supported-mobile-device-mailbox-policies-for-windows-phones-and-devices-exchange-2013-help.md) ausführlich behandelt.

Wenn Sie Postfachrichtlinieneinstellungen für mobile Geräte konfigurieren, die von Ihrer Version von Windows Phone nicht unterstützt werden, müssen Sie außerdem die Richtlinieneinstellung **AllowNonProvisionableDevices** auf "true" festlegen oder eine gesonderte Postfachrichtlinie für mobile Geräte für Windows Phone-Mobiltelefone erstellen.

