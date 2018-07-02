---
title: 'Verwalten von DNS-Meldungen: Exchange 2013 Help'
TOCTitle: Verwalten von DNS-Meldungen
ms:assetid: 23c9d844-6fc7-44c9-a308-587338281611
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa996803(v=EXCHG.150)
ms:contentKeyID: 50475354
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Kontingentmeldung ändern
- Systemmeldung ändern
- Zurückweisungsmeldung ändern
- Unzustellbarkeitsmeldung ändern
ms.translationtype: HT
---

# Verwalten von DNS-Meldungen

 

_**Gilt für:** Exchange Server 2013_

_**Letztes Änderungsdatum des Themas:** 2013-02-20_

Microsoft Exchange Server 2013 verwendet Benachrichtigungen über den Zustellungsstatus (Delivery Status Notifications, DSN), um Unzustellbarkeitsberichte und andere Statusnachrichten an die Nachrichtenabsender zu übermitteln. Sie können die integrierten DSN-Meldungen verwenden oder in Übereinstimmung mit den Anforderungen Ihrer Organisation benutzerdefinierte DSN-Meldungen erstellen.

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 15 Minuten

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "Benachrichtigungen über den Übermittlungsstatus (DSNs)" im Thema [Berechtigungen für den Nachrichtenfluss](mail-flow-permissions-exchange-2013-help.md).

  - Die in Exchange enthaltenen integrierten DSN-Meldungen können nicht entfernt werden. Wenn Sie eine integrierte DSN-Meldung ändern möchten, müssen Sie eine benutzerdefinierte DSN-Meldung für den DSN-Code erstellen, der angepasst werden soll. Wenn Sie eine benutzerdefinierte DSN-Meldung entfernen, wird der DSN-Code, der dieser Meldung zugeordnet ist, auf die ursprüngliche DSN-Meldung zurückgesetzt, die in Exchange enthalten ist.

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>.



## Was möchten Sie machen?

## Anzeigen von integrierten und benutzerdefinierten DSN-Meldungen mithilfe der Shell

Führen Sie den folgenden Befehl aus, um eine Übersichtsliste aller integrierten DSN-Meldungen in Exchange 2013 anzuzeigen:

    Get-SystemMessage -Original

Zur Anzeige einer Übersichtsliste aller benutzerdefinierten DSN-Meldungen in Ihrer Organisation führen Sie den folgenden Befehl aus:

    Get-SystemMessage

Führen Sie den folgenden Befehl aus, um detaillierte Informationen für die benutzerdefinierte DSN-Meldung für den DSN-Code 5.1.2 anzuzeigen, die in englischer Sprache an interne Absender gesendet wird:

    Get-SystemMessage En\Internal\5.1.2 | Format-List

## Erstellen einer benutzerdefinierten DSN-Meldung mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    New-SystemMessage -Internal <$true | $false> -Language <Locale> -DSNCode <x.y.z> -Text "<DSN text>"

In diesem Beispiel wird eine benutzerdefinierte DSN-Meldung (Nur-Text) für den DSN-Code 5.1.2 erstellt, die in englischer Sprache an interne Absender gesendet wird.

    New-SystemMessage -Internal $true -Language En -DSNCode 5.1.2 -Text "You tried to send a message to a disabled mailbox that's no longer accepting messages. Please contact the Help Desk at extension 123 for assistance."

In diesem Beispiel wird eine benutzerdefinierte DSN-Meldung (Nur-Text) für den DSN-Code 5.1.2 erstellt, die in englischer Sprache an externe Absender gesendet wird.

    New-SystemMessage -Internal $false -Language En -DSNCode 5.1.2 -Text "You tried to send a message to a disabled mailbox that's no longer accepting messages. Please contact your System Administrator for more information."

In diesem Beispiel wird eine benutzerdefinierte DSN-Meldung (HTML) für den DSN-Code 5.1.2 erstellt, die in englischer Sprache an interne Absender gesendet wird.

    New-SystemMessage -DSNCode 5.1.2 -Internal $true -Language En -Text 'You tried to send a message to a <B>disabled</B> mailbox. Please visit <A HREF="http://it.contoso.com">Internal Support</A> or contact &quot;InfoSec&quot; for more information.'

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine benutzerdefinierte DSN-Meldung erfolgreich erstellt wurde:

1.  Führen Sie den folgenden Befehl aus:
    
        Get-SystemMessge -DSNCode <x.y.z> | Format-List Name,Internal,Text,Language

2.  Überprüfen Sie, ob die angezeigten Werte den Werten entsprechen, die Sie konfiguriert haben.

3.  Senden Sie eine Testnachricht, durch welche die benutzerdefinierte DSN-Meldung generiert wird, die Sie konfiguriert haben.

## Ändern des Texts einer benutzerdefinierten DSN-Nachricht mithilfe der Shell

Führen Sie den folgenden Befehl aus, um den Text einer benutzerdefinierten DSN-Meldung zu ändern:

    Set-SystemMessage <Locale>\<Internal | External>\<DSNcode> -Text "<DSN text>"

In diesem Beispiel wird der Text der benutzerdefinierten DSN-Meldung für den DSN-Code 5.1.2 geändert, die in englischer Sprache an interne Absender gesendet wird.

    Set-SystemMessage En\Internal\5.1.2 -Text "The mailbox you tried to send an e-mail message to is disabled and is no longer accepting messages. Please contact the Help Desk at extension 123 for assistance."

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass der Text einer benutzerdefinierten DSN-Meldung erfolgreich geändert wurde:

1.  Führen Sie den folgenden Befehl aus: `Get-SystemMessage`.
    
        Set-SystemMessage <Locale>\<Internal | External>\<DSNcode> | Format-List -Text

2.  Überprüfen Sie, ob der angezeigte Wert dem Wert entspricht, den Sie konfiguriert haben.

## Entfernen einer benutzerdefinierten DSN-Meldung mithilfe der Shell

Führen Sie den folgenden Befehl aus:

    Remove-SystemMessage <Local>\<Internal | External>\<DSNcode>

In diesem Beispiel wird die benutzerdefinierte DSN-Meldung für den DSN-Code 5.1.2 entfernt, die in englischer Sprache an interne Absender gesendet wird.

    Remove-SystemMessage En\Internal\5.1.2

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Gehen Sie folgendermaßen vor, um sicherzustellen, dass eine benutzerdefinierte DSN-Meldung erfolgreich entfernt wurde:

1.  Führen Sie folgenden Befehl aus: `Get-SystemMessage`.

2.  Überprüfen Sie, ob die entfernte DSN-Meldung für das Gebietsschema und interne oder externe Empfänger sowie der gelöschte DSN-Code nicht mehr aufgeführt werden.

## Weiterleiten von Kopien von DSN-Meldungen an das Exchange-Empfängerpostfach

Sie können eine Liste mit DSN-Codes angeben, die überwacht werden sollen, indem die DSN-Meldungen in das Postfach des Exchange-Empfängers kopiert werden. Dem Exchange-Empfänger ist jedoch standardmäßig kein Postfach zugewiesen, sodass an den Exchange-Empfänger gesendete Nachrichten verworfen werden. Zum Senden von Kopien von DSN-Meldungen an das Exchange-Empfängerpostfach müssen Sie dem Exchange-Empfänger ein Postfach zuweisen und anschließend die DSN-Codes angeben, die überwacht werden sollen. Standardmäßig werden die folgenden DSN-Codes überwacht: `5.4.8`, `5.4.6`, `5.4.4`, `5.2.4`, `5.2.0` und `5.1.4`.

## Schritt 1: Weisen Sie dem Exchange-Empfänger mithilfe der Shell ein Postfach zu

Führen Sie die folgenden Schritte aus, um dem Exchange-Empfänger ein Postfach zuzuweisen:

1.  Aufgrund der potenziell großen Anzahl von E-Mails sollten Sie das Erstellen eines dedizierten Postfachs und Active Directory-Benutzerkontos für den Exchange-Empfänger in Betracht ziehen. Weitere Informationen finden Sie unter [Erstellen von Benutzerpostfächern](create-user-mailboxes-exchange-2013-help.md). Anderenfalls geben Sie das vorhandene Postfach an, das dem Exchange-Empfänger zugewiesen werden soll.

2.  Führen Sie den folgenden Befehl aus:
    
        Set-OrganizationConfig -MicrosoftExchangeRecipientReplyRecipient <MailboxIdentity>
    
    Wenn Sie dem Exchange-Empfänger z. B. das vorhandene Postfach "Contoso System Mailbox" zuweisen möchten, führen Sie den folgenden Befehl aus:
    
        Set-OrganizationConfig -MicrosoftExchangeRecipientReplyRecipient "Contoso System Mailbox"

## Schritt 2: Geben Sie die DSN-Codes an, die überwacht werden sollen

## Angeben von DSN-Codes mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Nachrichtenfluss** \> **Empfangsconnectors** \> **Weitere Optionen**![Weitere Optionen (Symbol)](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Weitere Optionen (Symbol)") \> **Einstellungen für Organisationstransport** \> **Zustellung**.

2.  Geben Sie im Abschnitt **DSN-Codes** die DSN-Codes ein, die überwacht werden sollen (mit dem Format *\<x.y.z\>*), und klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Wählen Sie einen vorhandenen Eintrag aus, und klicken Sie auf **Bearbeiten**![Bearbeitungssymbol](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Bearbeitungssymbol"), um den Eintrag zu ändern, oder klicken Sie auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)"), um den Eintrag zu entfernen. Klicken Sie nach Abschluss des Vorgangs auf **Speichern**.

## Angeben von DSN-Codes mithilfe der Shell

Führen Sie den folgenden Befehl aus, um die vorhandenen Werte zu ersetzen:

    Set-TransportConfig -GenerateCopyOfDSNFor <x.y.z>,<x.y.z>...

In diesem Beispiel wird die Exchange-Organisation so konfiguriert, dass alle DSN-Meldungen mit den DSN-Codes 5.7.1, 5.7.2 und 5.7.3 an den Exchange-Empfänger weitergeleitet werden.

    Set-TransportConfig -GenerateCopyOfDSNFor 5.7.1,5.7.2,5.7.3

Führen Sie folgenden Befehl aus, um Einträge hinzuzufügen bzw. zu entfernen, ohne vorhandene Werte zu ändern:

    Set-TransportConfig -GenerateCopyOfDSNFor @{Add="<x.y.z>","<x.y.z>"...; Remove="<x.y.z>","<x.y.z>"...}

In diesem Beispiel wird der DSN-Code 5.7.5 zur vorhandenen Liste der DSN-Meldungen hinzugefügt, die an den Exchange-Empfänger weitergeleitet werden, und der DSN-Code 5.7.1 wird aus dieser Liste entfernt.

    Set-TransportConfig -GenerateCopyOfDSNFor @{Add="5.7.5"; Remove="5.7.1"}

## Woher wissen Sie, dass dieses Verfahren erfolgreich war?

Überwachen Sie das dem Exchange-Empfänger zugeordnete Postfach, und überprüfen Sie, ob die DSN-Meldungen die angegebenen DSN-Codes enthalten, um zu überprüfen, ob Sie das Senden von Kopien der DSN-Meldungen an das Postfach des Exchange-Empfängers erfolgreich konfiguriert haben.

