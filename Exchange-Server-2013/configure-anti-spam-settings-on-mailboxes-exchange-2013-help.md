---
title: 'Konfigurieren von Antispameinstellungen für Postfächer: Exchange 2013 Help'
TOCTitle: Konfigurieren von Antispameinstellungen für Postfächer
ms:assetid: 868d7fd8-e817-46ba-9b67-edf2f50b9494
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb123559(v=EXCHG.150)
ms:contentKeyID: 50476174
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Konfigurieren von Antispameinstellungen für Postfächer

 

_**Gilt für:**Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:**2016-11-17_

Sie können für einzelne Postfächer bestimmte Antispameinstellungen konfigurieren, die sich von den Antispameinstellungen für die übrigen Postfächer in Ihrer Exchange-Organisation unterscheiden. Wenn Sie für ein Postfach eine Antispameinstellung konfigurieren, setzt diese Einstellung die organisationsweite Inhaltsfilterung oder die Antispameinstellung auf Organisationsebene außer Kraft.


> [!NOTE]
> Am 1. November 2016 hat Microsoft die Generierung von Spamdefinitionsupdates für die SmartScreen-Filter in Exchange und Outlook eingestellt. Die vorhandenen SmartScreen-Spamdefinitionen bleiben bestehen, ihre Effektivität wird aber im Laufe der Zeit wahrscheinlich abnehmen. Weitere Informationen finden Sie unter <A href="https://go.microsoft.com/fwlink/p/?linkid=835894">Deprecating support for SmartScreen in Outlook and Exchange</A>.



## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen der einzelnen Verfahren: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Antispamfunktionen" im Thema [Berechtigungen für Antispam- und Antischadsoftwareoptionen](anti-spam-and-anti-malware-permissions-exchange-2013-help.md) und "Antispam" im Thema [Empfängerberechtigungen](recipients-permissions-exchange-2013-help.md).

  - Standardmäßig sind die Antispamfunktionen im Transportdienst auf einem Postfachserver deaktiviert. In der Regel aktivieren Sie die Antispamfunktionen auf einem Postfachserver nur, wenn Ihre Exchange-Organisation vorab keine Antispamfilterung durchführt, bevor eingehende Nachrichten akzeptiert werden. Weitere Informationen finden Sie unter [Aktivieren der Antispamfunktionen auf einem Postfachserver](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Die Shell kann nur für diesen Vorgang verwendet werden.

  - Der SCL-Schwellenwert für den Junk-E-Mail-Ordner verhält sich anders als die SCL-Werte für Löschen, Zurückweisen und Quarantäne. Weitere Informationen finden Sie unter [SCL-Schwellenwert](spam-confidence-level-threshold-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Verwenden der Shell zum Konfigurieren von Antispamfunktionen für ein einzelnes Postfach

Verwenden Sie folgende Syntax, um die Antispameinstellungen für ein einzelnes Postfach zu konfigurieren.

    Set-Mailbox <MailboxIdentity> -AntispamBypassEnabled <$true | $false> -RequireSenderAuthenticationEnabled <$true | $false> -SCLDeleteEnabled <$true | $false | $null> -SCLDeleteThreshold <0-9 | $null> -SCLJunkEnabled <$true | $false | $null > -SCLJunkThreshold <0-9 | $null> -SCLQuarantineEnabled <$true | $false | $null > -SCLQuarantineThreshold <0-9 | $null> -SCLRejectEnabled <$true | $false | $null > -SCLRejectThreshold <0-9 | $null>

In diesem Beispiel wird das Postfach eines Benutzers namens Jeff Phillips so konfiguriert, dass alle Antispamfilter umgangen werden und Nachrichten, die einen SCL-Schwellenwert von 5 für den Junk-E-Mail-Ordner erreichen oder überschreiten, an seinen Junk-E-Mail-Ordner in Microsoft Outlook zugestellt werden.

    Set-Mailbox "Jeff Phillips" -AntispamBypassEnabled $true -SCLJunkEnabled $true -SCLJunkThreshold 4

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Antispamfunktionen für ein einzelnes Postfach erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-Mailbox <MailboxIdentity> | Format-List SCL*,Bypass*,*SenderAuth*

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Konfigurieren von Antispamfunktionen für mehrere Postfächer mithilfe der Shell

Verwenden Sie folgende Syntax, um alle Antispameinstellungen für mehrere Postfächer zu konfigurieren.

    Get-Mailbox [<Filter>]| Set-Mailbox <Anti-Spam Settings>

In diesem Beispiel wird für alle Postfächer im Container "Benutzer" der Domäne "Contoso.com" der SCL-Isolierungsschwellenwert mit einem Wert von 7 aktiviert.

    Get-Mailbox -OrganizationalUnit Contoso.com/Users | Set-Mailbox -SCLQuarantineEnabled $true -SCLQuarantineThreshold 7

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass die Antispamfunktionen für mehrere Postfächer erfolgreich konfiguriert wurden:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-Mailbox [<Filter>] | Format-List Name,SCL*,*SenderAuth*

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

## Konfigurieren des Junk-E-Mail-Schwellenwerts für alle Postfächer in Ihrer Organisation mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Set-OrganizationConfig -SCLJunkThreshold <Integer>

In diesem Beispiel wird in der Organisation der Schwellenwert für Junk-E-Mail auf 5 gesetzt.

    Set-OrganizationConfig -SCLJunkThreshold 5

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass der Junk-E-Mail-Schwellenwert für alle Postfächer in Ihrer Organisation erfolgreich konfiguriert wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-OrganizationConfig | Format-List SCLJunkThreshold

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

