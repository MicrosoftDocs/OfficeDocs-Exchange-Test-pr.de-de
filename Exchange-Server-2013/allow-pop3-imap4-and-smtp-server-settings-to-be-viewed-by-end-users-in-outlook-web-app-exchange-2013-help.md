---
title: 'Zulassen der Anz. von POP3-, IMAP4- und SMTP-Servereinst. in Outlook Web App'
TOCTitle: Zulassen der Anzeige von POP3-, IMAP4- und SMTP-Servereinstellungen durch Endbenutzer in Outlook Web App
ms:assetid: bd22bf7e-3bf7-45e6-8790-919b780166f6
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Gg298947(v=EXCHG.150)
ms:contentKeyID: 50554899
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Zulassen der Anzeige von POP3-, IMAP4- und SMTP-Servereinstellungen durch Endbenutzer in Outlook Web App

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2012-11-28_

Wenn Sie Benutzer haben, die über POP3 oder IMAP4 eine Verbindung zu ihren Microsoft Exchange Server 2013-Postfächern herstellen, müssen diese dazu die richtigen Servereinstellungen kennen. Nach einer Standardinstallation von Exchange 2013 können Ihre Benutzer nicht ihre eigenen eingehenden POP3- oder IMAP4-Servereinstellungen bzw. ausgehenden SMTP-Servereinstellungen nachschlagen. Sie können jedoch Exchange so konfigurieren, dass die Benutzer ihre eigenen Einstellungen mithilfe von MicrosoftOutlook Web App nachschlagen können.

Nachdem Sie diese Schritte ausgeführt habe, können die Benutzer ihre Servereinstellungen wie folgt in Outlook Web App nachschlagen:

1.  Klicken Sie in Outlook Web App auf **Einstellungen** \> **Optionen**.

2.  Klicken Sie in **Optionen** auf **Konto** \> **Mein Konto** \> **Einstellungen für den Zugriff über POP oder IMAP**.

Weitere Informationen zu POP3 und IMAP4 finden Sie unter [POP3 und IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Für die Verfahren in diesem Thema sind bestimmte Berechtigungen erforderlich. Informationen zu den Berechtigungen finden Sie in den einzelnen Verfahren.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zulassen, dass POP3- und IMAP4-Benutzer ihre eingehenden POP3- und IMAP4-Einstellungen in Outlook Web App anzeigen können, mithilfe der Shell

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "POP3-Einstellungen" und "IMAP4-Einstellungen" im Thema [Berechtigungen für Clients und mobile Geräte](clients-and-mobile-devices-permissions-exchange-2013-help.md).

Im folgenden Beispiel wird dem Endbenutzer erlaubt, externe Servereinstellungen für POP3 anzuzeigen.

```powershell
Set-PopSettings -ExternalConnectionSettings {Dublin01.Contoso.com:995:SSL}
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-PopSettings](https://technet.microsoft.com/de-de/library/aa997154\(v=exchg.150\)).

Im folgenden Beispiel wird dem Endbenutzer erlaubt, externe Servereinstellungen für IMAP4 anzuzeigen.

```powershell
Set-ImapSettings -ExternalConnectionSettings {Dublin01.Contoso.com:993:SSL}
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ImapSettings](https://technet.microsoft.com/de-de/library/aa998252\(v=exchg.150\)).

Sie müssen IIS neu starten, um diese Änderungen zu übernehmen. Sie müssen die POP3-Dienste nicht neu starten. Um IIS neu zu starten, geben Sie an einer Eingabeaufforderung Folgendes ein:

```powershell
iisreset
```

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

So überprüfen Sie, ob Sie Exchange so konfiguriert haben, dass Benutzer ihre POP3-Servereinstellungen anzeigen können:

1.  Führen Sie folgenden Befehl in der Shell aus.
    
    ```powershell
    Get-PopSettings | format-list
    ```

2.  Überprüfen Sie, ob die Eigenschaft *ExternalConnectionSettings* festgelegt ist.

So überprüfen Sie, ob Sie Exchange so konfiguriert haben, dass Benutzer ihre IMAP4-Servereinstellungen anzeigen können:

1.  Führen Sie folgenden Befehl in der Shell aus.
    
    ```powershell
    Get-ImapSettings | format-list
    ```

2.  Überprüfen Sie, ob die Eigenschaft *ExternalConnectionSettings* festgelegt ist.

## Zulassen, dass POP3- und IMAP4-Benutzer ihre ausgehenden SMTP-Einstellungen in Outlook Web App anzeigen können, mithilfe der Shell

Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Empfangsconnectors" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

Im folgenden Beispiel wird dem Endbenutzer erlaubt, interne und externe Servereinstellungen mithilfe von Outlook Web App anzuzeigen.

```powershell
    Get-ReceiveConnector "*Client Frontend*" | Set-ReceiveConnector -Fqdn Server.Contoso.com -AdvertiseClientSettings $true 
```

Ausführliche Informationen zu Syntax und Parametern finden Sie unter [Set-ReceiveConnector](https://technet.microsoft.com/de-de/library/bb125140\(v=exchg.150\)).

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

So überprüfen Sie, ob Sie Exchange so konfiguriert haben, dass Benutzer ihre SMTP-Servereinstellungen anzeigen können:

1.  Führen Sie folgenden Befehl in der Shell aus.
    
    ```powershell
    Get-ReceiveConnector | format-list
    ```

2.  Wenn die Eigenschaft *AdvertiseClientSettings* auf `true` festgelegt ist, können Benutzer ihre SMTP-Servereinstellungen in Outlook Web App anzeigen. Wenn *AdvertiseClientSettings* auf `false` festgelegt ist, können Benutzer ihre SMTP-Servereinstellungen nicht in Outlook Web App anzeigen.

## Weitere Informationen

Nachdem Sie dem Endbenutzer die Anzeige seiner POP3-, IMAP4- und SMTP-Einstellungen erlaubt haben, können Sie die folgenden Aufgaben ausführen:

[Aktivieren oder Deaktivieren des POP3-Zugriffs für einen Benutzer](enable-or-disable-pop3-access-for-a-user-exchange-2013-help.md)

[Aktivieren oder Deaktivieren des IMAP4-Zugriffs für einen Benutzer](enable-or-disable-imap4-access-for-a-user-exchange-2013-help.md)

