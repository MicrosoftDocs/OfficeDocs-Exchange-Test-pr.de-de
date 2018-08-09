---
title: 'Verw. d. Verbindungsfilterung auf Edge-Transport-Servern: Exchange 2013-Hilfe'
TOCTitle: Verwalten der Verbindungsfilterung auf Edge-Transport-Servern
ms:assetid: baebc865-ec3e-48ca-ac48-7aac8b34c003
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124376(v=EXCHG.150)
ms:contentKeyID: 60828922
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten der Verbindungsfilterung auf Edge-Transport-Servern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Die Verbindungsfilterung ist ein Antispamfeature und erfolgt durch den Verbindungsfilter-Agent, der in Microsoft Exchange 2013 nur auf Edge-Transport-Servern verfügbar ist. Die Verbindungsfilterung bietet die folgenden Funktionen:

  - IP-Sperrliste

  - IP-Sperrlistenanbieter

  - IP-Zulassungsliste

  - Anbieter für zugelassene IP-Adressen

Jede dieser Funktionen kann einzeln aktiviert und deaktiviert werden.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Verbindungsfilterung mithilfe der Shell

Um die Verbindungsfilterung vollständig zu aktivieren oder zu deaktivieren, müssen Sie den Verbindungsfilter-Agent aktivieren bzw. deaktivieren. Die Änderung wird nach einem Neustart des Microsoft Exchange-Transportdiensts wirksam. Während Sie den Microsoft Exchange-Transportdienst auf einem Edge-Transport-Server neu starten, wird der Nachrichtenfluss auf dem Server zeitweise unterbrochen.

Führen Sie zum Deaktivieren der Verbindungsfilterung den folgenden Befehl aus:

    Disable-TransportAgent "Connection Filtering Agent"

Führen Sie zum Aktivieren der Verbindungsfilterung den folgenden Befehl aus:

    Enable-TransportAgent "Connection Filtering Agent"

Damit die Änderung wirksam wird, starten Sie den Microsoft Exchange-Transportdienst mit dem folgenden Befehl neu:

    Restart-Service MSExchangeTransport

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie die Verbindungsfilterung erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-TransportAgent "Connection Filtering Agent" | Format-List Enabled

## Verfahren für IP-Sperrlisten

Diese Verfahren gelten für die IP-Sperrliste, die Sie manuell konfigurieren. Sie gelten nicht für IP-Sperrlistenanbieter.

Mit den Cmdlets **IPBlockListConfig** können Sie anzeigen und konfigurieren, wie die IP-Sperrliste für die Verbindungsfilterung verwendet wird. Mit den Cmdlets **IPBlockListEntry** können Sie die IP-Adressen in der IP-Sperrliste anzeigen und konfigurieren.

## Anzeigen der Konfiguration der IP-Sperrliste mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Konfiguration der IP-Sperrliste anzuzeigen:

    Get-IPBlockListConfig | Format-List *Enabled,*Response

## Aktivieren oder Deaktivieren der IP-Sperrliste mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die IP-Sperrliste zu deaktivieren:

    Set-IPBlockListConfig -Enabled $false

Führen Sie den folgenden Befehl aus, um die IP-Sperrliste zu aktivieren:

    Set-IPBlockListConfig -Enabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie die IP-Sperrliste erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-IPBlockListConfig | Format-List Enabled

## Konfigurieren der IP-Sperrliste mithilfe der Shell

Verwenden Sie folgende Syntax, um die IP-Sperrliste zu konfigurieren.

    Set-IPBlockListConfig [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false> -MachineEntryRejectionResponse "<Custom response text>"] [-StaticEntryRejectionResponse "<Custom response text>"]

Bei diesem Beispiel wird die IP-Sperrliste mit den folgenden Einstellungen konfiguriert:

  - Die IP-Sperrliste filtert von internen und externen Mailservern eingehende Verbindungen. Standardmäßig werden nur von externen Mailservern eingehende Verbindungen gefiltert (*ExternalMailEnabled* ist auf `$true` und *InternalMailEnabled* auf `$false` festgelegt). Nicht authentifizierte Verbindungen und authentifizierte Verbindungen von externen Partnern werden als extern eingestuft.

  - Der benutzerdefinierte Antworttext für Verbindungen, die anhand der IP-Adressen gefiltert wurden, die durch das Feature der Absenderzuverlässigkeit des Protokollanalyse-Agents der IP-Sperrliste hinzugefügt wurden, ist auf "Verbindung von IP-Adresse {0} wurde aufgrund der Absenderzuverlässigkeit abgelehnt" festgelegt.

  - Der benutzerdefinierte Antworttext für Verbindungen, die anhand der IP-Adressen gefiltert wurden, die der IP-Sperrliste manuell hinzugefügt wurden, ist auf "Verbindung von IP-Adresse {0} wurde von der Verbindungsfilterung abgelehnt" festgelegt.

<!-- end list -->

    Set-IPBlockListConfig -InternalMailEnabled $true -MachineEntryRejectionResponse "Connection from IP address {0} was rejected by sender reputation." -StaticEntryRejectionResponse "Connection from IP address {0} was rejected by connection filtering."

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie die IP-Sperrliste erfolgreich konfiguriert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass die angezeigten Werte die von Ihnen konfigurierten Werte sind.

    Get-IPBlockListConfig | Format-List *MailEnabled,*Response

## Verwenden der Shell zum Anzeigen der Einträge in der IP-Sperrliste

Führen Sie den folgenden Befehl aus, um alle Einträge in der IP-Sperrliste anzuzeigen:

    Get-IPBlockListEntry

Jeder Eintrag in der IP-Sperrliste wird durch einen ganzzahligen Wert angegeben. Wenn Sie der IP-Sperr- und IP-Zulassungsliste Einträge hinzufügen, wird die ganze Zahl zur Kennzeichnung in aufsteigender Reihenfolge zugewiesen.

Verwenden Sie die folgende Syntax, um einen bestimmten Eintrag in der IP-Sperrliste anzuzeigen:

    Get-IPBlockListEntry <-Identity IdentityInteger | -IPAddress IPAddress>

Führen Sie z. B. den folgenden Befehl aus, um den Eintrag in der IP-Sperrliste mit der IP-Adresse 192.168.1.13 anzuzeigen:

    Get-IPBlockListEntry -IPAddress 192.168.1.13


> [!NOTE]
> Bei Verwenden des Parameters <EM>IPAddress</EM> kann der resultierende Eintrag in der IP-Sperrliste eine einzelne IP-Adresse, ein IP-Adressbereich oder eine CIDR-IP-Adresse (Classless InterDomain Routing) sein. Zum Verwenden des Parameters <EM>Identity</EM> geben Sie den Ganzzahlwert an, der dem Eintrag der IP-Sperrliste zugewiesen ist.



## Verwenden der Shell zum Hinzufügen von Einträgen zur IP-Sperrliste

Verwenden Sie folgende Syntax, um der IP-Sperrliste Einträge hinzuzufügen:

    Add-IPBlockListEntry <-IPAddress IPAddress | -IPRange IP range or CIDR IP> [-ExpirationTime <DateTime>] [-comment "<Descriptive Comment>"]

Das folgende Beispiel fügt den IP-Sperrlisteneintrag für den IP-Adressbereich 192.168.1.10 bis 192.168.1.15 hinzu und konfiguriert den IP-Sperrlisteneintrag für einen Ablauf am 4. Juli 2014 um 15:00 Uhr.

    Add-IPBlockListEntry -IPRange 192.168.1.10-192.168.1.15 -ExpirationTime "7/4/2014 15:00"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Sperrlisteneintrag erfolgreich hinzugefügt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der IP-Sperrlisteneintrag angezeigt wird.

    Get-IPBlockListEntry

## Verwenden der Shell zum Entfernen von Einträgen aus der IP-Sperrliste

Verwenden Sie folgende Syntax, um aus der IP-Sperrliste Einträge zu entfernen:

    Remove-IPBlockListEntry <IdentityInteger>

Im folgenden Beispiel wird der IP-Sperrlisteneintrag mit dem Wert 3 für *Identity* entfernt.

    Remove-IPBlockListEntry 3

Im folgenden Beispiel wird der IP-Sperrlisteneintrag mit der IP-Adresse 192.168.1.12 entfernt, ohne den Ganzzahlwert von *Identity* zu verwenden. Ein IP-Sperrlisteneintrag kann eine einzelne IP-Adresse oder ein IP-Adressbereich sein.

    Get-IPBlockListEntry -IPAddress 192.168.1.12 | Remove-IPBlockListEntry

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Sperrlisteneintrag erfolgreich entfernt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der IP-Sperrlisteneintrag, den Sie entfernt haben, nicht mehr vorhanden ist.

    Get-IPBlockListEntry

## Verfahren für IP-Sperrlistenanbieter

Diese Verfahren gelten für IP-Sperrlistenanbieter. Sie gelten nicht für die IP-Sperrliste.

Mit den Cmdlets **IPBlockListProvidersConfig** können Sie anzeigen und konfigurieren, wie alle IP-Sperrlistenanbieter für die Verbindungsfilterung verwendet werden. Mit den Cmdlets **IPBlockListProvider** können Sie IP-Sperrlistenanbieter anzeigen, konfigurieren und testen.

## Anzeigen der Konfiguration aller IP-Sperrlistenanbieter mithilfe der Shell

Führen Sie den folgenden Befehl aus, um anzuzeigen, wie für die Verbindungsfilterung alle IP-Sperrlistenanbieter verwendet werden:

    Get-IPBlockListProvidersConfig | Format-List *Enabled,Bypassed*

## Aktivieren oder Deaktivieren aller IP-Sperrlistenanbieter mithilfe der Shell

Führen Sie den folgenden Befehl aus, um alle IP-Sperrlistenanbieter zu deaktivieren:

    Set-IPBlockListProvidersConfig -Enabled $false

Führen Sie den folgenden Befehl aus, um alle IP-Sperrlistenanbieter zu aktivieren:

    Set-IPBlockListProvidersConfig -Enabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie alle IP-Sperrlistenanbieter erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-IPBlockListProvidersConfig | Format-List Enabled

## Konfigurieren aller IP-Sperrlistenanbieter mithilfe der Shell

Verwenden Sie die folgende Syntax, um zu konfigurieren, wie für die Verbindungsfilterung alle IP-Sperrlistenanbieter verwendet werden:

    Set-IPBlockListProvidersConfig [-BypassedRecipients <recipient1,recipient2...>] [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false>]

Bei diesem Beispiel werden alle IP-Sperrlistenanbieter mit den folgenden Einstellungen konfiguriert:

  - IP-Sperrlistenanbieter filtern von internen und externen Mailservern eingehende Verbindungen. Standardmäßig werden nur von externen Mailservern eingehende Verbindungen gefiltert (*ExternalMailEnabled* ist auf `$true` und *InternalMailEnabled* auf `$false` festgelegt). Nicht authentifizierte Verbindungen und authentifizierte Verbindungen von externen Partnern werden als extern eingestuft.

  - Von den internen Empfängern chris@fabrikam.com und michelle@fabrikam.com gesendete Nachrichten sind von der Filterung durch IP-Sperrlistenanbieter ausgeschlossen. Wenn Sie der Liste Empfänger ohne Auswirkungen auf vorhandene Empfänger hinzufügen möchten, wählen Sie die Syntax `@{Add="<recipient1>","<recipient2>"...}`.

<!-- end list -->

    Set-IPBlockListProvidersConfig -BypassedRecipients chris@fabrikam.com,michelle@fabrikam.com -InternalMailEnabled $true

Weitere Informationen finden Sie unter [Set-IPBlockListProvidersConfig](https://technet.microsoft.com/de-de/library/aa998543\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie alle IP-Sperrlistenanbieter erfolgreich konfiguriert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass die angezeigten Werte die von Ihnen konfigurierten Werte sind.

    Get-IPBlockListProvidersConfig | Format-List *MailEnabled,Bypassed*

## Verwenden der Shell zum Anzeigen aller IP-Sperrlistenbieter

Führen Sie den folgenden Befehl aus, um die Übersichtsliste aller IP-Sperrlistenanbieter anzuzeigen:

    Get-IPBlockListProvider

Verwenden Sie die folgende Syntax, um die Details eines bestimmten Anbieters anzuzeigen:

    Get-IPBlockListProvider <IPBlockListProviderIdentity>

Das folgende Beispiel zeigt die Details des Anbieters Contoso IP Block List Provider.

    Get-IPBlockListProvider "Contoso IP Block List Provider" | Format-List Name,Enabled,Priority,LookupDomain,*Match,*Response

## Verwenden der Shell zum Hinzufügen eines IP-Sperrlistenbieters

Verwenden Sie folgende Syntax, um einen IP-Sperrlistenanbieter hinzuzufügen:

    Add-IPBlockListProvider -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-Enabled <$true | $false>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>] [-RejectionResponse "<Custom Text>"]

Bei diesem Beispiel wird der IP-Sperrlistenanbieter "Contoso IP Block List Provider" mit den folgenden Optionen erstellt:

  - **FQDN zum Verwenden des Anbieters**   rbl.contoso.com

  - **Vom Anbieter angegebener zu verwendender Bitmaskencode**   127.0.0.1

<!-- end list -->

    Add-IPBlockListProvider -Name "Contoso IP Block List Provider" -LookupDomain rbl.contoso.com -BitmaskMatch 127.0.0.1


> [!NOTE]
> Wenn Sie einen neuen IP-Sperrlistenanbieter hinzufügen, ist dieser standardmäßig aktiviert (der Wert <EM>Enabled</EM> ist <CODE>$true</CODE>), und der Prioritätswert wird erhöht (der erste Wert von <EM>Priority</EM> ist 1).



Weitere Informationen finden Sie unter [Add-IPBlockListProvider](https://technet.microsoft.com/de-de/library/bb124358\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Sperrlistenanbieter erfolgreich hinzugefügt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der IP-Sperrlistenanbieter angezeigt wird.

    Get-IPBlockListProvider

## Aktivieren oder Deaktivieren eines IP-Sperrlistenanbieters mithilfe der Shell

Verwenden Sie die folgende Syntax, um einen bestimmten IP-Sperrlistenanbieter zu aktivieren oder zu deaktivieren:

    Set-IPBlockListProvider <IPBlockListProviderIdentity> -Enabled <$true | $false>

Das folgende Beispiel deaktiviert den Anbieter Contoso IP Block List Provider.

    Set-IPBlockListProvider "Contoso IP Block List Provider" -Enabled $false

Das folgende Beispiel aktiviert den Anbieter Contoso IP Block List Provider.

    Set-IPBlockListProvider "Contoso IP Block List Provider" -Enabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Sperrlistenanbieter erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-IPBlockListProvider <IPBlockListProviderIdentity> | Format-List Enabled

## Verwenden der Shell zum Konfigurieren eines IP-Sperrlistenbieters

Die Konfigurationsoptionen, die für das Cmdlet **Set-IPBlockListProvider** zur Verfügung stehen, entsprechen denen für das Cmdlet **New-IPBlockListProvider**.

Verwenden Sie folgende Syntax, um einen vorhandenen IP-Sperrlistenanbieter zu konfigurieren:

    Set-IPBlockListProvider <IPBlockListProviderIdentity> -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>] [-RejectionResponse "<Custom Text>"]

Führen Sie beispielsweise den folgenden Befehl aus, um den IP-Adressstatuscode 127.0.0.1 der Liste der vorhandenen Statuscodes für den Anbieter Contoso IP Block List Provider hinzuzufügen:

    Set-IPBlockListProvider "Contoso IP Block List Provider" -IPAddressesMatch @{Add="127.0.0.1"}

Weitere Informationen finden Sie unter [Set-IPBlockListProvider](https://technet.microsoft.com/de-de/library/bb124979\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Sperrlistenanbieter erfolgreich konfiguriert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass die angezeigten Werte die von Ihnen konfigurierten Werte sind.

    Get-IPBlockListProvider <IPBlockListProviderIdentity> | Format-List

## Verwenden der Shell zum Testen eines IP-Sperrlistenbieters

Verwenden Sie folgende Syntax, um einen IP-Sperrlistenanbieter zu testen:

    Test-IPBlockListProvider <IPBlockListProviderIdentity> -IPAddress <IPAddressToTest>

Das folgende Beispiel testet den Anbieter Contoso IP Block List Provider, indem die IP-Adresse 192.168.1.1 nachgeschlagen wird.

    Test-IPBlockListProvider "Contoso IP Block List Provider" -IPAddress 192.168.1.1

## Verwenden der Shell zum Entfernen eines IP-Sperrlistenbieters

Verwenden Sie folgende Syntax, um einen IP-Sperrlistenanbieter zu entfernen:

    Remove-IPBlockListProvider <IPBlockListProviderIdentity>

Das folgende Beispiel entfernt den IP-Sperrlistenanbieter Contoso IP Block List Provider.

    Remove-IPBlockListProvider "Contoso IP Block list Provider"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Sperrlistenanbieter erfolgreich entfernt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der IP-Sperrlistenanbieter, den Sie entfernt haben, nicht mehr vorhanden ist.

    Get-IPBlockListProvider

## Verfahren für IP-Zulassungslisten

Diese Verfahren gelten für die IP-Zulassungsliste, die Sie manuell konfigurieren. Sie gelten nicht für Anbieter für zugelassene IP-Adressen.

Mit den Cmdlets **IPAllowListConfig** können Sie anzeigen und konfigurieren, wie die IP-Zulassungsliste für die Verbindungsfilterung verwendet wird. Mit den Cmdlets **IPAllowListEntry** können Sie die IP-Adressen in der IP-Zulassungsliste anzeigen und konfigurieren.

## Anzeigen der Konfiguration der IP-Zulassungsliste mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die Konfiguration der IP-Zulassungsliste anzuzeigen:

    Get-IPAllowListConfig | Format-List *Enabled

## Aktivieren oder Deaktivieren der IP-Zulassungsliste mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die IP-Zulassungsliste zu deaktivieren:

    Set-IPAllowListConfig -Enabled $false

Führen Sie den folgenden Befehl aus, um die IP-Zulassungsliste zu aktivieren:

    Set-IPAllowListConfig -Enabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie die IP-Zulassungsliste erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-IPAllowListConfig | Format-List Enabled

## Konfigurieren der IP-Zulassungsliste mithilfe der Shell

Verwenden Sie folgende Syntax, um die IP-Zulassungsliste zu konfigurieren.

    Set-IPAllowListConfig [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false>

Bei diesem Beispiel wird die IP-Zulassungsliste so konfiguriert, dass von internen und externen Mailservern eingehende Verbindungen gefiltert werden. Standardmäßig werden nur von externen Mailservern eingehende Verbindungen gefiltert (*ExternalMailEnabled* ist auf `$true` und *InternalMailEnabled* auf `$false` festgelegt). Nicht authentifizierte Verbindungen und authentifizierte Verbindungen von externen Partnern werden als extern eingestuft.

    Set-IPAllowListConfig -InternalMailEnabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie die IP-Zulassungsliste erfolgreich konfiguriert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass die angezeigten Werte die von Ihnen konfigurierten Werte sind.

    Get-IPAllowListConfig | Format-List *MailEnabled

## Verwenden der Shell zum Anzeigen der Einträge in der IP-Zulassungsliste

Führen Sie den folgenden Befehl aus, um alle Einträge in der IP-Zulassungsliste anzuzeigen:

    Get-IPAllowListEntry

Jeder Eintrag in der IP-Zulassungsliste wird durch einen ganzzahligen Wert angegeben. Wenn Sie der IP-Sperr- und IP-Zulassungsliste Einträge hinzufügen, wird die ganze Zahl zur Kennzeichnung in aufsteigender Reihenfolge zugewiesen.

Verwenden Sie die folgende Syntax, um einen bestimmten Eintrag in der IP-Zulassungsliste anzuzeigen:

    Get-IPAllowListEntry <-Identity IdentityInteger | -IPAddress IPAddress>

Führen Sie z. B. den folgenden Befehl aus, um den Eintrag in der IP-Zulassungsliste mit der IP-Adresse 192.168.1.13 anzuzeigen:

    Get-IPAllowListEntry -IPAddress 192.168.1.13


> [!NOTE]
> Bei Verwenden des Parameters <EM>IPAddress</EM> kann der resultierende Eintrag in der IP-Zulassungsliste eine einzelne IP-Adresse, ein IP-Adressbereich oder eine CIDR-IP-Adresse (Classless InterDomain Routing) sein. Zum Verwenden des Parameters <EM>Identity</EM> geben Sie den Ganzzahlwert an, der dem Eintrag der IP-Zulassungsliste zugewiesen ist.



## Verwenden der Shell zum Hinzufügen von Einträgen zur IP-Zulassungsliste

Verwenden Sie folgende Syntax, um der IP-Zulassungsliste Einträge hinzuzufügen:

    Add-IPAllowListEntry <-IPAddress IPAddress | -IPRange IP range or CIDR IP> [-ExpirationTime <DateTime>] [-Comment "<Descriptive Comment>"]

Dieses Beispiel fügt den IP-Zulassungslisteneintrag für den IP-Adressbereich 192.168.1.10 bis 192.168.1.15 hinzu und konfiguriert den IP-Zulassungslisteneintrag für einen Ablauf am 4. Juli 2014 um 15:00 Uhr.

    Add-IPAllowListEntry -IPRange 192.168.1.10-192.168.1.15 -ExpirationTime "7/4/2014 15:00"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Zulassungslisteneintrag erfolgreich hinzugefügt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der IP-Zulassungslisteneintrag angezeigt wird.

    Get-IPAllowListEntry

## Verwenden der Shell zum Entfernen der Einträge aus der IP-Zulassungsliste

Verwenden Sie folgende Syntax, um Einträge aus der IP-Zulassungsliste zu entfernen:

    Remove-IPAllowListEntry <IdentityInteger>

Im folgenden Beispiel wird der IP-Zulassungslisteneintrag mit dem Wert 3 für *Identity* entfernt.

    Remove-IPAllowListEntry 3

Im folgenden Beispiel wird der IP-Zulassungslisteneintrag mit der IP-Adresse 192.168.1.12 entfernt, ohne den Ganzzahlwert von *Identity* zu verwenden. Ein IP-Zulassungslisteneintrag kann eine einzelne IP-Adresse oder ein IP-Adressbereich sein.

    Get-IPAllowListEntry -IPAddress 192.168.1.12 | Remove-IPAllowListEntry

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen IP-Zulassungslisteneintrag erfolgreich entfernt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der IP-Zulassungslisteneintrag, den Sie entfernt haben, nicht mehr vorhanden ist.

    Get-IPAllowListEntry

## Verfahren für Anbieter für zugelassene IP-Adressen

Sie gelten für Anbieter für zugelassene IP-Adressen. Sie gelten nicht für die IP-Zulassungsliste.

Mit den Cmdlets **IPAllowListProvidersConfig** können Sie anzeigen und konfigurieren, wie alle Anbieter für zugelassene IP-Adressen für die Verbindungsfilterung verwendet werden. Mit den Cmdlets **IPAllowListProvider** können Sie Anbieter für zugelassene IP-Adressen anzeigen, konfigurieren und testen.

## Anzeigen der Konfiguration aller Anbieter für zugelassene IP-Adressen mithilfe der Shell

Führen Sie den folgenden Befehl aus, um anzuzeigen, wie für die Verbindungsfilterung alle Anbieter für zugelassene IP-Adressen verwendet werden:

    Get-IPAllowListProvidersConfig | Format-List *Enabled

## Aktivieren oder Deaktivieren aller Anbieter für zugelassene IP-Adressen mithilfe der Shell

Führen Sie den folgenden Befehl aus, um alle Anbieter für zugelassene IP-Adressen zu deaktivieren:

    Set-IPAllowListProvidersConfig -Enabled $false

Führen Sie den folgenden Befehl aus, um alle Anbieter für zugelassene IP-Adressen zu aktivieren:

    Set-IPAllowListProvidersConfig -Enabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie alle Anbieter für zugelassene IP-Adressen erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-IPAllowListProvidersConfig | Format-List Enabled

## Konfigurieren aller Anbieter für zugelassene IP-Adressen mithilfe der Shell

Verwenden Sie die folgende Syntax, um zu konfigurieren, wie für die Verbindungsfilterung alle Anbieter für zugelassene IP-Adressen verwendet werden:

    Set-IPAllowListProvidersConfig [-ExternalMailEnabled <$true | $false>] [-InternalMailEnabled <$true | $false>]

Bei diesem Beispiel werden alle Anbieter für zugelassene IP-Adressen so konfiguriert, dass von internen und externen Mailservern eingehende Verbindungen gefiltert werden. Standardmäßig werden nur von externen Mailservern eingehende Verbindungen gefiltert (*ExternalMailEnabled* ist auf `$true` und *InternalMailEnabled* auf `$false` festgelegt). Nicht authentifizierte Verbindungen und authentifizierte Verbindungen von externen Partnern werden als extern eingestuft.

    Set-IPAllowListProvidersConfig -InternalMailEnabled $true

Weitere Informationen finden Sie unter [Set-IPBlockListProvidersConfig](https://technet.microsoft.com/de-de/library/aa998543\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie alle Anbieter für zugelassene IP-Adressen erfolgreich konfiguriert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass die angezeigten Werte die von Ihnen konfigurierten Werte sind.

    Get-IPAllowListProvidersConfig | Format-List *MailEnabled

## Verwenden der Shell zum Anzeigen aller Anbieter für zugelassene IP-Adressen

Führen Sie den folgenden Befehl aus, um die Übersichtsliste aller Anbieter für zugelassene IP-Adressen anzuzeigen:

    Get-IPAllowListProvider

Verwenden Sie die folgende Syntax, um die Details eines bestimmten Anbieters anzuzeigen:

    Get-IPAllowListProvider <IPAllowListProviderIdentity>

Dieses Beispiel zeigt die Details des Anbieters Contoso IP Allow List Provider.

    Get-IPAllowListProvider "Contoso IP Allow List Provider" | Format-List Name,Enabled,Priority,LookupDomain,*Match

## Verwenden der Shell zum Hinzufügen eines Anbieters für zugelassene IP-Adressen

Verwenden Sie folgende Syntax, um einen Anbieter für zugelassene IP-Adressen hinzuzufügen:

    Add-IPAllowListProvider -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-Enabled <$true | $false>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>]

Bei diesem Beispiel wird der Anbieter für zugelassene IP-Adressen "Contoso IP Allow List Provider" mit den folgenden Optionen erstellt:

  - **FQDN zum Verwenden des Anbieters**   allow.contoso.com

  - **Vom Anbieter angegebener zu verwendender Bitmaskencode**   127.0.0.1

<!-- end list -->

    Add-IPAllowListProvider -Name "Contoso IP Allow List Provider" -LookupDomain allow.contoso.com -BitmaskMatch 127.0.0.1


> [!NOTE]
> Wenn Sie einen neuen Anbieter für zugelassene IP-Adressen hinzufügen, ist dieser standardmäßig aktiviert (der Wert <EM>Enabled</EM> ist <CODE>$true</CODE>), und der Prioritätswert wird erhöht (der erste Wert von <EM>Priority</EM> ist 1).



Weitere Informationen finden Sie unter [Add-IPBlockListProvider](https://technet.microsoft.com/de-de/library/bb124358\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen Anbieter für zugelassene IP-Adressen erfolgreich hinzugefügt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der Anbieter für zugelassene IP-Adressen angezeigt wird.

    Get-IPAllowListProvider

## Aktivieren oder Deaktivieren eines Anbieters für zugelassene IP-Adressen mithilfe der Shell

Verwenden Sie die folgende Syntax, um einen bestimmten Anbieter für zugelassene IP-Adressen zu aktivieren oder zu deaktivieren:

    Set-IPAllowListProvider <IPAllowListProviderIdentity> -Enabled <$true | $false>

Das folgende Beispiel deaktiviert den Anbieter Contoso IP Allow List Provider.

    Set-IPAllowListProvider "Contoso IP Allow List Provider" -Enabled $false

Das folgende Beispiel aktiviert den Anbieter Contoso IP Allow List Provider.

    Set-IPAllowListProvider "Contoso IP Allow List Provider" -Enabled $true

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen Anbieter für zugelassene IP-Adressen erfolgreich aktiviert oder deaktiviert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der angezeigte Wert der von Ihnen konfigurierte Wert ist.

    Get-IPAllowListProvider <IPAllowListProviderIdentity> | Format-List Enabled

## Verwenden der Shell zum Konfigurieren eines Anbieters für zugelassene IP-Adressen

Die Konfigurationsoptionen, die für das Cmdlet **Set-IPAllowListProvider** zur Verfügung stehen, entsprechen denen für das Cmdlet **New-IPAllowListProvider**.

Verwenden Sie folgende Syntax, um einen vorhandenen Anbieter für zugelassene IP-Adressen zu konfigurieren:

    Set-IPAllowListProvider <IPAllowListProviderIdentity> -Name "<Descriptive Name>" -LookupDomain <FQDN> [-Priority <Integer>] [-AnyMatch <$true | $false>] [-BitmaskMatch <IPAddress>] [-IPAddressesMatch <IPAddressStatusCode1,IPAddressStatusCode2...>]

Führen Sie beispielsweise den folgenden Befehl aus, um den IP-Adressstatuscode 127.0.0.1 der Liste der vorhandenen Statuscodes für den Anbieter Contoso IP Allow List Provider hinzuzufügen:

    Set-IPAllowListProvider "Contoso IP Allow List Provider" -IPAddressesMatch @{Add="127.0.0.1"}

Weitere Informationen finden Sie unter [Set-IPBlockListProvider](https://technet.microsoft.com/de-de/library/bb124979\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen Anbieter für zugelassene IP-Adressen erfolgreich konfiguriert haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass die angezeigten Werte die von Ihnen konfigurierten Werte sind.

    Get-IPAllowListProvider <IPAllowListProviderIdentity> | Format-List

## Verwenden der Shell zum Testen eines Anbieters für zugelassene IP-Adressen

Verwenden Sie folgende Syntax, um einen Anbieter für zugelassene IP-Adressen zu testen:

    Test-IPAllowListProvider <IPAllowListProviderIdentity> -IPAddress <IPAddressToTest>

Das folgende Beispiel testet den Anbieter Contoso IP Allow List Provider, indem die IP-Adresse 192.168.1.1 nachgeschlagen wird.

    Test-IPAllowListProvider "Contoso IP Allow List Provider" -IPAddress 192.168.1.1

## Verwenden der Shell zum Entfernen eines Anbieters für zugelassene IP-Adressen

Verwenden Sie folgende Syntax, um einen Anbieter für zugelassene IP-Adressen zu entfernen:

    Remove-IPAllowListProvider <IPAllowListProviderIdentity>

Dieses Beispiel entfernt den Anbieter für zugelassene IP-Adressen Contoso IP Allow List Provider.

    Remove-IPAllowListProvider "Contoso IP Allow List Provider"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Zum Bestätigen, dass Sie einen Anbieter für zugelassene IP-Adressen erfolgreich entfernt haben, führen Sie den folgenden Befehl aus, und vergewissern Sie sich, dass der Anbieter für zugelassene IP-Adressen, den Sie entfernt haben, nicht mehr vorhanden ist.

    Get-IPAllowListProvider

