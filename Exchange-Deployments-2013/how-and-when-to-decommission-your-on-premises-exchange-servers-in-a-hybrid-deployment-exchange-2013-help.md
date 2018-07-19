---
title: 'Außerbetriebnahme und Abschaltzeitpunkt Ihrer lokalen Exchange-Server in einer Hybrid-Umgebung: Exchange 2013 Help'
TOCTitle: Außerbetriebnahme und Abschaltzeitpunkt Ihrer lokalen Exchange-Server in einer Hybrid-Umgebung
ms:assetid: 4f884b7a-3b8a-4207-8843-65d3141731dc
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn931280(v=EXCHG.150)
ms:contentKeyID: 64965197
ms.date: 03/26/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Außerbetriebnahme und Abschaltzeitpunkt Ihrer lokalen Exchange-Server in einer Hybrid-Umgebung

 

_<strong>Gilt für:</strong>Exchange Online, Exchange Server, Exchange Server 2013, Exchange Server 2016_

_<strong>Letztes Änderungsdatum des Themas:</strong>2017-07-27_

Lesen Sie diesen Artikel, wenn Sie bereit sind, von einer Exchange-Hybridbereitstellung zu einer vollständigen Cloud-Implementierung zu wechseln.

Eine der attraktiveren Optionen zum Umstellen eines Unternehmens auf Exchange Online ist die Verwendung des hybriden Bereitstellungsansatzes, der in [Exchange-Hybridbereitstellung und Migration in Office 365](https://msdn.microsoft.com/de-de/library/ff633682\(v=exchsrvcs.149\).aspx) beschrieben wird. Dies ist die einzige Option zur einfachen Nutzung von On-Board- und Off-Board-Postfächern (alle anderen systemeigenen Optionen sind nur On-Board). Zusätzlich zu der Off-Board-Option gibt es folgende wichtige Optionen:

In diesem Thema erhalten Sie Informationen zu den Optionen für die Außerbetriebnahme von Exchange und dazu, wann diese Optionen implementiert werden sollten. Es gibt viele Unterschiede zum Zeitpunkt und der Art und Weise, wie Exchange-Hybrid-Server außer Betrieb zu nehmen sind. Es ist wichtig, sich die Zeit zu nehmen und in Erfahrung zu bringen, welche Auswirkungen es gibt und wie eine vollständige oder teilweise Stilllegung von lokalen Servern geplant werden sollte.

  - **Standortübergreifende Verfügbarkeit**. Dadurch können Sie freie/gebuchte Informationen eines Benutzers beim Planen einer Besprechung anzeigen, unabhängig von ihren lokalen Postfächern.

  - **Standortübergreifendes Archiv**. Damit kann ein Kunde nur ein Archivpostfach in die Cloud verschieben. Das ist oftmals der erste Schritt für Kunden, Office 365 auszuprobieren und konkret Exchange Online.

  - **Standortübergreifende Discovery-Suchen**. Dadurch kann ein Kunde eine e-Discovery-Suche durchführen, die Postfächer und Archive an beiden Standorten durchsucht (dazu muss die OAuth-Authentifizierung konfiguriert werden).

  - **Outlook Web App URL-Umleitung**. Dadurch können Benutzer für den Outlook Web App-Zugriff an entsprechende Standorte weitergeleitet werden.

  - **Keine erneute Profilerstellung nach dem Verschieben**. Im Gegensatz zu anderen Migrationsoptionen verändert sich der Postfach-GUID nicht. Dies bedeutet, dass Sie Ihr Profil nicht erneut erstellen müssen oder die OST-Datei nach einer Postfachverschiebung erneut herunterladen müssen.

Je nach den Anforderungen Ihrer Organisation ist eine Hybrid-Bereitstellung die beste Option zum Bereitstellen der häufigsten, nahtlosen Benutzer- und Koexistenz-Oberfläche.

## Andere Methoden zum Migrieren auf Exchange Online

Eine Hybrid-Bereitstellung ist nicht für alle Benutzer geeignet, da in der Regel bessere Optionen verfügbar sind. Viele der Mandanten, die sich entschieden haben, eine Hybrid-Konfiguration mit unter 50 Plätzen bereitzustellen. Auch wenn die Liste der Vorteile einer Hybrid-Bereitstellung attraktiv klingen mag, ist sie hinslich der Komplexibilität mit erheblichem Aufwand verbunden. Einige der kleineren Mandanten benötigen die Features einer Hybrid-Bereitstellung, für die meisten Mandanten wäre es jedoch viel besser, Übernahme-, bereitgestellte oder IMAP-Migrationsoption zu verwenden. Es gibt ein Programm namens FastTrack, die Sie bei der Entscheidung über die Vorgehensweise bei der Migration einsetzen können. Informationen zu FastTrack finden Sie auf der Seite[FastTrack für Office 365](https://go.microsoft.com/fwlink/?linkid=846696).

Anhand folgender Tabelle können Sie entscheiden, welcher Migrationstyp für Ihre Organisation geeignet ist. (Weitere Informationen finden Sie unter [Methoden zum Migrieren von mehreren E-Mail-Konten zu Office 365](https://support.office.com/de-de/article/methoden-zum-migrieren-mehrerer-e-mail-konten-zu-office-365-0a4913fe-60fb-498f-9155-a86516418842?ui=de-de%26rs=de-de%26ad=de)).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Vorhandene Organisation</th>
<th>Anzahl der zu migrierenden Postfächer</th>
<th>Sollen Benutzerkonten in der lokalen Organisation verwaltet werden?</th>
<th>Migrationstyp</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exchange 2013, Exchange 2010, Exchange 2007 oder Exchange 2003</p></td>
<td><p>Weniger als 2.000 Postfächer</p></td>
<td><p>Nein</p></td>
<td><p>Exchange-Übernahmemigration</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2007 oder Exchange 2003</p></td>
<td><p>Weniger als 2.000 Postfächer</p></td>
<td><p>Nein</p></td>
<td><p>Phasenweise Exchange-Migration</p></td>
</tr>
<tr class="odd">
<td><p>Exchange 2007 oder Exchange 2003</p></td>
<td><p>Mehr als 2.000 Postfächer*</p></td>
<td><p>Ja</p></td>
<td><p>Mehrstufige Exchange-Migration oder Remoteverschiebungsmigration in einer Exchange-Hybridbereitstellung</p></td>
</tr>
<tr class="even">
<td><p>Exchange 2013 oder Exchange 2010</p></td>
<td><p>Mehr als 2.000 Postfächer*</p></td>
<td><p>Ja</p></td>
<td><p>Remoteverschiebungsmigration in einer Exchange-Hybridbereitstellung</p></td>
</tr>
<tr class="odd">
<td><p>Exchange 2000 Server oder ältere Versionen</p></td>
<td><p>Kein Maximum</p></td>
<td><p>Ja</p></td>
<td><p>IMAP-Migration</p></td>
</tr>
<tr class="even">
<td><p>Exchange-fremdes lokales Messaging-System</p></td>
<td><p>Kein Maximum</p></td>
<td><p>Ja</p></td>
<td><p>IMAP-Migration</p></td>
</tr>
</tbody>
</table>


\* Einige Organisationen mit weniger als 2.000 Postfächern profitieren möglicherweise von den Features und Funktionen, die nur bei einer Hybrid-Bereitstellung verfügbar sind. Es ist wichtig, die Vorteile einer Hybrid-Bereitstellung mit der Komplexität zu berücksichtigen, die nötig ist. Es wird dringend empfohlen, dass Kunden mit weniger als 2.000 Postfächer eine Übernahme- oder bereitgestellte Migration erwägen, bevor Sie mit einer Hybrid-Bereitstellung fortfahren.

## Warum Sie möglicheweise keine Außerbetriebnahme der Exchange-Server vornehmen möchten

Kunden mit einer Hybridkonfiguration sehen nach einem bestimmten Zeitraum, dass alle ihre Postfächer auf Exchange Online verschoben wurden. An dieser Stelle können sie entscheiden, Exchange-Server lokal zu entfernen. Dabei stellen Sie jedoch fest, dass Sie ihre Cloud-Postfächer nicht mehr verwalten können.

Wenn die Verzeichnissynchronisierung für einen Mandanten aktiviert ist, und ein Benutzer der lokalen Bereitstellung synchronisiert wird, können die meisten Attribute nicht über Exchange Online verwaltet werden und müssen lokal verwaltet werden. Das liegt nicht an der Hybridkonfiguration, sondern an der Verzeichnissynchronisierung. Selbst wenn Sie die Verzeichnissynchronisierung einsetzen ohne den Hybridkonfigurationsassistenten auszuführen, können Sie die meisten Empfängeraufgaben nicht über die Cloud verwalten. Weitere Informationen finden Sie unter diesem [TechNet-Blog](http://blogs.technet.com/b/exchange/archive/2012/12/05/decommissioning-your-exchange-2010-servers-in-a-hybrid-deployment.aspx).

## Können Verwaltungstools von Drittanbietern verwendet werden?

Es wird häufig die Frage gestellt, ob ein Verwaltungstool eines Drittanbieters oder ADSIEDIT verwendet werden kann. Die Antwort ist, Sie können Sie diese verwenden, aber sie werden nicht unterstützt. Die Exchange-Verwaltungskonsole, das Exchange Admin Center (EAC) und die Exchange-Verwaltungsshell sind die einzigen unterstützten Tools, die zum Verwalten von Exchange-Empfängern und Objekten verfügbar sind. Wenn Sie sich entscheiden, Verwaltungstools von Drittanbietern zu verwenden, geschieht das auf eigenes Risiko. Drittanbieter-Verwaltungstools funktionieren häufig, aber Microsoft überprüft diese Tools nicht.

## Häufige Szenarien

Es ist nicht einfach, von einer Hybridkonfiguration in die Cloud umzuziehen. Mit dem Verfahren zum Umziehen in eine Hybridkonfiguration haben wir eine Menge Zeit verbracht, damit es gut funktioniert. Obwohl es Probleme gibt, haben wir das Gefühl, gute Arbeit geleistet zu haben, indem wir das Unmögliche möglich gemacht haben, ein Assistenten-Verfahren für eine Hybridkonfiguration bereitzustellen.

Allerdings haben wir nur wenig Zeit darauf aufgewendet, wie Sie von einer Hybridkonfiguration in die Cloud umziehen können. Je nach Ihren unmittelbaren Zielen kann dieses Verfahren mit ein wenig Unterstützung recht einfach sein. Im folgenden Beispiel werden drei allgemeine Hybridszenarien zusammen mit unserer Empfehlung bereitgestellt, wie das Ziel des Kunden ordnungsgemäß erreicht werden kann.

Da die hybride Kundenbasis sehr vielfältig ist, ist es schwierig, alle von ihnen in "allgemeine" Szenarien einzuordnen. Wir haben versucht, unten einige allgemeine Szenarien für die lokale Exchange Server-Außerbetriebsetzung bereitzustellen, während Sie diese Szenarios durchlesen und sich einen Plan zur Außerbetriebnahme erstellt haben, müssen Sie erörtern, welches dieser Szenarien am besten für Ihre Anforderungen geeignet ist.

## Szenario eins

**Problem:**  Meine Organisation wurde in einer Hybridkonfiguration ausgeführt, und alle meine Postfächer befinden sich in Exchange Online. Ich muss meine Benutzer nicht lokal verwalten und benötige die Verzeichnissynchronisierung oder Synchronisierung von Kennwörtern nicht mehr.

**Lösung:**  Da alle Benutzer in Office 365 verwaltet werden, und es keine weiteren Anforderungen für die Verzeichnissynchronisierung gibt, können Sie die Verzeichnissynchronisierung bedenkenlos deaktivieren und Exchange aus der lokalen Umgebung entfernen.

![Entfernen von Exchange aus der lokalen Umgebung](images/Dn931280.f9c2a2cb-4c16-4ca3-8244-b89c1cdf0744(EXCHG.150).jpg "Entfernen von Exchange aus der lokalen Umgebung") **So deaktivieren Sie die Verzeichnissynchronisierung und deinstallieren Exchange-Hybrid**

1.  Führen Sie `Get-OrganizationConfig |fl PublicFoldersEnabled` aus und stellen Sie sicher, dass es nicht auf Remote festgelegt ist. Wenn es auf Remote festgelegt ist und sie weiterhin auf die öffentlichen Ordner zugreifen möchten, müssen Sie sie auf Exchange Online migrieren. Weitere Informationen finden Sie unter [Use batch migration to migrate legacy public folders to Office 365 and Exchange Online](https://technet.microsoft.com/de-de/library/dn874017\(v=exchg.150\)).

2.  Unter der Voraussetzung, dass Sie alle Postfächer bereits zu Exchange Online verschoben haben, können Sie die MX- und Autodiscover DNS-Einträge so ändern, dass Sie auf Exchange Online verweisen, statt auf lokal. Weitere Informationen finden Sie unter [Referenz: Externe DNS-Einträgen für Office 365](http://technet.microsoft.com/de-de/library/hh852557.aspx).
    

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie sowohl die internen als auch die externen DNS-Einträge aktualisieren, andernfalls gibt es möglicherweise ein inkonsistentes Client-Verbindungsverhalten.



3.  Im nächsten Schritt sollten Sie die Werte (Service Connection Point SCP) auf Ihren Exchange-Servern entfernen. Dadurch wird sichergestellt, dass keine SCPS zurückgegeben werden, und der Client verwendet stattdessen die DNS-Methode für die AutoErmittlung. Nachfolgend ein Beispiel:
    
        Get-ClientAccessServer | Set-ClientAccessServer -AutoDiscoverServiceInternalUri $Null
    

    > [!NOTE]
    > Wenn Sie Exchange 2007-Server in der Umgebung haben, müssen Sie einen ähnlichen Befehl wie auf Ihren Exchange 2007-Servern ausführen, um die Einstellungen auszuführen.



4.  Es gibt eingehende und ausgehende Connectoren, die vom Hybrid-Konfigurations-Assistenten erstellt wurden, die Sie löschen möchten. Verwenden Sie dazu die folgenden Schritte:
    
    1.  Melden Sie sich am [Office 365-Administratorportal](http://portal.office.com) als Mandantenadministrator an.
    
    2.  Wählen Sie die Option zum Verwalten von **Exchange**.
    
    3.  Navigieren Sie zu **E-Mail-Fluss** -\> **Verbindung**.
    
    4.  Sie können jetzt die eingehenden und ausgehenden Connectoren deaktivieren oder löschen. Die HCW erstellt Connectoren mit eindeutigem Namespace **eingehend von \< eindeutiger Bezeichner\>** und **ausgehend aus \<eindeutiger Bezeichner\>** siehe Grafik unten.
        
        ![Hybrid-Konfigurationsassistent erstellt Connectors mit eindeutigem Namespace](images/Dn931280.7b1b6f0b-43d6-4407-8cd7-7dd52e016697(EXCHG.150).jpg "Hybrid-Konfigurationsassistent erstellt Connectors mit eindeutigem Namespace")  

5.  Entfernen Sie die Organisationsbeziehung, die vom Hybrid-Konfigurations-Assistenten erstellt wurden. Verwenden Sie dazu die folgenden Schritte:
    
    1.  Melden Sie sich am [Office 365-Administratorportal](http://portal.office.com) als Mandantenadministrator an.
    
    2.  Wählen Sie die Option zum Verwalten von Exchange.
    
    3.  Navigieren Sie zu **Organisation**.
    
    4.  Klicken Sie unter **Organisation Freigabe**, entfernen Sie die Organisation mit dem Namen **Office 365 zur lokalen Bereitstellung – \< eindeutige ID \>** wie in der Abbildung unten dargestellt.
        
        ![Entfernen der Organisationsbeziehung, die vom Hybrid-Konfigurations-Assistenten erstellt wurde.](images/Dn931280.2f0c1077-8785-487a-87a5-a75f0a4f0fea(EXCHG.150).jpg "Entfernen der Organisationsbeziehung, die vom Hybrid-Konfigurations-Assistenten erstellt wurde.")  

6.  Wenn OAuth für eine Exchange Hybrid-Bereitstellung konfiguriert ist, möchten Sie die Konfiguration aus lokalen und Office 365 deaktivieren. In den meisten Umgebungen können diese Schritte übersprungen werden, da nur eine kleine Teilmenge unserer Kunden OAuth konfiguriert haben.
    
    So deaktivieren Sie die lokale Konfiguration:
    
    1.  Öffnen Sie auf einem Exchange 2013-Server die Exchange-Verwaltungsshell.
    
    2.  Führen Sie den folgenden Befehl aus:
        
            Get-IntraorganizationConnector -Identity ExchangeHybridOnPremisesToOnline | Set-IntraOrganizationConnector -Enabled $False
    
    So deaktivieren Sie die Exchange Online-Konfiguration:
    
    1.  Herstellen einer Verbindung zwischen Windows PowerShell und Exchange Online.
    
    2.  Führen Sie den folgenden Befehl aus:
        
            Run Get-IntraorganizationConnector -Identity ExchangeHybridOnlineToOnPremises | Set-IntraOrganizationConnector -Enabled $False
        
        Der *Identity*-Parameter geht davon aus, dass Sie zum Konfigurieren von OAuth den Hybrid-Konfigurations-Assistenten verwendet haben. Wenn dies nicht der Fall ist, müssen Sie möglicherweise den Wert anpassen, den Sie für die Identität der Connectors angegeben haben.

7.  Deaktivieren der Verzeichnissynchronisierung von Ihrem Mandanten Wenn dieser Schritt abgeschlossen ist, werden alle Verwaltungsaufgaben über die Office 365-Verwaltungstools vorgenommen. Das heißt, Sie verwenden nicht mehr die Exchange-Verwaltungskonsole oder das Exchange Admin Center (EAC). Weitere Informationen zum Deaktivieren der Verzeichnissynchronisierung finden Sie unter [Deaktivieren der Verzeichnissynchronisierung](https://technet.microsoft.com/de-de/library/dn144760.aspx).

8.  Sie können Exchange jetzt sicher von den lokalen Serern deinstallieren.

## Szenario zwei

**Problem:**  Meine Organisation wurde im letzten Jahr in einer Hybridkonfiguration ausgeführt wurde und nun wurde mein letztes Postfach in die Cloud verschoben. Ich plane weiterhin die Active Directory Federation Services (AD FS) für die Benutzerauthentifizierung von meinen Exchange Online-Postfächern zu verwenden. (Dieses Szenario gilt für alle Kunden, die die Verzeichnissynchronisierung beibehalten möchten).

**Lösung:**  Da der Kunde AD FS beibehalten möchte, muss er auch die Verzeichnissynchronisierung beibehalten, da sie dazu eine Voraussetzung ist. Aus diesem Grund können Exchange-Server nicht vollständig aus der lokalen Umgebung entfernt werden. Allerdings können sie die meisten der Exchange-Server außer Betrieb nehmen, jedoch nicht einige Servern für die Benutzerverwaltung beibehalten. Denken Sie daran, dass Sie die Server, die weiterlaufen sollen, au virtuellen Computern ausführen können, da die Arbeitsauslastung nahezu vollständig in Exchange Online verschoben wird.

Die Abbildung unten beschreibt den gewünschten Endzustand:

![Außerbetriebnahme von Exchange-Servern, wobei einige verbleiben](images/Dn931280.d7734579-6999-45b2-9a0f-a23f18353a49(EXCHG.150).jpg "Außerbetriebnahme von Exchange-Servern, wobei einige verbleiben")

Die Abbildung unten beschreibt den tatsächlichen Endzustand:

![Status für der Außerbetriebsetzung von Exchange-Servern](images/Dn931280.c692f0af-6536-4bc9-950d-58a1e486525f(EXCHG.150).jpg "Status für der Außerbetriebsetzung von Exchange-Servern") **Um die AD FS und Verzeichnissynchronisierung und Außerbetriebnahme der meisten Exchange-Server**

1.  Führen Sie `Get-OrganizationConfig |fl PublicFoldersEnabled` aus und stellen Sie sicher, dass es nicht auf Remote festgelegt ist. Wenn es auf Remote festgelegt ist und sie weiterhin auf die öffentlichen Ordner zugreifen möchten, müssen Sie sie auf Exchange Online migrieren. Weitere Informationen dazu, finden Sie unter [Use batch migration to migrate legacy public folders to Office 365 and Exchange Online](https://technet.microsoft.com/de-de/library/dn874017\(v=exchg.150\)).
    

    > [!IMPORTANT]
    > Wenn die Migration von öffentlichen Ordnern zu Exchange Online nicht möglich ist, und Sie sie weiterhin für Ihre Benutzer benötigen, sollten Sie sie nicht nach vorne verschieben.



2.  Nachdem Sie alle Postfächer auf Exchange Online verschoben haben, sollten Sie als erstes zur Außerbetriebnahme der meisten Exchange-Server die MX- und Autodiscover DNS-Einträge auf zu Exchange Online statt zu lokal verweisen lassen. Weitere Informationen finden Sie unter [Referenz: Externe DNS-Einträgen für Office 365](http://technet.microsoft.com/de-de/library/hh852557.aspx).
    

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie sowohl die internen als auch die externen DNS-Einträge aktualisieren, andernfalls gibt es möglicherweise ein inkonsistentes Client-Verbindungs- und Mailflussverhalten.



3.  Im nächsten Schritt sollten Sie die Werte (Service Connection Point SCP) auf Ihren Exchange-Servern entfernen. Dadurch wird sichergestellt, dass keine SCPS zurückgegeben werden, und der Client verwendet stattdessen die DNS-Methode für die AutoErmittlung. Nachfolgend ein Beispiel:
    
        Get-ClientAccessServer | Set-ClientAccessServer -AutoDiscoverServiceInternalUri $Null
    

    > [!NOTE]
    > Wenn Sie Exchange 2007-Server in der Umgebung haben, müssen Sie einen ähnlichen Befehl wie auf Ihren Exchange 2007-Servern ausführen, um die Einstellungen auszuführen.



4.  Um zu verhindern, dass die hybriden Konfigurationsobjekte in Zukunft neu erstellt werden, sollten Sie das hybride Konfigurationsobjekt aus der Active Directory entfernen. Öffnen Sie dazu die Exchange-Verwaltungsshell, und führen Sie Folgendes aus:
    
        Remove-HybridConfiguration

5.  Entfernen Sie alle Exchange-Server mit Ausnahme der Server, die Sie für Benutzerverwaltung und Erstellung beibehalten werden. Zwei Server sollten für die Benutzerverwaltung ausreichen, obwohl ein Server möglicherweise auch reichen sollte. Darüber hinaus ist keine Datenbankverfügbarkeitsgruppe oder andere Hochverfügbarkeitsoptionen erforderlich.

6.  Wenn OAuth für eine Exchange Hybrid-Bereitstellung konfiguriert ist, möchten Sie die Konfiguration aus lokalen und Office 365 deaktivieren. In den meisten Umgebungen können diese Schritte übersprungen werden, da nur eine kleine Teilmenge unserer Kunden OAuth konfiguriert haben.
    
    So deaktivieren Sie die lokale Konfiguration:
    
    1.  Öffnen Sie auf einem Exchange 2013-Server die Exchange-Verwaltungsshell.
    
    2.  Führen Sie den folgenden Befehl aus:
        
            Get-IntraorganizationConnector -Identity ExchangeHybridOnPremisesToOnline | Set-IntraOrganizationConnector -Enabled $False
    
    So deaktivieren Sie die Exchange Online-Konfiguration:
    
    1.  Herstellen einer Verbindung zwischen Windows PowerShell und Exchange Online.
    
    2.  Führen Sie den folgenden Befehl aus:
        
            Run Get-IntraorganizationConnector -Identity ExchangeHybridOnlineToOnPremises | Set-IntraOrganizationConnector -Enabled $False
        
        Der Identitätsparameter geht davon aus, dass Sie zum Konfigurieren von OAuth den Hybrid-Konfigurations-Assistenten verwendet haben. Wenn dies nicht der Fall ist, müssen Sie möglicherweise den Wert anpassen, den Sie für die Identität der Connectors angegeben haben.

7.  Es gibt eingehende und ausgehende Connectoren, die vom Hybrid-Konfigurations-Assistenten erstellt wurden, die Sie löschen möchten. Verwenden Sie dazu die folgenden Schritte:
    
    1.  Melden Sie sich am [Office 365-Administratorportal](http://portal.office.com) als Mandantenadministrator an.
    
    2.  Wählen Sie die Option zum Verwalten von **Exchange**.
    
    3.  Navigieren Sie zu **E-Mail-Fluss** -\> **Connectors**.
    
    4.  Sie können jetzt die eingehenden und ausgehenden Connectoren deaktivieren oder löschen. Die HCW erstellt Connectoren mit eindeutigem Namespace **eingehend von \< eindeutiger Bezeichner\>** und **ausgehend aus \<eindeutiger Bezeichner\>** siehe Grafik unten.
        
        ![Hybrid-Konfigurationsassistent erstellt Connectors mit eindeutigem Namespace](images/Dn931280.7b1b6f0b-43d6-4407-8cd7-7dd52e016697(EXCHG.150).jpg "Hybrid-Konfigurationsassistent erstellt Connectors mit eindeutigem Namespace")  

8.  Entfernen Sie die Organisationsbeziehung, die vom Hybrid-Konfigurations-Assistenten erstellt wurden. Verwenden Sie dazu die folgenden Schritte:
    
    1.  Melden Sie sich am [Office 365-Administratorportal](http://portal.office.com) als Mandantenadministrator an.
    
    2.  Wählen Sie die Option zum Verwalten von **Exchange**.
    
    3.  Navigieren Sie zu **Organisation**.
    
    4.  Klicken Sie unter **Organisation Freigabe**, entfernen Sie die Organisation mit dem Namen **Office 365 zur lokalen Bereitstellung – \< eindeutige ID \>** wie in der Abbildung unten dargestellt.
        
        ![Entfernen der Organisationsbeziehung, die vom Hybrid-Konfigurations-Assistenten erstellt wurde.](images/Dn931280.2f0c1077-8785-487a-87a5-a75f0a4f0fea(EXCHG.150).jpg "Entfernen der Organisationsbeziehung, die vom Hybrid-Konfigurations-Assistenten erstellt wurde.")  

## Szenario drei

**Problem:**  Ich möchte meine lokalen Exchange-Server entfernen, nachdem ich alle Postfächer auf Exchange Online verschoben habe. Wir stellten fest, dass sie Exchange für andere Zwecke nutzen, wie z. B. für ein SMTP-Relay für eine Anwendung oder für den Zugriff auf öffentliche Ordner. Wenn Sie lokale Exchange-Server benötigen, um die aktuellen Anforderungen Ihrer Organisation zu erfüllen, ist es u. U. nicht ratsam, die lokalen Server zu entfernen.

**Lösung:**  Es wird nicht empfohlen, Exchange und die Hybridkonfiguration zu diesem Zeitpunkt zu entfernen. Wenn Sie den Prozess beginnen würden, indem Sie AutoErmittlung-Einträge auf Exchange Online verweisen lassen, würden einige Features wie der hybride Zugriff auf öffentliche Ordner nicht mehr funktionieren. Sie könnten den MX-Eintrag so ändern, dass er auf Exchange Online Protection verweist, wenn dass nicht bereits der Fall ist. Sie können sogar einige der lokalen Exchange-Server entfernen. Allerdings sollten Sie ausreichend Funktionen beizubehalten, um die verbleibenden Hybrid-Funktionen verarbeiten zu können. Dies würde in der Regel zu einem sehr kleinen lokalen Ressourcenbedarf führen.

