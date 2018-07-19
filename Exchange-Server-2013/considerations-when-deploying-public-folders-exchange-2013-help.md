---
title: 'Hinweise für das Bereitstellen von öffentlichen Ordnern: Exchange 2013 Help'
TOCTitle: Hinweise für das Bereitstellen von öffentlichen Ordnern
ms:assetid: 2e416eed-b88f-45db-a482-1232fd2610fa
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn957481(v=EXCHG.150)
ms:contentKeyID: 64965213
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Hinweise für das Bereitstellen von öffentlichen Ordnern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2016-07-12_

Obwohl öffentliche Ordner in Exchange 2013 zahlreiche Vorteile haben, müssen vor ihrer Implementierung in Ihrer Organisation verschiedene Aspekte beachtet werden.

## Bereitstellungshinweise für öffentliche Ordner

Dieser Artikel enthält Faktoren, die Sie beachten sollten, bevor Sie öffentliche Ordner in Ihrer Organisation bereitstellen, und zwar insbesondere bei der Planung einer großen Anzahl an öffentlichen Ordnern. Exchange 2013 unterstützt nun bis zu einer Million öffentlicher Ordner.

  - Die Aktivität in einem öffentlichen Ordner wirkt sich direkt auf die Auslastung des Postfachs des öffentlichen Ordners aus, in dem sich der Ordner befindet. Um Clientverbindungsprobleme zu vermeiden, wie zum Beispiel hohe Latenz oder der fehlende Zugriff auf einen öffentlichen Ordner, sollten Sie folgendermaßen vorgehen:
    
      - Sorgen Sie dafür, dass Postfächer öffentlicher Ordner 50 % des Postfachgrößenlimits nicht überschreiten. Falls dies geschieht, verwenden Sie das `Split-PublicFolderMailbox.ps1`-Skript unter "C:\\Program Files\\Microsoft\\Exchange Server\\V15\\Scripts" auf dem Exchange 2013-Server um einige öffentliche Ordner in ein neues Postfach für öffentliche Ordner zu verschieben.
    
      - Sie können häufig verwendete öffentliche Ordner auch in ein dediziertes Postfach für öffentliche Ordner verschieben.
    
      - Schließen Sie häufig verwendete öffentliche Ordner aus der Hierarchie für öffentliche Ordner aus. Legen Sie dazu die *IsExcludedFromServingHierarchy*-Eigenschaft des Postfachs für öffentliche Ordner mithilfe des **Set-Mailbox**-Cmdlets fest.
    
      - Für große Organisationen mit vielen öffentlichen Ordnern können Sie zusätzliche Postfächer für öffentliche Ordner hinzufügen, um die Last der Verarbeitung von Hierarchieanforderungen an den öffentlichen Ordner zu verteilen.

  - Platzieren Sie das primäre Postfach für öffentliche Ordner in einer DAG, um die Verfügbarkeit des Postfachs zu verbessern. Das primäre Postfach für öffentliche Ordner ist die autorisierende Kopie der Hierarchie für öffentliche Ordner.

  - Platzieren Sie sekundäre Postfächer für öffentliche Ordner in einer DAG, oder sichern Sie die Postfächer häufig.

  - Platzieren Sie Postfächer für öffentliche Ordner an dem geografischen Standort, der den Benutzern, die auf die Inhalte des öffentlichen Ordner zugreifen, am nächsten ist.

  - Verbessern Sie die Zugriffszeiten auf die Hierarchie für öffentliche Ordner mithilfe der "DefaultPublicFolderMailbox"-Eigenschaft in den Postfächern der Benutzer, um ein Postfach für öffentliche Ordner in ihrer Nähe anzugeben. Dadurch wird verhindert, dass Benutzer die Hierarchie für öffentliche Ordner aus einem Postfach für öffentliche Ordner an einem anderen geografischen Standort abrufen.

  - In Bereitstellungen mit mehr als 50 sekundären Postfächern für öffentliche Ordner sollten Sie die Inhalte der öffentlichen Ordner nicht im primären Postfach für öffentliche Ordner speichern. Dadurch muss das primäre Postfach für öffentliche Ordner die Hierarchie mit den sekundären Postfächern für öffentliche Ordner synchronisieren.

  - Exchange 2013 unterstützt öffentliche Ordnerdatenbanken nicht mehr. Aus diesem Grund können Benutzer von Outlook Web App mit Exchange 2013-Postfächern nicht auf öffentliche Ordner von Exchange 2010 oder Exchange 2007 zugreifen. Exchange 2013-Benutzer können mit Outlook oder Outlook für Mac auf öffentliche Ordner von Exchange 2010 oder Exchange 2007 zugreifen.

  - Outlook Web App wird unterstützt, aber mit Einschränkungen. Sie können öffentliche Ordner als Favoriten hinzufügen und entfernen und Vorgänge auf Elementebene durchführen, wie das Erstellen, Bearbeiten, Löschen und Beantworten von Beiträgen. Sie können jedoch öffentliche Ordner nicht über Outlook Web App erstellen oder löschen. Außerdem können nur öffentliche E-Mail-, Post-, Kalender oder Kontaktordner zur Favoritenliste in Outlook Web App hinzugefügt werden.

  - Zwar steht eine Volltextsuche im Inhalt eines öffentlichen Ordners zur Verfügung; Inhalte sind jedoch nicht über öffentliche Ordner hinweg durchsuchbar und werden nicht von der Exchange-Suche indiziert.

  - Für den Zugriff auf öffentliche Ordner auf Servern mit Exchange 2013 müssen Sie Outlook 2007 oder höher verwenden.

  - Aufbewahrungsrichtlinien werden für Postfächer für öffentliche Ordner nicht unterstützt.

