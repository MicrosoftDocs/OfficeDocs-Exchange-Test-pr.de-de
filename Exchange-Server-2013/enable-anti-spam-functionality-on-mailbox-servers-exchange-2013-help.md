---
title: 'Aktivieren der Antispamfunktionen auf einem Postfachserver: Exchange 2013 Help'
TOCTitle: Aktivieren der Antispamfunktionen auf einem Postfachserver
ms:assetid: 59d22c5e-64bc-4879-8ad1-364862b6ba11
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb201691(v=EXCHG.150)
ms:contentKeyID: 50475713
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren der Antispamfunktionen auf einem Postfachserver

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2014-01-23_

In Microsoft Exchange Server 2013 stehen die folgenden Antispam-Agents im Transportdienst auf Postfachservern zur Verfügung, diese werden jedoch nicht standardmäßig installiert:

  - Inhaltsfilter-Agent

  - Sender ID-Agent

  - Absenderfilter-Agent

  - Empfängerfilter-Agent

  - Protokollanalyse-Agent für die Absenderzuverlässigkeit

Sie können diese Antispam-Agents jedoch mithilfe eines Skripts der Exchange-Verwaltungsshell installieren. In der Regel installieren Sie diese Antispam-Agents nur dann auf einem Postfachserver, wenn Ihre Organisation alle eingehenden E-Mails ohne vorherige Antispamfilterung akzeptiert werden.

Was geschieht, wenn Sie die verfügbaren Antispam-Agents im Transportdienst auf einem Postfachserver installieren, aber auch andere Exchange-Antispam-Agents die Nachrichten verarbeiten, bevor Sie den Postfachserver erreichen? Was geschieht beispielsweise, wenn Sie über einen Microsoft Exchange 2007- oder Exchange 2010-Edge-Transport-Server im Umkreisnetzwerk verfügen, der eingehende E-Mails direkt an den Transportdienst auf dem Postfachserver weiterleitet? Die Antispam-Agents auf dem Postfachserver erkennen die Antispam-X-Headerwerte, die von anderen Exchange-Antispam-Agents zu Nachrichten hinzugefügt werden, und alle Nachrichten mit diesen X-Headern passieren den Server ohne erneute Prüfung. Vom Empfängerfilter-Agent ausgeführte Empfängersuchen werden jedoch auf dem Postfachserver erneut ausgeführt.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen dieser Aufgabe: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Transportkonfiguration" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Der Verbindungsfilter-Agent und der Anlagenfilter-Agent sind auf Postfachservern nicht verfügbar. Diese Agents stehen nur auf einem Edge-Transport-Server zur Verfügung. Der Antischadsoftware-Agent wird jedoch standardmäßig auf einem Postfachserver installiert und aktiviert. Weitere Informationen finden Sie unter [Antischadsoftwareschutz](anti-malware-protection-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Wie gehen Sie dazu vor?

## Schritt 1: Ausführen des Skripts "Install-AntispamAgents.ps1" mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    & $env:ExchangeInstallPath\Scripts\Install-AntiSpamAgents.ps1

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie wissen, dass dieser Schritt ordnungsgemäß ausgeführt wurde, wenn die Skriptausführung ohne Fehler abgeschlossen wurde und Sie aufgefordert werden, den Microsoft Exchange-Transportdienst neu zu starten.

## Schritt 2: Erneutes Starten des Microsoft Exchange-Transportdiensts mithilfe der Shell

Führen Sie den folgenden Befehl aus:

```powershell
Restart-Service MSExchangeTransport
```

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Sie wissen, dass dieser Schritt ordnungsgemäß ausgeführt wurde, wenn der Microsoft Exchange-Transportdienst fehlerfrei neu gestartet wurde.

## Schritt 3: Angeben der internen SMTP-Server in Ihrer Organisation mithilfe der Shell

Sie müssen die IP-Adresse eines beliebigen internen SMTP-Servers angeben, der durch den Sender ID-Agent ignoriert werden soll. Tatsächlich müssen Sie die IP-Adresse von mindestens einem internen SMTP-Server angeben. Wenn der Postfachserver, auf dem die Antispam-Agents ausgeführt werden, der einzige SMTP-Server in der Organisation ist, geben Sie die IP-Adresse dieses Computers ein.

Führen Sie den folgenden Befehl aus, um die IP-Adressen interner SMTP-Server hinzuzufügen, ohne vorhandene Werte zu beeinflussen:

```powershell
Set-TransportConfig -InternalSMTPServers @{Add="<ip address1>","<ip address2>"...}
```

In diesem Beispiel werden die internen SMTP-Serveradressen 10.0.1.10 und 10.0.1.11 zur Transportkonfiguration der Organisation hinzugefügt.

```powershell
Set-TransportConfig -InternalSMTPServers @{Add="10.0.1.10","10.0.1.11"}
```

## Woher wissen Sie, dass dieser Schritt erfolgreich war?

Gehen Sie wie folgt vor, um sicherzustellen, dass die IP-Adresse von mindestens einem internen SMTP-Server erfolgreich angegeben wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-TransportConfig | Format-List InternalSMTPServers
```

2.  Vergewissern Sie sich, dass die IP-Adresse von mindestens einem gültigen internen SMTP-Server angezeigt wird.

