---
title: 'Zurücksetzen einer Voicemail-PIN: Exchange 2013 Help'
TOCTitle: Zurücksetzen einer Voicemail-PIN
ms:assetid: bf07e6e7-01d2-4933-bff5-c615cc21a480
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124404(v=EXCHG.150)
ms:contentKeyID: 50554920
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.ResetUnifiedMessagingPinPropertyControl
ms.translationtype: HT
---

# Zurücksetzen einer Voicemail-PIN

 

_**Gilt für:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:**2013-02-22_

Wenn ein UM-aktivierter (Unified Messaging) Voicemailbenutzer sein Postfach durch mehrfache Anmeldeversuche bei Outlook Voice Access mit einer falschen PIN gesperrt oder seine PIN vergessen hat, kann seine PIN mithilfe eines der folgenden Verfahren zurückgesetzt werden. Beim Zurücksetzen der Outlook Voice Access-PIN eines Benutzers können Sie Unified Messaging für die automatische PIN-Generierung konfigurieren oder die PIN manuell angeben. Die neue PIN wird per E-Mail an den Benutzer gesendet. Sie können weitere PIN-Optionen angeben, z. B. den Benutzer auffordern, bei der ersten Anmeldung seine PIN zurückzusetzen. Benutzer können außerdem ihre UM-PIN mithilfe von Outlook oder Outlook Web App zurücksetzen.


> [!NOTE]
> Für den Zugriff auf UM-aktivierte Postfächer müssen Outlook Voice Access-Benutzer mit Tastaturwahl- bzw. DTMF-Eingaben (Dual Tone Multi-Frequency) arbeiten. Die Spracherkennung ist für die PIN-Eingabe nicht verfügbar.



Informationen zu weiteren Aufgaben im Zusammenhang mit der Outlook Voice Access-PIN-Sicherheit finden Sie unter [PIN-Sicherheitsverfahren](pin-security-procedures-exchange-2013-help.md).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: Weniger als 1 Minute.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Zurücksetzen einer Unified Messaging-PIN mithilfe der Exchange-Verwaltungskonsole

1.  Navigieren Sie in der Exchange-Verwaltungskonsole zu **Empfänger**. Wählen Sie in der Listenansicht das Benutzerpostfach aus, das angezeigt werden soll.

2.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** unter **Unified Messaging** auf **Details anzeigen**.

3.  Klicken Sie auf der Seite **UM-Postfach** auf **UM-Postfacheinstellungen** und dann auf **PIN zurücksetzen**.

4.  Wählen Sie auf der Seite **UM-Postfach-PIN zurücksetzen** die folgenden Optionen, um die PIN des UM-aktivierten Benutzers zurückzusetzen:
    
      - **PIN automatisch generieren**   Verwenden Sie diese Option, um automatisch die PIN zu generieren, die der Benutzer verwendet, wenn er mithilfe von Outlook Voice Access auf sein Postfach zugreift. Diese Einstellung ist standardmäßig aktiviert.
        
        Die automatisch generierte PIN wird in einer E-Mail-Nachricht an das Postfach des Benutzers gesendet. Nachdem der Benutzer die PIN erhalten und sich an seinem Postfach angemeldet hat, wird er aufgefordert, die PIN in eine leichter zu merkende PIN zu ändern.
        
        Outlook Web App und Microsoft Outlook ermöglichen Benutzern ebenfalls das Zurücksetzen der PIN. Die PIN wird automatisch auf Basis der PIN-Richtlinien generiert, die für die UM-Postfachrichtlinie konfiguriert sind, die dem Postfach des Benutzers zugeordnet ist. Es wird empfohlen, die PINs für Outlook Voice Access-Benutzer automatisch zu generieren.
    
      - **PIN angeben**   Wählen Sie diese Option, um eine PIN für einen Outlook Voice Access-Benutzer manuell anzugeben. Diese Einstellung ist standardmäßig deaktiviert.
        
        Wenn Sie eine PIN für einen Benutzer angeben, wird die PIN in einer E-Mail-Nachricht an das Postfach des Benutzers gesendet. Nachdem er die PIN erhalten und sich beim Postfach angemeldet hat, kann er die PIN durch Konfigurieren persönlicher Optionen in Outlook Voice Access ändern. In Outlook Web App und Microsoft Outlook ist jedoch keine Option für die manuelle Angabe einer PIN verfügbar.
    
      - **Benutzer muss PIN bei der ersten Anmeldung zurücksetzen**   Wählen Sie diese Option, um anzufordern, dass der Benutzer bei der ersten Anmeldung bei Outlook Voice Access seine PIN ändern muss. Diese Option ist standardmäßig aktiviert.
        
        Wenn Sie die Option zum automatischen Generieren einer PIN für einen Benutzer aktivieren, können Sie mithilfe dieser Option anfordern, dass der Benutzer seine PIN beim erstmaligen Anmelden bei Outlook Voice Access ändert. Dies erhöht die Sicherheit für die Benutzer-PIN.

5.  Klicken Sie auf **Speichern**.

## Zurücksetzen einer Unified Messaging-PIN mithilfe der Shell

In diesem Beispiel wird die Voicemail-PIN für Tony Smith auf 1985848 zurückgesetzt. Diese PIN muss jedoch beim erstmaligen Anmelden des Benutzers bei Outlook Voice Access geändert werden.

    Set-UMMailboxPIN -Identity tonysmith@contoso.com -PIN 1985848 -PinExpired $true

