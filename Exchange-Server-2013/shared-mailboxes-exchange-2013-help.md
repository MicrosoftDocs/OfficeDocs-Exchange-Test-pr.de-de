---
title: 'Freigegebene Postfächer: Exchange 2013 Help'
TOCTitle: Freigegebene Postfächer
ms:assetid: 1d71c01b-e261-408e-a633-1d1c9d00032a
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ150498(v=EXCHG.150)
ms:contentKeyID: 50475149
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Freigegebene Postfächer

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-06-04_

Informationen zum freigegebenen Exchange-Postfach in Microsoft Exchange Server 2013, Gründe für die Verwendung und das Konvertieren eines delegierten Postfachs in ein freigegebenes Exchange-Postfach.

Ein freigegebenes Postfach ist ein Postfach, das mehrere Benutzer verwenden können, um E-Mails zu lesen und zu senden. Mit freigegebenen Postfächern kann auch ein allgemeiner Kalender bereitgestellt werden, sodass mehrere Benutzer Urlaubszeiten oder Arbeitsschichten planen und anzeigen können.

Freigegebene Postfächer werden auf mobilen Geräten nicht unterstützt.

**Welche Vorteile bietet die Einrichtung eines freigegebenen Postfachs?**

  - Es stellt eine generische E-Mail-Adresse (beispielsweise "info@contoso.com" oder "sales@contoso.com") bereit, mit der Kunden Anfragen an Ihr Unternehmen richten können.

  - Es ermöglicht es Mitarbeitern in Abteilungen, die zentrale Dienste für Mitarbeiter bereitstellen (beispielsweise Helpdesk, Personalabteilung oder Druckdienste), auf Mitarbeiterfragen zu antworten.

  - Es ermöglicht es mehreren Benutzern, an eine E-Mail-Adresse gesendete E-Mails zu überwachen und sie zu beantworten (beispielsweise eine bestimmte Adresse, die vom Helpdesk verwendet wird).

## Was sind freigegebene Postfächer?

Ein freigegebenes Postfach ist eine Art Benutzerpostfach, das keinen eigenen Benutzernamen und kein Kennwort aufweist. Also können die Benutzer sich nicht direkt bei ihnen anmelden. Für den Zugriff auf ein freigegebenes Postfach muss den Benutzern erst die Berechtigung "Senden als" oder die Berechtigung "Vollzugriff" erteilt werden. Anschließend können sich die Benutzer bei ihren eigenen Postfächern anmelden und dann auf das freigegebene Postfach zugreifen, indem sie es ihrem Outlook-Profil hinzufügen. In Exchange 2003 und früheren Versionen waren freigegebene Postfächer einfach normale Postfächer, für die ein Administrator Stellvertretungszugriff erteilen konnte. Seit Exchange 2007 sind freigegebene Postfächer ein eigener Empfängertyp:

  - **RecipientType:** UserMailbox

  - **RecipientTypeDetails:** SharedMailbox

In früheren Versionen von Exchange mussten zum Erstellen eines freigegebenen Postfachs mehrere Schritte ausgeführt werden. Dabei mussten einige Aufgaben über die Exchange-Verwaltungsshell erledigt werden. In Exchange 2013 können Sie die Exchange-Verwaltungskonsole verwenden, um ein freigegebenes Postfach in einem Schritt zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines freigegebenen Postfachs](create-a-shared-mailbox-exchange-2013-help.md). Die Exchange-Verwaltungskonsole verfügt über einen eigenen Funktionsbereich für freigegebene Postfächer. Navigieren Sie einfach zu **Empfänger** \> **Freigegebene Postfächer**, um alle Verwaltungsaufgaben für freigegebene Postfächer anzuzeigen.

Sie können die folgenden Berechtigungen mit einem freigegebenen Postfach verwenden.

  - **Vollzugriff**   Die Berechtigung "Vollzugriff" ermöglicht es einem Benutzer, das freigegebene Postfach zu öffnen und als Besitzer dieses Postfachs zu agieren. Nach dem Zugriff auf das freigegebene Postfach kann der Benutzer Kalenderelemente erstellen, E-Mails lesen, anzeigen, löschen und ändern sowie Tasks und Kalenderkontakte erstellen. Ein Benutzer mit der Berechtigung "Vollzugriff" kann jedoch keine E-Mails über das freigegebene Postfach senden, außer er hat auch die Berechtigung "Senden als" oder "Senden im Auftrag von".

  - **Senden als**   Die Berechtigung "Senden als" ermöglicht es einem Benutzer, das freigegebene Postfach beim Senden von E-Mails zu imitieren. Beispiel: Kweku meldet sich beim freigegebenen Postfach der Marketing-Abteilung an und sendet eine E-Mail. Diese wird so angezeigt, als ob die Marketing-Abteilung die E-Mail gesendet hätte.

  - **Senden im Auftrag von**   Die Berechtigung "Senden im Auftrag von" ermöglicht es einem Benutzer, E-Mails im Auftrag des freigegebenen Postfachs zu senden. Beispiel: John meldet sich beim freigegebenen Postfach des Empfangs in Gebäude 32 an und sendet eine E-Mail. Dem Empfänger wird angezeigt, dass John sie im Auftrag des Empfangs in Gebäude 32 gesendet hat. Sie können die Exchange-Verwaltungskonsole nicht verwenden, um "Senden im Auftrag von" zu ermöglichen. Sie müssen das [Set-Mailbox](https://technet.microsoft.com/de-de/library/bb123981\(v=exchg.150\))-Cmdlet mit dem *GrantSendonBehalf*-Parameter verwenden.

## Konvertieren freigegebener Postfächer

In früheren Versionen von Exchange konnten Sie ein normales Postfach als Postfach mit Stellvertretungszugriff verwenden. Wenn Sie Postfächer delegiert haben, können Sie diese Postfächer mit Stellvertretungszugriff mithilfe der Shell in freigegebene Postfächer konvertieren. Weitere Informationen finden Sie unter [Konvertieren eines Postfachs](convert-a-mailbox-exchange-2013-help.md).

