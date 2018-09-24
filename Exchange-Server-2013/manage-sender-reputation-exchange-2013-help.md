---
title: 'Verwalten der Absenderzuverlässigkeit: Exchange 2013 Help'
TOCTitle: Verwalten der Absenderzuverlässigkeit
ms:assetid: f2716bd9-e3ac-46d9-9264-4e3dabfa0f38
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125186(v=EXCHG.150)
ms:contentKeyID: 50477064
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Absenderzuverlässigkeit

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Absenderzuverlässigkeit wird durch den Protokollanalyse-Agent bereitgestellt. Die Absenderzuverlässigkeit blockiert Nachrichten aufgrund verschiedener Merkmale des Absenders. Die Absenderzuverlässigkeit verwendet gespeicherte Daten über den Absender, um die Aktion zu bestimmen, die ggf. für eine eingehende Nachricht ausgeführt werden soll.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Der Protokollanalyse-Agent ist der zugrunde liegende Agent für die Funktion der Absenderzuverlässigkeit. Wenn Sie die Absenderzuverlässigkeit deaktivieren, bleibt der Protokollanalyse-Agent weiterhin aktiviert.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Absenderzuverlässigkeit mithilfe der Shell

In diesem Beispiel wird die Absenderzuverlässigkeit deaktiviert.

```powershell
Set-SenderReputationConfig -Enabled $false
```

Im folgenden Beispiel wird die Absenderzuverlässigkeit aktiviert.

```powershell
Set-SenderReputationConfig -Enabled $true
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Absenderzuverlässigkeit erfolgreich aktiviert oder deaktiviert haben:

1.  Überprüfen Sie mit dem folgenden Befehl, ob der Protokollanalyse-Agent installiert und aktiviert ist:
    
    ```powershell
    Get-TransportAgent
    ```

2.  Überprüfen Sie mit dem folgenden Befehl die Absenderzuverlässigkeitswerte, die Sie konfiguriert haben:
    
    ```powershell
    Get-SenderReputationConfig | Format-List Enabled,*MailEnabled
    ```

## Aktivieren oder Deaktivieren der Absenderzuverlässigkeit für interne oder externe Nachrichten mithilfe der Shell

Die Absenderzuverlässigkeit ist für externe Nachrichten standardmäßig aktiviert und für interne Nachrichten deaktiviert. Eine Nachricht gilt als extern, wenn sie von einer nicht authentifizierten Verbindung stammt, die sich außerhalb Ihrer Exchange-Organisation befindet. Eine Nachricht gilt als intern, wenn sie von einer authentifizierten Verbindung stammt und die Domäne des Absenders als autoritative Domäne in Ihrer Exchange-Organisation konfiguriert ist.

Führen Sie zum Deaktivieren der Absenderzuverlässigkeit für externe Nachrichten den folgenden Befehl aus:

```powershell
Set-SenderReputationConfig -ExternalMailEnabled $false
```

Führen Sie zum Aktivieren der Absenderzuverlässigkeit für externe Nachrichten den folgenden Befehl aus:

```powershell
Set-SenderReputationConfig -ExternalMailEnabled $true
```

Führen Sie zum Deaktivieren der Absenderzuverlässigkeit für interne Nachrichten den folgenden Befehl aus:

```powershell
Set-SenderReputationConfig -InternalMailEnabled $false
```

Führen Sie zum Aktivieren der Absenderzuverlässigkeit für interne Nachrichten den folgenden Befehl aus:

```powershell
Set-SenderReputationConfig -InternalMailEnabled $true
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Absenderzuverlässigkeit für interne und externe Nachrichten erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-SenderReputationConfig | Format-List Enabled,*MailEnabled
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Konfigurieren von Absenderzuverlässigkeitseigenschaften mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Eigenschaften der Absenderzuverlässigkeit zu konfigurieren:

```powershell
Set-SenderReputationConfig -SrlBlockThreshold <Value> -SenderBlockingPeriod <Hours>
```

In diesem Beispiel wird der Sperrschwellenwert für den Absenderzuverlässigkeitsgrad (Sender Reputation Level, SRL) auf 6 festgelegt, und die Absenderzuverlässigkeit wird so konfiguriert, dass problematische Absender für 36 Stunden der IP-Sperrliste hinzugefügt werden:

```powershell
Set-SenderReputationConfig -SrlBlockThreshold 6 -SenderBlockingPeriod 36
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Absenderzuverlässigkeitseigenschaften erfolgreich konfiguriert haben:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
    Get-SenderReputationConfig
    ```

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Konfigurieren des ausgehenden Zugriffs für die Erkennung offener Proxyserver mithilfe der Shell

Möglicherweise müssen Sie weitere Schritte ausführen, damit die Absenderzuverlässigkeit Firewalls zwischen dem Internet und dem Exchange-Server, auf dem der Protokollanalyse-Agent ausgeführt wird, überwinden kann. In der folgenden Tabelle sind die ausgehenden Ports aufgelistet, die für die Absenderzuverlässigkeit erforderlich sind.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Protokolle</th>
<th>Ports</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SOCKS4, SOCKS5</p></td>
<td><p>1081, 1080</p></td>
</tr>
<tr class="even">
<td><p>Wingate, Telnet, Cisco</p></td>
<td><p>23</p></td>
</tr>
<tr class="odd">
<td><p>HTTP CONNECT, HTTP POST</p></td>
<td><p>6588, 3128, 80</p></td>
</tr>
</tbody>
</table>


Mit dem folgenden Befehl konfigurieren Sie den ausgehenden Zugriff für die Erkennung von offenen Proxyservern:

```powershell
Set-SenderReputationConfig -ProxyServerName <String> -ProxyServerPort <Port> -ProxyServerType <String>
```

In diesem Beispiel wird die Absenderzuverlässigkeit für die Verwendung des offenen Proxyservers SERVER01 mit dem Protokoll HTTP CONNECT an Port 80 konfiguriert.

```powershell
Set-SenderReputationConfig - ProxyServerName SERVER01 -ProxyServerPort 80 -ProxyServerType HttpConnect
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie den ausgehenden Zugriff für die Erkennung von offenen Proxyservern erfolgreich konfiguriert haben:

1.  Führen Sie den folgenden Befehl aus:
    
       ```powershell
       Get-SenderReputationConfig | Format-List ProxyServer*
       ```

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

