---
title: 'MAPI über HTTP: Exchange 2013 Help'
TOCTitle: MAPI über HTTP
ms:assetid: 4663b5db-5b30-4a5a-a302-be6fef7fe5da
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Dn635177(v=EXCHG.150)
ms:contentKeyID: 61201338
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# MAPI über HTTP

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2017-05-10_

MAPI (Messaging Application Programming Interface) über HTTP ist ein neues Transportprotokoll, das in MicrosoftExchange Server 2013 Service Pack 1 (SP1) implementiert ist. MAPI über HTTP verbessert die Zuverlässigkeit und Stabilität der Outlook- und Exchange-Verbindungen durch Verschieben der Transportschicht auf das HTTP-Modell nach Industriestandard. Dies ermöglicht bessere Sichtbarkeit von Transportfehlern sowie verbesserte Wiederherstellbarkeit. Die weitere Funktionalität umfasst die Unterstützung für eine explizite Funktion zum Anhalten und Fortsetzen. Dies ermöglicht unterstützten Clients das Ändern des Netzwerks oder das Fortsetzen aus dem Ruhezustand heraus unter Beibehaltung desselben Serverkontexts.

Die Implementierung von MAPI über HTTP bedeutet nicht, dass dies das einzige Protokoll ist, das in Outlook für den Zugriff auf Exchange verwendet werden kann. Outlook-Clients, die MAPI über HTTP nicht ausführen können, können weiterhin Outlook Anywhere (RPC über HTTP) zum Zugriff auf Exchange über einen MAPI-fähigen Clientzugriffsserver verwenden.

## Vorteile von MAPI über HTTP

MAPI über HTTP bietet die folgenden Vorteile für Clients, die dieses Protokoll unterstützen:

  - Ermöglicht künftige Authentifizierungsneuerungen durch Verwendung eines HTTP-basierten Protokolls.

  - Bietet schnellere Neuverbindungen nach einer Kommunikationsunterbrechung, da nur TCP-Verbindungen (keine RPC-Verbindungen) erneut aufgebaut werden müssen. Beispiele für eine Kommunikationsunterbrechung:
    
      - Gerät im Ruhezustand
    
      - Wechsel von einem verkabelten zu einem Drahtlos- oder Mobilfunknetzwerk

  - Bietet Sitzungskontext, der unabhängig von der Verbindung ist. Der Server behält den Sitzungskontext für einen konfigurierbaren Zeitraum bei – selbst wenn der Benutzer das Netzwerk wechselt.

## Bereitstellen von MAPI über HTTP

Beachten Sie die folgenden Anforderungen zur Aktivierung von MAPI über HTTP.

  - **Unterstützung**   Stellen Sie sicher, dass Ihre gewünschten Konfigurationsversionen unterstützt werden.

  - **Voraussetzungen**   Vergewissern Sie sich, dass Ihre Umgebung für MAPI über HTTP aktualisiert und vorbereitet wurde.

  - **Konfiguration**   Konfigurieren Sie die virtuellen Verzeichnisse, und aktivieren Sie MAPI für Ihre Organisation.

## Unterstützung

Verwenden Sie die folgende Matrix, um sicherzustellen, dass Ihre Clients und Server MAPI über HTTP unterstützen.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Produkt</th>
<th>Exchange 2013 SP1</th>
<th>Exchange 2013 RTM</th>
<th>Exchange 2010 SP3</th>
<th>Exchange 2007 SP3</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook 2013 SP1</p></td>
<td><ul>
<li><p>MAPI über HTTP</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><p>Outlook Anywhere</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook 2013 RTM</p></td>
<td><p>Outlook Anywhere</p></td>
<td><p>Outlook Anywhere</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook 2010 SP2 und Updates KB2956191 und KB2965295 (14. April 2015)</p></td>
<td><ul>
<li><p>MAPI über HTTP<span></span></p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><p>Outlook Anywhere</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook 2010 SP2 und früher</p></td>
<td><p>Outlook Anywhere</p></td>
<td><p>Outlook Anywhere</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Outlook 2007</p></td>
<td><p>Outlook Anywhere</p></td>
<td><p>Outlook Anywhere</p></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
<td><ul>
<li><p>RPC</p></li>
<li><p>Outlook Anywhere</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Voraussetzungen

Führen Sie die folgenden Schritte aus, um die Clients und Server für die Unterstützung von MAPI über HTTP vorzubereiten.

1.  Aktualisieren Sie die Outlook-Clients auf Outlook 2013 SP1 oder Outlook 2010 SP2, und installieren Sie die Updates KB2956191 und KB2965295 (14. April 2015).

2.  Aktualisieren Sie die Clientzugriffs- und Postfachserver auf Exchange 2013 SP1. Weitere Informationen zum Upgrade finden Sie unter [Aktualisieren von Exchange 2013 auf das neueste kumulative Update oder Service Pack](upgrade-exchange-2013-to-the-latest-cumulative-update-or-service-pack-exchange-2013-help.md).
    

    > [!NOTE]
    > Alle Clientzugriffsserver müssen auf Exchange 2013 SP1 aktualisiert werden, bevor Sie MAPI über HTTP aktivieren. Andernfalls kann Outlook keine Verbindung zu den Postfächern herstellen.<BR>Falls nicht alle Postfachserver in der Datenbankverfügbarkeitsgruppe (DAG) aktualisiert werden, kann es zu Mailverzögerungen oder einer Neustartanforderung für Outlook auf dem Client bei Datenbank-Failover kommen.



3.  Auf allen Exchange 2013-Servern müssen Sie Microsoft.NET Framework 4.5.2 installieren. Weitere Informationen erhalten Sie unter [Installieren von .NET Framework](https://go.microsoft.com/fwlink/p/?linkid=518380).

4.  Fügen Sie auf allen Exchange 2013 SP1-Clientzugriffs-Servern anhand der folgenden Schritte die **COMPLUS\_DisableRetStructPinning**-Windows-Umgebungsvariable hinzu.
    
    1.  Führen Sie in einem Eingabeaufforderungsfenster `systempropertiesadvanced` aus, und klicken Sie auf **Umgebungsvariablen**.
    
    2.  Klicken Sie im Abschnitt **Systemvariablen** auf **Neu**, und geben Sie die folgenden Informationen ein.
        
          - **Name der Variable**   `COMPLUS_DisableRetStructPinning`
        
          - **Wert der Variable**   1
    
    3.  Klicken Sie nach Abschluss des Vorgangs auf **OK**.

## Konfiguration

Führen Sie die folgenden Schritte aus, um MAPI über HTTP für Ihre Organisation zu konfigurieren.

1.  **Virtuelle Verzeichniskonfiguration**   Standardmäßig erstellt Exchange 2013 SP1 ein virtuelles Verzeichnis für MAPI über HTTP. Verwenden Sie das Cmdet **Set-MapiVirtualDirectory**, um das virtuelle Verzeichnis zu konfigurieren. Sie müssen eine interne URL, eine externe URL oder beides konfigurieren. Weitere Informationen finden Sie unter [Set-MapiVirtualDirectory](https://technet.microsoft.com/de-de/library/dn595082\(v=exchg.150\)).
    
    Führen Sie beispielsweise folgenden Befehl aus, um das virtuelle Standard-MAPI-Verzeichnis auf dem lokalen Exchange-Server durch Festlegen des internen URL-Wertes auf "https://contoso.com/mapi" und `Negotiate` als Authentifizierungsmethode zu konfigurieren:
    
        Set-MapiVirtualDirectory -Identity "Contoso\mapi (Default Web Site)" -InternalUrl https://Contoso.com/mapi -IISAuthenticationMethods Negotiate

2.  **Zertifikatkonfiguration**   Das von der Exchange-Umgebung verwendete Zertifikat muss dieselben Werte für *InternalURL* und *ExternalURL* enthalten, die im virtuellen MAPI-Verzeichnis definiert sind. Weitere Informationen zur Exchange 2013-Zertifikatverwaltung finden Sie unter [Digitale Zertifikate und SSL](digital-certificates-and-ssl-exchange-2013-help.md). Stellen Sie sicher, dass das Exchange-Zertifikat auf der Outlook-Clientarbeitsstation vertrauenswürdig ist und dass keine Zertifikatfehler vorliegen, vor allem wenn Sie die im virtuellen MAPI-Verzeichnis konfigurierten URLs aufrufen.

3.  **Aktualisieren der Serverregeln**   Stellen Sie sicher, dass der Lastenausgleich, Reverse-Proxyserver und Firewalls für den Zugriff auf das virtuelle MAPI über HTTP-Verzeichnis konfiguriert sind.

4.  **Aktivieren von MAPI über HTTP in Ihrer Exchange-Organisation**
    
    Führen Sie den folgenden Befehl aus:
    
        Set-OrganizationConfig -MapiHttpEnabled $true

## Testen von MAPI über HTTP-Verbindungen

Sie können die End-to-End-Verbindung mit MAPI über HTTP mithilfe des Cmdlets **Test-OutlookConnectivity** testen. Um das Cmdlet **Test-OutlookConnectivity** verwenden zu können, muss der Microsoft Exchange-Integritätsdienst (MSExchangeHM) gestartet werden.

Im folgenden Beispiel wird die MAPI über HTTP-Verbindung von einem Exchange-Server namens ContosoMail getestet.

    Test-OutlookConnectivity -RunFromServerId ContosoMail -ProbeIdentity OutlookMapiHttpSelfTestProbe

Wenn der Test erfolgreich ist, ähnelt die Ausgabe dem folgenden Beispiel:

    MonitorIdentity                                          StartTime              EndTime                Result      Error     Exception
    ---------------                                          ---------              -------                ------      -----     ---------
    OutlookMapiHttp.Protocol\OutlookMapiHttpSelfTestProbe    2/14/2014 7:15:00 AM   2/14/2014 7:15:10 AM   Succeeded

Weitere Informationen finden Sie unter [Test-OutlookConnectivity](https://technet.microsoft.com/de-de/library/dd638082\(v=exchg.150\)).

Protokolle für MAPI über HTTP-Aktivitäten befinden sich in den folgenden Verzeichnissen:

  - %ExchangeInstallationspfad%Logging\\MAPI Address Book Service\\

  - %ExchangeInstallationspfad%Logging\\MAPI Client Access\\

  - %ExchangeInstallPath%Logging\\HttpProxy\\Mapi\\

## Verwalten von MAPI über HTTP

Sie können die MAPI über HTTP-Konfiguration mithilfe der folgenden Cmdlets verwalten:

  - [Set-MapiVirtualDirectory](https://technet.microsoft.com/de-de/library/dn595082\(v=exchg.150\))

  - [Get-MapiVirtualDirectory](https://technet.microsoft.com/de-de/library/dn595080\(v=exchg.150\))

  - [New-MapiVirtualDirectory](https://technet.microsoft.com/de-de/library/dn595081\(v=exchg.150\))

  - [Remove-MapiVirtualDirectory](https://technet.microsoft.com/de-de/library/dn595083\(v=exchg.150\))

