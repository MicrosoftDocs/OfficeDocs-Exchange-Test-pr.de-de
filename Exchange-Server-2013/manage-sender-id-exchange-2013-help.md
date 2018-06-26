---
title: 'Verwalten der Absender-ID: Exchange 2013 Help'
TOCTitle: Verwalten der Absender-ID
ms:assetid: 2e7b646a-8a66-4be7-a7c1-0bd43bb79a5b
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997136(v=EXCHG.150)
ms:contentKeyID: 50475405
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Absender-ID

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2015-04-08_

Die Funktion der Sender ID wird durch den Sender ID-Agent bereitgestellt. Die Sender ID bestätigt den Ursprung von E-Mails, indem die IP-Adresse des Absenders mit dem vorgeblichen Besitzer der Absenderdomäne verglichen wird. Die Sender ID-Filterung wird für eingehende Nachrichten durchgeführt, die aus dem Internet gesendet, aber nicht authentifiziert wurden. Diese Nachrichten werden als externe Nachrichten behandelt.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfeatures" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Aktivieren oder Deaktivieren der Sender ID

Führen Sie zum Deaktivieren von Sender ID den folgenden Befehl aus:

    Set-SenderIDConfig -Enabled $false

Führen Sie zum Aktivieren von Sender ID den folgenden Befehl aus:

    Set-SenderIDConfig -Enabled $true


> [!NOTE]
> Wenn Sie die Sender&nbsp;ID deaktivieren, bleibt der zugrunde liegende Sender ID-Agent weiterhin aktiviert. Führen Sie den folgenden Befehl aus, um den Sender ID-Agent zu deaktivieren: <CODE>Disable-TransportAgent "Sender ID Agent"</CODE>.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Sender ID erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-SenderIDConfig | Format-List Enabled

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Konfigurieren der Sender ID-Aktion für gefälschte Nachrichten mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Sender ID-Aktion für gefälschte Nachrichten zu konfigurieren:

    Set-SenderIDConfig -SpoofedDomainAction <StampStatus | Reject | Delete>

In diesem Beispiel wird der Sender ID-Agent so konfiguriert, dass alle Nachrichten zurückgewiesen werden, bei denen die IP-Adresse des sendenden Servers nicht als autoritativer SMTP-Server im DNS-SPF-Eintrag (Sender Policy Framework) für die sendende Domäne aufgeführt ist.

    Set-SenderIDConfig -SpoofedDomainAction Reject

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Sender ID-Aktion für gefälschte Nachrichten erfolgreich konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-SenderIDConfig | Format-List SpoofedDomainAction

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Konfigurieren der Sender ID-Aktion für vorübergehende Fehler mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Sender ID-Aktion für vorübergehende Fehler zu konfigurieren:

    Set-SenderIDConfig -TempErrorAction <StampStatus | Reject | Delete>

In diesem Beispiel wird der Sender ID-Agent so konfiguriert, dass Nachrichten gestempelt werden, deren Sender ID-Status aufgrund eines temporären DNS-Serverfehlers nicht ermittelt werden kann. Die Nachricht wird durch weitere Antispam-Agents verarbeitet, und der Inhaltsfilter-Agent verwendet die Markierung beim Ermitteln des SCL-Werts für die Nachricht.

    Set-SenderIDConfig -TempErrorAction StampStatus

Beachten Sie, dass `StampStatus` der Standardwert für den Parameter *TempErrorAction* ist.

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Sender ID-Aktion für vorübergehende Fehler erfolgreich konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-SenderIDConfig | Format-List TempErrorAction

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Konfigurieren von Ausnahmen für Empfänger und Absenderdomänen mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die vorhandenen Werte zu ersetzen:

    Set-SenderIDConfig -BypassedRecipients <recipient1,recipient2...> -BypassedSenderDomains <domain1,domain2...>

In diesem Beispiel wird der Sender ID-Agent so konfiguriert, dass die Überprüfung der Sender ID für an kim@contoso.com und john@contoso.com gesendete Nachrichten sowie für aus der Domäne "fabrikam.com" gesendete Nachrichten umgangen wird.

    Set-SenderIDConfig -BypassedRecipients kim@contoso.com,john@contoso.com -BypassedSenderDomains fabrikam.com

Führen Sie folgenden Befehl aus, um Einträge hinzuzufügen bzw. zu entfernen, ohne vorhandene Werte zu ändern:

    Set-SenderIDConfig -BypassedRecipients @{Add="<recipient1>","<recipient2>"...; Remove="<recipient1>","<recipient2>"...} -BypassedSenderDomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}

In diesem Beispiel wird der Sender ID-Agent mit den folgenden Informationen konfiguriert:

  - chris@contoso.com und michelle@contoso.com werden der Liste der vorhandenen Empfänger hinzugefügt, für die die Überprüfung der Sender ID umgangen wird.

  - tailspintoys.com wird aus der Liste der vorhandenen Domänen entfernt, für die die Überprüfung der Sender ID umgangen wird.

<!-- end list -->

    Set-SenderIDConfig -BypassedRecipients @{Add="chris@contoso.com","michelle@contoso.com"} -BypassedSenderDomains @{Remove="tailspintoys.com"}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um zu überprüfen, ob die Ausnahmen für die Empfänger- und die Absenderdomäne erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-SenderIDConfig | Format-List BypassedRecipients,BypassedSenderDomains

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

