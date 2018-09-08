---
title: 'Verwalten von Voicemail-Einstellungen für einen Benutzer: Exchange Online Help'
TOCTitle: Verwalten von Voicemail-Einstellungen für einen Benutzer
ms:assetid: 73957938-048a-4f9c-bd0f-a3c2c3dcd638
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Aa998851(v=EXCHG.150)
ms:contentKeyID: 50475952
ms.date: 05/23/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Verwalten von Voicemail-Einstellungen für einen Benutzer

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Sie können Unified Messaging- und Voicemailfunktionen sowie Konfigurationseinstellungen für einen Benutzer anzeigen und festlegen, der für UM und Voicemail aktiviert wurde. Sie können beispielsweise folgende Aufgaben ausführen:

  - Die Outlook Voice Access-PIN eines Benutzers zurücksetzen.

  - Die Durchwahlnummer für eine persönliche Vermittlungsstelle hinzufügen.

  - Andere Durchwahlnummern hinzufügen.

  - Die automatische Spracherkennung (Automatic Speech Recognition, ASR) aktivieren oder deaktivieren.

  - Mailboxansageregeln aktivieren oder deaktivieren.

  - Den Zugriff auf E-Mails oder Kalender aktivieren oder deaktivieren.


> [!NOTE]
> Einige Einstellungen und Funktionen können nur über die Shell konfiguriert werden.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://technet.microsoft.com/de-de/library/JJ835776(v=EXCHG.150)).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass ein UM-Wählplan erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://technet.microsoft.com/de-de/library/Bb123819(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://technet.microsoft.com/de-de/library/Bb123510(v=EXCHG.150)).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass der vorhandene Benutzer für Unified Messaging aktiviert ist. Ausführliche Anleitungen finden Sie unter [Aktivieren eines Benutzers für Voicemail](https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Konfigurieren oder Anzeigen der Eigenschaften eines UM-aktivierten Benutzers mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**  \> **Postfächer**.

2.  Wählen Sie in der Listenansicht das Postfach aus, dessen UM-Postfachrichtlinie Sie ändern möchten.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** \> **Unified Messaging** auf **Details anzeigen**.

4.  Klicken Sie auf der Seite **UM-Postfach** auf **UM-Postfacheinstellungen**, um folgende UM-Eigenschaften für einen vorhandenen UM-aktivierten Benutzer anzuzeigen oder zu ändern:
    
      - **PIN-Status**   In diesem schreibgeschützten Feld wird der Status des Benutzerpostfachs angezeigt. Bei UM-aktivierten Benutzern wird der PIN-Status standardmäßig als **Nicht gesperrt** aufgelistet. Wenn der Benutzer jedoch mehrmals eine falsche Outlook Voice Access-PIN eingegeben hat, wird der Status als **Gesperrt** angezeigt.
    
      - **UM-Postfachrichtlinie**   Dieses Feld zeigt den Namen der UM-Postfachrichtlinie, die dem UM-aktivierten Benutzer zugeordnet ist. Sie können auf **Durchsuchen** klicken, um die UM-Postfachrichtlinie zu finden und anzugeben, die diesem UM-Postfach zugeordnet werden soll.
    
      - **Durchwahl für persönliche Vermittlungsstelle**   Verwenden Sie dieses Feld, um die Durchwahlnummer der Vermittlungsstelle für den Benutzer anzugeben. Standardmäßig ist keine Durchwahlnummer konfiguriert. Die Durchwahlnummer darf 1 bis 20 Zeichen lang sein. Eingehende Anrufe für den UM-aktivierten Benutzer können damit an die in diesem Feld angegebene Durchwahlnummer weitergeleitet werden.
        
        Für Wähleinstellungen und automatische Telefonzentralen können weitere Typen von Durchwahlnummern für Vermittlungsstellen angegeben werden. Diese Durchwahlnummern gelten jedoch in der Regel für unternehmensweite Telefonvermittlungen. Die Einstellung Durchwahl für persönliche Vermittlungsstelle kann verwendet werden, wenn ein administrativer oder persönlicher Assistent eingehende Anrufe beantwortet, bevor diese für einen bestimmten Benutzer beantwortet werden.

5.  Auf der Seite **UM-Postfach** können Sie unter **Andere Durchwahlen** Durchwahlnummern für den Benutzer anzeigen, hinzufügen und ändern.
    
      - Zum Hinzufügen einer Durchwahlnummer klicken Sie auf **Hinzufügen**![Hinzufügen (Symbol)](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Hinzufügen (Symbol)"). Verwenden Sie auf der Seite **Weitere Durchwahl hinzufügen** das Feld **Durchsuchen**, um den UM-Wählplan auszuwählen, und geben Sie dann die Durchwahlnummer im Feld **Durchwahlnummer** ein.
    
      - Zum Entfernen einer Durchwahlnummer wählen Sie die entsprechende Durchwahlnummer aus, und klicken Sie dann auf **Entfernen**![Entfernen (Symbol)](images/JJ657492.479b6ced-8d64-4277-a725-f17fea202b28(EXCHG.150).gif "Entfernen (Symbol)").

6.  Wenn Sie Änderungen vorgenommen haben, klicken Sie auf **Speichern**.

## Konfigurieren von Funktionen für einen UM-aktivierten Benutzer mithilfe der Shell

In diesem Beispiel werden die Wiedergabe über Telefon und Benachrichtigungen über verpasste Anrufe deaktiviert, Textnachrichten (SMS) werden jedoch aktiviert.


> [!NOTE]
> Wenn Sie bei lokalen und Hybridbereitstellungen Unified Messaging und Lync Server integrieren, stehen Benachrichtigungen über verpasste Anrufe nicht für Benutzer zur Verfügung, die über ein Postfach auf einem Exchange&nbsp;2007- oder Exchange&nbsp;2010-Postfachserver verfügen. Es wird eine Benachrichtigung über einen verpassten Anruf generiert, wenn ein Benutzer sich abmeldet, bevor der Anruf an einen Postfachserver gesendet wurde.



    Set-UMMailbox -Identity tony@contoso.com -UMEnabled $true -UMMailboxPolicy AdminPolicy -MissedCallNotificationEnabled $false -PlayonPhoneEnabled $false -SMSMessageWaitingNotificationEnabled $true

In diesem Beispiel wird ein Benutzer am Zugriff auf den Kalender gehindert, es wird jedoch der E-Mail-Zugriff aktiviert, wenn der Benutzer Outlook Voice Access verwendet.

    Set-UMMailbox -Identity tony@contoso.com -UMEnabled $true -UMMailboxPolicy AdminPolicy -Extension 523456 -FAXEnabled $true -TUIAccessToCal $false -TUIAccessToEmail True

In diesem Beispiel wird ein Benutzer am Zugriff auf Kalender und E-Mail gehindert, wenn der Benutzer Outlook Voice Access verwendet.

    Set-UMMailbox -Identity tony@contoso.com -TUIAccessToCalendarEnabled $false -TUIAccessToEmailEnabled $false

In diesem Beispiel wird der Benutzer daran gehindert, Mailboxansageregeln zu erstellen, eingehende Faxe zu empfangen und Outlook Voice Access zu verwenden, die automatische Spracherkennung wird jedoch aktiviert.

    Set-UMMailbox -Identity tony@contoso.com -AutomaticSpeechRecognitionEnabled $true -CallAnsweringRulesEnabled $false -FaxEnabled $false -SubscriberAccessEnabled $false 

## Anzeigen der Eigenschaften eines UM-aktivierten Benutzers mithilfe der Shell

In diesem Beispiel wird eine Liste aller UM-aktivierten Postfächer in der Gesamtstruktur in einer formatierten Liste angezeigt.

    Get-UMMailbox | Format-List

In diesem Beispiel werden die UM-Postfacheigenschaften für "tonysmith@contoso.com" angezeigt.

    Get-UMMailbox -Identity tonysmith@contoso.com


> [!IMPORTANT]
> Wenn Sie Exchange 2007 und Exchange 2013 ausführen und das Postfach des Benutzers auf einem Exchange 2007-Postfachserver gespeichert ist, funktioniert das Cmdlet <STRONG>Get-UMMailbox</STRONG> nicht ordnungsgemäß. Zur Lösung dieses Problems führen Sie das Cmdlet <STRONG>Get-UMMailbox</STRONG> auf einem Exchange 2007-Server oder einem Computer mit den Exchange 2007-Verwaltungstools aus.


