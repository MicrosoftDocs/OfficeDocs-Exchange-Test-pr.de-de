---
title: 'Organisationsbeziehungen: Exchange 2013 Help'
TOCTitle: Organisationsbeziehungen
ms:assetid: 4c48db61-3370-462b-a3f8-2a6311c6e4ee
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ657445(v=EXCHG.150)
ms:contentKeyID: 50475639
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Organisationsbeziehungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-02-20_

Richten Sie eine Organisationsbeziehung ein, um Kalenderinformationen für externe Geschäftspartner freizugeben. Exchange-Administratoren können eine Organisationsbeziehung mit einer Office 365-Organisation oder mit einer anderen lokalen Exchange-Organisation einrichten. Wenn Sie Kalender für eine andere lokale Exchange-Organisation freigeben möchten, müssen die Administratoren der beiden lokalen Exchange-Organisationen eine Authentifizierungsbeziehung mit der Cloud (auch "Verbund" genannt) einrichten und die Mindestsoftwareanforderungen erfüllen.

Eine Organisationsbeziehung ist eine 1:1-Beziehung zwischen Unternehmen, die es den Benutzern in beiden Organisationen ermöglichen soll, die Verfügbarkeitsinformationen im Kalender anzuzeigen. Beim Einrichten einer Organisationsbeziehung konfigurieren Sie Ihre Seite der Beziehung, und legen Sie fest, welche Art von Informationen die Benutzer der externen Organisation anzeigen können. Die externe Organisation kann dieselben oder andere Einstellungen auf ihrer Seite konfigurieren. Wenn beispielsweise Contoso eine Organisationsbeziehung mit Tailspin Toys erstellt, können die Benutzer bei Tailspin Toys Besprechungen mit den Benutzern bei Contoso planen, indem sie ihre E-Mail-Adressen der Besprechungseinladung hinzufügen. Die Verfügbarkeit der eingeladenen Contoso-Benutzer wird dann für die Tailspin Toys-Benutzer angezeigt. Allerdings können die Benutzer bei Contoso die Verfügbarkeit der Benutzer bei Tailspin Toys erst sehen, nachdem deren Administrator eine Organisationsbeziehung mit Contoso eingerichtet hat.

Sie können drei Zugriffsebenen festlegen:

  - Kein Zugriff

  - Zugriff auf Frei/Gebucht-Kalenderinformationen nur mit Zeit

  - Frei/Gebucht-Zugriff mit Zeit plus Betreff und Ort


> [!NOTE]
> Wenn Benutzer die eigenen Frei/Gebucht-Informationen nicht für andere Benutzer freigeben möchten, können sie in Outlook den Berechtigungseintrag "Standard" ändern. Dazu müssen sie zur Registerkarte <STRONG>Kalendereigenschaften</STRONG> &gt; <STRONG>Berechtigungen</STRONG> wechseln, die Berechtigung <STRONG>Standard</STRONG> auswählen und dann in der Liste <STRONG>Berechtigungsstufe</STRONG> die Option <STRONG>Keine</STRONG> auswählen. Selbst wenn eine Organisationsbeziehung besteht, sind die entsprechenden Frei/Gebucht-Informationen dann weder für interne noch für externe Benutzer sichtbar. Die vom Benutzer festgelegten Berechtigungen gelten.



In den folgenden Themen finden Sie Informationen zum Konfigurieren und Verwalten von Organisationsbeziehungen als Bestandteil der Freigabe für Ihre Organisation:

[Erstellen einer Organisationsbeziehung](create-an-organization-relationship-exchange-2013-help.md)

[Ändern einer Organisationsbeziehung](modify-an-organization-relationship-exchange-2013-help.md)

[Entfernen einer Organisationsbeziehung](remove-an-organization-relationship-exchange-2013-help.md)

Benötigen Sie weitere Informationen zur Verbundfreigabe? Weitere Informationen finden Sie unter [Freigabe](sharing-exchange-2013-help.md).

