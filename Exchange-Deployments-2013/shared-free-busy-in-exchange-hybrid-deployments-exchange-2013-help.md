---
title: 'Freigegebene Frei/Gebucht-Informationen in Exchange-Hybridbereitstellungen: Exchange 2013 Help'
TOCTitle: Freigegebene Frei/Gebucht-Informationen in Exchange-Hybridbereitstellungen
ms:assetid: bd3884de-80ee-4ff2-a8a3-eacd5aa3e51b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ650274(v=EXCHG.150)
ms:contentKeyID: 50477191
ms.date: 01/01/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Freigegebene Frei/Gebucht-Informationen in Exchange-Hybridbereitstellungen

 

_**Gilt für:**Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2016-04-29_

Die Freigabe von Frei/Gebucht-Informationen (Kalenderverfügbarkeitsinformationen) durch lokale Benutzer und Benutzer in der Exchange Online-Organisation ist einer der wesentlichen Vorteile einer Hybridbereitstellung. Benutzer in beiden Organisationen können gegenseitig die Kalender anzeigen, als befänden sie sich in derselben physikalischen Organisation. Dies ermöglicht eine einfache und effiziente Planung von Sitzungen und Ressourcen.

In einer Hybridbereitstellung sind mehrere Komponenten erforderlich, um die Funktion für gemeinsam genutzte von Frei-/Gebucht-Informationen zwischen Ihren lokalen Exchange- und Exchange Online-Organisation zu aktivieren.

  - **Verbundvertrauensstellung**   Sowohl für die lokalen als auch für die Office 365-Dienstorganisationen muss eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem eingerichtet sein. Eine Verbundvertrauensstellung ist eine 1:1-Beziehung mit dem Azure AD-Authentifizierungssystem, mit dem die Parameter für die Exchange-Organisation definiert werden. Das System verwendet diese Parameter, wenn es beim Austausch von Frei/Gebucht-Informationen zwischen Ihrer lokalen Organisation und der Office 365-Dienstorganisation als Vertrauensbroker zwischen den Benutzern der lokalen und der Exchange Online-Organisation fungiert.
    
    Bei der Erstellung des Kontos wird für Ihre Office 365-Dienstorganisation automatisch eine Verbundvertrauensstellung mit dem System konfiguriert. Der Assistent für die Hybridkonfiguration überprüft automatisch, ob für die lokale Organisation eine vorhandene Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem vorliegt. Wenn ja, wird die vorhandene Verbundvertrauensstellung zur Unterstützung der Hybridbereitstellung verwendet. Wenn nicht, erstellt der Assistent für die lokale Organisation eine Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem. Der Assistent fügt der Verbundvertrauensstellung für die lokale Organisation außerdem alle im Assistenten für die Hybridkonfiguration ausgewählten Domänen hinzu.
    
    Weitere Informationen finden Sie unter [Freigabe](https://technet.microsoft.com/de-de/library/dd638083\(v=exchg.150\)).

  - **Organisationsbeziehungen**   Organisationsbeziehungen werden sowohl für die lokale als auch für die Exchange Online-Organisation benötigt und automatisch durch den Assistenten für die Hybridkonfiguration konfiguriert. Mit einer Organisationsbeziehung wird definiert, welche Ebene von Frei/Gebucht-Informationen für eine Organisation freigegeben wird.
    
    Die Frei/Gebucht-Datenzugriffsebene lautet sowohl für lokale als auch für Exchange Online-Organisationsbeziehungen standardmäßig **Frei/Gebucht-Zugriff mit Zeit plus Betreff und Ort**. Wenn Sie die Frei/Gebucht-Datenzugriffsebene zwischen Ihren lokalen und Exchange Online-Organisationsbenutzern ändern möchten, können Sie die Zugriffsebene für die Organisationsbeziehung nach der Ausführung des Assistenten für die Hybridkonfiguration manuell konfigurieren.
    
    Weitere Informationen finden Sie unter [Freigabe](https://technet.microsoft.com/de-de/library/dd638083\(v=exchg.150\)).

Bei der Konfiguration Ihrer Organisation für eine Hybridbereitstellung wird über den Assistenten für die Hybridkonfiguration für alle Szenarien automatisch ein gemeinsamer Zugriff auf den Frei/Gebucht-Kalender konfiguriert. Die Erstellung einer Verbundvertrauensstellung mit dem Azure AD-Authentifizierungssystem sowie das Konfigurieren von Organisationsbeziehungen für die lokale und die Exchange Online-Organisation sind Voraussetzungen für eine Hybridbereitstellung. Wenn Sie die gemeinsame Nutzung von Frei/Gebucht-Informationen durch lokale und Exchange Online-Organisationsbenutzer in der Hybridbereitstellung nicht zulassen möchten, können Sie die gemeinsame Verwendung von Frei/Gebucht-Informationen nach Ausführung des Assistenten für die Hybridkonfiguration manuell deaktivieren. Verwenden Sie hierzu die Exchange-Verwaltungsshell und das Cmdlet [Set-HybridConfiguration](https://technet.microsoft.com/de-de/library/hh529932\(v=exchg.150\)).

Die in der folgenden Tabelle gezeigten Funktionen einer Hybridbereitstellung weisen eine Abhängigkeit von Verbundvertrauensstellungen und Organisationsbeziehungen auf.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Nachrichtenbereich</th>
<th>Funktion</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>E-Mail-Client</p></td>
<td><ul>
<li><p>Nachrichtenverfolgung</p></li>
<li><p>E-Mail-Infos</p></li>
<li><p>Suche in mehreren Postfächern</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Richtlinientreue</p></td>
<td><ul>
<li><p>Exchange Online-Archivierung</p></li>
<li><p>Exchange Compliance-eDiscovery</p></li>
</ul></td>
</tr>
</tbody>
</table>

