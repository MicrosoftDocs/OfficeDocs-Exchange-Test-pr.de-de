---
title: 'Verw. d. Adressumschreibung auf Edge-Transport-Servern: Exchange 2013-Hilfe'
TOCTitle: Verwalten der Adressumschreibung auf Edge-Transport-Servern
ms:assetid: 323a0b55-f921-425d-b1b0-18ad0fac315c
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa997185(v=EXCHG.150)
ms:contentKeyID: 61061219
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten der Adressumschreibung auf Edge-Transport-Servern

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2015-04-08_

Sie können die Exchange-Verwaltungsshell auf einem Edge-Transport-Server für alle Verwaltungsaufgaben in Bezug auf das Umschreiben von Adressen und Adressumschreibungs-Agents verwenden. Weitere Informationen zum Umschreiben von Adressen finden Sie unter [Adressumschreibung auf Edge-Transport-Servern](address-rewriting-on-edge-transport-servers-exchange-2013-help.md).

Sie können Einträge für das Umschreiben von Adressen, die für einen einzelnen Empfänger, für alle Empfänger in einer bestimmten Domäne oder Unterdomäne oder für alle Empfänger in mehreren Unterdomänen gelten, erstellen. Die Adressumschreibung kann ausgehend oder ein- und ausgehend (bidirektional) sein. Wenn Sie Einträge zum Umschreiben von Adressen erstellen, beachten Sie Folgendes:

  - Stellen Sie sicher, dass die sich ergebenden E-Mail-Adressen in Ihrer Organisation eindeutig sind.

  - Nur Literalzeichenfolgen werden in den E-Mail-Adresswerten unterstützt.

  - Das Platzhalterzeichen (\*) wird nur in den internen Adressen (den zu ändernden Adressen) unterstützt. Die gültige Syntax zur Verwendung des Platzhalterzeichens ist **\*.contoso.com**. Die Werte **\*contoso.com** oder **sales.\*.com** sind nicht zulässig.

  - Wenn Sie ein Platzhalterzeichen verwenden, müssen Sie die Adressumschreibung als "Nur ausgehend" konfigurieren (setzen Sie den Parameter *OutboundOnly* auf den Wert `$true`).

  - Wenn Sie eine Adressumschreibung als "Nur ausgehend" konfigurieren (den Parameter *OutboundOnly* auf den Wert `$true` setzen), müssen Sie die Proxyadressen der betroffenen Empfänger konfigurieren. Dadurch wird sichergestellt, dass die an die umgeschriebene E-Mail-Adresse gesendeten E-Mails ordnungsgemäß zugestellt werden.

  - Standardmäßig ist die Adressumschreibung für einzelne Empfänger oder alle Empfänger in einer bestimmten Domäne bzw. Unterdomäne bidirektional (der Standardwert für den Parameter *OutboundOnly* ist `$false`).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 10 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Edge-Transport-Server" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Gehen Sie beim Konfigurieren der Adressumschreibung sorgfältig vor. Alle Änderungen, die Sie vornehmen, werden sofort wirksam, wenn der Befehl ausgeführt wird. Führen Sie den Befehl ggf. mit dem Parameter *WhatIf* aus. Weitere Informationen zum Parameter *WhatIf* finden Sie unter [Optionen "WhatIf", "Confirm" und "ValidateOnly"](whatif-confirm-and-validateonly-switches-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Aktivieren oder Deaktivieren der Adressumschreibung mithilfe der Shell

Um die Adressumschreibung komplett zu aktivieren oder zu deaktivieren, müssen Sie die Adressumschreibungs-Agents aktivieren bzw. deaktivieren. Die Adressumschreibungs-Agents sind auf Edge-Transport-Servern standardmäßig aktiviert.

Führen Sie die folgenden Befehle aus, um die Adressumschreibung zu deaktivieren:

    Disable-TransportAgent "Address Rewriting Inbound Agent"
    Disable-TransportAgent "Address Rewriting Outbound Agent"

Führen Sie die folgenden Befehle aus, um die Adressumschreibung zu aktivieren:

    Enable-TransportAgent "Address Rewriting Inbound Agent"
    Enable-TransportAgent "Address Rewriting Outbound Agent"

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die Adressumschreibung erfolgreich aktiviert oder deaktiviert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
    ```powershell
Get-TransportAgent
```

2.  Überprüfen Sie, ob die Werte der Eigenschaft **Enabled** für den eingehenden Adressumschreibungs-Agent und den ausgehenden Adressumschreibungs-Agent den von Ihnen konfigurierten Werten entsprechen.

## Verwenden der Shell zum Anzeigen der Adressumschreibungseinträge

Führen Sie zum Anzeigen einer Zusammenfassungsliste aller Adressumschreibungseinträge den folgenden Befehl aus:

```powershell
Get-AddressRewriteEntry
```

Verwenden Sie die folgende Syntax, um die Details eines Adressumschreibungseintrags anzuzeigen:

```powershell
Get-AddressRewriteEntry <AddressRewriteEntryIdentity> | Format-List
```

Im folgenden Beispiel werden die Details des Adressumschreibungseintrags "Rewrite Contoso.com to Northwindtraders.com" angezeigt:

```powershell
Get-AddressRewriteEntry "Rewrite Contoso.com to Northwindtraders.com" | Format-List
```

## Verwenden der Shell zum Erstellen von Adressumschreibungseinträgen

## Umschreiben der E-Mail-Adressen von einzelnen Empfängern

Verwenden Sie folgende Syntax, um die E-Mail-Adresse eines einzelnen Empfängers umzuschreiben:

    New-AddressRewriteEntry -Name "<Descriptive Name>" -InternalAddress <internal email address> -ExternalAddress <external email address> [-OutboundOnly <$true | $false>]

Im folgenden Beispiel wird die E-Mail-Adresse aller Nachrichten umgeschrieben, die in der Exchange-Organisation für den Empfänger "joe@contoso.com" ein- und ausgehen. Ausgehende Nachrichten werden so umgeschrieben, dass sie scheinbar von "support@nortwindtraders.com" kommen. Eingehende Nachrichten, die an "support@northwindtraders.com" gesendet wurden, werden zur Lieferung an den Empfänger in "joe@contoso.com" umgeschrieben (der Parameter *OutboundOnly* ist standardmäßig `$false`).

    New-AddressRewriteEntry -Name "joe@contoso.com to support@northwindtraders.com" -InternalAddress joe@contoso.com -ExternalAddress support@northwindtraders.com

## Umschreiben von E-Mail-Adressen für Empfänger in einer bestimmten Domäne oder Unterdomäne

Verwenden Sie folgende Syntax, um die E-Mail-Adressen für Empfänger in einer bestimmten Domäne oder Unterdomäne umzuschreiben:

    New-AddressRewriteEntry -Name "<Descriptive Name>" -InternalAddress <domain or subdomain> -ExternalAddress <domain> [-OutboundOnly <$true | $false>]

Im folgenden Beispiel werden die E-Mail-Adressen aller Nachrichten umgeschrieben, die in der Exchange-Organisation für Empfänger in der Domäne "contoso.com" ein- und ausgehen. Ausgehende Nachrichten werden so umgeschrieben, dass sie scheinbar von der Domäne "fabrikam.com" kommen. Eingehende Nachrichten, die an E-Mail-Adressen unter "fabrikam.com" gesendet wurden, werden zur Lieferung an die Empfänger in "contoso.com" umgeschrieben (der Parameter *OutboundOnly* ist standardmäßig `$false`).

    New-AddressRewriteEntry -Name "Contoso to Fabrikam" -InternalAddress contoso.com -ExternalAddress fabrikam.com

Im folgenden Beispiel werden die E-Mail-Adressen aller ausgehenden Nachrichten in der Exchange-Organisation umgeschrieben, die von Empfängern in der Unterdomäne "sales.contoso.com" gesendet wurden. Ausgehende Nachrichten werden so umgeschrieben, dass sie scheinbar von der Domäne "contoso.com" kommen. Eingehende Nachrichten an die E-Mail-Adressen unter "contoso.com" werden nicht umgeschrieben.

    New-AddressRewriteEntry -Name "sales.contoso.com to contoso.com" -InternalAddress sales.contoso.com -ExternalAddress contoso.com -OutboundOnly $true

## Umschreiben von E-Mail-Adressen für Empfänger in mehreren Unterdomänen

Verwenden Sie folgende Syntax, um die E-Mail-Adressen für Empfänger in einer Domäne und allen ihren Unterdomänen umzuschreiben:

    New-AddressRewriteEntry -Name "<Descriptive Name>" -InternalAddress *.<domain> -ExternalAddress <domain> -OutboundOnly $true [-ExceptionList <domain1,domain2...>]

Im folgenden Beispiel werden die E-Mail-Adressen aller ausgehenden Nachrichten in der Exchange-Organisation umgeschrieben, die von Empfängern in der Domäne "contoso.com" und allen ihren Unterdomänen gesendet wurden. Ausgehende Nachrichten werden so umgeschrieben, dass sie scheinbar von der Domäne "contoso.com" kommen. Eingehende Nachrichten, die an Empfänger unter "contoso.com" gesendet wurden, können nicht umgeschrieben werden, da ein Platzhalterzeichen im Parameter *InternalAddress* verwendet wurde.

    New-AddressRewriteEntry -Name "Rewrite all contoso.com subdomains" -InternalAddress *.contoso.com -ExternalAddress contoso.com -OutboundOnly $true

Das folgende Beispiel ist ähnlich wie das vorherige, nur dass Nachrichten, die von Empfängern in den Unterdomänen "legal.contoso.com" und "corp.contoso.com" gesendet wurden, nicht umgeschrieben werden:

    New-AddressRewriteEntry -Name "Rewrite all contoso.com subdomains except legal.contoso.com and corp.contoso.com" -InternalAddress *.contoso.com -ExternalAddress contoso.com -OutboundOnly $true -ExceptionList legal.contoso.com,corp.contoso.com

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob die Adressumschreibungseinträge erfolgreich erstellt wurden:

1.  Führen Sie den Befehl `Get-AddressRewriteEntry <AddressRewriteEntryIdentity> | Format-List` aus, und überprüfen Sie, ob die angezeigten Einstellungen den von Ihnen konfigurierten entsprechen.

2.  Senden Sie eine Testnachricht von einem Postfach, für das der Adressumschreibungseintrag zutrifft, an ein externes Postfach. Vergewissern Sie sich, dass die Testnachricht scheinbar von der umgeschriebenen E-Mail-Adresse stammt.

3.  Antworten Sie von einem externen Postfach auf die Testnachricht. Überprüfen Sie, ob das ursprüngliche Postfach die Antwortnachricht empfängt.

## Verwenden der Shell zum Ändern von Adressumschreibungseinträgen

Die verfügbaren Konfigurationsoptionen zum Ändern eines vorhandenen Adressumschreibungseintrags sind identisch mit den Konfigurationsoptionen zum Erstellen eines neuen Adressumschreibungseintrags.

## Ändern von Adressumschreibungseinträgen für einzelne Empfänger

Verwenden Sie folgende Syntax, um einen Adressumschreibungseintrag zu ändern, der die E-Mail-Adresse eines einzelnen Empfängers umschreibt:

    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -Name "<Descriptive Name>" -InternalAddress <internal email address> -ExternalAddress <external email address> -OutboundOnly <$true | $false>

Im folgenden Beispiel werden verschiedene Eigenschaften des Adressumschreibungseintrags "joe@contoso.com to support@nortwindtraders.com" für einen einzelnen Empfänger geändert:

  - Ändert die externe Adresse in "support@northwindtraders.net".

  - Ändert den Namen des Adressumschreibungseintrags in "joe@contoso.com to support@northwindtraders.net".

  - Ändert den Wert von *OutboundOnly* in `$true`. Beachten Sie, dass Sie für diese Änderung "support@northwindtraders.net" als Proxyadresse in Joes Postfach konfigurieren müssen.

<!-- end list -->

    Set-AddressRewriteEntry "joe@contoso.com to support@nortwindtraders.com" -Name "joe@contoso.com to support@northwindtraders.net" -ExternalAddress support@northwindtraders.net -OutboundOnly $true

## Ändern von Adressumschreibungseinträgen für Empfänger in einzelnen Domänen oder Unterdomänen

Verwenden Sie folgende Syntax, um einen Adressumschreibungseintrag zu ändern, der die E-Mail-Adressen von Empfängern in einer einzelnen Domäne oder Unterdomäne umschreibt:

    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -Name "<Descriptive Name>" -InternalAddress <domain or subdomain> -ExternalAddress <domain> -OutboundOnly <$true | $false>

Im folgenden Beispiel wird der interne Adresswert des Adressumschreibungseintrags "Northwind Traders to Contoso" für eine einzelne Domäne geändert.

```powershell
Set-AddressRewriteEntry "Northwindtraders to Contoso" -InternalAddress northwindtraders.net
```

## Ändern von Adressumschreibungseinträgen für Empfänger in mehreren Unterdomänen

Verwenden Sie folgende Syntax, um einen Adressumschreibungseintrag zu ändern, der die E-Mail-Adressen von Empfängern in einer Domäne und allen ihren Unterdomänen umschreibt:

    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -Name "<Descriptive Name>" -InternalAddress *.<domain> -ExternalAddress <domain> -ExceptionList <list of domains>

Verwenden Sie folgende Syntax, um die vorhandenen Ausnahmelistenwerte eines Adressumschreibungseintrags für mehrere Unterdomänen zu ersetzen:

    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -ExceptionList <domain1,domain2,...>

Im folgenden Beispiel wird die vorhandene Ausnahmeliste des Adressumschreibungseintrags "Contoso to Northwind Traders" für mehrere Unterdomänen durch die Werte "marketing.contoso.com" und "legal.contoso.com" ersetzt:

    Set-AddressRewriteEntry "Contoso to Northwind Traders" -ExceptionList sales.contoso.com,legal.contoso.com

Verwenden Sie folgende Syntax, um ausgewählte Ausnahmelistenwerte eines Adressumschreibungseintrags für mehrere Unterdomänen hinzuzufügen oder zu entfernen, ohne die vorhandenen Ausnahmelistenwerte zu ändern:

    Set-AddressRewriteEntry <AddressRewriteEntryIdentity> -ExceptionList @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}

Im folgenden Beispiel wird "finanace.contoso.com" in der Ausnahmeliste des Adressumschreibungseintrags "Contoso to Northwind Traders" für mehrere Unterdomänen hinzugefügt und "marketing.contoso.com" daraus entfernt:

    Set-AddressRewriteEntry "Contoso to Northwind Traders" -ExceptionList @{Add="finanace.contoso.com"; Remove="marketing.contoso.com"}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob der Adressumschreibungseintrag erfolgreich geändert wurde:

1.  Führen Sie den Befehl `Get-AddressRewriteEntry <AddressRewriteEntryIdentity> | Format-List` aus, und überprüfen Sie, ob die angezeigten Einstellungen den von Ihnen konfigurierten entsprechen.

2.  Senden Sie eine Testnachricht von einem Postfach, für das der Adressumschreibungseintrag zutrifft, an ein externes Postfach. Vergewissern Sie sich, dass die Testnachricht scheinbar von der umgeschriebenen E-Mail-Adresse stammt.

3.  Beantworten Sie die Testnachricht aus dem externen Postfach. Überprüfen Sie, ob das ursprüngliche Postfach die Antwortnachricht empfängt.

## Verwenden der Shell zum Entfernen von Adressumschreibungseinträgen

Verwenden Sie die folgende Syntax, um einen einzelnen Adressumschreibungseintrag zu entfernen:

```powershell
Remove-AddressRewriteEntry <AddressRewriteEntryIdentity>
```

Im folgenden Beispiel wird der Adressumschreibungseintrag "Contoso.com to Northwindtraders.com" entfernt:

```powershell
Remove-AddressRewriteEntry "Contoso.com to Northwindtraders.com"
```

Verwenden Sie die folgende Syntax, um mehrere Adressumschreibungseinträge zu entfernen:

    Get-AddressRewriteEntry [<search criteria>] | Remove-AddressRewriteEntry [-WhatIf]

Das folgende Beispiel entfernt alle Adressumschreibungseinträge:

```powershell
Get-AddressRewriteEntry | Remove-AddressRewriteEntry
```

Im folgenden Beispiel wird das Entfernen von Adressumschreibungseinträgen simuliert, die den Text "to contoso.com" im Namen enthalten. Mit der Option *WhatIf* können Sie das Ergebnis als Vorschau anzeigen, ohne die Änderungen tatsächlich anzuwenden.

    Get-AddressRewriteEntry "*to contoso.com" | Remove-AddressRewriteEntry -WhatIf

Wenn Sie mit dem Ergebnis zufrieden sind, führen Sie den Befehl erneut ohne die Option *WhatIf* aus, um die Adressumschreibungseinträge zu entfernen.

    Get-AddressRewriteEntry "*to contoso.com" | Remove-AddressRewriteEntry

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie wie folgt vor, um zu überprüfen, ob der Adressumschreibungseintrag erfolgreich entfernt wurde:

1.  Führen Sie den Befehl `Get-AddressRewriteEntry` aus, und vergewissern Sie sich, dass die entfernten Adressumschreibungseinträge nicht mehr aufgelistet werden.

2.  Senden Sie eine Testnachricht von einem Postfach, für das der Adressumschreibungseintrag zutrifft, an ein externes Postfach. Vergewissern Sie sich, dass die Testnachricht nicht mehr durch den entfernten Adressumschreibungseintrag betroffen ist.

3.  Beantworten Sie die Testnachricht aus dem externen Postfach. Überprüfen Sie, ob das ursprüngliche Postfach die Antwortnachricht empfängt und die Testnachricht nicht mehr durch den entfernten Adressumschreibungseintrag betroffen ist.

