---
title: 'Aktiv. d. Aufzeichn. benutzerdef. Ansagen ü. Benutzerschnitt. für Tel.eing.'
TOCTitle: Aktivieren der Aufzeichnung benutzerdefinierter Ansagen über die Benutzerschnittstelle für Telefoneingaben
ms:assetid: f2e5c636-2be9-4d48-b5e7-37913ded62d1
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb691404(v=EXCHG.150)
ms:contentKeyID: 54652713
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Aktivieren der Aufzeichnung benutzerdefinierter Ansagen über die Benutzerschnittstelle für Telefoneingaben

 

_**Gilt für:** Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2014-09-17_

Mithilfe der Shell können Sie die Aufzeichnung benutzerdefinierter Ansagen und Begrüßungen für UM-Wählpläne (Unified Messaging) und automatische UM-Telefonzentralen über die Benutzerschnittstelle für Telefoneingabe (Telephone User Interface, TUI) aktivieren. Dies kann hilfreich sein, wenn Sie eine benutzerdefinierte Begrüßung mithilfe der Exchange-Verwaltungskonsole oder der Shell ändern möchten oder wenn ein Notfall eintritt, z. B. eine Schließung der Organisation aufgrund extremer Wetterbedingungen. Wenn Sie eine benutzerdefinierte Begrüßung oder Ansage in einer automatischen UM-Telefonzentrale ändern, müssen Sie für den Wählplan, mit dem die automatische UM-Telefonzentrale verknüpft ist, TUI-Ansagenaufzeichnung aktivieren.

Zusätzliche Verwaltungsaufgaben im Zusammenhang mit UM-Wählplänen finden Sie unter [UM-Wählplan – Verfahren](um-dial-plan-procedures-exchange-2013-help.md).

Zusätzliche Verwaltungstasks im Zusammenhang mit automatischen UM-Telefonzentralen finden Sie unter [Automatische UM-Telefonzentrale – Verfahren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/um-auto-attendant-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 3 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Wählpläne" und "Automatische UM-Telefonzentralen" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine automatische UM-Telefonzentrale erstellt wurde. Genaue Anweisungen finden Sie unter [Erstellen einer automatischen UM-Telefonzentrale](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/create-a-um-auto-attendant).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Ermöglichen der Aufzeichnung einer benutzerdefinierten Ansage oder Begrüßung über die Benutzerschnittstelle für Telefoneingabe mithilfe der Shell

Befolgen Sie diese Schritte, um angepasste Ansagen und Begrüßungen über die TUI aufzuzeichnen:

1.  Erstellen Sie ein Domänenbenutzerkonto, für das keine interaktive Anmeldung möglich ist.

2.  Weisen Sie dem Domänenbenutzerkonto die Exchange-Organisationsadministrator-Rolle zu.

3.  Erstellen Sie ein Postfach für den Domänenbenutzer.

4.  Aktivieren Sie das Postfach des Domänenbenutzers für Unified Messaging.
    

    > [!IMPORTANT]
    > Gewähren Sie nur den Administratoren, die Ansagen und Begrüßungen verwalten sollen, den Zugriff auf die Durchwahl und die PIN für das Benutzerkonto. Verwenden Sie dieses Benutzerkonto ausschließlich für die Verwaltung von Ansagen über das Telefon.



5.  Erstellen und speichern Sie eine WAV- oder WMA-Datei, die für eine benutzerdefinierte Begrüßung für die UM-Wählpläne oder die automatische UM-Telefonzentrale verwendet werden soll.
    

    > [!NOTE]
    > MP3-Dateien können für benutzerdefinierte Ansagen nicht verwendet werden.



6.  Konfigurieren Sie den Wählplan über die Exchange-Verwaltungskonsole oder die Shell so, dass die benutzerdefinierte Begrüßung verwendet wird, oder konfigurieren Sie die automatische Telefonzentrale so, dass die Begrüßung während oder außerhalb der Geschäftszeiten verwendet wird. Nähere Informationen zur Konfiguration eines Wählplans finden Sie unter [Aktivieren einer benutzerdefinierten Begrüßung für Outlook Voice Access-Benutzer](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-client-voice-mail-features/enable-a-customized-greeting). Nähere Informationen zur Konfiguration einer automatischen Telefonzentrale finden Sie unter [Aktivieren Sie eine benutzerdefinierte Begrüßung während der Geschäftszeiten](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/enable-a-customized-business-hours-greeting) oder [Aktivieren Sie eine benutzerdefinierte Geschäftszeiten Begrüßung](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/automatically-answer-and-route-calls/enable-a-customized-non-business-hours-greeting).

7.  Führen Sie das folgende Cmdlet aus:
    
        Set-UMDialPlan -identity MyUMDialPlan -TUIPromptEditingEnabled $true


> [!NOTE]
> Bevor Sie die Aufzeichnung einer benutzerdefinierten Ansage oder Begrüßung aktivieren können, müssen Sie sich bei dem Postfach anmelden, das für Ansagenaufzeichnung eingerichtet ist. Nachdem Sie die neue Ansage oder Begrüßung aufgezeichnet haben, müssen Sie sich abmelden und dann erneut anmelden, bevor Sie die neue Ansage oder Begrüßung hören können, wenn Sie die TUI verwenden.



## Aufzeichnen von TUI-Ansagen für eine automatische UM-Telefonzentrale

1.  Vergewissern Sie sich, dass die automatische Telefonzentrale mit dem Wählplan verknüpft ist, den Sie für die Aufzeichnung von TUI-Ansagen aktiviert haben.

2.  Rufen Sie eine Telefonnummer an, die für die automatische UM-Telefonzentrale konfiguriert wurde.

3.  Drücken Sie während der Wiedergabe der Begrüßung während oder außerhalb der Geschäftszeiten durch die automatische Telefonzentrale die Taste mit dem Nummernzeichen (\#) und dann die Sterntaste (\*).

4.  Sie werden aufgefordert, die Durchwahlnummer des Benutzers einzugeben. Geben Sie die Durchwahlnummer des UM-aktivierten Benutzers ein, der die Berechtigung zum Aufzeichnen von TUI-Ansagen hat.

5.  Sie werden zur Eingabe einer PIN aufgefordert. Geben Sie die PIN des Benutzers ein.

6.  Befolgen Sie die Systemansagen, um die Begrüßung oder die Informationsansage für die automatische Telefonzentrale zu bearbeiten oder zu aktualisieren.

## Aufzeichnen von TUI-Ansagen für einen UM-Wählplan

1.  Rufen Sie eine Outlook Voice Access-Nummer an, mit der Sie sich bei Outlook Voice Access anmelden.

2.  Drücken Sie während der Wiedergabe der Begrüßung durch den UM-Wählplan die Taste mit dem Nummernzeichen (\#) und dann die Sterntaste (\*).

3.  Wenn Sie mit einem Telefon anrufen, das von einem UM-aktivierten Benutzer verwendet wird, werden Sie zur Eingabe einer PIN aufgefordert. Anstatt die PIN einzugeben, drücken Sie die Sterntaste (\*). Sie werden aufgefordert, eine Durchwahl einzugeben. Geben Sie die Durchwahlnummer des UM-aktivierten Benutzers ein, der die Berechtigung zum Aufzeichnen von TUI-Ansagen hat.

4.  Wenn Sie mit einem Telefon anrufen, das nicht von einem UM-aktivierten Benutzer verwendet wird, werden Sie automatisch zur Eingabe einer Durchwahl aufgefordert. Geben Sie die Durchwahlnummer des UM-aktivierten Benutzers ein, der die Berechtigung zum Aufzeichnen von TUI-Ansagen hat.

5.  Sie werden zur Eingabe einer PIN aufgefordert. Geben Sie die PIN des Benutzers ein.

6.  Befolgen Sie die Systemansagen, um die Begrüßung oder die Informationsansage für den Wählplan zu bearbeiten oder zu aktualisieren.

