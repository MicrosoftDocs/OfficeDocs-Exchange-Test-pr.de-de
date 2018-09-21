---
title: 'Verwalten der Absenderfilterung: Exchange 2013 Help'
TOCTitle: Verwalten der Absenderfilterung
ms:assetid: a7f4b3e1-2970-45ad-911e-a9f46d880d3d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124087(v=EXCHG.150)
ms:contentKeyID: 50476426
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Absenderfilterung

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Absenderfilterung wird durch den Absenderfilter-Agent bereitgestellt. Der Absenderfilter-Agent ist abhängig von der **MAIL FROM:** - SMTP-Kopfzeile, um die Aktion festzulegen, die ggf. auf eine eingehende E-Mail angewendet werden soll.

Wenn auf einem Exchange-Server die Absenderfilterungsfunktion aktiviert ist, filtert diese alle Nachrichten, die über alle Empfangsconnectors auf dem betreffenden Computer eingehen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfeatures" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Absenderfilterung mithilfe der Shell

Im Folgenden wird der Befehl zum Deaktivieren der Absenderfilterung beschrieben:

```powershell
Set-SenderFilterConfig -Enabled $false
```

Um Absenderfilterung zu aktivieren, führen Sie den folgenden Befehl aus:

```powershell
Set-SenderFilterConfig -Enabled $true
```


> [!NOTE]
> Wenn Sie die Absenderfilterung deaktivieren, ist der zugrunde liegende Absenderfilter-Agent nach wie vor aktiviert. Führen Sie zum Deaktivieren des Absenderfilter-Agents folgenden Befehl aus: <CODE>Disable-TransportAgent "Sender Filter Agent"</CODE>.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die Absenderfilterung erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-SenderFilterConfig | Format-List Enabled
```

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Verwenden Sie die Shell zum Konfigurieren von blockierten Absendern und Domänen

Führen Sie den folgenden Befehl aus, um die vorhandenen Werte zu ersetzen:

    Set-SenderFilterConfig -BlockedSenders <sender1,sender2...> -BlockedDomains <domain1,domain2...> -BlockedDomainsAndSubdomains <domain1,domain2...>

In diesem Beispiel wird der Absenderfilter-Agent so konfiguriert, dass Nachrichten von "kim@contoso.com" und "john@contoso.com", Nachrichten von der Domäne "fabrikam.com" sowie Nachrichten von der Domäne "northwindtraders.com" und allen zugehörigen Unterdomänen blockiert werden.

    Set-SenderFilterConfig -BlockedSenders kim@contoso.com,john@contoso.com -BlockedDomains fabrikam.com -BlockedDomainsAndSubdomains northwindtraders.com

Führen Sie folgenden Befehl aus, um Einträge hinzuzufügen bzw. zu entfernen, ohne vorhandene Werte zu ändern:

    Set-SenderFilterConfig -BlockedSenders @{Add="<sender1>","<sender2>"...; Remove="<sender1>","<sender2>"...} -BlockedDomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...} -BlockedDomainsAndSubdomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}

In diesem Beispiel wird der Absenderfilter-Agent mit den folgenden Informationen konfiguriert:

  - Fügen Sie "chris@contoso.com" und "michelle@contoso.com" der Liste vorhandener blockierter Absender hinzu.

  - Entfernen Sie "tailspintoys.com" aus der Liste vorhandener blockierter Absenderdomänen.

  - Fügen Sie "blueyonderairlines.com" der Liste vorhandener blockierter Absenderdomänen und zugehöriger Unterdomänen hinzu.

<!-- end list -->

    Set-SenderFilterConfig -BlockedSenders @{Add="chris@contoso.com","michelle@contoso.com"} -BlockedDomains @{Remove="tailspintoys.com"} -BlockedDomainsAndSubdomains @{Add="blueyonderairlines.com"}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob blockierte Absender erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-SenderFilterConfig | Format-List BlockedSenders,BlockedDomains,BlockedDomainsAndSubdomains
```

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Verwenden Sie die Shell zum Aktivieren oder Deaktivieren der Blockierung von Nachrichten ohne Absender

Führen Sie zum Aktivieren oder Deaktivieren der Blockierung von Nachrichten ohne Absender den folgenden Befehl aus:

```powershell
Set-SenderFilterConfig -BlankSenderBlockingenabled <$true | $false>
```

In diesem Beispiel wird der Absenderfilter-Agent so konfiguriert, dass Nachrichten blockiert werden, die keinen Absender im SMTP-Befehl "MAIL FROM:" aufweisen:

```powershell
Set-SenderFilterConfig -BlankSenderBlockingEnabled $true
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die Blockierung von Nachrichten ohne Absender erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-SenderFilterConfig | Format-List BlankSenderBlockingEnabled
```

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

