---
title: 'Aktivieren eines Benutzers für Voicemail: Exchange 2013 Help'
TOCTitle: Aktivieren eines Benutzers für Voicemail
ms:assetid: ad027767-5e14-4cb1-9f8a-0791d9188db5
ms:mtpsurl: https://technet.microsoft.com/de-de/library/Bb124147(v=EXCHG.150)
ms:contentKeyID: 50476448
ms.date: 04/24/2018
mtps_version: v=EXCHG.150
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Recipients.EnableUnifiedMessagingWizardForm.EnableUnifiedMessagingWizardPage
ms.translationtype: HT
---

# Aktivieren eines Benutzers für Voicemail

 

_**Gilt für:** Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Letztes Änderungsdatum des Themas:** 2013-02-22_

Wenn Sie einen Benutzer für Unified Messaging (UM) aktivieren, wird eine Standardgruppe von Eigenschaften auf den Benutzer angewendet, und der Benutzer ist in der Lage, die Voicemailfunktionen von Unified Messaging zu nutzen. Nachdem Sie einen Benutzer für Voicemail aktiviert haben, können Sie für den Benutzer eine SIP-Adresse (Session Initiation Protocol) hinzufügen, wenn er einem UM-Postfach zugewiesen ist, das mit einem SIP-URI-Wählplan verknüpft ist. Alternativ können Sie eine E.164-Nummer für den Benutzer hinzufügen, wenn er einer UM-Postfachrichtlinie zugewiesen ist, die mit einem E.164-Wählplan verknüpft ist. In beiden Fällen muss für den Benutzer weiterhin eine Durchwahlnummer konfiguriert sein.

Eine Durchwahlnummer ist für jeden Benutzer erforderlich, der einer Telefondurchwahl, einem SIP-URI oder einem E.164-Wählplan zugewiesen ist. Die Durchwahlnummer muss mit der Anzahl der Ziffern übereinstimmen, die in den UM-Wähleinstellungen für die UM-Postfachrichtlinie festgelegt sind.


> [!NOTE]
> Wenn Sie für einen UM-aktivierten Benutzer eine Durchwahlnummer hinzufügen, entfernen oder ändern möchten, müssen Sie die Exchange-Verwaltungskonsole oder die Shell verwenden. Dies gilt auch, wenn der Benutzer mit einem SIP-URI- oder E.164-Wählplan verknüpft ist. Wenn Sie für einen Benutzer eine SIP-Adresse oder E.164-Nummer hinzufügen, entfernen oder ändern möchten, müssen Sie die Shell verwenden, weil diese Optionen in der Exchange-Verwaltungskonsole nicht verfügbar sind.



Informationen zu weiteren Verwaltungsaufgaben in Bezug auf für Voicemail aktivierte Benutzer finden Sie unter [VoIP-e-Mail-aktivierten Benutzer Prozeduren](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/voice-mail-enabled-user-procedures).

## Was sollten Sie wissen, bevor Sie beginnen?

  - Geschätzte Zeit bis zum Abschließen des Vorgangs: 5 Minuten.

  - Bevor Sie diese Verfahren ausführen können, müssen Ihnen die entsprechenden Berechtigungen zugewiesen werden. Informationen zu den von Ihnen benötigten Berechtigungen finden Sie unter "UM-Postfächer" im Thema [Unified Messaging-Berechtigungen](unified-messaging-permissions-exchange-2013-help.md).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass UM-Wähleinstellungen erstellt wurden. Ausführliche Anleitungen finden Sie unter [Erstellen eines UM-Wählplans](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan).

  - Vergewissern Sie sich vor dem Ausführen dieser Verfahren, dass eine UM-Postfachrichtlinie erstellt wurde. Ausführliche Anleitungen finden Sie unter [Erstellen einer UM-Postfachrichtlinie](https://review.docs.microsoft.com/de-de/exchange/voice-mail-unified-messaging/set-up-voice-mail/create-um-mailbox-policy).

  - Informationen zu Tastenkombinationen für die Verfahren in diesem Thema finden Sie unter [Tastenkombinationen in der Exchange-Verwaltungskonsole](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Liegt ein Problem vor? Bitten Sie in den Exchange-Foren um Hilfe. Besuchen Sie die Foren unter <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A> oder <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Was möchten Sie machen?

## Aktivieren eines Benutzers für Voicemail mithilfe der Exchange-Verwaltungskonsole

1.  Klicken Sie in der Exchange-Verwaltungskonsole auf **Empfänger**.

2.  Wählen Sie in der Listenansicht den Benutzer aus, den Sie für Unified Messaging aktivieren möchten.

3.  Klicken Sie im Detailbereich unter **Telefon- und Sprachfunktionen** auf **Aktivieren**.

4.  Klicken Sie auf der Seite **UM-Postfach aktivieren** neben **UM-Postfachrichtlinie** auf die Schaltfläche **Durchsuchen**, navigieren Sie zu der UM-Postfachrichtlinie, der Sie den Benutzer aus der Liste zuweisen möchten, und klicken Sie dann auf **OK**.

5.  Füllen Sie auf der Seite **UM-Postfach aktivieren** die folgenden Felder aus:
    
      - **SIP-Adresse** oder **E.164-Nummer**   Geben Sie in das Textfeld **SIP-Adresse** oder **E.164-Nummer** die SIP-Adresse oder E.164-Nummer des Benutzers ein. Diese Optionen sind nur verfügbar, wenn der Benutzer, den Sie für Unified Messaging aktivieren, einer UM-Postfachrichtlinie zugewiesen ist, die mit einem SIP-URI- oder E.164-Wählplan verknüpft ist. Sie können keine SIP-Adresse oder E.164-Nummer für einen Benutzer hinzufügen, wenn dieser einem Wählplan mit Telefondurchwahlen zugeordnet ist.
        
        Wenn Sie den Benutzer einer UM-Postfachrichtlinie zuweisen, die mit einem SIP-URI oder E.164-Wählplan verknüpft ist, müssen Sie eine Durchwahlnummer für den Benutzer eingeben. Der Benutzer nutzt diese Durchwahlnummer für den Zugriff auf sein Postfach über Outlook Voice Access. Die Anzahl der in diesem Feld konfigurierten Ziffern muss der Anzahl von Ziffern entsprechen, die für die SIP-URI- oder E.164-Wähleinstellungen konfiguriert ist.
    
      - **Durchwahlnummer**   Verwenden Sie dieses Textfeld, wenn Sie die Durchwahlnummer für den Benutzer, den Sie für UM aktivieren, manuell eingeben möchten.
        
        Sie müssen für den Benutzer angeben eine gültige Durchwahlnummer, die mit der im Wählplan angegebenen Anzahl von Ziffern übereinstimmt. Sie können nur Ziffern von 1 bis 20 eingeben. Eine typische Durchwahlnummer hat 3 bis 7 Ziffern. Die Anzahl von Ziffern der Durchwahl ist für den Wählplan festgelegt, der mit dem UM-Postfach verknüpft ist, das dem Benutzer zugewiesen ist.
    
      - Führen Sie unter **PIN-Einstellungen** folgende Schritte aus:
        
          - **PIN automatisch generieren**   Klicken Sie auf diese Schaltfläche, um automatisch eine PIN für den UM-aktivierten Benutzer zu generieren, mit der der Benutzer über Outlook Voice Access auf das Voicemailsystem zugreifen kann. Dies ist die Standardeinstellung. Die PIN wird automatisch basierend auf den PIN-Richtlinien erstellt, die in der dem Empfänger zugeordneten UM-Postfachrichtlinie konfiguriert sind. Diese Einstellung hilft, die PIN des Benutzers zu schützen. Die PIN wird in der Begrüßungsnachricht an den Benutzer gesendet, die er nach der Aktivierung für UM erhält. Standardmäßig muss diese PIN bei der ersten Anmeldung beim Postfach zum Abrufen der Voicemail geändert werden.
        
          - **PIN eingeben**   Nach Klicken auf diese Schaltfläche können Sie eine PIN eingeben, die der Benutzer für den Zugriff auf das Voicemailsystem verwenden kann. Die PIN muss den PIN-Richtlinieneinstellungen entsprechen, die in der diesem UM-aktivierten Benutzer zugeordneten UM-Postfachrichtlinie konfiguriert sind. Wenn die UM-Postfachrichtlinie beispielsweise so konfiguriert wurde, dass ausschließlich PINs mit sieben oder mehr Ziffern akzeptiert werden, muss die in diesem Feld eingegebene PIN mindestens sieben Ziffern umfassen.
        
          - **Benutzer muss PIN bei der ersten Anmeldung zurücksetzen**   Aktivieren Sie dieses Kontrollkästchen, um festzulegen, dass der Benutzer seine Voicemail-PIN ändern muss, wenn er das erste Mal mit einem Telefon über Outlook Voice Access auf das Voicemailsystem zugreift. Sie werden dazu aufgefordert, eine ihnen vertrautere PIN einzugeben. Dabei handelt es sich um eine bewährte Sicherheitsmethode, mit der UM-aktivierte Benutzer gezwungen werden, ihre PIN bei der ersten Anmeldung zu ändern. Auf diese Weise werden die Daten und Posteingänge besser vor unbefugtem Zugriff geschützt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

6.  Überprüfen Sie auf der Seite **UM-Postfach aktivieren** Ihre Einstellungen. Klicken Sie auf **Fertig stellen**, um den Benutzer für Voicemail zu aktivieren. Klicken Sie auf **Zurück**, um Konfigurationsänderungen vorzunehmen.

## Aktivieren eines Benutzers für Voicemail mithilfe der Shell

In diesem Beispiel wird Unified Messaging für das Postfach von "tonysmith@contoso.com" aktiviert, die Durchwahlnummer wird auf 51234 festgelegt, die PIN für den Benutzer wird auf 5643892 festgelegt, und der Benutzer wird der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugewiesen.

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -PINExpired $true

In diesem Beispiel wird Unified Messaging für das Postfach von "tonysmith@contoso.com" aktiviert, der Benutzer wird der UM-Postfachrichtlinie `MyUMMailboxPolicy` zugewiesen, und für den Benutzer werden die Durchwahlnummer, die SIP-Adresse und die PIN festgelegt.

    Enable-UMMailbox -Identity tonysmith@contoso.com -UMMailboxPolicy MyUMMailboxPolicy -Extensions 51234 -PIN 5643892 -SIPResourceIdentifier "tonysmith@contoso.com" -PINExpired $true

