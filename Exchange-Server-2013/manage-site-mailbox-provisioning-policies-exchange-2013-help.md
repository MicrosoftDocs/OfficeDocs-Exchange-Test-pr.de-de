---
title: 'Verwalten v. Bereitstellungsrichtl. f. Websitepostfächer: Exchange 2013-Hilfe'
TOCTitle: Verwalten von Bereitstellungsrichtlinien für Websitepostfächer
ms:assetid: 2f160d1a-a031-461f-8d29-c9cd49ca1645
ms:mtpsurl: https://technet.microsoft.com/de-de/library/JJ710340(v=EXCHG.150)
ms:contentKeyID: 50475269
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Verwalten von Bereitstellungsrichtlinien für Websitepostfächer

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-21_

Bereitstellungsrichtlinien für Websitepostfächer gelten für E-Mails, die an Websitepostfächer und von einem Websitepostfach gesendet werden, und wirken sich auf die Größe des Websitepostfachs auf dem Exchange-Server aus.

Weitere Informationen zu Websitepostfächern finden Sie unter [Websitepostfächer](site-mailboxes-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Websitepostfächer" im Thema [Freigabe- und Zusammenarbeitsberechtigungen](sharing-and-collaboration-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

  - Wenngleich Sie mehrere Bereitstellungsrichtlinien für Websitepostfächer erstellen können, wird nur die standardmäßige Bereitstellungsrichtlinie auf alle Websitepostfächer angewendet. Sie können nicht mehrere Richtlinien in Ihrem Unternehmen anwenden.

  - Dieses Verfahren kann nicht in der Exchange-Verwaltungskonsole ausgeführt werden. Sie müssen die Shell verwenden.


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Erstellen einer Bereitstellungsrichtlinie für Websitepostfächer

In diesem Beispiel wird die Standardbereitstellungsrichtlinie "SM\_ProvisioningPolicy" mit den folgenden Einstellungen erstellt:

  - Das Kontingent für Websitepostfächer, ab dem eine Warnung ausgegeben wird, beträgt 9 GB.

  - Websitepostfächer können keine Nachrichten mehr erhalten, wenn das Postfach eine Größe von 10 GB erreicht hat.

  - Die maximale Größe für an ein Websitepostfach gesendete E-Mail-Nachrichten beträgt 50 MB.

<!-- end list -->

    New-SiteMailboxProvisioningPolicy -Name SM_ProvisioningPolicy -IsDefault -IssueWarningQuota 9GB -ProhibitSendReceiveQuota 10GB -MaxReceiveSize 50MB

## Anzeigen der Einstellungen einer Bereitstellungsrichtlinie für Websitepostfächer

In diesem Beispiel werden detaillierte Informationen zu allen Bereitstellungsrichtlinien für Websitepostfächer in Ihrer Organisation zurückgegeben.

```powershell
Get-SiteMailboxProvisioningPolicy | Format-List
```

In diesem Beispiel werden alle Richtlinien in Ihrer Organisation zurückgegeben, es werden jedoch lediglich die `IsDefault`-Informationen angezeigt, um die Standardrichtlinie zu ermitteln.

```powershell
Get-SiteMailboxProvisioningPolicy | Format-List IsDefault
```

## Änderungen an einer vorhandenen Bereitstellungsrichtlinie für Websitepostfächer

In diesem Beispiel wird die Bereitstellungsrichtlinie für Websitepostfächer "Default" geändert, indem die maximale Größe von E-Mails, die von dem Websitepostfach empfangen werden können, auf 25 MB festgelegt wird. (Bei der Installation von Exchange wird eine Bereitstellungsrichtlinie mit dem Namen **Default** erstellt.)

```powershell
Set-SiteMailboxProvisioningPolicy -Identity Default -MaxReceiveSize 25MB
```

In diesem Beispiel wird das Kontingent, ab dem eine Warnmeldung gesendet wird, auf 9,5 GB und das Kontingent für das Sende- und Empfangsverbot auf 10 GB festgelegt.

    Set-SiteMailboxProvisioningPolicy -Identity Default -IssueWarningQuota 9GB -ProhibitSendReceiveQuota 10GB

## Konfigurieren eines Präfixes für einen Websitepostfachnamen

Wenn ein neues Websitepostfach erstellt wird, verfügt die zugehörige E-Mail-Adresse standardmäßig über ein Präfix. Das Präfix der E-Mail-Adresse ermöglicht Ihnen die einfache Suche und Abfrage von Websitepostfächern und kann Benutzern außerdem helfen, die Postfächer zu erkennen. Sie können das Präfix optional deaktivieren oder das Präfix für Ihren Mandanten in Office 365 oder für eine bestimmte Gesamtstruktur in einer lokalen Bereitstellung ändern. Wenn Ihr Websitepostfach in Office 365 erstellt wird, lautet das Standardpräfix in der Standardeinstellung **SMO-**. Wenn Ihr Websitepostfach in Ihrer lokalen Bereitstellung erstellt wird, lautet das Präfix alternativ dazu **SM-**. Das Standardverhalten unterscheidet sich zwischen diesen Standorten, sodass bei Kunden mit einer Hybridbereitstellung keine Konflikte auftreten, wenn Websitepostfächer an beiden Standorten erstellt und anschließend standortübergreifend synchronisiert werden.

In diesem Beispiel wird die Präfixbenennung deaktiviert, indem der Parameter *DefaultAliasPrefixEnabled* auf "$false" festgelegt wird.

    Set-SiteMailboxProvisioningPolicy -Identity Default -DefaultAliasPrefixEnabled $false -AliasPrefix $null

In diesem Beispiel wird die Standardbereitstellungsrichtlinie geändert, und der Parameter *AliasPrefix* wird auf FOREST01 festgelegt.


> [!NOTE]
> Für Bereitstellungen mit mehreren Gesamtstrukturen empfiehlt es sich, in jeder Gesamtstruktur ein anderes Präfix zu verwenden, um bei der gesamtstrukturübergreifenden Synchronisierung von Objekten Konflikte zu vermeiden, falls Websitepostfächer desselben Namens in mehreren Gesamtstrukturen erstellt wurden.



    Set-SiteMailboxProvisioningPolicy -Identity Default -AliasPrefix FOREST01 -DefaultAliasPrefixEnabled $false


> [!NOTE]
> Im Fall einer Hybridbereitstellung, in der Exchange lokal und in Office 365 verwendet wird, werden alle cloudbasierten Websitepostfächer mit dem Präfix <STRONG>SMO-</STRONG> erstellt. Die Präfixe unterscheiden sich in Office 365 und lokalem Exchange, sodass bei Kunden mit einer Hybridbereitstellung keine Konflikte auftreten, wenn Websitepostfächer an beiden Standorten erstellt und anschließend standortübergreifend synchronisiert werden. Der Parameter "AliasPrefix" besitzt Vorrang vor dem Parameter "DefaultAliasPrefixEnabled"; wenn daher der Parameter <EM>AliasPrefix</EM> auf eine gültige, nicht leere Zeichenfolge gesetzt wird, wird diese Zeichenfolge dem Alias jedes neuen Websitepostfachs vorangestellt.



## Löschen einer Bereitstellungsrichtlinie für Websitepostfächer

In diesem Beispiel wird die Standardrichtlinie für Websitepostfächer gelöscht, die während des Exchange-Setups erstellt wird.

```powershell
Remove-SiteMailboxProvisioningPolicy -Identity Default
```


> [!IMPORTANT]
> Sie müssen zuerst eine andere Standardrichtlinie erstellen und zuweisen, bevor Sie die Richtlinie <STRONG>Default</STRONG> entfernen können.



## Weitere Informationen

Ausführliche Informationen zu Syntax und Parametern finden Sie in den folgenden Themen:

[New-SiteMailboxProvisioningPolicy](https://technet.microsoft.com/de-de/library/jj218647\(v=exchg.150\))

[Get-SiteMailboxProvisioningPolicy](https://technet.microsoft.com/de-de/library/jj218617\(v=exchg.150\))

[Set-SiteMailboxProvisioningPolicy](https://technet.microsoft.com/de-de/library/jj218624\(v=exchg.150\))

[Remove-SiteMailboxProvisioningPolicy](https://technet.microsoft.com/de-de/library/jj218672\(v=exchg.150\))

