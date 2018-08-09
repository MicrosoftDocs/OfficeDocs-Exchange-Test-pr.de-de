---
title: 'IIS 7-Komponente nicht installiert'
TOCTitle: IIS 7-Komponente nicht installiert_LonghornIIS7BasicAuthNotInstalled
ms:assetid: 2eb3290c-9ce2-4c01-ad47-a26ef60bddb5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.setupreadiness.longhorniis7basicauthnotinstalled(v=EXCHG.150)
ms:contentKeyID: 50475266
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# IIS 7-Komponente nicht installiert\_LonghornIIS7BasicAuthNotInstalled

 

_**Gilt für:** Exchange Server_

_**Letztes Änderungsdatum des Themas:** 2015-03-09_

Der Inhalt dieses Themas wurde für Microsoft Exchange Server 2013 nicht aktualisiert. Dennoch kann er für Exchange 2013 gültig sein. Weitere Hilfe finden Sie in den Community-Ressourcen weiter unten.

Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542) oder [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkid=285351).

Das Setup von Microsoft Exchange Server 2010 Setup oder Microsoft Exchange Server 2007 kann die Rolle „Clientzugriffsserver\&quot; (Client Access Server, CAS) oder die Rolle „Postfachserver\&quot; auf einem Microsoft Windows Server 2008-basierten Computer oder auf einem Windows Server 2008 R2-basierten Computer nicht installieren, da die erforderlichen Internet Information Server 7-Komponenten (IIS) nicht installiert werden.

Für das Setup von Exchange 2010 und Exchange 2007 ist es erforderlich, dass auf dem Windows Server 2008-basierten oder auf dem Windows Server 2008 R2-basierten Computer, auf dem Sie die CAS-Rolle installieren, die folgenden IIS 7-Komponenten bereits installiert sind.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Erforderliche II7-Komponenten für die CAS-Serverrolle</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Komprimierung dynamischer Inhalte</p></td>
</tr>
<tr class="even">
<td><p>Komprimierung statischer Inhalte</p></td>
</tr>
<tr class="odd">
<td><p>Standardauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Windows-Authentifizierung</p></td>
</tr>
<tr class="odd">
<td><p>IIS 7-Digestauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>ASP.NET</p></td>
</tr>
<tr class="odd">
<td><p>Clientzertifikatszuordnung</p></td>
</tr>
<tr class="even">
<td><p>Verzeichnissuche</p></td>
</tr>
<tr class="odd">
<td><p>HTTP-Fehler</p></td>
</tr>
<tr class="even">
<td><p>HTTP-Protokollierung</p></td>
</tr>
<tr class="odd">
<td><p>HTTP-Umleitung</p></td>
</tr>
<tr class="even">
<td><p>Ablaufverfolgung</p></td>
</tr>
<tr class="odd">
<td><p>ISAPI-Filter</p></td>
</tr>
<tr class="even">
<td><p>Anforderungsüberwachung</p></td>
</tr>
<tr class="odd">
<td><p>Statische Inhalte</p></td>
</tr>
</tbody>
</table>


Für das Setup von Exchange 2010 und Exchange 2007 ist es erforderlich, dass auf dem Windows Server 2008-basierten oder auf dem Windows Server 2008 R2-basierten Computer, auf dem Sie die Postfachserverrolle installieren, die folgenden IIS 7-Komponenten bereits installiert sind.


<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Erforderliche II7-Komponenten für die Postfachserverrolle</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Standardauthentifizierung</p></td>
</tr>
<tr class="even">
<td><p>Windows-Authentifizierung</p></td>
</tr>
</tbody>
</table>


Befolgen Sie zum Beheben dieses Problems die entsprechenden Schritte zum Installieren der erforderlichen IIS 7-Komponenten auf dem Zielcomputer, und führen Sie das Microsoft Exchange-Setup dann erneut aus.

Installieren der IIS 7-Komponenten für die CAS-Serverrolle mithilfe des Server-Managers von Windows Server 2008

1.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Server-Manager**.

2.  Erweitern Sie im Navigationsbereich die Option **Rollen**, und klicken Sie dann mit der rechten Maustaste auf **Webserver (IIS)**. Wählen Sie dann **Rollendienste hinzufügen** aus.

3.  Führen Sie im Bereich **Rollendienste hinzufügen** einen Bildlauf bis zum Eintrag **IIS** durch.

4.  Klicken Sie in den Bereich **Sicherheit**, um die folgenden Kontrollkästchen zu aktivieren:
    
      - **Standardauthentifizierung**
    
      - **Digestauthentifizierung**
    
      - **Windows-Authentifizierung**

5.  Klicken Sie in den Bereich **Leistung**, um die folgenden Kontrollkästchen zu aktivieren:
    
      - **Statische Komprimierung**
    
      - **Dynamische Komprimierung**

6.  Klicken Sie im Bereich **Rollendienste auswählen** auf **Weiter**, und klicken Sie dann im Bereich zur Bestätigung der Installationsauswahl auf **Installieren**.

7.  Klicken Sie auf **Schließen**, um den Assistenten für das Hinzufügen von Funktionsdiensten zu beenden.

Installieren der IIS 7-Komponenten für die Postfachserverrolle mithilfe des Server-Managers von Windows Server 2008

1.  Klicken Sie auf **Start**, klicken Sie auf **Verwaltung**, und klicken Sie dann auf **Server-Manager**.

2.  Erweitern Sie im Navigationsbereich die Option **Rollen**, und klicken Sie dann mit der rechten Maustaste auf **Webserver (IIS)**. Wählen Sie dann **Rollendienste hinzufügen** aus.

3.  Führen Sie im Bereich **Rollendienste hinzufügen** einen Bildlauf bis zum Eintrag **IIS** durch.

4.  Klicken Sie in den Bereich **Sicherheit**, um die folgenden Kontrollkästchen zu aktivieren:
    
      - **Standardauthentifizierung**
    
      - **Windows-Authentifizierung**

5.  Klicken Sie im Bereich **Rollendienste auswählen** auf **Weiter**, und klicken Sie dann im Bereich zur Bestätigung der Installationsauswahl auf **Installieren**.

6.  Klicken Sie auf **Schließen**, um den Assistenten für das Hinzufügen von Funktionsdiensten zu beenden.

