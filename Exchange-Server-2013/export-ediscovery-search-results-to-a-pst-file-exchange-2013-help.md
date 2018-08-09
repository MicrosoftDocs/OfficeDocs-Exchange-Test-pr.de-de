---
title: 'Exportieren v. eDiscovery-Suchergebnissen in PST-Datei: Exchange 2013-Hilfe'
TOCTitle: Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei
ms:assetid: bc47f5f9-d056-4b69-b669-ae65fad541c8
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn440164(v=EXCHG.150)
ms:contentKeyID: 59634154
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Exportieren von eDiscovery-Suchergebnissen in eine PST-Datei

 

_**Gilt für:** Exchange Online, Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-09-07_

Sie können das eDiscovery-Export-Tool in der Exchange-Verwaltungskonsole (EAC) So exportieren Sie die Ergebnisse einer Compliance-eDiscovery-Suche in eine Outlook-Datendatei, die auch eine PST-Datei bezeichnet wird. Administratoren können die Ergebnisse der Suche für andere Personen innerhalb Ihrer Organisation, wie Leiter der Personalabteilung oder Datensatzverwalter, oder entgegengesetzte einholen in rechtlichen Fall verteilen. Nachdem die Suchergebnisse in eine PST-Datei exportiert werden, können Sie oder andere Benutzer öffnen sie in Outlook zu überprüfen oder Drucken von Nachrichten, die in den Suchergebnissen zurückgegeben. PST-Dateien können auch in der Drittanbieter-eDiscovery und reporting-Applikationen geöffnet werden. In diesem Thema zeigt, wie Sie dies als auch eine beliebige möglicherweise Probleme zu beheben.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Die benötigte Zeit ist je nach Anzahl und Größe der exportierten Suchergebnisse unterschiedlich.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter „In-Situ-eDiscovery\&quot; im Thema [Berechtigungen für Messagingrichtlinien und -kompatibilität](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Der Computer, den Sie verwenden, um die Suchergebnisse in eine PST-Datei exportieren muss die folgenden Voraussetzungen erfüllen:
    
      - 32- oder 64-Bit-Versionen von Windows 7 und höher
    
      - Microsoft .NET Framework 4.7
    
      - Einen unterstützten Browser:
        
          - Internet Explorer 10 und höher
            
            ODER
        
          - Mozilla Firefox oder Google Chrome. Wenn Sie eine der folgenden Browser verwenden, installieren Sie die *ClickOnce*Erweiterung. Informationen zur Installation des ClickOnce-Add-Ins finden Sie unter [Mozilla ClickOnce-Add-Ons](https://addons.mozilla.org/en-us/firefox/search/?q=clickonce%26cat=1%2c0%26appver=%26platform=) oder [ClickOnce für Google Chrome](https://chrome.google.com/webstore/search/clickonce?_category=extensions).

  - An das Konto, das Sie exportieren möchten, muss ein aktives Postfach angefügt sein.

  - Stellen Sie sicher, dass die Einstellungen für lokales Intranet in Internet Explorer korrekt eingerichtet sind. Stellen Sie sicher, dass **https://\*.outlook.com** zur Zone für lokales Intranet hinzugefügt wurde.

  - Stellen Sie sicher, dass die folgenden URLs nicht in der Zone der vertrauenswürdigen Websites aufgeführt sind:
    
      - https://\*.outlook.com
    
      - https://r4.res.outlook.com
    
      - https://\*.res.outlook.com

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Verwenden des Exchange-Verwaltungskonsole zum Exportieren der In-Situ-eDiscovery-Suchergebnisse in eine PST-Datei

1.  Navigieren Sie zu **Verwaltung der Richtlinientreue** \> **Compliance-eDiscovery und -Archiv**.

2.  Wählen Sie in der Listenansicht die Compliance-eDiscovery-Suche aus, deren Ergebnisse Sie exportieren möchten, und klicken Sie auf die Option zum Exportieren in eine PST-Datei.
    
    ![Exportieren in eine PST-Datei](images/Dn440164.1ebee2ac-89b3-49fa-b70c-a07c9a65f958(EXCHG.150).gif "Exportieren in eine PST-Datei")  

3.  Gehen Sie im Fenster **eDiscovery-PST-Exporttool** folgendermaßen vor:
    
      - Klicken Sie auf **Durchsuchen**, und geben Sie das Verzeichnis an, in das die PST-Datei heruntergeladen werden soll.
    
      - Klicken Sie auf das Kontrollkästchen **Entfernung von Duplikaten aktivieren**, um doppelte Nachrichten auszuschließen. Es wird nur eine einzelne Instanz einer Nachricht in die PST-Datei aufgenommen.
    
      - Wählen Sie das Kontrollkästchen **Nicht durchsuchbare Elemente einschließen** aus, um Postfachelemente zu berücksichtigen, die nicht durchsucht werden konnten (z. B. Nachrichten mit Anhängen, die Dateitypen enthalten, die von der Exchange-Suche nicht indiziert werden konnten). Nicht durchsuchbare Elemente werden in eine separate PST-Datei exportiert.
        

        > [!IMPORTANT]
        > Das Einschließen nicht durchsuchbarer Elemente beim Export von eDiscovery-Suchergebnissen dauert längern, wenn Postfächer viele nicht durchsuchbare Elemente enthalten. Folgen Sie zum Reduzieren der Dauer des Exports von Suchergebnissen und Verhindern großer PST-Exportdateien den folgenden Empfehlungen: 
        > <UL>
        > <LI>
        > <P>Erstellen Sie mehrere eDiscovery-Suchvorgänge, damit bei jeder Suche weniger Quellpostfächer durchsucht werden müssen.</P>
        > <LI>
        > <P>Wenn Sie sämtliche Postfachinhalte innerhalb eines bestimmten Datumsbereichs (bei Weglassen der Angabe von Schlüsselwörtern in den Suchkriterien) exportieren, werden alle nicht durchsuchbaren Elemente in diesem Datumsbereich automatisch in die Suchergebnisse einbezogen. Aktivieren Sie deshalb nicht das Kontrollkästchen <STRONG>Nicht durchsuchbare Elemente einschließen</STRONG>.</P></LI></UL>



4.  Klicken Sie auf **Start**, um die Suchergebnisse in eine PST-Datei zu exportieren.
    
    Es wird ein Fenster angezeigt, das Statusinformationen über den Exportvorgang anzeigt.

## Weitere Informationen

  - Eine Möglichkeit der Verkleinerung von PST-Exportdateien ist das ausschließliche Exportieren der nicht durchsuchbaren Elemente. Erstellen oder bearbeiten Sie dazu eine Suche, geben Sie ein Startdatum in der Zukunft an, und entfernen Sie alle Schlüsselwörter aus dem Feld **Schlüsselwörter**. Dadurch werden keine Suchergebnisse zurückgegeben. Wenn Sie die Suchergebnisse kopieren oder exportieren und das Kontrollkästchen **Nicht durchsuchbare Elemente einschließen** aktivieren, werden die undurchsuchbaren Elemente in das Discoverypostfach kopiert oder in eine PST-Datei exportiert.

  - Falls Sie Deduplizierung aktiviert haben, werden alle Suchergebnisse in eine einzige PST-Datei exportiert. Wenn Sie Deduplizierung nicht aktivieren, wird für jedes durchsuchte Postfach eine separate PST-Datei exportiert. Wie bereits erwähnt, werden nicht durchsuchbare Elemente in eine separate PST-Datei exportiert.

  - Zusätzlich zu den PST-Dateien, welche die Suchergebnisse enthalten, werden zwei weitere Datei exportiert:
    
      - Eine Konfigurationsdatei (TXT-Datei), die Informationen über die PST-Exportanforderung enthält, wie z. B. den Namen der zu exportierenden eDiscovery-Suche, Datum und Zeit des Exports, Aktivierung von Deduplizierung und nicht durchsuchbaren Elementen, die Suchabfrage sowie die durchsuchten Quellpostfächer.
    
      - Ein Protokoll der Suchergebnisse (CSV-Datei), das einen Eintrag für jede in den Suchergebnissen zurückgegebene Nachricht enthält. Jeder Eintrag identifiziert das Quellpostfach, in dem sich die Nachricht befindet. Falls Sie Deduplizierung aktiviert haben, können Sie damit alle Postfächer identifizieren, die doppelte Nachrichten enthalten.

  - Der Name der Suche ist der erste Teil des Dateinamens jeder Datei, die exportiert wird. Außerdem werden Datum und Uhrzeit der Exportanforderung an den Dateinamen jeder PST-Datei und an das Ergebnisprotokoll angehängt.

  - Weitere Informationen zu Deduplizierung und nicht durchsuchbaren Elementen finden Sie unter:
    
      - [Estimate, preview, and copy search results](in-place-ediscovery-exchange-2013-help.md)
    
      - [Nicht durchsuchbare Elemente in Exchange eDiscovery](unsearchable-items-in-exchange-ediscovery-exchange-2013-help.md)

  - Informationen zum Exportieren von eDiscovery-Suchergebnissen aus dem eDiscovery Center in SharePoint oder SharePoint Online finden Sie unter [Exportieren von eDiscovery-Inhalten und Erstellen von Berichten](https://go.microsoft.com/fwlink/p/?linkid=324757).

## Problembehandlung


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Symptom</th>
<th>Mögliche Ursache</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exportieren in eine PST-Datei nicht möglich.</p></td>
<td><ul>
<li><p>Dem Konto ist kein aktives Konto angefügt. Sie benötigen ein aktives Konto, um die PST-Datei zu exportieren.</p></li>
<li><p>Ihre Version von Internet Explorer ist nicht mehr aktuell. Versuchen Sie, Internet Explorer auf Version 10 oder höher zu aktualisieren. Oder verwenden Sie einen anderen Browser.</p></li>
<li><p>Die Suchkriterien, die Sie in die Abfrage <strong>Auf Kriterien basierter Filter</strong>eingegeben haben, sind falsch. Es wurde beispielsweise ein Benutzername anstelle einer E-Mail-Adresse eingegeben. Weitere Informationen zum Filtern basierend auf Kriterien finden Sie unter <a href="modify-an-in-place-ediscovery-search-exchange-2013-help.md">Ändern einer Compliance-eDiscovery-Suche</a>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Das Exportieren von Suchergebnissen ist einem bestimmten Computer nicht möglich. Der Export funktioniert auf einem anderen Computer wie erwartet.</p></td>
<td><p>In der <strong>Anmeldeinformationsverwaltung</strong> wurden die falschen Windows-Anmeldeinformationen gespeichert. Löschen Sie Ihre Anmeldeinformationen ein, und melden Sie sich erneut an.</p></td>
</tr>
<tr class="odd">
<td><p>Das eDiscovery-PST-Exporttool kann nicht gestartet werden.</p></td>
<td><p>Die Einstellungen für die Zone für lokales Intranet wurden in Internet Explorer nicht korrekt eingerichtet. Vergewissern Sie sich, dass *.outlook.com, *.office365.com, *.sharepoint.com und *.onmicrosoft.com den vertrauenswürdigen Websites der Zone für lokales Intranet hinzugefügt wurden.</p>
<p>Informationen zum Hinzufügen dieser Websites zur Zone vertrauenswürdiger Sites in Internet Explorer finden Sie unter <a href="https://windows.microsoft.com/de-de/windows/security-zones-adding-removing-websites#1tc=windows-7">Sicherheitszonen: Hinzufügen oder Entfernen von Websites</a>.</p></td>
</tr>
</tbody>
</table>

