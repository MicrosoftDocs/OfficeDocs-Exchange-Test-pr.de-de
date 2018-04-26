---
title: Problembehandlung beim OWA.Protocol.Dep-Integritätssatz
TOCTitle: Problembehandlung beim OWA.Protocol.Dep-Integritätssatz
ms:assetid: f39c63d5-f161-4eee-9415-05f3355e7cc7
ms:mtpsurl: https://technet.microsoft.com/de-de/library/ms.exch.scom.owa.protocol.dep(v=EXCHG.150)
ms:contentKeyID: 54651569
ms.date: 01/12/2016
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Problembehandlung beim OWA.Protocol.Dep-Integritätssatz

 

_**Gilt für:**Exchange Server 2013, Project Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-11-10_

Der **OWA.Protocol.DEP**-Integritätssatz überwacht die Gesamtintegrität der Chatdienste in Outlook Web App, die zwischen Lync 2013 und Exchange 2013 integriert sind. Weitere Informationen über das Aktivieren von Chats in Outlook Web App finden Sie unter [Integrieren von Microsoft Lync Server 2013 und Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

Wenn Sie eine Warnung erhalten, die darauf hindeutet, dass der **OWA.Protocol.DEP**-Integritätssatz nicht intakt ist, weist dies auf ein Problem hin, das die ordnungsgemäße Funktionsweise des Chats in Outlook Web App möglicherweise verhindert.

## Erläuterung

Der **OWA.Protocol.DEP**-Dienst wird mithilfe der folgenden Tests und Monitore überwacht.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Test</th>
<th>Integritätssatz</th>
<th>Zugehörige Monitore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>OWA.Protocol.DEP</p></td>
<td><p>OwaIMInitializationFailedMonitor</p></td>
</tr>
<tr class="even">
<td><p>keine (Benachrichtigung oder Prüfung)</p></td>
<td><p>OWA.Protocol.DEP</p></td>
<td><p>WacDiscoveryFailureEventMonitor</p></td>
</tr>
</tbody>
</table>


Weitere Informationen zu Tests und Monitoren finden Sie unter [Serverstatus und -leistung](https://technet.microsoft.com/de-de/library/jj150551\(v=exchg.150\)).

## Benutzeraktion

Es ist möglich, dass der Dienst wiederhergestellt wurde, nachdem er die Warnung ausgegeben hat. Wenn Sie also eine Warnung erhalten, dass Integritätsfehler im **OWA.Protocol.DEP**-Integritätssatz vorliegen, überprüfen Sie zuerst, ob das Problem noch besteht. Besteht das Problem noch, führen Sie die geeigneten Wiederherstellungsaktionen aus, die in den folgenden Abschnitten beschrieben sind.

## Wiederherstellungsaktion für Fehler: "InstantMessageOCSProvider.InitializeEndpointManager. No registry setting for IM Provider." (InstantMessageOCSProvider.InitializeEndpointManager. Keine Registrierungseinstellung für Chatanbieter.)

Dieser Fehler weist darauf hin, dass ein erforderlicher Registrierungsschlüssel auf dem Postfachserver fehlt. Dieser Registrierungsschlüssel sollte beim Installieren von Microsoft Unified Communications Managed API (UCMA) 4.0 auf dem Server konfiguriert werden. Der fehlende Registrierungsschlüssel lautet:

    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\MSExchange OWA\InstantMessaging

Dieser Schlüssel sollte eine **ImplementationDLLPath**-Zeichenfolge enthalten, die auf die `Microsoft.Rtc.Internal.Ucweb`-DLL zeigt. Der Standardspeicherort ist `C:\Program Files\Microsoft UCMA 4.0\Runtime\SSP\Microsoft.Rtc.Internal.Ucweb.dll`.

Installieren Sie zum Beheben dieses Problems UCMA 4.0 erneut, oder erstellen Sie den Registrierungsschlüssel manuell. Sie können UCMA 4.0 hier herunterladen: [Unified Communications Managed API 4.0 Runtime](http://go.microsoft.com/fwlink/p/?linkid=260990).

## Wiederherstellungsaktion für Fehler: "InstantMessageOCSProvider.InitializeEndpointManager. IM provider not found." (InstantMessageOCSProvider.InitializeEndpointManager. Chatanbieter wurde nicht gefunden.)

Dieser Fehler weist darauf hin, dass die `Microsoft.Rtc.Internal.Ucweb`-DLL-Datei auf dem Postfachserver fehlt. Diese Datei sollte beim Installieren von UCMA 4.0 auf dem Server installiert worden sein. Der Standardspeicherort ist `C:\Program Files\Microsoft UCMA 4.0\Runtime\SSP`.

Installieren Sie zum Beheben dieses Problems UCMA 4.0 erneut. Weitere Informationen finden Sie unter [Unified Communications Managed API 4.0 Runtime](http://go.microsoft.com/fwlink/p/?linkid=260990).

## Wiederherstellungsaktion für Fehler: "Instant Messaging Server name is set to null or empty on web.config." (Name des Chatservers ist in der Datei 'web.config' auf 'null' festgelegt oder leer.)

Dieser Fehler weist darauf hin, dass der Lync 2013-Server in der Outlook Web App-Anwendungskonfigurationsdatei ("web.config") auf dem Postfachserver nicht definiert ist. Dieser `web.config`-Datei befindet sich unter `%ExchangeInstallPath%ClientAccess\Owa`. Sie sollte einen Schlüssel mit dem Namen **IMServerName** aufweisen, der den vollqualifizierten Domänennamen des Lync 2013-Servers angibt. Führen Sie zum Beheben dieses Problems die folgenden Schritte aus:

1.  Öffnen Sie in einem Befehlszeilenfenster die "web.config"-Datei für Outlook Web App in Editor, indem Sie den folgenden Befehl ausführen:
    
        Notepad %ExchangeInstallPath%ClientAccess\Owa\web.config

2.  Suchen Sie nach dem Schlüssel **IMServerName**. Wenn er gefunden wird, müssen Sie den vollqualifizierten Domänennamen des Lync 2013-Servers überprüfen. Wenn der Schlüssel nicht gefunden wird, fügen Sie ihn hinzu, indem Sie die folgenden Schritte ausführen.
    
    1.  Suchen Sie das Tag **\<appSettings\>**.
    
    2.  Fügen Sie im Knoten **\<appSettings\>** die folgende Zeile hinzu:
        
            <add key="IMServerName" value="Lync Server FQDN" />
        
        Beispiel:
        
            <add key="IMServerName" value="lync01.contoso.com" />
    
    3.  Führen Sie zum Übernehmen der Änderungen in Outlook Web App den folgenden Befehl aus:
        
            %windir%\system32\inetsrv\appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

## Wiederherstellungsaktion für Fehler: "Instant Messaging Certificate Thumbprint is null or empty on web.config." (Fingerabdruck des Chatzertifikats ist in der Datei 'web.config' auf 'null' festgelegt oder leer.)

Dieser Fehler deutet darauf hin, dass das zum Integrieren von Lync 2013 und Outlook Web App verwendete Zertifikat nicht in der Outlook Web App-Anwendungskonfigurationsdatei ("web.config") auf dem Postfachserver definiert ist. Diese `web.config`-Datei befindet sich unter `%ExchangeInstallPath%ClientAccess\Owa`. Sie sollte den Schlüssel **IMCertificateThumbprint** aufweisen, der den Fingerabdruck (Hash) des Zertifikats angibt.

Sie können den Fingerabdruckswert des Zertifikats über das Cmdlet **Get-ExchangeCertificate** verwenden oder in Exchange Admin Center (EAC) unter **Server** \> **Zertifikate** abrufen.

Führen Sie zum Beheben dieses Problems die folgenden Schritte aus:

1.  Öffnen Sie in einem Befehlszeilenfenster die "web.config"-Datei für Outlook Web App in Editor, indem Sie den folgenden Befehl ausführen:
    
        Notepad %ExchangeInstallPath%ClientAccess\Owa\web.config

2.  Suchen Sie nach dem Schlüssel **IMCertificateThumbprint**. Wenn er gefunden wird, stellen Sie sicher, dass der Fingerabdruckswert richtig ist. Wenn der Schlüssel nicht gefunden wird, fügen Sie ihn hinzu, indem Sie die folgenden Schritte ausführen:
    
    1.  Suchen Sie das Tag **\<appSection\>**.
    
    2.  Fügen Sie im Knoten **\<appSection\>** die folgende Zeile hinzu:
        
            <add key="IMCertificateThumbprint" value="thumbprint"/>
        
        Beispiel:
        
            <add key="IMCertificateThumbprint" value="35CB4C441D55506C88E59B7946B567A4F45B3B5C" />
    
    3.  Führen Sie zum Übernehmen der Änderungen in Outlook Web App den folgenden Befehl aus:
        
            %windir%\system32\inetsrv\appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

## Wiederherstellungsaktion für Fehler: "IM Certificate with thumbprint \<value\> could not be found." (Das Chatzertifikat mit dem Fingerabdruck 'value' wurde nicht gefunden.)

Dieser Fehler deutet darauf hin, dass das zum Integrieren von Lync 2013 und Outlook Web App verwendete Zertifikat auf dem Postfachserver nicht gefunden wird. Dieses Zertifikat muss auf dem Postfach- und dem Lync 2013-Server installiert sein, und ihm muss von beiden Servern vertraut werden. Weitere Informationen über die Zertifikatsanforderungen finden Sie im Abschnitt "Aktivieren von Chatfunktionen in Outlook Web App" unter [Integrieren von Microsoft Lync Server 2013 und Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

Sie können den Fingerabdruckswert im Fehler mit dem Zertifikat abgleichen, indem Sie das Cmdlet **Get-ExchangeCertificate** verwenden oder in Exchange Admin Center (EAC) zu **Server** \> **Zertifikate** wechseln.

## Wiederherstellungsaktion für Fehler: "IM Certificate has expired." (Chatzertifikat ist abgelaufen.)

Dieser Fehler deutet darauf hin, dass das zum Integrieren von Lync 2013 und Outlook Web App verwendete Zertifikat abgelaufen ist. Zum Beheben dieses Fehlers müssen Sie das Zertifikat erneuern.

Sie können den Fingerabdruckswert im Fehler mit dem Zertifikat abgleichen, indem Sie das Cmdlet **Get-ExchangeCertificate** verwenden oder in Exchange Admin Center (EAC) zu **Server** \> **Zertifikate** wechseln.

## Wiederherstellungsaktion für Fehler: "IM Certificate has not become valid yet." (Chatzertifikat ist noch nicht gültig)

Dieser Fehler deutet darauf hin, dass das zum Integrieren von Lync 2013 und Outlook Web App verwendete Zertifikat über ungültige Datumsangaben verfügt. Zum Beheben dieses Fehlers müssen Sie ein neues Zertifikat konfigurieren, und Sie müssen den neuen Fingerabdruckswert im Schlüssel **IMCertificateThumbprint** in `%ExchangeInstallPath%ClientAccess\Owa\web.config` hinzufügen. Weitere Informationen über die Zertifikatsanforderungen finden Sie im Abschnitt "Aktivieren von Chatfunktionen in Outlook Web App" unter [Integrieren von Microsoft Lync Server 2013 und Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

## Wiederherstellungsaktion für Fehler: "IM Certificate does not have a private key." (Chatzertifikat weist keinen privaten Schlüssel auf.)

Dieser Fehler weist darauf hin, dass das zum Integrieren von Lync 2013 und Outlook Web App verwendete Zertifikat über keinen privaten Schlüssel verfügt. Zum Beheben dieses Fehlers müssen Sie ein neues Zertifikat, das einen privaten Schlüssel aufweist, konfigurieren, und Sie müssen den neuen Fingerabdruckswert im Schlüssel **IMCertificateThumbprint** in `%ExchangeInstallPath%ClientAccess\Owa\web.config` hinzufügen. Weitere Informationen über die Zertifikatsanforderungen finden Sie im Abschnitt "Aktivieren von Chatfunktionen in Outlook Web App" unter [Integrieren von Microsoft Lync Server 2013 und Microsoft Outlook Web App 2013](http://go.microsoft.com/fwlink/p/?linkid=280418).

