---
title: 'Verwalten der Empfängerfilterung auf Edge-Transport-Servern: Exchange 2013 Help'
TOCTitle: Verwalten der Empfängerfilterung auf Edge-Transport-Servern
ms:assetid: f2d0041f-2872-4669-95ec-443233f4956d
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb125187(v=EXCHG.150)
ms:contentKeyID: 50477065
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Empfängerfilterung auf Edge-Transport-Servern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Empfängerfilterung wird durch den Empfängerfilter-Agent bereitgestellt. Wenn die Empfängerfilterung auf einem Exchange-Server aktiviert ist, werden eingehende Nachrichten gefiltert, die aus dem Internet stammen und nicht authentifiziert sind. Diese Nachrichten werden als externe Nachrichten behandelt.


> [!NOTE]
> Obwohl der Empfängerfilter-Agent auf Postfachservern verfügbar ist, sollten Sie ihn nicht konfigurieren. Wenn ein Empfängerfilter auf einem Postfachserver einen ungültigen oder gesperrten Empfänger in einer Nachricht entdeckt, die andere gültige Empfänger enthält, wird die Nachricht zurückgewiesen. Wenn Sie die Anti-Spam-Agents auf einem Postfachserver installieren, wird der Empfängerfilter-Agent standardmäßig aktiviert. Er wird aber nicht zum Sperren von Empfängern konfiguriert. Weitere Informationen finden Sie unter <A href="enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md">Aktivieren der Antispamfunktionen auf einem Postfachserver</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Der Parameter *AddressBookEnabled* des Cmdlets **Set-AcceptedDomain** aktiviert oder deaktiviert die Empfängerfilterung für Empfänger in einer akzeptierten Domäne. Die Empfängerfilterung ist standardmäßig für autoritative Domänen aktiviert und für interne sowie externe Relaydomänen deaktiviert. Führen Sie den folgenden Befehl aus, um den Status des Parameters *AddressBookEnabled* für die akzeptierten Domänen in Ihrer Organisation anzuzeigen:
    
        Get-AcceptedDomain | Format-List Name,AddressBookEnabled

  - Wenn Sie die Empfängerfilterung mithilfe des Verfahrens in diesem Thema deaktivieren, werden die Funktionen zur Empfängerfilterung deaktiviert, aber der zugrunde liegende Empfängerfilter-Agent bleibt aktiviert.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Empfängerfilterung mithilfe der Shell

Führen Sie zum Deaktivieren der Empfängerfilterung folgenden Befehl aus:

    Set-RecipientFilterConfig -Enabled $false

Führen Sie zum Aktivieren der Empfängerfilterung folgenden Befehl aus:

    Set-RecipientFilterConfig -Enabled $true


> [!NOTE]
> Wenn Sie die Empfängerfilterung deaktivieren, ist der zugrunde liegende Empfängerfilter-Agent weiterhin aktiviert. Führen Sie den folgenden Befehl aus, um den Empfängerfilter-Agent zu deaktivieren: <CODE>Disable-TransportAgent "Recipient Filter Agent"</CODE>.



## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Empfängerfilterung erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-RecipientFilterConfig | Format-List Enabled

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Aktivieren oder Deaktivieren der Empfängersperrliste mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Set-RecipientFilterConfig -BlockListEnabled <$true | $false>

In diesem Beispiel wird die Empfängersperrliste aktiviert:

    Set-RecipientFilterConfig -BlockListEnabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Empfängersperrliste erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-RecipientFilterConfig | Format-List BlockListEnabled

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Konfigurieren der Empfängersperrliste mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die vorhandenen Werte zu ersetzen:

    Set-RecipientFilterConfig -BlockedRecipients <recipient1,recipient2...>

In diesem Beispiel wird die Empfängersperrliste mit "valuesmark@contoso.com" und "kim@contoso.com" konfiguriert:

    Set-RecipientFilterConfig -BlockedRecipients mark@contoso.com,kim@contoso.com

Führen Sie folgenden Befehl aus, um Einträge hinzuzufügen bzw. zu entfernen, ohne vorhandene Werte zu ändern:

    Set-RecipientFilterConfig -BlockedRecipients @{Add="<recipient1>","<recipient2>"...; Remove="<recipient1>","<recipient2>"...}

In diesem Beispiel wird "chris@contoso.com" zur Empfängerliste hinzugefügt und "michelle@contoso.com" aus der Liste der Empfänger in der Empfängersperrliste entfernt:

    Set-RecipientFilterConfig -BlockedRecipients @{Add="chris@contoso.com"; Remove="michelle@contoso.com"}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Empfängersperrliste erfolgreich konfiguriert haben:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-RecipientFilterConfig | Format-List BlockedRecipients

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Aktivieren oder Deaktivieren der Empfängersuche mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Set-RecipientFilterConfig -RecipientValidationEnabled <$true | $false>

Führen Sie den folgenden Befehl aus, um Nachrichten an Empfänger, die in der Organisation nicht vorhanden sind, zu sperren:

    Set-RecipientFilterConfig -RecipientValidationEnabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Führen Sie die folgenden Aktionen aus, um zu überprüfen, ob Sie die Empfängersuche erfolgreich aktiviert oder deaktiviert haben:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-RecipientFilterConfig | Format-List RecipientValidationEnabled

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

